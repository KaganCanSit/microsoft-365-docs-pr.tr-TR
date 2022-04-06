---
title: Üçüncü taraf koruma hizmetlerinden posta hizmetine Office 365 için Microsoft Defender
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
description: Google Postini, Barracuda Spam ve Virüs Güvenlik Duvarı veya Cisco IronPort gibi üçüncü taraf koruma hizmetlerinden veya cihazlarından geçiş yapmak için doğru Office 365 için Microsoft Defender öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ba82621e76665ee94d2a182e777ad1d222ef8e56
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477049"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Üçüncü taraf koruma hizmetlerinden veya cihazından başka bir hizmete Office 365 için Microsoft Defender

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

Microsoft 365'in önünde bulunan bir üçüncü taraf koruma hizmetiniz veya cihazınız zaten varsa, bu kılavuzu kullanarak korumanızı Office 365 için Microsoft Defender'e geçirebilirsiniz. Bu kılavuzu kullanarak birleştirilmiş yönetim deneyimi, büyük olasılıkla daha düşük maliyet (ödemesini zaten ödemeniz gereken ürünleri kullanma) ve tümleşik güvenliği olan olgun bir ürün  korumasını sağlar. Daha fazla bilgi için bkz. [Office için Microsoft Defender](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Bu kılavuz, geçiş işleminiz için belirli ve işlem gerçekleştirilebilir adımlar sağlar ve aşağıdaki olguları varsaymaktadır:

- Zaten posta Microsoft 365, ancak şu anda e-posta koruması için üçüncü taraf bir hizmet veya cihaz kullanıyorsanız. İnternet'den gelen postalar, Microsoft 365'a teslimden önce koruma hizmeti aracılığıyla akar ve Microsoft 365 koruması da mümkün olduğunca düşüktür (asla tamamen kapalı değildir; örneğin, kötü amaçlı yazılıma karşı koruma her zaman zorunludur).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="Posta, üçüncü taraf koruma hizmeti veya cihazı aracılığıyla, teslimat öncesinde İnternet'Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- Sizin için inceleme ve koruma aşamasından daha ileri bir Office 365 için Defender. Değerlendirme değerlendirmeniz ve Office 365 için Defender doğru olup olmadığını karar vermek için Değerlendirme Modu'na karar [vermenizi öneririz](office-365-evaluation.md).

- Office 365 için Defender satın Office 365 için Defender var.

- Mevcut üçüncü taraf koruma hizmetinizi geri adanmanız gerekir, bu da sonuçta e-posta etki alanlarınızı içeren MX kayıtlarının artık kullanılabilir olduğunu Microsoft 365. İnternet üzerinden posta, postanızı doğrudan Microsoft 365'a akar ve Exchange Online Protection (EOP) ve başka bir Office 365 için Defender.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="Posta, İnternet'Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

Mevcut koruma hizmetinizi olumlu olarak Office 365 için Defender, hafif bir şekilde çalışmaması gereken büyük bir adımdır; değişikliği yapmaya hemen devam etmeyin. Bu geçiş kılavuzunda yer alan kılavuz, korumanızı kullanıcılarınıza en az kesintiyle, sırayla geçirmenize yardımcı olur.

Çok yüksek düzeyli geçiş adımları aşağıdaki diyagramda gösterildiği gibi. Asıl adımlar, bu makalenin sonraki [kısımlarında Geçiş işlemi](#the-migration-process) adlı bölümde listelenir.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="Üçüncü taraf koruma çözümünden veya cihazından başka bir cihaza geçiş Office 365 için Defender" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>Neden bu kılavuzda yer alan adımları kullanın?

IT sektörünün sürprizleri genellikle kötü olur. Önceden iyi bir test yapmadan MX kayıtlarınızı Microsoft 365 yapmanız pek çok sürprizle sonuçlanmayacaktır. Örneğin:

- Siz veya öncülleriniz, büyük olasılıkla en uygun posta teslimi için var olan koruma hizmetinizi özelleştirmek için çok fazla zaman ve çaba harcadınız (başka bir deyişle, engellenmesi gerekenleri engellemek ve izin verilmeleri gerekenleri engellemek). Geçerli koruma hizmetinizin her özelleştirmesini özelleştirmenin bu hizmette gerekli olmadığının neredeyse Office 365 için Defender. Ayrıca geçerli koruma hizmetinizin Office 365 için Defender olmayan veya hiç gerekli olmayan yeni sorunlar (izinler veya engellemeler) ile karşınıza çok olasıdır.
- Yardım masası ve güvenlik personelinizin çalışma masasındaki çalışanlara bu konuda Office 365 için Defender. Örneğin, bir kullanıcı eksik bir iletiden şikayet edebilirse yardım masanız iletiyi nerede veya nasıl aramanız gerektir? Bunlar büyük olasılıkla var olan koruma hizmetinizin araçlarına aşinadır, peki ya sizin Office 365 için Defender?

Buna karşılık, bu geçiş kılavuzunda adımları takip edersiniz, geçiş işleminiz için aşağıdaki uygun olmayan avantajları elde edersiniz:

- Kullanıcılar için en düşük kesinti.
- Hedef veriler Office 365 için Defender yönetime geçişin ilerleme durumuna ve başarı durumuna rapor olarak rapor etmek için kullanabileceğiniz hedef verileri.
- Yardım masası ve güvenlik personeli için erken katılım ve yönerge.

Geçişin kurumlarınızı nasıl etkileyeceğini Office 365 için Defender, geçiş süreci kullanıcılar, yardım masası personeli, güvenlik personeli ve yönetim için o kadar iyi olur.

Bu geçiş kılavuzu, Office 365 için Defender'in kullanıcılarınızı ve onların e-postalarını nasıl etkilediğini izleyebilir ve test etmek için aşamalı olarak "arama çevirme" planı sağlar ve böylece karşılaştığınız her sorunla hızlı bir şekilde tepki ve şekilde ifade etmek için bunu izleyebilir ve sınayabilirsiniz.

## <a name="the-migration-process"></a>Geçiş işlemi

Üçüncü taraf koruma hizmetlerinden üçüncü taraf koruma hizmetlerinden Office 365 için Defender aşağıdaki tabloda açıklandığı gibi üç aşamaya ayrılabilirsiniz:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="Office 365 için Defender'a Office 365 için Defender" lightbox="../../media/phase-diagrams/migration-phases.png":::

|Aşama|Açıklama|
|---|---|
|[Geçişe hazırlanma](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Mevcut koruma hizmetinizin ayarlarının envanterini alın](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Microsoft 365'te mevcut koruma yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Posta yönlendirme yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[İletileri farklı bir yere Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[İstenmeyen posta ve toplu kullanıcı deneyimlerini tanımlama](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Öncelik hesaplarını tanımlama ve belirleme](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Ayarlama Office 365 için Defender](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Pilot kullanıcılar için dağıtım grupları oluşturma](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Kullanıcı iletisi raporlaması için kullanıcı gönderimi yapılandırma](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[SCL=-1 posta akış kuralını koruma veya oluşturma](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Bağlayıcılar için Geliştirilmiş Filtrelemeyi Yapılandırma](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Pilot koruma ilkeleri oluşturma](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Office 365 için Defender'e Office 365 için Defender](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Güvenlik önlemlerini eklemeye Teams](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(İsteğe bağlı) Pilot kullanıcıların var olan koruma hizmetiniz tarafından filtre uygulamanın dışında tutulacak](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Akıllı ifadeyi ayarlama](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Kimliğe bürünme koruması ve posta kutusu zekası ayarlama](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Ölçmek ve ayarlamak için kullanıcı gönderimlerinden veri kullanma](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(İsteğe bağlı) Pilot uygulamanıza daha fazla kullanıcı ekleyin ve daha fazla kullanıcı ekleyin](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[SCL=Microsoft 365-1 posta akış kuralını tüm kullanıcılara genişletme ve kapatma](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[MX kayıtlarınızı değiştirme](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Sonraki adım

- Aşama [1: Hazırla'ya devam edin](migrate-to-defender-for-office-365-prepare.md).
