---
title: Contoso Corporation Microsoft 365 kurumsal güvenlik bilgileri özeti
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'ya kurumsal güvenlik özelliklerini Microsoft 365 nasıl kullanır?
ms.openlocfilehash: 15fd559b6dade63d56647c8f5f3437a57d27a56b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005465"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Contoso Corporation Microsoft 365 kurumsal güvenlik bilgileri özeti

Kuruluşta posta dağıtımı Microsoft 365 için Contoso IT güvenlik bölümü, kapsamlı bir güvenlik incelemesi yürütdü. Bulut için aşağıdaki güvenlik gereksinimlerini belirlediler:

- Çalışanların bulut kaynaklarına erişimi için en güçlü kimlik doğrulama yöntemlerini kullanın.
- Bilgisayarların ve mobil cihazların uygulamalara güvenli bir şekilde bağlana olduğundan ve bu uygulamalara erişe olduğundan emin olun.
- Bilgisayarları ve e-postaları kötü amaçlı yazılımdan koruyun.
- Bulut tabanlı dijital varlıklara izinler, kimlerin nelere, nelere eriş yalnızca ayrıcalıkla erişe bir şekilde erişe olduklarını tanımlar ve en az ayrıcalıkla erişim için tasarlanmıştır
- Hassas ve yüksek düzeyde düzenlenmiş dijital varlıklar etiketlenir, şifrelenir ve güvenli konumlarda depolanır.
- Yüksek düzeyde düzenlemeye tabi dijital varlıklar ek şifreleme ve izinlerle korunur.
- IT güvenlik personeli, merkezi panolardan geçerli güvenlik durumunu izleyebilir ve hızlı yanıt ve azaltma için güvenlik olayları hakkında bilgi edinebilirsiniz.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Hazır güvenlik hazırlığı Microsoft 365 Contoso yolu

Contoso, kurumsal dağıtım için güvenliklerini hazırlamak için şu Microsoft 365 takip etti:

1. Bulut için yönetici hesaplarını sınırlama

   Contoso, mevcut Active Directory Etki Alanı Hizmetleri (AD DS) yönetici hesapları üzerinde kapsamlı bir inceleme yaptı ve özel bulut yöneticisi hesapları ile grupları serisini kuramadı.

2. Verileri üç güvenlik düzeyine göre sınıflandır

   Contoso dikkatli bir inceleme yaptı ve en değerli verileri korumak için Microsoft 365 özelliklerini belirlemek için kullanılan üç düzeyi belirledi.

3. Veri düzeyleri için erişim, bekletme ve bilgi koruma ilkelerini belirleme

   Contoso, veri düzeylerine bağlı olarak buluta taşınan gelecekteki IT iş yüklerini hak kazanmak için ayrıntılı gereksinimler belirledi.

Kurumsal dağıtım gereksinimlerine yönelik en iyi Microsoft 365 ve güvenlik uygulamalarını takip etmek için, Contoso güvenlik yöneticileri ve onun IT bölümü birçok güvenlik özelliği ve özelliği, aşağıdaki bölümlerde açıklandığı gibi dağıtmıştır.

## <a name="identity-and-access-management"></a>Kimlik ve erişim yönetimi 

- MFA ve PIM ile adanmış genel yönetici hesapları

  Contoso, genel yönetici rolünü günlük kullanıcı hesaplarına atamak yerine güçlü parolalara sahip üç özel genel yönetici hesabı oluşturdu. Hesaplar, Azure AD Multi-Factor Authentication (MFA) ve Azure AD (Azure AD) Azure Active Directory (PIM) Privileged Identity Management tarafından korunur. *PIM yalnızca özel Microsoft 365 E5.*

  **Azure AD DC yöneticisi veya Genel yönetici** hesabıyla **oturum** açma yalnızca belirli yönetim görevleri için yapılır. Parolalar yalnızca belirlenen personel olarak bilinir ve yalnızca Azure AD PIM'de yapılandırılan bir süre içinde kullanılabilir.

  Contoso güvenlik yöneticileri, BU çalışanın işinin işlevine uygun hesaplara daha az yönetici rolü atadı.

  Daha fazla bilgi için bkz[. Microsoft 365 rolleri hakkında](/office365/admin/add-users/about-admin-roles).

