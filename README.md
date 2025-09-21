# Proyek Halaman Profil Instagram dgn Tailwind CSS

Proyek ini adalah implementasi halaman profil Instagram yg responsif menggunakan framework Tailwind CSS. Tujuannya adalah untuk menampilkan tata letak yg bersih dan adaptif di berbagai ukuran layar, mulai dari mobile hingga desktop.

---

### Fitur-fitur Utama

* **Struktur Halaman**: Dibangun dgn struktur yg jelas, memisahkan konten menjadi `Header Profil`, `Bio`, `Feed Foto`, dan `Footer`.
* **Feed Foto**: Menampilkan minimal 12 foto dlm format grid yg responsif, meniru tampilan galeri Instagram.
* **Responsivitas**: Halaman ini didesain dgn pendekatan *mobile-first*, memastikan tata letak yg optimal di setiap perangkat.
* **Tombol Interaksi**: Tombol "Follow" dan "Edit Profile" disesuaikan secara dinamis, mengubah posisi dan ukurannya tergantung pada *breakpoint* layar.
* **Penggunaan Tailwind**: Semua tata letak dan *styling* utama (seperti `grid`, `flex`, `shadow`, `rounded`) menggunakan *utility classes* dri Tailwind.

---

### Jawaban Pertanyaan README.md

**1. Jelaskan keputusan `grid-cols`/`gap` di tiap breakpoint kenapa begitu?**

Saya memilih konfigurasi `grid-cols` dan `gap` yg berbeda untuk setiap ukuran layar (breakpoint) untuk memastikan halaman tetap rapi dan mudah dilihat di perangkat apa pun. Pendekatan ini adalah inti dari **desain responsif**.

* **Mobile (ukuran kecil)**: Saya menggunakan `grid-cols-1`. Tujuannya adalah agar setiap foto postingan memenuhi seluruh lebar layar. Ini membuat gambar terlihat besar dan jelas, sehingga pengguna tidak perlu memperbesar (zoom) untuk melihat detail.
* **Tablet (ukuran sedang)**: Saya memilih `md:grid-cols-3` dgn `gap-4`. Di layar tablet yg lebih lebar, tiga kolom foto dlm satu baris adalah pilihan paling logis. Ini membuat halaman terlihat lebih padat dan efisien, mirip dgn tampilan aplikasi Instagram.
* **Desktop (ukuran besar)**: Saya menggunakan `lg:grid-cols-4` atau `xl:grid-cols-6`. Di layar komputer yg sangat lebar, kita bisa menampilkan lebih banyak foto sekaligus. Ini memungkinkan pengguna melihat banyak postingan dlm satu layar tanpa perlu banyak *scroll*.

Penggunaan `gap-4` juga penting untuk memberikan jarak yg konsisten antar foto, memastikan tata letak tetap bersih dan terorganisir.

---

**2. Bagaimana kamu memanfaatkan utility responsive Tailwind untuk memecahkan masalah layout yg muncul di mobile?**

Di tampilan mobile, masalah utama adalah ruang yg terbatas. Jika semua elemen ditampilkan seperti di desktop, halaman akan terlihat berantakan. Untuk mengatasinya, saya memanfaatkan beberapa *utility classes* responsif dri Tailwind:

* **Menyembunyikan Konten**: Saya menggunakan kelas seperti `hidden md:flex` untuk menyembunyikan elemen tertentu di mobile. Sebagai contoh, statistik jumlah *posts*, *followers*, dan *following* hanya ditampilkan di desktop (`md:flex`), sementara di mobile, saya membuatnya terpisah dan lebih sederhana.
* **Mengubah Tata Letak**: Saya menggunakan `flex flex-col md:flex-row` pada *header*. Ini membuat elemen di header (foto profil, nama, dan tombol) tersusun secara vertikal di mobile (`flex-col`), lalu berubah menjadi horizontal di tablet dan desktop (`flex-row`).
* **Mengatur Posisi Tombol**: Tombol "Follow" dan "Edit Profile" memiliki posisi berbeda di mobile dan desktop menggunakan kelas `order-3 md:order-2`. Ini memastikan tombol tetap mudah dijangkau di bawah nama pengguna pada tampilan mobile, tetapi kembali ke posisi normal di desktop.

---

**3. Jelaskan *trade-off* antara memakai banyak *utility classes* vs membuat *component* CSS tersendiri.**

Ada beberapa pertimbangan saat memilih antara menggunakan banyak *utility classes* atau membuat *component* CSS tersendiri:

* **Memakai Banyak *Utility Classes***:
    * **Kelebihan**: Sangat cepat dan fleksibel. Kita bisa membuat desain unik langsung di file HTML tanpa harus bolak-balik ke file CSS. Ini cocok untuk proyek kecil atau saat kita ingin melakukan perubahan cepat.
    * **Kekurangan**: Kode HTML bisa menjadi sangat panjang dan sulit dibaca jika ada terlalu banyak kelas. Jika kita perlu mengubah satu gaya (misalnya, warna tombol), kita harus mengubahnya di semua tempat di mana tombol itu digunakan, yg bisa menjadi tidak efisien.

* **Membuat *Component* CSS Tersendiri**:
    * **Kelebihan**: Kode HTML tetap bersih dan mudah dibaca (`<button class="btn-primary">`). Kita bisa mengelola semua gaya di satu tempat (misalnya, di file `style.css`). Jika kita ingin mengubah gaya, kita hanya perlu mengubahnya di satu tempat saja, dan perubahannya akan diterapkan di seluruh halaman.
    * **Kekurangan**: Prosesnya lebih lambat. Kita harus membuat nama kelas baru setiap kali ada gaya yg berbeda. Ini juga membuat proses pengembangan menjadi kurang fleksibel karena kita harus terus beralih antara HTML dan CSS.

**Kesimpulan**: Untuk proyek kecil seperti ini, menggunakan banyak *utility classes* adalah pilihan yg sangat efisien dan praktis. Namun, untuk proyek yg lebih besar dan kompleks, pendekatan *component* akan lebih mudah dikelola dlm jangka panjang.