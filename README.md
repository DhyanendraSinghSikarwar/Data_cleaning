# Data-Cleaning

The process of data cleaning or data wrangling involves several steps to ensure that the data is accurate, consistent, and ready for analysis. Here are the summarized steps of data cleaning/wrangling with examples based cleaning done in the code:

---

### **1. Data Assessment**
   - **Manual Assessment**: 
     - Manually inspect the data to identify issues like missing values, incorrect entries, or structural problems.
     - Example: In a patient dataset, you notice that the name "David" is incorrectly entered as "D" for Patient ID 9.
   - **Programmatic Assessment**:
     - Use functions like `info()`, `describe()`, `isnull()`, and `duplicates()` to identify issues programmatically.
     - Example: Running `df.info()` reveals that 12 patients have missing data in the address, city, state, and contact columns.

---

### **2. Define Data Quality Dimensions**
   - Categorize issues into four data quality dimensions:
     1. **Completeness**: Missing data.
         - Example: Missing values in the `hba1c_change` column.
     2. **Validity**: Data that doesn’t conform to the expected format or rules.
         - Example: Zip codes should be 4 digits, but some entries are invalid.
     3. **Accuracy**: Data that is logically incorrect.
         - Example: A patient's weight is recorded as 48 pounds (21 kg), which is unrealistic.
     4. **Consistency**: Data that is represented differently across the dataset.
         - Example: State names are sometimes written in full (e.g., "California") and sometimes abbreviated (e.g., "CA").

---

### **3. Data Cleaning Order**
   - **Step 1: Quality-> Completeness**:
   - **Step 2: Tidiness**:
   - **Step 3: Quality-> Validity**:
   - **Step 4: Quality-> Accuracy**:
   - **Step 5: Quality-> Consistency**:

---

### **4. Data Cleaning Steps**
   - **Step 1: Handle Completeness Issues**:
     - Fill or remove missing values.
     - Example: For missing `hba1c_change` values, calculate them by subtracting `hba1c_start` from `hba1c_end`.
   - **Step 2: Handle Validity Issues**:
     - Correct invalid data entries (negative heights).
     - Example: Ensure all zip codes are 4 digits by removing invalid entries.
   - **Step 3: Handle Accuracy Issues**:
     - Correct logically incorrect data (valid but not accurate, ex-weight of an adult is 1kg).
     - Example: Correct the patient's name from "D" to "David" for Patient ID 9.
   - **Step 4: Handle Consistency Issues**:
     - Standardize data representation (both valid and accurate but written differently, ex-New York and NY).
     - Example: Convert all state names to either full names or abbreviations consistently.

---

### **5. Structural Issues (Messy Data)**
   - **Issue 1: Combining Multiple Variables in One Column**:
     - Example: In the `Contact` column, both phone numbers and email IDs are combined. Split them into separate columns.
   - **Issue 2: Incorrect Data Format**:
     - Example: In the `Dosage Range` column, the start and end values are combined. Split them into separate `Start` and `End` columns.
   - **Issue 3: Unnecessary Tables**:
     - Example: The `Adverse Reactions` table should not exist independently. Merge it with the main treatment table.

---

### **6. Data Transformation**
   - **Melt/Pivot Data**:
     - Reshape data to ensure each variable forms a column and each observation forms a row.
     - Example: Convert a wide-format table (e.g., columns for China, India, Pakistan) into a long-format table with a single `Country` column.
   - **Split Columns**:
     - Example: Split the `Dosage Range` column into `Start` and `End` dosage columns.

---

### **7. Data Validation**
   - After cleaning, validate the data to ensure all issues are resolved.
   - Example: Check for duplicates, missing values, and consistency in the cleaned dataset.

---

### **8. Documentation**
   - Document all steps taken during the cleaning process for reproducibility.
   - Example: Create a notebook with detailed comments on how missing values were handled, how columns were split, etc.

---

### **Example Workflow**
1. **Identify Issues**:
   - Missing values in `hba1c_change`.
   - Invalid zip codes.
   - Incorrect patient name ("D" instead of "David").
   - Combined phone and email in the `Contact` column.
2. **Clean Data**:
   - Calculate missing `hba1c_change` values.
   - Remove invalid zip codes.
   - Correct the patient's name.
   - Split the `Contact` column into `Phone` and `Email`.
3. **Validate Data**:
   - Ensure no missing values, duplicates, or inconsistencies remain.
4. **Document Steps**:
   - Record all cleaning steps in a notebook.

---

By following these steps, you can systematically clean and prepare your data for analysis, ensuring it is accurate, consistent, and reliable.
