Tools for the analysis of protein correlation profiling data
=================================================================

* [Shiny app](#shiny-app)
* [Statistical analyses](#statistical-analyses)
* [Other tasks](#misc-tasks)
* [Resources and references](#Resources-and-references) (Markdown, Docker, Git, ...)

--------------------------------------

The goal is to create tools to handle data that is generated by **protein correlation profiling** (PCP) data.

At the moment, this entails **two main tasks** (and several things that are difficult to categorize):

>1. A [Shiny app](#shiny-app) for data wrangling and visual exploration
>2. Developing functions for [statistical analyses](#statistical-analyses)

The `DepLab` package that has been developed by the Applied Bioinformatics Core at Weill Cornell Medicine will serve as a starting point.

## General data workflow for PCP data

![](https://github.com/NCBI-Hackathons/Proteomic_Correlation_Shiny/blob/master/images/PCPdata_workflow.png)

## Shiny app

The `DepLab` package contains a shiny app that allows for:

* upload of PCP data into a data base
* smoothening of the data
* visual exploration of individual protein profiles

More details can be found in the [manual](https://github.com/NCBI-Hackathons/Proteomic_Correlation_Shiny/blob/master/DepLab_manual/PCP_manual.pdf).

__The Hackathon Shiny App can be found [here](https://github.com/NCBI-Hackathons/Proteomic_Correlation_Shiny/tree/master/demo-shiny).__

It includes functions and examples for the following cool tasks:

- [x] interactive graphics
- [x] additional plots, e.g. histograms of QC values to allow for user-defined filtering [QC should definitely be part of the development]
- [x] log files once a user saves a plot to reload the exact same settings in the future
- [x] connection to String, the database of protein interactions


## Statistical analyses

- [ ] Identify proteins whose **profiles change** between two (or more) conditions (taking the variability based on replicates into account)

      * some sort of ranking
      * statistical significance?

- [ ] Identify proteins that **co-elute**/change the same/different way(s), i.e.,

      * that may be in the same complex
      * that may change the complex membership depending on the condition
      * ...

## Misc tasks

- [x] An R package containing the **example data** that we are going to work with
- [ ] **Quality control**, both visually and perhaps even cooking up some sort of score?

      - per protein
      - reproducibility between replicates
      - how well are certain "gold-standard" complexes revocered?

- [ ] Updating the manual, making a **proper vignette/tutorial** (there should be one for every package at least)
- [ ] Implementing proper **tests** for the functions, e.g. using Hadley's `testthat` package

## Resources and references

### PCP data

* __MaxQuant__ - the software we rely on to produce our primary data
     - [Brief description @ MPI website](http://www.biochem.mpg.de/5111795/maxquant)
     - [GUI user guide with some info about the output](http://greproteomics.lifesci.dundee.ac.uk/webpage%20front%20page/dreamweaver%20webpage/maxquant%20how%20to.pdf)
     - [Andromeda paper](http://pubs.acs.org/doi/pdf/10.1021/pr101065j)
     - [How to interpret MQ output](http://oisb-1.med.uottawa.ca/prc/interpret.html)
     - [Nat. Methods MQ Practical Guide](https://www.researchgate.net/publication/24284062_A_practical_guide_to_the_MaxQuant_computational_platform_for_SILAC-based_quantitative_proteomics) --> mostly **Box 2**
     - [Quantitative Proteome Profiling, Methods in Mol Biol](https://www.researchgate.net/publication/225186303_In_Vivo_Quantitative_Proteome_Profiling_Planning_and_Evaluation_of_SILAC_Experiments) --> **Section 3.4** Data Analysis Using MaxQuant contains many details about the MQ output (ignore the SILAC details)
     - [Presentation with lots of MQ details](http://www.bspr.org/sites/default/files/bspr11pdf/BSPR2011_Cox.pdf)
 * __Protein correlation profiling__
     - Foster Lab pubs: 
          - [Kristensen et al, 2012, initial description of the method and analysis](https://www.embl.de/predoccourse/2015/modules/proteomics/journal_club/MS_B.pdf)
          - [Kristensen et al., 2014, Protocol](https://www.researchgate.net/publication/264246047_Protein_Correlation_Profiling-SILAC_to_Study_Protein-Protein_Interactions)
          - [Scott et al., 2015, Computational Workflow](https://www.researchgate.net/publication/269184078_Development_of_a_computational_framework_for_the_analysis_of_protein_correlation_profiling_and_spatial_proteomics_experiments)

### Git

* [15 minute interactive Git tutorial](https://try.github.io/)
* Longish [Data camp course for using Git via RStudio]()
    - [briefer alternative](https://nicercode.github.io/git/rstudio.html)
    - to set up Git/RStudio, see [Hadley Wickham's guide](http://r-pkgs.had.co.nz/git.html)
* Brief summary of git lingo and commands with a focus on [team work](https://docs.google.com/presentation/d/179ACErhWwCOxKKCsgo-H2Xc1cPKBwQhVIbHnDIIu4Tw/edit#slide=id.p)

### Docker

* [How to use/run a Docker image](https://github.com/NCBI-Hackathons/Cancer_Epitopes_CSHL/blob/master/doc/Docker.md)

### Markdown cheat sheets

* [daring fireball](https://daringfireball.net/projects/markdown/basics)
* [Adam P](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
* [Squarespace](https://support.squarespace.com/hc/en-us/articles/206543587-Markdown-cheat-sheet)

### Making diagrams, flow charts etc.

* [draw.io](https://www.draw.io/)

### Creating R packages

* [Brief intro](https://github.com/abcdbug/dbug/blob/master/R_Packages/Creating_R_packages.pdf)
* The very long and detailed [R page](https://cran.r-project.org/doc/manuals/R-exts.html) (I used it mostly as a reference for the formating of the documentation)

### R packages that we will rely on

This is based on the packages currently used in DepLab. This is, of course, subject to change!

* R package creation and maintenance
  - `devtools`
  - `roxygen2`
  - `testthat`
* data wrangling
  - `data.table`
  - `dplyr`
* visualization
  - `ggplot2`
