# MLOps Used Cars Mirror

A machine learning operations (MLOps) project for predicting used car prices using Azure ML Studio integration.

## Project Overview

This project implements an end-to-end MLOps pipeline for training, deploying, and monitoring machine learning models that predict used car prices. The pipeline leverages Azure ML Studio for model training, tracking, and deployment, while GitHub Actions automates the continuous integration and delivery process.

**Key Features:**
- Automated model training pipeline
- Azure ML Studio integration for experiment tracking
- Data preprocessing and feature engineering
- Model versioning and registry
- CI/CD with GitHub Actions
- Reproducible model training workflows

## Dataset Description

The project uses a used cars dataset containing various features to predict vehicle prices:

**Features:**
- **Vehicle Information**: Make, model, year, mileage
- **Technical Specifications**: Engine size, transmission type, fuel type
- **Condition Metrics**: Overall condition, service history
- **Market Data**: Location, seller type, listing date

**Target Variable:** Price (in local currency)

**Data Sources:**
- The dataset is expected to be stored in Azure Blob Storage or loaded from a public repository
- Data preprocessing scripts handle missing values, outliers, and feature encoding

## Model Pipeline Steps

The ML pipeline consists of the following stages:

### 1. Data Ingestion
- Load raw data from configured data sources
- Validate data schema and quality
- Split data into training, validation, and test sets

### 2. Data Preprocessing
- Handle missing values using appropriate imputation strategies
- Encode categorical variables (one-hot encoding, label encoding)
- Scale numerical features (standardization, normalization)
- Feature engineering (age of car, price per mile, etc.)

### 3. Model Training
- Train multiple model candidates (Linear Regression, Random Forest, XGBoost, etc.)
- Perform hyperparameter tuning using grid search or Bayesian optimization
- Cross-validation for robust model evaluation
- Log metrics and artifacts to Azure ML Studio

### 4. Model Evaluation
- Evaluate models on validation set using metrics:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - R² Score
- Compare model performance
- Select best performing model

### 5. Model Registry
- Register the best model in Azure ML Model Registry
- Version control for models
- Add model metadata and tags

### 6. Model Deployment (Future)
- Deploy model as REST API endpoint
- Monitor model performance in production
- Set up alerts for model drift

## How to Run the Code Locally

### Prerequisites

- Python 3.8 or higher
- pip package manager
- Azure account with ML Studio workspace (for cloud training)
- Git

### Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone https://github.com/kenderovemil/mlops-used-cars-mirror.git
   cd mlops-used-cars-mirror
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Azure credentials (if using Azure ML Studio):**
   ```bash
   # Set environment variables
   export AZURE_SUBSCRIPTION_ID="your-subscription-id"
   export AZURE_RESOURCE_GROUP="your-resource-group"
   export AZURE_WORKSPACE_NAME="your-workspace-name"
   ```
   
   Or create a `.env` file:
   ```
   AZURE_SUBSCRIPTION_ID=your-subscription-id
   AZURE_RESOURCE_GROUP=your-resource-group
   AZURE_WORKSPACE_NAME=your-workspace-name
   ```

5. **Run the training pipeline:**
   ```bash
   python train.py
   ```

6. **Run with Jupyter notebooks (optional):**
   ```bash
   jupyter notebook
   # Open and run notebooks in the notebooks/ directory
   ```

### Local Development

For local development and experimentation:

```bash
# Run data preprocessing
python preprocess.py

# Train model locally
python train.py --local

# Evaluate model
python evaluate.py --model-path outputs/model.pkl
```

## Azure ML Studio Integration

This project is integrated with Azure ML Studio for enterprise-grade MLOps capabilities.

### Azure ML Components Used

- **Workspaces**: Centralized place to manage all ML artifacts
- **Compute Targets**: Managed compute for training (CPU/GPU clusters)
- **Experiments**: Track and compare multiple training runs
- **Models**: Version control and registry for trained models
- **Datasets**: Versioned datasets with lineage tracking
- **Pipelines**: Orchestrated ML workflows

### Setting Up Azure ML Workspace

1. **Create Azure ML Workspace:**
   ```bash
   az ml workspace create \
     --name your-workspace-name \
     --resource-group your-resource-group \
     --location eastus
   ```

2. **Configure workspace connection:**
   - Download workspace config file from Azure Portal
   - Place `config.json` in the project root directory
   
   Or use Azure CLI:
   ```bash
   az ml workspace show \
     --name your-workspace-name \
     --resource-group your-resource-group > config.json
   ```

### Running Training on Azure ML

```bash
# Submit training job to Azure ML
python train.py --azure

# Monitor run in Azure ML Studio
# Navigate to: https://ml.azure.com
```

### CI/CD with GitHub Actions

The project uses GitHub Actions for automated model training:

- **Trigger**: Automatic on push to `main` branch
- **Steps**: Environment setup, dependency installation, model training
- **Artifacts**: Trained models and metrics are uploaded as artifacts

See `.github/workflows/train_model.yaml` for configuration details.

## Project Structure

```
mlops-used-cars-mirror/
├── .github/
│   ├── workflows/
│   │   └── train_model.yaml       # CI/CD workflow
│   └── ISSUE_TEMPLATE/            # Issue templates
├── data/                          # Data files (not tracked in git)
├── notebooks/                     # Jupyter notebooks for exploration
├── outputs/                       # Model outputs (not tracked in git)
├── prep_outputs/                  # Preprocessing outputs (not tracked in git)
├── src/                           # Source code
│   ├── preprocess.py             # Data preprocessing
│   ├── train.py                  # Model training
│   └── evaluate.py               # Model evaluation
├── tests/                        # Unit and integration tests
├── .gitignore                    # Git ignore rules
├── CONTRIBUTING.md               # Contribution guidelines
├── README.md                     # This file
└── requirements.txt              # Python dependencies
```

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

For questions or issues, please open an issue in the GitHub repository or contact the maintainers.

## Acknowledgments

- Azure ML Studio team for excellent documentation
- Open source community for ML libraries and tools
