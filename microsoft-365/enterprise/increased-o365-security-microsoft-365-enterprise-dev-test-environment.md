---
title: Kurumsal test ortamınız için Microsoft 365 için daha fazla Microsoft 365 güvenliği
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Kurumsal test ortamı için Microsoft 365 ek Microsoft 365 güvenlik ayarlarını etkinleştirmek için bu Test Laboratuvarı Kılavuzu'nu kullanın.
ms.openlocfilehash: 4c69fadd3fb3e6744fad850e76282ea2339f48ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100731"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için Microsoft 365 için daha fazla Microsoft 365 güvenliği

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Bu makaledeki yönergelerle, kurumsal test ortamınıza yönelik Microsoft 365 güvenliği artırmak için ek Microsoft 365 ayarları yapılandıracaksınız.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınının Microsoft 365 tüm makalelerin görsel haritası için [buraya](../downloads/Microsoft365EnterpriseTLGStack.pdf) tıklayın.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

Yalnızca en düşük gereksinimlerle daha yüksek Microsoft 365 güvenliği basit bir şekilde yapılandırmak istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
Sanal bir kuruluşta artırılmış Microsoft 365 güvenlik yapılandırmak istiyorsanız Doğrudan [kimlik doğrulamasındaki](pass-through-auth-m365-ent-test-environment.md) yönergeleri izleyin.
  
> [!NOTE]
> Artan güvenlik Microsoft 365 test etmek, İnternet'e bağlı bir sanal intranet ve bir Active Directory Domain Services (AD DS) ormanı için dizin eşitlemesi içeren sanal kurumsal test ortamını gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>2. Aşama: Artırılmış Microsoft 365 güvenliği yapılandırma

