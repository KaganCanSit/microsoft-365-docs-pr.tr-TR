---
title: Eğitilebilir sınıflandırıcıları kullanmaya başlama
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
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Microsoft 365 sınıflandırıcı, çeşitli içerik türlerini tanımak için eğitebileceğiniz ve bakabileceği örnekler veren bir araçtır. Bu makalede, özel sınıflandırıcı oluşturma ve eğitme ve doğruluğu artırmak için bunları yeniden eğitme hakkında bilgi verilmektedir.
ms.openlocfilehash: d3a7639ed31dc42688cffbffb151049659a41660
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173195"
---
# <a name="get-started-with-trainable-classifiers"></a>Eğitilebilir sınıflandırıcıları kullanmaya başlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

eğitilebilir Microsoft 365 sınıflandırıcı, çeşitli içerik türlerini tanımak için eğitebileceğiniz ve bakabileceği örnekler veren bir araçtır. Eğitildikten sonra, Office duyarlılık etiketlerinin, İletişim uyumluluk ilkelerinin ve bekletme etiketi ilkelerinin uygulanmasına yönelik öğeyi tanımlamak için kullanabilirsiniz.

Özel eğitilebilir bir sınıflandırıcı oluşturmak için öncelikle bu sınıflandırıcıya insan tarafından seçilen ve kategoriyle pozitif bir şekilde eşleşen örnekler verilmesi gerekir. Ardından, bunları işledikten sonra, sınıflandırıcıların tahmin etme becerisini test etmek için pozitif ve negatif örneklerin bir karışımını verirsiniz. Bu makalede, özel sınıflandırıcı oluşturma ve eğitme ve yeniden eğitme yoluyla özel eğitilebilir sınıflandırıcıların ve önceden eğitilmiş sınıflandırıcıların yaşam süreleri boyunca performansını artırma işlemleri gösterilmektedir.

Farklı sınıflandırıcı türleri hakkında daha fazla bilgi edinmek için bkz. [Eğitilebilir sınıflandırıcılar hakkında bilgi edinin](classifier-learn-about.md).

Eğitilebilir sınıflandırıcı oluşturmanın hızlı bir özeti için bu videoyu izleyin. Ayrıntıları almak için bu makalenin tamamını okumanız gerekir.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Önkoşullar

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Sınıflandırıcılar bir Microsoft 365 E5 veya E5 Uyumluluğu özelliğidir. Bu aboneliklerden yararlanmak için bu aboneliklerden birine sahip olmanız gerekir.

### <a name="permissions"></a>İzinler

Kullanıcı arabirimindeki sınıflandırıcılara erişmek için: 

- Genel yöneticinin kiracının özel sınıflandırıcılar oluşturmasını kabul etmesi gerekir.
- Sınıflandırıcıyı eğitmek için Uyumluluk Yöneticisi rolü gereklidir.

Bu senaryolarda sınıflandırıcıları kullanmak için bu izinlere sahip hesaplara ihtiyacınız vardır:

- Bekletme etiketi ilkesi senaryosu: Kayıt Yönetimi ve Bekletme Yönetimi rolleri 
- Duyarlılık etiketi ilkesi senaryosu: Güvenlik Yöneticisi, Uyumluluk Yöneticisi, Uyumluluk Verileri Yöneticisi
- İletişim uyumluluk ilkesi senaryosu: Insider Risk Management Yöneticisi, Gözetmen Gözden Geçirme Yöneticisi 

> [!IMPORTANT]
> Varsayılan olarak, yalnızca özel sınıflandırıcı oluşturan kullanıcı söz konusu sınıflandırıcı tarafından yapılan tahminleri eğitebilir ve gözden geçirebilir.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Özel eğitilebilir sınıflandırıcı için hazırlanma 

Başlamadan önce özel eğitilebilir sınıflandırıcı oluşturma işleminin neleri içerdiğini anlamak yararlı olur. 

### <a name="timeline"></a>Zaman çizelgesi

Bu zaman çizelgesi eğitilebilir sınıflandırıcıların örnek dağıtımını yansıtır.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Eğitilebilir sınıflandırıcılar için ilk kez kabul etmek gerekir. Microsoft 365 kuruluş içeriğinizin temel değerlendirmesini tamamlaması on iki gün sürer. Kabul işlemini başlatması için genel yöneticinize başvurun.

