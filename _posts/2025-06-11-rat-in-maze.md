---
title: RAT IN A MAZE
date: 2025-06-11 13.14.00 +0800
categories: [Desain dan Analisis Algoritma]
tags: [Backtracking, Maze, Pathfinding, Recursion, DFS]
---

# Rat in a Maze 🐭

Halo para penjelajah algoritma! 🌟

Kali ini kita bakal menyusuri lorong-lorong penuh teka-teki dalam **Rat in a Maze Problem**! Bayangin ada seekor tikus kecil yang harus keluar dari labirin. Misinya? Temukan semua jalan dari pintu masuk sampai ke pintu keluar! Tapi hati-hati ya—gak semua jalan bisa dilewati!

---

## Apa Itu Rat in a Maze? 🧀

Masalah ini mengajarkan kita tentang **backtracking**—sebuah teknik eksplorasi jalur yang “mundur” saat menemui jalan buntu.

Bayangin sebuah labirin yang direpresentasikan sebagai matriks (grid) berisi angka:
- `1` artinya jalan bisa dilewati
- `0` artinya jalan buntu atau tembok

Tugas kita? Cari semua **jalur dari kiri atas** (0,0) ke **kanan bawah** (N-1,N-1) tanpa mengunjungi sel yang sama dua kali dalam satu jalur.

---

## Aturan Mainnya 🎯

- Tikus bisa bergerak ke empat arah: `U` (Up), `D` (Down), `L` (Left), `R` (Right)
- Tidak boleh keluar dari batas matriks
- Tidak boleh melewati sel yang bernilai `0`
- Setiap langkah harus ke sel yang belum pernah dikunjungi dalam satu jalur

---

## Contoh Labirin 🧩

```
1 0 0 0
1 1 0 1
1 1 0 0
0 1 1 1
```

Tikus mulai dari `(0,0)` dan harus mencapai `(3,3)`

Contoh jalur valid:
- DRDDRR
- DDRDRR

---

## Simulasi Jalannya Tikus 🐭➡️

1. Mulai di `(0,0)` → pilih `Down` ke `(1,0)`
2. Dari `(1,0)` → bisa ke `(2,0)` atau `(1,1)`
3. Teruskan ke `(1,1)` → lalu `(2,1)`
4. Lanjut ke `(3,1)` → lalu `(3,2)` → dan terakhir `(3,3)` 🎉

---

## Implementasi dalam C++ 💻

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

void solveMaze(vector<vector<int>>& maze, int x, int y, vector<vector<bool>>& visited, string path, vector<string>& res) {
    int n = maze.size();
    if (x == n-1 && y == n-1) {
        res.push_back(path);
        return;
    }

    int dx[] = {1, 0, 0, -1}; // D, L, R, U
    int dy[] = {0, -1, 1, 0};
    char move[] = {'D', 'L', 'R', 'U'};

    for (int i = 0; i < 4; i++) {
        int newX = x + dx[i];
        int newY = y + dy[i];
        if (newX >= 0 && newY >= 0 && newX < n && newY < n &&
            maze[newX][newY] == 1 && !visited[newX][newY]) {
            visited[newX][newY] = true;
            solveMaze(maze, newX, newY, visited, path + move[i], res);
            visited[newX][newY] = false;
        }
    }
}

vector<string> findPaths(vector<vector<int>> &maze) {
    int n = maze.size();
    vector<string> res;
    vector<vector<bool>> visited(n, vector<bool>(n, false));
    if (maze[0][0] == 1)
        solveMaze(maze, 0, 0, visited, "", res);
    return res;
}

int main() {
    vector<vector<int>> maze = {
        {1, 0, 0, 0},
        {1, 1, 0, 1},
        {1, 1, 0, 0},
        {0, 1, 1, 1}
    };

    vector<string> paths = findPaths(maze);
    for (string path : paths)
        cout << path << endl;

    return 0;
}
```

---

## Kelebihan & Kekurangan 📊

**Kelebihan:**
- Sederhana dan mudah diimplementasikan
- Bisa temukan semua solusi!
- Tidak butuh struktur data kompleks

**Kekurangan:**
- Tidak efisien untuk labirin besar
- Berpotensi stack overflow (karena rekursi)
- Bisa ulang jalur yang sama jika tidak hati-hati

---

## Aplikasi Dunia Nyata 🌎

- **Robot Navigasi 🤖**
- **Peta & GPS 📍**
- **Simulasi & Game 🎮**

---

## Penutup 🎉

Rat in a Maze adalah contoh klasik dari **backtracking** yang sangat seru dan aplikatif. Dengan memahami cara kerja tikus kecil di labirin, kamu juga sedang belajar menyusun solusi optimal dengan strategi eksplorasi dan mundur!

Ayo terus eksplorasi algoritma dan jangan takut tersesat—karena kadang, mundur selangkah bisa bikin kamu maju lebih jauh! 🚀

Happy coding! 🐭💻
