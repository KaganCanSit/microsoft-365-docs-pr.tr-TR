---
title: Microsoft Yönetilen Masaüstü işlemleri ve izleme
description: Who değişiklik işlemleri için neler yapar?
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6b1771660cb25ccd9d23c97d1e3fcf6edd27feaa
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015273"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Microsoft Yönetilen Masaüstü işlemleri ve izleme

<!-- Operations and monitoring: -->

## <a name="change-management"></a>Değişiklik yönetimi

Hizmet teklifte, donanım bakımı ve güvenlik güncelleştirmeleri ile ilgili sorumluluk bakiyesi, müşteriden (siz) hizmet sağlayıcısına (Microsoft) kaydırır. Ancak, güncelleştirmeler gönderilirken Microsoft olmayan ve özel yazılımın beklendiği gibi çalışmasına devam etmek zorundasiniz.

Şirket içi ürünler için, değişiklik yönetiminin tüm sorumluluğu, organizasyonu tarafından kabul edildi.

### <a name="balance-of-responsibility"></a>Sorumluluk bakiyesi

| Sorumluluk | Microsoft Yönetilen Masaüstü hizmeti | Microsoft 365 istemci yazılımı | Şirket içi istemciler ve sunucular | Microsoft dışı ve özel yazılım
| ----- | ----- | ----- | ----- | ----- |
| Yeni işlevler sağlama | Microsoft | Microsoft | Her ikisi | Müşteri
| Kalite güvencesi için yeni özellikleri test etmek |  Microsoft | Microsoft | Her ikisi | Müşteri
| Yeni özellikler hakkında iletişim kurma | Her ikisi | Her ikisi | Her ikisi | Müşteri
| Özel yazılımı tümleştirin | Her ikisi | Her ikisi | Müşteri | Müşteri
| Güvenlik güncelleştirmelerini uygulama | Microsoft | Microsoft | Müşteri | Müşteri
| Sistem yazılımını koruma | Microsoft | Microsoft | Müşteri | Müşteri
| Dağıtım paketi | Microsoft | Microsoft | Müşteri | Müşteri

### <a name="change-process-overview"></a>Değişiklik sürecine genel bakış

Aşağıda, değişiklik işleminin Microsoft ile müşteriler arasında nasıl paylaşılıyor olduğu özetlenmiştir:

| Senaryo | Microsoft'un rolü | Müşterinin rolü |
| ----- | ----- | ----- |
| Değişiklik öncesinde | <ul><li>Hizmet değişikliklerine ilişkin beklentilerinizi ayarlayın.</li><li>Yönetici eylemi gerektiren değişiklikler için müşterileri 5 gün önceden bilgilendirin.</li><li>Acil durum değişiklikleri için, bildirim öncesinde bir risk azaltma uygulayabilirsiniz.</li></ul> | <ul><li>Değişikliklerden ve iletişimlerden neler beklemeniz olduğunu anlıyoruz.</li><li>Microsoft Yönetilen Masaüstü İleti Merkezi'nde düzenli olarak okuma.</li><li>İç değişiklik yönetimi işlemlerini gözden geçirme ve güncelleştirme.</li><li>Microsoft Yönetilen Masaüstü gereksinimlerini an edin ve uyumluluğu kontrol edin. </li><li>Gerektiğinde onaylar ve onaylar.</li></ul>
| Değişiklik sırasında | <ul><li>Müşteriler ve müşteriler için aylık güvenlik güncelleştirmelerini ve güvenlikle ilgili olmayan Windows 10 dağıtın Office 365 dağıtın.</li><li>Veri sinyallerini takip edin ve etki için sıraları desteklenin.</li></ul> | <ul><li>Microsoft Yönetilen Masaüstü İleti Merkezi'ne bakın ve varsa ek bilgileri gözden geçirin.</li><li>Uygunsa, gereken her işlemi uygulama ve test etmek.</li><li>Bir hata/düzeltme senaryosu yaşanıyorsa, bir destek isteği oluşturun.</li></ul> |
| Değişiklik sonrasında | <ul><li>Gelecek değişikliklerin daha iyi bir şekilde çıkışlarını sağlamak için müşteri geri bildirimlerini toplayın.</li><li>Veri sinyallerini takip edin ve etki için sıraları desteklenin.</li></ul> | <ul><li>Değişikliği benimsemek için organizasyon değişikliğini benimseyenlerle birlikte çalış.</li><li>Verimlilik kazanma fırsatları için değişiklik ve benimseme yönetim sürecini gözden geçirin.</li><li>Yönetici geri bildirim aracında genel geri bildirim ve belirli geri bildirimler gönderin.</li><li>Kullanıcıları, uygulama sayfalarındaki Gülümseme Windows Geri Bildirim Merkezi kullanarak uygulamaya özel geri bildirim sağlamak Office eğitin.</li></ul> |

### <a name="change-types"></a>Türleri değiştirme

