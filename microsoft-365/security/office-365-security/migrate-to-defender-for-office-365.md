---
title: Üçüncü taraf koruma hizmetinden Office 365 için Microsoft Defender geçiş
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Google Postini, Barracuda İstenmeyen Posta ve Virüs Güvenlik Duvarı veya Cisco IronPort gibi üçüncü taraf koruma hizmetlerinden veya cihazlardan Office 365 için Microsoft Defender korumaya geçiş yapmak için doğru yolu öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 87100c2faa071075b9658591dad821d240b60b84
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65284984"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Üçüncü taraf koruma hizmetinden veya cihazından Office 365 için Microsoft Defender geçiş

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

zaten Microsoft 365 önünde duran bir üçüncü taraf koruma hizmetiniz veya cihazınız varsa, birleştirilmiş bir yönetim deneyiminin avantajlarından, potansiyel olarak düşük maliyetlerden (zaten ödeme yaptığınız ürünleri kullanarak) ve tümleşik güvenlikle olgun bir üründen yararlanmak için korumanızı Office 365 için Microsoft Defender geçirmek için bu kılavuzu kullanabilirsiniz  Koruma. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Office 365 için Defender geçiş hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfH]

Bu kılavuz, geçişiniz için belirli ve eyleme dönüştürülebilir adımlar sağlar ve aşağıdaki olguları varsayar:

- Zaten Microsoft 365 posta kutunuz var, ancak şu anda e-posta koruması için üçüncü taraf bir hizmet veya cihaz kullanıyorsunuz. İnternet'ten gelen postalar, Microsoft 365 kuruluşunuza teslim etmeden önce koruma hizmeti üzerinden akar ve Microsoft 365 koruması mümkün olduğunca düşüktür (hiçbir zaman tamamen kapalı değildir; örneğin, kötü amaçlı yazılım koruması her zaman uygulanır).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="Posta, İnternet'ten üçüncü taraf koruma hizmeti veya cihazı aracılığıyla Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- Office 365 için Defender koruma için araştırma ve değerlendirme aşamasını aşıyorsunuz. Kuruluşunuz için uygun olup olmadığına karar vermek için Office 365 için Defender değerlendirmeniz gerekiyorsa, [Office 365 için Microsoft Defender Deneyin](try-microsoft-defender-for-office-365.md) bölümünde açıklanan seçenekleri göz önünde bulundurmanızı öneririz.

- Office 365 için Defender lisansları zaten satın almışsınızdır.

- Mevcut üçüncü taraf koruma hizmetinizi devre dışı bırakmanız gerekir, bu da sonuçta e-posta etki alanlarınızın MX kayıtlarının Microsoft 365 işaret etmeniz gerektiği anlamına gelir. İşiniz bittiğinde, İnternet'ten gelen postalar doğrudan Microsoft 365 akacak ve yalnızca Exchange Online Protection (EOP) ve Office 365 için Defender tarafından korunacaktır.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="Posta İnternet'ten Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

Mevcut koruma hizmetinizi Office 365 için Defender lehine ortadan kaldırmak, hafife almamanız ve değişikliği yapmak için acele etmemeniz gereken büyük bir adımdır. Bu geçiş kılavuzundaki kılavuz, kullanıcılarınızın en az kesintiye uğraması durumunda korumanızı düzenli bir şekilde geçirmenize yardımcı olur.

