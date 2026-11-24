# Template LaTeX Final Project PCD & Visi Komputer

Template ini disusun untuk laporan final project bergaya artikel jurnal dua kolom.

## Aturan inti project
- 1 kelompok = 3 mahasiswa.
- Dataset utama wajib **data primer**, diambil sendiri **hanya di dalam lingkungan Universitas Brawijaya**.
- Akuisisi dilakukan pada kondisi yang wajar dan berisiko rendah; hindari identitas personal/sensitif sebagai target utama.
- Project wajib menunjukkan proses PCD sebelum/bersama Computer Vision.
- Wajib membandingkan minimal:
  1. PCD + handcrafted feature + Machine Learning,
  2. Raw Image + Deep Learning,
  3. PCD + Deep Learning.
- Wajib ada evaluasi kuantitatif dan analisis error.
- Final harus memiliki demo/prototipe yang berjalan.

## Pembagian peran
1. Mahasiswa 1: Data & PCD.
2. Mahasiswa 2: Feature Extraction & Machine Learning.
3. Mahasiswa 3: Deep Learning/Computer Vision & Integrasi.

Akuisisi data adalah tanggung jawab bersama. Semua anggota wajib memahami seluruh pipeline.

## Timeline
- Progress 1: 4–5 November 2026 — proposal, desain data, pipeline, contoh data primer awal.
- Progress 2: 18–19 November 2026 — dataset mayoritas selesai, PCD, fitur, baseline ML.
- Progress 3: 25–26 November 2026 — dataset final, DL, perbandingan eksperimen, prototype awal.
- Final: 2–3 Desember 2026 — hasil final, evaluasi, analisis, demo, laporan dan source code.

## Instalasi Dependensi & Build Lokal

Template ini membutuhkan distribusi TeX (`pdflatex` + `bibtex`). Daftar paket TeX Live yang digunakan tercantum di [`latex-requirements.txt`](latex-requirements.txt).

### 1. Install TeX Distribution

* **Windows:**
  1. Install [MiKTeX](https://miktex.org/download) (saat instalasi pilih *"Install missing packages on-the-fly: Yes"*).
  2. *(Opsional untuk `latexmk`)* Install Strawberry Perl jika MiKTeX memintanya saat menjalankan `latexmk`.
* **macOS:**
  * **Opsi lengkap:**
    ```bash
    brew install --cask mactex
    ```
  * **Opsi ringan (BasicTeX):**
    ```bash
    brew install --cask basictex
    sudo tlmgr update --self
    sudo tlmgr install $(grep -vE '^\s*(#|$)' latex-requirements.txt)
    ```
* **Linux (Ubuntu/Debian):**
  ```bash
  sudo apt update && sudo apt install -y \
    texlive-latex-base texlive-latex-recommended texlive-latex-extra \
    texlive-fonts-recommended texlive-publishers texlive-science latexmk
  ```

### 2. Live Preview di VS Code (Pengganti Overleaf)

1. Install extension **LaTeX Workshop** (`james-yu.latex-workshop`) di VS Code.
2. Buka `main.tex`. Setiap kali file disimpan (`Cmd+S` / `Ctrl+S`), LaTeX Workshop akan otomatis mengompilasi dan memperbarui preview PDF.

### 3. Build Manual via Terminal hingga `main.pdf` Final

Masuk ke direktori `latex/`, lalu jalankan salah satu cara berikut:

* **Dengan `latexmk` (disarankan):**
  ```bash
  cd latex
  latexmk -pdf main.tex
  ```
  Untuk membersihkan file build sementara (`.aux`, `.log`, `.bbl`, dll.):
  ```bash
  latexmk -c
  ```

* **Tanpa `latexmk` (wajib 4 langkah agar sitasi `references.bib` dan referensi silang muncul):**
  ```bash
  cd latex
  pdflatex main.tex
  bibtex main
  pdflatex main.tex
  pdflatex main.tex
  ```

Bagian berwarna abu-abu dan diawali `[Isi: ...]` adalah petunjuk yang harus diganti/dihapus pada laporan final.
