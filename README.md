# Swiss_German_to_German_Translation_ANLP_2023

This repository contains the code and result files for the project "Handling Syntactical Particularities of Western Swiss German Dialects: A Study of Embedding Vector Initialization in Machine Translation" developed as a final project in the course Advanced Natural Language Processing and Deep Learning at the IT University of Copenhagen.

## Authors
Andreas Møller Belsager  
Linda Caroline Schombach  
Mira Metzger

## Folder Structure

The folders are structured as follows:

```bash
.
├── Code
│   ├── 1_data_preparation.ipynb
│   ├── 2_training.ipynb
│   ├── 3_testing.ipynb
│   └── 4_scores_test_statistics.ipynb
├── README.md
├── Report.pdf
└── Results
    ├── Manual_Syntax_Evaluation_Synt_TestSet.xlsx
```

## Code

### Installation & Requirements

The code is run on Google Colab, with the following additional requirements:

```bash
pip install sentencepiece transformers==4.33 datasets wandb sacremoses sacrebleu -q
```

### Notebooks

To reproduce the results of this project, execute the notebooks in the folder /Code. The notebooks are numbered based on the stage in the workflow. Each notebook contains further information and instructions on how to run the notebook and which parameters to change. 

**1_data_preparation.ipynb**:
* Preprocess the raw data file, generate the training and test sets, and stores resulting CSV files in a /Data folder. The test set is generated in a way so that it contains the same data for all three relevant dialects, i.e. GR, BE and VS.

**2_training.ipynb**:
* This notebook is run to add a new language to the model and finetune it on the SwissDial training dataset. This notebook is executed with a T4 GPU in Google Colab. The model used for training is the [facebook/nllb-200-distilled-600M](https://huggingface.co/facebook/nllb-200-distilled-600M) from Hugging Face. 

**3_testing.ipynb**:
* Generates translations for the synthetic test set and SwissDial test set between the source language (BE) and the target language (DE) using five different models trained on distinct embedding strategies. The fine-tuned models for Swiss German dialects GR, VS and BE can be found [here](https://drive.google.com/drive/folders/1Vfe1fAmGQdUWecqt2HKNxUkObRbRqfFo?usp=sharing).

**4_scores_test_statistics.ipynb**: 
* Notebook to calculate the BLEU, CHRF and TER scores as well as test statistics.


## Data

* The dataset [SwissDial](https://mtc.ethz.ch/publications/open-source/swiss-dial.html) is obtained from the Eidgenössische Technische Hochschule (ETH) Zürich and contains the Swiss German and High German transcripts.


## Results

* **Manual_Syntax_Evaluation_Synt_TestSet.xlsx**: contains the translations of the **synthetic** test set from the source to the target language (BE-DE) for all 5 different models (5 different embedding strategies). The file contains scores and detailed error analysis for each model and syntax phenomenon.
