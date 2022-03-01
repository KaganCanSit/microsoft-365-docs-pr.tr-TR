---
title: Düzeltme algılamaları için Microsoft Defender Virüsten Koruma yapılandırma
description: Bir Microsoft Defender Virüsten Koruma algılayana kadar ne olacağını ve karantina klasöründe ne kadar süreyle karantinada tutmaları gerektiğini yapılandırma
keywords: düzeltme, düzeltme, kaldırma, tehdit, karantina, tarama, geri yükleme
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 182e0b39c1a9c7795fbdd716fc2e260d06d5c451
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997033"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Düzeltme algılamaları için Microsoft Defender Virüsten Koruma yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bir Microsoft Defender Virüsten Koruma çalıştıracaksa, algılanan tehditleri düzeltmeye veya kaldırmaya çalışır. Belirli tehditlere karşı Microsoft Defender Virüsten Koruma, düzeltmeden önce bir geri yükleme noktası oluşturulacak mı ve tehditlerin ne zaman kaldırılacaklarını yapılandırabilirsiniz.

Bu makalede, Grup İlkesi kullanarak bu ayarların nasıl yapılandırıldığından emin olun; ancak, [Microsoft Endpoint Configuration Manager ve Microsoft Intune](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings)[.](/intune/device-restrictions-configure)

Bu ayarları yapılandırmak için [`Set-MpPreference` PowerShell cmdlet'ini](/powershell/module/defender/set-mppreference) veya [`MSFT_MpPreference` WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) sınıfını da kullanabilirsiniz.

## <a name="configure-remediation-options"></a>Düzeltme seçeneklerini yapılandırma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. Bileşenleri ve bileşenleri Windows **için** \> **Microsoft Defender Virüsten Koruma**.

4. Aşağıdaki tabloyu kullanarak, bir konum seçin ve sonra ilkeyi gereken şekilde düzenleyin.

5. **Tamam**'ı seçin.

<br/><br/>

|Konum|Ayar|Açıklama|Varsayılan ayar (yapılandırılmamışsa)|
|---|---|---|---|
|Tarama|Sistem geri yükleme noktası oluşturma|Her gün temizleme veya tarama denenmeden önce bir sistem geri yükleme noktası oluşturulur|Devre dışı|
|Tarama|Tarama geçmişi klasöründen öğeleri kaldırmayı açma|Tarama geçmişinde kaç gün öğenin tutulacaklarını belirtme|30 gün|
|Kök|Düzenli düzeltmeyi kapatma|Tehditlere otomatik olarak Microsoft Defender Virüsten Koruma düzeltmesi gerekip gerek olmadığını veya uç nokta kullanıcıya ne yapacaklarını sorarak belirtebilirsiniz.|Devre dışı (tehdit otomatik olarak düzeltilir)|
|Karantina|Öğeleri Karantina klasöründen kaldırmayı yapılandırma|Öğenin kaldırılması için karantinada kaç gün tutulacaklarını belirtme|90 gün|
|Tehdit|Algılandığında varsayılan eylemin alınmayacak tehdit uyarı düzeylerini belirtme|Kullanıcı tarafından algılanan her tehdit Microsoft Defender Virüsten Koruma bir tehdit düzeyine (düşük, orta, yüksek veya ciddi) atanır. Bu ayarı kullanarak tehdit düzeylerinin her biri için tüm tehditlerin nasıl düzelt(karantinaya alın, kaldırılır veya yoksayılır) olacağını tanımlayabilirsiniz.|Geçerli değil|
|Tehdit|Algılandığında varsayılan eylemin alınmayacak tehditlerini belirtme|Belirli tehditlerin (tehdit kimliklerini kullanarak) nasıl düzeltile olacağını belirtin. Belirli tehdidin karantinaya mı alınıp alınmayacak, kaldırılacak veya yoksa yoksayılacak|Geçerli değil|

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma çok faktöre dayalı olarak dosyaları algılar ve düzelter. Bazen, bir düzeltmeyi tamamlamak için yeniden başlatma gerekir. Algılamanın hatalı pozitif olduğu daha sonra belirlense bile, tüm ek düzeltme adımlarının tamamlandığından emin olmak için yeniden başlatmanın tamamlanması gerekir.
>
> Hatalı pozitif bir Microsoft Defender Virüsten Koruma dayalı olarak dosyayı karantinaya almak istediğinizden eminsanız, cihaz yeniden başlatıldıktan sonra dosyayı karantinadan geri yükleyebilirsiniz. Bkz[. Karantinaya alınmış dosyaları tek Microsoft Defender Virüsten Koruma](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> Gelecekte bu sorunu önlemek için dosyaları taramaların dışında tutabilirsiniz. Bkz[. Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md).

Ayrıca bkz[. Düzeltmeyle ilgili daha fazla ayar Microsoft Defender Virüsten Koruma taramaları](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) için düzeltme için gereken tam zamanlanmış tam taramayı yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarama Microsoft Defender Virüsten Koruma yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Zamanlanmış taramaları Microsoft Defender Virüsten Koruma yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Taramalarda isteğe bağlı olarak Microsoft Defender Virüsten Koruma çalıştırma](run-scan-microsoft-defender-antivirus.md)
- [Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)
- [Son kullanıcı veya Microsoft Defender Virüsten Koruma yapılandırma](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
