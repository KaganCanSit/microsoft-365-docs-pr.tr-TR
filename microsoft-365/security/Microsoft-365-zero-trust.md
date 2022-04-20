---
title: Microsoft 365 Sıfır Güven dağıtım planı
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Tehditlere karşı savunmak ve hassas verileri korumak için ortamınıza Microsoft 365 Sıfır Güven güvenlik dağıtmayı öğrenin.
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
ms.openlocfilehash: 3b943569485ffaa96b33208c1c4bf0a491c23a95
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939487"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 Sıfır Güven dağıtım planı

Bu makalede, **Microsoft 365 ile Sıfır Güven** güvenliği oluşturmaya yönelik bir dağıtım planı sağlanır. Sıfır Güven, ihlal olduğunu varsayan ve her isteği kontrolsüz bir ağdan geliyormuş gibi doğrulayan yeni bir güvenlik modelidir. İsteğin nereden kaynaklandığına veya hangi kaynağa eriştiğine bakılmaksızın, Sıfır Güven modeli bize "hiçbir zaman güvenme, her zaman doğrulama" öğretir.

## <a name="zero-trust-security-architecture"></a>Sıfır Güven güvenlik mimarisi

Sıfır Güven bir yaklaşım tüm dijital emlak genelinde genişletilir ve tümleşik bir güvenlik felsefesi ve uçtan uca strateji olarak hizmet eder.

Bu çizim, Sıfır Güven katkıda bulunan birincil öğelerin bir gösterimini sağlar.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Sıfır Güven güvenlik mimarisi" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Çizimde:

- Güvenlik ilkesi zorlama, Sıfır Güven mimarisinin merkezindedir. Bu, kullanıcı hesabı riskini, cihaz durumunu ve ayarladığınız diğer ölçütleri ve ilkeleri dikkate alan koşullu erişime sahip Multi Factor kimlik doğrulamasını içerir.
- Kimlikler, cihazlar, veriler, uygulamalar, ağ ve diğer altyapı bileşenlerinin tümü uygun güvenlikle yapılandırılır. Bu bileşenlerin her biri için yapılandırılan ilkeler, genel Sıfır Güven stratejinizle koordine edilir. Örneğin, cihaz ilkeleri iyi durumdaki cihazlar için ölçütleri belirler ve koşullu erişim ilkeleri belirli uygulamalara ve verilere erişmek için iyi durumdaki cihazlar gerektirir.
- Tehdit koruması ve zeka ortamı izler, mevcut riskleri ortaya çıkarır ve saldırıları düzeltmek için otomatik eylem gerçekleştirir.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype).
-->

Sıfır Güven hakkında daha fazla bilgi için bkz. Microsoft'un [_**Sıfır Güven Rehberlik Merkezi**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Microsoft 365 için Sıfır Güven dağıtma

Microsoft 365, ortamınızda Sıfır Güven oluşturmanıza yardımcı olacak birçok güvenlik ve bilgi koruma özelliğiyle kasıtlı olarak oluşturulur. Kuruluşunuzun kullandığı diğer SaaS uygulamalarına ve bu uygulamalardaki verilere erişimi korumak için özelliklerin çoğu genişletilebilir.

Bu çizim, Sıfır Güven özellikleri dağıtma işlemini temsil eder. Bu çalışma, alttan başlayıp en üste doğru çalışarak birlikte yapılandırılabilir çalışma birimlerine bölünerek önkoşul çalışmasının tamamlanmasını sağlar.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Microsoft 365 Sıfır Güven dağıtım yığını" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Bu çizimde:

- Sıfır Güven, kimlik ve cihaz korumasının temeli ile başlar.
- Tehdit koruma özellikleri, güvenlik tehditlerinin gerçek zamanlı izlenmesini ve düzeltilmesi için bu temelin üzerine kurulmuştur.
- Bilgi koruma ve idare, en değerli bilgilerinizi korumak ve kişisel bilgileri korumak da dahil olmak üzere uyumluluk standartlarına uymanıza yardımcı olmak için belirli veri türlerini hedefleyen gelişmiş denetimler sağlar.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Adım 1. Sıfır Güven kimliği ve cihaz erişim korumasını yapılandırma — başlangıç noktası ilkeleri

İlk adım, kimlik ve cihaz erişim korumasını yapılandırarak Sıfır Güven temelinizi oluşturmaktır.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Sıfır Güven kimliği ve cihaz erişim korumasını yapılandırma işlemi" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

Bunu gerçekleştirmek için Sıfır Güven [**_kimlik ve cihaz erişim korumasına_**](office-365-security/microsoft-365-policies-configurations.md) gidin. Bu makale serisinde bir dizi kimlik ve cihaz erişimi önkoşul yapılandırması ve Azure Active Directory (Azure AD) Koşullu Erişim, Microsoft Intune ve Microsoft 365 erişiminin güvenliğini sağlamak için diğer ilkeler açıklanmaktadır  Azure AD Uygulama Ara Sunucusu ile yayımlanan kurumsal bulut uygulamaları ve hizmetleri, diğer SaaS hizmetleri ve şirket içi uygulamalar için.

