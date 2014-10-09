---
layout: post
title: What SQLite can do for you and how it interacts with Python
---

![Image]({{ site.baseurl }}/images/sqlite.png)

In case your not up to date with latest adventures I've been attending the coder's bootcamp Byte Academy. My latest assignment was to dive into the excellent technology that is SQLite and how we can interact with using the API in Python. Python has something called "import" that lets you bring in files from remote places. To start on our journey of databse awesomeness we use import to bring SQLite and "sys" into our project. For those of you who don't know what sys is [here](https://docs.python.org/2/library/sys.html) is a great documentation on it. Next we connect sql to a database and assign that connection object to a variable later for ease of use as this will be our go-to method for interacting with SQLite.

{% highlight python %}
import sqlite3 as lite
import sys

con = lite.connect('test.db')
{% endhighlight %}
<br />
The way programmers traverse the many columns and rows within database tables with Python is to use a cursor. There is a built-in method called cursor() that we can use on our connection variable "con". Now all we need to do to attach that to our connection object is to call that method on it and assign that specific action to another variable, preferrably "cur".
{% highlight python %}
cur = con.cursor()
{% endhighlight %}
<br />
Now comes the fun part. To interact with our database and send queries we use "cur.execute("QUERY GOES HERE")". Being the fact that we're only doing one query here we use "cur.fetchone()". If we were getting more then one we would say fetchall(). After all is said in done we can print the data to the screen.
{% highlight python %}
cur.execute('SELECT SQLITE_VERSION()')
data = cur.fetchone()
print "SQLite version: %s" % data
{% endhighlight %}
<br />
On the regular when we do these things we have to commit and close these statements for them to save in the database but with a statement call with we can skip all of that and it does it for us. The "with" keyword also handles error checking for us if the specific table, column, or row doesn't exist. Here's that another example using "with":
{% highlight python %}
with con:
    
    cur = con.cursor()    
    cur.execute("CREATE TABLE Cars(Id INT, Name TEXT, Price INT)")
    cur.execute("INSERT INTO Cars VALUES(1,'Audi',52642)")
    cur.execute("INSERT INTO Cars VALUES(2,'Mercedes',57127)")
    cur.execute("INSERT INTO Cars VALUES(3,'Skoda',9000)")
    cur.execute("INSERT INTO Cars VALUES(4,'Volvo',29000)")
    cur.execute("INSERT INTO Cars VALUES(5,'Bentley',350000)")
    cur.execute("INSERT INTO Cars VALUES(6,'Citroen',21000)")
    cur.execute("INSERT INTO Cars VALUES(7,'Hummer',41400)")
    cur.execute("INSERT INTO Cars VALUES(8,'Volkswagen',21600)")
{% endhighlight %}
<br />
So have fun with your newfound smarts and get to querying. You've just learned a new function Young Cyborg!