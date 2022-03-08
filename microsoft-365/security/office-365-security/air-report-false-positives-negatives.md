---
title: Office 365 için Microsoft Defender'da otomatik incelemeden sonra hatalı pozitif veya yanlış negatifleri Office 365
description: Bu sorun için Microsoft Defender'da AIR tarafından bir şey cevapsız veya yanlış Office 365? Çözümleme için Microsoft'a hatalı pozitif veya yanlış negatif sonuçlar göndermeyi öğrenin.
keywords: otomatik, araştırma, uyarı, tetikleyici, eylem, düzeltme, yanlış pozitif, hatalı negatif
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
ms.prod: m365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: 98164fd42a0ed2e2d79e2319823363057d15e7d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318613"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Otomatik araştırma ve yanıt yeteneklerinde hatalı pozitif/negatifleri bildirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bir [şeyi kaçırmanız veya](automated-investigation-response-office.md) yanlış şekilde algılaymanıza neden olan otomatik soruşturma ve yanıt (AIR) özellikleri Office 365, güvenlik işlemleri ekibimizin bu durumu düzeltmek için atılması gereken adımlar vardır. Bu tür eylemler şunlardır:

- [Microsoft'a hatalı pozitif/negatif bir rapor bildirme](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Uyarıları ayarlama](#adjust-an-alert-to-prevent-false-positives-from-recurring) (gerekirse); ve
- [Yapılan düzeltme eylemleri geri alınıyor](#undo-a-remediation-action).

Bu makaleyi kılavuz olarak kullanın.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Çözümleme için hatalı pozitif/negatif microsoft raporu

Office 365 için Microsoft Defender'da AIR bir e-posta mesajını, e-posta ekini, e-posta iletisinde bir URL'yi veya Office dosyasındaki bir URL'yi kaçırıyorsa, tarama yapmak için şüpheli istenmeyen posta, kimlik avı[, URL'ler ve dosyaları Microsoft'a Office 365](admin-submission.md) gönderebilirsiniz.

Ayrıca kötü amaçlı [yazılım çözümlemesi yapmak için dosyayı Microsoft'a gönderebilirsiniz](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Hatalı pozitif sonuç yinelemesini önlemek için uyarı ayarlama

Geçerli kullanım bir uyarı tarafından tetiklenirse veya uyarı yanlışsa, Bulut Uygulamaları için [Defender portalında uyarıları yönetebilirsiniz](/cloud-app-security/managing-alerts).

Cihazınız güvenli olsa bile, bir dosya, Office 365 IP adresi, URL veya etki alanı uç nokta için [Microsoft Defender for Endpoint](/windows/security/threat-protection) kullanıyorsa ve bir cihazda kötü amaçlı yazılım olarak kabul edilen bir dosya, IP adresi, URL veya etki alanı, cihazınız için "İzin Ver["](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) eylemiyle özel bir gösterge oluşturabilirsiniz.

## <a name="undo-a-remediation-action"></a>Düzeltme eylemlerini geri alma

Çoğu durumda, bir e-posta iletisi, e-posta eki veya URL üzerinde bir düzeltme eylemi gerçek oldu ve öğe aslında bir tehdit değil, güvenlik işlemleri ekibinin düzeltme eylemini geri alabilir ve hatalı pozitif sonuç tekrarı önleyen adımlar atabilirsiniz. Bir eylemi geri almak [üzere bir](#undo-an-action-using-threat-explorer) soruşturma için [Tehdit Gezgini'ni veya](#undo-an-action-in-the-action-center) Eylemler sekmesini kullanabilirsiniz.

> [!IMPORTANT]
> Aşağıdaki görevleri gerçekleştirmeyi denemeden önce gerekli izinlere sahip olduğundan emin olun.

### <a name="undo-an-action-using-threat-explorer"></a>Threat Explorer'ı kullanarak eylemi geri alma

Tehdit Gezgini'nde, güvenlik işlemleri ekipleriniz bir eylemden etkilenen bir e-posta bulabilir ve bu işlemi geri alabilir.

<br>

****

|Senaryo|Geri Alma Seçenekleri|Daha fazla bilgi|
|---|---|---|
|Bir e-posta iletisi kullanıcının Gereksiz E-posta klasörüne yönlendirildi|<ul><li>İletiyi kullanıcının Silinmiş Öğeler klasörüne taşıma</li><li>İletiyi kullanıcının Gelen Kutusu'na taşıma</li><li>İletiyi silme</li></ul>|[Teslim edilen kötü amaçlı e-postaları bulma ve Office 365](investigate-malicious-email-that-was-delivered.md)|
|E-posta iletisi veya dosya karantinaya alındı|<ul><li>E-postayı veya dosyayı serbest bırakma</li><li> E-postayı veya dosyayı silme</li></ul>|[Karantinaya alınan iletileri yönetici olarak yönetme](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-in-the-action-center"></a>İşlem merkezinde eylemi geri alma

İşlem merkezinde, yapılan düzeltme eylemlerini görebilir ve eylemi geri alma olasılığı vardır.

1. aşağıdaki Microsoft 365 Defender portalında <https://security.microsoft.com>İşlem merkezi'ne gidin. Doğrudan İşlem merkezine gitmek için, 'i kullanın <https://security.microsoft.com/action-center/>.
2. İşlem merkezinde Geçmiş sekmesini **seçerek** tamamlanmış eylemlerin listesini görüntüleyin.
3. Bir öğe seçin. Açılır bölmesi açılır.
4. Uçarak çıkış bölmesinde Geri Al'ı **seçin**. (Yalnızca geri alınmayacak eylemlerin Geri Al **düğmesi** olur.)

## <a name="see-also"></a>Ayrıca bkz.

- [Office 365 için Microsoft Defender](defender-for-office-365.md)
- [Office 365 için Microsoft Defender'da otomatik Office 365](office-365-air.md)
