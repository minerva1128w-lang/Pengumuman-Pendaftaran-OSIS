<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pengumuman Seleksi OSIS 2025/2026</title>
  <script>
    function cekHasil(event) {
      event.preventDefault();
      const nama = document.getElementById("nama").value.trim().toUpperCase();
      const absen = document.getElementById("absen").value.trim();

      const peserta = [
        { nama: "AZIZATUL MUNAWAROH", absen: "01", status: "belum memenuhi" },
        { nama: "AMEERA NAURA SYIFA", absen: "02", status: "memenuhi" },
        { nama: "MUHAMMAD RAMADAN WIDYANTARA", absen: "03", status: "belum memenuhi" },
        { nama: "ACHMAD THAHA METWALLY", absen: "82", status: "memenuhi" }
      ];

      const found = peserta.find(p => p.absen === absen && p.nama === nama);
      const hasilBox = document.getElementById("hasil");
      hasilBox.innerHTML = "";

      if (!found) {
        hasilBox.innerHTML = `
          <div style="padding:20px; background:#FFF3CD; border:1px solid #FFEEBA; border-radius:10px;">
            <h2 style="color:#856404;">DATA TIDAK DITEMUKAN</h2>
            <p>Nama atau nomor absen salah. Silakan coba lagi.</p>
          </div>
        `;
        return;
      }

      if (found.status === "memenuhi") {
        hasilBox.innerHTML = `
          <div style="padding:20px; background:#D4EDDA; border:1px solid #C3E6CB; border-radius:10px;">
            <h2 style="color:#155724;">MEMENUHI</h2>
            <p>Selamat, Anda lolos seleksi!</p>
          </div>
        `;
      } else {
        hasilBox.innerHTML = `
          <div style="padding:20px; background:#F8D7DA; border:1px solid #F5C6CB; border-radius:10px;">
            <h2 style="color:#721C24;">TIDAK MEMENUHI</h2>
            <p>Mohon maaf, Anda belum lolos seleksi.</p>
          </div>
        `;
      }
    }
  </script>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(to bottom right, #e0f0ff, #ffffff);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
    }
    .header {
      font-size: 2rem;
      font-weight: bold;
      color: #0d1b75;
      margin-bottom: 20px;
    }
    .card {
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      max-width: 400px;
      width: 100%;
      text-align: center;
    }
    h1 {
      color: #0d1b75;
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin: 10px 0 5px;
      text-align: left;
    }
    input {
      width: 100%;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      margin-bottom: 15px;
    }
    button {
      background: #0d1b75;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 8px;
      width: 100%;
      cursor: pointer;
      font-size: 1rem;
    }
    button:hover {
      background: #102694;
    }
    #hasil {
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div class="header">BRIGATAOSAGA</div>
  <div class="card">
    <h1>Pengumuman Seleksi OSIS 2025/2026</h1>
    <form onsubmit="cekHasil(event)">
      <label for="nama">Nama Lengkap</label>
      <input type="text" id="nama" placeholder="Masukkan nama (huruf besar)" required>

      <label for="absen">Nomor Absen</label>
      <input type="text" id="absen" placeholder="Masukkan nomor absen (01)" required>

      <button type="submit">Lihat Hasil</button>
    </form>
    <div id="hasil"></div>
  </div>
</body>
</html>

