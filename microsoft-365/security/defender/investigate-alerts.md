---
title: E-postada uyarıları Microsoft 365 Defender
description: Cihazlar, kullanıcılar ve posta kutuları genelinde görülen uyarıları araştırabilirsiniz.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: cfa39ca38046c131de2531b4ad6446626895090f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015530"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>E-postada uyarıları Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Uyarılar tüm olayların temeli olup, ortamınıza kötü amaçlı veya şüpheli olayların ortaya çıkmasını sağlar. Uyarılar normalde daha geniş bir saldırının bir parçası olur ve bir olay hakkında ipucu sağlar.

Daha Microsoft 365 Defender, ilgili uyarılar olay oluşturmak için bir [araya toplanır](incidents-overview.md). Ancak, olaylar her zaman bir saldırının daha geniş bağlamını sağlayacaktır; ancak daha derin çözümleme yapmak gerektiğinde uyarıları çözümlemek değerli olabilir. 

Uyarılar **sırası geçerli** uyarı kümelerini gösterir. Microsoft 365 Defender portalının hızlı başlatında, Olaylar **& veya Uyarılar >** sırasında <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">uyarı kuyruğuna Microsoft 365 Defender</a>.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Portalda uyarı kuyruğu Microsoft 365 Defender.":::

Uç Nokta için Microsoft Defender, Güvenlik için Microsoft Defender ve Güvenlik için Microsoft Defender gibi farklı Microsoft Office 365 Microsoft 365 Defender uyarıları burada görünür.

Varsayılan olarak, portalda Microsoft 365 Defender sırasındaki uyarı sırası son 30 gün içinde gelen yeni ve devam eden uyarıları görüntüler. En son uyarı listenin en üstünde yer alıyor, böylece ilk olarak siz de onu görüyorsunuz. 

Varsayılan uyarılar kuyruğundan Filtre'yi seçerek **uyarıların bir** alt kümesini belirtebilirsiniz. Filtre bölmesini görmek için bu bölmeyi de görebilirsiniz. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Yeni portalda uyarılar sırası için filtreler Microsoft 365 Defender.":::

Uyarıları şu ölçütlere göre filtreleyabilirsiniz:

- Önem Derecesi
- Durum
- Hizmet kaynakları
- Varlıklar (etkilene varlıklar)
- Otomatik soruşturma durumu

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Güvenlik uyarıları için Defender Office 365 rolleri

Kullanıcı uyarıları için Microsoft Defender'a erişmek için aşağıdaki rollerden herhangi Office 365 gerekir:

- Daha Azure Active Directory (Azure AD) genel rolleri için:

   - Genel yönetici

   - Güvenlik yöneticisi

   - Güvenlik İşleci

   - Genel Okuyucu

   - Güvenlik Okuyucu

- Office 365 Güvenlik & Uyumluluk Rol Grupları

   - Uyumluluk Yöneticisi

   - Kuruluş Yönetimi 

- Özel [bir rol](custom-roles.md)

## <a name="analyze-an-alert"></a>Uyarıyı çözümleme

Ana uyarı sayfasını görmek için uyarının adını seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Portalda uyarının ayrıntılar Microsoft 365 Defender.":::

Ayrıca, Uyarıyı yönet **bölmesinden Ana uyarı sayfasını** aç **eylemlerini de seçin** .

Bu bölümlerde bir uyarı sayfası oluşur: 

- Bu uyarıyla ilgili olayların ve uyarıların zinciri olan ve kronolojik sırayla uyarı hikayesi
- Özet ayrıntıları

Uyarı sayfasının tamamında, herhangi bir varlığın yanındaki üç noktayı (**...**) seçerek uyarı sayfasını açma veya uyarıyı başka bir olayla bağlama gibi kullanılabilir eylemleri görebilirsiniz.

### <a name="alert-sources"></a>Kaynakları uyarın

