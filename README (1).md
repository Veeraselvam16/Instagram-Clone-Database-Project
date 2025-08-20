## 🗂️ Verify Tables  

```sql
SHOW TABLES;
```

---

## 🔍 Example Queries  

```sql
-- 1. Find the 5 oldest users
SELECT USERNAME 
FROM USERS
ORDER BY CREATED_AT ASC
LIMIT 5;

-- 2. Identify inactive users (never posted a photo)
SELECT USERNAME 
FROM USERS 
WHERE ID NOT IN (SELECT USER_ID FROM PHOTOS);

-- 3. Who got the most likes on a photo?
SELECT USERS.USERNAME, COUNT(*) AS TOTAL_LIKES
FROM LIKES
JOIN PHOTOS ON LIKES.PHOTO_ID = PHOTOS.ID
JOIN USERS ON PHOTOS.USER_ID = USERS.ID
GROUP BY USERS.USERNAME
ORDER BY TOTAL_LIKES DESC
LIMIT 1;

-- 4. Average number of posts per user
SELECT AVG(PHOTO_COUNT) AS AVG_POSTS
FROM (
  SELECT USER_ID, COUNT(*) AS PHOTO_COUNT 
  FROM PHOTOS 
  GROUP BY USER_ID
) AS POST_COUNT;

-- 5. Top 5 most used hashtags
SELECT TAGS.TAG_NAME, COUNT(*) AS TAG_COUNT
FROM PHOTO_TAGS
JOIN TAGS ON PHOTO_TAGS.TAG_ID = TAGS.ID
GROUP BY TAGS.TAG_NAME
ORDER BY TAG_COUNT DESC
LIMIT 5;
```

---

## 📈 Project Highlights  

- ✅ Simulates an Instagram-like relational database  
- ✅ Includes dataset with **100+ users** and interactions  
- ✅ Demonstrates **realistic SQL queries** for analytics  
- ✅ Showcases **data modeling** with ER diagrams  
- ✅ Useful for learning **MySQL joins, subqueries, and views**  
