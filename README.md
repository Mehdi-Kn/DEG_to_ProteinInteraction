
# DEG2PPI: Differentially Expressed Genes to Protein-Protein Interaction Analysis

## Overview

`DEG2PPI` is a workflow for building and analyzing protein-protein interaction (PPI) networks starting from differentially expressed genes (DEGs). This pipeline integrates transcriptomic data with curated PPI databases to identify key proteins, functional modules, and enriched biological pathways.

## Features
- Identification of high-confidence PPIs from DEGs.
- Mapping genes to protein identifiers using UniProt or other databases.
- PPI network construction and visualization.
- Network topology analysis to detect hubs and bottlenecks.
- Functional enrichment analysis (Gene Ontology, pathways, etc.).
- Modular and customizable for various datasets and organisms.

---

## Workflow
1. **Input DEGs**: Provide a list of differentially expressed genes (e.g., from RNA-Seq analysis).
2. **Map to Proteins**: Convert gene identifiers to UniProt protein IDs.
3. **Retrieve PPI Data**: Query interaction data from databases like STRING, BioGRID, or IntAct.
4. **Build PPI Network**: Construct and visualize the interaction network.
5. **Analyze the Network**: Identify key proteins and clusters using network metrics.
6. **Functional Enrichment**: Perform pathway and GO enrichment analysis.

---

## Installation

### Clone the Repository
```bash
git clone https://github.com/yourusername/DEG2PPI.git
cd DEG2PPI
```

### Install Dependencies
#### Python
```bash
pip install -r requirements.txt
```
#### R
Install required R packages:
```R
install.packages(c("DESeq2", "clusterProfiler", "org.Hs.eg.db", "igraph"))
```

---

## Usage

### **1. Input DEGs**
Prepare a file (`DEGs.csv`) with the following columns:
- `gene_symbol`: Gene symbol or ID.
- `log2FoldChange`: Log fold change values.
- `padj`: Adjusted p-value.

Example:
```csv
gene_symbol,log2FoldChange,padj
TP53,2.5,0.001
BRCA1,-1.8,0.02
EGFR,1.2,0.03
```

### **2. Run the Workflow**
#### Python Workflow:
```bash
python run_workflow.py --input DEGs.csv --output PPI_network.tsv
```

#### R Workflow:
```R
source("run_workflow.R")
```

### **3. Output Files**
- **Mapped_DEGs.csv**: DEGs mapped to UniProt protein IDs.
- **PPI_network.tsv**: PPI network data retrieved from STRING.
- **ppi_network.gml**: Network graph for visualization.
- **node_centrality.csv**: Key metrics for proteins in the network.

---

## Visualization
- Use `pyvis` for interactive visualization:
```python
python visualize_network.py --input PPI_network.tsv --output PPI_network.html
```
- Alternatively, load `ppi_network.gml` into Cytoscape for advanced visualization.

---

## Functional Enrichment
- Run enrichment analysis in R using `clusterProfiler`:
```R
source("run_enrichment.R")
```
- Outputs:
  - **GO_enrichment.csv**: Enriched Gene Ontology terms.
  - **Pathway_enrichment.csv**: KEGG/Reactome pathway enrichment results.

---

## Example Data
Example input and output files are available in the `example_data` directory for testing the workflow.

---

## Dependencies

### Python
- `pandas`
- `networkx`
- `requests`
- `pyvis`

### R
- `DESeq2`
- `clusterProfiler`
- `org.Hs.eg.db`
- `igraph`

---

## PPI Databases
Supported databases:
- [STRING](https://string-db.org)
- [BioGRID](https://thebiogrid.org)
- [IntAct](https://www.ebi.ac.uk/intact)

---

## Future Features
- Integration of multi-omics data (e.g., proteomics, metabolomics).
- Automated dynamic network analysis.
- Graph Neural Networks (GNNs) for advanced predictions.

---

## Contributing
Contributions are welcome! Please submit issues or pull requests to improve the project.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments
- This pipeline leverages tools and data from STRING, UniProt, and other open-access resources.
- Special thanks to the bioinformatics community for their support and inspiration.

---

## Contact
For questions, issues, or suggestions, please contact:
- **Name**: Knidiri Mehdi
- **Email**: m.knidiri70@gmail.com
```

---

### Customization
Replace placeholders (e.g., `yourusername`, `your.email@example.com`) with your details. Let me know if you need help tailoring any part further!
