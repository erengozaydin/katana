# Project Discovery Katana: Kapsamlı Rehber

## Giriş

Katana, Project Discovery tarafından geliştirilen güçlü bir web crawling ve otomatik keşif aracıdır. Bu blog yazısında, Katana'nın tüm özelliklerini, parametrelerini ve kullanım senaryolarını detaylı bir şekilde inceleyeceğiz.

## Katana Nedir?

Katana, web uygulamalarının otomatik keşfi ve crawling işlemleri için tasarlanmış hızlı ve esnek bir araçtır. Go programlama dili ile yazılmıştır ve modern web uygulamalarını etkili bir şekilde tarayabilir.

## Kurulum

Katana'yı kurmak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

1. Go ile kurulum:
   ```
   go install github.com/projectdiscovery/katana/cmd/katana@latest
   ```

2. GitHub'dan indirme:
   ```
   git clone https://github.com/projectdiscovery/katana.git
   cd katana/cmd/katana
   go build .
   mv katana /usr/local/bin
   ```

3. Docker ile kullanım:
   ```
   docker pull projectdiscovery/katana:latest
   ```

## Temel Kullanım

Katana'nın en basit kullanımı şu şekildedir:

```
katana -u https://example.com
```

Bu komut, example.com sitesini crawl edecek ve bulunan URL'leri gösterecektir.

## Katana Parametreleri

Katana, çeşitli parametrelerle özelleştirilebilir. İşte en önemli parametreler ve açıklamaları:

1. `-u, --url string`: Crawl edilecek URL'i belirtir.
   Örnek: `katana -u https://example.com`

2. `-l, --list string`: Crawl edilecek URL'lerin bulunduğu dosya.
   Örnek: `katana -l urls.txt`

3. `-d, --depth int`: Crawling derinliği (varsayılan: 3).
   Örnek: `katana -u https://example.com -d 5`

4. `-c, --concurrent int`: Eşzamanlı istek sayısı (varsayılan: 10).
   Örnek: `katana -u https://example.com -c 20`

5. `-p, --proxy string`: Proxy URL'i.
   Örnek: `katana -u https://example.com -p http://127.0.0.1:8080`

6. `-o, --output string`: Sonuçları kaydetmek için dosya adı.
   Örnek: `katana -u https://example.com -o results.txt`

7. `-f, --field string`: Çıktıda gösterilecek alan (url, path, fqdn, vb.).
   Örnek: `katana -u https://example.com -f url,path`

8. `-fs, --field-separator string`: Çıktı alanları için ayırıcı (varsayılan: " ").
   Örnek: `katana -u https://example.com -f url,path -fs "|"`

9. `-j, --json`: JSON formatında çıktı.
   Örnek: `katana -u https://example.com -j`

10. `-nc, --no-color`: Renkli çıktıyı devre dışı bırakır.

11. `-silent`: Sadece sonuçları gösterir, banner ve diğer bilgileri gizler.

12. `-v, --verbose`: Ayrıntılı çıktı modu.

13. `-version`: Katana sürümünü gösterir.

## Gelişmiş Özellikler ve Parametreler

1. `-jc, --js-crawl`: JavaScript dosyalarından URL çıkarma.
   Örnek: `katana -u https://example.com -jc`

2. `-ct, --crawl-duration duration`: Crawling süresi sınırı.
   Örnek: `katana -u https://example.com -ct 5m`

3. `-kf, --known-files string`: Bilinen dosya/dizinlerin listesi.
   Örnek: `katana -u https://example.com -kf files.txt`

4. `-mrs, --max-response-size int`: Maksimum yanıt boyutu (bytes).
   Örnek: `katana -u https://example.com -mrs 10485760`

5. `-timeout int`: Zaman aşımı süresi (saniye).
   Örnek: `katana -u https://example.com -timeout 20`

6. `-retry int`: Başarısız istekler için yeniden deneme sayısı.
   Örnek: `katana -u https://example.com -retry 3`

7. `-delay duration`: İstekler arası bekleme süresi.
   Örnek: `katana -u https://example.com -delay 100ms`

8. `-aff, --automatic-form-fill`: Otomatik form doldurma.
   Örnek: `katana -u https://example.com -aff`

9. `-H, --header string[]`: Özel HTTP başlıkları.
   Örnek: `katana -u https://example.com -H "User-Agent: CustomBot"`

10. `-config string`: Özel yapılandırma dosyası.
    Örnek: `katana -u https://example.com -config custom-config.yaml`

## Kullanım Senaryoları

1. Basit Crawling:
   ```
   katana -u https://example.com
   ```

2. Derinlemesine Crawling:
   ```
   katana -u https://example.com -d 10 -c 50
   ```

3. JavaScript Dosyalarından URL Çıkarma:
   ```
   katana -u https://example.com -jc -o js_urls.txt
   ```

4. Özel Çıktı Formatı:
   ```
   katana -u https://example.com -f url,path,fqdn -fs "," -o custom_output.csv
   ```

5. Proxy Kullanımı ve Form Doldurma:
   ```
   katana -u https://example.com -p http://127.0.0.1:8080 -aff
   ```

6. Zaman Sınırlı Crawling:
   ```
   katana -u https://example.com -ct 10m -o timed_crawl.txt
   ```

7. Özel HTTP Başlıkları ile Crawling:
   ```
   katana -u https://example.com -H "User-Agent: CustomBot" -H "Authorization: Bearer token123"
   ```

## Katana'nın Güçlü Yönleri

1. Hız: Go dilinde yazılmış olması sayesinde çok hızlı çalışır.
2. Modern Web Desteği: JavaScript rendering ve form doldurma gibi modern web özelliklerini destekler.
3. Özelleştirilebilirlik: Çok sayıda parametre ile farklı senaryolara uyarlanabilir.
4. Entegrasyon: Diğer güvenlik araçlarıyla kolayca entegre edilebilir.

## Sınırlamalar ve Dikkat Edilmesi Gerekenler

1. Etik Kullanım: Katana'yı yalnızca izin verilen sistemlerde kullanın.
2. Kaynak Kullanımı: Yüksek derinlik ve eşzamanlılık ayarları, hedef sistemde yük oluşturabilir.
3. Yasal Uyarılar: Bazı web siteleri, otomatik crawling'i yasaklamış olabilir. robots.txt dosyasına dikkat edin.

## Sonuç

Katana, web uygulamalarının otomatik keşfi için güçlü ve esnek bir araçtır. Doğru parametrelerle kullanıldığında, güvenlik testleri, web uygulama analizi ve keşif aşamalarında çok değerli olabilir. Bu rehberde öğrendiklerinizle artık Katana'yı etkili bir şekilde kullanabilir ve web uygulamalarını daha derinlemesine analiz edebilirsiniz.

Unutmayın, her güçlü araç gibi Katana da sorumlu ve etik bir şekilde kullanılmalıdır. İyi keşifler!
