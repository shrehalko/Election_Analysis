# Election_Analysis
Performing Analysis on Election data in Colorado. 

## Table of Contents
- [Overview of Project](#OverviewProject)
  * [Background](#Background)
  * [Purpose](#purpose)
- [Pseudo Code](#Pseudocode)
- [Election Audit Results](#results)
    * [Total Votes Casted](#Totalvotes)
    * [Election Results per Candidate](#CandidateResults)
    * [Election Results per County](#CountyResults)
    * [Election Results report in Text File](#textResults)
    * [Election Results report on Terminal](#terminalResults)
- [Election Audit Summary](#Summary)
- [Resources](#resources)


## <a name="OverviewProject"></a>Overview of Project
### <a name="Background"></a>Background
I am assisting a Colorado Board of elections employee in an election audit of a recent local congressional election. There are 3 primary voting methods:
1. Mail-in Ballots: These votes are **hand-counted** at the central office.
2. Punch Cards : These are collected and then fed into a machine that tabulates vote totals and sends the resuts to the central office. These are **Machine counted.**
3. Direct Recording Electronic(DRE): Memory cards from DRE counting machines are sent to central office and read by computer. These are **Computer counted.**

The total votes cast by these three methods determine the final Election Results.


### <a name="Purpose"></a>Purpose

The total votes casted by the three methods have been populted in the excel file named [election_results.csv](election_results.csv).
I am tasked to do the following:
1. Total number of votes cast
2. The total number of votes for each candidate
3. The percentage of votes for each candidate
4. The winner of the election based on the popular vote.
5. The voter turnout for each county.
6. The percentage of votes from each county out of the total count.
7. The county with the highest turnout

 This process is usually done using Excel. But we would automate this process by using **Python**.<br> 
 **Our job is to generate a vote count report to certify this US congressional race.**

## <a name="Pseudocode"></a>Pseudo Code
1. We import the **dependencies** as below:
```
import csv
import os
```
2. Add a variable to **load the input csv file** and **the text file** where the report will be written.
```
file_to_load = os.path.join("Resources", "election_results.csv")
file_to_save = os.path.join("analysis", "election_results.txt")
```
3. Next,we **open** the file and **read** the file.
```
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)
```
4. Run a **For** loop to **read every record from the CSV** file. Retrieve the candidate name and county name and count their votes.

 Below is the snap shot of the code:
 ```
     for row in reader:
        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1]

        # If the candidate does not match any existing candidate add it to the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # Check if the county does not match any existing county in the county list.
        if county_name not in county_list:

            # Add the existing county to the list of counties.
            county_list.append(county_name)

            # Begin tracking the county's vote count.
            county_votes[county_name] = 0

        # Add a vote to that county's vote count.
        county_votes[county_name] += 1
```
5. Next, **open the output file and the write the results** to it. Also display the results on the terminal.
```
with open(file_to_save, "w") as txt_file:
    * Print the total votes
    * write to file.
      txt_file.write(election_results)
    * Print the counties and the total votes and percentage of votes for each county.
    * Print the candidates and the total votes and percentage of votes for each candidate.
    * Print the winning candidate and the winning county.
    * Write the results to the output file.
```      
## <a name="results"></a>Election Audit Results

### <a name="Totalvotes"></a>Total Votes casted

The total votes casted this election : ***369,711*** </n> 

### <a name="CandidateResults"></a>Election Results per Candidate

The table below shows the election results **per candidate**:

         Candidates        |  Total Votes  |  % Votes
    -----------------------|-------------  |---------
    Charles Casper Stockham|   85,213      |  23.0%
    Diana DeGette          |  272,892      |  73.8%
    Raymon Anthony Doane   |   11,606      |   3.1%  

**Winning Candidate**: ***Diana DeGette*** received ***73.8%*** of the vote and ***272,892*** of total votes. 

### <a name="CountyResults"></a>Election Results per County

The table below shows the election results **per county**:

        County Name     |  Total Votes  |  % Votes
    --------------------|-------------  |---------
          Jefferson     |    38,855     |   10.5%
          Denver        |   306,055     |   82.8%
          Arapahoe      |    24,801     |    6.7%  

**Winning County**: ***Denver*** with an ***82.8%*** vote of the total count and ***306,055*** of total votes. 

### <a name="textResults"></a>Election Results report in Text File

<p align="center"> <img src = "election_results.png" width ="45%"> </p> 

### <a name="terminalResults"></a>Election Results report on Terminal

<p align="center"> <img src = "Terminal_results.png" width ="45%"> </p> 

## <a name="Summary"></a>Election Audit Summary
There is a statement to the election commission that explores how this script can be used for any election, with two examples for modifying the script. (4 pt)

There are various advantages of using **Python** over **Excel**. That was the main reason for choosing Python for this project. Few of the advantages are listed below:
* Automation of code 
* Reusability of code
* Faster execution
* Easy to write and read the code

This code can be reused by Election Comission for any election by just changing a few lines of code. Below are the few changes that can be done to further automate the process:
1. We can modify the code to get the winning candidate in each county.
2. A much larger dataset can be used containing the election data not only for Colorado, but for other states as well. This way we can create a report of the winning candidates for all states.
3. The input file being read in the code is a CSV file. We can change the code to read a file in any format such as JSon,xls,txt by importing the proper dependencies.


## <a name="resources"></a> Resources
[1] [Code for Election Analysis](PyPoll_Challenge.py) <br>
[2] [Election Data](Resources/election_results.csv) <br>
[3] [Election Results Printed to Command Line](Terminal_results.png)  <br>
[4] [Election Results Saved to Text File](Analysis/election_results.txt) <br>
[5] Software: 
* Python 3.10.2
* Visual Studio Code 1.64.2
