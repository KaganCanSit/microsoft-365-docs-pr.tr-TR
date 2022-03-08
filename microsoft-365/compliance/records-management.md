---
title: Kayıt Yönetimi'Microsoft 365
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
description: Microsoft 365'de kayıt yönetimiyle, bekletme, kayıt bildirimi ve yoklamayı yöneten bir dosya planına bekletme zamanlamalarınızı uygulayabilirsiniz.
ms.openlocfilehash: c7546216a935960e5c4b66b37bb3308d0a69e89e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324823"
---
# <a name="learn-about-records-management-in-microsoft-365"></a>Microsoft 365'de kayıt yönetimi hakkında bilgi Microsoft 365

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Her tür kuruluş, şirket verileri genelinde mevzuat, yasal ve iş açısından kritik kayıtları yönetmek için bir kayıt yönetimi çözümü gerektirir. Microsoft 365'te kayıt yönetimi, kuruluşun yasal yükümlülüklerini yönetmeye yardımcı olur, yasal düzenlemelere uyumluluğu gösterme olanağı sağlar ve artık korunacak, değeri olmayacak veya artık iş amacıyla gerekli olmayacak öğelerin normal olarak yok olmasıyla verimliliği artırır.

Kayıt yönetimi çözümlerinizi desteklemek için aşağıdaki özellikleri Microsoft 365:

