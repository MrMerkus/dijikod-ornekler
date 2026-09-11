# 04 — Saat markası tanıtım sitesi (`saat/`)

Diğer üç örnek yerel esnaf sitesiydi. Bu dördüncüsü **onlardan bilerek farklı**: tek bir
ürünün etrafında kurulu, sinematik, lüks bir **marka tanıtım sayfası**. Müşteri adayına
"biz sadece esnaf sitesi yapmıyoruz" demek için var.

## Marka

- **Ad:** **Kadem** — İstanbul'da kurulmuş kurgusal bağımsız mekanik saat atölyesi.
- **Konum:** Karaköy, Perşembe Pazarı. Eski bir han katında atölye.
- **Tek ürün:** **Kadem Bosphorus 01** — 39 mm, paslanmaz çelik kasa, elle kurmalı
  mekanik kalibre, safir cam, 42 saat güç rezervi. Fiyat **48.500 ₺**. Yılda 120 adet.
- **Hikâye ekseni:** seri üretim değil, sayılı üretim. "Zamanı satın almazsınız,
  ona eşlik edersiniz."
- **Ton:** ölçülü, soğukkanlı, süssüz. Ünlem yok, "en iyi" yok, indirim dili yok.

## Kimlik

- **Palet:** derin gece mavisi `#0d1520`, çelik `#c8ccd4`, kadran sütü `#eae6dd`,
  vurgu şampanya altını `#c9a961`. Zemin koyu, sayfa boyunca koyu kalır.
- **Fontlar:** başlık **Cormorant Garamond** (400/600), gövde **Inter** (400/500).
  Google Fonts, `&display=swap`.
- **Favicon:** inline SVG data URI — altın çember içinde ince "K".
- İkonlar elle çizilmiş inline SVG, 1.5px çizgi.

## Hero — 3B sahne (zorunlu)

`00-3D-KATMAN.md` bütünüyle geçerli. Bu sitenin sahnesi **prosedürel bir kol saati**:

- Kasa: `CylinderGeometry`, fırçalanmış çelik görünümü (`MeshStandardMaterial`,
  `metalness .9`, `roughness .35`).
- Çerçeve (bezel): ince `TorusGeometry`, şampanya altını.
- Kadran: hafif içe gömülü silindir yüzeyi, süt rengi; 12 indeks çubuğu ince kutu
  geometrileriyle dizilir (tam saatlerde uzun, aralarda kısa).
- Akrep, yelkovan ve saniye: ince kutular; **kullanıcının gerçek saatini gösterir**
  ve saniye ibresi gerçek zamanda ilerler. Bu sitenin imzası budur.
- Safir cam: ince, saydam (`transparent`, `opacity .18`), hafif altın yansımalı.
- Kayış ucu ima edilir (iki kısa koyu kutu), tam kayış modellenmez.
- Sahne yavaşça kendi ekseninde salınır (±18°), fareyle çevrilebilir.
- Arka planda kadranın altından yükselen tek bir sıcak vurgu ışığı.
- Gölge haritası kapalı, üç ışık sınırı geçerli.

Hero metni canvas'ın üstünde HTML olarak: `<h1>` "Kadem Bosphorus 01", altında tek
cümlelik iddia, iki buton — **"Saati incele"** (sayfa içi bağlantı) ve **"Atölyeye yazın"**
(WhatsApp).

## Bölümler (sırayla)

1. **Hero** — yukarıdaki 3B sahne.
2. **Manifesto** — üç kısa paragraf, seri üretim eleştirisi değil, sabır üzerine.
   Perspektifli girişle açılır.
3. **Anatomi** — saatin beş parçası (kasa, kalibre, kadran, safir cam, kayış), her biri
   eğilen kart; kartta parça adı, tek cümle ve teknik değer. Fotoğraf tutucusu var.
4. **Kalibre** — teknik tablo: çap 39 mm, kalınlık 10,2 mm, kalibre KDM-01 elle kurmalı,
   güç rezervi 42 saat, frekans 21.600 A/s, su geçirmezlik 50 m, cam safir,
   kayış İtalyan vidalası derisi, garanti 5 yıl.
5. **Atölye** — Karaköy atölyesinden görsel şeridi (parallax katmanlı), üç fotoğraf
   tutucusu ve iki kısa alıntı.
6. **Sayılı üretim** — yılda 120 adet vurgusu, sıra numarası fikri, bekleme listesi
   çağrısı.
7. **Sahiplik** — fiyat `48.500 ₺`, ne dahil (kutu, sertifika, 5 yıl garanti, ömür boyu
   bakım), nasıl alınır (atölye randevusu veya WhatsApp).
8. **Atölyeyi ziyaret** — adres (Perşembe Pazarı Cd. No: 00, Karaköy / Beyoğlu, İstanbul),
   randevu esaslı çalışma saatleri tablosu ve **canlı durum rozeti**
   (`00-ORTAK-TEKNIK.md` §6 — Pzt–Cum 10:00–18:00, Cmt 11:00–16:00, Paz kapalı),
   telefon `0212 XXX XX XX`, harita bağlantısı.
9. **Altbilgi** — marka satırı, KVKK/gizlilik yer tutucu bağlantıları, DijiKod imzası.

## Dönüşüm

`00-ORTAK-TEKNIK.md` §5 aynen geçerli: sabit WhatsApp butonu (markanın altın rengiyle,
özel çizilmiş SVG), mobilde alt sabit çubuk (**Ara** ve **Yol Tarifi**), 48×48px dokunma
hedefleri, `100svh`. WhatsApp ön yazısı: "Merhaba, Bosphorus 01 için bekleme listesi
hakkında bilgi almak istiyorum."

## Fotoğraf sözleşmesi — `saat/gorseller/OKU.md` dosyasına aynen yaz

| Dosya | Oran | Ne |
| --- | --- | --- |
| `og.jpg` | 1200×630 | Paylaşım kapağı: koyu zeminde saat |
| `anatomi-kasa.jpg` | 1:1 | Kasa yakın çekim |
| `anatomi-kalibre.jpg` | 1:1 | Hareket mekanizması, açık kasa arkası |
| `anatomi-kadran.jpg` | 1:1 | Kadran detayı, indeksler |
| `anatomi-cam.jpg` | 1:1 | Safir camda yansıma |
| `anatomi-kayis.jpg` | 1:1 | Deri kayış dokusu |
| `atolye-1.jpg` | 3:2 | Tezgâh başında çalışma |
| `atolye-2.jpg` | 3:2 | Atölyeden genel görünüm |
| `atolye-3.jpg` | 3:2 | El aletleri, detay |

Fotoğraflar **henüz yok**. `00-ORTAK-TEKNIK.md` §2 geçerli: her görsel kutusu markanın
renklerinde degrade tutucu gösterir, üstünde ne geleceği ince harflerle yazar, sayfa
fotoğraf gelince zıplamaz.

## Yapısal veri

JSON-LD `Product` + `Organization`: ürün adı, marka Kadem, fiyat 48500 TRY,
`availability` `PreOrder`, üretici adresi. Ayrıca `LocalBusiness` olarak atölye adresi.

## Dosya

`saat/index.html` — tek dosya. `saat/gorseller/OKU.md` — fotoğraf sözleşmesi.
Bu sitenin 2B sürümü **yok**; sıfırdan 3B doğuyor.
