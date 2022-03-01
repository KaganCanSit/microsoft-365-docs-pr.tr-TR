---
title: Microsoft 365 Sıfır Güveni dağıtım planı
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Tehditlere karşı savunmak Microsoft 365 hassas verileri korumak için ortamınıza Sıfır Güveni Güvenliği dağıtımı yapmayı öğrenin.
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
ms.openlocfilehash: 9b37e353af74b7a01c0647f99b149f5fac0ae8a3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011783"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 Sıfır Güveni dağıtım planı

Bu makalede, güven ve güvenlik nedeniyle **Sıfır Güveni sağlayan** bir Microsoft 365. Sıfır Güven, ihlal olduğunu varsayanın ve her isteğin denetimsiz bir ağdan geliyor gibi doğrulandığını varsayan yeni bir güvenlik modelidir. İsteğin nereden geldiğine veya hangi kaynağa erişten olursa olsun, Sıfır Güven modeli "asla güvenme, her zaman doğrulama" öğretecek.


## <a name="zero-trust-security-architecture"></a>Sıfır Güveni mimarisi

Sıfır Güven yaklaşımı tüm dijital emlak genelinde genişler ve tümleşik bir güvenlik uzmanı ve  uç strateji olarak hizmet vermektedir. 

Bu çizim, Sıfır Güven'e katkıda bulunan birincil öğelerin bir gösterimini sağlar.

