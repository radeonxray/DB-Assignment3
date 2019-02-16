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
