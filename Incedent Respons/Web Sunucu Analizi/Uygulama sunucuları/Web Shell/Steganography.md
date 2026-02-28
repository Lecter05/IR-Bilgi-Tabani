Burada zararlı kod herhangi bir görselin exif bilgisinin içerisine yerleştiriliyor ve PHP ile görselin exif bilgisi okunarak kod çalıştırılıyor.
![[Pasted image 20251102141733.png]]
exif_read_data() and preg_replace()  bunları ekstra olarak araman gerekebilir.

find "$WEBROOT" -type f \( -iname '*.jpg' -o -iname '*.jpeg' -o -iname '*.png' \) -print0 \
| xargs -0 -n1 exiftool -S -s -Make -Model -UserComment -ImageDescription \
| grep -Ei '^.*(eval|base64_decode|<\?php|system\(|exec\(|passthru|shell_exec|preg_replace).*$' -n
