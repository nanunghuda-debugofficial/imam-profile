# SOP Otomasi Bisnis & Integrasi AI Agent — Kelas Mentor

> Berdasarkan catatan Kopdar KPMI Solo + contexto Kelas Mentor
> Versi: 1.0 | Tanggal: 2026-06-23

---

## 1. VISI SISTEM

**Tujuan:** Dari lead masuk sampai produk dikirim, semua alur bisa dipantau dan diotomasi oleh AI Agent.

```
Lead Masuk → Profiling → Follow Up → Closing → Order → Produksi → Kirim → Resi → Feedback
     ↑                                                                              ↓
     └────────────────────── AI Agent Pantau & Ingatkan ───────────────────────────┘
```

**Prinsip:**
- Setiap pekerjaan yang alurnya jelas → bisa diotomasi
- Keputusan penting (refund, budget besar, pesan massal) → tetap perlu persetujuan manusia
- Data rapi + SOP jelas = AI bekerja maksimal

---

## 2. ALUR UTAMA: DARI IKLAN SAMPAE BARANG DIKIRIM

### 2.1 Tahap 1 — Lead Masuk

| Trigger | AI Agent Action |
|---------|-----------------|
| Calon chat via WA (0812-9665-6851) | Balas otomatis, tanya kebutuhan, kirim link landing page |
| Calon isi form di landing page | Catat data (nama, WA, minat produk), kirim notifikasi ke Mas Imam |
| Calan klik iklan & landing di web | Trigger WA follow-up otomatis via webhook |

**Script Balas Awal (WA):**
```
Halo [Nama]! 👋 Terima kasih sudah menghubungi Kelas Mentor.

Saya bisa bantu informasi tentang:
1. Kelas Mentor — program & harga
2. Produk digital — template & tools
3. Konsultasi bisnis — jadwal & detail

Mau tanya yang mana dulu?
```

---

### 2.2 Tahap 2 — Profiling & Kualifikasi

AI Agent menilai apakah lead itu:
- **Cold** — baru tanya-tanya, belum siap beli
- **Warm** — sudah minta detail harga/paket
- **Hot** — sudah siap bayar, cuma butuh link pembayaran

| Tanda | Status | Action |
|-------|--------|--------|
| Tanya Produk aja | Cold | Kirim info produk + testimoni |
| Tanya harga & paket | Warm | Kirim detail paket + bandingkan |
| Minta link bayar | Hot | Kirim payment link + instruksi |

**Data yang dicatat:**
- Nama
- Nomor WA
- Produk yang diminat
- Status (cold/warm/hot)
- Terakhir interaksi
- Follow-up ke berapa

---

### 2.3 Tahap 3 — Follow-Up Sequence

**Timeline follow-up untuk lead yang belum closing:**

| Hari | Action | Channel |
|------|--------|---------|
| 0 (saat chat) | Balas pertanyaan + info produk | WA |
| 2 | Cek status → kirim testimoni/social proof | WA |
| 5 | Kirim penawaran spesial / diskon terbatas | WA |
| 7 | Follow up terakhir — "Masih tertarik?" | WA |
| 14 |Masuk ke nurturing — kirim konten/edukasi | Telegram/WA |
| 30 | Re-engagement — promo baru / produk baru | WA |

**Contoh pesan follow-up Hari 2:**
```
Halo [Nama]! Masih ingat soal [produk yang diminat]?

Kita punya testimoni baru dari [klien] yang berhasil [hasil spesifik].

Mau lihat detail lengkapnya? Saya kirim link-nya 👇
```

**Contoh pesan follow-up Hari 5 (penawaran):**
```
[Nama], kita ada promo spesial minggu ini buat [produk]:
- Harga normal: Rp X
- Promo: Rp Y (hemat Rp Z)
- Berlaku sampai [tanggal]

Mau ambil kesempatan ini? 😊
```

---

### 2.4 Tahap 4 — Closing & Pembayaran

| Step | Action |
|------|--------|
| 1. Kirim link payment (BSI 7190166168 / payment gateway) | AI Agent / Admin |
| 2. Konfirmasi pembayaran masuk | Manual cek |
| 3. Kirim bukti pembayaran + akses produk | AI Agent |
| 4. Catat status: PAID | AI Agent |

**Script setelah pembayaran:**
```
Terima kasih [Nama]! Pembayaran sudah dikonfirmasi ✅

Akses Kelas Mentor:
🔗 [link kelas]
📧 [kalau ada email]

Kalau ada pertanyaan, hubungi saya kapan saja di 0812-9665-6851.
```

---

### 2.5 Tahap 5 — Pengiriman & Resi (kalau produk fisik)

| Step | PIC | Notifikasi ke Pelanggan |
|------|-----|------------------------|
| 1. Order masuk ke tim packing | Admin | Otomatis via WA |
| 2. Barang dikirim + input resi | Packing | Kirim ke AI Agent |
| 3. AI Agent kirim resi ke pelanggan | AI Agent | WA: "Barang dikirim, resi: XXX" |
| 4. Cek status pengiriman H+3 | AI Agent | WA: "Barang sudah sampai belum?" |

