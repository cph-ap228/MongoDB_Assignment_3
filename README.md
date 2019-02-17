# MongoDB_Assignment_3

## Twitter_Database_Queries

### 1. How many Twitter users are in the database?
![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Question1.png)

### 2. Which Twitter users link the most to other Twitter users? (Provide the top ten.)
![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Question2.png)

### 3. Who are the most mentioned Twitter users? (Provide the top five.)
![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Question3.png)

### 4. Who are the most active Twitter users (top ten)?
![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Question4.png)

### 5.0-5.1 Who are the five most grumpy (most negative tweets) and the most happy (most positive tweets)?
![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Question5-5.1.png)

## MongoDB_Modelling

![picture](https://github.com/cph-ap228/MongoDB_Assignment_3/blob/master/Queries/Model.png)

### Arrays of Ancestors 
* Atomicity 
  * The write operations are considered antomic since we're only carrying out operations on a single document. 
ie. The Twitter .csv file 

* Indexes 
  * In this particular case MongoDB is already creating a unique index field by default "_id",  
  which we're using in this assignment, which is a great approach that utilizes the Array of Ancestors pattern. 

* Large Number of Collections 
 * Since we're only making use of one document, there's only really need for one collection that is grouped,
 this makes working on subtrees via. the collection a much easier approach for the tast given, ie. "tweets" - collection. 
 This would make for an optimal approach if the task was using multiple documents. 


### Materialized Paths 
* Sharding 
  * Sharding for this task would not have been necessary since we're not dealing with an humongous amount of data, though 
  it can be stressing for older hardware/servers etc. This can be used as a last measure, if everything else fails. 
  Taking example from my own queries that I've answered the assignments questions with, I've made use of Pipelines. 
  This was used to transform and receive a final estimator, to by-pass the MongoDB's own byte restrictions of larger queries.

* Large Number of Collections 
  *  Reducing the number of documents could improve the performance of the DB and keep the overall document size smaller. 

* Collection Contains Large Number of Small Documents
  * In this particular case, we have a document with a relatively small path to the data we need, resulting them being group up, 
  and fairly easy to access. 
  
### Nested Sets 
* Atomicity 
  * Writing is atomic cause the data is inserted into a single document, and the relations are already specified. 
  Which results in obsolence in insert/updating other objects. 
  
* Sharding 
  * Since this Data Structure Pattern is good at modyfying the tree structure, it might benefit from sharding. 
    However this might also have the opposite effect, introducing more complexity and possibly failure. 
    
* Indexes 
  * Indexes doesn't help that much in this case, since you're only able to index the following: parent, left and right element of the document. 
