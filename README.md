# MVP-Cheminformatics: ODAPT

This project explores drug repurposing for Hepatitis B using gene expression data.
Two main workflows were developed:
	1.	Version 1 — Drug Scoring & REINVENT (Molecule Generation)
	2.  Version 2 — DEG Analysis & Functional Enrichment (Biological Context)

## Repository Structure

-- First Version (first_version/)

Focus: Drug repurposing and de novo molecule generation
	•	data/ → Source data and CMap results used to identify candidate compounds.
	•	generate_molecules/ → REINVENT input/output files, generated molecules, and run logs.
	•	notebooks/ → Main Google Colab notebook performing molecule generation and scoring.
	•	results/ → Tables, plots, and summary outputs of the generation process.

-- Second Version (second_version/)

Focus: Gene expression analysis and enrichment in R
	•	data/ → Expression matrix and metadata used for DEG analysis.
	•	results/ → Processed data, enrichment results, and visualization outputs.
	•	notebooks/ → R notebook (or Colab notebook with R kernel) containing the full workflow.

## Results Summary

**Version 1:** Drug Scoring and REINVENT
	•	Differential analysis from GEO data showed minimal differences between control and infected samples, limiting the signal for Connectivity Map (CLUE.io).
	•	Out of 7 suggested drugs, 2 were directly related to Hepatitis B (notably HSP90 inhibitors such as Geldanamycin), while the others had indirect antiviral or immune-modulatory effects.
	•	The generated compounds displayed:
	•	High drug-likeness (QED > 0.9)
	•	Good synthetic accessibility (SA < 3)
	•	Novel structural diversity, with Tanimoto similarity 0.2–0.39 vs. ChEMBL/FDA-approved drugs.
	•	These results suggest REINVENT successfully proposed structurally novel and pharmaceutically viable candidates.

**Version 2:**  DEG and Functional Enrichment
	•	Differential expression was performed using limma (R) for robust statistical testing.
	•	Functional enrichment was done with Reactome GSEA, classifying pathways into:
	•	Interferon / Innate Immune
	•	Lipid / Nucleotide Metabolism
	•	Xenobiotic Enzymes
	•	Oxysterol / Prostaglandin
	•	The dot plot highlights these categories, showing the number of genes involved in each — making it easier to focus on key biological processes affected by HBV.
	•	The analysis indicates that the pathways of interest (Interferon response, lipid metabolism) are indeed modulated, but the genes targeted by the previously identified compounds are not direct HBV targets — suggesting the drugs act through secondary immune or metabolic mechanisms.

> **Important:**  
> The main notebook is developed to run in Google Colab, so it may require adaptations to run properly in a local Jupyter Notebook environment.  

> - I recommend downloading all needed files to Google Drive and just run the notebook, it’s the easiest way. 
> - If you want to run the notebook locally, download all files to your local folder.  
> - You need to install all dependencies listed in `requirements.txt`.  
> - Also, you must modify the code to remove or adapt Colab-specific commands such as `!pip install` and Google Drive integration (`drive.mount()`), as they do not work the same way in Jupyter Notebook.


---

## Usage

To reproduce the REINVENT generation step, please follow the installation and usage instructions in the official REINVENT4 repository.

---

If you have any questions or issues adapting the code for local Jupyter Notebook use, feel free to reach out.
