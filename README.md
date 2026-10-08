# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Buño, Carl Axle | 23-01607 | MEXE-4102 |
| Soriano, Heart Erica | 23-02684| MEXE-4102 |

## Notebook links

| Chapter | |
|---|---|
| Ch1_2_3 | https://colab.research.google.com/drive/1sFq5uTvxhFwvD9zm5DPTvRlLkWfKhwKT?usp=sharing |
| Ch4 |https://colab.research.google.com/drive/1jUgWuFjr9IiHn8nhAl91qW63nFYTjoCH?usp=sharing  |
| Ch5 | https://colab.research.google.com/drive/1dglhCcQAyypT0eHH3BEsci7_Smpbksnn?usp=sharing |
| Ch6 | https://colab.research.google.com/drive/1r1SS9q8qm8aAlB8UiMZ1LJAyWbzM7Tds?usp=sharing |
| Ch7 | https://colab.research.google.com/drive/1kMfHcajrx5wE0cUuxzADicLqPREv9DZZ?usp=sharing |
| Ch8 | https://colab.research.google.com/drive/1dotoRGndorrYg2s0aK51d-fQ8fi2Um7N?usp=sharing |
| Ch9 |  |

## What we learned

### One short paragraph per chapter, Ch1_2_3 to Ch9. Say what the chapter taught you and what surprised you. Not what the library does, but what you understood.

#### Chapter 4 
We learned that this chapter focuses on feature engineering, which involves transforming existing data into new and more useful features. As we experienced working with coding, we learned how to create new features through binning, which converts numerical data into categorical data, interaction features, which combine two or more variables into a new feature, and polynomial features, which add more complexity and additional features to the data. We also experienced how Python and Pandas can be used to organize data through ordinal encoding, perform calculations, and create new columns from existing data. We were already familiar with calculations because engineering involves a lot of mathematical concepts, but applying them through coding gave us a different experience. Overall, this chapter helped us understand how transforming data can make it easier to identify patterns and provide more useful information for analysis.

#### Chapter 5
We learned that this chapter focuses on data scaling and normalization, which is the process of adjusting numerical data so that different features can be compared more fairly. As we experienced working with coding, we learned how to use StandardScaler to standardize data based on its mean and standard deviation, while MinMaxScaler adjusts the data to a range from 0 to 1. We also experienced how Python and Pandas can be used to organize datasets and how Scaler.fit_transform can transform features such as study hours and grades. Through this activity, we understood that scaling and normalization are important because they prevent features with larger numerical values from having too much influence on the results. Overall, this chapter helped us understand how properly scaled data can make analysis easier and prepare datasets for machine learning.

#### Chapter 6
We learned about outliers, which are data values that are very different from the others. We learned that outliers can affect or bias the data because of their extreme positive or negative values. However, if these outliers are irrelevant, removing or handling them can make the data more reliable and easier to evaluate. We also learned different ways to detect and handle outliers, such as the Z-score, IQR method, capping and flooring, and log transformation. Overall, this chapter taught me the importance of checking unusual data before analyzing the results. We were surprised with the result of z-score because even if it's obvious in the data that there's an outlier which is 100, it says that there are no outliers since the z-score does not exceed or equalize to 3 or negative 3. That's why I\We think IQR is the more reliable method based on the given dataset.



List any mistake you found in the original notebooks, and the correct version.
There are real ones in there. Finding them earns points.


## Errors we found

***CHAPTER 1_2_3***
<br>
I found errors in the program. The code runs without crashing, but it contains problems that would cause incorrect or unreliable results. First is the chained inplace=True assignment used to fill the missing values: <br>
<mark>df['Year'].fillna(df['Year'].mean(), inplace=True)
df['Publisher'].fillna(df['Publisher'].mode()[0], inplace=True)</mark>. <mark>df['Year']</mark> returns an intermediate Series, which may be a copy and not a direct view of the DataFrame column. With <mark>inplace=True</mark>, <mark>fillna()</mark> modifies that intermediate object, and the change is not guaranteed to propagate back to df. The FutureWarning in the notebook’s output reports that the inplace method will never work because the intermediate object on which we are setting values always behaves as a copy. 
<br>
To fix it, Assign the result back to the column instead of modifying in place:
<mark>df['Year'] = df['Year'].fillna(df['Year'].mean())
df['Publisher'] = df['Publisher'].fillna(df['Publisher'].mode()[0])</mark>
<br><br>

***CHAPTER 4***
<br>
 We did not find any errors that would stop the program from running or provide incorrect results
 <br><br>

***CHAPTER 5***
<br>
 We don't see any errors in this program. We went through it cell by cell, and it should run from top to bottom without problems.
 <br><br>

 ***CHAPTER 6***
 <br>
 The only real error that we found is that the Z-score cell finds no outliers while the text claims it found 100. The reason for this is that with only 8 data points, a z-score above 3 is mathematically impossible.
 But there are no problem with syntax since it runs without crashing. 
 To  fix it use a larger dataset so a threshold of 3 is reachable or set a lower threshold for small samples
outliers = data[np.abs(z_scores) > 2  inorder for the logic to be corrected.


## Note on AI tools

#### Say whether you used an AI tool, and what for. This is not a penalty. Hiding it is.

For finding the errors since we're not yet familiar with various codes, we seek help from Claude AI to detect and specify each problems within the code.

steps used to find the errors:
(PROMPTS)


1.Act as a professional python programmer

2. (Sent files individually) with prompt " find what are the errors found within the program itself and specify it."



(IMPLEMENTATION)


3. Even after claude provides the found errors, the AI provides corrections on how to fix the code which helped us to understand further how the code shoud be and what is the correct code for each specific chapters.
4. After receiving the faults and errors, we inspect and analyzed the program and included the errors in every chapters.


## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
