### 1. Proyek Restful API Point of Sale

#### 1.1 Persiapan Awal

- 1.1.1 Identifikasi Kebutuhan Bisnis
- 1.1.2 Analisis Persyaratan API
- 1.1.3 Persiapan Lingkungan Pengembangan

#### 1.2 Desain API

+ 1.2.1 Identifikasi Endpoint Utama
    - _auth_ = login, register (admin, cashier) kasir hanya bisa membuat transaksi baru, yang bisa membuat role cashier adalah role admin 
    - _product_ = menambahkan produk baru, memperbarui informasi produk termasuk menambahkan stock product, atau menghapus produk.
    - _transactions_ =  membuat transaksi baru, history penjualan, pembelian product ke supplier(kulak an)[perputaran uang], pengeluaran(pake uang bisnis untuk keperluan di luar bisnis, seperti gaji karyawan)[uang tidak berputar],
    - _supplier_ = untuk mengelola informasi supplier, seperti menambahkan data supplier baru atau mengambil informasi supplier yang ada.
    - _customers_ = untuk mengelola informasi pelanggan, seperti menambahkan data pelanggan baru atau mengambil informasi pelanggan yang ada.
    - _member_ = kalo melakukan transaksi baru sebagai member otomatis bisa mendapatkan diskon, diskon bisa di ubah-ubah tergantung role admin
    - _payments_ = untuk mengelola proses pembayaran, termasuk memproses pembayaran, mengelola metode pembayaran, atau mengambil riwayat pembayaran.
    - _reports_ = untuk menghasilkan laporan keuangan atau laporan lainnya terkait penjualan, stok, atau kinerja toko.
+ 1.2.2 Spesifikasi Request dan Response
+ 1.2.3 Desain Struktur Database
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