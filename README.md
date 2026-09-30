# Wibe Studio - Cloud Full-Stack Deployment (Final Project)

Proyek ini merupakan tugas akhir bootcamp yang mengimplementasikan otomatisasi CI/CD, kontainerisasi aplikasi web modern menggunakan Docker, serta *deployment* ke layanan cloud **GCP Cloud Run**

## 🚀 Tech Stack
* **Frontend:** React (Vite)
* **Web Server / Proxy:** Nginx (Alpine)
* **Containerization:** Docker (Multi-stage build)
* **CI/CD Pipeline:** GitHub Actions
* **Cloud Infrastructure:** Google Cloud Platform (GCP Cloud Run & Artifact Registry)

---

## 🛠️ Arsitektur & Alur CI/CD
1. **Source Code Push:** Setiap kali dilakukan `git push` ke branch `main`, GitHub Actions akan otomatis memicu *workflow* deployment[cite: 1].
2. **Docker Build:** Menggunakan *multi-stage Dockerfile*[cite: 10]:
   * **Stage 1 (Builder):** Menginstal dependensi Node.js dan melakukan kompilasi aplikasi React menggunakan Vite (`npm run build`) ke direktori output `build`.
   * **Stage 2 (Production):** Menyajikan file statis hasil *build* menggunakan web server Nginx yang ringan.
3. **Registry Upload:** Docker image yang sudah jadi di-*push* secara aman ke **Google Artifact Registry** di region `asia-southeast2`.
4. **Cloud Run Deployment:** Layanan secara otomatis memperbarui revisi aplikasi di **GCP Cloud Run** dengan *image* terbaru.

---

## 🔒 Keamanan & Monitoring
* **Secrets Management:** Kredensial sensitif seperti Service Account Key GCP disimpan dengan aman di **GitHub Secrets** (`GCP_SA_KEY`) tanpa di-*hardcode* di dalam *source code*.
* **Monitoring & Autoscaling:** Performa aplikasi dipantau secara *real-time* melalui **GCP Cloud Run Metrics** (mencakup *Request count*, *Latencies*, *Container instance count*, dan *CPU/Memory utilization*).

---

## 📋 Link Akses & Bukti Pengerjaan
* **Repository GitHub:** https://github.com/francodkz/DigitalSkola-Final
* **Pipeline CI/CD:** https://github.com/francodkz/DigitalSkola-Final/actions/runs/36524259196
* **Aplikasi Live (Cloud Run):** https://wibe-studio-app-476505133961.asia-southeast2.run.app
