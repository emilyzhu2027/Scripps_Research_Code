## Scripps_Research_Code
Some snippets of code from my work as a data science intern at the Scripps Research Institute under the direction of the Dr. Zorrilla Lab

#### General Description:
At the Dr. Zorrilla Lab, I've been working on using UK Biobank data to better understand what socioeconomic and environmental factors are connected with alcohol use disorder recurrence. Utilizing data science techniques, I've transformed and performed several analyses of the given data, with the eventual end goal of creating Random Forest Classification models trained to predict recurrence from these factors. 

In this repository, I wanted to showcase some of the code that I've been working on recently without divulging any private or individual data. So, I selected some code files from the overall project to show but won't be uploading the full project or any of the data files.

#### Progress:
##### Step 1: Importing and Selecting Features
* After web scraping the UKB showcase for socioeconomic and environmental factors, I was able to identify the broad range of factors that we might consider in our analysis. We took a more manual look at ICD hospital codes to select those that might be relevant to this analysis as well. 
* Following this, I calculated the percentage of missing data for each participant and the percentage of missing data for the features we selected. For participants or features with data that was over 20% missing, we opted to drop them.
* Given that ICD codes were presented as a binary (0 if the diagnosis wasn't made, 1 if the diagnosis was made), the ICD code features all had 0% missing. So to narrow down the ICD codes to those that are most important, I identified the knee point of the ICD diagnoses' frequencies and kept all the ICD code features prior to the knee point. (seen in "ICDBreakpoint.ipynb")
##### Step 2: Transforming Data
* With the selected features and participants narrowed down, I normalized the features that weren't already normal and scaled the data using Box-Cox and Standard Scaler. The categorical features were then one-hot encoded, with missing or non-responsive answers accounting for columns as well.
* Finally, I conducted MICE imputation to fill in missing values.
#### Step 3: Further Feature Selection (Correlation Matrices and PCA)
* In order to analyze and further narrow down the number of features needed, I calculated several correlation matrices between the features and the recurrence variable. With these correlation scores, I was able to eliminate any overly correlated variables. (seen in "Female_CorrMatrix.ipynb") Additionally, I also conducted principal component analysis which further demonstrated what features played the largest role in the variance and offered a way to combine features into fewer principal components. (seen in "PCA_PostImp.ipynb")

#### File Descriptions:
* **ICDBreakpoint-Github.ipynb**: This file identifies what ICD codes to include by graphing the frequencies of each ICD code and calculating the point where the frequencies suddenly decrease to find the most frequently occuring ICD codes. All ICD codes prior to this breakpoint were kept for the analysis.

* **Female_CorrMatrix-Github.ipynb**: This file calculates the correlation matrices for female data. It calculates the correlation between the features to identify any features that are overly correlated with one another using Cramer's V for comparing categorical features and Pearson for comparing continuous features.

* **PCA_PostImp-Github.ipynb**: This file conducts principal component analysis on the data; calculating the principal component scores, eigenvalues, loadings, and more. It also graphs and provides visualization for the PCA analysis to better understand what principal components are most important and what features contribute the most to the principal components.
  
#### Credits:
Everything completed here was under the guidance and mentorship of Dr. Zorrilla and the help of other lab members.