Hizmette düzenli olarak çeşitli türlerde değişiklik yapılanlar vardır. Bu değişikliklerin iletişim kanalı ve değişiklik yapmakla sorumlu olduğunuz eylemler.

Tüm değişiklikler kullanıcılarınız üzerinde aynı etkiyi olmaz veya bir işlem gerektirir. Bazıları planlandı, bazıları planlanmamış. Örneğin, güvenlikle ilgili olmayan güncelleştirmeler ve güvenlik güncelleştirmeleri genellikle planlanamaz.

Değişiklik türüne bağlı olarak iletişim kanalı farklılık gösterebilir. Aşağıdaki tabloda, Microsoft Yönetilen Masaüstü hizmeti için bekleyebilirsiniz değişiklik türleri listelemektedir.

|  | İşlevsellik | Güvenlikle ilgili olmayan güncelleştirmeler | Güvenlik |
| ----- | ----- | ----- | ----- |
| **Değişiklik türü** | <ul><li>Özellik güncelleştirmeleri</li><li>Yeni özellikler veya uygulamalar</li><li>Kullanım dışı olan özellikler</li></ul> | Sorunlar için istemci düzeltmeleri | Güvenlik güncelleştirmesi |
**Önceden bildirim** | İşlem gerektiren değişiklikler için beş gün uyarı | Bu tür değişiklikler aylık sürüme dahil değildir | Aylık sürümde hiçbir değişiklik yoktur |
**İletişim kanalı** | <ul><li>İleti Merkezi</li><li>E-posta uyarısı</li></ul> | <ul><li>İleti Merkezi</li><li>E-posta uyarısı</li></ul> | <ul><li>İleti Merkezi</li><li>E-posta uyarısı</li></ul> |
**Genel yönetici eylemi gerektirir** | Bazen | Nadiren | Nadiren |
**Eylem türü** | Ayarları değiştirme | Değişiklikleri kullanıcılara ilet | Yönetici ayarlarını değiştirme |
**Test gerektirir** | Uzaktan erişim hizmetleri dahil olmak üzere iş uygulamalarını denetleme | Bazen; düzeltmeyi işlemler veya özelleştirmelere karşı test etme | Nadiren |
**Değişiklik örnekleri** | <ul><li>Özellik güncelleştirmeleri: IT Yönetici Portalı basitleştirilmiş destek bileti gönderimi ve gözden geçirme</li><li>Yeni özellikler veya uygulamalar: Semi-Annual özellik güncelleştirmesi Windows 10 sürümü</li></ul> | Müşteri tarafından bildirilen hatalara dayalı düzeltmeler |

## <a name="standard-operating-procedures"></a>Standart işletim yordamları

Microsoft Yönetilen Masaüstü hizmeti, diğer yönetim etkinliklerini gerçekleştirebilirsiniz ve Microsoft tarafından bulut örneğiniz içinde uygulanır ve yönetilir. Microsoft tarafından yönetilen Masaüstü kurulumu, yapılandırması ve işlemi yalnızca Microsoft'un sorumluluğundadır.

Şirket içi ürünler için, kurulum, yapılandırma ve işlem etkinliklerinin yönetilmesiyle ilgili tüm sorumluluk, organizasyon tarafından üstlenen bir kuruluştur.

