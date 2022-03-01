---
title: Denetimde Temel Denetimi Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MOE150
- MET150
description: Bu makalede, kuruluşta kullanıcılar ve yöneticiler tarafından gerçekleştirilen denetim etkinliklerini aramaya başlamak için Temel Denetim'in nasıl ayar tarihi açıklanmıştır.
ms.openlocfilehash: e4ae5901c9a4f400e2a01659395d27947ad433c2
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018815"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a>Denetimde Temel Denetimi Microsoft 365

Denetim bilgileri Microsoft 365, kullanıcılar ve yöneticiler tarafından farklı yönetim hizmetleri içinde gerçekleştirilen Microsoft 365 için denetim kayıtlarını aramanızı sağlar. Çoğu Microsoft 365 ve Office 365 kuruluşta Temel Denetim varsayılan olarak etkinleştirildiğinden, siz ve kuruluşta diğer kuruluşların denetim günlüğünde arama yapamadan önce yalnızca birkaç işlem gerekir.

Bu makalede, Temel Denetimi ayarlamak için gereken aşağıdaki adımlar tartışılacaktır.

![Temel Denetimi ayarlama adımları.](../media/BasicAuditingWorkflow.png)

Bu adımlar, denetim kayıtlarını oluşturmak ve korumak için doğru kuruluş aboneliklerinin ve kullanıcı lisanslarının gerekli olmasını sağlamayı ve güvenlik işlemleri, IT, uyumluluk ve yasal ekip üyelerine denetim günlüğünde arama yapabilecek izinler atamayı içerir.

Daha fazla bilgi [için bkz.](auditing-solutions-overview.md#basic-audit) Microsoft 365.

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>1. Adım: Kuruluş aboneliğini ve kullanıcı lisanslarını doğrulama

Temel Denetim için Lisanslama, denetim günlüğü arama aracına erişim sağlayan uygun kuruluş aboneliği ve denetim kayıtlarını günlüğe kaydederek tutmak için gereken kullanıcı başına lisanslama gerektirir.

Kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirilen, bir denetim kaydı oluşturulur ve kuruluşun denetim günlüğünde depolanır. Temel Denetim'de, denetim kayıtları 90 gün boyunca denetim günlüğünde korunur ve aranabilir.

Temel Denetim için abonelik ve lisans gereksinimlerinin listesi için bkz. Temel [Denetim için Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>2. Adım: Denetim günlüğünde arama yapmak için izin atama

Yöneticiler ve araştırma ekiplerinin üyelerine, denetim View-Only için Exchange Online'de Denetim Günlükleri veya Denetim Günlükleri rolü atanabilir. Varsayılan olarak, bu roller yönetim merkezinin İzinler sayfasında yer alan Uyumluluk Yönetimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. Office 365 ve Microsoft 365 genel yöneticiler otomatik olarak Kuruluş Yönetimi rol grubuna üye olarak Exchange Online. Kullanıcıya denetim günlüğünde en düşük düzeydeki ayrıcalıklarla arama yapma olanağı vermek için, Exchange Online'de özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve sonra da kullanıcıyı yeni rol grubunun üyesi olarak ebilirsiniz. Daha fazla bilgi için bkz[. Gruptaki rol gruplarını Exchange Online](/Exchange/permissions-exo/role-groups).

Aşağıdaki ekran görüntüsünde, denetimle ilgili olarak yönetim merkezinde Kuruluş Yönetimi rol grubuna atanan Exchange gösterir.

![Exchange Online'da rol grubuna atanan Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>3. Adım: Denetim günlüğünde arama

Artık kayıtta denetim günlüğünde arama yapmaya Microsoft 365 uyumluluk merkezi.

1. Uygun denetim <https://compliance.microsoft.com> izinleri atanmış bir hesabı kullanarak gidip oturum açın.

2. Gezinti bölmesinin sol bölmesinde, **Microsoft 365 uyumluluk merkezi'e ve sonra** Denetim'e **tıklayın**.

3. Denetim **sayfasında** , Arama sekmesindeki aşağıdaki koşulları kullanarak **aramanızı yapılandırabilirsiniz** . 

   ![Denetim günlüğü araması için yapılandırma ayarları.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Tarih ve saat aralığı**. Bir tarih ve saat aralığında 2013 olayları görüntülemek için, o tarih ve saat aralığını seçin. Tarih ve saat, yerel saatle birlikte sunulacaktır. Son yedi gün varsayılan olarak seçilidir.
  
   2. **Etkinlikler**. Aranan etkinlikleri seçin. Listeye eklemek istediğiniz etkinlikleri aramak için arama kutusunu kullanın. Denetlenen etkinliklerin kısmi listesi için bkz. [Denetlenen etkinlikler](search-the-audit-log-in-security-and-compliance.md#audited-activities). Tüm denetlenen etkinliklere yönelik girdilerin geri dönmesi için bu kutuyu boş bırakın.
  
   3. **Kullanıcılar.**  Bu kutuya tıklayın ve arama sonuçlarını görüntülemek istediğiniz kullanıcıların adını yazmaya başlayın. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliklere yönelik denetim günlüğü girdileri, sonuç listesinde görüntülenir. Tüm kullanıcılara (ve hizmet hesaplarına) ait girdilerin kuruma geri dönmesi için bu kutuyu boş bırakın.
  
   4. **Dosya, klasör veya site**. Belirtilen anahtar sözcüğü içeren klasör dosyasıyla ilgili etkinliği aramak için, dosya veya klasör adının bir veya hepsini yazın. Dosya veya klasörün URL'sini de belirtebilirsiniz. Dosya veya klasörün URL'sini kullanıyorsanız, tam URL yolunun yaz olduğundan emin olun veya URL'nin bir bölümünü yazın; özel karakter ya da boşluk içermesin. Kuruma ait tüm dosya ve klasörlere ait girdilerin geri dönmesi için bu kutuyu boş bırakın.

4. **Arama'yı** çalıştırmak için Ara'ya tıklayın.

Denetim günlüğü aramanın çalıştırnını gösteren yeni bir sayfa görüntülenir. Arama tamamlandığında, denetim kayıtları sayfada görüntülenir. Ayrıntılı özelliklere sahip bir çıkış sayfası görüntülemek için kayda tıklayın.

Daha ayrıntılı yönergeler için bkz[. Uyumluluk merkezinde denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)
