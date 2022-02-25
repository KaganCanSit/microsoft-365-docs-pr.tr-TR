---
title: Değerlendirme Microsoft 365 Defender
description: Test etmek Microsoft 365 Defender test etmek ve kurumdaki cihazları, kimlikleri, verileri ve uygulamaları korumak üzere tasarlanmış güvenlik çözümünü denemek için test laboratuvarınızı veya pilot ortamınızı ayarlayın.
keywords: Microsoft 365 Defender, denemeyi Microsoft 365 Defender, Microsoft 365 Defender, Microsoft 365 Defender değerlendirme laboratuvarına veya Microsoft 365 Defender  pilot, siber güvenlik, gelişmiş kalıcı tehdit, kurumsal güvenlik, cihazlar, cihaz, kimlik, kullanıcılar, veri, uygulamalar, olaylar, otomatik araştırma ve düzeltme, gelişmiş tarama
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1c260588b80d8325567b74148a7a62586cfbc707
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959676"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Test laboratuvarı Microsoft 365 Defender pilot ortamı oluşturma 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender


Bu kılavuz, kullanıcılar ve gruplarla bir laboratuvar ortamı ayarlama üzerinde çalışmanıza yardımcı olur, ardından tehdit saldırısını taklit etmek ve anlamlı bir deneme sonucu elde etmek için Microsoft 365 Defender'daki yeteneklerin yapılandırmasında size yol gösterir. 

Bu deneme laboratuvarı veya pilot ortamını oluşturmanın amacı, kapsamlı ve tümleşik çalışma Microsoft 365 Defender göstermektir. Bu akıllı güvenlik çözümünün, kuruluşu ileri düzey tehditlere karşı nasıl algıla, önle, otomatik olarak incelemesini ve buna yanıt vermesini deneyimlenin. 


Önerilen dağıtım yollarına dayalı olarak değerlendirmenizi Microsoft 365 Defender adımlarda size yol kılavuzunuz olur. Amaç, test hesabı olan bir laboratuvar ortamında veya tam lisansa sahip üretim ortamında bir pilot ortamda güvenlik çözümünü ayarlamanıza yardımcı olmaktır. Deneme laboratuvarınızı veya pilot ortamınızı hazırlamak, organizasyondaki karar vericilere güvenlik işlemi kullanım durumlarını sunmanıza yardımcı olabilir. Saldırı benzetimlerinizi çalıştırmayı tamamlarsanız ve sonuçlardan memnun olursanız, Microsoft Teknik Satış Uzmanları veya organizasyonu çalıştıran uzmanların yardımıyla bunu tamamen dağıtın ve çalıştırın. 

Bu kılavuz size yardımcı olacaktır:
- Laboratuvar sunucularınızı ve bilgisayarlarınızı ayarlama
- Kullanıcılar ve gruplarla Active Directory'yi yapılandırma
- Kimlik için Microsoft Defender'ı, Kimlik için Microsoft Defender'ı, Office 365 için Microsoft Defender'ı ve Uç Nokta için Microsoft Defender'ı ayarlayın Microsoft Cloud App Security
- Sunucunuz ve bilgisayarlarınız için yerel ilkeler ayarlama
- Bir test olayı veya uyarı oluşturmak için tehdit saldırılarını taklit Microsoft 365 Defender

>[!IMPORTANT]
>En iyi sonuçları elde etmek için mümkün olan en iyi sonuçları elde etmek için laboratuvar kurulumu yönergelerini izleyin.


## <a name="deployment-phases"></a>Dağıtım aşamaları

Deneme laboratuvarı ortamı için üç Microsoft 365 Defender aşaması vardır.

![Dağıtım aşamaları: hazırlama, kurulum, ekleme](../../media/evaluation-guide-phases.png)

