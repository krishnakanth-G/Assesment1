# Assesment1

## Introduction

Hello, my name is Krishnakanth Gunta, and in this document I will describe how I solved all of the questions in the assessment. I executed each question in a separate python/ipynb file and labelled it with the question number.  All the solved questions are uploaded in my google drive (click here).

## Part 1
Question 1: Write a regex to extract all the numbers with orange color background from the below text in italics.
![alt text](https://github.com/krishnakanth-G/Assesment1/blob/main/img/0.png)

First take the above text in to a python dictionary and pick the values of the dictionary. Apply the regular expression to each value in the values and select the first integer. Figure-1 depicts the code and output.

<p align="center">
 <img width="800" src="https://github.com/krishnakanth-G/Assesment1/blob/main/img/1.png" alt="img"><br>
 Figure-1
</p>



Question 2:  Here’s the list of reviews of Chrome apps - scraped from Play store. Datset link: https://drive.google.com/file/d/1SuiFw4MYxOBlqsRgyXLfch28-gzx8bX6/view

Problem statement - There are times when a user writes Good, Nice App or any other positive text, in the review and gives 1-star rating. Your goal is to identify the reviews where the semantics of review text does not match rating. Your goal is to identify such ratings where review text is good, but rating is negative so that the support team can point this to users. Deploy it using - Flask/Streamlit etc and share the live link.

The dataset contains many attributes but our main focus should be on review text and stars attributes. First, I cleaned the review data by removing special characters using regular expression, and stop words using NLTK tools. The code snippet for cleaning the reviews is in figure-2.1 
 
<p align="center">
 <img width="800" src="https://github.com/krishnakanth-G/Assesment1/blob/main/img/2.1.png" alt="img"><br>
 Figure-2.1
</p>

After cleaning the reviews, Filter the records where star is 1 or 2 to get all the negative reviews. Then apply a sentiment analyzer for each review and find the sentiment using NLTK sentiment analyzer. The code snippet for the sentiment analyzer is in figure 2.2
 
<p align="center">
 <img width="800" src="https://github.com/krishnakanth-G/Assesment1/blob/main/img/2.2.png" alt="img"><br>
 Figure-2.2
</p>

After getting the sentiment of the review filter all the records where sentiment is positive and then output the records using streamlit. 
Live Link: https://share.streamlit.io/krishnakanth-g/review-analysis/main/ReviewAnalysis.py

Question 3: Ranking Data - Understanding the co-relation between keyword rankings with description or any other attribute. Here’s the dataset.
Suggested questions:
1. Is there any co-relation between short description, long description and ranking? Does the placement of keyword (for example - using a keyword in the first 10 words - have any co-relation with the ranking)?
2. Does APP ID (Also known as package name) play any role in ranking?
3. Any other pattern or good questions that you can think of and answer?

The dataset contains 10 attributes and 3066 records. It is related to ranking of different category of browsers types. There are 7 different categories in keyword (browser). There are 8 different App ID’s. There are 13 and 9 different short and long descriptions respectively. For checking correlation between two variables i am using Chi squares test, the hypothesis of chi squared test is

* H0: There is no relation between the variables
* H1: There is relation between the variables

we can verify hypothesis using P-value that is if the P-value is higher than 0.05, H0 will be accepted otherwise rejected.<br>
Answers for suggested questions

1. Is there any co-relation between short description, long description and ranking? Does the placement of keyword (for example - using a keyword in the first 10 words - have any co-relation with the ranking)? <br> Ans) There is strong correlation between short description, long description and ranking which is evident from the p-value (0.0) of the chi squared test.
2. Does APP ID (Also known as package name) play any role in ranking? <br> Ans) To know the answer we need regression analysis which estimates parameters in a linear equation that can be used to predict values of one variable based on the other. After analyzing the data, it is found that App ID is playing an important role to provide the rank because the regression score is quite good with the App ID itself.
3. Any other pattern or good questions that you can think of and answer?
Ans) The other question which I got when I see the problem is
* 	what are the most frequent words in long description?
A) The most frequent words in long description are web, browser, serach, private, engine, etc. Word cloud of words is shown in figure-3.1
 
Figure-3.1

* what are the most frequent words in short description?
A) The most frequent words in short description are private, browser, amp, etc.
Word cloud of words is shown in figure-3.2

 
Figure-3.1

* Are there any common words between short and long description?
A) From the word clouds for short and long descriptions, we can observe that they have some words in common like browser, private, ad blocker, etc.

## Part 2
Question 1: Check if the sentence is Grammatically correct: Please use any pre-trained model or use text from open datasets. Once done, please evaluate the English Grammar in the text column of the below dataset. DataSet Link
Optional - if you can indicate the grammatical accuracy of sentences in percentage or on number scale (1-10), that would be an added plus - but is not essential.

I used a fine-tuned version of Google's T5 model. T5 is a text-to-text model, meaning given text, it produces a standalone piece of text. It is currently considered "state-of-the-art," and the largest model even outperforms the human baseline on the General Language Understanding Evaluation benchmark. The pre-tuned model is then applied to a sample of the given dataset to produce the correct grammatical sentence. Then a similarity score between given and produce text is calculated. Using the similarity score we will decide whether the given text is grammatically correct or not. In Figure-4, few rows of the output data frame are shown.
 
Figure-4
Note: The output in figure-4 will be different if we run the code again because I used random sampling of data. 


