# BizCardX: Extracting Business Card Data with OCR

BizCardX is a simple program that anyone can use to get data from business cards. The software uses optical character recognition (OCR) technology to read the information on business cards, classifying the data using regular expressions before extracting it into an SQL database. A user interface created using streamlit allows users to retrieve the collected data. The BizCardX program has a straightforward UI that walks users through uploading a photo of a business card and then extracting the relevant data. The gathered data would be presented in an orderly, and its incorporation into the database would be as simple as clicking a button. The information in the database may be read, changed, and removed by the user at will.

## Prerequisites
1. **Python** -- Programming Language
2. **pandas** -- Python Library for Data Visualization
3. **easyocr** -- End-to-End Multi-Lingual Optical Character Recognition (OCR) Solution: text extraction from images
4. **streamlit** -- Python framework to rapidly build and share beautiful machine learning and data science web apps
5. **mysql.connector** -- Python Library that enables Python programs to access MySQL databases
6. **os** -- Python Module that provides functions for interacting with the operating system
7. **cv2** -- Python library which is very useful for computer vision applications such as video and image analysis

<br/>
   
## EasyOCR in Brief
Easy OCR is a font-dependent printed character reader based on a template matching algorithm. It has been designed to read any kind of short text (part numbers, serial numbers, expiry dates, manufacturing dates, lot codes, …) printed on labels or directly on parts.

The Highlight Features
- Comprehensive character verification with automatic training
- Grayscale analysis
- Text and character-level inspection
- Contrast, position and shape defect detection

<br/>

## Project Workflow
### Step 1 -- Installing and Importing the required Libraries
Firstly install all the required extensions/libraries/modules given above, if not installed
   
   > pip install (name of the library/module)

After installing the required libraries one need to import them in the program before one can use them.

   ```
   import streamlit as st
   import os
   from streamlit_option_menu import option_menu
   import mysql.connector as sql
   import easyocr
   import cv2
   import matplotlib.pyplot as plt
   import re
   import pandas as pd
   ```
<br/>

### Step 2 -- After that one need to create a MySQL Database in there local system. Now below is the Python code to connect to that SQL Database.

   ```
    hostname = "your host name goes here"
    database = "your database name goes here"
    username = "your username goes here"
    pwd = "your password goes here"
  
    mydb = sql.connect(host=hostname, user=username, password=pwd, database=database)
                       
    cursor1 = mydb.cursor()
   ```
<br/>

### Step 3 -- Initializing the easyOCR: Specifically for English Language(en)
I have initialized the easyOCR with the below code and one can explore more in the main.py file attached above.

   ```
   reader = easyocr.Reader(['en'])
   ```
<br/>

### Step 4 -- Run the below command to execute the main.py file and launch the Streamlit Application

   > streamlit run main.py

 - The Streamlit Application will open in your default browser. In this section, users are given the opportunity to submit their own business cards, the information on which may then be retrieved, saved, edited, or removed as necessary.
   
 - Once a user has uploaded their business card, the easyOCR library will extract any text that is present on the card. The extracted text will contain the name, cardholder name, designation, mobile number, email address, website URL, area, city, state, and pin code. These respective text classifications are accomplished via the use of loops and various regular expressions.

- The user can edit the classified data on screen to suit their needs. Also, provided the option to store derived data in a SQL database. One can save or transfer the data with a single click.

- Atlast also provided the option to read, modify, and delete the uploaded data in a SQL database, allowing easy access and manipulation of the data within the streamlit application.
