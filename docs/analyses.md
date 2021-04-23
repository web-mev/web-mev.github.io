# Executing analyses

By navigating to the "tools" tab in the workspace view, user can choose from among various analysis workflows which are grouped in a hierarchy of analysis "styles" (e.g. clustering, differential expression, etc.). Note that the analysis options presented do not reflect a particular or recommended analysis workflow-- they are simply all possible options, whether they make sense or not.

Indeed, some analysis methods may require other analyses to be run first, creating a dependency. For instance, a gene-set enrichment analysis requires an input file that contains a log fold-change and p-value for each gene. Of course, you *may* already have already have a file with the proper format, but it is more common to first run a differential expression analysis whose outputs will feed into the GSEA analysis. We typically construct our analyses so that it is relatively easy to pass the outputs of one analysis to the inputs of another. Thus, the outputs of certain analyses may be different than the "default" outputs you may get from running the same software on a different system/platform.

## Naming your analysis

Each analysis includes a "name" field, which allows you to quickly identify the analysis you have run. For instance, you may wish to run a similar analysis multiple times with different parameters(e.g. a k-means algorithm with a different number of clusters). The naming helps in identifying from among these executed analyses.


## About analysis inputs

All analyses will have one or more inputs which specify the data to use and potentially different parameters for executing the analysis. Often, these inputs are not comprehensive and advanced users or more complex use-cases may require the software to be run outside of WebMeV, such as directly executing a script using R/Bioconductor. However, we generally design the inputs to be flexible and powerful enough to be useful, yet "safe". That is, critical options are explained and occasionally protected to avoid making subtle but significant mistakes when specifying input parameters. It is not the goal of WebMeV to provide a "one stop shop" for all genomic analyses. Rather, we provide easy and accessible analyses with an eye towards covering the most common cases.

One common "pitfall" is that you may see an empty field for one of the required analysis inputs. For instance, you can't immediately run a differential gene expression analysis until you have 1) an expression count file and 2) groups of samples (observation sets) to contrast. Therefore, to run a differential expression analysis, one has to first define the two observation sets either by directly annotating the samples (i.e. with an "annotation file") or by executing a clustering analysis like PCA. Both of those methods allow you to create new observation sets which will be provided as inputs to the differential expression analysis. 

