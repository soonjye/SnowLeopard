# Introduction
This repository contains pipeline for metagenomic diet analysis of Snow Leopard.


# Requirements
The script is designed to be run with Python 3.5+ using the platform Jupyter Notebook.

Requires:
* Python >= 3.5+
* Biopython >= 1.74
* Jupyter Notebook >= 6.0.1
* ncbi-blast+ >= 2.2.31.4
* vsearch >= 2.15.1

# Pipeline
Download `blastRefDatabase.ipynb` and open it using Jupyter Notebook. The program performs the pipeline as described below.

### Build local BLAST database
Download `GbRefgene.zip` and unzip it. The zipped folder contains all available sequence of barcoding genes from NCBI Genbank. Six barcoding genes are included: COI, COX3, CYTB, ND2, ND4 and RBCL. The program builds local databases (one database for one barcoding gene) for the usage of BLAST. If you wish to retrieve other barcoding genes, download `retrieveGBseq.ipynb` and follow the instructions.

### Run BLAST against Local Reference Databases
The program reads the given input file (in fasta format) and performs BLAST locally against the local databases. The BLAST is performed using default settings, except expected value (E-value) threshold is set to 0.001.

### Parse BLAST results
The program then parsed the BLAST output. First, it removes hits that found to belong to Human (Homo sapiens), Bacteria or Fungi (Modifications are needed if you want to keep these). Then, it filters hits which identity < 98% and those sharing < 50 bp overlap with reference sequence. Finally, it extracted the top hit for each read and count the number of read aligned to each species.


# Acknowledgement
We acknowledge support from Biomedical Science Department and Computer Science Department of Wright State University.

Last updated: August 2021
