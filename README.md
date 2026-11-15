# Monitor Kelelahan Otot Trapezius

Aplikasi monitor berbasis browser untuk memantau sinyal EMG real-time dari ESP32 melalui kabel USB. Menampilkan grafik RMS dan MDF beserta garis batas, kartu baseline dan status, serta log serial, dan dapat menyimpan data ke CSV.

## Cara Menjalankan

Web Serial memerlukan Chrome atau Edge dan akses melalui `localhost`.

```bash
cd BED_Monitor
python -m http.server 8000
```

Buka `http://localhost:8000/monitor/monitor.html`, lalu klik **Hubungkan ESP32** dan pilih port ESP32.

Tutup Serial Monitor Arduino IDE sebelum menghubungkan, karena port hanya bisa dipakai satu aplikasi. Baud rate: 115200.

## Format Data

Firmware mengirim satu baris per jendela sampel:

```
[MONITOR Normal] RMS:19.050 BatasRMS:26.430 MDF:187.50 BatasMDF:221.65 BaseRMS:17.620 BaseMDF:260.80
[HASIL] Baseline RMS = 17.620 , MDF = 260.80
[EVENT] Terapi mulai - kelelahan terdeteksi
```

Setiap baris data membawa baseline, sehingga kartu baseline terisi walaupun monitor tersambung setelah kalibrasi selesai.

## Fitur

- Grafik RMS dan MDF real-time dengan garis batas.
- Kartu: RMS, MDF, baseline RMS, baseline MDF, dan mode/status.
- **Simpan CSV**: mengunduh seluruh data sesi (waktu, RMS, batas RMS, MDF, batas MDF).
- **Bersihkan Grafik**: mengosongkan tampilan dan data sesi.
