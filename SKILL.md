---
name: academic-assistant
description: "Workflow akademik: tulis makalah dari referensi yang dikirim user, sitasi APA, daftar pustaka, gaya penulisan akademik"
version: 2.0.0
platforms: [linux, macos, windows]
---

# Academic Assistant v2

Workflow bikin makalah akademik — **user kirim referensi sendiri** (file PDF/link), AI tulis makalah + sitasi APA.

> **Perubahan dari v1:** User mencari jurnal sendiri. Tidak ada lagi auto-search arXiv/Semantic Scholar untuk menghemat token.

## Workflow Baru

### 1. User Kirim Referensi

Kamu bisa kirim referensi ke saya dalam format berikut:

| Format | Cara kirim | Contoh |
|--------|-----------|--------|
| **PDF** | Path file lokal | `C:\Users\PC\Documents\paper.pdf` |
| **DOCX** | Path file lokal | `C:\Users\PC\Documents\paper.docx` |
| **TXT / Markdown** | Path file atau paste teks | Langsung copas teks jurnal |
| **arXiv link/ID** | URL atau ID | `https://arxiv.org/abs/2301.12345` atau `2301.12345` |
| **DOI** | DOI link | `https://doi.org/10.xxxx/xxxxx` |
| **Link PDF publik** | URL langsung | `https://example.com/paper.pdf` |

**Contoh prompt kirim referensi:**
> "Saya mau bikin makalah, ini referensinya: C:\Users\PC\paper.pdf"
> "Pakai jurnal ini: https://arxiv.org/abs/2301.12345"
> "Ini link jurnalnya https://doi.org/10.xxxx/xxxxx"

### 2. Saya Baca & Ekstrak

Saya akan:
- Baca file PDF/DOCX/TXT via `read_file` atau script Python (lihat `references/pdf-text-extraction.md` untuk teknik ekstraksi PDF via PyMuPDF jika `read_file` gagal)
- Atau akses link arXiv/DOI Semantic Scholar via web
- Extract: judul, penulis, tahun, abstrak, metodologi, temuan utama

### 3. Generate Sitasi APA

Saya generate APA 7th edition citation dari referensi yang kamu kirim.

Format APA 7th:
```
Lastname, F. M. (Year). Title of article. *Journal/arXiv*. https://doi.org/XXX
```

**Contoh prompt:**
> "Buat APA citation dari paper yang saya kirim"
> "Buat daftar pustaka APA dari semua referensi ini: [list ID/DOI]"

### 4. Tulis Makalah

Perintah workflow menulis:

> "Buat outline makalah tentang TOPIK dari referensi yang saya kirim"
> "Tulis section Introduction, 300-500 kata, gaya akademik, sertakan sitasi"
> "Tulis Literature Review dari referensi yang ada"
> "Generate abstract 150-250 kata dari draft yang sudah ada"

### 5. Review & Finalisasi

> "Cek grammar & spelling draft saya — [paste text]"
> "Review — pastikan setiap klaim punya sitasi APA"
> "Cek format APA di References section"
> "Generate daftar pustaka final dari semua sitasi di makalah"

## Struktur Makalah Standar

1. Abstract
2. Introduction
3. Literature Review
4. Methodology
5. Results
6. Discussion
7. Conclusion
8. References (APA 7th)

## Panduan Prompt Cepat

| Tujuan | Prompt |
|--------|--------|
| Kirim referensi | "Ini paper saya: [path/link]" |
| Sitasi APA | "Buat APA citation dari referensi ini" |
| Outline | "Buat outline makalah tentang [topik]" |
| Tulis section | "Tulis Introduction, 400 kata, dari referensi yang ada" |
| Proofread | "Proofread text ini: [paste]" |
| Daftar pustaka | "Generate References APA dari semua referensi" |
| Full makalah | "Buat full makalah dari referensi yang saya kasih, topik: [topik]" |

## Aturan Penulisan

- Gaya penulisan akademik formal (bahasa Indonesia atau Inggris sesuai permintaan)
- Semua sumber pakai APA 7th edition
- Setiap klaim harus ada sitasi
- Cek grammar & spelling sebelum final
- Hindari plagiarisme — gunakan paraphrase

## Skill Terkait

- `ocr-and-documents` — baca PDF/scanned paper lokal (jika butuh OCR)
- `arxiv` — fallback jika butuh cek detail paper dari arXiv ID
