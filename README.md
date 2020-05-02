# Booksters

The website is thought as a comunity of books fans where info and opinions on books can be shared.

## Tutorial

The user can see informations about books, create new book entries, delete or update existing ones (CRUD).
In the homepage the guest can search for a book or choose to consult one from the list.
The user can also choose in the list by genre or author.

In the book page the guest will find the basic info about the book and will be able to do the following:
1. update the book info
2. delete the book
3. rate the book based on a star rating system (min 1 - max 5)
4. leave a review
5. go to the store to buy it (this functionality has not been developed)

The user can create a book.
The user will be able to choose an existing genre / author or add a new one

In the STATS page the use can see the following:
1. top 10 rated books
2. the most voted book
3. the book that has been rated the highest of the current date
4. interactive chart of rating by author
5. interactive chart of rating by genre


## UX design

User is invited to give his/her contribution whenever a request does find any result in the database.
This is done through flash messages on the screen with link when user can add new entries.

The aim is to create a big database of books but not big collection of genres/authors not connected to any book.
For this reason the option to add genre / author is only available during the submission of a new book.

All books are editable and deletable. This is based on an idea of comunity where components trust each other.

## problems

# entry repetition

I had to consider the possiblity that the user could try to add an entry already existing (book , genre , author).
For this reason in the corresponing functions I added some code to avoid this from happening.
Guest instead is redirected to the previous page and informed that the entry already exists 

# entry identification 
Intially my functions were fed with arguments like book title and author. Crossing those info I could identify the document in the database.
I, later, decided to use a more efficient approach and used id instead

# cursor issue

When I had to manipulate results from a database search, I had issue handling cursors.
In many cases I resolved the problem oof not being able to loop through a cursor changing it to a list

# review score

From the beginning I decided that I wanted the ratings to be store in a list . 
This would allow further manipulation of data in the Stat page.
This decision forced me to add an extra function that add to calculate the mean rating based on the elements of the list
The numeric rating was very precise and useful for stats but I also wanted a more user friendly rapresentation.
I then decided to keep the original numeric rating and add an extra function to create a star based rating sistem from 1 to 5.
Eventually I decided that ahving the timestamp associated to a rating would give many more possibilities to work with the data.
I, then, decided to store rating data in the form of an array of 2-elements-arrays (rating and autogenerated timestamp)

# stat page: use of charts

For the stats page I have considered different approaches. 
Insitially I was considering usign only charts rendered with DC and CROSSFILTER.
I then decided that it was was not really a good choiche for a project about books. 
I finally decided to use charts in a more discrete way.

Only a couple of charts where used. The user can interact woth the chart through JS

# stat page: Comunication between JS and Python

In the Stats page I had to put front end (JS) and back end (Python) in comunication in order to send user choice and check in the DB what was the highest rated book.
Initially I have tried to just call my flask method again from the front end. This was definetely not a good idea and I finally undestood I had to make Ajax requests instead.
I solved the issue using Fetch API that allowed me to keep client and server side in comunication. In order to transfer the data I had to use JSON format and serialize/ parse methods in both languages.
In order to deal with errors (author with no books) I have added a catch() function .

# helper functions
As my code was growing, I had noticed a lot of code was getting repeated in my app.py . 
In order to achieve a DRY code, I have decided to make us of few helper functions

For the stats page I have considered different approaches. Insitially I was usign Js only . Then I ahve used dc with corssfilter in order to render everything with charts.
I then decided that it was was not really a good choiche for a project about books. I fanlly decided for a mixed approach with only limited use of charts

## Unit Testing

# Mongo DB interaction : GET functions

Being the app based on a database, it is crucial that the app responds to data modification in the expected way.

For GET functions I was able to achieve this simply using test DB entries and a test client pointed to the correct url.

# Mongo DB interaction : POST functions (checking DB)

Testing POST function where the user was actually amending the content of the DB was more complex.

In this case I had to feed a test client with the content of the data posted .

After that, I could verify if the DB content was correct by a simple search.

# Mongo DB interaction : POST functions (checking response)

In some cases I did not only wanted to check that the DB was correctly amended but also that the guest was informed correctly on screen.

This was achieved feeding a test client with the content of the data posted and, after, reviewing the response data.

The following problem was that data response was just showing a redirection message. 

This would not allow me to check what guest could seen on screen.

The problem was solved by setting the parameter "follow_redirects" to True.


### Purpose



### Features/Technologies
bootstrap 4 
Mongo DB (Atlas)
local variables file(.gitignore)
js 

Fetch API and Json format :  

## Testing

unit testing

## Deployment

Heroku



## Acknowledgments and contributions

1.Code Institute full Gitpod template

2.Pictures used are taken from stocksnap.io (Creative Commons CC0) 

3.Bootstrap theme Clean Blog

