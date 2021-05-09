# Overview

In this exercise, we are provided with a raw text file containing records of votes cast for each candidate. The objective is to determine the winner; a secondary objective is to determine the county with the most votes cast.

While this exercise is simple in nature, most sophisticated voting analysis today is done using similar principles. While the immediate objective is to determine the winner of the election, there are multiple secondary objectives such as:
* Keep a historical record of voting patterns for future trend analyses enabing every participating political party determine where their strongholds are and where they should spend most money.
* Reconcile votes to see if they match expected trends and measure deviations if any. Detect instances of anolamies if necessary.
* Understand which counties cast the most votes and take subsequent actions. For example, the government may spend resources to increase the turnout in under-represented counties.

The data on voters and actual voting records is considered invaluable today and every political party in most of the world would spend considerable resources in collecting and analyzing such data to take strategic decisions.

# Input Data, Pseudocode and Analysis

## Input Data
In this file, we are given the actual voting data in Colorado's first congressional district for the US House of Representatives election. The data is recorded in a text file. Each line of the text file contains three fields in a comma separated format. The three fields are:
* Ballot ID
* County Name
* Candidate Name

## Objective
We have two objectives in this exercise.
* Find the winning candidate.
* Find the county with most votes cast.

## Methodology
A python program will be written that:
* Parses the input file and reads each line
* Keeps track of every candidate
  * When a vote is encountered for *this candidate*, increment the total votes case for *that candidate*
* Keeps track of every county
  * When a vote is encountered for *this county*, increment the total votes case for *that county*
* Determine the winning candidate from the list of candidates by finding the candidate receiving the most votes.
* Determine the county with the most votes cast from the list of counties.

## Pseudocode:
The actual code can be found in the python script *PyPoll_Challenge.py*. The pseudocode is given below.

```
Initialize a list to keep track of all candidates
Initialize a dictionary to keep track of votes received by each candidate

Initialize a list to keep track of all counties
Initialize a ductionary to keep track of votes cast in each county

Initialize variables to keep track of winning candidate count and the winning candidate name
Initialize variables to keep track of name and the total votes case for the county with most votes cast

for each line in the input file:

  Get this candidate name
  Get this county name
  
  if this candidate is not seen in the list of all candidates:
    add the candidate to this list
    initialize its vote count to 0 in the dictionary
  add 1 to the candidate vote count
  
  if this county is not seen in the list of all counties:
    add the county to this list
    initialize its vote count to 0 in the dictionary
  add 1 to the county vote count
  
  if this candidate vote count > winning candidate vote count:
    winning vote count --> this candidate vote count
    winning candidate name --> this candidate
    
  if this county vote count > most votes county vote count:
    most votes county vote count --> this county vote count
    most votes county name --> this county

```

## Code Observations:
* Python can easily parse and write to files. The *csv* module made parsing easy. Similar modules are available to parse input in any format (even Excel).
* The *dictionary* data structure excels in aggregating data. The key to a dictionary doesn't have to be a simple string; it could easily be an object.
* The *list* data structure in python excels in keeping track of a collection. Since lists are immutable, it's easy to add to them.
* Using the list and the dictionary in this manner allowed us to parse the input file only once and get all the answers from this single iteration. In module 2, we used a similar optimization technique to speed up the VBA script.


# Results of the Congressional Race in Colorado

The following table shows votes cast for each candidate.

| Candidate | Votes Received | Votes Received (%) | Winner? |
| --------- | -------------- |--------------------|---------|
| Charles Casper | 85,213 | 23.0% | - [ ] |
| Diana DeGette | 272,892 | 73.8% | - [ x ] |
| Raymon Anthony Doane | 11,606 | 3.1% | - [ ] |


The following table shows votes cast across each county.

