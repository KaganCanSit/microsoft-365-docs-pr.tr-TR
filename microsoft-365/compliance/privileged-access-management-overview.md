---
title: Ayrıcalıklı erişim yönetimi hakkında bilgi
description: Bu makalede, sık sorulan soruların (SSS) yanıtları Microsoft 365, standart standartlarda ayrıcalıklı erişim yönetimi hakkında genel bir bakış bulabilirsiniz.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: 4fb4b548d71cf3e1da11e3c861a16929ac7073d8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986728"
---
# <a name="learn-about-privileged-access-management"></a>Ayrıcalıklı erişim yönetimi hakkında bilgi

Ayrıcalıklı erişim yönetimi, aynı konumdaki ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim Office 365. Bu, hassas verilere ayakta erişim veya kritik yapılandırma ayarlarına erişimle, var olan ayrıcalıklı yönetici hesaplarının kullanımına yönelik ihlallere karşı kuruluşu korumaya yardımcı olabilir. Ayrıcalıklı erişim yönetimi, kullanıcıların yüksek kapsamlı ve zaman sınırı olan bir onay iş akışı aracılığıyla yükseltilmiş ve ayrıcalıklı görevleri tamamlamak için tam zamanında erişim isteğinde bulundurmalarını gerektirir. Bu yapılandırma, hassas verilerin veya kritik yapılandırma ayarlarının maruz kalma riski olmadan, kullanıcılara görevi gerçekleştirmeleri için yeterli erişim sağlar. Microsoft 365'de ayrıcalıklı erişim yönetiminin etkinleştirilmesi, kurum personelinizin sıfır ayaktaki ayrıcalıklarla çalışmasına ve yönetim erişimi güvenlik açıklarına karşı bir savunma katmanı sağlamasına olanak sağlar.

