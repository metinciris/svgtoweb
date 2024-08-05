# svgtoweb
svg image file to virtual microscope webpage on Github page

Anladım, `.svs` dosyasını `vips` kullanarak Deep Zoom Image (DZI) formatına dönüştürmek ve ardından bu çıktıyı GitHub üzerinde sanal mikroskop olarak paylaşmak istiyorsunuz. Aşağıda, bu işlemi nasıl yapabileceğinizi adım adım açıklayan bir kılavuz ve İngilizce ve Türkçe README dosyaları bulunmaktadır.

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
3. `C:\vips\bin` yolunu sistem PATH değişkeninize ekleyin.

#### 1.2. SVS Dosyasını Dönüştürme

Komut istemini açarak aşağıdaki komutu çalıştırın:

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

### İngilizce ve Türkçe README Dosyaları

#### README.md (English)

```markdown
# Virtual Microscope

This project demonstrates how to create a virtual microscope using a DZI image generated from an SVS file and OpenSeadragon. You can explore the image in detail as if you're using a real microscope.

## Project Structure

```
my-microscope
│
├── index.html
└── output
    ├── output.dzi
    └── output_files/
```

## How to Run

1. Clone the repository to your local machine.
2. Open `index.html` in a web browser.

## GitHub Pages

The project is published on GitHub Pages and can be accessed via this [link](https://<username>.github.io/my-microscope/).

## Notes

- The DZI file and the tiles in the `output_files` directory were generated using VIPS.
- You can use GitHub Desktop to manage and upload your files to GitHub.

---

This project is a simple demonstration of how to use OpenSeadragon for viewing DZI images on the web.
```

#### README_tr.md (Türkçe)

```markdown
# Sanal Mikroskop

Bu proje, bir SVS dosyasından üretilmiş DZI görüntüsünü ve OpenSeadragon'u kullanarak nasıl sanal mikroskop oluşturabileceğinizi gösterir. Görüntüyü gerçek bir mikroskop kullanıyormuş gibi detaylı inceleyebilirsiniz.

## Proje Yapısı

```
my-microscope
│
├── index.html
└── output
    ├── output.dzi
    └── output_files/
```

## Nasıl Çalıştırılır

1. Depoyu yerel makinenize klonlayın.
2. `index.html` dosyasını bir web tarayıcısında açın.

## GitHub Pages

Proje GitHub Pages üzerinde yayınlanmıştır ve şu [bağlantı](https://<kullanıcı_adı>.github.io/my-microscope/) üzerinden erişilebilir.

## Notlar

- `output_files` dizinindeki DZI dosyası ve parçalar VIPS kullanılarak oluşturulmuştur.
- Dosyalarınızı GitHub'a yüklemek ve yönetmek için GitHub Desktop kullanabilirsiniz.

---

Bu proje, DZI görüntülerini web üzerinde görüntülemek için OpenSeadragon kullanımının basit bir gösterimidir.
```

### Sonuç

Bu adımları takip ederek `.svs` dosyanızı DZI formatına dönüştürüp sanal mikroskop olarak görüntüleyen bir web sayfasını GitHub üzerinden oluşturup paylaşabilirsiniz.

ÖRnek Çıktı: https://metinciris.github.io/sliv/
