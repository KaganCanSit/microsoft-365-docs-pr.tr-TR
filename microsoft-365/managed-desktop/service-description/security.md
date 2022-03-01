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
ms.openlocfilehash: 7b5f99a6927fd87b1d75bde0dcc5e4fde1ff3a62
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015568"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'nden güvenlik teknolojileri

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft Yönetilen Masaüstü, yönetilen cihazların ve verilerin güvenliğini sağlamak için çeşitli Microsoft teknolojileri kullanır. Buna ek olarak, Microsoft Yönetilen Masaüstü Güvenlik İşlemleri Merkezi bu [teknolojilerle çeşitli](security-operations.md) işlemler kullanır. Özel olarak:

| İşlem | Açıklama |
| ------ | ------ |
| [Cihaz güvenliği](#device-security)| Microsoft Yönetilen Masaüstü cihazlarda güvenlik ve koruma. |
| [Kimlik ve Erişim Yönetimi](#identity-and-access-management) | Kimlik hizmetlerini kullanarak cihazların güvenli Azure Active Directory yönetme. |
| [Ağ güvenliği](#network-security)| VPN bilgileri ve Microsoft Yönetilen Masaüstü önerilen çözüm ve ayarları. |
| [Bilgi güvenliği](#information-security)| Hassas bilgileri daha fazla korumak için isteğe bağlı kullanılabilir hizmetler. |

Microsoft Yönetilen Masaüstü tarafından kullanılan veri depolama, kullanım ve güvenlik uygulamaları hakkında bilgi için, bağlantısında yer alan teknik bilgimize bakın [https://aka.ms/mmd-data](https://aka.ms/mmd-data).

## <a name="device-security"></a>Cihaz güvenliği

Microsoft Yönetilen Masaüstü, tüm yönetilen cihazların güvenli ve korumalı olduğunu güvence altına alınır ve aşağıdaki hizmetleri kullanarak tehditleri mümkün olan en erken şekilde algılar:

| Hizmet | Açıklama |
| ----- | ----- |
| Virüsten koruma | Microsoft Defender Virüsten Koruma yüklü ve yapılandırılmış<br>Microsoft Defender Virüsten Koruma tanımları günceldir. |
| Tam Toplu Şifreleme | Windows BitLocker, Microsoft Yönetilen Masaüstü cihazları için toplu şifreleme çözümüdür.<br><br>Kuruluş hizmete kaydolduruktan sonra, cihaz uyku modunda veya kapalı olduğunda yerel verilere yetkisiz erişimi önlemek için cihazlar yerleşik Güven Platformu Modülü (TPM) ile Windows BitLocker kullanılarak şifrelenir.
| İzleme | Uç Nokta için Microsoft Defender, tüm Microsoft Yönetilen Masaüstü cihazları genelinde güvenlik tehditlerini izlemek için kullanılır. Uç Nokta için Defender, kurumsal müşterilerin şirket ağlarında ileri düzey tehditleri algılamalarına, araştırmalarına ve yanıtlamalarına olanak sağlar. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) |
| İşletim sistemi güncelleştirmeleri | Microsoft Yönetilen Masaüstü cihazları her zaman en son güvenlik güncelleştirmeleriyle güvenlik altına alınır. |
| Güvenli Cihaz Yapılandırması | Microsoft Yönetilen Masaüstü, Microsoft Güvenlik Temeli'nin uygulanmasını sağlar. Daha fazla bilgi için bkz[. Windows temelleri atama.](/windows/security/threat-protection/windows-security-baselines)|

## <a name="identity-and-access-management"></a>Kimlik ve erişim yönetimi

Kimlik ve erişim yönetimi şirket varlıklarını ve iş açısından kritik verileri korur. Microsoft Yönetilen Masaüstü, cihazları kimlik bilgileri (Azure AD) Azure Active Directory güvenli kullanım sağlamak için yapılandırıyor. Azure AD kiracılarında doğru bilgileri korumak müşterinin sorumluluğundadır.

| Hizmet | Açıklama |
| ----- | ----- |
| Biyometrik Kimlik Doğrulaması | Windows Hello, kullanıcıların yüzlerini veya PIN'lerini kullanarak oturum açmalarına olanak sağlar ve parolaları unutmalarını veya çalmalarını zorlaştırır. Müşteriler, bu hizmeti karma bir yapılandırmada kullanmak için şirket içi Active Directory'leri için gerekli önkulları uygulamakla sorumludur. Daha fazla bilgi için bkz. [Windows Hello.](/windows-hardware/design/device-experiences/windows-hello) |
| Standart kullanıcı izni | Sistemi korumak ve daha güvenli hale getirebilirsiniz; kullanıcıya Standart Kullanıcı İzinleri atanır. Bu izin, AutoPilot'Windows ilk kullanma deneyiminin bir parçası olarak atanır.

## <a name="network-security"></a>Ağ güvenliği

Ağ güvenliğinden müşteriler sorumludur.

| Hizmet | Açıklama |
| ----- | ----- |
| VPN | Intranet dışında sınırlı şirket kaynaklarının açık olmasını sağlamak için müşterilerin VPN altyapıları vardır.<br><br>En düşük gereksinim: Microsoft Yönetilen Masaüstü için Windows 10 ve desteklenen bir VPN çözümü gerekir. Kuruluşun bir VPN çözümüne ihtiyacı varsa, vpn çözümünü desteklemesi Windows 10 Intune aracılığıyla paketlenebilir ve dağıtılabilir. Daha fazla bilgi için yazılım yayımcınıza ulaşın.<br><br>Öneri:<br><ul><li> Microsoft, INtune aracılığıyla VPN profillerini itmek için kolayca dağıtılacak modern bir VPN çözümü önerebilir. Bu yaklaşım, şirket ağına erişim için her zaman açık, sorunsuz, güvenilir ve güvenli bir yol sağlar. Daha fazla bilgi için [bkz. Intune'da VPN ayarları](/intune/vpn-settings-configure).</li><li>Microsoft Yönetilen Masaüstü kullanırken kalın VPN istemcileri veya daha eski VPN istemcileri kullanıcı ortamını etkiley etkiledikçe Microsoft tarafından önerilmez.</li><li>Microsoft, performans sorunlarından kaçınmak için giden web trafiğinin VPN'den geç kalmadan doğrudan İnternet'e giden trafikten kaçınmasını önerir.</li><li>İdeal olarak Microsoft VPN yerine Azure Active Directory Proxy'nin kullanımını önermaktadır.</li></ul>


## <a name="information-security"></a>Bilgi güvenliği

Kurumsal yüksek değerli varlıkları korumanıza yardımcı olması için bu isteğe bağlı hizmetleri yapılandırabilirsiniz.

| Hizmet | Açıklama |
| ----- | ----- |
| Veri kurtarma | Cihaz'daki anahtar klasörlerde depolanan bilgiler yeni klasöre OneDrive İş. Microsoft Yönetilen Masaüstü, masaüstü ile eşitlenm bkz. OneDrive İş.
| Windows Koruma | Yüksek bilgi güvenliği düzeyi gerektiren şirketlere Bilgi Koruması'Windows Azure [Information Protection'i](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) [öneririz.](https://www.microsoft.com/cloud-platform/azure-information-protection)