|Aşama | Açıklama | 
|:-------|:-----|
|[Aşama 1: Hazırlama](prepare-m365d-eval.md)| Bir deneme laboratuvarında veya pilot ortamında Microsoft 365 Defender neleri göz önünde bulunduracaklarını öğrenin: <br><br>- Paydaşlar ve oturum kapatma <br> - Ortamda dikkate alınacak noktalar <br>- Access <br>- Azure Active Directory kurma <br> - Yapılandırma sırası
|[Aşama 2: Kurulum](setup-m365deval.md)|  Test laboratuvarı veya pilot ortamınızı Microsoft 365 için Güvenlik Merkezi'ne erişmek Microsoft 365 Defender adımlarını izleyin. Şu adımlara yönlendirildiniz:<br><br>- Deneme sürümüne Microsoft 365 E5 olun <br>  - Etki alanını yapılandırma<br>- Microsoft 365 E5 atama<br>- Portalda kurulum sihirbazını tamamlama|
|[Aşama 3: Ekleme & yapılandırma](config-m365d-eval.md) | Her sütunlu Microsoft 365 Defender ekleme uç noktalarını yapılandırma. Şu adımlara yönlendirildiniz:<br><br>- Windows için Microsoft Defender'ı Office 365<br>- Microsoft Cloud App Security<br>- Kimlik için Microsoft Defender'ı yapılandırma<br>- Uç Nokta için Microsoft Defender'ı Yapılandırma


Bu kılavuzu tamamlandıktan sonra katılan paydaşları ve gerekli onayları tanımlamış, doğru erişim izinlerine sahip, deneme sürümüne ve yapılandırılmış etki alanlarına ve Microsoft 365 Defender sütunlarından her biri için imzalanmış ve uç noktalarınız hizmete dahil edilmiş olur.

## <a name="key-capabilities"></a>Önemli özellikler

Microsoft 365 Defender çok sayıda özellik sağlarken, bu dağıtım kılavuzunun temel amacı, cihaz ekleme ile başlamanızı sağlar. Bu kılavuz, eklemeye ek olarak aşağıdaki özelliklerle başlamana da yardımcı olur.


Özellik | Açıklama 
:---|:---
Office 365 için Microsoft Defender | Tüm tehditlerinizi Office 365 tehditlere karşı korumanıza yardımcı olur
Kimlik için Microsoft Defender | Güvenliği tehlikeye atılmış kimlikleri ve kötü amaçlı insider eylemlerini tanımlar ve algılar.
Microsoft Cloud App Security | Bulut hizmetleri genelinde zengin görünürlük sağlar, veri seyahatini kontrol eder ve siber saldırıları algılar.
Uç Nokta için Microsoft Defender | Kapsamlı uç nokta güvenliği olan gelişmiş tehditlere karşı engelleme, algılama ve yanıt özellikleri sağlar.


## <a name="in-scope"></a>Kapsamda

Bu kılavuz için aşağıdaki görevler kapsamdadır:
-   Ayarlama Azure Active Directory
-   E-Microsoft 365 Defender
    -   Deneme sürümüne Microsoft 365 E5 veya pilot kullanıyorsanız tam lisansınızı kullanma
    -   Etki alanını yapılandırma
    -   Kullanıcı Microsoft 365 E5 atama
    -   Portalda kurulum sihirbazını tamamlama
-   En iyi Microsoft 365 Defender dayalı olarak tüm yığma sütunlarını yapılandırma
    -   Office 365 için Microsoft Defender
    -   Kimlik için Microsoft Defender
    -   Microsoft Cloud App Security
    -   Uç Nokta için Microsoft Defender

## <a name="out-of-scope"></a>Kapsam dışında

Aşağıdakiler, bu dağıtım kılavuzunun kapsamı dışındadır:

-   Diğer taraflarla tümleştir belki de üçüncü taraf çözümlerinin Microsoft 365 Defender
-   Üretim ortamında test etme

## <a name="next-step"></a>Sonraki adım
[Aşama 1: Hazırlama](prepare-m365d-eval.md) 
<br> Microsoft 365 Defender test laboratuvarınızı veya pilot ortamınızı hazırlama
