Data 201 Project 1: Classification in Practice

This project classifies breast masses as malignant or benign using the Wisconsin Diagnostic Breast Cancer dataset, which has 569 masses and 30 numeric predictors measured from digitized images of cell nuclei. I fit four classifiers, Logistic Regression, LDA, QDA and KNN, compare them on a held-out test set, and recommend one for deployment.

## Main finding

Logistic regression with the threshold of 0.40 is my recommendation. False negative is a costly mistake, and therefore, recall is the target metric for this case. Both the model and the threshold are selected based on 5-fold cross-validation with only training data. The criterion is the largest value from a grid of 0.05-0.95 where the out-of-fold recall is at least 0.95. Test data were used only once.

For 143 masses in the test data, 53 of which are malignant, this model detects 50 cancers, misses 3 and makes 1 false positive detection of 90 benign masses, recall being 0.943. With the threshold of 0.50, it misses 4 cancers. KNN and LDA make higher recalls on their optimal thresholds, but with 4 and 9 false detections. With only 53 malignant cancers in test data, there are several patients between model performances, and therefore, the order is promising.

## Files

- `Data201_Project1_Classification.ipynb`: the full analysis with outputs.
- `breast_cancer_wdbc.csv`: the dataset.
- `test_predictions.csv`: predicted probability and class for every test mass from all four models.
- `Model_Pitch_-_Breast_Mass_Classification.pptx`: the four-slide model pitch.

## How to run

Open the notebook in Google Colab and choose Runtime, then Run all. The notebook reads the CSV from this repository by its raw GitHub URL, so nothing needs to be uploaded. It uses only numpy, pandas, matplotlib and scikit-learn, with `RANDOM_STATE = 42` throughout.
