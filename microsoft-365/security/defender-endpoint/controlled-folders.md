---
title: Önemli klasörleri fidye yazılımlarından, dosyalarınızı denetimli klasör erişimiyle şifrelemeye karşı koruma
description: Varsayılan klasörlerdeki dosyalar kötü amaçlı uygulamalar tarafından değiştirilmeye karşı korunabilir. Fidye yazılımlarının dosyalarınızı şifrelemesini önleyin.
keywords: denetimli klasör erişimi, windows 10, windows defender, fidye yazılımı, koruma, dosyalar, klasörler
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 02017a614544cfb10eb43d375212fc7e37124ad3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840397"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Denetimli klasör erişimiyle önemli klasörleri koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Uygulandığı öğe**
- Windows


> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Denetimli klasör erişimi nedir?

Denetimli klasör erişimi değerli verilerinizi fidye yazılımı gibi kötü amaçlı uygulamalardan ve tehditlerden korumaya yardımcı olur. Denetimli klasör erişimi, uygulamaları bilinen, güvenilen uygulamalar listesine karşı denetleyerek verilerinizi korur. Windows Server 2019, Windows Server 2022, Windows 10 ve Windows 11 istemcilerinde desteklenen denetimli klasör erişimi, Windows Güvenliği Uygulaması kullanılarak açılabilir. Microsoft Endpoint Configuration Manager veya Intune (yönetilen cihazlar için).

> [!NOTE]
> Betik altyapılarına güvenilmez ve denetimli korumalı klasörlere erişmelerine izin veremezsiniz. Örneğin, [sertifika ve dosya göstergeleriyle](/microsoft-365/security/defender-endpoint/indicator-certificates) izin verseniz bile PowerShell'e denetimli klasör erişimi tarafından güvenilmez.

