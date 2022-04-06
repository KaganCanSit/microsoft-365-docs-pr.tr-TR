---
title: İstenmeyen yazılım
ms.reviewer: ''
description: İstenmeyen yazılımın sizin izniniz olmadan varsayılan ayarlarınızı nasıl değiştir olduğunu ve kendinizi korumak için neler yapabilirsiniz hakkında bilgi alın.
keywords: güvenlik, kötü amaçlı yazılım, koruma, istenmeyen, yazılım, değiştirme, bulaşabilir, istenmeyen yazılım, yazılım paketleyenler, tarayıcı değiştiricileri, gizlilik, güvenlik, bilgi işlem deneyimi, bulaşmayı önleme, çözüm, WDSI, MMPC, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, virüs araştırma tehditleri, kötü amaçlı yazılım araştırma, bilgisayar koruması, bilgisayar bulaşması, virüs bulaşması, açıklamalar, düzeltme, en son tehditler
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 94b3bad5b5653420d91cd422d40a0ff7802e6442
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706202"
---
# <a name="unwanted-software"></a>İstenmeyen yazılım

İstenmeyen yazılımlar, sizin izniniz Windows denetiminiz olmadan bu deneyimi değiştiren programlardır. Bu durum değiştirilmiş gözatma deneyimi, indirmeler ve yükleme üzerinde denetim olmaması, yanıltıcı iletiler veya kurulum ayarlarına yönelik yetkisiz değişiklikler Windows olabilir.

## <a name="how-unwanted-software-works"></a>İstenmeyen yazılım nasıl çalışır?

Bir kullanıcı internetten uygulama arar ve indirirken istenmeyen yazılım kullanılabilir. Bazı uygulamalar yazılım paketçileridir, yani başka uygulamalarla bir paketlenirler. Sonuç olarak, özgün uygulama indirilirken başka programlar yanlışlıkla yüklenebilir.

İstenmeyen yazılıma dair bazı göstergeler:

- Yüklememişsiniz ve programı kaldırmak zor olabilir

- Tarayıcı özellikleri veya ayarları değişti ve bunları görüntüleyeme ya da değiştireyesiniz

- Cihazınızın durumu veya dosyalar ve programlar hakkında çok fazla ileti var

- Kolayca kapatılayılan reklamlar var

Bazı göstergelerin farksı daha zordur, çünkü bunlar daha az kesintiye neden olur, ancak yine de istenmeyendir. Örneğin, istenmeyen yazılımlar belirli reklamları görüntülemek, gözatma etkinliklerini izlemek veya tarayıcının kontrollerini kaldırmak için web sayfalarını değiştirebilir.

Microsoft, istenmeyen yazılımları [tanımlamak için kapsamlı](criteria.md) bir değerlendirme ölçütleri kullanır.

## <a name="how-to-protect-against-unwanted-software"></a>İstenmeyen yazılımlara karşı koruma

İstenmeyen yazılım bulaşmasını önlemek için, yazılımı yalnızca resmi web sitelerinden veya web sitesinden Microsoft Store. Üçüncü taraf sitelerden yazılım indirmeye karşı çok fazla bilgi kullanın.

[İnternet'Microsoft Edge](/microsoft-edge/deploy/index) göz atma videolarını kullanın. Microsoft Edge tarayıcı ayarlarınızı değiştiren tarayıcı değiştiricileri etkili bir şekilde engel olan ek korumalar içerir. Microsoft Edge Ayrıca, [SmartScreen](/microsoft-edge/deploy/index) (Internet Explorer tarafından da kullanılır) Windows Defender web sitelerini kullanarak istenmeyen yazılım barındırmasını engeller.

[E-Microsoft Defender Virüsten Koruma'i](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) Windows 10. Tehditlere karşı gerçek zamanlı koruma sağlar, bilinen ve istenmeyen yazılımları tespit eder ve kaldırır.

7 veya Windows Vista'da gerçek zamanlı koruma için [Microsoft Security Essentials'Windows'i](https://www.microsoft.com/download/details.aspx?id=5201) indirin.

Daha genel ipuçları için bkz. Kötü [amaçlı yazılım bulaşmasını önleme](prevent-malware-infection.md).

### <a name="what-should-i-do-if-my-device-is-infected"></a>Cihazıma virüs bulaşmışsa ne yapabilirim? 

İstenmeyen bir yazılıma sahip olduğunuz varsa analiz için [dosya gönderebilirsiniz](https://www.microsoft.com/wdsi/filesubmission).

Bazı istenmeyen yazılımlar kaldırma girdilerini ekler ve bu da, bunları kaldırmak için bir **kullanıcı Ayarlar**.
1. Başlat düğmesini seçin
2. Uygulamalar ve **Ayarlar > özellikleri > uygulamaları ve & gidin**.
3. Kaldırmak istediğiniz uygulamayı seçin ve Kaldır'a **tıklayın**.

Yalnızca istenmeyen yazılım bulaşmanın belirtilerini yeni fark ettiysanız, yükleme tarihine göre uygulamaları sıralamayı ve ardından yüklememiş olmadığınız en son uygulamaları kaldırmayı göz önünde bulundurabilirsiniz.

Ayrıca Internet Explorer, Firefox **veya** Chrome gibi tarayıcılar ınıza tarayıcı eklentilerini kaldırmanız da gerekir.

Tehdit kaldırmanın başarısız olduğu durumda, kötü amaçlı yazılım algılama ve kaldırma [sorunlarını giderme hakkında bilgi edinebilirsiniz](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware).