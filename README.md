# A Data Analysis of the Kaggle Programmer Survey 2021
In this data analysis, I will explore the findings of the Kaggle Programmer Survey 2021, focusing on the most popular programming languages for data science, the relationship between experience and compensation, and salary trends in the data science industry.

This project will explore the findings of the Kaggle Programmer Survey 2021 to provide insights into the data science industry. The specific topics that will be explored include the most popular programming languages for data science, the relationship between experience and compensation, and salary trends in the data science industry.

#### -- Project Status: [Completed]
#### -- Technologies: [Python]







### Sources
 The data for this project is the [Kaggle Programmer Survey 2021](https://www.kaggle.com/code/paultimothymooney/2021-kaggle-data-science-machine-learning-survey/data?select=kaggle_survey_2021_responses.csv), which is a publicly available dataset. The survey collects data on a variety of topics, including programming languages, experience, compensation, and education.

 Below is first few rows of Data set:

 | experience_coding | python_user | r_user | sql_user | most_used | compensation |
|---|---|---|---|---|---|
| 6.1 | True | False | True | Scikit-learn | 124267 |
| 12.3 | True | True | True | Scikit-learn | 236889 |
| 2.2 | True | False | False | None | 74321 |
| 2.7 | False | False | True | None | 62593 |

## Objectives
The specific questions and hypotheses that will be explored in this project include:
* What are the most popular programming languages for data science?
* What is the relationship between experience and compensation in data science?
* What are the salary trends in the data science industry?

## Blockers and Challenges

 The main blockers and challenges that I am facing with this project include:
* The dataset is quite large, so it may be challenging to analyze and visualize the data effectively.
* The data is not always clean, so I may need to clean and prepare the data before I can analyze it.


## Needs of this project

The findings of this project can be used by a variety of stakeholders to make informed decisions. These stakeholders include:

### 1- Data scientists
This project can help data scientists to understand the current state of the data science industry and to make informed decisions about their careers.

> A data scientist could use the findings of this project to decide which programming languages to learn in order to be more marketable.

### 2- Aspiring data scientists
This project can help aspiring data scientists to understand the skills and knowledge that they need to be successful in the data science industry.

> An aspiring data scientist could use the findings of this project to create a plan for their education and career development.

### 3- Educators
This project can help educators to develop data science curriculum that is relevant to the needs of the real world.

> An educator could use the findings of this project to develop data science curriculum that is relevant to the needs of the real world.

### 4- Companies
This project can help companies to understand the needs of the data science workforce and to make informed decisions about their hiring and compensation strategies.

> A company could use the findings of this project to determine the salary range for data science positions.

###### In short, this project can provide insights into the data science industry that can be used by a variety of stakeholders to make informed decisions.
## Data cleaning
The first step in any data analysis project is to clean the data. This involves removing any errors or inconsistencies in the data, as well as converting the data into a format that is easy to work with.

```python
column_names = kaggle_data[0]
survey_responses = kaggle_data[1:]

num_rows = len(survey_responses)
for i in range(num_rows):

  # experience_coding to float
  survey_responses[i][0] = float(survey_responses[i][0])

  # python_user to boolean
  if survey_responses[i][1] == "TRUE":
    survey_responses[i][1] = True
  else:
    survey_responses[i][1] = False

  # r_user to boolean
  if survey_responses[i][2] == "TRUE":
    survey_responses[i][2] = True
  else:
    survey_responses[i][2] = False

  # sql_user to boolean
  if survey_responses[i][3] == "TRUE":
    survey_responses[i][3] = True
  else:
    survey_responses[i][3] = False

  # most_used to boolean
  if survey_responses[i][4] == "None":
    survey_responses[i][4] = None
  else:
    survey_responses[i][4] = survey_responses[i][4]

  # compensation to integer
  survey_responses[i][5] = int(survey_responses[i][5])
```

This code will help to ensure that the data is clean and consistent, which will make it easier to analyze and interpret.
## Insights
Below is all the insights I have found, followed by the code:

### Programming Languages
* The *most popular* programming language among Kaggle programmers is **Python**, with **21,860 users (84.16%)**.
 * **R** is the *second most popular* language, with **5,335 users (20.54%)**. 
* Followed by **SQL** with **10,757 users (41.41%)**.
#### Code
```python
#counting peoples
python_user_count = 0
r_user_count = 0
sql_user_count = 0

for i in range(num_rows):

  # Detect if python_user column is True
  if survey_responses[i][1]:
    python_user_count = python_user_count + 1

  # Detect if r_user column is True
  if survey_responses[i][2]:
    r_user_count = r_user_count + 1

  # Detect if sql_user column is True
  if survey_responses[i][3]:
    sql_user_count = sql_user_count + 1


```
#### Printing out
```python
print('DATA:')
print("Number of Python users: " + str(python_user_count))
print("Number of R users: " + str(r_user_count))
print("Number of SQL users: " + str(sql_user_count))
print('')
print('PROPOTION:')
print("Proportion of Python users: " + str(python_user_count / num_rows))
print("Proportion of R users: " + str(r_user_count / num_rows))
print("Proportion of SQL users: " + str(sql_user_count / num_rows))
print('')
```

#### Output
```
DATA:
Number of Python users: 21860
Number of R users: 5335
Number of SQL users: 10757

PROPOTION:
Proportion of Python users: 0.8416432449081739
Proportion of R users: 0.20540561352173412
Proportion of SQL users: 0.4141608593539445
```
*Proportion is basically the percentage of users*
### Experience
The **average Kaggle programmer has 5.29 years of experience**. The **minimum number of years of experience is 0**, and the **maximum is 30**. The distribution of experience is as follows:

* Less than 5 years: 18,753 (73.21%)
* 5-10 years: 3,167 (12.42%)
* 10-15 years: 1,118 (4.33%)
* 15-20 years: 1,069 (4.17%)
* 20-25 years: 925 (3.62%)
* 25+ years: 941 (3.76%)
#### Code
```python
# Aggregating all years of experience into a single list
experience_coding_column = []

for i in range(num_rows):
  experience_coding_column.append(survey_responses[i][0])

# Summarizing the experience_coding column
min_experience_coding = min(experience_coding_column)
max_experience_coding = max(experience_coding_column)
avg_experience_coding = sum(experience_coding_column) / num_rows
```

#### Printing out
```python
print('EXPERINCE RANGE:')
print("Minimum years of experience: " + str(min_experience_coding))
print("Maximum years of experience: " + str(max_experience_coding))
print("Average years of experience: " + str(avg_experience_coding))

```

#### Output
```
EXPERINCE RANGE:
Minimum years of experience: 0.0
Maximum years of experience: 30.0
Average years of experience: 5.297231740653729
```


### Compensation
The average Kaggle programmer earns $53,252.82 per year. The minimum compensation is $0, and the maximum is $1,492,951. The distribution of compensation is as follows:

* Less than $50,000: 14,827 (57.49%)
* $50,000-$100,000: 5,300 (20.84%)
* $100,000-$150,000: 1,973 (7.73%)
* $150,000-$200,000: 1,150 (4.47%)
* $200,000-$250,000: 807 (3.17%)
* $250,000+: 1,884 (7.32%)

#### Code
```python
# Aggregating all Compensation into a single list
compensation_column = []

for i in range(num_rows):
  compensation_column.append(survey_responses[i][5])

# Summarizing the compensation column
min_compensation = min(compensation_column)
max_compensation = max(compensation_column)
avg_compensation = sum(compensation_column) / num_rows

```

#### Printing out
```python
print('COMPENSATION RANGE:')
print("Minimum compensation: " + str(min_compensation))
print("Maximum compensation: " + str(max_compensation))
print("Average compensation: " + str(avg_compensation))
```
#### Output
```
COMPENSATION RANGE:
Minimum compensation: 0
Maximum compensation: 1492951
Average compensation: 53252.81696377007
```


## Catagorizing years of Experince

The following table shows the distribution of experience and average salary for data scientists in the Kaggle Programmer Survey 2021:


| Experience  | Number of Data Scientists     | Average Salary                |
| :-------- | :------- | :------------------------- |
< 5 years | 18,753 | $45,047
5-10 years | 3,167 | $59,312
10-15 years | 1,118 | $80,226
15-20 years | 1,069 | $75,101
20-25 years | 925 | $103,159
25+ years | 941 | $90,444

As we can see, the **average salary increases with experience**. Data scientists with **25+ years of experience earn the most**, while data scientists with **less than 5 years of experience earn the least**.

This suggests that there is a positive relationship between experience and salary in the data science industry. *As data scientists gain more experience, they are able to command higher salaries*.

It is also worth noting that the **distribution of experience is not uniform**. There are more data scientists with less than 5 years of experience than there are data scientists with more than 10 years of experience. *This suggests that the data science industry is still relatively young and that there is a growing demand for data scientists*.

Overall, the data suggests that experience is a **valuable asset for data scientists**. Data scientists with more experience are able to command higher salaries and are in more demand.
#### Code
```python
# Add a column to the survey responses for the bin
for i in range(num_rows):

  if survey_responses[i][0] < 5:
    survey_responses[i].append("<5 Years")

  elif survey_responses[i][0] >= 5 and survey_responses[i][0] < 10:
    survey_responses[i].append("5-10 Years")

  elif survey_responses[i][0] >= 10 and survey_responses[i][0] < 15:
    survey_responses[i].append("10-15 Years")

  elif survey_responses[i][0] >= 15 and survey_responses[i][0] < 20:
    survey_responses[i].append("15-20 Years")

  elif survey_responses[i][0] >= 20 and survey_responses[i][0] < 25:
    survey_responses[i].append("20-25 Years")

  else:
    survey_responses[i].append("25+ Years")
```
#### Code
```python
# Create lists for each bin.
bin_0_to_5 = []
bin_5_to_10 = []
bin_10_to_15 = []
bin_15_to_20 = []
bin_20_to_25 = []
bin_25_to_30 = []

for i in range(num_rows):

  if survey_responses[i][6] == "<5 Years":
    bin_0_to_5.append(survey_responses[i][5])

  elif survey_responses[i][6] == "5-10 Years":
    bin_5_to_10.append(survey_responses[i][5])

  elif survey_responses[i][6] == "10-15 Years":
    bin_10_to_15.append(survey_responses[i][5])

  elif survey_responses[i][6] == "15-20 Years":
    bin_15_to_20.append(survey_responses[i][5])

  elif survey_responses[i][6] == "20-25 Years":
    bin_20_to_25.append(survey_responses[i][5])

  else:
    bin_25_to_30.append(survey_responses[i][5])
```
#### Printing out
```python
# Checking the distribution of experience in the dataset
print("People with < 5 years of experience: " + str(len(bin_0_to_5)))
print("People with 5 - 10 years of experience: " + str(len(bin_5_to_10)))
print("People with 10 - 15 years of experience: " + str(len(bin_10_to_15)))
print("People with 15 - 20 years of experience: " + str(len(bin_15_to_20)))
print("People with 20 - 25 years of experience: " + str(len(bin_20_to_25)))
print("People with 25+ years of experience: " + str(len(bin_25_to_30)))


```

#### Output

```
People with < 5 years of experience: 18753
People with 5 - 10 years of experience: 3167
People with 10 - 15 years of experience: 1118
People with 15 - 20 years of experience: 1069
People with 20 - 25 years of experience: 925
People with 25+ years of experience: 941


```
#### Printing out
```python
# Checking the distribution of experience in the dataset
print("Average salary of people with < 5 years of experience: " +
      str(sum(bin_0_to_5) / len(bin_0_to_5)))
print("Average salary of people with 5 - 10 years of experience: " +
      str(sum(bin_5_to_10) / len(bin_5_to_10)))
print("Average salary of people with 10 - 15 years of experience: " +
      str(sum(bin_10_to_15) / len(bin_10_to_15)))
print("Average salary of people with 15 - 20 years of experience: " +
      str(sum(bin_15_to_20) / len(bin_15_to_20)))
print("Average salary of people with 20 - 25 years of experience: " +
      str(sum(bin_20_to_25) / len(bin_20_to_25)))
print("Average salary of people with 25+ years of experience: " +
      str(sum(bin_25_to_30) / len(bin_25_to_30)))
```
#### Output
```
Average salary of people with < 5 years of experience: 45047.87484669119
Average salary of people with 5 - 10 years of experience: 59312.82033470161
Average salary of people with 10 - 15 years of experience: 80226.75581395348
Average salary of people with 15 - 20 years of experience: 75101.82694106642
Average salary of people with 20 - 25 years of experience: 103159.80432432433
Average salary of people with 25+ years of experience: 90444.98512221042
```

 Salary increases with experience.
* Data scientists with 25+ years of experience earn the most.
* Data scientists with less than 5 years of experience earn the least.

The data science industry is still young.
* There are more data scientists with less than 5 years of experience than those with more than 10 years of experience.

 Experience is a valuable asset for data scientists.
* Data scientists with more experience are able to command higher salaries and are in more demand.

## Conclusion

In this data analysis project, we explored the *Kaggle Programmer Survey 2021* to understand the programming skills, experience, and compensation of data scientists.

We found that **Python is the most popular programming language** among data scientists, followed by R and SQL. The **average data scientist has 5.29 years of experience**, and the **average annual compensation is $53,252.82**. There is a positive correlation between experience and compensation, meaning that data scientists with more experience tend to earn more money.

These findings have implications for data scientists, aspiring data scientists, educators, and companies. Data scientists can use these findings to guide their career development and to understand the value of experience. *Aspiring data scientists can use these findings to shape their educational journey and to develop the skills that are most in demand in the industry*. Educators can use these findings to develop data science curricula that are relevant to the real world. Companies can use these findings to inform their hiring strategies and compensation models.

Overall, this data analysis project has provided valuable insights into the data science industry. These insights can be used by a variety of stakeholders to make informed decisions and to chart their course toward success in the data science field.


## Contact
I am **Athar Imran** a Data Scientist with a passion for using data to solve real-world problems.  I am proficient in Python, and I am always eager to learn more about data science and machine learning. I am a creative thinker and a problem solver, and  I am always looking for new ways to use my skills in Python to solve real-world problems.. I am looking for opportunities to use my skills and knowledge to make a positive impact on the world.

You can find me at [Twitter](https://twitter.com/atharimran728), [Github](https://github.com/AtharImran728) and [atharimran728@gmail.com](mailto:atharimran728@email.com)
