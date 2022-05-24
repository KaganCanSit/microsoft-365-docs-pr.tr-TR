---
title: Kimlik avından korumayı ayarlama
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- MET150
description: Yöneticiler, Microsoft 365'da kimlik avı iletisinin neden ve nasıl geçtiğini ve gelecekte daha fazla kimlik avı iletisini önlemek için yapılması gerekenleri belirlemeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7c39d3f4b3ee6fb98cadcd5518a81710402c1cb3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647765"
---
# <a name="tune-anti-phishing-protection"></a>Kimlik avından korumayı ayarlama

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365, varsayılan olarak etkinleştirilen çeşitli kimlik avı önleme özellikleriyle birlikte gelse de, bazı kimlik avı iletilerinin posta kutularınıza ulaşmış olması mümkündür. Bu konu başlığı altında, bir kimlik avı iletisinin neden geçtiğini keşfetmek için yapabilecekleriniz ve Microsoft 365 kuruluşunuzdaki kimlik avı önleme ayarlarını _yanlışlıkla kötü hale getirmeden_ ayarlamak için yapabilecekleriniz açıklanmaktadır.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Öncelikle güvenliği aşılmış hesaplarla ilgilenin ve diğer kimlik avı iletilerinin üzerinden geçmelerini engellediğinizden emin olun

Kimlik avı iletisi nedeniyle bir alıcının hesabının gizliliği tehlikeye girdiyse, [Microsoft 365'da güvenliği aşılmış bir e-posta hesabını yanıtlama'daki](responding-to-a-compromised-email-account.md) adımları izleyin.

