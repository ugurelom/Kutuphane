# 📚 Kütüphanem - Android PWA Kurulum Rehberi

## Uygulama Nedir?
Kütüphanem, kişisel kütüphanenizi yönetmenizi sağlayan bir Progressive Web App (PWA) uygulamasıdır.
Android telefonunuza gerçek bir uygulama gibi kurulabilir.

## Özellikler
- ✅ Kitap ekleme, düzenleme, silme
- ✅ Kitap kapağı fotoğrafından OCR ile bilgi çekme (AI destekli)
- ✅ Gerçek, taranabilir QR kod üretimi
- ✅ Canlı kamera ile QR kod tarama
- ✅ Arama ve filtreleme
- ✅ Ödünç verme/iade takibi
- ✅ Excel içe/dışa aktarım
- ✅ Veri giriş şablonu
- ✅ Çevrimdışı çalışma (temel özellikler)

---

## 🚀 Kurulum Yöntemleri

### Yöntem 1: GitHub Pages (Ücretsiz & Kolay) ⭐ ÖNERİLEN

1. **GitHub hesabı açın** (yoksa): https://github.com/signup

2. **Yeni repository oluşturun**:
   - https://github.com/new adresine gidin
   - Repository name: `kutuphane` yazın
   - "Public" seçin
   - "Create repository" tıklayın

3. **Dosyaları yükleyin**:
   - "uploading an existing file" linkine tıklayın
   - ZIP'ten çıkardığınız TÜM dosyaları sürükleyin:
     - `index.html`
     - `manifest.json`
     - `sw.js`
     - `icons/` klasörü (içindeki tüm PNG dosyalarıyla birlikte)
   - "Commit changes" tıklayın

4. **GitHub Pages'i etkinleştirin**:
   - Repository → Settings → Pages
   - Source: "Deploy from a branch"
   - Branch: `main` / `root`
   - Save tıklayın

5. **2-3 dakika bekleyin**, siteniz şu adreste yayınlanacak:
   ```
   https://KULLANICI_ADINIZ.github.io/kutuphane/
   ```

6. **Android'e kurun** (aşağıdaki "Android'e Kurulum" bölümüne bakın)

---

### Yöntem 2: Netlify (Sürükle-Bırak)

1. https://app.netlify.com adresine gidin
2. Ücretsiz hesap açın
3. "Sites" sayfasında "Deploy manually" bölümüne
4. ZIP'ten çıkardığınız klasörü sürükleyip bırakın
5. Otomatik bir URL alacaksınız (ör: `kutuphane-xyz.netlify.app`)

---

### Yöntem 3: Firebase Hosting

1. Firebase Console'da proje oluşturun
2. Firebase CLI kurun: `npm install -g firebase-tools`
3. `firebase init hosting` çalıştırın
4. Dosyaları `public/` klasörüne kopyalayın
5. `firebase deploy` çalıştırın

---

## 📱 Android'e Kurulum

Siteniz yayınlandıktan sonra:

1. **Chrome** tarayıcısında sitenizi açın
2. Sağ üstteki **⋮** (üç nokta) menüsüne dokunun
3. **"Ana ekrana ekle"** veya **"Uygulamayı yükle"** seçeneğine dokunun
4. İsmi onaylayın → **"Ekle"** / **"Yükle"**
5. Ana ekranınızda "Kütüphanem" ikonu belirecek! 🎉

Artık tam ekran, adres çubuğu olmadan, gerçek bir uygulama gibi çalışır.

---

## ⚙️ Teknik Notlar

### Veri Saklama
- Veriler telefonunuzun **localStorage**'ında saklanır
- Tarayıcı verilerini silmediğiniz sürece verileriniz güvendedir
- Excel'e düzenli yedekleme yapmanız önerilir
- İndirdiğiniz Excel dosyalarını Google Drive'a yükleyerek bulut yedekleme yapabilirsiniz

### OCR Özelliği
- Kitap kapağı fotoğrafından AI ile bilgi çekme özelliği
- İnternet bağlantısı gerektirir (Anthropic API kullanır)
- Claude.ai üzerinden çalıştırıldığında API anahtarı otomatik sağlanır
- Bağımsız kullanımda API anahtarı gerekebilir

### QR Kod
- Her kitaba gerçek, taranabilir QR kod üretilir
- Canlı kamera taramasıyla kitap aranabilir
- QR kod kitabın Kütüphane ID'sini içerir

### Çevrimdışı Kullanım
- Temel özellikler (kitap görüntüleme, arama, ödünç takibi) çevrimdışı çalışır
- OCR ve QR tarama için internet gerekir
- İlk yüklemeden sonra Service Worker sayesinde uygulama önbelleklenir

---

## 📁 Dosya Yapısı

```
kutuphane-pwa/
├── index.html          # Ana uygulama (tek dosya, tüm kod içeride)
├── manifest.json       # PWA manifest (uygulama bilgileri, ikonlar)
├── sw.js              # Service Worker (çevrimdışı destek)
├── README.md          # Bu dosya
└── icons/
    ├── icon-72.png
    ├── icon-96.png
    ├── icon-128.png
    ├── icon-144.png
    ├── icon-152.png
    ├── icon-192.png
    ├── icon-384.png
    └── icon-512.png
```

---

## 🔧 Sorun Giderme

**"Ana ekrana ekle" seçeneği görünmüyor:**
- HTTPS üzerinden eriştiğinizden emin olun (GitHub Pages otomatik sağlar)
- Chrome tarayıcı kullanın
- Sayfayı yenileyip tekrar deneyin

**Verilerim kayboldu:**
- Tarayıcı verilerini silmiş olabilirsiniz
- Düzenli Excel yedekleme yapın!

**OCR çalışmıyor:**
- İnternet bağlantınızı kontrol edin
- Claude.ai artifact ortamı dışında API anahtarı gerekebilir

**Kamera açılmıyor (QR tarama):**
- Tarayıcıya kamera izni verin
- HTTPS bağlantı gereklidir
