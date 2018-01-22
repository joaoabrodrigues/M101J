# Homework 2.5

Which of the choices below is the title of a movie from the year 2013 that is rated PG-13 and won no awards? Please query the video.movieDetails collection to find the answer.

NOTE: There is a dump of the video database included in the handouts for the "Creating Documents" lesson. Use that data set to answer this question.

* Journey to the West
* Saving Mr. Banks
* Escape from Planet Earth
* World War Z
* Man of Steel
* Iron Man 3
* Evil Dead
* A Tribute to J. J. Abrams
* Thor: The Dark World
* A Decade of Decadence, Pt. 2: Legacy of Dreams

Correct Answer: A Decade of Decadence, Pt. 2: Legacy of Dreams

```bash
db.movieDetails.find({ "rated": "PG-13", "year": 2013, "awards.wins": 0})
```