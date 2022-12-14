# Exercise 4 - an aggregation step

In this exercise we will aggregate the information from the available A and
B sample and jointly call variants. In this aggregation step, we suggest
using the `expand` Snakemake function to dynamically create your lists
of necessary input files. In this way, just a simple modification (i.e.
modifying your initial list), will be necessary to change which samples
the workflow runs on. You can start from the Snakefile produced
in the previous exercise.

For example, you can create a list of sample names at the beginning of your
Snakemake file:

```
SAMPLES = ['A', 'B']
```

then, the list of e.g. sorted reads files corresponding of all your samples
will be expressed by:

```
expand(sorted_reads/{sample}.bam, sample=SAMPLES)
```

this function call will return:

```
['sorted_reads/A.bam', 'sorted_reads/B.bam']
```

for the variant calling step you will need:

- the genome file `data/genome.fa`
- both the A and B sorted reads files `sorted_reads/[AB].bam`
- both the A and B index files `sorted_reads/[AB].bam.bai`

and you want to obtain:

- the final vcf variants file `calls/all.vcf`

using the command:

```
bcftools mpileup -f GENOME_FILE SORTED_READS_A SORTED_READS_B | bcftools call -mv - > OUTPUT_VARIANTS_FILE
```

Notice that you're not explicitly using the index files in this command! So
you need a way to specify only part of the input files in the command line
(hint: you can use named inputs, `genome=....`)

