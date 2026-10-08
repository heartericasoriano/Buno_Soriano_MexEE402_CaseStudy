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
| Ch1_2_3 |  |
| Ch4 |  |
| Ch5 |  |
| Ch6 |  |
| Ch7 |  |
| Ch8 |  |
| Ch9 |  |

## What we learned

### One short paragraph per chapter, Ch1_2_3 to Ch9. Say what the chapter taught you and what surprised you. Not what the library does, but what you understood.

#### Chapter 4 
I learned that this chapter focuses on feature engineering, which involves transforming existing data into new and more useful features. I learned how to create new features using binning which converts numerical data into categorial data, interaction features which can combine two or more variables into a new feature, and polynomial features for more complexity or to add more features to datas. I also observed how Python and Pandas can be used to organize data using ordinal encoding, perform calculations which I knew from the start because engineering pronciples are focused on calculations, and create new columns from existing data. Overall, the chapter taught me how transforming data can help reveal patterns and provide better information for analysis.

#### Chapter 5
I learned that this chapter focuses on data scaling and normalization, which involves adjusting numerical data so that different features can be compared fairly. I learned how to use StandardScaler to standardize data by adjusting it based on the mean and standard deviation, and MinMaxScaler to normalize data into a range of 0 to 1. I also observed how Python, Pandas, and Scaler.fit_transform can be used to organize datasets and transform features such as study hours and grades. Overall, the chapter taught me how properly scaling and normalizing data can prevent features with larger numerical values from dominating and can help prepare data for better analysis and machine learning.

#### Chapter 6
I learned about outliers, which are data values that are very different from the others. I learned that outliers can affect or bias the data because of their extreme positive or negative values. However, if these outliers are irrelevant, removing or handling them can make the data more reliable and easier to evaluate. I also learned different ways to detect and handle outliers, such as the Z-score, IQR method, capping and flooring, and log transformation. Overall, this chapter taught me the importance of checking unusual data before analyzing the results. I was surprised with the result of z-score because even if it's obvious in the data that there's an outlier which is 100, it says that there are no outliers since the z-score does not exceed or equalize to 3 or negative 3. That's why I think IQR is the more reliable method based on the given dataset.



List any mistake you found in the original notebooks, and the correct version.
There are real ones in there. Finding them earns points.


## Errors we found

FOR CHAPTER 4

there are 5 errors found plus one structural flaw

Errors found in the code

Error 1: Binning cell. "very hot" is never assigned (logic error)

Code: bins = [70, 75, 85, 95, 100] with pd.cut(...)
Result: very hot has a count of 0. The highest temperature, 95, falls into (85, 95], which is hot.
Cause: pd.cut intervals are right-inclusive by default, so the edge value 95 belongs to the lower bin.
Fix: change the edge (e.g. [70, 75, 85, 92, 100]), or use right=False.

Error 2: Binning cell. Boundary value misclassified

Temperature 75 is labeled cool because the interval is (70, 75]. Your notes imply 75 is the start of "warm".
Fix: pd.cut(..., right=False) or include_lowest=True with adjusted edges.

Error 3: One-hot encoding cell. Output is True/False, not 1/0

Your markdown says "Assigns 1 = True, 0 = False", but the output columns are dtype bool. (This runs on pandas 3.0.2; since pandas 2.0 this has been the default.)
Fix: pd.get_dummies(df_2, columns=['Weather'], dtype=int)

Error 4: Ordinal encoding cell. Output contradicts the documented mapping

Your notes say Little → 1, Medium → 2, Lots → 3. The actual output is 0.0, 1.0, 2.0, which is zero-based and float.
Fix: correct the note, or use ord_enc.fit_transform(...).astype(int) + 1.

Error 5:(own observed error)

Since output contradicts the documented mapping the outputs became unreliable since outputs are:
little = 0
Medium = 1
Lots = 2

Error 6: Structural/naming flaw

Mislabeled interaction feature

The cell is titled "Interaction Features", but Ice Cubes / Temperature is a ratio, not an interaction. An interaction term is normally a product: df['Temperature'] * df['Ice Cubes']

FOR CHAPTER 5

The defects are in how the program is written and in what its text claims.

the errors found are

Error 1: Duplicate data definition (code redundancy)

data / df and data_2 / df_2 hold identical values. I confirmed with df.equals(df_2), which returns True.
Risk: if one copy is edited, the two comparisons silently diverge.
Fix: define the data once and reuse df for both scalers.

Error 2: Scaler variable is reused and overwritten

