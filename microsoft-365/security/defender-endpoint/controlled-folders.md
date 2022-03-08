---
title: Denetimli klasör erişimiyle dosyalarınızı şifrelemeye karşı önemli klasörleri fidye yazılımlarından koruyun
description: Varsayılan klasörlerdeki dosyalar, kötü amaçlı uygulamalar tarafından değiştirilebilir. Fidye yazılımlarının dosyalarınızı şifrelemesini engelin.
keywords: denetimli klasör erişimi, windows 10, windows Defender, fidye yazılımı, koruma, dosyalar, klasörler
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
ms.openlocfilehash: ea3e45a5469c9769f55f9ce90f799c54556de814
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322905"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Denetimli klasör erişimiyle önemli klasörleri koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Denetimli klasör erişimi nedir?

Denetimli klasör erişimi, değerli verilerinizin fidye yazılımı gibi kötü amaçlı uygulamalara ve tehditlere karşı korunmasına yardımcı olur. Denetimli klasör erişimi, uygulamaları bilinen, güvenilen uygulamalar listesine göre kontrol ederek verilerinizi korur. Windows Server 2019, Windows Server 2022, Windows 10 ve Windows 11 istemcisinde desteklenen denetimli klasör erişimi Windows Güvenliği Uygulaması kullanılarak açabilirsiniz. Microsoft Endpoint Configuration Manager veya Intune (yönetilen cihazlar için).

