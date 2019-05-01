---
layout: post
title: CMS Medicare Data Fraud Detection
subtitle: Fraud Detection in CMS Part D open dataset
bigimg: /img/path.jpg
image: /img/cms.png
tags: [Machine Learning, Fraud Detection,Python, Big Query]
---

###  CMS Medicare Data Fraud Detection [GitHub](https://github.com/Pyligent/CMS-Medicare-Data-FRAUD-Detection)

#### Problem Definition
Healthcare fraud is a main problem that causes substantial monetary loss in Medicare/Medicaid and insurance industry. The Centers for Medicare and Medicaid Services (CMS) have setup Medicare Part D programs since 2006. CMS relies on it to detect and prevent fraud, waste and abuse in Part D program. But using the traditional methods, the fraud detection is conducted on random samples by human experts. The consequences are the samples might be misleading or manual detection is costly. According to Office of Inspector General report: Since 2006, the Medicare Fraud has rapidly increased. The fraud patterns include the following four types:

- Fraud by Service Providers (Doctors, hospitals, pharmacies) 
- Fraud by Insurance subscribers (patient or patient’s employers)
- Fraud by insurance carriers •	Conspiracy Frauds (involved with all parties)

Also along with fraud the following patterns reported by OIG report:

- Commonly abuse drug/opioid has grown faster than spending for all Part D drugs 
- Pharmacies with questionable billing raise concerns about pharmacy-related fraud schemes 
- Geographic hotspots for certain non-controllable drugs points to possible fraud and abuse

This project will try to use the machine learning method to address the above problems and detect the fraudulence Medicare claims from the CMS open datasets and other use open data.

#### The objectives

- Build a simple Data Model to show the relationships among the different datasets and identify the key feature-sets for fraud detections 
- Build a comprehensive machine learning model to detect fraud pattern based on the different features: Service Providers (Doctors, Pharmacies), Insurance subscribers (patients), Geo-demographic and commonly abuse drugs prescriptions 
- Setup a benchmark metrics to measure and evaluate the experimental result 
- Market-ready product

### Data Set:
We will use the following open [datasets](https://www.cms.gov/openpayments/explore-the-data/dataset-downloads.html):
- Part D Prescriber dataset 
- Excluded (LEIE) dataset
- Payment Received dataset
- FDA Drug ingredients dataset
- Others: Part D Opioid Prescriber Summary


### Analytics Technique

- Descriptive Analytics for Fraud Detection
Descriptive analytics or unsupervised learning aims at finding unusual anomalous behavior deviating from the average behavior or norm. When used for fraud detection, unsupervised learning is often referred to as anomaly detection, since it aims at finding anomalous and thus suspicious observations. Unsupervised learning can be useful for fraud detection and thus have no labeled historical data set available (such as LEIE). It can also be used in existing fraud models by uncovering new fraud mechanisms. We will try to use the nearest-neighbour based techniques, Clustering-based methods and other algorithms.


- Predictive Analytics for Fraud Detection
In predictive analytics, the aim is to build an analytical model predicting a target measure of interest. The target is then typically used to steer the learning process during an optimization procedure. Two types of predictive analytics can be distinguished depending on the measurement level of the target: regression and classification. 
We will use the logistic Regression and Random Forest Classification to build the machine-learning model. Also we will use the ensemble and boosting model to optimize the model.

### Challenges in handling huge Data Sets
Normally, the size of CMS Medicare Part D data is more than 3Gbytes. Given the facts in huge capacity of Medicare data, we need more efficient ways to handling the data. There are lots of challenges with pre-processing, querying and analyzing data. We have tried three possible ways to address these challenges:
- Google Cloud Big-Query API
Part D data is integrated with Google Cloud platform and Google provides cloud-based query API. We could use Python to do SQL query to Pandas Data-frame. But the limitation is the size of query is limited below one Gbytes.
- PostgreSQL or MySQL 
Use Python packages, we can SQL query the data from some local SQL servers. But the problem is it can’t process the huge data efficiently. Also need a lots work on SQL servers.
- Apache Spark and PySpark
So far, Spark is the fastest way to handling the huge data due to the in-memory computation and distributing computing framework. We will try to use PySpark as the mainly data technique to handling data. 