scaler = StandardScaler() is later reassigned as scaler = MinMaxScaler().
The fitted StandardScaler (with its learned mean and std) is lost, so you cannot inverse-transform or reuse it afterward.
Fix: use distinct names, e.g. std_scaler and minmax_scaler.

Error 3: Output loses column names (usability flaw)

fit_transform returns a bare NumPy array (confirmed: numpy.ndarray), so print(scaled_data) shows unlabeled numbers and you can't tell which column is Study Hours.
Fix: wrap it, pd.DataFrame(scaled_data, columns=df.columns), or call StandardScaler().set_output(transform="pandas").

Error 4: Misleading markdown claim ("equal footing")

The text says standardization puts the features "on an equal footing". Standardization gives mean 0 and standard deviation 1. It does not make features equal in importance or range. Standardized values are not bounded to 0–1 (they range from about -1.88 to 1.40 here).
The header sentence is also formatted as a ## heading, but it is body text, not a section title.

Error 5: Imprecise claim about the 0–1 scaling bullet

The first section says scaling "commonly scales data to 0–1 or to mean = 0, std = 1", then later lists MinMax as "normalization" and Standard as "scaling". Both are scaling techniques, and the notebook never says which method produces which result.

Error 6: Inconsistent import placement

MinMaxScaler is imported mid-notebook, while StandardScaler is imported in the first cell. Fix: put all imports in the first cell.

Error 7: Missing train/test fit logic (conceptual flaw)

Both scalers call fit_transform on the entire dataset. In a real pipeline this leaks test statistics into training. The correct pattern is fit on the training split and transform on the test split. The notebook never mentions this.

FOR CHAPTER 6

Errors found

Error 1: Z-score method finds no outliers, contradicting the notebook (critical)

The cell outliers = data[np.abs(z_scores) > 3] prints Outliers: [].
The very next markdown cell says "the number 100 is a clear outlier". The notebook's own output contradicts that sentence.
Cause: the z-score of 100 is only 2.615, below the threshold of 3.
This is a mathematical limit of the example, not a typo. With only 8 points, a z-score above 3 is impossible when using scipy's default population standard deviation, because the maximum possible |z| is √(n−1) ≈ 2.646. The ±3 rule needs a much larger sample.
Fix: use a threshold of 2 for this tiny dataset (which would flag 100), or switch to a larger dataset (about 30+ points) to demonstrate the ±3 rule, and add a note about the small-sample limitation.

Error 2: Variable data is overwritten with a different type

data starts as a np.array and is later reassigned to a pd.Series with identical values. Any cell run out of order uses the wrong type, and the first version is lost.
Fix: use separate names (data_np, data_series) or one structure throughout.

Error 3: Markdown describes a different Q1/Q3 method than the code uses

The notes say "Q1 = median of lower half, Q3 = median of upper half". That gives Q1 = 12.0, Q3 = 21.5, IQR = 9.5.
The code uses data.quantile(), which interpolates linearly. That gives Q1 = 12.0, Q3 = 21.25, IQR = 9.25, which is the value shown in the output.
The result happens to be the same here (100 is the only outlier), but the described method and the implemented method differ.
Fix: describe the interpolation method in the notes, or compute the medians of the halves manually.

Error 4: Bounds are never printed or shown

The notebook computes Q1 - 1.5*IQR and Q3 + 1.5*IQR inline and discards them. The reader never sees the lower bound (−1.875) or upper bound (35.125) that justify flagging 100.
Fix: assign them to lower and upper variables and print them.

Error 5: Strategies section has no code (incomplete)

Capping/flooring, log transformation, and removal are described, but none is implemented, even though the section sits in a coding notebook.
Example I verified: capping with the IQR bounds turns 100 into 35.125, and np.log compresses 100 to 4.61 against about 2.3–3.1 for the rest.

Error 6: Inaccurate claim about log transformation

The notes say it "creates a more normally distributed dataset" and is "best for exponential relationships". It only reduces right skew, and does not guarantee normality. It also fails for zero or negative values (use np.log1p for zeros).

Error 7: Headings misused for body text

"In this example, the number 100…" and "In this scenario, again…" are written as # H1 headings, so they render as huge titles. They should be plain text.

Error 8: Leftover empty cell with duplicated execution count

The final code cell is empty and shows execution_count: 25, the same as the IQR outlier cell, indicating it was run out of order or re-run. Remove it.

Error 9: Import placement

import pandas as pd sits in the middle of the notebook, separate from the other imports.



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
