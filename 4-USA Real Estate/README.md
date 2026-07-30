# Scalable K-Means Clustering & Elbow Method (WCSS)  
**Fast experimentation with MiniBatchKMeans, sampling, and Windows/MKL notes**

This repository demonstrates a complete, practical workflow for **unsupervised clustering** using **K-Means** and the **Elbow Method** (based on **WCSS / inertia**) to estimate an appropriate number of clusters \(K\).  
It is designed for real-world datasets where classic K-Means can become slow, so it includes **data sampling**, **MiniBatchKMeans**, and **Windows + MKL** considerations.

---

## Table of Contents
- [Motivation](#motivation)
- [What You Will Learn](#what-you-will-learn)
- [Project Scope](#project-scope)
- [Key Concepts](#key-concepts)
- [Tech Stack](#tech-stack)
- [Repository Structure (Suggested)](#repository-structure-suggested)
- [Data Requirements](#data-requirements)
  - [Input Assumptions](#input-assumptions)
  - [Common Data Issues & Fixes](#common-data-issues--fixes)
- [Setup](#setup)
  - [Option A: Conda](#option-a-conda)
  - [Option B: venv + pip](#option-b-venv--pip)
  - [Dependencies](#dependencies)
- [End-to-End Workflow](#end-to-end-workflow)
  - [1) Load Data](#1-load-data)
  - [2) Clean & Prepare Features](#2-clean--prepare-features)
  - [3) Scale Features](#3-scale-features)
  - [4) (Optional) Dimensionality Reduction](#4-optional-dimensionality-reduction)
  - [5) Elbow Method with MiniBatchKMeans](#5-elbow-method-with-minibatchkmeans)
  - [6) Train Final Model](#6-train-final-model)
  - [7) Evaluate Cluster Quality (Recommended)](#7-evaluate-cluster-quality-recommended)
  - [8) Profile & Interpret Clusters](#8-profile--interpret-clusters)
- [Windows + MKL Warning: Why It Happens & How to Fix](#windows--mkl-warning-why-it-happens--how-to-fix)
- [Performance Tips](#performance-tips)
- [Reproducibility](#reproducibility)
- [Troubleshooting](#troubleshooting)
- [Results](#results)
- [Roadmap / Next Improvements](#roadmap--next-improvements)
- [License](#license)
- [Author](#author)

---

## Motivation

Choosing the number of clusters is one of the most common challenges in clustering problems.  
The **Elbow Method** provides an intuitive way to pick a candidate \(K\) by checking when improvements in WCSS start to diminish.

This repository focuses on:
- **Simple and explainable** clustering workflow
- **Scalable execution** on bigger datasets
- **Reproducible experiments** suitable for portfolios and academic applications

---

## What You Will Learn

By following this project you will be able to:

- Properly **scale** features for distance-based clustering
- Run K-Means (and MiniBatchKMeans) for multiple values of \(K\)
- Plot and interpret the **Elbow curve**
- Handle Windows-specific **MKL** warnings safely
- Validate clusters using **Silhouette Score** and other metrics
- Interpret clusters via **cluster profiling** (means/medians per cluster)

---

## Project Scope

This project is **dataset-agnostic** and works for:
- Customer segmentation
- Product grouping
- Behavioral clustering
- Similarity grouping in numeric feature space

The code assumes you are working with **tabular numeric features** (or features that can be converted to numeric).

---

## Key Concepts

### K-Means (high-level)
K-Means aims to partition \(n\) samples into \(K\) clusters such that each point belongs to the nearest centroid.

### Objective function (WCSS / inertia)
K-Means minimizes:

\[
\text{WCSS}(K) = \sum_{i=1}^{K} \sum_{x \in C_i} \| x - \mu_i \|^2
\]

Where:
- \(C_i\) is cluster \(i\)
- \(\mu_i\) is centroid of cluster \(i\)

**Lower WCSS** is better, but WCSS always decreases as \(K\) increases.  
So we look for the **“elbow”** where improvements begin to flatten.

---

## Tech Stack

- Python 3.9+ (3.10 recommended)
- NumPy
- Pandas
- Matplotlib
- scikit-learn

Optional (recommended for advanced analysis):
- seaborn (better plots)
- joblib (model persistence)
- tqdm (progress bars)

---

## Repository Structure (Suggested)

You can keep everything in a notebook, but for a portfolio-ready project, consider:

