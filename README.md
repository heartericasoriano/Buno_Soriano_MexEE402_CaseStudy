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
| Ch9 | https://colab.research.google.com/drive/126SFow3I7iNEAo7Y5s0zZLjJk-xDR0ID?usp=sharing |

## What we learned

### One short paragraph per chapter, Ch1_2_3 to Ch9. Say what the chapter taught you and what surprised you. Not what the library does, but what you understood.

***CHAPTER 1_2_3***
<br>
in this chapter, I learned that data preprocessing and data cleaning are important steps in analyzing data using Python. I learned how to load datasets using the Pandas library, identify different data types, and explore data using functions such as head(), describe(), and info(). I also learned how to handle missing values through imputation, deletion, and prediction, as well as remove duplicate entries, irrelevant features, and noisy data. Through these activities, I realized that the quality of the data directly affects the accuracy and reliability of the results. This lesson helped me understand how Python can be used to organize, clean, and prepare data for analysis, which is useful in engineering research

***CHAPTER 4***
<br>
In this chapter, we learned that machine learning models aren't smart enough to spot patterns on their own, they really need us to shape and manipulate the data for them. That's where feature engineering comes into play. We were surprised that simple coding steps, like making ratios or squaring numbers, help a basic model understand curved trends. We learned that data can be transformed and organized to make patterns easier to understand.
Overall, the chapter taught us that proper data transformation through feature engineering is important for getting clearer and more meaningful results.

***CHAPTER 5***
<br>
In Chapter 5, we realized that computer models don't actually understand what our numbers mean, they just see bigger numbers and assume they're more important. When we looked at study hours (0–20) alongside grades (0–100), the higher grade numbers automatically overwhelmed the study hours, even though both mattered. We learned that scaling fixes this by leveling the playing field, either by squeezing all our data between 0 and 1 or centering it around zero so every variable gets a fair say. Another important fact was learning that squashing these numbers makes them fair without messing up the actual patterns between them, and that we don't always have to scale—it entirely depends on our data and the algorithm we're using.

***CHAPTER 6***
<br>
We learned about outliers, which are data values that are very different from the others. We learned that outliers can affect or bias the data because of their extreme positive or negative values. However, if these outliers are irrelevant, removing or handling them can make the data more reliable and easier to evaluate. We also learned different ways to detect and handle outliers, such as the Z-score, IQR method, capping and flooring, and log transformation. Overall, this chapter taught me the importance of checking unusual data before analyzing the results. We were surprised with the result of z-score because even if it's obvious in the data that there's an outlier which is 100, it says that there are no outliers since the z-score does not exceed or equalize to 3 or negative 3. That's why I\We think IQR is the more reliable method based on the given dataset.






## Errors we found
### List any mistake you found in the original notebooks, and the correct version. There are real ones in there. Finding them earns points.

***CHAPTER 1_2_3***
<br>
There are no errors in the program. The code runs without crashing.

***CHAPTER 4***
<br>
 There are no errors in the program. The code runs without crashing.
 <br><br>

***CHAPTER 5***
<br>
There are no errors in the program. The code runs without crashing.
 <br><br>

 ***CHAPTER 6***
 <br>
The program runs smoothly without syntax or runtime errors. However, there is a logical inconsistency, the Z-score cell finds no outliers while the text claims it found 100. The reason for this is that with only 8 data points, a z-score above 3 is mathematically impossible.
 But there are no problem with syntax since it runs without crashing. 
 To  fix it use a larger dataset so a threshold of 3 is reachable or set a lower threshold for small samples
outliers = data[np.abs(z_scores) > 2  inorder for the logic to be corrected.
<br><br>

***CHAPTER 7***
<br>
 There are no errors in the program. The code runs without crashing.
 <br><br>

***CHAPTER 8***
<br>
There are no errors in the program. The code runs without crashing. However, the chapter says to use *Titanic-Dataset.csv*, but the code I reviewed calls *pd.read_csv('train.csv')*. That works only if the uploaded file is literally named *train.csv*. If someone uploads the chapter’s Titanic file instead, the notebook raises a *FileNotFoundError* at the loading step. I decided to change it into *Titanic_Dataset.csv* 
 The error comes from the filename mismatch, not from the pipeline logic. thus, there are no errors.
<br>
 
Later on, I tried the *train.csv* provided recently, it works perfectly, no alternation needed. Thus, there is no error. 

 <br><br>

 ***CHAPTER 9***
<br>
 There are no errors in the program. The code runs without crashing.
 <br><br>

ADDTIONAL ERROR: When error occurs and we changed only the wrong part in one line there are chances that the program will not run smoothly even if the wrong code is corrected. Based from our experience, re-writing the whole line is a safer option for the program to run smoothly once corrected.

## Note on AI tools

#### Say whether you used an AI tool, and what for. This is not a penalty. Hiding it is.

FOR WHAT WE LEARNED PART:
AI TOOLS USED: GEMINI & CHAT GPT

They were used not to seek for answers but to further understand what each chapter's purpose is. It was used to further understand new concepts and also used as a paraphrasing tool for better workflow of ideas.
before every paraphrasing, a draft was provided so that the essence of our own understanding won't be wasted.

FOR ERRORS WE FOUND
AI TOOLS USED: CLAUDE AI

PROMPT USED: "Suppose you're an engineering student: Find and specify errors within the program (code) and provide corrections on how to fix it. If none, say so". With separate files attached.

Once the result says the program runs without crashing, it serves as an automatic green light for us that the syntax are correct but of course there are other minor and major errors to considered which are present in various chapters.

Since we're newly exposed to this kind of programming and we're still not familiar with couple of commands, we directly asked for assistance from claude AI to identify the Errors. Our participation takes into place at the part where we check one by one the errors found and verify it through our own understanding of the commands and understanding how it can affect the program so that we can learn and come to a point where we can point out errors within a program with just ourselves and a little help from AI as possible. (Obvious errors in the codes we're directly written like for example, the chapter 6 logical error).


## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
