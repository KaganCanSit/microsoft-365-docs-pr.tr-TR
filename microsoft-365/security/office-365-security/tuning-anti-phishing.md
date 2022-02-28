---
title: Kimlik avı korumasını ayarlama
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
description: Yöneticiler, kimlik avı iletilerinin neden ve nasıl ilerler yaptığını Microsoft 365, gelecekte daha fazla kimlik avı iletisine neden olan iletileri önlemek için neleri yapacaklarını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 299488a7ed8a891d870efb3ace618178c36552f1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988608"
---
# <a name="tune-anti-phishing-protection"></a>Kimlik avı korumasını ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu Microsoft 365 varsayılan olarak etkinleştirilen çeşitli kimlik avı önleme özellikleriyle birlikte gelir, ancak bazı kimlik avı iletileri posta kutularınıza yine de etkinleştirilmiş olabilir. Bu konu başlığında, kimlik avı iletisiyle ilgili bir iletinin neden iletide yer yaptığını keşfetmek için neler yapabilirsiniz ve Microsoft 365 yanlışlıkla işleri kötüye hale göndermeden, Microsoft 365 koruma ayarlarını değiştirmek için neler _yapabilirsiniz_.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Her şey ilk olarak, güvenliği tehlikeye atılmış hesaplarla ilgilenin ve daha fazla kimlik avı iletilerinin engellemeye devam

Kimlik avı iletisi sonucunda alıcının hesabı tehlikeye atılmışsa, Kimlik avı iletisinde güvenliği tehlikeye atılmış bir e-posta hesabını [Microsoft 365](responding-to-a-compromised-email-account.md).

Aboneliğiniz Microsoft Defender for Office 365'ı da dahil ediyorsa, [kimlik avı Office 365](office-365-ti.md) diğer kullanıcıları belirlemek için Tehdit Zekası'Office 365 kullanabilirsiniz. Kimlik avı iletilerini engellemek için ek seçenekleriniz vardır:

- [Kasa için Microsoft Defender'daki Office 365](set-up-safe-links-policies.md)

- [Kasa için Microsoft Defender'daki Ekleri Office 365](set-up-safe-attachments-policies.md)

- [Kimlik avı için Microsoft Defender'da kimlik avı Office 365](configure-mdo-anti-phishing-policies.md). Gelişmiş kimlik avı eşiklerini standarttan Agresif, Daha saldırgan veya En saldırgan ilkeye geçici  olarak **artıry defterine getirebilirsiniz**.

Yeni uygulama için bu Office 365 Defender'ın açık olduğunu doğrulayın.

## <a name="report-the-phishing-message-to-microsoft"></a>Kimlik avı iletisi Microsoft'a bildirme

Kimlik avı iletilerini raporlamak, aynı anda tüm müşterileri korumak için kullanılan filtreleri ayarlama Microsoft 365. Yönergeler için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>İleti üst bilgilerini denetleme

Daha fazla kimlik avı iletisine neden olan sorunlardan korunmak için, kimlik avı iletisi için bir şeyler olup olmadığını görmek üzere kimlik avı iletisi üst bilgilerini inceebilirsiniz. Başka bir deyişle, ileti üst bilgilerini incelemeniz, kimlik avı iletilerine izin veren kuruluşta yer alan tüm ayarları tanımlamanıza yardımcı olabilir.

Özellikle, İleti üst bilgisinde İstenmeyen Posta Filtreleme Kararının (SFV) istenmeyen posta veya kimlik avı için atlanan filtrelemeyle ilgili göstergeler için **X-Forefront-Antispam-Report** üst bilgi alanını denetlemeniz gerekir. Filtrelemeyi atlayıp `SCL:-1`atlamayı tercih edilen iletilerin bir girdisi olur; başka bir ifadeyle, hizmet tarafından belirlenen istenmeyen posta veya kimlik avı kararlarını geçersiz kılınarak bu iletiye izin verilir. İleti üstbilgilerini ve kullanılabilir tüm istenmeyen posta önleme ve kimlik avı önleme ileti üst bilgilerini içeren tam liste hakkında daha fazla bilgi için bkz. Microsoft 365'de İstenmeyen posta önleme [ileti üst bilgileri](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Korunmak için en iyi yöntemler

- Aylık olarak, güvenli puanı [çalıştırarak](../defender/microsoft-secure-score.md) kuruluş güvenlik ayarlarını değerlendirin.

- Yanlışlıkla karantinaya alınan veya izin verilen iletiler için, bu iletileri Tehdit Gezgini'nde ve gerçek zamanlı algılamalarda [aramanızı öneririz](threat-explorer.md). Gönderene, alıcıya veya ileti kimliğine göre aramaabilirsiniz. İletiyi bu gönderdikten sonra, konuya tıklayarak ayrıntılara gidin. Karantinaya alınmış bir ileti için, "algılama teknolojisi"nin ne olduğunu bakın; böylece geçersiz kılmak için uygun yöntemi kullanabilirsiniz. İzin verilen bir ileti için, iletiye izin verilen ilkeyi görmek için bakın.

- Sahte adresli gönderenlerden gelen e-postalar (iletinin Gönderen adresi iletinin kaynağıyla eşleşmez) Office 365 için Defender'da kimlik avı olarak sınıflandırılır. Bazen de kimliği doğru olan bir iletidir ve bazen kullanıcılar kimliği doğruya alınmış belirli bir gönderenden gelen iletilerin karantinaya alınmasını istemez. Kullanıcılar üzerindeki etkiyi en aza indirmek için, bilgi oturum açma bilgileri içgörüsini [, Kiracı](learn-about-spoof-intelligence.md) İzin Ver [/](tenant-allow-block-list.md)Engelleme Listesi'nin **Spoof** sekmesi ve Oturum Açma algılamaları raporunu düzenli [aralıklarla gözden geçirebilirsiniz](view-email-security-reports.md#spoof-detections-report). İzin verilen ve kimlik sahtesi yapılmış gönderenleri gözden geçirerek gerekli geçersiz kılmaları bir kez yaptıktan sonra, kimlik avı ilkeleri içinde kimlik avı önleme ilkeleri içinde şüpheli iletileri kullanıcının Gereksiz [E-posta](set-up-anti-phishing-policies.md#spoof-settings) klasörüne teslim etmek yerine karantinaya alma için yapılandırma konusunda güvenebilirsiniz.

- Sizin için Microsoft Defender'da Kimliğe Bürünme (etki alanı veya kullanıcı) için yukarıdaki adımı Office 365. Kimliğe Bürünme raporu Threat **Management** \> **Dashboard Analizler** \> **.**

- Tehdit Koruması Durumu raporunu [düzenli aralıklarla gözden geçirebilirsiniz](view-reports-for-mdo.md#threat-protection-status-report).

- Bazı müşteriler İstenmeyen posta önleme ilkelerinde Gönderene izin ver veya Etki alanına izin ver listesine kendi etki alanlarını koyarak kimlik avı iletilerine yanlışlıkla izin verir. Bu yapılandırma bazı yasal iletilere izin verse de, normalde istenmeyen posta ve/veya kimlik avı filtreleri tarafından engellenmiş kötü amaçlı iletilere de izin verecek. Etki alanına izin yerine, temel sorunu düzeltmeniz gerekir.

  Microsoft 365 (yanlış pozitif sonuçlar) tarafından engellenen ve etki alanınıza gönderenleri içeren geçerli iletilerle başa çıkarmanın en iyi yolu, tüm e-posta etki alanlarınız için DNS'deki SPF, DKIM ve DMARC kayıtlarını tam ve  tamamen yapılandırmaktır:

  - SPF kaydınızı, etki _alanınız_ içinde yer alan gönderenler için tüm e-posta kaynaklarını tanım doğrula (üçüncü taraf hizmetleri unutmayın!).

  - Yetkisiz gönderenlerin, bunu yapacak şekilde yapılandırılmış e-posta sistemleri tarafından reddedilirken emin olmak için başarısız olun (\-hepsi). Kimlik [bilgisi bilgi](learn-about-spoof-intelligence.md) içgörülerini kullanarak etki alanlarınızı kullanan gönderenleri tanımlayabilir ve böylelikle SPF kaydınıza yetkili üçüncü taraf gönderenleri dahil edinebilirsiniz.

  Yapılandırma yönergeleri için bkz:

  - [SPF'yi, sanallık engellemeye yardımcı olacak şekilde ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md)

  - [E-postayı doğrulamak için DMARC kullanma](use-dmarc-to-validate-email.md)

- Mümkün olduğunda, etki alanınız için e-postayı doğrudan e-posta adresinize Microsoft 365. Başka bir deyişle, Microsoft 365 etki alanının MX kaydını söz Microsoft 365. Exchange Online Protection (EOP), bulut kullanıcılarınız için posta doğrudan posta hizmetine teslim edilirken en iyi korumayı Microsoft 365. EOP'nin önünde üçüncü taraf bir e-posta sistemi kullanıyorsanız, Bağlayıcılar için Gelişmiş Filtreleme'i kullanın. Yönergeler için bkz. [Exchange Online'ta Bağlayıcılar için İyileştirilmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Kullanıcıların iletileri [Microsoft'a bildirmesi](enable-the-report-message-add-in.md) için Rapor İletisi [](enable-the-report-phish-add-in.md) eklentiini veya Kimlik Avını Bildir eklentilerini kullanmaları gerekir. Bu eklenti sistemimizi eğitebilirsiniz. Yöneticiler, Yönetici Gönderimi [yeteneklerine de sahip](admin-submission.md) olması gerekir.

- Multi factor authentication (MFA), güvenliği ihlal edilmiş hesapları önlemek için iyi bir yol sağlar. Tüm kullanıcılarınız için MFA'nın etkinleştirilmesini kesinlikle göz önünde bulundurabilirsiniz. Aşamalı bir yaklaşım için, MFA'yi herkes için etkinleştirmeden önce en hassas kullanıcılarınız (yöneticiler, yöneticiler vb.) için MFA'yi etkinleştirerek çalışmaya başlayabilirsiniz. Yönergeler için bkz [. Çok faktörlü kimlik doğrulamasını ayarlama](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Dış alıcılara iletme kuralları genellikle saldırganlar tarafından verileri ayıklamak için kullanılır. Dış **alıcılara iletme kurallarını bulmak ve hatta** engellemek için [Microsoft Güvenli Puanı'nın](../defender/microsoft-secure-score.md) Posta kutusu iletme kurallarını gözden geçir bilgilerini kullanın. Daha fazla bilgi için bkz [. Güvenli Puanla İstemci Dış Yönlendirme Kurallarını Azaltma](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
