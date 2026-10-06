# LAPORAN PRAKTIKUM PEMROGRAMAN TYPESCRIPT

## Membuat Segitiga Angka, Deret Aritmatika, dan Bilangan Prima Berdasarkan NIM

---

**Nama** : Cavan Rijal Retadiyanto

**NIM** : 043826907

**Prodi** : Sistem Informasi

**Semester** : 8

**Tanggal Praktikum** : 05/10/2026

---

## 1. Tujuan

Praktikum ini bertujuan untuk:
- Membuat program TypeScript untuk menampilkan pola segitiga angka berdasarkan digit terakhir NIM.
- Membuat program TypeScript untuk menampilkan deret aritmatika berdasarkan dua digit terakhir NIM dan digit ketiga dari belakang.
- Membuat program TypeScript untuk menampilkan bilangan prima hingga batas tertentu berdasarkan dua digit terakhir NIM.

---

## 2. Analisis NIM

**NIM: 043826907**

| Komponen | Nilai | Keterangan |
|----------|-------|-----------|
| Digit terakhir | 7 | Tinggi segitiga = 7 |
| Dua digit terakhir | 07 | Angka awal deret = 7 |
| Digit ke-3 dari belakang | 9 | Beda = 9 + 1 = 10 |
| Dua digit terakhir + 10 | 17 | Batas akhir bilangan prima = 17 |

---

## 3. Program 1: Segitiga Angka

**File**: `segitiga.ts`

**Deskripsi**: Program ini membuat segitiga angka dengan tinggi 7 (sesuai digit terakhir NIM). Setiap baris menampilkan angka dari 1 hingga nomor baris tersebut.

**Kode Program**:

```typescript
const nimSegitiga = "043826907";

function segitigaAngka(tinggi: number): void {
  for (let i = 1; i <= tinggi; i++) {
    let baris = "";
    for (let j = 1; j <= i; j++) {
      baris += j + " ";
    }
    console.log(baris.trim());
  }
}

const digitTerakhir = Number(nimSegitiga[nimSegitiga.length - 1]);
console.log("Soal 1 - Segitiga angka:");
segitigaAngka(digitTerakhir);
```

**Output**:

```
Soal 1 - Segitiga angka:
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
1 2 3 4 5 6
1 2 3 4 5 6 7
```

**Penjelasan Logika**:
- Fungsi `segitigaAngka()` menerima parameter `tinggi` sebagai jumlah baris
- Loop pertama `for (let i = 1; i <= tinggi; i++)` mengiterasi setiap baris
- Loop kedua `for (let j = 1; j <= i; j++)` menampilkan angka dari 1 hingga nomor baris
- `console.log(baris.trim())` menampilkan hasil dengan spasi dihilangkan di akhir

---

## 4. Program 2: Deret Aritmatika

**File**: `aritmatika.ts`

**Deskripsi**: Program ini membuat deret aritmatika dengan angka awal 7, beda 10, dan menampilkan 10 angka pertama.

**Kode Program**:

```typescript
const nimAritmatika = "043826907";

function deretAritmatika(start: number, beda: number, jumlah: number): void {
  const hasil: number[] = [];
  for (let i = 0; i < jumlah; i++) {
    hasil.push(start + i * beda);
  }
  console.log(hasil.join(", "));
}

const duaDigitTerakhir = Number(nimAritmatika.slice(-2));
const digitKeTigaDariBelakang = Number(nimAritmatika[nimAritmatika.length - 3]);
const beda = digitKeTigaDariBelakang + 1;

console.log("Soal 2 - Deret aritmatika:");
deretAritmatika(duaDigitTerakhir, beda, 10);
```

**Output**:

```
Soal 2 - Deret aritmatika:
7, 17, 27, 37, 47, 57, 67, 77, 87, 97
```

**Penjelasan Logika**:
- Fungsi `deretAritmatika()` menerima parameter `start` (angka awal), `beda` (selisih), dan `jumlah` (banyak angka)
- Loop `for (let i = 0; i < jumlah; i++)` menghitung setiap suku dengan rumus: `suku = start + i * beda`
- `hasil.push()` menambahkan setiap suku ke dalam array
- `hasil.join(", ")` menampilkan array dengan format yang rapi (dipisahkan koma dan spasi)

**Rumus Deret Aritmatika**:
- U₁ = 7
- U₂ = 7 + 10 = 17
- U₃ = 7 + (2 × 10) = 27
- Dan seterusnya hingga U₁₀ = 7 + (9 × 10) = 97

---

## 5. Program 3: Bilangan Prima

**File**: `prima.ts`

**Deskripsi**: Program ini menampilkan semua bilangan prima dari 1 hingga 17 (dua digit terakhir NIM + 10).

**Kode Program**:

