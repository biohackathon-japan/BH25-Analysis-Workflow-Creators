# Consideration to Software Quality

The official website of CWL provides a set of recommended good practices to keep
in mind when writing a Common Workflow Language description. Even though more
application of these practices is generally better, not all are required.

We evaluated these practices in the perspective of life scientists, who are not
necessarily skillful software developers. We classified them into difficulty,
importance, and applicability categories. The evaluation is only for this
hackathon project, which time and resources are limited. Therefore, this may
not be generalized to other cases.

* D  - Difficulty (E:Easy, M:Medium, H:Hard)
* I  - Importance (L:Low, M:Medium, H:High)
* A  - Applicability (Y:Yes, M:Maybe, N:No)

| Practice Name | D | I | A | Description |
|---------------|---|---|---|-------------|
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
