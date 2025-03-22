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