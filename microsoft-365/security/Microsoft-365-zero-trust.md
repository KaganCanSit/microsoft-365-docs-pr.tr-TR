---
title: Microsoft 365 Sıfır Güven dağıtım planı
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Tehditlere karşı savunmak Microsoft 365 Sıfır Güven hassas verileri korumak için ortamınıza güvenlik dağıtımı yapmayı öğrenin.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: f8ffdcb817763589dfb43f7389bc44b7a28459f2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473067"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 Sıfır Güven dağıtım planı

Bu makalede, güvenlik ve güvenlik **Sıfır Güven için dağıtım** planı Microsoft 365. Sıfır Güven, ihlal olduğunu varan ve her isteğin, denetimsiz bir ağdan geliyor gibi doğrulandığı yeni bir güvenlik modelidir. İsteğin nereden geldiğine veya hangi kaynağa erişten olursa olsun, Sıfır Güven modeli "asla güvenme, her zaman doğrula" dersi veriyor.


## <a name="zero-trust-security-architecture"></a>Sıfır Güven mimarisini benimser

Kısa Sıfır Güven yaklaşımı dijital emlakın tamamına doğru genişler ve tümleşik bir güvenlik stratejisi ve  uç-uç stratejisi olarak hizmet ediyor. 

Bu çizimde, çalışmalara katkıda bulunan birincil öğeler Sıfır Güven.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="En Sıfır Güven mimarisi" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Çizimde:
- Güvenlik ilkesi zorlaması, güvenlik ilkesi mimarisinin Sıfır Güven merkezindedir. Bu, kullanıcı hesabı riskini, cihaz durumunu ve sizin ayardınız diğer ölçütleri ve ilkeleri hesaba katan koşullu erişimle Çok Faktörlü kimlik doğrulamasını içerir.
- Kimlikler, cihazlar, veriler, uygulamalar, ağ ve diğer altyapı bileşenlerinin hepsi uygun güvenlikle yapılandırılır. Bu bileşenlerin her biri için yapılandırılan ilkeler, genel güvenlik stratejiniz Sıfır Güven eşgüdüm sağlar. Örneğin, cihaz ilkeleri sağlıklı cihazlar için ölçütleri belirler ve belirli uygulamalara ve verilere erişim için sağlıklı cihazlara yönelik koşullu erişim ilkeleri gerekir.
- Tehdit koruması ve zeka ortamı izler, geçerli riskleri ortaya çıkartır ve saldırılarını düzeltmek için otomatik eylem alır.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

Daha fazla bilgi Sıfır Güven için Microsoft'un Kılavuz [_**Merkezi'Sıfır Güven bakın**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Sıfır Güven için Microsoft 365'i dağıtma

Microsoft 365 birçok güvenlik ve bilgi koruma özelliğiyle, ortamınıza güvenlik ve bilgi koruması Sıfır Güven bilerek yerleşik olarak tasarlanmıştır. Pek çok özellik, kurum tarafından kullanan diğer SaaS uygulamalarına ve bu uygulamalar içindeki verilere erişimi korumak için genişletılabilir.

Bu çizim, yeni ve kolay Sıfır Güven çalışma gösterir. Bu çalışma, önkoşulların tamamlandıktan sonra alttan başlayarak en alttan başlayarak en üstten başlayarak birlikte yapılandırılana kadar çalışma birimlerine bozulur.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Microsoft 365 Sıfır Güven dağıtım yığını" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Bu şekilde:
- Sıfır Güven temel kimlik ve cihaz koruması temel bilgileriyle başlar. 
- Tehdit koruması özellikleri, güvenlik tehditlerini gerçek zamanlı olarak izleme ve düzeltme sağlamak için bu temelin üzerine kurulur. 
- Bilgi koruma ve yönetim, en değerli bilgilerinizi korumak ve kişisel bilgilerinizi koruma da dahil olmak üzere uyumluluk standartlarına uymanıza yardımcı olmak için belirli veri türlerine yönelik gelişmiş denetimler sağlar.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Adım 1. Kimlik Sıfır Güven cihaz erişim korumasını (başlangıç noktası ilkeleri) yapılandırma

İlk adım, kimlik ve cihaz Sıfır Güven korumasını yapılandırarak temel yapınızı oluşturmaktır. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Kimlik ve cihaz erişim Sıfır Güven yapılandırma işlemi" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



Bunu Sıfır Güven [**_önceden yönlendirme için kimlik_**](office-365-security/microsoft-365-policies-configurations.md) ve cihaz erişim korumasına gidin. Bu makale dizisinde, kimlik ve cihaz erişimi önkoşulları yapılandırmaları ve bu yapılandırmalara erişimin güvenliğini sağlamak için Azure Active Directory (Azure AD) Koşullu Erişim, Microsoft Intune ve diğer ilkeler kümesi Microsoft 365  Kurumsal bulut uygulamaları ve hizmetleri, diğer SaaS hizmetleri ve Azure AD ile yayımlanan şirket içi uygulamalar için Uygulama Ara Sunucusu.



|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
|Korumanın üç katmanı için önerilen kimlik ve cihaz erişimi ilkeleri:<br>- Başlangıç noktası<br>- Enterprise (önerilir)<br>- Özel<br><br>Ek öneriler:<br>- Dış kullanıcılar (konuklar)<br>- Microsoft Teams<br>- SharePoint Online<br>- Microsoft Defender for Cloud Apps| Microsoft E3 veya E5<br><br>Azure Active Directory modlardan birini seçin:<br>- Yalnızca bulut<br>- Parola karma eşitlemesi (PHS) kimlik doğrulaması ile karma<br>- Geçişli kimlik doğrulamasıyla karma (PTA)<br>- Federasyon     |Yönetilen cihazlar gerektiren ilkeler için cihaz kaydı. Cihazları kaydetmek için "Uç noktaları Intune" bağlantı noktalarına bakın |
| | | |

