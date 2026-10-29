# Navigating PCOS with Machine Learning

An academic team project comparing four classification models on a 541-record PCOS dataset. Includes data cleaning, exploratory analysis, statistical tests, model training, ROC plots, and confusion matrices.

## Team
Abhinaya Malempati, Aruna Prasanna Simhambhatla, Charulata Sree Pokala, Cherry Gupta, Priyanka Reddy Kuta.

## Historical results from the original notebook
| Model | Test accuracy |
|---|---:|
| Logistic regression | 84.56% |
| Decision tree | 78.68% |
| Random forest | 88.97% |
| XGBoost | 91.18% |

The 93.83% logistic regression result was training accuracy, not test accuracy. A subsequent run of the model workflow reproduced the first three test accuracies; XGBoost achieved 90.44% with the newer environment. No external clinical validation is claimed.

## Data
Download the workbook from the original dataset source:
https://www.kaggle.com/datasets/prasoonkottarathil/polycystic-ovary-syndrome-pcos

Place `PCOS_data_without_infertility.xlsx` beside the notebook. The required sheet is `Full_new`. Data is not redistributed in this repository. Review the dataset's license and cite its provider when reusing it.

The original report also referenced this public notebook:
https://www.kaggle.com/code/dj67rockers/pcos-diagnosis

## Run locally on macOS
```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyter lab PCOS_Analysis.ipynb
```
In Jupyter, select Run → Run All Cells. On Google Colab, upload the notebook and install the required packages if needed; the first code cell prompts for the Excel workbook when it is missing.

## Changes to the recovered notebook
- Cleared outputs and execution counts before publishing.
- Replaced the Colab-only loader with local-file support and an optional Colab upload.
- Added a DataFrame wrapper for the outlier mask for current SciPy compatibility.
- Added the missing confusion-matrix helper used by the final metrics cell.
- Removed an obsolete XGBoost parameter.
- Preserved the original analysis and model settings; this is not a newly validated pipeline.

## Limitations and interpretation
The original workflow includes identifiers as predictors, imputes values before splitting, and replaces selected outliers using full-data means. These choices should be revised in a separate improved analysis before making generalization claims. Some exploratory test descriptions and clinical interpretations in the original materials need review; association does not establish causation. Ultrasound and other diagnostic features may overlap with how labels were assigned. Model scores are educational results, not evidence of clinical readiness.

## Validation
All code cells passed Python syntax parsing. The core training workflow was executed with the supplied workbook after the outlier-mask fix. The entire EDA notebook has not been rerun end to end. Package ranges are compatibility guidance, not the recovered original environment.
