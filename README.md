# 5G DoS Detection Dataset

A comprehensive synthetic dataset for Denial-of-Service (DoS) attack detection in 5G networks, featuring labeled packet-level and flow-level features extracted from MAC and RLC layers.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Open In Colab - Dataset Processing](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/5G-DoD/blob/main/5G_DoD_DATASET.ipynb)
[![Open In Colab - Model Training](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/5G-DoD/blob/main/5G_DoD_TRAINING.ipynb)

## Overview

With 5G networks increasingly becoming critical infrastructure supporting diverse applications, securing these systems against advanced threats has become paramount. This dataset addresses the challenge of DoS attack detection in 5G environments by providing over **680,000 labeled records** with comprehensive packet and flow-level features.

### Key Features

- **680,075 labeled records** across three collection sessions
- **30 distinctive features** (16 flow-level + 14 packet-level)
- **MAC and RLC layer captures** available separately or for fusion analysis
- **Real 5G infrastructure**: Built using srsRAN and OpenAirInterface 5G Core
- **Realistic traffic patterns**: Benign behavior simulation and DoS attacks
- **High-quality labels**: Based on controlled experimental conditions

## Dataset Statistics

| Metric | Value |
|--------|-------|
| **Total Records** | 680,075 |
| **MAC Layer Records** | 356,803 (52.45%) |
| **RLC Layer Records** | 323,272 (47.55%) |
| **Benign Traffic** | 594,730 (87.45%) |
| **Malicious Traffic (DoS)** | 85,345 (12.55%) |
| **Total Size** | 257.58 MB |
| **Features** | 30 |

### Session Breakdown

**Session 1 (Benign):** 117,024 records
- MAC Layer: 64,128 records
- RLC Layer: 52,896 records

**Session 2 (Benign):** 131,140 records
- MAC Layer: 71,632 records
- RLC Layer: 59,508 records

**Session 3 (Mixed - Benign + DoS):** 431,911 records
- MAC Layer: 221,043 records
- RLC Layer: 210,868 records

## Features

### Flow-Level Features (16)
- Flow duration
- Packet count statistics
- Inter-arrival time (IAT) metrics
- Throughput rates (packets/second, bytes/second)
- Flow size characteristics
- IAT coefficient of variation

### Packet-Level Features (14)
- Shannon entropy of payload
- Compression ratio
- Number of unique bytes
- N-gram frequency analysis
- Header-to-payload ratio
- Small packet flag
- Byte distribution statistics

### Metadata
- User Equipment Identifier (UEID)
- Binary attack labels (Benign/DoS)

## Repository Structure

```
5G-DoD/
├── 5G_DoD_DATASET.ipynb          # Data treatment and feature extraction
├── 5G_DoD_TRAINING.ipynb         # Model training and evaluation
├── BENIGN_SECTIONS-CSV.zip       # Benign traffic (CSV format)
├── BENIGN_SECTIONS-PCAP.zip      # Benign traffic (PCAP format)
├── MALICIOUS_SECTION-CSV.zip     # Mixed traffic with DoS attacks (CSV)
├── MALICIOUS_SECTION-PCAP.zip    # Mixed traffic with DoS attacks (PCAP)
├── LICENSE                        # MIT License
└── README.md                      # This file
```

## Getting Started

### Option 1: Google Colab (Recommended)

Click on the Colab badges above to run the notebooks directly in your browser:

- **Dataset Processing**: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/5G-DoD/blob/main/5G_DoD_DATASET.ipynb)
- **Model Training**: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j3les-0/5G-DoD/blob/main/5G_DoD_TRAINING.ipynb)

### Option 2: Local Installation

1. Clone the repository:
```bash
git clone https://github.com/j3les-0/5G-DoD.git
cd 5G-DoD
```

2. Extract the dataset files:
```bash
unzip BENIGN_SECTIONS-CSV.zip
unzip MALICIOUS_SECTION-CSV.zip
```

3. Install required dependencies:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

4. Run the Jupyter notebooks:
```bash
jupyter notebook 5G_DoD_DATASET.ipynb
```

## Experimental Setup

The dataset was generated using an experimental 5G infrastructure:

- **RAN**: srsRAN (open-source Radio Access Network)
- **Core Network**: OpenAirInterface 5G Core (OAI5G) in Docker Compose
- **User Equipment**: 4 independent UE instances
- **Traffic Generation**:
  - Benign behavior: Weighted probabilistic actions (DNS lookups, pings, P2P communication, SSH checks, idle periods)
  - DoS attacks: hping3-based flooding with randomized packet sizes (32-1500 bytes) and variable burst intervals

## Citation

If you use this dataset in your research, please cite:

```bibtex
@misc{ramos2025_5g_dod_dataset,
  author = {Ramos, João Victor Jales and Gurjão, Edmar C. and Santos, Matheus Vilarim P. dos},
  title = {Dataset for 5G DDoS and DoS Detection},
  year = {2025},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/j3les-0/5G-DoD}},
  institution = {Federal University of Campina Grande}
}
```

## Authors

- **João Victor Jales Ramos** - [joao.victor.ramos@ee.ufcg.edu.br](mailto:joao.victor.ramos@ee.ufcg.edu.br)
- **Edmar C. Gurjão** - [ecg@dee.ufcg.edu.br](mailto:ecg@dee.ufcg.edu.br)
- **Matheus Vilarim P. dos Santos** - [matheus.vilarim@ee.ufcg.edu.br](mailto:matheus.vilarim@ee.ufcg.edu.br)

*Electrical Engineering Department*  
*Federal University of Campina Grande*  
*Campina Grande, Brazil*

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- srsRAN Project for the open-source RAN implementation
- OpenAirInterface Software Alliance for the 5G Core Network
- Federal University of Campina Grande, LAPSI and LABMET for infrastructure support
---

**For questions, issues, or contributions, please open an issue on GitHub.**
