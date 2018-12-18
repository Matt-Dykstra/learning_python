# GIT Rehberi

<img src="https://i.imgflip.com/xsdtv.jpg" width="300">

### Yeni bir depo oluşturmak

Yeni bir depo oluşturmak için, bir klasör oluşturup içerisinde

```git init```

komutunu çalıştırın.

### Bir depoyu kopyalamak

Yerel deponuzun çalışan bir kopyasını oluşturmak için

```git clone /yol/depo```

uzak sunucu kullandığımız durumda

```git clone kullaniciadi@sunucu:/yol/depo```

### Ekleme & teslim

Değişiklikleri belirtmek (Index'e eklemek) için

```
git add <dosyaadı>
git add *
```

temel git iş akışında bu ilk adımdır. Değişiklikleri depoya eklemek için

```git commit -m "Teslim mesajı"```

şimdi dosyalar HEAD'e eklendi, fakat henüz uzak deponuza değil.

### Değişiklikleri göndermek

Şimdi değişiklikleriniz yerel deponuzun HEAD'i içerisinde.

Bu değişiklikleri uzak deponuza göndermek için,

```git push origin master```

değişiklikleri uzak deponuzdaki göndermek istediğiniz dal'ı master ile değiştirin. 

Henüz uzak bir deponuz yoksa ve uzak depo eklemek istiyorsanız,

```git remote add origin <sunucu>```

şimdi değişikliklerinizi uzak sunucuya gönderebilirsiniz.

### Dallar ile çalışmak

Dallar farklı özellikleri ayrı ayrı geliştirmek için kullanılır. Yeni bir depo oluşturduğunuzda master "varsayılan" daldır. Diğer dallar geliştirildikten sonra master'a birleştirilir.

"feature_x" adıyla yeni bir dal oluşturup o dala geçmek için 

```git checkout -b feature_x```

master'a geri geçmek için

```git checkout master```

ve oluşturduğumuz dalı silmek için

```git branch -d feature_x```

bir dalı uzak deponuza göndermedikçe başkaları tarafından kullanılabilir olmaz

```git push origin <dal>```

### Güncelleme & birleştirme

En son değişiklikleri (commit) yerel deponuza almak için

```git pull```

komutunu çalıştırın. Bu değişiklikleri al (fetch) ve birleştir (merge) yapacaktır. Aktif dala (örn. master) başka bir dalı birleştirmek için 

```git merge <dal>```

her iki durumda da git değişiklikleri otomatik birleştirmeyi (auto-merge) dener. Maalesef, bu her zaman mümkün olmaz ve çakışmalarla (conflict) sonuçlanır. Git tarafından gösterilen dosyaları elle düzenleyerek bu çakışmaları birleştirmek size düşer. Değişikliklerden sonra, dosyaları eklemek için

```git add <dosyaadı>```

değişiklikleri birleştirmeden önce, önizleme yapmak için

```git diff <kaynak_dal> <hedef_dal>```

### Sürümlemek

Yazılım sürümleriniz için sürüm adı (tag) oluşturmanız tavsiye edilir. bu SVN'de de mevcut olan bilindik bir kavramdır. 1.0.0 adıyla bir sürüm numarası (tag) oluşturmak için

```git tag 1.0.0 1b2e1d63ff```

buradaki 1b2e1d63ff yayımlanacak yazılım sürümünüzün işlem numarasının ilk 10 karakteridir. İşlem kimlik numaralarını görmek için

```git log```

tekil olduğu sürece daha az işlem numarası da kullanabilirsiniz.

### Yerel değişiklikleri geri almak

Yanlış birşey yapmanız durumunda (tabi ki böyle şeyler hiç olmaz ;)) yerel değişiklikleri geri almak için

```git checkout -- <dosyaadı>```

bu değişikliklerinizi HEAD içerisindeki son içerik ile değiştirir. Index'e önceden eklenmiş değişiklikler ve yeni dosyalar korunacaktır.

Eğer tüm yerel değişiklik ve teslimlerinizi iptal etmek istiyorsanız, sunucudan en son kayıtları getirin ve yerel master dalınıza gösterin

```
git fetch origin
git reset --hard origin/master
```
