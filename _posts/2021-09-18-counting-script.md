---
layout: post
title:  "Jack Davis - Gibbon and Smith Counting Script"
date:   2021-09-18 20:08:00 -0400
categories: jekyll update
---

Below you will find my Python script designed to count the words in Gibbon's Rise and Fall of the Roman Empire and Smith's Wealth of Nations. Contained are also personal annotations to help me remember and notes for future reference, and they have been commented out within the code.

Steps to take:

1. Get texts in raw form
2. Print all the lines
3. Get words from lines
4. Instantiate dictionary
5. Make if/else command with dictionary to store data
6. Sort all the words
7. Print words with frequency
8. Get rid of all lowercase words and words that, if lowercase, were in the word list (The) - if you find The in lowercase, get rid of The
9. Print words
10. Generalize everything above to be a replicable function

```
!git clone https://github.com/msaxton/gibbon-decline-and-fall-text.git

fullgibbontext = open('/content/declineandfall-gut.txt')

def countwords(textfilename): # this creates a replicable function
  gibbonchapter = open(textfilename)
  totalwords = 0 #this makes it so that all the words can be counted in total
  worddict = {}
  #for line in gibbonchapter:
      #line = re.sub('[/.;,:"\(\)]',' ',line) # adapted from the code in Micah's script used in class
      # unable to figure out how to appropriately get rid of punctuation, but Peter said it doesn't matter for now so I won't worry
      #words=line.split()

  for line in gibbonchapter:
    #print(line.split())
    for word in line.split(): #colon auto-formats, otherwise need a tab 
      totalwords = totalwords + 1
      if word in worddict:
        worddict[word] += 1
      else: worddict[word] = 1 #this makes it so if item already in dictionary, adds one; if not, starts with one
  print(totalwords)
  for word in sorted(worddict,key=worddict.get,reverse=True):
    if word.lower() in worddict:
      continue # says to go past and ignore lowercase word
    if worddict[word] >=100:
      print(word,worddict[word])

  return(worddict) # tells the computer that this is over

# told not to worry about punctuation because it involves regular expressions, which we haven't done yet
  # this prints each word followed by its frequency - still has capitalization
    # sorted() sorts things numerically or alphabetically
# sorted will always take a list or dictionary, need to specify which thing it should sort - key or associated value
# Here, I've told it to get the associated value
# Since it goes from lowest to highest, need reverse=True command to sort by actual frequency



#want the key to be the word, item associated with key to be number
#first check if item is already in dictionary; if yes, add one, if no, instantiate with 1
# print(sorted(worddict,key=worddict.get,reverse=True)) 

# issues I've had: unable to have the computer distinguish what's part of the actual text and what's added by the editors, inability to remove punctuation


countwords('/content/declineandfall-gut.txt')
```


**The below is the script for counting words from Smith's Wealth of Nations**

```
fullsmithtext = open('/content/wealthofnations-gut.txt')

def countwords(textfilename): 
  smithchapter = open(textfilename)
  totalwords = 0 
  worddict = {}
  #for line in smithchapter:
      #line = re.sub('[/.;,:"\(\)]',' ',line) # adapted from the code in Micah's script used in class
      # unable to figure out how to appropriately get rid of punctuation, but Peter said it doesn't matter for now so I won't worry
      #words=line.split()

  for line in smithchapter:
    
    for word in line.split(): 
      totalwords = totalwords + 1
      if word in worddict:
        worddict[word] += 1
      else: worddict[word] = 1 
  print(totalwords)
  for word in sorted(worddict,key=worddict.get,reverse=True):
    if word.lower() in worddict:
      continue 
    if worddict[word] >=10:
      print(word,worddict[word])

  return(worddict) 

# told not to worry about punctuation because it involves regular expressions, which we haven't done yet
  # this prints each word followed by its frequency - still has capitalization
    # sorted() sorts things numerically or alphabetically
# sorted will always take a list or dictionary, need to specify which thing it should sort - key or associated value
# Here, I've told it to get the associated value
# Since it goes from lowest to highest, need reverse=True command to sort by actual frequency





# print(sorted(worddict,key=worddict.get,reverse=True)) 

# issues I've had: unable to have the computer distinguish what's part of the actual text and what's added by the editors, inability to remove punctuation

countwords('/content/wealthofnations-gut.txt')

```