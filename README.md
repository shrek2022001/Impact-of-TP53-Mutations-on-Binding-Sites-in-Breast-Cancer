# TP53 Mutations and Binding Sites in Breast Cancer

This project explores how TP53 mutations affect TP53 DNA binding sites in breast cancer using ChIP-sequencing (ChIP-seq) data. Specifically, it compares the binding profiles of wild-type TP53 and mutant TP53 (R175H) in MCF-7 breast cancer cells to understand the impact of mutation on chromatin accessibility and gene regulation.

## Project Overview

The TP53 gene is a critical tumor suppressor frequently mutated in cancer. These mutations can lead to both loss and gain of function, affecting transcriptional regulation and promoting tumor progression.

In this study, we focus on four TP53-regulated loci: **BAX**, **BBC3**, **BRCA1**, and **CDKN1A**, comparing binding site profiles between wild-type and mutant TP53.

## Methods Summary

### 1. Data Acquisition
- ChIP-seq datasets from SRA:
  - Wild-type: `SRR18355704`
  - Mutant-type: `SRR18355705`
- Downloaded using:
  ```bash
  fasterq-dump SRR18355704 --split-files --outdir ./fastq_files/wild_type
  fasterq-dump SRR18355705 --split-files --outdir ./fastq_files/mutant_type

### 2. Quality control
```bash
fastqc ./fastq_files/wild_type/*.fastq -o ./qc_reports/wild_type
fastqc ./fastq_files/mutant_type/*.fastq -o ./qc_reports/mutant_type
```

### 3. Read Alignment
- Aligned to human reference genome hg38 using Bowtie2:
  ```bash
  bowtie2 -x hg38_index -1 sample_1.fastq -2 sample_2.fastq -S output.sam
  ```
- Converted to BAM, sorted, and indexed with Samtools.

### 4. Peak Calling
Performed with MACS2
```bash
macs2 callpeak -t sample.bam -f BAM -g hs -n sample_name --outdir ./macs2_output/
```
### 5. Visualization
-Peaks visualized with IGV.
-Used DeepTools to generate heatmaps:
```bash
computeMatrix scale-regions ...
plotHeatmap ...
```
### 6. Peak Annotation
```bash
annotatePeaks.pl peaks.bed hg38 > annotated.txt
```
## Results: 
BAX: Similar peak heights between wild-type and mutant — binding appears preserved.
BBC3: Mutant TP53 shows additional/ectopic peaks — possible gain of function activity.
BRCA1 and CDKN1A: Similar patterns — likely preserved regulatory function.

