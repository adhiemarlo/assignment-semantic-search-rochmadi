# Semantic Search Retrieval Test Results

## 1. Overview

Pengujian ini dilakukan untuk mengevaluasi performa prototipe asisten customer service e-commerce yang menggabungkan semantic search menggunakan FAISS dan pembuatan jawaban menggunakan Gemini API.

Evaluasi mencakup pertanyaan langsung, parafrase, pertanyaan mengenai barang rusak, serta pertanyaan di luar cakupan knowledge base.

## 2. Test Results

### Test Case 1 — Pertanyaan Langsung tentang Pengiriman

**Query:**

> Pengiriman,Berapa lama estimasi waktu pengiriman barang?

**Generated Answer:**

> Halo! Estimasi waktu pengiriman barang umumnya adalah 2-5 hari kerja untuk area dalam kota dan 5-10 hari kerja untuk luar pulau, tergantung pada jasa kirim yang Anda pilih.
>
> Semoga informasi ini membantu! Jika ada pertanyaan lain, jangan ragu untuk bertanya kembali, ya.

**Top Retrieved FAQ:**

> Berapa lama estimasi waktu pengiriman barang?

**Analysis:**

Sistem berhasil menemukan FAQ yang sesuai dengan pertanyaan pengguna. Hasil ini menunjukkan bahwa semantic search mampu mengambil informasi yang relevan untuk pertanyaan langsung dengan kemiripan tinggi terhadap data FAQ.

**Status:** Berhasil.

---

### Test Case 2 — Pertanyaan tentang Status Pembayaran

**Query:**

> Pembayaran,Kenapa pembayaran saya berhasil dipotong tapi status pesanan masih belum terbayar?

**Generated Answer:**

> Halo! Hal ini biasanya terjadi karena adanya keterlambatan sinkronisasi pada sistem pembayaran.
>
> Mohon kesediaannya untuk menunggu sekitar 15-30 menit. Namun, jika status pesanan masih belum berubah setelah kurun waktu tersebut, silakan hubungi customer service kami agar dapat dibantu pengecekan lebih lanjut, ya.

**Top Retrieved FAQ:**

> Kenapa pembayaran saya berhasil dipotong tapi status pesanan masih belum terbayar?

**Analysis:**

Sistem berhasil menemukan FAQ yang sesuai dengan inti permasalahan pengguna. Jawaban yang dihasilkan memberikan penjelasan mengenai kemungkinan keterlambatan sinkronisasi dan langkah tindak lanjut.

**Status:** Berhasil.

---

### Test Case 3 — Parafrase Pertanyaan Pembatalan Pesanan

**Query:**

> Saya berubah pikiran setelah checkout, masih bisakah pesanan dibatalkan?

**Generated Answer:**

> Halo! Tentu bisa, Anda masih dapat membatalkan pesanan melalui halaman 'Pesanan Saya' selama status pesanan masih 'Diproses'.
>
> Namun, mohon diperhatikan bahwa jika status pesanan sudah berubah menjadi 'Dikirim', pembatalan sudah tidak dapat dilakukan lagi.
>
> Semoga informasi ini membantu! Jika ada hal lain yang ingin ditanyakan, silakan beri tahu saya.

**Top Retrieved FAQ:**

> Bagaimana cara membatalkan pesanan yang sudah dibuat?

**Analysis:**

Meskipun menggunakan susunan kalimat yang berbeda dari FAQ asli, sistem berhasil menemukan pertanyaan dengan maksud yang sama. Hasil ini menunjukkan kemampuan semantic search dalam menangani parafrase, bukan hanya pencocokan kata secara persis.

**Status:** Berhasil.

---

### Test Case 4 — Parafrase Pertanyaan tentang Barang Rusak

**Query:**

> Paket baru datang, tetapi barang di dalamnya pecah. Bagaimana solusinya?

**Generated Answer:**

> Halo! Mohon maaf atas ketidaknyamanan yang dialami.
>
> Jika barang diterima dalam kondisi rusak/pecah, silakan segera ambil foto atau video kondisi paket saat diterima, lalu laporkan melalui menu komplain dalam waktu 2x24 jam sejak barang diterima.
>
> Semoga masalahnya lekas terselesaikan! Jika ada hal lain yang perlu ditanyakan, jangan ragu untuk memberi tahu saya.

**Top Retrieved FAQ:**

> Apa yang harus dilakukan jika paket diterima dalam kondisi rusak?

**Analysis:**

Sistem berhasil mengidentifikasi hubungan makna antara kata "barang pecah" pada query dan "paket diterima dalam kondisi rusak" pada FAQ. Jawaban yang dihasilkan juga menyampaikan langkah penanganan yang relevan dengan permasalahan pengguna.

**Status:** Berhasil.

---

### Test Case 5 — Pertanyaan di Luar Knowledge Base

**Query:**

> Apakah tersedia layanan pembayaran menggunakan cryptocurrency?

