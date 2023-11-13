# EX-09 DATA VISUALIZATION 2
### AIM:
To Perform Data Visualization on a complex dataset and save the data to a file.
### EXPLANATION:
Data visualization->graphical representation of information and data.Using visual elements like charts,graphs,maps,it provide an accessible way to see and understand trends, outliers,and patterns in data.

### ALGORITHM:
- Step1: Read the given Data. 
- Step2: Clean the Data Set using Data Cleaning Process.
- Step3: Apply Feature generation and selection techniques to all the features of the data set.
- Step4: Apply data visualization techniques to identify the patterns of the data.
```
Developed By: SATHISH R
Register No: 212222230138
```

### CODE: &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; OUTPUT:
<table>
<tr>
<td>

```Python
#Importing packages and Load Data    
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
df.head()
df.isnull().sum()
``` 
</td> 
<td>

<img height=50% width=65% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/44161065-c459-49a3-954c-ef9e67be83ec">&emsp;<img height=50% width=25% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/dae81958-2894-4660-af37-dfa4205fe7ed">

</td>
</tr> 
<tr>
<td>

```Python
#ANALYZING OUTLIERS
plt.title("Data with Outliners")
sns.boxplot(data=df)
plt.show()
#REMOVINF OUTLIERS
cols=["size","tip","total_bill"]
q1=df[cols].quantile(0.25)
q3=df[cols].quantile(0.75)
iqr=q3-q1
df=df[~((df[cols]<(q1-1.5*iqr))|
(df[cols]>(q3+1.5*iqr))).any(axis=1)]
plt.title("Outliers Removed")
sns.boxplot(data=df)
plt.show()
``` 
</td> 
<td>

<img height=50% width=47% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/895f51e5-5e0f-4621-be3e-8312942663ae">&emsp;<img height=50% width=47% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/329fbded-b342-4535-80bf-acea9cb44b0d">
</td>
</tr> 
</table>

- **1.Which day of the week has the highest total bill amount?**
<table>
<tr>
<td>

```Python
sns.barplot(x=df["day"],y=df["total_bill"],hue=df["day"])
plt.legend(loc="center")
plt.title("highest total bill amount by day of the week")
``` 
</td> 
<td>

<img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/8b2501b0-3cb0-4070-b113-2f73e7ae9369">

</td>
</tr> 
</table>

- **2.What is the average tip amount given by smokers and non-smokers?**
<table>
<tr>
<td>

```Python
plt.figure(figsize=(6,3))
sns.boxplot(x=df["smoker"],y=df["tip"],hue=df["smoker"])
plt.title("Tip amount given by Smokers and Non-Smokers")
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/1d8022e8-c8ba-4f98-b9ee-38968485267a">

</td>
</tr> 
</table>

- **3.How does the tip percentage vary based on the size of the dining party?**
<table>
<tr>
<td>

```Python
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip Percentage by Dining Party Size")
``` 
</td> 
<td>
  
<img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/ef62cb5e-35b6-4b0c-afda-3e34a410576b">

</td>
</tr> 
</table>

- **4.Which gender tends to leave higher tips?**
<table>
<tr>
<td>

```Python
sns.barplot(x=df["sex"],y=df["tip"],hue=df["sex"])    
plt.legend(loc="best")
plt.title("Highest Tips Based on Gender")
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/cd44bf62-7db9-4a7c-bd28-f6acf36081d8">

</td>
</tr> 
</table>

- **5.Is there any relationship between the total bill amount and the day of the week?**
<table>
<tr>
<td>

```Python
sns.scatterplot(x=df["day"],y=df["total_bill"],
          hue=df["day"])
plt.legend(loc="best")
plt.title("Relation Between Total Bill Amount by Day
            of the Week")
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/506c2f1a-e4da-49db-a993-3553e8b39b95">

</td>
</tr> 
</table>

- **6.How does distribution of total bill amounts vary across different time periods(lunch vs dinner)?**
<table>
<tr>
<td>

```Python
sns.histplot(data=df,x="total_bill",hue="time",
                 lement="step",stat="density")
plt.title("Total Bill Amounts by Time of Day")
plt.show()
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/fe37f512-ab02-46a8-9b37-bb1b60badc2d">

</td>
</tr> 
</table>

- **7. Which dining party size group tends to have the highest average total bill amount?**
<table>
<tr>
<td>

```Python
plt.figure(figsize=(6,3))
sns.barplot(x=df["size"],y=df["total_bill"],hue
                =df["size"])
plt.title("Highrst Average Total Bill Amount by Dining
             Party Size")
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/e7284780-c2f0-4f56-9d6a-7f97ffc33bda">

</td>
</tr> 
</table>

- **8. What is the distribution of tip amounts for each day of the week?**
<table>
<tr>
<td>

```Python
sns.boxplot(x="day", y="tip", data=df)
plt.title("Distribution of Tip Amount by Day \
           of Week")
plt.show()
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/c42eb921-636e-444f-a2fa-421f30be3382">

</td>
</tr> 
</table>

- **9.How does the tip amount vary based on type of service(lunch vs dinner)?**
<table>
<tr>
<td>

```Python
plt.figure(figsize=(6,3))
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip Amount Based on Type of Service")
``` 
</td> 
<td>

 <img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/1c7efd0c-b659-4a2b-934a-00425a3419d8">

</td>
</tr> 
</table>

- **10.Is there any correlation between the total bill amount and the tip amount?**
<table>
<tr>
<td>

```Python
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between Total Bill Amount and
           Tip Amount")
plt.show()
``` 
</td> 
<td>

<img height=50% width=99% src="https://github.com/ROHITJAIND/EX-09-DATA-VISUALIZATION-2/assets/118707073/2df9c9ce-1734-440e-99f1-e7f2d8b864a1">
</td>
</tr> 
</table>

### RESULT:
Thus, Data Visualization on a complex dataset and save the data to a file has been performed successfully.
