---
title: "DBCLS BioHackathon 2025 report: Creation and Publication Analytical Workflow of Creators' Interests"
title_short: 'BioHackJP25: Analytical Workflow Creators'
tags:
  - Workflows
  - Common Workflow Languages
  - Snakamake
authors:
  - name: Ryo Maemda
    affiliation: 1
  - name: Hyeokjin Kwon
    orcid: 0000-0003-1088-0446 # please confirm
    affiliation: 2
  - name: Pitiporn Noisagul
    orcid: 0000-0001-5351-9998 # please confirm
    affiliation: 3
  - name: Sora Yonezawa
    orcid: 0009-0004-1874-3117 # please confirm
    affiliation: 1
affiliations:
  - name: Hiroshima University
    ror: 03t78wx29
    index: 1
  - name: University of Potsdam # please confirm
    ror: 03bnmw459 # please confirm
    index: 2
  - name: Chiang Mai University # please confirm
    ror: 05m2fqn25 # please confirm
    index: 3
date: 20 September 2025
cito-bibliography: paper.bib
event: BH25JP
biohackathon_name: "DBCLS BioHackathon 2025"
biohackathon_url:   "https://2025.biohackathon.org/"
biohackathon_location: "Mie, Japan, 2025"
group: Analytical Workflow Creators
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackathon-japan/BH25-Analysis-Workflow-Creators
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Ryo Mameda, Hyeokjin Kwon, Pitiporn Noisagul, Sora Yonezawa
---

# Introduction

As part of the DBCLS BioHackathon 2025, we here report about creating and publishing analytical workflow. The analytical workflow is usually based on shell scripts. However, problems of reusability and environmental dependencies are sometimes occuring. Here, we aimed to this problems, the workflow based on workflow languages is developed.

# Results

## Metatranscriptomic analysis

We already published shell script on [github](https://github.com/RyoMameda/workflow) for metatranscriptomic analysis. Although the software version using this shell scripts were listed in [the article](https://doi.org/10.3390/microorganisms13050995), managing its version on user's own are difficult. In DBCLS BioHackathon 2025, published shell scripts were converted into CWL scripts, and 13 steps of the scripts are now avilable on [github.com/RyoMameda/workflow_cwl/tree/main/Tools](https://github.com/RyoMameda/workflow_cwl/tree/main/Tools). Also, we combined scripts into sub-workflow which composes each pert of steps; construction of metagenomic contigs and prediction of proteins, mapping metagenomic or metatranscriptomic reads to predicted protein coding sequences (CDS), and gene annotation of predicted CDS. The workflows are also available on [github.com/RyoMameda/workflow_cwl/tree/main/Worlkflow](https://github.com/RyoMameda/workflow_cwl/tree/main/Worlkflow). 

## Author information

Information about the authors is given in the [YAML](https://en.wikipedia.org/wiki/YAML) format at the top of this template.
For authors you provide their names, their affiliations, and ideally their [ORCID](https://orcid.org/)
identifier. For affiliations, the [Research Organization Registry](https://ror.org/) (ROR) identifier can be given.
For example, this is the author information for this template:

```yaml
authors:
  - name: Ryo Maemda
    affiliation: 1
  - name: Hyeokjin Kwon
    orcid: 0000-0003-1088-0446 # please confirm
    affiliation: 2
  - name: Pitiporn Noisagul
    orcid: 0000-0001-5351-9998 # please confirm
    affiliation: 3
  - name: Sora Yonezawa
    orcid: 0009-0004-1874-3117 # please confirm
    affiliation: 1
affiliations:
  - name: Hiroshima University
    ror: 03t78wx29
    index: 1
  - name: University of Potsdam # please confirm
    ror: 03bnmw459 # please confirm
    index: 2
  - name: Chiang Mai University # please confirm
    ror: 05m2fqn25 # please confirm
    index: 3
```

# Formatting

This document use Markdown and you can look at [this tutorial](https://www.markdowntutorial.com/).

## Subsection level 2

Please keep sections to a maximum of only two levels.

## Tables

Tables can be added in the following way, though alternatives are possible:

```markdown
Table: Note that table caption is automatically numbered and should be
given before the table itself.

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |
```

This gives:

Table: Note that table caption is automatically numbered and should be
given before the table itself.

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

## Figures

A figure is added with:

```markdown
![Caption for BioHackrXiv logo figure](./biohackrxiv.png)
```

This gives:

![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

Figures can be scaled by adding the width or height to the Markdown like this:

```markdown
![Caption for BioHackrXiv logo figure](./biohackrxiv.png){ width=50px }
```

# Other main section on your manuscript level 1

Lists can be added with:

1. Item 1
2. Item 2

# Citation Typing Ontology annotation

You can use [CiTO](http://purl.org/spar/cito/2018-02-12) annotations, as explained in [this BioHackathon Europe 2021 write up](https://raw.githubusercontent.com/biohackrxiv/bhxiv-metadata/main/doc/elixir_biohackathon2021/paper.md) and [this CiTO Pilot](https://www.biomedcentral.com/collections/cito).
Using this template, you can cite an article and indicate _why_ you cite that article, for instance DisGeNET-RDF [@citesAsAuthority:Queralt2016].

The syntax in Markdown is as follows: a single intention annotation looks like
`[@usesMethodIn:Krewinkel2017]`; two or more intentions are separated
with colons, like `[@extends:discusses:Nielsen2017Scholia]`. When you cite two
different articles, you use this syntax: `[@citesAsDataSource:Ammar2022ETL; @citesAsDataSource:Arend2022BioHackEU22]`.

Possible CiTO typing annotation include:

* citesAsDataSource: when you point the reader to a source of data which may explain a claim
* usesDataFrom: when you reuse somehow (and elaborate on) the data in the cited entity
* usesMethodIn
* citesAsAuthority
* citesAsEvidence
* citesAsPotentialSolution
* citesAsRecommendedReading
* citesAsRelated
* citesAsSourceDocument
* citesForInformation
* confirms
* documents
* providesDataFor
* obtainsSupportFrom
* discusses
* extends
* agreesWith
* disagreesWith
* updates
* citation: generic citation


# Results


# Discussion

...

## Acknowledgements

...

## References
