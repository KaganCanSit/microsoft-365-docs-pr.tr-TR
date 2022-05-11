---
title: Microsoft 365'de şifreleme
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
description: Office 365 ile içeriğiniz bekleyen ve aktarım halindeki en güçlü şifreleme, protokoller ve teknolojiler ile şifrelenir. Office 365'da şifrelemeye genel bir bakış edinin.
ms.openlocfilehash: 5f866931eba3078074b47c9cc8c5ed310489b9bb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319275"
---
# <a name="encryption"></a>Şifreleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Şifreleme, dosya koruma ve bilgi koruma stratejinizin önemli bir parçasıdır. Bu makalede, Office 365 için şifrelemeye genel bir bakış sağlanır. Kuruluşunuz için şifrelemeyi ayarlama ve Office belgeleri parolayla koruma gibi şifreleme görevleriyle ilgili yardım alın.
  
- TLS gibi sertifikalar ve teknolojiler hakkında bilgi için bkz. [Office 365 şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md).

- Kuruluşunuz için şifrelemeyi yapılandırma veya ayarlama hakkında bilgi için bkz. [Office 365 Kurumsal'de şifrelemeyi ayarlama](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Şifreleme nedir ve Office 365 nasıl çalışır?

Şifreleme işlemi verilerinizi (düz metin olarak adlandırılır) şifreleme metnine kodlar. Düz metinden farklı olarak, şifre metni şifresi çözülene kadar ve şifresi çözülene kadar kişiler veya bilgisayarlar tarafından kullanılamaz. Şifre çözme, yalnızca yetkili kullanıcıların sahip olduğu bir şifreleme anahtarı gerektirir. Şifreleme, içeriğinizin şifresini yalnızca yetkili alıcıların çözebilmesine yardımcı olur. İçerik dosyaları, e-posta iletilerini, takvim girdilerini vb. içerir.
  
Şifreleme tek başına içerik kesmeyi engellemez. Şifreleme, kuruluşunuz için daha büyük bir bilgi koruma stratejisinin bir parçasıdır. Şifrelemeyi kullanarak, şifrelenmiş verileri yalnızca yetkili tarafların kullanabilmesini sağlamanıza yardımcı olursunuz.
  
Aynı anda birden çok şifreleme katmanına sahip olabilirsiniz. Örneğin, e-posta iletilerini ve e-postanızın aktığı iletişim kanallarını şifreleyebilirsiniz. Office 365 ile verileriniz, Aktarım Katmanı Güvenliği/Güvenli Yuva Katmanı (TLS/SSL), İnternet Protokolü Güvenliği (IPSec) ve Gelişmiş Şifreleme Standardı (AES) gibi çeşitli güçlü şifreleme protokolleri ve teknolojiler kullanılarak bekleyen ve aktarım halinde şifrelenir.
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Bekleyen veriler ve aktarımdaki veriler için şifreleme

 **Bekleyen verilere örnek** olarak SharePoint kitaplığına yüklediğiniz dosyalar, Project Online veriler, Skype Kurumsal toplantısına yüklediğiniz belgeler, posta kutunuzdaki klasörlerde depoladığınız e-posta iletileri ve ekler ve OneDrive İş'a yüklediğiniz dosyalar verilebilir.
  
 **Aktarımdaki verilere örnek olarak** teslim edilme sürecinde olan posta iletileri veya çevrimiçi bir toplantıda gerçekleşen konuşmalar verilebilir. Office 365'da, kullanıcının cihazı bir Microsoft sunucusuyla iletişim kurarken veya bir Microsoft sunucusu başka bir sunucuyla iletişim kurarken veriler aktarımda olur.
  
Office 365 ile verilerinizin güvenliğini sağlamak için birden çok katman ve şifreleme türü birlikte çalışır. Aşağıdaki tabloda bazı örnekler ve ek bilgilerin bağlantıları yer almaktadır.
  
|**İçerik Türleri**|**Şifreleme Teknolojileri**|**Daha fazla bilgi edinmek için kaynaklar**|
|:-----|:-----|:-----|
|Bir cihazdaki dosyalar. Bu dosyalar bir klasöre kaydedilmiş e-posta iletilerini Office bilgisayara, tablete veya telefona kaydedilmiş belgeleri ya da Microsoft buluta kaydedilmiş verileri içerebilir.  <br/> |Microsoft veri merkezlerinde BitLocker. BitLocker, Windows bilgisayarlar ve tabletler gibi istemci makinelerinde de kullanılabilir  <br/> Microsoft veri merkezlerinde Dağıtılmış Anahtar Yöneticisi (DKM)  <br/> Microsoft 365 için Müşteri Anahtarı  <br/> |[Windows BT Merkezi: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Microsoft Güven Merkezi: Şifreleme](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Bulut güvenlik denetimleri serisi: Bekleyen Verileri Şifreleme](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Exchange Online, e-posta sırlarınızı nasıl güvence altına alır?](exchange-online-secures-email-secrets.md) <br/> [Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md) <br/> |
|Kullanıcılar arasında aktarımda olan dosyalar. Bu dosyalar, kullanıcılar arasında paylaşılan Office belgeleri veya SharePoint liste öğelerini içerebilir.  <br/> |Aktarımdaki dosyalar için TLS  <br/> |[Data Encryption in OneDrive for Business and SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype Kurumsal Online: Güvenlik ve Arşivleme](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Alıcılar arasında aktarım halindeki e-posta. Bu e-posta, Exchange Online tarafından barındırılan e-postaları içerir.  <br/> |Aktarımdaki e-posta için Azure Rights Management, S/MIME ve TLS ile Microsoft Purview İleti Şifrelemesi  <br/> |[essage Şifrelemesi](ome.md) <br/> [Office 365'de e-posta şifrelemesi](email-encryption.md) <br/> [Exchange Online, Office 365’de e-posta bağlantılarını güvence altına almak için TLS'yi nasıl kullanır?](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Microsoft Teams kullanarak alıcılar arasında ileti halinde olan sohbetler, iletiler ve dosyalar. <br/> |Teams anlık iletileri şifrelemek için TLS ve MTLS kullanır. Medya trafiği Güvenli RTP (SRTP) kullanılarak şifrelenir. Teams şifreleme anahtarı değişimleri için FIPS (Federal Bilgi İşleme Standardı) uyumlu algoritmalar kullanır. <br/> |[Teams için şifreleme](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Güvenlik ve uyumluluk gereksinimlerini karşılamak için şifreleme üzerinde daha fazla denetime ihtiyacım olursa ne olur?

Microsoft 365, Office 365'da birim şifrelemesi, dosya şifrelemesi ve posta kutusu şifrelemesi için Microsoft tarafından yönetilen çözümler sağlar. Ayrıca, Microsoft yönetebileceğiniz ve denetleyebileceğiniz şifreleme çözümleri sağlar. Bu şifreleme çözümleri Azure'da oluşturulur.
  
Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
  
- [Azure Rights Management nedir?](/information-protection/understand-explore/what-is-azure-rms)

- [Yönetim merkezinde Rights Management etkinleştirme](../enterprise/activate-rms-in-microsoft-365.md)

- [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)

- [Microsoft Purview Müşteri Anahtarı ile hizmet şifreleme](customer-key-overview.md)

- [Çift Anahtarlı Şifreleme](double-key-encryption.md)

## <a name="how-do-i"></a>Nasıl yaparım?...

|**Bu görevi yapmak için**|**Bu kaynaklara bakın**|
|:-----|:-----|
|Kuruluşum için şifrelemeyi ayarlama|[Office 365 Kurumsal'de şifrelemeyi ayarlama](set-up-encryption.md)|
|Sertifikalar, teknolojiler ve TLS şifreleme paketleri hakkındaki ayrıntıları görüntüleme|[Şifreleme hakkında teknik ayrıntılar](technical-reference-details-about-encryption.md)|
|Mobil cihazda şifrelenmiş iletilerle çalışma|[Android cihazınızda şifrelenmiş iletileri görüntüleme](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [iPhone veya iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Parola koruması kullanarak belgeyi şifreleme. (Parola koruması tarayıcıda desteklenmez. Parola koruması için Word, Excel ve PowerPoint masaüstü sürümlerini kullanın.) |[Belgenize, çalışma kitabınıza veya sununuza koruma ekleyin veya kaldırın](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). **Koruma ekle** bölümünü seçin ve ardından bkz. **Parola ile şifreleme**.|
|Belgeden şifrelemeyi kaldırma|[Belgenize, çalışma kitabınıza veya sununuza koruma ekleyin veya kaldırın](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). **Korumayı kaldır** bölümünü seçin ve ardından bkz **. Parola şifrelemesini kaldırma**.  |

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 güvenlik ve bilgi koruma özelliklerini planlama](plan-for-security-and-compliance.md)

[İş planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream Video düzeyinde şifreleme ve kayıttan yürütme akışı](/stream/network-overview#video-level-encryption-and-playback-flow)
