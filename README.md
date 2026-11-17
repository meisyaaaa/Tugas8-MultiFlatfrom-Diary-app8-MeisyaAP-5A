# Identitas
Nama: Meisya Amelia Putri
Nim: 2430511002
Kelas: 5A

# Diary App 8
Aplikasi buku harian sederhana dengan React Native (Expo Router) dan Redux Toolkit. Dibuat untuk Praktikum 08 Mobile Programming: Global State Management.

## Fitur
- Daftar diary, tambah, edit, dan hapus
- Tandai diary sebagai favorite, dan hapus semua favorite sekaligus
- Filter diary berdasarkan mood
- Statistik Total Diary dan Total Favorite
- Validasi form (judul minimal 3 karakter, isi wajib diisi)
- Empty state informatif pada Home dan Favorite

## Teknologi
- React Native + Expo + Expo Router
- Redux Toolkit dan React-Redux
- TypeScript
- Menjalankan Project
- bash
  npm install
  npx expo start

  Tekan w untuk web, atau scan QR dengan Expo Go.

## Struktur Project
diary-app8/
├── app/                      # Route (Expo Router)
│   ├── _layout.tsx           # Provider Redux + Stack
│   ├── (tabs)/               # Home, Tambah, Favorite
│   ├── detail/[id].tsx
│   └── edit/[id].tsx
└── src/
    ├── store/                # store.ts, hooks.ts
    ├── features/diary/       # diarySlice.ts, selectors.ts
    ├── components/           # DiaryCard, DiaryForm, EmptyState, Screen
    ├── constants/            # moods.ts
    ├── utils/                # validation.ts, dialog.ts
    └── styles/               # tokens.ts

Folder store bernama src/store, bukan src/app, karena Expo Router versi terbaru menganggap src/app sebagai folder route.

# Perbedaan Local State, Redux State, dan Database
Jenis	Contoh di aplikasi ini	Sifat
Local state (useState)	Isi form judul, cerita, dan mood yang sedang diketik	Hanya dipakai satu komponen. Hilang saat komponen ditutup.
Global Redux state	Daftar diary, status favorite, filter mood	Dipakai banyak screen dan tersimpan di memori aplikasi. Hilang saat aplikasi di-reload.
Persistent database	Belum dipakai	Penyimpanan permanen. Data tetap ada walaupun aplikasi ditutup.

Redux bukan database. Data diary yang ditambahkan akan kembali ke initialState ketika aplikasi di-reload. Pada pertemuan berikutnya, Redux dihubungkan dengan REST API dan database agar data tersimpan permanen.

## Alur Redux Singkat
- User menekan tombol
  -> dispatch(action)
  -> reducer di slice memproses action
  -> state baru disimpan di Store
  -> useSelector membaca state terbaru
  -> komponen re-render
- Reducer pada diarySlice
- Reducer	Fungsi
- addDiary	Menambah diary baru
- editDiary	Mengubah title, body, dan mood
- toggleFavorite	Menandai atau melepas favorite (payload { id })
- clearAllFavorites	Menghapus semua status favorite
- deleteDiary	Menghapus satu diary
- resetDiaries	Mengembalikan data ke kondisi awal
- setMoodFilter	Mengatur filter mood di Home
  
## Screenshoot Aplikasi
1. Halaman Home
<img width="635" height="335" alt="Halaman-Home" src="https://github.com/user-attachments/assets/2b436ad3-5018-4fb0-a3f5-d1daf9d52f08" />

2. Halaman Tambah Diary
<img width="635" height="335" alt="Tambah-Diary" src="https://github.com/user-attachments/assets/bf395620-2890-4bb0-9d0e-521f952ec7d5" />

3. Halaman Favorite
<img width="635" height="337" alt="Halaman-Favorite" src="https://github.com/user-attachments/assets/3af06c60-ef95-487a-af78-2a5e057c9a86" />

4. Halaman Detail
<img width="634" height="329" alt="Detail-Diary" src="https://github.com/user-attachments/assets/4bd5795c-f5e6-472f-87c0-0e607e6c0685" />
