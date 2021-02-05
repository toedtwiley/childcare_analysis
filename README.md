# **Child Care Analysis**
-----------

###### **Installation Steps**
----------------------
* The first step is to get jupyter notebook on your computer (see site for details)
https://jupyter.org/install
* The next step is to download python on your machine
* If you want a one stop solution please just get anaconda (https://www.anaconda.com/products/individual)
* This is a cell based notebook so at the top you can just click 'cell' then 'run all cells'. After running you will be output a final file called 'final_table.csv' This will be output into the same directory and the python notebook

###### **Languages Used**
----------------------
For this task I went ahead and used python since we had to pull data from an api as well as scrape a website table. Python has very good libraries for this and didn't take to long to grab the data. I also used python because I did not want to set up a database and instead could just use the pandas library to store everything into a dataframe and then manipulate as needed.

For the SQL analysis section I ended up writing pseudo code for the actual query. I got the answers using python though.


###### **Assumptions and What I'd do different with more time (Tradeoffs)**
----------------------
**Assumptions**
One of the major assumptions that I made was using the phone number and provider name as a unique identifier. I noticed that both of these fields were common from all 3 data sources and also had 0 blank values. I ended up concatenating the provider name and the phone number to form one string. Once I had that string I ran it through a hash function so I could use a unique private key. This is so anytime I see this combo in any datafile the same unique key is given to that record of data. Allowing for an easy join key.

```python
provider_name = "daycare_one"
phone = "6195555555"
combined_string = "daycare_one6195555555"
unique_key = md5(combined_string)
```
I then took all the unique keys from all 3 data sets and used that as my source of truth and left joined all of information to that row.

**What I'd do different with more time (Tradeoffs)**
The biggest thing I would like to do is more cleaning. I was able to do a decent amount, by standardizing columns, and Coalescing multiple columns into one but I'm sure there is still more to do. I could have added more descriptive names for blank columns. For example, if there was a row of data without a type of provider I could have put "No Type Listed", it would make the result table a little nicer in my opinion. It would also help out any BI analyst who pulls the table into their weekly report and wonders what the missing values are from.

----------------------
Overall a fun project!

