import csv

with open('kaggle2021-short.csv') as f:
  reader = csv.reader(f, delimiter=",")
  kaggle_data = list(reader)

column_names = kaggle_data[0]
survey_responses = kaggle_data[1:]

num_rows = len(survey_responses)
for i in range(num_rows):

  # experience_coding
  survey_responses[i][0] = float(survey_responses[i][0])

  # python_user
  if survey_responses[i][1] == "TRUE":
    survey_responses[i][1] = True
  else:
    survey_responses[i][1] = False

  # r_user
  if survey_responses[i][2] == "TRUE":
    survey_responses[i][2] = True
  else:
    survey_responses[i][2] = False

  # sql_user
  if survey_responses[i][3] == "TRUE":
    survey_responses[i][3] = True
  else:
    survey_responses[i][3] = False

  # most_used
  if survey_responses[i][4] == "None":
    survey_responses[i][4] = None
  else:
    survey_responses[i][4] = survey_responses[i][4]

  # compensation
  survey_responses[i][5] = int(survey_responses[i][5])

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

# Aggregating all years of experience and compensation together into a single list
experience_coding_column = []
compensation_column = []

for i in range(num_rows):
  experience_coding_column.append(survey_responses[i][0])
  compensation_column.append(survey_responses[i][5])

# Summarizing the experience_coding column
min_experience_coding = min(experience_coding_column)
max_experience_coding = max(experience_coding_column)
avg_experience_coding = sum(experience_coding_column) / num_rows

print('EXPERINCE RANGE:')
print("Minimum years of experience: " + str(min_experience_coding))
print("Maximum years of experience: " + str(max_experience_coding))
print("Average years of experience: " + str(avg_experience_coding))

# Summarizing the compensation column
min_compensation = min(compensation_column)
max_compensation = max(compensation_column)
avg_compensation = sum(compensation_column) / num_rows

print('')
print('COMPENSATION RANGE:')
print("Minimum compensation: " + str(min_compensation))
print("Maximum compensation: " + str(max_compensation))
print("Average compensation: " + str(avg_compensation))
print('')

# Categorizing Years of Experience
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

# Distribution of Experience and Compensation

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

print('')
# Checking the distribution of experience in the dataset
print("People with < 5 years of experience: " + str(len(bin_0_to_5)))
print("People with 5 - 10 years of experience: " + str(len(bin_5_to_10)))
print("People with 10 - 15 years of experience: " + str(len(bin_10_to_15)))
print("People with 15 - 20 years of experience: " + str(len(bin_15_to_20)))
print("People with 20 - 25 years of experience: " + str(len(bin_20_to_25)))
print("People with 25+ years of experience: " + str(len(bin_25_to_30)))

print('')
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



