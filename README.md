# Ex02-Outlier

# Aim:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1:
Read the given Data.

# STEP 2:
Get the information about the data.

# STEP 3:
Detect the Outliers using IQR method and Z score.

# STEP 4:
Remove the outliers:

# STEP 5:
Plot the datas using box plot.

# PROGRAM:
  Name: Yogeshvar M
  
  Reg no: 212222230180
  ```python
import pandas as pd
import seaborn as sns
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
<img width="49" alt="263958774-3e07b80e-68d3-47bf-8617-675a82f7f76d" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/11c763a1-26cf-45d6-84b2-ea5e6843dec9">


```python
sns.boxplot(data=af)
```
<img width="286" alt="263959219-b2e694ee-5d35-41aa-8135-81fcbeae529a" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/0d8343ee-3940-49ea-b330-d0aa53a5109f">

```python
sns.scatterplot(data=af)
```
<img width="290" alt="263959521-d7ea0bd1-b3be-4931-85b2-0688cf837cf1" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/08f1ccf0-4c74-423c-a218-cce4684e5a63">

```python
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
irq=af.quantile(0.5)
```
```python
low=q1-1.5*iqr
low
```
<img width="69" alt="263960433-3f44bada-feca-42d2-a602-75ef93fadda8-1" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/85d29823-b567-46e9-a337-88a656d6a0df">

```python
high=q3+1.5*iqr
high
```
<img width="66" alt="263960984-8a8e591b-7862-40ff-80f1-d351fcb1c780" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/e96c6a32-3ee3-4872-bb91-5e446c26fc6b">

```python
aq=af[((af>=low)&(af<=high))]
aq.dropna()
```
<img width="52" alt="263961281-3a42186f-b1da-4646-b62b-b659152036c5" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/df8086c7-7f99-43cf-baa1-b0274c313dd1">

```python
sns.boxplot(data=af)
```
<img width="283" alt="263961987-5efbc140-3782-45b1-b723-4b04cbf9e87f" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/5da4f520-c84e-484b-91aa-59bd591bbd24">

```python
af=af[((af>=low)&(af<=high))]
af.dropna()
```
<img width="52" alt="263962155-d991b2e9-4ad5-4e78-afa0-f244ca53ff19" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/dc97f2a4-ab2e-4d37-9c21-bdffa012bb0f">

```python
sns.boxplot(data=af)
```
<img width="285" alt="263962311-9733583f-c1de-486d-9f35-5eb9850e1c9f" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/b2bc2e36-1807-439b-b50e-0a25016fbfc1">

```python
sns.scatterplot(data=af)
```
<img width="282" alt="263963407-05f71607-e5c0-499a-b397-0b10f88e0009" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/577b52ca-7650-4b35-8e7e-f45434c60254">
  
```python
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
```
```python
data = {'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
<img width="52" alt="263963869-9666a946-ca20-4801-95d4-25a68b5aec77" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/5f315562-f996-4f55-b6b5-fbb8fb48a82e">

```python
sns.boxplot(data=df)
```
<img width="286" alt="263964174-bd33df32-2dea-4b33-8be6-2d1b81eab374" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/bc8a29c9-9b63-407c-a7ae-c81e1067c7e9">

```python
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
<img width="53" alt="263964421-7a647b1c-2f99-4394-8de3-021557977e78" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/d0decb7e-46be-4046-b69b-cc404af7d7c4">

```python
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
df=pd.DataFrame(data)
```
```python
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
```
```python
op=d_o(val)
op
``
![264526707-ec8fe698-d4ba-4a26-941b-177d2f3ff9b6](https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/846e488a-8354-497a-a644-574f5d9a3287)

```python
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
```
```python
id=pd.read_csv("iris.csv")
id
```
<img width="272" alt="263965247-2a34017f-c89a-48c4-8f22-6f1e0df886ff" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/6c60db5e-0d80-4ee3-83af-7d9b177b7dd5">

```python
sns.boxplot(x='sepal_width',data=id)
```
<img width="277" alt="263965605-fbacb6f4-4d89-469c-829e-25a3b3ee38ac" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/08f8ed7c-f104-4243-9b25-ffad110b25ab">

```pyhton
c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
<img width="29" alt="263965898-2143cf85-e8bd-4f03-bb72-562dc0bfc7f2" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/b9c1fa4c-73e8-4b32-81ab-9672bb90b794">

```python
rid=id[((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
<img width="206" alt="265197967-0c6bd8aa-e54d-4824-8011-827c3e0485f9" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/8a9ad963-5fce-4a70-a895-7dc1d3be71f7">

```python
delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
delid
```
<img width="268" alt="265198041-bc3a76ca-73fb-4406-8f9a-590fe97b0f48" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/83c51bd3-2068-4c95-ad7c-f1130a8902f7">

```python
sns.boxplot(x='sepal_width',data=delid)
```
<img width="269" alt="265198063-212cc2fc-03cd-4fe6-a484-a2c2a182a51e" src="https://github.com/Yogeshvar005/ODD2023---Datascience---Ex-02/assets/113497367/e68b9e1a-fba7-4dc0-844a-76bed38e7301">

# Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
