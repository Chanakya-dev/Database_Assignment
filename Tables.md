# **SQL Database Schema for Industries**

## **1. E-Commerce - Online Retail Database**
### **Tables and Fields**
#### **Users**
- `user_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)
- `password` (VARCHAR(255), NOT NULL)
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)
- `address` (TEXT, NULL)
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

#### **Products**
- `product_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `description` (TEXT, NULL)
- `price` (DECIMAL(10,2), NOT NULL, CHECK (price >= 0))
- `stock` (INT, NOT NULL, CHECK (stock >= 0))
- `category_id` (INT, FOREIGN KEY REFERENCES Categories(category_id))
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

#### **Categories**
- `category_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), UNIQUE, NOT NULL)

#### **Orders**
- `order_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `user_id` (INT, FOREIGN KEY REFERENCES Users(user_id))
- `total_price` (DECIMAL(10,2), NOT NULL)
- `status` (ENUM('Pending', 'Shipped', 'Delivered', 'Cancelled'), DEFAULT 'Pending')
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

#### **Order_Items**
- `order_item_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `order_id` (INT, FOREIGN KEY REFERENCES Orders(order_id))
- `product_id` (INT, FOREIGN KEY REFERENCES Products(product_id))
- `quantity` (INT, NOT NULL, CHECK (quantity > 0))
- `price` (DECIMAL(10,2), NOT NULL)

#### **Payments**
- `payment_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `order_id` (INT, FOREIGN KEY REFERENCES Orders(order_id))
- `payment_method` (ENUM('Credit Card', 'Debit Card', 'PayPal', 'UPI'), NOT NULL)
- `amount` (DECIMAL(10,2), NOT NULL)
- `status` (ENUM('Pending', 'Completed', 'Failed'), DEFAULT 'Pending')
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

---

## **2. Healthcare - Patient Management System**
### **Tables and Fields**
#### **Patients**
- `patient_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `dob` (DATE, NOT NULL)
- `gender` (ENUM('Male', 'Female', 'Other'), NOT NULL)
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)
- `address` (TEXT, NULL)

#### **Doctors**
- `doctor_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `specialization` (VARCHAR(255), NOT NULL)
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)

#### **Appointments**
- `appointment_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `patient_id` (INT, FOREIGN KEY REFERENCES Patients(patient_id))
- `doctor_id` (INT, FOREIGN KEY REFERENCES Doctors(doctor_id))
- `appointment_date` (DATETIME, NOT NULL)
- `status` (ENUM('Scheduled', 'Completed', 'Cancelled'), DEFAULT 'Scheduled')

#### **Medical_Records**
- `record_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `patient_id` (INT, FOREIGN KEY REFERENCES Patients(patient_id))
- `diagnosis` (TEXT, NOT NULL)
- `treatment` (TEXT, NOT NULL)
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

#### **Prescriptions**
- `prescription_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `patient_id` (INT, FOREIGN KEY REFERENCES Patients(patient_id))
- `doctor_id` (INT, FOREIGN KEY REFERENCES Doctors(doctor_id))
- `medicine` (TEXT, NOT NULL)
- `dosage` (VARCHAR(255), NOT NULL)
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

---

## **3. Banking & Finance - Transactional and Customer Data**
### **Tables and Fields**
#### **Customers**
- `customer_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)
- `address` (TEXT, NULL)
- `dob` (DATE, NOT NULL)

#### **Accounts**
- `account_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `customer_id` (INT, FOREIGN KEY REFERENCES Customers(customer_id))
- `account_type` (ENUM('Savings', 'Current', 'Fixed Deposit'), NOT NULL)
- `balance` (DECIMAL(15,2), NOT NULL, CHECK (balance >= 0))

#### **Transactions**
- `transaction_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `account_id` (INT, FOREIGN KEY REFERENCES Accounts(account_id))
- `amount` (DECIMAL(15,2), NOT NULL)
- `transaction_type` (ENUM('Credit', 'Debit'), NOT NULL)
- `status` (ENUM('Completed', 'Failed', 'Pending'), DEFAULT 'Completed')
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

---

## **4. Education - Student Records and Course Management**
### **Tables and Fields**
#### **Students**
- `student_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `dob` (DATE, NOT NULL)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)

#### **Courses**
- `course_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `name` (VARCHAR(255), NOT NULL)
- `credits` (INT, NOT NULL)

#### **Enrollments**
- `enrollment_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `student_id` (INT, FOREIGN KEY REFERENCES Students(student_id))
- `course_id` (INT, FOREIGN KEY REFERENCES Courses(course_id))
- `grade` (VARCHAR(2), NULL)

---

## **5. Social Media - User Profiles and Interaction Data**
### **Tables and Fields**
#### **Users**
- `user_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `username` (VARCHAR(255), UNIQUE, NOT NULL)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)
- `password` (VARCHAR(255), NOT NULL)

#### **Posts**
- `post_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `user_id` (INT, FOREIGN KEY REFERENCES Users(user_id))
- `content` (TEXT, NOT NULL)
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

#### **Likes**
- `like_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `post_id` (INT, FOREIGN KEY REFERENCES Posts(post_id))
- `user_id` (INT, FOREIGN KEY REFERENCES Users(user_id))

#### **Comments**
- `comment_id` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `post_id` (INT, FOREIGN KEY REFERENCES Posts(post_id))
- `user_id` (INT, FOREIGN KEY REFERENCES Users(user_id))
- `content` (TEXT, NOT NULL)