Başlangıç noktası katmanını uygulayarak başlayabilirsiniz. Bu ilkeler, cihazları yönetime kaydetmeyi gerektirmez. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Kullanıcı Sıfır Güven cihaz erişimi ilkeleri (başlangıç noktası katmanı)" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>Adım 2. Uç noktaları başka bir Intune

Ardından, cihazlarınızı yönetime kaydettirin ve bunları daha gelişmiş denetimlerle korumaya başlayabilirsiniz. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Intune öğesiyle uç Intune yönetme" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


Bunu [**_yapmak için önceden Intune_**](../solutions/manage-devices-with-intune-overview.md) Kılavuzu ile cihazları yönetme'ye gidin. 


|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
|Cihazları başka bir Intune<br>- Kurumsal cihazlar<br>- AutoPilot/automated<br>- kayıt<br><br>İlkeleri yapılandırma<br>- Uygulama Koruma ilkeleri<br>- Uyumluluk ilkeleri<br>- Cihaz profili ilkeleri | Uç noktaları Azure AD ile kaydetme     | Bilgi koruma özelliklerini yapılandırma, şunları da içerir:<br>- Hassas bilgi türleri<br>- Etiketler<br>- DLP ilkeleri<br>Bu özellikler için bkz. 5. Adım. Verileri koruyun ve yönetirsiniz (bu makalenin devamlarında).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Adım 3. Kimlik Sıfır Güven cihaz erişim koruması (kimlik ve cihaz erişim Enterprise ekleme

Yönetime kayıtlı cihazlarla, artık uyumlu cihazlar gerektiren tüm önerilen kimlik Sıfır Güven ve cihaz erişim ilkelerinin tamamını gerçekleştirebilirsiniz.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Cihaz Sıfır Güven kimlik ve erişim ilkeleri" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Ortak kimlik [**_ve cihaz erişimi ilkelerine geri_**](office-365-security/identity-access-policies.md) dönme ve ilkeleri ortak kimlik Enterprise ekleyin.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Kullanıcı Sıfır Güven ve erişim ilkeleri — Enterprise (önerilen) katman" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Adım 4. Değerlendirme, pilot uygulama ve dağıtım Microsoft 365 Defender

Microsoft 365 Defender, Microsoft 365 ortamınız genelinde uç nokta, e-posta, uygulamalar ve kimlikler dahil olmak üzere sinyali, tehdide ve uyarıyı otomatik olarak toplayan, bu iletişimleri analiz eden ve analiz eden genişletilmiş bir algılama ve yanıt (XDR) çözümüdür.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Sıfır Güven mimarisine Microsoft 365 Defender ekleme işlemi" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Elektronik [**_bileşenlerin pilot Microsoft 365 Defender_**](defender/eval-overview.md) dağıtımına ve dağıtımına ilişkin yöntemsel kılavuz için, Değerlendirme ve Microsoft 365 Defender gidin. 

|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
| Tüm bileşenler için değerlendirme ve pilot ortamını ayarlama:<br>- Kimlik için Defender<br>- Office 365 için Defender<br>- Uç Nokta için Defender<br>- Microsoft Defender for Cloud Apps<br><br>Tehditlere karşı korunun<br><br> Tehditleri araştırın ve karşı yanıt verin   | Bu makalenin her bileşenine yönelik mimari gereksinimleri hakkında bilgi Microsoft 365 Defender.        | Azure AD Identity Protection, bu çözüm kılavuzuna dahil değildir. Kimlik ve cihaz erişim koruması için 1. Sıfır Güven yapılandırma'ya dahildir.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>Adım 5. Hassas verileri koruma ve yönetme

Hayat Microsoft Bilgi Koruması seyahat istediği her yerde hassas bilgileri bulan, sınıflandıracak ve korumanıza yardımcı olacak bir yol (MIP) uygulaması gerçekleştirin.

MIP özellikleri, Uyumluluk Microsoft 365 dahil edilir ve size verilerinizi bilmek, verilerinizi korumak ve veri kaybını önlemek için gerekli araçları sağlar.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Bilgi koruma özellikleri, ilke zorlaması aracılığıyla verileri korur" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Bu çalışma, bu makalenin önceki kısmında gösterildiği gibi dağıtım yığınının en üstünde gösterse de, bu çalışmaya istediğiniz zaman başlayabilirsiniz. 

Microsoft Bilgi Koruması, belirli iş hedeflerinize yönelik olarak kullanabileceğiniz bir çerçeve, süreç ve özellikler sağlar.

:::image type="content" source="../media/zero-trust/mip-solution-overview.png" alt-text="Microsoft Bilgi Koruması (MIP) çerçevesi" lightbox="../media/zero-trust/mip-solution-overview.png":::


Bilgi korumasını planlama ve dağıtma hakkında daha fazla bilgi için bkz [**_. Microsoft Bilgi Koruması dağıtma_**](../compliance/information-protection-solution.md). 

Veri gizliliği düzenlemeleri için bilgi korumasını dağıtıyorsanız, bu çözüm kılavuzu tüm süreç için önerilen çerçeveyi sunar: Veri gizliliği düzenlemelerine uygun olarak bilgi [**_korumayı_**](../solutions/information-protection-deploy.md) Microsoft 365.