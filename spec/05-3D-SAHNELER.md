# Hero 3B sahneleri — site site

`00-3D-KATMAN.md` bütün sahnelerin ortak kuralıdır. Bu dosya her sitenin **ne**
göstereceğini söyler. Bütün nesneler Three.js geometrileriyle prosedürel kurulur,
model dosyası indirilmez. Renkler her sitenin **mevcut paletinden** alınır, uydurma
renk eklenmez.

## kafe — Türk kahvesi fincanı

- **Fincan:** `CylinderGeometry`, ağzı tabanından geniş; süt beyazı seramik
  (`MeshStandardMaterial`, `roughness .6`, `metalness .05`).
- **Altın kenar:** fincanın ağzını saran ince `TorusGeometry`.
- **Kahve yüzeyi:** fincanın içinde koyu kahve renkli ince silindir, hafif parlak
  (`roughness .25`).
- **Tabak:** geniş ve çok ince `CylinderGeometry`, aynı seramik.
- **Kulp:** `TorusGeometry`'nin yarısı, fincanın yanında.
- **Buhar:** 20–30 küçük küre ya da sprite; yavaşça yükselip sönümlenir, döngüsel.
  Hafif tut, parçacık sistemi kurma.
- Sahne yavaşça kendi ekseninde döner, fareyle/dokunmayla yatayda çevrilebilir.

## kuafor — soyut akan saç telleri

Somut nesne değil; stüdyoya yakışan zarif bir soyutlama.

- **7–9 uzun ince kıvrımlı tüp:** `CatmullRomCurve3` ile eğri, `TubeGeometry` ile katı
  (`radialSegments` 6–8 yeterli).
- Her tüp farklı fazda **ağır ve akışkan** dalgalanır — eğrinin kontrol noktaları
  zamanla hafifçe kayar. Titrek olmayacak.
- **Malzeme:** sitenin altın/şampanya vurgusunda `MeshStandardMaterial`,
  `metalness .7`, `roughness .3`. Birkaç tel daha koyu tonda olsun ki derinlik doğsun.
- Teller ekranın **sağ yarısında** toplanır; sol yarı hero metni için boş kalır.
- Fareyle/dokunmayla çevrilebilir, bırakınca yavaş salınımına döner.

## restoran — kokteyl bardağı (Nar Teras)

- **Bardak:** ters `ConeGeometry` (martini kadehi siluetı), saydam cam
  (`transparent`, `opacity .25`, `roughness .05`, `metalness .1`).
- **Ayak ve taban:** ince `CylinderGeometry` + geniş ince silindir taban.
- **İçecek:** kadehin içinde nar kırmızısı koni, camdan hafif küçük.
- **Nar taneleri:** 5–7 küçük küre, içeceğin yüzeyinde toplanmış, koyu kırmızı,
  hafif parlak.
- **Süsleme:** ince bir çubuk (karıştırıcı) kadehin içinde eğik durur.
- Arkadan gelen sıcak gün batımı vurgusu camdan kırılır gibi görünsün (tek vurgu ışığı).
- Sahne yavaşça salınır, fareyle/dokunmayla çevrilebilir.

## saat — Kadem Bosphorus 01

Ayrıntılı tanım `04-saat.md` içindedir. Özeti: prosedürel kol saati; çelik kasa,
altın çerçeve, süt kadran, 12 indeks, **kullanıcının gerçek saatini gösteren** ve
gerçek zamanda ilerleyen ibreler, saydam safir cam, ima edilen kayış ucu.
