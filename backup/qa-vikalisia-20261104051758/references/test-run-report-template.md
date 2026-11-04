# Test Run / Execution Report Reference Template

Standard QA test execution report format for Jira comments, Confluence, Qase, and test documentation.

---

## 1. Blank Template (Standard Markdown)

```markdown
### Laporan Hasil Test Run: [Nama Fitur / Modul / Versi]

[Deskripsi singkat ruang lingkup pengujian, sistem/aplikasi, dan daftar Case ID yang dieksekusi]

* **Test Suite:** [Nama Suite] (Suite ID: [ID])
* **Ticket:** [Kode Tiket Utama Jira, misal: BQS-XXXX] (terkait [Tiket Terkait, misal: OP-XXXX])
* **Tanggal Eksekusi:** [Tanggal, misal: DD Bulan YYYY]
* **Tipe Pengujian:** [Manual / Automation - Functional, Data Validation, RBAC, Regression, dll.]
* **Tester:** QA Team ([Nama QA])
* **Environment / Build:** [Staging / Production / URL / Build Hash / Asset Version]
* **Link Test Run:** [URL Public Test Run Qase / TMS]
* **Evidence Video:** [URL Video / Loom / Jam.dev] ([Catatan singkat evidence jika ada])

---

### Summary

| Metrik | Nilai |
|---|---|
| **Total Test Cases** | [Angka] |
| **Passed** | [Angka] |
| **Failed** | [Angka] |
| **Blocked / Skipped / Invalid** | [Angka] |
| **Belum selesai** | [Angka] |
| **Case dengan Retest** | [Angka, sertakan Case ID jika ada] |
| **Total waktu eksekusi** | [Estimasi durasi, misal: ~45 menit] |
| **Hasil Akhir** | **[PASSED (LULUS 100%) / PASSED WITH ISSUES / FAILED]** |

---

### Daftar Test Case

* **[Case ID XXX-XXXX]** [Judul test case] - **[Passed / Failed / Retest Passed]** *([Severity / Priority, misal: high / major])*
* **[Case ID XXX-XXXX]** [Judul test case] - **[Passed / Failed / Retest Passed]** *([Severity / Priority])*

---

### Bug yang Ditemukan

[Jelaskan bug baru yang ditemukan jika ada. Jika tidak ada bug / status passed 100%, tulis:
"Nihil. Tidak ada status Failed pada run ini. Seluruh temuan perbaikan sebelumnya ([sebutkan perbaikan]) telah diselesaikan dan terverifikasi valid."]

---

### Kesimpulan & Catatan

1. **[Poin Status & Pass Rate]:** [Ringkasan persentase kelulusan dan tipe test case (Gherkin/klasik)]
2. **[Poin Validasi / Test Data]:** [Catatan data testing, dinamis/properti-agnostik]
3. **[Poin Retest (jika ada)]:** [Penjelasan verifikasi ulang case yang sebelumnya gagal]
4. **[Kriteria Keberterimaan]:** [Pernyataan pemenuhan AC (Acceptance Criteria) dan status Approval]
```

---

## 2. Concrete Example (Standard Markdown)

### Laporan Hasil Test Run: PMS Dashboard V2

Pengujian ini mencakup validasi fungsional PMS Dashboard V2 pada sistem PMS Lite berdasarkan judul case dan suite yang dieksekusi:
`PMS-1120`, `PMS-1121`, `PMS-1122`, `PMS-1123`, `PMS-1124`, `PMS-1125`, `PMS-1126`, `PMS-1127`, `PMS-1128`, `PMS-1129`, `PMS-1130`, `PMS-1131`, `PMS-1132`, `PMS-1141`, `PMS-1142`.

