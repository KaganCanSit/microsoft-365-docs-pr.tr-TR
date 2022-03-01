---
title: Posta kutusu kullanımı hizmet uyarıları
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
description: Posta kutusu kullanım hizmeti uyarılarını kullanarak, posta kutusu kotasına ulaşan posta kutularının tutarak izlenmesini sağlar.
ms.openlocfilehash: 311be4159d45b19ce1123baa840eebdf844840ec
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012875"
---
# <a name="service-alerts-for-mailbox-utilization-in-exchange-online-monitoring"></a>Posta kutusu kullanımının izlemesinde Exchange Online uyarıları

Kotalarına ulaşma veya aşma riski olan Exchange Online posta kutuları hakkında sizi bilgilendiren yeni bir Exchange Online hizmeti uyarısı yayınlandı. Bu hizmet uyarıları, kuruluşta yönetici müdahalesi gerektiren posta kutularının sayısına görünürlük sağlar.

Bu hizmet uyarıları aşağıdaki Microsoft 365 yönetim merkezi. Bu hizmet uyarılarını görüntülemek için <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**HealthService health (HealthService**</a> >  health > ) Exchange Online sonra da **Etkin sorunlar sekmesine** tıklayın. İşte, posta kutusu kullanımı hizmet uyarısı örneği.

:::image type="content" alt-text="Posta kutusu kullanımı hizmet uyarısı." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Depolama kotasına yakın olan posta kutularının listesini görüntülemek için (posta kutusu *kullanım* raporu olarak adlandırılan), aşağıdaki ekran görüntüsünde vurgulanan bağlantıya tıklayın. Bu bağlantı hizmet uyarılarında görüntülenir.

:::image type="content" alt-text="Posta kutusu kullanım raporunun bağlantısı." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Alternatif olarak, posta kutusu kullanım raporunun doğrudan URL'si de şudur <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>: .

## <a name="what-do-these-service-alerts-indicate"></a>Bu hizmet uyarıları neleri gösteriyor?

Posta kutusu kullanımıyla ilgili hizmet uyarıları yöneticilere, posta kutusu depolama kotasının yaklaşacak olan saklama posta kutuları hakkında bilgi sağlar. Posta kutularına yerleştirilebiliyor olan bekletme türü mahkeme nedeniyle tutma, eBulma bekletme ve Microsoft 365 bekletme ilkelerini (verileri içerecek şekilde yapılandırılmış) içerir. Bir posta kutusu tutma sırasında, kullanıcılar (veya otomatik süreçler) posta kutularından verileri kalıcı olarak kaldırlarınız. Bunun yerine yöneticilerin, verileri kullanıcının birincil posta kutusundan arşiv posta kutusuna taşımak için Exchange Online'de MRM bekletme ilkelerini (veri bekletmeyle ilgili kuruluş uyumluluk ilkeleriyle satır içi) yapılandırmaları gerekir. Değil ve saklama durumdaki bir posta kutusu kritik veya uyarı durumuna ulaşırsa, yöneticilerin arşiv [](../compliance/enable-archive-mailboxes.md) posta kutularını etkinleştirmesi ve otomatik genişleyen arşivlemeyi etkinleştirmesi ve ardından posta kutusuna atanan arşiv ilkesi bekletme döneminin ([e-postayı](../compliance/enable-autoexpanding-archiving.md) birincil posta kutusundan arşiv posta kutusuna taşır) yeterli olduğundan emin olmak zorunda olur. Posta kutusu kullanımı hizmet uyarıları tarafından tanımlanan kota sorunlarının çözümü için hiçbir şey yapılmazsa, kullanıcılar e-posta iletileri veya toplantı davetleri göndereylem veya alamabilirsiniz.

Posta kutusu kullanımına karşı bir hizmet uyarısı, kotalarına yaklaşan posta kutusu sayısıyla ilgili tablolar içerir. Aşağıdaki bölümlerde bu tablolarda yer alan bilgiler açıklanmaktadır ve bu posta kutularının kotalarını aşmamalarına yardımcı olmak için eylem yöneticilerinin gerçekleştirebilirsiniz.

> [!NOTE]
> Hizmet uyarıları, aşağıdaki bölümlerde açıklanan tablolarda sütunlarda görünen posta kutusu kota özellikleriyle ilgili açıklamalar içerir.