Çok üst düzey geçiş adımları aşağıdaki diyagramda gösterilmiştir. Gerçek adımlar, bu makalenin devamında [Geçiş işlemi](#the-migration-process) adlı bölümde listelenmiştir.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="Üçüncü taraf koruma çözümünden veya cihazından Office 365 için Defender geçiş işlemi" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>Bu kılavuzdaki adımları neden kullanmalısınız?

BT sektöründe sürprizler genellikle kötü olur. MX kayıtlarınızı önceden ve düşünceli test yapmadan Microsoft 365 işaret edecek şekilde çevirmek birçok sürprize neden olur. Örneğin:

- Siz veya öncülleriniz büyük olasılıkla en iyi posta teslimi için mevcut koruma hizmetinizi özelleştirmek için çok zaman ve çaba harcamışsınızdır (başka bir deyişle, engellenmesi gerekenleri engelleme ve izin verilmesi gereken şeylere izin verme). Geçerli koruma hizmetinizdeki her özelleştirmenin Office 365 için Defender gerekmediği neredeyse garanti edilir. Ayrıca Office 365 için Defender, geçerli koruma hizmetinizde gerçekleşmemiş veya gerekli olmayan yeni sorunlar (izinler veya bloklar) ortaya çıkacaktır.
- Yardım masanızın ve güvenlik personelinizin Office 365 için Defender ne yapacağını bilmesi gerekir. Örneğin, bir kullanıcı eksik bir iletiden şikayet ederse yardım masanız bu iletiyi nerede veya nasıl arayabileceğinizi biliyor mu? Mevcut koruma hizmetinizdeki araçları biliyor olabilirler ama Office 365 için Defender araçları ne olacak?

Buna karşılık, bu geçiş kılavuzundaki adımları izlerseniz, geçişiniz için aşağıdaki somut avantajları elde edersiniz:

- Kullanıcılar için minimum kesinti.
- yönetime geçişin ilerleme durumunu ve başarısını rapor ederken kullanabileceğiniz hedef veriler Office 365 için Defender.
- Yardım masası ve güvenlik personeli için erken katılım ve talimat.

Office 365 için Defender kuruluşunuzu nasıl etkileyeceğini ne kadar iyi bilirseniz, kullanıcılar, yardım masası personeli, güvenlik personeli ve yönetim için geçiş o kadar iyi olur.

Bu geçiş kılavuzu, karşılaştığınız sorunlara hızla yanıt vermek için Office 365 için Defender kullanıcılarınızı ve e-postalarını nasıl etkilediğini izleyip test edebilmeniz için aşamalı olarak "aramayı çevirme" planı sunar.

## <a name="the-migration-process"></a>Geçiş işlemi

Üçüncü taraf koruma hizmetinden Office 365 için Defender geçiş işlemi, aşağıdaki tabloda açıklandığı gibi üç aşamaya ayrılabilir:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="Office 365 için Defender geçiş işlemi" lightbox="../../media/phase-diagrams/migration-phases.png":::

|Aşama|Açıklama|
|---|---|
|[Geçişiniz için hazırlanma](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Mevcut koruma hizmetinizdeki ayarların envanterini oluşturun](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Microsoft 365'de mevcut koruma yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Posta yönlendirme yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[İletileri değiştiren özellikleri Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[İstenmeyen posta ve toplu kullanıcı deneyimlerini tanımlama](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Öncelik hesaplarını belirleme ve belirleme](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Office 365 için Defender ayarlama](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Pilot kullanıcılar için dağıtım grupları oluşturma](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Kullanıcı ileti raporlaması için kullanıcı gönderimini yapılandırma](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[SCL=-1 posta akışı kuralını koruma veya oluşturma](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Bağlayıcılar için Gelişmiş Filtrelemeyi Yapılandırma](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Pilot koruma ilkeleri oluşturma](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Office 365 için Defender ekleme](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Güvenlik Teams eklemeye başlama](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(İsteğe bağlı) Pilot kullanıcıların mevcut koruma hizmetinize göre filtrelemesini muaf tutma](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Sahte zekayı ayarlama](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Kimliğe bürünme koruması ve posta kutusu zekasını ayarlama](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Ölçmek ve ayarlamak için kullanıcı gönderimlerindeki verileri kullanma](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(İsteğe bağlı) Pilotunuza daha fazla kullanıcı ekleme ve yineleme](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[Microsoft 365 korumasını tüm kullanıcılara genişletme ve SCL=-1 posta akışı kuralını kapatma](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[MX kayıtlarınızı değiştirme](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Sonraki adım

- 1. [Aşama: Hazırlama'ya](migrate-to-defender-for-office-365-prepare.md) geçin.