<!---
[![Zero Trust security architecture](../media/zero-trust/zero-trust-architecture.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/zero-trust/zero-trust-architecture.png)
-->

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Sıfır Güveni mimarisi" lightbox="../media/zero-trust/zero-trust-architecture.png":::



Çizimde:
- Güvenlik ilkesi zorlaması, Sıfır Güven mimarisinin merkezindedir. Bu, kullanıcı hesabı riskini, cihaz durumunu ve sizin ayardınız diğer ölçütleri ve ilkeleri hesaba katan koşullu erişimle Çok Faktörlü kimlik doğrulamasını içerir.
- Kimlikler, cihazlar, veriler, uygulamalar, ağ ve diğer altyapı bileşenlerinin hepsi uygun güvenlikle yapılandırılır. Bu bileşenlerin her biri için yapılandırılan ilkeler, genel Sıfır Güven stratejiniz ile eşgüdüm sağlar. Örneğin, cihaz ilkeleri sağlıklı cihazlar için ölçütleri belirler ve belirli uygulamalara ve verilere erişim için sağlıklı cihazlara yönelik koşullu erişim ilkeleri gerekir.
- Tehdit koruması ve zeka ortamı izler, geçerli riskleri ortaya çıkartır ve saldırılarını düzeltmek için otomatik eylem alır.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

Sıfır Güven hakkında daha fazla bilgi için Microsoft'un Sıfır Güven [_**Kılavuzu Merkezi'ne bakın**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Microsoft 365 için Sıfır Güveni Dağıtma

Microsoft 365, ortamınıza Sıfır Güveni oluşturmanızı yardımcı olmak için bilerek birçok güvenlik ve bilgi koruma özelliğiyle tasarlanmıştır. Pek çok özellik, kurum tarafından kullanan diğer SaaS uygulamalarına ve bu uygulamalar içindeki verilere erişimi korumak için genişletılabilir.

Bu çizim, Sıfır Güveni özelliklerini dağıtma çalışmalarını temsil eder. Bu çalışma, önkoşulların tamamlandıktan sonra alttan başlayarak en alttan başlayarak en üstten başlayarak birlikte yapılandırılana kadar çalışma birimlerine bozulur.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Microsoft 365 Sıfır Güven dağıtım yığını" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Bu şekilde:
- Sıfır Güven, bir kimlik ve cihaz koruması temeli ile başlar. 
- Tehdit koruması özellikleri, güvenlik tehditlerini gerçek zamanlı olarak izleme ve düzeltme sağlamak için bu temelin üzerine kurulur. 
- Bilgi koruma ve yönetim, en değerli bilgilerinizi korumak ve kişisel bilgilerinizi koruma da dahil olmak üzere uyumluluk standartlarına uymanıza yardımcı olmak için belirli veri türlerine yönelik gelişmiş denetimler sağlar.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Adım 1. Sıfır Güven kimliğini ve cihaz erişim korumasını (başlangıç noktası ilkeleri) yapılandırma

İlk adım, kimlik ve cihaz erişim korumasını yapılandırarak Sıfır Güven temelini oluşturmaktır. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Sıfır Güven kimliğini ve cihaz erişim korumasını yapılandırma" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



Bunu [**_gerçekleştirmeyle ilgili ön simge bilgileri için Sıfır_**](office-365-security/microsoft-365-policies-configurations.md) Güven kimliği ve cihaz erişim koruması'ne gidin. Bu makale dizisinde, kimlik ve cihaz erişimi önkoşulları yapılandırmaları ve bu yapılandırmalara erişimin güvenliğini sağlamak için Azure Active Directory (Azure AD) Koşullu Erişim, Microsoft Intune ve diğer ilkeler kümesi Microsoft 365  Azure AD Uygulama Ara Sunucusu ile yayımlanan kurumsal bulut uygulamaları ve hizmetleri, diğer SaaS hizmetleri ve şirket içi uygulamalar için.



|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
|Korumanın üç katmanı için önerilen kimlik ve cihaz erişimi ilkeleri:<br>- Başlangıç noktası<br>- Enterprise (önerilir)<br>- Özel<br><br>Ek öneriler:<br>- Dış kullanıcılar (konuklar)<br>- Microsoft Teams<br>- SharePoint Online<br>- Bulut Uygulamaları için Microsoft Defender| Microsoft E3 veya E5<br><br>Azure Active Directory modlardan birini seçin:<br>- Yalnızca bulut<br>- Parola karma eşitlemesi (PHS) kimlik doğrulaması ile karma<br>- Geçişli kimlik doğrulamasıyla karma (PTA)<br>- Federasyon     |Yönetilen cihazlar gerektiren ilkeler için cihaz kaydı. Cihazları kaydetmek için bkz. "Uç noktaları Intune ile yönetme". |
| | | |

Başlangıç noktası katmanını uygulayarak başlayabilirsiniz. Bu ilkeler, cihazları yönetime kaydetmeyi gerektirmez. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Sıfır Güven kimliği ve cihaz erişim ilkeleri — başlangıç noktası katmanı" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>Adım 2. Intune ile uç noktaları yönetme

Ardından, cihazlarınızı yönetime kaydettirin ve bunları daha gelişmiş denetimlerle korumaya başlayabilirsiniz. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Intune ile uç noktaları yönetme" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


Bunu [**_yapmak için ön simge kılavuzu için Cihazları Intune_**](../solutions/manage-devices-with-intune-overview.md) ile yönetme'ye gidin. 


|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
|Intune ile cihazları kaydetme<br>- Kurumsal cihazlar<br>- AutoPilot/automated<br>- kayıt<br><br>İlkeleri yapılandırma<br>- Uygulama Koruma ilkeleri<br>- Uyumluluk ilkeleri<br>- Cihaz profili ilkeleri | Uç noktaları Azure AD ile kaydetme     | Bilgi koruma özelliklerini yapılandırma, şunları da içerir:<br>- Hassas bilgi türleri<br>- Etiketler<br>- DLP ilkeleri<br>Bu özellikler için bkz. 5. Adım. Verileri koruyun ve yönetirsiniz (bu makalenin devamlarında).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Adım 3. Sıfır Güven kimliği ve cihaz erişim koruması (güvenlik Enterprise ekleme

Yönetime kayıtlı cihazlarla, artık uyumlu cihazlar gerektiren, önerilen Sıfır Güveni kimliği ve cihaz erişim ilkelerinin tamamını hayata geçirebilirsiniz.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Cihaz yönetimiyle Sıfır Güven kimliği ve erişim ilkeleri" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Ortak kimlik [**_ve cihaz erişimi ilkelerine geri_**](office-365-security/identity-access-policies.md) dönme ve ilkeleri ortak kimlik Enterprise ekleyin.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Sıfır Güven kimliği ve erişim ilkeleri — Enterprise (önerilen) katman" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Adım 4. Değerlendirme, pilot uygulama ve dağıtım Microsoft 365 Defender

Microsoft 365 Defender, Microsoft 365 ortamınız genelinde uç nokta, e-posta, uygulamalar ve kimlikler dahil olmak üzere sinyali, tehdide ve uyarıyı otomatik olarak toplayan, bu iletişimleri analiz eden ve analiz eden genişletilmiş bir algılama ve yanıt (XDR) çözümüdür.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Sıfır Microsoft 365 Defender mimarisine kullanıcı ekleme" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Elektronik [**_bileşenlerin pilot Microsoft 365 Defender_**](defender/eval-overview.md) dağıtımına ve dağıtımına ilişkin yöntemsel kılavuz için, Değerlendirme ve Microsoft 365 Defender gidin. 

|Şunları içerir:  |Önkoşullar  |Bu,  |
|---------|---------|---------|
| Tüm bileşenler için değerlendirme ve pilot ortamını ayarlama:<br>- Kimlik için Defender<br>- Office 365 için Defender<br>- Uç Nokta için Defender<br>- Bulut Uygulamaları için Microsoft Defender<br><br>Tehditlere karşı koruma<br><br> Tehditleri araştırma ve yanıtlama   | Bu makalenin her bileşenine yönelik mimari gereksinimleri hakkında bilgi Microsoft 365 Defender.        | Azure AD Identity Protection, bu çözüm kılavuzuna dahil değildir. 1. Adım: Sıfır Güven kimliğini ve cihaz erişim korumasını yapılandırma'ya dahildir.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>Adım 5. Hassas verileri koruma ve yönetme

Hayat Microsoft Bilgi Koruması seyahat istediği her yerde hassas bilgileri bulan, sınıflandıracak ve korumanıza yardımcı olacak bir yol (MIP) uygulaması gerçekleştirin.

MIP özellikleri, Uyumluluk Microsoft 365 dahil edilir ve size verilerinizi bilmek, verilerinizi korumak ve veri kaybını önlemek için gerekli araçları sağlar.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Bilgi koruma özellikleri, ilke zorlaması aracılığıyla verileri korur" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Bu çalışma, bu makalenin önceki kısmında gösterildiği gibi dağıtım yığınının en üstünde gösterse de, bu çalışmaya istediğiniz zaman başlayabilirsiniz. 

Microsoft Bilgi Koruması, belirli iş hedeflerinize yönelik olarak kullanabileceğiniz bir çerçeve, süreç ve özellikler sağlar.

![Microsoft Bilgi Koruması (MIP) çerçevesi](../media/zero-trust/mip-solution-overview.png)

Bilgi korumasını planlama ve dağıtma hakkında daha fazla bilgi için bkz [**_. Microsoft Bilgi Koruması dağıtma_**](../compliance/information-protection-solution.md). 

Veri gizliliği düzenlemeleri için bilgi korumasını dağıtıyorsanız, bu çözüm kılavuzu tüm süreç için önerilen çerçeveyi sunar: Veri gizliliği düzenlemelerine uygun olarak bilgi [**_korumayı_**](../solutions/information-protection-deploy.md) Microsoft 365.