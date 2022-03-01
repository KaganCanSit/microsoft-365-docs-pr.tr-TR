---
title: Microsoft dışı bulut uygulamaları için Veri kaybı önleme ilkelerini kullanma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Microsoft dışı bulut uygulamaları için dlp ilkelerini kullanmayı öğrenin.
ms.openlocfilehash: b374f9b85d41b6dd6a5281e17347dffd414361da
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005456"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma

Microsoft dışı bulut uygulamalarına yönelik veri kaybı önleme (DLP) ilkeleri Microsoft 365 DLP özellik paketinin bir parçasıdır; bu özellikleri kullanarak, farklı hizmetler genelinde hassas öğeleri Microsoft 365 ve koruyabilirsiniz. Tüm Microsoft DLP teklifleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi.](dlp-learn-about-dlp.md)

DLP ilkelerini, Microsoft'a uygun olmayan bulut uygulamaları için kullanarak, hassas öğelerin ne zaman kullanılmış ve Microsoft dışı bulut uygulamalarıyla ne zaman paylaşılıyor olduğunu izleyebilir ve algıabilirsiniz. Bu ilkelerin kullanımı, doğru kullanıldıklardan ve korunduklardan emin olmak için gereken görünürlük ve denetime sahip olur ve güvenliğini tehlikeye atacak riskli davranışları önlemeye yardımcı olur.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Microsoft bulut uygulamalarına yönelik olmayan DLP ilkelerini kullanmaya başlamadan önce, Microsoft 365 [eklentilerinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) onaylayın. Bu işleve erişmek ve bu işlevi kullanmak için, şu aboneliklerden veya eklentilerden birini kullanasınız:

- Microsoft 365 E5
- Microsoft 365 E5 Uyumluluk
- Microsoft 365 E5 Güvenlik

### <a name="permissions"></a>İzinler
DLP ilkesi oluşturan kullanıcı aşağıdaki gibi olması gerekir:

- Genel yönetici
- Uyumluluk yöneticisi: Azure AD'de ata
- Uyumluluk veri yöneticisi: Azure AD'de atama

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Defender'nızı Bulut Uygulamaları ortamına hazırlama

Microsoft bulut uygulamalarına yönelik DLP ilkeleri, Bulut Uygulamaları için Defender DLP özelliklerini kullanır. Bunu kullanmak için Defender'nızı Bulut Uygulamaları ortamına hazırlamanız gerekir. Yönergeler için bkz [. Uygulamalarınız için anında görünürlük, koruma ve yönetim eylemlerini ayarlama](/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps).

### <a name="connect-a-non-microsoft-cloud-app"></a>Bağlan olmayan bir bulut uygulamasını güncelleştirme

DLP ilkesini Microsoft olmayan belirli bir bulut uygulamasında kullanmak için, uygulamanın Bulut Uygulamaları için Defender'a bağlı olması gerekir. Bilgi için bkz:

- [Bağlan Kutusu](/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [Bağlan Dropbox](/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [Bağlan G-Workspace](/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [Bağlan Salesforce](/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [Bağlan Cisco Webex](/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

Bulut uygulamalarınızı Bulut Uygulamaları için Defender'a bağdikten sonra, Microsoft 365 DLP ilkeleri oluşturabilirsiniz.

> [!NOTE]
> Ayrıca Bulut Uygulamaları için Microsoft Defender'ı kullanarak Microsoft bulut uygulamalarına DLP ilkeleri oluşturabilirsiniz. Bununla birlikte, Microsoft bulut uygulamalarına DLP Microsoft 365 ilkeleri oluşturmak ve yönetmek için Microsoft 365'i kullanılması önerilir.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>Microsoft dışı bir bulut uygulaması için DLP ilkesi oluşturma

DLP ilkesi için bir konum seçin, Bulut Uygulamaları için **Microsoft Defender konumunu** seçin.

- Belirli bir uygulama veya örneği seçmek için Örnek **seç'i seçin**.
- Bir örneği seç etmezseniz, ilke Bulut Uygulamaları için Microsoft Defender kiracısı uygulamanıza bağlı tüm uygulamaları kullanır.

   ![İlkenin geçerli olduğu konumlar.](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Box-US ve Box-General.](../media/2-dlp-non-microsoft-cloud-app-box.png)

Microsoft'a özel olarak desteklenen her bulut uygulaması için çeşitli eylemler seçebilirsiniz. Her uygulama için farklı olası eylemler vardır (bulut uygulama API'sini gösterir).

![Kural oluşturma.](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

DLP ilkesinde bir kural  oluşturmak için Microsoft dışı bulut uygulamaları için bir eylem seçin. Üçüncü taraf uygulamalarını kısıtlamak için Üçüncü Taraf Uygulamaları **Kısıtla'ya seçin**.

![Üçüncü taraf uygulamalarını kısıtla.](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Microsoft uygulamalarına uygulanmayan DLP ilkeleri Bulut Uygulamaları için Microsoft Defender'ı kullanır. Microsoft uygulaması olmayan bir uygulama için DLP ilkesi oluşturulduğunda, aynı ilke Bulut Uygulamaları için Microsoft Defender'da da otomatik olarak oluşturulur.

DLP ilkelerini oluşturma ve yapılandırma hakkında bilgi için bkz. [Test oluşturma ve DLP ilkesi ayarlama](./create-test-tune-dlp-policy.md).

## <a name="see-also"></a>Ayrıca Bkz

- [Test oluşturma ve DLP ilkesi ayarlama](./create-test-tune-dlp-policy.md)
- [Varsayılan DLP ilkesiyle çalışmaya başlama](./get-started-with-the-default-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](./create-a-dlp-policy-from-a-template.md)
