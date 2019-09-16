# Project

The goal of the project is to acquire an understanding of the basic concepts and techniques of data analysis, understand how they work, and get an intuition when and how they should be applied in order to get knowledge from data. You should get an idea about the questions we can answer with data analysis and you should be able to apply and evaluate the basic approaches of machine learning.

**Project is solved in pairs.** We expect you to use `Python` programming language and available data analysis libraries (such as `pandas`, `matplotlib`, etc.). In each phase, you should submit an executable `Jupyter Notebook` that should contain and document all the transformations of the data. The submitted notebook must contain not only your code, but also its results (computed values, outputs, visualizations, etc.) together with your commentary in which you should interpret the obtained results and your decisions for the next data analysis steps that you can base on these results. Your ability to communicate and select relevant results of the data analysis will present a substantial part of the project assessment. *In each phase, please indicate in the submitted notebook the percentage ratio of the work done by the individual members of the pair.*

## Data

Each pair will work with randomly assigned data set. Your task is to predict a variable **Y** (it can differ based on the assigned data set). You will have to deal with multiple problems contained in the data (data formats, missing or nonsensical data, outliers, etc.).

## Exploratory analysis (max. 12 points)

Exploratory analysis is a crucial part of data analysis. Without this step, we would not be able to process the data, because we would not know anything about it. We mainly use descriptive statistics and various supporting visualizations.

In this phase, we expect from you: 
- **Univariate analysis: a basic description of data together with its characteristics (3 points).** To get the full amount of points, you should state the number of records (observations), the number of attributes and their types and for selected relevant attributes also their distributions, basic descriptive statistics, etc.
- **Bivariate analysis (4 points).** You should explore the relations between the selected pairs of attributes (e.g., correlations). Focus also on the dependencies of a predicted variable and other variables (potential predictors).
- **Formulation and statistical evaluation of hypotheses about data (2 points).** You should formulate at least two hypotheses about data which will be relevant in the context of the assigned prediction task. An example of a hypothesis (based on the assigned data set) is that *patients with thyroid disease have on average different (higher/lower) value of a given hormone than patients without the disease*. You should test your hypotheses using a suitable statistical test.
- **Identification of the problems in the data together with a scenario (plan) of next steps (3 points).** You should identify what you will have to address during the preprocessing phase and discuss your possible next steps for the second phase of the project. The problems that might be present in your data include for example the following:
  - bad data structure (data are not in a tabular form or an entity is described by multiple rows in a table),
  - duplicate records or ambiguous mapping between the records in multiple tables,
  - multiple data formats,
  - missing values,
  - outliers,
  - and others, i.e., the data can contain other, here not specified, problems that still needs to be identified and addressed in your analysis.

In the submitted report (Jupyter Notebook), you should be able to answer these questions:
- Do the data have a suitable format for their further processing? If not, what problems do they contain?
- Are some attributes dependent on each other? On which attributes does the predicted variable depend?
- Are there missing values? How are they represented? How do you plan to solve this issue for individual attributes or observations? (You can use different strategies for different attributes.)
- Do some attributes have nonsensical or inconsistent values? Are there any outliers?
- How do you plan to address these issues in the next (preprocessing) phase?

The report is due in the 6th week of the semester. The pair should present their analysis in a `Jupyter Notebook` during the labs to their teacher. Then, one of the pair should submit the report to the AIS before **Sunday, 3rd November, 2019, 23:59**.

## Preprocessing (max. 18 points)

Based on the problems identified in the previous phase and the proposed solutions, you should carry out data preprocessing. The output of this phase should be a modified data set (in `csv` format) that will have a suitable form for a selected machine learning algorithm. That means that each observation has to be described by one row in a table; also, because we will work in the last phase with an algorithm, the implementation of which supports only numerical data, you will have to transform all non-numerical data into numerical. Finally, since the preprocessing can change the characteristics of the data (the number of attributes, data distributions, etc.), you should again carry out relevant parts of exploratory analysis. A substantial part of the assessment in this phase will be based on the reusability of the preprocessing on the new data. 

