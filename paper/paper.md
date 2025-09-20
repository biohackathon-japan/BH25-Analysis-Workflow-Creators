---
title: "DBCLS BioHackathon 2025 report: Creation and Publication Analytical Workflow of Creators' Interests"
title_short: 'BioHackJP25: Analytical Workflow Creators'
tags:
  - Workflows
  - Common Workflow Languages
  - Snakamake
authors:
  - name: Ryo Maemda
    orcid: 0009-0007-5830-6482
    affiliation: 1
  - name: Hyeokjin Kwon
    orcid: 0000-0003-1088-0446
    affiliation: 2
  - name: Pitiporn Noisagul
    orcid: 0000-0001-5351-9998
    affiliation: 3
  - name: Sora Yonezawa
    orcid: 0009-0004-1874-3117
    affiliation: 1
affiliations:
  - name: Hiroshima University
    ror: 03t78wx29
    index: 1
  - name: University of Potsdam
    ror: 03bnmw459
    index: 2
  - name: Chiang Mai University
    ror: 05m2fqn25
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

As part of the DBCLS BioHackathon 2025, we here report about creating and publishing analytical workflow. The analytical workflow is usually based on shell scripts. However, problems of reusability and environmental dependencies are sometimes occuring [@citation:Nahan2024]. Here, we aimed to this problems, the workflow based on workflow languages is developed.

# Results

## Metatranscriptomic analysis

We already published shell scripts on [GitHub](https://github.com/RyoMameda/workflow) for metatranscriptomic analysis. Although the software versions used in these shell scripts were listed in [the article](https://doi.org/10.3390/microorganisms13050995), managing their versions individually can be difficult for users. During DBCLS BioHackathon 2025, the published shell scripts were converted into CWL scripts, and 13 steps are now available on [github.com/RyoMameda/workflow_cwl/tree/main/Tools](https://github.com/RyoMameda/workflow_cwl/tree/main/Tools). All scripts work with Docker images.  

In addition, we combined the scripts into sub-workflows, each corresponding to different parts of the analysis pipeline: (i) construction of metagenomic contigs and protein prediction, (ii) mapping of metagenomic or metatranscriptomic reads to predicted protein-coding sequences (CDSs), and (iii) gene annotation of predicted CDSs. The workflows are also available on [github.com/RyoMameda/workflow_cwl/tree/main/Workflow](https://github.com/RyoMameda/workflow_cwl/tree/main/Workflow), and publication on [WorkflowHub](https://workflowhub.eu/workflows/1955) is in progress (DOI pending approval by the gatekeeper).  

We confirmed that the published CWL files work correctly with test datasets (metagenomic reads: [SRR27548858](https://www.ncbi.nlm.nih.gov/sra/?term=SRR27548858); metatranscriptomic reads: [SRR27548863](https://www.ncbi.nlm.nih.gov/sra/?term=SRR27548863), [SRR27548864](https://www.ncbi.nlm.nih.gov/sra/?term=SRR27548864), [SRR27548865](https://www.ncbi.nlm.nih.gov/sra/?term=SRR27548865)). The workflow image showing the constructed parts is provided below.

![Metatranscriptomic Analysis Workflow](./workflow_cwlization.png)


# Discussion

## Consideration to Software Quality

The official website of CWL provides a set of [recommended best practices](
https://www.commonwl.org/user_guide/topics/best-practices.html) to keep
in mind when writing a Common Workflow Language description. Appliying these
practices to tools and workflows can improve their software quality. Also,
[FAIR principles](https://www.go-fair.org/fair-principles/) are naturally
satisfied by following these practices. Even though more application of these
practices is generally better, not all are required.

We evaluated these practices in the perspective of life scientists, who are not
necessarily skillful software developers. We classified them into difficulty,
importance, and applicability categories. The evaluation is only for this
hackathon project, which time and resources are limited. Therefore, this may
not be generalized to other cases.

* D  - Difficulty (E:Easy, M:Medium, H:Hard)
* I  - Importance (L:Low, M:Medium, H:High)
* A  - Applicability (Y:Yes, M:Maybe, N:No)

| Practice Name |D|I|A| Description |
|------|:-:|:-:|:-:|-------------|
| Use class type for files | E | M | Y | Avoid using `type: string` for input/output files. Use `type: File` or `type: Directory` appropriately. |
| License Declaration | M | H | Y | Include a license field in all tools/workflows. Prefer licenses corresponding to SPDX identifier like Apache 2.0. |
| Author Attribution | E | M | Y | Include author and contributor information. Use unambiguous identifiers like ORCID. |
| Software Requirement (dep) | H | H | M | List dependencies using short names under `SoftwareRequirement`. |
| Software Requirement (ver) | H | H | M | Specify known working tool versions under `SoftwareRequirement`. |
| SciCrunch Identifiers (RRID) | H | M | M | Include SciCrunch identifiers for dependencies in `https://identifiers.org/rrid/RRID:SCR_NNNNNN` format. |
| Informative Identifiers | E | H | Y | Use descriptive names for inputs/outputs (e.g., `unaligned_sequences`) instead of generic ones (`fasta1`). |
| File Format Specification (EDAM) | H | H | N | Specify file formats using identifiers from EDAM (e.g., `format: edam:format_3489`). |
| Streaming Compatibility | E | L | M | Mark input/output files that are read/written in a streaming compatible way as `streamable: true`. |
| Single Operation Focus | E | H | Y | Each `CommandLineTool` should focus on a single operation. Avoid overcomplicating with unnecessary options. |
| Custom Type Definitions | E | H | Y | Define custom types in separate YAML files for reusability. |
| Top-Level Label & Doc | E | H | Y | Include a short label and, if useful, a longer doc for summarizing the tool/workflow. |
| Enum Types | E | L | M | Use `type: enum` for elements with a fixed list of valid values. |
| JavaScript Evaluation | M | M | M | Evaluate the use of JavaScript and consider first use of built-in File properties instead. |
| Peer Review | H | H | N | Have a colleague test and provide feedback on the tool description. |
| Subworkflow Feature Requirement | M | H | M | Utilize `SubworkflowFeatureRequirement` for modular workflows with abstractable components. |
| Container Conformity | M | M | M | Ensure software containers conform to the “Recommendations for the packaging and containerizing of bioinformatics software”. |

## Next Step

The main workflow of metatranscriptomic analysis could not be fully constructed during this BioHackathon. Further work is needed to complete its publication.

## Author Contribution
workflow creation, S.Y., P.N. and R.M.; validation, S.Y., P.N. and R.M.; critical commets, H.K. and S.Y.; writing, R.M., P.N. and H.K..

## References

