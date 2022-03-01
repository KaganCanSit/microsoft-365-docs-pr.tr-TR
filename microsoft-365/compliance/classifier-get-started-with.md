---
title: Eğitilebilir sınıflayıcılarla çalışmaya başlama
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
description: Sınıf Microsoft 365, çeşitli içerik türlerini tanımaya eğitip bak verilmesini sağlar. Bu makalede, özel bir sınıflandırıcıyı nasıl oluşturamaz ve eğitebilir ve doğruluk oranı artırmak üzere bunları nasıl yeniden kısıtlayabilirsiniz?
ms.openlocfilehash: 263791549e314a116f21231e8dc4cde5be380cb7
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005932"
---
# <a name="get-started-with-trainable-classifiers"></a>Eğitilebilir sınıflayıcılarla çalışmaya başlama

Aynı Microsoft 365 sınıfı belirtilebilir bir araçtır. Bu araç, çeşitli içerik türlerini tanımanız için onlara örnek vererek onlara bakmaları için eğitebilirsiniz. Eğitimden sonra, bu uygulamayı kullanarak hassaslık etiketlerinin, Office uyumluluk ilkelerinin ve bekletme etiketi ilkelerinin uygulamasını tanımlayabilirsiniz.

Önce özel bir eğitilebilir sınıflandırıcı oluşturma işlemi, bu sınıfa insan tarafından alınan ve kategoriyle pozitif olarak uygun olan örnekler verilmesini içerir. Ardından, bu örnekleri işledikten sonra, sınıflayıcıların tahmin etme yeteneğini sınamak için pozitif ve negatif örnekler karma olarak hazırlarsiniz. Bu makalede, özel bir sınıflandırıcıyı nasıl oluşturamaz ve eğitebilir, yeniden kısıtlayıcı aracılığıyla özel eğitilebilir sınıflayıcılarla ön eğitimcilerin yaşam süresi boyunca performansını nasıl artırabilirsiniz.

Farklı sınıflandırıcı türleri hakkında daha fazla bilgi edinmek için bkz [. Eğitilebilir sınıflandırıcılar hakkında bilgi öğrenin](classifier-learn-about.md).

Eğitilebilir sınıflandırıcı oluşturmanın hızlı bir özeti için bu videoyu izleyin. Yine de ayrıntıları almak için bu makalenin tamamını okumalısiniz.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Önkoşullar

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Sınıflandırıcılar, E5 Microsoft 365 E5 uyumluluk özelliğidir. Bu aboneliklerden birini kullanmak için bu aboneliklerden birini kullanasınız.

### <a name="permissions"></a>İzinler

Kullanıcı arabiriminde sınıflayıcılara erişmek için: 

- Genel yöneticinin özel sınıflayıcılar oluşturmak için kiracıya katılmasını tercih olması gerekir.
- Sınıflandırıcıyı eğitmek için Uyumluluk Yöneticisi rolü gereklidir.

Bu senaryolarda sınıflayıcıları kullanmak için bu izinlere sahip hesaplara ihtiyacınız vardır:

- Bekletme etiketi ilkesi senaryosu: Kayıt Yönetimi ve Bekletme Yönetimi rolleri 
- Duyarlılık etiketi ilkesi senaryosu: Güvenlik Yöneticisi, Uyumluluk Yöneticisi, Uyumluluk Veri Yöneticisi
- İletişim uyumluluğu ilkesi senaryosu: Insider Risk Yönetimi Yöneticisi, Gözetmen İnceleme Yöneticisi 

> [!IMPORTANT]
> Varsayılan olarak, yalnızca özel sınıflandırıcı oluşturan kullanıcı bu sınıflandırıcı tarafından yapılan tahminleri eğitip gözden geçirebilirsiniz.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Özel bir eğitilebilir sınıflandırıcıya hazırlanma 

Başlamadan önce, özel bir eğitilebilir sınıflandırıcı oluşturmanın ne işe yarar olduğunu anlamak yararlı olur. 

### <a name="timeline"></a>Zaman çizelgesi

Bu zaman çizelgesi, eğitilebilir sınıflayıcıların örnek bir dağıtımını yansıtıyor.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Eğitime uygun sınıflayıcılar için ilk kez kabul etmek gerekir. Kuruluş içeriğinizin temel Microsoft 365 tamamlanması on iki gün sürer. Kabul işleminin son haline geldi ve genel yöneticinize başvurun.

