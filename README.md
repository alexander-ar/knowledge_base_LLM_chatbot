# knowledge_retrieval_LLM_chatbot
LLM based chatbot that takes a text document as input and answers questions about document content while retaining memory of the conversation. Works from command line.


## Overview
The application leverages GPT 3.5 model that is accessed through OpenAI API.  In this version of the app, the app accepts two text files as input. The first text file contains contents that the app users are interested in (or for which the app is designed). The second text file contains a list of questions concerning the contents in the first text file. 

For additional requirements,  app is designed to handle multiple questions about the same topic in succession (i.e. retain memory of the conversation).  The app is also tailored to answer questions on the topic contained in the input document. If asked about significantly unrelated topics (e.g. “Give me a recipe for a cheesecake”), the app may respond by saying ``The question is not relevant to the domain of interest.``.

## How to Run This Application
The code for this application is contained in the root directory - file `app.py`.  This application is designed to run from command line.  Navigate to the folder where the app.py is saved and then run:
```
python3 app.py --content_text_file "path_to_file/content_file.txt" --question_text_file "path_to_file/questions_file.txt" 

```
where `path_to_file/content_file.txt` should be the location for the file with content and `path_to_file/questions_file.txt` is a path to text file containing user's questions (one question per line).

## Application Dependencies
The dependencies for this application are described in the `requirements.txt` file located in the root directory.  From the same directory, from the command line run:
```
pip install -r requirements.txt
```
to install the required python libraries.

## Setting Environmental Variables
Environmental variables needed to authenticate OpenAI connection are located in .env file.  

## Example of Use
The root directory contains a content text file named `Software_Engineering_Practices.txt` and a input text file with sample questions `questions_list.txt` with sample questions, follow up questions, as well as a question unrelated to the document's content:
```
What does TOP stand for?
What kind of algorithms does it apply to?
What are the phases of the development life cycle?
What is their number?
Give me a recipe for an omelet
What are coding standards?
```

Here is an example of the app use with the two sample text files as an input:
```
$ python3 app.py --content_text_file "Software_Engineering_Practices_TOP.txt" --question_text_file "test_question_list.txt" 

Answer to question 1: 

TOP stands for Technical Operating Procedure. 

Answer to question 2: 

The TOP applies to both rule-based and Machine Learning (ML) based algorithms within the PHC Imaging group. However, for ML based algorithms, the TOP is limited to locked models and does not cover continuously learning models. 

Answer to question 3: 

The phases of the development life cycle in the context of the TOP are:
1. Initialization & preparation
2. Development/Experimental phase
3. Qualification phase
4. Deployment phase

Answer to question 4:

The number of phases in the development life cycle is 4.

Answer to question 5:

The question is not relevant to the domain of interest.

Answer to question 6:

Coding standards refer to a series of recommendations and mandates for a specific programming language that determine the programming style, procedures, and methods for various aspects of the program written in that language. They provide guidelines for developers to ensure consistency, readability, quality, scalability, and maintainability of the code.
```


## Author and Acknowledgments
All the code in this repo was created by the author of this repo, Alexander Arefolov. 
