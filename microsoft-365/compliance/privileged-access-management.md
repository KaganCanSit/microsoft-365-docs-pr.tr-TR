---
title: Ayrıcalıklı erişim yönetimi hakkında daha fazla bilgi edinme
description: Bu makalede, sık sorulan soruların (SSS) yanıtları da dahil olmak üzere Microsoft Purview'da ayrıcalıklı erişim yönetimi hakkında genel bir bakış sağlanmaktadır.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, ayrıcalıklı erişim yönetimi
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
ms.openlocfilehash: 6bf13adb96ae5d4d4030ebe44f10dab22602196e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622557"
---
# <a name="learn-about-privileged-access-management"></a>Ayrıcalıklı erişim yönetimi hakkında daha fazla bilgi edinme

Microsoft Purview Privileged Access Management, Office 365 ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim denetimi sağlar. Kuruluşunuzun hassas verilere veya kritik yapılandırma ayarlarına erişimi olan mevcut ayrıcalıklı yönetici hesaplarını kullanan ihlallere karşı korunmasına yardımcı olabilir. Ayrıcalıklı erişim yönetimi, kullanıcıların yüksek kapsamlı ve zamana bağlı bir onay iş akışı aracılığıyla yükseltilmiş ve ayrıcalıklı görevleri tamamlamak için tam zamanında erişim istemelerini gerektirir. Bu yapılandırma, kullanıcılara hassas verilerin veya kritik yapılandırma ayarlarının açığa çıkmadan eldeki görevi gerçekleştirmeleri için yeterli erişim sağlar. Ayrıcalıklı erişim yönetiminin etkinleştirilmesi, kuruluşunuzun sıfır daimi ayrıcalıklarla çalışmasına ve yönetim erişim açıklarına karşı bir savunma katmanı sağlamasına olanak tanır.

