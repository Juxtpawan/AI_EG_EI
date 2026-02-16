# AI-based Enterprise Knowledge Graph - Data Preprocessing Module

This project is a component of an AI-based Enterprise Knowledge Graph system, currently focusing on the ingestion, cleaning, and preprocessing of supply chain and access log data. The primary goal is to prepare raw datasets for downstream tasks such as graph construction and analysis.

## Features

The data preprocessing pipeline (`data_preprocessing.ipynb`) includes the following features:

### Data Cleaning
- **Duplicate Removal**: Automatically identifies and removes duplicate records to ensure data integrity.
- **Missing Value Handling**:
    - Drops rows with critical missing identifiers (e.g., `Order Id`, `Customer Id`, `Product Card Id`, `Date`, `Product`).
    - Fills missing `Customer Zipcode` values with 0.
    - Standardizes column names by replacing spaces and special characters with underscores.

### Text Normalization
- **Standardization**: Converts text fields (e.g., `Customer City`, `Product Name`, `Category`, `Department`) to title case and strips leading/trailing whitespace for consistency.

### Data Enrichment
- **Profitability Classification**: Adds a new column `Order_Profitability_Classification` to classify orders based on `Benefit per order`:
    - **Positive**: Profit > 0
    - **Negative**: Profit < 0
    - **Neutral**: Profit = 0 or other cases.

### Log Data Processing
- **Date Parsing**: Converts date strings to datetime objects and filters out invalid dates.
- **Product Normalization**: Standardizes product names in access logs for consistent mapping.

## Project Structure

```
AI_KG_EI/
├── Datasets/                               # Raw input datasets
│   └── DataCoSupplyChainDataset/           # DataCo dataset files
├── Processed_Datasets/                     # Cleaned and processed output files
├── data_preprocessing.ipynb                # Main Jupyter Notebook for data processing
├── README.md                               # Project documentation
└── .venv/                                  # Python virtual environment (if applicable)
```

## Prerequisites

- Python 3.x
- Jupyter Notebook or JupyterLab
- Required Python libraries:
    - `pandas`
    - `numpy`

## Installation

1.  **Clone the repository** (if applicable) or download the project files.
2.  **Set up a virtual environment** (optional but recommended):
    ```bash
    python -m venv .venv
    # Windows
    .venv\Scripts\activate
    # macOS/Linux
    source .venv/bin/activate
    ```
3.  **Install dependencies**:
    ```bash
    pip install pandas numpy notebook
    ```

## Usage

1.  **Open the Notebook**:
    Launch Jupyter Notebook in the project directory:
    ```bash
    jupyter notebook data_preprocessing.ipynb
    ```

2.  **Run the Cells**:
    Execute the cells in order. The notebook is structured to:
    - Initialize the `DataPreprocessing` class.
    - Define methods for cleaning and processing.
    - Run the main execution block to process the datasets.

3.  **Output**:
    The script will generate cleaned CSV files in the `Processed_Datasets/` directory:
    - `Processed_DataCoSupplyChain.csv`
    - `Processed_TokenizedAccessLogs.csv`

## Future Scope

This preprocessing module is the foundational step for building the Enterprise Knowledge Graph. Future enhancements will include:
- Entity Extraction and Linking.
- Knowledge Graph Construction (Nodes and Edges).
- Integration with Graph Databases (e.g., Neo4j).
