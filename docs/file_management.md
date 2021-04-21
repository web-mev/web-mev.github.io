# File uploads

To upload your data...

**About file names**
Note that we try to be flexible about how files are named, but we generally advocate for "simple" names without spaces and/or special characters *other than* dashes ("-") or underscores ("_"). Special characters can cause unexpected issues when attempting to read files and/or use them for analyses.

To be clear, we permit files to have spaces within their names, but we ultimately convert the names within WebMeV to avoid any downstream problems. So do not be surprised if you see that your uploaded file has a *slightly* different name in the file manager.

Some pitfalls to avoid:
- Avoid files that start with numbers or other characters (e.g. "2A.tsv"). We will reject those outright.


# File "types" and extensions

To run analysis operations, we need to be able to parse the input files. To do that in a predictable and reproducible way, we need to know what types of files we are dealing with. Each analysis type expects files in a particular format and we can better control for errors if we assign "types" to each file and validate their format *before* attempting to use them in any analyses.

After uploading your file(s), the file manager will prompt you to select the file type. Upon selection, WebMeV will attempt to parse and validate your file to confirm that it can be used for downstream analyses. The file manager page has a guide to help understand each file type and what they mean, but you can also see these types [here](file_types.md#type_explanations). It is not feasible to validate large sequencing files, so certain file types bypass any pre-validation.

The file extension (e.g. "tsv" in "myFile.tsv") serves as a clue for the format of the data and how we attempt to parse it. We note that a file's format is different than its "type"; whereas the "type" refers to *what it represents* (e.g. an expression matrix, a BED file, etc.), the file's format refers to *how* the data is stored. An example is the extension of "csv" (`myFile.csv`), which signals that each column is separated/delimited with a comma. There is no "official" guide to this, but we follow conventional nomenclature. See [here](file_types.md#format_extensions) for a list of the formats/extensions we support. If the format does not match the extension (e.g. a tab-delimited file named as "myFile.csv"), this will *often* result in parsing errors and warnings, but this is not always the case. Thus, it is important that you preview your files (if available) in WebMeV to see that they have been interpreted correctly.

Finally, we make note that some common bioinformatics file types implicitly enforce a particular format and extension. An example is a BED-format file. These are required to be saved in a tab-delimited format and we further require that the file extension is set to "bed" (e.g. myBedFile.bed). Again, these formats are simply conventions to simplify bioinformatics workflows and communication, but we strictly enforce this within WebMeV.

Note that we attempt to provide useful instructions if your file does not validate, but we cannot anticipate the many things that can go wrong in formatting files. If you believe there is an error, please let us know!

# Previewing files

To check that your file was uploaded and parsed correctly, you can click on the "preview" icon (the eyeball) to see a portion of your file. If, for instance, your count matrix does not appear as a "sensible" looking table of numbers, then this is a clue that something has gone wrong. Generally, plain-text files are best, but we also accept Excel files. Note, however, that auto-formatting within Excel has been implicated in *many* errors in the bioinformatics field (https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-5-80)

# Removing files

To preserve the fidelity of your workspace, we do not allow you to delete files which are part of a workspace. To fully delete a file, you must first remove it from all workspaces. A list of the current workspaces is provided in the file manager table.

One important caveat of all this is that you **cannot delete a file which has been used for an analysis**. This includes *inputs* and *outputs* of analyses. For example, if you used a file containing differential expression results to execute a GSEA pathway analysis, you can't remove that input file. To do so would "break" your analysis flow since we would no longer have any record of a file required to fully recreate your analysis workflow. 

Hence, you can only delete files which have not been used in any workspaces and further are not attached to any workspaces.

# Renaming files

By default, many analyses will name your files automatically. If you wish to simplify these names, you may rename them in the file manager/editor. *It is up to you* to keep these names distinct and memorable. The analyses track these files by unique identifiers, so the human-assigned name is primarily used as a cue for the user.

Note that the file extension (e.g. "tsv" in "myfile.tsv") is often used as a "clue" for how to parse the file. Changing that extension can lead to unexpected behavior, so we advise against altering the extension. Generally, we try to catch these sorts of errors, but it is a challenge to anticipate the many things that can go wrong.
