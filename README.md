# FidelityFinderSimulation


## Table of Contents 

1. [Introduction](#introduction)
2. [Input parameters](#input-parameters)
3. [Sample_output_results](#test-data-results)
4. [Creative Commons](#creative-commons)
5. [Citation](#citation)
6. [Developers](#developers)


## Introduction

Python script to simulate an RT-PCR experiment incorporating cDNA barcoding and NGS sequencing. The purpose of the program is to assess the ability of single-strand consensus sequencing (SSCS) to identify mutations present in the original cDNAs, as well as its accuracy to discard errors introduced during library preparation and sequencing.
  
The program initiates by generating a specified number of cDNA sequences (`initial_seq_number`) with a length defined by `seq_len`. A barcode (also known as Unique Molecular Identifier) is assigned to each cDNA sequence. The length of the barcode can be specified with `barcode_len` parameter. Random mutations are introduced to the cDNA sequences based on the probability defined by the `RT_error_rate parameter`. These mutations emulate transcription and reverse transcription errors.

Subsequently, the cDNAs are then amplified through the indicated PCR cycles with a probability of introducing errors in the sequences (determined by `PCR_error_rate`) or in the barcodes associated (`PCR_error_rate_for_barcodes`). `PCR_selection_rate` governs the proportion of sequences amplified during each PCR cycle, thereby simulating PCR bias.

Following PCR amplification, a subset of sequences (determined by `NGS_reads_number`) undergoes sequencing simulation. Errors may be introduced in the sequences or their associated barcodes, as defined by `NGS_error_rate` and `NGS_error_rate_for_barcodes`.Additionally, the program also allows the introduction of errors in specific positions of the barcodes with varying probabilities, controlled by `NGS_error_rate_for_barcodes_hotspots` and modulated by `hotspots_module`. A `hotspots_module` of 2 introduces errors in even positions of the barcodes, while a value higher than `barcode_len` has no effect.

For both cDNA and barcode sequences, single nucleotide substitution errors are the sole type of simulated errors.

Numbers are used to represent nucleotide bases in the sequences:
    0    correct nucleotide
    1    mutated nucleotide introduced in the cDNA (transcription or reverse transcription origin)
    2    mutated nucleotide introduced during PCR
    3    mutated nucleotide introduced during NGS

  For barcode sequences, the same numerical system is employed, but the numbers hold no inherent meaning.

## Quick start

## Input parameters



## Sample_output_results

## Citation  
We politely request that this work be cited as:  
(Citation details are not yet available)

## Developers
### Main developer
- Javier Martínez del Río
