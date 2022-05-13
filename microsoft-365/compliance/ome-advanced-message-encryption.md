---
title: Gelişmiş İleti Şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Gelişmiş İleti Şifrelemesi, yöneticilerin korumalı iletilerle daha da fazlasını yapmalarını sağlayarak kuruluşların uyumluluk yükümlülüklerini karşılamasına yardımcı olur.
ms.openlocfilehash: 077a17921c456ddff30e7490611dd4e78aaa5232
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393296"
---
# <a name="advanced-message-encryption"></a>Gelişmiş İleti Şifrelemesi

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Gelişmiş İleti Şifrelemesi [Microsoft 365 Kurumsal E5, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home), Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması), Office 365 Kurumsal E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması), ve A5 Office 365 Eğitim. Kuruluşunuzun Microsoft Purview Gelişmiş İleti Şifrelemesi içermeyen bir aboneliği varsa, Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için Microsoft 365 E5 Uyumluluk SKU eklentisiyle veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması), Office 365 SKU'ları veya Microsoft 365 E5/A5 Information Protection için Office 365 Gelişmiş Uyumluluk SKU eklentisi  ve Microsoft 365 A3/E3 için İdare SKU eklentisi.

Gelişmiş İleti Şifrelemesi, müşterilerin dış alıcılar ve şifrelenmiş e-postalara erişimleri üzerinde daha esnek denetimler gerektiren uyumluluk yükümlülüklerini karşılamasına yardımcı olur. Office 365 Gelişmiş İleti Şifrelemesi ile, otomatik ilkelerle kuruluş dışında paylaşılan hassas e-postaları denetleyebilir ve şifrelenmiş ileti portalı erişim günlükleri aracılığıyla bu etkinlikleri izleyebilirsiniz. Bu ilkeleri PII, Finansal veya Sistem Durumu Kimlikleri gibi hassas bilgi türlerini tanımlamak için yapılandırabilir veya korumayı geliştirmek için anahtar sözcükleri kullanabilirsiniz. İlkeleri yapılandırdıktan sonra, ilkeleri özel markalı e-posta şablonlarıyla eşleştirip ilkeye uyan e-postaların ek denetimi için bir sona erme tarihi eklersiniz. Ayrıca yöneticiler, istedikleri zaman posta erişimini iptal ederek güvenli bir web portalı aracılığıyla dışarıdan erişilen şifrelenmiş e-postaları daha fazla denetleyebiliyor.

Yalnızca dış alıcılara gönderilen e-postaları iptal edebilir ve son kullanma tarihi ayarlayabilirsiniz.

## <a name="get-started-with-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifrelemesi ile Kullanmaya başlayın

Aşağıdaki makalelerde Gelişmiş İleti Şifrelemesi'ni nasıl ayarlayıp kullandığınız açıklanmaktadır.

Kuruluşunuzun Microsoft Purview Gelişmiş İleti Şifrelemesi içeren bir aboneliği olmalıdır. Desteklenen abonelikler hakkında ayrıntılı bilgi için [İleti ilkesi ve uyumluluk hizmeti açıklamasına](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance) bakın.

henüz Office 365 İleti Şifrelemesi'ni ayarlamadıysanız bkz. [Yeni Office 365 İleti Şifrelemesi özelliklerini ayarlama](set-up-new-message-encryption-capabilities.md).

Gelişmiş İleti Şifrelemesi ile tek bir marka şablonuyla sınırlı değilsiniz. Bunun yerine, birden çok marka şablonu oluşturabilir ve kullanabilirsiniz. Özel marka ekleme, şifrelenmiş iletilerin iptalini izlemeyi etkinleştirmenize de olanak tanır. Bilgi için bkz. [Şifrelenmiş iletilerinize kuruluşunuzun markasını ekleme](add-your-organization-brand-to-encrypted-messages.md). Özel markalama kullandığınızda, dış alıcılar OME portalının bağlantısını içeren bir bildirim e-postası alır. Posta akışı kuralı, bildirim e-postasının ve OME Portalı'nın hangi marka şablonunu kullandığını belirler. Bu şekilde, güvenli içeriğiniz kuruluşunuzun dışına gönderilmez.

İletileri iptal edebilir ve kullanıcıların portaldan aldığı iletilere son kullanma tarihleri uygulayabilirsiniz. Başka bir deyişle, özel markalama şablonu uygulanmış e-posta. Daha fazla bilgi ve örnek için [, Tüm dış alıcıların şifrelenmiş postaları okumak için OME Portalını kullanmasını sağlama altındaki yönergelere](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail) bakın.

[Microsoft Purview Gelişmiş İleti Şifrelemesi ile şifrelenen e-posta için bir sona erme tarihi ayarlayın](ome-advanced-expiration.md). Güvenli bir web portalından şifrelenmiş e-postalara erişimin süresi dolarak korumayı geliştiren otomatik ilkelerle kuruluş dışında paylaşılan hassas e-postaları denetleyin.

[Gelişmiş İleti Şifrelemesi Microsoft Purview tarafından şifrelenen e-postayı iptal edin](revoke-ome-encrypted-mail.md). Kuruluş dışında paylaşılan hassas e-postaları denetleyin ve güvenli bir web portalı üzerinden şifrelenmiş e-postalara erişimi iptal ederek korumayı geliştirin.

[Gelişmiş İleti Şifrelemesi Microsoft Purview tarafından şifrelenmiş ileti portalı etkinlik günlüğü](ome-message-access-logs.md). Şifrelenmiş ileti portalında kuruluş dışında paylaşılan hassas e-postaları izleyin.
