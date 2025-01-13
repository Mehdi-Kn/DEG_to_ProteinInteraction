# **DEG_to_ProteinInteraction**

## **Overview**
`DEG_to_ProteinInteraction` is a bioinformatics pipeline designed to construct and analyze protein-protein interaction (PPI) networks starting from a list of differentially expressed genes (DEGs). This workflow integrates transcriptomic data with publicly available protein interaction databases, enabling researchers to uncover key biological insights such as hub proteins, functional modules, and enriched pathways.

---

## **Features**
- **Input Support:** Accepts DEGs in CSV format (gene symbols, log2 fold changes, and p-values).
- **Gene-to-Protein Mapping:** Maps DEGs to UniProt protein identifiers using APIs or annotation tools.
- **PPI Retrieval:** Queries interaction data from STRING, BioGRID, and other databases.
- **Network Construction:** Builds and visualizes PPI networks using `networkx` and other tools.
- **Topology Analysis:** Identifies hub proteins and key network metrics (degree centrality, betweenness, clustering).
- **Enrichment Analysis:** Performs Gene Ontology (GO) and pathway enrichment analysis.
- **Interactive Visualization:** Generates interactive network plots for easy interpretation.

---

## **Pipeline Workflow**

### **1. Differential Expression Analysis**
- Input: Raw RNA-Seq count data or preprocessed DEG list.
- Method: Differential expression analysis using tools like `DESeq2`, `edgeR`, or `limma` (examples provided in R).
- Output: A CSV file with significant DEGs (gene symbols, log2 fold changes, and p-values).

---

### **2. Gene-to-Protein Mapping**
- **Description:** Maps DEGs to protein identifiers (e.g., UniProt IDs) for compatibility with PPI databases.
- **Tools:** 
  - **Python:** UniProt API via `bioservices`.
  - **R:** Bioconductor packages like `biomaRt` or `org.Hs.eg.db`.
- **Output:** A file (`Mapped_DEGs.csv`) with mapped protein identifiers.

---

### **3. Retrieve PPI Data**
- **Description:** Fetches PPI data for mapped proteins from databases like STRING or BioGRID.
- **Method:** Queries APIs or downloads data manually.
- **Output:** A tabular file (`PPI_network.tsv`) containing interaction data with scores.

---

### **4. Build and Analyze PPI Networks**
- **Construction:** Uses tools like `networkx` or `igraph` to build PPI networks.
- **Topology Analysis:**
  - Degree Centrality: Identifies highly connected proteins (hubs).
  - Betweenness Centrality: Finds bottleneck proteins critical for information flow.
  - Clustering Coefficient: Analyzes modular structure.

---

### **5. Functional Enrichment Analysis**
- **Description:** Enriches key proteins in the network for pathways and biological processes.
- **Tools:** 
  - Python: `gseapy`, `goatools`.
  - R: `clusterProfiler`, `ReactomePA`.
- **Output:** Enriched terms and pathways, saved in CSV format.

---

### **6. Visualization**
- **Tools:**
  - **Interactive:** `pyvis` for Python or Cytoscape.
  - **Static:** Use `matplotlib` for high-quality figures.
- **Output:** Graph files (`PPI_network.html`, `ppi_network.gml`) for network exploration.

---

## **Installation**

### **Clone Repository**
```bash
git clone https://github.com/Mehdi-Kn/DEG_to_ProteinInteraction.git
cd DEG_to_ProteinInteraction
```

### **Install Dependencies**
#### Python
Install the required Python packages:
```bash
pip install -r requirements.txt
```

#### R
Install the required R packages:
```R
install.packages(c("DESeq2", "clusterProfiler", "org.Hs.eg.db", "igraph"))
```

---

## **Usage**

### **1. Input DEGs**
Prepare a file (`DEGs.csv`) with the following format:
```csv
gene_symbol,log2FoldChange,padj
TP53,2.5,0.001
BRCA1,-1.8,0.02
EGFR,1.2,0.03
```

### **2. Run the Workflow**
#### **Python Pipeline**
Execute the main Python script to map DEGs, retrieve PPI data, and construct the network:
```bash
python run_pipeline.py --input DEGs.csv --output results/
```

#### **R Scripts**
If you're using R for differential expression or enrichment analysis:
```R
source("run_DESeq2.R")       # For DEG analysis
source("run_enrichment.R")  # For functional enrichment
```

### **3. Output Files**
- **Mapped_DEGs.csv:** Mapped protein identifiers.
- **PPI_network.tsv:** PPI interactions from STRING or BioGRID.
- **ppi_network.gml:** Graph file for visualization.
- **node_centrality.csv:** Network topology metrics.
- **GO_enrichment.csv:** Enriched biological processes.
- **Pathway_enrichment.csv:** Enriched pathways.

---

## **Visualization**
### Interactive Visualization with `pyvis`:
```bash
python visualize_network.py --input PPI_network.tsv --output PPI_network.html
```
Open `PPI_network.html` in your browser for exploration.

### Advanced Visualization with Cytoscape:
1. Import `ppi_network.gml` into Cytoscape.
2. Apply clustering or enrichment plugins for further analysis.

---

## **Example Dataset**
Example input and output files are provided in the `example_data/` directory:
- `example_DEGs.csv`
- `example_PPI_network.tsv`
- `example_GO_enrichment.csv`

---

## **Dependencies**
- **Python:** `pandas`, `networkx`, `requests`, `pyvis`, `gseapy`
- **R:** `DESeq2`, `clusterProfiler`, `ReactomePA`, `igraph`

---

## **PPI Databases Supported**
- **STRING:** [https://string-db.org](https://string-db.org)
- **BioGRID:** [https://thebiogrid.org](https://thebiogrid.org)
- **IntAct:** [https://www.ebi.ac.uk/intact](https://www.ebi.ac.uk/intact)

---

## **Future Features**
- Multi-omics integration (e.g., proteomics, metabolomics).
- Dynamic PPI networks based on time-course data.
- Graph neural networks for PPI prediction.

---

## **Contributing**
Contributions are welcome! Submit issues or pull requests to enhance the pipeline.

---

## **License**
This project is licensed under the MIT License.

---

## **Acknowledgments**
- Leveraged APIs and datasets from STRING, UniProt, and public resources.
- Special thanks to the open-source bioinformatics community.

---

## Contact
For questions, issues, or suggestions, please contact:
- **Name**: Knidiri Mehdi
- **Email**: m.knidiri70@gmail.com
```

---

### Customization
Replace placeholders (e.g., `yourusername`, `your.email@example.com`) with your details. Let me know if you need help tailoring any part further!
