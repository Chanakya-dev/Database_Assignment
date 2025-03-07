# **SQL Query Assignment - Categorized Questions**  

## **1. E-Commerce Database Queries**  
1. Retrieve the top 5 most expensive products. **(Data Retrieval & Sorting - ORDER BY DESC, LIMIT 5)**  
2. Find the total revenue generated from all orders. **(Aggregations - SUM)**  
3. Get the average order value per customer. **(Aggregations & Grouping - AVG, GROUP BY)**  
4. Retrieve the total number of orders placed per category. **(Aggregations & Grouping - COUNT, GROUP BY)**  
5. List all products priced between $50 and $200. **(Filtering with AND - WHERE price BETWEEN 50 AND 200)**  
6. Find all products that are either out of stock or cost more than $500. **(Filtering with OR - WHERE stock = 0 OR price > 500)**  
7. Retrieve customer names who have placed orders. **(Joins - INNER JOIN orders ON customers.customer_id = orders.customer_id)**  
8. Find the total amount spent by each customer. **(Joins & Aggregations - SUM, GROUP BY)**  
9. Get the details of orders that contain at least one product from the "Electronics" category. **(Joins & Filtering - INNER JOIN, WHERE category = 'Electronics')**  
10. Retrieve the top 3 customers who have spent the most. **(Subquery - ORDER BY total_spent DESC, LIMIT 3)**  
11. Find the names of customers who have never placed an order. **(Subquery & LEFT JOIN - WHERE order_id IS NULL)**  

---  

## **2. Healthcare Database Queries**  
1. List the top 5 oldest patients. **(Data Retrieval & Sorting - ORDER BY ASC, LIMIT 5)**  
2. Find the total number of appointments scheduled per doctor. **(Aggregations & Grouping - COUNT, GROUP BY)**  
3. Retrieve the average number of patients treated per day. **(Aggregations - AVG, GROUP BY)**  
4. Get the number of prescriptions issued per department. **(Aggregations & Grouping - COUNT, GROUP BY)**  
5. Find all patients who are older than 60 and have a chronic illness. **(Filtering with AND - WHERE age > 60 AND condition = 'Chronic')**  
6. Retrieve all doctors who specialize in either cardiology or neurology. **(Filtering with OR - WHERE specialty = 'Cardiology' OR specialty = 'Neurology')**  
7. Retrieve the doctor’s name along with the number of patients they have treated. **(Joins & Aggregations - COUNT, GROUP BY)**  
8. Find the names of doctors who have never scheduled an appointment. **(Joins & Subqueries - LEFT JOIN, WHERE appointment_id IS NULL)**  
9. List patients who have been prescribed medication but haven't scheduled a follow-up appointment. **(Subqueries & Joins - WHERE NOT EXISTS (SELECT * FROM appointments WHERE patient_id = prescriptions.patient_id))**  
10. Find the department with the highest number of appointments. **(Subquery & GROUP BY - WHERE appointment_count = (SELECT MAX(appointment_count) FROM appointments))**  

---  

## **3. Banking & Finance Database Queries**  
1. Retrieve the last 10 high-value transactions. **(Data Retrieval & Sorting - ORDER BY DESC, LIMIT 10)**  
2. Calculate the total deposits made in the last month. **(Aggregations - SUM, WHERE date >= LAST_MONTH_START)**  
3. Find the average balance of all accounts per branch. **(Aggregations & Grouping - AVG, GROUP BY)**  
4. Count the number of transactions per customer. **(Aggregations & Grouping - COUNT, GROUP BY)**  
5. Retrieve all transactions where the amount is greater than $10,000 but not made via credit card. **(Filtering with AND - WHERE amount > 10000 AND payment_method != 'Credit Card')**  
6. List all customers who have either a savings account or a fixed deposit. **(Filtering with OR - WHERE account_type = 'Savings' OR account_type = 'Fixed Deposit')**  
7. Retrieve customer names along with their total balance. **(Joins & Aggregations - SUM, GROUP BY)**  
8. Get a list of accounts that have never made a transaction. **(Joins & Subqueries - LEFT JOIN, WHERE transaction_id IS NULL)**  
9. Find the customer with the highest total balance. **(Subquery - WHERE total_balance = (SELECT MAX(total_balance) FROM accounts))**  
10. Retrieve the list of customers who have made more than 10 transactions in the past year. **(Subquery & Aggregations - COUNT, GROUP BY, HAVING COUNT(transaction_id) > 10)**  

---  

## **4. Education Database Queries**  
1. Retrieve the names of the top 5 highest-scoring students. **(Data Retrieval & Sorting - ORDER BY DESC, LIMIT 5)**  
2. Find the total number of students enrolled in each course. **(Aggregations & Grouping - COUNT, GROUP BY)**  
3. Get the average GPA of students in each department. **(Aggregations & Grouping - AVG, GROUP BY)**  
4. Count the total number of courses taught by each professor. **(Aggregations & Grouping - COUNT, GROUP BY)**  
5. List all students with a GPA higher than 3.5 and enrolled in more than 3 courses. **(Filtering with AND - WHERE GPA > 3.5 AND enrolled_courses > 3)**  
6. Retrieve all courses that are either elective or have more than 50 students enrolled. **(Filtering with OR - WHERE course_type = 'Elective' OR student_count > 50)**  
7. Retrieve students along with the courses they are enrolled in. **(Joins - INNER JOIN students_courses ON students.id = students_courses.student_id)**  
8. Find students who have never enrolled in a course. **(Joins & Subqueries - LEFT JOIN, WHERE course_id IS NULL)**  
9. Get the professor who teaches the most courses. **(Subquery - WHERE course_count = (SELECT MAX(course_count) FROM courses))**  
10. List students who have enrolled in all available courses. **(Subquery - WHERE enrolled_course_count = (SELECT COUNT(*) FROM courses))**  

---  

## **5. Social Media Database Queries**  
1. Retrieve the 10 most popular posts based on the number of likes. **(Data Retrieval & Sorting - ORDER BY DESC, LIMIT 10)**  
2. Find the total number of likes received per user. **(Aggregations & Grouping - COUNT, GROUP BY)**  
3. Get the average number of posts made per user. **(Aggregations - AVG, GROUP BY)**  
4. Count the total number of comments per post. **(Aggregations & Grouping - COUNT, GROUP BY)**  
5. Find all users who have more than 1,000 followers and have posted at least 10 times. **(Filtering with AND - WHERE followers > 1000 AND post_count >= 10)**  
6. Retrieve all posts that either have no comments or less than 5 likes. **(Filtering with OR - WHERE comment_count = 0 OR likes < 5)**  
7. Retrieve usernames along with the number of posts they have made. **(Joins & Aggregations - COUNT, GROUP BY)**  
8. Find users who have never made a post. **(Joins & Subqueries - LEFT JOIN, WHERE post_id IS NULL)**  
9. List the users who have received the most likes overall. **(Subquery - WHERE total_likes = (SELECT MAX(total_likes) FROM users))**  
10. Find users who follow at least 50 other users and have at least 500 followers. **(Subquery & Aggregations - WHERE following_count >= 50 AND follower_count >= 500)**  

---
