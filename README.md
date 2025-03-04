## EX NO:1
## REG NO:212223240050
## NAME: Harshini Y
# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output 
   # Data cleaning
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```

![Screenshot 2025-03-04 104355](https://github.com/user-attachments/assets/60e31b91-5558-45df-b8f0-9aebd708b83f)

```
df.isnull().sum()
```

![Screenshot 2025-03-04 104539](https://github.com/user-attachments/assets/f1ed9484-7092-44b5-967c-28adcc4ef4d3)

```
df.isnull().any()
```

![Screenshot 2025-03-04 104616](https://github.com/user-attachments/assets/940c11d3-6a1d-4ca3-8569-7b8d4495f157)

```
df.dropna()
```

![Screenshot 2025-03-04 104659](https://github.com/user-attachments/assets/21d9c731-fc92-476e-a36f-142ee1cd718c)

```
df.fillna(0)
```

![Screenshot 2025-03-04 104738](https://github.com/user-attachments/assets/30d1a410-f9b5-447b-98ac-975b2bdcfc5d)
```
df.fillna(method = 'ffill')
```
![WhatsApp Image 2025-03-04 at 11 22 12_2dcc2dbf](https://github.com/user-attachments/assets/aa0a35ed-c5c8-408f-968d-bcad83eaed28)

```
df.fillna(method = 'bfill')
```
![WhatsApp Image 2025-03-04 at 11 22 19_2f3825a2](https://github.com/user-attachments/assets/a68765f8-6fbb-4baf-a7b9-4be916331eb1)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![WhatsApp Image 2025-03-04 at 11 22 30_5ed01eb1](https://github.com/user-attachments/assets/71c34f49-5959-49fe-a169-50b0647e22af)

  # IQR(Inter Quartile Range)

```
ir=pd.read_csv("/content/iris.csv")
ir
```

![Screenshot 2025-03-04 104929](https://github.com/user-attachments/assets/2d0cd107-569a-4e48-8271-e188399f128e)

```
ir.describe()
```

![Screenshot 2025-03-04 105000](https://github.com/user-attachments/assets/6cd143fb-fe39-4091-8d47-f5db8eb2d135)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![Screenshot 2025-03-04 105236](https://github.com/user-attachments/assets/dfce8bd0-6618-4285-8b73-7c252fd673b6)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![Screenshot 2025-03-04 105314](https://github.com/user-attachments/assets/4b0add73-ee5a-47a9-815a-b262cc1c6158)

```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```

![Screenshot 2025-03-04 105402](https://github.com/user-attachments/assets/91a44f96-8154-45fc-aebe-1af70c53ef9d)

```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
  ```

![Screenshot 2025-03-04 105437](https://github.com/user-attachments/assets/76146634-b06d-479b-8d9f-e8dde5454a18)

```
sns.boxplot(x='sepal_width',data=delid)
```

![Screenshot 2025-03-04 105512](https://github.com/user-attachments/assets/69ffcae7-5ec1-438c-8aef-0785005d34e5)

## z score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
data=pd.read_csv("/content/heights.csv")
data
```
![Screenshot 2025-03-04 111157](https://github.com/user-attachments/assets/ba8de8a7-e3dc-4dd5-bc7c-cf6c011943a7)
```
z=np.abs(stats.zscore(data['height']))
z
```
![Screenshot 2025-03-04 111232](https://github.com/user-attachments/assets/e0592c71-7203-4afb-bc59-cd3eb8b19eee)




# Result
   Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
