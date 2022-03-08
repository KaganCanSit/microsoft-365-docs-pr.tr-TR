---
title: Adım 1. Güvenlik taban çizgilerini yapılandırma
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
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: Önemli kaynaklarınızı fidye yazılımı saldırılarından Microsoft 365 için güvenlik taban çizgilerini kullanın.
ms.openlocfilehash: 22092994765e9015421c21f2ee057c63463d594d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320193"
---
# <a name="step-1-configure-security-baselines"></a>Adım 1. Güvenlik taban çizgilerini yapılandırma

Fidye yazılımı fidye yazılımlarına karşı bir ilk adım olarak, aşağıdaki Microsoft tarafından tanımlanan güvenlik taban çizgilerini yapılandırmalı:

- [Microsoft 365 güvenliği](#microsoft-365-security-baseline)
- [Exchange-posta yönetimi](#exchange-email-management-baseline)
- [Mobil cihazlar ve istemci Windows için ek taban çizgisi](#additional-baselines)

Bu taban çizgisi, saldırganlar tarafından iyi bilinen yapılandırma ayarları ve kurallar içerir; bunların olmaması hızla dikkati çekmez ve yaygın olarak istismarlanır.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 temeli

İlk olarak, Microsoft Güvenli Puan'ı kullanarak güvenlik nedenlerinizi [değerlendirin ve ölçün](/microsoft-365/security/defender/microsoft-secure-score) ve gerektiğinde geliştirmek için yönergeleri izleyin.

Ardından, şüpheli [etkinlikleri ve korumasız içeriği](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) engellemeye yardımcı olmak için saldırı yüzeyini azaltma kurallarını kullanın. Bu kurallar şunları engellemeyi içerir:

- Alt Office tüm uygulama ve uygulamalar
- E-posta istemcisi ve web postası yürütülebilir içeriği
- Yürütülebilir dosyaların yaygın bir hale gelen, yaş veya güvenilir liste ölçütüne uygun olmadığı sürece çalıştırılamaları
- Obfusced olabilecek betikleri yürütme
- İndirilen yürütülebilir içeriği başlatmadan JavaScript veya VBScript
- Office yürütülebilir içerik oluşturmadan önce uygulama yükleme
- Office işlemlere kod eklemeden uygulama ekleme
- Office işlemleri oluşturmadan iletişim uygulamasını uygulama
- USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemler
- Windows Management Interface (WMI) olay aboneliği aracılığıyla kalıcılık
- Yerel güvenlik yetkilisi alt sisteminden (Windows) çalan kimlik lsass.exe
- PSExec ve WMI komutlarından kaynaklanan süreç oluşturma

## <a name="exchange-email-management-baseline"></a>Exchange-posta yönetimi temeli 

Bu e-posta taban çizgisi ayarları ile kiracınıza ilk erişimin e-posta tabanlı Exchange engellemeye yardımcı olun:

- [E-Microsoft Defender Virüsten Koruma taramayı etkinleştirin](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- Gelişmiş kimlik avı koruması için Office 365 ve [yeni](/microsoft-365/security/office-365-security/anti-phishing-protection) tehditlere ve polimorphic çeşitlemelere karşı kapsam için Microsoft Defender'ı kullanın.
- Kimlik e Office 365, istenmeyen posta ve kötü amaçlı yazılım içeren e-postaları engellemiş olmak için e-posta filtreleme ayarlarınızı kontrol edin. Gelişmiş kimlik avı Office 365 ve yeni tehditlere ve polimorphic çeşitlemelere karşı kapsam için Defender'ı kullanın. Yeni alınan tehdit Office 365 [tıkla ve](/microsoft-365/security/office-365-security/atp-safe-links) sil seçeneğinde bağlantıları yeniden kontrol etmek için [](/microsoft-365/security/office-365-security/zero-hour-auto-purge) Defender'ı Yapılandır.
- EOP ve Defender için güvenlik  [ayarlarını gözden geçirin ve en son Office 365 güncelleştirin](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp).
- Yeni alınan tehdit Office 365 tıkla [ve](/microsoft-365/security/office-365-security/set-up-safe-links-policies) sil seçeneğinde bağlantıları yeniden kontrol etmek için Defender'ı Yapılandır.

## <a name="additional-baselines"></a>Ek taban çizgisi

Güvenlik [taban çizgilerini şu özellikler için](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) uygula:

- Microsoft Windows 11 veya 10
- Microsoft 365 Uygulamaları için Enterprise
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar üzerindeki etkisi ve değişiklik yönetimi

Saldırı yüzeyini azaltma kuralı için en iyi uygulama olarak, bir kuralın ilgili kuralla ilgili güvenlik önerisini Bu kuralın güvenlik önerisini Yakın Zaman'da açarak ağınızı nasıl etkiley Tehdit ve Güvenlik Açığı Yönetimi. Öneri ayrıntıları bölmesi, kullanıcı etkisini açıklar. Cihazlarınızı yüzde kaçının, kullanıcı üretkenliğini olumsuz etkilemeden engelleme modunda kuralı etkinleştiren yeni bir ilkeyi kabul edebilir.

Buna ek Exchange e-posta taban çizgisi ayarlarını kullanarak gelen e-postayı engelleyebilir ve e-postanın gönderilmesini veya e-posta içindeki bağlantıların tık tıklatması önlenebilir. Çalışanlarınızı bu davranış konusunda eğitin ve bu önlemlerin alınma nedeni konusunda eğitin.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

İşte bu adımdan sonra kiracınız için fidye yazılımı koruması.

![1. Adım'dan Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)


## <a name="next-step"></a>Sonraki adım

[![Yazılım yazılımlarını ve fidye yazılımlarını koruma için 2. Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Kiracınız [için saldırı algılama](ransomware-protection-microsoft-365-attack-detection-response.md) ve yanıt özelliklerini dağıtmak için 2. Adımdan Microsoft 365 devam edin.
