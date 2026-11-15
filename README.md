# QKRISHI-OS-CHALLENGE

## Quantum Hardware Characterization and Connected Qubit Region Selection

This project analyzes calibration and topology data from the **IBM Kingston quantum processor** to identify reliable connected regions of **16 qubits** and **32 qubits**.

The goal is to select physically connected qubits while considering calibration quality, two-qubit connection quality, robustness, and hardware connectivity.

---

## 📌 Project Objective

The IBM Kingston processor contains multiple physical qubits connected through a hardware topology.

The objective of this project is to:

- Analyze qubit calibration data.
- Analyze the hardware connectivity topology.
- Evaluate individual qubit quality.
- Evaluate two-qubit connection quality.
- Identify weak qubits and unreliable connections.
- Find a connected **16-qubit region**.
- Find a connected **32-qubit region**.
- Validate that the selected regions are physically connected.

---

## 📂 Repository Structure

```text
QKRISHI-OS-CHALLENGE/
│
├── HASITHA_VARMA_ASSIGNMENT.ipynb
├── ibm_kingston_calibrations_2026-03-31T09_24_11Z.xls
├── ibm_kingston_topology_complete.json
└── README.md
```

---

## 📊 Dataset

The project uses two main sources of hardware information:

### 1. Calibration Data

The calibration dataset contains information related to qubit and gate performance, including:

- **T1** – Energy relaxation time.
- **T2** – Quantum coherence time.
- **Readout Error** – Error during measurement.
- **Single-Qubit Gate Error** – Error during single-qubit operations.
- **CZ Error** – Error associated with two-qubit interactions.
- **RZZ Error** – Additional two-qubit interaction information.

### 2. Hardware Topology

The topology JSON file describes which physical qubits are connected.

For example:

```json
"25": [24, 26, 37]
```

This means that **qubit 25 is physically connected to qubits 24, 26, and 37**.

---

## 🔍 Methodology

This project uses a **Bottleneck-Aware Connected Region Search** approach.

The methodology considers both the overall quality of a region and its weakest components.

### 1. Qubit Quality

Individual qubits are evaluated using:

- T1
- T2
- Readout error
- Single-qubit gate error

Higher coherence times and lower error rates are preferred.

### 2. Edge Quality

Physical connections between qubits are evaluated primarily using two-qubit gate error information such as **CZ error**.

Lower connection errors indicate more reliable interactions.

### 3. Robustness

A region is not evaluated only by its average performance.

The methodology also checks for:

- Weak qubits
- Weak connections
- Poor bottlenecks

This helps avoid selecting a region where one unreliable component significantly affects the entire region.

### 4. Connectivity

All selected qubits must form a **connected region** in the IBM Kingston hardware topology.

---

## 🧮 Region Scoring

The region evaluation combines four components:

| Component | Weight |
|---|---:|
| Edge Quality | 35% |
| Qubit Quality | 25% |
| Robustness | 25% |
| Connectivity | 15% |

This approach gives strong importance to two-qubit connection quality while also considering individual qubit performance and weak points.

---

## 🏆 16-Qubit Recommendation

The selected 16-qubit connected region is:

```text
[97, 104, 105, 106, 107, 117, 122, 123,
124, 125, 126, 136, 140, 141, 142, 143]
```

This region was selected based on:

- Physical connectivity.
- Individual qubit quality.
- Two-qubit connection quality.
- Robustness against weak components.

---

## 🏆 32-Qubit Recommendation

The selected 32-qubit connected region is:

```text
[59, 73, 74, 75, 79, 91, 92, 93,
94, 97, 98, 103, 104, 105, 106, 107,
108, 109, 110, 111, 117, 122, 123, 124,
125, 126, 136, 140, 141, 142, 143, 144]
```

The selected qubits form a connected region and were evaluated using the same bottleneck-aware methodology.

---

## ✅ Validation

The final candidate regions are checked to ensure:

- The required number of qubits is selected.
- All qubit IDs are valid.
- The selected region is physically connected.
- Internal connections can be evaluated using the available calibration information.

---

## 💡 Key Learning

This project demonstrates that selecting qubits for a quantum computation is not simply about choosing the individually best qubits.

A useful multi-qubit region must consider:

> **Qubit quality + Connection quality + Connectivity + Robustness**

A group with excellent individual qubits may still be unsuitable if the qubits are disconnected or if the connections between them are unreliable.

---

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NetworkX
- JSON
- IBM Quantum hardware calibration data

---

## 👩‍💻 Author

**Hasitha Varma**

B.Tech – Computer Science and Engineering

---

## 📌 Project Files

Run the Jupyter Notebook with the calibration and topology files available in the same project directory.

```text
HASITHA_VARMA_ASSIGNMENT.ipynb
```

The notebook contains the complete analysis, methodology, candidate search, validation, and final recommendations.