|Içerir|Önkoşullar|Şunları içermez:|
|---------|---------|---------|
|Üç koruma katmanı için önerilen kimlik ve cihaz erişim ilkeleri: <ul><li>Başlangıç noktası</li><li>Enterprise (önerilir)</li><li>Özel</li></ul> <br> Ek öneriler: <ul><li>Dış kullanıcılar (konuklar)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Bulut Uygulamaları için Microsoft Defender</lu></ul>|Microsoft E3 veya E5 <br><br> Bu modlardan birinde Azure Active Directory: <ul><li>Yalnızca bulut</li><li>Parola karması eşitleme (PHS) kimlik doğrulaması ile karma</li><li>Doğrudan kimlik doğrulaması (PTA) ile karma</li><li>Federe</li></ul>|Yönetilen cihazlar gerektiren ilkeler için cihaz kaydı. Bkz[. 2. Adım. Cihazları kaydetmek için Intune ile uç noktaları yönetme](#step-2-manage-endpoints-with-intune)|

Başlangıç noktası katmanını uygulayarak başlayın. Bu ilkeler, cihazların yönetime kaydedilmesini gerektirmez.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Sıfır Güven kimlik ve cihaz erişim ilkeleri — başlangıç noktası katmanı" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>Adım 2. uç noktaları Intune ile yönetme

Ardından, cihazlarınızı yönetime kaydedin ve bunları daha gelişmiş denetimlerle korumaya başlayın.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="uç noktaları Intune ile yönet öğesi" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

Bunu gerçekleştirmek için açıklayıcı yönergeler için [**_Cihazları Intune ile yönetme_**](../solutions/manage-devices-with-intune-overview.md) konusuna gidin.

|Içerir|Önkoşullar|Şunları içermez:|
|---------|---------|---------|
|Cihazları Intune ile kaydetme: <ul><li>Şirkete ait cihazlar</li><li>Otomatik pilot/otomatik</li><li>Kayıt</li></ul> <br> İlkeleri yapılandırma: <ul><li>Uygulama Koruma ilkeleri</li><li>Uyumluluk ilkeleri</li><li>Cihaz profili ilkeleri</li></ul>|Uç noktaları Azure AD'ye kaydetme|Aşağıdakiler dahil olmak üzere bilgi koruma özelliklerini yapılandırma: <ul><li>Hassas bilgi türleri</li><li>Etiket</li><li>DLP ilkeleri</li></ul> <br> Bu özellikler için bkz [. 5. Adım. Hassas verileri koruma ve yönetme](#step-5-protect-and-govern-sensitive-data) (bu makalenin ilerleyen bölümlerinde).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Adım 3. Sıfır Güven kimlik ve cihaz erişim koruması ekleme — Enterprise ilkeleri

Yönetime kayıtlı cihazlar sayesinde artık uyumlu cihazlar gerektiren önerilen Sıfır Güven kimlik ve cihaz erişim ilkelerinin tamamını uygulayabilirsiniz.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Cihaz yönetimiyle Sıfır Güven kimliği ve erişim ilkeleri" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

[**_Ortak kimlik ve cihaz erişim ilkelerine_**](office-365-security/identity-access-policies.md) dönün ve ilkeleri Enterprise katmanına ekleyin.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Sıfır Güven kimlik ve erişim ilkeleri — Enterprise (önerilen) katman" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Adım 4. Microsoft 365 Defender değerlendirme, pilot uygulama ve dağıtma

Microsoft 365 Defender uç nokta, e-posta, uygulamalar ve kimlikler dahil olmak üzere Microsoft 365 ortamınızda sinyal, tehdit ve uyarı verilerini otomatik olarak toplayan, ilişkilendiren ve analiz eden genişletilmiş bir algılama ve yanıt (XDR) çözümüdür.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Sıfır Güven mimarisine Microsoft 365 Defender ekleme işlemi" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Microsoft 365 Defender bileşenleri pilot oluşturma ve dağıtmaya yönelik yöntemsel bir kılavuz için [**_Değerlendirme_**](defender/eval-overview.md) ve pilot Microsoft 365 Defender bölümüne gidin.

|Içerir|Önkoşullar|Şunları içermez:|
|---------|---------|---------|
|Tüm bileşenler için değerlendirme ve pilot ortamı ayarlayın: <ul><li>Kimlik için Microsoft Defender</li><li>Office 365 için Defender</li><li>Uç Nokta için Defender</li><li>Bulut Uygulamaları için Microsoft Defender</li></ul> <br> Tehditlere karşı korunun <br><br> Tehditleri araştırın ve karşı yanıt verin|Microsoft 365 Defender her bileşeni için mimari gereksinimleri hakkında bilgi edinmek için kılavuza bakın.| Azure AD Kimlik Koruması bu çözüm kılavuzuna dahil değildir. [1. Adım'a dahildir. Sıfır Güven kimliği ve cihaz erişim korumasını yapılandırın](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>Adım 5. Hassas verileri koruma ve yönetme

Microsoft Purview Information Protection uygulayarak hassas bilgileri nerede yaşarsa yaşasın veya seyahat etseler keşfetmenize, sınıflandırmanıza ve korumanıza yardımcı olun.

Microsoft Purview Information Protection özellikleri Microsoft Purview'a dahil edilir ve verilerinizi bilmeniz, verilerinizi korumanız ve veri kaybını önlemeniz için size araçlar sağlar.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Bilgi koruma özellikleri, ilke uygulama yoluyla verileri koruma" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Bu çalışma, bu makalenin önceki bölümlerinde gösterilen dağıtım yığınının en üstünde gösteriliyor olsa da, bu çalışmaya istediğiniz zaman başlayabilirsiniz.

Microsoft Purview Information Protection, belirli iş hedeflerinizi gerçekleştirmek için kullanabileceğiniz bir çerçeve, süreç ve özellikler sağlar.

![Microsoft Purview Information Protection](../media/zero-trust/mip-solution-overview.png)

Bilgi korumasını planlama ve dağıtma hakkında daha fazla bilgi için bkz. [**_Microsoft Purview Information Protection çözümü dağıtma_**](../compliance/information-protection-solution.md). 

Veri gizliliği düzenlemeleri için bilgi koruması dağıtıyorsanız, bu çözüm kılavuzu sürecin tamamı için önerilen bir çerçeve sağlar: [**_Microsoft 365 ile veri gizliliği düzenlemeleri için bilgi koruması dağıtma_**](../solutions/information-protection-deploy.md).
