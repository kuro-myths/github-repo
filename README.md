# GitHub Repository Registry

Repository ini menjadi pusat katalog repository milik akun `kuro-myths`.

## Fitur

- Sinkronisasi repository otomatis setiap hari (00:00 UTC / 07:00 WIB).
- Bisa dijalankan manual melalui tab **Actions**.
- Mengambil repository public dan private yang dapat diakses token.
- Menyimpan metadata ke `data/repositories.json`.
- Tidak mengubah atau menghapus source code repository lain.

## Aktifkan sinkronisasi

1. Buat Personal Access Token GitHub (fine-grained atau classic) yang dapat membaca daftar repository akun `kuro-myths`, termasuk private repository yang ingin dimasukkan.
2. Berikan akses **Contents: Read and write** ke repository `kuro-myths/github-repo`.
3. Buka **Settings → Secrets and variables → Actions → New repository secret**.
4. Isi nama secret: `GH_REPO_SYNC_TOKEN`, lalu tempel token. Jangan masukkan token ke file atau commit.
5. Buka **Actions → Sync GitHub Repositories → Run workflow**.

Untuk fine-grained token, pilih owner `kuro-myths`, aktifkan akses metadata read dan contents read/write pada repository registry, serta pastikan token dapat membaca semua repository sumber yang ingin didaftarkan. Jika cakupan akses tidak mencakup semua repo private, repo tersebut tidak akan muncul.

## Hasil

File katalog: [data/repositories.json](data/repositories.json)

Workflow: [.github/workflows/sync-repositories.yml](.github/workflows/sync-repositories.yml)

Sinkronisasi terjadwal berjalan setiap hari pukul 07.00 WIB. GitHub Actions membutuhkan secret `GH_REPO_SYNC_TOKEN` agar dapat membaca seluruh repository akun.
