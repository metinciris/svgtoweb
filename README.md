# svgtoweb
svg image file to virtual microscope webpage on Github page

Aşağıda, GitHub'da bir `.svg` dosyasını kullanarak sanal mikroskop web sayfası oluşturma ve paylaşma sürecini adım adım anlatan bir kılavuz bulunmaktadır. Bu kılavuz, Windows 10-11 kurulu bilgisayarlarda nasıl yapılacağını açıklamaktadır.

Örnek web sayfası: https://metinciris.github.io/sliv/

## Adım Adım Kılavuz

### Gereksinimler

- **GitHub Hesabı:** GitHub'da bir hesap oluşturun.
- **GitHub Desktop:** [GitHub Desktop](https://desktop.github.com/) uygulamasını indirin ve kurun.
- **Metin Düzenleyici:** Visual Studio Code veya Notepad++ gibi bir metin düzenleyici kullanabilirsiniz.
- **OpenSeadragon:** Sanal mikroskop için kullanacağımız JavaScript kütüphanesi.

### 1. Proje Klasörünü Hazırlayın

#### 1.1. Klasör Yapısı Oluşturun

Bilgisayarınızda bir proje klasörü oluşturun ve aşağıdaki yapıyı oluşturun:

```
my-microscope
│
├── index.html
└── assets
    └── images
        └── your-image.svg
```

- `index.html`: Ana HTML dosyası.
- `assets/images/`: `.svg` dosyanızı bu klasöre koyun.

#### 1.2. OpenSeadragon'u İndirin

[OpenSeadragon](https://openseadragon.github.io/) kütüphanesini kullanacağız. `index.html` dosyasında kullanmak üzere OpenSeadragon'un CDN bağlantısını ekleyeceğiz.

### 2. index.html Dosyasını Oluşturun

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
            tileSources: {
                type: 'image',
                url: 'assets/images/your-image.svg'
            }
        });
    </script>
</body>
</html>
```

- **Görsel Yolu:** `'assets/images/your-image.svg'` kısmını `.svg` dosyanızın yolu ile değiştirin.

### 3. GitHub Reposu Oluşturma

#### 3.1. GitHub'da Yeni Repo Oluşturma

1. GitHub hesabınıza giriş yapın.
2. Sağ üst köşede bulunan `+` simgesine tıklayın ve `New repository` seçeneğine tıklayın.
3. Proje adını (örneğin, `my-microscope`) girin ve `Create repository` butonuna tıklayın.

#### 3.2. GitHub Desktop Kullanarak Projeyi Yükleyin

1. GitHub Desktop uygulamasını açın.
2. `File > New repository` seçeneğine gidin.
3. Proje adını ve yerel yolunu girin.
4. `Create repository` butonuna tıklayın.
5. Projenizi oluşturduktan sonra dosyalarınızı proje klasörüne kopyalayın.
6. GitHub Desktop uygulamasında `Current Repository` altında projenizi seçin.
7. Sağ altta bulunan `Commit to main` butonuna tıklayın.
8. `Publish repository` butonuna tıklayın ve ayarları yaparak projeyi GitHub'a yükleyin.

### 4. GitHub Pages Ayarları

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

This project demonstrates how to create a virtual microscope using an SVG image and OpenSeadragon. You can explore the image in detail as if you're using a real microscope.

## Project Structure

```
my-microscope
│
├── index.html
└── assets
    └── images
        └── your-image.svg
```

## How to Run

1. Clone the repository to your local machine.
2. Open `index.html` in a web browser.

## GitHub Pages

The project is published on GitHub Pages and can be accessed via this [link](https://<username>.github.io/my-microscope/).

## Notes

- Replace `your-image.svg` with your own SVG file in the `assets/images` directory.
- You can use GitHub Desktop to manage and upload your files to GitHub.

---

This project is a simple demonstration of how to use OpenSeadragon for viewing SVG images on the web.
```

#### README_tr.md (Türkçe)

```markdown
# Sanal Mikroskop

Bu proje, bir SVG görüntüsünü ve OpenSeadragon'u kullanarak nasıl sanal mikroskop oluşturabileceğinizi gösterir. Görüntüyü gerçek bir mikroskop kullanıyormuş gibi detaylı inceleyebilirsiniz.

## Proje Yapısı

```
my-microscope
│
├── index.html
└── assets
    └── images
        └── your-image.svg
```

## Nasıl Çalıştırılır

1. Depoyu yerel makinenize klonlayın.
2. `index.html` dosyasını bir web tarayıcısında açın.

## GitHub Pages

Proje GitHub Pages üzerinde yayınlanmıştır ve şu [bağlantı](https://<kullanıcı_adı>.github.io/my-microscope/) üzerinden erişilebilir.

## Notlar

- `your-image.svg` dosyasını `assets/images` dizininde kendi SVG dosyanızla değiştirin.
- Dosyalarınızı GitHub'a yüklemek ve yönetmek için GitHub Desktop kullanabilirsiniz.

---

Bu proje, SVG görüntülerini web üzerinde görüntülemek için OpenSeadragon kullanımının basit bir gösterimidir.
```

### Sonuç

Bu adımları takip ederek `.svg` dosyanızı sanal mikroskop olarak görüntüleyen bir web sayfasını GitHub üzerinden oluşturup paylaşabilirsiniz. Eğer daha fazla yardıma ihtiyaç duyarsanız veya başka sorularınız varsa lütfen bildirin!

ÖRnek Çıktı: https://metinciris.github.io/sliv/
