# CTEC 121 - Lab No. 7

## Overview

This assignment will have you build a program that will be capable of converting text from English to 4 other languages.

## Lab Details

1. Install the Requests Python library from the MS DOS command prompt. There’s a video in Canvas along with some instructions that tell you on how to do this. It will also be reviewed during class.
2. Test that the requests library is installed correctly by entering **import requests** at the Python command prompt. Contact the instructor if you need assistance.
3. Now create a new Python program and name it Watson_Translate.py
4. Place the following comments at the top of your program:

```python
# CTEC 121 Intro to Programming and Problem Solving
# Bruce Elgort / Clark College
# Using IBM Watson's Language Translator
```

5. Now place **import requests** and **import json** below the comments
6. Now create a function named cls(). The job of cls() is to print 5 new \n’s when called.
7. Now create a function named translate_text() as follows:

```python
def translate_text(text,source,target):
    username = '2f7d5590-976c-4df9-bd00-1736c808381b'
    # The instructor will provide you with the password in Canvas
    password = ''
    # the statement below should all be on a single line
    watsonUrl = 'https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01'

    headers = {"content-type": "application/json"}
    data = {'source': source,
            'target':target,
            'text':text}

    try:
	     # the statement below should all be on a single line
        r = requests.post(watsonUrl, auth=(username,password),headers = headers, json=data)
        return r.text
    except:
        return False
```

8. In the function you just created what are the three formal parameters? What purpose do they serve in the function? Place your answer as a comment in your code.
9. In a comment answer the following question “Explain how the try/except works by placing a comment in the function. Be as specific as possible.
10.	Now create a function named welcome() that has the following code in it:

```python
    message = "Welcome to the IBM Watson Translator\n"
    print(message + "-" * len(message) + "\n")
    print("Have fun!\n")
```

11.	In your code answer the following question by placing a comment in the welcome() function “What is the purpose of the len() around the message? What specifically is it doing?
12.	Now create a main function.
13.	In the main function call the cls() and welcome() functions

Now copy and paste this code into the main function:

```python
    data = input("Enter some text to be translated: ")

    print()
    print("What language should I translate it to?")
    print("1) Spanish")
    print("2) Arabic")
    print("3) French")
    print("4) Portuguese")
    print()
    target = input("Select a language from the list above: ")

    if target == "1":
        target = 'es'
    elif target == "2":
        target = 'ar'
    elif target == "3":
        target = 'fr'
    elif target == "4":
        target = 'pt'

    results = translate_text(data,'en',target)
    results = json.loads(results)

    for i in results['translations']:
        print(i['translation'])

    print()
    print("Here is the text translated for you:")
    print(results)
    print('The number of words:',results['word_count'])
    print('The number of characters:',results['character_count'])

```

14.	Now test your code and see if it runs.
15.	Question: Explain what this line of code does:
results = translate_text(data,'en',target). Place the answer as comment in your code
16.	Try each of the languages using a sentence or two of your choice.
17. **IMPORTANT:** After you are done testing, be sure to first remove the code with the password. In it. Replace it with an empty string.
17.	Stage, commit and push your code back to GitHub once you are done.