### <a name="overall-workflow"></a>Genel iş akışı

Özel eğitilebilir sınıflandırıcılar oluşturmanın genel iş akışı hakkında daha fazla bilgi edinmek için bkz. [Özel eğitilebilir sınıflandırıcılar oluşturmak için süreç akışı](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>Tohum içeriği

Eğitilebilir bir sınıflandırıcının bir öğeyi belirli bir içerik kategorisinde olduğu gibi bağımsız ve doğru bir şekilde tanımlamasını istediğinizde, önce bu öğeyi kategorideki içerik türünden birçok örnekle sunmanız gerekir. Örneklerin eğitilebilir sınıflandırıcıya beslenmesi *, tohumlama* olarak bilinir. Tohum içeriği bir insan tarafından seçilir ve içerik kategorisini temsil etmek üzere değerlendirilir.

> [!TIP]
> En az 50 pozitif örnek ve 500 kadar olması gerekir. Eğitilebilir sınıflandırıcı en son oluşturulan 500 örneği (dosya tarafından oluşturulan tarih/saat damgasına göre) işler. Ne kadar çok örnek sağlarsanız sınıflandırıcının yapacağı tahminler de o kadar doğru olur.

### <a name="testing-content"></a>İçeriği test etme

Eğitilebilir sınıflandırıcı bir tahmin modeli oluşturmak için yeterli pozitif örneği işledikten sonra, sınıflandırıcının kategoriyle eşleşen öğelerle eşleşmeyen öğeler arasında doğru ayrım yapıp yapamadığını görmek için yaptığı tahminleri test etmeniz gerekir. Bunu yapmak için, kategoriye dahil edilmesi gereken örneklerden ve seçmeyecek örneklerden oluşan, daha büyük ve insan tarafından seçilmiş başka bir içerik kümesi seçersiniz. İlk sağladığınız ilk tohum verilerinden farklı verilerle test etmelisiniz. Bunları işledikten sonra sonuçları el ile gözden geçirip her tahminin doğru, yanlış veya emin olmadığınızı doğrularsınız. Eğitilebilir sınıflandırıcı, tahmin modelini geliştirmek için bu geri bildirimi kullanır.

> [!TIP]
> En iyi sonuçları elde için, test örnek kümenizde pozitif ve negatif eşleşmelerin eşit dağılımıyla en az 200 öğe kullanın.

## <a name="how-to-create-a-trainable-classifier"></a>Eğitilebilir sınıflandırıcı oluşturma

1. 50-500 arasında tohum içerik öğesi toplayın. Bunlar yalnızca eğitilebilir sınıflandırıcının sınıflandırma kategorisinde olduğunu pozitif olarak tanımlamasını istediğiniz içerik türünü güçlü bir şekilde temsil eden örnekler olmalıdır. Desteklenen dosya türleri için bkz. [SharePoint Sunucusu'nda varsayılan gezinilen dosya adı uzantıları ve ayrıştırılmış](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dosya türleri.

   > [!IMPORTANT]
   > Tohum kümenizdeki öğelerin kategoriye **güçlü** örnekler olduğundan emin olun. Eğitilebilir sınıflandırıcı, başlangıçta modelini, neyle kullandığınıza göre oluşturur. Sınıflandırıcı, tüm çekirdek örneklerinin güçlü pozitifler olduğunu varsayar ve bir örneğin kategoriyle zayıf mı yoksa negatif mi olduğunu anlamanın hiçbir yolu yoktur.

2. Tohum içeriğini *, yalnızca* tohum içeriğini tutmaya ayrılmış bir SharePoint Online klasörüne yerleştirin. Site, kitaplık ve klasör URL'sini not edin.

   > [!TIP]
   > Tohum verileriniz için yeni bir site ve klasör oluşturursanız, bu tohum verilerini kullanacak eğitilebilir sınıflandırıcıyı oluşturmadan önce bu konumun dizine alınması için en az bir saat bekleyin.

3. Uyumluluk yöneticisi veya güvenlik yöneticisi rolü erişimiyle Microsoft Purview uyumluluk portalında oturum açın ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalını</a> veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalVeri</a> >  **sınıflandırmasını** açın.

4. **Eğitilebilir sınıflandırıcılar** sekmesini seçin.

5. **Eğitilebilir sınıflandırıcı oluştur'u** seçin.

6. Bu eğitilebilir sınıflandırıcının tanımlamasını `Name` istediğiniz öğe kategorisinin ve `Description` alanları için uygun değerleri doldurun.

7. 2. adımdaki SharePoint Çevrimiçi site, kitaplık ve klasör URL'sini seçin. öğesini seçin `Add`.

8. Ayarları gözden geçirin ve öğesini seçin `Create trainable classifier`.

9. Eğitilebilir sınıflandırıcı 24 saat içinde tohum verilerini işler ve bir tahmin modeli oluşturur. Sınıflandırıcı durumu, `In progress` tohum verilerini işlerken kullanılır. Sınıflandırıcı, tohum verilerini işlemeyi bitirdiğinde, durumu olarak `Need test items`değişir.

10. Artık sınıflandırıcıyı seçerek ayrıntılar sayfasını görüntüleyebilirsiniz.

    > [!div class="mx-imgBorder"]
    > ![eğitilebilir sınıflandırıcı test için hazır.](../media/classifier-trainable-ready-to-test-detail.png)

11. En iyi sonuçlar için en az 200 test içeriği öğesi (en fazla 10.000) toplayın. Bunlar güçlü pozitifler, güçlü negatifler ve doğasında biraz daha az belirgin olan öğelerin bir karışımı olmalıdır. Desteklenen dosya türleri için bkz. [SharePoint Sunucusu'nda varsayılan gezinilen dosya adı uzantıları ve ayrıştırılmış](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dosya türleri.

12. Test içeriğini *yalnızca* test içeriğini tutmaya ayrılmış bir SharePoint Çevrimiçi klasörüne yerleştirin. SharePoint Çevrimiçi site, kitaplık ve klasör URL'sini not edin.

    > [!TIP]
    > Test verileriniz için yeni bir site ve klasör oluşturursanız, bu tohum verilerini kullanacak eğitilebilir sınıflandırıcıyı oluşturmadan önce bu konumun dizine alınması için en az bir saat bekleyin.

13. öğesini seçin `Add items to test`.

14. 12. adımdaki test içeriği sitesinin SharePoint Çevrimiçi site, kitaplık ve klasör URL'sini seçin. öğesini seçin `Add`.

15. sihirbazını seçerek `Done`tamamlayın. Eğitilebilir sınıflandırıcınızın test dosyalarını işlemesi bir saat kadar sürer.

16. Eğitilebilir sınıflandırıcı test dosyalarınızı işlemeyi bitirdiğinde ayrıntılar sayfasındaki durum olarak `Ready to review`değişir. Test örneği boyutunu artırmanız gerekiyorsa, eğitilebilir sınıflandırıcının ek öğeleri işlemesine izin verin ve seçin `Add items to test` .

    > [!div class="mx-imgBorder"]
    > ![ekran görüntüsünü gözden geçirmeye hazır.](../media/classifier-trainable-ready-to-review-detail.png)

17. Öğeleri gözden geçirmek için Sekme'yi seçin `Tested items to review` .

18. Microsoft 365 bir kerede 30 öğe gösterir. Bunları gözden geçirin ve `We predict this item is "Relevant". Do you agree?` kutuda veya öğesini `No` `Not sure, skip to next item`seçin`Yes`. Model doğruluğu her 30 öğeden sonra otomatik olarak güncelleştirilir.

    > [!div class="mx-imgBorder"]
    > ![öğeleri gözden geçir kutusu.](../media/classifier-trainable-review-detail.png)

19. *En az* 200 öğeyi gözden geçirin. Doğruluk puanı dengelendikten sonra **yayımlama** seçeneği kullanılabilir hale gelir ve sınıflandırıcı durumu olarak gösterilir `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![doğruluk puanı ve yayımlamaya hazır.](../media/classifier-trainable-review-ready-to-publish.png)

20. Sınıflandırıcıyı yayımlayın.

21. Sınıflandırıcınız yayımlandıktan sonra [duyarlılık etiketleriyle Office otomatik etiketlemede](apply-sensitivity-label-automatically.md) bir koşul olarak kullanılabilir, [bekletme etiketi ilkesini bir koşula göre](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) ve [İletişim uyumluluğuna](communication-compliance.md) göre otomatik olarak uygulayın.