Tümleşik Müşteri Kilidi ve ayrıcalıklı erişim yönetimi iş akışına hızlı bir genel bakış için, bu Müşteri Kasa ve ayrıcalıklı erişim [yönetimi videosuna bakın](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>Koruma katmanları

Ayrıcalıklı erişim yönetimi, güvenlik mimarisi kapsamındaki diğer verileri ve erişim Microsoft 365 tamamlar. Güvenlikle tümleşik ve katmanlı bir yaklaşımın parçası olarak ayrıcalıklı erişim yönetiminin dahil olması, hassas bilgilerin korumasını en üst düzeye çıkaran ve en iyi yapılandırma Microsoft 365 sağlar. Diyagramda da gösterildiği gibi, ayrıcalıklı erişim yönetimi, Microsoft 365 verilerin yerel şifrelemesi ve Microsoft 365 hizmetlerinin rol tabanlı erişim denetim güvenlik modeli ile sağlanan korumayı temel Microsoft 365 sağlar. [Azure AD veritabanıyla Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure), bu iki özellik farklı kapsamlarda tam zamanlı erişim ile erişim denetimi sağlar.

![Katman korumasını Microsoft 365.](../media/pam-layered-protection.png)

Ayrıcalıklı erişim yönetimi görev düzeyinde tanımlanır ve kapsamına kapsamındayken, Azure AD Privileged Identity Management birden çok görevi yürütme özelliğine sahip rol düzeyinde  korumayı uygular. Azure AD Privileged Identity Management, öncelikli olarak AD rolleri ve rol grupları için erişimlerin yönetimine izin verirken, Microsoft 365 düzeyde ayrıcalıklı erişim yönetimi geçerlidir.

- **Azure AD Privileged Identity Management'i** kullanırken ayrıcalıklı erişim yönetimini etkinleştirme: Ayrıcalıklı erişim yönetiminin eklemesi, verilere ayrıcalıklı erişim için bir başka ayrıntılı koruma katmanı ve denetim Microsoft 365 sağlar.

- **Azure AD Privileged Identity Management bir yandan** Office 365'de ayrıcalıklı erişim yönetimini kullanırken diğer yandan da etkinleştirme: Azure AD Privileged Identity Management'in ayrıcalıklı erişim yönetimine eklemesi, verilerin dışarıyla olan ayrıcalıklı erişimini Microsoft 365  temelde kullanıcı rolleri veya kimlik tarafından tanımlanmıştır.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Ayrıcalıklı erişim yönetimi mimarisi ve süreç akışı

Aşağıdaki işlem akışlarından her biri, ayrıcalıklı erişimin mimarisini ve bu erişimin Microsoft 365, denetim ve Exchange alanıyla etkileşim kurmasını ana hatlarıyla özetler.

### <a name="step-1-configure-a-privileged-access-policy"></a>1. Adım: Ayrıcalıklı bir erişim ilkesi yapılandırma

[Microsoft 365 yönetim merkezi veya Exchange](https://admin.microsoft.com) Management PowerShell ile ayrıcalıklı bir erişim ilkesi yapılandırıyorken, bu ilkeyi ve ayrıca erişim özelliği işlemlerini ve ilke özniteliklerini Microsoft 365 tanımlarsınız. Etkinlikler, Güvenlik Uyumluluk Merkezi'nde günlüğe &amp; kaydedilir. İlke artık etkinleştirilmiştir ve onay için gelen istekleri işlemeye hazırdır.

![1. Adım: İlke oluşturma.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>2. Adım: Erişim isteği

Microsoft 365 yönetim merkezi [yönetim merkezi](https://admin.microsoft.com) veya Exchange Yönetim PowerShell ile, kullanıcılar yükseltilmiş veya ayrıcalıklı görevlere erişim isteğinde olabilir. Ayrıcalıklı erişim özelliği, isteği yapılandırılmış ayrıcalık erişim ilkesine yönelik Microsoft 365 için güvenlik alt kaydına gönderir ve Etkinlik'i &amp; Güvenlik Uyumluluk Merkezi günlüklerine kaydeder.

![2. Adım: Erişim isteği.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>3. Adım: Erişim onayı

Bir onay isteği oluşturulur ve onaylayanlara bekleyen istek bildirimi e-postayla gönderilir. Onaylanırsa, ayrıcalıklı erişim isteği onay olarak işlenir ve görev tamamlanmaya hazırdır. Reddedilirse, görev engellenir ve istekte bulundurana erişim izni yoktur. İstekten sonra, istek onayı veya engellemesi e-posta iletisi aracılığıyla size bildirilecek.

![3. Adım: Onaya erişin.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>4. Adım: Access işleme

Onaylanan istek için, görev Yönetim çalışma Exchange tarafından işlenir. Onay, ayrıcalıklı erişim ilkesine göre denetlenir ve Microsoft 365 işlenir. Görevin tüm etkinlikleri Güvenlik Uyumluluk Merkezi'ne &amp; kaydedilir.

![4. Adım: Access işleme.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Hangi SKD'ler tek bir Office 365?

Ayrıcalıklı erişim yönetimi birçok farklı abonelik ve eklenti Microsoft 365 Office 365 müşteriler tarafından kullanılabilir. Ayrıntılar [için bkz. Ayrıcalıklı erişim yönetimiyle](privileged-access-management-configuration.md) çalışmaya başlama.

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Ayrıcalıklı erişim, iş yüklerinin Office 365 yüklerini ne zaman Exchange?

Ayrıcalıklı erişim yönetimi diğer iş yüklerinde Office 365 kullanılabilir. Daha fazla [Microsoft 365 için Yol Haritası'nın](https://www.microsoft.com/microsoft-365/roadmap) sonlarını ziyaret edin.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Kuruluşumda 30'dan fazla ayrıcalıklı erişim ilkelerine ihtiyacı var, bu sınır artırılacak mı?

Evet, her kuruluş için 30 ayrıcalıklı erişim ilkelerinin geçerli sınırını yükselterek özellik yol haritasında yer var.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Office 365'de ayrıcalıklı erişimi yönetmek için Genel Yönetici Office 365?

Hayır, Exchange erişimi yöneten hesaplara atanmış Rol Yönetimi rolüne Office 365. Rol Yönetimi rolünü tek başına bir hesap izni olarak yapılandırmak istemiyorsanız, Genel Yönetici rolü varsayılan olarak bu rolü içerir ve ayrıcalıklı erişimi yönetebilir. Onaylayanlar grubuna dahil olan kullanıcıların Genel Yönetici olması veya PowerShell'de istekleri gözden geçirmek ve onaylamak için Rol Yönetimi rolünün atanmış olması gerekmektedir.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Ayrıcalıklı erişim yönetimi, Müşteri Kilidi ile nasıl ilişkili?

[Müşteri Kilidi,](/office365/admin/manage/customer-lockbox-requests) Microsoft verilere erişirken kuruluşlar için bir erişim denetimi düzeyine izin verir. Ayrıcalıklı erişim yönetimi, tüm fazla güvenlikli görevler için kuruluş içindeki ayrıntılı erişim Microsoft 365 olanak sağlar.

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

Ayrıcalıklı [erişim yönetimi için organizasyonlarınızı yapılandırmaya başlayabilirsiniz](privileged-access-management-configuration.md).

## <a name="learn-more"></a>Daha fazla bilgi

[Etkileşimli kılavuz: Ayrıcalıklı erişim yönetimiyle yönetici görevlerini izleme ve denetleme](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
