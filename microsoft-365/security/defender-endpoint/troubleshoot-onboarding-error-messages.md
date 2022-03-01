---
title: Ekleme sorunlarını ve hata iletilerini giderme
description: Uç Nokta için Microsoft Defender kurulumunu tamamlarken ekleme sorunlarını ve hata iletisini giderin.
keywords: sorun giderme, sorun giderme, Azure Active Directory, ekleme, hata iletisi, hata iletileri, uç nokta için Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: cbf2049841f2987eb71e9c716de133872c1e6a81
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014112"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Abonelik ve portal erişimi sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Bu sayfada, Uç Nokta için Microsoft Defender hizmetinizi ayarlarken ortaya çıkabilir sorunları gidermeye yardımcı olacak ayrıntılı adımlar sağlar.

Hata iletisi alırsanız, Microsoft 365 Defender sorunun ne olduğu ve ilgili bağlantılar hakkında ayrıntılı bir açıklama sağlanır.

## <a name="no-subscriptions-found"></a>Abonelik bulunamadı

Abonelik bulunamadı Microsoft 365 Defender iletisi alırsanız bu, kullanıcıda  portalda oturum açmak için kullanılan Azure Active Directory (Azure AD) kullanıcının Uç nokta lisansı için Microsoft Defender'a sahip olmadığını belirtir.

Olası nedenler:

- En Windows E5 ve Office E5 lisansları ayrı lisanslardır.
- Lisans satın alınmış ancak bu Azure AD örneğine sağlanmaz.
  - Bu bir lisans sağlama sorunu olabilir.
  - Lisansı, hizmette kimlik doğrulaması için kullanılandan farklı bir Microsoft Azure AD yanlışlıkla sağmış da olabilir.

Her iki durumda da, Uç Nokta Desteği için [Genel Microsoft Defender veya Toplu lisans desteği'nde Microsoft](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) [desteğine başvurun](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

![Abonelik bulunamadı resmi.](images/atp-no-subscriptions-found.png)

## <a name="your-subscription-has-expired"></a>Aboneliğinizin süresi doldu

Erişim sırasında Microsoft 365 Defender Aboneliğinizin süresi doldu **iletisi** alırsanız, çevrimiçi hizmet aboneliğinizin süresi dolmaz. Diğer çevrimiçi hizmet abonelikleri gibi Uç nokta aboneliği için Microsoft Defender'ın son kullanma tarihi vardır.

Lisansı istediğiniz zaman yenilemeyi veya genişletmeyi seçebilirsiniz. Sona erme tarihinden sonra portala erişirken Aboneliğinizin süresi doldu iletisi cihaz çıkarımı paketini indirme seçeneğiyle birlikte, lisansı yenilemeyi seçmeyseniz de size bir seçenek sunulacaktır.

> [!NOTE]
> Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

![Aboneliğin süresi doldu resmi.](images/atp-subscription-expired.png)

## <a name="you-are-not-authorized-to-access-the-portal"></a>Portala erişim yetkisine sahip değilsiniz

Portala erişim yetkisine sahip değilsanız **, Uç** Nokta için Microsoft Defender'ın bir güvenlik izleme, olay soruşturması ve yanıt ürünü olduğunu ve buna gibi erişimin kullanıcı tarafından kısıtlanmış ve denetlenen bir ürün olduğunu fark edebilirsiniz.
Daha fazla bilgi için bkz. [**Portala kullanıcı erişimi atama**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

![Portala erişim yetkisi olmayan resmi.](images/atp-not-authorized-to-access-portal.png)

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Veriler şu anda portalın bazı bölümlerinde kullanılamıyor

Portal panosunda ve diğer bölümlerde "Veriler şu anda kullanılamıyor" gibi bir hata iletisi görüntülenirse:

![Şu anda kullanılamıyor veri görüntüsü.](images/atp-data-not-available.png)

Web tarayıcınızda ve altındaki tüm `security.windows.com` alt etki alanlarına izin verebilirsiniz. Örneğin, `*.security.windows.com`.

## <a name="portal-communication-issues"></a>Portal iletişim sorunları

Portala erişim sorunlarıyla, eksik verilerle veya portalın belirli bölümlerine kısıtlı erişimle ilgili sorunlarla karşılaşırsanız, aşağıdaki URL'lere izin verilmiyor ve iletişim için açık olduğunu doğrulamanız gerekir.

- `*.blob.core.windows.net`
- `crl.microsoft.com`
- `https://*.microsoftonline-p.com`
- `https://*.security.microsoft.com`
- `https://automatediracs-eus-prd.security.microsoft.com`
- `https://login.microsoftonline.com`
- `https://login.windows.net`
- `https://onboardingpackagescusprd.blob.core.windows.net`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://security.microsoft.com`
- `https://static2.sharepointonline.com`
