# Zen Bahçe — Klinik Rehabilitasyon Oyun Sistemi

Hemipleji, Parkinson ve yüz felci için minimalist/Zen arayüzlü, tek dosyalık web uygulaması. Üç modül tek bir bahçe dünyasında birleşir; her modül seans içi metrikler üretir ve standart klinik skalalarla (UPDRS-III, Fugl-Meyer ÜE, House-Brackmann) eşlenen yönlendirici bir gösterge sunar.

## Modüller
- **Kum** (Parkinson): ritmik işitsel ipucu + tremor filtresi, geniş amplitüdlü yaylar (LSVT BIG mantığı).
- **Taş** (hemipleji): yüksek tekrarlı uzanma / kavrama, göreve yönelik motor eğitim.
- **Rüzgar** (yüz felci): ön kamera + MediaPipe FaceMesh ile mimik simetrisi; kontrollü ve simetrik hareketi ödüllendirir, zorlanmayı (sinkinezi riski) caydırır. Kullanıcının yüzü ekranda gösterilmez.

## Teknik
Tek `index.html`. Harici bağımlılık yalnızca MediaPipe (CDN):
`@mediapipe/face_mesh`, `@mediapipe/camera_utils`. Derleme adımı yok.

## GitHub Pages ile yayınlama
1. Yeni bir GitHub deposu oluştur (ör. `zen-bahce`).
2. `index.html` dosyasını deponun köküne yükle.
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch**, dal `main`, klasör `/ (root)`.
4. Birkaç dakika içinde site `https://<kullanıcı-adı>.github.io/zen-bahce/` adresinde yayınlanır.

> HTTPS otomatik olduğu için kamera (Rüzgar modülü) sorunsuz çalışır. Kamera yalnızca güvenli bağlamda (HTTPS veya localhost) açılır; dosyayı `file://` ile doğrudan açarsan kamera engellenir.

## Yerelde çalıştırma
Kamerayı yerelde denemek için basit bir sunucu yeterli:
```bash
python3 -m http.server 8000
# tarayıcıda: http://localhost:8000
```

## Notlar
- Skala eşlemeleri **yönlendiricidir, klinik tanı yerine geçmez.**
- Rüzgar modülü internet bağlantısı ister (MediaPipe CDN).
- Ayarlar panelinden zorluk, tempo ve girdi filtre gücü ayarlanabilir.
