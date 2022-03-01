---
title: İçerik gezgininde sınıflandırıcıyı yeniden sınırlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: İçerik gezgininde, eğitilebilir bir sınıflandırıcıya nasıl geri bildirim sağlay öğrenin.
ms.openlocfilehash: bbc724b94997a4668115314df0c627dcfa5ddc77
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021731"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>İçerik gezgininde sınıflandırıcıyı yeniden sınırlama

Aynı Microsoft 365 sınıfı belirtilebilir bir araçtır. Bu araç, çeşitli içerik türlerini tanımanız için onlara örnek vererek onlara bakmaları için eğitebilirsiniz. Eğitimden sonra, bu uygulamayı kullanarak hassaslık etiketlerini, iletişim uyumluluk Office ve bekletme etiketi ilkelerinin uygulama öğelerini tanımlayabilirsiniz.

Bu makalede, ek geri bildirim sağlayarak özel eğitilebilir sınıflayıcıların performansını nasıl geliştirebilirsiniz?

Farklı sınıflandırıcı türleri hakkında daha fazla bilgi edinmek için bkz [. Eğitilebilir sınıflandırıcılar hakkında bilgi öğrenin](classifier-learn-about.md).

Ayarlama ve yeniden kısıtlama işleminin hızlı bir özeti için bu videoyu izleyin. Yine de ayrıntıları almak için bu makalenin tamamını okumalısiniz.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Önceden eğitilmiş sınıflayıcılar yeniden kısıt kullanılamaz.

## <a name="permissions"></a>İzinler

Uyumluluk Merkezi'nde sınıflayıcılara Microsoft 365 için:

- Sınıflandırıcıyı eğitmek için Uyumluluk yöneticisi rolü veya Uyumluluk Veri Yöneticisi gereklidir

Bu senaryolarda sınıflayıcıları kullanmak için bu izinlere sahip hesaplara ihtiyacınız vardır:

- Bekletme etiketi ilkesi senaryosu: Kayıt Yönetimi ve Bekletme Yönetimi rolleri 

## <a name="overall-workflow"></a>Genel iş akışı

> [!IMPORTANT]
> öğeleri otomatik olarak uygulamak için içerik gezgininde, bekletme etiketi ilkelerini otomatik olarak uygulama hakkında geri Exchange sağlar ve sınıflandırıcıyı koşul olarak kullanır. **Öğeleri otomatik olarak bu öğeler Exchange e otomatik olarak ek alan ve koşul olarak sınıflandırıcı kullanan bir bekletme ilkeniz yoksa, burada durun.**

Sınıflayıcılarınızı kullana kadar, bu sınıflandırmaların yaparken duyarlığı artırmak da iyi olabilir. Bunu yapmak için, eşleşme olarak tanımlandı veya eşleşme değil olarak tanımlanan öğeler için yapılan sınıflandırmaların kalitesini değerlendirebilirsiniz. Sınıflandırıcı için 30 değerlendirme yaptıktan sonra, bu geri bildirimi alır ve kendini otomatik olarak yeniden kısıtlar.

