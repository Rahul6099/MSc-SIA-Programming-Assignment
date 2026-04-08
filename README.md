# RAHUL SINGH
# MSc SIA 26
# Paris School of Economics


```python

```

# Automatic Data from Kaggle


```python
!pip install kaggle
!kaggle datasets download -d mlg-ulb/creditcardfraud
!unzip -o creditcardfraud.zip
```

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
    
#
This step ensures reproducible and automated data access using the Kaggle API. Instead of manually downloading the dataset, the pipeline programmatically retrieves and extracts the credit card fraud dataset. This improves transparency, replicability, and efficiency of the workflow, aligning with best practices in data-driven research and ensuring that the analysis can be easily reproduced in different environments.
# data loading 


```python
import pandas as pd

data = pd.read_csv("creditcard.csv", low_memory=False)

print("Shape:", data.shape)
display(data.head(25))
```

    Shape: (284807, 31)
    


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Time</th>
      <th>V1</th>
      <th>V2</th>
      <th>V3</th>
      <th>V4</th>
      <th>V5</th>
      <th>V6</th>
      <th>V7</th>
      <th>V8</th>
      <th>V9</th>
      <th>...</th>
      <th>V21</th>
      <th>V22</th>
      <th>V23</th>
      <th>V24</th>
      <th>V25</th>
      <th>V26</th>
      <th>V27</th>
      <th>V28</th>
      <th>Amount</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>-1.359807</td>
      <td>-0.072781</td>
      <td>2.536347</td>
      <td>1.378155</td>
      <td>-0.338321</td>
      <td>0.462388</td>
      <td>0.239599</td>
      <td>0.098698</td>
      <td>0.363787</td>
      <td>...</td>
      <td>-0.018307</td>
      <td>0.277838</td>
      <td>-0.110474</td>
      <td>0.066928</td>
      <td>0.128539</td>
      <td>-0.189115</td>
      <td>0.133558</td>
      <td>-0.021053</td>
      <td>149.62</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.0</td>
      <td>1.191857</td>
      <td>0.266151</td>
      <td>0.166480</td>
      <td>0.448154</td>
      <td>0.060018</td>
      <td>-0.082361</td>
      <td>-0.078803</td>
      <td>0.085102</td>
      <td>-0.255425</td>
      <td>...</td>
      <td>-0.225775</td>
      <td>-0.638672</td>
      <td>0.101288</td>
      <td>-0.339846</td>
      <td>0.167170</td>
      <td>0.125895</td>
      <td>-0.008983</td>
      <td>0.014724</td>
      <td>2.69</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>-1.358354</td>
      <td>-1.340163</td>
      <td>1.773209</td>
      <td>0.379780</td>
      <td>-0.503198</td>
      <td>1.800499</td>
      <td>0.791461</td>
      <td>0.247676</td>
      <td>-1.514654</td>
      <td>...</td>
      <td>0.247998</td>
      <td>0.771679</td>
      <td>0.909412</td>
      <td>-0.689281</td>
      <td>-0.327642</td>
      <td>-0.139097</td>
      <td>-0.055353</td>
      <td>-0.059752</td>
      <td>378.66</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>-0.966272</td>
      <td>-0.185226</td>
      <td>1.792993</td>
      <td>-0.863291</td>
      <td>-0.010309</td>
      <td>1.247203</td>
      <td>0.237609</td>
      <td>0.377436</td>
      <td>-1.387024</td>
      <td>...</td>
      <td>-0.108300</td>
      <td>0.005274</td>
      <td>-0.190321</td>
      <td>-1.175575</td>
      <td>0.647376</td>
      <td>-0.221929</td>
      <td>0.062723</td>
      <td>0.061458</td>
      <td>123.50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2.0</td>
      <td>-1.158233</td>
      <td>0.877737</td>
      <td>1.548718</td>
      <td>0.403034</td>
      <td>-0.407193</td>
      <td>0.095921</td>
      <td>0.592941</td>
      <td>-0.270533</td>
      <td>0.817739</td>
      <td>...</td>
      <td>-0.009431</td>
      <td>0.798278</td>
      <td>-0.137458</td>
      <td>0.141267</td>
      <td>-0.206010</td>
      <td>0.502292</td>
      <td>0.219422</td>
      <td>0.215153</td>
      <td>69.99</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2.0</td>
      <td>-0.425966</td>
      <td>0.960523</td>
      <td>1.141109</td>
      <td>-0.168252</td>
      <td>0.420987</td>
      <td>-0.029728</td>
      <td>0.476201</td>
      <td>0.260314</td>
      <td>-0.568671</td>
      <td>...</td>
      <td>-0.208254</td>
      <td>-0.559825</td>
      <td>-0.026398</td>
      <td>-0.371427</td>
      <td>-0.232794</td>
      <td>0.105915</td>
      <td>0.253844</td>
      <td>0.081080</td>
      <td>3.67</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4.0</td>
      <td>1.229658</td>
      <td>0.141004</td>
      <td>0.045371</td>
      <td>1.202613</td>
      <td>0.191881</td>
      <td>0.272708</td>
      <td>-0.005159</td>
      <td>0.081213</td>
      <td>0.464960</td>
      <td>...</td>
      <td>-0.167716</td>
      <td>-0.270710</td>
      <td>-0.154104</td>
      <td>-0.780055</td>
      <td>0.750137</td>
      <td>-0.257237</td>
      <td>0.034507</td>
      <td>0.005168</td>
      <td>4.99</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7.0</td>
      <td>-0.644269</td>
      <td>1.417964</td>
      <td>1.074380</td>
      <td>-0.492199</td>
      <td>0.948934</td>
      <td>0.428118</td>
      <td>1.120631</td>
      <td>-3.807864</td>
      <td>0.615375</td>
      <td>...</td>
      <td>1.943465</td>
      <td>-1.015455</td>
      <td>0.057504</td>
      <td>-0.649709</td>
      <td>-0.415267</td>
      <td>-0.051634</td>
      <td>-1.206921</td>
      <td>-1.085339</td>
      <td>40.80</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>7.0</td>
      <td>-0.894286</td>
      <td>0.286157</td>
      <td>-0.113192</td>
      <td>-0.271526</td>
      <td>2.669599</td>
      <td>3.721818</td>
      <td>0.370145</td>
      <td>0.851084</td>
      <td>-0.392048</td>
      <td>...</td>
      <td>-0.073425</td>
      <td>-0.268092</td>
      <td>-0.204233</td>
      <td>1.011592</td>
      <td>0.373205</td>
      <td>-0.384157</td>
      <td>0.011747</td>
      <td>0.142404</td>
      <td>93.20</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9.0</td>
      <td>-0.338262</td>
      <td>1.119593</td>
      <td>1.044367</td>
      <td>-0.222187</td>
      <td>0.499361</td>
      <td>-0.246761</td>
      <td>0.651583</td>
      <td>0.069539</td>
      <td>-0.736727</td>
      <td>...</td>
      <td>-0.246914</td>
      <td>-0.633753</td>
      <td>-0.120794</td>
      <td>-0.385050</td>
      <td>-0.069733</td>
      <td>0.094199</td>
      <td>0.246219</td>
      <td>0.083076</td>
      <td>3.68</td>
      <td>0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10.0</td>
      <td>1.449044</td>
      <td>-1.176339</td>
      <td>0.913860</td>
      <td>-1.375667</td>
      <td>-1.971383</td>
      <td>-0.629152</td>
      <td>-1.423236</td>
      <td>0.048456</td>
      <td>-1.720408</td>
      <td>...</td>
      <td>-0.009302</td>
      <td>0.313894</td>
      <td>0.027740</td>
      <td>0.500512</td>
      <td>0.251367</td>
      <td>-0.129478</td>
      <td>0.042850</td>
      <td>0.016253</td>
      <td>7.80</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>10.0</td>
      <td>0.384978</td>
      <td>0.616109</td>
      <td>-0.874300</td>
      <td>-0.094019</td>
      <td>2.924584</td>
      <td>3.317027</td>
      <td>0.470455</td>
      <td>0.538247</td>
      <td>-0.558895</td>
      <td>...</td>
      <td>0.049924</td>
      <td>0.238422</td>
      <td>0.009130</td>
      <td>0.996710</td>
      <td>-0.767315</td>
      <td>-0.492208</td>
      <td>0.042472</td>
      <td>-0.054337</td>
      <td>9.99</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>10.0</td>
      <td>1.249999</td>
      <td>-1.221637</td>
      <td>0.383930</td>
      <td>-1.234899</td>
      <td>-1.485419</td>
      <td>-0.753230</td>
      <td>-0.689405</td>
      <td>-0.227487</td>
      <td>-2.094011</td>
      <td>...</td>
      <td>-0.231809</td>
      <td>-0.483285</td>
      <td>0.084668</td>
      <td>0.392831</td>
      <td>0.161135</td>
      <td>-0.354990</td>
      <td>0.026416</td>
      <td>0.042422</td>
      <td>121.50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>11.0</td>
      <td>1.069374</td>
      <td>0.287722</td>
      <td>0.828613</td>
      <td>2.712520</td>
      <td>-0.178398</td>
      <td>0.337544</td>
      <td>-0.096717</td>
      <td>0.115982</td>
      <td>-0.221083</td>
      <td>...</td>
      <td>-0.036876</td>
      <td>0.074412</td>
      <td>-0.071407</td>
      <td>0.104744</td>
      <td>0.548265</td>
      <td>0.104094</td>
      <td>0.021491</td>
      <td>0.021293</td>
      <td>27.50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>12.0</td>
      <td>-2.791855</td>
      <td>-0.327771</td>
      <td>1.641750</td>
      <td>1.767473</td>
      <td>-0.136588</td>
      <td>0.807596</td>
      <td>-0.422911</td>
      <td>-1.907107</td>
      <td>0.755713</td>
      <td>...</td>
      <td>1.151663</td>
      <td>0.222182</td>
      <td>1.020586</td>
      <td>0.028317</td>
      <td>-0.232746</td>
      <td>-0.235557</td>
      <td>-0.164778</td>
      <td>-0.030154</td>
      <td>58.80</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>12.0</td>
      <td>-0.752417</td>
      <td>0.345485</td>
      <td>2.057323</td>
      <td>-1.468643</td>
      <td>-1.158394</td>
      <td>-0.077850</td>
      <td>-0.608581</td>
      <td>0.003603</td>
      <td>-0.436167</td>
      <td>...</td>
      <td>0.499625</td>
      <td>1.353650</td>
      <td>-0.256573</td>
      <td>-0.065084</td>
      <td>-0.039124</td>
      <td>-0.087086</td>
      <td>-0.180998</td>
      <td>0.129394</td>
      <td>15.99</td>
      <td>0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>12.0</td>
      <td>1.103215</td>
      <td>-0.040296</td>
      <td>1.267332</td>
      <td>1.289091</td>
      <td>-0.735997</td>
      <td>0.288069</td>
      <td>-0.586057</td>
      <td>0.189380</td>
      <td>0.782333</td>
      <td>...</td>
      <td>-0.024612</td>
      <td>0.196002</td>
      <td>0.013802</td>
      <td>0.103758</td>
      <td>0.364298</td>
      <td>-0.382261</td>
      <td>0.092809</td>
      <td>0.037051</td>
      <td>12.99</td>
      <td>0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>13.0</td>
      <td>-0.436905</td>
      <td>0.918966</td>
      <td>0.924591</td>
      <td>-0.727219</td>
      <td>0.915679</td>
      <td>-0.127867</td>
      <td>0.707642</td>
      <td>0.087962</td>
      <td>-0.665271</td>
      <td>...</td>
      <td>-0.194796</td>
      <td>-0.672638</td>
      <td>-0.156858</td>
      <td>-0.888386</td>
      <td>-0.342413</td>
      <td>-0.049027</td>
      <td>0.079692</td>
      <td>0.131024</td>
      <td>0.89</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>14.0</td>
      <td>-5.401258</td>
      <td>-5.450148</td>
      <td>1.186305</td>
      <td>1.736239</td>
      <td>3.049106</td>
      <td>-1.763406</td>
      <td>-1.559738</td>
      <td>0.160842</td>
      <td>1.233090</td>
      <td>...</td>
      <td>-0.503600</td>
      <td>0.984460</td>
      <td>2.458589</td>
      <td>0.042119</td>
      <td>-0.481631</td>
      <td>-0.621272</td>
      <td>0.392053</td>
      <td>0.949594</td>
      <td>46.80</td>
      <td>0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>15.0</td>
      <td>1.492936</td>
      <td>-1.029346</td>
      <td>0.454795</td>
      <td>-1.438026</td>
      <td>-1.555434</td>
      <td>-0.720961</td>
      <td>-1.080664</td>
      <td>-0.053127</td>
      <td>-1.978682</td>
      <td>...</td>
      <td>-0.177650</td>
      <td>-0.175074</td>
      <td>0.040002</td>
      <td>0.295814</td>
      <td>0.332931</td>
      <td>-0.220385</td>
      <td>0.022298</td>
      <td>0.007602</td>
      <td>5.00</td>
      <td>0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>16.0</td>
      <td>0.694885</td>
      <td>-1.361819</td>
      <td>1.029221</td>
      <td>0.834159</td>
      <td>-1.191209</td>
      <td>1.309109</td>
      <td>-0.878586</td>
      <td>0.445290</td>
      <td>-0.446196</td>
      <td>...</td>
      <td>-0.295583</td>
      <td>-0.571955</td>
      <td>-0.050881</td>
      <td>-0.304215</td>
      <td>0.072001</td>
      <td>-0.422234</td>
      <td>0.086553</td>
      <td>0.063499</td>
      <td>231.71</td>
      <td>0</td>
    </tr>
    <tr>
      <th>21</th>
      <td>17.0</td>
      <td>0.962496</td>
      <td>0.328461</td>
      <td>-0.171479</td>
      <td>2.109204</td>
      <td>1.129566</td>
      <td>1.696038</td>
      <td>0.107712</td>
      <td>0.521502</td>
      <td>-1.191311</td>
      <td>...</td>
      <td>0.143997</td>
      <td>0.402492</td>
      <td>-0.048508</td>
      <td>-1.371866</td>
      <td>0.390814</td>
      <td>0.199964</td>
      <td>0.016371</td>
      <td>-0.014605</td>
      <td>34.09</td>
      <td>0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>18.0</td>
      <td>1.166616</td>
      <td>0.502120</td>
      <td>-0.067300</td>
      <td>2.261569</td>
      <td>0.428804</td>
      <td>0.089474</td>
      <td>0.241147</td>
      <td>0.138082</td>
      <td>-0.989162</td>
      <td>...</td>
      <td>0.018702</td>
      <td>-0.061972</td>
      <td>-0.103855</td>
      <td>-0.370415</td>
      <td>0.603200</td>
      <td>0.108556</td>
      <td>-0.040521</td>
      <td>-0.011418</td>
      <td>2.28</td>
      <td>0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>18.0</td>
      <td>0.247491</td>
      <td>0.277666</td>
      <td>1.185471</td>
      <td>-0.092603</td>
      <td>-1.314394</td>
      <td>-0.150116</td>
      <td>-0.946365</td>
      <td>-1.617935</td>
      <td>1.544071</td>
      <td>...</td>
      <td>1.650180</td>
      <td>0.200454</td>
      <td>-0.185353</td>
      <td>0.423073</td>
      <td>0.820591</td>
      <td>-0.227632</td>
      <td>0.336634</td>
      <td>0.250475</td>
      <td>22.75</td>
      <td>0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>22.0</td>
      <td>-1.946525</td>
      <td>-0.044901</td>
      <td>-0.405570</td>
      <td>-1.013057</td>
      <td>2.941968</td>
      <td>2.955053</td>
      <td>-0.063063</td>
      <td>0.855546</td>
      <td>0.049967</td>
      <td>...</td>
      <td>-0.579526</td>
      <td>-0.799229</td>
      <td>0.870300</td>
      <td>0.983421</td>
      <td>0.321201</td>
      <td>0.149650</td>
      <td>0.707519</td>
      <td>0.014600</td>
      <td>0.89</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>25 rows × 31 columns</p>
