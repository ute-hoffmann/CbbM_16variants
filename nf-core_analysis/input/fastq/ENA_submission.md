Instructions based mainly on instructions by Michael Jahn

# Submission of sequencing data to ENA - European Nucleotide Archive

This file is a mark down document and can be rendered to HTML, PDF and other formats using for example Rstudio. The entries were used for a file submission of TnSeq files, but it can also serve as template for future submissions.

## Submission How-To

1. upload individual samples using FTP, see details below
2. login to ENA web client at https://www.ebi.ac.uk/ena/submit/sra/#home
3. create new study or select existing one
4. enter study details 
5. enter sample details (alternatively upload a premade table)
6. enter run details  (alternatively upload a premade table)
7. finalize submission


----------

### FTP file submission

Upload via FTP is the best option. Data must be uploaded **before** entering any study/sample details, so that the system can map it. First start the local FTP program in linux terminal:

```
ftp webin2.ebi.ac.uk
```

Login data for ENA is saved in keepass

Enter user name and password. Then enter and execute the following commands (in this order).
**Important note: Switch to passive mode on client side** if the following error message appears:
`200 PORT command successful. Consider using PASV. 425 Failed to establish connection.` after trying to upload a file. If `passive` switches the client to active, just repeat the command to switch back to passive. The command `mput <file-pattern>` (= multiple file upload) should match the file names that are supposed to be uploaded.

```
ftp> bin
ftp> prompt
ftp> passive
ftp> mput *.fastq.gz
```

Comment 2024-09-02: Somehow worked without all the commands above, press "a" for "all" when asked [anpqy?]. "prompt" would suppress re-iterating questions.

### Create new study (optional)

**Release date**

some future day

**Short name of study**

Cyanobacterial Form II Rubisco screening platform

**Full name of study**

A cyanobacterial screening platform for mutant variants of a Form II Rubisco

**Keywords**

Rubisco, high-throughput screening, cyanobacteria, Synechocystis, protein engineering, enzyme engineering

**Abstract**

Flux control in the Calvin-Benson-Bessham (CBB) cycle is distributed over several reactions operating far from equilibrium. In particular Rubisco has significant control over carbon fixation for growth or biosynthesis. We have developed an enzyme engineering platform with the ultimate goal of increasing carbon fixation and conversion by the model cyanobacterium Synechocystis sp. PCC 6803. Starting with targeted mutagenesis libraries, we used competitive growth coupled to deep sequencing to compare the properties of Rubisco protein variants under different cultivation conditions. As the type I Rubisco of cyanobacteria, green algae and land plants may be phylogenetically constrained regarding mutations and catalytic parameters, we used a type II Rubisco, as these show more sequence diversity and lower folding requirements. We show that the platform identifies enzyme variants of the type II Rubisco that affect cell growth in different conditions. The establishment of this platform is a first step towards high-throughput screening of Rubisco variants in Synechocystis and creating optimized enzyme variants to accelerate the CBB cycle in cyanobacteria and possibly chloroplasts.

### Sample annotation

A tab-separated table in `*.tsv` format has to be prepared for sample annotation. The file for the 1st cultivation large library is ENA_defaultSampleTable_SmallLibrary.tsv

### Run annotation

A tab-separated table in `*.tsv` format has to be prepared with file (run) names and descriptions. For the first cultivation large library, the file is called fastq1_template_1725275624938_smallLibrary.tsv

### Finalize submission

Push the submit button
