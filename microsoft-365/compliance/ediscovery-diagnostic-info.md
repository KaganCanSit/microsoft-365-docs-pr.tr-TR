---
title: eBulma tanılama bilgilerini toplama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Bir Microsoft Desteği durumu için eKbulma tanılama bilgilerini toplamayı öğrenin.
ms.openlocfilehash: cab21c71168119b27a478b99a19ad5693ffb678e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021606"
---
# <a name="collect-ediscovery-diagnostic-information"></a>eBulma tanılama bilgilerini toplama

Core eDiscovery veya Advanced eDiscovery ile ilgili bir destek vakası açarken, Microsoft Destek mühendisleri zaman zaman sorun hakkında özel Advanced eDiscovery. Bu makalede, destek mühendislerinin sorunları araştırmasını ve çözmesini sağlayan tanılama bilgilerini toplama konusunda yol gösterici bilgiler yer almaktadır. Normalde, bir Microsoft Destek mühendisi tarafından sorulana kadar bu bilgileri toplamaya gerek yok.

> [!IMPORTANT]
> Bu makalede açıklanan cmdlet'lerden ve tanılama bilgilerinden alınan çıktı, kurum davaları veya iç soruşturmalar hakkında hassas bilgiler içerebilir. Ham tanılama bilgilerini Microsoft Desteği'ne göndermeden önce, yerine 'i kullanarak bilgileri gözden geçirmeli ve tüm hassas bilgileri (mahkemeler veya soruşturmalar için taraflar hakkında adlar veya diğer bilgiler gibi) yeniden işlemle incelemelisiniz `XXXXXXX`. Bu yöntemin kullanımı, Microsoft Destek mühendisine bilgilerin redacted olduğunu da belirtecek.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>Core eKovery için tanılama bilgilerini toplama

Core eDiscovery için tanılama bilgilerini toplama cmdlet tabanlıdır, dolayısıyla PowerShell'de Güvenlik ve Uyumluluk &'ı kullanacağız. Aşağıdaki PowerShell örnekleri cmdlet'leri çalıştıracak ve sonra çıkışı belirtilen bir metin dosyasına kaydedecek. Çoğu destek durumda, bu komutlardan yalnızca birini çalıştırmalısınız.

Aşağıdaki cmdlet'leri çalıştırmak için Güvenlik [ve Uyumluluk & PowerShell'e bağlanın</span>](/powershell/exchange/connect-to-scc-powershell). Bağlandıktan sonra, aşağıdaki komutlardan birini veya birkaçı çalıştırın ve yer tutucuları gerçek nesne adlarla değiştirdikten emin olun.

Oluşturulan metin dosyasını gözden geçirdikten ve hassas bilgileri yeniden işlemden geçirildikten sonra, dosyanız üzerinde çalışan Microsoft Desteği mühendisine gönderin.

> [!NOTE]
> Ayrıca bu bölümdeki komutları çalıştırarak, ilgili bölümdeki İçerik arama sayfasında listelenen arama ve dışarı **aktarmalar** için tanılama bilgilerini Microsoft 365 uyumluluk merkezi.

### <a name="collect-information-about-searches"></a>Aramalar hakkında bilgi toplama

Aşağıdaki komut, İçerik arama veya Çekirdek eBulma olayıyla ilişkilendirilmiş bir aramayla ilgili sorunları incelerken yararlı olacak bilgileri toplar.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Arama eylemleri hakkında bilgi toplama

Aşağıdaki komut, İçerik aramanın veya Çekirdek eKbulma durumuyla ilişkilendirilmiş bir aramanın sonuçlarını önizleme, dışarı aktarma veya temizleme sorunlarını araştırmayla ilgili bilgi toplar. Dışarı Aktarmalar sekmesinde listelenen bir dışarı aktarmaya tıklayarak, arama eyleminin adını **tanımlayabilirsiniz** . Önizleme ve temizleme eylemlerinin adlarını tanımlamak için, **Get-ComplianceSearchAction cmdlet'ini** çalıştırarak tüm eylemlerin listesini görüntüebilirsiniz. Arama eylem adının biçimi, , ekinde `_Preview`veya `_Export`ilgili aramanın `_Purge` adına ek adıyla oluşturulur.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>eBulma 3- 6

Çekirdek eBulma durumuyla ilişkilendirilmiş bir eBulma ayrımı beklendiği gibi çalışmıyorsa, eBulma ayrımı için Büyük/Küçük Harf Ayrımı İlkesi ve ilişkili Büyük/Küçük Harf Ayrımı Kuralı hakkında bilgi toplamak için aşağıdaki komutu çalıştırın. Aşağıdaki *komutta yer alan* Büyük/kısa süre tutma ilkesi adı, eBulma ayrımı ile aynıdır. Bu adı, Çekirdek **eKbulma durumundaki** Esnat sekmelerinde tanımlayabilirsiniz.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Tüm vaka bilgilerini toplama

Bazen, Microsoft Desteği'nin sorunlarınızı araştırması için gereken bilgilerin ne olduğu görünür olmaz. Bu durumda, Çekirdek eBulma durumu için tüm tanılama bilgilerini toplayabilirsiniz. Aşağıdaki komutta yer alan **Core eDiscovery** olay adı, aşağıdaki komutun Core *eDiscovery* sayfasında görüntülenen vakanın adıyla Microsoft 365 uyumluluk merkezi.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>Tanılama bilgilerini Advanced eDiscovery

Büyük **Ayarlar** Durum sekmesinde Advanced eDiscovery durum için tanılama bilgilerini hızla kopyalamanız gerekir. Tanılama bilgileri panoya kaydedilir ve böylece bir metin dosyasına yapıştırarak Microsoft Desteği'ne gönderebilirsiniz.

1. Takvime gidin Microsoft 365 uyumluluk merkezi **eDiscoveryAdvanced** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**öğesini seçin**</a>.

2. Bir büyük/küçük harf seçin ve sonra **Ayarlar** tıklayın.

3. Büyük **/Küçük Harf Bilgileri'nin** altında **Seç'e tıklayın**.

4. Uçarak çıkış sayfasında, ActionsCopy **destek** >  **bilgilerini tıklatın ve** bilgileri panoya kopyalayın.

5. Bir metin dosyası açın (Not Defteri) ve bilgileri metin dosyasına yapıştırın.

6. Metin dosyasını kaydedin ve benzer bir ad `AeD Diagnostic Info YYYY.MM.DD` (örneğin, `AeD Diagnostic Info 2020.11.03`).

Dosyayı gözden geçirdikten ve hassas bilgileri yeniden işlemden geçirdikten sonra, dosyanız üzerinde çalışan Microsoft Destek mühendisine gönderin.