**Generated Answer:**

> Halo! Mohon maaf, saat ini saya belum memiliki informasi terkait layanan pembayaran menggunakan cryptocurrency.
>
> Metode pembayaran yang saat ini kami dukung adalah transfer bank, kartu kredit/debit, e-wallet, dan pembayaran melalui minimarket rekanan.
>
> Untuk informasi lebih lanjut mengenai hal tersebut, kami sarankan untuk langsung menghubungi tim customer service kami, ya. Terima kasih!

**Top Retrieved FAQ:**

> Metode pembayaran apa saja yang tersedia?

**Analysis:**

Sistem mengambil FAQ mengenai metode pembayaran karena memiliki keterkaitan topik dengan query. Jawaban menyatakan bahwa informasi spesifik mengenai cryptocurrency belum tersedia dan menyarankan pengguna menghubungi customer service.

Pendekatan ini cukup baik dalam menangani pertanyaan di luar cakupan knowledge base. Namun, daftar metode pembayaran yang disebutkan dalam jawaban tetap harus diverifikasi terhadap FAQ sumber untuk memastikan tidak ada informasi tambahan yang dibuat oleh LLM.

**Status:** Berhasil dengan catatan validasi jawaban.

---

## 3. Summary of Evaluation

| No. | Test Scenario | Retrieval Result | Evaluation |
|---|---|---|---|
| 1 | Pertanyaan langsung tentang pengiriman | FAQ sesuai | Berhasil |
| 2 | Pertanyaan tentang status pembayaran | FAQ sesuai | Berhasil |
| 3 | Parafrase pembatalan pesanan | FAQ relevan ditemukan | Berhasil |
| 4 | Parafrase barang rusak | FAQ relevan ditemukan | Berhasil |
| 5 | Pertanyaan cryptocurrency | FAQ terkait pembayaran ditemukan | Berhasil dengan catatan |

Berdasarkan lima skenario pengujian, seluruh query menghasilkan sumber FAQ yang berkaitan dengan kebutuhan informasi pengguna. Empat query pertama berhasil mengambil FAQ yang sesuai secara langsung atau berdasarkan kemiripan makna, sedangkan query kelima mengambil FAQ terkait pembayaran meskipun pertanyaan spesifik mengenai cryptocurrency belum terjawab oleh knowledge base.

## 4. Key Findings

Beberapa temuan utama dari pengujian ini adalah:

1. **Pencarian berdasarkan makna:** Semantic search mampu menemukan FAQ yang relevan meskipun query tidak selalu menggunakan susunan kalimat yang sama dengan pertanyaan dalam dataset.
2. **Penanganan parafrase:** Pertanyaan tentang pembatalan pesanan dan barang rusak tetap menghasilkan sumber FAQ yang sesuai meskipun disampaikan dengan bahasa berbeda.
3. **Integrasi retrieval dan generation:** Gemini API dapat menggunakan hasil pencarian sebagai konteks untuk menyusun jawaban yang lebih alami dan mudah dipahami.
4. **Pertanyaan di luar knowledge base:** Sistem dapat menemukan FAQ dengan topik berdekatan dan menghasilkan respons yang mengakui keterbatasan informasi.
5. **Pentingnya validasi jawaban:** Jawaban LLM perlu diperiksa terhadap sumber FAQ untuk mengurangi risiko informasi yang tidak didukung oleh knowledge base.

## 5. Limitations and Recommendations

Pengujian ini masih bersifat kualitatif dan menggunakan lima query. Hasilnya belum cukup untuk menyimpulkan akurasi sistem secara menyeluruh.

Pengembangan selanjutnya dapat mencakup:

- Membandingkan hasil retrieval dengan ID FAQ yang diharapkan untuk setiap query.
- Mengukur metrik retrieval seperti Precision@K, Recall@K, dan Mean Reciprocal Rank (MRR).
- Menambahkan ambang batas relevansi agar sistem dapat mengenali query yang tidak memiliki sumber yang cukup relevan.
- Memastikan jawaban LLM hanya menggunakan fakta yang didukung oleh FAQ yang ditemukan.
- Memperluas pengujian dengan variasi sinonim, parafrase, typo, dan pertanyaan di luar cakupan knowledge base.

## 6. Conclusion

Berdasarkan pengujian awal, prototipe semantic search customer service e-commerce mampu mengambil FAQ yang relevan untuk pertanyaan langsung maupun parafrase. Integrasi dengan Gemini API juga membantu menyajikan informasi dalam bentuk jawaban yang lebih natural.

Untuk pertanyaan di luar knowledge base, sistem menunjukkan respons yang mengakui keterbatasan informasi, tetapi tetap memerlukan validasi agar informasi tambahan yang diberikan tidak melampaui sumber FAQ. Dengan pengujian kuantitatif dan pengendalian relevansi yang lebih baik, sistem dapat dikembangkan menjadi asisten customer service yang lebih andal.
