# Exercise 2 - more general rule with wildcards

In this exercise we want to make the rule you generated in the previous
step more general, allowing it to be able to work on read files 
of different names, such as `data/A.fastq` and `data/B.fastq`,
using wildcards. You can work on this starting from the Snakefile
you built in the previous exercise.

You will need:

- the genome FASTA file `data/genome.fa`
- the reads FASTQ files `data/A.fastq` and `data/B.fastq`

We want to obtain:

- mapped reads file `mapped_reads/A.bam` and `mapped_reads/B.bam`

Using the command:

```
bwa mem GENOME_FILE READS_FILE | samtools view -Sb - > OUTPUT_FILE
```

first, create a Snakefile with a single rule that performs this operation
and run it. The file will need to work on both A.fasta and B.fasta
depending on the target you select. This can be done using wildcards.

Remember that in order to specify a target file it needs to be an
argument of the snakemake command line, i.e.:

```
snakemake -c 1 my_output_file.bam
```

finally, add to the snakemake a first pseudorule `all` to specify
all your targets and rerun your workflow. Be aware that in this case
you don't need to specify targets in the command line (as they are already)
defined in the Snakefile rule `all`). Also remember that Snakemake doesn't
rerun rules whose output files are already present - if this is the case, either
remove them or use option --forceall to force overwrite.

- can you find a way to ask snakemake to run both samples at the same time?

