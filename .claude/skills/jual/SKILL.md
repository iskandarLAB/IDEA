---
name: jual
description: Jalankan pipeline penuh video affiliate TikTok/Shopee untuk satu produk — cari produk, gambar 360, storyboard 30s, skrip, voice AI, transform footage & publish. Guna bila aku taip /jual <produk> atau minta "buat video jual <produk>".
---

# /jual — Pipeline video affiliate

Argumen: nama produk atau niche (contoh `/jual kipas portable`). Kosong → mula dari Agen 0.

## Setup
1. Buat slug (huruf kecil, sengkang) → folder `produk/<slug>/` dengan subfolder `screenshots/`, `footage/`, `kalodata/`, `01-360/`.
2. Kalau folder dah wujud, baca fail `0X-*.md` yang ada dan **sambung dari langkah yang belum siap**.

## Langkah (setiap langkah = panggil subagent, kemudian GATE)
| Langkah | Subagent | Gate — tanya aku sebelum teruskan |
|--------|----------|------|
| 0 | `product-hunter` | Produk mana dipilih? (langkau jika aku dah bagi produk spesifik + link) |
| 1 | `product-360` | Letak screenshot dalam `screenshots/`. Setuju kos kredit? Gambar lulus QC? |
| 2 | `storyboard` | Pilih dunia absurd & hook. Storyboard ok? → **aku pergi rakam footage** ikut shot list |
| 3 | `scriptwriter` | Skrip ok? (boleh jalan selari dengan langkah 2 selepas storyboard diluluskan) |
| 4 | `voice-ai` | Mod A (voice change) atau B (TTS)? Voice mana? Setuju kos? |
| 5 | `video-transform` | Footage dah ada dalam `footage/`? Setuju kos? Video final ok? Publish draf TikTok? |

Pass kepada setiap subagent: slug, path folder produk, dan keputusan aku dari gate sebelumnya.

## Peraturan
- Jangan langkau gate kos kredit. Jangan publish tanpa aku sahkan.
- Selepas setiap langkah, update `produk/<slug>/STATUS.md` (checklist 0–5 + nota).
- Hujung: ringkasan — URL video, kredit dipakai, 3 hook alternatif untuk video seterusnya (A/B test).
