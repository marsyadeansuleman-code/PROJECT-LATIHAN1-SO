# PROJECT-LATIHAN1-SO
Project Based Leaning 1
# LANGKAH 1 BUAT STRUKTUR DIREKTORI
# Berikut contoh membuat project_1
Deskripsi gambar
(https://drive.google.com/file/d/1MVXPJKMpbQW9O593lhQ5g_O1_ioE2EoU/view?usp=drivesdk)

```
ubuntu@marsyadea : mkdir project_1
```
# Berikut contoh perintah Berpindah Direktori ke Project_1 dan Membuat folder document images archives logs:
Deskripsi gambar
(https://drive.google.com/file/d/174EXAB5gp6M534iQk3WNLus02XC4cSO6/view?usp=drivesdk)
```
cd Project_1
```
```
mkdir documents images archives logs
```
# Perintah Membuat 20 file simple
Deskripsi gambar
(https://drive.google.com/file/d/1ElBSKUW-tkxIyN0sz_8EpPy8nFnk68Zg/view?usp=drivesdk)
```
touch file{1..10}.txt file{11..15}.jpg file{16..18}.pdf file{19..20}.log
```
# Berikut contoh perintah memasukan sebuah teks ke masing masing file yang berbeda:
Deskripsi gambar
(https://drive.google.com/file/d/1OZDcUTnj2-Gl9_xCLzu4Jjwjrrs5f4f4/view?usp=drivesdk)
```
echo "Ini adalah dokumen contoh" > file1.txt
```
```
echo "Data gambar" > file11.jpg
```
```
echo "Log sistem contoh" > file20.log
```
Penjelasan:

-`mkdir` → membuat folder baru.
-`touch` → membuat file kosong dengan cepat.
-`echo` → menulis teks ke dalam file.
# LANGKAH 2 SCRIPT ORGANISASI FILE
# Buat Script Organisasi File di dalam direktori projek:
```
nano operasi_file.sh
```
# ISI SCRIPT
Deskripsi gambar
(https://drive.google.com/file/d/1WNVE7yjSLjFm3vfcCp0gp3x9ZN6Z-Nvv/view?usp=drivesdk)

```
#!/bin/bash
# Script untuk mengorganisasi file berdasarkan ekstensi

# Pastikan berada di direktori proyek
cd ~/project_1

# Pindahkan file sesuai ekstensi
find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
find . -maxdepth 1 -type f -name "*.jpg" -exec mv {} images/ \;
find . -maxdepth 1 -type f -name "*.pdf" -exec mv {} archives/ \;
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

# Konfirmasi hasil
echo "File berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
```
# Beri Hak Eksekusi:
```
chmod +x operasi_file.sh
```
# Eksekusi Script Yang Telah Dibuat:
```
./operasi_file.sh
```
Penjelasan:
-`find . -maxdepth 1 -type f -name "*.ext"` → mencari file berdasarkan ekstensi di direktori saat ini.

-`exec mv {} folder/ ;` → memindahkan file hasil pencarian ke folder sesuai.

-`chmod +x` → memberi izin eksekusi ke script.
# LANGKAH 3 FUNGSI PENCARIAN
# Buat file Search_file.sh
```
nano search_file.sh
```
Deakripsi gambar
(https://drive.google.com/file/d/1n5t0VWrIg_a3R7hrayUk7-USORuMqhqV/view?usp=drivesdk)

```
 #!/bin/bash
# Script: search_files.sh
# Fungsi: Mencari file berdasarkan nama, ukuran, atau konten

cd ~/project_1

echo "=== PENCARIAN FILE ==="
echo "1. Cari berdasarkan nama"
echo "2. Cari berdasarkan ukuran"
echo "3. Cari berdasarkan isi konten"
read -p "Pilih opsi (1/2/3): " opsi

case $opsi in
  1)
    read -p "Masukkan nama atau pola file (contoh: *.txt): " nama
    echo "Hasil pencarian:"
    find . -type f -name "$nama"
    ;;
  2)
    read -p "Masukkan batas ukuran (contoh: +1M untuk lebih dari 1MB, -500k untuk kurang dari 500KB): " ukuran
    echo "Hasil pencarian:"
    find . -type f -size "$ukuran"
    ;;
  3)
    read -p "Masukkan kata kunci yang ingin dicari dalam file: " keyword
    echo "Hasil pencarian:"
    grep -r "$keyword" .
    ;;
  *)
    echo "Opsi tidak valid."
    ;;
esac
```
# Beri Hak Eksekusi
```
chmod +x search_file.sh
```
# Eksekusi File Yang Telah Dibuat
```
./search_file.sh
```
Penjelasan:
-`find . -type f -name "*.txt"` → mencari file dengan pola nama tertentu.

-`find . -size +1M` → mencari file berukuran lebih dari 1 MB.

-`grep -r "teks"`→ mencari teks di dalam isi file secara rekursif.
# Langkah 4 – Generate Laporan File Sistem

Buat file report.sh
```
nano report.sh
```
Deskripsi gambar
(https://drive.google.com/file/d/1TuVoeQBkh60cibHXGzCttor8HRLFhG6M/view?usp=drivesdk)
```
#!/bin/bash
# Script: generate_report.sh
# Fungsi: Membuat laporan statistik file sistem

cd ~/project_file_management

echo "=== LAPORAN FILE SISTEM ===" > report.txt
echo "Tanggal: $(date)" >> report.txt
echo "" >> report.txt

echo "--- Jumlah File dan Folder ---" >> report.txt
ls -lR | wc -l >> report.txt
echo "" >> report.txt

echo "--- Ukuran Total Folder ---" >> report.txt
du -sh . >> report.txt
echo "" >> report.txt

echo "--- Daftar 10 File Terbesar ---" >> report.txt
find . -type f -exec du -h {} + | sort -rh | head -10 >> report.txt
echo "" >> report.txt

echo "--- Statistik Berdasarkan Ekstensi ---" >> report.txt
echo "TXT: $(find . -type f -name '*.txt' | wc -l)" >> report.txt
echo "JPG: $(find . -type f -name '*.jpg' | wc -l)" >> report.txt
echo "PDF: $(find . -type f -name '*.pdf' | wc -l)" >> report.txt
echo "LOG: $(find . -type f -name '*.log' | wc -l)" >> report.txt

echo "" >> report.txt
echo "=== Selesai! Laporan disimpan di report.txt ==="
```
# Beri Hak Akses Eksekusi
```
chmod +x report.sh
```
# Eksekusi File Yang Telah Di Buat
```
./report.sh
```

# Melihat isi Laporan
```
cat report.sh
```
Penjelasan:

-`find . -type f -name "*.txt"` → mencari file dengan pola nama tertentu.

-`find . -size +1M` → mencari file berukuran lebih dari 1 MB.

-`grep -r "teks"` → mencari teks di dalam isi file secara rekursif.






































