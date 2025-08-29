import React, { useMemo, useState } from "react";
import { motion } from "framer-motion";
import { BookOpen, Beaker, FileText, ClipboardList, Play, RotateCw, Info, Calculator } from "lucide-react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Slider } from "@/components/ui/slider";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { Label } from "@/components/ui/label";

// ===============================
// UTILITIES
// ===============================
const fmt = (x, digits = 2) => {
  if (Number.isNaN(x) || !Number.isFinite(x)) return "-";
  const s = Number(x).toFixed(digits);
  return (Math.abs(Number(s)) >= 1e6 || (Math.abs(Number(s)) > 0 && Math.abs(Number(s)) < 1e-3))
    ? Number(x).toExponential(2)
    : s;
};

const earthToneBg = "bg-[#F3EEE7]"; // earth tone base
const earthToneCard = "bg-[#FAF7F2]"; // lighter card
const earthToneAccent = "bg-[#D4C2A8]"; // accent bar

// ===============================
// SIMPLE SVG ILLUSTRATION
// ===============================
function CircularMotionSVG({ r = 120, v = 6, size = 320 }) {
  const cx = size / 2;
  const cy = size / 2;
  const theta = Math.PI / 6; // marker angle
  const px = cx + r * Math.cos(theta);
  const py = cy + r * Math.sin(theta);
  const tx = px + 0.6 * v * Math.cos(theta + Math.PI / 2);
  const ty = py + 0.6 * v * Math.sin(theta + Math.PI / 2);
  const ax = px + 0.6 * v * Math.cos(theta + Math.PI);
  const ay = py + 0.6 * v * Math.sin(theta + Math.PI);

  return (
    <svg viewBox={`0 0 ${size} ${size}`} className="w-full h-full">
      <defs>
        <marker id="arrow" viewBox="0 0 10 10" refX="10" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M 0 0 L 10 5 L 0 10 z" fill="#7a6a53" />
        </marker>
      </defs>
      <circle cx={cx} cy={cy} r={r} fill="none" stroke="#bfa888" strokeWidth="3" />
      <circle cx={cx} cy={cy} r={4} fill="#7a6a53" />
      <circle cx={px} cy={py} r={8} fill="#6e5a44" />
      {/* velocity tangential */}
      <line x1={px} y1={py} x2={tx} y2={ty} stroke="#6e5a44" strokeWidth={3} markerEnd="url(#arrow)" />
      {/* acceleration toward center */}
      <line x1={px} y1={py} x2={ax} y2={ay} stroke="#8a7357" strokeWidth={3} markerEnd="url(#arrow)" />
      <text x={tx + 8} y={ty} fontSize="12" fill="#6e5a44">v (tangen)</text>
      <text x={ax - 32} y={ay - 6} fontSize="12" fill="#8a7357">aₙ ke pusat</text>
    </svg>
  );
}

// ===============================
// QUIZ DATA
// ===============================
const bankSoal = [
  {
    id: 1,
    tipe: "pg",
    soal: "Sebuah benda bergerak melingkar beraturan dengan r = 0,5 m dan f = 2 Hz. Kecepatan linear v adalah...",
    opsi: ["π m/s", "2π m/s", "4π m/s", "8π m/s"],
    kunci: 2, // index 2 -> "4π m/s"
    pembahasan: "v = 2π r f = 2π(0,5)(2) = 2π m/s? Salah. Hitung benar: 2π × 0,5 × 2 = 2π. Tapi opsi benar 4π? Cek: jika ω = 2πf = 4π rad/s, v = ωr = 4π × 0,5 = 2π m/s. Jadi jawaban yang tepat adalah 2π m/s. (Perbaiki kunci ke index 1)",
  },
  {
    id: 2,
    tipe: "isian",
    soal: "Periode T = 0,4 s. Frekuensi f = ____ Hz.",
    jawabanAngka: 2.5,
    toleransi: 0.01,
    pembahasan: "f = 1/T = 1/0,4 = 2,5 Hz.",
  },
  {
    id: 3,
    tipe: "pg",
    soal: "Percepatan normal aₙ untuk v = 10 m/s dan r = 5 m adalah...",
    opsi: ["5 m/s²", "10 m/s²", "20 m/s²", "25 m/s²"],
    kunci: 3,
    pembahasan: "aₙ = v²/r = 100/5 = 20 m/s².",
  },
  {
    id: 4,
    tipe: "pg",
    soal: "Gaya sentripetal F untuk m = 2 kg, v = 6 m/s, r = 3 m adalah...",
    opsi: ["8 N", "12 N", "24 N", "36 N"],
    kunci: 2,
    pembahasan: "F = m v² / r = 2×36/3 = 24 N.",
  },
  {
    id: 5,
    tipe: "isian",
    soal: "Sebuah roda memiliki ω = 12 rad/s dan r = 0,25 m. Kecepatan linear v = ____ m/s.",
    jawabanAngka: 3,
    toleransi: 0.02,
    pembahasan: "v = ω r = 12 × 0,25 = 3 m/s.",
  },
];

