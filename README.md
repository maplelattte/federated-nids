# Federated Learning based Network Intrusion Detection System for 4G/5G Networks

## Overview
Network security in modern 4G/5G infrastructure presents a unique 
challenge — base stations generate massive amounts of traffic data, 
but sharing that data with a central server raises serious privacy 
concerns and creates bandwidth bottlenecks.

This project addresses that problem by implementing a 
privacy-preserving Network Intrusion Detection System (NIDS) using 
Federated Learning. Instead of centralizing raw traffic data, each 
base station trains a local model and shares only the model weights 
with a central aggregation server. The server combines these updates 
using the FedAvg algorithm to produce a continuously improving global 
detection model — without ever seeing the underlying data.

## How it Works
The system simulates a real-world 5G deployment with 5 base stations 
acting as federated clients. Each client holds its own local dataset 
of network flow records and trains independently. After every round 
of local training, the server collects the weight updates, averages 
them, and redistributes the improved global model back to all clients. 
This process repeats for 10 rounds, with the model's detection 
accuracy improving measurably after each one.

## Dataset
The project uses a synthetic dataset modeled on the structure of 
CIC-IDS2017, one of the most widely used benchmarks in network 
intrusion detection research. It contains 200,000 network flow 
records across 8 traffic categories:

- BENIGN
- DDoS
- PortScan  
- Bot
- DoS Slowloris
- FTP-Patator
- SSH-Patator
- Web Attack

Each record includes 15 flow-level features such as packet length, 
flow duration, bytes per second, and TCP flag counts — the kind of 
measurements a real network sensor would capture.

## Tech Stack
- Python, PyTorch — model building and training
- Flower (flwr) — federated learning framework
- Scikit-learn — preprocessing and evaluation metrics
- Pandas, NumPy — data manipulation
- Matplotlib, Seaborn — visualization

## Results
The federated model achieves approximately 86% overall accuracy 
after 10 communication rounds. It performs particularly well on 
high-volume attack types like DDoS and PortScan, which are detected 
with near-perfect precision. The round-by-round accuracy graph below 
shows consistent improvement as the global model benefits from 
knowledge aggregated across all five clients.


## Running the Project
The entire pipeline runs in Google Colab with no local setup required.

1. Open `NIDS_Federated_Learning.ipynb` in Google Colab
2. Run all cells from top to bottom
3. Charts and evaluation metrics generate automatically


## Team
- [Aviral Upadhyay](https://github.com/maplelattte)
- [Dakshita Mathur](https://github.com/dakshita1010)
