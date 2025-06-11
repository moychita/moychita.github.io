---
title: HUFFMAN CODING
date: 2025-06-11 13.14.00 +0800
categories: [Desain dan Analisis Algoritma]
tags: [huffman, compression, greedy-algorithm, data-encoding]
---

# Huffman Coding 📦  
*Cara Kompres Data Biar Dompet dan Memori Sama-Sama Lega*

---

## Hai, teman-teman pecinta algoritma dan hemat ruang! 😄  
Pernah ngerasa file kamu kegedean padahal isinya cuma teks doang? Nah, itu tandanya kamu belum kenalan sama si jenius **Huffman Coding**. Algoritma ini ibarat Marie Kondo-nya data: dia bikin semuanya jadi lebih ringkas tanpa buang-buang informasi.✨

---

## 1. Kenalan Dulu Sama Huffman Coding 💌  
Huffman Coding adalah algoritma **kompresi data lossless**. Artinya, gak ada satu huruf pun yang hilang saat dikecilin.  
Ditemukan oleh **David A. Huffman** pada tahun 1952 — iya, udah tua tapi masih dipakai sampai sekarang, loh!

Dia bekerja dengan cara **mengganti karakter yang sering muncul** dengan **kode yang pendek**, dan karakter yang jarang muncul dengan **kode lebih panjang**. Hasilnya? File jadi lebih kecil, tapi gak kehilangan makna. 💡

---

## 2. Konsep Dasar 🧠  
Huffman itu cinta sama statistik!

- Karakter yang **paling sering muncul** → dapet kode **paling pendek**  
- Karakter yang **jarang muncul** → dapet kode **lebih panjang**  

Semua ini dibangun dalam sebuah **pohon biner**. Jadi, kalau kamu suka naik pohon, Huffman juga suka! 🌳

---

## 3. Langkah-Langkah Huffman Coding 🪜  
Langkah-langkahnya tuh kayak bikin minuman es campur, tapi buat karakter:

1. Hitung frekuensi setiap karakter.
2. Bikin simpul untuk masing-masing karakter.
3. Gabungkan dua simpul dengan frekuensi terkecil.
4. Ulangi sampai terbentuk **satu pohon Huffman**.
5. Tetapkan kode biner: kiri = 0, kanan = 1.

Dan boom! Data siap dikompres!

---

## 4. Contoh Kasus Sederhana 🍰  
Misalnya kita punya string: `ABBCCCDDDD`  
Frekensinya:
- A = 1  
- B = 2  
- C = 3  
- D = 4  

Bentuk pohon Huffman-nya nanti kasih kode kayak gini:
- D = 0  
- C = 10  
- B = 110  
- A = 111  

Hasilnya? Pesan jadi lebih pendek dibandingkan format aslinya. Hemat byte, hemat stres. 😌

---

## 5. Simulasi Seru! 🎮  
Pesan: `BCCABBDDAECCBBAEDDCC`  
Jumlah karakter: 20

Kalau pakai ASCII standar (8 bit per karakter), kita butuh:  
**8 × 20 = 160 bit**

### Tapi… Setelah Huffman?
- Hitung frekuensi tiap huruf  
- Bangun pohon Huffman dengan cara gabungkan frekuensi terkecil → jadi node baru  
- Tandai sisi kiri 0, kanan 1  
- Lakukan **traversal** buat dapetin kode setiap huruf  

Misalnya:
- A = 001 (3 bit × 3 huruf = 9 bit)  
- B = 10 (2 bit × 6 huruf = 12 bit)  
- … dan seterusnya  

🎉 Total = **45 bit**  
Dari 160 ke 45? Itu penghematan **lebih dari 70%**! Wow banget kan? 😍

---

## 6. Implementasi Pseudo Code & Kompleksitas 💻  
### Pseudo Code:
(Singkat aja ya, yang penting ngerti idenya 😎)
- Buat priority queue dari frekuensi karakter
- Gabungkan dua node dengan frekuensi terendah
- Bangun pohon sampai satu root
- Traversal untuk generate kode

### Kompleksitas:
- Waktu: **O(N log N)** (N = karakter unik)

---

## 7. Kelebihan & Kekurangan Huffman ⚖️  
**✅ Kelebihan:**
- Lossless (data utuh, gak hilang satu huruf pun)
- Efisien kalau karakter gak merata
- Banyak digunakan (ZIP, MP3, JPEG)

**❌ Kekurangan:**
- Gak optimal kalau frekuensi merata
- Perlu tabel kode untuk decoding

---

## Kesimpulan Manis 🍬  
Huffman Coding itu solusi keren buat ngurangin ukuran data tanpa harus ngorbanin satu huruf pun. Dia pintar, hemat, dan cocok banget buat kamu yang suka kompresi tapi gak mau kehilangan apapun. Bener-bener sahabat sejati buat pengkodean data!


