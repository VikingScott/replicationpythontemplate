---
title: A template for Quantitative Finance Research Replication 
authors:
  - name: First Author
    email: youremail@illinois.edu
    department: Financial Engineering
    affiliation: University of Illinois
  - name: Second Author (optional, continue for third, fourth, etc)
    email: youremail@illinois.edu
    department: Financial Engineering
    affiliation: University of Illinois
abstract: |
  Enter the text of your abstract here. Consider your précis from the summary
  and add 1-3 sentences about your conclusions.  6-10 sentences.
keywords:
  - trading strategies
  - quantitative analysis
  - machine learning
  - these are optional and can be removed
nocite: |
  @PetersonReplication, @jabref, @Rmarkdown, @Peterson2015, @jupyterbook, @jupytext
bibliography: references.bib
bibtex_bibfiles: references.bib
bibtex_default_style: 'alpha'
copyright: Copyright CC-BY ©2023 
output: rticles::arxiv_article 
sphinx:
  config:
    bibtex_reference_style: author_year
    bibtex_bibfiles: "your_reference_file.bib"
jupyter:
  jupytext:
    cell_metadata_filter: -all
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.14.4
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

# Introduction

<!-- This is a template for Research Replication projects following the process -->
<!-- outlined in @PetersonReplication.  This template was originally created using Rmarkdown [@Rmarkdown]. -->
<!-- The sample bibliography file was generated via @jabref . The additional sections -->
<!-- in this template will be inserted as comments, and will not be included in the -->
<!-- compiled output. This version of the template has been converted to a Jupyter Notebooks with @jupyterbook and @jupytext -->
<!-- note that I (still) feel that RMarkdown with python code blocks is easier to work in and produces more professional output. --> 

{cite}`jupyterbook`

{cite}`jupytext`



# Paper Summary

<!-- Start with a single paragraph in précis form. -->
<!-- See @PetersonReplication p. 1-2 for details. -->
<!-- Complete this section with paragraphs describing each major point in the paper. -->
<!-- The entire summary will be 4-10 paragraphs. -->


# Hypothesis Overview

<!-- Formally detail the paper's key hypotheses. -->
<!-- See @PetersonReplication p. 2 for details. -->


# Literature Review

<!-- Write your literature review. See @PetersonReplication p. 2-4 for details. This -->
<!-- section must include paragraphs at least for the 3-5 key references for the -->
<!-- paper to be replicated, similar work, implementation references, more recent -->
<!-- references where available, and any references with attempt to refute the -->
<!-- hypotheses of the replicated work.  A full literature review may contain 20-50 -->
<!-- references.  Not all will be covered in the same level of detail.  Important -->
<!-- references probably warrant an entire paragraph, but similar work can probably -->
<!-- be covered together in 1-2 paragraphs for multiple related works. -->


# Replication

<!-- Now we move on to the actual replication.  The sections included here are all -->
<!-- necessary, but the may not be sufficient.  Add additional sections and sub-sections -->
<!-- as required to describe your work and make your analytical case. -->

## Data

<!-- Describe the approach that the replication is taking to Data. -->
<!-- See @PetersonReplication p. 4-5 for details. -->
<!-- Describe both the data used in the original paper, and the data you are using -->
<!-- for replication.  For your replicated data, include detailed descriptions of -->
<!-- obtaining, parsing, and cleaning the data to prepare it for use.  Describe data -->
<!-- quality issues. -->


## Replication of Key Analytical Techniques

<!-- Model the Key Analytical Techniques from the paper to be replicated. -->
<!-- See @PetersonReplication p. 5-6 for details. -->
<!-- This section will vary significantly based on the paper being replicated. -->
<!-- Describe your process as you work, documenting the steps you are taking, -->
<!-- referencing any libraries, websites, or third party code that you use as part of -->
<!-- your replication, and the decree to which your replication agrees or disagrees -->
<!-- with the source material. Be sure to include summary statistics used in the -->
<!-- original paper, as well as any additional summary statistics that you feel are -->
<!-- relevant for checking the quality of your replication. -->

### Technique 1

### Technique 2

### Technique 3


## Hypothesis Tests

<!-- After replicating the initial work, it is time to evaluate the hypotheses of -->
<!-- the replicated work. Those hypotheses were identified above, before you started -->
<!-- replication. Describe, in detail, the statistical tests you perform to refute or -->
<!-- validate the hypotheses in the replicated work.  This should go beyond any explicit -->
<!-- tests performed in the original paper. -->


## Extended Analysis

<!-- Extend the analysis with more (recent) data or additional asset classes, and/or -->
<!-- replicate similar or extended techniques and compare them to the original paper's methods. -->
<!-- See @PetersonReplication p. 6-7 for details. -->


## Overfitting

<!-- Analyze the likelihood that the original paper is overfit.  Include data -->
<!-- considerations, experiment design, model assumptions, parameterization, and -->
<!-- biases, out of sample results, etc.  Assess how changes to these affects -->
<!-- results, and produce an opinion on whether and how the original work is overfit, -->
<!-- as well as what might be doable to reduce the degree of overfitting, and whether -->
<!-- the main results would hold if the level of overfitting were reduced. -->


# Future Work

<!-- What additional work on this topic should be performed in the future, if this -->
<!-- project were to be picked up again or continued? -->


# Conclusions

<!-- Summarize the project and describe your conclusions.  This sections can -->
<!-- range from 1-2 paragraphs to 1-2 pages. -->

\newpage 

![CC-BY](cc_by_88x31.png)


# References

```{bibliography}
```


