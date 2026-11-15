# Monitor Kelelahan Otot Trapezius

Aplikasi monitor berbasis browser untuk memantau sinyal EMG secara real-time dari ESP32 melalui kabel USB. Menampilkan grafik RMS dan MDF beserta garis batas, kartu statistik, dan log serial, serta dapat menyimpan data ke CSV.

## Cara Menjalankan

Web Serial memerlukan Chrome atau Edge dan akses melalui `localhost`.

```bash
cd BED_Monitor
python -m http.server 8000
```

Buka `http://localhost:8000/monitor/monitor.html`, lalu klik **Hubungkan ESP32** dan pilih port ESP32.

Tutup Serial Monitor Arduino IDE sebelum menghubungkan, karena port hanya bisa dipakai satu aplikasi. Baud rate: 115200.

## Fitur

- Grafik RMS dan MDF real-time dengan garis batas.
- Kartu statistik: RMS, MDF, baseline RMS, baseline MDF, dan mode/status.
- **Simpan CSV**: mengunduh seluruh data sesi (waktu, RMS, batas RMS, MDF, batas MDF).
- **Bersihkan Grafik**: mengosongkan tampilan dan data sesi.

## Format Data yang Dibaca

Monitor membaca baris berikut dari ESP32:

```
[MONITOR NORMAL] RMS:0.812 BatasRMS:1.250 MDF:94.30 BatasMDF:80.10
BASELINE RMS:0.833 MDF:94.10
STATUS: TERAPI dimulai (manual)
```

Baris lain tetap ditampilkan di log tanpa diproses.
