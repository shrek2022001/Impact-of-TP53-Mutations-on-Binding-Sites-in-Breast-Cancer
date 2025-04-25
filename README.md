# TP53 Mutations and Binding Sites in Breast Cancer

This project explores how TP53 mutations affect TP53 DNA binding sites in breast cancer using ChIP-sequencing (ChIP-seq) data. Specifically, it compares the binding profiles of wild-type TP53 and mutant TP53 (R175H) in MCF-7 breast cancer cells to understand the impact of mutation on chromatin accessibility and gene regulation.

## 📌 Project Overview

The TP53 gene is a critical tumor suppressor frequently mutated in cancer. These mutations can lead to both loss and gain of function, affecting transcriptional regulation and promoting tumor progression.

In this study, we focus on four TP53-regulated loci: **BAX**, **BBC3**, **BRCA1**, and **CDKN1A**, comparing binding site profiles between wild-type and mutant TP53.

## 🔬 Methods Summary

### 1. Data Acquisition
- ChIP-seq datasets from SRA:
  - Wild-type: `SRR18355704`
  - Mutant-type: `SRR18355705`
- Downloaded using:
  ```bash
  fasterq-dump SRR18355704 --split-files --outdir ./fastq_files/wild_type
  fasterq-dump SRR18355705 --split-files --outdir ./fastq_files/mutant_type
