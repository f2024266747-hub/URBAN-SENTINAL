# UrbanSentinel: AI-Powered Intrusion Detection for Smart-City IoT Networks

**Track:** AI in Urban Tech
**Entry type:** 2 member team 
**Focus areas:** Artificial Intelligence, IoT, Cyber Security, Computer Networks, Cloud Computing

\---

## 1\. Project Overview \& Problem Statement

Modern cities depend on large numbers of connected devices: smart electricity meters, street lights, traffic sensors, water monitors, and surveillance cameras. These devices run around the clock, are cheap, and are often deployed with weak security. If attackers take control of them, they can disrupt power distribution, interfere with traffic systems, or turn the devices into a botnet for large DDoS attacks.

Three problems make this hard to defend:

1. **Scale:** City networks produce far more traffic than human operators can monitor.
2. **Weak devices:** Many IoT devices cannot run heavy security software.
3. **Unknown attacks:** Traditional signature-based tools only catch attacks they already know, so new attack types go unnoticed.

UrbanSentinel addresses these problems with an AI system that continuously analyzes IoT network traffic, detects known attacks, and also flags new, previously unseen attacks.

## 2\. Proposed Solution

UrbanSentinel is a two-layer AI detection system with a cloud dashboard.

**Layer 1: Known attack detection (supervised learning).**
Random Forest and XGBoost classifiers are trained on labeled IoT traffic. They identify known attack categories such as DDoS, port scanning, spoofing, and malware-related traffic.

**Layer 2: Unknown attack detection (anomaly detection).**
An autoencoder neural network is trained only on normal traffic. It learns how healthy city IoT traffic looks. When traffic arrives that it cannot reconstruct well (high reconstruction error), the system flags it as a suspicious, possibly new attack.

**Decision logic.**
Each traffic record gets one of three outcomes: *Normal*, *Known attack (with type)*, or *Unknown suspicious*. A severity level is attached to each alert.

**Cloud dashboard.**
A web dashboard hosted in the cloud shows live traffic, alerts, attack types, and trends. Traffic is replayed from a public dataset to simulate a real-time city network.

## 3\. Objectives \& Expected Outcomes

**Objectives**

* Build and compare multiple AI models for IoT intrusion detection.
* Detect known attack types with high precision and recall.
* Detect unseen attack types using an autoencoder trained only on normal traffic.
* Present results through a clear, cloud-hosted dashboard.

**Expected outcomes**

* A working, end-to-end prototype with a live demo.
* A comparison table of Random Forest, XGBoost, and the autoencoder using accuracy, precision, recall, and F1-score.
* Confusion matrices that show which attack types are detected well and which are confused.
* An experiment showing detection of an attack type that was held out from training.
* Measured detection speed per record, to show real-time suitability.

## 4\. Target Users

* City and municipal IT and security teams
* Smart-grid and utility operators
* Smart-city infrastructure providers
* Universities, campuses, and industrial sites with large IoT deployments

## 5\. Key Features / Deliverables

1. **Data pipeline:** cleaning, encoding, scaling, class balancing, and a proper train/test split.
2. **Supervised detectors:** Random Forest and XGBoost for known attacks.
3. **Autoencoder detector:** trained on normal traffic to catch unknown attacks.
4. **Combined decision engine:** normal, known attack, or unknown suspicious, with severity.
5. **Evaluation report:** metrics, confusion matrices, and model comparison charts.
6. **Cloud dashboard:** live traffic replay, alert feed, attack type breakdown, and trend graphs.
7. **Demo scenario:** normal traffic, then a known attack, then a held-out unknown attack.
8. **Documentation and GitHub repository:** code, results, and setup instructions.

## 6\. Implementation Plan \& Timeline

|Days|Phase|Tasks|
|-|-|-|
|1-2|Data|Select a public IoT intrusion dataset (for example CIC-IoT-2023 or ToN-IoT), download a manageable sample, explore and clean it|
|3-5|Supervised models|Train and tune Random Forest and XGBoost, record all metrics|
|6-8|Anomaly model|Build the autoencoder, set the detection threshold, run the unseen-attack test|
|9-10|Integration|Combine the models into one decision flow with severity levels|
|11-12|Dashboard|Build the dashboard and deploy it to the cloud|
|13-14|Finalization|Collect results, write documentation, prepare the demo and a backup recording|

## 7\. Resources or Requirements

**Data:** a public IoT network intrusion dataset containing normal and labeled attack traffic.

**Software:** Python, pandas, NumPy, scikit-learn, XGBoost, TensorFlow or PyTorch, Streamlit, Git and GitHub.

**Computing:** Google Colab (free GPU) for training; a free cloud hosting service for the dashboard.

**Hardware:** no special hardware needed; a standard laptop is enough.

**Skills used:** machine learning, network traffic analysis, cyber security concepts, cloud deployment.

## 8\. Potential Challenges or Risks

|Risk|Mitigation|
|-|-|
|Dataset is very large and slow to process|Work on a representative sample and process in batches|
|Attack classes are heavily imbalanced|Use class balancing and judge models by F1-score and recall, not accuracy alone|
|Unrealistically perfect scores|Keep the test set separate and check for data leakage|
|Autoencoder produces too many false alarms|Tune the threshold on validation data|
|Results on a dataset may not match real deployments|State this clearly and list real-device testing as future work|
|Demo or internet problems on the day|Keep a recorded backup demo and a local copy of the dashboard|

## 9\. Additional Details

* **Innovation:** most student intrusion detection projects only recognize attacks seen during training. UrbanSentinel adds a second layer that detects unseen attacks, which suits the fast-changing threats that cities face.
* **Urban relevance:** the project protects city infrastructure such as smart grids, street lighting, and traffic systems.
* **Scalability:** the same models and dashboard can be extended to more device types and larger networks.
* **Future work:** deployment on real edge devices (for example a Raspberry Pi gateway), live packet capture, automated response such as isolating a suspicious device, and explainable alerts that show why traffic was flagged.

## 10\. Supporting Documents Submitted With This Proposal

1. UrbanSentinel\_proposal.md`: this proposal
2. system architecture: end-to-end system diagram
3. flowchart: how each traffic record is classified
4. dashboard prototype: design sketch of the dashboard (sample values only)
5. evaluation plan: metrics, experiments, and data-handling rules

