---
title: Microsoft Edge'de eBulma Dışarı Aktarma Aracı'nı kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: güvenlik ve uyumluluk merkezinde İçerik Arama ve eBulma'dan arama sonuçlarını indirmek için ClickOnce desteğinin Microsoft Edge en yeni sürümünü kullanmasını etkinleştirmeniz gerekir.
ms.openlocfilehash: cd20a35a0a6ee2518667d21fadbca4577342de36
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995788"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Microsoft Edge'de eBulma Dışarı Aktarma Aracı'nı kullanma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

en yeni Microsoft Edge sürümünde yapılan son değişikliklerin sonucunda ClickOnce desteği artık varsayılan olarak etkin değildir. İçerik Arama veya eBulma arama sonuçlarını indirmek için eBulma Dışarı Aktarma Aracı'nı kullanmaya devam etmek için [Microsoft Internet Explorer'ı](https://support.microsoft.com/help/17621/internet-explorer-downloads) kullanmanız veya Microsoft Edge en yeni sürümünde ClickOnce desteğini etkinleştirmeniz gerekir.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Microsoft Edge'da ClickOnce desteğini etkinleştirme

1. Microsoft Edge'da **edge://flags/#edge-click-once** gidin.

2. Açılan listede mevcut değer **Varsayılan** veya **Devre Dışı** olarak ayarlandıysa, **etkin** olarak değiştirin.

   ![Açılan listeden Etkin'i seçin.](../media/ClickOnceimage1.png)

3. Tarayıcı penceresinin en altına kadar aşağı kaydırın ve Edge'i yeniden başlatmak için **Yeniden Başlat'a** tıklayın.

   ![Yeniden Başlat'a tıklayın.](../media/ClickOnceimage2.png)

**Not:** Kuruluşlar ClickOnce desteğini devre dışı bırakmak için grup ilkesi kullanabilir. ClickOnce desteği için bir kuruluş ilkesi olup olmadığını denetlemek için **edge://policy** gidin. Aşağıdaki ekran görüntüsünde ClickOnce tüm kuruluş genelinde etkinleştirildiği gösterilmektedir. Bu ilke değeri **false** olarak ayarlanırsa, kuruluşunuzdaki bir yöneticiye başvurmanız gerekir.

![Edge kuruluş ilkelerinin listesi.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>eBulma Dışarı Aktarma Aracı'nı yükleme ve çalıştırma

1. İçerik Arama'da dışarı aktarmanın veya eBulma servis talebinin açılır sayfasında **Sonuçları indir'e** tıklayın.

   ![Arama sonuçlarını indirmek için açılır sayfada Sonuçları indir'e tıklayın.](../media/ClickOnceExport1.png)

2. Aracı başlatmanız için bir onay istenir ve **Aç'a** tıklayın.

   ![eBulma Dışarı Aktarma Aracı'nı başlatmak için Aç'a tıklayın.](../media/ClickOnceimage4.png)

   eBulma Dışarı Aktarma Aracı yüklü değilse, sizden bir Güvenlik Uyarısı istenir. 

   ![eBulma Dışarı Aktarma Aracı'nı yüklemek için Yükle'ye tıklayın.](../media/ClickOnceimage5.png)

3. **Yükle**'ye tıklayın. Yüklendikten sonra dışarı aktarma aracı otomatik olarak başlatılır.

Daha fazla bilgi için, aşağıdaki konulara bakın:

- [İçerik Arama sonuçlarını dışarı aktarma](export-search-results.md)

- [Microsoft Edge'de deneme bayraklarını etkinleştirme](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
