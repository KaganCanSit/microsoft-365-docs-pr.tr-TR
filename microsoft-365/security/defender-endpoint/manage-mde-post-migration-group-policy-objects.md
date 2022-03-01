---
title: Grup İlkesi Nesnelerini Kullanarak Uç Nokta için Microsoft Defender'ı Yönetme
description: Grup İlkesi Nesneleriyle Uç Nokta için Microsoft Defender'ı yönetmeyi öğrenin
keywords: geçiş sonrası, yönetme, işlemler, bakım, kullanım, PowerShell, Uç Nokta için Microsoft Defender, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2155c72d7008bf3669a1908b3fd866877eb36a7c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016714"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Grup İlkesi Nesneleriyle Uç Nokta için Microsoft Defender'ı Yönetme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> [Microsoft Endpoint Manager'i](/mem) kullanarak, kuruluşta cihazlar için tehdit koruması özelliklerini (uç nokta olarak da adlandırılır) yönetmenizi öneririz. Endpoint Manager[, Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [ve Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction). **[Daha fazla bilgi Endpoint Manager](/mem/endpoint-manager-overview)**.

Uç Nokta için Microsoft Defender'da bazı ayarları yönetmek Azure Active Directory Alanı Hizmetleri'nden Grup İlkesi Nesneleri'ne yönetebilirsiniz.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Grup İlkesi Nesneleriyle Uç Nokta için Microsoft Defender'ı Yapılandırma

> [!NOTE]
> [Windows Server 2012 R2 ve 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview) için yeni, birleşik Uç nokta çözümü olan Birleşik Microsoft Defender'ı kullanıyorsanız, uç nokta için doğru Microsoft Defender ilke seçeneklerine erişmek için lütfen merkezi mağazanıza en son ADMX dosyalarını kullanırkenn emin olun. Genel Web [Site'de](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Grup İlkesi Yönetim Şablonları için Merkezi Mağaza oluşturma ve yönetme Windows ve **Windows 10.** 

Aşağıdaki tabloda, Grup İlkesi Nesneleriyle Uç Nokta için Microsoft Defender'ı yapılandırmak üzere gerçekleştirebilirsiniz çeşitli görevler listele.

<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**Kullanıcı ve bilgisayar nesnelerinin ayarlarını yönetme** <br/><br/> *Yerleşik Grup İlkesi Nesnelerini özelleştirin veya kuruluş gereksinimlerinize uygun olarak özel Grup İlkesi Nesneleri ve kuruluş birimleri oluşturun.*|[Bir Etki Alanı Hizmetleri tarafından yönetilen Azure Active Directory içinde Grup İlkesi yönetme](/azure/active-directory-domain-services/manage-group-policy)|
|**E-Microsoft Defender Virüsten Koruma** <br/><br/> *Virüsten koruma & ilke ayarları, dışlamalar, düzeltme ve kuruluş cihazlarında zamanlanmış taramalar (uç noktalar olarak da adlandırılır) dahil olmak üzere bu özellikleri yapılandırabilirsiniz.*|[Grup İlkesi ayarlarını kullanarak grup ayarlarını yapılandırma ve Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Buluta teslim edilen korumayı etkinleştirmek için Grup İlkesi kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Saldırı yüzeyini azaltma kurallarını yönetin** <br/><br/> *Saldırı alanı azaltma kurallarınızı, dosyaların ve klasörlerin & kullanıcıların cihazlarında görünen bildirim uyarılarında özel metin ekleyerek özelleştirin.*|[Grup İlkesi Nesneleri ile saldırı yüzeyini azaltma kurallarını özelleştirin](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders)|
|**Exploit protection ayarlarını yönetme** <br/><br/> *Exploit Protection ayarlarınızı özelleştirilebilir, bir yapılandırma dosyasını içeri aktarabilirsiniz ve sonra bu yapılandırma dosyasını dağıtmak için Grup İlkesi kullanabilirsiniz.*|[Exploit protection ayarlarını özelleştirme](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Exploit Protection yapılandırmalarını içeri aktarma, dışarı aktarma ve dağıtma](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Yapılandırmayı dağıtmak için Grup İlkesi kullanma](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Çalışanların İnternet'de** kötü amaçlı içerik kullanan uygulamaları kullanmalarını önlemeye yardımcı olmak için Ağ Korumasını Etkinleştir <br/><br/> *Bir test [ortamında, hangi](/microsoft-365/security/defender-endpoint/evaluate-network-protection) uygulamaların gitmeden önce engellenmiş olacağını görmek için önce ağ koruması için denetim modunu kullanmanız önerilir.*|[Grup İlkesini kullanarak ağ korumasını açma](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Fidye yazılımlarına karşı korunmak için** denetimli klasör erişimini yapılandırma <br/><br/> *[Denetimli klasör](/microsoft-365/security/defender-endpoint/controlled-folders) erişimi, yazılım önleme yazılımı koruması olarak da adlandırılır.*|[Grup İlkesi kullanarak denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Web Microsoft Defender SmartScreen** ve internet'e yönelik kötü amaçlı sitelere ve dosyalara karşı korumak üzere yapılandırma.|[Grup Microsoft Defender SmartScreen kullanarak Grup İlkesi ve mobil cihaz yönetimi (MDM) ayarlarını yapılandırma](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Şifrelemeyi ve BitLocker'ı** yapılandırarak kuruluş kuruluşlarının çalışan cihazlarında yer alan bilgileri Windows|[BitLocker Grup İlkesi ayarları](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Kimlik bilgileri hırsızlığı saldırılarına karşı korumak için Microsoft Defender Credential Guard'ı** yapılandırma|[Grup Windows Defender kullanarak Kimlik Bilgileri Koruması'na sahip güvenliği etkinleştirme](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Daha önce bunu yapmadısanız, Microsoft 365 Defender portalınızı uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve genel güvenlik sonrası hakkında ayrıntılı bilgileri görüntülemek üzere yapılandırabilirsiniz. Bkz[. Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Ayrıca, son kullanıcıların portalda hangi özellikleri göreceğini Microsoft 365 Defender.

- [Genel bakış Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl olduğunu genel Tehdit ve Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft 365 Defender portal güvenlik işlemleri panosuna ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Intune ile Uç Nokta için Microsoft Defender'ı yönetme](manage-mde-post-migration-intune.md)
