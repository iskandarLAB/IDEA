# IDEA — Studio Affiliate TikTok & Shopee

Repo ni ialah "studio" untuk buat video affiliate TikTok Shop & Shopee yang **bukan AI slop**.

## Konsep
- Footage **sebenar** (aku pegang/guna produk betul-betul) → diubah guna AI: tukar muka, tukar suara, tukar background.
- Background/situasi sengaja **tak masuk akal** untuk hook (contoh: jual kipas portable sambil duduk atas lava mendidih).
- Produk sentiasa **real** — rupa, saiz, warna, fungsi produk TIDAK boleh diubah oleh AI. Yang absurd hanya dunia sekeliling.

## Pipeline (ikut nombor)
| # | Agen | Input | Output (dalam `produk/<slug>/`) |
|---|------|-------|------|
| 0 | `product-hunter` | niche / bajet / data Kalodata | `00-produk.md` (shortlist + pilihan) |
| 1 | `product-360` | screenshot produk | `01-360/` + `01-360.md` (gambar multi-angle, turntable) |
| 2 | `storyboard` | `00` + `01` | `02-storyboard.md` (30 saat, shot-by-shot sampai CTA) |
| 3 | `scriptwriter` | `02` | `03-script.md` (VO + teks skrin + caption + hashtag) |
| 4 | `voice-ai` | `03` | `04-voice.md` + audio VO |
| 5 | `video-transform` | footage aku + `02/03/04` | `05-video.md` + video siap, draf TikTok |

Jalankan semua sekali guna skill `/jual <nama produk>` — ia panggil agen satu-satu dan berhenti untuk aku approve di setiap gate.

## Tools yang dipakai
- **Higgsfield MCP** — gambar (`generate_image`), video (`generate_video`, Genjutsu `hf_mult_replace_object` / `hf_mult_motion_control`), 3D (`generate_3d`), suara (`create_voice`, `generate_audio`, `voice_change`), upload (`media_upload` → `media_confirm`), publish TikTok (`tiktok_prepare_publish`), skor viral (`virality_predictor`), lagu trending (`tiktok_music_trending`).
- **vidIQ MCP** — cari video outlier TikTok/IG (`vidiq_instagram_tiktok_outlier_search`), trend.
- **WebSearch / WebFetch** — riset produk & harga Shopee/TikTok Shop.
- **Kalodata** — tiada connector. Aku export CSV / screenshot dari kalodata.com dan letak dalam `produk/<slug>/kalodata/`. Agen 0 baca dari situ.
- **Shopee** — tiada API publish. Agen 5 export video 9:16 + caption; aku upload sendiri di Shopee Video / Shopee Live.

## Peraturan keras (semua agen)
1. **Kos kredit**: sebelum generate apa-apa yang guna kredit, buat `get_cost: true` dulu dan tunjuk kos. Jangan generate tanpa aku setuju. Jangan set `use_unlim` melainkan aku minta.
2. **Produk jangan dipalsukan**: tiada claim fungsi yang produk tak ada, tiada "hasil" AI (contoh kipas tiup salji). Demo fungsi mesti dari footage sebenar.
3. **Label AI**: setiap post TikTok tandakan AI-generated (`is_aigc`) dan disclosure affiliate/komersial. Caption Shopee pun sebut "#affiliate".
4. **Muka & suara**: hanya muka/suara aku sendiri atau karakter/voice preset AI. Jangan sesekali tiru muka atau suara orang sebenar (selebriti, influencer).
5. **Bahasa**: skrip default Bahasa Melayu santai (boleh campur slang/English sikit). Teks skrin pendek, besar, mudah baca.
6. Simpan semua job_id / media_id dalam fail `.md` produk supaya boleh sambung sesi lain.
