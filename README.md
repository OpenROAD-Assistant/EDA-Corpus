# EDA Corpus
EDA Corpus is a data corpus for Electronic Design Automation (EDA) Large Language Model (LLM) research. In particular, the datapoints are tailored to [OpenROAD](https://github.com/The-OpenROAD-Project/OpenROAD) and [OpenROAD-flow-scripts](https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts). The corpus contains datasets for both question-answering and prompt-scripting for OpenROAD to improve user productivity.

## Background
Recent works have shown that LLMs have tremendous potential in the chip design area in terms of writing code/script for hardware description language (HDL) or electronic design automation (EDA) flow. However, many of these works rely on data which are not publicly available and/or not permissively licensed for use in LLM training and distribution, especially in the EDA domain. To foster research in LLM-assisted physical design, we introduce EDA Corpus, a curated dataset for physical design automation tasks. EDA Corpus is based on OpenROAD, a widely utilized open-source EDA tool for automated place and route tasks. Leveraging OpenROAD mitigates obstacles associated with proprietary EDA tools, enabling the public release of our dataset and facilitating its use with LLMs without licensing constraints.

## Dataset Description
EDA Corpus consists of two types of data: (1) question-answer pairs and (2) prompt-script pairs

### Question-answer (QA) dataset
  - Contains pairs of question prompts and prose answers which are collected from The OpenROAD Project's GitHub issues, discussions, and documentation
  - Datapoints are categorized into three categories: OpenROAD general, OpenROAD tool, and OpenROAD flow
  - CSV file format and Microsoft Excel file format provided

An example question-answer pair:
**Question:**

***What does the SKIP_PIN_SWAP variable in Clock Tree Synthesis indicate?***

**Answer:**

***Do not use pin swapping as a transform to fix timing violations (default: use pin swapping)***

### Prompt-script (PS) dataset
  - Contains pairs of scripting prompts and OpenROAD Python scripts
  - Data points are categorized into two three categories: flow scripts and database (DB) scripts
  - CSV file format and Microsoft Excel file format provided

While Tcl is the normal interface for OpenROAD, leveraging Python allows the reuse of pretrained LLMs for Python code generation. It is worth noting that Python code examples are significantly more prevalent, hence the focus on Python-based scripts.

An example prompt-script pair:
**Prompt:**

***Show me how I can read a Verilog file into OpenROAD.***

**Script:**

```python
from openroad import Tech, Design
from pathlib import Path

tech = Tech()
# Make sure you have .lef files read into OpenROAD DB
design = Design(tech)

designDir = Path("design_path")
design_file_name = "design_filename"
design_top_module_name = "design_top_module_name"
verilogFile = designDir/str(design_file_name + ".v")
design.readVerilog("verilogFile")
design.link(design_top_module_name)
```

# Citing This Work

If you use this corpus in your work, please use the following citation:
```
@inproceedingsV{wu2024eda,
  title        = {EDA Corpus: A Large Language Model Dataset for Enhanced Interaction with OpenROAD},
  author       = {Wu, Bing-Yue and Sharma, Utsav and Kankipati, Sai Rahul Dhanvi and Yadav, Ajay and George, Bintu Kappil and Guntupalli, Sai Ritish and Rovinski, Austin and Chhabria, Vidya A.},
  booktitle    = {The First IEEE International Workshop on LLM-Aided Design (LAD'24)},
  month        = {June},
  year         = {2024},
  organization = {IEEE},
  address      = {New York, NY}
}
```

## Taxonomy
The question-answer and prompt-script data should be individually referred to as "datasets". The two dataset combined should be referred to as a "corpus".

Citations to this work can be mentioned by `corpusName-datasetName-version`:

| **Data**                     | **Name**           |
|------------------------------|--------------------|
| All of EDA Corpus            | `eda-corpus-v1`    |
| Only question-answer dataset | `eda-corpus-qa-v1` |
| Only prompt-script dataset   | `eda-corpus-ps-v1` |

Additionally, you can mention whether you use the **augmented** or **non-augmented** versions. For example, "We train on the augmented eda-corpus-ps-v1 dataset."
