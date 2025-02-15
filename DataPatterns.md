## **1. E-Commerce - Online Retail Database**
### **Users**
| user_id | name    | email            | password  | phone       | address             | created_at           |
|---------|--------|------------------|-----------|------------|---------------------|----------------------|
| 1       | Alice  | alice@email.com  | pass123   | 9876543210 | 123 Main St, NY    | 2024-02-15 10:30:00 |
| 2       | Bob    | bob@email.com    | bobpass   | 8765432109 | 456 Elm St, LA     | 2024-02-15 11:00:00 |

### **Products**
| product_id | name       | description          | price  | stock | category_id | created_at           |
|------------|-----------|----------------------|--------|-------|-------------|----------------------|
| 1          | Laptop    | High-end gaming laptop | 1200.50 | 10    | 1           | 2024-02-15 10:00:00 |
| 2          | Phone     | Latest smartphone    | 799.99  | 20    | 2           | 2024-02-15 10:15:00 |

### **Categories**
| category_id | name       |
|------------|-----------|
| 1          | Electronics |
| 2          | Mobiles     |

### **Orders**
| order_id | user_id | total_price | status  | created_at           |
|---------|--------|------------|--------|----------------------|
| 1       | 1      | 1200.50    | Pending | 2024-02-15 12:00:00 |
| 2       | 2      | 799.99     | Shipped | 2024-02-15 12:30:00 |

### **Order_Items**
| order_item_id | order_id | product_id | quantity | price  |
|--------------|---------|------------|---------|--------|
| 1           | 1       | 1          | 1       | 1200.50 |
| 2           | 2       | 2          | 1       | 799.99  |

### **Payments**
| payment_id | order_id | payment_method | amount  | status   | created_at           |
|-----------|---------|---------------|--------|---------|----------------------|
| 1         | 1       | Credit Card   | 1200.50 | Pending  | 2024-02-15 12:05:00 |
| 2         | 2       | PayPal        | 799.99  | Completed | 2024-02-15 12:35:00 |

---

## **2. Healthcare - Patient Management System**
### **Patients**
| patient_id | name  | dob        | gender | phone       | address             |
|-----------|------|-----------|--------|------------|---------------------|
| 1         | John  | 1985-05-10 | Male   | 9123456789 | 789 Maple St, TX   |
| 2         | Sarah | 1990-08-25 | Female | 9234567890 | 567 Pine St, FL    |

### **Doctors**
| doctor_id | name     | specialization | phone       | email               |
|----------|---------|--------------|------------|--------------------|
| 1        | Dr. Smith | Cardiology   | 9456123789 | drsmith@hospital.com |
| 2        | Dr. Adams | Neurology    | 9321456780 | dradams@hospital.com |

### **Appointments**
| appointment_id | patient_id | doctor_id | appointment_date     | status   |
|--------------|-----------|----------|---------------------|--------|
| 1           | 1         | 1        | 2024-02-20 09:30:00 | Scheduled |
| 2           | 2         | 2        | 2024-02-21 11:00:00 | Completed |

### **Medical_Records**
| record_id | patient_id | diagnosis    | treatment         | created_at           |
|----------|-----------|------------|----------------|----------------------|
| 1        | 1         | Hypertension | Medication       | 2024-02-20 10:00:00 |
| 2        | 2         | Migraine     | Pain Management | 2024-02-21 12:00:00 |

### **Prescriptions**
| prescription_id | patient_id | doctor_id | medicine        | dosage   | created_at           |
|---------------|-----------|----------|---------------|---------|----------------------|
| 1            | 1         | 1        | Amlodipine    | 5mg/day | 2024-02-20 10:05:00 |
| 2            | 2         | 2        | Sumatriptan   | 50mg PRN | 2024-02-21 12:10:00 |

---

## **3. Banking & Finance - Transactional and Customer Data**
### **Customers**
| customer_id | name    | email           | phone       | address         | dob        |
|------------|--------|----------------|------------|---------------|-----------|
| 1          | Tom    | tom@email.com   | 9345678912 | 123 Oak St, CA | 1980-02-12 |
| 2          | Jerry  | jerry@email.com | 9456789123 | 456 Birch St, NY | 1995-06-22 |

### **Accounts**
| account_id | customer_id | account_type  | balance  |
|-----------|------------|-------------|--------|
| 1         | 1          | Savings     | 5000.00 |
| 2         | 2          | Current     | 12000.75 |

### **Transactions**
| transaction_id | account_id | amount  | transaction_type | status   | created_at           |
|--------------|-----------|--------|----------------|--------|----------------------|
| 1           | 1         | 1000.00 | Debit          | Completed | 2024-02-15 13:00:00 |
| 2           | 2         | 2000.00 | Credit         | Completed | 2024-02-15 13:30:00 |

---

## **4. Education - Student Records and Course Management**
### **Students**
| student_id | name   | dob        | email             | phone       |
|-----------|-------|-----------|------------------|------------|
| 1         | Alex  | 2002-09-10 | alex@edu.com     | 9561234789 |
| 2         | Emma  | 2001-12-15 | emma@edu.com     | 9654123789 |

### **Courses**
| course_id | name          | credits |
|----------|-------------|--------|
| 1        | Mathematics | 3      |
| 2        | Physics     | 4      |

### **Enrollments**
| enrollment_id | student_id | course_id | grade |
|-------------|-----------|----------|------|
| 1           | 1         | 1        | A    |
| 2           | 2         | 2        | B+   |

---

## **5. Social Media - User Profiles and Interaction Data**
### **Users**
| user_id | username  | email         | password  |
|--------|----------|-------------|-----------|
| 1      | john_doe  | john@sm.com | pass123   |
| 2      | jane_doe  | jane@sm.com | pass456   |

### **Posts**
| post_id | user_id | content                 | created_at           |
|--------|--------|-----------------------|----------------------|
| 1      | 1      | Hello world!            | 2024-02-15 14:00:00 |
| 2      | 2      | Excited to be here!     | 2024-02-15 14:30:00 |

### **Likes**
| like_id | post_id | user_id |
|--------|--------|--------|
| 1      | 1      | 2      |
| 2      | 2      | 1      |

### **Comments**
| comment_id | post_id | user_id | content           |
|-----------|--------|--------|------------------|
| 1         | 1      | 2      | Nice post!        |
| 2         | 2      | 1      | Welcome aboard!   |

This sample data covers a variety of industries and helps illustrate database relationships. 🚀
