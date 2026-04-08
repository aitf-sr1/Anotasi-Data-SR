# Evaluasi Anotasi Emosi Siswa SR

Repository ini berisi script Python untuk mengukur tingkat kesepakatan (reliabilitas) antara dua annotator saat melabeli tingkat emosi siswa. Script ini sangat cocok untuk dataset yang memiliki label bertingkat.

## Kenapa Pakai Metode Ini?

Dalam evaluasi ini, respons emosi siswa (Confusion, Engagement, Frustration, Boredom) dinilai menggunakan **data bertingkat** dengan 4 level:
- 0: Sangat Rendah (Very Low)
- 1: Rendah (Low)
- 2: Tinggi (High)
- 3: Sangat Tinggi (Very High)

Karena labelnya bertingkat, kita tidak bisa mengevaluasinya menggunakan sekadar perhitungan Akurasi biasa. Alasannya sederhana:
Jika nilai aslinya adalah `0`, lalu annotator menjawab `3`, itu adalah kesalahan fatal. Namun jika annotator menjawab `1`, itu hanya meleset sedikit. Akurasi biasa menganggap kedua kesalahan ini sama beratnya.

Oleh karena itu, script ini menggunakan metrik **Quadratic Weighted Kappa (QWK)**. QWK akan memberikan "hukuman" atau penalti yang jauh lebih besar jika perbedaan penilaiannya ekstrem (misal beda 3 tingkat), dibandingkan jika perbedaannya tipis (misal beda 1 tingkat).

## Persyaratan
Library standar untuk machine learning:
```bash
pip install scikit-learn numpy