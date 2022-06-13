---
title: eKeşif tanılama bilgilerini toplama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: bir Microsoft Desteği olayı için eBulma tanılama bilgilerini toplama hakkında bilgi edinin.
ms.openlocfilehash: f5dba88a598a73441c67e3eaa08a59b7258ea712
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014442"
---
# <a name="collect-ediscovery-diagnostic-information"></a>eKeşif tanılama bilgilerini toplama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bazen Microsoft Desteği mühendisleri, Microsoft Purview eKeşif (Standart) veya Microsoft Purview eKeşif (Premium) ile ilgili bir destek olayı açtığınızda sorununuz hakkında belirli bilgiler gerektirir. Bu makalede, destek mühendislerinin sorunları araştırmasına ve çözmesine yardımcı olmak için tanılama bilgilerini toplama konusunda rehberlik sağlanır. Genellikle, bir Microsoft Desteği mühendisi tarafından isteninceye kadar bu bilgileri toplamanız gerekmez.

> [!IMPORTANT]
> Bu makalede açıklanan cmdlet'lerden ve tanılama bilgilerinden elde edilen çıkış, kuruluşunuzdaki davalar veya iç soruşturmalar hakkında hassas bilgiler içerebilir. ham tanılama bilgilerini Microsoft Desteği göndermeden önce, bilgileri gözden geçirmeli ve yerine ile değiştirerek `XXXXXXX`hassas bilgileri (dava veya soruşturma tarafları hakkında adlar veya diğer bilgiler gibi) yeniden dağıtmanız gerekir. Bu yöntemin kullanılması, Microsoft Desteği mühendisine bilgilerin yeniden dağıtıldığını da gösterir.

## <a name="collect-diagnostic-information-for-ediscovery-standard"></a>eBulma için tanılama bilgilerini toplama (Standart)

eBulma (Standart) için tanılama bilgilerini toplama cmdlet tabanlıdır, bu nedenle Güvenlik & Uyumluluk PowerShell'i kullanmanız gerekir. Aşağıdaki PowerShell örnekleri cmdlet'leri çalıştırır ve çıkışı belirtilen bir metin dosyasına kaydeder. Çoğu destek durumunda, bu komutlardan yalnızca birini çalıştırmanız gerekir.

Aşağıdaki cmdlet'leri çalıştırmak [için Güvenlik & Uyumluluk PowerShell'e bağlanın</span>](/powershell/exchange/connect-to-scc-powershell). Bağlandıktan sonra aşağıdaki komutlardan birini veya daha fazlasını çalıştırın ve yer tutucuları gerçek nesne adlarıyla değiştirdiğinizden emin olun.

Oluşturulan metin dosyasını gözden geçirdikten ve hassas bilgileri yeniden işledikten sonra, olayınız üzerinde çalışan Microsoft Desteği mühendisine gönderin.

> [!NOTE]
> Microsoft Purview uyumluluk portalındaki **İçerik arama** sayfasında listelenen aramalar ve dışarı aktarmalar için tanılama bilgilerini toplamak için bu bölümdeki komutları da çalıştırabilirsiniz.

### <a name="collect-information-about-searches"></a>Aramalar hakkında bilgi toplama

Aşağıdaki komut, bir İçerik aramasıyla veya eBulma (Standart) olayıyla ilişkili aramayla ilgili sorunları araştırırken yararlı olan bilgileri toplar.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Arama eylemleri hakkında bilgi toplama

Aşağıdaki komut, bir İçerik aramasının veya eBulma (Standart) olayıyla ilişkili bir aramanın sonuçlarını önizleme, dışarı aktarma veya temizleme ile ilgili sorunları araştırmak için bilgi toplar. **Dışarı Aktarmalar** sekmesinde listelenen bir dışarı aktarmaya tıklayarak arama eyleminin adını tanımlayabilirsiniz. Önizleme ve temizleme eylemlerinin adlarını tanımlamak için **Get-ComplianceSearchAction** cmdlet'ini çalıştırarak tüm eylemlerin listesini görüntüleyebilirsiniz. Arama eylemi adının biçimi, veya ilgili aramanın adına eklenerek `_Preview``_Export``_Purge` oluşturulur.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>eBulma tutmaları hakkında bilgi toplama

Bir eBulma (Standart) olayıyla ilişkilendirilmiş bir eBulma ayrı tutması beklendiği gibi çalışmadığında, eBulma ayrı tutması için Servis Talebi Tutma İlkesi ve ilişkili Servis Talebi Tutma Kuralı hakkında bilgi toplamak için aşağıdaki komutu çalıştırın. Aşağıdaki komuttaki *Büyük/küçük harf saklama ilkesi adı* , eBulma saklama adıyla aynıdır. Bu adı eBulma (Standart) durumundaki **Ayrı Tutmalar** sekmelerinde tanımlayabilirsiniz.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Tüm servis talebi bilgilerini toplama

Bazen sorununuzu araştırmak için Microsoft Desteği hangi bilgilerin gerekli olduğu belirgin değildir. Bu durumda, eBulma (Standart) olayı için tüm tanılama bilgilerini toplayabilirsiniz. Aşağıdaki komuttaki *eBulma (Standart) büyük/küçük harf adı* , uyumluluk portalındaki **eBulma (Standart)** sayfasında görüntülenen servis talebi adıyla aynıdır.

```powershell
Get-ComplianceCase "<eDiscovery (Standard) case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-ediscovery-premium"></a>eBulma (Premium) için tanılama bilgilerini toplama

eBulma (**Premium**) durumundaki Ayarlar sekmesi, servis talebi için tanılama bilgilerini hızla kopyalamanıza olanak tanır. Tanılama bilgileri panoya kaydedilir, böylece bunu bir metin dosyasına yapıştırabilir ve Microsoft Desteği gönderebilirsiniz.

1. Uyumluluk portalına gidin ve **eBulma Gelişmiş'i** >  seçin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. Bir servis talebi seçin ve **Ayarlar** sekmesine tıklayın.

3. **Servis Talebi Bilgileri'nin** altında **Seç'e** tıklayın.

4. Açılır sayfada **Eylemler** > **Destek bilgilerini kopyalama'ya** tıklayarak bilgileri panoya kopyalayın.

5. Bir metin dosyası açın (Not Defteri) ve ardından bilgileri metin dosyasına yapıştırın.

6. Metin dosyasını kaydedin ve gibi `AeD Diagnostic Info YYYY.MM.DD` bir ad verin (örneğin, `AeD Diagnostic Info 2020.11.03`).

Dosyayı gözden geçirdikten ve hassas bilgileri yeniden işledikten sonra, olayınız üzerinde çalışan Microsoft Desteği mühendisine gönderin.