### <a name="overall-workflow"></a>Genel iş akışı

Özel eğitilebilir sınıflandırıcılar oluşturmanın genel iş akışı hakkında daha fazla bilgi için bkz. Müşteri eğitilebilir sınıflandırıcıları oluşturmak [için süreç akışı](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>İçerik içeriğine çekirdek

Eğitilebilir bir sınıflandırıcının belirli bir içerik kategorisi içinde olduğunu bağımsız olarak ve doğru bir şekilde tanımlaması için, önce bu öğeyi kategorideki içerik türünün birçok örneğiyle sunabilirsiniz. Eğitilebilir sınıflandırıcıya örnek besleme, çekirdekleme *olarak bilinir*. çekirdek içeriği bir insan tarafından seçilir ve içerik kategorisini temsil edecek şekilde değerlendirilmelidir.

> [!TIP]
> En az 50 pozitif örnek ve en çok 500 örnek gerekir. Eğitilebilir sınıflayıcı en son oluşturulan 500 örneği (dosya oluşturulmuş tarih/saat damgasına göre) işler. Ne kadar fazla örnek sağlarsa, sınıflandırıcının ne kadar çok tahminde yer alsa, o kadar doğru olur.

### <a name="testing-content"></a>İçeriği test etme

Eğitilebilir sınıflandırıcı bir tahmin modeli oluşturmak için yeterince pozitif örnek işledikten sonra, sınıflandırıcının kategoriyle eşleşmeen öğelerle doğru ayırt edilebilir olup olmadığını görmek için tahminlerini test etmek gerekir. Bunu yapmak için başka, umarız daha büyük, insan seçmesi gereken ve örneklerden oluşan ve kategori ve olmayacak örneklerden oluşan içerikler seçersiniz. İlk olarak sağlanan ilk çekirdek veriminde yer alan farklı verilerle test etmek gerekir. Bunlar işlemden sonra, sonuçları el ile ilerler ve her tahminin doğru, yanlış veya emin olmadığını doğrularsınız. Eğitilebilir sınıflayıcı, tahmin modelini geliştirmek için bu geri bildirimi kullanır.

> [!TIP]
> En iyi sonuçları elde etmek için, test örnek kümenize pozitif ve negatif eşleşmelerin bile bir dağılımıyla birlikte en az 200 öğe alın.

## <a name="how-to-create-a-trainable-classifier"></a>Eğitilebilir sınıflandırıcı oluşturma

1. 50-500 çekirdek içerik öğeleri arasında toplayın. Bunlar yalnızca, eğitilebilir sınıflayıcısının sınıflandırma kategorisinde olduğu gibi pozitif bir şekilde tanımlaması istediğiniz içerik türünü kesinlikle temsil eden örnekler olmalıdır. Desteklenen [dosya türleri için bkz. SharePoint Server'da varsayılan gezinilen](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dosya adı uzantıları ve ayrıştırıldı dosya türleri.

   > [!IMPORTANT]
   > Çekirdek kümenizin öğelerinin kategoriye yönelik **güçlü örnekler olduğundan** emin olun. Eğitilebilir sınıflandırıcı ilk olarak modeli, sınıfı sizin neyle olduğunu temel alarak inşa ediyor. Sınıflayıcı, tüm çekirdek örneklerinin güçlü pozitif olduğunu varsayarak, örneğin zayıf veya negatif bir kategoriyle eş olup olmadığını anlamanın hiçbir yolu yoktur.

2. Çekirdek içeriğini, yalnızca çekirdek SharePoint tutmak için ayrılmış bir SharePoint Online *klasörüne yazın*. Site, kitaplık ve klasör URL'sini not edin.

   > [!TIP]
   > Çekirdek verileriniz için yeni bir site ve klasör oluşturursanız, bu veri çekirdek verilerini kullanan eğitilebilir sınıflandırıcıyı oluşturmadan önce bu konumun dizine alındı olması için en az bir saat izin kullanın.

3. Uyumluluk yöneticisi veya Microsoft 365 uyumluluk merkezi yöneticisi rolü erişimiyle oturum açın ve portalda <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">veya Microsoft 365 Defender sınıflandırmasını</a> >  **açın**.

4. Eğitilebilir **sınıflayıcılar sekmesini** seçin.

5. **Eğitilebilir sınıflandırıcı oluştur'a seçin**.

6. Bu eğitilebilir sınıflandırıcının `Name` `Description` tanımlaması istediğiniz öğe kategorisinin ve alanlarının uygun değerlerini doldurun.

7. 2. SharePoint içerik sitesi içerik sitesi için çevrimiçi site, kitaplık ve klasör URL'sini seçin. 'yi seçin `Add`.

8. Ayarları gözden geçirin ve 'ı seçin `Create trainable classifier`.

9. 24 saat içinde, eğitilebilir sınıflayıcısı çekirdek verilerini işler ve bir tahmin modeli oluşturmaz. Sınıflandırıcı durumu, `In progress` çekirdek verilerini işlerken olur. Sınıflandırıcı, çekirdek verilerini işlemeyi bitirdikten sonra, durum olarak değişir `Need test items`.

10. Artık sınıflandırıcıyı seçerek ayrıntılar sayfasını görüntüleyebilirsiniz.

    > [!div class="mx-imgBorder"]
    > ![test için hazır, eğitilebilir sınıflandırıcı.](../media/classifier-trainable-ready-to-test-detail.png)

11. En iyi sonuçları elde etmek için en az 200 test içeriği öğelerini (en fazla 10.000) toplayın. Bunlar, güçlü pozitif, güçlü negatif ve bazıları da doğalarında biraz daha az belirgin olan öğelerin karışımı olmalıdır. Desteklenen [dosya türleri için bkz. SharePoint Server'da varsayılan gezinilen](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) dosya adı uzantıları ve ayrıştırıldı dosya türleri.

12. Test içeriğini yalnızca test içeriğini SharePoint ayrılmış bir SharePoint Online *klasörüne yazın*. Çevrimiçi site, SharePoint ve klasör URL'sini not alın.

    > [!TIP]
    > Test verileriniz için yeni bir site ve klasör oluşturursanız, bu veri çekirdek verilerini kullanan eğitilebilir sınıflandırıcıyı oluşturmadan önce bu konumun dizine alındı olması için en az bir saat izin kullanın.

13. 'yi seçin `Add items to test`.

14. 12 SharePoint test içeriği sitesinin çevrimiçi site, kitaplık ve klasör URL'sini seçin. 'yi seçin `Add`.

15. 'i seçerek sihirbazı tamamlayın `Done`. Eğitilebilir sınıflandırıcının test dosyalarını işlemesi bir saat kadar sürer.

16. Eğitilebilir sınıflandırıcı test dosyalarınızı işlemeyi bitir olduğunda, ayrıntılar sayfasındaki durum olarak değişir `Ready to review`. Test örnek boyutunu artırmanız gerekirse, eğitilebilir sınıflandırıcının `Add items to test` ek öğeleri işlemesine izin ver'i seçin.

    > [!div class="mx-imgBorder"]
    > ![ekran görüntüsünü gözden geçirmeye hazır.](../media/classifier-trainable-ready-to-review-detail.png)

17. Öğeleri gözden `Tested items to review` geçirmek için Sekme'yi seçin.

18. Microsoft 365 bir defada 30 öğe gösterir. Bunları gözden geçirebilirsiniz ve kutuda `We predict this item is "Relevant". Do you agree?` ya da `Yes` ya da ' seçin `No` `Not sure, skip to next item`. Model doğruluğu her 30 öğeden sonra otomatik olarak güncelleştirilir.

    > [!div class="mx-imgBorder"]
    > ![öğeleri gözden geçir kutusu.](../media/classifier-trainable-review-detail.png)

19. En *az* 200 öğe gözden geçirebilirsiniz. Doğruluk puanı sağlandıktan sonra, **yayımlama** seçeneği kullanılabilir hale gelecek ve sınıflandırıcı durumu şöyle olur `Ready to use`: .

    > [!div class="mx-imgBorder"]
    > ![doğruluk puanına sahip olur ve yayım yapmaya hazır olur.](../media/classifier-trainable-review-ready-to-publish.png)

20. Sınıflandırıcıyı yayımlama.

21. Sınıflandırıcınız yayımlandıktan sonra, duyarlılık etiketleriyle otomatik etiketleme [](apply-sensitivity-label-automatically.md)Office bir koşula dayalı olarak bekletme etiketi ilkesi otomatik olarak uygulama [](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) ve İletişim uyumluluğu içinde bir koşul olarak [kullanılabilir.](communication-compliance.md)
