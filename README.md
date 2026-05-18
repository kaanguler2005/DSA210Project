# DSA210Project
DSA210 2026 Spring Term Project
# Motivation:
As usual, many students have been taking university entrance exams to have the right to go to a university, and different countries around the world conduct different exams centralized or not to determine the qualification of each graduate student and where these students deserve to go as universities. Even if the components and style of the exam differ, the main purpose is what is explained above. About these exams, there is a rumor that all students are able to go to qualified universities by working hard. This might be true to such extent. However, my aim in this project is to reveal the fact that “geography is destiny”. To elaborate, the wealthiness of where you reside significantly determines where to study. Additionally, in order for you to familiarize yourself with the project, I am to mainly focus on Türkiye and YKS (The Higher-Education Institutions Examination) which stands for the centralized university exam in Türkiye. Here, I am planning to apply the “geography is destiny” principle on distinct regions in Türkiye.
# Data Collection
## Where did I collect data?
Here are the links from the websites from which I collected data:
### TÜİK:
https://veriportali.tuik.gov.tr/tr/press/53712
### ÖSYM:
https://www.osym.gov.tr/TR,25736/2023-yks-yerlestirme-sonuclarina-iliskin-sayisal-bilgiler.html

https://www.osym.gov.tr/TR,29511/2024-yks-yerlestirme-sonuclarina-iliskin-sayisal-bilgiler.html

https://www.osym.gov.tr/TR,33437/2025-yks-yerlestirme-sonuclarina-iliskin-sayisal-bilgiler.html

### Note: I also collected data from YÖK Atlas. However, the website was renovated, and thus, the exact data has not been published anymore.

## How did I collect data?
Even if I planned to use API for YÖK Atlas, due to the dynamic-style webpage, no API emerged to provide sufficiently extensive data if I do not click any button on the website. Hence, without using web-scraping or API, I just rearranged the data into a suitable form.
### Important Notes:
1. I constrained the time-length to be between 2023-2025.
### Reasoning:
If I chose the time-length to be too broad; due to the instability of economy, increasing inflation rate, and changing household income rate; the data would be misleading in terms of the ranking of the regions by socioeconomic status.

2. I focused on "Computer Science" program for each university.
### Reasoning:
As mentioned above, due to the dynamic structure of the webpage for YÖK Atlas, I could not collect data by direct communication with the website. Since "Computer Science" is common among almost all universities, in order to avoid time-wasting, I selected this program as reference for each university. 

I did not directly use raw data, but I did rearrange the data into suitable form. Here is the prosedure of how I converted and combined raw datasets into proper datasets in order for them to be suitable for the next stages of the project.
### TÜİK:
### Issues:
1. These datasets indicate average household income value pairwise, i.e., one for 2023 and 2024, the other one for 2024 and 2025.
### How to fix?
I rewrote the dataset into another document where household income for each year is clearly specified.

2. TÜİK prepares the dataset considering districts in the form of TRXY, not regions
### How to fix?
I rewrote the dataset adding another column indicating which district belongs to which region.

Here is the link for final version of TÜİK income dataset:
https://1drv.ms/x/c/d6557b72095b37c2/IQBVfcPhnN1VSKGj9UcCayWLAWPk7brGnrdx6BG6Ay8EWgs?e=r5Fc2O

### ÖSYM:
### Issues:
1. These datasets are separated by "tablo3" and "tablo4" where "tablo3" represents two-year programs and "tablo4" represents four-year programs.
### How to Fix?
No need to fix anything since I considered "Computer Science" as reference and this is a four-year program. Hence, I rearrange the document just including the "Computer Science" program for each university and its score.

Here is the link for final versios of ÖSYM 2023, 2024, and 2025 accommodation result datasets respectively:
https://1drv.ms/x/c/d6557b72095b37c2/IQC_8d84juyJTIdb6Z_-EFkdAbYIOzhPMSSS8jPsO4JHNBU?e=ylpxh1

https://1drv.ms/x/c/d6557b72095b37c2/IQA9MFp2DAX4SbAMgelw6jiyAQUXhXD3qh2aglS9TlW2KD0?e=sg9Y8I

https://1drv.ms/x/c/d6557b72095b37c2/IQCatDiPuWYURZrkY5nJR70vAX_-ZRavx6aYATGdNbxrSGE?e=Mes1pN
### YÖK Atlas:
As I mentioned, I prepared this data manually by writing down all findings on an excel file, i.e., I did not have a ready dataset to convert.

