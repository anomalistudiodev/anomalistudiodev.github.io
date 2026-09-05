# Anomali Stüdyo — Site Dosyaları

> **Marka adı notu:** Resmi isim **"Anomali Stüdyo"** olarak belirlendi (sadece "Anomali" değil). Bunun sebebi: `anomali.com`, `anomali.io` ve `anomali.studio` gibi ana alan adları, ABD merkezli, $96M yatırım almış bir siber güvenlik/AI şirketi olan **Anomali Inc.** tarafından kullanılıyor — hatta onların iç araştırma ekibinin adı bile "Anomali Labs". Marka karışıklığını ve alan adı çakışmasını önlemek için "Stüdyo" ekini resmi isme dahil ettik. Alan adı ararken `anomalistudio.com`, `anomalistudyo.com`, `anomali.com.tr`, `.agency`, `.digital`, `.work` gibi seçenekleri bir kayıt firmasından (isim.com.tr, Namecheap, GoDaddy) doğrulayarak ilerleyin.

## İçerik
- `index.html` — Tüm site (HTML + CSS + JS tek dosyada). Tarayıcıda çift tıklayıp doğrudan açabilirsiniz.
- `admin.html` — İş yönetimi (talepler, görevler) ve site içerik editörü olan admin paneli. **Aşağıdaki "Admin paneli" bölümünü mutlaka okuyun — önemli sınırlamaları var.**
- `anomali-logo-dark-bg.svg` — Koyu zeminler için logo (beyaz yazı + mor nokta)
- `anomali-logo-light-bg.svg` — Açık zeminler için logo (siyah yazı + mor nokta)
- `anomali-icon-mark.svg` — Yalnızca amblem (favicon, sosyal medya profil fotoğrafı için kare ikon)

## Yayınlama
Her iki HTML dosyası da bağımsızdır, herhangi bir sunucu/derleme gerektirmez. Aşağıdakilerden birine yükleyip anında yayına alabilirsiniz:
- Netlify, Vercel, GitHub Pages (sürükle‑bırak yeterli)
- Kendi hosting'inizde `index.html` ve `admin.html`'i aynı klasöre koymanız yeterli

**Önemli:** Admin panelinin site içeriğini güncelleyebilmesi için (`localStorage` senkronizasyonu) her iki dosyanın da **aynı gerçek sunucu/domain üzerinden** açılması gerekir. Dosyaları bilgisayarınızda çift tıklayıp `file://` olarak açarsanız, tarayıcılar (özellikle Chrome) güvenlik nedeniyle bu senkronizasyonu engelleyebilir. Bunun için en basit yol: Netlify/Vercel gibi bir yere yükleyip oradan açmak, ya da yerel test için basit bir sunucu çalıştırmak (örn. `python3 -m http.server`).

Google Fonts (Space Grotesk, Plus Jakarta Sans) ve favicon internetten yüklendiği için siteyi açan kişinin internet bağlantısı olmalı.

## Admin paneli — çok önemli sınırlamalar
`admin.html` gerçek, güvenli bir "backend admin panel" **değildir** — bu tek bir statik HTML dosyası, sunucusuz bir ortamda çalıştığı için:

- **Şifre güvenli değildir.** Kullanıcı adı/şifre tarayıcının `localStorage`'ında düz metin olarak tutulur. Teknik bilgisi olan biri geliştirici araçlarından bunu görebilir. Gerçek/hassas bir sitede kullanmayın.
- **Veriler yalnızca o tarayıcıda yaşar.** Talepler, görevler ve içerik değişiklikleri sadece admin paneline giriş yaptığınız cihaz + tarayıcıda saklanır; başka bir cihazdan görüntülenemez, ekip arkadaşlarınızla paylaşılmaz, tarayıcı verileri temizlenirse kaybolur.
- **Gerçek çok kullanıcılı / production kullanım için** bir backend (sunucu + veritabanı) ve gerçek bir kimlik doğrulama sistemi gerekir. Bu dosyalar bunun **prototipi/demosu** olarak düşünülmeli — konsepti göstermek ve tek kişilik/tek cihazlı kullanım için işlevsel, ama kurumsal bir CRM'in yerini tutmaz.

