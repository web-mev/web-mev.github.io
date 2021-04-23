# Ensuring reproducible workflows

WebMeV was designed to be a platform that easily supports reproducibility of analysis workflows. Each type of analysis used in WebMeV is supported by a GitHub repository that has *all* of the necessary software *and* infrastructure code. These can be found at the WebMeV GitHub project: [https://github.com/web-mev](https://github.com/web-mev). For example, the DESeq2 differential expression process can be found at [https://github.com/web-mev/deseq2](https://github.com/web-mev/deseq2). Depending on the computational resources needed for a particular workflow, the jobs can be executed in one of several manners.

This architecture choice enables WebMeV users to easily reference the repository which will be able to completely reproduce every aspect of a computational analysis/process *independent of WebMeV*. This makes the analysis outputs of workflows amenable for use in publications where authors can simply reference the appropriate repository. Additionally, the same workflows can be recalled at any time if further data is acquired. 

## The local Docker-based job runner

Computational environments (operating system, libraries, and software installations) are controlled through containerization technologies such as Docker. Docker images are saved to a public Dockerhub repository which allows users to simply pull the exact version of the container image. The software used to run the analysis is loaded into the container and one only needs to provide the same inputs to ensure a completely reproducible analysis workflow. These worklows can be executed on any system with Docker installed.

## The remote Cromwell-based job runner.

Workflows that require more significant computational time or resources are run via the remote Cromwell job runner. While not consequential to the WebMeV user, Cromwell handles starting, managing, and stopping new computational nodes (cloud-based machines). Note that all the computation still happens in Docker containers, but these are simply run on different machines than the WebMeV server. 

The workflows themselves are prescribed using Workflow Definition Language (WDL) which dictates the various steps of a potentially complex, multi-step analysis process. While not as straightforward as a local, Docker-based process, all the elements of the process are there for complete reproducibility. One has to either "extract" the individual steps or setup their own Cromwell server. Regardless, all workflow elements are self-contained in the repository.

