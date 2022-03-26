---
title: Microsoft 365'daki öncelik hesapları için güvenlik önerileri, öncelik hesapları, Office 365'te öncelik hesapları, Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-protecthve
ms.custom: ''
description: Yöneticiler, güvenlik ayarlarını yükseltmeyi ve kendi kuruluşlarında öncelik hesapları için raporları, uyarıları ve soruşturmaları kullanmayı Microsoft 365 öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f27e146df680b36c117816f0a07e45e0345c647a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63675426"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Microsoft 365'de öncelik hesapları için güvenlik Microsoft 365

Tüm kullanıcı hesaplarının aynı şirket bilgilerine erişimi olmaz. Bazı hesapların mali veriler, ürün geliştirme bilgileri, kritik derleme sistemlerine iş ortağı erişimi gibi hassas bilgilere erişimi vardır. Gizliliği tehlikeye atılmışsa, çok gizli bilgilere erişimi olan hesaplar önemli bir tehdit oluşturuyor. Bu tür hesaplar öncelik hesapları _olarak çağrılıyor_. Öncelik hesapları CEOS, CISOs, CFO'lar, altyapı yönetici hesapları, yapı sistem hesapları ve daha fazlasını içerir (ancak bunlarla sınırlı değildir).

Saldırganlar için, sıradan veya bilinmeyen kullanıcılar için rastgele bir net kullanan sıradan kimlik avı saldırıları verimsizdir. Öte yandan, hedef öncelik _hesaplarının hedef olduğu_ kimlik avı veya _whaling_ saldırıları saldırganlar için çok ödüllendiricidir. Dolayısıyla, öncelik hesapları, hesap güvenliğini engellemeye yardımcı olmak için sıradan korumadan daha güçlü bir koruma gerektirir.

Microsoft 365 için Microsoft Defender Office 365, öncelik hesaplarınız için ek güvenlik katmanları sağlayan bazı önemli özellikler içerir. Bu makalede bu özellikler ve bunların nasıl kullanımı açıklanmıştır.

![Simge formundaki güvenlik önerilerinin özeti.](../../media/security-recommendations-for-priority-users.png)

