# Overview

In this exercise, we are provided with a raw text file containing records of votes cast for each candidate. The objective is to determine the winner; a secondary objective is to determine the county with the most votes cast.

While this exercise is simple in nature, most sophisticated voting analyses today are done using similar principles. While the immediate objective is to determine the winner of the election, there are multiple secondary objectives such as:
* Keep a historical record of voting patterns for future trend analyses enabing every participating political party determine where their strongholds are and where they should spend most money.
* Reconcile votes to see if they match expected trends and measure deviations if any. Detect instances of anolamies if necessary.
* Understand which counties cast the most votes and take subsequent actions. For example, the government may spend resources to increase the turnout in under-represented counties.

The data on voters and actual voting records is considered invaluable today and every political party in most of the world spends considerable resources in collecting and analyzing such data to take strategic decisions.

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
| Charles Casper | 85,213 | 23.0% | <ul><li>- [ ] </li> |
| Diana DeGette | 272,892 | 73.8% | <ul><li>- [x] </li> |
| Raymon Anthony Doane | 11,606 | 3.1% | <ul><li>- [ ] </li> |


The following table shows votes cast across each county.

| County | Votes Cast | Votes Cast (%) | Most Votes? |
| ------ | ---------- |----------------|-------------|
| Jefferson | 38,855 | 10.5% | <ul><li>- [ ] </li> |
| Denver | 306,055 | 82.8% | <ul><li>- [x] </li> |
| Arapahoe | 24,801 | 6.7% | <ul><li>- [ ] </li> |
 
# Election Commission Statement and Future Enhancements

* **Election Commission Statement**: The *PyPoll_Challenge.py* script can read a comma separated text file containing actual voting records of any election (each comma separated record being ballot ID, county name and the candidate name). The script produces the total votes and the percent votes received by each candidate, the total votes and percent votes case across each county, and finally, the winner of the election as well the county where most votes are cast. This script can work to analyze any election data and produce the said output, as long as the election data input conforms to the required format.
* **Uniqueness and validity of ballots**: The first enhancement to the code is to check if each ballot is unique and that there are no duplicates. Another objective is to determine if the ballots are valid. For example, if we could pass in the python program argument a *range* of valid ballots, we could confirm if the given ballot is within that range.
  * Which data structure could be used to check uniqueness? Either a list or a dictionary could be used. For the *list* approach, each uniquely discovered ballot ID could be appended to the list; before appending a newly found ballot ID, we could scan the list to check if one exists. For the *dictionary*, a new entry could be added to the dictionary with ballot ID as the *key*. Before adding a newly discovered ballot ID as the key, we could check if one exists. The dictionary approach is superior since a dictionary lookup is much faster than a list lookup. Intuitively too, it makes sense, since a dictionary key works the same way an *index of a real dictionary* works. 
* **Candidate results for each county**: The second enhancement is to analyze how a given candidate performed in each county. Even though a candidate might have lost a congressional election, by understanding their performance at the county level, the political party can understand its strongholds and this information could prove useful for local elections.