Denetimli klasör erişimi, her zamanki [uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak denetimli klasör erişimi olayları ve blokları hakkında ayrıntılı raporlama sağlayan [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) ile en iyi şekilde çalışır.

> [!TIP]
> Denetimli klasör erişim blokları [Uyarılar kuyruğunda](alerts-queue.md) uyarı oluşturmaz. Ancak, [gelişmiş tehdit avcılığı](advanced-hunting-overview.md) kullanırken veya [özel algılama kurallarıyla](custom-detection-rules.md) denetimli klasör erişim blokları hakkındaki bilgileri [cihaz zaman çizelgesi görünümünde](investigate-machines.md) görüntüleyebilirsiniz.

## <a name="how-does-controlled-folder-access-work"></a>Denetimli klasör erişimi nasıl çalışır?

Denetimli klasör erişimi yalnızca güvenilen uygulamaların korumalı klasörlere erişmesine izin vererek çalışır. Denetimli klasör erişimi yapılandırıldığında korumalı klasörler belirtilir. Genellikle, belgeler, resimler, indirmeler vb. için kullanılanlar gibi yaygın olarak kullanılan klasörler, denetlenen klasörler listesine eklenir.

Denetimli klasör erişimi, güvenilen uygulamaların listesiyle çalışır. Güvenilir yazılım listesine dahil edilen uygulamalar beklendiği gibi çalışır. Listeye dahil edilmeyen uygulamaların korumalı klasörler içindeki dosyalarda değişiklik yapması engellenir.

Uygulamalar, yaygınlıkları ve saygınlıkları temelinde listeye eklenir. Kuruluşunuz genelinde yüksek oranda yaygın olan ve kötü amaçlı olarak kabul edilen hiçbir davranışı görüntülemeyen uygulamalar güvenilir kabul edilir. Bu uygulamalar otomatik olarak listeye eklenir.

Uygulamalar, Configuration Manager veya Intune kullanılarak güvenilir listeye el ile de eklenebilir. Microsoft 365 Defender portalından ek eylemler gerçekleştirilebilir.

## <a name="why-controlled-folder-access-is-important"></a>Denetimli klasör erişimi neden önemlidir?

Denetimli klasör erişimi, belgelerinizi ve bilgilerinizi [fidye yazılımlarından](https://www.microsoft.com/wdsi/threats/ransomware) korumaya yardımcı olmak için özellikle yararlıdır. Fidye yazılımı saldırısında dosyalarınız şifrelenebilir ve rehin tutulabilir. Denetimli klasör erişimi uygulandığında, bir uygulamanın korumalı klasördeki bir dosyada değişiklik yapmaya çalıştığı bilgisayarda bir bildirim görüntülenir. Bildirimi şirketinizin ayrıntıları ve iletişim bilgileriyle [özelleştirebilirsiniz](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) . Ayrıca, özelliklerin izlediği teknikleri özelleştirmek için kuralları tek tek etkinleştirebilirsiniz.

[Korumalı klasörler](#review-controlled-folder-access-events-in-windows-event-viewer) ortak sistem klasörlerini (önyükleme kesimleri dahil) içerir ve [daha fazla klasör ekleyebilirsiniz](customize-controlled-folders.md#protect-additional-folders). [Ayrıca uygulamaların](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) korumalı klasörlere erişmesine izin verebilirsiniz.

Denetim [modunu](audit-windows-defender.md) kullanarak denetimli klasör erişiminin kuruluşunuz etkinse nasıl etkilendiğini değerlendirebilirsiniz. Ayrıca Windows Defender Test zemini web sitesini [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) ziyaret ederek özelliğin çalıştığını onaylayabilir ve nasıl çalıştığını görebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Denetimli klasör erişimi aşağıdaki Windows sürümlerinde desteklenir:

- [Windows 10, sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) ve üzeri
- Windows 11
- Windows 2012 R2
- Windows 2016
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows sistem klasörleri varsayılan olarak korunur

Windows sistem klasörleri, diğer birkaç klasörle birlikte varsayılan olarak korunur:

Korumalı klasörler ortak sistem klasörlerini (önyükleme kesimleri dahil) içerir ve ek klasörler ekleyebilirsiniz. Ayrıca uygulamaların korumalı klasörlere erişmesine izin verebilirsiniz.  Varsayılan olarak korunan Windows sistemleri klasörleri şunlardır:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

Varsayılan klasörler kullanıcının profilinde **, Bu Bilgisayar** altında görünür.
   > [!div class="mx-imgBorder"]
   > ![Korumalı Windows varsayılan sistem klasörleri](images/defaultfolders.png)

> [!NOTE]
> Ek klasörleri korumalı olarak yapılandırabilirsiniz, ancak varsayılan olarak korunan Windows sistem klasörlerini kaldıramazsınız.

## <a name="requirements-for-controlled-folder-access"></a>Denetimli klasör erişimi gereksinimleri

Denetimli klasör erişimi Microsoft Defender Virüsten Koruma [gerçek zamanlı korumayı](configure-real-time-protection-microsoft-defender-antivirus.md) etkinleştirmeyi gerektirir.

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında denetimli klasör erişimi olaylarını gözden geçirme

Uç Nokta için Defender, Microsoft 365 Defender portalındaki [uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak olaylara ve bloklara ayrıntılı raporlama sağlar; bkz. [Microsoft 365 Defender'da Uç Nokta için Microsoft Defender](../defender/microsoft-365-security-center-mde.md).

[Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) kullanarak Uç Nokta için Microsoft Defender verileri sorgulayabilirsiniz. [Denetim modunu](audit-windows-defender.md) kullanıyorsanız, denetimli klasör erişim ayarlarının etkinleştirildiyse ortamınızı nasıl etkileyeceğini görmek için [gelişmiş avcılığı](advanced-hunting-overview.md) kullanabilirsiniz.

Örnek sorgu:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Windows Olay Görüntüleyicisi'de denetimli klasör erişimi olaylarını gözden geçirme

Denetimli klasör erişim blokları (veya denetimler) bir uygulama olduğunda oluşturulan olayları görmek için Windows olay günlüğünü gözden geçirebilirsiniz:

1. [Değerlendirme Paketi'ni](https://aka.ms/mp7z2w) indirin *vecfa-events.xmldosyayı* cihazda kolayca erişilebilen bir konuma ayıklayın.
2. Windows Olay Görüntüleyicisi açmak için Başlat menüsü **Olay görüntüleyicisi** yazın.
3. Sol paneldeki **Eylemler'in** altında **Özel görünümü içeri aktar...** öğesini seçin.
4. *cfa-events.xml* ayıkladığınız yere gidin ve seçin. Alternatif olarak [, XML'yi doğrudan kopyalayın](event-views.md).
5. **Tamam**'ı seçin.

Aşağıdaki tabloda, denetimli klasör erişimiyle ilgili olaylar gösterilmektedir:

<br/><br/>

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarlar değiştirildiğinde gerçekleşen olay|
|1124|Denetlenen denetimli klasör erişimi olayı|
|1123|Engellenen denetimli klasör erişimi olayı|

## <a name="view-or-change-the-list-of-protected-folders"></a>Korumalı klasörlerin listesini görüntüleme veya değiştirme

denetimli klasör erişimiyle korunan klasörlerin listesini görüntülemek için Windows Güvenliği uygulamasını kullanabilirsiniz.

1. Windows 10 veya Windows 11 cihazınızda Windows Güvenliği uygulamasını açın.
2. **Virüs ve tehdit koruması**’nı seçin.
3. **Fidye yazılımı koruması'nın** altında **Fidye yazılımı korumasını yönet'i** seçin.
4. Denetimli klasör erişimi kapalıysa, bunu açmanız gerekir. **Korumalı klasörler'i** seçin.
5. Aşağıdaki adımlardan birini yapın:
   - Klasör eklemek için **+ Korumalı klasör ekle'yi** seçin.
   - Bir klasörü kaldırmak için klasörü seçin ve ardından **Kaldır'ı** seçin.

> [!NOTE]
> [Windows sistem klasörleri](#windows-system-folders-are-protected-by-default) varsayılan olarak korunur ve bunları listeden kaldıramazsınız.
