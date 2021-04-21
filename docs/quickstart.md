# WebMeV Quickstart Guide

This quickstart is not meant to be comprehensive, but simply to provide a brief introduction for those who would like to get started as soon as possible. For more details, see the corresponding pages in the side menu.

## Login

To better understand WebMeV usage and provide better security, we require that users register with WebMeV. You can do this using either your own email address or by using a Google account. If you register via email, we will send you a link to validate your account.

## Uploading files

To run an analysis, you obviously need to have data to work with. You may either upload data from your local machine or by using our Dropbox uploader (Fig 1.)

If available, you can also create data from a number of public data sources we provide.

## Assigning file "types"

We need to know what types of files we are dealing with. Each analysis type expects files in a particular format and we can better control for errors if we assign "types" to each file and validate their format *before* using them in any analyses.

After uploading your file(s), the file manager will prompt you to select the file type. Upon selection, WebMeV will attempt to parse and validate your file to confirm that it can be used for downstream analyses. The file manager page has a guide to help understand each file type, but you can also see these types [here](file_types.md#xyz).

Note that we attempt to provide useful instructions if your file does not validate, but we cannot anticipate the many things that can go wrong in formatting files. If you believe there is an error, please let us know!

## Creating a workspace

To help with managing and organizing multiple types of analyses, we allow users to create "workspaces". All your analysis is performed within the context of a workspace. While you are not required to use more than one workspace, we encourage users to separate different types of analyses if they concern fundamentally different data. For example, one workspace might contain analyses related to an RNA-seq experiment performed on a cell-line while another workspace might contain analyses pertaining to an unrelated patient-derived xenograft mouse experiment. 

## Adding data to your workspace

Workspaces are initially empty. You can then "import" files to one or more workspaces to use in analysis. Even if you have uploaded all your files, you cannot use them until they have been validated and added to your workspace.

## Running analyses

Under the "tools" tab, you will find a list of available analyses grouped by their general "type". For instance, the differential expression menu contains several common packages for performing a differential expression analysis.

**Common pitfall- no options for a given input**

Each analysis input is restricted to an expected type and the available options are based on that expectation. For example, if we are attempting to run a differential expression analysis, one required input is a "count matrix" (also called an expression matrix). Accordingly, the options for such an input will be populated with a list of files in your workspace which have a "file type" appropriate for this input. 

If you do not see any input options for a given field, you likely have to perform another action first. For instance, to execute a pathway analysis (e.g. GSEA), you first need an ordered list of genes (typically ranked by a measure of their differential expression). If you attempt to run a GSEA analysis right away, you will most likely notice that the dropdown menu for the input file is empty. Hence, you either need to first upload a file with the proper format *or* (most likely) run a differential expression analysis first.

Similarly, some analyses (such as differential expression analysis) require you to provide two groups of samples/observations to compare. Therefore, you must first create these two groups, either through a clustering analysis or by annotating your samples (e.g. telling WebMeV which samples are "experimental" and which should be considered as a "control" group).

## Viewing results

After requesting an analysis, your job will be queued and executed in a (hopefully!) timely manner. Depending on the size of your dataset and the requested analysis, this can be relatively quick (e.g. under 10 seconds) or take significantly longer (minutes, hours).

WebMeV will periodically check the state of your job and report back with the status (i.e. running, finishing, preparing visualization). Unfortunately, we cannot provide fine-grained details on the progress (such as "75% complete").

Once the job is complete, you can view the results by finding your "executed analysis" in the results menu. Most result pages will provide interactive visualizations or plots that will allow you to define interesting groups of samples, genes, and perform other actions. Most figures can be exported for download.
