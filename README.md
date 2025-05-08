**AbsenSiswa**  
**Aplikasi Absensi Siswa Berbasis Web**

![](media/image1.jpg){width="2.0833333333333335in"
height="2.0416666666666665in"}

**Nurul Ardaniyah  
D0220037**

**Framwork Web Based  
2025  
**

**Role dan Fitur-fiturnya**

**Role: Admin**

- Mengelola data siswa (tambah, ubah, hapus)

- Mengelola data guru

- Mengelola data mata pelajaran

- Melihat dan mengelola data absensi

- Melihat laporan absensi berdasarkan siswa atau tanggal

**Role: Guru**

- Melihat data siswa

- Mengisi absensi siswa berdasarkan kelas dan mata pelajaran

- Melihat riwayat absensi yang sudah dilakukan

**Role: Siswa**

- Melihat histori kehadiran sendiri

- Mendapatkan notifikasi kehadiran

**Tabel-tabel database beserta field dan tipe datanya**

**Tabel 1: Siswa**

| **Nama Field**    | **Tipe Data**         | **Keterangan**                   |
|-------------------|-----------------------|----------------------------------|
| **id_siswa**      | **int(11)**           | **Primary Key, Auto Increment**  |
| **nis**           | **varchar(20)**       | **Nomor Induk Siswa**            |
| **nama**          | **varchar(100)**      | **Nama lengkap siswa**           |
| **jenis_kelamin** | **enum(\'L\',\'P\')** | **L = Laki-laki, P = Perempuan** |
| **alamat**        | **text**              | **Alamat rumah siswa**           |
| **kelas**         | **varchar(10)**       | **Kelas siswa**                  |

**Tabel 2: Guru**

| **Nama Field** | **Tipe Data**    | **Keterangan**                  |
|----------------|------------------|---------------------------------|
| **id_guru**    | **int(11)**      | **Primary Key, Auto Increment** |
| **nip**        | **varchar(20)**  | **Nomor Induk Pegawai**         |
| **nama**       | **varchar(100)** | **Nama lengkap guru**           |
| **mapel**      | **varchar(50)**  | **Mata pelajaran yang diajar**  |

**Tabel 3: Absen**

| **Nama Field** | **Tipe Data**                     | **Keterangan**                        |
|----------------|-----------------------------------|---------------------------------------|
| **id_absen**   | **int(11)**                       | **Primary Key, Auto Increment**       |
| **id_siswa**   | **int(11)**                       | **Foreign Key ke tabel siswa**        |
| **tanggal**    | **date**                          | **Tanggal kehadiran**                 |
| **keterangan** | **enum(\'H\',\'I\',\'S\',\'A\')** | **H=Hadir, I=Izin, S=Sakit, A=Alpha** |
| **id_guru**    | **int(11)**                       | **Foreign Key ke tabel guru**         |

**Tabel 4: pengguna**

| **Nama Field**  | **Tipe Data**                          | **Keterangan**                  |
|-----------------|----------------------------------------|---------------------------------|
| **id_pengguna** | **int(11)**                            | **Primary Key, Auto Increment** |
| **username**    | **varchar(50)**                        | **Nama pengguna login**         |
| **password**    | **varchar(255)**                       | **Password (terenkripsi)**      |
| **role**        | **enum(\'admin\',\'guru\',\'siswa\')** | **Jenis pengguna**              |
| **id_siswa**    | **int(11)**                            | **Nullable, jika role = siswa** |
| **id_guru**     | **int(11)**                            | **Nullable, jika role = guru**  |

**Jenis relasi dan tabel yang berelasi**

| **Tabel 1**  | **Tabel 2** | **Jenis Relasi** | **Penjelasan**                                            |
|--------------|-------------|------------------|-----------------------------------------------------------|
| **absen**    | **siswa**   | **Many to One**  | **Banyak absensi milik satu siswa**                       |
| **absen**    | **guru**    | **Many to One**  | **Banyak absensi dicatat oleh satu guru**                 |
| **pengguna** | **siswa**   | **One to One**   | **Satu akun pengguna untuk satu siswa (jika role siswa)** |
| **pengguna** | **guru**    | **One to One**   | **Satu akun pengguna untuk satu guru (jika role guru)**   |
