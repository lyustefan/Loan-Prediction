# Loan Prediction
* **Background**: Lending Club is a US peer-to-peer lending company, headquartered in San Francisco, California. It was the first peer-to-peer lender to register its offerings as securities with the Securities and Exchange Commission (SEC), and to offer loan trading on a secondary market. Lending Club is the world's largest peer-to-peer lending platform. The company claims that 15.98 billion in loans had been originated through its platform up to December 31, 2015. Lending Club enables borrowers to create unsecured personal loans between 1,0000 and 40,000. The standard loan period is three years. Investors can search and browse the loan listings on Lending Club website and select loans that they want to invest in based on the information supplied about the borrower, amount of loan, loan grade, and loan purpose. Investors make money from interest. Lending Club makes money by charging borrowers an origination fee and investors a service fee.

* **Introduction**: Before a loan is issued to a borrower, lending club will collect information on a certain individual, generally including two aspects. The first one is personal information which includes age, sex, annual income, and etc. The second is information from third-party which includes FICO score, credit history, delinquency records, and etc. Lending club will then use a predictive model to predict whether this individual will default on loan, in order to make a final decision. The application of machine learning in fraud detection and risk management is very important to Lending Club. In additional to operational expense, default risk is a major component of a company’s loss. Default risk refers to loss exposure when a borrower fails to fulfill its debt obligation, in other words, losing the ability to pay back its loans. Generally, lending club tends to avoid ‘bad’ loans because trivial increase in net profit could leads to tremendous loss due to default. Often, both internal such as individual attributes and external factors such as economic change need to be considered to find an optimal strategy. In the project, we will focus on building internal model to predict the probability of default and classify loan application into default and non-default. The incentive behind this project is to help Lending Club perform better risk management as well as maximize its profit.

* **Dataset**: The dataset is provided by Kaggle in a competition sponsored by Lending Club. A complete data can be found on Lending Club’s website (https://www.lendingclub.com/info/download- data.action). The data contains all loans from 2012-2013, which has 200k rows and 145 features. Features included are demographic information, financial information (annual income, grade, accrued payment, oustanding balance, number of open accounts, number of deliquencies in the past 2 years), loan-related information (term, loan amount, loan purpose, interest rate, etc). Overall default rate is 2%.

* **Data Preprocessing and EDA**:
  * Missing Value: Dropped features > 80% missing, mean-imputation
  * `Term`, `Grade`, `Delinquency`, `Annual Income` seems to be highly correlated with default
 
* **Feature Engineering**:
  * Wrapper: Wrapper method is also known as the feature ranking with recursive feature elimination and implemented using sklearn machine learning module. The goal of RFE is to select features recursively by considering a smaller and smaller subsets of features. Initially, the model is trained on all of the variables and feature important of each variable is computed. Then the least significant variable is dropped from the model. This process is repeated until a desired number of features is reached. We used RFE to dropped until we have 30 features left.
  * Filter: Then we used Pearson correlation based filter method to remove features that are highly correlated.

* **Model Building**:
  * Xgboost:
  * SMOTE: Synthetic Minority Over-sampling Technique
Over-sampling technique by creating synthetic examples rather than over-sampling with replacement. The minority class is over-sampled by taking each minority class sample and introduce synthetic examples along the line segments joining any/all of the k minority class nearest neighbors.

* **Recommendation**:
  * RFE with cross-validation to determine number of features to include
  * Use more sophicated model like Neural Network
