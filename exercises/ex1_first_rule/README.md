# Exercise 1 - simple rule

This is the first step of our pipeline. We will create a single rule that
performs read mapping starting from a reads file and a genome file.

You will need:

- the genome FASTA file `data/genome.fa`
- the reads FASTQ file `data/A.fastq`

We want to obtain:

- a mapped reads file `mapped_reads/A.bam`

Using the command:

```
bwa mem GENOME_FILE READS_FILE | samtools view -Sb - > OUTPUT_FILE
```

create a Snakefile with a single rule that performs this operation
and run it, by running `snakemake -c 1`.

- what do you notice in the snakemake output?
- what if you had to process the `data/B.fastq` file as well?