Here is the link for the csv of the excel file manually written:
https://1drv.ms/x/c/d6557b72095b37c2/IQAA7vStpq9jQqQ9_e483HDzAdeWHkcWZpbu0d0A3bTMAD8?e=174fNE
# EDA and Data Visualization
### Note: For this part, you can find more information in "TermProjectPhase2.ipynb"
### EDA Part:
In this stage, I computed:
   1. For each year (2023, 2024, and 2025) the average score of each university by taking the average of the lowest score and highest score of students.
   2. For each university, the average of resulting scores in 2023, 2024, and 2025 from (1).
   ### These two computations were necessary to construct the dataframe.
   3. For each region, total household income year-by-year (for 2023, 2024, and 2025). 
   ### This is crucial for EDA since it gives some insights about the main purpose of the project by comparing and ranking the income results for each region.
   4. For each region, the average income per year from (3).
   ### The relation of this computation as a result of data visualization is explained under the data visualization part.
   5. For each university, the proportion (percentage) of the number of students coming to the university for each region.
### Data Visualization Part:
In this stage, I utilized histogram with categorical data (Region) to trace the change in income rate year be year and to make the categorical data ordinal by ranking them in terms of income rate values.
#### Observations:
As observed from the histogram, the highest income is in 2025 and the lowest income is in 2023 for all regions, which indicates that the data is unstationary.
In order to make it stationary and comparable, computing average income per year for each region would be better.
# Hypothesis Testing Part
### Note: For this part, you can find more information in "TermProjectPhase2.ipynb"
## Null Hypothesis (H0): 
There is no relation betweeen the region and the score of university to sudy at.
## Alternative Hypothesis (H1): 
There is a significant relation between the region and the score of the univerisity.
## Test to Be Applied:
Chi-Square Test of Independence
## Test Results:
p-value: 4.0126500164510436e-285

degrees of freedom: 42

Chi-Square value: 1489.6024244030439
#### Conclusion: Strong rejection of H0. Hence, test results in as successful.
#### Interpretation: There is an intimate relationship between the region and the ranking of university. Hence, YKS does not resolve equity in terms of socioeconomic degree, and statistically, no equal chances to go to a specific university occur among Türkiye.
# ML (Machine Learning) and Model Evaluation Part
### Note: For this part, you can find more information in "TermProjectPhase3.ipynb"
## Aim: 
To classify universities as "high", "medium", or "low" by considering proportions of students from different regions.
## Machine Learning (ML) Mathod to Be Applied:
Decision Tree Algorithm
#### Features
Marmara, Ege, Ic Anadolu, Karadeniz, Akdeniz, Dogu Anadolu, Guneydogu Anadolu (each of them are numerical data (proportion of students).
#### Target 
Level (ordinal but categorical data, which can take "High", "Medium", or "Low" as its value.
## Performance Evaluation:
Confusion Matrix

Classification Report
## Finding the Best Decision Tree Model:
#### Here, two approaches are considered (I did splitting by these two approaches):
  1. Gini Index
  2. Entropy
### Gini Index:
  #### Tree Depth:
  4
  #### Accuracy:
  0.50
  #### Note: since accuracy itself may be misleading to evaluate overall performance, classification report needs to be examined:
  ### Classification Report:
  #### f1-scores (It is high if both precision and recall are high, so it gives more insights):
  High:  0.32
  
  Low:  0.80
  
  Medium:  0.56
  #### Important Observation: The data is clearly biased since f1-scores are not equal among different classes.
  #### Here, "Low" is tested more accurately whereas "High" is tested badly.
### Entropy:
  #### Tree Depth:
  3
  #### Accuracy:
  0.64
  #### Note: For same reason, it also needs to be checked f1-scores for each class and compare:
  High:  0.46
  
  Low:  0.33
  
  Medium:  0.76
  #### Important Observation: The data is biased and even behaves differently than the results of Gini Index.
  #### Here, "Medium" is tested more accurately, and "Low" is tested the worst, which mostly opposes to the observation in Gini Index.
  #### However, Entropy seems to detect the information gain more accurately.
  ### Conclusion: Decision tree model moderately determines the dependence between the university ranking and the region.
  # What could be done better and what future extensions could be explored?
  1. It would be better to use a communicatable website instead of YÖK Atlas to collect regional distribution for each university directly.
  2. I should have focused on parameters (sample size etc.) as well as hyperparameters (tree depth etc.) not just changing hyperparameters in order to make the f1-score         values more consistent.
# LLM Disclosure
I consulted chatGPT to ask what are the stages of API to collect data

I consulted chatGPT to ask how to better evaluate classification report during the decision tree phase
# Acknowledgements
#### Website Links: 
https://www.tuik.gov.tr/

https://www.osym.gov.tr/

https://yokatlas.yok.gov.tr/
(Since YÖK Atlas was renovated, the current link does not contain the exact data.)
# Sabancı University Spring 2025-2026 DSA210 Term Project

   
