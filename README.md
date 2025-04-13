# 🥗 DoormaT Farm — Ready-to-Eat Meal Kit Delivery System

> **🏆 Awarded Best Project & Best Use of Database – CSE 5330 (Spring 2023)**  
> A database-driven solution for optimizing delivery logistics, subscription plans, and meal diversity in the ready-to-eat food industry.

---

## 📌 **Overview**

**DoormaT Farm** is a database management system designed to streamline operations for a homemade meal kit delivery service. Our platform focuses on solving key challenges such as meal customization, delivery route optimization, and subscription flexibility—tailored for busy professionals and students.

This project was highly appreciated by faculty and peers alike, earning the **"Best Project"** title for its comprehensive approach and **"Best Use of Database"** for its advanced schema design, efficient queries, and real-world application.

---

## 👩‍💻 **Team Members**

- Manjeet Acharya  
- Sai Santoshi Praneetha  
- Harshada Thombre  
- Meghana Mendu

---

## 💡 **Problem Statement**

With a growing demand for healthier, ready-to-eat options, many individuals lack time to cook or trust store-bought processed foods. While fast delivery services exist, they often lack personalization and effective logistics. Our system aims to:

- Provide customizable meal kit plans  
- Identify optimal warehouse locations  
- Analyze customer orders and delivery patterns  
- Recommend efficient subscription options based on real data

---

## 🧩 **Features**

- **Healthy Home-made Meal Kits**  
- **Cuisine-Based Demand Analysis**  
- **Top-performing Delivery Drivers**  
- **Optimized Warehouse Location Suggestions**  
- **Customer-centric Subscription Plans**

---

## 🗃️ **Database Schema**

The system consists of 20+ relational tables covering:

- Vendors, Warehouses, Delivery Workers  
- Customer Profiles, Orders, Subscriptions  
- Meal Kits, Cuisine Types, Delivery Times

**Key Tables Include:**

- `Spring23_S003_12_Mealkit`  
- `Spring23_S003_12_Customer2`  
- `Spring23_S003_12_orders1`  
- `Spring23_S003_12_Subscription_mealkit`  

---

## 🧠 **Key Insights (SQL Examples)**

```sql
-- 1. Top-Selling Meal Kit Cuisines
SELECT m.cusine_type, COUNT(m.mealkit_id) AS Total_Mealkits_Sold
FROM Spring23_S003_12_Mealkit m
JOIN Spring23_S003_12_Subscription_mealkit o2 ON m.mealkit_id = o2.mealkit_id
GROUP BY m.cusine_type
ORDER BY COUNT(m.mealkit_id) DESC;

-- 2. Ideal Warehouse Locations
SELECT c2.Address, COUNT(o1.customer_id) AS Number_Of_Orders
FROM Spring23_S003_12_Customer2 c2
JOIN Spring23_S003_12_orders1 o1 ON c2.customer_id = o1.customer_id
GROUP BY c2.Address
ORDER BY Number_Of_Orders DESC
FETCH FIRST 5 ROWS ONLY;

-- 3. Delivery Driver Performance (Average Delivery Time vs. Distance)
SELECT wd.warehouse_id, dw.worker_ssn,
AVG(CAST(((TO_DATE(Order_DeliverTS, 'YYYY-MM-DD HH24:MI:SS') - TO_DATE(Order_PickupTS, 'YYYY-MM-DD HH24:MI:SS'))*24*60) AS DECIMAL(10,2))) AS Average_Delivery_Time,
AVG(Distance_Covered_per_order) as Mean_Distance
FROM Spring23_S003_12_warehouse_deliveryVehicle wd
JOIN Spring23_S003_12_delivery_worker1 dw ON wd.warehouse_id = dw.warehouse_id
JOIN Spring23_S003_12_Delivery_Order o ON o.Worker_SSN = dw.worker_ssn
GROUP BY wd.warehouse_id, dw.worker_ssn, Distance_Covered_per_order
ORDER BY Average_Delivery_Time ASC
FETCH FIRST 5 ROWS ONLY;

### **🎯 Project Goals**
- Enhance data-driven decision-making for logistics  
- Improve customer satisfaction through optimized plans  
- Use SQL queries to deliver business value through insights  

---

### **🧪 Technologies Used**
- **SQL**  
- **Oracle DB**  
- **EER Diagram Design**  
- **Microsoft Teams** (for collaboration)  

---

### **📚 Lessons Learned**
- Real-world database design involves more than just schema—it’s about aligning data with business goals  
- Importance of data-driven decisions in logistics and customer service  
- Effective teamwork and clear task delegation were key to our success  

---

### **🙌 Acknowledgements**
- Special thanks to **CSE 5330 Faculty** for continuous support and feedback  
- This project strengthened our database fundamentals and was recognized for its **technical depth** and **business relevance**

