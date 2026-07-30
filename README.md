# Runic DarkRP — Yükleme Ekranı

Garry's Mod sunucusunun bağlanma ekranı. `sv_loadingurl` ile gösterilir.

## Yayın

GitHub Pages üzerinden yayınlanıyor:

```
Settings → Pages → Source: Deploy from a branch → main / (root)
```

Adres: `https://efekank.github.io/runic-loading/`

Bu adres sunucunun `cfg/server.cfg` dosyasında:

```
sv_loadingurl "https://efekank.github.io/runic-loading/"
```

## Dosyalar

| | |
|---|---|
| `index.html` | Ekranın tamamı — stil ve mantık tek dosyada, harici bağımlılık yok |
| `background.jpg` | Arka plan, 1920×1080 |

Harici kaynak (font, script, CDN) **bilerek kullanılmadı**: yükleme ekranı
oyuncu bağlanırken açılıyor ve dış bir sunucu yavaşsa ekran boş kalırdı.

## Nasıl çalışıyor

GMod bu sayfayı açar ve aşağıdaki fonksiyonları **kendisi** çağırır; sayfa
sadece onları tanımlar:

```
GameDetails(sunucuAdi, sunucuURL, harita, maxOyuncu, steamid, gamemode)
SetFilesTotal(n)      -- indirilecek toplam dosya
SetFilesNeeded(n)     -- kalan dosya
DownloadingFile(ad)   -- su an inen dosya
```

`background.jpg` yüklenemezse sayfa hata vermez: koyu bir degrade ve kendi
yazı tabanlı başlığıyla çalışmaya devam eder.

## İpuçları

Alt kısımda dönen ipuçları `index.html` içindeki `tips` dizisinde. Sunucu
klasik DarkRP'den farklı çalıştığı için oyuncuyu en çok şaşırtan noktalar
seçildi — meslek alma, ölmeden meslek değiştirme, üretim ekonomisi.

Yeni ipucu eklemek için diziye bir satır yazmak yeterli; HTML etiketleri
(`<b>`) kullanılabilir.
