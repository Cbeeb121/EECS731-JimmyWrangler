Clay Beabout | EECS 731 - Jimmy Wrangler | Sept 7, 2020

## Process

### Choosing datasets
For this project I used Kaggle to find datasets. While searching, I found datasets geared towards mental health data. In particular, suicide rates. In the midst of COVID, suicide rates have increased exponentially across the world due to increased isolation and loneliness which exacerbates depressive tendencies. The main crude data set includes 500+ rows due to the nature of the datasets. This is not a very large set because each row covers national data for several countries that maintain their own public mental health data. 

### Cleaning and Transforming datasets
There were a few pieces of missing data in both datasets. All fields with the exception of the country were of the Float type. I replaced all missing fields with mean column values because of this. 

Combining the datasets was rather easy using the pandas `merge` method. By merging on two keys ('Country', 'Sex') I was able to join the datasets easily. Upon merging, two columns ('day_treatment', 'residential_facilities') resulted with several NaN fields. Using `fillna` I was able to update said NaN cells with the mean of the respective parent column.

```
fc_df = pd.merge(df, facilities, on=['Country'])
column_means = fc_df.mean()
fc_df = fc_df.fillna(column_means)
```

## Ideas & Results

### Formulated Ideas 
From prior research to this project, I knew suicide rates were not constant. Meaning there are several factors leading an individual to commit suicide. Using the data, I intend on finding the most at-risk age range and sex. These analytics would allow social scientists and psychologists to better predict suicide within communities involving higher at-risk individuals. 

I split the larger crude data set into two separate sets based on sex (male_df, female_df). 


### Results 