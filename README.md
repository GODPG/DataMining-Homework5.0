# Recommender System Analysis - MovieLens 100k Dataset

## Introduction

In the era of information overload, recommender systems are essential for filtering vast amounts of data and offering personalized suggestions to users. This report explores two fundamental approaches in building recommender systems: Collaborative Filtering and Content-Based Filtering. Using the widely-acknowledged **MovieLens 100k dataset**, this report implements and evaluates the two techniques through the following problems:

1. **Problem 1:** Identification of the 10 most similar users to User 1 based on cosine similarity, followed by prediction of User 1's rating for Item 508.
2. **Problem 2:** Construction of user profiles based on centered data, calculation of cosine similarity, and determining which user would be recommended Movie 95.

## Dataset Description

The **MovieLens 100k dataset** is widely used for benchmarking recommender systems. It contains:

- **100,000 ratings** (ranging from 1 to 5)  
- **943 users** and **1682 movies**  
- Data collected by the **GroupLens Research Group** between September 1997 and April 1998  

### Files
- **u.data:** Contains core ratings information (`user_id`, `item_id`, `rating`, `timestamp`).  
- **u.item:** Contains movie-related data, including 19 binary genre columns.

## Problem 1: Collaborative Filtering - Cosine Similarity

### Objective
- Load the MovieLens 100k data.  
- Represent ratings in a user-item utility matrix.  
- Find the 10 most similar users to User 1 using cosine similarity on centered ratings.  
- Predict User 1’s rating for Item 508.

### Methodology
1. **Data Loading:** Load `u.data` into a Pandas DataFrame.  
2. **Utility Matrix:** Pivot to create user–item matrix.  
3. **Center Ratings:** Subtract each user's mean from their ratings.  
4. **Compute Similarity:** Use cosine similarity on centered vectors.  
5. **Find Neighbors:** Select top 10 users similar to User 1.  
6. **Predict Rating:** Average the neighbors' ratings for Item 508.

### Result
- **Predicted rating for User 1 on Item 508:** 4.200

## Problem 2: Content-Based Filtering - User Profiles

### Objective
- Build user profiles from centered ratings and movie genres.  
- Compute cosine similarity between user profiles and Movie 95’s genre vector.  
- Determine which user (200 or 15) is more likely to enjoy Movie 95.

### Methodology
1. **Data Loading:** Load `u.data` and `u.item`.  
2. **Center Ratings:** Normalize each user’s ratings.  
3. **Item Features:** Represent movies by 19-dimensional genre vectors.  
4. **User Profiles:** Weighted sum of genre vectors by centered ratings.  
5. **Similarity:** Cosine similarity between user profile and Movie 95’s genre vector.

### Result
- **User 200 vs Movie 95:** Cosine similarity = -0.2652  
- **User 15 vs Movie 95:** Cosine similarity = -0.3259  
- **Recommendation:** Movie 95 would be recommended to User 200.

## Conclusion

- **Problem 1:** User 1’s rating for Item 508 predicted as **4.200** via collaborative filtering.  
- **Problem 2:** Content-based filtering indicates **User 200** is the better match for Movie 95.
