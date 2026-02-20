# FORENSIC GRAPH
ForensicGraph is a graph-based financial crime detection system designed to identify suspicious transaction patterns such as money muling networks, circular fund routing, smurfing behavior, and shell account structures.

The platform allows users to upload transaction datasets in CSV format and automatically analyzes relationships between accounts using graph theory algorithms to detect fraud patterns.

🚀 Features
🔄 Cycle Detection

Identifies circular fund routing patterns where money flows through multiple accounts and returns to the origin (e.g., A → B → C → A).

💸 Smurfing Analysis

Detects fan-in and fan-out patterns where many small deposits aggregate into a single account and are later dispersed.

🏦 Shell Network Detection

Finds layered chains of intermediate accounts with minimal transaction history, often associated with shell entities.

📂 CSV Upload Interface

Users can upload transaction data directly through a drag-and-drop interface for instant analysis.

📊 Input Format

The system accepts transaction datasets in CSV format with the following structure:

transaction_id,sender_id,receiver_id,amount,timestamp


Example:

TXN001,A123,B456,5000,2025-01-01 10:30:00
TXN002,B456,C789,4800,2025-01-01 11:00:00

🧠 How It Works

Upload transaction CSV file.

System converts transactions into a graph network.

Algorithms analyze patterns using graph traversal and anomaly detection.

Suspicious networks and accounts are identified.

Results are visualized and exported.

🛠️ Tech Stack (Typical)

Frontend: React / Modern Web UI

Backend: Python / Node.js (Graph processing)

Graph Algorithms: Network analysis (cycles, clustering, path detection)

Data Handling: CSV parsing

Visualization: Graph rendering libraries (e.g., D3.js / Cytoscape)

🌐 Live Demo

🔗 https://6996cc8b1fc39d1ad0954d42--teal-phoenix-7f61fd.netlify.app/

📌 Use Cases

Financial fraud detection

AML (Anti-Money Laundering) investigations

Banking risk analysis

Law enforcement intelligence

FinTech compliance monitoring




📈 Future Improvements

Real-time transaction monitoring

Machine learning risk scoring

Interactive graph visualization

API integration with banking systems

Alert notification system
