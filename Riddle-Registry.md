picoCTF Forensic Challenge (Easy) — Writeup

medium write-up : "https://medium.com/@abrar.fathoni/picoctf-forensic-challenge-easy-1842dbdda0ba?postPublishedType=initial"

Deskripsi Singkat
Pada challenge ini, diberikan sebuah file PDF bernama confidential.pdf. 
Tujuan utamanya adalah menemukan flag yang tersembunyi di dalam file tersebut menggunakan teknik digital forensics sederhana.
Challenge ini menguji pemahaman dasar tentang metadata file dan encoding, khususnya penggunaan Base64.

Tools yang Digunakan : 

- ExifTool

- Base64 Decoder (CLI Linux / WSL)


Langkah Penyelesaian
1. Analisis File Awal
Pertama, file PDF diperiksa menggunakan ExifTool untuk melihat apakah terdapat metadata tersembunyi di dalam file.
Command yang digunakan:
exiftool confidential.pdf
Dari hasil output, ditemukan field metadata pada bagian Author yang berisi string mencurigakan dalam format Base64.

2. Identifikasi Encoding
String yang ditemukan memiliki karakteristik Base64:

- Kombinasi huruf besar dan kecil
- Angka
- Kadang diakhiri dengan tanda =
Hal ini menjadi indikasi kuat bahwa string tersebut adalah encoded text.

3. Decode Base64
String Base64 kemudian didecode menggunakan command berikut:
echo "BASE64_STRING" | base64 -d
Setelah proses decoding, muncul string dalam format flag picoCTF.
Flag :
picoCTF{puzzl3d_m3tadata_f0und!_c8f91d68}

Pembelajaran yang Didapat
Dari challenge ini, ada beberapa poin penting:
Metadata file bisa menyimpan informasi sensitif.
Tools forensics sederhana seperti ExifTool sangat powerful.
Encoding seperti Base64 sering digunakan dalam CTF untuk menyembunyikan flag.
Selalu periksa metadata sebelum melakukan analisis yang lebih kompleks.
