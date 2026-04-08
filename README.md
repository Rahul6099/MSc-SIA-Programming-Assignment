RAHUL SINGH
MSc SIA 26
Paris School of Economics
 
Automatic Data from Kaggle
!pip install kaggle
!kaggle datasets download -d mlg-ulb/creditcardfraud
!unzip -o creditcardfraud.zip
Requirement already satisfied: kaggle in c:\users\engin\.conda\anacondanew\lib\site-packages (2.0.0)
Requirement already satisfied: bleach in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (6.3.0)
Requirement already satisfied: kagglesdk<1.0,>=0.1.15 in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (0.1.16)
Requirement already satisfied: packaging in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (25.0)
Requirement already satisfied: protobuf in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (5.29.3)
Requirement already satisfied: python-dateutil in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (2.9.0.post0)
Requirement already satisfied: python-slugify in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (8.0.4)
Requirement already satisfied: requests in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (2.32.5)
Requirement already satisfied: tqdm in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (4.67.1)
Requirement already satisfied: urllib3>=1.15.1 in c:\users\engin\.conda\anacondanew\lib\site-packages (from kaggle) (1.26.20)
Requirement already satisfied: webencodings in c:\users\engin\.conda\anacondanew\lib\site-packages (from bleach->kaggle) (0.5.1)
Requirement already satisfied: six>=1.5 in c:\users\engin\.conda\anacondanew\lib\site-packages (from python-dateutil->kaggle) (1.17.0)
Requirement already satisfied: text-unidecode>=1.3 in c:\users\engin\.conda\anacondanew\lib\site-packages (from python-slugify->kaggle) (1.3)
Requirement already satisfied: charset_normalizer<4,>=2 in c:\users\engin\.conda\anacondanew\lib\site-packages (from requests->kaggle) (3.4.4)
Requirement already satisfied: idna<4,>=2.5 in c:\users\engin\.conda\anacondanew\lib\site-packages (from requests->kaggle) (3.11)
Requirement already satisfied: certifi>=2017.4.17 in c:\users\engin\.conda\anacondanew\lib\site-packages (from requests->kaggle) (2025.11.12)
Requirement already satisfied: colorama in c:\users\engin\.conda\anacondanew\lib\site-packages (from tqdm->kaggle) (0.4.6)
Dataset URL: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
License(s): DbCL-1.0
creditcardfraud.zip: Skipping, found more recently modified local copy (use --force to force download)
Archive:  creditcardfraud.zip
  inflating: creditcard.csv          
# This step ensures reproducible and automated data access using the Kaggle API. Instead of manually downloading the dataset, the pipeline programmatically retrieves and extracts the credit card fraud dataset. This improves transparency, replicability, and efficiency of the workflow, aligning with best practices in data-driven research and ensuring that the analysis can be easily reproduced in different environments.
data loading
import pandas as pd

data = pd.read_csv("creditcard.csv", low_memory=False)

