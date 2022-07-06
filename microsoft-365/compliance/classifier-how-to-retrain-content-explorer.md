---
title: İçerik gezgininde bir sınıflandırıcıyı yeniden eğitme
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
description: İçerik gezgininde eğitilebilir bir sınıflandırıcıya geri bildirim sağlamayı öğrenin.
ms.openlocfilehash: bde570b8bbb104d7f89523eb12bd8b9ac9210ad7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637449"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>İçerik gezgininde bir sınıflandırıcıyı yeniden eğitme

Microsoft 365 eğitilebilir sınıflandırıcı, inceleyebileceğiniz örnekler vererek çeşitli içerik türlerini tanımak için eğitebileceğiniz bir araçtır. Eğitildikten sonra, Office duyarlılık etiketlerinin, iletişim uyumluluk ilkelerinin ve bekletme etiketi ilkelerinin uygulanmasına yönelik öğeleri tanımlamak için kullanabilirsiniz.

Bu makalede, özel eğitilebilir sınıflandırıcılara ek geri bildirim sağlayarak performansı nasıl artırabileceğiniz gösterilmektedir.

Farklı sınıflandırıcı türleri hakkında daha fazla bilgi edinmek için bkz. [Eğitilebilir sınıflandırıcılar hakkında bilgi edinin](classifier-learn-about.md).

Ayarlama ve yeniden eğitme işleminin hızlı bir özeti için bu videoyu izleyin. Ayrıntıları almak için bu makalenin tamamını okumanız gerekir.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]

> [!NOTE]
> Önceden eğitilmiş sınıflandırıcılar yeniden eğitilemez.

## <a name="permissions"></a>İzinler

Microsoft Purview uyumluluk portalı sınıflandırıcılara erişmek için:

- Sınıflandırıcıyı eğitmek için Uyumluluk yöneticisi rolü veya Uyumluluk Verileri Yöneticisi gereklidir

Bu senaryolarda sınıflandırıcıları kullanmak için bu izinlere sahip hesaplara ihtiyacınız vardır:

- Bekletme etiketi ilkesi senaryosu: Kayıt Yönetimi ve Bekletme Yönetimi rolleri 

## <a name="overall-workflow"></a>Genel iş akışı

> [!IMPORTANT]
> Exchange öğelerine bekletme etiketi ilkelerini otomatik olarak uygulamak için içerik gezgininde geri bildirim sağlarsınız ve sınıflandırıcıyı koşul olarak kullanırsınız. **Exchange öğelerine otomatik olarak bekletme etiketi uygulayan ve koşul olarak sınıflandırıcı kullanan bir bekletme ilkeniz yoksa, burada durun.**

Sınıflandırıcılarınızı kullanırken, yaptıkları sınıflandırmaların duyarlığı artırmak isteyebilirsiniz. Bunu, eşleşme olarak tanımladığı veya eşleşmediği belirlenen öğeler için yapılan sınıflandırmaların kalitesini değerlendirerek yaparsınız. Sınıflandırıcı için 30 değerlendirme yaptıktan sonra bu geri bildirimi alır ve otomatik olarak kendini yeniden eğiter.