Microsoft 365 Defender için Microsoft Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender uygulaması yönetim eklentisini gibi çözümlerden uyarılar gelebilir. Uyarıda, ön karakter içeren uyarılar farkedebilirsiniz. Aşağıdaki tablo, uyarı kaynaklarının eşlemesini, uyarının ön ekli karakterini temel alarak anlamanıza yardımcı olacak kılavuz bilgiler sağlar.

> [!NOTE]
> - Hazır GUID'ler yalnızca birleşik uyarılar sırası, birleşik uyarılar sayfası, birleşik araştırma ve birleşik olay gibi birleşik deneyimlere özeldir.
> - Önki karakter uyarının GUID'sini değiştirmez. GUID'ye yapılan tek değişiklik, ön bileşendir.

| Uyarı kaynağı | Ön uç karakteri |
| :---|:--- |
| Office 365 için Microsoft Defender | `fa{GUID}` <br> Örnek: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Uç Nokta için Microsoft Defender | `da` veya `ed` özel algılama uyarıları için <br> |
| Kimlik için Microsoft Defender | `aa{GUID}` <br> Örnek: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Bulut Uygulamaları için Microsoft Defender |`ca{GUID}` <br> Örnek: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Etkilenen varlıkları çözümleme

**Yapılan Eylemler** bölümünde, bu uyarıdan etkilenen posta kutuları, cihazlar ve kullanıcılar gibi etkilenen varlıkların listesi yer almaktadır. 

Ayrıca, aynı **portalda İşlem merkezi'nin** **Geçmiş** sekmesini görüntülemek **için İşlem merkezinde** görüntüle'yi Microsoft 365 Defender. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Uyarı hikayesinde uyarının rolünü izleme

Uyarı hikayesinde, bir işlem ağacı görünümünde uyarıyla ilgili tüm varlıklar veya varlıklar görüntülenir. Seçili uyarının sayfasına ilk kez geldiğinde, başlıkta uyarı odakta olan uyarıdır. Uyarı hikayesinde yer alan varlıklar genişletilebilir ve tıklanabilir. Bunlar ek bilgi sağlar ve uyarı sayfası bağlamında hemen işlemnize izin vererek yanıt sürecinizi hızlandırtır. 

> [!NOTE]
> Uyarı anlatısı bölümü, seçtiğiniz uyarıdan önce veya sonra görünen aynı yürütme ağacıyla ilgili ek uyarılar içeren birden fazla uyarı içerebilir.

### <a name="view-more-alert-information-on-the-details-page"></a>Ayrıntılar sayfasında daha fazla uyarı bilgisi görüntüleme

Ayrıntılar sayfasında, seçilen uyarının ayrıntıları ve bu uyarıyla ilgili eylemlerle birlikte ayrıntılar görüntülenir. Uyarı hikayesinde etkilenen varlıklardan veya varlıklardan herhangi birini seçtiysanız, ayrıntılar sayfası seçili nesne için bağlamsal bilgi ve eylemler sağlamak üzere değişir.

İlgi alanı olan bir varlık seçtikten sonra, ayrıntılar sayfasında seçili varlık türü, varsa tarihi bilgiler ve bu varlık üzerinde doğrudan uyarı sayfasından işlem görüntüleme seçenekleri görüntülenir.

## <a name="manage-alerts"></a>Uyarıları yönetme

Bir uyarıyı yönetmek için, kendi sırasındaki uyarılar sırasındaki uyarıyı seçerek Yönet **uyarı bölmesini** görüntüleyin. İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Portalda uyarı için özet Microsoft 365 Defender.":::

Yönet **uyarı bölmesi** şunları görüntülemenizi veya belirtmenizi sağlar:

- Uyarı durumu (Yeni, Çözümlendi, Sürüyor).
- Uyarının atandığı kullanıcı hesabı.
- Uyarının sınıflandırması (Ayarlanmaz, Doğru uyarı, Yanlış Uyarı).
- Sınıflandırma için gerçek uyarı, Kararlama alanında uyarı için tehdit **türü** .
- Uyarıyla ilgili bir açıklama.

> [!NOTE]
> Etiketlerin kullanımıyla uyarıyı yönetmenin bir yolu. Microsoft Defender For Office 365 etiketleme özelliği artımlı olarak dağıtımda ve şu anda önizlemededir. <br>
> Şu anda, değiştirilmiş etiket adları yalnızca güncelleştirmeden sonra oluşturulan *uyarılara* uygulanır. Değişiklik öncesinde oluşturulan uyarılar, güncelleştirilmiş etiket adını yansıtmaz. 

Bu bölmede, şu ek eylemleri de gerçekleştirebilirsiniz: 

- Ana uyarı sayfasını açma
- Microsoft tehdit uzmanına danışın
- Gönderiyi görüntüleme
- Başka bir olayla bağlantı
- Uyarıyı zaman çizelgesinde görme
- Gizleme kuralı oluşturma

İşte bir örnek.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-actions.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-actions.png" alt-text="Portalda bir uyarıda Microsoft 365 Defender örneği":::

Ek eylemlerin listesi uyarının türüne bağlıdır.

## <a name="resolve-an-alert"></a>Uyarıyı çözme

Bir uyarıyı çözümlemeyi bitirerek bu uyarıyı çözümleyene kadar, uyarının  Uyarıyı yönet bölmesine gidin ve durumu Çözümlendi olarak  işaretleyebilirsiniz ve bunu Yanlış uyarı veya Doğru  uyarısı olarak **sınıflandırabilirsiniz**. Doğru uyarılar için, Belirleme alanında uyarının tehdit **türünü** belirtin.

Uyarıları sınıflama ve bunların belirlemesi, daha doğru Microsoft 365 Defender daha az yanlış uyarı sağlamak için uyarıları ayarlamaya yardımcı olur.

## <a name="use-power-automate-to-triage-alerts"></a>Uyarıların Power Automate için uyarıların önce gelen durumuyla ilgili bilgileri kullanma

Modern güvenlik işlemlerinin (SecOps) ekiplerinin etkin bir şekilde çalışması için otomasyona ihtiyacı olur. SecOps ekipleri, gerçek tehditlere karşı aramalara ve gerçek tehditlere karşı Power Automate için uyarı listesinin öncelerini kaldırmak ve tehdit olmayanları ortadan kaldırmak için bu uyarıları kullanır.  

### <a name="criteria-for-resolving-alerts"></a>Uyarıları çözümleme ölçütleri

- Kullanıcı Ofis dışında iletisi açık

- Kullanıcı yüksek risk olarak etiketlenmiş değil

Her ikisi de doğruysa, SecOps uyarıyı yasal bir seyahat olarak işaretler ve sorunu çözer. Bu uyarı çözümlendikten Microsoft Teams bu alan alanla birlikte bir bildirim postalanmıştır.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Bağlan Power Automate Uygulamaları için Microsoft Defender'a Geç

Otomasyon oluşturmak için bir API belirteci gerekir ve bu belirteci bulut Power Automate Microsoft Defender'a bağlanabilirsiniz.

1. Ekle **Ayarlar** e tıklayın, **Güvenlik uzantıları'yı** seçin ve ARDıNDAN API **belirteçleri** sekmesinde Belirteç **ekle'ye** tıklayın.

2. Belirtecniz için bir ad girin ve oluştur'a **tıklayın**. Belirteci daha sonra ihtiyacınız olacak şekilde kaydedin.

### <a name="create-an-automated-flow"></a>Otomatik akış oluşturma

Adım adım ayrıntılı işlem için buradaki videoya [bakın](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

Bu videoda ayrıca Bulut Uygulamaları için Defender'a power automate ile nasıl bağlan bağlantısı olduğu da açık almaktadır.

## <a name="next-steps"></a>Sonraki adımlar

Süreç içinde yaşanan olaylarda olduğu gibi, incelemenize devam [edersiniz](investigate-incidents.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları yönetme](manage-incidents.md)
- [Olayları araştırma](investigate-incidents.md)
