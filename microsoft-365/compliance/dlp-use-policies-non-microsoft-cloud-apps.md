---
title: Microsoft dışı bulut uygulamaları için DLP ilkelerini kullanma
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
ms.openlocfilehash: a50849b53819a7c5872c3ec8cb279ffa8d14e27f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634405"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma

Hassas öğeler Microsoft dışı bulut uygulamaları aracılığıyla kullanıldığında ve paylaşıldığında, bunları izlemek, algılamak ve eylemlere Microsoft Defender for Cloud Apps için DLP ilkelerini kapsamlandırabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

DLP ilkelerini kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) ve tüm eklentileri onaylayın. Bu işleve erişmek ve bu işlevselliği kullanmak için şu aboneliklerden veya eklentilerden birine sahip olmanız gerekir:

- Microsoft 365 E5
- Microsoft 365 E5 Uyumluluk
- Microsoft 365 E5 Güvenlik

### <a name="permissions"></a>İzinler
DLP ilkesini oluşturan kullanıcı şu olmalıdır:

- Genel yönetici
- Uyumluluk yöneticisi: Azure AD'de atama
- Uyumluluk veri yöneticisi: Azure AD'de atama

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Defender for Cloud Apps ortamınızı hazırlama

Kapsamı Microsoft Defender for Cloud Apps olarak belirlenmiş DLP ilkelerini yapılandırmadan önce Defender for Cloud Apps ortamınızı hazırlamanız gerekir. Yönergeler için bkz[. Hızlı Başlangıç: Microsoft Defender for Cloud Apps kullanmaya başlama](/defender-cloud-apps/get-started).

### <a name="connect-a-non-microsoft-cloud-app"></a>Microsoft dışı bir bulut uygulamasını bağlama

Kapsamı Microsoft olmayan belirli bir bulut uygulamasıyla belirlenmiş bir DLP ilkesi kullanmak için uygulamanın Cloud Apps için Defender'a bağlı olması gerekir. Bilgi için bkz:

- [Bağlan Kutusu](/defender-cloud-apps/connect-box)
- [Dropbox'ı bağlama](/defender-cloud-apps/connect-dropbox)
- [Google Workspace'i bağlama](/defender-cloud-apps/connect-google-workspace)
- [Salesforce'u bağlama](/defender-cloud-apps/connect-salesforce)
- [Cisco Webex'i bağlama](/defender-cloud-apps/connect-webex)

Bulut uygulamalarınızı Cloud Apps için Defender'a bağladıktan sonra, bunlar için DLP ilkeleri oluşturabilirsiniz.

## <a name="create-a-dlp-policy-scoped-to-a-non-microsoft-cloud-app"></a>Kapsamı Microsoft olmayan bir bulut uygulamasına göre belirlenmiş bir DLP ilkesi oluşturma

DLP ilkesi oluşturma yordamları için [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md) makalesine bakın. İlkenizi yapılandırdığınızda bu noktaları göz önünde bulundurun.

- **Microsoft Defender for Cloud Apps** konumunu açın seçeneğini belirleyin.
- Belirli bir uygulamayı veya örneği seçmek için **Örnek seç'i** seçin. Örnek seçmezseniz ilkenin kapsamı Microsoft Defender for Cloud Apps kiracınızdaki tüm bağlı uygulamalar olarak belirlenir.
- Üçüncü taraf uygulamaları zorlamak için bir dizi **Eylem** arasından seçim yapabilirsiniz. Üçüncü taraf uygulamaları kısıtlamak için **Üçüncü Taraf Uygulamalarını Kısıtla'yı** ve ardından belirli eylemleri seçin.

![bağlı bulut uygulamalarında zorunlu kılınacak eylemlerin listesi](../media/dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> kapsamı Microsoft Defender for Cloud Apps olarak belirlenmiş bir DLP ilkesi oluşturduğunuzda, aynı ilke otomatik olarak Microsoft Defender for Cloud Apps oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz

- [Test oluşturma ve DLP ilkesini ayarlama](./create-test-tune-dlp-policy.md)
- [Varsayılan DLP ilkesini kullanmaya başlama](./get-started-with-the-default-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](./create-a-dlp-policy-from-a-template.md)
