# Exercise 3 - a longer workflow

In this exercise we want to add two more steps (=rules) to our pipeline,
which correspond to sorting and indexing. Remember that we should always
try and keep our pipeline general, and therefore use wildcards where possible. 
You can start from the Snakefile produced in the previous exercise.

For the *sorting* step, you will need:

- a mapped reads files `mapped_reads/[AB].bam`

We want to obtain:

- a sorted reads file `sorted_reads/[AB].bam`

Using the command (for example, for sample A):

```
samtools sort -T sorted_reads/A -O bam mapped_reads/A.bam > sorted_reads/A.bam
```

We then want to *index* the sorted reads file. This is done in another step
that needs:

- the sorted reads file `sorted_reads/[AB].bam`

and has as output:

- the index file `sorted_reads/[AB].bam.bai`

using command (for example, for sample A):

```
samtools index sorted_reads/A.bam
```

once you are ready, run the pipeline, check the output and output files