| Kategoriler | Microsoft | Müşteri, |
| ----- | ----- | ----- |
| Ağ (proxy, paket incelemesi, VPN) | İşletme kullanıcılarına riski en aza indirmeleri için müşterilere öneride veya planlarda öneride bulundurarak plannızı yapmayı tercih ettiysiniz. | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li></ul> |
Hizmet hesapları | <ul><li>Kimlik bilgilerini uygulama, güvenli bir şekilde depolama ve yönetme.</li><li>Bu kimlik bilgilerine yetkisiz erişimi veya bu kimlik bilgilerinin kullanımını Güvenlik İşlemleri ekibinize iletin.</li></ul> | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li><li>Microsoft Yönetilen Masaüstü Hizmeti Hesaplarına ilke, çok faktörlü kimlik doğrulaması, koşullu erişim veya uygulama dağıtımı atamaz.</li><li>Parolayı sıfırlamayın veya kimlik bilgilerini kullanmayın.</li><li>Intune veya Azure denetim günlüklerinde bu hizmet hesaplarıyla ilgili şüpheli etkinlikler gözlemlenirse, Microsoft Yönetilen Masaüstü İşlemleri'ne Bir Sev C destek isteği açın.</li></ul>
| Cihaz Grupları | <li> Microsoft Yönetilen Masaüstü grupları içinde cihazların üyeliğini uygulama ve atama.</li><li>Atamayı, yapılandırmayı ve cihazlara yapılan güncelleştirmeleri yönetmek için Microsoft Yönetilen Masaüstü gruplarını kullanın.</li></ul> | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li><li>Cihazları dağıtım grubuna atama konusunda açıklanan adımları kullanarak cihazları yalnızca Microsoft Yönetilen [Masaüstü grubuna attayabilirsiniz](../working-with-managed-desktop/assign-deployment-group.md).</li><li>Grupları yalnızca VPN, Kurumsal İnternet bağlantısı veya e-posta şifreleme veya kurumsal WiFi profili yapılandırması Windows Hello hizmetlere kurumsal sertifikalar atamak için kullanın.</li><li>Birlikte yönetim varsa, Configuration Manager istemcisini dağıtırken tüm Microsoft Yönetilen Masaüstü gruplarını açık bir şekilde dışlayın.</li></ul>
| İlkeler | <ul><li>Hizmet içindeki cihazların yapılandırma durumunu yöneten Microsoft Yönetilen Masaüstü ilkelerini uygulama ve yönetme.</li><li> Cihaz Grupları'ı kullanarak güncelleştirmeleri ilkeye Windows adım adım dağıtın.</li><li>Microsoft Yönetilen Masaüstü grupları olmayanları hedeflemeyi açıkça dışarıda bırakabilirsiniz.</li></ul> | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li><li>Microsoft Yönetilen Masaüstü hizmeti tarafından yönetilmiyor cihazlara veya kullanıcılara Microsoft Yönetilen Masaüstü ilkeleri düzenlenemez ve atanmamalıdır.
Microsoft 365 Defender Için Bağlantı Noktası.</li></ul> | Microsoft Yönetilen Masaüstü hizmeti kapsamındaki cihazları izleyebilir ve araştırabilirsiniz. | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li></ul>
| İş İçin Microsoft Store | Microsoft Yönetilen Masaüstü Windows AutoPilot profilini yapılandırarak ve sürdürün. | <ul><li>Planlı bir yapılandırma değişikliğiyle ilgili bilgi isteği isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li><li>AutoPilot profilinde Microsoft Yönetilen Masaüstü Windows yapılandırmasını değiştirmeyin veya atanmış cihazları ekleyin/kaldırın.</li></ul>
| Sertifikalar | | <ul><li>Planlı bir yapılandırma değişikliği için bilgi talep etmek üzere, sertifikanın süresi dolmadan 60 gün önce bir destek isteği oluşturun. Microsoft'un gözden geçirmesi için yapılandırma ayrıntılarını, kapsamı, zaman çizelgesini ve diğer ilgili ayrıntıları ekleyin.</li><li>Değişikliği yalnızca Microsoft Yönetilen Masaüstü İşlemleri değerlendirildi ve bilgilendirilsin.</li><li>Sertifika profillerini, VPN profillerini ve güvenlik profillerini yapılandırmak için gereken tüm Wi-Fi güncelleştirin.</li></ul>|

## <a name="device-wipe-with-factory-reset"></a>Fabrika sıfırlama ile cihaz temizleme

Microsoft Yönetilen Masaüstü İşlemleri ekibi, gerektiğinde hizmete kaydolan cihazlarda fabrika sıfırlaması gerçekleştirebilirsiniz. Bir cihazı farklı bir çalışana vermeniz gerekirse veya bir çalışan şirketten ayrılırsa sıfırlama yararlı olur.

Birkaç gereklilik vardır:

- Genel yöneticiniz bir destek isteği göndermesi gerekir.
- İstekte cihazın bilgisayar adını yazın.
- Cihazı sıfırlamadan önce kullanıcı hesabının Azure AD'de olması gerekir.

Yönetilen Masaüstü İşlemleri ekibi şunları başaracak:

- Intune'da cihaz adını bakın.
- Fabrika sıfırlama komutunu cihaza gönderin.

> [!NOTE]
> Cihaz sıfırdan önce kullanıcı hesabını Azure AD'den kaldırmayın. Kullanıcı Azure AD'de değilse, Intune fabrika sıfırlama komutunu cihaza gönderer.

Cihaz "ilk başlatma deneyimine" önyükler ve önceden yüklenmiş tüm uygulama ve ayarlar yeniden uygulanır. Cihazın kullanıcılarının ilk kurulum bilgilerini yeniden sağlamaları gerekir.

Cihaz sıfır olduğunda, bunu kuruluşta başka bir kişiye veabilirsiniz. Önceki kullanıcının verileri veya kurumsal verileri cihaza bağlı olmayacaktır. Sonraki kullanıcı, önceki kişinin yeni Microsoft Yönetilen Masaüstü cihazıyla aynı işlemi uygulamasına geçmektedir.

BitLocker, bu süreçteki veri güvenliğinin önemli bir bileşenidir. Microsoft Yönetilen Masaüstü cihazlarda BitLocker şifrelemesi ile cihaz fabrika sıfırlaması yapıldıktan sonra bile sürücüde bulunan veriler güvende kalır. Sürücüde olan veriler, cihazın bir sonraki kullanıcısı tarafından kullanılamaz. Daha fazla bilgi için bkz. [BitLocker'a genel bakış](/windows/security/information-protection/bitlocker/bitlocker-overview).

Daha fazla bilgi için bkz. [Cihazı fabrika sıfırlama](/intune/remote-actions/devices-wipe#factory-reset-a-device).
