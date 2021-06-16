# PeakData Hiring Assingment
Given a list of medical publications, provide a list of unique authors and institutions.

### Table of Contents

1. [Installation](#installation)
2. [Run](#run)
3. [Potential failures and bottlenecks](#bottlenecks)
4. [I want to go into production with it! What should I do?](#steps)

## Installation <a name="installation"></a>
I suggest that you upload the attached notebook in a Colab (the next section describes how to do it), but if you prefer to run the code locally, follow the instructions below. They should work both with linux console and Windows PowerShell.

1. Make sure that your Python installation has pip

`pip -h`

2. Install virtual envinronment

`pip install virtualenv`

3. Create virtual envinroment 

`python -m venv *env_name*`

4. Activate virtualenv

`source *env_name*/bin/activate`

4. Install necessary libraries (this will take a while)

`pip install -r requirements.txt`

## Running a code <a name="run"></a>
All the code is in the jupyter file because in my opinion this is the best source of information and visualization when creating ETL pipelines.

The easiest way to run code is to upload it to the colab environment. To do this, go to colab.research.google.com, click upload and upload the .jpynb file. Then upload the publications_min.csv.gz file using the file menu on the left and run all the cells with the code in sequence while reading markdown with the explanation.

If you want to run the code locally, being in location of PeakData_Assignment.jpynb type in the console:

`jupyter lab .`

Go to URL that will show up and open .jpynb file.

## Potential failures and bottlenecks <a name="bottlenecks"></a>

Many of the assumptions and possible errors are described directly in the notebook's markdowns. However, when analyzing individual cells, one should bear in mind:

1. The code will fail when it cannot find the loaded file, because I have not introduced mechanisms to check the file instance.

2. I tried to use the entire range of data engineer / scientist tools, so there are both well-proven functions, e.g. from the gensim library, and those created by me using regexes. The latter will not be resistant to "hacking" and you should bear in mind that unit tests have not been written for them, as this was not the subject of the task and the code will not be used in a production environment.

3. The code should run relatively fast as it was written in the pythonic way. However, there are solutions that will not work so well for larger data, e.g. one function uses a combination, or the data is fully loaded into memory.

4. Last but not least. I had to make some assumptions while creating the code. They are explained in the notebook and relate to some controversial decisions. Based on the example output, I decided that the initials of scientists do not count for us, this may lead to a situation when we consider someone with the same name and surname as one person, even though, for example, one of them will have a middle name written as an initial. Perhaps a better solution would then be to keep the first name and initial and save it to a .csv file. To check if similar names refer to the same person, you would have to look at the affiliation and see if people with similar names are working in different places. However, this still does not solve the problem, because a scientist, like any human, can change jobs, so the publication date could also be taken into account, if there is a short time between them, we are probably dealing with a different person. However, these are solutions worth considering in the case of a customer product.

## I want to go into production with it! What should I do?<a name="steps"></a>

1. Convert code provided in jupyter notebook to Python script.
2. Write Unit Tests.
3. Consider informations provided within markdowns and section "Potential failures and bottlenecks"
