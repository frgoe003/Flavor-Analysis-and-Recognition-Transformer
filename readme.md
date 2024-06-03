# FART: Flavor Analysis and Recognition Transformer Model

Welcome to the repository for the **Flavor Analysis and Recognition Transformer (FART) Model**, a project developed as part of the Digital Chemistry Lecture at the Department of Chemistry and Applied Biosciences, ETH Zurich. This project is a collaborative effort by Franz Goerlich†, Philipp Pestlin†, Henrik Seng†, Leif Sieben†, and Yoel Zimmermann†, with all authors contributing equally to this work.

## Overview

Determining the taste of molecules is a laborious and time-consuming process in food chemistry. While various machine learning approaches have been used for taste classification, transformer models, despite their success in sequential learning tasks, have not been applied to this domain until now.

The FART model aims to fill this gap by leveraging the power of transformer models for taste classification of molecules. Our approach utilizes ChemBERTa, a transformer model pretrained on 10 million SMILES from PubChem, to predict the taste of query molecules.

## Key Features

- **Large Dataset**: A dataset of 19,478 molecules was curated from five publicly available datasets. The dataset is now accessible online with full FAIR compliance.
- **Data Imbalance Handling**: The dataset is imbalanced, with a predominance of sweet molecules. To address this, expert-generated data was used to collect sour molecules, and a loss function penalizing the prediction of more common classes was implemented.
- **Attention Mechanism**: FART's attention mask aligns well with chemical intuition, focusing on acid groups for sour compounds.
- **Performance**: FART outperforms two different random forest approaches, suggesting that transformers can outperform simpler machine learning models given sufficient data.
- **User Interface**: An interactive web-app with a molecule drawer enables users to easily interact with FART and check the taste of query molecules.

## Dataset

A comprehensive dataset of 19,478 molecules, nearly all publicly known molecule-taste pairs, was collected from five sources. Each entry includes a canonicalized SMILES and a taste class. The database excludes salty molecules due to their scarcity and labels molecules with no known taste as "undefined".

## Model

The FART model is based on ChemBERTa, which is pretrained on 10 million SMILES using 6 layers and 12 attention heads. The model was fine-tuned on our curated dataset to predict the taste of molecules.

## Try It Out

You can try out the FART model yourself using our interactive web application. The web app features a molecule drawer that allows you to input a molecule and get the predicted taste classification.

[Try FART now](https://fart-labs.web.app/)

## Results and Discussion

FART was compared with two different random forest approaches and demonstrated superior performance:

| Approach                          | Accuracy | Precision | Recall  | F1-Score |
|-----------------------------------|----------|-----------|---------|----------|
| FART                              | 0.8381   | 0.8348    | 0.8381  | 0.8347   |
| FART with class weighting         | 0.8155   | 0.8444    | 0.8155  | 0.8248   |
| Random Forest with oversampling   | 0.8085   | 0.8316    | 0.8085  | 0.8176   |
| Random Forest with weights biases | 0.8095   | 0.8388    | 0.8095  | 0.8204   |

## Conclusion

The FART model demonstrates that transformer models, with sufficient data, can outperform simpler machine learning approaches in the domain of molecular taste prediction. The model is accessible via an online user interface, making it easy for users to predict the taste of molecules interactively.

## References

1. Y. Song, S. Chang, J. Tian, W. Pan, L. Feng, and H. Ji, “A Comprehensive Comparative Analysis of Deep Learning Based Feature Representations for Molecular Taste Prediction,” Foods, vol. 12, no. 18, p. 3386, (2023), doi: 10.3390/foods12183386.
2. Malavolta, M., Pallante, L., Mavkov, B. et al. "A survey on computational taste predictors". Eur Food Res Technol 248, 2215–2235 (2022), doi: 10.1007/s00217-022-04044-5
3. S. Chithrananda, G. Grand, and B. Ramsundar, “ChemBERTa: Large-Scale Self-Supervised Pretraining for Molecular Property Prediction.” arXiv, (2020). Accessed: Feb. 23, 2024. Arxiv.org/abs/2010.09885
4. [FART Database](https://huggingface.co/datasets/FartLabs/FartDB)
