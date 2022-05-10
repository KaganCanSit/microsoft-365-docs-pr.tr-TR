---
title: Microsoft Purview Kayıt Yönetimi hakkında bilgi edinin
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- admindeeplinkCOMPLIANCE
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Microsoft Purview Kayıt Yönetimi'nin iş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri nasıl desteklediğini öğrenin.
ms.openlocfilehash: b14c622d1468cdb91ad1ac8e58c184e650ebbe6c
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65284874"
---
# <a name="learn-about-records-management"></a>Kayıt yönetimi hakkında daha fazla bilgi edinme

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!TIP]
> *Dokuz Microsoft Purview çözümlerinin tamamının premium sürümlerini ücretsiz olarak deneyebileceğinizi biliyor muydunuz?* Sağlam Purview özelliklerinin kuruluşunuzun uyumluluk gereksinimlerini karşılamasına nasıl yardımcı olabileceğini keşfetmek için 90 günlük Purview çözümleri deneme sürümünü kullanın. Microsoft 365 E3 ve Office 365 E3 müşterileri artık [Microsoft Purview uyumluluk portalı deneme hub'ında](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef) başlayabilir. [Kaydolabilecek kişiler ve deneme koşulları](compliance-easy-trials.md) hakkında ayrıntılı bilgi edinin.

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Her türden kuruluş, kurumsal verileri genelinde yasal, yasal ve iş açısından kritik kayıtları yönetmek için bir kayıt yönetimi çözümüne ihtiyaç duyar. Microsoft Purview için kayıt yönetimi, bir kuruluşun yasal yükümlülüklerini yönetmesine yardımcı olur, düzenlemelere uyumluluğu gösterme olanağı sağlar ve artık saklanması gerekmeyen, artık değerli olmayan veya iş amaçları için artık gerekli olmayan öğelerin düzenli olarak elden bırakılmasıyla verimliliği artırır.

Microsoft 365 hizmetleri ve uygulamaları için kayıt yönetimi çözümünüzü desteklemek için aşağıdaki özellikleri kullanın:

- **İçeriği kayıt olarak etiketle**. İçeriği kullanıcılar tarafından uygulanabilecek veya hassas bilgiler, anahtar sözcükler veya içerik türleri tanımlanarak otomatik olarak uygulanabilecek bir [kayıt](#records) olarak işaretlemek için bekletme etiketleri oluşturun ve yapılandırın.

- **Dosya planıyla bekletme gereksinimlerinizi geçirin ve yönetin**. [Bir dosya planı](file-plan-manager.md) kullanarak, Microsoft 365 için mevcut bir bekletme planını getirebilir veya gelişmiş yönetim özellikleri için yeni bir tane oluşturabilirsiniz.

- **Bekletme etiketleriyle bekletme ve silme ayarlarını yapılandırın**. [Bekletme etiketlerini,](retention.md#retention-labels) en son değiştirilme veya oluşturulma tarihini içeren çeşitli faktörlere göre bekletme dönemleri ve eylemleriyle yapılandırın.

- Olay [tabanlı](event-driven-retention.md) **saklama ile bir olay gerçekleştiğinde farklı saklama süreleri başlatın**.

- **Değerlendirme gözden geçirmeleri ve** [kayıt silme](disposition.md#disposition-of-records) kanıtı ile [değerlendirmeyi](disposition.md#disposition-reviews) gözden geçirin ve doğrulayın.

- **Dışarı aktarma seçeneğiyle, atılan tüm öğeler hakkındaki bilgileri** [dışarı aktarın](disposition.md#filter-and-export-the-views).

- Kuruluşunuzdaki kayıt yöneticisi [işlevlerinin doğru erişime sahip](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) olması için **belirli izinleri ayarlayın**.

Bu özellikleri kullanarak, kuruluşunuzun bekletme zamanlamalarını ve gereksinimlerini, içeriğinizin tüm yaşam döngüsünü desteklemek için bekletmeyi, kayıt bildirimini ve eğilimi yöneten bir kayıt yönetimi çözümüne dahil edebilirsiniz.

Çevrimiçi belgelere ek olarak, kayıt yönetimi web seminerinden [SSS içeren bir deste](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) indirmeyi yararlı bulabilirsiniz. Gerçek web seminerinin kaydı artık kullanılamaz.

## <a name="records"></a>Kayıt

İçerik kayıt olarak bildirildiğinde:

- Öğelere izin [verilen veya engellenen eylemler](#compare-restrictions-for-what-actions-are-allowed-or-blocked) açısından kısıtlamalar yerleştirilir.

- Öğeyle ilgili ek etkinlikler günlüğe kaydedilir.

- Öğeler saklama sürelerinin sonunda silindiğinde edat kanıtınız olur.

İçeriği **kayıt** veya **mevzuat kaydı** olarak işaretlemek için [bekletme etiketlerini](retention.md#retention-labels) kullanırsınız. Bu ikisi arasındaki fark bir sonraki bölümde açıklanmıştır. Kullanıcıların ve yöneticilerin bunları içeriğe el ile uygulayabilmesi için bu etiketleri yayımlayabilir veya bu etiketleri kayıt veya mevzuat kaydı olarak işaretlemek istediğiniz içeriğe otomatik olarak uygulayabilirsiniz.

Kayıtları bildirmek için bekletme etiketlerini kullanarak, Microsoft 365 ortamınızda kayıtları yönetmek için tek ve tutarlı bir strateji uygulayabilirsiniz.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma

Standart bir bekletme etiketi ve içeriği kayıt veya mevzuat kaydı olarak işaretleyen bekletme etiketlerinin uygulanması sonucunda içeriğe hangi kısıtlamaların uygulandığını belirlemek için aşağıdaki tabloyu kullanın.

Standart saklama etiketinde bekletme ayarları ve eylemleri vardır, ancak içeriği kayıt veya mevzuat kaydı olarak işaretlemez.

> [!NOTE]
> Tamlık için, tablo kilitli ve kilidi açılmış bir kaydın sütunlarını içerir. Bu sütun SharePoint ve OneDrive için geçerlidir ancak Exchange için geçerli değildir. Kaydı kilitleme ve kilidini açma özelliği, Exchange öğeler için desteklenmeyen [kayıt sürümü oluşturmayı](record-versioning.md) kullanır. Bu nedenle, kayıt olarak işaretlenmiş tüm Exchange öğeler için davranış **Kayıt - kilitli** sütununa eşlenir ve **Kayıt - kilidi açılmış sütun** uygun değildir.


|Eylem| Bekletme etiketi |Kayıt - kilitli| Kayıt - kilidi açık| Mevzuat kaydı |
|:-----|:-----|:-----|:-----|:-----|:-----|
|İçeriği düzenle|Izin verilen | **Engellenen** | Izin verilen | **Engellenen**|
|Yeniden adlandırma dahil olmak üzere özellikleri düzenleme|Izin verilen |İzin verilen <sup>1</sup> | Izin verilen | **Engellenen**|
|Silme|İzin Verilen <sup>2</sup> |**Engellenen** |**Engellenen**| **Engellenen**|
|Kopya|Izin verilen |Izin verilen | Izin verilen| Izin verilen|
|<sup>Kapsayıcı 3</sup> içinde taşıma|Izin verilen |Izin verilen | Izin verilen| Izin verilen|
|Kapsayıcılar arasında hareket etme <sup>3</sup>|Izin verilen |Kilidi hiç açmadıysa izin verilir | **Engellenen** | **Engellenen**|
|Aç/Oku|Izin verilen |Izin verilen | Izin verilen| Izin verilen|
|Etiketi değiştir|Izin verilen |İzin verildi - yalnızca kapsayıcı yöneticisi | **Engellenen**| **Engellenen**
|Etiketi kaldır|Izin verilen |İzin verildi - yalnızca kapsayıcı yöneticisi | **Engellenen**| **Engellenen**

Dipnot:

<sup>1</sup> Kilitli bir kaydın düzenleme özelliklerine varsayılan olarak izin verilir, ancak [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com/) >  bir kiracı ayarı tarafından **engellenebilirKayıt yönetimikayıt yönetimi** >  **ayarlarıKayıt** >  **etiketleriKayıt** >  **özelliklerinin düzenlenmesine izin verin**.

<sup>2</sup> SharePoint ve OneDrive etiketli öğelerin silinmesi [, Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com/) >  kiracı ayarı olarak engellenebilirKayıt **yönetimiKayıt yönetimi** >  **ayarlarıKayıt** >  **etiketleriSeçlerin** >  silinmesi.

Belge eki olan bir liste öğesine bekletme etiketi uyguladığınızda, bu belge bekletme ayarlarını devralamaz ve liste öğesinden silinebilir. Buna karşılık, bu liste öğesi bekletme etiketine sahip bir kayıt olarak bildirilmişse, belge eki bekletme ayarlarını devralır ve silinemez.

<sup>3</sup> Kapsayıcılar SharePoint belge kitaplıklarını, OneDrive hesaplarını ve Exchange posta kutularını içerir.

> [!IMPORTANT]
> Yasal kayıt için en önemli fark, içeriğe uygulandıktan sonra, etiketi hiçbir genel yöneticinin bile kaldıramayacak olmasıdır.
>
> Mevzuat kayıtları için yapılandırılan bekletme etiketlerinin de aşağıdaki yönetici kısıtlamaları vardır:
>
> - Saklama süresi, etiket kaydedildikten sonra kısaltılamaz, yalnızca uzatılır.
> - Bu etiketler otomatik etiketleme ilkeleri tarafından desteklenmez ve [bekletme etiketi ilkeleri](create-apply-retention-labels.md) kullanılarak uygulanmalıdır.
>
> Ayrıca, SharePoint kullanıma alınmış bir belgeye mevzuat etiketi uygulanamaz.
>
> Kısıtlamalar ve geri alınamaz eylemler nedeniyle, bekletme etiketleriniz için bu seçeneği belirlemeden önce mevzuat kayıtlarını kullanmanız gerektiğinden emin olun. Yanlışlıkla yapılandırmayı önlemeye yardımcı olmak için bu seçenek varsayılan olarak kullanılamaz, ancak önce PowerShell kullanılarak etkinleştirilmesi gerekir. Yönergeler [, Bekletme etiketlerini kullanarak kayıtları bildirme](declare-records.md) bölümüne eklenir.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bkz. [kayıt yönetimiyle Kullanmaya başlayın](get-started-with-records-management.md). Bu makalede abonelikler, izinler ve kayıt yönetimi senaryoları için uçtan uca yapılandırma kılavuzu bağlantıları hakkında bilgiler yer alır.
