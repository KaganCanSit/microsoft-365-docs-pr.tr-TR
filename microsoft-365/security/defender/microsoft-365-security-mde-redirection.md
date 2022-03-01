---
title: Hesapları Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender
description: Uç nokta için Defender'dan hesapları ve oturumları yeniden yönlendirme ve Microsoft 365 Defender.
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 64a9926253ea699fa6cc62d1ec2d80d07f25fd29
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010737"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>Hesapları Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Defender

SIEM ve Genişletilmiş algılama ve yanıt (XDR) ile Microsoft'un etki alanı arası tehdit koruması yaklaşımıyla uyumlu olarak, Uç Nokta için Microsoft Defender olarak Microsoft Defender Gelişmiş Tehdit Koruması'nın markasını yeniden marka kullandık ve tek bir tümleşik portalda bir araya Microsoft 365 Defender.

Bu kılavuzda, eski Uç Nokta portalı için Microsoft Defender portalında (securitycenter.windows.com veya securitycenter.microsoft.com) otomatik yeniden yönlendirmeyi etkinleştirerek hesapları Microsoft 365 Defender'e nasıl <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

> [!NOTE]
> Microsoft 365 Defender'daki Uç Nokta için Microsoft Defender, aynı İnternet sitesinde erişim verilen şekilde yönetilen güvenlik hizmeti [sağlayıcılarına (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) [erişim Microsoft Defender Güvenlik Merkezi](./mssp-access.md).

## <a name="what-to-expect"></a>Neler olabilir?

Otomatik yeniden yönlendirme etkinleştirildikten sonra, securitycenter.windows.com veya securitycenter.microsoft.com'de uç nokta portalı için eski Microsoft Defender portalına erişen hesaplar otomatik olarak Microsoft 365 Defender portalında <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><security.microsoft.com></a>.

