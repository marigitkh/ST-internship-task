This solution defines a CustomerDataExtractor class to transform a nested .pkl dataset of customer orders into a clean, flat pandas DataFrame.

## Key Processing Steps

- VIP Detection: Loads VIP customer IDs from a text file and flags matching customers.

- Date Parsing: Safely converts date strings to pandas datetime objects with fallback to NaT.

- Order ID Normalization: Cleans order_id values by removing "ORD" prefixes and setting invalid or missing values to -1.

- Category Mapping: Maps category codes (1–4) to labels; unmatched categories default to "Misc".

- Price and Quantity Handling:
  - Strips symbols like $ from prices and converts to float.
  - Treats "FREE" quantity as 0.
  - Skips items with invalid price or quantity.

- Missing Data: Records with missing product info or 0 quantity are skipped. Fields like order_id or product_id are imputed with -1 or "Unknown" when needed.

- Data Cleaning: Final DataFrame is explicitly typed, sorted by customer_id, order_id, and product_id.
