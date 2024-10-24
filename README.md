
**Exploratory Data Analysis (EDA)**

**Products Table:**

Checked null value distribution across columns.

Removed duplicate records to ensure data integrity.

**Users Table:**

Updated column names for better readability and consistency (ID -> USER_ID).

Converted data types for relevant columns (CREATED_DATE, BIRTH_DATE).

Handled null values by filling or filtering where necessary.

Added an AGE column calculated from the BIRTH_DATE.

Standardized GENDER column values to reduce inconsistencies.

Performed binning on the AGE column to count users in age groups.

**Transactions Table:**

Updated data types for SCAN_DATE, PURCHASE_DATE, FINAL_SALE, FINAL_QUANTITY, and BARCODE.

Checked null distribution and addressed missing values in FINAL_QUANTITY and FINAL_SALE. Missing values were filled using the average price per unit, calculated based on available quantity and sales for each product.
Ensured consistency in Final_Quantity and Final_Sale by calculating the average price per item and filling missing data accordingly. Made an assumption that if the data is appeared in receipt it has been purchased but good errored while scanning. 

**Are there any data quality issues present?**

- Standardization in User's Gender Column
  
Gender Column (Users Table)

The GENDER column in the df_user table was not standardized, leading to inconsistent representations of gender values such as 'female', 'Female', 'Non-Binary', 'non-binary', and more. During preprocessing, we standardized the values to a consistent format using the following categories:

female
male
non_binary
prefer_not_to_say
not_specified
unknown
This was done to ensure uniformity in data analysis and eliminate discrepancies caused by inconsistent entries.

- Final Quantity and Sale Issue (Transactions Table)
  
In the df_transaction table, each RECEIPT_ID is associated with at least two entries per BARCODE. Upon analysis, it was found that 50% of the records are missing either the FINAL_SALE or FINAL_QUANTITY value. For each RECEIPT_ID, 50% of the rows contain both sale and quantity data, while the other 50% either have sale without quantity or quantity without sale.

It is not entirely clear whether these multiple entries reflect the same item being ordered multiple times (due to customers scanning the same item more than once) or if they are caused by an error in data entry. This ambiguity presents a challenge in determining whether these represent distinct purchases or duplicates within the receipt.