```typescript
const nimPrima = "043826907";

function isPrima(n: number): boolean {
  if (n <= 1) return false;
  if (n === 2) return true;
  if (n % 2 === 0) return false;

  for (let i = 3; i * i <= n; i += 2) {
    if (n % i === 0) return false;
  }
  return true;
}

function bilanganPrima(sampai: number): void {
  const hasil: number[] = [];
  for (let i = 1; i <= sampai; i++) {
    if (isPrima(i)) {
      hasil.push(i);
    }
  }
  console.log(hasil.join(", "));
}

const duaDigitTerakhir = Number(nimPrima.slice(-2));
const batasPrima = duaDigitTerakhir + 10;

console.log("Soal 3 - Bilangan prima:");
bilanganPrima(batasPrima);
```

**Output**:

```
Soal 3 - Bilangan prima:
2, 3, 5, 7, 11, 13, 17
```

**Penjelasan Logika**:
- Fungsi `isPrima()` mengecek apakah sebuah angka adalah bilangan prima
  - Jika n ≤ 1, bukan prima → return false
  - Jika n = 2, adalah prima → return true
  - Jika n habis dibagi 2, bukan prima → return false
  - Loop `for (let i = 3; i * i <= n; i += 2)` mengecek pembagi dari 3 hingga √n
  - Jika ada pembagi, bukan prima → return false
  - Jika tidak ada pembagi, adalah prima → return true

- Fungsi `bilanganPrima()` menampilkan semua bilangan prima dari 1 hingga batas
- Loop `for (let i = 1; i <= sampai; i++)` mengiterasi setiap angka
- Jika `isPrima(i)` bernilai true, angka ditambahkan ke array `hasil`

**Bilangan Prima 1-17**:
- 2 (hanya habis dibagi 1 dan 2)
- 3 (hanya habis dibagi 1 dan 3)
- 5 (hanya habis dibagi 1 dan 5)
- 7 (hanya habis dibagi 1 dan 7)
- 11 (hanya habis dibagi 1 dan 11)
- 13 (hanya habis dibagi 1 dan 13)
- 17 (hanya habis dibagi 1 dan 17)

---

## 6. Cara Menjalankan Program

### Prasyarat:
- Node.js dan TypeScript sudah terinstall di komputer
- VS Code atau editor lainnya

### Langkah-langkah:

1. **Buat folder project**:
   ```bash
   mkdir nim-programs-typescript
   cd nim-programs-typescript
   ```

2. **Inisialisasi project TypeScript**:
   ```bash
   npm init -y
   npm install --save-dev typescript
   ```

3. **Buat file TypeScript** (`segitiga.ts`, `aritmatika.ts`, `prima.ts`)

4. **Jalankan dengan Node.js**:
   ```bash
   npx ts-node segitiga.ts
   npx ts-node aritmatika.ts
   npx ts-node prima.ts
   ```

   Atau compile ke JavaScript terlebih dahulu:
   ```bash
   npx tsc segitiga.ts
   node segitiga.js
   ```

---

## 7. Kesimpulan

Berdasarkan NIM 043826907, program TypeScript berhasil dibuat untuk:

1. **Segitiga Angka**: Menampilkan segitiga dengan tinggi 7 baris, di mana setiap baris menampilkan angka dari 1 hingga nomor baris tersebut.

2. **Deret Aritmatika**: Menampilkan deret aritmatika dengan angka awal 7, beda 10, dan menampilkan 10 suku pertama dari deret tersebut (7, 17, 27, 37, 47, 57, 67, 77, 87, 97).

3. **Bilangan Prima**: Menampilkan semua bilangan prima dari 1 hingga 17 (7 bilangan prima: 2, 3, 5, 7, 11, 13, 17).

Setiap program dibuat dengan teknik perulangan (loop), kondisional (if-else), dan fungsi-fungsi dasar pemrograman. Program ini dapat dipahami dan dikembangkan lebih lanjut sesuai kebutuhan.

---

## 8. Catatan Teknis

### Error yang Mungkin Terjadi:

**Error**: `Cannot redeclare block-scoped variable 'nim'`

**Penyebab**: Ketika beberapa file TypeScript dalam satu folder menggunakan nama variabel yang sama di scope global.

**Solusi**:
- Ubah nama variabel per file: `nimSegitiga`, `nimAritmatika`, `nimPrima`
- Atau tambahkan `export {};` pada setiap file untuk menjadikannya module

Contoh:
```typescript
export {};
const nim = "043826907";
```

---

## 9. Referensi Repository

Link GitHub Repository: https://github.com/cavanrjl/nim-programs-typescript

Semua file kode tersedia di repository di atas.

---

**Disiapkan oleh**: Cavan Rijal Retadiyanto  
**NIM**: 043826907  
**Tanggal**: 05/10/2026
