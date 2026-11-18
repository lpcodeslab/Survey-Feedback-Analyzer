# Survey-Feedback-Analyzer
A Python-based Survey Feedback Analyzer that collects, cleans, and analyzes customer feedback using dictionaries, lists, loops, functions, and string operations. It calculates average ratings, identifies the longest feedback, counts specific words, and extracts unique words.

This project focuses on collecting and analyzing survey feedback using basic Python programming concepts. It performs text cleaning, word counting, rating analysis, and extracts useful insights from customer feedback.

# Objectives

Store preloaded feedback using a dictionary of lists.

Allow users to add more feedback entries.

Clean feedback by removing punctuation and extra spaces.

Convert feedback text into lowercase.

Count feedbacks containing specific words.

Calculate the average rating.

Find the feedback with the longest comment.

Identify unique words across all feedback entries.

Sort feedbacks based on ratings from highest to lowest.

# Technologies Used

Python

Lists and Dictionaries

For Loops

Conditional Statements

User-Defined Functions

String Methods

zip() and sorted()

# Project Features

1. Preloaded Feedbacks

   Starts with 10 predefined survey feedback entries.

2. Add More Feedbacks

   Allows users to enter additional details:

            Serial Number (automatically generated)

            Name

            Written Feedback

            Rating (1–5)

3. Text Cleaning

Removes punctuation such as periods, commas, exclamation marks and question marks.

Removes extra spaces.

Removes leading and trailing spaces.

Converts all feedback into lowercase.

4. Word Count Insights

Counts the number of feedback entries containing:

    good

    poor

    excellent

5. Final Summary and Insights

Displays the cleaned feedback data.

Calculates the average rating.

Identifies the feedback with the longest comment.

Displays the list of unique words.

6. Feedback Sorting

Sorts feedback entries by rating in descending order (highest to lowest).



# ==========================================
# PROJECT: SURVEY FEEDBACK ANALYZER
# ==========================================


# STEP 1: PRELOADED FEEDBACKS

feedback_data = {
'S_No': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],

'Name': ['Ravi', 'Meera', 'Sam', 'Anu', 'Raj','Divya', 'Arjun', 'Kiran', 'Leela', 'Nisha'],

'Feedback': ['   Very GOOD Service!!!','poor support,        not happy   ','GREAT experience! will come again.','okay okay...','   not    BAD','Excellent care, excellent staff!','good food and good ambience!','Poor response and poor handling of issue','Satisfied. But could be better.','Good support... quick service.'],

'Rating': [5, 2, 5, 3, 2, 5, 4, 1, 3, 4]
}


# STEP 2: ADD MORE FEEDBACKS

print("===== ADD MORE FEEDBACKS =====")
print(" ")

n = int(input("How many more feedbacks do you want to add? "))

for i in range(n):

print("\nFeedback", i + 1)

name = input("Enter Name: ")
feedback = input("Enter Feedback: ")
rating = int(input("Enter Rating (1-5): "))

feedback_data['S_No'].append(len(feedback_data['S_No']) + 1)
feedback_data['Name'].append(name)
feedback_data['Feedback'].append(feedback)
feedback_data['Rating'].append(rating)
print(" ")

# STEP 3: TEXT CLEANING

for i in range(len(feedback_data['Feedback'])):

text = feedback_data['Feedback'][i]

 # Remove punctuation
   text = text.replace('.', '')
   text = text.replace(',', '')
   text = text.replace('!', '')
   text = text.replace('?', '')

 # Remove extra spaces
    text = ' '.join(text.split())

 # Convert to lowercase
    text = text.lower()

    feedback_data['Feedback'][i] = text


# STEP 4: WORD COUNT INSIGHTS

def count_word_in_feedbacks(word):

count = 0

for feedback in feedback_data['Feedback']:

if word.lower() in feedback.split():
count += 1

return count


print("\n===== WORD COUNT INSIGHTS =====")
print(" ")
print("Feedbacks containing GOOD:",
      count_word_in_feedbacks("good"))
print(" ")
print("Feedbacks containing POOR:",
      count_word_in_feedbacks("poor"))
print(" ")
print("Feedbacks containing EXCELLENT:",
      count_word_in_feedbacks("excellent"))
print(" ")


# STEP 5: FINAL SUMMARY AND INSIGHTS

# Display cleaned feedback data

print("\n===== CLEANED FEEDBACK DATA =====")
print(" ")

for key, value in feedback_data.items():
    print(key, ":", value)
    print(" ")
    
print(" ")


# Calculate Average Rating

print("\n===== AVERAGE RATING =====")
print(" ")

total_rating = sum(feedback_data['Rating'])

total_feedbacks = len(feedback_data['Rating'])

average_rating = total_rating / total_feedbacks

print("Average Rating:", round(average_rating, 2))
print(" ")

# Find Longest Feedback

print("\n===== LONGEST FEEDBACK =====")
print(" ")

longest_feedback = ""
longest_name = ""
max_words = 0

for i in range(len(feedback_data['Feedback'])):

feedback = feedback_data['Feedback'][i]

word_count = len(feedback.split())

if word_count > max_words:

max_words = word_count
longest_feedback = feedback
longest_name = feedback_data['Name'][i]

print("Name:", longest_name)
print("Feedback:", longest_feedback)
print("Word Count:", max_words)
print(" ")


# Find Unique Words

print("\n===== UNIQUE WORDS =====")
print(" ")

unique_words = []

for feedback in feedback_data['Feedback']:

words = feedback.split()

for word in words:

if word not in unique_words:
unique_words.append(word)

print(unique_words)
print(" ")

# SORT FEEDBACKS BY RATING

print("\n===== FEEDBACKS SORTED BY RATING =====")
print(" ")

sorted_feedbacks = sorted(
zip(feedback_data['Name'],
   feedback_data['Feedback'],
   feedback_data['Rating']),
   key=lambda x: x[2],
   reverse=True
)

for name, feedback, rating in sorted_feedbacks:

print("Name:", name)
print("Feedback:", feedback)
print("Rating:", rating)
print("-------------------------")


# ==========================================
# END OF PROJECT
# ==========================================
