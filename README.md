# 🧠 NeuroNest — High-Performance Vector Database & RAG Pipeline

<p align="center">
  <img src="neuronest.jpeg" width="600" alt="NeuroNest Logo">
</p>

<p align="center">
  <b>A lightweight, high-performance Vector Database engine built from scratch in C++.</b><br>
  Featuring HNSW indexing, KD-Tree partitioning, and a local RAG pipeline powered by Ollama.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17-blue.svg?style=for-the-badge&logo=c%2B%2B" alt="C++">
  <img src="https://img.shields.io/badge/AI-Ollama-orange.svg?style=for-the-badge" alt="Ollama">
  <img src="https://img.shields.io/badge/Algorithm-HNSW-green.svg?style=for-the-badge" alt="HNSW">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="MIT License">
</p>

---

## 🚀 Overview

**NeuroNest** is a custom-built Vector Database designed to handle high-dimensional data efficiently. It allows users to perform semantic searches, visualize clusters in 2D space, and interact with local documents using a **Retrieval-Augmented Generation (RAG)** pipeline.

### Why NeuroNest?
* **Zero Dependencies:** Core engine built in pure C++ using standard libraries.
* **Hybrid Search:** Compare **HNSW**, **KD-Tree**, and **Brute Force** performance side-by-side.
* **Local Privacy:** Integrated with **Ollama** to keep your data 100% private and offline.

---

## 🏗️ System Architecture

Data flows through NeuroNest in three main stages: **Embedding**, **Indexing**, and **Retrieval**.

```mermaid
graph TD
    A[User Input/Doc] -->|HTTP POST| B[C++ Backend]
    B -->|API Call| C[Ollama: Nomic-Embed]
    C -->|768D Vector| B
    B -->|Insert| D[HNSW Multi-layer Graph]
    E[Search Query] -->|Greedy Search| D
    D -->|Top-K Context| F[RAG Pipeline]
    F -->|Prompt + Context| G[Ollama: Llama 3.2]
    G -->|Final Answer| H[UI Response]
