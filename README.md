orensicGraph - Money Muling Detection System



Live Demo URL
https://6996cc8b1fc39d1ad0954d42--teal-phoenix-7f61fd.netlify.app
LinkedIn Video:
https://www.linkedin.com/posts/omm-prakash-lenka-b20498364_rift2026-teaminvincible-moneymuling-ugcPost-7430415296189931522-d1-j?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFp8BUgBkz4jgtW7sy0efEL-s5oC8lGXyek
Problem Statement
Financial institutions require fast, interpretable, and scalable detection of money muling structures hidden inside raw transaction logs. This system identifies high-risk account clusters, detects structural fraud rings, and visualizes suspicious fund movement patterns to support investigator triage.
System Architecture:
CSV Upload -> Validation Layer -> Detection Engine -> Graph Builder -> D3 Visualization
                                      |
                                      +-> [Cycle Detection (Depth-Limited DFS)]
                                      +-> [Smurfing Detection (Fan-In / Fan-Out)]
                                      +-> [Shell Chain Detection (BFS)]
                                      +-> [False Positive Filter]
                                      +-> [Suspicion Scoring Engine]
Algorithm Approach
Cycle detection: O(V × (V + E)) depth-limited DFS traversal (bounded path length 3-5) with cycle normalization.
Smurfing detection: O(T log T) timestamp sorting with 72-hour sliding window aggregation checks.
Shell chains: O(V + E) BFS traversal with constrained multi-hop path validation and low-degree filtering.
False positive filter: O(V) heuristic node-level behavioral filtering to protect merchants and payroll accounts.
Suspicion Score Methodology
Signal	Weight
cycle_length_3	+45
cycle_length_4	+55
cycle_length_5	+65
fan_in	+40
fan_out	+40
shell_network	+30
high_velocity	+10
multi-pattern bonus	+15
Final score is capped at 100.0 and sorted in descending order in the JSON output.
Tech Stack
Layer	Technology
Frontend	React.js, Tailwind CSS
Visualization	D3.js v7 (Force Directed Graph)
Backend	Node.js / Express (or Python / Flask)
Detection Engine	Custom DFS/BFS + heuristic scoring
Deploy	Netlify (Frontend), Render/Railway (Backend)
Installation & Setup
Clone repository.
Install backend dependencies:
npm install
or
pip install -r requirements.txt
Start backend server:
npm run dev
or
python app.py
Install frontend dependencies:
npm install
Start frontend:
npm start
Open:
http://localhost:3000
API Documentation
POST /analyze
Content-Type: multipart/form-data
Field: csv_file
Response includes:
suspicious_accounts
fraud_rings
summary
graph.nodes
graph.links
GET /download-json
Returns latest completed analysis as downloadable JSON.
Filename: forensicgraph_report.json
CSV Format Requirements
Required canonical fields:
transaction_id
sender_id
receiver_id
amount
timestamp
Timestamp format must be:
YYYY-MM-DD HH:MM:SS
Strict schema validation is enforced before processing.
Known Limitations
Cycle detection is bounded to length 3-5 to maintain performance guarantees.
Extremely dense transaction graphs may reduce visualization clarity.
Smurfing detection currently uses a fixed 72-hour time window.
Heuristic-based scoring does not yet include machine learning anomaly detection.
Cross-dataset fraud correlation is not supported in the current version.
Team Members
OMM PRAKASH LENKA (Team Leader)
RASHI TIWARI
ARPITA AWASTHI
