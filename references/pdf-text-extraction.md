# PDF Text Extraction for Academic Papers

When user submits PDF files as references, `read_file` may fail (too large, binary PDF). Use PyMuPDF via terminal instead.

## Setup

```bash
# Install PyMuPDF in the active python venv
uv pip install PyMuPDF --python python
```

## Extract Full Text

```python
import fitz
doc = fitz.open(r'C:\path\to\paper.pdf')
text = ''.join(p.get_text() for p in doc)
# text now contains all extractable text
doc.close()
```

## Common Pitfalls

- **Backtick in username**: On Windows, MSYS/bash interprets backticks as command substitution. Use escaped forms: `\`` in bash strings, or write extraction as a `.py` file and run it.
- **MSYS paths vs Windows paths**: `python` (hermes venv) may not resolve MSYS `/c/Users/...` paths. Use raw Windows paths with `r'C:\Users\...'` prefix when calling PyMuPDF.
- **`python3` vs `python`**: On this host `python3` → Python 3.14.4 (no pip), `python` → hermes venv 3.11.15 (has PyMuPDF after uv install). Install packages with `uv pip install --python python` to target the correct interpreter.
- **Scanned PDFs**: Some PDFs contain scanned images, not text. Try `ocr-and-documents` skill or `marker-pdf` for OCR fallback.

## Quick One-Liner (bash-safe)

```bash
python -c "import fitz; doc=fitz.open('C:/path/to/file.pdf'); print(''.join(p.get_text() for p in doc)); doc.close()"
```

Note: Use forward slashes in the path string (bash-safe) or `\u0060` for backtick in username.
