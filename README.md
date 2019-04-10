# Mutual exclusivity analysis for de novo mutation datasets

This project searches for mutual exclusivity in the given mutation matrix, for the given list of gene sets.

## Copy

```
git pull https://github.com/PathwayAndDataAnalysis/mutex-de-novo.git
```

## Build

```
cd mutex-de-novo
mvn compile
mvn assembly:single
```
The last command will generate the `mutex-de-novo.jar` file under the `target` directory. Put this jar to a convenient location to use in analyses.

## Analysis inputs

### Mutation matrix

Prepare the mutation matrix as a tab-delimited text file. Example:

|  |Sample1|Sample2|Sample3|Sample4|
|---|---|---|---|---|
|Gene1|0 |1 |0 |1
|Gene2|1 |1 |0 |0
|Gene3|0 |1 |1 |0

### Gene sets file

Prepare the gene sets file as a two-column tab-delimited text file. First column should have a unique name or ID for the gene set. Second column should have the genes separated with a space. Example:

|   |   |
|---|---|
|Set1|Gene1 Gene2 Gene3|
|Set2|Gene4 Gene5 Gene1 Gene3|
|Set3|Gene2 Gene5 Gene7|

Use the HGNC Symbol for the genes.

## Execution
Assume you have the following in your current directory.

`mutex-de-novo.jar:` The jar file that was previously generated.<br>
`matrix.txt:` The tab-delimited mutation matrix as described above.<br>
`gene-sets.txt:` The tab-delimited gene sets file as described above.

Run mutex-de-novo using the below command.
```
java -jar mutex-de-novo.jar calculate matrix.txt gene-sets.txt output-directory 1000
```
Here, `output-directory` is the desired name for the output directory that will be generated during execution. `1000` is the randomization parameter that will be directly proportional to the run time. Use a small value, like `10`, for testing, and use a large value, like `10000` for actual analysis.
