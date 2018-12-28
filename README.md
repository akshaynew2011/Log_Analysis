# Logs Analysis

This is the third side project of the Software Development

The objective of the Logs Analysis Project is to create a reporting tool that prints out reports (in plain text) based on the data in the database. This reporting tool is a Python program using the psycopg2 module to connect to the database.


## How do I run this?

### 1. Setup: Configure VM & Database

**Step 1:** Download and install [Vagrant](https://www.vagrantup.com/) and [VirtualBox](https://www.virtualbox.org) to manage the virtual machine


**Step 2:** Configure the VM according to need


**Step 3:**  Download the database dump from the [downloads folder](downloads/) or [this link](https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip).

Then, copy the database dump `newsdata.sql` to the `vagrant/` .

**Step 4:**  Download the python programs (`reportingtool.py` and `dbmanager.py`) from the current folder. Then, copy them to the `vagrant/` (one of the folders you downloaded in step 2).

**Step 5:** Open the terminal. Then, run the following commands:

```
# Install & Configure VM
cd /path/to/vagrant
vagrant up

# Log into machine
vagrant ssh

# Populate database using dump in shared folder 
cd /vagrant 
psql -d news -f newsdata.sql

# Log out of machine
# <Ctrl + D>

# Destroy machine once done
vagrant destroy

```

Note: If this is the first time you're running [Vagrant Up](https://www.vagrantup.com/docs/cli/up.html) command, you need to wait a while after running the command. 


### 2. Run the Reporting Tool

Open the terminal. Then, run the following commands:

```
# Launch & Login to machine
cd /path/to/vagrant
vagrant up
vagrant ssh

# Open shared folder
cd /vagrant 

# Run the program
python reportingtool.py
```

### Extra: Using the PSQL CLI

Open the terminal and use the following commands to familiarise with the database:

```
# Log into machine
cd /path/to/vagrant
vagrant up
vagrant ssh

# Open PostgreSQL Interactive Terminal
psql

# Commands to navigate and familiarise
\list # list all databases
\connect news # connect to the 'news' database
\dt # list all tables of the connected database
\d articles # show info about the table 'articles'
<CTRL+D> # terminate command and exit shell
```
## Questions to answer

The reporting tool will answer the following questions

**(1) What are the most popular three articles of all time? Which articles have been accessed the most? Present this information as a sorted list with the most popular article at the top.**

Example:

- "Princess Shellfish Marries Prince Handsome" — 1201 views
- "Baltimore Ravens Defeat Rhode Island Shoggoths" — 915 views
- "Political Scandal Ends In Political Scandal" — 553 views

**(2) Who are the most popular article authors of all time? That is, when you sum up all of the articles each author has written, which authors get the most page views? Present this as a sorted list with the most popular author at the top.***

Example:

- Ursula La Multa — 2304 views
- Rudolf von Treppenwitz — 1985 views
- Markoff Chaney — 1723 views
- Anonymous Contributor — 1023 views



**(3) On which days did more than 1% of requests lead to errors? The log table includes a column status that indicates the HTTP status code that the news site sent to the user's browser.**

Example:

- July 29, 2016 — 2.5% errors


## References

- [String Functions & Operators](https://www.postgresql.org/docs/9.5/static/functions-string.html)
- [Data Type Formatting](https://www.postgresql.org/docs/8.3/static/functions-formatting.html)
- [Casting](https://www.postgresql.org/docs/10/static/sql-createcast.html)
- [Aggregate Functions](https://www.postgresql.org/docs/9.5/static/functions-aggregate.html)
- [Subqueries](https://www.postgresql.org/docs/9.4/static/functions-subquery.html)
- [PSQL CLI Commands](https://www.postgresql.org/docs/9.2/static/app-psql.html)

