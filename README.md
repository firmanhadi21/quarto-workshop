# Quarto Workshop

Materi workshop (Zoom) memperkenalkan **Quarto** untuk menulis dokumen ilmiah yang
*reproducible* — untuk **mahasiswa** (skripsi) dan **dosen/peneliti**. Tersedia dalam
**Bahasa Indonesia** dan **English** (berkas terpisah).

*Workshop materials introducing Quarto for reproducible scientific writing — for students
and researchers. Available in Indonesian and English (separate files).*

## Isi · Contents

| | Bahasa Indonesia | English |
|---|---|---|
| **Beranda / Home** | `index.qmd` | `en/index.qmd` |
| **Hands-on (±1 jam / ~1 hour)** | `hands-on.qmd` | `en/hands-on.qmd` |
| **Slide (Beamer + Reveal.js)** | `slides/slides-id.qmd` | `slides/slides-en.qmd` |
| **Data contoh / sample data** | `data/` | |

## Render

```bash
# Situs tutorial (HTML) -> _site/
quarto render

# Slide presentasi (Beamer PDF + Reveal.js HTML)
quarto render slides/slides-id.qmd     # -> slides/slides-id.pdf + .html
quarto render slides/slides-en.qmd     # -> slides/slides-en.pdf + .html
```

Halaman tutorial hanya **menampilkan** kode (tidak dieksekusi saat build), jadi situs bisa
diterbitkan tanpa R/Python di CI. Slide **mengeksekusi** R (grafik & peta dari data), jadi
butuh R + paket (`dplyr, ggplot2, sf, maptiles, tidyterra`) + koneksi internet (ubin OSM).

## Terbit · Publish

GitHub Actions (`.github/workflows/publish.yml`) merender situs dan menerbitkannya ke
**GitHub Pages** (branch `gh-pages`) setiap kali ada *push* ke `main`.

Buku lengkap: <https://firmanhadi21.github.io/thesis-with-quarto/>
