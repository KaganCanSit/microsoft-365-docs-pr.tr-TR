---
title: Contoso Corporation için kurumsal güvenlik Microsoft 365 özeti
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'nun kuruluş için Microsoft 365 güvenlik özelliklerini kullanma şekli.
ms.openlocfilehash: 7ffde6eec3e5f294311926fa013d9e089ad67e0f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091335"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Contoso Corporation için kurumsal güvenlik Microsoft 365 özeti

Contoso BT güvenlik departmanı, kuruluşa Microsoft 365 dağıtma onayı almak için kapsamlı bir güvenlik incelemesi gerçekleştirdi. Bulut için aşağıdaki güvenlik gereksinimlerini tanımladılar:

- Çalışanların bulut kaynaklarına erişimi için en güçlü kimlik doğrulama yöntemlerini kullanın.
- Bilgisayarların ve mobil cihazların güvenli yollarla uygulamalara bağlandığından ve uygulamalara erişdiğinden emin olun.
- Bilgisayarları ve e-postayı kötü amaçlı yazılımlardan koruyun.
- Bulut tabanlı dijital varlıklar üzerindeki izinler, kimlerin nelere ve neler yapabileceklerine kimlerin erişebileceğini tanımlar ve en az ayrıcalıklı erişim için tasarlanmıştır
- Hassas ve yüksek düzeyde düzenlenmiş dijital varlıklar etiketlenir, şifrelenir ve güvenli konumlarda depolanır.
- Yüksek oranda düzenlenmiş dijital varlıklar ek şifreleme ve izinlerle korunur.
- BT güvenlik personeli, geçerli güvenlik duruşunu merkezi panolardan izleyebilir ve hızlı yanıt ve risk azaltma amacıyla güvenlik olayları hakkında bildirim alabilir.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Güvenlik hazırlığını Microsoft 365 contoso yolu

Contoso, güvenliklerini kuruluş için Microsoft 365 dağıtımına hazırlamak için şu adımları izledi:

1. Bulut için yönetici hesaplarını sınırlama

   Contoso, mevcut Active Directory Domain Services (AD DS) yönetici hesaplarını kapsamlı bir şekilde gözden geçirdi ve bir dizi ayrılmış bulut yöneticisi hesabı ve grubu ayarladı.

2. Verileri üç güvenlik düzeyine sınıflandırma

   Contoso dikkatli bir inceleme yaptı ve en değerli verileri korumak amacıyla kurumsal özelliklerin Microsoft 365 belirlemek için kullanılan üç düzeyi belirledi.

3. Veri düzeyleri için erişim, saklama ve bilgi koruma ilkelerini belirleme

   Contoso, veri düzeylerini temel alarak buluta taşınacak gelecekteki BT iş yüklerini niteleyen ayrıntılı gereksinimleri belirledi.

Contoso güvenlik yöneticileri ve BT departmanı, kurumsal dağıtım gereksinimlerine yönelik en iyi güvenlik uygulamalarını ve Microsoft 365 izlemek için, aşağıdaki bölümlerde açıklandığı gibi birçok güvenlik özelliği ve özelliğini dağıttı.

## <a name="identity-and-access-management"></a>Kimlik ve erişim yönetimi 

- MFA ve PIM ile ayrılmış genel yönetici hesapları

  Contoso, günlük kullanıcı hesaplarına genel yönetici rolü atamak yerine güçlü parolalara sahip üç ayrılmış genel yönetici hesabı oluşturmuştur. Hesaplar Azure AD Multi-Factor Authentication (MFA) ve Azure Active Directory (Azure AD) Privileged Identity Management (PIM) tarafından korunur. *PIM yalnızca Microsoft 365 E5 ile kullanılabilir.*

  **Azure AD DC yöneticisiyle** veya **Genel yönetici** hesabıyla oturum açmak yalnızca belirli yönetim görevleri için yapılır. Parolalar yalnızca belirlenen personel tarafından bilinir ve yalnızca Azure AD PIM'de yapılandırılan bir süre içinde kullanılabilir.

  Contoso güvenlik yöneticileri, BT çalışanının iş işlevine uygun hesaplara daha az yönetici rolü atadı.

  Daha fazla bilgi için bkz. [Microsoft 365 yönetici rolleri hakkında](/office365/admin/add-users/about-admin-roles).

