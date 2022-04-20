---
title: Microsoft 365'de Denetimi Ayarlama (Standart)
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
description: Bu makalede, kuruluşunuzdaki kullanıcılar ve yöneticiler tarafından gerçekleştirilen denetim etkinliklerini aramaya başlayabilmeniz için Denetimin (Standart) nasıl ayarlanacağı açıklanır.
ms.openlocfilehash: 93245abfc4f57b22d6db715103f93428487a648d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936059"
---
# <a name="set-up-microsoft-purview-audit-standard"></a>Microsoft Purview Denetimini Ayarlama (Standart)

Microsoft 365'deki Microsoft Purview Denetimi (Standart), kullanıcılar ve yöneticiler tarafından farklı Microsoft 365 hizmetlerinde gerçekleştirilen etkinliklerin denetim kayıtlarını aramanızı sağlar. Denetim (Standart) çoğu Microsoft 365 ve Office 365 kuruluş için varsayılan olarak etkinleştirildiğinden, siz ve kuruluşunuzdaki diğer kişilerin denetim günlüğünde arama yapabilmesi için yapmanız gereken yalnızca birkaç şey vardır.

Bu makalede, Denetimi (Standart) ayarlamak için gereken aşağıdaki adımlar ele alınmaktadır.

![Denetimi ayarlama adımları (Standart).](../media/BasicAuditingWorkflow.png)

Bu adımlar, denetim kayıtlarını oluşturmak ve korumak için gereken uygun kuruluş aboneliklerini ve kullanıcı lisanslarını sağlamayı ve denetim günlüğünde arama yapmak için güvenlik işlemlerinizin, BT, uyumluluk ve yasal ekiplerinizin ekip üyelerine izinler atamayı içerir.

Daha fazla bilgi için bkz. [Microsoft 365'de Denetim (Standart](auditing-solutions-overview.md#audit-standard)).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>1. Adım: Kuruluş aboneliğini ve kullanıcı lisanslama bilgilerini doğrulama

Denetim için Lisanslama (Standart), denetim kayıtlarını günlüğe kaydetmek ve tutmak için gereken denetim günlüğü arama aracına ve kullanıcı başına lisanslamaya erişim sağlayan uygun kuruluş aboneliğini gerektirir.

Bir kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirildiğinde, bir denetim kaydı oluşturulur ve kuruluşunuz için denetim günlüğünde depolanır. Denetim (Standart) bölümünde denetim kayıtları 90 gün boyunca denetim günlüğünde tutulur ve aranabilir.

Denetim (Standart) için abonelik ve lisans gereksinimlerinin listesi için bkz. [Microsoft 365'de denetim çözümleri](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>2. Adım: Denetim günlüğünde arama yapmak için izinler atama

Araştırma ekiplerinin yöneticilerine ve üyelerine denetim günlüğünde arama yapmak için Exchange Online'da View-Only Denetim Günlükleri veya Denetim Günlükleri rolü atanmalıdır. Varsayılan olarak, bu roller <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezindeki</a> **İzinler** sayfasındaki Uyumluluk Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Office 365 ve Microsoft 365'deki genel yöneticiler otomatik olarak Exchange Online'da Kuruluş Yönetimi rol grubunun üyeleri olarak eklenir. Kullanıcıya en düşük ayrıcalık düzeyiyle denetim günlüğünde arama yapma olanağı vermek için, Exchange Online'da özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve kullanıcıyı yeni rol grubunun bir üyesi olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [Exchange Online rol gruplarını yönetme](/Exchange/permissions-exo/role-groups).

Aşağıdaki ekran görüntüsünde, Exchange yönetim merkezindeki Kuruluş Yönetimi rol grubuna atanan denetimle ilgili iki rol gösterilmektedir.

![Exchange Online rol grubuna atanan rolleri denetleme.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>3. Adım: Denetim günlüğünde arama yapma

Artık Microsoft Purview uyumluluk portalında denetim günlüğünde arama yapmaya hazırsınız.

1. <https://compliance.microsoft.com> Adresine gidin ve uygun denetim izinlerine atanmış bir hesabı kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Tümünü göster'e** ve ardından **Denetim'e** tıklayın.

3. **Denetim** sayfasında, **Arama** sekmesinde aşağıdaki koşulları kullanarak aramayı yapılandırın. 

   ![Denetim günlüğü araması için yapılandırma ayarları.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Tarih ve saat aralığı**. Bu dönemde gerçekleşen olayları görüntülemek için bir tarih ve saat aralığı seçin. Tarih ve saat yerel saatte gösterilir. Son yedi gün varsayılan olarak seçilir.
  
   2. **Etkinlikler**. Aranacak etkinlikleri seçin. Listeye eklenecek etkinlikleri aramak için arama kutusunu kullanın. Denetlenen etkinliklerin kısmi listesi için bkz. [Denetlenen etkinlikler](search-the-audit-log-in-security-and-compliance.md#audited-activities). Tüm denetlenen etkinliklerin girdilerini döndürmek için bu kutuyu boş bırakın.
  
   3. **Kullanıcılar**.  Bu kutuya tıklayın ve arama sonuçlarının görüntüleneceği kullanıcıların adını yazmaya başlayın. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliklerin denetim günlüğü girişleri, sonuç listesinde görüntülenir. Kuruluşunuzdaki tüm kullanıcıların (ve hizmet hesaplarının) girdilerini döndürmek için bu kutuyu boş bırakın.
  
   4. **Dosya, klasör veya site**. Belirtilen anahtar sözcüğü içeren klasör dosyasıyla ilgili etkinliği aramak için bir dosya veya klasör adının bir kısmını veya tümünü yazın. Ayrıca bir dosya veya klasörün URL'sini de belirtebilirsiniz. Bir dosya veya klasörün URL'sini kullanıyorsanız, tam URL yolunu yazdığınızdan veya URL'nin bir bölümünü yazdığınızdan emin olun, özel karakter veya boşluk eklemeyin. Kuruluşunuzdaki tüm dosya ve klasörlerin girdilerini döndürmek için bu kutuyu boş bırakın.

4. Aramayı çalıştırmak için **Ara'ya** tıklayın.

Denetim günlüğü aramasının çalıştığını gösteren yeni bir sayfa görüntülenir. Arama tamamlandığında, denetim kayıtları sayfada görüntülenir. Ayrıntılı özelliklere sahip bir açılır sayfa görüntülemek için bir kayda tıklayın.

Daha ayrıntılı yönergeler için bkz [. Uyumluluk merkezinde denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.
