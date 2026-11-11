# PayPulsa Admin — Sandbox

Panel admin statis untuk Cloudflare Pages. File utama: `admin/index.html`.

## Konfigurasi
- Worker API Sandbox: `https://paypulsa-api-sandbox.shanowellexcel.workers.dev`
- Endpoint daftar pesanan: `GET /api/admin/orders`
- Endpoint riwayat payout: `GET /api/admin/payouts`
- Endpoint catat payout: `POST /api/admin/payout/:id`
- Origin admin: `https://paypulsa-admin.pages.dev`

## Cara pakai
1. Deploy folder `admin/` sebagai project Pages terpisah dengan hostname `paypulsa-admin.pages.dev`.
2. Pastikan Worker Sandbox mengizinkan CORS dari origin admin dan tetap mengizinkan frontend Sandbox.
3. Pastikan seluruh endpoint admin memakai autentikasi `Authorization: Bearer <ADMIN_API_TOKEN>`.
4. Buka halaman dan masukkan token Sandbox. Token hanya disimpan di memori halaman dan hilang saat reload/keluar.
5. Verifikasi data transaksi dan rekening tujuan sebelum mengonfirmasi payout.

## Penting
- Halaman ini menunjuk Sandbox saja. Jangan ubah API_BASE ke Worker Live.
- Tombol konfirmasi hanya memanggil endpoint untuk mencatat payout SUCCESS. Admin harus melakukan transfer dana secara terpisah dan hanya menekan tombol setelah transfer benar-benar selesai.
- Frontend ini mengakomodasi beberapa nama field respons umum, tetapi bentuk JSON final tetap harus dicocokkan dengan Worker sebelum pengujian integrasi.
- Tidak ada kredensial yang ditanam di source code.
- Jangan commit token admin ke GitHub.
