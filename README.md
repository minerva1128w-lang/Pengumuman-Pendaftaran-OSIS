# Pengumuman-Pendaftaran-OSIS
import React, { useState } from 'react';

// Halaman Pengumuman Seleksi OSIS 2025/2026
// Input: Nama & Nomor Absen
// Output: Hanya tampilkan "Memenuhi" atau "Tidak Memenuhi"

export default function OSISPengumumanPage() {
  const [submitted, setSubmitted] = useState(false);
  const [nama, setNama] = useState('');
  const [absen, setAbsen] = useState('');
  const [result, setResult] = useState(null);
  const [error, setError] = useState(false);

  // Data peserta seleksi OSIS
  const peserta = [
    { nama: "AZIZATUL MUNAWAROH", absen: "01", status: "belum memenuhi" },
    { nama: "AMEERA NAURA SYIFA", absen: "02", status: "memenuhi" },
    { nama: "MUHAMMAD RAMADAN WIDYANTARA", absen: "03", status: "belum memenuhi" },
    // ... (data tetap sama)
    { nama: "ACHMAD THAHA METWALLY", absen: "82", status: "memenuhi" }
  ];

  function handleSubmit(e) {
    e.preventDefault();
    const found = peserta.find(
      r => r.absen === absen.trim() && r.nama === nama.trim().toUpperCase()
    );
    if (found) {
      setResult(found.status);
      setError(false);
    } else {
      setError(true);
    }
    setSubmitted(true);
  }

  if (!submitted) {
    return (
      <div className="min-h-screen flex flex-col items-center justify-center bg-gradient-to-br from-green-200 via-white to-green-100">
        {/* Logo Header */}
        <h2 className="text-4xl font-extrabold text-blue-900 mb-6">BRIGATAOSAGA</h2>
        
        <div className="bg-white shadow-xl rounded-2xl p-8 w-full max-w-md border border-green-300">
          <h1 className="text-3xl font-bold mb-6 text-center text-blue-900">
            Pengumuman Seleksi OSIS 2025/2026
          </h1>
          <form onSubmit={handleSubmit} className="space-y-4">
            <div>
              <label className="block text-sm font-medium mb-1 text-gray-700">Nama Lengkap</label>
              <input
                type="text"
                value={nama}
                onChange={e => setNama(e.target.value)}
                className="w-full border border-gray-300 rounded-lg p-2 focus:ring-2 focus:ring-blue-400 focus:outline-none"
                placeholder="Masukkan nama (huruf besar)"
              />
            </div>
            <div>
              <label className="block text-sm font-medium mb-1 text-gray-700">Nomor Absen</label>
              <input
                type="text"
                value={absen}
                onChange={e => setAbsen(e.target.value)}
                className="w-full border border-gray-300 rounded-lg p-2 focus:ring-2 focus:ring-blue-400 focus:outline-none"
                placeholder="Masukkan nomor absen (01)"
              />
            </div>
            <button
              type="submit"
              className="w-full bg-blue-900 text-white py-2 rounded-lg font-medium hover:bg-blue-800 transition duration-200"
            >
              Lihat Hasil
            </button>
          </form>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-gradient-to-r from-green-100 via-white to-green-200">
      {/* Logo Header */}
      <h2 className="text-4xl font-extrabold text-blue-900 mb-6">BRIGATAOSAGA</h2>

      <div className="bg-white shadow-2xl rounded-2xl p-10 max-w-lg w-full text-center border border-green-400">
        <h1 className="text-3xl font-extrabold text-blue-900 mb-4">
          Hasil Seleksi OSIS 2025/2026
        </h1>
        {error ? (
          <div className="p-6 bg-yellow-100 border border-yellow-300 rounded-xl">
            <p className="text-2xl font-bold text-yellow-700">DATA TIDAK DITEMUKAN</p>
            <p className="text-gray-600 mt-2">Nama atau nomor absen salah. Silakan coba lagi.</p>
          </div>
        ) : result === 'memenuhi' ? (
          <div className="p-6 bg-green-100 border border-green-300 rounded-xl">
            <p className="text-2xl font-bold text-green-700">MEMENUHI</p>
            <p className="text-gray-600 mt-2">Selamat, Anda lolos seleksi!</p>
          </div>
        ) : (
          <div className="p-6 bg-red-100 border border-red-300 rounded-xl">
            <p className="text-2xl font-bold text-red-700">TIDAK MEMENUHI</p>
            <p className="text-gray-600 mt-2">Mohon maaf, Anda belum lolos seleksi.</p>
          </div>
        )}
        <button
          onClick={() => setSubmitted(false)}
          className="mt-6 px-4 py-2 bg-blue-900 text-white rounded-lg hover:bg-blue-800"
        >
          Cek Lagi
        </button>
      </div>
    </div>
  );
}
