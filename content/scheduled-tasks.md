# Scheduled Tasks

## Uygulama ve Hizmet Günlükleri

Konum: `Microsoft > Windows > TaskScheduler`

- **106** - Görev oluşturuldu
- **140** - Görev güncellendi
- **141** - Görev silindi
- **200** - Görev çalıştırıldı
- **201** - Görev tamamlandı

## Security Loglarında

- **4698** - Görev oluşturuldu
- **4702** - Görev güncellendi
- **4699** - Görev silindi
- **4700** - Görev etkinleştirildi
- **4701** - Görev devre dışı bırakıldı

## Disk Artefaktı

- `C:\Windows\System32\Tasks\`
- `C:\Windows\SysWOW64\Tasks\`
- XML dosyası — içinde Action komutu düz metin okunur

## Şüpheli İşaretler

- Görev adı sistem adına benzemeye çalışıyor
- Action içinde **PowerShell -EncodedCommand**
- Çalışma dizini `%TEMP%` veya kullanıcı klasörü