</div>

#
The dataset is loaded into a pandas DataFrame for structured analysis. A quick inspection of the dataset shape and initial rows provides an understanding of its structure, including the number of observations and features. This step ensures that the dataset is correctly imported and ready for further processing, while enabling rapid verification of data integrity and format.
# Data Checking


```python
print("\nData types:")
print(data.dtypes.head())

print("\nMissing values:")
print(data.isnull().sum().sum())

print("\nDuplicate rows:")
print(data.duplicated().sum())

print("\nClass counts:")
print(data['Class'].value_counts())
```

    
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
    


```python
print(data.shape)
print(data.dtypes)
print(data.isnull().sum())
print(data.duplicated().sum())
```

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
    
#
A preliminary data audit is conducted to assess data quality and structure. This includes checking data types, identifying missing values, and detecting duplicate records. Even though the dataset is generally clean, this step ensures robustness and confirms that no preprocessing issues will affect downstream analysis. It establishes a reliable foundation for modeling and prevents potential biases or inconsistencies.
# Target Ration


```python
#STEP4

print(data['Class'].value_counts(normalize=True) * 100)
```

    Class
    0    99.827251
    1     0.172749
    Name: proportion, dtype: float64
    
# The distribution of the target variable is examined to quantify the imbalance between fraudulent and genuine transactions. The dataset exhibits a highly skewed distribution, with fraud representing a very small proportion of total observations. This characteristic is critical, as it directly impacts model selection, evaluation metrics, and the overall strategy for detecting rare events.
# Scale Amount and Time


```python
#5
from sklearn.preprocessing import RobustScaler

scaler = RobustScaler()

data['scaled_amount'] = scaler.fit_transform(data[['Amount']])
data['scaled_time'] = scaler.fit_transform(data[['Time']])

data = data.drop(['Amount', 'Time'], axis=1)
```

# EDA Plotting


```python
#EDA
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
#############6.1 CLASS DISTRIBUTION
sns.countplot(x='Class', data=data)
plt.title("Fraud vs Genuine")
plt.show()
```


    
![png](output_19_0.png)
    



```python
#6.2 AMOUNT DISTRIBUTION

sns.histplot(data['scaled_amount'], bins=40)
plt.title("Scaled Amount Distribution")
plt.show()
```


    
![png](output_20_0.png)
    



```python
#6.3 TIME DISTRIBUTION

sns.histplot(data['scaled_time'], bins=40)
plt.title("Scaled Time Distribution")
plt.show()
```


    
![png](output_21_0.png)
    



```python
#6.4 AMOUNT BY CLASSSS
sns.boxplot(x='Class', y='scaled_amount', data=data)
plt.title("Amount by Class")
plt.show()
```


    
![png](output_22_0.png)
    



```python
###############6.5 CORRELATION HEATMAP

plt.figure(figsize=(12,8))
sns.heatmap(data.corr(), cmap='coolwarm', center=0)
plt.title("Correlation Heatmap")
plt.show()
```


    
![png](output_23_0.png)
    

#
Exploratory analysis is conducted to uncover patterns, distributions, and relationships within the dataset. Visualizations highlight the imbalance between classes, skewness in transaction amounts, and potential differences between fraudulent and genuine transactions. Correlation analysis further identifies variables that are strongly associated with fraud, providing insights into the underlying structure of the data.
# Data Splits


```python
#7 SPLIT DATA

from sklearn.model_selection import train_test_split

X = data.drop('Class', axis=1)
y = data['Class']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, stratify=y, random_state=42
)

print(X_train.shape, X_test.shape)
```

    (227845, 30) (56962, 30)
    
#
The dataset is divided into training and testing subsets using stratified sampling to preserve the original class distribution. This is particularly important in imbalanced datasets to ensure that both subsets contain representative proportions of fraud cases. The split enables unbiased evaluation of the model’s performance on unseen data while maintaining consistency in class representation.
# Model- logistics Regression


```python
# MODEL---
# LOGISTIC REGRESSION 

from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight='balanced', max_iter=1000)
model.fit(X_train, y_train)
```




<style>#sk-container-id-1 {
  /* Definition of color scheme common for light and dark mode */
  --sklearn-color-text: #000;
  --sklearn-color-text-muted: #666;
  --sklearn-color-line: gray;
  /* Definition of color scheme for unfitted estimators */
  --sklearn-color-unfitted-level-0: #fff5e6;
  --sklearn-color-unfitted-level-1: #f6e4d2;
  --sklearn-color-unfitted-level-2: #ffe0b3;
  --sklearn-color-unfitted-level-3: chocolate;
  /* Definition of color scheme for fitted estimators */
  --sklearn-color-fitted-level-0: #f0f8ff;
  --sklearn-color-fitted-level-1: #d4ebff;
  --sklearn-color-fitted-level-2: #b3dbfd;
  --sklearn-color-fitted-level-3: cornflowerblue;

  /* Specific color for light theme */
  --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, white)));
  --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-icon: #696969;

  @media (prefers-color-scheme: dark) {
    /* Redefinition of color scheme for dark theme */
    --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, #111)));
    --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-icon: #878787;
  }
}

