---
title: Sınırlı düzenli tarama Microsoft Defender Virüsten Koruma etkinleştirme
description: Sınırlı düzenli tarama, diğer yüklü AV Microsoft Defender Virüsten Koruma yanı sıra belirli aralıklarla taramayı da kullanmanızı sağlar
keywords: lps, sınırlı, düzenli, tarama, tarama, uyumluluk, üçüncü taraf, diğer av, devre dışı
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 1ba846402bb2ee447ee5f38ff035c119bdc28fc1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467697"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>2010'da sınırlı düzenli tarama Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Sınırlı düzenli tarama, bir Windows 10 veya Windows 11 cihazına başka bir virüsten koruma ürünü yükledikten sonra etkinleştirilebilir, özel bir tehdit algılama Windows 11 tt.

Yalnızca belirli durumlarda etkinleştirilebilir. Sınırlı düzenli tarama ve diğer virüsten koruma Microsoft Defender Virüsten Koruma çalışma hakkında daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma uyumluluğu koruma.](microsoft-defender-antivirus-compatibility.md)

**Microsoft, kurumsal ortamlarda bu özelliğin kullanılması önerilmez. Bu öncelikle tüketicilere yönelik bir özelliktir.** Bu özellik, kötü amaçlı yazılımı Microsoft Defender Virüsten Koruma özelliklerinden yalnızca sınırlı bir alt kümesini kullanır ve kötü amaçlı yazılımları ve istenmeyen olabilecek yazılımların çoğunu algılamayacaktır. Ayrıca, yönetim ve raporlama özellikleri de sınırlı olacaktır. Microsoft, kuruluşlara birincil virüsten koruma çözümlerini seçmelerini ve özel olarak kullanmalarını önerir.

## <a name="how-to-enable-limited-periodic-scanning"></a>Sınırlı düzenli tarama nasıl etkinleştirilen

Varsayılan olarak Microsoft Defender Virüsten Koruma başka virüsten koruma ürünü yüklü yoksa ya da diğer ürün güncel değil, süresi dolmuşsa veya düzgün çalışmıyorsa, Windows 10 veya Windows 11 cihazında kendisini etkinleştirir.

Devre Microsoft Defender Virüsten Koruma ise, bu cihazda yapılandıracak şekilde normal seçenekler görüntülenir:

:::image type="content" source="images/vtp-wdav.png" alt-text="Tarama Windows Güvenliği, ayarlar ve güncelleştirme seçenekleri de dahil olmak üzere Microsoft Defender AV seçeneklerini gösteren en iyi uygulama" lightbox="images/vtp-wdav.png":::

Başka bir virüsten koruma ürünü yüklüyse ve düzgün şekilde çalışıyorsa, Microsoft Defender Virüsten Koruma kendisini devre dışı bırakacak. Bu Windows Güvenliği, AV **ürünüyle ilgili durumu göstermek &** Virüs koruması bölümünü değiştirir ve ürünün yapılandırma seçeneklerinin bağlantısını sağlar.

Tüm üçüncü taraf AV ürünlerinin altında, yeni bir bağlantı diğer Microsoft Defender Virüsten Koruma **görünür**. Sınırlı düzenli taramaya olanak sağlayan iki durumlu düğmeyi göstermek için bu bağlantıya tıklar. Sınırlı düzenli tarama seçeneğinin, düzenli taramayı etkinleştirme veya devre dışı bırakma arasında geçiş yapmak olduğunu unutmayın. 

Sliding the switch to **On** will show the standard Microsoft Defender AV options underneath the third party AV product. Sınırlı düzenli tarama seçeneği sayfanın en altında görüntülenir.

## <a name="related-articles"></a>İlgili makaleler

- [Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)