Tümleşik Müşteri Kasası ve ayrıcalıklı erişim yönetimi iş akışına hızlı bir genel bakış için bu [Müşteri Kasası ve ayrıcalıklı erişim yönetimi videosuna](https://go.microsoft.com/fwlink/?linkid=2066800) bakın.

## <a name="layers-of-protection"></a>Koruma katmanları

Ayrıcalıklı erişim yönetimi, Microsoft 365 güvenlik mimarisindeki diğer verileri ve erişim özelliği korumalarını tamamlar. Tümleşik ve katmanlı bir güvenlik yaklaşımının parçası olarak ayrıcalıklı erişim yönetimi dahil etmek, hassas bilgilerin ve Microsoft 365 yapılandırma ayarlarının korunmasını en üst düzeye çıkaran bir güvenlik modeli sağlar. Diyagramda gösterildiği gibi ayrıcalıklı erişim yönetimi, Microsoft 365 verilerinin yerel olarak şifrelenmesi ve Microsoft 365 hizmetlerinin rol tabanlı erişim denetimi güvenlik modeli ile sağlanan korumayı temel alır. [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) ile kullanıldığında, bu iki özellik farklı kapsamlarda tam zamanında erişim ile erişim denetimi sağlar.

![Microsoft 365'te katmanlı koruma.](../media/pam-layered-protection.png)

Ayrıcalıklı erişim yönetimi **görev** düzeyinde tanımlanır ve kapsamı belirlenirken, Azure AD Privileged Identity Management birden çok görevi yürütme özelliğiyle **rol** düzeyinde koruma uygular. Azure AD Privileged Identity Management öncelikle AD rolleri ve rol grupları için erişimlerin yönetilmesine izin verirken, Microsoft Purview Privileged Access Management yalnızca görev düzeyinde geçerlidir.

- **Azure AD Privileged Identity Management kullanırken ayrıcalıklı erişim yönetimini etkinleştirme:** Ayrıcalıklı erişim yönetimi eklemek, Microsoft 365 verilerine ayrıcalıklı erişim için başka bir ayrıntılı koruma ve denetim özellikleri katmanı sağlar.

- **Microsoft Purview Privileged Access Management'ı kullanırken Azure AD Privileged Identity Management etkinleştirme:** Azure AD Privileged Identity Management ekleme  Microsoft Purview Privileged Access Management'a, öncelikli olarak kullanıcı rolleri veya kimliği tarafından tanımlanan Microsoft 365 dışındaki verilere ayrıcalıklı erişimi genişletebilir.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Ayrıcalıklı erişim yönetimi mimarisi ve işlem akışı

Aşağıdaki işlem akışlarının her biri ayrıcalıklı erişim mimarisini ve Bunun Microsoft 365 alt yapısı, denetimi ve Exchange Yönetimi çalışma alanıyla nasıl etkileşime geçtiğini özetler.

### <a name="step-1-configure-a-privileged-access-policy"></a>1. Adım: Ayrıcalıklı erişim ilkesi yapılandırma

[Microsoft 365 yönetim merkezi](https://admin.microsoft.com) veya Exchange Management PowerShell ile ayrıcalıklı bir erişim ilkesi yapılandırdığınızda, microsoft 365 alt klasöründe ilkeyi ve ayrıcalıklı erişim özelliği işlemlerini ve ilke özniteliklerini tanımlarsınız. Etkinlikler Güvenlik &amp; Uyumluluk Merkezi'nde günlüğe kaydedilir. İlke artık etkindir ve onaylar için gelen istekleri işlemeye hazırdır.

![1. Adım: İlke oluşturma.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>2. Adım: Erişim isteği

[Microsoft 365 yönetim merkezi](https://admin.microsoft.com) veya Exchange Management PowerShell ile kullanıcılar yükseltilmiş veya ayrıcalıklı görevlere erişim isteyebilir. Ayrıcalıklı erişim özelliği, isteği yapılandırılan ayrıcalık erişim ilkesine göre işlenmek üzere Microsoft 365 alt katmanına gönderir ve Etkinliği Güvenlik &amp; Uyumluluk Merkezi günlüklerine kaydeder.

![2. Adım: Erişim isteği.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>3. Adım: Erişim onayı

Onay isteği oluşturulur ve bekleyen istek bildirimi onaylayanlara e-postayla gönderilir. Onaylanırsa, ayrıcalıklı erişim isteği onay olarak işlenir ve görev tamamlanmaya hazırdır. Reddedilirse, görev engellenir ve istekte bulunana erişim verilmez. İstek sahibine e-posta iletisi aracılığıyla istek onayı veya reddi bildirilir.

![3. Adım: Erişim onayı.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>4. Adım: Erişim işleme

Onaylanan bir istek için görev Exchange Yönetimi çalışma alanı tarafından işlenir. Onay, ayrıcalıklı erişim ilkesine göre denetlenip Microsoft 365 alt tabaka tarafından işlenir. Görevin tüm etkinlikleri Güvenlik &amp; Uyumluluk Merkezi'nde günlüğe kaydedilir.

![4. Adım: Erişim işleme.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Hangi SKU'lar Office 365 ayrıcalıklı erişimi kullanabilir?

Ayrıcalıklı erişim yönetimi, çok çeşitli Microsoft 365 ve Office 365 abonelikleri ile eklentileri için müşteriler tarafından kullanılabilir. Ayrıntılar için bkz. [Ayrıcalıklı erişim yönetimini kullanmaya başlama](privileged-access-management-configuration.md) .

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Ayrıcalıklı erişim, Exchange'in ötesindeki iş yüklerini Office 365 ne zaman desteklenecek?

Ayrıcalıklı erişim yönetimi yakında diğer Office 365 iş yüklerinde kullanılabilir olacak. Diğer ayrıntılar için [Microsoft 365 Yol Haritası'nı](https://www.microsoft.com/microsoft-365/roadmap) ziyaret edin.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Kuruluşumun 30'dan fazla ayrıcalıklı erişim ilkesine ihtiyacı var, bu sınır artırılacak mı?

Evet, kuruluş başına geçerli 30 ayrıcalıklı erişim ilkesi sınırının artırılması özellik yol haritasındadır.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Office 365'da ayrıcalıklı erişimi yönetmek için Genel Yönetici olmak gerekiyor mu?

Hayır, Office 365'da ayrıcalıklı erişimi yöneten hesaplara Exchange Rol Yönetimi rolünün atanmış olması gerekir. Rol Yönetimi rolünü tek başına hesap izni olarak yapılandırmak istemiyorsanız, Genel Yönetici rolü varsayılan olarak bu rolü içerir ve ayrıcalıklı erişimi yönetebilir. Onaylayanların grubuna dahil olan kullanıcıların Genel Yönetici olması veya PowerShell ile istekleri gözden geçirmek ve onaylamak için Rol Yönetimi rolünün atanmış olması gerekmez.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Ayrıcalıklı erişim yönetimi Müşteri Kasası ile nasıl ilişkilidir?

[Müşteri Kasası](/office365/admin/manage/customer-lockbox-requests) , Microsoft verilere eriştiğinde kuruluşlar için bir erişim denetimi düzeyi sağlar. Ayrıcalıklı erişim yönetimi, tüm Microsoft 365 ayrıcalıklı görevleri için kuruluş içinde ayrıntılı erişim denetimine olanak tanır.

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

[Kuruluşunuzu ayrıcalıklı erişim yönetimi için yapılandırmaya](privileged-access-management-configuration.md) başlayın.

## <a name="learn-more"></a>Daha fazla bilgi

[Etkileşimli kılavuz: Ayrıcalıklı erişim yönetimi ile yönetici görevlerini izleme ve denetleme](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
