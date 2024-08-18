# svstoweb
svs image file to virtual microscope webpage on Github page

 `.svs` resim tarama dosyasını `vips` kullanarak Deep Zoom Image (DZI) formatına dönüştürmek ve ardından bu çıktıyı GitHub üzerinde sanal mikroskop olarak paylaşmak. 
 
 Aşağıda, bu işlemi nasıl yapabileceğinizi  bir kılavuz mevcuttur.

 Projemizin çıktısı web sayfası olarak şu şekildedir:[ [https://github.com/metinciris/svgtoweb bakabilirsiniz.](https://metinciris.github.io/svgtoweb/)
](https://metinciris.github.io/svstoweb/)
## Adım Adım Kılavuz

### Gereksinimler

- **GitHub Hesabı:** GitHub'da bir hesap oluşturun.
- **GitHub Desktop:** [GitHub Desktop](https://desktop.github.com/) uygulamasını indirin ve kurun.
- **Metin Düzenleyici:** Visual Studio Code veya Notepad++ gibi bir metin düzenleyici kullanabilirsiniz.
- **VIPS:** VIPS kütüphanesi yüklü olmalıdır.
- **OpenSeadragon:** Sanal mikroskop için kullanacağımız JavaScript kütüphanesi.

### 1. VIPS ile DZI Formatına Dönüştürme

#### 1.1. VIPS Kurulumu

1. VIPS binaries dosyalarını [buradan](https://github.com/libvips/build-win64-mxe/releases) indirin.
2. Dosyayı bir klasöre çıkartın, örneğin `C:\vips`.
3. `C:\vips\bin` yolunu sistem PATH değişkeninize ekleyin. PATH değişkeninize eklemeyi bilmiyorsanız internette "PATH değişkeninize ekleme" arayın.

#### 1.2. SVS Dosyasını Dönüştürme

Komut istemini açarak aşağıdaki komutu çalıştırın (Python kurulu olması gereklidir, kurulu değilse en aşağıda "Ek açıklama VIPS ile DZI Formatına Dönüştürme" bakın):
svs dosyalarınızı şu dizine kaydedin C:\svs\
Dönüştürülmüş dosyalar şu dizinde oluşacaktır  C:\svs\output_folder 

```bash
cd C:\svs
vips dzsave file_name.svs output_folder\output
```

- `file_name.svs`: Dönüştürmek istediğiniz SVS dosyanızın adı.
- `output_folder\output`: DZI formatına dönüştürülmüş dosyaların kaydedileceği klasör.

Bu işlem, `output.dzi` dosyası ve `output_files` klasörünü oluşturacaktır.

### 2. Proje Klasörünü Hazırlayın

#### 2.1. Klasör Yapısı Oluşturun

Bilgisayarınızda bir proje klasörü oluşturun ve aşağıdaki yapıyı oluşturun:

```
my-microscope
│
├── index.html
└── output
    ├── output.dzi
    └── output_files/
```

- `output/`: VIPS ile dönüştürülmüş dosyalarınızı bu klasöre kopyalayın.

### 3. index.html Dosyasını Oluşturun

Aşağıdaki HTML kodunu `index.html` dosyasına yapıştırın:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Virtual Microscope</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/openseadragon/2.4.2/openseadragon.min.js"></script>
    <style>
        #openseadragon {
            width: 100%;
            height: 80vh;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <h1>Virtual Microscope</h1>
    <div id="openseadragon"></div>

    <script type="text/javascript">
        var viewer = OpenSeadragon({
            id: "openseadragon",
            prefixUrl: "https://cdnjs.cloudflare.com/ajax/libs/openseadragon/2.4.2/images/",
            tileSources: "output/output.dzi"
        });
    </script>
</body>
</html>
```

### 4. GitHub Reposu Oluşturma

#### 4.1. GitHub'da Yeni Repo Oluşturma

1. GitHub hesabınıza giriş yapın.
2. Sağ üst köşede bulunan `+` simgesine tıklayın ve `New repository` seçeneğine tıklayın.
3. Proje adını (örneğin, `my-microscope`) girin ve `Create repository` butonuna tıklayın.

#### 4.2. GitHub Desktop Kullanarak Projeyi Yükleyin

1. GitHub Desktop uygulamasını açın.
2. `File > New repository` seçeneğine gidin.
3. Proje adını ve yerel yolunu girin.
4. `Create repository` butonuna tıklayın.
5. Projenizi oluşturduktan sonra dosyalarınızı proje klasörüne kopyalayın.
6. GitHub Desktop uygulamasında `Current Repository` altında projenizi seçin.
7. Sağ altta bulunan `Commit to main` butonuna tıklayın.
8. `Publish repository` butonuna tıklayın ve ayarları yaparak projeyi GitHub'a yükleyin.

### 5. GitHub Pages Ayarları

1. GitHub'daki projenizin sayfasına gidin.
2. `Settings` sekmesine tıklayın.
3. Sol menüden `Pages` seçeneğine tıklayın.
4. `Source` bölümünde `main` branch'ini seçin ve `/root` klasörünü belirleyin.
5. `Save` butonuna tıklayın.

GitHub Pages sayfanız birkaç dakika içinde yayınlanacaktır. Yayınlanan sayfanın URL'si `https://<kullanıcı_adınız>.github.io/my-microscope/` formatında olacaktır.

Örnek çıktı: https://metinciris.github.io/sliv/

### ##############################################################################

### Ek açıklama Python kurulumu,  VIPS ile DZI Formatına Dönüştürme 

### A. Python Kurulumu

#### Adım 1: Python İndirin

1. Python'ın en son sürümünü [Python resmi web sitesi](https://www.python.org/downloads/) üzerinden indirin.
2. Windows için uygun olan `Python 3.x` sürümünü seçin.

#### Adım 2: Python Yükleyin

1. İndirilen kurulum dosyasını (`python-3.x.x.exe`) çalıştırın.
2. **"Add Python to PATH"** seçeneğini işaretleyin.
3. **"Install Now"** seçeneğine tıklayın ve kurulumu tamamlayın.

#### Adım 3: Kurulumu Kontrol Edin

Komut İstemini (`cmd`) açın ve aşağıdaki komutları çalıştırarak Python'ın düzgün yüklendiğini doğrulayın:

```bash
python --version
pip --version
```

### B. VIPS Kurulumu

#### Adım 1: VIPS Binaries İndirin

1. VIPS binaries dosyalarını [buradan](https://github.com/libvips/build-win64-mxe/releases) indirin.
2. En son sürümü seçin ve ZIP dosyasını indirin.

#### Adım 2: VIPS Dosyalarını Çıkartın

1. İndirilen ZIP dosyasını `C:\vips` gibi bir klasöre çıkartın.

#### Adım 3: VIPS'i Sistem PATH'ine Ekleyin

1. `C:\vips\bin` yolunu sistem PATH değişkeninize ekleyin:
   - `Bilgisayarım` üzerine sağ tıklayın ve `Özellikler` seçeneğine gidin.
   - `Gelişmiş sistem ayarları`na tıklayın ve ardından `Çevre Değişkenleri`ne girin.
   - `Sistem değişkenleri` altında, `Path` seçeneğini bulun ve `Düzenle`ye tıklayın.
   - `Yeni` butonuna tıklayarak `C:\vips\bin` yolunu ekleyin.

#### Adım 4: Kurulumu Kontrol Edin

Komut İstemini (`cmd`) açın ve aşağıdaki komutu çalıştırarak VIPS'in düzgün yüklendiğini doğrulayın:

```bash
vips --version
```

### C. SVS Dosyasını DZI Formatına Dönüştürme

1. Komut İstemini (`cmd`) açın.
2. SVS dosyanızın bulunduğu dizine gidin:

   ```bash
   cd C:\svs
   ```

3. Aşağıdaki komutu kullanarak SVS dosyanızı DZI formatına dönüştürün:

   ```bash
   vips dzsave file_name.svs output_folder\output
   ```

   - `file_name.svs`: Dönüştürmek istediğiniz SVS dosyanızın adı.
   - `output_folder\output`: Dönüştürülmüş DZI dosyalarının ve parçalarının kaydedileceği klasör.

Bu işlem sonucunda, `output.dzi` dosyası ve `output_files` klasörü oluşturulacaktır.

### D. Proje Dosyalarını GitHub'a Yükleme

1. DZI dosyalarını ve `output_files` klasörünü proje klasörünüze (`my-microscope`) kopyalayın.
2. GitHub Desktop kullanarak projeyi GitHub'a yükleyin ve GitHub Pages üzerinden yayınlayın.

Bu adımlar ile, SVS dosyanızı başarıyla DZI formatına dönüştürebilir ve GitHub üzerinde sanal mikroskop olarak paylaşabilirsiniz. Yardımcı olabileceğim başka bir konu varsa lütfen belirtin!

### Sonuç

Bu adımları takip ederek `.svs` dosyanızı DZI formatına dönüştürüp sanal mikroskop olarak görüntüleyen bir web sayfasını GitHub üzerinden oluşturup paylaşabilirsiniz.

Öenek başka gösterim: https://metinciris.github.io/sliv/
