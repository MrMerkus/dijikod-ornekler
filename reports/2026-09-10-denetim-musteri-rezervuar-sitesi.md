# Denetim — Gömme Rezervuar Ustası (müşteri sitesi)

Tarih: 2026-09-10 · Dosya: `Google tag eklendi(kontrol et hata var mı diye.).html`, 1855 satır
Yöntem: Codex (`gpt-5.6-luna`, high) tam dosya denetimi; bulgular ana döngü tarafından
kaynak kodda tek tek doğrulandı. Doğrulanmayan iki iddia aşağıda ayrıca işaretlendi.

## Hemen düzelt

**1. Dönüşüm butonları gtag yüklenmezse tamamen ölür (satır 47–60).**
`gtag_report_conversion` `event_callback` tanımlıyor ama **`event_timeout` yok** ve fonksiyon
`return false` döndürüyor. Bağlantıların hepsi `onclick="return gtag_report_conversion(this.href)"`
ile bağlı, yani tıklama her durumda iptal ediliyor ve yönlendirme yalnızca callback'e kalıyor.
Reklam engelleyici, yavaş bağlantı veya googletagmanager erişilemezse callback hiç çalışmaz:
**telefon da WhatsApp da açılmaz.** Sitenin tek dönüşüm yolu bu butonlar; sessizce kaybedilen
müşteri buradan çıkar. Google'ın kendi kalıbında `'event_timeout': 2000` bulunur, burada
düşmüş. Düzeltme:

```js
gtag('event', 'conversion', {
  'send_to': 'AW-18265217831/EEkTCJ7DksQcEKe2xIVE',
  'value': 1.0, 'currency': 'TRY',
  'event_timeout': 2000,
  'event_callback': callback
});
```

**2. Aynı fonksiyon `target="_blank"`ı iptal ediyor.**
WhatsApp bağlantıları `target="_blank" rel="noopener"` taşıyor ama callback `window.location = url`
diyor — yani WhatsApp aynı sekmede açılıyor, ziyaretçi siteden çıkıyor. WhatsApp bağlantıları için
`window.open(url, '_blank', 'noopener')` kullanılmalı; `tel:` için mevcut hali doğru.

**3. Sayfada dört tane `<h1>` var** (satır 1270, 1316, 1341, 1364).
Hero slider'ında her slayt kendi `h1`'ini taşıyor. Bir sayfada tek `h1` olur; diğer üçü `h2` ya da
`p.hs-title` olmalı. Arama motoru açısından sayfanın konusu belirsizleşiyor.

**4. Domain yazımı kontrol edilmeli — muhtemel yazım hatası.**
`canonical`, `og:url`, `og:image` ve JSON-LD `url` alanlarının tamamı
`https://www.gommerezarvuarustasi.com/` adresini gösteriyor: **"rez-A-rvuar"**. Sitenin bütün
metninde kelime doğru biçimde "rezervuar" geçiyor. Kayıtlı alan adı gerçekten böyleyse sorun yok;
değilse site kendini var olmayan bir adrese işaret ediyor demektir ve **paylaşım görselleri,
canonical ve yapısal veri toptan bozuktur.** Baran'ın müşteriye tek soruyla doğrulaması gereken
madde budur.

**5. KVKK / consent yok.**
`gtag('consent', 'default', …)` çağrısı ve çerez bildirimi yok. Google Ads dönüşüm etiketi
ziyaretçi onayı alınmadan çalışıyor. Türkiye'de yerel esnaf sitesinde yaygın bir eksik ama
KVKK açısından açık. En azından `ad_storage` / `analytics_storage` için varsayılan `denied` ve
onay sonrası `update` kurulmalı.

## Düzeltilmeli

- **Ziyaretçi analitiği hiç yok.** Kurulan etiket `AW-18265217831`, yani **yalnızca Google Ads
  dönüşüm etiketi**. GA4 (`G-…`) yok: kaç kişi geliyor, nereden geliyor, hangi bölümde çıkıyor
  ölçülmüyor. Reklam veriliyorsa GA4 ayrıca kurulmalı; aynı `gtag` bloğuna ikinci bir `config`
  satırı yeter.
- **Ads kimliği ve dönüşüm etiketi hesapta doğrulanmalı.** `AW-18265217831/EEkTCJ7DksQcEKe2xIVE`
  değerlerinin gerçek hesaba ait olduğu Google Ads panelinden teyit edilmeli; yanlış label sessizce
  hiçbir dönüşüm kaydetmez.
- **Görsellere boyut ve `loading="lazy"` verilmemiş.** `resim1.png`, `mekanizma.jpg`,
  `su-kacirma.jpg`, `buton.jpg`, `hizmet-gorseli.jpg` ve altı marka logosu boyutsuz; sayfa
  yüklenirken içerik zıplıyor (CLS).
- **Slider erişilebilirliği.** Otomatik dönen hero'nun durdurma düğmesi yok, slayt durumları
  ekran okuyucuya bildirilmiyor, `:focus-visible` stili tanımsız.
- **JSON-LD alanları gerçek veriyle doldurulmalı** — `addressLocality` yalnızca "İstanbul",
  sokak/ilçe yok; `geo` koordinatları ve `openingHours` gerçek durumla eşleşmeli.

## İyi olur

- `meta keywords` (satır 13) hiçbir arama motorunda 2009'dan beri kullanılmıyor, silinebilir.
- Dekoratif inline SVG'lere `aria-hidden="true"` verilmeli.
- Arka planda dönen parçacık animasyonu sekme görünmezken durdurulmalı (`visibilitychange`).
- Güvenlik başlıkları (CSP, `X-Content-Type-Options`) sunucu tarafında eklenmeli — HTML içinden
  çözülmez, barındırma paneli işi.

## Codex'in doğrulanmayan iki iddiası

- **"Eksik görselleri yükle (satır 1221–1542)."** Yanlış alarm. Görseller `resim1.png`,
  `mekanizma.jpg` gibi **göreli yollarla** çağrılıyor; bize yalnızca HTML dosyası verildiği için
  yerelde bulunamıyorlar. Müşterinin sunucusunda yanlarında duruyorlarsa sorun yok. Canlı adres
  açılmadan bu madde ne doğrulanabilir ne çürütülebilir.
- **"CTA kontrastı yetersiz."** Ölçülmedi; sayısal kontrast oranı hesaplanmadan iddia olarak kalır.

## Sıradaki adım

Baran müşteriye tek soru sorar: **alan adı gerçekten `gommerezarvuarustasi.com` mu?** Cevap
geldikten sonra 1–3 numaralı maddeler tek oturumda düzeltilir; bunlar doğrudan telefon ve
WhatsApp dönüşümünü etkiliyor.
