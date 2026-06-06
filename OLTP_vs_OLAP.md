# Rangkuman OLTP vs OLAP

> **Mata Kuliah:** Basis Data  
> **Materi:** OLTP (Online Transaction Processing) vs OLAP (Online Analytical Processing)

---

## 1. Pengertian

### 🔷 OLTP (Online Transaction Processing)
OLTP adalah sistem basis data yang dirancang untuk mengelola **transaksi harian** secara real-time. Sistem ini berfokus pada operasi baca/tulis yang cepat dan sering dilakukan oleh banyak pengguna secara bersamaan.

### 🔶 OLAP (Online Analytical Processing)
OLAP adalah sistem basis data yang dirancang untuk **analisis data** dalam jumlah besar guna mendukung pengambilan keputusan bisnis. Sistem ini berfokus pada query kompleks terhadap data historis.

---

## 2. Karakteristik

### OLTP
- Transaksi cepat, singkat, dan sering
- Data selalu up-to-date (real-time)
- Banyak pengguna mengakses secara bersamaan
- Operasi utama: `INSERT`, `UPDATE`, `DELETE`, `SELECT` sederhana
- Data terstruktur dan ternormalisasi

### OLAP
- Query kompleks dengan pembacaan data dalam jumlah besar
- Data historis (tidak sering berubah)
- Sedikit pengguna, namun query berat
- Operasi utama: `SELECT` dengan agregasi (`SUM`, `AVG`, `COUNT`, `GROUP BY`)
- Data denormalisasi untuk performa analitik

---

## 3. Perbandingan OLTP vs OLAP

| Aspek | OLTP | OLAP |
|---|---|---|
| **Tujuan** | Transaksi harian | Analisis data |
| **Operasi** | Read/Write cepat | Read kompleks |
| **Volume data per query** | Kecil | Sangat besar |
| **Kecepatan query** | Milidetik | Detik hingga menit |
| **Jumlah pengguna** | Banyak (ratusan–ribuan) | Sedikit (analis/manajer) |
| **Jenis data** | Data terkini (current) | Data historis |
| **Desain database** | Normalized (3NF) | Denormalized (Star/Snowflake Schema) |
| **Prioritas** | Konsistensi & integritas data | Performa query & kecepatan analisis |

---

## 4. Contoh Penggunaan

### OLTP
- Sistem perbankan (transfer, setor, tarik tunai)
- Aplikasi e-commerce (order, pembayaran, stok barang)
- Sistem kasir / Point of Sale (POS)
- Sistem reservasi tiket

### OLAP
- Laporan penjualan bulanan/tahunan
- Analisis tren bisnis
- Business Intelligence (BI) Dashboard
- Prediksi dan forecasting

---

## 5. Database yang Digunakan

### OLTP
- **PostgreSQL** — open source, fitur lengkap, mendukung ACID
- **MariaDB** — fork dari MySQL, ringan dan cepat
- **MySQL** — populer untuk web application
- **Oracle Database** — enterprise-grade

### OLAP
- **Amazon Redshift** — cloud data warehouse dari AWS
- **Google BigQuery** — cloud analytics dari Google
- **Snowflake** — cloud data platform
- **ClickHouse** — open source, sangat cepat untuk analitik

---

## 6. Hubungan OLTP dan OLAP

Data dari sistem OLTP biasanya dipindahkan secara berkala ke sistem OLAP melalui proses **ETL (Extract, Transform, Load)**:

```
[OLTP Database]  →  ETL Process  →  [Data Warehouse / OLAP]
(transaksi harian)   (Extract,        (analisis & laporan)
                      Transform,
                       Load)
```

**Alur kerja:**
1. **Extract** – Data diambil dari database OLTP
2. **Transform** – Data dibersihkan dan diformat ulang
3. **Load** – Data dimuat ke Data Warehouse (OLAP)

---

## 7. Kesimpulan

| | OLTP | OLAP |
|---|---|---|
| **Cocok untuk** | Operasi bisnis sehari-hari | Pengambilan keputusan strategis |
| **Digunakan oleh** | Kasir, teller bank, admin | Analis data, manajer, eksekutif |
| **Contoh DB** | PostgreSQL, MariaDB | BigQuery, Redshift |

> **Intinya:** OLTP untuk **transaksi**, OLAP untuk **analisis**. Keduanya saling melengkapi dalam ekosistem data modern.

---