Bir sınıflandırıcıyı yeniden kısıtlamanın genel iş akışı hakkında daha fazla bilgi için bkz [. Sınıflandırıcıyı yeniden sınırlamak için süreç akışı](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Sınıflandırıcının yeniden kısıtlanamaz olması için, önce yayımlanmış ve kullanımda olması gerekir.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>İçerik gezgininde sınıflandırıcıyı yeniden sınırlama

1. Uyumluluk yöneticisi veya Microsoft 365 uyumluluk merkezi rolü erişimiyle oturum açın ve **Microsoft 365 uyumluluk merkezi** >  **Data classificationContent** >  **explorer'ı açın**. 
2. Etiketlere **, bilgi türlerine veya kategorilere göre filtrele** listesinin altında, **Eğitilebilir sınıflayıcılar'ın kapsamını genişletin**.

> [!IMPORTANT]
> Birleştirilmiş öğelerin, eğitilebilir sınıflandırıcılar başlığı altında görünmesi sekiz gün kadar zaman alsa da, bu süre sekiz gün kadar sürer.

3. Bekletme etiketi ilkesine otomatik olarak uygula seçeneğinde, hangi sınıfı kullanabiliyorsunuz? Bu, geri bildirim vermek için eğitilebilir sınıflandırıcıdır.

> [!NOTE]
> Bir öğenin Bekletme etiketi **sütununda bir** girdisi varsa, bu öğenin bir .`match`  Bir öğenin Bekletme etiketi sütununda bir girdisi **yoksa,** bu öğenin bir olarak sınıflandırılmış olduğu anlamına gelir `close match`. Öğelerle ilgili geri bildirim sağlayarak sınıflandırıcı duyarlığı en iyi şekilde geliştirebilirsiniz `close match` . 

4. Bir öğeyi seçin ve açın.
 
 > [!TIP]
> Birden çok öğe hakkında aynı anda geri bildirim sağlamak için, öğenin hepsini seçin ve  ardından komut çubuğunda Sınıflandırmayı geliştir'i seçin.

5. Geri bildirim **sağla'ya seçin**.
6. Ayrıntılı **geri bildirim bölmesinde** öğe gerçekten pozitifse, Eşleşme'yi **seçin**.  Öğe hatalı pozitifse, yani yanlış kategoriye dahil edildiyse, Eşleşme **değil'i seçin**.
7. Öğe için daha uygun olan başka bir sınıflandırıcı varsa, Diğer eğitilebilir sınıflayıcıları önerin **listesinden bunu seçebilirsiniz** . Bu, öğeyi değerlendirmek için diğer sınıflandırıcıyı tetikler.
8. **Değerlendirmenizi , sınıflandırmaları** göndermek ve eğitilebilir `match``not a match` diğer sınıflayıcıları önermek için Geri bildirim gönder'i seçin. Sınıflandırıcıya 30 geri bildirim örneği sağladıklarında, otomatik olarak yeniden kısıtlar. Yeniden sınırlama bir ile dört saat kadar sürebilir. Sınıflayıcılar günde yalnızca iki kez yeniden kısıtlandı.

> [!IMPORTANT]
> Bu bilgiler kiracınızı sınıflandırıcıya gider, **Microsoft'a geri dönmez**.

9. **Eğitime uygun sınıflayıcılar'a açın**.
10. İletişim uyumluluğu ilkeniz içinde kullanılan sınıflandırıcı, Yeniden eğitim **başlığı altında** görünür.

![durumu yeniden kısıtlarken sınıflandırıcı.](../media/classifier-retraining.png)

11. Yeniden sınırlayıcı tamamlandıktan sonra, yeniden kısıtlayıcıya genel bakış için sınıflandırıcıyı seçin.

![sınıflandırıcı yeniden kısıtlayıcı sonuçlarına genel bakış.](../media/classifier-retraining-overview.png)

12. Önerilen eylemi ve sınıflandırıcının yeniden kısıtlanmış ve şu anda yayımlanmış sürümlerinin tahmin karşılaştırmalarını gözden geçirme.
13. Yeniden sınırlamanın sonuçlarından memnunsanız, Yeniden **yayımla'yı seçin**.
14. Yeniden sınırlamanın sonuçlarından memnun değilseniz, İçerik Gezgini arabiriminde sınıflandırıcıya ek geri bildirim sağlamayı ve başka bir yeniden kısıtlama döngüsü başlatmayı seçebilir veya herhangi bir şey yapmasanız da sınıflandırıcının şu anda yayımlanmış sürümü kullanılmaya devam eder. 

## <a name="details-on-republishing-recommendations"></a>Önerileri yeniden yayımlama hakkında ayrıntılar

Aşağıda, yeniden kısıtlanmış bir sınıf değiştiriciyi yeniden yayımlama veya daha fazla yeniden sınırlayıcı önerme önerisini nasıl formüle ekleymız konusunda biraz bilgi veznede bulunuz. Bunun için, eğitilebilir sınıflayıcıların nasıl çalışması hakkında biraz daha fazla bilgi gerekir.

Yeniden kısıtlayıcının performansını, hem geri bildirimle birlikte hem de özgün olarak sınıflandırıcıyı eğitmek için kullanılan öğeler üzerinde değerlendiririz. 

- Yerleşik modellerde, sınıflandırıcıyı eğitmek için kullanılan öğeler Microsoft tarafından modeli oluşturmak için kullanılan öğelerdir.
- Özel modellerde, özgün eğitimde kullanılan sınıflandırıcı, test ve gözden geçirme için eklettiricilerdendir.

Yeniden yayımlamada geliştirme olup olmadığı konusunda öneri sağlamak için, yeniden kısıtlanmış ve yayımlanmış sınıflandırıcı için her iki öğe kümesinde yer alan performans sayılarını karşılaştırıldığında. 

## <a name="see-also"></a>Ayrıca bkz.

- [Eğitilebilir sınıflayıcılar hakkında bilgi](classifier-learn-about.md)
- [SharePoint Server'da varsayılan gezinilen dosya adı uzantıları ve ayrıştırıldı dosya türleri](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)