- Tüm kullanıcı hesapları için MFA

  MFA, oturum açma işlemine ek bir koruma katmanı ekler. Kullanıcıların parolalarını doğru bir şekilde girdikten sonra akıllı telefonlarında telefon aramasını, kısa mesajı veya uygulama bildirimini kabul etmelerini gerektirir. MFA ile Azure AD kullanıcı hesapları, bir hesap parolası tehlikeye girse bile yetkisiz oturum açma işlemlerine karşı korunur.

   - contoso, Microsoft 365 aboneliğinin güvenliğinin aşılmasına karşı koruma sağlamak için tüm **Azure AD DC yöneticisinde** veya **Genel yönetici** hesaplarında MFA gerektirir.
   - Bir saldırganın kuruluştaki güvenilir bir kişinin kimlik bilgilerini tehlikeye atıp kötü amaçlı e-posta gönderdiği kimlik avı saldırılarına karşı koruma sağlamak için Contoso, yöneticiler ve yöneticiler de dahil olmak üzere tüm kullanıcı hesaplarında MFA'yı etkinleştirdi.

- Koşullu Erişim ilkeleriyle daha güvenli cihaz ve uygulama erişimi

  Contoso kimlik, cihazlar, Exchange Online ve SharePoint için [Koşullu Erişim ilkeleri](../security/office-365-security/microsoft-365-policies-configurations.md) kullanıyor. Kimlik Koşullu Erişim ilkeleri, yüksek riskli kullanıcılar için parola değişiklikleri gerektirmeyi ve istemcilerin modern kimlik doğrulamasını desteklemeyen uygulamaları kullanmasını engellemeyi içerir. Cihaz ilkeleri, onaylı uygulamaların tanımını ve uyumlu bilgisayarlar ile mobil cihazlar gerektirmeyi içerir. Exchange Online Koşullu Erişim ilkeleri ActiveSync istemcilerini engellemeyi ve Office 365 ileti şifrelemesini ayarlamayı içerir. SharePoint Koşullu Erişim ilkeleri, hassas ve yüksek düzeyde düzenlenmiş siteler için ek koruma içerir.

- İş İçin Windows Hello

  Contoso[, Windows 10 Enterprise](/windows/security/identity-protection/hello-for-business/hello-identity-verification) çalıştıran bilgisayarlarda ve mobil cihazlarda güçlü iki faktörlü kimlik doğrulaması aracılığıyla parola gereksinimini ortadan kaldırmak için İş İçin Windows Hello dağıttı.

- Windows Defender Credential Guard

  Contoso, işletim sisteminde çalışan hedefli saldırıları ve kötü amaçlı yazılımları yönetim ayrıcalıklarıyla engellemek için AD DS grup ilkesi aracılığıyla [Credential Guard Windows Defender](/windows/security/identity-protection/credential-guard/credential-guard) etkinleştirdi.

## <a name="threat-protection"></a>Tehdit koruması

- Windows Defender Virüsten Koruma ile kötü amaçlı yazılımlara karşı koruma

  Contoso, [Windows 10 Enterprise](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) çalıştıran bilgisayarlar ve cihazlar için kötü amaçlı yazılımdan koruma ve kötü amaçlı yazılımdan koruma yönetimi için Windows Defender Virüsten Koruma kullanıyor.

- Office 365 için Microsoft Defender ile e-posta akışının ve posta kutusu denetim günlüğünün güvenliğini sağlama 

  Contoso, e-postalar aracılığıyla iletilen bilinmeyen kötü amaçlı yazılımlara, virüslere ve kötü amaçlı URL'lere karşı koruma sağlamak için [Exchange Online Protection ve Office 365 için Defender](/office365/securitycompliance/office-365-atp) kullanıyor.

  Contoso ayrıca kullanıcı posta kutularında kimlerin oturum açtığını, ileti gönderdiğini ve posta kutusu sahibi, temsilci kullanıcı veya yönetici tarafından gerçekleştirilen diğer etkinlikleri belirlemek için posta kutusu denetim günlüğünü etkinleştirdi.

