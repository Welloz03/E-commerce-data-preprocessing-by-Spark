# 🛒 **Demand Forecasting Data Preparation**

## 🚀 **Project Overview**
As data engineers at **Voltmart**, an electronics e-commerce company, we are responsible for preparing last year's order data for a demand forecasting project. Accurate data preparation is critical to enable the Machine Learning team to build a reliable forecasting model. This project uses **PySpark** for efficient and scalable data cleaning and preprocessing.

The dataset, stored in a Parquet file (`orders_data.parquet`), contains customer order information with attributes like order dates, products, purchase addresses, and financial metrics. The cleaning and transformation steps aim to ensure data quality and meet the requirements outlined by business analysts.

---

## 📂 **Dataset Details**

| **Column**          | **Data Type**  | **Description**                                     | **Cleaning Requirements**                              |
|----------------------|----------------|-----------------------------------------------------|-------------------------------------------------------|
| `order_date`         | `timestamp`    | Date and time when the order was made               | Remove orders placed between 12am-5am; convert to `date`. |
| `time_of_day`        | `string`       | Period of the day when the order was made           | Add new column: "morning" (5-12am), "afternoon" (12-6pm), "evening" (6-12pm). |
| `order_id`           | `long`         | Unique order ID                                     | _N/A_                                                 |
| `product`            | `string`       | Name of the product ordered                        | Remove rows with "TV"; ensure lowercase.              |
| `category`           | `string`       | Product category                                    | Ensure lowercase.                                     |
| `purchase_address`   | `string`       | Address of the purchase                             | _N/A_                                                 |
| `purchase_state`     | `string`       | State abbreviation from the purchase address       | Extract and add as a new column.                     |
| Other columns        | Various types  | Financial and quantity details                     | _No cleaning required._                              |

---

## 🛠️ **Technologies Used**
- **PySpark**: For distributed data processing.
- **Parquet**: For efficient data storage and retrieval.
- **Jupyter Notebook**: For developing and showcasing the workflow.

---

## 🧹 **Data Cleaning and Preprocessing Steps**

### 1. **Session Setup and Dataset Loading**
- Created a Spark session using `pyspark`.
- Loaded the dataset from the `orders_data.parquet` file and reviewed the schema and initial rows.

### 2. **Transformations**
- **`order_date` Cleanup**:
  - Converted the timestamp to a date format.
  - Filtered out orders placed between 12am-5am as they are considered invalid for forecasting.
- **`time_of_day` Column**:
  - Added a new column categorizing orders into "morning", "afternoon", or "evening" based on the `order_date` timestamp.
- **`product` and `category` Cleanup**:
  - Ensured all product names and categories are lowercase.
  - Removed rows where the product is "TV" (discontinued).
- **`purchase_state` Extraction**:
  - Extracted the U.S. state abbreviation from the `purchase_address` and created a new column `purchase_state`.

### 3. **Validation and Summary**
- Verified the distinct number of states (`purchase_state`) in the dataset.
- Ensured that all required transformations were applied successfully.

### 4. **Output**
- Saved the cleaned dataset as `orders_data_clean.parquet` in Parquet format with overwrite mode.

---

## 📈 **Project Highlights**
- **Efficient Data Handling**: Used PySpark for distributed processing of a large dataset.
- **Transformations Aligned with Business Needs**: Focused on ensuring data quality and usability for demand forecasting.
- **Scalable Workflow**: Designed the pipeline to handle growing data sizes with ease.

---

## 🎯 **Purpose**
This data preparation project ensures a high-quality dataset that can serve as the foundation for building an accurate and robust demand forecasting model. It aligns with Voltmart's goal of enhancing operational efficiency through data-driven insights.
