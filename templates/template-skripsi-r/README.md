# Templat Skripsi Quarto — Versi R (Format FEB UNDIP)

Templat siap pakai untuk menyusun skripsi dengan Quarto, memakai **R** (mesin knitr)
untuk seluruh analisis. Fokuslah menulis isi; format dan penomoran sudah otomatis.
Versi Python tersedia di folder `template-skripsi-python/`.

## Mulai cepat

1. **Salin** folder ini, ganti namanya (mis. `skripsi-saya/`).
2. **Isi data diri**: buka `tex/frontmatter.tex`, edit blok **DATA DIRI** di bagian
   atas (judul, nama, NIM, program studi, dosen pembimbing).
3. **Sesuaikan** `title` dan `author` di `_quarto.yml`.
4. **Ganti data** di `data/` dengan data penelitian Anda.
5. **Tulis isi** di `bab/01` sampai `bab/05`.
6. **Tambahkan logo** universitas sebagai `gambar/logo-undip.png` (opsional).
7. **Render**:

   ```bash
   quarto render --to pdf
   ```

   Hasil ada di `_book/`.

## Apa yang sudah otomatis

- Halaman sampul, persetujuan, pengesahan kelulusan ujian, pernyataan orisinalitas,
  abstrak, dan kata pengantar (dari `tex/frontmatter.tex`).
- Penomoran bab gaya "BAB I", "BAB II", ... (angka Romawi, rata tengah).
- Penomoran tabel & gambar mengikuti bab (Tabel 4.1, Gambar 4.2, ...).
- Daftar isi, daftar tabel, daftar gambar.
- Daftar pustaka otomatis dari `referensi.bib` (gaya APA).
- Statistik deskriptif, regresi, dan uji asumsi klasik di BAB IV dihitung langsung
  dari data.

## Prasyarat

Pasang **R** dan paket-paket berikut (di Console R), lalu **TinyTeX** untuk PDF:

```r
install.packages(c("rmarkdown", "knitr", "jsonlite",
                   "dplyr", "ggplot2", "sf",        # olah data, grafik, peta
                   "maptiles", "tidyterra",          # basemap OSM untuk peta
                   "tseries", "lmtest", "car"))      # uji asumsi klasik (JB, BP, VIF)
```

```bash
quarto install tinytex
```

Paket **`sf`** dipakai untuk peta tematik (*choropleth*) di BAB III & IV. Batas wilayah
berasal dari [GADM](https://gadm.org) dan sudah disertakan sebagai `data/jateng.geojson`.
Peta digambar dengan `ggplot2::geom_sf` di atas **basemap OpenStreetMap** (paket
`maptiles` + `tidyterra`), jadi perlu **koneksi internet** saat render.

Data berasal dari **dua berkas** yang digabung otomatis melalui `kode_wilayah` + `tahun`:
`data/data_kemiskinan_jateng.csv` (utama) dan `data/data_pendukung_jateng.json`
(pendukung: akses sanitasi & TPAK). Lihat BAB III untuk cara penggabungannya.

## Catatan penting

- Data `data/data_kemiskinan_jateng.csv` adalah **data tiruan** untuk demonstrasi.
  Ganti dengan data asli (mis. BPS) dan cantumkan sumbernya.
- Format mengikuti pedoman umum FEB UNDIP. **Selalu** periksa dan sesuaikan dengan
  buku pedoman penulisan skripsi terbaru program studi Anda.

## Slide sidang (bonus)

Berkas **`slide-sidang.qmd`** di folder ini adalah contoh slide presentasi sidang yang
**memakai `data/` yang sama** dengan skripsi — jadi ubah data sekali, slide ikut
diperbarui. Satu sumber, dua format slide:

```bash
quarto render slide-sidang.qmd --to revealjs   # -> slide-sidang.html (layar/web)
quarto render slide-sidang.qmd --to beamer     # -> slide-sidang.pdf  (proyektor/cetak)
```

Beamer (PDF) memerlukan TinyTeX. Lihat buku, bab *Membuat Slide Sidang*.
