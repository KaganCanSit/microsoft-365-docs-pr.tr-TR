---
title: Posta kutusu kullanım hizmeti uyarıları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Posta kutusu kotalarına ulaşan beklemedeki posta kutularını izlemek için posta kutusu kullanım hizmeti uyarılarını kullanın.
ms.openlocfilehash: fdc87e92aa6614d78347984cfa09bf75edc131e5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935313"
---
# <a name="service-alerts-for-mailbox-utilization-in-exchange-online-monitoring"></a>Exchange Online izlemede posta kutusu kullanımı için hizmet uyarıları

Kotalarına ulaşma veya kotalarını aşma riski olan beklemedeki posta kutuları hakkında sizi bilgilendiren yeni bir Exchange Online hizmet uyarısı yayımladık. Bu hizmet uyarıları, kuruluşunuzda yönetici müdahalesi gerektirebilecek posta kutularının sayısını gösterir.

Bu hizmet uyarıları Microsoft 365 yönetim merkezi görüntülenir. Bu hizmet uyarılarını görüntülemek için **Sistem Durumu** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Hizmet durumu Exchange Online'na**</a> >  gidin ve **Etkin sorunlar** sekmesine tıklayın. Posta kutusu kullanım hizmeti uyarısı örneği aşağıda verilmiştır.

:::image type="content" alt-text="Posta kutusu kullanım hizmeti uyarısı." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Depolama kotasına yakın olan posta kutularının listesini görüntülemek için ( *posta kutusu kullanım raporu* olarak adlandırılır), aşağıdaki ekran görüntüsünde vurgulanan bağlantıya tıklayın. Bu bağlantı hizmet uyarısında görüntülenir.

:::image type="content" alt-text="Posta kutusu kullanım raporuna bağlantı." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Alternatif olarak, posta kutusu kullanım raporunun doğrudan URL'si olur <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>.

## <a name="what-do-these-service-alerts-indicate"></a>Bu hizmet uyarıları neleri gösteriyor?

Posta kutusu kullanımına yönelik hizmet uyarıları, yöneticileri, posta kutusu depolama kotasının yakınında olan beklemedeki posta kutuları hakkında bilgilendirir. Posta kutularına yerleştirilebilen ayrı tutma türleri arasında Dava tutmaları, eBulma tutma ve Microsoft 365 bekletme ilkeleri (verileri saklamak için yapılandırılmıştır) bulunur. Posta kutusu beklemede olduğunda, kullanıcılar (veya otomatik işlemler) posta kutularındaki verileri kalıcı olarak kaldıramaz. Bunun yerine, yöneticilerin kullanıcının birincil posta kutusundan arşiv posta kutusuna veri taşımak için Exchange Online (kuruluşlarının veri saklamayla ilgili uyumluluk ilkeleriyle satır içi) MRM bekletme ilkelerini yapılandırmaları gerekir. Değilse ve ayrı tutmadaki bir posta kutusu kritik veya uyarı durumuna ulaşırsa, yöneticilerin [arşiv posta kutularını etkinleştirmesi](../compliance/enable-archive-mailboxes.md) ve [arşivlemeyi otomatik genişletmeyi etkinleştirmesi](../compliance/enable-autoexpanding-archiving.md) ve ardından posta kutusuna atanan arşiv ilkesinin saklama süresinin (e-postayı birincil posta kutusundan arşiv posta kutusuna taşıyan) yeterince kısa olduğundan emin olması gerekir. Posta kutusu kullanım hizmeti uyarıları tarafından tanımlanan kota sorunlarını çözmek için hiçbir şey yapılmazsa, kullanıcılar e-posta iletileri veya toplantı davetleri gönderemeyebilir veya alamayabilir.

Posta kutusu kullanımına yönelik bir hizmet uyarısı, kotalarına yakın olan posta kutularının sayısıyla ilgili tablolar içerir. Aşağıdaki bölümlerde, bu tablolardaki bilgiler açıklanır ve yöneticilerin bu posta kutularının kotalarını aşmamasını sağlamak için gerçekleştirebilecekleri eylem açıklanmaktadır.

> [!NOTE]
> Hizmet uyarıları, aşağıdaki bölümlerde açıklanan tablolardaki sütunlarda görünen posta kutusu kotası özelliklerinin açıklamalarını içerir.

### <a name="mailboxes-on-hold-without-an-archive"></a>Arşiv olmadan beklemedeki posta kutuları

