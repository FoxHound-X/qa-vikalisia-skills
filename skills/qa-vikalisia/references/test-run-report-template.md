# Test Run / Execution Report Reference Template

Standard QA test execution report format for Jira comments, Confluence, Qase, and test documentation.

---

## 1. Blank Template (Standard Markdown)

```markdown
### Laporan Hasil Test Run: [Nama Fitur / Modul / Verifikasi Bug]

[Deskripsi singkat ruang lingkup pengujian, sistem/aplikasi, dan daftar Case ID yang dieksekusi]

* **Test Suite:** [Nama Suite] (Suite ID: [ID])
* **Ticket:** [Kode Tiket Utama Jira, misal: BQS-XXXX]
* **Tanggal Eksekusi:** [Tanggal, misal: DD Bulan YYYY]
* **Tipe Pengujian:** [Manual - Functional, Bug Verification, Data Validation, Regression, dll.]
* **Tester:** QA Team ([Nama QA])
* **Environment / Build:** [Staging / Production / URL / Build Version]
* **Link Test Run:** [URL Public Test Run Qase / TMS]
* **Evidence Video:** [URL Google Drive / Jam.dev / Loom] ([Catatan singkat evidence jika ada])

---

### Summary

| Metrik | Nilai |
|---|---|
| **Total Test Cases** | [Angka] |
| **Passed** | [Angka] |
| **Failed** | [Angka] |
| **Blocked / Skipped / Invalid** | [Angka] |
| **Belum selesai** | [Angka] |
| **Case dengan Retest** | [Angka, sertakan keterangan / Case ID jika ada] |
| **Total waktu eksekusi** | [Durasi dari time_spent_ms, misal: ~52 menit (3.107 detik)] |
| **Hasil Akhir** | **[PASSED (LULUS 100%) / PASSED WITH ISSUES / FAILED]** |

---

### Daftar Test Case

* **[Case ID XXX-XXXX]** [Judul test case] - **[Passed / Failed / Retest Passed]** *([Priority / Severity, misal: High / Major atau Normal])*
* **[Case ID XXX-XXXX]** [Judul test case] - **[Passed / Failed / Retest Passed]** *([Priority / Severity])*

---

### Bug yang Ditemukan

[Jika passed 100% pada feature run:
"Nihil. Tidak ada status Failed pada run ini. Seluruh alur fungsional terverifikasi valid dan sesuai dengan kriteria yang ditentukan."

Jika pada bug verification run:
"Nihil. Tidak ada status Failed pada run ini. Bug yang sebelumnya terjadi—di mana [jelaskan issue awal]—telah berhasil diperbaiki oleh developer dan terverifikasi valid ([jelaskan perilaku baru yang benar])."

Jika ada bug baru yang ditemukan:
Jelaskan ringkasan bug, Case ID yang gagal, dan link/nomor tiket bug baru yang dibuat.]

---

### Kesimpulan & Catatan

1. **[Poin Status & Pass Rate]:** [Ringkasan persentase kelulusan dan tipe/suite test case yang dieksekusi]
2. **[Poin Validasi Alur / Fix Verification]:** [Hasil uji spesifik fitur baru atau verifikasi perbaikan bug beserta dampaknya pada alur terkait (misal Night Audit / folios)]
3. **[Poin Filter / Penelusuran / Data Integrity]:** [Catatan data testing, filter search/reset, atau konsistensi antar-halaman]
4. **[Kriteria Keberterimaan & Approval]:** [Pernyataan pemenuhan Acceptance Criteria (AC) dan status rekomendasi sign-off, misal: Approved / Ready to Close]
```

---

## 2. Blank Template (Jira Wiki Markup)

*Gunakan format ini saat menulis di komentar Jira klasik/deskripsi Jira agar tabel dan heading tidak rusak.*