- Office 365 tehdit araştırması ve yanıtı ile saldırı izleme ve önleme

  Contoso, saldırıları tanımlamayı ve ele almalarını kolaylaştırarak ve gelecekteki saldırıları önleyerek kullanıcıları korumak için [Office 365 tehdit araştırması ve yanıtı](/office365/securitycompliance/office-365-ti) kullanır.

- Gelişmiş Tehdit Analizi ile gelişmiş saldırılara karşı koruma

  Contoso, kendisini gelişmiş hedefli [saldırılardan korumak için Advanced Threat Analytics 'i (ATA)](/advanced-threat-analytics/what-is-ata) kullanıyor.  ATA normal ve anormal varlık (kullanıcı, cihazlar ve kaynaklar) davranışını otomatik olarak analiz eder, öğrenir ve tanımlar.

## <a name="information-protection"></a>Bilgi koruması

- Azure Information Protection etiketleriyle hassas ve yüksek oranda düzenlenmiş dijital varlıkları koruma

  Contoso, kullanıcıların dijital varlıklara uyguladığı üç veri koruma düzeyi belirledi ve [Microsoft 365 duyarlılık etiketleri](../compliance/sensitivity-labels.md) dağıttı. Contoso, ticari gizli dizileri ve diğer fikri mülkiyetleri için yüksek düzeyde düzenlenmiş veriler için duyarlılık alt etiketlerini kullanır. Bu işlem içeriği şifreler ve belirli kullanıcı hesaplarına ve gruplarına erişimi kısıtlar.

- Veri Kaybı Önleme ile intranet veri sızıntılarını önleme

  Contoso, kullanıcıların yanlışlıkla veya kasıtlı olarak hassas verileri paylaşmasını önlemek amacıyla Exchange Online, SharePoint ve OneDrive İş için [Microsoft Purview Veri Kaybı Önleme](../compliance/dlp-learn-about-dlp.md) ilkelerini yapılandırdı.

- Cihaz veri sızıntılarını önleme Windows Information Protection

  Contoso, İnternet tabanlı uygulamalar ve hizmetler ve kurumsal uygulamalar aracılığıyla veri sızıntısına karşı koruma sağlamak için [Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) kullanıyor ve çalışanların işe getirdiği kurumsal cihazlar ve kişisel cihazlardaki veriler.

- Microsoft Defender for Cloud Apps ile bulut izleme

  Contoso, bulut ortamını eşlemek, kullanımını izlemek ve güvenlik olaylarını ve olaylarını algılamak için [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) kullanıyor. *Microsoft Defender for Cloud Apps yalnızca Microsoft 365 E5 ile kullanılabilir.*

- Cihaz yönetimi ve Microsoft Intune

  Contoso, mobil cihazlara ve üzerinde çalışan uygulamalara erişimi kaydetmek, yönetmek ve yapılandırmak için [Microsoft Intune](/intune/introduction-intune) kullanır. Cihaz tabanlı Koşullu Erişim ilkeleri ayrıca onaylı uygulamalar, uyumlu bilgisayarlar ve mobil cihazlar gerektirir.

## <a name="security-management"></a>Güvenlik yönetimi

- Bulut için Microsoft Defender ile BT için merkezi güvenlik panosu

  Contoso[, güvenlik](https://azure.microsoft.com/services/security-center/) ve tehdit korumasının birleşik bir görünümünü sunmak, iş yükleri genelinde güvenlik ilkelerini yönetmek ve siber saldırılara yanıt vermek için Bulut için Microsoft Defender kullanır.

- Windows Defender Güvenlik Merkezi'ne sahip kullanıcılar için merkezi güvenlik panosu

  Contoso[, kullanıcıların güvenlik](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) duruşlarını bir bakışta görebilmeleri ve eyleme geçebilmeleri için Windows Güvenliği uygulamasını Windows 10 Enterprise çalıştıran bilgisayarlarına ve cihazlarına dağıttı.
