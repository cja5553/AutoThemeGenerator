AutoThemeGenerator is a package that allows you to perform thematic analysis in qualitative studies using OpenAI's GPT models. 


[![Documentation](https://img.shields.io/badge/Documentation-v0.2.1-orange)](https://cja5553.github.io/ReadTheDocs_AutoThemeGenerator/) [![pypi package](https://img.shields.io/badge/pypi_package-v0.2.1-brightgreen)](https://pypi.org/project/AutoThemeGenerator/) [![GitHub Source Code](https://img.shields.io/badge/github_source_code-source_code?logo=github&color=green)](https://github.com/cja5553/AutoThemeGenerator) [![Colab Example](https://img.shields.io/badge/-Colab_Example-grey?logo=google&logoColor=F9AB00)](https://colab.research.google.com/drive/1BoAI-QNL-yL8j8hUJ3K8cJkbyp4spoQ3)


## User inputs
Users are only required to specify the folder location where their interview transcripts are stored. Accepted formats of transcripts include `PDF`, `.docx`, and `.txt` (prefered). `AutoThemeGenerator` assumes that each document is a transcript of one interviewed participant.

## Requirements
### Required packages
To use `AutoThemeGenerator`, you are required to have the following packages installed:  
- `openai`  
- `docx`    
- `tqdm`    
- `nltk`    
- `nltk.tokenize` (submodule of `nltk`)   
- `python-docx`  
- `textract`  
- `requests`  
- `zipfile` (Python standard library)   
- `shutil`  (Python standard library)  
- `json`  (Python standard library)  
- `pprint`  (Python standard library)  

If you do not have these packages installed in python, you can do the following:
```bash
pip install openai==1.12.0 python-docx docx tqdm nltk textract requests
```
### OpenAI API key
You also need an OpenAI key to be able to use this package. If you do not have one, you can apply for an OpenAI API key at [platform.openai.com/api-keys](https://platform.openai.com/api-keys). 


### `pip` version  
The package could only be installed with version older than `24.1`. Newer versions of `pip` will not work due to compatability issues with `textract`. To downgrade to a version older than `24.1`, please do the following:
```bash
pip install "pip<24.1"
```

## Installation
To install in python, simply do the following: 
```bash
pip install AutoThemeGenerator
```

## Quick Start
Here we provide a quick example on how you can execute `AutoThemeGenerator` to conveniently perform qualitative analysis from your transcript. For details towards each of the package's functions and parameters, refer to the [documention](https://cja5553.github.io/ReadTheDocs_AutoThemeGenerator/). 
```python
from AutoThemeGenerator import analyze_and_synthesize_transcripts

# Specify the folders containing your transcript
# This is the folder containing transcripts in .docx, .PDF or .txt format
directory_path = "my_transcript_folder"
# specify your OpenAI API key
api_key = "<insert your API key>"
# specify the folder you wish to save your themes. 
save_results_path = "folder_of_my_saved_results"

# specify the context of your study
context = (
    "Physical inactivity is a major risk factor for developing several chronic illness. "
    "However, university students and staff in the UK are found to be more physically inactive "
    "compared the general UK population. "
    )
# specify your research questions
research_questions = (
    "This study seeks to understand the barriers and enablers "
    "of physical activity (PA) among university staff and students in "
    "the UK under the university setting, using the Theoretical "
    "Domain Framework (TDF) to guide the investigation. "
    )
# specify your survey script
survey_script = (
    "Knowledge\n "
    "What do you know about physical activity? How might you define physical activity? "
    "... ..." # note: truncated to save space
    "... ..." 
    )

# Analyze and synthesize transcripts
initial_themes, individual_synthesized_themes, overall_synthesized_themes = \
analyze_and_synthesize_transcripts(
    directory_path = directory_path, context = context,
    research_questions = research_questions, script = survey_script,
    api_key = api_key, save_results_path = save_results_path)

# display your study-level themes
print(overall_synthesized_themes)
```
You can now view the themes in the form of a topic sentence, a detailed explaination and a relevant quote

## Citation
Yuyi Yang, Charles Alba, Chenyu Wang, Xi Wang, Jami Anderson, and Ruopeng An. "GPT Models Can Perform Thematic Analysis in Public Health Studies, Akin to Qualitative Researchers." Journal of Social Computing, vol. 5, no. 4, (2024): 293-312. doi: [10.23919/JSC.2024.0024](https://doi.org/10.23919/JSC.2024.0024)

# Questions?

Contact me at [alba@wustl.edu](mailto:alba@wustl.edu)
