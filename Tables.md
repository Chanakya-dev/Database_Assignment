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
- `appointment_date` (DATETIME NOT NULL)
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
---

