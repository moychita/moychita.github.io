---
title: SUBSET SUM PROBLEM
date: 2025-06-11 13.14.00 +0800
categories: [Desain dan Analisis Algoritma]
tags: [Greedy, Dynamic Programming, NP-Complete, Subset Sum]
---

# Subset Sum Problem 🎯

Hai teman-teman algoritmik! 👋

Pernah gak sih kalian dikasih daftar angka terus disuruh cari kombinasi yang jumlahnya pas sama target tertentu? Rasanya kayak lagi main tebak-tebakan sambil ngitung cepat ya 😅 Nah, ternyata itu bukan sekadar soal matematika biasa—itu adalah **Subset Sum Problem** alias **SSP**!

Yuk, kita telusuri dunia SSP ini dengan gaya yang fun tapi tetap penuh ilmu! 🚀

---

## Apa Itu Subset Sum Problem? 🤔

Bayangin kamu punya satu set angka, misalnya `{3, 34, 4, 12, 5, 2}` dan ditantang buat cari kombinasi angka dari set itu yang jumlahnya **pas** jadi 9.

Misalnya:
- `{4, 5}` ✅ cocok banget!
- `{3, 2}` ❌ masih kurang
- `{12}` ❌ terlalu besar

Kalau ada kombinasi yang pas, kita jawab “YES”, kalau gak ada, kita jawab “NO”. Simpel, tapi ternyata cukup rumit juga kalau jumlah elemennya banyak!

---

## Kenapa SSP Itu Penting? 🌍

Masalah ini muncul di banyak hal nyata loh:

- **Kriptografi 🔐**: Banyak sistem keamanan digital memakai SSP sebagai fondasi dasar!
- **Keuangan 💰**: Mau pilih investasi yang totalnya sesuai budget? SSP bisa bantu!
- **AI & Genetika 🤖🧬**: Dari analisa data DNA sampai penyusunan solusi otomatis—semuanya bisa pakai SSP!
- **Manajemen Proyek 🧠**: Milih proyek mana yang bisa dikerjain dalam anggaran? SSP dong jawabannya!

---

## SSP Itu NP-Complete 😱

Yap, SSP termasuk ke dalam golongan **masalah NP-Complete**. Artinya:
- Solusinya bisa dicek dengan cepat ✅
- Tapi nyari solusinya bisa sangat lambat ❌ (kalau pakai cara brute-force)

Jadi kita perlu pendekatan yang cerdas buat menaklukkan si SSP ini!

---

## Strategi Menyelesaikan SSP 💡

### 1. **Brute Force (Tapi Capek 😓)**
Coba semua kemungkinan subset → ada `2ⁿ` kombinasi!
> Cocok untuk data kecil. Tapi kalau set-nya besar, komputernya bisa nangis 😭

### 2. **Rekursif**
Kita bisa buat fungsi rekursif:
```cpp
bool isSubsetSum(arr, n, sum)
```
Tapi tetap aja kompleksitas waktunya **O(2ⁿ)**.

### 3. **Dynamic Programming (Senjata Rahasia! 💪)**

Nah ini dia pendekatan cerdas kita:
- Waktu: `O(n × sum)`
- Memori: `O(n × sum)` (bisa dioptimasi jadi `O(sum)` saja!)

#### Contoh Table DP (Tabulation Style)
Misalnya:
- Set = `{1, 2, 3}`
- Target = `3`

DP Table:
```
  j→  0   1   2   3
i↓
0   T   F   F   F
1   T   T   F   F
2   T   T   T   T
3   T   T   T   T
```

Hasil: YES! Kita bisa dapat sum 3 dari `{1,2}` atau `{3}`

---

## Variasi SSP yang Seru! 🎲

1. **Bounded SSP**  
   Setiap angka cuma bisa dipakai 1x. Kayak jatah liburan, harus pilih dengan bijak! ✈️

2. **Unbounded SSP**  
   Angka boleh dipakai berkali-kali. Cocok buat masalah seperti koin receh! 💰

3. **Exact k Elements**  
   Harus pas jumlahnya **dan** jumlah elemennya juga pas k buah!

4. **Partition Problem**  
   Bisa gak set dibagi jadi dua subset yang totalnya sama?

5. **Multi-target SSP**  
   Misalnya: total harga ≤ 100 dan berat ≤ 2kg. Banyak banget aplikasinya!

6. **Approximate SSP**  
   Kalau gak bisa pas, cari yang **mendekati** target—mirip strategi hidup kan? 😄

---

## Implementasi C++ 🧑‍💻

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool isSubsetSum(const vector<int>& arr, int n, int sum) {
    vector<vector<bool>> dp(n+1, vector<bool>(sum+1, false));

    // Base case: sum 0 bisa dicapai dengan subset kosong
    for (int i = 0; i <= n; i++) dp[i][0] = true;

    // Fill DP table
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= sum; j++) {
            if (arr[i-1] > j)
                dp[i][j] = dp[i-1][j];
            else
                dp[i][j] = dp[i-1][j] || dp[i-1][j - arr[i-1]];
        }
    }

    return dp[n][sum];
}

int main() {
    vector<int> arr = {3, 34, 4, 12, 5, 2};
    int sum = 9;

    if (isSubsetSum(arr, arr.size(), sum))
        cout << "Subset ditemukan!\n";
    else
        cout << "Tidak ada subset yang sesuai.\n";

    return 0;
}
```

---

## Kompleksitas Algoritma 📈

| Pendekatan             | Waktu       | Memori     |
|------------------------|-------------|-------------|
| Rekursif               | O(2ⁿ)       | O(n)        |
| DP - Tabulasi          | O(n × sum)  | O(n × sum)  |
| DP - Optimasi Ruang    | O(n × sum)  | O(sum)      |

---

## Kesimpulan Manis 🍬

✨ **Subset Sum Problem** adalah tantangan klasik dengan berbagai aplikasi dunia nyata—dari keuangan hingga keamanan digital.

Dengan teknik seperti **dynamic programming**, kita bisa menaklukkan masalah ini dengan cara yang elegan dan efisien.

Jadi, jangan takut lagi sama soal-soal kombinasi jumlah! Kamu sudah punya ilmu dan kode C++-nya juga! 😉

Happy coding! 🌈💻
