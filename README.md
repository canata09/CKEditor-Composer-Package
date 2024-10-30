Laragon içerisinde mevcut Composer'ı local projelerinizde kullanmak oldukça basit. Aşağıdaki adımları takip ederek Composer'ı projelerinizde kullanabilirsiniz:

1. **Laragon'u Açın**: Laragon'u başlatın ve ana pencerede projelerinizi yönetmeye başlayın.

2. **Yeni Proje Oluşturun veya Var Olan Projeyi Açın**: Laragon ana penceresinde "New" butonuna tıklayarak yeni bir proje oluşturabilir veya mevcut bir projeye geçebilirsiniz.

3. **Terminali Açın**: Proje dizinine gitmek için Laragon'un sağ alt köşesindeki "Terminal" butonuna tıklayın. Bu, proje dizininde bir komut istemcisi açacaktır.

4. **`composer.json`** Dosyasını Oluşturma
`autoload.php` dosyası, Composer ile proje yapılandırıldığında otomatik olarak oluşturulur. Bu dosyanın oluşması için belirli adımların izlenmesi gereklidir. İşte bu süreç:
Oluşturmak çin, terminalde projenizin kök dizinine gidin ve şu komutu çalıştırın:

```bash
composer init
```

Projenizin kök dizininde bir `composer.json` dosyası oluşturmalısınız. Bu dosya, projenizin bağımlılıklarını ve autoload ayarlarını tanımlar. Örnek bir içerik:

```json
{
    "require": {
        "ckeditor/ckeditor": "^4.21"
    },
    "autoload": {
        "psr-4": {
            "MyNamespace\\": "src/"
        }
    }
}
```

5. **Composer'ı Yükleme ve Kullanma**

- Eğer sisteminizde Composer yüklü değilse, [Composer resmi web sitesinden](https://getcomposer.org/) yükleme yapmalısınız.

6. **Paket Yükleme**

`composer.json` dosyanız hazırsa, terminalde projenizin kök dizinine gidin ve şu komutu çalıştırın:

```bash
composer install
```

Bu komut, `composer.json` dosyasındaki bağımlılıkları yükleyecek ve `vendor` klasörünü oluşturacaktır. Bu işlem sırasında:

- Gerekli paketler indirilecek.
- `vendor` dizini oluşturulacak.
- `vendor/autoload.php` dosyası otomatik olarak oluşturulacaktır.



7. **`composer update`**

Eğer daha önceden bir `vendor` dizini oluşturduysanız ve `composer.json` dosyanızda değişiklik yaptıysanız, `composer update` komutunu kullanarak paketlerinizi güncelleyebilir ve `autoload.php` dosyasını güncelleyebilirsiniz:

```bash
composer update
```

8. **Composer'ı Kontrol Edin**
Kurulumdan sonra, Composer'ın doğru bir şekilde kurulduğunu kontrol etmek için şu komutu çalıştırın:

```bash
composer --version
```


9. **Önemli Not**

`vendor/autoload.php` dosyasını değiştirmeye çalışmaktan kaçının. Bunun yerine, `composer.json` dosyanızı güncelleyerek yeni paketler ekleyebilir veya mevcut paketleri güncelleyebilirsiniz. Sonrasında terminalde şu komutu çalıştırarak autoload dosyasını güncelleyebilirsiniz:

```bash
composer dump-autoload
```

Bu, autoload dosyalarını yeniden oluşturur ve projenizin güncel durumunu yansıtır.





10. **Composer ile Paket Kurulumu:** Eğer henüz yapmadıysanız, terminal veya komut istemcisinde proje dizininize gidin ve gerekli paketleri yüklemek için Composer kullanın. Örneğin:
`index.php` dosyanızda, `vendor` klasöründeki Composer paketlerini kullanmak için öncelikle Composer'ın otomatik yükleyicisini (`autoload.php`) dahil etmeniz gerekir. Bu sayede projeye dahil ettiğiniz paketler otomatik olarak kullanılabilir hale gelecektir.

Aşağıdaki adımları izleyebilirsiniz:
   ```bash
   composer require paket-adi
   ```

11. **`index.php` Dosyasını Güncelleme:**
   `index.php` dosyanızda, en üstte `autoload.php` dosyasını dahil edin. Örneğin:

   ```php
   <?php
   require 'vendor/autoload.php';

   // Header bileşenini ekle
   include 'header.php';

   // Burada Composer ile yüklediğiniz paketleri kullanabilirsiniz
   use Some\Package\ClassName;

   // Footer bileşenini ekle
   include 'footer.php';
   ?>
   ```

12. **Paket Kullanımı:** İlgili paketlerin sınıflarını kullanarak kodunuzu yazabilirsiniz.

Bu şekilde, `vendor` klasöründeki tüm Composer paketlerini projenizde kullanabilirsiniz. Eğer spesifik bir paketle ilgili daha fazla yardıma ihtiyacınız olursa, o paketin dökümantasyonuna göz atmayı unutmayın.