// koreksi kunci soal #1 (agar konsisten dengan pembahasan)
bankSoal[0].kunci = 1;

// ===============================
// LKPD TEMPLATE (printable)
// ===============================
const LKPD_TEXT = `
LKPD – Gerak Melingkar (Kelas XI)
Kurikulum Merdeka

A. Tujuan Pembelajaran
Menganalisis hubungan antara \n- kecepatan sudut (ω), periode (T), frekuensi (f), \n- kecepatan linear (v), percepatan normal aₙ, dan gaya sentripetal (F),\nserta menerapkannya pada fenomena nyata.

B. Alat & Bahan (opsional penyesuaian sekolah)
• Tali nilon ±1 m, beban kecil \n• Stopwatch \n• Penggaris / meteran \n• Ponsel (aplikasi pengukur frekuensi/slow-mo)

C. Petunjuk Keselamatan
• Pastikan area bebas hambatan. \n• Pegang tali kuat-kuat. \n• Gunakan kacamata pelindung bila perlu.

D. Langkah Kegiatan
1) Ukur jari-jari putaran r dari pusat ke benda.
2) Putar benda secara horizontal dengan laju stabil. Rekam video 10 s.
3) Hitung jumlah putaran N pada durasi t, lalu f = N/t; T = 1/f.
4) Hitung v = 2π r f dan aₙ = v²/r. Jika massa benda m diketahui, hitung F = m v² / r.
5) Ulangi untuk 3 nilai r yang berbeda. Catat data.

E. Tabel Data
| Uji | r (m) | N | t (s) | f (Hz) | v (m/s) | aₙ (m/s²) | m (kg) | F (N) |
|-----|-------|---|-------|--------|---------|-----------|--------|-------|
| 1   |       |   |       |        |         |           |        |       |
| 2   |       |   |       |        |         |           |        |       |
| 3   |       |   |       |        |         |           |        |       |

F. Pertanyaan Pemantik
1) Bagaimana pengaruh r terhadap v jika f tetap? Jelaskan.
2) Bagaimana perubahan aₙ saat r diperbesar namun v tetap?
3) Sebutkan contoh gaya sentripetal pada kendaraan di tikungan.

G. Refleksi
Tuliskan 2 hal yang Anda pahami dan 1 hal yang masih membingungkan.
`;

