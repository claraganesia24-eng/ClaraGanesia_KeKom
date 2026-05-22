[Decision Tree.py](https://github.com/user-attachments/files/28134037/Decision.Tree.py) Silahkan klik ini
# =====================================================
# SMART ATTENDANCE MONITOR
# Decision Tree Sederhana - Python
# Mata Kuliah : Kecerdasan Komputasional
# =====================================================

# ======================
# WARNA TERMINAL
# ======================

biru = "\033[94m"
cyan = "\033[96m"
hijau = "\033[92m"
merah = "\033[91m"
kuning = "\033[93m"
reset = "\033[0m"

# ======================
# DATA MAHASISWA
# ======================

mahasiswa = [
    ["Nea", "Tinggi", "Lengkap"],
    ["Jenifer", "Rendah", "Tidak Lengkap"],
    ["Yowr", "Tinggi", "Tidak Lengkap"],
    ["Jewel", "Rendah", "Lengkap"],
    ["Lintang", "Tinggi", "Lengkap"]
]

# ======================
# VARIABEL REKAP
# ======================

aktif = 0
tidak_aktif = 0
disiplin = 0

# ======================
# JUDUL PROGRAM
# ======================

print(cyan + """
╔════════════════════════════════════════════════════════════════════╗
║                 SMART ATTENDANCE MONITOR                           ║
╚════════════════════════════════════════════════════════════════════╝
""" + reset)

# ======================
# HEADER TABEL
# ======================

print(biru + "┌──────────┬────────────┬──────────────────┬──────────────┬────────────────────────────┐" + reset)
print("│ Nama     │ Kehadiran  │ Tugas            │ Status       │ Catatan                    │")
print(biru + "├──────────┼────────────┼──────────────────┼──────────────┼────────────────────────────┤" + reset)

# ======================
# PROSES DATA
# ======================

for data in mahasiswa:

    nama = data[0]
    kehadiran = data[1]
    tugas = data[2]

    # Decision Tree
    if kehadiran == "Tinggi":
        status = "Aktif"
        aktif += 1
        warna_status = hijau
    else:
        status = "Tidak Aktif"
        tidak_aktif += 1
        warna_status = merah

    # Catatan
    if kehadiran == "Tinggi" and tugas == "Lengkap":
        catatan = "🌟 Performa Baik"
        disiplin += 1

    elif kehadiran == "Tinggi" and tugas == "Tidak Lengkap":
        catatan = "📝 Tugas Kurang"

    elif kehadiran == "Rendah" and tugas == "Tidak Lengkap":
        catatan = "⚠ Perlu Evaluasi"

    else:
        catatan = "📌 Kehadiran Kurang"

    # OUTPUT TABEL RAPI
    print(
        biru + "│" + reset +
        f" {nama:<8} " +
        biru + "│" + reset +
        f" {kehadiran:<10} " +
        biru + "│" + reset +
        f" {tugas:<16} " +
        biru + "│" + reset +
        f" {warna_status}{status:<12}{reset} " +
        biru + "│" + reset +
        f" {catatan:<26} " +
        biru + "│" + reset
    )

# ======================
# PENUTUP TABEL
# ======================

print(biru + "└──────────┴────────────┴──────────────────┴──────────────┴────────────────────────────┘" + reset)

# ======================
# REKAP DATA
# ======================

total = len(mahasiswa)
persentase = (aktif / total) * 100

print(cyan + """
╔══════════════════════════════════════════════╗
║                 HASIL REKAP                  ║
╚══════════════════════════════════════════════╝
""" + reset)

print(hijau + f"✅ Mahasiswa Aktif        : {aktif}" + reset)
print(merah + f"❌ Mahasiswa Tidak Aktif  : {tidak_aktif}" + reset)
print(kuning + f"⭐ Mahasiswa Disiplin     : {disiplin}" + reset)
print(cyan + f"📊 Persentase Aktif       : {persentase:.1f}%" + reset)

# ======================
# KESIMPULAN
# ======================

if persentase >= 70:
    print(hijau + "\n🎉 Kesimpulan : Tingkat keaktifan mahasiswa sangat baik" + reset)
else:
    print(merah + "\n⚠ Kesimpulan : Keaktifan mahasiswa perlu ditingkatkan" + reset)

print(cyan + "\n✨ Sistem selesai dijalankan tanpa error ✨" + reset)
print("=" * 70)
