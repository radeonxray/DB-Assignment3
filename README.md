# DB-Assignment3

Assignment Description: https://github.com/datsoftlyngby/soft2019spring-databases/blob/master/assignments/assignment3.md

Lecture Slides: https://github.com/datsoftlyngby/soft2019spring-databases/blob/master/lecture_notes/03-MongoDB_Modelling.ipynb

## 1. Twitter data 

The repo and assignment for the Twitter data can be found here: [DB-Assignment2](https://github.com/radeonxray/DB-Assignment2)

### Results

With the `DB-Assignment2`-project running, you can see the results by using a browser (*Chrome, Firefox, Internet Explore etc.*) or tools such as [*Postman*](https://www.getpostman.com).

The answers to the questions posed in the assignment can be found using the given api-path

**[Please note that the given Paths are given using the default values for the IP, PORT, Database and Collections]**.

- How many Twitter users are in the database?
  - Path: http://localhost:3001/usercount
  - Result: 659774 (out of 1600000 documents)
  
- Which Twitter users link the most to other Twitter users? (Provide the top ten.)
  - Path: http://localhost:3001/mostlinks
  - Results:
    - lost_dog 
      - Mentions : 549
    - tweetpet
      - Mentions : 310
    - VioletsCRUK
      - Mentions : 251
    - what_bugs_u
      - Mentions : 246
    - tsarnick
      - Mentions : 245
    - SallytheShizzle
      - Mentions : 229
    - mcraddictal
      - Mentions : 217
    - Karen230683
      - Mentions : 216
    - keza34
      - Mentions : 211
    - TraceyHewins
      - Mentions : 202
  
- Who is are the most mentioned Twitter users? (Provide the top five.) 
  - Path:http://localhost:3001/mostmentioned
      - @mileycyrus
        - Mentions: 4310
      - @tommcfly
        - Mentions: 3837
      - @ddlovato
        - 3349
      - @Jonasbrothers
        - 1263
      - @DavidArchie
        - 1222
  
- Who are the most active Twitter users (top ten)?
  - Path: http://localhost:3001/mostactive
  - Results: 
    - lost_dog 
      - Count : 549
    - weboke
      - Count : 345
    - tweetpet
      - Count : 310
    - SallytheShizzle
      - Count : 281
    - VioletsCRUK
      - Count : 279
    - mcraddictal
      - Count : 276
    - tsarnick
      - Count : 248
    - what_bugs_u
      - Count : 246
    - Karen230683
      - Count : 238
    - DarkPiano
      - Count : 236
      
- Who are the five most grumpy (most negative tweets) and the most happy (most positive tweets)? (Provide five users for each group) 
  - Path: 
    - Most Positive: http://localhost:3001/positivepolarity
      - what_bugs_u
        - Count : 246
      - KevinEdwardsJr
        - Count : 171
      - whitsundays
        - Count : 144
      - longestpoem
        - Count : 116
      - tweeteradder7
        - Count : 114
        
    - Most Negative: http://localhost:3001/negativepolarity
      - lost_dog
        - Count : 549
      - tweetpet
        - Count : 310
      - TheAmazingCat
        - Count : 86
      - nova937music
        - Count : 67
      - Nathan133
        - Count : 51
        
----
## 2. Modeling

|  Solutions |  Atomicity | Sharding  |  Indexes | Large Number of Collections  |  Collection Contains Large Number of Small Documents |
|---|---|---|---|---|---|
| Arrays of Ancestors  |X|   | X  | X  |   |
|  Materialized paths |   |  X |   | X  |  X |
|  Nested sets |  X | X  | X  |   |   |

### The Model Trees
- What is *Array of Ancestors*?
  - The Array of Ancestors pattern stores each tree node in a document; in addition to the tree node, document stores in an array the id(s) of the node’s ancestors or path.
  - The Array of Ancestors pattern provides a fast and efficient solution to find the descendants and the ancestors of a node by creating an index on the elements of the ancestors field. This makes Array of Ancestors a good choice for working with subtrees.
  - The Array of Ancestors pattern is slightly slower than the Materialized Paths pattern but is more straightforward to use
  
- What is *Materialized paths*?
  - The Materialized Paths pattern stores each tree node in a document; in addition to the tree node, document stores as a string the id(s) of the node’s ancestors or path. Although the Materialized Paths pattern requires additional steps of working with strings and regular expressions, the pattern also provides more flexibility in working with the path, such as finding nodes by partial paths.

- What is *Nested sets*?
  - The Nested Sets pattern identifies each node in the tree as stops in a round-trip traversal of the tree. The application visits each node in the tree twice; first during the initial trip, and second during the return trip. The Nested Sets pattern stores each tree node in a document; in addition to the tree node, document stores the id of node’s parent, the node’s initial stop in the left field, and its return stop in the right field.
  - The Nested Sets pattern provides a fast and efficient solution for finding subtrees but is inefficient for modifying the tree structure. As such, this pattern is best for static trees that do not change.
  
### So how does the five given factors of *Atomicity*, *Sharding*, *Indexes*, *Large Number of Collections* and *Collection Contains Large Number of Small Documents* work in conjunction with each of the Models Tree's?

**Note: I've only focused on the ones marked in the given table**
  
- **Arrays of Ancestors (AOA)**
  - Atomicity
    - Works well with AoA since the action/operation is atomic, so that if you try to inserting into the collection, only the single document is changed (or created).  
  - Indexes
    - Can be very useful with AOA, since the parents can be indexed on a specific document.
  - Large Number of Collections
    - The collection can grow incredible large, since each document has to refer to all the ancestors.
- **Materialized Paths (MP)**
  - Sharding
    - Sharding can become incredibly useful in MP, since you can get the partial path to a document
  - Large Number of Collections
    - For MP, the path is still stored in each document, so Large Number of Collections makes great sense. 
  - Collection Contains Larger Number of Small Documents
    - Rather than having one big document, because the documents are split up, you’ll end up having many smaller documents in MP.
- **Nested Sets (NS)**
  - Atomicity
    - Works well with NS since the action/operation is atomic, so that if you try to inserting into the collection, only the single document is changed (or created).
  - Sharding
    - NS benefits greatly from Sharding, since the different categories can be sharded
  - Indexes
    - Indexes can be added to the different categories