Aşağıdaki tabloda, kotasına yakın olan ancak arşiv posta kutusu etkin olmayan beklemedeki posta kutularının sayısı listelenir. Tablodaki her sütun belirli kotayı ve bu kotaya yakın posta kutularının sayısını tanımlar.

| # Mailboxes ProhibitSendReceiveQuota (Uyarı)| # Mailboxes ProhibitSendReceiveQuota (Kritik)** |# Mailboxes RecoverableItemsQuota (Uyarı)|# Mailboxes RecoverableItemsQuota (Kritik)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Yöneticilerin bu posta kutuları için gerçekleştirebileceği eylem, arşiv posta kutusunu etkinleştirmek ve öğelerin arşiv posta kutusuna taşınması için posta kutusuna bir MRM arşiv ilkesinin (öğeleri arşiv posta kutusuna taşıyan Exchange Online MRM bekletme ilkesidir) uygulanmasını sağlamaktır. Daha fazla bilgi için bkz. [Posta kutuları için arşiv ve silme ilkesi ayarlama](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Arşiv posta kutusunu etkinleştirdikten sonra Kurtarılabilir Öğeler klasörünün kotasını artırmayı göz önünde bulundurmanızı öneririz. Bu, ayrı tutulan posta kutuları için Kurtarılabilir Öğeler klasörünün kotasının aşılmasını önlemeye yardımcı olur. Daha fazla bilgi için bkz. [Bekleyen posta kutuları için Kurtarılabilir Öğeler kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Arşiv içeren beklemedeki posta kutuları

Aşağıdaki tabloda, kotasına yakın olan ve bir arşiv posta kutusunun etkin olduğu ayrı tutmadaki posta kutularının sayısı listelenir.

|# Mailboxes ProhibitSendReceiveQuota (Uyarı) |# Mailboxes ProhibitSendReceiveQuota (Kritik) |# Mailboxes RecoverableItemsQuota (Uyarı) |# Mailboxes RecoverableItemsQuota (Kritik)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