```jira
h3. Laporan Hasil Test Run: [Nama Fitur / Modul / Verifikasi Bug]

[Deskripsi singkat ruang lingkup pengujian, sistem/aplikasi, dan daftar Case ID yang dieksekusi]

* *Test Suite:* [Nama Suite] (Suite ID: [ID])
* *Ticket:* [Kode Tiket Utama Jira, misal: BQS-XXXX]
* *Tanggal Eksekusi:* [Tanggal]
* *Tipe Pengujian:* [Manual - Functional, Bug Verification, Data Validation, Regression, dll.]
* *Tester:* QA Team ([Nama QA])
* *Environment / Build:* [Staging / Production / URL / Build Version]
* *Link Test Run:* [URL Public Test Run Qase / TMS]
* *Evidence Video:* [URL Google Drive / Jam.dev / Loom] ([Catatan singkat evidence jika ada])

----

h3. Summary

||Metrik||Nilai||
|Total Test Cases|[Angka]|
|Passed|[Angka]|
|Failed|[Angka]|
|Blocked / Skipped / Invalid|[Angka]|
|Belum selesai|[Angka]|
|Case dengan Retest|[Angka / Keterangan]|
|Total waktu eksekusi|[Durasi, misal: ~52 menit (3.107 detik)]|
|Hasil Akhir|*PASSED (LULUS 100%)*|

----

h3. Daftar Test Case

* *[Case ID XXX-XXXX]* [Judul test case] - *Passed* _(Priority / Severity)_
* *[Case ID XXX-XXXX]* [Judul test case] - *Passed* _(Priority / Severity, lulus verifikasi bug)_

----

h3. Bug yang Ditemukan

[Keterangan bug atau konfirmasi nihil jika passed 100%]

----

h3. Kesimpulan & Catatan

# [Poin 1: Pass Rate & Tipe Test Case]
# [Poin 2: Hasil Verifikasi Fitur / Bug Fix]
# [Poin 3: Alur Operasional / Regresi Terkait]
# [Poin 4: Pemenuhan AC & Status Approval]
```

---

## 3. Concrete Example A: Feature / Full Execution Run (Jira Wiki Markup)

```jira
h3. Laporan Hasil Test Run: PMS Room Maintenance Log — Tracking Perubahan Status Kamar

Pengujian ini mencakup validasi fungsional Room Maintenance dan integrasi audit Change Log pada sistem PMS Lite berdasarkan daftar Case ID yang dieksekusi:
PMS-210; PMS-214; PMS-215; PMS-1232; PMS-696; PMS-700; PMS-701; PMS-702; PMS-707; PMS-711; PMS-712; PMS-713

* *Test Suite:* Room Maintenance (Suite ID: 28) & Change Log (Suite ID: 66)
* *Ticket:* BQS-1877
* *Tanggal Eksekusi:* 04 November 2026
* *Tipe Pengujian:* Manual - Functional, Data Validation, & Regression
* *Tester:* QA Team (Kadek Setia Dharma)
* *Environment / Build:* Staging (pms-staging.omnihotelier.net)
* *Link Test Run:* https://app.qase.io/project/PMS
* *Evidence Video:* [Link Google Drive / Jam.dev] (Tersedia rekaman validasi alur Room Maintenance ke Change Log)

----

h3. Summary

||Metrik||Nilai||
|Total Test Cases|12|
|Passed|12|
|Failed|0|
|Blocked / Skipped / Invalid|0|
|Belum selesai|0|
|Case dengan Retest|0|
|Total waktu eksekusi|~52 menit (3.107 detik)|
|Hasil Akhir|*PASSED (LULUS 100%)*|

----

h3. Daftar Test Case

* *[Case ID PMS-210]* Verify Room Maintenance List is Displayed - *Passed* _(Normal)_
* *[Case ID PMS-214]* Verify Add New Button - *Passed* _(Normal)_
* *[Case ID PMS-215]* Verify Edit Button - *Passed* _(Normal)_
* *[Case ID PMS-1232]* Verify Room Maintenance Log - *Passed* _(Normal)_
* *[Case ID PMS-696]* Verify Change Log Is Created When Reservation Is Cancelled - *Passed* _(High / Major)_
* *[Case ID PMS-700]* Verify Search Change Log by Property - *Passed* _(High / Normal)_
* *[Case ID PMS-701]* Verify Search Change Log by User - *Passed* _(High / Normal)_
* *[Case ID PMS-702]* Verify Search Change Log with "All Users" - *Passed* _(Medium / Normal)_
* *[Case ID PMS-707]* Verify Search Change Log by Date - *Passed* _(High / Normal)_
* *[Case ID PMS-711]* Verify Search Button Executes Search - *Passed* _(High / Normal)_
* *[Case ID PMS-712]* Verify Reset Button Clears All Search Filters - *Passed* _(High / Normal)_
* *[Case ID PMS-713]* Verify Change Log Results After Reset - *Passed* _(High / Major)_

----

h3. Bug yang Ditemukan

Nihil. Tidak ada status Failed pada run ini. Seluruh alur Room Maintenance dan Change Log terverifikasi valid dan sesuai dengan kriteria yang ditentukan.

----

h3. Kesimpulan & Catatan

# Seluruh 12 test case pada Suite Room Maintenance (Suite ID: 28) dan Change Log (Suite ID: 66) berhasil dieksekusi dengan status Passed (100% Pass Rate).
# Verifikasi pencatatan log (PMS-1232) mengonfirmasi bahwa alur setup hingga release Room Maintenance berhasil tercatat pada menu System > Change Log secara konsisten beserta rincian pelaku dan waktunya.
# Fitur pencarian dan filter Change Log berdasarkan Property, User, Rentang Tanggal, serta tombol Reset berfungsi normal tanpa anomali data.
# Acceptance Criteria terkait tracking perubahan status kamar dan integrasi log maintenance telah terpenuhi secara utuh. Status: *Approved*.
```

