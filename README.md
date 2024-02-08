# 1. Proyek RESTfulAPI Point of Sale

___

### 1.1 Persiapan Awal

#### + 1.1.1 Identifikasi Kebutuhan Bisnis

- satu
- dua

#### + 1.1.2 Analisis Persyaratan API

- satu
- dua

#### + 1.1.3 Persiapan Lingkungan Pengembangan

- satu
- dua

### 1.2 Desain API

#### + 1.2.1 Identifikasi Endpoint

1. _/auth_ = login, register (admin, cashier) kasir hanya bisa membuat transaksi baru, yang bisa membuat role cashier adalah role admin
    + Endpoints:
        - POST /auth/login
        - POST /auth/register
    + Deskripsi:
        - login: Endpoint untuk mengotentikasi pengguna.
        - register: Endpoint untuk mendaftarkan pengguna baru (admin atau kasir).

2. _/product_ = menambahkan produk baru, memperbarui informasi produk termasuk menambahkan stock product, atau menghapus produk.
    + Endpoints:
        - POST /product/add
        - PUT /product/update
        - DELETE /product/delete
    + Deskripsi:
        - add: Endpoint untuk menambahkan produk baru.
        - update: Endpoint untuk memperbarui informasi produk, termasuk penambahan stok.
        - delete: Endpoint untuk menghapus produk.

3. _/transactions_ = membuat transaksi baru, history penjualan, pembelian product ke supplier(kulak an)[perputaran uang], pengeluaran(pake uang bisnis untuk keperluan di luar bisnis, seperti gaji karyawan)[uang tidak berputar],
    + Endpoints:
        - POST /transactions/new
        - GET /transactions/history
    + Deskripsi:
        - new: Endpoint untuk membuat transaksi baru.
        - history: Endpoint untuk mendapatkan riwayat transaksi.

4. _/supplier_ = untuk mengelola informasi supplier, seperti menambahkan data supplier baru atau mengambil informasi supplier yang ada.
    + Endpoints:
        - POST /supplier/add
        - GET /supplier/list
    + Deskripsi:
        - add: Endpoint untuk menambahkan data supplier baru.
        - list: Endpoint untuk mendapatkan daftar supplier yang ada.

5. _/customers_ = untuk mengelola informasi pelanggan, seperti menambahkan data pelanggan baru atau mengambil informasi pelanggan yang ada.
    + Endpoints:
        - POST /customers/add
        - GET /customers/list
    + Deskripsi:
        - add: Endpoint untuk menambahkan data pelanggan baru.
        - list: Endpoint untuk mendapatkan daftar pelanggan yang ada.

6. _/member_ = kalo melakukan transaksi baru sebagai member otomatis bisa mendapatkan diskon, diskon bisa di ubah-ubah tergantung role admin
    + Endpoints:
        - PUT /member/discount
    + Deskripsi:
        - discount: Endpoint untuk mengatur diskon untuk anggota, yang dapat diubah oleh admin.

7. _/payments_ = untuk mengelola proses pembayaran, termasuk memproses pembayaran, mengelola metode pembayaran, atau mengambil riwayat pembayaran.
    + Endpoints:
        - POST /payments/process
        - GET /payments/history
    + Deskripsi:
        - process: Endpoint untuk memproses pembayaran.
        - history: Endpoint untuk mendapatkan riwayat pembayaran.

8. _/reports_ = untuk menghasilkan laporan keuangan atau laporan lainnya terkait penjualan, stok, atau kinerja toko.
    + Endpoints:
        - GET /reports/financial
        - GET /reports/sales
    + Deskripsi:
        - financial: Endpoint untuk menghasilkan laporan keuangan.
        - sales: Endpoint untuk menghasilkan laporan penjualan.

#### + 1.2.2 Spesifikasi Request dan Response

#### + 1.2.3 Desain Struktur Database

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