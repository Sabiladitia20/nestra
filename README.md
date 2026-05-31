# Nestra: AI/ML Wind Energy Analysis & Prediction Platform

Nestra (Dashboard Mahi) adalah platform monorepo terintegrasi untuk analisis, pemetaan, dan prediksi potensi energi angin untuk Pembangkit Listrik Tenaga Bayu (PLTB) di Indonesia menggunakan AI/ML.

Platform ini terdiri dari dua komponen utama:
1. **`nestra-web` (Frontend)**: Dashboard web berbasis Next.js modern, interaktif, dan responsif dengan peta spasial serta visualisasi grafik tingkat lanjut.
2. **`backend` (Backend)**: API server berbasis FastAPI yang kuat, terintegrasi dengan model prediksi Machine Learning (Scikit-Learn) dan asisten AI/LLM berbasis RAG.

---

## 📁 Struktur Monorepo

```text
Dashboard Mahi/
├── nestra-web/           # Frontend Next.js (App Router)
│   ├── src/
│   │   ├── app/          # Halaman (Dashboard, Wind Prediction, Data Analysis, dll.)
│   │   ├── components/   # Komponen UI (WindRoseChart, SiteMap, Header, Sidebar)
│   │   └── lib/          # API & Mock Data utility
│   └── package.json
│
├── backend/              # Backend FastAPI (Python)
│   ├── app/
│   │   ├── api/          # Endpoints API (Chat, Health, Prediction)
│   │   ├── core/         # Konfigurasi & Logging
│   │   ├── schemas/      # Model request/response (Pydantic)
│   │   └── services/     # Logika bisnis (LLM & ML Predictor)
│   ├── pltb_artifacts/   # Model ML terlatih (.joblib) & metadata lokasi
│   ├── tests/            # Test suite (pytest)
│   ├── run.py            # Entry point backend
│   └── requirements.txt  # Dependency Python
│
├── .gitignore            # Gitignore global tingkat root
└── README.md             # Dokumentasi utama platform
```

---

## 🛠️ Arsitektur & Teknologi

### Frontend (`nestra-web`)
* **Framework**: Next.js 16 (React 19) dengan App Router.
* **Styling**: Tailwind CSS v4 & Tailwind Animate.
* **Charts**: Recharts (Custom Wind Rose Chart, Time-Series Analysis).
* **Maps**: Leaflet & React Leaflet (Peta Sebaran Lokasi PLTB).
* **Icons**: Lucide React.

### Backend (`backend`)
* **Framework**: FastAPI (Asynchronous Python Web Framework).
* **Machine Learning**: Scikit-Learn & Joblib (Model Prediksi Lokasi: Baron, Bawean, Pandeglang, Situbondo, Sukabumi).
* **Generative AI / LLM**: OpenAI GPT API & ChromaDB (RAG Pipeline untuk asisten AI "Mahi").
* **Configuration**: Pydantic v2 (Typed Environment Settings).
* **Unit Testing**: Pytest.

---

## 🚀 Petunjuk Memulai Cepat (Quick Start)

### Prasyarat
* Node.js v18 atau versi terbaru
* Python 3.10 atau versi terbaru

---

### Langkah 1: Jalankan Backend (FastAPI)

1. Masuk ke folder backend:
   ```bash
   cd backend
   ```

2. Buat dan aktifkan virtual environment Python:
   ```bash
   # Windows (PowerShell/CMD)
   python -m venv venv
   .\venv\Scripts\activate

   # macOS/Linux
   python -m venv venv
   source venv/bin/activate
   ```

3. Instal semua dependensi:
   ```bash
   pip install -r requirements.txt
   ```

4. Konfigurasikan Environment Variables:
   ```bash
   cp .env.example .env
   # Edit file .env dan masukkan OPENAI_API_KEY Anda (opsional untuk mode fallback)
   ```

5. Jalankan server backend:
   ```bash
   python run.py
   ```
   * Server backend berjalan di: `http://localhost:8000`
   * Dokumentasi interaktif Swagger UI: `http://localhost:8000/docs`

---

### Langkah 2: Jalankan Frontend (Next.js)

1. Buka terminal baru dan masuk ke folder frontend dari tingkat root:
   ```bash
   cd nestra-web
   ```

2. Instal dependensi Node.js:
   ```bash
   npm install
   ```

3. Jalankan server pengembangan Next.js:
   ```bash
   npm run dev
   ```
   * Frontend berjalan di: `http://localhost:3000`

---

## 🔌 API Utama (Backend)

| Metode | Endpoint | Deskripsi |
|--------|----------|-----------|
| **GET** | `/api/v1/health` | Status kesehatan sistem backend |
| **POST** | `/api/v1/chat` | Chat dengan Mahi AI chatbot |
| **POST** | `/api/v1/predict` | Melakukan prediksi kecepatan & arah angin berdasarkan lokasi |

---

## 📈 Fitur Utama Platform

1. **Dashboard Overview**: Ringkasan performa dan estimasi efisiensi energi turbin angin di seluruh lokasi PLTB di Indonesia.
2. **Peta Interaktif Spasial (Site Assessment)**: Pemetaan lokasi turbin secara spasial dengan Leaflet, lengkap dengan indikator kelayakan lokasi.
3. **Prediksi Angin (Wind Prediction)**: Menjalankan kalkulasi model ML `.joblib` terlatih secara real-time untuk memprediksi kecepatan dan arah angin.
4. **Grafik Wind Rose**: Visualisasi grafis frekuensi dan intensitas arah mata angin yang disajikan secara dinamis.
5. **Mahi AI Assistant**: Chatbot asisten pintar yang memberikan wawasan, analisis, dan rekomendasi terkait potensi energi angin di lokasi tertentu menggunakan integrasi LLM & RAG.
