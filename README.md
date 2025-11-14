# Sistem Dokumentasi Agenda Kegiatan Polrestabes

Aplikasi web untuk manajemen dokumentasi agenda kegiatan Polrestabes dengan fitur upload, konversi format, dan manajemen user.

## 🚀 Fitur Utama

- **Manajemen Dokumen**: Upload, edit, hapus, dan lihat dokumen
- **Multi-format Support**: PDF, Word, Excel, Image, dan Manual Input
- **Konversi File**: Konversi antar format (PDF, Word, Excel)
- **Manajemen User**: Admin dan User dengan permission berbeda
- **Responsive Design**: Tampilan optimal di semua device
- **Security**: Login system dengan role-based access

## 👥 Role dan Permission

### Admin

- ✅ Baca SEMUA dokumen
- ✅ Tambah dokumen baru
- ✅ Edit SEMUA dokumen
- ✅ Hapus SEMUA dokumen
- ✅ Tambah user/admin baru

### User

- ✅ Baca SEMUA dokumen
- ✅ Tambah dokumen baru
- ❌ Tidak bisa edit dokumen orang lain
- ❌ Tidak bisa hapus dokumen

## 🔧 Instalasi dan Setup

### 1. Install Dependencies

````bash
pip install flask flask-sqlalchemy werkzeug pandas reportlab PyPDF2 openpyxl Pillow docx2txt

Buka browser dan kunjungi: http://localhost:5000

🔐 Login Default
Akun Admin
Username: admin

Password: admin123

Akun User
Username: user

Password: user123

👨‍💼 Cara Menambah User/Admin Baru
Method 1: Edit Langsung di app.py
Edit file app.py, cari fungsi init_db() dan tambahkan user baru:

def init_db():
    with app.app_context():
        db.create_all()

        # User default yang sudah ada
        if not User.query.filter_by(username='admin').first():
            admin_user = User(
                username='admin',
                password=generate_password_hash('admin123'),
                role='admin'
            )
            db.session.add(admin_user)

        if not User.query.filter_by(username='user').first():
            regular_user = User(
                username='user',
                password=generate_password_hash('user123'),
                role='user'
            )
            db.session.add(regular_user)

        # ✅ TAMBAH USER BARU DI SINI:

        # Contoh: Tambah Admin baru
        if not User.query.filter_by(username='kepala').first():
            new_admin = User(
                username='kepala',           # Username
                password=generate_password_hash('kepala123'),  # Password
                role='admin'                 # Role: 'admin' atau 'user'
            )
            db.session.add(new_admin)

        # Contoh: Tambah User biasa
        if not User.query.filter_by(username='staff1').first():
            new_user = User(
                username='staff1',
                password=generate_password_hash('staff123'),
                role='user'
            )
            db.session.add(new_user)

        # Contoh: Tambah lebih banyak user
        if not User.query.filter_by(username='bambang').first():
            new_user2 = User(
                username='bambang',
                password=generate_password_hash('bambang123'),
                role='user'
            )
            db.session.add(new_user2)

        db.session.commit()

contoh format user baru :
if not User.query.filter_by(username='NAMA_USER').first():
    new_user = User(
        username='NAMA_USER',      # Ganti dengan username yang diinginkan
        password=generate_password_hash('PASSWORD'),  # Ganti dengan password
        role='admin'               # 'admin' atau 'user'
    )
    db.session.add(new_user)

📊 Jenis Dokumen yang Didukung
Manual Input - Input teks langsung

PDF - File PDF (.pdf)

Word - Document (.doc, .docx)

Excel - Spreadsheet (.xls, .xlsx)

Image - Gambar (.jpg, .jpeg, .png)

🔄 Fitur Konversi Format
Manual Input → PDF, Word, Excel

PDF → Word, Excel

Word → PDF, Excel

Excel → PDF, Word

Image → PDF, Word, Excel (metadata)

🛡️ Keamanan
Password di-hash menggunakan Werkzeug

Session management

Role-based access control

File type validation

SQL injection protection

📞 Support
Jika ada masalah atau pertanyaan, silakan hubungi AI Assisten.


## 🎯 Ringkasan Cara Tambah User:

### Langkah Cepat:
1. **Buka `app.py`**
2. **Cari `def init_db():`**
3. **Tambahkan code seperti ini:**
```python
if not User.query.filter_by(username='USERNAME_BARU').first():
    new_user = User(
        username='USERNAME_BARU',
        password=generate_password_hash('PASSWORD_BARU'),
        role='admin'  # atau 'user'
    )
    db.session.add(new_user)

Save dan restart Flask app
````