Aboneliğinizde Office 365 için Microsoft Defender varsa, kimlik avı iletisini de alan diğer kullanıcıları belirlemek için [Office 365 Tehdit Bilgileri'ni](office-365-ti.md) kullanabilirsiniz. Kimlik avı iletilerini engellemek için ek seçenekleriniz vardır:

- [Office 365 için Microsoft Defender'da bağlantıları Kasa](set-up-safe-links-policies.md)

- [Office 365 için Microsoft Defender'da Ekleri Kasa](set-up-safe-attachments-policies.md)

- [Office 365 için Microsoft Defender kimlik avı önleme ilkeleri](configure-mdo-anti-phishing-policies.md). İlkedeki **Gelişmiş kimlik avı eşiklerini** **Standart,** **Daha agresif** veya **En agresif** olarak geçici olarak artırabileceğinizi unutmayın.

Bu Office 365 için Defender özelliklerinin açık olduğunu doğrulayın.

## <a name="report-the-phishing-message-to-microsoft"></a>Kimlik avı iletisini Microsoft'a bildirme

Kimlik avı iletilerini raporlamak, Microsoft 365'daki tüm müşterileri korumak için kullanılan filtrelerin ayarlanmasında yararlıdır. Yönergeler için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>İleti üst bilgilerini inceleme

Daha fazla kimlik avı iletisinin gelmesini önlemek için kendiniz yapabileceğiniz bir şey olup olmadığını görmek için kimlik avı iletisinin üst bilgilerini inceleyebilirsiniz. Başka bir deyişle, iletilerin üst bilgilerini incelemek, kuruluşunuzda kimlik avı iletilerine izin vermekle sorumlu olan tüm ayarları belirlemenize yardımcı olabilir.

Özellikle, İstenmeyen Posta Filtreleme Kararı (SFV) değerinde istenmeyen posta veya kimlik avı için atlanan filtrelemenin göstergeleri için ileti üst bilgilerindeki **X-Forefront-Antispam-Report** üst bilgi alanını denetlemeniz gerekir. Filtrelemeyi atlayan iletilerin girdisi `SCL:-1`olur. Bu, ayarlarınızdan birinin hizmet tarafından belirlenen istenmeyen posta veya kimlik avı kararlarını geçersiz kılarak bu iletiye izin verdiği anlamına gelir. İleti üst bilgilerini alma hakkında daha fazla bilgi ve tüm kullanılabilir istenmeyen posta önleme ve kimlik avı önleme ileti üst bilgilerinin tam listesi için bkz. [Microsoft 365'da istenmeyen posta önleme ileti üst bilgileri](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Korunmaya yönelik en iyi yöntemler

- Kuruluşunuzun güvenlik ayarlarını değerlendirmek için aylık olarak [Güvenli Puan'ı](../defender/microsoft-secure-score.md) çalıştırın.

- Yanlışlıkla karantinaya alınan iletiler veya izin verilen iletiler için [Tehdit Gezgini'nde ve gerçek zamanlı algılamalarda](threat-explorer.md) bu iletileri aramanızı öneririz. Gönderene, alıcıya veya ileti kimliğine göre arama yapabilirsiniz. İletiyi buldukktan sonra, konuya tıklayarak ayrıntılara gidin. Karantinaya alınmış bir ileti için, geçersiz kılmak için uygun yöntemi kullanabilmeniz için "algılama teknolojisinin" ne olduğuna bakın. İzin verilen bir ileti için, iletiye hangi ilkenin izin verdiğini görün.

- Sahte gönderenlerden gelen e-postalar (iletinin Kimden adresi iletinin kaynağıyla eşleşmiyor) Office 365 için Defender kimlik avı olarak sınıflandırılır. Bazen sahtekarlık zararsızdır ve bazen kullanıcılar sahte gönderenin belirli iletilerinin karantinaya alınmasına izin vermez. Kullanıcılar üzerindeki etkiyi en aza indirmek için kimlik [sahtekarı zekası içgörülerini](learn-about-spoof-intelligence.md), [Kiracı İzin Ver/Engelle Listesi'ndeki](tenant-allow-block-list.md) **Kimlik Sahtekarı** sekmesini ve [Kimlik Sahtekarı algılamaları raporunu düzenli aralıklarla](view-email-security-reports.md#spoof-detections-report) gözden geçirin. İzin verilen ve engellenen kimlik sahtekarlığı gönderenleri gözden geçirdikten ve gerekli geçersiz kılmaları yaptıktan sonra, kimlik [avı önleme ilkelerinde kimlik sahtekarlığı zekasını](set-up-anti-phishing-policies.md#spoof-settings) şüpheli iletileri kullanıcının Gereksiz E-posta klasörüne teslim etmek yerine **Karantinaya** almak üzere yapılandırabileceğinizden emin olabilirsiniz.

- Office 365 için Microsoft Defender'de Kimliğe Bürünme (etki alanı veya kullanıcı) için yukarıdaki adımı yineleyebilirsiniz. Kimliğe Bürünme raporu **Tehdit Yönetimi** \> **Panosu** \> **Analizler** altında bulunur.

- [Tehdit Koruması Durumu raporunu](view-reports-for-mdo.md#threat-protection-status-report) düzenli aralıklarla gözden geçirin.

- Bazı müşteriler istenmeyen posta önleme ilkelerinde kendi etki alanlarını Gönderene izin ver veya Etki alanına izin ver listesine koyarak kimlik avı iletilerine yanlışlıkla izin verir. Bu yapılandırma bazı meşru iletilere izin verecek olsa da, normalde istenmeyen posta ve/veya kimlik avı filtreleri tarafından engellenecek kötü amaçlı iletilere de izin verir. Etki alanına izin vermek yerine, temel alınan sorunu düzeltmeniz gerekir.

  Etki alanınızdaki gönderenleri içeren Microsoft 365 (hatalı pozitifler) tarafından engellenen meşru iletilerle başa çıkmanın en iyi yolu _, tüm_ e-posta etki alanlarınız için DNS'deki SPF, DKIM ve DMARC kayıtlarını tamamen ve tamamen yapılandırmaktır:

  - SPF kaydınızın etki alanınızdaki gönderenler için _tüm_ e-posta kaynaklarını tanımladığını doğrulayın (üçüncü taraf hizmetlerini unutmayın!).

  - Yetkisiz gönderenlerin bunu yapacak şekilde yapılandırılmış e-posta sistemleri tarafından reddedildiğinden emin olmak için sabit başarısız\- (tümü) kullanın. SPF kaydınıza yetkili üçüncü taraf gönderenleri dahil edebilmeniz için, etki alanınızı kullanan gönderenleri tanımlamaya yardımcı olması için kimlik sahtekarlık [bilgileri içgörülerini](learn-about-spoof-intelligence.md) kullanabilirsiniz.

  Yapılandırma yönergeleri için bkz:

  - [Kimlik sahtekarlığını önlemeye yardımcı olmak için SPF'yi ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM'yi kullanma](use-dkim-to-validate-outbound-email.md)

  - [E-postayı doğrulamak için DMARC kullanma](use-dmarc-to-validate-email.md)

- Mümkün olduğunda, etki alanınız için doğrudan Microsoft 365 e-posta göndermenizi öneririz. Başka bir deyişle, Microsoft 365 etki alanınızın MX kaydını Microsoft 365 işaret edin. Exchange Online Protection (EOP), postaları doğrudan Microsoft 365 teslim edildiğinde bulut kullanıcılarınız için en iyi korumayı sağlayabilir. EOP'nin önünde bir üçüncü taraf e-posta hijyen sistemi kullanmanız gerekiyorsa Bağlayıcılar için Gelişmiş Filtreleme'yi kullanın. Yönergeler için bkz. [Exchange Online'da Bağlayıcılar için Gelişmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Kullanıcılar, iletileri [Microsoft'a bildirmek için Rapor İletisi eklentisini](enable-the-report-message-add-in.md) veya [Rapor Kimlik Avı eklentisini](enable-the-report-phish-add-in.md) kullanmalıdır ve bu da sistemimizi eğitebilir. Yöneticiler ayrıca [Yönetici Gönderimi](admin-submission.md) özelliklerinden de yararlanmalıdır.

- Çok faktörlü kimlik doğrulaması (MFA), güvenliği aşılmış hesapları önlemenin iyi bir yoludur. Tüm kullanıcılarınız için MFA'yi etkinleştirmeyi kesinlikle göz önünde bulundurmalısınız. Aşamalı bir yaklaşım için, herkes için MFA'yı etkinleştirmeden önce en hassas kullanıcılarınız (yöneticiler, yöneticiler vb.) için MFA'yı etkinleştirerek başlayın. Yönergeler için bkz. [Çok faktörlü kimlik doğrulamasını ayarlama](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Dış alıcılara iletme kuralları genellikle saldırganlar tarafından verileri ayıklamak için kullanılır. Kuralların dış alıcılara iletilmesini bulmak ve hatta engellemek için [Microsoft Güvenli Puanı'nda](../defender/microsoft-secure-score.md) **Posta kutusu iletme kurallarını gözden geçirme** bilgilerini kullanın. Daha fazla bilgi için bkz. [Güvenli Puan ile İstemci Dış İletme Kurallarını Azaltma](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
