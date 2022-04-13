---
title: Adım 1. Güvenlik temel hatlarını yapılandırın
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, HumOR, gasp saldırısı, fidye yazılımı saldırısı, şifreleme, kriptoviroloji, sıfır güven
description: Microsoft 365 kaynaklarınızı fidye yazılımı saldırılarına karşı korumak için güvenlik temellerini kullanın.
ms.openlocfilehash: 925a64e1d7852aeed6f596e99b20dbff8b34d1be
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825112"
---
# <a name="step-1-configure-security-baselines"></a>Adım 1. Güvenlik temel hatlarını yapılandırın

Fidye yazılımı saldırganlarına karşı ilk adım olarak, aşağıdaki Microsoft tanımlı güvenlik temellerini yapılandırmanız gerekir:

- [Microsoft 365 güvenliği](#microsoft-365-security-baseline)
- [E-posta yönetimini Exchange](#exchange-email-management-baseline)
- [Windows cihazlar ve istemci yazılımı için ek temeller](#additional-baselines)

Bu temeller, saldırganlar tarafından iyi bilinen yapılandırma ayarlarını ve kurallarını içerir; bunların yokluğu hızla fark edilir ve yaygın olarak kötüye kullanılır.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 güvenlik temeli

İlk olarak [, Microsoft Güvenli Puanını](/microsoft-365/security/defender/microsoft-secure-score) kullanarak güvenlik duruşunuzu değerlendirin ve ölçün ve gerektiğinde geliştirmek için yönergeleri izleyin.

Ardından, şüpheli etkinlikleri ve savunmasız içeriği engellemeye yardımcı olmak için [saldırı yüzeyi azaltma kurallarını](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) kullanın. Bu kurallar şunları önlemeyi içerir:

- Tüm Office uygulamalarının alt işlemler oluşturması
- E-posta istemcisinden ve web postasından yürütülebilir içerik
- Bir yaygınlık, yaş veya güvenilir liste ölçütüne uymayan yürütülebilir dosyaların çalıştırılması
- Karartılmış olabilecek betiklerin yürütülmesi
- JavaScript veya VBScript'in indirilen yürütülebilir içeriği başlatması
- Uygulamaların yürütülebilir içerik oluşturmalarını Office
- Uygulamaların diğer işlemlere kod eklemesini Office
- alt işlemler oluşturmadan iletişim uygulamasını Office
- USB'den çalışan güvenilmeyen ve imzalanmamış işlemler
- Windows Yönetim Arabirimi (WMI) olay aboneliği aracılığıyla kalıcılık
- Windows yerel güvenlik yetkilisi alt sisteminden kimlik bilgisi çalma (lsass.exe)
- PSExec ve WMI komutlarından kaynaklanan işlem oluşturma işlemleri

## <a name="exchange-email-management-baseline"></a>Exchange e-posta yönetimi temeli

Şu Exchange e-posta temeli ayarlarıyla kiracınıza e-posta tabanlı bir saldırıdan ilk erişimi önlemeye yardımcı olun:

- [Microsoft Defender Virüsten Koruma e-posta taramasını](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus) etkinleştirin.
- Yeni tehditlere ve polimorfik değişkenlere karşı [gelişmiş kimlik avı koruması](/microsoft-365/security/office-365-security/anti-phishing-protection) ve kapsamı için Office 365 için Microsoft Defender kullanın.
- Sahte e-postaları, istenmeyen postaları ve kötü amaçlı yazılım içeren e-postaları engellediğinizden emin olmak için Office 365 e-posta filtreleme ayarlarınızı denetleyin. Yeni tehditlere ve polimorfik değişkenlere karşı gelişmiş kimlik avı koruması ve kapsamı için Office 365 için Defender kullanın. Yeni alınan tehdit bilgilerine yanıt olarak, [Office 365 için Defender tıklayarak bağlantıları yeniden](/microsoft-365/security/office-365-security/atp-safe-links) [denetleyecek ve teslim edilen postaları silecek](/microsoft-365/security/office-365-security/zero-hour-auto-purge) şekilde yapılandırın.
- [EOP ve Office 365 için Defender güvenliği için önerilen](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp) en son ayarları gözden geçirin ve güncelleştirin.
- Yeni alınan tehdit bilgilerine yanıt olarak, [Office 365 için Defender tıklayarak bağlantıları yeniden denetleyecek](/microsoft-365/security/office-365-security/set-up-safe-links-policies) ve teslim edilen postaları silecek şekilde yapılandırın.

## <a name="additional-baselines"></a>Ek temeller

Güvenlik [temellerini](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) uygulama:

- Microsoft Windows 11 veya 10
- Enterprise için Microsoft 365 Uygulamaları
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar ve değişiklik yönetimi üzerindeki etkisi

Saldırı yüzeyini azaltma kuralı için en iyi yöntem olarak, kuralın ağınızı nasıl etkileyebileceklerini değerlendirmek için Tehdit ve Güvenlik Açığı Yönetimi'da bu kural için güvenlik önerisini açın. Öneri ayrıntıları bölmesi, kullanıcı etkisini açıklar. Bu etkiyi, cihazlarınızın yüzde kaçının kullanıcı üretkenliğini olumsuz etkilemeden engelleme modunda etkinleştiren yeni bir ilkeyi kabul edebileceğini belirlemek için kullanabilirsiniz.

Ayrıca Exchange e-posta temel ayarları gelen e-postayı engelleyebilir ve e-postanın gönderilmesini veya e-posta içindeki bağlantıların tıklanmasını engelleyebilir. Çalışanlarınızı bu davranış ve bu önlemlerin alınma nedeni konusunda eğitin.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

Bu adımdan sonra kiracınız için fidye yazılımı koruması aşağıdadır.

![1. Adımdan sonra Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)

## <a name="next-step"></a>Sonraki adım

[![Microsoft 365 ile fidye yazılımı koruması için 2. Adım](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Microsoft 365 kiracınız için saldırı algılama ve yanıt özelliklerini dağıtmak için [2. Adımla](ransomware-protection-microsoft-365-attack-detection-response.md) devam edin.
