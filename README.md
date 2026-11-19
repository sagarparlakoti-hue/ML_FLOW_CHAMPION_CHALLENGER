# MLflow Champion–Challenger Model Comparison

## Project Overview
This project implements a Champion–Challenger framework for comparing two Hugging Face transformer models using MLflow.

The objective is to evaluate two sentiment classification models, compare their performance using evaluation metrics, select the best-performing model as the Champion, and register both models in the MLflow Model Registry.

## Project Details
- **Student Name:** Sagar Parlakoti
- **USN:** 1MS25CI111
- **Branch:** CSE AIML
- **Section:** B
- **Skill Lab:** CISL-1

## Technologies Used
- Python
- MLflow
- Hugging Face Transformers
- PyTorch
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

## Models Used

| Model | Role |
|---|---|
| DistilBERT SST-2 | Initial Champion |
| BERT-base SST-2 | Challenger |

**Dataset:** SST-2 Validation Dataset from Hugging Face.

The models were evaluated using 200 balanced sentences (100 positive and 100 negative).

## Evaluation Metrics
The following metrics are used to compare both models:

- Accuracy
- Macro Precision
- Macro Recall
- Macro F1-score
- Average Inference Latency
- Total Inference Time

## Results

| Metric | DistilBERT | BERT-base |
|---|---:|---:|
| Accuracy | 89.50% | 92.50% |
| Macro Precision | 89.82% | 92.54% |
| Macro Recall | 89.50% | 92.50% |
| Macro F1-score | 0.8948 | 0.9250 |
| Average Latency | 51.27 ms | 76.23 ms |

**Final Champion:** BERT-base SST-2

BERT-base achieved a higher Macro F1-score and satisfied the predefined latency condition. Therefore, it was selected as the Champion model, while DistilBERT remained the Challenger.

## Project Workflow
1. Load the SST-2 validation dataset.
2. Evaluate both Hugging Face models on the same dataset.
3. Calculate performance metrics.
4. Log experiments, parameters, metrics, and artifacts using MLflow.
5. Compare the Champion and Challenger models.
6. Register both models in the MLflow Model Registry.
7. Assign Champion and Challenger aliases.
8. Load the Champion model from MLflow and perform predictions on new input data.

## How to Run

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Start MLflow Server
```bash
python -m mlflow server --host 127.0.0.1 --port 5000 --backend-store-uri sqlite:///mlflow.db
```

### 3. Evaluate Models
```bash
python evaluate.py
```

### 4. Register Models
```bash
python register_champion.py
```

### 5. Perform Predictions
```bash
python predict_from_mlflow.py
```

## Repository Structure
```text
├── data/
│   ├── eval_inputs.csv
│   └── new_data.csv
├── outputs/
│   ├── predictions
│   ├── metrics_summary
│   ├── model_comparison.csv
│   └── confusion matrices and charts
├── screenshots/
├── evaluate.py
├── hf_wrapper.py
├── register_champion.py
├── predict_from_mlflow.py
├── requirements.txt
└── README.md
```

## Conclusion
This project demonstrates how MLflow can be used to track machine learning experiments, compare multiple models, manage model versions, and deploy the best-performing model using model aliases.

The Champion–Challenger approach helps ensure that model updates are based on measurable performance improvements rather than assumptions.
