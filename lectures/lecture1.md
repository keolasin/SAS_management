---
Week: 1
Lecture: Lecture 1
Topic: SAS Introduction
Instructor: Sadie Costello PhD, Jessica Ni
Course: SAS, PH 271K
Tags: SAS, Database Management, Introduction
---

# Introduction

SAS, incorporated in 1976

Uses a unique programming language, same for all platforms

- we'll use free SAS studio interface
- windows interface (used in most public health settings)

## Outline

- SAS Studio Interface orientation
- write a program
- data and proc steps
- SAS dataset
- SAS variable types
- temporary vs permanent datasets
- save a permanent dataset
- save a program

## First Program

```SAS

/* comments */

/* SAS variables can be either 
1) numeric or 
2) character ($) 

2 parts of a SAS program:
DATA Step: a group of statements that define your data, create a SAS dataset, create new vars, etc.


Syntax:

Capitalization does not matter, except:
- when dealing with the value of a character variable

Formatting does not matter for the compiler (but it's good to be legible)

Spelling does matter
All SAS statements must end with a semi-colon ;

Other things that matter:
Conventions for variable names and dataset names
- less than 32 characters
- starts with letter or underscore

*/

DATA FirstSAS;

INPUT ID Gender$ Height_in Weight_kg Tot_Chol; /* character delineation has to have $ at the end of the variable name */
DATALINES; /* creating a SAS dataset, rows sometimes called "observations" or "records", columns called "variables" */
1001 M 61 51.1 201
1002 F 62 52.2 202
1003 F 63 53.3 203
1004 M 64 54.4 204
; 
RUN;

PROC PRINT DATA = FirstSAS; /* print the dataset `FirstSAS` on our screen */
RUN;

/* after running code, check the log to identify errors */

PROC CONTENTS DATA = FirstSAS; /* provides metadata of the `FirstSAS` data */
RUN;

```

## Contents Metadata

LIB_NAME.DATASET_NAME indicates where the data is stored

## Temp vs permanent datasets

- temporary datasets will go away when session ends
	- work. = temp
	- no libname = temp
- permnanent datasets
	- must assign library name to make a permanent dataset
	
## Saving programs & Saving datasets

- Program
	- click save icon
	- choose save location
- Saving a Permanent Dataset
	- Define a libname
		- libname is one of the few SAS statements that doesn't occur in a DATA or PROC step
			- eight characters
			- begins with letter or _
			- only letters, numbers, _
			- example: `libname day1 "/home/u63125930/data"`, where libname tells us it's a library, day1 is the name, and "path/to/data" indicates the location to save
		- pathway to folder where you want to save your dataset
	- Use data step to save permanent SAS dataset
	
## Data come in different formats

- enter raw data directly in SAS
	- can use this with DATALINES (aka CARDS)
	- not practical with lots of data (research)
- Raw data file (.dat)
	- (.DAT files), National Death Index Data for example
	- Our first lab
	- Little SAS Book ch2
		- how to pull in very messy raw data
- CSV file
- SAS Dataset
- Excel, Access, Stata, R, etc.

### Data Dictionaries

Should always commpany a dataset

- usually a text or spreadsheet document
- 'readme' files can be super helpful