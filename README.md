# IDEA — Studio Video Affiliate (TikTok Shop & Shopee)

Video affiliate dari **footage sebenar** yang diubah guna AI (muka, suara, background) ke dunia **tak masuk akal** supaya hook kuat — tapi produk & demo kekal real. Bukan AI slop.

> Contoh: jual kipas portable sambil duduk atas lava mendidih.

## Cara guna (Claude Code)
```
/jual kipas portable
```
Atau panggil agen satu-satu: "guna agen storyboard untuk produk/contoh-kipas-lava".

## Agen (`.claude/agents/`)
| # | Agen | Kerja |
|---|------|------|
| 0 | `product-hunter` | Cari produk menang (data Kalodata + vidIQ + web) |
| 1 | `product-360` | Screenshot → set gambar 8 angle + close-up + 3D/turntable, dengan QC anti-slop |
| 2 | `storyboard` | Storyboard 30s shot-by-shot, hook absurd → demo real → CTA, + shot list rakaman |
| 3 | `scriptwriter` | Skrip VO BM santai, teks skrin, caption, hashtag |
| 4 | `voice-ai` | Voice change atas footage (lip-sync kekal) atau TTS |
| 5 | `video-transform` | Tukar background/muka/suara footage, cantum, draf TikTok + export Shopee |

## Struktur folder produk
```
produk/<slug>/
  kalodata/      ← export CSV/screenshot dari Kalodata
  screenshots/   ← screenshot produk dari Shopee/TikTok Shop
  footage/       ← rakaman kau: shot01.mp4, shot02.mp4 …
  00-produk.md  01-360.md  02-storyboard.md  03-script.md  04-voice.md  05-video.md  STATUS.md
```
Template kosong dalam `templates/`. Contoh lengkap dalam `produk/contoh-kipas-lava/`.

## Keperluan
- **Higgsfield** connector (gambar, video, 3D, suara, publish TikTok) — perlu kredit.
- **vidIQ** connector (trend/outlier) — pilihan.
- **Kalodata** — akaun sendiri; export manual (tiada API).
- **Shopee** — upload manual di Shopee Video (tiada API publish).

## Tips rakam footage (supaya AI senang ubah)
- 9:16, 1080p+ 30fps, cahaya terang & rata, latar plain (dinding kosong / green screen).
- Produk sentiasa nampak jelas, jangan tutup logo dengan jari.
- Gerakan perlahan & jelas; elak rambut/objek bergerak laju di tepi badan.
- Rakam 2–3 take setiap shot; rakam juga 5s "clean plate" (produk sahaja atas meja).
- Kalau guna voice change: cakap skrip betul-betul masa rakam supaya lip-sync tepat.

## Pematuhan
- Tandakan video sebagai **AI-generated** di TikTok dan buat **disclosure komersial/affiliate**.
- Jangan guna muka/suara orang lain. Jangan claim fungsi yang produk tak ada.
