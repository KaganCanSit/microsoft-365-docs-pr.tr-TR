---
title: Saldırı yüzeyini azaltma kuralları ile ilgili sorunları giderme
description: Uç Nokta için Microsoft Defender'da saldırı yüzeyini azaltma kurallarıyla ilgili sorunları gidermek için kaynaklar ve örnek kod.
keywords: sorun giderme, hata, düzeltme, windows defender eg, asr, kurallar, hips, sorun giderme, denetim, dışlama, yanlış pozitif, bozuk, engelleme, Uç Nokta için Microsoft Defender
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: c503c3ed4cfea4ed0645cf18a9c9bf4ebe4a5ade
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015201"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kuralları ile ilgili sorunları giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Saldırı yüzeyini [azaltma kurallarını kullanırken](attack-surface-reduction.md) aşağıdakiler gibi sorunlar ile karşı koyun:

- Kural bir dosyayı, işlemi engeller veya olmaması gereken başka işlemler gerçekleştirir (hatalı pozitif)
- Kural açıklandığı gibi çalışmıyor veya olması gereken bir dosyayı veya işlemi engellemez (hatalı negatif)

Bu sorunları gidermenin dört adımı vardır:

1. [Önkoşulları onaylayın](#confirm-prerequisites)
2. [Kuralı test etmek için denetim modunu kullanma](#use-audit-mode-to-test-the-rule)
3. [Belirtilen kural için dışlamalar ekleme](#add-exclusions-for-a-false-positive) (hatalı pozitif sonuçlar için)
4. [Destek günlüklerini gönderme](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Önkoşulları onaylayın

Saldırı yüzeyini azaltma kuralları yalnızca aşağıdaki koşulların geçerli olduğu cihazlarda çalışır:

- Uç noktalar, sürüm Windows 10 Enterprise 1709'da (Fall Creators Update olarak da bilinir) çalışıyor.

- Uç noktalar, Microsoft Defender Virüsten Koruma virüsten koruma uygulaması olarak E-posta uygulamasını kullanıyor. [Başka herhangi bir virüsten koruma uygulaması kullanmak, Microsoft Defender Virüsten Koruma devre dışı bırakılamayacak kadar çok neden olur](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [Gerçek zamanlı koruma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) etkinleştirilir.

- Denetim modu etkinleştirilmedi. Saldırı yüzeyini azaltma kurallarını etkinleştirme konusunda açıklandığı **gibi kuralı** Devre Dışı (değer: **0**) [olarak ayarlamak için Grup İlkesi kullanın](enable-attack-surface-reduction.md).

Bu önkoşulların hepsi karşı kullandısa, denetimi modunda kuralı test etmek için bir sonraki adıma geçin.

## <a name="use-audit-mode-to-test-the-rule"></a>Kuralı test etmek için denetim modunu kullanma

Saldırı yüzeyini azaltma kurallarının genellikle bir cihazda önceden yapılandırılmış senaryolar ve işlemler için çalıştığını onaylamak üzere [demo.wd.microsoft.com Windows Defender](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Test temel web sitesini ziyaret edebilirsiniz veya yalnızca raporlama kurallarını sağlayan denetim modunu kullanabilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Sorunla karşılaştığınız [belirli kuralı test](evaluate-attack-surface-reduction.md) etmek için saldırı yüzeyini azaltma kurallarının nasıl çalışıp çalışmadı yerine tanıtım aracını kullanma altında verilen bu yönergeleri izleyin.

1. Test etmek istediğiniz belirli bir kural için denetim modunu etkinleştirin. Saldırı yüzeyini azaltma kurallarını etkinleştirme konusunda açıklandığı **gibi** kuralı Denetim modu (değer: **2**) [olarak ayarlamak için Grup İlkesi kullanın](enable-attack-surface-reduction.md). Denetim modu kuralın dosyayı veya işlemi bildirmesine izin verir, ancak yine de çalışmasına izin verir.

2. Soruna neden olan etkinliği gerçekleştirme (örneğin, engellenmiş ancak izin verilen bir dosya veya işlemi açın veya yürütün).

3. [Saldırı yüzeyini azaltma kuralı olay günlüklerini](attack-surface-reduction.md) gözden geçirin ve kuralın, kural Etkin olarak ayarlanmışsa dosya veya işlemi engellemiş olup olacağını **görmek için.**

Bir kural engellemesi gereken bir dosya veya işlemi engelliyorsa, önce denetim modunun etkin olup olmadığını kontrol edin.

Denetim modu başka bir özelliği test etmek için veya otomatik bir PowerShell betiği tarafından etkinleştirilmiştir ve sınamalar tamamlandıktan sonra devre dışı bırakılamaz.

Kuralı tanıtım aracıyla ve denetim moduyla test ettiyseniz ve saldırı yüzeyini azaltma kuralları önceden yapılandırılmış senaryolarda çalışıyor ancak kural beklendiği gibi çalışmıyorsa, sizin durumunuz temel alarak aşağıdaki bölümlerden biri ile devam edin:

1. Saldırı yüzeyini azaltma kuralı engellemediği bir şeyi engelliyorsa (hatalı pozitif olarak da bilinir), öncelikle saldırı yüzeyini azaltma kuralı [dışlama eklersiniz](#add-exclusions-for-a-false-positive).

2. Saldırı yüzeyini azaltma kuralı engellemesi gereken bir şeyi (yanlış negatif olarak da bilinir) engelliyorsa, tanılama verilerini toplayarak ve sorunu bize göndererek son adıma hemen [geçebilirsiniz](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>Hatalı pozitif sonuç için dışlama ekleme

Saldırı yüzeyini azaltma kuralı engellemediği bir şeyi engelliyorsa (bunun yanı sıra hatalı pozitif olarak da bilinir) saldırı yüzeyini azaltma kurallarının hariç tutulan dosyaları veya klasörleri değerlendirmesini engellemek için dışlamalar  eklemeniz gerekir.

Dışlama eklemek için Bkz. Saldırı [yüzeyini azaltmayı özelleştirme](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> Hariç tutulacak tek tek dosyaları ve klasörleri belirtebilirsiniz, ancak tek tek kuralları belirtamazsınız.
> Bu, dışlanan tüm dosyaların veya klasörlerin tüm ASR kuralları dışında tutulacakları anlamına gelir.

## <a name="report-a-false-positive-or-false-negative"></a>Hatalı pozitif veya hatalı negatif sonuçlar bildirme

Ağ koruması [Windows Defender hatalı negatif veya hatalı](https://www.microsoft.com/wdsi/filesubmission) pozitif bir sonuç olduğunu rapor etmek için Akıllı Güvenlik Zekası web tabanlı gönderme formunu kullanın. Windows E5 aboneliğiyle, ilgili [uyarılara bağlantı da sebilirsiniz](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>Dosya gönderimleri için tanılama verilerini toplama

Saldırı yüzeyini azaltma kurallarıyla ilgili bir sorun bildirerek, microsoft desteği ve mühendislik ekipleri tarafından sorunların giderilmesine yardımcı olmak için kullanılmaktadır.

1. Yükseltilmiş bir komut istemi açın ve Windows Defender olarak değiştirme:

   ```console
   cd "c:\program files\windows defender"
   ```

2. Tanılama günlüklerini oluşturmak için bu komutu çalıştırın:

   ```console
   mpcmdrun -getfiles
   ```

3. Varsayılan olarak, 'a kaydedilirler `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. Dosyayı gönderme formuna ekleme.

## <a name="related-articles"></a>İlgili makaleler

- [Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md)
- [Saldırı yüzeyini azaltma kurallarını etkinleştirin](enable-attack-surface-reduction.md)
- [Saldırı yüzeyini azaltma kurallarını değerlendirin](evaluate-attack-surface-reduction.md)