print("Shape:", data.shape)
display(data.head(25))
Shape: (284807, 31)
Time	V1	V2	V3	V4	V5	V6	V7	V8	V9	...	V21	V22	V23	V24	V25	V26	V27	V28	Amount	Class
0	0.0	-1.359807	-0.072781	2.536347	1.378155	-0.338321	0.462388	0.239599	0.098698	0.363787	...	-0.018307	0.277838	-0.110474	0.066928	0.128539	-0.189115	0.133558	-0.021053	149.62	0
1	0.0	1.191857	0.266151	0.166480	0.448154	0.060018	-0.082361	-0.078803	0.085102	-0.255425	...	-0.225775	-0.638672	0.101288	-0.339846	0.167170	0.125895	-0.008983	0.014724	2.69	0
2	1.0	-1.358354	-1.340163	1.773209	0.379780	-0.503198	1.800499	0.791461	0.247676	-1.514654	...	0.247998	0.771679	0.909412	-0.689281	-0.327642	-0.139097	-0.055353	-0.059752	378.66	0
3	1.0	-0.966272	-0.185226	1.792993	-0.863291	-0.010309	1.247203	0.237609	0.377436	-1.387024	...	-0.108300	0.005274	-0.190321	-1.175575	0.647376	-0.221929	0.062723	0.061458	123.50	0
4	2.0	-1.158233	0.877737	1.548718	0.403034	-0.407193	0.095921	0.592941	-0.270533	0.817739	...	-0.009431	0.798278	-0.137458	0.141267	-0.206010	0.502292	0.219422	0.215153	69.99	0
5	2.0	-0.425966	0.960523	1.141109	-0.168252	0.420987	-0.029728	0.476201	0.260314	-0.568671	...	-0.208254	-0.559825	-0.026398	-0.371427	-0.232794	0.105915	0.253844	0.081080	3.67	0
6	4.0	1.229658	0.141004	0.045371	1.202613	0.191881	0.272708	-0.005159	0.081213	0.464960	...	-0.167716	-0.270710	-0.154104	-0.780055	0.750137	-0.257237	0.034507	0.005168	4.99	0
7	7.0	-0.644269	1.417964	1.074380	-0.492199	0.948934	0.428118	1.120631	-3.807864	0.615375	...	1.943465	-1.015455	0.057504	-0.649709	-0.415267	-0.051634	-1.206921	-1.085339	40.80	0
8	7.0	-0.894286	0.286157	-0.113192	-0.271526	2.669599	3.721818	0.370145	0.851084	-0.392048	...	-0.073425	-0.268092	-0.204233	1.011592	0.373205	-0.384157	0.011747	0.142404	93.20	0
9	9.0	-0.338262	1.119593	1.044367	-0.222187	0.499361	-0.246761	0.651583	0.069539	-0.736727	...	-0.246914	-0.633753	-0.120794	-0.385050	-0.069733	0.094199	0.246219	0.083076	3.68	0
10	10.0	1.449044	-1.176339	0.913860	-1.375667	-1.971383	-0.629152	-1.423236	0.048456	-1.720408	...	-0.009302	0.313894	0.027740	0.500512	0.251367	-0.129478	0.042850	0.016253	7.80	0
11	10.0	0.384978	0.616109	-0.874300	-0.094019	2.924584	3.317027	0.470455	0.538247	-0.558895	...	0.049924	0.238422	0.009130	0.996710	-0.767315	-0.492208	0.042472	-0.054337	9.99	0
12	10.0	1.249999	-1.221637	0.383930	-1.234899	-1.485419	-0.753230	-0.689405	-0.227487	-2.094011	...	-0.231809	-0.483285	0.084668	0.392831	0.161135	-0.354990	0.026416	0.042422	121.50	0
13	11.0	1.069374	0.287722	0.828613	2.712520	-0.178398	0.337544	-0.096717	0.115982	-0.221083	...	-0.036876	0.074412	-0.071407	0.104744	0.548265	0.104094	0.021491	0.021293	27.50	0
14	12.0	-2.791855	-0.327771	1.641750	1.767473	-0.136588	0.807596	-0.422911	-1.907107	0.755713	...	1.151663	0.222182	1.020586	0.028317	-0.232746	-0.235557	-0.164778	-0.030154	58.80	0
15	12.0	-0.752417	0.345485	2.057323	-1.468643	-1.158394	-0.077850	-0.608581	0.003603	-0.436167	...	0.499625	1.353650	-0.256573	-0.065084	-0.039124	-0.087086	-0.180998	0.129394	15.99	0
16	12.0	1.103215	-0.040296	1.267332	1.289091	-0.735997	0.288069	-0.586057	0.189380	0.782333	...	-0.024612	0.196002	0.013802	0.103758	0.364298	-0.382261	0.092809	0.037051	12.99	0
17	13.0	-0.436905	0.918966	0.924591	-0.727219	0.915679	-0.127867	0.707642	0.087962	-0.665271	...	-0.194796	-0.672638	-0.156858	-0.888386	-0.342413	-0.049027	0.079692	0.131024	0.89	0
18	14.0	-5.401258	-5.450148	1.186305	1.736239	3.049106	-1.763406	-1.559738	0.160842	1.233090	...	-0.503600	0.984460	2.458589	0.042119	-0.481631	-0.621272	0.392053	0.949594	46.80	0
19	15.0	1.492936	-1.029346	0.454795	-1.438026	-1.555434	-0.720961	-1.080664	-0.053127	-1.978682	...	-0.177650	-0.175074	0.040002	0.295814	0.332931	-0.220385	0.022298	0.007602	5.00	0
20	16.0	0.694885	-1.361819	1.029221	0.834159	-1.191209	1.309109	-0.878586	0.445290	-0.446196	...	-0.295583	-0.571955	-0.050881	-0.304215	0.072001	-0.422234	0.086553	0.063499	231.71	0
21	17.0	0.962496	0.328461	-0.171479	2.109204	1.129566	1.696038	0.107712	0.521502	-1.191311	...	0.143997	0.402492	-0.048508	-1.371866	0.390814	0.199964	0.016371	-0.014605	34.09	0
22	18.0	1.166616	0.502120	-0.067300	2.261569	0.428804	0.089474	0.241147	0.138082	-0.989162	...	0.018702	-0.061972	-0.103855	-0.370415	0.603200	0.108556	-0.040521	-0.011418	2.28	0
23	18.0	0.247491	0.277666	1.185471	-0.092603	-1.314394	-0.150116	-0.946365	-1.617935	1.544071	...	1.650180	0.200454	-0.185353	0.423073	0.820591	-0.227632	0.336634	0.250475	22.75	0
24	22.0	-1.946525	-0.044901	-0.405570	-1.013057	2.941968	2.955053	-0.063063	0.855546	0.049967	...	-0.579526	-0.799229	0.870300	0.983421	0.321201	0.149650	0.707519	0.014600	0.89	0
25 rows × 31 columns