### <a name="mailboxes-on-hold-without-an-archive"></a>Arşiv olmadan posta kutuları tutma

Aşağıdaki tabloda, kotalarına yaklaşan ancak arşiv posta kutusu etkinleştirilmiş durumdaki posta kutularının sayısı listelenir. Tablodaki her sütun belirli kotayı ve bu kotaya yaklaşan posta kutularının sayısını tanımlar.

| # Mailboxes ProhibitSendReceiveQuota (Warning)| # Mailboxes ProhibitSendReceiveQuota (Critical)** |# Mailboxes RecoverableItemsQuota (Warning)|# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Yöneticilerin bu posta kutuları için bir işlemde esnayası, arşiv posta kutusunu etkinleştirmek ve öğelerin arşiv posta kutusuna taşınmasını sağlamak için, posta kutusuna bir MRM arşiv ilkesi (Exchange Online'te öğeleri taşınan MRM bekletme ilkesidir) uygulandığını sağlamaktır. Daha fazla bilgi için bkz [. Posta kutuları için arşivleme ve silme ilkesi ayarlama](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Arşiv posta kutusunu etkinleştirdikten sonra, Kurtarılabilir Öğeler klasörü kotasını artırmayı göz önünde bulundurmanızı öneririz. Bu, tutmada durumdaki posta kutuları için Kurtarılabilir Öğeler klasörü kotasının aşılmalarını önlemeye yardımcı olur. Daha fazla bilgi için bkz [. Posta kutularının Kurtarılabilir Öğe kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Arşivle birlikte posta kutuları tutma

Aşağıdaki tabloda, kotalarına yaklaşan ve arşiv posta kutusu etkinleştirilmiş durumdaki posta kutularının sayısı listelenir.

|# Mailboxes ProhibitSendReceiveQuota (Warning) |# Posta Kutuları ProhibitSendReceiveQuota (Critical) |# Mailboxes RecoverableItemsQuota (Warning) |# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

