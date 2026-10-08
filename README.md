# Turcihan Yıldırım — portfolyo sitesi

Gastronomi, mekan ve etkinlik fotoğrafçısı Turcihan Yıldırım'ın tek sayfalık sitesi.
Düz HTML, CSS ve JavaScript; derleme adımı, paket yöneticisi ve bağımlılık yok.

## Klasörler

| Yer | Ne |
|---|---|
| `site/index.html` | Sitenin tamamı (HTML + CSS + JS tek dosyada) |
| `site/img/` | Fotoğraflar; her birinin `.jpg` ve `.webp` sürümü |
| `site/video/` | Reels videoları ve afiş (poster) kareleri |
| `site/og.jpg` | Sosyal medyada paylaşım görseli (1200x630) |
| `netlify.toml` | Netlify ayarı: yayın klasörü `site`, derleme komutu yok |

## Yerelde çalıştırma

```
py -m http.server 8750 --directory site
```

Sonra tarayıcıda `http://127.0.0.1:8750/` adresini açın.

## Doldurulması gereken yer tutucular

`site/index.html` içinde köşeli parantezle duruyorlar:

| Yer tutucu | Nerede | Ne yazılacak |
|---|---|---|
| `[SITE_ADRESI]` (3 yer) | `<head>`: canonical, `og:url`, `og:image` | Yayına alınan alan adı |
| `[MEKAN]` (55 yer) | `MEKANLAR` listesi | Her fotoğrafın çekildiği mekan adı |
| `[YORUM]`, `[MEKAN ADI]`, `[KİŞİ – GÖREV]` | Referans bölümü (şu an HTML yorumu içinde) | Gerçek müşteri yorumu gelince |

Ayrıca:

- **Formspree**: form `https://formspree.io/f/xabcdwxy` adresine gönderiyor.
  Kimliği değiştirmek için `index.html` içindeki form `action` değerini düzenleyin.
- **Mekan bağlantıları**: adresi henüz olmayan mekanlar `MEKAN_ADRESLERI`
  listesinde boş duruyor; adres yazıldığında isim kendiliğinden bağlantıya döner.

## Fotoğraf eklemek

1. Küçültülmüş `.jpg` kopyayı `site/img/` içine koyun (uzun kenar 1600 px, kalite 80).
2. Aynı adla bir `.webp` kopya üretin (`dosya.jpg` → `dosya.webp`).
3. `index.html` içindeki `isler` listesine satır ekleyin:
   `["img/dosya.jpg","Alt metin","menu"]` — kategori: `menu`, `mekan`, `etkinlik` ya da `reels`.

Orijinal, tam çözünürlüklü dosyaları depoya koymayın; `.gitignore` bunları dışarıda tutar.