#sk-container-id-1 {
  color: var(--sklearn-color-text);
}

#sk-container-id-1 pre {
  padding: 0;
}

#sk-container-id-1 input.sk-hidden--visually {
  border: 0;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

#sk-container-id-1 div.sk-dashed-wrapped {
  border: 1px dashed var(--sklearn-color-line);
  margin: 0 0.4em 0.5em 0.4em;
  box-sizing: border-box;
  padding-bottom: 0.4em;
  background-color: var(--sklearn-color-background);
}

#sk-container-id-1 div.sk-container {
  /* jupyter's `normalize.less` sets `[hidden] { display: none; }`
     but bootstrap.min.css set `[hidden] { display: none !important; }`
     so we also need the `!important` here to be able to override the
     default hidden behavior on the sphinx rendered scikit-learn.org.
     See: https://github.com/scikit-learn/scikit-learn/issues/21755 */
  display: inline-block !important;
  position: relative;
}

#sk-container-id-1 div.sk-text-repr-fallback {
  display: none;
}

div.sk-parallel-item,
div.sk-serial,
div.sk-item {
  /* draw centered vertical line to link estimators */
  background-image: linear-gradient(var(--sklearn-color-text-on-default-background), var(--sklearn-color-text-on-default-background));
  background-size: 2px 100%;
  background-repeat: no-repeat;
  background-position: center center;
}

/* Parallel-specific style estimator block */

#sk-container-id-1 div.sk-parallel-item::after {
  content: "";
  width: 100%;
  border-bottom: 2px solid var(--sklearn-color-text-on-default-background);
  flex-grow: 1;
}

#sk-container-id-1 div.sk-parallel {
  display: flex;
  align-items: stretch;
  justify-content: center;
  background-color: var(--sklearn-color-background);
  position: relative;
}

#sk-container-id-1 div.sk-parallel-item {
  display: flex;
  flex-direction: column;
}

#sk-container-id-1 div.sk-parallel-item:first-child::after {
  align-self: flex-end;
  width: 50%;
}

#sk-container-id-1 div.sk-parallel-item:last-child::after {
  align-self: flex-start;
  width: 50%;
}

#sk-container-id-1 div.sk-parallel-item:only-child::after {
  width: 0;
}

/* Serial-specific style estimator block */

#sk-container-id-1 div.sk-serial {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--sklearn-color-background);
  padding-right: 1em;
  padding-left: 1em;
}


/* Toggleable style: style used for estimator/Pipeline/ColumnTransformer box that is
clickable and can be expanded/collapsed.
- Pipeline and ColumnTransformer use this feature and define the default style
- Estimators will overwrite some part of the style using the `sk-estimator` class
*/

/* Pipeline and ColumnTransformer style (default) */

#sk-container-id-1 div.sk-toggleable {
  /* Default theme specific background. It is overwritten whether we have a
  specific estimator or a Pipeline/ColumnTransformer */
  background-color: var(--sklearn-color-background);
}

/* Toggleable label */
#sk-container-id-1 label.sk-toggleable__label {
  cursor: pointer;
  display: flex;
  width: 100%;
  margin-bottom: 0;
  padding: 0.5em;
  box-sizing: border-box;
  text-align: center;
  align-items: start;
  justify-content: space-between;
  gap: 0.5em;
}

#sk-container-id-1 label.sk-toggleable__label .caption {
  font-size: 0.6rem;
  font-weight: lighter;
  color: var(--sklearn-color-text-muted);
}

#sk-container-id-1 label.sk-toggleable__label-arrow:before {
  /* Arrow on the left of the label */
  content: "▸";
  float: left;
  margin-right: 0.25em;
  color: var(--sklearn-color-icon);
}

#sk-container-id-1 label.sk-toggleable__label-arrow:hover:before {
  color: var(--sklearn-color-text);
}

/* Toggleable content - dropdown */

#sk-container-id-1 div.sk-toggleable__content {
  display: none;
  text-align: left;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content pre {
  margin: 0.2em;
  border-radius: 0.25em;
  color: var(--sklearn-color-text);
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content.fitted pre {
  /* unfitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-1 input.sk-toggleable__control:checked~div.sk-toggleable__content {
  /* Expand drop-down */
  display: block;
  width: 100%;
  overflow: visible;
}

#sk-container-id-1 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {
  content: "▾";
}

/* Pipeline/ColumnTransformer-specific style */

#sk-container-id-1 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-label.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator-specific style */

/* Colorize estimator box */
#sk-container-id-1 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-estimator.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

#sk-container-id-1 div.sk-label label.sk-toggleable__label,
#sk-container-id-1 div.sk-label label {
  /* The background is the default theme color */
  color: var(--sklearn-color-text-on-default-background);
}

/* On hover, darken the color of the background */
#sk-container-id-1 div.sk-label:hover label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

/* Label box, darken color on hover, fitted */
#sk-container-id-1 div.sk-label.fitted:hover label.sk-toggleable__label.fitted {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator label */

#sk-container-id-1 div.sk-label label {
  font-family: monospace;
  font-weight: bold;
  display: inline-block;
  line-height: 1.2em;
}

#sk-container-id-1 div.sk-label-container {
  text-align: center;
}

/* Estimator-specific */
#sk-container-id-1 div.sk-estimator {
  font-family: monospace;
  border: 1px dotted var(--sklearn-color-border-box);
  border-radius: 0.25em;
  box-sizing: border-box;
  margin-bottom: 0.5em;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-estimator.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

/* on hover */
#sk-container-id-1 div.sk-estimator:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-estimator.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Specification for estimator info (e.g. "i" and "?") */

/* Common style for "i" and "?" */

.sk-estimator-doc-link,
a:link.sk-estimator-doc-link,
a:visited.sk-estimator-doc-link {
  float: right;
  font-size: smaller;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1em;
  height: 1em;
  width: 1em;
  text-decoration: none !important;
  margin-left: 0.5em;
  text-align: center;
  /* unfitted */
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
  color: var(--sklearn-color-unfitted-level-1);
}

.sk-estimator-doc-link.fitted,
a:link.sk-estimator-doc-link.fitted,
a:visited.sk-estimator-doc-link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
div.sk-estimator:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover,
div.sk-label-container:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

div.sk-estimator.fitted:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover,
div.sk-label-container:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

/* Span, style for the box shown on hovering the info icon */
.sk-estimator-doc-link span {
  display: none;
  z-index: 9999;
  position: relative;
  font-weight: normal;
  right: .2ex;
  padding: .5ex;
  margin: .5ex;
  width: min-content;
  min-width: 20ex;
  max-width: 50ex;
  color: var(--sklearn-color-text);
  box-shadow: 2pt 2pt 4pt #999;
  /* unfitted */
  background: var(--sklearn-color-unfitted-level-0);
  border: .5pt solid var(--sklearn-color-unfitted-level-3);
}

.sk-estimator-doc-link.fitted span {
  /* fitted */
  background: var(--sklearn-color-fitted-level-0);
  border: var(--sklearn-color-fitted-level-3);
}

.sk-estimator-doc-link:hover span {
  display: block;
}

/* "?"-specific style due to the `<a>` HTML tag */

#sk-container-id-1 a.estimator_doc_link {
  float: right;
  font-size: 1rem;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1rem;
  height: 1rem;
  width: 1rem;
  text-decoration: none;
  /* unfitted */
  color: var(--sklearn-color-unfitted-level-1);
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
}

#sk-container-id-1 a.estimator_doc_link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
#sk-container-id-1 a.estimator_doc_link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

#sk-container-id-1 a.estimator_doc_link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
}

.estimator-table summary {
    padding: .5rem;
    font-family: monospace;
    cursor: pointer;
}

.estimator-table details[open] {
    padding-left: 0.1rem;
    padding-right: 0.1rem;
    padding-bottom: 0.3rem;
}

