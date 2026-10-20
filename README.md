# Semantic Search E-commerce Customer Service Assistant

## 1. Problem Statement

Proyek ini bertujuan untuk membangun prototipe asisten customer service e-commerce yang mampu menemukan informasi FAQ yang relevan berdasarkan pertanyaan pengguna menggunakan metode *semantic search*, kemudian menyusun jawaban secara kontekstual dengan bantuan Large Language Model (LLM).

## 2. Knowledge Base

Sistem menggunakan dataset FAQ e-commerce yang disediakan oleh mentor sebagai sumber informasi utama. Dataset asli disimpan di dalam direktori `data/` dan digunakan sebagai basis pengetahuan untuk proses pencarian serta pembuatan jawaban.

## 3. Technology Stack

Teknologi dan library yang digunakan dalam pengembangan sistem meliputi:

- **Python** — bahasa pemrograman utama.
- **Pandas dan NumPy** — untuk pemrosesan dan manipulasi data.
- **Gemini Embeddings API** — untuk mengubah teks FAQ menjadi representasi vektor numerik.
- **FAISS** — untuk menyimpan indeks vektor dan melakukan pencarian kemiripan secara efisien.
- **Gemini API** — untuk menghasilkan jawaban berdasarkan pertanyaan pengguna dan konteks FAQ yang ditemukan.

## 4. System Workflow

Sistem bekerja melalui beberapa tahapan berikut:

1. **Ingest:** Membaca dan memuat dataset FAQ dari direktori `data/`.
2. **Embed:** Menghasilkan embedding dari teks pertanyaan dan jawaban FAQ menggunakan Gemini Embeddings API.
3. **Store:** Menyimpan dan mengindeks embedding menggunakan FAISS agar dapat dicari berdasarkan kemiripan vektor.
4. **Retrieve:** Mencari sejumlah FAQ yang paling relevan dengan pertanyaan pengguna melalui semantic search.
5. **Generate:** Menggunakan Gemini API untuk menyusun jawaban berdasarkan pertanyaan pengguna dan hasil pencarian FAQ yang relevan.

## 5. How to Run

Untuk menjalankan proyek ini, ikuti langkah-langkah berikut:

1. Buat virtual environment Python.
2. Instal seluruh dependensi yang tercantum dalam `requirements.txt`.
3. Siapkan API key Gemini melalui variabel lingkungan `GEMINI_API_KEY` di file `.env`.
4. Buka notebook proyek dan jalankan seluruh cell secara berurutan, mulai dari pemuatan dataset hingga pengujian sistem.

Pastikan API key telah dikonfigurasi dengan benar dan seluruh dependensi berhasil diinstal sebelum menjalankan notebook.

## 6. Evaluation

Evaluasi dilakukan menggunakan minimal lima skenario pengujian yang mencakup:

- Pertanyaan langsung yang sesuai dengan FAQ.
- Pertanyaan dengan struktur kalimat berbeda atau parafrase.
- Pertanyaan yang menggunakan sinonim.
- Pertanyaan yang membutuhkan pencarian informasi relevan berdasarkan konteks.
- Pertanyaan di luar cakupan informasi yang tersedia dalam knowledge base.

Hasil pengujian dan analisis performa retrieval didokumentasikan dalam file `documentation/retrieval_test_results.md`.

## 7. Limitations

Prototipe ini memiliki beberapa keterbatasan yang perlu diperhatikan:

- Kualitas jawaban sangat bergantung pada kelengkapan, relevansi, dan kualitas data FAQ.
- Proses semantic search dapat mengambil dokumen yang kurang relevan terhadap pertanyaan pengguna.
- LLM berpotensi menghasilkan informasi yang tidak sepenuhnya akurat meskipun telah diberikan konteks FAQ.
- Sistem belum tentu dapat menjawab pertanyaan yang informasinya tidak tersedia dalam knowledge base.
- Hasil pencarian dan jawaban yang dihasilkan masih perlu dievaluasi untuk memastikan relevansi serta konsistensinya.

Oleh karena itu, hasil dari prototipe ini sebaiknya diperlakukan sebagai bantuan informasi customer service, bukan sebagai jaminan bahwa setiap jawaban selalu benar.