# The dataset is loaded into a pandas DataFrame for structured analysis. A quick inspection of the dataset shape and initial rows provides an understanding of its structure, including the number of observations and features. This step ensures that the dataset is correctly imported and ready for further processing, while enabling rapid verification of data integrity and format.
Data Checking
print("\nData types:")
print(data.dtypes.head())

print("\nMissing values:")
print(data.isnull().sum().sum())

print("\nDuplicate rows:")
print(data.duplicated().sum())

print("\nClass counts:")
print(data['Class'].value_counts())
Data types:
Time    float64
V1      float64
V2      float64
V3      float64
V4      float64
dtype: object

Missing values:
0

Duplicate rows:
1081

Class counts:
Class
0    284315
1       492
Name: count, dtype: int64
print(data.shape)
print(data.dtypes)
print(data.isnull().sum())
print(data.duplicated().sum())
(284807, 31)
Time      float64
V1        float64
V2        float64
V3        float64
V4        float64
V5        float64
V6        float64
V7        float64
V8        float64
V9        float64
V10       float64
V11       float64
V12       float64
V13       float64
V14       float64
V15       float64
V16       float64
V17       float64
V18       float64
V19       float64
V20       float64
V21       float64
V22       float64
V23       float64
V24       float64
V25       float64
V26       float64
V27       float64
V28       float64
Amount    float64
Class       int64
dtype: object
Time      0
V1        0
V2        0
V3        0
V4        0
V5        0
V6        0
V7        0
V8        0
V9        0
V10       0
V11       0
V12       0
V13       0
V14       0
V15       0
V16       0
V17       0
V18       0
V19       0
V20       0
V21       0
V22       0
V23       0
V24       0
V25       0
V26       0
V27       0
V28       0
Amount    0
Class     0
dtype: int64
1081
# A preliminary data audit is conducted to assess data quality and structure. This includes checking data types, identifying missing values, and detecting duplicate records. Even though the dataset is generally clean, this step ensures robustness and confirms that no preprocessing issues will affect downstream analysis. It establishes a reliable foundation for modeling and prevents potential biases or inconsistencies.
Target Ration
#STEP4

print(data['Class'].value_counts(normalize=True) * 100)
Class
0    99.827251
1     0.172749
Name: proportion, dtype: float64
# The distribution of the target variable is examined to quantify the imbalance between fraudulent and genuine transactions. The dataset exhibits a highly skewed distribution, with fraud representing a very small proportion of total observations. This characteristic is critical, as it directly impacts model selection, evaluation metrics, and the overall strategy for detecting rare events.
Scale Amount and Time
#5
from sklearn.preprocessing import RobustScaler

scaler = RobustScaler()

data['scaled_amount'] = scaler.fit_transform(data[['Amount']])
data['scaled_time'] = scaler.fit_transform(data[['Time']])

data = data.drop(['Amount', 'Time'], axis=1)
EDA Plotting
#EDA
import matplotlib.pyplot as plt
import seaborn as sns
#############6.1 CLASS DISTRIBUTION
sns.countplot(x='Class', data=data)
plt.title("Fraud vs Genuine")
plt.show()
No description has been provided for this image
#6.2 AMOUNT DISTRIBUTION

sns.histplot(data['scaled_amount'], bins=40)
plt.title("Scaled Amount Distribution")
plt.show()
No description has been provided for this image
#6.3 TIME DISTRIBUTION

