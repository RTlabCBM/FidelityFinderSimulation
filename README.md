# FidelityFinderSimulation


## Table of Contents 

1. [Introduction](#introduction)
2. [Quick Start](#quick-start)
3. [Input Parameters](#input-parameters)
4. [Sample Output Results](#sample-output-results)
5. [Creative Commons](#creative-commons)
6. [Citation](#citation)
7. [Developers](#developers)


## Introduction

Python script to simulate an RT-PCR experiment incorporating cDNA barcoding and NGS sequencing. The program aims to assess the ability of single-strand consensus sequencing (SSCS) to evaluate the fidelity of reverse transcriptases, as well as its accuracy in discarding errors introduced during library preparation and sequencing.

Single Strand Consensus Sequencing method to determine the fidelity of reverse transcriptases:
![SSCS](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/sscs_method.PNG?raw=true)

The program initiates by generating a specified number of cDNA sequences (`initial_seq_number`) with a length defined by `seq_len`. A barcode (also known as Unique Molecular Identifier) is assigned to each cDNA sequence. The length of the barcode can be specified with `barcode_len` parameter. Random mutations are introduced to the cDNA sequences based on the probability defined by the `RT_error_rate parameter`. These mutations emulate transcription and reverse transcription errors.

Subsequently, the cDNAs are then amplified through the indicated PCR cycles with a probability of introducing errors in the sequences (determined by `PCR_error_rate`) or in the barcodes associated (`PCR_error_rate_for_barcodes`). `PCR_selection_rate` governs the proportion of sequences amplified during each PCR cycle, thereby simulating PCR bias.

Following PCR amplification, a subset of sequences (determined by `NGS_reads_number`) undergoes sequencing simulation. Errors may be introduced in the sequences or their associated barcodes, as defined by `NGS_error_rate` and `NGS_error_rate_for_barcodes`. Additionally, the program also allows the introduction of errors in specific positions of the barcodes with varying probabilities, controlled by `NGS_error_rate_for_barcodes_hotspots` and modulated by `hotspots_module`. A `hotspots_module` of 2 introduces errors in even positions of the barcodes, while a value higher than `barcode_len` has no effect. 

Single nucleotide substitution errors are the sole type of simulated errors.

## Quick Start
The program is available as a Jupyter Notebook. It can be opened and run with the following Google Colab link: [fidelity_finder_simulation](https://colab.research.google.com/github/RTlabCBM/FidelityFinderSimulation/blob/main/JupyterNotebooks/fidelity_finder_simulation.ipynb)

## Input Parameters

Parameters that can be provided as input together with example values:

- Number of cDNA sequences that are generated by reverse transcription
```console
initial_seq_number = 3000
```
- Length of the initial_sequences (nt)
```console
seq_len = 300
```
- Length of the barcode added to each sequence (nt)
```console
barcode_len = 14
```
- Error rate during reverse transcription
```console
RT_error_rate = 0.00002
```
- Number of PCR cycles
```console
PCR_cycles_number = 15
```
- Proportion of sequences that are amplified in each PCR cycle (0.0-1.0)
```console
PCR_selection_rate = 0.3
```
- Error rate during each cycle of PCR
```console
PCR_error_rate = 0.00003
```
- Error rate during each cycle of PCR for barcode amplification
```console
PCR_error_rate_for_barcodes = 0.00003
```
- Number of reads that are sequenced
```console
NGS_reads_number = 130000
```
- Error rate during sequencing
```console
NGS_error_rate = 0.001
```
- Error rate during sequencing of barcodes
```console
NGS_error_rate_for_barcodes = 0.001
```
- Error rate during sequencing of barcodes hotspots
```console
NGS_error_rate_for_barcodes_hotspots = 0.01
```
- Hotspots module. Select a 2 to introduce hotspots in even positions. Select a number higher than barcode_len to avoid hotspots
```console
hotspots_module = 2
```
- Cutoffs for sequence filtering. Barcode frequencies equal to or lower are discarded. Provide a comma-separated list
```console
cutoffs_list = "1,2,3,4"
```
- Thresholds for consensus construction. Provide a comma-separated list
```console
thresholds_list = "0,75,100"
```
- Output_prefix for the generated files
```console
output_prefix = "simulation1"
```

## Sample Output Results
The program generates several files, including graphs, an Excel file with a summary of the obtained results, and `.json` files with specific data. These are some examples of the output data:

- Summary data excel (`<output_prefix>summary_data.xlsx`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/excel_file_sample.png?raw=true)
- Barcode size families distribution(`<output_prefix>total_frequencies_distribution_graph.png`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/simulation30000total_frequencies_distribution_graph.png?raw=true)
- Distribution of mutations across the sequence for a fixed cutoff and threshold (`<output_prefix>mutations_distribution_graph_cutoff_3_threshold_100`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/simulation30000mutations_distribution_graph_cutoff_3_threshold_100.png?raw=true)
- Error rates by barcode for a fixed threshold value (`<output_prefix>all_error_rates_graph.png`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/simulation30000all_error_rates_graph.png?raw=true)
- Histogram with the percentages of the max frequency nucleotide in each position of the aligned sequences used for consensus construction (`<output_prefix>Max_frequent_nucleotides_percentages_histogram_cutoff_1_threshold_0.png`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/simulation30000Max_frequent_nucleotides_percentages_histogram_cutoff_1_threshold_0.png?raw=true)
- Distribution of barcode size families together with offsprings percentages (`<output_prefix>percentage_differences.png`)
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/simulation30000percentage_differences.png?raw=true)

## Creative Commons
![image](https://github.com/RTlabCBM/FidelityFinderSimulation/blob/main/docs/images/cc_logo.png?raw=true)
**Attribution-NonCommercial-ShareAlike 4.0 International**  
**(CC BY-NC-SA 4.0)** 

## Citation  
We politely request that this work be cited as:  
(Citation details are not yet available)

## Developers
### Main developer
- Javier Martínez del Río
