# Homework 6.3

Which of the following statements are true about choosing and using a shard key?

* The shard key must be unique
* There must be a index on the collection that starts with the shard key.
* MongoDB can not enforce unique indexes on a sharded collection other than the shard key itself, or indexes prefixed by the shard key.
* Any single update that does not contain the shard key or _id field will result in an error.
* You can change the shard key on a collection if you desire.

------

Answer:<br/>
* There must be a index on the collection that starts with the shard key.
* MongoDB can not enforce unique indexes on a sharded collection other than the shard key itself, or indexes prefixed by the shard key.
* Any single update that does not contain the shard key or _id field will result in an error.