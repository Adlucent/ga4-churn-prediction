# An End-to-End Customer Churn Prediction Model for Retail Using GA4 Data

This repo contains a full solution for predicting customer churn propensity for retail. It contains a series of Google Colab notebooks and is written primarily in Python, using this [BigQuery sample dataset](https://developers.google.com/analytics/bigquery/web-ecommerce-demo-dataset) from Google Analytics 4.<br>

In these notebooks, you’ll:
1. Analyze, preprocess, and engineer a GA4 dataset from BigQuery and prepare it for modeling,
2. Build, tune and evaluate an XGBoost Classifier model that returns customer-level churn propensity scores, and
3. Save the results into a table for visualization and further analysis.

One of the main things to remember when building your model is that the metric you choose to optimize your model to should support your specific business needs. In our example, we optimized to Specificity, with the goal of correctly identify as many True Negatives (non-churners) as possible in an imbalanced dataset. For example, we may want to use our propensity scores to create marketing audiences that help us find and market to new customers who look like our existing "low churn propensity" customers. <br>
<br>
You may choose instead to optimize your model to recall, precision, or F1 score depending on your specific use case. <br>

## Notebooks included

I. Setup & EDA <br>
I.i. EDA - RFM Customer Segmentation <br>
II. Array Flattening and EDA Part 2 <br>
III. Preprocessing and Feature Engineering <br>
IV. Defining the Churn Target <br>
V. Aggregation and Initial Feature Selection <br>
VI. Multicollinearity Check and Model Building, Tuning and Evaluation <br>

## Prerequisites and Initial Setup Requirements
1.	A Google Cloud Platform [account](https://cloud.google.com/docs/get-started) and [project](https://cloud.google.com/resource-manager/docs/creating-managing-projects) <br>
2.	A [GA4 BigQuery Export](https://support.google.com/analytics/answer/9823238?hl=en#zippy=%2Cin-this-article) of the data you want to use in the churn model <br>

## GCP tools available

1.	[**Vertex AI Workbench**](https://cloud.google.com/vertex-ai-workbench): The Vertex AI Workbench within the GCP console has an integration with JupyterLabs where you can create managed or user-managed notebooks directly within GCP. If you’re handling sensitive data or need more scalable computing resources to process larger amounts of data, you can create a user-managed notebook within the workbench that runs on a Compute Engine virtual machine and open the .ipynb notebooks within that. Jupyter Labs within the Vertex AI workbench has all of the same features (and then some) as the version you typically have installed locally, 
2.	[**AutoML**](https://cloud.google.com/automl): Once you get to the model building step, AutoML could be a great alternative if your Python models are not performing as well as you’d like, if your training dataset is very large, or if you’re looking to fully automate and deploy your model for real-time or batch predictions. You can train AutoML models from within the Vertex AI Training section of the GCP console, or directly from your notebook using Python. 
* *For large data sources, you may need to connect Colab to a local runtime or upgrade to a hosted runtime, or use JupyterLabs from the Vertex AI Workbench in the GCP console.* 

## Other helpful links

### Google resources
* [GA4 BigQuery Export Schema](https://support.google.com/analytics/answer/7029846?hl=en)
* [Connecting to BigQuery from Google Colab](https://colab.research.google.com/notebooks/bigquery.ipynb)
* [Connecting Google Colab to a local runtime](https://research.google.com/colaboratory/local-runtimes.html)
* [Training AutoML models](https://cloud.google.com/automl-tables/docs/train)
* [Specifying a Schema for a BigQuery Table Export](https://cloud.google.com/bigquery/docs/schemas)
* [Vertex AI Jupyter Notebook Tutorials](https://cloud.google.com/vertex-ai/docs/tutorials/jupyter-notebooks)

### API and Other Documentation
* [Python Client for Google BigQuery](https://googleapis.dev/python/bigquery/latest/index.html)
* [Imbalanced-learn (Python library for over or undersampling imbalanced datasets)](https://imbalanced-learn.org/stable/references/index.html#api)
* [XGBoost Hyperparameters](https://xgboost.readthedocs.io/en/stable/parameter.html)
