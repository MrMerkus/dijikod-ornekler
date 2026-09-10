# DijiKod — örnek siteler

Bu proje NemesesOS'a bağlıdır. Kimlik, ton ve hafıza protokolü için
`~/Documents/Benim yapay zeka sistemim/NemesesOS/CLAUDE.md` ve `🔮 zihin/Ruh.md` dosyalarını oku.

**Bu klasör:** kaynak kod, çalışan iş.
**Projenin beyni:** `~/Documents/Benim yapay zeka sistemim/NemesesOS/🏰 İş/dijikod-ornekler/`
kararlar, açık sorular ve öğrenilenler oraya yazılır, buraya değil.

## Çalışma protokolü

- **`AGENTS.md` bu dosyaya symlink'tir.** Codex ve Claude aynı kuralları okur; birini
  değiştirmek ikisini birden değiştirir. Symlink'i kopyaya çevirme.
- **Yarım kalan iş `backlog.md`'ye düşer.** Oturum işi bitiremeden kapanıyorsa nerede kaldığı
  ve sıradaki adım oraya tek satır yazılır. Biten satır silinmez, `backlog-log.md`'ye taşınır.
- **Arka plan araştırmaları `reports/` altına yazılır.** Alt ajanlara yaptırılan keşif ve
  doküman taraması oraya düşer, doğrudan koda girmez: önce okunur, sonra karar olur.

## Bu projenin sabitleri

- Her örnek site `<slug>/index.html` olarak **tek dosyadır**. Build aracı yok, npm yok.
- Fotoğraflar `<slug>/gorseller/` altında durur, dosya adları ve en-boy oranları
  `<slug>/gorseller/OKU.md` içinde sözleşme olarak yazılıdır. Baran klasörü doldurup
  üzerine kopyalayınca site kendiliğinden dolar, kodda satır değişmez.
- İşletmeler **kurgusaldır**; içerikte geçen gerçek ürün ve marka adları serbesttir.
- Yayın GitHub Pages. Klasörler taşınabilir kalır, müşteriye doğrudan verilebilir.
