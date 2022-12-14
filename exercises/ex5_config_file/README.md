# Exercise 5 - configuration file

In this exercise we will create a configuration file to specify the samples
we want to work on, instead of having them specified in the Snakefile. This
allows to decouple the code from the data, as it means that modifying the
pipeline won't be necessary to rerun it on different samples.

you can write a configuration file in YAML format (see [this tutorial](https://www.educative.io/blog/yaml-tutorial)
for details).

Briefly, for our case, a yaml file consists in a list of associations, like this:

```
key:
    - value1
    - value2
    - value3
```

in this case, the `value*` entries are all part of `key`. A close analogy is
folders in your hard drive - you would have the `key` folder, which contains
the `value` files.

Of course, keys (=directories) can be nested:

```
key:
    key2:
        value
    key3:
        value 
```

In Snakemake, a configuration is loaded using the `configfile` directive, once
and at the beginning of a Snakefile:

```
configfile: "config.yaml"
```

this allows to access the `config` object within the Snakefile. `config` acts 
as a dictionary which respects the same structure as the yaml file. For instance,
for the first case you would have:

```
config['key']
```

that contains the three `value` strings.

edit your Snakefile so that it reads sample name from a configuration file
rather than having them being specified in the Snakefile directly.
Once you use the `configfile` directive, you can use the `config`
object which stores the values you need. 
