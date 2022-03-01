---
title: Kurumsal Microsoft 365 ortamınız için Microsoft 365 güvenliğinizi artırmış
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Test Laboratuvarı Kılavuzu'Microsoft 365 test Microsoft 365 için güvenlik Microsoft 365 ayarlarını etkinleştirin.
ms.openlocfilehash: 5d431bba21c02daf2ec5af384e2d4fde53ab6edb
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006764"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal Microsoft 365 ortamınız için Microsoft 365 güvenliğinizi artırmış

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Bu makaledeki yönergelerle, kurumsal test Microsoft 365 ortamınıza güvenliği artırmak üzere ek Microsoft 365 ayarları yapılandırabilirsiniz.

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal [Test](../downloads/Microsoft365EnterpriseTLGStack.pdf) Laboratuvarı Kılavuzu yığınına göre görsel bir harita Microsoft 365 için buraya tıklayın.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Yalnızca en düşük gereksinimlerle yüksek Microsoft 365 kolay bir şekilde yapılandırmaksanız, Hafif taban [yapılandırma'daki yönergeleri izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta artırılmış Microsoft 365 yapılandırmak için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Artırılmış Microsoft 365 testi, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamı gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test etmek ve normal bir kuruluşu temsil eden bir ortamda bu üyelikle denemeler yapmak için bir seçenek olarak sağlanmıştır. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Aşama 2: Artırılmış güvenlik Microsoft 365 yapılandırma

Bu aşamada, kurumsal test Microsoft 365 için güvenlik Microsoft 365 artırılmış güvenlik etkinleştirildi. Ek ayrıntılar ve ayarlar için bkz. [Daha yüksek güvenlik için kiracınızı yapılandırma](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Modern SharePoint desteklemez uygulamaları engellemek için SharePoint Online'da yapılandırma

Modern kimlik doğrulamayı desteklemez, bu uygulamalara kimlik ve cihaz erişimi yapılandırmaları uygulanamaz. Bu, Microsoft 365 aboneliğinizin ve dijital varlıklarının güvenliğini sağlamanın önemli bir öğesidir.[](../security/office-365-security/microsoft-365-policies-configurations.md) 

1. Genel yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> oturum açın ve Microsoft 365 test laboratuvarı aboneliğiniz ile oturum açın.
    
  - Basit sınama ortamını Microsoft 365, yerel bilgisayarınızdan oturum açma.
    
  - Sanal kurumsal sınama ortamını Microsoft 365, CLIENT1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın ve ardından İSTEMCI1'den oturum açın.
 
2. Yeni **Gezinti Microsoft 365 yönetim merkezi,** sol gezinti **bölmesindeki** Yönetim merkezleri'nin altında Seçenekler'e **SharePoint**.
3. Yeni yönetim merkezi **SharePoint Access denetimi** için **İlkeler> tıklayın**.
4. Modern **kimlik doğrulamasını desteklemez uygulamalar'a tıklayın, Erişimi** **engelle'yi seçin ve** ardından Kaydet'e **tıklayın**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>SharePoint, OneDrive İş ve Office 365 için Defender'ı Microsoft Teams

SharePoint, OneDrive için Office 365 Defender, Microsoft Teams yanlışlıkla kötü amaçlı dosyaları paylaşmaya karşı korur.

1. Güvenlik ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Uyumluluk & gidin</a> ve genel yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesinde, Tehdit yönetimi'nin **altında İlke'ye** **tıklayın** ve sonra Ekleri **Ekle'Kasa tıklayın**. 

3. Dosyaları **Dosya, Klasör SharePoint, OneDrive altında Microsoft Teams**. **AtP'yi sırasıyla, SharePoint, OneDrive aç'ı Microsoft Teams**.

4. **Kaydet**'e tıklayın.


### <a name="enable-anti-malware"></a>Kötü amaçlı yazılımdan korumayı etkinleştirme

Kötü amaçlı yazılım virüslerden ve casus yazılımlardan oluşur. Virüs diğer programlara ve verilere bulaşarak bulaşarak, bilgisayarınızın her yerinde bulaşarak bulaştırılacak programlar arıyor. Casus yazılım, oturum açma bilgileri ve kişisel veriler gibi kişisel bilgilerinizi toplayıp kötü amaçlı yazılım yazarına geri gönderen kötü amaçlı yazılım anlamına gelir. 

Microsoft 365 gelen ve giden iletileri kötü amaçlı yazılımlardan korumaya ve sizi istenmeyen postalardan korumaya yardımcı olan yerleşik kötü amaçlı yazılım ve istenmeyen posta filtreleme özellikleri vardır. Daha fazla bilgi için bkz[. İstenmeyen postadan koruma & kötü amaçlı yazılımdan koruma.](../security/office-365-security/anti-spam-and-anti-malware-protection.md)

Kötü amaçlı yazılımdan koruma dosya türleri yaygın olarak kullanılan dosya türlerine sahip dosyalar üzerinde gerçekleştirile olduğundan emin olmak için:

1. İlke sayfasına dönmek için tarayıcınızda **geri düğmesine tıklayın** .
2. Kötü amaçlı **yazılımdan koruma'ya tıklayın**.
3. Varsayılan adlı ilkeye çift **tıklayın**.
4. Kötü amaçlı **yazılımdan koruma ilkesi penceresinde,** Kötü amaçlı **yazılımdan koruma** ilkesi Ayarlar.
4. Ortak **Ek Türleri filtresi altında,** **Aç'ı seçin** ve kaydet'e **tıklayın**.


## <a name="phase-3-examine-the-security-dashboard"></a>Aşama 3: Güvenlik panosuyu inceleme

Microsoft 365'da tehdit yönetimi, kuruluş verilerinize mobil cihaz erişimini denetlemenize ve yönetmenize, kurum verilerinizin veri kaybına karşı korunmasına ve gelen ve giden iletilerin kötü amaçlı yazılımlardan ve istenmeyen postalardan korunmasına yardımcı olabilir. Ayrıca, tehdit yönetimini etki alanınıza karşı itibarını korumak ve gönderenlerin etki alanınıza yönelik kötü amaçlı hesaplara yönelik kötü amaçlı hesap olup olmadığını belirlemek için kullanırsınız. 

Güvenlik panosuyu görmek için:

1. Gerekirse Güvenlik ve Uyumluluk Merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">'& gidin</a> ve genel yönetici hesabınızla oturum açın.

2. Sol gezinti bölmesinde, Tehdit **yönetimi'nin altında Pano'ya** **tıklayın**.

Sağlanan bilgileri tanımanız için panonun tüm kartlarına yakından bakın.

Daha fazla bilgi için bkz. [Güvenlik Panosu](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Aşama 4: Microsoft Güvenli Puanı'nın incele

Microsoft Güvenli Puanı, geçerli düzeyinizin aboneliğinize bağlı olarak güvenlik nedenini bir sayı olarak gösterir. Ayrıca, puanınızı geliştirmek için gerçekleştirebilirsiniz geliştirme eylemlerinin bir listesini de verir.

1. Tarayıcınızda yeni bir sekme oluşturun, Puanlar <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalına Microsoft 365 Defender ardından</a> Güvenli **puan'a tıklayın**.
2. Genel Bakış **sekmesinde**  , geçerli Güvenli Puanınızı ve genel ortalamayla ve benzer sayıda lisansla aboneliklerle karşılaştırmasını not alın.
3. Geliştirme **eylemleri sekmesinde** , puanınızı artırmak için gerçekleştirebilirsiniz eylemler listesini okuyun.

Daha fazla bilgi için [bkz. Microsoft Güvenli Puanı](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Sonraki adımlar

Test [ortamınıza ek](m365-enterprise-test-lab-guides.md#information-protection) bilgi koruma özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
