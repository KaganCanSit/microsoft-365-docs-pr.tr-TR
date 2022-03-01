---
title: Pilot Microsoft 365 Defender olay yanıtı özelliklerini deneyin
description: Olaylarda öncelikleri belirlemek Microsoft 365 Defender yönetmek, soruşturmaları otomatikleştirmek ve tehdit algılamada gelişmiş arama kullanmak için olay yanıtı özelliklerini deneyin.
keywords: Microsoft 365 Defender deneyin, Microsoft 365 Defender deneyin, Microsoft 365 Defender, Microsoft 365 Defender laboratuvarına veya Microsoft 365 Defender  pilot, siber güvenlik, gelişmiş kalıcı tehdit, kurumsal güvenlik, cihazlar, cihaz, kimlik, kullanıcılar, veri, uygulamalar, olaylar, otomatik araştırma ve düzeltme, gelişmiş tarama
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 362e8360900f53d7bfc9eccf12d1107091860cb9
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015507"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Pilot Microsoft 365 Defender olay yanıtı özelliklerini deneyin

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, pilot ortam kullanarak olayla ilgili bir soruşturma ve yanıtını gerçekleştirme sürecindeki Microsoft 365 Defender [Adım 2'dir](eval-defender-investigate-respond.md). Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine](eval-defender-investigate-respond.md) bakın.

Benzetimi yapılan bir [saldırı için bir olay yanıtı gerçekleştirin](eval-defender-investigate-respond-simulate-attack.md), keşfetmeniz Microsoft 365 Defender özelliklerden bazıları:

|Özellik |Açıklama |
|:-------|:-----|
| [Olayları önceliklendirme](#prioritize-incidents) | Bundan sonra hangi olayları ele alamayacaklarını belirlemek için, olayları sırasına göre filtreleme ve sıralama kullanın. |
| [Olayları yönetme](#manage-incidents) | Doğru atamayı sağlamak, etiketler ve açıklamalar eklemek ve bir olayı çözmek için olay özelliklerini değiştirin. |
| [Otomatik araştırma ve yanıt](#examine-automated-investigation-and-response-with-the-action-center) | Güvenlik işlemleri ekibinin tehditlere daha verimli ve etkili bir şekilde müdahale edebilirim. İşlem merkezi, bekleyen düzeltme eylemlerini onaylama gibi olay ve uyarı görevleri için "tek bir cam bölmesi" deneyimidir. |
| [Gelişmiş av](#use-advanced-hunting) | Ağ'daki olayları önceden incelemek ve tehdit göstergeleriyle varlıkları bulmak için sorguları kullanın. Ayrıca, bir olayın soruşturması ve düzeltmesi sırasında gelişmiş avlar da kullanırsiniz. |


## <a name="prioritize-incidents"></a>Olayları önceliklendirme

Microsoft 365 Defender portalının hızlı **başlatılmasında Olaylar & veya >'den** olay <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sırasına Microsoft 365 Defender</a>. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Olay sırası örneği.":::

En **son olaylar ve uyarılar** bölümünde, alınan uyarı sayısının ve son 24 saat içinde oluşturulan olay sayısının grafiği gösterilir.

Olay listesini incelemek ve bunların atama ve soruşturmaya önemlerini önceliklendirmek için şunları şunlarıabilirsiniz: 

- Olayın farklı karakteristiklerini veya **etkileyen** varlıkları daha kolay şekilde takip etmek için özelleştirilebilir sütunları yapılandırabilirsiniz (Sütunları seç'i seçin). Bu, çözümleme için olayları önceliklendirme konusunda bilinçli bir karar alamanıza yardımcı olur.

- Belirli bir senaryoya veya tehdite odaklanmak için filtrelemeyi kullanın. Olay sırasında filtre uygulamak, acil dikkat gerektiren olayları belirlemeye yardımcı olabilir. 

Varsayılan olay kuyruğundan **Filtreler'i** seçerek, belirli  bir olay kümesi belirtebilirsiniz. Filtreler bölmesini görüntüleyin. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Olay sırası için filtreler bölmesi örneği.":::

Daha fazla bilgi için bkz [. Olayları önceliklendirme](incident-queue.md).

## <a name="manage-incidents"></a>Olayları yönetme

Olayları, Bir olayın Olay yönetme **bölmesinden** yönetebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Bir olayın Olayları yönet bölmesi örneği.":::

Bu bölmeyi, şu bölmede **yer alan Olayı** yönet bağlantısından görüntüleyebilirsiniz:

- Olay sırasındaki bir olayın Özellikler bölmesi.
- **Bir** olayın özet sayfası.

Olaylarınızı şöyle yönetebilirsiniz:

- Olay adını düzenleme

  Otomatik olarak atanan adı, güvenlik ekibinin en iyi yöntemlerine göre değiştirebilirsiniz.
  
- Olay etiketleri ekleme

  Güvenlik ekibimizin olayları sınıflandırmak için kullandığı etiketleri ekleyin. Daha sonra filtrelendirebilirsiniz.
  
- Olayı ata

  Bunu daha sonra filtrelilen bir kullanıcı hesabı adına attayabilirsiniz.
  
- Bir olayı çözme

  Düzeltilen olayı kapatın.
  
- Sınıflandırmasını ve belirlemesini ayarlama

  Bir olayı çözümken tehdit türünü sınıflandırarak seçin.
  
- Açıklama ekleme

  Güvenlik ekibinin en iyi yöntemlerine dayalı olarak ilerleme durumu, notlar veya diğer bilgiler için yorumları kullanın. Tüm açıklama geçmişini, bir olayın **ayrıntılar sayfasındaki** Açıklamalar ve geçmiş seçeneğiyle bulabilirsiniz.

Daha fazla bilgi için bkz [. Olayları yönetme](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>İşlem Merkezi ile otomatik araştırmayı ve yanıtı inceleme

Otomatik araştırma ve yanıt yeteneklerinizin, sizin için nasıl yapılandırıldığına bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca güvenlik işlemleri ekibinin onayı üzerine alınır. Bekleyen veya tamamlanmış olan tüm eylemler İşlem Merkezinde listelenir. [Burada cihazlarınız](m365d-action-center.md) için bekleyen ve tamamlanmış düzeltme eylemleri, e-posta & işbirliği içeriği ve tek bir konumda kimlikler listelenir.

İşte bir örnek.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Birleşik İşlem Merkezi'nin Microsoft 365 Defender.":::

İşlem merkezinde, bekleyen eylemleri seçerek çıkış bölmesinde onayabilir veya reddedebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Eylemi onaylama veya reddetme.":::

Otomatik araştırmalarınızı zamanında devam etmek ve tamamlamak için beklemedeki eylemleri en kısa zamanda onaylayın (veya reddedin).

Daha fazla bilgi için bkz [. Otomatik araştırma ve yanıt](m365d-autoir.md) ve [İşlem merkezi](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>Gelişmiş av kullanma

> [!NOTE]
> Gelişmiş arama benzetimini takip edene kadar gelişmiş av benzetimini anlamadan önce gelişmiş av kavramlarını anlamak için aşağıdaki videoyu izleyin, portalda bu özellikleri nerede bulamaya ulaşabilirsiniz ve güvenlik işlemleriniz için size nasıl yardımcı olduğunu bilebilirsiniz.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


İsteğe bağlı dosyasız [PowerShell](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) saldırı benzetimi, kimlik bilgileri erişim aşamasına zaten ulaşmış olan gerçek bir saldırı ise, oluşturulan uyarılardan ve etkilenen varlıklardan önceden biliyorsanız, ağdaki etkinlikleri ve kayıtları önceden aramak için araştırmanın herhangi bir noktasında gelişmiş avdan kullanabilirsiniz. 

Örneğin, Kullanıcı ve IP adresi üzerinde mutabıklık [(SMB)](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) uyarıdaki bilgilere dayanarak, `IdentityDirectoryEvents` tabloyu kullanarak tüm SMB oturumu numaralama olaylarını bulabilir veya tabloyu kullanarak Kimlik verileri için Microsoft Defender'daki `IdentityQueryEvents` diğer çeşitli protokollerde daha fazla keşif etkinlikleri bulabilirsiniz.


### <a name="hunting-environment-requirements"></a>Av ortamı gereksinimleri

Bu benzetim için tek bir iç posta kutusu ve cihaz gereklidir. Test iletisi göndermek için bir dış e-posta hesabına da ihtiyacınız vardır.

1. Kiracınız etkiyi [etkinleştirmiş Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. E-posta almak için kullanılacak hedef posta kutusunu tanımlama.

   - Bu posta kutusu, Windows için Microsoft Defender tarafından izlen Office 365

   - 3. gereksinime sahip cihazın bu posta kutusuna erişmesi gerekiyor

3. Bir test aygıtını yapılandırma:

    a. 1903 veya Windows 10 sürümünü kullanmaya devam edin.

    b. Test cihazına test etki alanına katılın.

    c. [Aç'Windows Defender Virüsten Koruma](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). E-bilgileri etkinleştirmede sorun Windows Defender Virüsten Koruma, bu [sorun giderme başlığına bakın](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    d. [Uç Nokta için Microsoft Defender'a ekleme](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Benzetimi çalıştırma

1. Dış e-posta hesabından, av ortamı gereksinimleri bölümünün 2. adım bölümünde tanımlanan posta kutusuna bir e-posta gönderin. Var olan herhangi bir e-posta filtresi ilkeleri aracılığıyla izin verilen bir ek iliştirin. Bu dosyanın kötü amaçlı veya yürütülebilir bir dosya olması gerekir. Önerilen dosya <i> türleri.pdf, </i><i>.exe</i> ( izin verilmiyorsa) veya Word Office gibi bir belge türünde olabilir.

2. Gönderilen e-postayı, av ortamı gereksinimleri bölümünün 3. adımda tanımlandığı şekilde yapılandırılan cihazdan açın. Eki açın veya dosyayı cihaza kaydedin.

#### <a name="go-hunting"></a>Go hunting

1. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">açın</a>.

2. Gezinti bölmesinde, Avla ve **Gelişmiş >'ı seçin**.

3. E-posta olaylarını toparak başlayan bir sorgu oluşturun.

   1. Sorgu Yeni **'> seçin**.

   1. Gelişmiş av **altındaki E-posta** **gruplarında**, E-posta **Olayları'nın altına çift tıklayın**. Bunu sorgu penceresinde görüyor olması gerekir.

      ```console
      EmailEvents
      ```

   1. Sorgunun zaman çerçevesini son 24 saat olarak değiştirme. Yukarıdaki benzetimi çalıştırarak gönderilen e-postanın son 24 saat içinde olduğunu varsayarak, aksi takdirde zaman dilimini gereken şekilde değiştirin.

   1. Sorguyu **çalıştır'ı seçin**. Pilot ortamınıza bağlı olarak farklı sonuçlar elde ediyor olabilirsiniz.

      > [!NOTE]
      > Veri dönüşlerini sınırlamak için sonraki adıma bakın.

      ![Gelişmiş arama sorgusu sonuçları örneği.](../../media/advanced-hunting-incident-response-try-1.png)

        > [!NOTE]
        > Gelişmiş arama, sorgu sonuçlarını tablo verileri olarak görüntüler. Ayrıca, verileri grafik gibi başka biçim türlerinde görüntülemeyi de tercihebilirsiniz.

   1. Sonuçlara bakın ve açtığınız e-postayı belirley olup görene bir bakın. İletinin gelişmiş avda iletiyi göstermesi iki saat kadar sürebilir. Sonuçları daraltmak için, sorgunuza koşul koşula göre yalnızca SenderMailFromDomain olarak "yahoo.com" olan e-postaları aramanız gerekir. İşte bir örnek.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Kaydı incelerken sorgudan sonuç satırlarına tıklayın.

      ![Gelişmiş av sonucu seçildiğinde açılan kayıt tarafındaki inceleme paneli örneği.](../../media/advanced-hunting-incident-response-try-2.png)

4. Artık e-postayı gördüğünüze göre, eklere filtre ekleyin. Ortamda ekleri olan tüm e-postalara odaklanın. Bu benzetim için, ortamından gönderilen e-postalara değil, gelen e-postalara odaklanın. İletinizi bulmak için, eklediklerinizi kaldırın ve "Filtre" | burada **AttachmentCount > 0** ve **EmailDirection** == **"Inbound""**

   Aşağıdaki sorgu, tüm e-posta olaylarını ilk sorgunuza göre daha kısa bir listeyle size gösterir:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Ardından, sonuç kümenize ek hakkında bilgileri (örneğin, dosya adı, karmalar) girin. Bunu yapmak için **EmailAttachmentInfo tablosuna** katılın. Bu durumda, katılmak için kullanılan ortak alanlar **NetworkMessageId** ve **RecipientObjectId'dir**.

   Aşağıdaki sorgu, bir de "Özel" satırı | **project-rename EmailTimestamp=Timestamp", e-postayla** hangi zaman damgasının ilişkili olduğunu ve bir sonraki adımda ekley o eylemleriyle ilgili zaman damgasını tanımlamanıza yardımcı olur.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Ardından, **EmailAttachmentInfo** **tablosundan SHA256** değerini kullanarak bu karmanın **DeviceFileEvents'in** (uç noktada olan dosya eylemleri) adını bulun. Buradaki ortak alan, ekin SHA256 karması olur.

   Sonuçta elde edilen tablo artık cihaz adı, yapılan eylem (bu durumda yalnızca FileCreated olaylarını içerecek şekilde filtrelenmiş) ve dosyanın depolandığı yer gibi uç noktadan (Uç nokta için Microsoft Defender) ayrıntıları içerir. İşlemle ilişkili hesap adı da dahil edilir.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Artık kullanıcının eki açtığı veya kayded olduğu tüm gelen e-postaları belirleyen bir sorgu oluşturdunuz. Ayrıca, belirli gönderen etki alanlarını, dosya boyutlarını, dosya türlerini ve diğer özellikleri filtrelemek için de bu sorguyu daraltabilirsiniz.

7. İşlevler, yaygın kullanımı, imzacı ve imzalayanın bilgileri vb. bir dosya hakkında daha fazla TI verisi çekmene izin verir. Dosya hakkında daha fazla ayrıntı almak için **, FileProfile() işlevini** zenginleştirmeyi kullanın:

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Algılama oluşturma

Daha sonra uyarı almak istediğiniz bilgileri tanımlayan bir sorgu oluşturduktan sonra, sorgudan  özel bir algılama oluşturabilirsiniz.

Özel algılamalar, sorguyu ayar aralığına göre çalıştıracak ve sorguların sonuçları, seçtiğiniz etkiyi etkileyen varlıklara bağlı olarak güvenlik uyarıları oluşturur. Bu uyarılar olaylarla bağlantılıdır ve ürünlerden biri tarafından oluşturulan diğer güvenlik uyarılarından biri olarak triyaktı oluşturulacak.

1. Sorgu sayfasında, 7. adımda eklenen 7. ve 8. satırları kaldırın, sonra da Avlamaya git yönergelerine tıklayın ve Algılama kuralı **oluştur'a tıklayın**.

   ![Gelişmiş av sayfasında algılama kuralı oluştur'a tık oluştur seçeneğinin tıklanması örneği.](../../media/advanced-hunting-incident-response-try-3.png)

   > [!NOTE]
   > Algılama kuralı **oluştur'a tıklarsanız** ve sorgunuzda söz dizimi hataları varsa, algılama kuralınız kaydedilemiyor. Hata olmadığını kontrol etmek için sorguyu bir kez daha denetleyin.

2. Gerekli alanları, güvenlik ekibinin uyarıyı, neden oluşturulmuş olduğunu ve hangi eylemleri gerçekleştireceklerini anlamalarına olanak sağlayacak bilgilerle doldurun.

   ![Uyarı ayrıntılarını tanımladığınız algılama kuralı oluşturma sayfası örneği.](../../media/mtp/fig23.png)

   Sonraki kullanıcıya bu algılama kuralı uyarısı hakkında bilinçli bir karar vermeye yardımcı olmak için alanları açık bir şekilde doldurmanıza dikkat edin

3. Bu uyarıda hangi varlıkların etkile ilgili olduğunu seçin. Bu durumda Cihaz ve Posta **Kutusu'seçin****.**

   ![Etkileyen varlıkların parametrelerini seçebilirsiniz algılama kuralı oluşturma sayfası örneği.](../../media/mtp/fig24.png)

4. Uyarı tetiklenirse hangi eylemlerin gerçekleştir dikkatli olması gerektiğini belirleme. Bu durumda, başka eylemler de gerçekleştirese de bir virüsten koruma taraması çalıştırın.

   ![Tehditlere yardımcı olmak için bir uyarı tetiklendiğinde virüsten koruma taraması çalıştırabilirsiniz algılama kuralı sayfası örneği.](../../media/mtp/fig25.png)

5. Uyarı kuralının kapsamını seçin. Bu sorgu cihazlar içerdiği için, cihaz grupları Uç nokta için Microsoft Defender bağlamına göre bu özel algılamada çok uygun olur. Etkilenmek istediğiniz cihazlar dışında bir özel algılama oluşturulurken kapsam geçerli olmaz.

   ![Uyarı kuralının kapsamını ayar İlke oluştur sayfası örneği, göreceğiniz sonuçlarla ilgili beklentilerinizi yönetir.](../../media/mtp/fig26.png)

   Bu pilot için, bu kuralı üretim ortamınızı test cihazlarının bir alt kümesiyle sınırlandırabilirsiniz.

6. **Oluştur**’u seçin. Ardından, gezinti **bölmesinden Özel algılama** kuralları'nı seçin.

   ![Menü içinde Özel algılama kuralları seçeneği örneği.](../../media/mtp/fig27a.png)

   ![Kural ve yürütme ayrıntılarını görüntüleyen algılama kuralları sayfası örneği.](../../media/mtp/fig27b.png)

   Bu sayfadan, algılama kuralını seçerek ayrıntılar sayfasını açabilirsiniz.

   ![Kural yürütme, tetiklenen uyarılar ve eylemler, algılamayı düzenleme gibi işlemlerin durumunu gördüğünüz e-posta ekleri sayfası örneği.](../../media/mtp/fig28.png)


### <a name="expert-training-on-advanced-hunting"></a>Gelişmiş avla ilgili uzman eğitimi

**Hasımları takip etmek,** yeni güvenlik analistleri ve uzman tehdit avcıları için bir web yayını serisidir. Kendi gelişmiş sorgularınızı oluşturmanın tüm yollarında, gelişmiş aramanın temelleri konusunda size yol sağlar. 

Bkz [. Gelişmiş avla ilgili uzman eğitimi](advanced-hunting-expert-training.md) almak için başlama.

### <a name="navigation-you-may-need"></a>Gezintiye ihtiyacınız olabilir

[Değerlendirme Microsoft 365 Defender Oluşturma](eval-create-eval-environment.md)