---

## 4. Concrete Example B: Bug Verification Run (Jira Wiki Markup)

```jira
h3. Laporan Hasil Test Run: Verifikasi Bug PMS Unallocated Reservation

Pengujian ini mencakup verifikasi perbaikan bug reservasi berstatus Unallocated (Release/Cancel via Room Charting) serta validasi pembuatan reservasi pada sistem PMS Lite berdasarkan daftar Case ID yang dieksekusi:
PMS-1233; PMS-1234

* *Test Suite:* Create booking (Suite ID: 48)
* *Ticket:* BQS-1880
* *Tanggal Eksekusi:* 04 November 2026
* *Tipe Pengujian:* Manual - Bug Verification, Functional, & Night Audit Cycle
* *Tester:* QA Team (Kadek Setia Dharma)
* *Environment / Build:* Staging (pms-staging.omnihotelier.net)
* *Link Test Run:* https://app.qase.io/project/PMS
* *Evidence Video:* https://drive.google.com/drive/folders/16TqNaqblrJmmnJQ_n1JToLel6cUJqLss?usp=sharing (Rekaman verifikasi reservasi released/unallocated tidak membuat folio atau auto check-in saat Night Audit)

----

h3. Summary

||Metrik||Nilai||
|Total Test Cases|2|
|Passed|2|
|Failed|0|
|Blocked / Skipped / Invalid|0|
|Belum selesai|0|
|Case dengan Retest|1 (PMS-1233, verifikasi fix bug)|
|Total waktu eksekusi|~13 menit (772.062 ms)|
|Hasil Akhir|*PASSED (LULUS 100%)*|

----

h3. Daftar Test Case

* *[Case ID PMS-1233]* Verify released/cancelled reservations via Room Charting don't create folios or check in - *Passed* _(Normal, lulus verifikasi bug)_
* *[Case ID PMS-1234]* Verify Create Reservation/Booking - *Passed* _(Medium / Normal)_

----

h3. Bug yang Ditemukan

Nihil. Tidak ada status Failed pada run ini. Bug yang sebelumnya terjadi—di mana reservasi yang di-release/cancel (Unallocated) masih membuat folio dan otomatis ter-check-in saat Night Audit melewati tanggal reservasi—telah berhasil diperbaiki oleh developer dan terverifikasi valid (tidak terbentuk folio dan tidak terjadi check-in).

----

h3. Kesimpulan & Catatan

# Seluruh 2 test case pada Suite Create booking (Suite ID: 48) berhasil dieksekusi dengan status Passed (100% Pass Rate).
# Hasil Verifikasi Bug (PMS-1233): Pengujian siklus Night Audit melewati tanggal reservasi yang di-release/cancel membuktikan bahwa sistem tidak lagi membuat folio tagihan baru maupun melakukan auto check-in pada kamar/reservasi tersebut.
# Alur Pembuatan Reservasi (PMS-1234): Pembuatan reservasi baru melalui halaman Create Booking tetap berjalan normal dan muncul sesuai jadwal pada Room Charting.
# Kriteria Keberterimaan & Evidence: Perilaku sistem sudah sesuai dengan expected behavior dan didukung rekaman pengujian lengkap pada Google Drive folder. Status: *Approved / Ready to Close*.
```
