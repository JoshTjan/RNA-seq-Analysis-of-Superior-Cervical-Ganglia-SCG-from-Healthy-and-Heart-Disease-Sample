# RNA-seq Analysis of Superior Cervical Ganglia (SCG) from Healthy and Heart Disease Samples

## Overview

This repository contains the code and documentation for performing RNA-seq analysis on SCG samples obtained from healthy and heart disease donors. The analysis workflow includes data retrieval using `SRAtools`, genome index generation with `STAR`, alignment with `STAR`, and differential expression analysis using `pyDESeq2`. The results are visualized with heatmaps and volcano plots to identify key genes and interesting findings.

## Dataset

- **Title**: RNA-seq of heart healthy and heart diseased SCGs
- **Organism**: Homo sapiens
- **Experiment Type**: Expression profiling by high throughput sequencing

## Analysis Workflow

### 1. Data Retrieval

The first step is to retrieve the RNA-seq data from the SRA (Sequence Read Archive) using `SRAtools`. The following geo data set was used GSE231763. This command can be used to download or can create SRA_list.
fastq-dump --split-files <SRA accession number>


### 2. Genome Index Generation

Before aligning the reads, we need to build a genome index using `STAR`. Make sure you have the reference genome FASTA file and gene annotation GTF file ready. Here's an example of building the index:
STAR --genomeDir /path/to/genome/index --genomeFastaFiles /path/to/genome.fasta --sjdbGTFfile /path/to/annotations.gtf


### 3. Alignment

With the genome index in place, we can align the RNA-seq reads to the reference genome using `STAR`. Here's an example command: STAR --genomeDir /path/to/genome/index --readFilesIn sample_R1.fastq sample_R2.fastq --outSAMtype BAM SortedByCoordinate --outFileNamePrefix sample


### 4. Count Table Generation

Next, we generate a count table from the aligned BAM files using `featureCounts`. Here's an example command:
featureCounts -a /path/to/annotations.gtf -o counts.txt sample.bam


### 5. Differential Expression Analysis

We perform differential expression analysis using `pyDESeq2`. The code for this step can be found in the Jupyter notebook `DESeq2_Analysis.ipynb`.

### 6. Visualization

To visualize the results, we used `gseaplot` for generating plots. The code for creating heatmaps and volcano plots can be found in the Jupyter notebook `Visualization.ipynb`.

## Results

This analysis identified key genes and interesting findings related to the disruption of the physiologic sleep-wake cycle and low melatonin levels in cardiac disease. Please refer to the `Results` section in the Jupyter notebook `DESeq2_Analysis.ipynb` for detailed findings and visualizations using `gseaplot`.

## Conclusion

This analysis provides insights into the mechanism underlying the disturbance of diurnal rhythmicity in cardiac disease and suggests potential therapeutic interventions. The code and data used in this analysis are publicly available for reference.

## Dependencies

- `SRAtools`
- `STAR`
- `pyDESeq2`
- `gseaplot`
- Jupyter notebooks for analysis and visualization

## Usage

To replicate or extend this analysis, follow the workflow steps outlined above and refer to the provided Jupyter notebooks for code and details.