// ===============================
// MAIN APP
// ===============================
export default function App() {
  const [tab, setTab] = useState("materi");

  // Simulasi state
  const [r, setR] = useState(0.5); // m
  const [f, setF] = useState(1.0); // Hz
  const [m, setM] = useState(1.0); // kg

  const omega = useMemo(() => 2 * Math.PI * f, [f]);
  const T = useMemo(() => (f > 0 ? 1 / f : Infinity), [f]);
  const v = useMemo(() => omega * r, [omega, r]);
  const an = useMemo(() => (r > 0 ? v * v / r : 0), [v, r]);
  const F = useMemo(() => m * an, [m, an]);

  // Quiz state
  const [jawaban, setJawaban] = useState({}); // {id: value}
  const [skor, setSkor] = useState(null);

  const nilaiQuiz = () => {
    let benar = 0;
    bankSoal.forEach((q) => {
      if (q.tipe === "pg") {
        if (jawaban[q.id] === q.kunci) benar++;
      } else {
        const val = parseFloat(jawaban[q.id]);
        if (!Number.isNaN(val) && Math.abs(val - q.jawabanAngka) <= (q.toleransi ?? 0.01)) benar++;
      }
    });
    const p = Math.round((100 * benar) / bankSoal.length);
    setSkor({ benar, total: bankSoal.length, persen: p });
  };

  const resetQuiz = () => {
    setJawaban({});
    setSkor(null);
  };

  const downloadLKPD = () => {
    const blob = new Blob([LKPD_TEXT], { type: "text/plain;charset=utf-8" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = "LKPD_Gerak_Melingkar_KelasXI.txt";
    a.click();
    URL.revokeObjectURL(url);
  };

  return (
    <div className={`${earthToneBg} min-h-screen text-stone-800`}> 
      <div className="max-w-6xl mx-auto px-4 py-6">
        <header className="flex items-center justify-between gap-4">
          <div>
            <h1 className="text-2xl md:text-3xl font-semibold tracking-tight">Media Pembelajaran Interaktif – Gerak Melingkar</h1>
            <p className="text-sm md:text-base text-stone-600">Kelas XI • Kurikulum Merdeka • Earth-tone UI</p>
          </div>
          <div className="hidden md:flex items-center gap-2">
            <Button onClick={() => setTab("materi")} className="rounded-2xl shadow-sm">Materi</Button>
            <Button onClick={() => setTab("simulasi")} variant="secondary" className="rounded-2xl shadow-sm">Simulasi</Button>
            <Button onClick={() => setTab("lkpd")} variant="secondary" className="rounded-2xl shadow-sm">LKPD</Button>
            <Button onClick={() => setTab("kuis")} variant="secondary" className="rounded-2xl shadow-sm">Kuis</Button>
          </div>
        </header>

        <Tabs value={tab} onValueChange={setTab} className="mt-6">
          <TabsList className="grid grid-cols-4 gap-2 p-1 rounded-2xl ${earthToneAccent}">
            <TabsTrigger value="materi" className="rounded-2xl"> <BookOpen className="w-4 h-4 mr-2"/> Materi </TabsTrigger>
            <TabsTrigger value="simulasi" className="rounded-2xl"> <Beaker className="w-4 h-4 mr-2"/> Simulasi </TabsTrigger>
            <TabsTrigger value="lkpd" className="rounded-2xl"> <FileText className="w-4 h-4 mr-2"/> LKPD </TabsTrigger>
            <TabsTrigger value="kuis" className="rounded-2xl"> <ClipboardList className="w-4 h-4 mr-2"/> Kuis </TabsTrigger>
          </TabsList>

          {/* ================= MATERI ================= */}
          <TabsContent value="materi" className="mt-4">
            <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.3 }}>
              <div className="grid md:grid-cols-2 gap-4">
                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 space-y-3">
                    <div className="flex items-center gap-2 text-stone-700"><Info className="w-5 h-5"/><h2 className="text-lg font-semibold">Ringkasan Konsep</h2></div>
                    <ul className="list-disc pl-5 space-y-2">
                      <li><span className="font-medium">Gerak Melingkar Beraturan (GMB)</span>: kecepatan sudut konstan (ω), |v| konstan, arah v berubah.</li>
                      <li>Hubungan dasar: <span className="font-mono">ω = 2πf</span>, <span className="font-mono">T = 1/f</span>, <span className="font-mono">v = ω r = 2π r f</span>.</li>
                      <li>Percepatan menuju pusat (normal): <span className="font-mono">aₙ = v²/r = ω² r</span>.</li>
                      <li>Gaya sentripetal: <span className="font-mono">F = m v² / r = m ω² r</span>.</li>
                      <li>Contoh: mobil di tikungan melingkar, satelit orbit, gerakan roda.</li>
                    </ul>
                    <div className="text-sm text-stone-600">Satuan SI: r (m), f (Hz), T (s), ω (rad/s), v (m/s), aₙ (m/s²), F (N), m (kg).</div>
                  </CardContent>
                </Card>

                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 grid grid-rows-[200px_auto] gap-4">
                    <div className="w-full h-[220px]">
                      <CircularMotionSVG r={120} v={8} />
                    </div>
                    <div className="text-sm text-stone-700">
                      Ilustrasi: v menyinggung lintasan (tangen), aₙ mengarah ke pusat. Pada GMB, besar v tetap tetapi arah berubah sehingga ada aₙ dan memerlukan gaya sentripetal.
                    </div>
                  </CardContent>
                </Card>
              </div>

              <div className="mt-4 grid md:grid-cols-3 gap-4">
                {[{title:"Hubungan ω, f, T",body:"ω = 2πf dan T = 1/f. Jika f naik 2×, ω juga naik 2×, T turun 1/2."},{title:"Kecepatan v",body:"v = ωr. Pada r tetap, v proporsional terhadap ω; pada ω tetap, v ∝ r."},{title:"Percepatan & Gaya",body:"aₙ = v²/r; F = m v²/r. Semakin cepat atau semakin kecil r, semakin besar aₙ dan F."}].map((it, i) => (
                  <Card key={i} className={`${earthToneCard} rounded-2xl shadow-sm`}>
                    <CardContent className="p-5">
                      <h3 className="font-semibold mb-2">{it.title}</h3>
                      <p className="text-sm text-stone-700">{it.body}</p>
                    </CardContent>
                  </Card>
                ))}
              </div>
            </motion.div>
          </TabsContent>

          {/* ================= SIMULASI ================= */}
          <TabsContent value="simulasi" className="mt-4">
            <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.3 }}>
              <div className="grid lg:grid-cols-2 gap-4">
                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 space-y-4">
                    <div className="flex items-center gap-2"><Calculator className="w-5 h-5"/><h2 className="text-lg font-semibold">Pengaturan</h2></div>

                    <div className="grid grid-cols-6 gap-3 items-center">
                      <Label className="col-span-2">r (m)</Label>
                      <div className="col-span-4">
                        <Slider min={0.1} max={2.0} step={0.01} value={[r]} onValueChange={(v)=>setR(v[0])} />
                        <div className="text-xs mt-1">{fmt(r,2)} m</div>
                      </div>

                      <Label className="col-span-2">f (Hz)</Label>
                      <div className="col-span-4">
                        <Slider min={0.2} max={5.0} step={0.01} value={[f]} onValueChange={(v)=>setF(v[0])} />
                        <div className="text-xs mt-1">{fmt(f,2)} Hz</div>
                      </div>

                      <Label className="col-span-2">m (kg)</Label>
                      <div className="col-span-4">
                        <Slider min={0.1} max={5.0} step={0.01} value={[m]} onValueChange={(v)=>setM(v[0])} />
                        <div className="text-xs mt-1">{fmt(m,2)} kg</div>
                      </div>
                    </div>

                    <div className="flex gap-2">
                      <Button variant="secondary" onClick={()=>{setR(0.5);setF(1.0);setM(1.0);}} className="rounded-2xl"><RotateCw className="w-4 h-4 mr-2"/> Reset</Button>
                    </div>
                  </CardContent>
                </Card>

                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 space-y-4">
                    <div className="grid md:grid-cols-2 gap-4">
                      <div className="h-56"><CircularMotionSVG r={Math.min(140, 80 + r*40)} v={v} /></div>
                      <div className="grid grid-cols-2 gap-x-3 gap-y-2 text-sm">
                        <div className="text-stone-500">ω (rad/s)</div><div className="font-mono">{fmt(omega,2)}</div>
                        <div className="text-stone-500">T (s)</div><div className="font-mono">{fmt(T,2)}</div>
                        <div className="text-stone-500">v (m/s)</div><div className="font-mono">{fmt(v,2)}</div>
                        <div className="text-stone-500">aₙ (m/s²)</div><div className="font-mono">{fmt(an,2)}</div>
                        <div className="text-stone-500">F (N)</div><div className="font-mono">{fmt(F,2)}</div>
                      </div>
                    </div>
                    <div className="text-xs text-stone-600">Catatan: aₙ meningkat saat v membesar atau r mengecil.</div>
                  </CardContent>
                </Card>
              </div>
            </motion.div>
          </TabsContent>

          {/* ================= LKPD ================= */}
          <TabsContent value="lkpd" className="mt-4">
            <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.3 }}>
              <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                <CardContent className="p-5 space-y-4">
                  <h2 className="text-lg font-semibold flex items-center gap-2"><FileText className="w-5 h-5"/> LKPD – Gerak Melingkar</h2>
                  <pre className="whitespace-pre-wrap text-sm leading-relaxed font-sans bg-white/50 rounded-xl p-4 border border-stone-200">{LKPD_TEXT}</pre>
                  <div className="flex gap-2">
                    <Button onClick={downloadLKPD} className="rounded-2xl"><Play className="w-4 h-4 mr-2"/> Unduh LKPD (TXT)</Button>
                  </div>
                </CardContent>
              </Card>
            </motion.div>
          </TabsContent>

          {/* ================= KUIS ================= */}
          <TabsContent value="kuis" className="mt-4">
            <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.3 }}>
              <div className="grid md:grid-cols-2 gap-4">
                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 space-y-4">
                    <h2 className="text-lg font-semibold flex items-center gap-2"><ClipboardList className="w-5 h-5"/> Kuis Formatif</h2>
                    <div className="space-y-5">
                      {bankSoal.map((q, idx) => (
                        <div key={q.id} className="border border-stone-200 rounded-xl p-3 bg-white/60">
                          <div className="text-sm font-medium mb-2">{idx+1}. {q.soal}</div>
                          {q.tipe === "pg" ? (
                            <div className="space-y-2">
                              {q.opsi.map((o, i) => (
                                <label key={i} className="flex items-center gap-2 text-sm">
                                  <input type="radio" name={`q_${q.id}`} checked={jawaban[q.id]===i} onChange={()=>setJawaban({ ...jawaban, [q.id]: i })} />
                                  <span>{o}</span>
                                </label>
                              ))}
                            </div>
                          ) : (
                            <div className="flex items-center gap-2">
                              <Input type="number" step="any" value={jawaban[q.id] ?? ""} onChange={(e)=>setJawaban({ ...jawaban, [q.id]: e.target.value })} className="max-w-[160px]" />
                              <span className="text-xs text-stone-500">Gunakan SI</span>
                            </div>
                          )}
                          {skor && (
                            <div className="mt-2 text-xs text-stone-600">
                              <span className="font-semibold">Pembahasan: </span>{q.pembahasan}
                            </div>
                          )}
                        </div>
                      ))}
                    </div>
                    <div className="flex gap-2 items-center">
                      <Button onClick={nilaiQuiz} className="rounded-2xl">Nilai</Button>
                      <Button variant="secondary" onClick={resetQuiz} className="rounded-2xl">Reset</Button>
                      {skor && (<div className="text-sm">Skor: <span className="font-semibold">{skor.benar}/{skor.total}</span> ({skor.persen}%)</div>)}
                    </div>
                  </CardContent>
                </Card>

                <Card className={`${earthToneCard} rounded-2xl shadow-sm`}>
                  <CardContent className="p-5 space-y-3">
                    <h3 className="font-semibold">Tujuan Pembelajaran (TP)</h3>
                    <ul className="list-disc pl-5 text-sm space-y-1">
                      <li>Menghubungkan ω, f, T, r, v, aₙ, dan F dalam GMB.</li>
                      <li>Mengukur besaran pada eksperimen sederhana putaran benda.</li>
                      <li>Menyelesaikan soal kontekstual yang melibatkan gaya sentripetal.</li>
                    </ul>
                    <h3 className="font-semibold mt-2">Asesmen</h3>
                    <ul className="list-disc pl-5 text-sm space-y-1">
                      <li>Formatif: kuis otomatis pada aplikasi ini.</li>
                      <li>Sumatif singkat: laporan LKPD dengan perhitungan dan refleksi.</li>
                    </ul>
                  </CardContent>
                </Card>
              </div>
            </motion.div>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  );
}