Yöneticilerin bu posta kutuları için esnayabilecek eylem, Kurtarılabilir Öğeler klasörünün kotasını artırmaktır. Daha fazla bilgi için bkz [. Posta kutularının Kurtarılabilir Öğe kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Yöneticiler ayrıca, öğeleri arşiv posta kutusuna taşırken uygulanan MRM arşiv ilkesi'nin de posta kutularına uygulandığından ve arşiv ilkesi bekletme döneminin kısa olduğundan, öğelerin arşive taşınmadan önce birincil posta kutusunda fazla uzun süre tutulmayacak kadar kısa olduğundan emin olun.

> [!NOTE]
> MRM arşiv ilkeleri öğeleri birincil posta kutusunun Kurtarılabilir Öğeler klasöründen ilgili arşiv posta kutusunun Kurtarılabilir Öğeler klasörüne de taşımalıdır. Bu özellik, posta kutusunun Kurtarılabilir Öğe kotasının kotasını aşmasını önlemeye yardımcı olur.

### <a name="mrm-retention-policies-in-your-organization"></a>Kuruluşta MRM bekletme ilkeleri

Posta kutusu kullanımıyla ilgili hizmet uyarıları, ayrıca kurumdaki MRM bekletme ilkeleri hakkında bilgiler içeren bir tablo ve bekletme ilkesi olan posta kutularının bir arşiv posta kutusu olup olmadığını da içeren bir tablo içerebilir. Bekletme ilkeleri hakkında daha fazla bilgi için bkz. İlke altında bekletme [etiketleri ve Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | MailboxType | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Posta Kutuları |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | True | False | True | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Birincil | True | False | True | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | False | True | False | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | True | True | True | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | True | True  | False | 1 |
|||||||

Aşağıdaki listede, önceki tabloda yer alan her sütun açık masasıdır.

- **RetentionPolicyGuid**: Kuruluşta posta kutularına atanan bekletme ilkesi GUID değeri. Önceki örnekte, aynı bekletme ilkesi için iki ayrı satır vardır. İlk satır, ilkeye atanmış arşivi olan posta kutularının sayısını gösterir. İkinci satır, arşivi olmayan ve aynı ilkeye atanmış posta kutularının sayısını gösterir.

   Bu sütunda listelenen bekletme ilkesi hakkında daha fazla bilgi almak için, [Exchange Online PowerShell'de çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   Ad özelliğinin **değeri**, yönetim merkezinde bulunan Bekletme ilkeleri sayfasında görüntülenen bekletme <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange olur</a>.

- **MailboxType**: İlkenin hangi posta kutusuna atandığı belirtir. Değerler Primary ( *arşiv* olmayan posta kutuları) veya *PrimaryWithArchive* (arşiv içeren posta kutuları) içerebilir. Bu sütundaki *değer Birincil ise*, ilkeye atanan posta kutuları için arşivi etkinleştirmeniz (Posta Kutusu sütunu bu  posta kutularının sayısını gösterir). Aksi takdirde, öğeleri taşınabilecek bir arşiv yok olduğundan arşiv ilkesi veya kişisel arşiv etiketi işe yaramadı.

- **HasMoveDumpsterToArchiveTag**: Bekletme ilkesinde, birincil posta kutusunda bulunan Kurtarılabilir Öğeler klasöründeki (dökümün adı da *denir) öğeleri* arşivdeki Kurtarılabilir Öğeler klasörüne taşıan bir bekletme etiketi olduğunu gösterir. Bu tür bir bekletme etiketi yönetici tarafından ayarlanır. Kurtarılabilir öğeler etiketinin bekletme süresi çok uzunsa, bekletme süresinin azaltılması, posta kutularının Kurtarılabilir Öğeler klasörü kotasının yaklaşmasını önlemeye yardımcı olur. Örneğin, bekletme süresi 30 gün olarak ayarlanırsa, bu sürenin üç veya beş gün kadar kısal tutulması size yardımcı olabilir.  Daha fazla bilgi için bkz [. Posta kutularının Kurtarılabilir Öğe kotasını artırma](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag**: Bekletme ilkesinde yer alan bir varsayılan "arşive taşı" bekletme etiketi (arşiv ilkesi olarak da *denir) olup* olduğunu gösterir. Bu durumda, iletiler birincil posta kutusunda normal klasörlerden arşiv posta kutusuna taşınır. Bu tür bir bekletme etiketi yönetici tarafından ayarlanır. Bir kez daha, bu etiketi tutma süresi çok kısa olursa, kullanıcılar birincil posta kutuları için kotaya sürekli ulaşmada sorun olabilir. Arşiv ilkesi bekletme süresinin azaltılması bu sorunu çözmeye yardımcı olabilir.

- **HasPersonalArchiveTag**: Bekletme ilkesinde kişisel bir "Arşive taşı" etiketi olup olduğunu gösterir. Bekletme ilkesi kişisel bir "Arşive taşı" etiketi içerecekse, kullanıcılar öğeleri arşive taşımak için bu etiketi posta kutularına uygulayabilir. Kullanıcılar ayrıca, iletileri bu etiket uygulanmış bir klasöre taşımak için gelen kutusu kuralı da kurabilirsiniz. Her iki durumda da, bu birincil posta kutuları için kotaya ulaşmayı önlemeye yardımcı olmak için öğeleri arşive taşımaya yardımcı olabilir.

- **Posta Kutuları**: Bekletme ilkesine atanan posta kutularının (arşive sahip veya arşivsiz olan ve **MailboxType** sütununda gösterilen posta kutularının sayısını gösterir).

## <a name="how-often-will-i-see-these-service-alerts"></a>Bu hizmet uyarılarını ne sıklıkta görebilirim?

Kota sorunlarını çözmek için hiçbir işlem görmüyorsanız, bu tür hizmet uyarılarını her dört günde bir görmeyi bekliyor olabilir. Sonraki hizmet uyarıları kotalarına yaklaşan diğer posta kutuları için daha yüksek posta kutusu sayısı içerebilir. Kota sorunlarını çözmeye ilişkin bir işlem alırsanız, bu hizmet uyarısı yalnızca kota sorunları olan başka bir posta kutusu tanım olduğunda gerçekleşir.

## <a name="more-information"></a>Daha fazla bilgi

- Arşiv posta kutusu sorunlarını giderme ve çözme hakkında bilgi için bkz. [Uyumluluk Microsoft 365 giderme](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Posta kutusuna yerleştirilen tutma sürelerini belirleme konusunda yol gösterici bilgi için bkz. Posta kutusuna [yerleştirilen tutma türünü belirleme](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
