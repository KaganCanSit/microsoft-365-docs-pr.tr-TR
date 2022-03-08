---
title: Playbooks'a not verme uyarısı
description: İyi bilinen saldırılar için uyarıları gözden geçirin ve saldırıyı düzeltmek ve ağın korunması için önerilen eylemleri gerçekleştirin.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 129a4f2efd9a47c09535be3ba0f56504f3da697c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328015"
---
# <a name="alert-grading-playbooks"></a>Playbooks'a not verme uyarısı

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Uyarı notlama playbooks'ları iyi bilinen saldırılara yönelik uyarıları yöntemsel olarak gözden geçirmenize, hızla sınıflandırmanıza ve saldırıyı düzeltmek ve ağın korunması için önerilen eylemlere izin verir. Uyarı notlama, genel olayı düzgün bir şekilde sınıflandırmaya da yardımcı olur.

Güvenlik araştırmacısı veya güvenlik işlemleri merkezi (SOC) analisti olarak, aşağıdaki işlemleri yapmak için Microsoft 365 Defender portalına erişiminiz olması gerekir:

- Oluşturulan uyarıları ve ilişkili olayları değerlendirin ve gözden geçirin. Uyarıları [araştırma'ya bakın](investigate-alerts.md).
- Kiracının güvenlik sinyali verinde arama gerçekleştirin ve olası tehdit ve şüpheli etkinlikleri kontrol edin. Gelişmiş [ava bakın](advanced-hunting-overview.md).

>[!Note]
>Microsoft'a yalnızca araştırmanın sonunda değil, aynı zamanda soruşturma süreci sırasında da doğru pozitif ve yanlış pozitif uyarılar hakkında geri bildirim sebilirsiniz. Bu, Microsoft'a gelecekte güvenlik olaylarının analiz ve sınıflandırması için yardımcı olabilir.
>

## <a name="microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender

[Microsoft Defender For Office 365](/microsoft-365/security/office-365-security/defender-for-office-365), e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. Defender for Office 365 şunları içerir:

- Tehdit koruması ilkeleri

   Organizasyonu için uygun koruma düzeyini ayarlamak üzere tehdit koruması ilkelerini tanımlayın.

- Raporlar

  Defender'ı izlemek ve Office 365 performansını izlemek için gerçek zamanlı raporları görüntüleniyor.

- Tehdit soruşturması ve yanıt özellikleri

  Tehditleri araştırmak, anlamak, benzetimini yapmak ve engellemek için önde gelen araçları kullanın.

- Otomatik araştırma ve yanıt özellikleri

  Zaman ve çabadan tasarruf etmek için inceler ve tehditleri azaltabilirsiniz.

Güvenlik Office 365 Defender şöyle sınıflandırılabilir: 

- Onaylanmış kötü amaçlı etkinlikler için doğru pozitif (TP). 
- Kötü amaçlı olmayan onaylanmış etkinlikler için hatalı pozitif (FP).

>[!Note]
>Microsoft 365 Defender portalı [https://security.microsoft.com](https://security.microsoft.com) mevcut Microsoft güvenlik portallarından gelen işlevleri bir araya getirir. Hızlı Microsoft 365 Defender erişimi vurgular, daha basit düzenler ve daha kolay kullanım için ilgili bilgileri bir araya getirir.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

[Bulut Uygulamaları için Microsoft Defender](/defender-cloud-apps) ; günlük toplama, API bağlayıcıları ve ters ara sunucu gibi çeşitli dağıtım modlarını destekleyen bir Bulut Erişim Güvenlik Aracısı (CASB) aracıdır. Tüm Microsoft ve üçüncü taraf bulut hizmetleriniz genelinde siber tehditleri tespit etmek ve tehditlere karşı mücadele etmek için zengin görünürlük, veri seyahati üzerinde denetim ve gelişmiş analiz sağlar.

Bulut Uygulamaları için Defender, önde gelen Microsoft çözümleriyle yerel olarak tümleştirilmiştir ve güvenlik uzmanlarının göz göre göre tasarlanmıştır. Basit dağıtım, merkezi yönetim ve yenilikçi otomasyon özellikleri sağlar.

Bulut Uygulamaları için Defender çerçevesi, anızı siber tehditlere ve bilgisayarlara karşı koruma özelliği içerir; fidye yazılımlarını, güvenliği tehlikeye atılmış kullanıcıları veya bazı uygulama uygulamalarını belirlemek için bulut uygulamaları genelinde alışılmışın dışında bir davranış algılar. Yüksek riskli kullanımın analiz edini sağlar ve otomatik olarak düzeltmek ve riski organizasyonum ile sınırlandırmanızı sağlar.

Bulut Uygulamaları için Defender uyarıları şöyle sınıflandırılabilir: 

- Onaylandı kötü amaçlı etkinlikler için TP. 
- Bir test veya diğer yetkili şüpheli eylem gibi şüpheli ama kötü amaçlı olmayan etkinlikler için gerçek pozitif (B-TP). 
- Kötü amaçlı olmayan onaylandı etkinlik için FP.

## <a name="alert-grading-playbooks"></a>Playbooks'a not verme uyarısı

Aşağıdaki tehditlere karşı uyarıları daha hızlı şekilde puanlayacak adımlar için bu playbooks'lara bakın:

- [Şüpheli e-posta iletme etkinliği](alert-grading-playbook-email-forwarding.md)
- [Şüpheli gelen kutusu işleme kuralları](alert-grading-playbook-inbox-manipulation-rules.md)
- [Şüpheli gelen kutusu iletme kuralları](alert-grading-playbook-inbox-forwarding-rules.md)

Güvenlik [portalında uyarıları](investigate-alerts.md) inceleme hakkında bilgi için bkz. Microsoft 365 Defender.