I'll continue adding tables and fields for the remaining industries.  

---

## **6. Real Estate - Property Listings and Transactions Database**  
### **Tables and Fields**  

#### **Properties**  
- `property_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `title` (VARCHAR(255), NOT NULL)  
- `description` (TEXT, NULL)  
- `price` (DECIMAL(15,2), NOT NULL, CHECK (price >= 0))  
- `location` (VARCHAR(255), NOT NULL)  
- `property_type` (ENUM('Apartment', 'House', 'Commercial', 'Land'), NOT NULL)  
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)  

#### **Agents**  
- `agent_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `email` (VARCHAR(255), UNIQUE, NOT NULL)  
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)  

#### **Transactions**  
- `transaction_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `property_id` (INT, FOREIGN KEY REFERENCES Properties(property_id))  
- `buyer_id` (INT, FOREIGN KEY REFERENCES Users(user_id))  
- `seller_id` (INT, FOREIGN KEY REFERENCES Users(user_id))  
- `agent_id` (INT, FOREIGN KEY REFERENCES Agents(agent_id))  
- `transaction_price` (DECIMAL(15,2), NOT NULL)  
- `status` (ENUM('Pending', 'Completed', 'Cancelled'), DEFAULT 'Pending')  
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)  

---

## **7. Logistics & Supply Chain - Shipment Tracking and Inventory Management**  
### **Tables and Fields**  

#### **Warehouses**  
- `warehouse_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `location` (VARCHAR(255), NOT NULL)  

#### **Products**  
- `product_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `category` (VARCHAR(255), NOT NULL)  
- `quantity` (INT, NOT NULL, CHECK (quantity >= 0))  
- `warehouse_id` (INT, FOREIGN KEY REFERENCES Warehouses(warehouse_id))  

#### **Shipments**  
- `shipment_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `product_id` (INT, FOREIGN KEY REFERENCES Products(product_id))  
- `quantity` (INT, NOT NULL, CHECK (quantity > 0))  
- `source_warehouse` (INT, FOREIGN KEY REFERENCES Warehouses(warehouse_id))  
- `destination_warehouse` (INT, FOREIGN KEY REFERENCES Warehouses(warehouse_id))  
- `status` (ENUM('Pending', 'In Transit', 'Delivered', 'Cancelled'), DEFAULT 'Pending')  
- `created_at` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)  

---

## **8. Entertainment & Streaming - Movies, Shows, and User Preferences Database**  
### **Tables and Fields**  

#### **Users**  
- `user_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `email` (VARCHAR(255), UNIQUE, NOT NULL)  
- `password` (VARCHAR(255), NOT NULL)  

#### **Movies**  
- `movie_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `title` (VARCHAR(255), NOT NULL)  
- `genre` (VARCHAR(255), NOT NULL)  
- `release_date` (DATE, NOT NULL)  
- `duration` (INT, NOT NULL, COMMENT 'Duration in minutes')  

#### **Watchlist**  
- `watchlist_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `user_id` (INT, FOREIGN KEY REFERENCES Users(user_id))  
- `movie_id` (INT, FOREIGN KEY REFERENCES Movies(movie_id))  
- `status` (ENUM('Planned', 'Watching', 'Completed'), DEFAULT 'Planned')  

---

## **9. Retail & Inventory - Product Stock and Sales Management**  
### **Tables and Fields**  

#### **Stores**  
- `store_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `location` (VARCHAR(255), NOT NULL)  

#### **Products**  
- `product_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `price` (DECIMAL(10,2), NOT NULL, CHECK (price >= 0))  
- `stock` (INT, NOT NULL, CHECK (stock >= 0))  
- `store_id` (INT, FOREIGN KEY REFERENCES Stores(store_id))  

#### **Sales**  
- `sale_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `store_id` (INT, FOREIGN KEY REFERENCES Stores(store_id))  
- `product_id` (INT, FOREIGN KEY REFERENCES Products(product_id))  
- `quantity_sold` (INT, NOT NULL, CHECK (quantity_sold > 0))  
- `sale_amount` (DECIMAL(10,2), NOT NULL)  
- `sale_date` (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)  

---

## **10. Human Resources (HRMS) - Employee Records and Payroll Management**  
### **Tables and Fields**  

#### **Employees**  
- `employee_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), NOT NULL)  
- `email` (VARCHAR(255), UNIQUE, NOT NULL)  
- `phone` (VARCHAR(15), UNIQUE, NOT NULL)  
- `department_id` (INT, FOREIGN KEY REFERENCES Departments(department_id))  
- `hire_date` (DATE, NOT NULL)  
- `salary` (DECIMAL(15,2), NOT NULL, CHECK (salary > 0))  

#### **Departments**  
- `department_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `name` (VARCHAR(255), UNIQUE, NOT NULL)  

#### **Payroll**  
- `payroll_id` (INT, PRIMARY KEY, AUTO_INCREMENT)  
- `employee_id` (INT, FOREIGN KEY REFERENCES Employees(employee_id))  
- `salary_month` (DATE, NOT NULL)  
- `amount` (DECIMAL(15,2), NOT NULL, CHECK (amount > 0))  
- `status` (ENUM('Pending', 'Processed'), DEFAULT 'Pending')  

---
