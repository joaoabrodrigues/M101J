# Homework $substr

Prefered Cities to Live!

In this problem you will calculate the number of people who live in a zip code in the US where the city starts with one of the following characthers:

• B, D, O, G, N or M .

We will take these are the prefered cities to live in (chosen by this instructor, given is special affection to this set of characters!).

You will be using the zip code collection data set, which you will find in the 'handouts' link in this page.

Import it into your mongod using the following command from the command line:

```bash
mongoimport --drop -d test -c zips zips.json
```

If you imported it correctly, you can go to the test database in the mongo shell and confirm that

```bash
> db.zips.count()
```

yields 29353 documents.

The $project stage can extract the first character from any field. For example, to extract the first character from the city field, you could write this pipeline:

```bash
db.zips.aggregate([
    {$project:
     {
    first_char: {$substr : ["$city",0,1]},
     }
   }
])
```

Using the aggregation framework, calculate the sum total of people who are living in a zip code where the city starts with one of those possible first characters. Choose the answer below.

You will need to probably change your projection to send more info through than just that first character. Also, you will need a filtering step to get rid of all documents where the city does not start with the select set of initial characters.

• 76394871<br/>
• 9134188<br/>
• 9430890<br/>
• 19499064<br/>
• 11623385<br/>
• 20043717<br/>
• 3326663627<br/>

Query:
```bash
db.zips.aggregate([ { $project: { first_char: { $substr : ["$city",0,1]}, "pop": "$pop" } }, {$match: {"first_char": { $in:['B','D','O','G','N','M']}}}, { $group: {"_id" : null, sum: {$sum:"$pop"}} } ])
```

Answer:<br/>
• 76394871