- Tüm kullanıcı hesapları için MFA

  MFA, oturum açma işlemi için ek bir koruma katmanı ekler. Kullanıcıların parolalarını doğru girdikten sonra akıllı telefonlarında bir telefon aramasını, kısa mesajı veya uygulama bildirimini kabullerini gerektirir. MFA ile, Bir hesap parolası ihlal edilmiş olsa bile Azure AD kullanıcı hesapları yetkisiz oturum açmalara karşı korunur.

   - Yeni aboneliğin güvenliğinin tehlikeye Microsoft 365 için Contoso'ya tüm **Azure AD DC** yöneticisi veya Genel yönetici hesaplarından MFA gerekir.
   - Kimlik avı saldırılarına karşı korunmak için, bir saldırgan kuruluşta güvenilir bir kişinin kimlik bilgilerini tehlikeye atarak kötü amaçlı e-postalar gönderirken, Contoso yöneticiler ve yöneticiler de dahil olmak üzere tüm kullanıcı hesapları için MFA'ya olanak sağladı.

- Koşullu Erişim ilkeleriyle daha güvenli cihaz ve uygulama erişimi

  Contoso kimlik[, cihazlar, belgeler](../security/office-365-security/microsoft-365-policies-configurations.md) ve diğer belgeler için Koşullu Exchange Online ilkeleri SharePoint. Kimlik Koşullu Erişim ilkeleri, yüksek riskli kullanıcılar için parola değişiklikleri gerektirmeyi ve istemcilerin modern kimlik doğrulamasını desteklemeyen uygulamaları kullanmalarını engellemeyi içerir. Cihaz ilkeleri onaylanan uygulamaların tanımını ve uyumlu bilgisayarları ve mobil cihazları gerektiren uygulamaları içerir. Exchange Online Erişimi ilkeleri arasında ActiveSync istemcilerini engelleme ve ileti şifreleme Office 365 vardır. SharePoint koşullu Erişim ilkeleri hassas ve yüksek düzeyde düzenlemeye tabi siteler için ek koruma içerir.

- Windows Hello Kurumsal

  Contoso, [Windows Hello çalıştıran](/windows/security/identity-protection/hello-for-business/hello-identity-verification) bilgisayarlarda ve mobil cihazlarda güçlü iki faktörlü kimlik doğrulaması yoluyla parola ihtiyacının ortadan kaldırılması için İş için Windows 10 Enterprise.

