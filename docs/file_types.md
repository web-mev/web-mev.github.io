# File types and formats

<a name="type_explanations">
## File types
</a>

As mentioned elsewhere, file *types* dictate what the file represents, *not* how it's stored (e.g. comma-separated values, tab-separated values). Each of these file types can be stored in multiple formats.

###Table types

- A **numeric table** is a table of where all the entries are numbers except the first column (which names the rows) and the first line (which gives the column names). The cell at the first row and column may be left blank (as shown below). Example:

|       | Sample_A | Sample_B | ... | Sample_T |
|-------|---------|---------|-----|---------|
| geneA | 2.1       | 5.2       | ... | 54      |
| geneB | 101     | 102     | ... | 8.3       |
| geneC  | 56      | 51.1      | ... | 56      |

- An **integer table** is a table of where all the entries are integers *except* the first column (which names the rows) and the first line (which gives the column names). The cell at the first row and column may be left blank as shown below. Example:

|       | Sample_A | Sample_B | ... | Sample_T |
|-------|---------|---------|-----|---------|
| geneA | 2       | 5       | ... | 54      |
| geneB | 101     | 102     | ... | 8       |
| geneC   | 56      | 51      | ... | 56      |

- A **RNA-seq count matrix** is a table of where all the entries are integers except the first column (which names the rows) and the first line (which gives the column names). The cell at the first row and column may be left blank. *This type is identical to the integer matrix above, but we have this type so it's more obvious what the data represents.* 


- An **expression matrix** is a table where all the entries are numbers except the first column (which names the rows) and the first line (which gives the column names). The cell at the first row and column may be left blank. This is the same as the *numeric matrix* listed above, but we have this type so it's more obvious what the data represents. Numeric tables can hold many types of data, but the intention of the *expression matrix* is to hold data about gene/transcript expression.


- A **feature table** describes or annotates the "features" of your data. In the genomics context, one example of a feature is a gene. Therefore, you could use this table to give additional information about each gene, such as alternative symbols, oncogene status, or similar. Each *row* contains information about a single gene and each *column* gives a different item of information about that gene. Note, however, that this concept is completely general and not restricted to information about genes or transcripts. Another example of a feature table is the output of a differential gene expression analysis. In that context, each *row* holds information
about the statistics of differential expression, such as the log-fold change and p-value.. 

|       | mean | logFC | ... | pvalue |
|-------|---------|---------|-----|---------|
| geneA | 200.2       | 0.2       | ... | 0.32      |
| geneB | 1001.1     | 5.2     | ... | 0.0001       |
| geneC   | 10.2      | -3.2      | ... | 0.03      |

- An **annotation table** is used to add metadata to your samples. The first column has the sample name and the remaining columns contain metadata about each sample (for instance, experimental group, treatment, or similar. 

|       | phenotype | batch |
|-------|---------|---------|
| sample_A | WT      | 1      | 
| sample_B | KO     | 1     | 
| sampleC   | WT      | 2      |

- A **BED file** is a three-column BED-format file which is used to give genomic coordinates or regions. These can represent regions of interest (e.g. transcription-factor binding sites) or simply the genomic coordinates of a gene. "Expanded" BED formats can have additional columns and those *are permitted*. However, at this time, we only read the first three columns which gives the chromosome/contig, the start position, and the end position. *BED-format* does not expect a column header.

| | | |
|------|--------|--------|
| chr1 | 2000       | 2305       |
| chr2 | 4000       | 4502       |
| chrX | 200       | 205       |


### Sequence-based formats

Most often, sequence-based files are reserved for the larger, more computationally intensive aspects of WebMeV. Unfortunately, due to their size, dynamic interaction and data exploration with such files is not feasible and hence most users will not perform analyses or workflows that involve raw sequence data. However, since we work with these types of files, we admit them to be uploaded to WebMeV. *However,* we do not provide error-checking or validation on these files due to their size and overhead.

- **Fasta** represents a FASTA-format sequence file. [https://en.wikipedia.org/wiki/FASTA_format](https://en.wikipedia.org/wiki/FASTA_format)

- **Fastq** represents a FASTQ-format sequence files. The is the most common format used for sequencing experiments. Sequencing providers will typically deliver FASTQ-format files in addition to other files. More info: [https://en.wikipedia.org/wiki/FASTQ_format](https://en.wikipedia.org/wiki/FASTQ_format)

- An **alignment (SAM/BAM)** represents a BAM- or SAM-format aligned sequence file. Typically the output of an alignment process such as an alignment of sequencing reads against a reference genome/transcriptome. Other formats exist, but this is the most common format you will see. Full file specification: [http://samtools.sourceforge.net/SAM1.pdf](http://samtools.sourceforge.net/SAM1.pdf)


### JSON format

JSON-format file is used for data that is not easily represented in a table-based format. Typically not a file you will work with directly, but is a file format that 
is convenient for use *within* WebMeV. Can hold multiple data types and represent arbitrary relationships. [https://en.wikipedia.org/wiki/JSON](https://en.wikipedia.org/wiki/JSON)


### General Format

A general file is typically used to denote an unspecified type. This is rarely used as it represents data that cannot be predictably validated. It is quite rare that an analysis or workflow will take arbitrary data as input, so you will not see this format used very often.


<a name="format_extensions">
## Extensions and file formats
</a>

As mentioned above, the file *types* indicate what the data represents (e.g. gene expression), but the file *format* indicates how it is stored. The file "extension" (e.g. the "csv" part of "myFile.csv") is used as a signal or cue for the storage format and how it should be parsed when being read. However, this is merely a common practice/convention and there is nothing that prevents you from saving files in a format that is incompatible with the file extension we expect. If this happens (e.g. a comma-delimited file stored as "myfile.tsv"), then an error will typically be raised when parsing. For instance, if a CSV file is saved with a "tsv" extension then the software will scan each line expecting to split your columns based on "tab" characters. Since it will not find any tab characters in a comma-delimited file, it will fail to split the lines and it will parse the file as if it contains a single column of "junk". As a result, the file parsing will likely fail and you will be alerted to this.

For table-based data, we permit several storage formats including CSV (comma-separated values), TSV (tab-separated values), and Excel-based formats (xls/xlsx). There are other table-based formats for file types which are conventional/common types in the bioinformatics field. The file extensions are case-insensitive, so "tsv", "Tsv", "TSV", etc. are all acceptable. We currently accept:

- Tab-delimited formats: "tsv"

- Comma-delimited formats: "csv"

- Excel formats: "xls", "xlsx". 

Note that Excel format can have the potential to "corrupt" some gene names. For example, the "Sept1" gene is typically interpreted and replaced as "September 1" (a date) if you import genomic data into Excel.

For BED and VCF (for variant data: [https://en.wikipedia.org/wiki/Variant_Call_Format](https://en.wikipedia.org/wiki/Variant_Call_Format) ) formats, we expect their canonical/common extensions of "bed" or "vcf", respectively.