sns.histplot(data['scaled_time'], bins=40)
plt.title("Scaled Time Distribution")
plt.show()
No description has been provided for this image
#6.4 AMOUNT BY CLASSSS
sns.boxplot(x='Class', y='scaled_amount', data=data)
plt.title("Amount by Class")
plt.show()
No description has been provided for this image
###############6.5 CORRELATION HEATMAP

plt.figure(figsize=(12,8))
sns.heatmap(data.corr(), cmap='coolwarm', center=0)
plt.title("Correlation Heatmap")
plt.show()
No description has been provided for this image
# Exploratory analysis is conducted to uncover patterns, distributions, and relationships within the dataset. Visualizations highlight the imbalance between classes, skewness in transaction amounts, and potential differences between fraudulent and genuine transactions. Correlation analysis further identifies variables that are strongly associated with fraud, providing insights into the underlying structure of the data.
Data Splits
#7 SPLIT DATA

from sklearn.model_selection import train_test_split

X = data.drop('Class', axis=1)
y = data['Class']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, stratify=y, random_state=42
)

print(X_train.shape, X_test.shape)
(227845, 30) (56962, 30)
# The dataset is divided into training and testing subsets using stratified sampling to preserve the original class distribution. This is particularly important in imbalanced datasets to ensure that both subsets contain representative proportions of fraud cases. The split enables unbiased evaluation of the model’s performance on unseen data while maintaining consistency in class representation.
Model- logistics Regression
# MODEL---
# LOGISTIC REGRESSION 

from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight='balanced', max_iter=1000)
model.fit(X_train, y_train)

LogisticRegression
?i
Parameters
# A logistic regression model is selected as the primary classification approach due to its interpretability, simplicity, and effectiveness for structured data. The model is configured with class weighting to address imbalance in the target variable. This choice allows for a focused and rigorous implementation while maintaining transparency in how predictions are generated.
Prediction
#9 PREDICTIONNNNNNNN

y_pred = model.predict(X_test)
y_prob = model.predict_proba(X_test)[:, 1]
The logistic regression model is trained using the prepared training dataset. Class weighting is applied to ensure that fraudulent transactions receive higher importance during learning. This step enables the model to learn patterns associated with fraud while mitigating the bias toward the majority class, resulting in a more balanced and meaningful predictive performance.
Model Evaluation
#10.1 CLASSIFICATION REPORT
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))
              precision    recall  f1-score   support

           0       1.00      0.98      0.99     56864
           1       0.06      0.92      0.11        98

    accuracy                           0.98     56962
   macro avg       0.53      0.95      0.55     56962
weighted avg       1.00      0.98      0.99     56962

#10.2 COFUSION MATRIX

from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
plt.title("Confusion Matrix")
plt.show()
No description has been provided for this image
#10.3 ROC AUC
from sklearn.metrics import roc_auc_score

print("ROC AUC:", roc_auc_score(y_test, y_prob))
ROC AUC: 0.9720323571887957
The trained model is used to generate predictions on the test dataset. Both class labels and probability scores are computed, allowing for flexible evaluation and threshold adjustment. Probability outputs are particularly important in fraud detection, as they enable ranking of transactions based on risk rather than relying solely on binary classification.Model performance is evaluated using metrics appropriate for imbalanced classification, including precision, recall, F1-score, and ROC-AUC. The confusion matrix provides a detailed breakdown of prediction outcomes. Emphasis is placed on recall, as correctly identifying fraudulent transactions is more critical than overall accuracy in this context.
INTERPRETATION
# The dataset is highly imbalanced, with fraudulent transactions representing a very small share of total observations. After scaling the non-standardized variables and performing exploratory analysis, a logistic regression model with balanced class weights was trained. The results show that recall is more important than raw accuracy in this problem because missing fraudulent transactions is more costly than flagging some genuine transactions.
LIMITATION
# This implementation has several limitations. First, the dataset is highly imbalanced, which makes prediction difficult. Second, logistic regression captures mainly linear relationships and may miss more complex fraud patterns. Third, the anonymized variables reduce interpretability. A natural next step would be to test boosting methods or threshold optimization.
Future Improvement
Future work can extend this analysis by incorporating more advanced models such as gradient boosting or anomaly detection techniques. Additional improvements may include threshold optimization, cost-sensitive learning, and time-aware validation strategies. These approaches can enhance fraud detection performance and better reflect real-world deployment scenarios.
 
