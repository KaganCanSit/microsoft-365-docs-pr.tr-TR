---
title: Şifreleme Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 0a322724-08ca-43db-b69a-afbfa20484cd
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365solution-mip
- m365initiative-compliance
description: En Office 365, içeriğiniz beklemede ve kullanılabilen en güçlü şifreleme, protokol ve teknolojilerle iletilir. E-Office 365'de şifreleme hakkında genel Office 365.
ms.openlocfilehash: a1ee73d7ded7a02cd7851081412d2403e0ca8f1d
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "62988850"
---
# <a name="encryption"></a>Şifreleme

Şifreleme, dosya koruma ve bilgi koruma stratejinizin önemli bir bölümüdir. Bu makalede, şifreleme işlemi için genel bir Office 365. Organizasyon için şifreleme ayarlama ve belgelerinizi parolayla koruma gibi şifreleme görevleriyle ilgili Office elde edin.
  
- TLS gibi sertifikalar ve teknolojiler hakkında bilgi için bkz[. Şifreleme hakkında teknik başvuru Office 365](technical-reference-details-about-encryption.md).

- Kurum için şifrelemeyi yapılandırma veya ayarlama hakkında bilgi için bkz. Şifrelemeyi ayarlamak için bkz[. Office 365 Kurumsal](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Şifreleme nedir ve bu şifreleme nasıl Office 365?

Şifreleme işlemi, verilerinizi (düz metin olarak adlandırılır) şifreleme metnine kodlar. Düz metinden farklı olarak, şifreleme metni şifre çözmediği sürece ve şifre çözmediği sürece, kişiler veya bilgisayarlar tarafından kullanılamaz. Şifre çözme işlemi, yalnızca yetkili kullanıcıların sahip olduğu bir şifreleme anahtarı gerektirir. Şifreleme, yalnızca yetkili alıcıların içeriğinizin şifresini çözmelerini sağlamaya yardımcı olur. İçerikte dosyalar, e-posta iletileri, takvim girdileri gibi içerikler yer alır.
  
Tek başına şifreleme, içerik kesişmesini engellemez. Şifreleme, organizasyonunız için daha büyük bir bilgi koruma stratejisinin parçasıdır. Şifrelemeyi kullanarak, şifrelenmiş verileri yalnızca yetkili tarafların kullanabileceğini garanti edersiniz.
  
Aynı anda birden çok şifreleme katmanı oluşturabilirsiniz. Örneğin, e-posta iletilerini ve ayrıca e-posta akışlarınızı içeren iletişim kanallarını şifreebilirsiniz. Office 365 ile, Aktarım Katmanı Güvenliği/Güvenli Yuva Katmanı (TLS/SSL), İnternet Protokolü Güvenliği (IPSec) ve Gelişmiş Şifreleme Standardı (AES) içeren çeşitli güçlü şifreleme protokolleri ve teknolojiler kullanılarak, verileriniz beklemede ve aktarım sırasında şifrelenir.
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Beklemede olan veriler ve geçişte veriler için şifreleme

  Geri kalan veri örnekleri arasında SharePoint kitaplığına yüklediğiniz dosyalar, Project Online verileri, Skype Kurumsal toplantılarında yüklediğiniz belgeler, posta kutunuzu klasörünüzdeki klasörlerde depolanmış olan e-posta iletileri ve ekler ve OneDrive İş'e yüklediğiniz dosyalar yer alır.
  
 **İletilen verilere örnek** olarak, teslim sürecinde olan posta iletileri veya çevrimiçi bir toplantıda yapılan konuşmalar yer almaktadır. Diğer Office 365, kullanıcının cihazı bir Microsoft sunucusuyla her iletişim kurduğunda veya bir Microsoft sunucusu başka bir sunucuyla iletişim kurduğunda veriler iletir.
  
Daha Office 365, verilerinizin güvenliğini sağlamak için birden çok katman ve şifreleme türü birlikte çalışır. Aşağıdaki tabloda bazı örnekler ve ek bilgilerin bağlantıları yer alır.
  
|**İçerik Türleri**|**Encryption Technologies**|**Daha fazla bilgi edinmek için kaynaklar**|
|:-----|:-----|:-----|
|Cihazda dosyalar. Bu dosyalar bir klasöre kaydedilmiş e-posta iletilerini, Office, tablet veya telefona kaydedilen belgeleri veya Microsoft bulutuna kaydedilmiş verileri içerebilir.  <br/> |Microsoft veri merkezlerinde BitLocker. BitLocker, bilgisayar ve tablet bilgisayarlar ve tabletler gibi Windows makinelerde de kullanılabilir  <br/> Microsoft veri merkezlerinde Dağıtılmış Anahtar Yöneticisi (DKM)  <br/> Müşteri Müşteri Microsoft 365  <br/> |[Windows Merkezi: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Microsoft Güven Merkezi: Şifreleme](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Bulut güvenlik denetimleri serisi: Rest'de Verileri Şifreleme](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [E Exchange Online, e-posta sırlarınızı nasıl güvence altına alır?](exchange-online-secures-email-secrets.md) <br/> [Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md) <br/> |
|Kullanıcılar arasında geçişte olan dosyalar. Bu dosyalar, kullanıcılar Office paylaşılan SharePoint belgeleri veya liste öğelerini içerebilir.  <br/> |TlS, geçişte olan dosyalar için  <br/> |[Data Encryption in OneDrive for Business and SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype Kurumsal Online: Güvenlik ve Arşivleme](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Alıcılar arasında iletili e-posta. Bu e-posta, e-posta tarafından barındırılan e-Exchange Online.  <br/> |Office 365 İleti Şifrelemesi-posta için Azure Hak Yönetimi, S/MIME ve TLS ile iletişim  <br/> |[Office 365 İleti Şifrelemesi (OME)](ome.md) <br/> [E-posta şifrelemesi Office 365](email-encryption.md) <br/> [Nasıl Exchange Online güvenli e-posta bağlantıları için TLS'yi Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Alıcı arasında iletili sohbetler, iletiler ve dosyalar kullanılarak Microsoft Teams. <br/> |Teams iletileri şifrelemek için TLS ve MTLS kullanır. Medya trafiği Güvenli RTP (SRTP) kullanılarak şifrelenir. Teams şifreleme anahtarı değişimleri için FIPS (Federal Information Processing Standard) uyumlu algoritmaları kullanır. <br/> |[Şifreleme için Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Güvenlik ve uyumluluk gereksinimlerini karşılamak için şifreleme üzerinde daha fazla denetime ihtiyacım olursa ne olur?

Microsoft 365, microsoft tarafından yönetilen ağ şifrelemesi, dosya şifrelemesi ve posta kutusu şifrelemesi için Office 365. Buna ek olarak, Microsoft yönet yönetmenizi ve denetlemenizi sağlayan şifreleme çözümleri de sağlar. Bu şifreleme çözümleri Azure'da yerleşik olarakdır.
  
Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
  
- [Azure Hak Yönetimi nedir?](/information-protection/understand-explore/what-is-azure-rms)

- [Yönetim merkezinde Hak Yönetimi'ni etkinleştirme](../enterprise/activate-rms-in-microsoft-365.md)

- [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)

- [Müşteri Hizmetleri'ne Müşteri Anahtarı ile Office 365](customer-key-overview.md)

- [Double Key Encryption for Microsoft 365](double-key-encryption.md)

## <a name="how-do-i"></a>Nasıl...

|**Bu görevi yapmak için**|**Bu kaynaklara bakın**|
|:-----|:-----|
|Kuruluşum için şifrelemeyi ayarlama|[Verilerde şifrelemeyi Office 365 Kurumsal](set-up-encryption.md)|
|Sertifikalar, teknolojiler ve TLS şifreleme paketleri hakkında ayrıntıları görüntüleme|[Şifreleme hakkında teknik ayrıntılar](technical-reference-details-about-encryption.md)|
|Mobil cihazda şifrelenmiş iletilerle çalışma|[Şifrelenmiş iletileri Android aygıtınızda görüntüleme Şifreli](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) iletileri Android veya [iPhone iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Parola koruması kullanarak belgeyi şifreler. (Parola koruması tarayıcıda desteklenmiyor. Parola koruması için Word, Excel ve PowerPoint sürümlerini kullanın.) |[Belgenize, çalışma kitabınıza veya sununuzu koruma ekleyin veya kaldırın](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Koruma ekle **bölümünü seçin** ve ardından Parola ile **Şifrele'ye bakın**.|
|Belgeden şifrelemeyi kaldırma|[Belgenize, çalışma kitabınıza veya sununuzu koruma ekleyin veya kaldırın](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Korumayı **kaldır bölümünü** seçin ve sonra Parola **şifrelemeyi kaldırma bölümüne bakın**.  |

## <a name="related-topics"></a>İlgili konular

[Güvenlik Microsoft 365 bilgi koruma özelliklerini planlama](plan-for-security-and-compliance.md)

[kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream Video düzeyi şifreleme ve kayıttan yürütme akışı](/stream/network-overview#video-level-encryption-and-playback-flow)