# Predicting Diabetes Disease Progression

## Project Overview
This project utilizes the Scikit-Learn Diabetes dataset to build and evaluate predictive models for estimating the quantitative measure of **disease progression one year after baseline**. The ultimate objective is to develop a robust screening tool to assist physicians in identifying high-risk patients. 

The project progresses from Exploratory Data Analysis (EDA) and univariate modeling to complex multivariate machine learning algorithms, emphasizing modular code design, mathematical validity, and the prevention of data leakage.

---

## Setup Instructions

To run this project locally, you will need Python 3.8+ installed. Follow these steps to set up your environment:

### 1. Clone the Repository
Clone this repository to your local machine and navigate into the project directory:
```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Create a Virtual Environment
Open your terminal or command prompt and create a virtual environment:
```bash
python -m venv .venv
```

### 3. Activate the Virtual Environment
*   **On macOS / Linux:**
    ```bash
    source .venv/bin/activate
    ```
*   **On Windows:**
    ```bash
    .venv\Scripts\activate
    ```

### 4. Install Dependencies
Install the required Python packages using the provided `requirements.txt`:
```bash
python -m pip install -r requirements.txt
```

### 5. Launch Jupyter Notebook
Start the Jupyter environment to interact with the notebook:
```bash
jupyter notebook
```

---

## Notebook Walkthrough & Accomplishments

The notebook (`multivariate-linear.ipynb`) is strictly divided into three parts, adhering to a modular and readable code structure.

### Part 1: Data Acquisition, Problem Framing, and EDA
*   **Data Loading & EDA:** Loaded the dataset directly into Pandas DataFrames. Conducted thorough EDA including descriptive statistics, distribution histograms, scatter plots, and a correlation heatmap.
*   **Data Cleaning:** Verified that the dataset contains zero missing values and is already pre-standardized, requiring no further imputation or scaling.
*   **Train/Val/Test Split:** Engineered a custom modular function to execute a strict 75% Train / 10% Validation / 15% Test split, ensuring the test set remains completely unseen during model selection.
*   **Conceptual Framing:** Connected the continuous regression problem to course concepts, specifically discussing how classification metrics, KNN distance metrics, and Logistic Regression probabilistic boundaries apply to clinical screening.

### Part 2: Univariate Polynomial Regression
*   **Modeling:** Fitted 6 univariate polynomial regression models (Degrees 0 through 5) using only the `bmi` feature.
*   **Modular Evaluation:** Created reusable helper functions to calculate and compare R², MAE, and MAPE across Train and Validation sets without code duplication.
*   **Model Selection:** Programmatically selected the optimal degree based strictly on the highest Validation R² to prevent overfitting.
*   **Interpretation:** Extracted the exact algebraic equation of the best model, visualized the fit against the data splits, and calculated the expected progression for an "average" patient.

### Part 3: Multivariate Modeling
*   **Algorithmic Diversity:** Expanded the feature space to all 10 physiological variables and evaluated four distinct algorithmic families: Polynomial Regression, Decision Trees, K-Nearest Neighbors (KNN), and Regularized Linear Models (Ridge and Lasso).
*   **Methodological Adjustment:** The original instructions requested "Two Logistic Regression models." Because Logistic Regression is strictly a *classification* algorithm and the target variable is *continuous*, running it would result in a scikit-learn error. To fulfill the mathematical intent of evaluating regularized linear models, **Ridge (L2)** and **Lasso (L1)** regression were implemented instead. 
*   **Multivariate Visualization:** Adapted the visualization step to a "Predicted vs. Actual" scatter plot, as plotting a 10-dimensional regression surface is mathematically impossible.
*   **Parameter Analysis:** Detailed the trainable parameters for each model family, explicitly noting that KNN is a "lazy learner" with 0 trainable parameters, while Decision Trees utilize leaf-node predictions.

---

## Disclosure & Acknowledgments
This project, including the code architecture, mathematical validations, and documentation, was developed with the assistance of **Qwen**, a large language model created by Alibaba Cloud's Tongyi Lab. Qwen assisted in structuring the modular Python functions, ensuring mathematical rigor (such as handling the constraints of applying classification algorithms to continuous regression targets), and generating comprehensive documentation.