Nelerin değiştir olduğu hakkında daha fazla bilgi edinmek için: [Microsoft 365 Defender'te Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md).

Bu, e-posta bildirimlerinin bağlantıları ve SIEM API aramaları tarafından döndürülen bağlantılar gibi, eski securitycenter.windows.com portalına doğru olan bağlantılar da dahil olmak üzere, tarayıcı yoluyla eski portala doğrudan erişim için yeniden yönlendirme içerir.  

 E-posta bildirimleri veya SIEM API'lerinden gelen dış bağlantılar şu anda her iki portalın da bağlantılarını içerir. Yeniden yönlendirme etkinleştirildikten sonra, her iki bağlantı da Microsoft 365 Defender bir süre sonra kaldırılana kadar bu bağlantıyı gösterir. Bu yeni sayfaya işaret eden yeni bağlantıyı Microsoft 365 Defender.

Bağlantılar ve yönlendirme hakkında daha fazla bilgi için aşağıdaki tabloya bakın.
## <a name="siem-api-routing"></a>SIEM API yönlendirmesi

| Özellik | Yönlendirme KAPALı olduğunda hedef | YönlendirmeNIN ON olduğu hedef |
|---------|---------|---------|
| LinkToWDATP | Securitycenter.windows.com'de uyarı securitycenter.windows.com | Sayfa içinde security.microsoft.com |
| IncidentLinkToWDATP | Olay securitycenter.windows.com | Olay security.microsoft.com |
| LinkToMTP | Sayfa içinde security.microsoft.com | Sayfa içinde security.microsoft.com |
| IncidentLinkToMTP | Olay security.microsoft.com | Olay security.microsoft.com |

## <a name="email-alert-notifications"></a>E-posta uyarısı bildirimleri

| Özellik | Yönlendirme KAPALı olduğunda hedef** | YönlendirmeNIN ON olduğu hedef |
|---------|---------|---------|
| Uyarı sayfası | Securitycenter.windows.com'de uyarı securitycenter.windows.com | Sayfa içinde security.microsoft.com |
| Olay sayfası |Olay securitycenter.windows.com | Olay security.microsoft.com |
| Bulut portalı için Defender'daki uyarı sayfası | Sayfa içinde security.microsoft.com | Sayfa içinde security.microsoft.com |
| Bulut portalı için Defender'daki olay sayfası | Olay security.microsoft.com | Olay security.microsoft.com |

## <a name="when-does-this-take-effect"></a>Bu durum ne zaman etkili olur?

Etkinleştirildikten sonra, bu güncelleştirme bazı hesaplarda neredeyse hemen yürürlüğe girecektir. Ancak yeniden yönlendirmenin, kurumuz daki her hesaba yayılması daha uzun sürebilir. Bu ayar uygulandığında etkin oturumlarda yer alan hesaplar kendi oturumlarından çıkarlanmaz ve yalnızca geçerli oturumlarını bitirdikten ve yeniden oturum Microsoft 365 Defender sonra Microsoft 365 Defender'e yönlendirilene kadar devam edecek.  

### <a name="set-up-portal-redirection"></a>Portal yeniden yönlendirmesini ayarlama

Hesapları başka bir hesaba yönlendirmeyi Microsoft 365 Defender:

1. Bu hizmette genel yönetici veya güvenlik yöneticisi izinlerine sahip Azure Active Directory.

2. E-Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">.</a>

3. **Ayarlar** >  **EndpointsGeneralPortal** >  >  **yeniden yönlendirmesi'ne gidin veya** [buraya tıklayın](https://security.microsoft.com/preferences2/portal_redirection).  

4. Otomatik yeniden yönlendirme ayarını Açık olarak **değiştir.**

5. Çalışma **sayfasına** otomatik yeniden yönlendirme uygulamak için Etkinleştir'Microsoft 365 Defender.

>[!IMPORTANT]
>Bu ayarın etkinleştirilmesi, etkin kullanıcı oturumlarını sonlandırmaz. Bu ayar uygulandığı sırada etkin bir oturumda olan hesaplar, yalnızca geçerli oturumlarını bitirdikten Microsoft 365 Defender yeniden oturum açıldıktan sonra Oturum Açma'ya yönlendirildi.

>[!NOTE]
>Bu ayarı etkinleştirmek veya devre dışı bırakmak için genel yönetici olmalı veya Azure Active Directory yönetici izinlerine sahip olasınız.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Eski portalı kullanmaya geri gidebilir miyim?

Sizin için bir sorun yoksa veya çalışma süreniz boyunca tamamlayamadığınız bir Microsoft 365 Defender, bu konuda bilgi almak isteriz. Yeniden yönlendirmeyle ilgili sorunlarla karşılaştınızsa, Geri bildirim gönderme formuyla bize bunu haber vermenizi tavsiye ederiz.

Uç nokta portalı için eski Microsoft Defender'a geri dönmek için:

1. Genel yönetici olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> veya Azure Active Directory'de güvenlik yöneticisi izinlerini kullanarak ve hesabınızla oturum açın.

2. **Ayarlar** >  **EndpointsGeneralPortal** >  >  **yeniden yönlendirmesi'ne gidin** [veya sayfayı burada açın](https://security.microsoft.com/preferences2/portal_redirection).  

3. Otomatik yeniden yönlendirme ayarını Kapalı olarak **seçin**.

4. **İstendiğinde &'i** devre dışı bırak'a tıklayın.

Bu ayar herhangi bir zamanda yeniden etkinleştirilebilir. 

Devre dışı bırakıldıktan sonra hesaplar artık security.microsoft.com'a yönlendirimeyecek ve bir kez daha eski portala (eski portala veya posta securitycenter.windows.com) securitycenter.microsoft.com. 

## <a name="related-information"></a>İlgili bilgiler
- [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
- [Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md)
- [Microsoft, güvenlik işlemlerini modernleştirmek için birleşik SIEM ve XDR sağlar](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR ve SIEM bilgi grafiği](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [Daha fazla Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Microsoft güvenlik portalları ve yönetim merkezleri](portals.md)
