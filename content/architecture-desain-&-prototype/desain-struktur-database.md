
+ _table Auth_
    - user_id
    - username
    - password
    - created_at

+ _table Product_
    - product_id
    - name
    - category
    - merk
    - purchase price
    - selling price
    - stock

+ _table supplier_
    - name
    - address
    - phone_number

+ _table transaction_
    - transaction_id
    - customer_id (Foreign Key): ID pelanggan terkait dengan transaksi (jika ada).
    - transaction_date
    - total_amount
    - payment_status

+ _table detail_transaction_
    - transaction_detail_id
    - transaction_id
    - product_id
    - quantity
    - unit_price

+ _table customers_
    - customer_id
    - name
    - email
    - phone_number