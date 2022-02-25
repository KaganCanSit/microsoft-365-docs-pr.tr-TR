---
title: eBulma Dışarı Aktarma Aracı'nı Microsoft Edge
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
description: Güvenlik ve uyumluluk ClickOnce İçerik Arama ve eKbulma'dan arama sonuçlarını indirmek üzere Microsoft Edge'un en yeni sürümünü kullanmak için, ClickOnce desteğini etkinleştirmeniz gerekir.
ms.openlocfilehash: bd42ebffce326e4abe4943ff4187fc2bd960ff65
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2021
ms.locfileid: "62959907"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>eBulma Dışarı Aktarma Aracı'nı Microsoft Edge

Yeni sürümde yapılan son değişikliklerin sonucu olarak, Microsoft Edge ClickOnce artık varsayılan olarak etkinleştirilmez. İçerik Arama veya eBulma arama sonuçlarını indirmek üzere eBulma Dışarı Aktarma Aracı'nı kullanmaya devam etmek için [Microsoft Internet Explorer'ı](https://support.microsoft.com/help/17621/internet-explorer-downloads) kullanın veya ClickOnce'un en yeni sürümünde Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Destek ClickOnce Microsoft Edge etkinleştirme

1. Bu Microsoft Edge, **Tamam'a edge://flags/#edge-click-once**.

2. Var olan değer açılan listede Varsayılan **veya** **Devre Dışı** olarak ayarlanmışsa, bunu Etkin olarak **ayarlayın**.

   ![Açılan listeden Etkin'i seçin.](../media/ClickOnceimage1.png)

3. Tarayıcı penceresinin en altına kadar ekranı aşağı kaydırın ve Edge'i yeniden başlatmak **için Yeniden Başlat'a** tıklayın.

   ![Yeniden Başlat'a tıklayın.](../media/ClickOnceimage2.png)

**Not:** Kuruluşlar, grup desteğini devre dışı bırakmak için Grup ClickOnce kullanabilir. Destek birimi desteğiyle ilgili bir kuruluş ilkesi olup ClickOnce olup **edge://policy.** Aşağıdaki ekran görüntüsünde, ClickOnce genelinde etkinleştirilmiştir. Bu ilke değeri false olarak **ayarlanırsa**, kuruluşta bir yöneticiyle iletişim kurmanız gerekir.

![Edge kuruluş ilkelerinin listesi.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>eBulma Dışarı Aktarma Aracı'nı yükleme ve çalıştırma

1. İçerik **Arama veya** eBulma durumunda dışarı aktarmanın çıkış sayfasında Sonuçları indir'e tıklayın.

   ![Arama sonuçlarını indirmek için Uç sayfada sonuçları indir'e tıklayın.](../media/ClickOnceExport1.png)

2. Aracı başlatmanız için bir onay istenir; Aç'a **tıklayın**.

   ![eBulma Dışarı Aktarma Aracı'nı başlatmak için Aç'a tıklayın.](../media/ClickOnceimage4.png)

   eBulma Dışarı Aktarma Aracı yüklü değilse, bir Güvenlik Uyarısı girmeniz istenir 

   ![eBulma Dışarı Aktarma Aracı'nı yüklemek için Yükle'ye tıklayın.](../media/ClickOnceimage5.png)

3. **Yükle**'ye tıklayın. Yüklendikten sonra, dışarı aktarma aracı otomatik olarak başlatılır.

Daha fazla bilgi için, aşağıdaki konulara bakın:

- [İçerik Arama sonuçlarını dışarı aktarma](export-search-results.md)

- [E-Microsoft Edge'de deneme bayrakları nasıl Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