* **Test Suite:** Dashboard V2 (Suite ID: 94)
* **Ticket:** BQS-1823 (terkait OP-1532)
* **Tanggal Eksekusi:** 20 Oktober 2026
* **Tipe Pengujian:** Manual - Functional, Data Validation, & RBAC
* **Tester:** QA Team (Dio Mahardika)
* **Environment / Build:** Staging (`pms-staging.omnihotelier.net` / build `assets/index-b7c0ed17.js`)
* **Link Test Run:** [Qase Test Run Report](https://app.qase.io/public/report/c5854aaf2e7df2da941391bd24c5bf34f2f5e0d7)
* **Evidence Video:** [Jam.dev Evidence](https://jam.dev/c/84a9fc78-4290-4cf7-a99e-9bde3eb6f1c7) (Bukti retest: KPI card clickable & Cancel only)

---

### Summary

| Metrik | Nilai |
|---|---|
| **Total Test Cases** | 15 |
| **Passed** | 15 |
| **Failed** | 0 |
| **Blocked / Skipped / Invalid** | 0 |
| **Belum selesai** | 0 |
| **Case dengan Retest** | 2 (PMS-1128 & PMS-1142, lulus setelah retest) |
| **Total waktu eksekusi** | ~45 menit |
| **Hasil Akhir** | **PASSED (LULUS 100%)** |

---

### Daftar Test Case

* **[Case ID PMS-1120]** Show daily operational KPI tile counts matching property reports - **Passed** *(high / major)*
* **[Case ID PMS-1121]** Show room status donut chart matching active housekeeping units - **Passed** *(high / major)*
* **[Case ID PMS-1122]** Show vacant rooms KPI count matching ready housekeeping units - **Passed** *(medium / normal)*
* **[Case ID PMS-1123]** Show room revenue by segment matching agent production report - **Passed** *(high / major)*
* **[Case ID PMS-1124]** Hide financial performance metrics for user without financial access - **Passed** *(high / critical)*
* **[Case ID PMS-1125]** Show individual guest name on group reservation row in arrivals table - **Passed** *(high / major)*
* **[Case ID PMS-1126]** Show expected departure list with folio link on table row - **Passed** *(medium / normal)*
* **[Case ID PMS-1127]** Update arrivals table balance with extra charge added to folio - **Passed** *(high / major)*
* **[Case ID PMS-1128]** Update cancelled reservation KPI tile count for cancelled booking - **Passed** *(medium / normal, lulus setelah retest)*
* **[Case ID PMS-1129]** Calculate daily performance metrics with updated label copy - **Passed** *(high / critical)*
* **[Case ID PMS-1130]** Show room monthly revenue trend line chart matching DSR nett revenue - **Passed** *(high / major)*
* **[Case ID PMS-1131]** Show guest birthday notification banner with modal for more guests - **Passed** *(medium / normal)*
* **[Case ID PMS-1132]** Show zero performance metrics without division error on zero divisor - **Passed** *(high / major)*
* **[Case ID PMS-1141]** Show night audit failure badge on failed audit run - **Passed** *(medium / normal)*
* **[Case ID PMS-1142]** Show related module page after clicking operational KPI tile - **Passed** *(medium / normal, lulus setelah retest)*

---

### Bug yang Ditemukan

Tidak ada status Failed pada run ini, sehingga tidak ada bug yang dilaporkan. Seluruh temuan perbaikan sebelumnya (nama tamu kamar grup, sinkronisasi balance folio, penyesuaian tile Cancel Only, standarisasi Gherkin, dan navigasi klik pada 7 tile KPI) telah diselesaikan oleh developer dan terverifikasi lulus.

---

### Kesimpulan & Catatan

1. Seluruh 15 test case pada Suite Dashboard V2 (Suite ID: 94) bertipe Gherkin dan berhasil dieksekusi dengan status Passed (100% Pass Rate).
2. Test data pada seluruh test case telah distandarisasi agar dinamis dan fleksibel untuk dijalankan pada properti mana pun (properti-agnostik).
3. Catatan Retest: Test case PMS-1128 (Tile Cancelled hanya menghitung status Cancel) dan PMS-1142 (7 Tile KPI atas interaktif/dapat diklik menuju modul terkait) telah terkonfirmasi lulus melalui bukti pengujian video Jam.dev (https://jam.dev/c/84a9fc78-4290-4cf7-a99e-9bde3eb6f1c7).
4. Seluruh Acceptance Criteria (AC-1 s/d AC-11) dan poin enhancement hasil grooming BOD telah terpenuhi secara utuh dan valid. Status: **Approved**.

---

## 3. Jira Wiki Markup Template (For Classic Jira Comment / Text Mode)

*Gunakan format ini saat menulis di komentar Jira klasik agar tabel dan heading tidak rusak.*

```jira
h3. Laporan Hasil Test Run: [Nama Fitur / Modul / Versi]

[Deskripsi singkat ruang lingkup pengujian, sistem/aplikasi, dan daftar Case ID yang dieksekusi]

* *Test Suite:* [Nama Suite] (Suite ID: [ID])
* *Ticket:* [Kode Tiket Utama Jira, misal: BQS-XXXX] (terkait [Tiket Terkait, misal: OP-XXXX])
* *Tanggal Eksekusi:* [Tanggal]
* *Tipe Pengujian:* [Manual / Automation - Functional, Data Validation, RBAC, dll.]
* *Tester:* QA Team ([Nama QA])
* *Environment / Build:* [Staging / URL / Build Asset]
* *Link Test Run:* [URL Public Test Run Qase]
* *Evidence Video:* [URL Jam.dev / Loom] ([Catatan singkat evidence])

----

h3. Summary

||Metrik||Nilai||
|Total Test Cases|[Angka]|
|Passed|[Angka]|
|Failed|[Angka]|
|Blocked / Skipped / Invalid|[Angka]|
|Belum selesai|[Angka]|
|Case dengan Retest|[Angka / Keterangan]|
|Total waktu eksekusi|[Estimasi durasi]|
|Hasil Akhir|*PASSED (LULUS 100%)*|

----

h3. Daftar Test Case

* *[Case ID XXX-XXXX]* [Judul test case] - *Passed* _(severity / priority)_
* *[Case ID XXX-XXXX]* [Judul test case] - *Passed* _(severity / priority, lulus setelah retest)_

----

h3. Bug yang Ditemukan

[Keterangan bug atau konfirmasi nihil jika passed 100%]

----

h3. Kesimpulan & Catatan

# [Poin 1: Pass Rate & Tipe Test Case]
# [Poin 2: Standarisasi Data]
# [Poin 3: Catatan Retest & Bukti Evidence]
# [Poin 4: Pemenuhan AC & Status Approval]
```

---

## 4. Concrete Example (Jira Wiki Markup)

```jira
h3. Laporan Hasil Test Run: PMS Dashboard V2

Pengujian ini mencakup validasi fungsional PMS Dashboard V2 pada sistem PMS Lite berdasarkan judul case dan suite yang dieksekusi:
PMS-1120; PMS-1121; PMS-1122; PMS-1123; PMS-1124; PMS-1125; PMS-1126; PMS-1127; PMS-1128; PMS-1129; PMS-1130; PMS-1131; PMS-1132; PMS-1141; PMS-1142

* *Test Suite:* Dashboard V2 (Suite ID: 94)
* *Ticket:* BQS-1823 (terkait OP-1532)
* *Tanggal Eksekusi:* 20 Oktober 2026
* *Tipe Pengujian:* Manual - Functional, Data Validation, & RBAC
* *Tester:* QA Team (Dio Mahardika)
* *Environment / Build:* Staging (pms-staging.omnihotelier.net / build assets/index-b7c0ed17.js)
* *Link Test Run:* https://app.qase.io/public/report/c5854aaf2e7df2da941391bd24c5bf34f2f5e0d7
* *Evidence Video:* https://jam.dev/c/84a9fc78-4290-4cf7-a99e-9bde3eb6f1c7 (Bukti retest: KPI card clickable & Cancel only)

----

h3. Summary

||Metrik||Nilai||
|Total Test Cases|15|
|Passed|15|
|Failed|0|
|Blocked / Skipped / Invalid|0|
|Belum selesai|0|
|Case dengan Retest|2 (PMS-1128 & PMS-1142, lulus setelah retest)|
|Total waktu eksekusi|~45 menit|
|Hasil Akhir|*PASSED (LULUS 100%)*|

----

h3. Daftar Test Case

* *[Case ID PMS-1120]* Show daily operational KPI tile counts matching property reports - *Passed* _(high / major)_
* *[Case ID PMS-1121]* Show room status donut chart matching active housekeeping units - *Passed* _(high / major)_
* *[Case ID PMS-1122]* Show vacant rooms KPI count matching ready housekeeping units - *Passed* _(medium / normal)_
* *[Case ID PMS-1123]* Show room revenue by segment matching agent production report - *Passed* _(high / major)_
* *[Case ID PMS-1124]* Hide financial performance metrics for user without financial access - *Passed* _(high / critical)_
* *[Case ID PMS-1125]* Show individual guest name on group reservation row in arrivals table - *Passed* _(high / major)_
* *[Case ID PMS-1126]* Show expected departure list with folio link on table row - *Passed* _(medium / normal)_
* *[Case ID PMS-1127]* Update arrivals table balance with extra charge added to folio - *Passed* _(high / major)_
* *[Case ID PMS-1128]* Update cancelled reservation KPI tile count for cancelled booking - *Passed* _(medium / normal, lulus setelah retest)_
* *[Case ID PMS-1129]* Calculate daily performance metrics with updated label copy - *Passed* _(high / critical)_
* *[Case ID PMS-1130]* Show room monthly revenue trend line chart matching DSR nett revenue - *Passed* _(high / major)_
* *[Case ID PMS-1131]* Show guest birthday notification banner with modal for more guests - *Passed* _(medium / normal)_
* *[Case ID PMS-1132]* Show zero performance metrics without division error on zero divisor - *Passed* _(high / major)_
* *[Case ID PMS-1141]* Show night audit failure badge on failed audit run - *Passed* _(medium / normal)_
* *[Case ID PMS-1142]* Show related module page after clicking operational KPI tile - *Passed* _(medium / normal, lulus setelah retest)_

----

h3. Bug yang Ditemukan

Tidak ada status Failed pada run ini, sehingga tidak ada bug yang dilaporkan. Seluruh temuan perbaikan sebelumnya (nama tamu kamar grup, sinkronisasi balance folio, penyesuaian tile Cancel Only, standarisasi Gherkin, dan navigasi klik pada 7 tile KPI) telah diselesaikan oleh developer dan terverifikasi lulus.

----

h3. Kesimpulan & Catatan

# Seluruh 15 test case pada Suite Dashboard V2 (Suite ID: 94) bertipe Gherkin dan berhasil dieksekusi dengan status Passed (100% Pass Rate).
# Test data pada seluruh test case telah distandarisasi agar dinamis dan fleksibel untuk dijalankan pada properti mana pun (properti-agnostik).
# Catatan Retest: Test case PMS-1128 (Tile Cancelled hanya menghitung status Cancel) dan PMS-1142 (7 Tile KPI atas interaktif/dapat diklik menuju modul terkait) telah terkonfirmasi lulus melalui bukti pengujian video Jam.dev (https://jam.dev/c/84a9fc78-4290-4cf7-a99e-9bde3eb6f1c7).
# Seluruh Acceptance Criteria (AC-1 s/d AC-11) dan poin enhancement hasil grooming BOD telah terpenuhi secara utuh dan valid. Status: *Approved*.