---

### 2.6 Tahap 6 — Feedback & Retensi

| Trigger | Action |
|---------|--------|
| 7 hari setelah barang diterima | Kirim pesan minta feedback |
| Rating bagi ≥ 4 | Minta testimoni video/tulis |
| Rating < 3 | Mas Imam notifikasi manual |
| 30 hari setelah beli | Cross-sell produk lain |

---

## 3. ROLE AI AGENT DALAM SISTEM

### 3.1 AI Agent Melakukan:

- ✅ **Balas chat awal** — pertanyaan umum tentang produk, harga, cara order
- ✅ **Catat & profiling lead** — simpan data CRM, update status
- ✅ **Follow-up otomatis** — berdasarkan sequence & timing
- ✅ **Kirim pesan internal** — "Ada order baru dari [nama], tolong diproses"
- ✅ **Monitor order** — ingatkan packing/admin kalau ada order belum diproses
- ✅ **Kirim resi** — forward resi dari tim packing ke pelanggan
- ✅ **Buat laporan** — rekap mingguan: lead masuk, conversion, revenue

### 3.2 AI Agent TIDAK Melakukan (Perlu Manusia):

- ❌ Transfer dana / kelola keuangan besar
- ❌ Ubah harga / beri diskon besar
- ❌ Kirim pesan massal tanpa review
- ❌ Keputusan strategis bisnis
- ❌ Handle komplain escalation tinggi

---

## 4. SKENARIO PESAN INTERNAL AI AGENT

Ketika ada event penting, AI Agent kirim notifikasi ke Mas Imam/Admin:

| Event | Pesan Internal |
|-------|---------------|
| Order baru | "🆕 Order baru: [Nama], [Produk], Rp [Jumlah]. Tolong cek pembayaran." |
| Order belum diproses (H+1) | "⚠️ Order [Nama] belum diproses. Sudah 1 hari sejak pembayaran." |
| Stok menipis | "📦 Stok [Produk] tinggal [X] pcs. Restock diperlukan." |
| Lead hot tidak difollow | "🔥 Lead [Nama] status HOT sudah 3 hari tidak di-follow up." |
| Komplain masuk | "😟 Komplain dari [Nama]: [Detail]. Perlu penanganan manual." |
| Mingguan | "📊 Laporan Minggu [X]: [Y] lead masuk, [Z] closing, Rp [total] revenue." |

---

## 5. TOOLS & INTEGRASI

### 5.1 Channel yang Terhubung:

| Channel | Fungsi |
|---------|--------|
| **WhatsApp (0812-9665-6851)** | CS utama, follow-up, konfirmasi order |
| **Landing Page** | Entry point, capture lead, redirect ke WA |
| **Telegram** | Konten edukasi, nurturing, komunitas |
| **Notion** | Database CRM, tracker order, SOP |
| **Meta Ads** | Akuisisi lead (redirect ke WA/LP) |
| **Google Ads** | Akuisisi lead (redirect ke LP) |

### 5.2 Alur Data:

```
Meta/Google Ads → Landing Page (capture name+WA) → AI Agent chat
                                               → Notion CRM (log)
                                               → WA follow-up sequence
                                               → Order → Payment → Fulfillment
                                               → Feedback → Testimoni
```

---

## 6. PENERAPAN BERTAHAP

### Phase 1 — Foundation (Minggu 1-2)
1. Setup landing page dengan form → WA redirect ✅ (sudah)
2. Buat database lead sederhana (Notion/Google Sheets)
3. Script balas awal WA untuk pertanyaan umum

### Phase 2 — Automation (Minggu 3-4)
1. Setup follow-up sequence otomatis (H+2, H+5, H+7, H+14, H+30)
2. Buat dashboard tracker order
3. Integrasi notifikasi internal ke Mas Imam

### Phase 3 — AI Agent Full (Bulan 2)
1. AI baca data iklan → rekomendasi optimasi
2. AI pantau workflow → ingatkan yang telat
3. AI buat laporan mingguan otomatis
4. Prospecting: AI cari calon klien di Google Maps → buat penawaran

---

## 7. KPI & MONITORING

| Metrik | Target |
|--------|--------|
| Response time chat | < 10 menit (AI Agent) |
| Lead-to-chat conversion | > 30% (yang landing di LP → chat WA) |
| Chat-to-order conversion | > 15% |
| Follow-up effectiveness | > 20% closing dari follow-up sequence |
| Order fulfillment time | < 2 hari setelah pembayaran |
| Customer satisfaction | > 4.5/5 |

---

_Dokumen ini hidup — akan diupdate seiring implementasi berjalan._
_By: Kelas Mentor AI Agent System_
