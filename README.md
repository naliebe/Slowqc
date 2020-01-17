# Slowqc
RNAseq Pipeline to go from raw Fastq files to DEBrowser/iDEP ready input

This pipeline accepts untrimmed FASTQ files and performs the following: 
* Quality and adapter trimming using `Trimmomatic` 
* Transcript abundance quantification using Kallisto 
* Alignment and quantification to Human mitochondrial, and ribosomal sequences (5.8s, 18s, 28s) using  `bowtie2` 
* Generate FASTQC output 
* Returns a csv with read counts of the original FASTQ file, reads aligning to the ribosome and mitochondrial sequences, and mapped reads to the Human transcriptome. 

## Running the pipeline 

All paired end FASTQ files in the folder with the python script will be run through the pipeline. Wildcard searches are used to distinguish R1 and R2 files, so they must have "R1" and "R2" in their filenames. `Trimmomatic` and `Bowtie2` must be installed and added to `$PATH`. 

#### *If all of this is fine all you have to do is place the python script in the folder of FASTQ files* 

The required reference sequences for the `bowtie2`  alignment and adapters.fa for the trimming will be automatically downloaded and built by the script. The only file that must be provided is for the optional kallisto alignment: [Transcriptome.idx](https://github.com/pachterlab/kallisto-transcriptome-indices/releases/download/ensembl-96/homo_sapiens.tar.gz). 

