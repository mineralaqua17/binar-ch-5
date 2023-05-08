# BCR - Car Management API

Api untuk management layanan web Car Rental. Api ini adalah bagian dari project individu kursus fullstack development yang di selenggarakan oleh Binar Academy.

Pada aplikasi ini user di bagi menjadi 3 Role, yaitu superadmin, admin dan member.

Default account untuk superadmin bisa di temukan [disini](#akun-superadmin). Akun superadmin juga bisa di modifikasi dengan mengikuti instruksi di halaman ini.

## Setup Server

    npm install

Perintah ini digunakan untuk meng-install semua dependencies yang dibutuhkan agar server ini bisa berjalan.
Selanjutnya adalah mengkonfigurasi pengaturan server ( server settings ). Semua konfigurasi berada pada folder `config`. Semua file konfigurasi tergambarkan di bawah ini :

| Filename      | Details                                                              |
| ------------- | -------------------------------------------------------------------- |
| cloudinary.js | Secret dari account Cloudinary dan folder target untuk upload gambar |
| database.js   | Akun database PostgreSQL dan detail database details untuk Sequelize |
| superadmin.js | data akun superadmin yang digunakan untuk seeder                     |
| encryption.js | Konfigurasi enkripsi untuk proses autentikasi.                       |
| server.js     | Konfigurasi server.                                                  |
| routes.js     | Konfigurasi API routes.                                              |
| upload.js     | Konfigurasi Multer.                                                  |

Setelah konfigurasi selesai, jalankan command di bawah ini untuk menyelesaikan setup server dengan satu command:

    npm run setup

apabila ada masalah dengan command diatas, maka bisa menjalankan command set :

    sequelize db:drop
    sequelize db:create
    sequelize db:migrate
    sequelize db:seed:all

Menjalankan perintah tersebut akan me-reset database server.

## Akun Superadmin

Akun superadmin bisa mengakses semua endpoint pada api dan membuat akun dengan role admin. konfigurasi akun default superadmin adalah sebagai berikut :

    name: Superadmin
    email: super@admin.com
    password: admin

Untuk merubah konfigurasi default akun superadmin, bisa merubah detail pada file `config/superadmin.js`. untuk menerapkan perubahan pada akun default superadmin, jalankan perintah ini :

    npm run superadmin

apabila terdapat masalah dengan perintah di atas, maka bisa menjalankan perintah-perintah di bawah ini :

    sequelize db:seed:undo
    sequelize db:seed:all

## Run Server

Untuk menjalankan pada mode normal, jalankan perintah ini :

    npm start

Untuk menjalankan server pada mode development, bisa menjalankan perintah di bawah ini :

    npm run develop

Server secara default akan berjalan pada `http://localhost:8000` .

## API Documentation

Dokumentasi API bisa di akses dengan format berbeda :

| Tipe Dokumentasi   | Link                                                      | Details                                                                                      |
| ------------------ | --------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| OpenAPI Swagger UI | http://localhost:8000 <br> http://localhost:8000/api-docs | Swagger UI merujuk pada file `docs/openapi.json` . Bisa di akses setelah menjalankan server. |
| Dokumentasi Statis | [Here](/docs)                                             | Markdown file documentation                                                                  |

Sistem Autentikasi dan Autorisasi yang di gunakan adalah `token-based auth`.

## Database Design

Model database yang di gunakan pada aplikasi ini bisa di representasikan oleh diagram berikut :

![erd image](/docs/erd.png)
