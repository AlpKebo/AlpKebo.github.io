# Kişisel Website — Mimari Plan

**Alp Küçükkebabçı** · Canlı site: https://alpkebo.github.io · Repo: https://github.com/AlpKebo/AlpKebo.github.io

## 1. Hangi linkler var?

| Link | Neden |
|---|---|
| GitHub (github.com/AlpKebo) | Projelerimin yaşadığı yer |
| LinkedIn | Profesyonel profilim |
| Instagram | Sosyal taraf |

Hepsi hero bölümünde minimal SVG ikonlar olarak duruyor — dağınık bir link listesi yerine tek bakışta görünen üç ikon.

## 2. Görsel plan

Konsept: **"mürekkep ve kağıt, koyu mavide"** — kişisel site bir portfolyo değil, bir imza gibi olmalı.

- **Tipografi öncelikli tasarım:** Sayfanın kahramanı dev serif (Georgia) isim; üzerinde açık tondan mavi-griye akan bir gradyan var. Destek metinleri daktilo hissi için monospace (Courier).
- **Renk paleti:** Koyu lacivert zemin (`#0e1a2b`), bir ton açık lacivert kartlar, açık gri-mavi metin. Tek palet, her bileşen (arka plan, kartlar, oyun) aynı değişkenlerden besleniyor.
- **Canlı arka plan:** Canvas üzerinde çizilen akan çizgiler fare hareketine hafifçe tepki veriyor — sayfa "nefes alıyor".
- **ASCII otoportre:** Sağdaki çerçeveli kartta duran portre statik bir resim değil; her karede sinüs dalgalarıyla yeniden hesaplanan üretken (generative) ASCII sanatı. Mürekkep suda dalgalanıyormuş gibi hareket ediyor.
- **Responsive:** 900px altında tek sütuna geçiyor, oyun kanvası ekrana göre ölçekleniyor.

## 3. Bana özel dokunuş: oynanabilir "otoportre"

Sloganım "I hide small games in the things I make" — site de bunu bizzat yapıyor:

- **Play →** butonuna basınca arka planı buğulayan bir pencerede **mürekkep temalı yılan oyunu** açılıyor.
- Oyun sitenin estetiğiyle aynı dili konuşuyor: yem bir ✦ yıldızı, yılan kuyruğa doğru solan mürekkep blokları, oyun bitince italik serif "fin." yazısı.
- **UX detayları:** Oyun açılır açılmaz yılan koşmaya başlamıyor — ilk yön tuşuna/kaydırmaya kadar bekliyor (kimse daha yönelemeden ölmesin). Klavye (ok tuşları + WASD), mobilde kaydırma destekli. En iyi skor `localStorage`'da saklanıyor. Escape, ✕ veya pencere dışına tıklamayla kapanıyor.

## 4. Teknik mimari

- **Tek dosya, sıfır bağımlılık:** Her şey `index.html` içinde — framework yok, kütüphane yok, harici istek yok. Sayfa aniden yükleniyor.
- **3 bağımsız modül** (IIFE olarak izole):
  1. Akan çizgi arka planı (canvas + `requestAnimationFrame`)
  2. Üretken ASCII portre (sinüs alanı → karakter yoğunluğu eşlemesi)
  3. Yılan oyunu (grid tabanlı durum makinesi: bekleme → oyun → oyun sonu)
- **Yayınlama:** GitHub Pages, `AlpKebo.github.io` reposundan otomatik deploy — `main`'e her push canlıya çıkıyor.
