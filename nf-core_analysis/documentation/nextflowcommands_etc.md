# Preparing input files

Collect all relevant input files in [input](../input).

* [2023-05-23_Rubisco_barcodes.fa](../input/2023-05-23_Rubisco_barcodes.fa) is the library of used barcodes
* [samplesheet_Rubisco.csv](../input/samplesheet_Rubisco.csv) gives which sample is which
* the respective .fastq.gz files are collected in the folder [../input/fastq](../input/fastq) and are the output of a sequencing run on a NextSeq 2000 system using NextSeq 1000/2000 P1 reagents (Illumina). The used workflow is "Illumina DRAGEN BCL Convert 3.10.4". Downloaded using the command "bs download run --id 273520278" (compare [Basespace CLI documentation](https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-overview))

# nf-core-crispriscreen parameter decisions

Pipeline commit used for analysis: [e4aad5be10264d99e632761fc8fc56e68d6357c4](https://github.com/MPUSP/nf-core-crispriscreen/commit/e4aad5be10264d99e632761fc8fc56e68d6357c4) from 11th April 2024

```
conda activate env_nf
nextflow run ../../../pipelines/nf-core-crispriscreen/ -profile singularity --input "input/samplesheet_Rubisco.csv" --fasta "input/2023-05-23_Rubisco_barcodes.fa" --outdir "output_new" --five_prime_adapter GTCTAGAatcgccgaaagtaattcaactccattaa...TCTAGATGCTTACTAGTTACCGCGGCCA --error_rate 0.2 --filter_mapq=1 --max_cpus 5 --max_memory 12GB --run_mageck false --gene_fitness false
```

# nf-core-crispriscreen parameter decisions with third replicate LD, only LD and HLHC

Pipeline commit used for analysis: [e4aad5be10264d99e632761fc8fc56e68d6357c4](https://github.com/MPUSP/nf-core-crispriscreen/commit/e4aad5be10264d99e632761fc8fc56e68d6357c4) from 11th April 2024

Run this script alone to create heat map showing correlation of LD replicate 3 with continuous light samples

```
conda activate env_nf
nextflow run ../../../pipelines/nf-core-crispriscreen/ -profile singularity --input "input/samplesheet_Rubisco_only_MC_HLHC_LDHC.csv" --fasta "input/2023-05-23_Rubisco_barcodes.fa" --outdir "output_compare_HLHC_LDHC" --five_prime_adapter GTCTAGAatcgccgaaagtaattcaactccattaa...TCTAGATGCTTACTAGTTACCGCGGCCA --error_rate 0.2 --filter_mapq=1 --max_cpus 5 --max_memory 12GB --run_mageck false --gene_fitness false
```

# Further analyses

For creating heat map to show correlation of LD replicate 3 with continuous light samples [plots_correlations_LD_HL.Rmd](source/plots_correlations_LD_HL.Rmd)

For creating other plots: [plots.Rmd](source/plots.Rmd)