- Windows Defender Credential Guard

  İşletim sisteminde çalışan hedefli saldırıları ve kötü amaçlı yazılımı yönetim ayrıcalıklarıyla engellemek için Contoso, AD DS [grup ilkesi aracılığıyla Windows Defender Credential Guard'ın](/windows/security/identity-protection/credential-guard/credential-guard) etkinleştirildi.

## <a name="threat-protection"></a>Tehdit koruması

- Kötü amaçlı yazılımdan ve yazılımdan Windows Defender Virüsten Koruma

  Contoso, kötü [amaçlı Windows Defender Virüsten Koruma](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) koruma ve kötü amaçlı yazılımdan koruma ile çalışan bilgisayarlar ve cihazlar için kötü amaçlı yazılımdan koruma Windows 10 Enterprise.

- Microsoft Defender ile e-posta akışının ve posta kutusu denetim günlüğünün güvenliğini Office 365 

  Contoso, bilinmeyen kötü amaçlı Exchange Online Protection ve virüslere [ve e-postalarla](/office365/securitycompliance/office-365-atp) iletilen kötü amaçlı URL'lere karşı korumak amacıyla Office 365 için Office 365 Defender kullanıyor.

  Contoso ayrıca, kullanıcı posta kutularında kimlerin oturum açtığını belirlemek, ileti göndermek ve posta kutusu sahibi, temsili kullanıcı veya yönetici tarafından gerçekleştirilen diğer etkinlikleri yapmak için posta kutusu denetim günlüğünü de etkinleştirdi.

- Tehdit soruşturması ve yanıt Office 365 saldırı izleme ve önleme

  Contoso, [Office 365 belirlemeyi ve](/office365/securitycompliance/office-365-ti) adresleri belirlemeyi ve gelecekteki saldırılardan korunmayı kolaylaştırarak tehdit soruşturması ve yanıtını kullanır.

- Gelişmiş Tehdit Analizi ile gelişmiş saldırılara karşı koruma

  Contoso, kendisini [gelişmiş hedefli saldırılardan korumak](/advanced-threat-analytics/what-is-ata) için Gelişmiş Tehdit Analizi (ATA) kullanıyor.  ATA normal ve olağandışı varlık (kullanıcı, cihazlar ve kaynaklar) davranışını otomatik olarak analiz eder, öğrenir ve tanımlar.

## <a name="information-protection"></a>Bilgi koruması

- Azure Information Protection etiketleriyle hassas ve yüksek düzeyde düzenlemeye tabi dijital varlıkları koruyun

  Contoso tarafından belirlenen üç veri koruma düzeyi ve kullanıcıların [dijital Microsoft 365 ilgili duyarlılık](../compliance/sensitivity-labels.md) etiketlerinin dağıtıldı. Contoso ticari sırrı ve diğer fikri mülkiyeti için, yüksek düzeyde düzenlemeye tabi veriler için duyarlılık alt etiketlerini kullanır. Bu işlem içeriği şifreler ve belirli kullanıcı hesaplarıyla gruplara erişimi kısıtlar.

- Veri Kaybını Önleme ile intranet veri sızıntılarını önleme

  Kullanıcıların yanlışlıkla veya [bilerek hassas verileri](../compliance/dlp-learn-about-dlp.md) paylaşmasını önlemek Exchange Online, SharePoint ve OneDrive İş için Contoso tarafından yapılandırılmış Veri Kaybı Önleme ilkeleri.

- Bilgi Koruması ile cihaz veri Windows sızıntılarını önleme

  Contoso, İnternet tabanlı uygulamalar ve hizmetler ile kurumsal uygulamalar ve çalışanların çalışmaya getirdiği kurumsal cihazlarda ve kişisel cihazlardaki veriler aracılığıyla veri sızıntısını önlemek için Windows Bilgi Koruması [(WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) kullanıyor.

- Bulut Uygulamaları için Microsoft Defender ile bulut izleme

  Contoso, bulut [ortamlarını eşlemek](/cloud-app-security/what-is-cloud-app-security) , kullanımını izlemek ve güvenlik olaylarını ve olayları algılamak için Bulut Uygulamaları için Microsoft Defender'ı kullanıyor. *Bulut Uygulamaları için Microsoft Defender yalnızca Microsoft 365 E5.*

- Cihaz yönetimi ve Microsoft Intune

  Contoso, [Microsoft Intune](/intune/introduction-intune) cihazlara ve bu cihazlarda çalışan uygulamalara erişimi kaydetmek, yönetmek ve yapılandırmak için bu uygulamaları kullanır. Cihaz Tabanlı Koşullu Erişim ilkeleri ayrıca onaylanmış uygulamaları, uyumlu bilgisayarları ve mobil cihazları da gerektirir.

## <a name="security-management"></a>Güvenlik yönetimi

- Bulut için Microsoft Defender ile IT için merkezi güvenlik panosu

  Contoso, bulut için [Microsoft Defender'ı](https://azure.microsoft.com/services/security-center/) kullanarak birleşik bir güvenlik ve tehdit koruması görünümü sunar, iş yükleri genelinde güvenlik ilkelerini yönetir ve siber saldırılara yanıt verir.

- Windows Defender Güvenlik Merkezi'ne sahip kullanıcılar için merkezi güvenlik panosu

  Contoso, Windows Güvenliği [bir](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) bakışta güvenlik nedenlerini görmek ve önlem almak için Windows 10 Enterprise çalışan bilgisayarlarına ve cihazlarına uygulama dağıttı.
