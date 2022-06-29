---
title: Uç Nokta için Microsoft Defender diğer Microsoft çözümleriyle tümleştirme
description: Uç Nokta için Microsoft Defender Kimlik için Microsoft Defender ve Bulut için Microsoft Defender dahil olmak üzere diğer Microsoft çözümleriyle nasıl tümleştireceğinizi öğrenin.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, koşullu erişim, office, Uç Nokta için Microsoft Defender, kimlik için microsoft defender, Office için Microsoft Defender, Bulut için Microsoft Defender, microsoft bulut uygulaması güvenliği, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 24244fa9b0cbb9ed452c8b09b6a108055ac6f770
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489436"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Uç Nokta için Microsoft Defender ve diğer Microsoft çözümleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Diğer Microsoft çözümleriyle tümleştirme

Uç Nokta için Microsoft Defender çeşitli Microsoft çözümleriyle doğrudan tümleştirilir.

### <a name="microsoft-defender-for-cloud"></a>Bulut için Microsoft Defender

Uç Nokta için Microsoft Defender, Windows Sunucularında uç nokta algılama ve yanıt (EDR) özellikleri de dahil olmak üzere kapsamlı bir sunucu koruma çözümü sağlar.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Uç Nokta için Microsoft Defender bağlayıcısı, Uç Nokta için Microsoft Defender'dan Microsoft Sentinel'e uyarı akışı yapmanızı sağlar. Bu, kuruluşunuz genelindeki güvenlik olaylarını daha kapsamlı bir şekilde analiz etmenizi ve etkili ve anında yanıt için playbook'lar oluşturmanıza olanak tanır.

### <a name="azure-information-protection"></a>Azure Information Protection

Uç Nokta DLP özelliklerimiz, uç nokta cihazlarında depolanan hassas veriler için çözümler arasında daha fazla görünürlük ve tümleştirmeyi kolaylaştıran geliştirilmiş bir bulma ve koruma çözümü içerdiğinden Kısa süre önce Azure Information Protection tümleştirmesini kullanım dışı bırakılmıştır. Bu, aşağıdaki [blogda](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555) duyuruldu. Müşterilerin Uç Nokta DLP'sini kullanmaya geçmelerini öneririz.

### <a name="conditional-access"></a>Koşullu Erişim

Uç Nokta için Microsoft Defender dinamik cihaz risk puanı Koşullu Erişim değerlendirmesiyle tümleştirildiğinden, kaynaklara yalnızca güvenli cihazların erişimi olduğundan emin olur.

### <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

Microsoft Defender for Cloud Apps, desteklenmeyen bulut hizmetlerinin (gölge BT) tümünden kullanımı dahil olmak üzere bulut uygulaması kullanımına doğrudan görünürlük sağlamak için Uç Nokta için Microsoft Defender sinyallerinden yararlanıyor İzlenen cihazları Uç Nokta için Microsoft Defender.

### <a name="microsoft-defender-for-identity"></a>Kimlik için Microsoft Defender

Şüpheli etkinlikler, kullanıcı bağlamı altında çalışan işlemlerdir. Uç Nokta için Microsoft Defender ile Kimlik için Microsoft Defender arasındaki tümleştirme, etkinlikler ve kimlikler arasında siber güvenlik araştırması yapma esnekliği sağlar.

### <a name="microsoft-defender-for-office"></a>Office için Microsoft Defender

[Office 365 için Defender](/office365/securitycompliance/office-365-atp), Güvenli Bağlantılar, Güvenli Ekler, gelişmiş Kimlik Avı Önleme ve kimlik sahtekarlığı zekası özellikleri aracılığıyla kuruluşunuzu e-posta iletilerinde veya dosyalarda kötü amaçlı yazılımlardan korumaya yardımcı olur. Office 365 için Microsoft Defender ile Uç Nokta için Microsoft Defender arasındaki tümleştirme, güvenlik analistlerinin bir saldırının giriş noktasını araştırmak için yukarı akışa geçmelerini sağlar. Tehdit bilgileri paylaşımı aracılığıyla, saldırılar barındırılabilir ve engellenebilir.

> [!NOTE]
> Office 365 için Defender veriler son 30 gün içindeki olaylar için görüntülenir. Uyarılar için, Office 365 için Defender veriler ilk etkinlik zamanına göre görüntülenir. Bundan sonra veriler artık Office 365 için Defender'de kullanılamaz.

### <a name="skype-for-business"></a>Skype Kurumsal

Skype Kurumsal tümleştirmesi, analistlerin risk altında olabilecek bir kullanıcı veya cihaz sahibiyle portaldan basit bir düğme aracılığıyla iletişim kurması için bir yol sağlar.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Microsoft 365 Defender, Uç Nokta için Microsoft Defender ve çeşitli Microsoft güvenlik çözümleri ile gelişmiş saldırıları algılamak, önlemek, araştırmak ve otomatik olarak yanıtlamak için uç nokta, kimlik, e-posta ve uygulamalar arasında yerel olarak tümleşen birleşik bir ihlal öncesi ve sonrası kurumsal savunma paketi oluşturur.

[Microsoft 365 Defender hakkında daha fazla bilgi edinin](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>İlgili konular

- [Tümleştirmeyi ve diğer gelişmiş özellikleri yapılandırma](advanced-features.md)
- [Microsoft 365 Defender genel bakış](/microsoft-365/security/defender/microsoft-365-defender)
- [Microsoft 365 Defender’ı açın](/microsoft-365/security/defender/m365d-enable)
- [Koşullu Erişim ile kullanıcıları, verileri ve cihazları koruma](conditional-access.md)