.estimator-table .parameters-table {
    margin-left: auto !important;
    margin-right: auto !important;
}

.estimator-table .parameters-table tr:nth-child(odd) {
    background-color: #fff;
}

.estimator-table .parameters-table tr:nth-child(even) {
    background-color: #f6f6f6;
}

.estimator-table .parameters-table tr:hover {
    background-color: #e0e0e0;
}

.estimator-table table td {
    border: 1px solid rgba(106, 105, 104, 0.232);
}

.user-set td {
    color:rgb(255, 94, 0);
    text-align: left;
}

.user-set td.value pre {
    color:rgb(255, 94, 0) !important;
    background-color: transparent !important;
}

.default td {
    color: black;
    text-align: left;
}

.user-set td i,
.default td i {
    color: black;
}

.copy-paste-icon {
    background-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0NDggNTEyIj48IS0tIUZvbnQgQXdlc29tZSBGcmVlIDYuNy4yIGJ5IEBmb250YXdlc29tZSAtIGh0dHBzOi8vZm9udGF3ZXNvbWUuY29tIExpY2Vuc2UgLSBodHRwczovL2ZvbnRhd2Vzb21lLmNvbS9saWNlbnNlL2ZyZWUgQ29weXJpZ2h0IDIwMjUgRm9udGljb25zLCBJbmMuLS0+PHBhdGggZD0iTTIwOCAwTDMzMi4xIDBjMTIuNyAwIDI0LjkgNS4xIDMzLjkgMTQuMWw2Ny45IDY3LjljOSA5IDE0LjEgMjEuMiAxNC4xIDMzLjlMNDQ4IDMzNmMwIDI2LjUtMjEuNSA0OC00OCA0OGwtMTkyIDBjLTI2LjUgMC00OC0yMS41LTQ4LTQ4bDAtMjg4YzAtMjYuNSAyMS41LTQ4IDQ4LTQ4ek00OCAxMjhsODAgMCAwIDY0LTY0IDAgMCAyNTYgMTkyIDAgMC0zMiA2NCAwIDAgNDhjMCAyNi41LTIxLjUgNDgtNDggNDhMNDggNTEyYy0yNi41IDAtNDgtMjEuNS00OC00OEwwIDE3NmMwLTI2LjUgMjEuNS00OCA0OC00OHoiLz48L3N2Zz4=);
    background-repeat: no-repeat;
    background-size: 14px 14px;
    background-position: 0;
    display: inline-block;
    width: 14px;
    height: 14px;
    cursor: pointer;
}
</style><body><div id="sk-container-id-1" class="sk-top-container"><div class="sk-text-repr-fallback"><pre>LogisticRegression(class_weight=&#x27;balanced&#x27;, max_iter=1000)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class="sk-container" hidden><div class="sk-item"><div class="sk-estimator fitted sk-toggleable"><input class="sk-toggleable__control sk-hidden--visually" id="sk-estimator-id-1" type="checkbox" checked><label for="sk-estimator-id-1" class="sk-toggleable__label fitted sk-toggleable__label-arrow"><div><div>LogisticRegression</div></div><div><a class="sk-estimator-doc-link fitted" rel="noreferrer" target="_blank" href="https://scikit-learn.org/1.7/modules/generated/sklearn.linear_model.LogisticRegression.html">?<span>Documentation for LogisticRegression</span></a><span class="sk-estimator-doc-link fitted">i<span>Fitted</span></span></div></label><div class="sk-toggleable__content fitted" data-param-prefix="">
        <div class="estimator-table">
            <details>
                <summary>Parameters</summary>
                <table class="parameters-table">
                  <tbody>

        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('penalty',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">penalty&nbsp;</td>
            <td class="value">&#x27;l2&#x27;</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('dual',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">dual&nbsp;</td>
            <td class="value">False</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('tol',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">tol&nbsp;</td>
            <td class="value">0.0001</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('C',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">C&nbsp;</td>
            <td class="value">1.0</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('fit_intercept',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">fit_intercept&nbsp;</td>
            <td class="value">True</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('intercept_scaling',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">intercept_scaling&nbsp;</td>
            <td class="value">1</td>
        </tr>


        <tr class="user-set">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('class_weight',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">class_weight&nbsp;</td>
            <td class="value">&#x27;balanced&#x27;</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('random_state',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">random_state&nbsp;</td>
            <td class="value">None</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('solver',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">solver&nbsp;</td>
            <td class="value">&#x27;lbfgs&#x27;</td>
        </tr>


        <tr class="user-set">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('max_iter',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">max_iter&nbsp;</td>
            <td class="value">1000</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('multi_class',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">multi_class&nbsp;</td>
            <td class="value">&#x27;deprecated&#x27;</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('verbose',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">verbose&nbsp;</td>
            <td class="value">0</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('warm_start',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">warm_start&nbsp;</td>
            <td class="value">False</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('n_jobs',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">n_jobs&nbsp;</td>
            <td class="value">None</td>
        </tr>


        <tr class="default">
            <td><i class="copy-paste-icon"
                 onclick="copyToClipboard('l1_ratio',
                          this.parentElement.nextElementSibling)"
            ></i></td>
            <td class="param">l1_ratio&nbsp;</td>
            <td class="value">None</td>
        </tr>

                  </tbody>
                </table>
            </details>
        </div>
    </div></div></div></div></div><script>function copyToClipboard(text, element) {
    // Get the parameter prefix from the closest toggleable content
    const toggleableContent = element.closest('.sk-toggleable__content');
    const paramPrefix = toggleableContent ? toggleableContent.dataset.paramPrefix : '';
    const fullParamName = paramPrefix ? `${paramPrefix}${text}` : text;

    const originalStyle = element.style;
    const computedStyle = window.getComputedStyle(element);
    const originalWidth = computedStyle.width;
    const originalHTML = element.innerHTML.replace('Copied!', '');

    navigator.clipboard.writeText(fullParamName)
        .then(() => {
            element.style.width = originalWidth;
            element.style.color = 'green';
            element.innerHTML = "Copied!";

            setTimeout(() => {
                element.innerHTML = originalHTML;
                element.style = originalStyle;
            }, 2000);
        })
        .catch(err => {
            console.error('Failed to copy:', err);
            element.style.color = 'red';
            element.innerHTML = "Failed!";
            setTimeout(() => {
                element.innerHTML = originalHTML;
                element.style = originalStyle;
            }, 2000);
        });
    return false;
}

document.querySelectorAll('.fa-regular.fa-copy').forEach(function(element) {
    const toggleableContent = element.closest('.sk-toggleable__content');
    const paramPrefix = toggleableContent ? toggleableContent.dataset.paramPrefix : '';
    const paramName = element.parentElement.nextElementSibling.textContent.trim();
    const fullParamName = paramPrefix ? `${paramPrefix}${paramName}` : paramName;

    element.setAttribute('title', fullParamName);
});
</script></body>


# A logistic regression model is selected as the primary classification approach due to its interpretability, simplicity, and effectiveness for structured data. The model is configured with class weighting to address imbalance in the target variable. This choice allows for a focused and rigorous implementation while maintaining transparency in how predictions are generated.
# Prediction 


```python
#9 PREDICTIONNNNNNNN

y_pred = model.predict(X_test)
y_prob = model.predict_proba(X_test)[:, 1]
```
The logistic regression model is trained using the prepared training dataset. Class weighting is applied to ensure that fraudulent transactions receive higher importance during learning. This step enables the model to learn patterns associated with fraud while mitigating the bias toward the majority class, resulting in a more balanced and meaningful predictive performance.
# Model Evaluation


```python
#10.1 CLASSIFICATION REPORT
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))
```

                  precision    recall  f1-score   support
    
               0       1.00      0.98      0.99     56864
               1       0.06      0.92      0.11        98
    
        accuracy                           0.98     56962
       macro avg       0.53      0.95      0.55     56962
    weighted avg       1.00      0.98      0.99     56962
    
    


```python
#10.2 COFUSION MATRIX

from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
plt.title("Confusion Matrix")
plt.show()
```


    
![png](output_36_0.png)
    



```python
#10.3 ROC AUC
from sklearn.metrics import roc_auc_score

print("ROC AUC:", roc_auc_score(y_test, y_prob))
```

    ROC AUC: 0.9720323571887957
    
The trained model is used to generate predictions on the test dataset. Both class labels and probability scores are computed, allowing for flexible evaluation and threshold adjustment. Probability outputs are particularly important in fraud detection, as they enable ranking of transactions based on risk rather than relying solely on binary classification.Model performance is evaluated using metrics appropriate for imbalanced classification, including precision, recall, F1-score, and ROC-AUC. The confusion matrix provides a detailed breakdown of prediction outcomes. Emphasis is placed on recall, as correctly identifying fraudulent transactions is more critical than overall accuracy in this context.
# INTERPRETATION
# The dataset is highly imbalanced, with fraudulent transactions representing a very small share of total observations. After scaling the non-standardized variables and performing exploratory analysis, a logistic regression model with balanced class weights was trained. The results show that recall is more important than raw accuracy in this problem because missing fraudulent transactions is more costly than flagging some genuine transactions.
# LIMITATION
# This implementation has several limitations. First, the dataset is highly imbalanced, which makes prediction difficult. Second, logistic regression captures mainly linear relationships and may miss more complex fraud patterns. Third, the anonymized variables reduce interpretability. A natural next step would be to test boosting methods or threshold optimization.
# Future Improvement
Future work can extend this analysis by incorporating more advanced models such as gradient boosting or anomaly detection techniques. Additional improvements may include threshold optimization, cost-sensitive learning, and time-aware validation strategies. These approaches can enhance fraud detection performance and better reflect real-world deployment scenarios.

```python

```
