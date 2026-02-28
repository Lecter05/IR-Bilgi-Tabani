**Cross-Site Scripting (XSS)**

**cat access.log | grep -E "%3C|%3E|alert|script|src|cookie|onerror|document"**

**grep -Ei '(%3C|%3E|%22|%27|%28|%29|%2F|%5C|%60)' access.log.1** --> Encode edilmiş XSS İndikatörleri

**grep -Ei '(alert\(|prompt\(|confirm\(|document\.cookie|document\.location|window\.location|eval\(|setTimeout\(|setInterval\()' access.log.1** --> JavaScript Fonksiyonları