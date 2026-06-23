# Academic Assistant Skill 🎓

> **Hermes AI skill** — tulis makalah akademik dari referensi PDF/link, sitasi APA 7th edition, daftar pustaka otomatis.

Skill untuk [Hermes Agent](https://hermes-agent.nousresearch.com) yang mengubah workflow penulisan akademik jadi lebih cepat. **User kirim referensinya sendiri** (PDF, arXiv link, DOI), AI baca, ekstrak, lalu tulis makalah lengkap dengan sitasi APA 7th edition.

---

## ✨ Fitur

| Fitur | Detail |
|-------|--------|
| 📄 **Baca Referensi** | PDF lokal, DOCX, TXT, arXiv link, DOI, URL publik |
| 📝 **APA 7th Edition** | Generate sitasi & daftar pustaka otomatis |
| 🧠 **Tulis Makalah** | Full paper: Abstract s/d References |
| 🔍 **Review & Proofread** | Cek grammar, spelling, format APA |
| 💾 **Output File** | Hasil makalah bisa disimpan sebagai PDF |

## 🚀 Cara Pakai

### Load skill
```bash
hermes -s academic-assistant
```

### Contoh prompt

| Tujuan | Prompt |
|--------|--------|
| **Kirim referensi** | `"Ini paper saya: C:\Users\...\paper.pdf"` |
| **APA citation** | `"Buat APA citation dari referensi ini"` |
| **Outline** | `"Buat outline makalah tentang [topik]"` |
| **Tulis section** | `"Tulis Introduction, 400 kata, dari referensi yang ada"` |
| **Full makalah** | `"Buat full makalah dari referensi yang saya kasih, topik: [topik]"` |
| **Proofread** | `"Proofread text ini: [paste]"` |
| **Daftar pustaka** | `"Generate References APA dari semua referensi"` |

## 📋 Format Referensi yang Didukung

| Format | Cara Kirim | Contoh |
|--------|-----------|--------|
| **PDF** | Path file lokal | `C:\Users\...\paper.pdf` |
| **DOCX** | Path file lokal | `C:\Users\...\paper.docx` |
| **TXT / Markdown** | Paste teks | Langsung copas jurnal |
| **arXiv** | URL atau ID | `https://arxiv.org/abs/2301.12345` |
| **DOI** | DOI link | `https://doi.org/10.xxxx/xxxxx` |
| **Link PDF publik** | URL langsung | `https://example.com/paper.pdf` |

## 📑 Struktur Makalah Standar

1. **Abstract** — 150-250 kata
2. **Introduction** — latar belakang, research gap, tujuan
3. **Literature Review** — sintesis referensi terkait
4. **Methodology** — pendekatan penelitian
5. **Results** — temuan utama
6. **Discussion** — interpretasi hasil
7. **Conclusion** — kesimpulan & saran
8. **References** — daftar pustaka APA 7th

> Bisa request struktur custom sesuai kebutuhan.

## ⚙️ Aturan Penulisan

- ✅ Gaya akademik formal (Indonesia / Inggris)
- ✅ Semua sumber pakai APA 7th edition
- ✅ Setiap klaim harus punya sitasi
- ✅ Cek grammar & spelling sebelum final
- ✅ Paraphrase, hindari plagiarisme

## 🔧 Skill Terkait

- `ocr-and-documents` — baca PDF/scanned paper (via OCR)
- `arxiv` — fallback cek detail paper dari arXiv ID

## 📦 Instalasi

```bash
hermes skill install academic-assistant
```

Atau clone repo ini ke folder skills Hermes:

```bash
git clone https://github.com/zeven0709/academic-assistant-skill.git ~/.hermes/skills/academic-assistant
```

## 📄 Lisensi

MIT