|Görev|Tüm Office 365 Kurumsal planları|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Öncelik hesapları için oturum açma güvenliğini artırma](#increase-sign-in-security-for-priority-accounts)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Öncelik hesapları için kesin önceden belirlenmiş güvenlik ilkelerini kullanma](#use-strict-preset-security-policies-for-priority-accounts)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Öncelik hesaplarına kullanıcı etiketleri uygulama](#apply-user-tags-to-priority-accounts)|||![Dahil](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Uyarılarda, raporlarda ve algılamalarda öncelik hesaplarını izleme](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Dahil](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Kullanıcıları eğitin](#train-users)|![Dahil.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dahil](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

> [!NOTE]
> Ayrıcalıklı hesapların ( _yönetici hesapları_ ) güvenliğini sağlama hakkında bilgi için bu [konuya bakın](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="increase-sign-in-security-for-priority-accounts"></a>Öncelik hesapları için oturum açma güvenliğini artırma

Öncelik hesapları için daha fazla oturum açma güvenliği gerekir. Çok faktörlü kimlik doğrulamasını (MFA) gerektirerek ve eski kimlik doğrulama protokollerini devre dışı bırakarak oturum açma güvenliğini artırabilirsiniz.

Yönergeler için bkz [. 1. Adım. MFA ile uzak çalışanlar için oturum açma güvenliğini artırma](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Bu makale uzaktan çalışanlar hakkında olsa da, aynı kavramlar öncelikli kullanıcılar için de geçerlidir.

**Not**: Önceki makalede açıklandığı gibi tüm öncelikli kullanıcılar için eski kimlik doğrulama protokollerini genel olarak devre dışı bırakmanızı kesinlikle öneririz. İş gereksinimleriniz bunu yapmanızı engelle Exchange Online, eski kimlik doğrulama protokollerinin kapsamını sınırlamaya yardımcı olmak için aşağıdaki denetimleri sunar:

- belirli [kullanıcılar için,](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) Exchange Online'te kimlik doğrulama ilkelerini ve İstemci Erişim Kuralları'nu kullanarak POP3, IMAP4 ve kimliği doğrulanmış SMTP gibi temel kimlik doğrulama protokollerini engelleyebilir veya bu protokole izin veebilirsiniz.[](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

- Tek tek posta kutuları üzerinde POP3 ve IMAP4 erişimini devre dışı abilirsiniz. Kuruluş düzeyinde kimliği doğrulanmış SMTP'yi devre dışı bırakarak, yine de bunu gerektiren belirli posta kutularında etkinleştirebilirsiniz. Yönergeler için aşağıdaki makalelere bakın:
  - [Kullanıcı için POP3 veya IMAP4 erişimini etkinleştirme veya devre dışı bırakma](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Kimliği doğrulanmış istemci SMTP gönderimi (SMTP AUTH) etkinleştirme veya devre dışı bırakma](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Ayrıca, Temel kimlik doğrulamasının Exchange Web Hizmetleri (EWS), Exchange ActiveSync, POP3, IMAP4 ve uzak PowerShell için Exchange Online'te kullanımdandan kullanım dışıdır. Ayrıntılar için bu [blog gönderisi'ne bakın](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Öncelik hesapları için kesin önceden belirlenmiş güvenlik ilkelerini kullanma

Öncelikli kullanıcılar, Exchange Online Protection (EOP) ve Office 365 için Defender'da bulunan çeşitli korumalar için daha sıkı eylemler Office 365.

Örneğin, istenmeyen posta olarak sınıflandırılmış iletileri Gereksiz E-posta klasörüne teslim etmek yerine, öncelik hesaplarına yönelikse bu iletileri karantinaya alısınız.

Önceden ayarlanmış güvenlik ilkelerde Katı profilini kullanarak öncelik hesapları için bu sıkı yaklaşımı kullanabilirsiniz.

Önceden belirlenmiş güvenlik ilkeleri, EOP'de tüm korumalar için önerilen Katı ilke ayarlarımızı ve İlkeler için Defender'ı uygulamanın kullanışlı ve merkezi bir Office 365. Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).

Katı ilke ayarlarının varsayılan ve Standart ilke ayarlarından nasıl farklı olduğuyla ilgili ayrıntılar için bkz. EOP için önerilen ayarlar ve Güvenlik [için Microsoft Defender Office 365.](recommended-settings-for-eop-and-office365.md)

## <a name="apply-user-tags-to-priority-accounts"></a>Öncelik hesaplarına kullanıcı etiketleri uygulama

Office 365 Plan 2 için Microsoft Defender'daki kullanıcı etiketleri (Microsoft 365 E5 veya eklenti aboneliğinin bir parçası olarak), raporlarda ve olay araştırmalarında belirli kullanıcıları veya kullanıcı gruplarını hızla tanımlamanın ve sınıflandırmanın bir yoludur.

**Öncelik hesapları**, öncelik hesaplarını içeren olayları ve uyarıları tanımlamak için kullanabileceğiniz bir tür yerleşik kullanıcı etiketidir (sistem etiketi olarak bilinir). Öncelik hesapları hakkında daha **fazla bilgi için** bkz. [Öncelik hesaplarını yönetme ve izleme](../../admin/setup/priority-accounts.md).

Ayrıca, öncelik hesaplarınızı daha fazla tanımlamak ve sınıflandırmak için özel etiketler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md). Öncelik hesaplarını **(sistem etiketleri** ) özel kullanıcı etiketleriyle aynı arabirimde yönetebilirsiniz.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Uyarılarda, raporlarda ve algılamalarda öncelik hesaplarını izleme

Öncelik kullanıcılarınızı güvenlik altına alındıktan ve etiketledikten sonra, öncelik hesaplarını içeren olayları veya algılamaları hızla tanımlamak üzere EOP ve Office 365 için Defender'daki kullanılabilir raporları, uyarıları ve soruşturmaları kullanabilirsiniz. Kullanıcı etiketlerini destekleyen özellikler aşağıdaki tabloda açıklanmıştır.

|Özellik|Açıklama|
|---|---|
|Uyarılar|Etkilenen kullanıcıların kullanıcı etiketleri, kullanıcı portalında Uyarılar sayfasında görünür ve Microsoft 365 Defender kullanılabilir. Daha fazla bilgi için bkz [. Uyarıları görüntüleme](../../compliance/alert-policies.md#viewing-alerts).|
|Explorer <p> Gerçek zamanlı algılamalar|**Gezgin'de** (Office 365 Plan 2 için Defender) veya Gerçek zamanlı algılamalar (Office 365 Plan 1 için Defender), kullanıcı etiketleri **E-posta kılavuz görünümünde ve E-posta** ayrıntıları uçarak çıkışta görünür. Kullanıcı etiketleri de filtrelenebilir özellik olarak kullanılabilir. Daha fazla bilgi için bkz.  [Explorer'daki Etiketler](threat-explorer.md#tags-in-threat-explorer).|
|Kampanya Görünümleri|Kullanıcı etiketleri, Plan 2'de yer alan Microsoft Defender'daki Kampanya Görünümleri'Office 365 özelliklerdendir. Daha fazla bilgi için bkz. [Kampanya Görünümleri](campaigns.md).|
|Tehdit koruması durum raporu|Tehdit koruması durum raporudaki görünümlerin ve ayrıntı tablolarının neredeyse tümsinde **, sonuçları** öncelik hesaplarına **göre filtrelendirebilirsiniz**. Daha fazla bilgi için tehdit [koruması durum raporuna bakın](view-email-security-reports.md#threat-protection-status-report).|
|Öncelik hesapları raporu için e-posta sorunları|**Exchange yönetim** merkezinde (EAC) öncelik hesapları için e-posta sorunları raporu, öncelik hesapları için teslim edilmeyen ve geciktirilen iletiler hakkında **bilgi içerir**. Daha fazla bilgi için bkz [. Öncelik hesapları raporu için e-posta sorunları](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|

## <a name="train-users"></a>Kullanıcıları eğitin

Öncelik hesapları olan eğitim kullanıcıları, bu kullanıcıları ve güvenlik işlemleri ekibinizi çok zaman ve sıkıntılı bir şekilde kaydetmeye yardımcı olabilir. Meraklı kullanıcıların ekleri açma veya şüpheli e-posta iletilerinden bağlantılara tıklama olasılığı daha düşük ve şüpheli web sitelerinden kaçınma olasılığı daha düşük olur.

Harvard Harvard School [Cybersecurity Campaign El](https://www.belfercenter.org/CyberPlaybook) Kitabı, kullanıcıları kimlik avı saldırılarını belirlemeye yönelik eğitim de dahil olmak üzere, organizasyonu dahilinde güvenlik farkındalığı kültürü oluşturmak için mükemmel rehberlik sağlar.

Microsoft 365, kullanıcıları bilgilendirmeye yardımcı olmak için aşağıdaki kaynakları sağlar:

|Kavram|Kaynaklar|Açıklama|
|---|---|---|
|Microsoft 365|[Özelleştirilebilir öğrenme yolları](/office365/customlearning/)|Bu kaynaklar, kurumda kullanıcılar için bir eğitim bir araya çalışmanıza yardımcı olabilir.|
|Microsoft 365 güvenliği|[Learning: Yerleşik ve akıllı güvenlik ile kuruluş güvenliğinizi Microsoft 365](/learn/modules/security-with-microsoft-365)|Bu modül, güvenlik özelliklerinin Microsoft 365 birlikte nasıl olduğunu açıklamaya ve bu güvenlik özelliklerinin avantajlarını açıklamaya olanak sağlar.|
|Çok faktörlü kimlik doğrulaması|[İki aşamalı doğrulama: Ek doğrulama sayfası nedir?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Bu makale, son kullanıcıların çok faktörlü kimlik doğrulamasının ne olduğunu ve bu kimlik doğrulamanın neden kuruluşta kullanılıyor olduğunu anlıyoruz.|
|Saldırı benzetimi eğitimi|[Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md)|Plan 2 için Microsoft Defender'daki saldırı benzetimi eğitimi Office 365 yöneticinin belirli kullanıcı gruplarına karşı sanal kimlik avı saldırılarını yapılandırmasını, başlatmasını ve izlemesini sağlar.|

Microsoft ayrıca, kullanıcıların bu makalede açıklanan eylemleri uygulamalarını önermektedir: Hesaplarınızı ve cihazlarınızı bilgisayar korsanlarından ve kötü amaçlı [yazılımdan koruyun](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Bu eylemler şunlardır:

- Güçlü parolalar kullanma
- Cihazları koruma
- Mac bilgisayarlarda ve Windows özelliklerini etkinleştirme (unmanaged cihazlar için)

## <a name="see-also"></a>Ayrıca bkz.

[Office 365 için Microsoft Defender'da Öncelik Hesap Koruması'Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
