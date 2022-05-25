## Project Title: Development of machine learning model integrating transcriptional and biological interaction data to predict non-small cell lung cancer using LASSO. 

### Motivation: This repository contains all information to develope a LASSO model for predicting Non-small cell lung cancer (NSCLC). It can also be applied for other cancers.

**It contains following steps:**
1. Identification of Differentially Expressed Genes (DEGs)
    - Lung specific gene expression data was selected TCGA-TARGET-GTEx from Xena (https://xena.ucsc.edu/).
    - Ma'ayan lab's Appyter bulk RNA-seq analysis pipeline was used for DEGs.
        Jupyter Notebook [Xena_DE_Analysis_Pipeline.ipynb](https://github.com/firozimtech/LASSO-for-NSCLC/blob/8e997912adc303525b1a384cd0c32ae2336635e2/Xena_DE_Analysis_Pipeline.ipynb) for DEGs is provided.

2. Create a Volcano plot of DEGs
    - Use the program [Volcano_plot.R.](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/Volcano_plot.R)
    - Use input file [DEGs.](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/DEG_results_Primary_Tumor_Recurrent_Tumor_vs_Normal_Tissue_Solid_Tissue_Normal.csv)
    - Output JPEG file named "volcano_plot.jpeg".
    
3. Identification of biologically important nodes in the network
    - 40 genes identified by analyzing the DEGs and interactome data from BIOGRID using Cytoscape.

4. LASSO model development 
    - Lung specific Gene Expression (RSEM norm_count) data was downloaded from UCSC Xena (https://xena.ucsc.edu/). 
    - The dataset consists of expression values of 40 genes identified in step (2), from 1013 samples of lung cancer and 397 samples as control, was selected.
    - This dataset was divided into 80% training dataset (TR contains 1128 samples) and 20% as independent test dataset 1 (TD1 contains 282 samples).
    - The LASSO model was developed using 10-fold cross-validations(cv) on the TR dataset, and performance was checked on test dataset TD1
    - The performance of LASSO model was checked on three independent datasets:
    GSE18842 (Sanchez-Palencia, Gomez-Morales et al. 2011), GSE27262 (Wei, Juan et al. 2012), and GSE19804 (Lu, Tsai et al. 2010).
    - Programe file (LASSO_Classification_NSCLC.R) is provided.
    - Input file 1: "GeneExp.txt", (Gene Expression data downloaded from Xena). This file is not available due to its big size (373 MB). However, we are providing the TR data as [x.training](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/x4.train.rds) and [y.training.](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/y.train.rds)
    - Input file 2: [DEGs_degree.txt](https://github.com/firozimtech/LASSO-for-NSCLC/blob/8e997912adc303525b1a384cd0c32ae2336635e2/DEGs_degree.txt), List of selecetd genes (40) identified by DEGs and Network analysis.
    - Input file 3: [Sample_Name_3.csv](https://github.com/firozimtech/LASSO-for-NSCLC/blob/8e997912adc303525b1a384cd0c32ae2336635e2/Sample_Name_3.csv), sample name and sample type (Cancer vs Normal).
    - Here is the final [LASSO-MODEL](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/LASSO_model.rds).

5. Checking the performance of [LASSO-MODEL](https://github.com/firozimtech/LASSO-for-NSCLC/blob/main/LASSO_model.rds) on independend datasets(TD1 and TD2).
    


