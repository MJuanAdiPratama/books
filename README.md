# Books

M Juan Adi Pratama - 1122140109  
Flutter project yang menjalankan operasi asyncronous dan integrasi API.

## Laporan Praktikum

### Soal no 1
menambahkan nama panggilan pada title app sebagai identitas hasil pekerjaaan.

```dart
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Juan',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      home: const FuturePage(),
    );
  }
```

### Soal no 2

Implementasi pencarian buku menggunakan Google Books API.
[Lihat contoh buku Mantappu Jiwa](https://www.google.co.id/books/edition/Mantappu_Jiwa_Buku_Latihan_Soal/TzCyDwAAQBAJ)

![Hasil Pencarian Buku](/images/soal2.png)

### Soal no 3

```dart
    onPressed: () {
        setState(() {});
        getData()
        .then((value) {
            result = value.body.toString().substring(0, 450);
            setState(() {});
        })
        .catchError((_) {
            result = 'An error occured';
            setState(() {});
        });
    },
```

#### Penjelasan:

- **Substring**: Untuk mengambil 450 karakter dari awal respons.
- **Catch Error**: Untuk menangkap jika terjadi error pada pemanggilan data.
- **Set State**: Untuk memperbarui UI.

#### Demo

<img src="images/soal3.gif" alt="Capture no 3" width="300">

### Soal no 4

#### Langkah 1

```dart
Future<int> returnOneAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 1;
  }

Future<int> returnTwoAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 2;
  }

Future<int> returnThreeAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 3;
  }
```

#### Langkah 2

```dart
Future count() async {
    int total = 0;
    total = await returnOneAsync();
    total += await returnTwoAsync();
    total += await returnThreeAsync();
    setState(() {
      result = total.toString();
    });
  }
```

#### Penjelasan:

- **Fungsi returnOneAsync()**: Untuk mengembalikan nilai 1 setelah 3 detik.
- **Fungsi returnTwoAsync()**: Untuk mengembalikan nilai 2 setelah 3 detik.
- **Fungsi returnThreeAsync()**: Untuk mengembalikan nilai 3 setelah 3 detik.
- **Fungsi count() async**:  Untuk menghitung total dari ketiga angka tersebut, Setelah total dihitung hasilnya diubah menjadi teks dan ditampilkan di UI menggunakan setState(), jadi total waktu proses 9 detik.

#### Demo

<img src="images/soal4.gif" alt="Capture no 4" width="300">