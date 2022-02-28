---
title: Üçüncü taraf koruma hizmetlerinden iş için Microsoft Defender'a Office 365
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
description: Google Postini, Barracuda Spam ve Virüs Güvenlik Duvarı veya Cisco IronPort gibi üçüncü taraf koruma hizmetlerinden veya cihazlarından Microsoft Defender'a geçiş için doğru Office 365 öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c80d9e6005b5f9f329164dbc4ba0ebfed6a05a1b
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "62990613"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Üçüncü taraf koruma hizmeti veya cihazından Microsoft Defender'a geçiş Office 365

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

Zaten Microsoft 365'in önünde bulunan bir üçüncü taraf koruma hizmetiniz veya cihazınız varsa, bu kılavuzu kullanarak birleştirilmiş bir yönetim deneyimi, potansiyel olarak azaltılmış maliyet (zaten ödemesini yapan ürünleri kullanarak) ve tümleşik güvenlik korumasına sahip olgun bir ürün elde etmek üzere korumanızı Office 365 için Microsoft Defender'a geçirebilirsiniz. Daha fazla bilgi için bkz. [Office için Microsoft Defender](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Bu kılavuz, geçiş işleminiz için belirli ve işlem gerçekleştirilebilir adımlar sağlar ve aşağıdaki olguları varsaymaktadır:

- Zaten posta Microsoft 365, ancak şu anda e-posta koruması için üçüncü taraf bir hizmet veya cihaz kullanıyorsanız. İnternet'den gelen postalar, Microsoft 365'a teslimden önce koruma hizmeti aracılığıyla akar ve Microsoft 365 koruması da mümkün olduğunca düşüktür (asla tamamen kapalı değildir; örneğin, kötü amaçlı yazılıma karşı koruma her zaman zorunludur).

  ![Posta akışları, üçüncü taraf koruma hizmeti veya cihazı üzerinden, teslim öncesinde İnternet'Microsoft 365.](../../media/mdo-migration-before.png)

- Defender'ın sizin için koruma için araştırma ve dikkate alınması gereken aşamayı Office 365. Sizin için doğru olup Office 365 karar vermek için Defender'ı değerlendirmeniz gerekirse Değerlendirme Modu'na karar [vermenizi öneririz](office-365-evaluation.md).

- Office 365 lisansı için Defender'ı Office 365 satın aldınız.

- Mevcut üçüncü taraf koruma hizmetinizi geri adanmanız gerekir, bu da sonuçta e-posta etki alanlarınızı içeren MX kayıtlarının artık kullanılabilir olduğunu Microsoft 365. İnternet üzerinden posta, postanızı doğrudan Microsoft 365'a akar ve Exchange Online Protection (EOP) ve Office 365 için Defender tarafından özel Office 365.

  ![Mevcut koruma hizmetiniz veya cihazlarınız ortadan kaldırılmış, dolayısıyla posta internetten Microsoft 365'a ve Microsoft Defender'dan Mobil Cihaz'a Office 365.](../../media/mdo-migration-after.png)

Mevcut koruma hizmetinizi Defender for Office 365'den çıkararak mevcut koruma hizmetinizi ortadan kaldırmak, hafif bir şekilde çalışmaması gereken büyük bir adımdır; değişikliği yapmaya da hazır olmasanız da. Bu geçiş kılavuzunda yer alan kılavuz, korumanızı kullanıcılarınıza en az kesintiyle, sırayla geçirmenize yardımcı olur.

Çok yüksek düzeyli geçiş adımları aşağıdaki diyagramda gösterildiği gibi. Asıl adımlar, bu makalenin sonraki [kısımlarında Geçiş işlemi](#the-migration-process) adlı bölümde listelenir.

![Üçüncü taraf koruma çözümünden veya cihazından üçüncü taraf için Defender'a Office 365.](../../media/mdo-migration-overview.png)

## <a name="why-use-the-steps-in-this-guide"></a>Neden bu kılavuzda yer alan adımları kullanın?

IT sektörünün sürprizleri genellikle kötü olur. Önceden iyi bir test yapmadan MX kayıtlarınızı Microsoft 365 yapmanız pek çok sürprizle sonuçlanmayacaktır. Örneğin:

- Siz veya öncülleriniz, büyük olasılıkla en uygun posta teslimi için var olan koruma hizmetinizi özelleştirmek için çok fazla zaman ve çaba harcadınız (başka bir deyişle, engellenmesi gerekenleri engellemek ve izin verilmeleri gerekenleri engellemek). Geçerli koruma hizmetinizin her özelleştirmesi için, bu hizmet için Defender'da herhangi bir özelleştirmenin gerekli Office 365. Ayrıca, Office 365 için Defender'ın geçerli koruma hizmetiniz içinde olmayan veya hiç gerekli olmayan yeni sorunlar (izinler veya engellemeler) ile karşınıza olması da mümkündür.
- Destek ekibi ve güvenlik personelinizin, destek ekibi için Defender'da ne Office 365. Örneğin, bir kullanıcı eksik bir iletiden şikayet edebilirse yardım masanız iletiyi nerede veya nasıl aramanız gerektir? Bunlar büyük olasılıkla var olan koruma hizmetinizin araçlarına aşinadır, peki ya sizin için Defender'daki Office 365?

Buna karşılık, bu geçiş kılavuzunda adımları takip edersiniz, geçiş işleminiz için aşağıdaki uygun olmayan avantajları elde edersiniz:

- Kullanıcılar için en düşük kesinti.
- Yönetime geçişin Office 365 ve başarı durumuna rapor etmek için kullanabileceğiniz, Defender'dan hedef veriler.
- Yardım masası ve güvenlik personeli için erken katılım ve yönerge.

Office 365 için Defender'ın organizasyonu nasıl etkileyeceğini ne kadar iyi biliyor olursunuz; geçiş kullanıcılar, yardım masası personeli, güvenlik personeli ve yönetim için o kadar iyi olur.

Bu geçiş kılavuzu, size aşamalı olarak "arama çevirme" planı sağlar. Böylece Office 365 için Defender'ın kullanıcılarınızı ve e-postalarını nasıl etkilediğini izleyebilir ve sınayabilirsiniz, böylece karşılaştığınız tüm sorunlarla hızlı bir şekilde ifade etmek için bu plan kullanılabilir.

## <a name="the-migration-process"></a>Geçiş işlemi

Aşağıdaki tabloda açıklandığı gibi, üçüncü taraf koruma hizmetlerinden üçüncü taraf koruma hizmetlerinden Office 365 Defender'a iki aşamaya ayrılabilirsiniz:

![Office 365 için Defender'a Office 365.](../../media/phase-diagrams/migration-phases.png)

<p>

****

|Aşama|Açıklama|
|---|---|
|[Geçişe hazırlanma](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Mevcut koruma hizmetinizin ayarlarının envanterini alın](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Microsoft 365'te mevcut koruma yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Posta yönlendirme yapılandırmanızı denetleme](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[İletileri farklı bir yere Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[İstenmeyen posta ve toplu kullanıcı deneyimlerini tanımlama](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Öncelik hesaplarını tanımlama ve belirleme](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Defender'ı Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Pilot kullanıcılar için dağıtım grupları oluşturma](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Kullanıcı iletisi raporlaması için kullanıcı gönderimi yapılandırma](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[SCL=-1 posta akış kuralını koruma veya oluşturma](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Bağlayıcılar için Geliştirilmiş Filtrelemeyi Yapılandırma](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Pilot koruma ilkeleri oluşturma](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Office 365 için Defender'a Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Güvenlik önlemlerini eklemeye Teams](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(İsteğe bağlı) Pilot kullanıcıların var olan koruma hizmetiniz tarafından filtre uygulamanın dışında tutulacak](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Akıllı ifadeyi ayarlama](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Kimliğe bürünme koruması ve posta kutusu zekası ayarlama](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Ölçmek ve ayarlamak için kullanıcı gönderimlerinden veri kullanma](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(İsteğe bağlı) Pilot uygulamanıza daha fazla kullanıcı ekleyin ve daha fazla kullanıcı ekleyin](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[SCL=Microsoft 365-1 posta akış kuralını tüm kullanıcılara genişletme ve kapatma](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[MX kayıtlarınızı değiştirme](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|
|

## <a name="next-step"></a>Sonraki adım

- Aşama [1: Hazırla'ya devam edin](migrate-to-defender-for-office-365-prepare.md).
