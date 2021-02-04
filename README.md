# Decoding Program Creation Support Tool
## Introduction
### What is this software ?
This software is a tool to list up candidates of matching parameter names for the received Argo float’s messages when the output parameter names differ depending on the version. 
It compares the output parameter names of msg files between new and previos versions, and then lists the parameter name candidates corresponding to each parameter stored in the msg files of new version by the Jarro-Winkler distance method.
### Motivation to develop the software
The names of technical information items in Argo data often change slightly due to manufacturer's reasons, and DAC and DMQC operators need to check for parameter differences every time a new float is delivered. 
 In the past, this was done visually, but it tends to oversight differences and to make errors. By using the Jaro-Winkler distance method which is a string comparison method that mainly used in natural language processing, users can find candidate parameter names that may match and reduce human errors when checking for modifications.
### Machine environment
Need Python3.x
### How to get the software? 
Freely available from github site
## Requirement of environment
### Development of operating environment 
#### Application language
Installing Python3.x
Getting and installing Python language on your computer. Check your OS and visit the Python official site (https://www.python.org/).
#### Installing necessary libraries
```
$pip install pandas python-Levenshtein
```
pandas. possible to use anaconda
#### Format of information table for msg and tech files (see sample file “Navis.xlsx” for Navis float）
Written by MS Excel.
1st Colimn: Database name (here name of JAMSTEC’s DB)
2nd column: Item name of output file from float
19th-21th columns: decode name of floats (here JAMSTEC’s management name)
“msg” row “log” row: msg file and log file output from floats
### How to use on your computer?
On the command line just write a command as follows.
```
$python3 FloatCheck.py {xlsx file }{type.msg}
```
#### Flow chart and procedure to get results
![flowchart](https://user-images.githubusercontent.com/5100793/106864327-0caf8f80-670d-11eb-959d-9f3671098932.png)

Read Excel (information) file  
Input values in the dataframe tabe in the pandas, then compare new data with old one  
Read float raw data (exchange from binary to ascii is implemented by a tool by manufacturer)  
Using Jaro Winkler method, result is written in Dataflame to compare with characters  
Sort by values and show the top 3 result  
```
% EmergencyTimerInterval is probably TelemetryRetryInterval ( 70.0% )
or DeepDescentTimeout ( 55.00000000000001% )
or DeepProfileFirst ( 54.0% )
```
### Parameters
Stored parameters information  
-scheme : (Dataframe)  Excel scheme information  
-tech : (Dataframe) Excel technical information  
-msgdf : (Dataframe) Msg file  
-logdf : (Dataframe) Log file  
## How to use: in the case if users change the paramter
-6 column: Change the reading excel file name at pd.read_excel method
-10 column: Identify the row and tab name of excel file to store values in parameters
-30 column: Change file names  of raw data (system_log and science_log) in the with open method

## License
Copyright [2021] [JAMSTEC GOORC RIGC]  
The licence of Apache is based on “Apache License Version 2.0”. If users use this program, the users need to follow the licence, which can be obtained from following address.  
http://www.apache.org/licenses/LICENSE-2.0  
Unless otherwise ordered by applicable law or written agreement, the software distributed under this license is distributed as it stands, without warranty or condition of any kind, either express or implied. See the license regulated by the rights and restrictions in this program’s license.