> [!NOTE]
> Komut dosyası altyapıları güvenilir değildir ve denetimli klasörlere erişmelerine izin vermezsiniz. Örneğin, sertifika ve dosya göstergeleriyle izin versanız bile denetimli klasör erişimi [PowerShell'e güvenilmiyor](/microsoft-365/security/defender-endpoint/indicator-certificates).

Denetimli klasör erişimi en iyi şekilde Uç Nokta için [Microsoft Defender'la](microsoft-defender-endpoint.md) çalışır. Bu, size denetimli klasör erişimi olaylarına ve bloklara her zamanki uyarı soruşturma senaryolarının bir parçası olarak ayrıntılı [raporlama sağlar](investigate-alerts.md).

> [!TIP]
> Denetimli klasör erişim blokları, Uyarılar sırasında [uyarı oluşturmaz](alerts-queue.md). Ancak, gelişmiş arama kullanırken veya özel algılama kurallarıyla cihaz [zaman](investigate-machines.md) çizelgesi görünümünde denetimli [klasör erişim](advanced-hunting-overview.md) blokları hakkında [bilgileri görüntüebilirsiniz](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>Denetimli klasör erişimi nasıl çalışır?

Denetimli klasör erişimi, yalnızca güvenilen uygulamaların korumalı klasörlere erişmesına izin vererek çalışır. Denetimli klasör erişimi yapılandırıldığında korumalı klasörler belirtilir. Belgeler, resimler, indirmeler ve diğer öğeler için kullanılanlar gibi yaygın olarak kullanılan klasörler, denetimli klasörler listesine eklenir.

Denetimli klasör erişimi güvenilen uygulamalar listesiyle çalışır. Güvenilir yazılım listesine dahil edilen uygulamalar beklendiği gibi çalışır. Listede yer alan uygulamaların korumalı klasörler içindeki dosyalarda değişiklik yapmaları engellenebilir.

Uygulamalar, yaygınlık ve itibarına bağlı olarak listeye eklenir. Kuruluş genelinde yaygın olarak yaygın olarak yaygın olarak görülen ve hiçbir zaman kötü amaçlı olduğu kabul edilen uygulamalar güvenilir kabul edilir. Bu uygulamalar listeye otomatik olarak eklenir.

Uygulamalar, Configuration Manager veya Intune kullanılarak güvenilir listeye el ile de eklenebilir. Web portalında ek Microsoft 365 Defender yapılabilir.

## <a name="why-controlled-folder-access-is-important"></a>Denetimli klasör erişimi neden önemlidir?

Denetimli klasör erişimi, belgelerinizi ve bilgileri fidye yazılımlarına karşı korumaya yardımcı olmak için özellikle [kullanışlıdır](https://www.microsoft.com/wdsi/threats/ransomware). Fidye yazılımı saldırılarında, dosyalarınız şifrelenir ve devamını alır. Denetimli klasör erişimi yerine, uygulamanın korumalı klasördeki bir dosyada değişiklik yapmaya çalıştığınız bilgisayarda bir bildirim görüntülenir. Bildirimi [şirket ayrıntılarınız](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) ve iletişim bilgileriyle özelleştirebilirsiniz. Ayrıca, bu özelliğin hangi teknikleri izler? tekniklerini özelleştirmek için kuralları tek tek etkinleştirebilirsiniz.

Korumalı [klasörler yaygın sistem](#review-controlled-folder-access-events-in-windows-event-viewer) klasörlerini (önyükleme önyüklemesi dahil) içerir ve daha [fazla klasör eklersiniz](customize-controlled-folders.md#protect-additional-folders). Ayrıca, uygulamaların [onlara korumalı](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) klasörlere erişim vermelerine de izin veebilirsiniz.

Denetim modunu kullanarak [denetimli klasör](audit-windows-defender.md) erişiminin, etkinleştirilmişse bu erişimin organizasyonlarınızı nasıl etkiley olacağını değerlendirebilirsiniz. Ayrıca, özelliğin çalıştığını onaylamak Windows Defender nasıl çalıştığını görmek [için demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Temel test web sitesini ziyaret edebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Denetimli klasör erişimi aşağıdaki dosya sürümlerinde Windows:

- [Windows 10, sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) ve sonrası
- Windows 11
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows klasörleri varsayılan olarak korumalıdır

Windows klasörleri, diğer birçok klasörle birlikte varsayılan olarak korunur:

Korumalı klasörler yaygın sistem klasörlerini (önyükleme önyüklemesi dahil) içerir ve ek klasörler  eklersiniz. Ayrıca, uygulamaların onlara korumalı klasörlere erişim vermelerine de izin veebilirsiniz.  Varsayılan Windows korunan sistem klasörleri aşağıdaki gibi olur:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

Varsayılan klasörler kullanıcının profilinde, Bu Bilgisayar **altında görünür**.
   > [!div class="mx-imgBorder"]
   > ![Korumalı Windows sistem klasörleri](images/defaultfolders.png)

> [!NOTE]
> Ek klasörleri korumalı olarak yapılandırabilirsiniz, ancak varsayılan olarak Windows olan sistem klasörlerini kaldıramazsınız.

## <a name="requirements-for-controlled-folder-access"></a>Denetimli klasör erişimi gereksinimleri

Denetimli klasör erişimi için gerçek [Microsoft Defender Virüsten Koruma etkinleştirilmesi gerekir](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında denetimli klasör erişimi Microsoft 365 Defender gözden geçirme

Uç Nokta için Defender, Microsoft 365 Defender portalında uyarı soruşturma senaryoları kapsamında olaylara [](investigate-alerts.md) ve bloklara ayrıntılı raporlama sağlar. bkz. [Microsoft 365 Defender'te Uç Nokta için Microsoft Defender](../defender/microsoft-365-security-center-mde.md).

Gelişmiş arama kullanarak Uç nokta verileri için Microsoft Defender'ı [sorguabilirsiniz](advanced-hunting-overview.md). Denetim modunu kullanıyorsanız, [denetimli](audit-windows-defender.md) klasör erişimi ayarlarının [](advanced-hunting-overview.md) etkinleştirilmişse ortamınızı nasıl etkileyeceğini görmek için gelişmiş arama kullanabilirsiniz.

Örnek sorgu:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Olay Görüntüleyicisi'nde denetimli klasör Windows olaylarını gözden geçirme

Denetimli klasör erişim Windows (veya denetimler) bir uygulama sırasında oluşturulan olayları görmek için bu olay günlüğünü gözden geçirebilirsiniz:

1. Değerlendirme [Paketi'i](https://aka.ms/mp7z2w) indirin ve *cfa-events.xml* cihazda kolayca erişilebilir bir konuma ulaşacak şekilde dosyayı ayıklayabilirsiniz.
2. Olay **Görüntüleyicisi'ni** Başlat menüsü için ekrana Olay Windows yazın.
3. Sol panelde, Eylemler'in **altında Özel** görünümü **içeri aktar... öğesini seçin**.
4. Metin ayıklamak istediğiniz *cfa-events.xml* seçin. Alternatif olarak, [XML'yi doğrudan kopyalayın](event-views.md).
5. **Tamam**'ı seçin.

Aşağıdaki tablo denetimli klasör erişimiyle ilgili olayları gösterir:

<br/><br/>

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarların değiştir olduğu olay|
|1124|Denetlenen denetimli klasör erişimi olayı|
|1123|Denetlenen klasör erişimi olayı engellendi|

## <a name="view-or-change-the-list-of-protected-folders"></a>Korumalı klasörler listesini görüntüleme veya değiştirme

Denetimli klasör erişimi Windows Güvenliği klasörlerin listesini görüntülemek için Windows Güvenliği uygulamasını kullanabilirsiniz.

1. Windows 10 veya Windows 11 cihazınızın Windows Güvenliği açın.
2. Virüs **ve tehdit &'yi seçin**.
3. Fidye **yazılımı koruması'nın** altında Fidye yazılımı **korumasını yönet'i seçin**.
4. Denetimli klasör erişimi kapalı ise bu erişimi açabilirsiniz. Korumalı **klasörler'i seçin**.
5. Aşağıdaki adımlardan birini yapın:
   - Klasör eklemek için + **Korumalı klasör ekle'yi seçin**.
   - Bir klasörü kaldırmak için klasörü seçin ve sonra Kaldır'ı **seçin**.

> [!NOTE]
> [Windows klasörleri varsayılan](#windows-system-folders-are-protected-by-default) olarak korumalıdır ve bunları listeden kaldıramazsınız.
