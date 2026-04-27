NeuroNest — High-Performance Vector Database & RAG Pipeline🚀 OverviewNeuroNest is an educational yet powerful Vector Database designed to demonstrate how modern search engines like Pinecone or Milvus handle high-dimensional data. It allows users to perform semantic searches, visualize clusters in 2D space, and chat with their local documents using a RAG (Retrieval-Augmented Generation) pipeline.Why NeuroNest?Zero Dependencies: Core engine built in pure C++.Hybrid Search: Compare HNSW, KD-Tree, and Brute Force performance in real-time.Local Privacy: No data leaves your machine; LLM processing is handled by Ollama.🛠️ Tech StackComponentTechnologyLanguageC++17 (High-performance threading & STL)IndexingHNSW (Hierarchical Navigable Small World), KD-TreeLLM InterfaceOllama (Llama 3.2, Nomic-Embed-Text)BackendHeader-only cpp-httplibFrontendVanilla JS, Tailwind CSS, PCA.js (Visualizer)🏗️ System ArchitectureData flows through NeuroNest in three main stages: Embedding, Indexing, and Retrieval.Code snippetgraph TD
    A[User Input/Doc] -->|HTTP POST| B[C++ Backend]
    B -->|API Call| C[Ollama: Nomic-Embed]
    C -->|768D Vector| B
    B -->|Insert| D[HNSW Multi-layer Graph]
    E[Search Query] -->|Greedy Search| D
    D -->|Top-K Context| F[RAG Pipeline]
    F -->|Prompt + Context| G[Ollama: Llama 3.2]
    G -->|Final Answer| H[UI Response]
✨ Key FeaturesMultilayer HNSW Index: Achieves $O(\log N)$ search complexity for lightning-fast retrieval.2D PCA Visualization: Watch high-dimensional 768D vectors collapse into a 2D map to see "semantic clusters."Live Benchmarking: Run "Compare All" to see exactly how much faster HNSW is compared to Brute Force.Persistence: Data is indexed and kept in memory with persistent storage capabilities.💻 Getting StartedPrerequisitesOllama: Download here and run ollama pull llama3.2 & ollama pull nomic-embed-text.Compiler: GCC (MinGW/MSYS2 for Windows) with C++17 support.Installation & RunBash# 1. Clone the repo
git clone https://github.com/anshika0021/Custom-VectorDataBase-with-HNSW-RAG-Pipeline.git
cd Custom-VectorDataBase-with-HNSW-RAG-Pipeline

# 2. Compile the backend
g++ -std=c++17 -O2 main.cpp -o db -lws2_32

# 3. Run the server
./db
Access the dashboard at: http://localhost:8080📊 Performance ComparisonAlgorithmSearch ComplexityAccuracyBest ForBrute Force$O(N)$100%Small datasetsKD-Tree$O(\log N)$100%Low-dimensional data (<20D)HNSW$O(\log N)$~95-99%High-dimensional (Embeddings)🛡️ API ReferenceMethodEndpointDescriptionGET/search?v=...&algo=hnswPerforms K-NN search using specified algorithm.POST/doc/insertEmbeds and stores a new document chunk.POST/doc/askTriggers the RAG pipeline for Q&A.GET/benchmarkReturns millisecond comparison for all algos.📈 Visualizing High-Dimensional DataNeuroNest uses Principal Component Analysis (PCA) to project 16D (demo) or 768D (real) vectors onto a 2D plane.Pro Tip: Look for the Category Legend in the UI. You will notice that "Computer Science" vectors naturally group together, away from "Food & Cooking" vectors. This is the power of vector embeddings!