In this phase, we expect you to do the following:
- **Data integration and data deduplication (4 points).** This should result into a single data table that will serve as an input for further data preprocessing.
- **Data preprocessing and documentation of each step (5 points).**
  - When addressing the missing values, you are expected to try out various strategies (you should try out at least two strategies and one of those should be from the last three in the list below):
    - Replacing missing values with median
    - Replacing missing values with mean
    - Replacing missing values with their ratio to a correlated attribute
    - Replacing missing values with a segment mean
    - Replacing missing values using a linear regression
    - Replacing missing values using a k-nearest neighbors algorithm
  - Similarly, when addressing outliers, try out at least two of the following strategies:
    - Outliers removal
    - Replacing outliers with 5 percentile or 95 percentile value
    - Transforming the attribute with outliers using a function, such as logarithm, square root, etc.
- **Reusability of the preprocessing code (5 points).** You should modify your code that serves to preprocess the training set so that it will be possible to reuse it without additional changes to preprocess validation and testing set (their preprocessing is not required in this phase, but the code in the submitted `Jupyter Notebook` has to be ready for it). Therefore, it is expected that the preprocessing will be enveloped in reusable functions or that you will use the `sklearn.pipeline` library. There is often a problem with using information that is not available at the time of data collection (e.g., statistical information about the whole data set when preprocessing training data or even when processing individual observation in the testing set), which can cause the information leak from the validation/testing set during training. Your code should address (prevent) this issue.
- **Rerun of the relevant parts of the exploratory analysis (4 points).** You should answer the question how the data distributions changed after your preprocessing (i.e., rerun only those parts of the exploratory analysis that were somehow affected by the preprocessing).

The report is due in the 9th week of the semester. The pair should present their preprocessing in a `Jupyter Notebook` during the labs to their teacher. Then, one of the pair should submit the report to the AIS before **Sunday, 24th November, 2019, 23:59**.

## Machine learning (max. 15 points)

Our goal in data analysis is not only to get knowledge contained in the original data set, but often also to train a prediction model that will be able to make reasonable predictions for new observations. That requires the use of machine learning. In this project, we will focus on decision trees because of their interpretability.

In this phase, you will obtain a new data set, on which you will demonstrate the reusability of your preprocessing code. Your classifiers will be evaluated together, so that you will be able to see how you stand compared to your classmates.

In the last phase of the project, we expect you to do the following:
- **Preprocessing of the newly obtained data set using your preprocessing code and description of the required changes (2 points).** You should run the preprocessing code from the previous step on the new data set. The new data set will have the same structure as the original one. It is possible that some of the original issues will not be present, but there will not be new ones. If you had to make changes to the code in order to make it run correctly, describe these changes.
- **Manual creation and evaluation of classification decision rules (3 points).** Try to come up with simple rules concerning only one attribute, but also more complicated ones concerning multiple attributes (or their combinations) at once. The rules should be created manually based on the observed dependencies in the data. You are expected to evaluate the rules using the accuracy, precision and recall metrics.
- **Classifier training and testing using decision trees algorithm (4 points).** You are expected to use `CART` algorithm implementation contained in the `scikit-learn` library. Visualize the trained rules (decision trees). Evaluate the trained decision tree using the accuracy, precision and recall metrics. Compare the trained classifier with your manually created (hand-crafted) rules from the previous step.
- **Hyperparameters optimization (4 points).** Explore the hyperparameters of the `CART` classification algorithm and try out their various values in order to minimize overfitting. Explain what these hyperparameters represent. When testing the various hyperparameters settings, use 10-fold cross validation on the training set.
- **Evaluation of the impact of the selected strategy for missing values replacement on the classification accuracy (2 points).** You should evaluate whether the use of different missing values replacement strategies hand any effect on the classification accuracy. Which strategy turned out to be the most suitable for the given problem?

The report is due in the final (12th) week of the semester. The pair should present the results of machine learning in a `Jupyter Notebook` during the labs to their teacher. Then, one of the pair should submit the report to the AIS before **Sunday, 15th December, 2019, 23:59**.
