---
title: Hesapları Güvenlik ve Uyumluluk Office 365 Yeni Güvenlik Merkezi'ne yeniden Microsoft 365 Defender
description: Office 365 için Defender'dan Microsoft 365 Defender.
keywords: Microsoft 365 Defender, Güvenlik merkezi yeniden Microsoft 365 Defender ile çalışmaya başlama
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.custom:
- admindeeplinkDEFENDER
- admindeeplinkEXCHANGE
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fc49494d924129ed2771bc399467f3e9101e7620
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010743"
---
# <a name="redirecting-accounts-from-office-365-security-and-compliance-center-to-microsoft-365-defender"></a>Hesapları Güvenlik ve Uyumluluk Office 365 Merkezi'ne yeniden yönlendirme Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Office 365 için Defender

Bu makalede, eski Office 365 Güvenlik ve Uyumluluk Merkezi'nde (protection.office.com) otomatik yeniden yönlendirmeyi etkinleştirerek, hesapları Microsoft 365 Defender'e nasıl Microsoft 365 Defender security.microsoft.com.

## <a name="what-to-expect"></a>Neler olabilir?

Otomatik yeniden yönlendirme etkinleştirildikten ve etkinleştirildikten sonra, Office 365 Güvenlik ve Uyumluluk (protection.office.com) içinde güvenlikle ilgili özelliklere erişen kullanıcılar otomatik olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a>

Nelerin değiştir olduğu hakkında daha fazla bilgi edinmek için: [Office 365 için Microsoft Defender Microsoft 365 Defender](microsoft-365-security-center-mdo.md).

Otomatik yeniden yönlendirme açıkken, kullanıcılar Güvenlik ve Uyumluluk Microsoft 365 Defender'nde güvenlik özelliklerini kullandıklarında Office 365'e yönlendirilenler.

Bunlar Tehdit Yönetimi bölümünde, Uyarılar (Uyarıları ve Uyarı İlkelerini Görüntüle) ve Tehdit Yönetimi panosu ve raporlarıyla raporlarında yer alan özellikleri içerir. Güvenlik ve Office 365 Merkezi'nde yer alan ve güvenlikle ilgili olan öğeler Güvenlik ve Uyumluluk Merkezi'ne Microsoft 365 Defender.

Uyumlulukla ilgili öğeler Genel Microsoft 365 uyumluluk merkezi ve posta akışıyla ilgili öğeler de Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">merkezinde bulunabilir</a>.

İster uyumlulukla ilgili ister her ikisini de hizmet eden özellikler olsun, diğer tüm özellikler yeniden yönlendirmeden etkilenmez.

### <a name="set-up-portal-redirection"></a>Portal yeniden yönlendirmesini ayarlama

2021 Ekim 2021'in başlangıcından itibaren, portal yeniden yönlendirmesi otomatik olarak veya varsayılan olarak  yapılır. Bununla birlikte, geçici olarak devre dışı bırakılması gerekirse, bu adımlar takip eder.

<!--To start routing accounts to Microsoft 365 Defender at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>:

1. Make sure you're a global administrator or have security administrator permissions in Azure Active directory.
2. Sign in to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.
3. Go to **Settings** > **Email & collaboration** > **Portal redirection**.  
4. Toggle the Automatic redirection setting to **On**.
5. Click **Enable** to apply automatic redirection to Microsoft 365 Defender.

> [!NOTE]
> After redirection is enabled, accounts in active sessions while this setting is applied will not be ejected from their session and will only be routed to Microsoft 365 Defender after ending their current session and signing back in again.-->

## <a name="can-i-go-back-to-using-the-former-portal"></a>Eski portalı kullanmaya geri gidebilir miyim?

Sizin için bir sorun varsa veya çalışmadan önce tamamlayamadığınız bir Microsoft 365 Defender, portal geri bildirim seçeneğini kullanarak bu konuda bilgi almak isteriz. Yeniden yönlendirmeyle ilgili sorunlarla karşılaştıysanız, lütfen bize haber verme.

Eski portala dönmek için:

1. Genel yönetici olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> veya Azure Active Directory'de güvenlik yöneticisi izinlerini kullanarak ve hesabınızla oturum açın.

2. İşbirliğini **Ayarlar** >  **Email & Portal** >  **yeniden yönlendirme'ye gidin**.

3. Otomatik yeniden yönlendirme ayarını Kapalı olarak **seçin**.

4. **İstendiğinde &'i** devre dışı bırak'a tıklayın.

Bu ayar herhangi bir zamanda yeniden etkinleştirilebilir.

## <a name="related-information"></a>İlgili bilgiler
- [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
- [Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md)
- [Microsoft, güvenlik işlemlerini modernleştirmek için birleşik SIEM ve XDR sağlar](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR ve SIEM bilgi grafiği](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [Daha fazla Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Microsoft güvenlik portalları ve yönetim merkezleri](portals.md)
