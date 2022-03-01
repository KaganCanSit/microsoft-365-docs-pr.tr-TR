---
title: Adım 3. SOC hizmet Microsoft 365 Defender ile veri tümleştirmesi planlama
description: Bu hizmetleri güvenlik Microsoft 365 Defender kataloğumuzla tümleştirmenin temelleri.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f18ff452d7f268aa652af097db19f53f2002d8ae
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010762"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Adım 3. SOC hizmet Microsoft 365 Defender ile veri tümleştirmesi planlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Köklü bir Güvenlik İşlemleri Merkezi'nin (SOC) şunları içermesi için bir hizmet kataloğu olması gerekir:

- Kötü amaçlı yazılım & izinsiz giriş
- Attribution & reverse engineering
- Tehdit İstihbaratı
- Analiz
- Araştırma
- 10000 Yıl Sonra
- Olay yanıtı 
- Bilgisayar Güvenliği Olay Yanıt Ekibi (CSIRT) (SOC'dan farklı olabilir) 
- Uyumluluk testi
- Insider tehdit & sahtekarlığı izleme
- Güvenlik olayı & izleme 
- Güvenlik Açığı Tarama
- Genişletilmiş Algılama ve Yanıt (XDR)/Security Alıkat, Otomasyon ve Yanıt (SOAR)
- Kimlik avı
- Veri kaybını önleme
- Marka izleme

Microsoft 365 Defender teknolojileri çeşitli işlevlere yayılmış olduğundan, SOC ekibinin her bileşeni yönetmek ve hizmet işleviyle uyumlu olmak için hangi rollere ve sorumluluklara en uygun Microsoft 365 Defender belirlemesi gerekir.

Bu iki Microsoft 365 Defender vardır:

- **Kimlik için Microsoft Defender** (eski adı Azure Gelişmiş Tehdit Koruması), Active Directory Etki Alanı Hizmetleri (AD DS) kullanarak gelişmiş tehditleri, güvenliği tehlikeye kimlikleri ve kuruluşlara yönelik kötü amaçlı insider eylemlerini tanımlamak, algılamak ve araştırmak üzere sinyaller kullanan bulut tabanlı bir güvenlik çözümüdür.

- Uç Nokta için **Microsoft Defender**, risk tabanlı güvenlik açığı yönetimi ve değerlendirme, saldırı yüzeyini azaltma, davranış tabanlı ve bulut destekli yeni nesil koruma (uç noktada algılama ve yanıtlama) içeren cihazlar için holist, bulut teslimi uç nokta güvenlik çözümüdür EDR ), otomatik araştırma ve düzeltme, yönetilen arama hizmetleri, zengin API'ler ve birleşik güvenlik yönetimi.

 - **Office 365 için Microsoft Defender**, güçlü sıfır günlük koruma sağlayarak kuruluşların bilinmeyen kötü amaçlı yazılımlara ve virüslere karşı korunmasına yardımcı olan ve kuruluşları gerçek zamanlı olarak zararlı bağlantılardan korumaya yönelik özellikler içeren bulut tabanlı bir e-posta filtreleme hizmetidir. Ayrıca, kapsamlı bir araştırma ve arama, yanıt ve düzeltme, farkındalık ve eğitim ve güvenli posture özelliklerine yönelik kapsamlı bir sayfa sunar.

- **Bulut Uygulamaları için Microsoft Defender** ; günlük toplama, API bağlayıcıları ve ters ara sunucu gibi çeşitli dağıtım modlarını destekleyen bir bulut erişim güvenlik aracıcısıdır (CASB). Tüm Microsoft ve üçüncü taraf bulut hizmetlerde siber tehditleri tespit etmek ve buna karşı mücadele etmek için zengin görünürlük, veri seyahati üzerinde denetim ve gelişmiş analiz sağlar.

Bu Microsoft 365 Defender ve teknolojiler çeşitli işlevlere yayılmış olduğundan, SOC ekibinin her bileşeni yönetmek ve hizmet işleviyle uyumlu olmak için hangi rollerin ve sorumlulukların en Microsoft 365 Defender olduğunu belirlemesi gerekir.

Bu hizmetlerin özelliklerini tüm Microsoft 365 Defender için SOC hizmetlerini geliştirmeniz gerekir. Bu özelliğin özellikleri hakkında daha fazla Microsoft 365 Defender aşağıdaki makalelere bakın:

- [Uç Nokta için Microsoft Defender nedir?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Kimlik için Microsoft Defender nedir?](/defender-for-identity/what-is)
- [Office 365 için Defender nedir?](/office-365-security/defender-for-office-365)
- [Bulut Uygulamaları için Microsoft Defender nedir?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Sonraki adım

[Adım 4. Farklı Microsoft 365 Defender, sorumluluklar ve gözetim tanımlayın](integrate-microsoft-365-defender-secops-roles.md)
