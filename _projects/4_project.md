---
layout: page
title: End to End Data Engineering Process on the NSL- KDD dataset
description:
img: assets/img/proj_4_1.png
importance: 2
category: work
---

In this project, the focus was on developing a system capable of predicting and classifying network intrusions using the NSL-KDD dataset, which comprises around 125,000 data points. The aim was to analyze the dataset, identify patterns, and similarities between intrusions to enhance network security.

The project began with extensive exploratory data analysis (EDA) and data cleaning to ensure data quality and reliability. Various data preprocessing techniques were employed to prepare the dataset for machine learning model implementation. The use of PySpark facilitated efficient data processing, while PostgreSQL aided in managing the dataset. Scikit-learn was utilized for implementing machine learning models, and Google Cloud Platform (GCP) tools were leveraged for model training and deployment.

After performing EDA, data cleaning and engineering (imputation, detecting and removing outliers, string indexing and one-hot encoding), and implementing machine learning models (fully connected neural networks and tree-based methods), the system demonstrated robustness, accuracy, and scalability in predicting and classifying network intrusions. The combination of PySpark, PostgreSQL, Scikit-learn, and GCP tools played a crucial role in achieving efficient data processing, model training, and deployment.

The project's successful outcome underscores the importance of thorough data preprocessing, effective machine learning model implementation, and utilizing cloud-based platforms like GCP for scalability and deployment. The system's capabilities in network intrusion detection showcase its potential as a comprehensive and effective solution for enhancing cybersecurity measures.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proj_4_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The pipeline
</div>

Out of all the models, the neural network performed the best with a test accuracy of 80% which signifies the % of network intrusions detected correctly.