Bu aşamada, kurumsal test ortamı için Microsoft 365 için daha fazla Microsoft 365 güvenliği etkinleştirirsiniz. Ek ayrıntılar ve ayarlar için bkz [. Artan güvenlik için kiracınızı yapılandırma](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Modern kimlik doğrulamasını desteklemeyen uygulamaları engellemek için SharePoint Online'ı yapılandırma

Modern kimlik doğrulamasını desteklemeyen uygulamalar, Microsoft 365 aboneliğinizin ve dijital varlıklarınızın güvenliğini sağlamanın önemli bir öğesi olan [kimlik ve cihaz erişim yapılandırmalarına](../security/office-365-security/microsoft-365-policies-configurations.md) sahip olamaz. 

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve genel yönetici hesabınızla Microsoft 365 test laboratuvarı aboneliğinizde oturum açın.
    
  - Basit Microsoft 365 test ortamını kullanıyorsanız yerel bilgisayarınızdan oturum açın.
    
  - Sanal kurumsal Microsoft 365 test ortamını kullanıyorsanız, [İstemci1](https://portal.azure.com) sanal makinesine bağlanmak için Azure portal kullanın ve ardından CLIENT1'den oturum açın.
 
2. Yeni **Microsoft 365 yönetim merkezi** sekmesinde, sol gezinti bölmesindeki **Yönetim merkezleri'nin** altında **SharePoint'e** tıklayın.
3. Yeni **SharePoint yönetim merkezi** sekmesinde **İlkelerAccess denetimi'ni** >  seçin.<a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank"></a>
4. **Modern kimlik doğrulamayı desteklemeyen uygulamalar'ı** seçin, **Erişimi engelle'yi** ve ardından **Kaydet'i** seçin.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>SharePoint, OneDrive İş ve Microsoft Teams için Office 365 için Defender etkinleştirme

SharePoint, OneDrive ve Microsoft Teams için Office 365 için Defender, kuruluşunuzu yanlışlıkla kötü amaçlı dosyaları paylaşmaya karşı korur.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Güvenlik & Uyumluluk Merkezi'ne</a> gidin ve genel yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesinde, **Tehdit yönetimi'nin** altında **İlke'ye** tıklayın ve ardından **Ekler'Kasa** tıklayın. 

3. **SharePoint, OneDrive ve Microsoft Teams dosyaları koruma** altında. **SharePoint, OneDrive ve Microsoft Teams için ATP'yi aç'ı** seçin.

4. **Kaydet**'e tıklayın.


### <a name="enable-anti-malware"></a>Kötü amaçlı yazılımdan korumayı etkinleştirme

Kötü amaçlı yazılım virüslerden ve casus yazılımlardan oluşur. Virüsler diğer programlara ve verilere bulaşır ve bilgisayarınıza yayılarak bulaşacak programları arar. Casus yazılım, oturum açma bilgileri ve kişisel veriler gibi kişisel bilgilerinizi toplayan ve kötü amaçlı yazılım yazarına geri gönderen kötü amaçlı yazılımları ifade eder. 

Microsoft 365, gelen ve giden iletileri kötü amaçlı yazılımlardan korumaya ve istenmeyen postalardan korunmanıza yardımcı olan yerleşik kötü amaçlı yazılım ve istenmeyen posta filtreleme özelliklerine sahiptir. Daha fazla bilgi için bkz [. İstenmeyen posta önleme & kötü amaçlı yazılımdan koruma](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Yaygın ek dosya türlerine sahip dosyalarda kötü amaçlı yazılımdan koruma işleminin gerçekleştirildiğinden emin olmak için:

1. **İlke** sayfasına dönmek için tarayıcınızda geri düğmesine tıklayın.
2. **Kötü amaçlı yazılımdan koruma'ya** tıklayın.
3. **Varsayılan** adlı ilkeye çift tıklayın.
4. **Kötü amaçlı yazılımdan koruma ilkesi** penceresinde **Ayarlar'e** tıklayın.
4. **Ortak Ek Türleri filtresi** altında **Açık'ı** seçin ve **kaydet'e** tıklayın.


## <a name="phase-3-examine-the-security-dashboard"></a>3. Aşama: Güvenlik panosunu inceleme

Microsoft 365'de tehdit yönetimi, kuruluşunuzun verilerine mobil cihaz erişimini denetlemenize ve yönetmenize, kuruluşunuzun veri kaybına karşı korunmasına yardımcı olabilir ve gelen ve giden iletileri kötü amaçlı yazılımlardan ve istenmeyen postalardan korumaya yardımcı olabilir. Ayrıca etki alanınızın itibarını korumak ve gönderenlerin etki alanınızdan kötü amaçlı olarak hesap sahtekarlığı yapıp yapmadığını belirlemek için de tehdit yönetimini kullanırsınız. 

Güvenlik panosunu görmek için:

1. Gerekirse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Güvenlik & Uyumluluk Merkezi'ne</a> gidin ve genel yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesindeki **Tehdit yönetimi'nin** altında **Pano'ya** tıklayın.

Sağlanan bilgileri öğrenmek için panodaki tüm kartları yakından inceleyin.

Daha fazla bilgi için bkz [. Güvenlik Panosu](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>4. Aşama: Microsoft Güvenli Puanını İnceleme

Microsoft Güvenli Puanı, güvenlik duruşunuzu bir sayı olarak gösterir ve bu da aboneliğinizde kullanılabilen özelliklere göre geçerli düzeyinizi gösterir. Ayrıca puanınızı geliştirmek için gerçekleştirebileceğiniz iyileştirme eylemlerinin bir listesini de sunar.

1. Tarayıcınızda yeni bir sekme oluşturun, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve **ardından Güvenli puan'a** tıklayın.
2. **Genel Bakış** sekmesinde, geçerli Güvenli Puanınızı ve genel ortalamayla ve benzer sayıda lisansa sahip aboneliklerle karşılaştırmasını not edin.
3. **İyileştirme eylemleri** sekmesinde, puanınızı artırmak için gerçekleştirebileceğiniz eylemlerin listesini okuyun.

Daha fazla bilgi için bkz. [Microsoft Güvenli Puanı](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Sonraki adımlar

Test ortamınızdaki ek [bilgi koruma](m365-enterprise-test-lab-guides.md#information-protection) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)
