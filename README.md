# Introduction
This repository contains pipeline for metagenomic diet analysis of Snow Leopard.


# Requirements
The script is designed to be run with Python 3.5+ using the platform Jupyter Notebook.

Requires:
* Python >= 3.5+
* Biopython >= 1.74
* Jupyter Notebook >= 6.0.1
* ncbi-blast+ >= 2.2.31.4


# Pipeline
Download `blastRefDatabase.ipynb` and open it using Jupyter Notebook. The program performs the pipeline as described below.

### Build local BLAST database
Download `GenbankRef.zip` and unzip it. The zipped folder contains all available sequence of barcoding genes from NCBI Genbank. Five barcoding genes are included: COI, COX3, CYTB, ND2 and ND4. The program builds five databases (one database for one barcoding gene) for the usage of BLAST.

### Run BLAST against Local Reference Databases
The program reads the given input file (in fasta format) and performs BLAST locally against the local databases. The BLAST is performed using default settings, except expected value (E-value) threshold is set to 0.001.

### Parse BLAST results
The program then parsed the BLAST output. First, it removes hits that found to belong to Human (Homo sapiens), Bacteria or Fungi. Then, it filters hits which identity < 98% and those sharing < 50 bp overlap with reference sequence. Finally, it extracted the top hit for each read and count the number of read aligned to each species.


# Acknowledgement
We acknowledge support from Biomedical Science Department and Computer Science Department of Wright State University.

Last updated: March 2021