Yöneticilerin bu posta kutuları için gerçekleştirebileceği eylem, Kurtarılabilir Öğeler klasörünün kotasını artırmaktır. Daha fazla bilgi için bkz. [Bekleyen posta kutuları için Kurtarılabilir Öğeler kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Yöneticiler ayrıca öğeleri arşiv posta kutusuna taşıyan bir MRM arşiv ilkesinin de posta kutularına uygulandığından ve arşiv ilkesinin bekletme süresinin yeterince kısa olduğundan ve öğelerin arşive taşınmadan önce birincil posta kutusunda çok uzun süre saklanmadığından emin olmalıdır.

> [!NOTE]
> MRM arşiv ilkeleri, öğeleri birincil posta kutusunda bulunan Kurtarılabilir Öğeler klasöründen ilgili arşiv posta kutusunun Kurtarılabilir Öğeler klasörüne de taşır. Bu özellik, posta kutusunun Kurtarılabilir Öğeler kotası kotasını aşmasını önlemeye yardımcı olur.

### <a name="mrm-retention-policies-in-your-organization"></a>Kuruluşunuzda MRM bekletme ilkeleri

Posta kutusu kullanımına yönelik hizmet uyarıları, kuruluşunuzdaki MRM bekletme ilkeleri ve bekletme ilkesi olan posta kutularının arşiv posta kutusu olup olmadığı hakkında bilgi içeren bir tablo da içerebilir. Bekletme ilkeleri hakkında daha fazla bilgi için bkz[. Exchange Online bekletme etiketleri ve bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | MailboxType | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Posta kutu -ları |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | True | False | True | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Birincil | True | False | True | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | False | True | False | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True | True | True | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True | True  | False | 1 |
|||||||

Aşağıdaki listede, önceki tablodaki her sütun açıklanmaktadır.

- **RetentionPolicyGuid**: Kuruluşunuzdaki posta kutularına atanan bekletme ilkesinin GUID'i. Önceki örnekte, aynı bekletme ilkesi için iki ayrı satır vardır. İlk satır, ilkeye atanmış bir arşive sahip posta kutularının sayısını gösterir. İkinci satır, aynı ilkeye atanmış arşivi olmayan posta kutularının sayısını gösterir.

   Bu sütunda listelenen bekletme ilkesi hakkında daha fazla bilgi edinmek için [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) Exchange Online de aşağıdaki komutu çalıştırın.

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   **Name** özelliğinin değeri, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezindeki</a> **Bekletme ilkeleri sayfasında görüntülenen bekletme ilkesinin** adıdır.

- **MailboxType**: İlkenin atandığı posta kutularının türünü belirtir. Değerler *Birincil* (arşiv içermeyen posta kutuları) veya *PrimaryWithArchive* (arşiv içeren posta kutuları) değerlerini içerir. Bu sütundaki değer *Birincil* ise, ilkeye atanan posta kutuları ( **Posta Kutusu** sütunu bu posta kutularının sayısını gösterir) için arşivi etkinleştirmeniz gerekir. Aksi takdirde, öğeleri taşınacak bir arşiv olmadığından arşiv ilkesi veya kişisel arşiv etiketi çalışmaz.

- **HasMoveDumpsterToArchiveTag**: Bekletme ilkesinin, birincil posta kutusunun Kurtarılabilir Öğeler klasöründeki ( *döküm kutusu* olarak da adlandırılır) öğeleri arşivdeki Kurtarılabilir Öğeler klasörüne taşıyabilen bir bekletme etiketi içerdiğini gösterir. Bu tür bekletme etiketi bir yönetici tarafından ayarlanır. Kurtarılabilir öğeler etiketi için bekletme süresi çok uzunsa, bekletme süresinin azaltılması posta kutularının Kurtarılabilir Öğeler klasörünün kotaya yaklaşmasını önlemeye yardımcı olur. Örneğin, saklama süresi 30 gün olarak ayarlanırsa, bunun üç veya beş güne indirilmesi yararlı olabilir.  Daha fazla bilgi için bkz. [Bekleyen posta kutuları için Kurtarılabilir Öğeler kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag**: Bekletme ilkesinde varsayılan "arşive taşı" bekletme etiketi ( *arşiv ilkesi* olarak da adlandırılır) olup olmadığını gösterir. Bu durumda, iletiler birincil posta kutusundaki normal klasörlerden arşiv posta kutusuna taşınır. Bu tür bekletme etiketi bir yönetici tarafından ayarlanır. Yine, bu etiketin saklama süresi çok kısaysa, kullanıcılar birincil posta kutularının kotasına sürekli olarak ulaşma konusunda sorun yaşayabilir. Arşiv ilkesinin saklama süresini azaltmak bu sorunun çözülmesine yardımcı olabilir.

- **HasPersonalArchiveTag**: Bekletme ilkesinin kişisel bir "arşive taşı" etiketi içerip içermediğini gösterir. Bekletme ilkesi kişisel bir "arşive taşı" etiketi içermiyorsa, kullanıcılar öğeleri arşive taşımak için bu etiketi posta kutularındaki klasörlere ve iletilere uygulayabilir. Kullanıcılar, iletileri bu etiketli klasöre uygulanacak bir klasöre taşımak için de bir gelen kutusu kuralı ayarlayabilir. Her iki durumda da bu, birincil posta kutularının kotasına ulaşmamaya yardımcı olmak için öğeleri arşive taşımaya yardımcı olabilir.

- **Posta kutuları**: Bekletme ilkesinin atandığı posta kutularının sayısını (arşive sahip olanlar veya arşivleri olmayanlar, **MailboxType** sütununda gösterilir) gösterir.

## <a name="how-often-will-i-see-these-service-alerts"></a>Bu hizmet uyarılarını ne sıklıkta göreceğim?

Kota sorunlarını çözmek için işlem yapmazsanız, dört günde bir bu tür bir hizmet uyarısı görmeyi bekleyebilirsiniz. Sonraki hizmet uyarıları, kotalarına yakın olan diğer posta kutuları için daha yüksek posta kutusu sayısı içerebilir. Kota sorunlarını çözmek için işlem yaparsanız, bu hizmet uyarısı yalnızca kota sorunları olan başka bir posta kutusu tanımlandığında oluşur.

## <a name="more-information"></a>Daha fazla bilgi

- Arşiv posta kutusu sorunlarını giderme ve çözme hakkında bilgi için bkz. [Microsoft Purview sorunlarını giderme](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Posta kutusuna yerleştirilen ayrı tutmaları tanımlama hakkında rehberlik için bkz. Posta [kutusuna yerleştirilen ayrı tutmanın türünü tanımlama](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
