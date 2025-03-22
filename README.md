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
[Lihat contoh buku buku Mantappu Jiwa](https://www.google.co.id/books/edition/Mantappu_Jiwa_Buku_Latihan_Soal/TzCyDwAAQBAJ)

![Hasil Pencarian Buku](/images/soal2.png)