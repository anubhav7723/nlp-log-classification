# 🔍 Log Classification System using NLP, Clustering & LLMs

## 📌 Project Overview

The **Log Classification System** is an intelligent NLP-based pipeline designed to automatically analyze, cluster, and classify large volumes of log messages.  
The system combines **traditional NLP techniques**, **unsupervised learning**, **rule-based classification**, and **LLM-powered inference** to efficiently assign meaningful labels to log entries—even when predefined rules fail.

This hybrid approach ensures **scalability, accuracy, and robustness** in real-world log analysis scenarios where log formats, sources, and patterns vary significantly.

---

## 🎯 Problem Statement

In real-world systems, logs:
- Come from multiple sources
- Have inconsistent formats
- Contain unstructured text
- Often include unknown or unseen patterns

Manual classification is inefficient and error-prone.  
This project solves the problem by **automating log grouping and classification** using NLP, clustering, and AI-driven fallback mechanisms.

---

## 🧠 Solution Architecture (High-Level Flow)

1. Log Ingestion  
2. Text Embedding using Sentence Transformers  
3. Unsupervised Clustering with DBSCAN  
4. Regex-based Rule Classification  
5. Bert Classification with Logistic Regression 
6. LLM-based Classification for Unknown Logs  
7. Final Labeled & Clustered Output  

---

## 📂 Input Data

- Log messages are stored in **CSV or Excel format**
- Each log entry may include:
  - Log message text
  - Source or system identifier

---

## 🔎 Key Components & Methodology

### 1️⃣ Log Preprocessing
- Reads logs from CSV or Excel files
- Cleans and normalizes raw log text
- Handles missing, noisy, or malformed entries

---

### 2️⃣ Sentence Embeddings (NLP)
- Converts log messages into dense vector representations
- Uses **Sentence Transformer models** for semantic understanding
- Enables similarity detection beyond keyword matching

**Why embeddings?**
- Logs with different wording but same meaning are grouped together
- Improves clustering and downstream classification accuracy

---

### 3️⃣ Log Clustering using DBSCAN
- Applies **DBSCAN (Density-Based Spatial Clustering)** on embeddings
- Groups semantically similar log messages
- Automatically detects:
  - Natural clusters
  - Noise and outliers

**Why DBSCAN?**
- No need to define number of clusters
- Handles noise effectively
- Suitable for real-world log distributions

---

### 4️⃣ Regex-Based Classification
- Applies predefined regex rules on clustered logs
- Extracts **target labels** such as:
  - Authentication failures
  - Network issues
  - Database errors

This step ensures **fast and deterministic classification** wherever rules are applicable.

---

### 5️⃣ Bert Classification + Logistic Regression
If a log message:
- Cannot be classified by regex
- Is marked with target label **Unknown**

The system checks:
- Availability of sufficient labeled training samples for that **source and cluster**

If sufficient data exists:
- Performs **Logistic Regression**
- It has been done with help of target labels in Dataset(Supervised Learning)
- Assigns labels based on dominant patterns within the cluster

---

### 6️⃣ LLM-Based Classification (Fallback Layer)
If:
- Target label remains **Unknown**
- Training samples are insufficient
- It is especially for **LegacyCRM** type of source

Then:
- The log message is passed to a **Large Language Model (LLM)**
- The LLM performs contextual understanding
- Generates an appropriate target label

This guarantees coverage even for **rare or unseen log patterns**.

---

### 7️⃣ Final Output
- Each log entry contains:
  - Cluster ID
  - Log source
  - Final target label

- Output can be exported in **CSV or Excel format**

---

## 🛠️ Tech Stack

### 🔍 NLP & Machine Learning
- Python
- Sentence Transformers
- DBSCAN (Unsupervised Clustering)
- Regex-based rule classification
- Logistic Regression

### 🤖 AI / LLM
- Large Language Models for intelligent fallback classification

### 📊 Data Processing
- Pandas
- CSV and Excel file handling

---

## 🚀 Key Features

- Hybrid classification approach (Rules + ML + LLM)
- Unsupervised clustering of log messages
- Semantic similarity-based grouping
- Handles unknown and unseen log patterns
- Scalable for large datasets
- Modular and extensible architecture

---

## 📈 Use Cases

- Application log monitoring
- System and server log analysis
- Incident categorization
- Root cause analysis
- DevOps and IT operations automation

---

## 🏆 Key Highlights

- Combines **NLP embeddings, clustering, and LLM intelligence**
- Reduces manual log analysis effort
- Improves accuracy compared to rule-only systems
- Easily adaptable to new log sources

---

## 📌 Future Enhancements

- Real-time log streaming support
- Interactive dashboard for cluster visualization
- Active learning for continuous improvement
- Adaptive thresholds per log source
