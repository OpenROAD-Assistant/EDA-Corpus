# EDA Corpus
This is a GitHub repository that has the dataset for EDA LLM research. In particular,  the datapoints are tailored to [OpenROAD](https://github.com/The-OpenROAD-Project/OpenROAD) and [OpenROAD-flow-scripts](https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts). The dataset contains both prompt-script and question-answer format data for OpenROAD to improve user productivity and 

## Background
Recent works have shown that large language models (LLMs) have tremendous potential in the chip design area in terms of writing code/script for hardware description language (HDL) or electronic design automation (EDA) flow. However, many of these works rely on data which are not publicly available and/or not permissively licensed for use in LLM training and distribution, especially in the EDA domain. To foster research in LLM-assisted physical design, we introduce EDA Corpus, a curated dataset for physical design automation tasks. EDA Corpus is based on OpenROAD, a widely utilized open-source EDA tool for automated place and route tasks. Leveraging OpenROAD mitigates obstacles associated with proprietary EDA tools, enabling the public release of our dataset and facilitating its use with LLMs without licensing constraints.

## Dataset Description
EDA Corpus consists of two types of data: (1) Question-answer pairs and (2) Prompt-script pairs 

### Question-answer pairs:
  - The question-answer dataset contains pairs of question prompts and prose answers which are collected from the OpenROAD GitHub issues, discussions, and documentation. The datapoints are categorized into three categories: OpenROAD general, OpenROAD tool, and OpenROAD flow.
  - For each category, we provide a CSV file version and a Microsoft Excel version for different usecase scenarios.
  - Each datapoint contains a question and a corresponding answer. For example:


**Question:**

***What does the SKIP_PIN_SWAP variable in Clock Tree Synthesis indicate?***

**Answer:**

***Do not use pin swapping as a transform to fix timing violations (default: use pin swapping)***



### Prompt-script pairs:
  - The prompt-script dataset is comprised of prompts and OpenROAD Python code pairs. While Tcl is the normal interface for OpenROAD, leveraging Python allows the reuse of pretrained LLMs for Python code generation. It is worth noting that there are currently no publicly available LLMs trained specifically for generating Tcl scripts, hence the focus on Python-based scripts. Within our prompt-script dataset, data points are categorized into two main types: flow-based scripts and database (DB)-based scripts.
  - We provide a CSV file format and a Microsoft Excel file format as well for the prompt-script dataset.
  - Each datapoint contains a prompt and a corresponding python script. For example:


**Prompt:**

***Show me how I can read a Verilog file into OpenROAD.***

**Script:**

```python
from openroad import Tech, Design
from pathlib import Path

tech = Tech()
# Make sure you have .lef files read into OpenROAD DB
design = Design(tech)

designDir = Path(""design_path"")
design_file_name = ""design_filename""
design_top_module_name = ""design_top_module_name""
verilogFile = designDir/str(design_file_name + "".v"")
design.readVerilog(""verilogFile"")
design.link(design_top_module_name)"}
```


