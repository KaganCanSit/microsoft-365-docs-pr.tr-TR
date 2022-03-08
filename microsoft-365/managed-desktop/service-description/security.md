---
title: Microsoft Yönetilen Masaüstü'nden güvenlik teknolojileri
description: Cihaz güvenliği, kimlik ve erişim yönetimi, ağ güvenliği ve bilgi güvenliği için kullanılan teknolojiler
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 4a6eb73a172ecfb680cbc48367851e40b1a54401
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315421"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'nden güvenlik teknolojileri

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft Yönetilen Masaüstü, yönetilen cihazların ve verilerin güvenliğini sağlamak için çeşitli Microsoft teknolojileri kullanır. Buna ek olarak, Microsoft Yönetilen Masaüstü Güvenlik İşlemleri Merkezi bu [teknolojilerle çeşitli](security-operations.md) işlemler kullanır. Özel olarak:

| İşlem | Açıklama |
| ------ | ------ |
| [Cihaz güvenliği](#device-security)| Microsoft Yönetilen Masaüstü cihazlarda güvenlik ve koruma. |
| [Kimlik ve Erişim Yönetimi](#identity-and-access-management) | Azure Active Directory kimlik hizmetleri aracılığıyla cihazların güvenli kullanımını yönetme. |
| [Ağ güvenliği](#network-security)| VPN bilgileri ve Microsoft Yönetilen Masaüstü önerilen çözüm ve ayarları. |
| [Bilgi güvenliği](#information-security)| Hassas bilgileri daha fazla korumak için isteğe bağlı kullanılabilir hizmetler. |

Microsoft Yönetilen Masaüstü tarafından kullanılan veri depolama, kullanım ve güvenlik uygulamaları hakkında bilgi için, bağlantısında yer alan teknik bilgimize bakın [https://aka.ms/mmd-data](https://aka.ms/mmd-data).

## <a name="device-security"></a>Cihaz güvenliği

Microsoft Yönetilen Masaüstü, tüm yönetilen cihazların güvenli ve korumalı olduğunu güvence altına alınır ve aşağıdaki hizmetleri kullanarak tehditleri mümkün olan en erken şekilde algılar:

| Hizmet | Açıklama |
| ----- | ----- |
| Virüsten koruma | Microsoft Defender Virüsten Koruma yüklü ve yapılandırılmış<br>Microsoft Defender Virüsten Koruma tanımları günceldir. |
| Tam Toplu Şifreleme | Windows BitLocker, Microsoft Yönetilen Masaüstü cihazları için toplu şifreleme çözümüdür.<br><br>Kuruluş hizmete kaydettiklerinde, cihaz uyku modunda veya kapalı olduğunda yerel verilere yetkisiz erişimi önlemek için, cihazlar yerleşik Güven Platformu Modülü (TPM) ile Windows BitLocker kullanılarak şifrelenir.
| İzleme | Uç Nokta için Microsoft Defender, tüm Microsoft Yönetilen Masaüstü cihazları genelinde güvenlik tehditlerini izlemek için kullanılır. Uç Nokta için Defender, kurumsal müşterilerin şirket ağlarında ileri düzey tehditleri algılamalarına, araştırmalarına ve yanıtlamalarına olanak sağlar. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) |
| İşletim sistemi güncelleştirmeleri | Microsoft Yönetilen Masaüstü cihazları her zaman en son güvenlik güncelleştirmeleriyle güvenlik altına alınır. |
| Güvenli Cihaz Yapılandırması | Microsoft Yönetilen Masaüstü, Microsoft Güvenlik Temeli'nin uygulanmasını sağlar. Daha fazla bilgi için [bkz. Windows güvenlik taban çizgisi.](/windows/security/threat-protection/windows-security-baselines)|

## <a name="identity-and-access-management"></a>Kimlik ve erişim yönetimi

Kimlik ve erişim yönetimi şirket varlıklarını ve iş açısından kritik verileri korur. Microsoft Yönetilen Masaüstü, cihazları Azure Active Directory (Azure AD) tarafından yönetilen kimliklerle güvenli kullanımı güvence altına almak için yapılandırr. Azure AD kiracılarında doğru bilgileri korumak müşterinin sorumluluğundadır.

| Hizmet | Açıklama |
| ----- | ----- |
| Biyometrik Kimlik Doğrulaması | Windows Hello, kullanıcıların yüzlerini veya PIN'lerini kullanarak oturum açmalarına olanak sağlar ve parolaları unutmalarını veya çalmalarını zorlaştırır. Müşteriler, bu hizmeti karma bir yapılandırmada kullanmak için şirket içi Active Directory'leri için gerekli önkulları uygulamakla sorumludur. Daha fazla bilgi için bkz. [Windows Hello.](/windows-hardware/design/device-experiences/windows-hello) |
| Standart kullanıcı izni | Sistemi korumak ve daha güvenli hale getirebilirsiniz; kullanıcıya Standart Kullanıcı İzinleri atanır. Bu izin, Windows AutoPilot ilk kullanmama deneyiminin bir parçası olarak atanır.

## <a name="network-security"></a>Ağ güvenliği

Ağ güvenliğinden müşteriler sorumludur.

| Hizmet | Açıklama |
| ----- | ----- |
| VPN | Intranet dışında sınırlı şirket kaynaklarının açık olmasını sağlamak için müşterilerin VPN altyapıları vardır.<br><br>En düşük gereksinim: Microsoft Yönetilen Masaüstü için Windows 10 uyumlu ve desteklenen bir VPN çözümü gerekir. Kuruluşun bir VPN çözümüne ihtiyacı varsa Windows 10'u desteklemesi ve Intune aracılığıyla paketlenebilir ve dağıtılabilir olması gerekir. Daha fazla bilgi için yazılım yayımcınıza ulaşın.<br><br>Öneri:<br><ul><li> Microsoft, INtune aracılığıyla VPN profillerini itmek için kolayca dağıtılacak modern bir VPN çözümü önerebilir. Bu yaklaşım, şirket ağına erişim için her zaman açık, sorunsuz, güvenilir ve güvenli bir yol sağlar. Daha fazla bilgi için [bkz. Intune'da VPN ayarları](/intune/vpn-settings-configure).</li><li>Microsoft Yönetilen Masaüstü kullanırken kalın VPN istemcileri veya daha eski VPN istemcileri kullanıcı ortamını etkiley etkiledikçe Microsoft tarafından önerilmez.</li><li>Microsoft, performans sorunlarından kaçınmak için giden web trafiğinin VPN'den geç kalmadan doğrudan İnternet'e giden trafikten kaçınmasını önerir.</li><li>İdeal olarak Microsoft VPN yerine Azure Active Directory Uygulama Ara Sunucusu kullanımını önerer.</li></ul>

## <a name="information-security"></a>Bilgi güvenliği

Kurumsal yüksek değerli varlıkları korumanıza yardımcı olması için bu isteğe bağlı hizmetleri yapılandırabilirsiniz.

| Hizmet | Açıklama |
| ----- | ----- |
| Veri kurtarma | Cihaz'daki anahtar klasörlerde depolanan bilgiler OneDrive İş'e depolanır. Microsoft Yönetilen Masaüstü, OneDrive İş ile eşitlenmeen verilerden sorumlu değildir.
| Windows Bilgi Koruması | Yüksek bilgi güvenliği düzeyi gerektiren şirketler için Windows Bilgi Koruması ve [Azure Information](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) [Protection'ı öneririz.](https://www.microsoft.com/cloud-platform/azure-information-protection)