Sınıflandırıcıyı yeniden eğitme işleminin genel iş akışı hakkında daha fazla bilgi edinmek için bkz. [Sınıflandırıcıyı yeniden eğitmek için süreç akışı](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Yeniden eğitilmeden önce sınıflandırıcının zaten yayımlanmış ve kullanımda olması gerekir.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>İçerik gezgininde bir sınıflandırıcıyı yeniden eğitme

1. Uyumluluk yöneticisi veya güvenlik yöneticisi rolü erişimiyle Microsoft Purview uyumluluk portalı oturum açın ve **Microsoft Purview uyumluluk portalı** >  **Veri sınıflandırması** > **İçerik gezginini** açın. 
2. **Etiketlere, bilgi türlerine veya kategorilere göre filtrele** listesinin altında **Eğitilebilir sınıflandırıcılar'ı** genişletin.

> [!IMPORTANT]
> Toplu öğelerin eğitilebilir sınıflandırıcılar başlığı altında görünmesi sekiz güne kadar sürebilir.

3. Bekletme etiketi ilkesini otomatik olarak uygularken kullandığınız eğitilebilir sınıflandırıcıyı seçin. Bu, geri bildirimde bulunmak için eğitilebilir sınıflandırıcıdır.

> [!NOTE]
> Bir öğenin **Bekletme etiketi** sütununda bir girdisi varsa, bu, öğenin olarak `match`sınıflandırıldığı anlamına gelir.  Bir öğenin **Bekletme etiketi** sütununda bir girdisi yoksa, bu öğe olarak `close match`sınıflandırıldığı anlamına gelir. Öğeler hakkında `close match` geri bildirim sağlayarak sınıflandırıcı duyarlılığını en iyi şekilde geliştirebilirsiniz. 

4. Bir öğe seçin ve açın.
 
 > [!TIP]
> Birden çok öğe hakkında aynı anda geri bildirim sağlamak için tümünü seçip komut çubuğunda **Sınıflandırmayı geliştir'i** seçebilirsiniz.

5. **Geri bildirim sağla'yı** seçin.
6. **Ayrıntılı geri bildirim** bölmesinde, öğe gerçek bir pozitifse **Eşleştir'i** seçin.  Öğe hatalı pozitifse, yani yanlış kategoriye dahil edilmişse Eşleşme **değil'i** seçin.
7. Öğeye daha uygun olacak başka bir sınıflandırıcı varsa, **Diğer eğitilebilir sınıflandırıcıları öner** listesinden bunu seçebilirsiniz. Bu, öğeyi değerlendirmek için diğer sınıflandırıcıyı tetikler.
8. değerlendirmenizi `match``not a match` göndermek ve diğer eğitilebilir sınıflandırıcıları önermek için **Geri bildirim gönder'i** seçin. Sınıflandırıcıya 30 geri bildirim örneği sağladığınızda otomatik olarak yeniden eğitilecektir. Yeniden eğitme bir ila dört saat sürebilir. Sınıflandırıcılar günde yalnızca iki kez yeniden eğitilebilir.

> [!IMPORTANT]
> Bu bilgiler kiracınızdaki sınıflandırıcıya gider, **Microsoft'a geri dönmez**.

9. **Eğitilebilir sınıflandırıcıları** açın.
10. İletişim uyumluluk ilkenizde kullanılan sınıflandırıcı **, Yeniden eğitim** başlığı altında görünür.

![yeniden eğitme durumunda sınıflandırıcı.](../media/classifier-retraining.png)

11. Yeniden eğitme tamamlandıktan sonra yeniden eğitmeye genel bakışı açmak için sınıflandırıcıyı seçin.

![sınıflandırıcı yeniden eğitme sonuçlarına genel bakış.](../media/classifier-retraining-overview.png)

12. Önerilen eylemi ve sınıflandırıcının yeniden eğitilmiş ve şu anda yayımlanmış sürümlerinin tahmin karşılaştırmalarını gözden geçirin.
13. Yeniden eğitme sonuçlarından memnunsanız **Yeniden yayımla'yı** seçin.
14. Yeniden eğitme sonuçlarından memnun değilseniz, İçerik Gezgini arabiriminde sınıflandırıcıya ek geri bildirim sağlamayı ve başka bir yeniden eğitim döngüsü başlatmayı seçebilir veya hiçbir şey yapmazsanız sınıflandırıcının şu anda yayımlanmış olan sürümü kullanılmaya devam eder. 

## <a name="details-on-republishing-recommendations"></a>Önerileri yeniden yayımlama ayrıntıları

Yeniden eğitilen sınıflandırıcıyı yeniden yayımlama veya daha fazla yeniden eğitme önerme önerisini nasıl formüle ettiğimiz hakkında küçük bilgiler aşağıdadır. Bu, eğitilebilir sınıflandırıcıların nasıl çalıştığının biraz daha derin bir şekilde anlaşılmasını gerektirir.

Yeniden eğitildikten sonra sınıflandırıcının performansını hem geri bildirim içeren öğelerde hem de sınıflandırıcıyı eğitmek için kullanılan öğelerde değerlendiririz. 

- Yerleşik modellerde sınıflandırıcıyı eğitmek için kullanılan öğeler, Microsoft tarafından modeli oluşturmak için kullanılan öğelerdir.
- Özel modeller için, sınıflandırıcının özgün eğitimde kullanılan öğeler test ve gözden geçirme için eklediğiniz sitelerdendir.

Yeniden eğitilen ve yayımlanan sınıflandırıcı için her iki öğe kümesindeki performans sayılarını karşılaştırarak yeniden yayımlamaya yönelik bir iyileştirme olup olmadığına ilişkin bir öneri sunuyoruz. 

## <a name="see-also"></a>Ayrıca bkz.

- [Eğitilebilir sınıflandırıcılar hakkında daha fazla bilgi edinme](classifier-learn-about.md)
- [SharePoint Server'da varsayılan gezinilen dosya adı uzantıları ve ayrıştırılmış dosya türleri](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
