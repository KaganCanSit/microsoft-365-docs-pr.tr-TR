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
ms.openlocfilehash: e0a8293709da44dc3a46cf565ad099666e8dae24
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997029"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>2010'da sınırlı düzenli tarama Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Sınırlı düzenli tarama, bir Windows 10 veya Windows 11 cihazına başka bir virüsten koruma ürünü yükledikten sonra etkinleştirilebilir, özel bir tehdit algılama ve düzeltme t t tipidir.

Yalnızca belirli durumlarda etkinleştirilebilir. Sınırlı düzenli tarama ve diğer virüsten koruma Microsoft Defender Virüsten Koruma çalışma hakkında daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma uyumluluğu koruma.](microsoft-defender-antivirus-compatibility.md)

**Microsoft, kurumsal ortamlarda bu özelliğin kullanılması önerilmez. Bu öncelikle tüketicilere yönelik bir özelliktir.** Bu özellik, kötü amaçlı yazılımı Microsoft Defender Virüsten Koruma özelliklerinden yalnızca sınırlı bir alt kümesini kullanır ve kötü amaçlı yazılımları ve istenmeyen olabilecek yazılımların çoğunu algılamayacaktır. Ayrıca, yönetim ve raporlama özellikleri de sınırlı olacaktır. Microsoft, kuruluşlara birincil virüsten koruma çözümlerini seçmelerini ve özel olarak kullanmalarını önerir.

## <a name="how-to-enable-limited-periodic-scanning"></a>Sınırlı düzenli tarama nasıl etkinleştirilen

Varsayılan olarak, Microsoft Defender Virüsten Koruma başka virüsten koruma ürünü yüklü yoksa veya diğer ürün güncel değilse, süresi dolduysa veya düzgün çalışmıyorsa, Windows 10 veya Windows 11 cihazında kendisini etkinleştirir.

Devre Microsoft Defender Virüsten Koruma ise, bu cihazda yapılandıracak şekilde normal seçenekler görüntülenir:

![Windows Güvenliği, ayarlar ve güncelleştirme seçenekleri de dahil olmak üzere Microsoft Defender AV seçeneklerini gösteren bir uygulama.](images/vtp-wdav.png)

Başka bir virüsten koruma ürünü yüklüyse ve düzgün şekilde çalışıyorsa, Microsoft Defender Virüsten Koruma kendisini devre dışı bırakacak. Bu Windows Güvenliği, AV **ürünüyle ilgili durumu göstermek &** Virüs koruması bölümünü değiştirir ve ürünün yapılandırma seçeneklerinin bağlantısını sağlar.

Tüm üçüncü taraf AV ürünlerinin altında, yeni bir bağlantı diğer Microsoft Defender Virüsten Koruma **görünür**. Sınırlı düzenli taramaya olanak sağlayan iki durumlu düğmeyi göstermek için bu bağlantıya tıklar. Sınırlı düzenli tarama seçeneğinin, düzenli taramayı etkinleştirme veya devre dışı bırakma arasında geçiş yapmak olduğunu unutmayın. 

Sliding the switch to **On** will show the standard Microsoft Defender AV options underneath the third party AV product. Sınırlı düzenli tarama seçeneği sayfanın en altında görüntülenir.

## <a name="related-articles"></a>İlgili makaleler

- [Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)