- **İçeriği kayıt olarak etiketleme**. İçeriği kullanıcılar tarafından uygulanmayacak veya hassas bilgiler, anahtar [](#records) sözcükler veya içerik türleri tanımarak otomatik olarak uygulanan bir kayıt olarak işaretlemek için bekletme etiketleri oluşturun ve yapılandıryın.

- **Dosya planıyla bekletme gereksinimlerinizi geçirin ve yönetin**. Dosya planı [kullanarak, var](file-plan-manager.md) olan bir bekletme planını başka bir plana Microsoft 365 veya gelişmiş yönetim özellikleri için yeni bir plan oluşturabilirsiniz.

- **Bekletme ve silme ayarlarını bekletme etiketleriyle yapılandırabilirsiniz**. Bekletme [etiketlerini,](retention.md#retention-labels) son değiştirme veya oluşturma tarihini içeren çeşitli etmenlere dayalı olarak bekletme dönemleri ve eylemleriyle yapılandırabilirsiniz.

- **Olay tabanlı bekletme ile bir olay oluştuğunda farklı** [bekletme dönemleri başlatma](event-driven-retention.md).

- **Disposition incelemeleri ve** kayıt [silme kanıtı ile inceleme](disposition.md#disposition-reviews) [ve doğrulama.](disposition.md#disposition-of-records)

- **Dışarı aktarma seçeneğiyle, dışarı aktaran tüm** öğelerle ilgili [bilgileri dışarı aktarın](disposition.md#filter-and-export-the-views).

- **Doğru erişime** sahip olmak için, kuruluşta kayıt yöneticisi işlevleri [için belirli izinler ayarlayın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Bu özellikleri kullanarak, içeriğinizin tüm yaşam döngüsünü desteklemek için, kuruluş bekletme zamanlamalarını ve gereksinimlerini bekletmeyi, kayıt bildirimini ve yoklamayı yöneten bir kayıt yönetimi çözümüne dahil edebilirsiniz.

Çevrimiçi belgelere ek olarak, bir kayıt yönetimi web sitesinden [SSS](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) ile bir deste indirmeniz yararlı olabilir. Gerçek web tarayıcısı kaydı artık kullanılamaz.

## <a name="records"></a>Kayıtlar

İçerik kayıt olarak bildir mu?

- Öğelere, izin verilen veya engellenen eylemlerle ilgili [kısıtlamalar yerleştirilir](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Öğeyle ilgili ek etkinlikler günlüğe kaydedilir.

- Bekletme döneminin sonunda öğeler silindiğinde, konumlandırma kanıtınız olur.

İçeriği kayıt [veya mevzuat](retention.md#retention-labels) kaydı olarak **işaretlemek için** bekletme **etiketlerini kullanırsiniz**. Bu ikisi arasındaki fark sonraki bölümde açıklanmıştır. Bu etiketleri yayımlayın; böylece kullanıcılar ve yöneticiler bunları içeriğe el ile uygulayabilir ya da bu etiketleri bir kayıt veya mevzuat kaydı olarak işaretlemek istediğiniz içeriğe otomatik olarak uygulayabilir.

Kayıtları beyan etmek için bekletme etiketlerini kullanarak, kayıt ortamınız genelinde kayıtları yönetmek için tek ve tutarlı bir Microsoft 365 gerçekleştirabilirsiniz.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>İzin verilen veya engellenen eylemlerle ilgili kısıtlamaları karşılaştırma

Standart bir bekletme etiketi ve içeriği kayıt veya mevzuat kaydı olarak işaretleyen bekletme etiketlerinin uygulanması sonucunda içerik üzerinde hangi kısıtlamaların yerleştiril olduğunu belirlemek için aşağıdaki tabloyu kullanın.

Standart bekletme etiketinde bekletme ayarları ve eylemleri vardır, ancak içeriği kayıt veya mevzuat kaydı olarak işaretlemez.

> [!NOTE]
> Eksiksizlik için, tablo kilitli ve kilitli kilitli kayıt için sütunlar içerir; bu sütun ve SharePoint OneDrive uygulanabilir, ancak Exchange. Kaydı kilitleme ve kilidini açma özelliği, kayıt [öğeleri](record-versioning.md) tarafından desteklenen kayıt sürümü Exchange kullanır. Dolayısıyla, Exchange olarak işaretlenmiş tüm kayıt öğeleri için davranış Kayıt **-** kilitli sütununa ve Kayıt **- kilitli olmayan** sütuna eşlenir.


|Eylem| Bekletme etiketi |Kayıt - kilitli| Kayıt - kilidi açık| Mevzuat kaydı |
|:-----|:-----|:-----|:-----|:-----|:-----|
|İçeriği düzenleme|İzin verildi | **Engellendi** | İzin verildi | **Engellendi**|
|Yeniden adlandırma da dahil olmak üzere özellikleri düzenleme|İzin verildi |İzin <sup>verilen 1</sup> | İzin verildi | **Engellendi**|
|Silme|İzin <sup>verildi 2</sup> |**Engellendi** |**Engellendi**| **Engellendi**|
|Kopyala|İzin verildi |İzin verildi | İzin verildi| İzin verildi|
|Kapsayıcı <sup>3 içinde hareket etme</sup>|İzin verildi |İzin verildi | İzin verildi| İzin verildi|
|Kapsayıcılar arasında hareket <sup>etme 3</sup>|İzin verildi |Kilidi hiç açık değilken izin verildi | **Engellendi** | **Engellendi**|
|Açma/Okuma|İzin verildi |İzin verildi | İzin verildi| İzin verildi|
|Etiketi değiştir|İzin verildi |İzin verildi - yalnızca kapsayıcı yöneticisi | İzin verildi - yalnızca kapsayıcı yöneticisi| **Engellendi**
|Etiketi kaldır|İzin verildi |İzin verildi - yalnızca kapsayıcı yöneticisi | İzin verildi - yalnızca kapsayıcı yöneticisi| **Engellendi**

Dipnotlar:

<sup>1</sup> Kilitli kaydın özelliklerine varsayılan olarak izin verilir, ancak [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) >  **Decords yönetimiRecords** >  yönetim **ayarlarıRetention** >  **labelsAlt** >  özelliklerini düzenlemeye izin ver.

<sup>2</sup> SharePoint ve OneDrive etiketli öğelerin silinmesi [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) >  **Cords yönetimiRecords** >  >  yönetim **ayarlarıRetention etiketleriDeletion** >  of items altında kiracı ayarı **olarak engellenmiş olabilir**.

Belge eki olan bir liste öğesine bekletme etiketi uygulayabilirsiniz, bu belge bekletme ayarlarını devralmaz ve liste öğesinden silinebilir. Buna karşılık, bu liste öğesi bir bekletme etiketiyle kayıt olarak bildirmişse, belge eki bekletme ayarlarını devralabilir ve silinemez.

<sup>3</sup> Kapsayıcılar belge SharePoint kitaplıklarını, OneDrive hesaplarını ve posta Exchange içerir.

> [!IMPORTANT]
> Bir mevzuat kaydı için en önemli fark, bu kaydın içeriklere uygulandıktan sonra hiç kimsenin, hatta genel yöneticinin bile etiketi kaldıramamalıdır.
>
> Mevzuat kayıtları için yapılandırılan bekletme etiketleri de aşağıdaki yönetici kısıtlamalarına sahiptir:
>
> - Etiket kaydedildikten sonra bekletme süresi kısalıp yalnızca uzatılabilir.
> - Bu etiketler otomatik etiket ilkeleri tarafından destek desteklemez ve bekletme etiketi ilkeleri kullanılarak [uygulanmalıdır](create-apply-retention-labels.md).
>
> Buna ek olarak, düzenleyici etiketi şirket içinde kullanıma alınmış olan bir belgeye SharePoint.
>
> Kısıtlamalar ve geri alınamaz işlemler nedeniyle, bekletme etiketleriniz için bu seçeneği seçmeden önce yasal düzenleme kayıtlarını gerçekten kullanmaya gerek olduğundan emin olun. Yanlışlıkla yapılandırmayı önlemeye yardımcı olmak için, bu seçenek varsayılan olarak kullanılamaz, ancak önce PowerShell kullanılarak etkinleştirilmesi gerekir. Yönergeler, bekletme etiketleri [kullanılarak Kayıt bildir'e ek açıklamalarında bulunmaktadır](declare-records.md).

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bkz [. Kayıt yönetimiyle çalışmaya başlama](get-started-with-records-management.md). Bu makalede abonelikler, izinler hakkında bilgiler ve kayıt yönetimi senaryoları için  uç  uç yapılandırma kılavuzuna bağlantılar vardır.