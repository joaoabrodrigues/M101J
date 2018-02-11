# Homework 5.1

Finding the most frequent author of comments on your blog

In this assignment you will use the aggregation framework to find the most frequent author of comments on your blog. We will be using a data set similar to ones we've used before.
Start by downloading the handout zip file for this problem. Then import into your blog database as follows:

```bash
mongoimport --drop -d blog -c posts posts.json
```

Now use the aggregation framework to calculate the author with the greatest number of comments.

To help you verify your work before submitting, the author with the fewest comments is Mariela Sherer and she commented 387 times.

Please choose your answer below for the most prolific comment author:

* Gwyneth Garling<br/>
* Milan Mcgavock<br/>
* Elizabet Kleine<br/>
* Dusti Lemmond<br/>
* Leonida Lafond<br/>
* Corliss Zuk<br/>

------

Query:
```bash
db.posts.aggregate([
 { "$project" : { "author" : "$comments.author"}}
,{ "$unwind"  : "$author"}
,{ "$group"   : { "_id"            : "$author",
      "numPosts" : { "$sum" : 1} }}
,{ "$sort" : { "numPosts" :-1}}
,{"$limit" : 1}
])
```

Answer:<br/>
* Elizabet Kleine