**İlk giriş bilgileri:** kullanıcı adı `admin`, şifre `anomali2026` — Ayarlar sekmesinden değiştirebilirsiniz (yine yalnızca bu tarayıcı için geçerli olur).

### Admin panelinde neler var
- **Genel bakış** — talep/görev sayıları, son talepler
- **Talepler** — sitedeki iletişim formunu dolduran herkes otomatik olarak burada bir "lead" olarak birikir (Yeni / İletişimde / Kazanıldı / Kaybedildi durumları arasında taşıyabilirsiniz), elle de talep ekleyebilirsiniz
- **Görevler** — basit bir Yapılacak / Sürüyor / Tamamlandı panosu
- **Site içeriği** — e‑posta, telefon, adres, üst menüdeki durum rozeti ve hero açıklama metnini buradan değiştirip kaydedebilirsiniz; `index.html` aynı sunucudan açıldığında bu değerleri otomatik uygular
- **Ayarlar** — kullanıcı adı/şifre değiştirme, tüm yerel veriyi sıfırlama

## Yayına almadan önce mutlaka değiştirin
Aşağıdaki yerler örnek/placeholder içerik olarak bırakıldı, gerçek bilgilerinizle değiştirmeniz gerekiyor (admin panelinden veya doğrudan `index.html` kodundan):

| Ne | Nerede | Kod içinde arayın |
|---|---|---|
| E‑posta | İletişim bölümü + footer | `merhaba@anomali.studio` |
| Telefon | İletişim bölümü | `+90 (000) 000 00 00` |
| Adres | İletişim bölümü | `İstanbul, Türkiye` |
| Sosyal medya linkleri | Footer | `href="#"` (Instagram, X, LinkedIn, YouTube) |
| Fiyat hesaplayıcı rakamları | Hesaplayıcı bölümü | `data-price`, `data-days` özellikleri |
| "Yaklaşım örnekleri" kartları | Portfolyo bölümü | `KAVRAMSAL SENARYO` etiketli kartlar — gerçek projeleriniz oldukça bunların yerine geçmeli |
| "2026 ALIM DÖNEMİ: AÇIK" rozeti | Üst menü | `status-pill` — güncel durumunuza göre güncelleyin |
| Admin şifresi | `admin.html` içinde ilk kullanım | Yukarıdaki "Admin paneli" bölümüne bakın |

## Öne çıkan interaktif özellikler
- **Fiyat hesaplayıcı** (`#hesapla`) — canlı bütçe/süre tahmini
- **Anomali Testi** (`#test`) — 3 soruluk mini quiz, ziyaretçiye hizmet önerisi çıkarıyor
- **Graffiti & Fikir Duvarı** — hikaye bölümünün altında, ziyaretçinin çizim bırakıp PNG olarak indirebildiği tuval
- **Hikaye terminali** — sayfa kaydırıldıkça kendiliğinden yazılan, canlı klavye yankısı yapan bir "erişim günlüğü"
- **Retro telsiz** — üzerine gelince cızırtı sesi çıkaran, tıklayıp "ANOMALİ" diye bağırarak (veya yazarak) gizli modu açan bir widget
- **Renk teması seçici** — üst menüdeki 4 nokta, vurgu rengini canlı değiştiriyor
- **Ses sistemi** — sağ alttaki düğme, hiçbir ses dosyası kullanmadan (Web Audio API) hover/tık/ambiyans sesleri üretiyor
- **Gizli mod ("Anomali Modu")** — sayfanın herhangi bir yerinde klavyeden `anomali` yazmak ya da retro telsizden bağırmak, büyük bir uyarı ekranıyla birlikte sürekli sloganların uçuştuğu bir moda geçiyor (tekrar yazarak, `Esc` ile ya da rozetteki "Kapat" butonuyla kapatılır)
- **Admin panel entegrasyonu** — iletişim formunu dolduran ziyaretçiler admin panelindeki "Talepler" listesine otomatik düşer

## Özelleştirme
Renk paleti dosyanın en başında `:root` içinde CSS değişkenleri olarak tanımlı (`--violet`, `--pink`, `--mint`, `--sun`, `--sky`, `--accent` vb.) — buradan tüm site genelinde renkleri değiştirebilirsiniz.

