---
title: Ekleme sorunlarını ve hata iletilerini giderme
description: E-posta kurulumunu tamamlarken ekleme sorunlarını ve hata Uç Nokta için Microsoft Defender.
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
ms.openlocfilehash: cfbd91743ed2e61809d9e2b6f0243b5c327bdae4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467565"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Abonelik ve portal erişimi sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Bu sayfada, Hizmet Hizmetinizi ayarlarken ortaya çıkacak sorunları gidermeye Uç Nokta için Microsoft Defender sağlar.

Hata iletisi alırsanız, Microsoft 365 Defender sorunun ne olduğu ve ilgili bağlantılar hakkında ayrıntılı bir açıklama sağlanır.

## <a name="no-subscriptions-found"></a>Abonelik bulunamadı

Abonelik bulunamadı Microsoft 365 Defender iletisi alırsanız bu, kullanıcının portalda oturum a Azure Active Directory için kullanılan Abonelik bulunamadı iletisiyle Uç Nokta için Microsoft Defender anlamına gelir.

Olası nedenler:

- En Windows E5 ve Office E5 lisansları ayrı lisanslardır.
- Lisans satın alınmış ancak bu Azure AD örneğine sağlanmaz.
  - Bu bir lisans sağlama sorunu olabilir.
  - Lisansı, hizmette kimlik doğrulaması için kullanılandan farklı bir Microsoft Azure AD yanlışlıkla sağmış da olabilir.

Her iki durumda da, Genel Lisans Desteği veya Toplu [lisans Uç Nokta için Microsoft Defender Microsoft](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) [desteği'nden Microsoft desteğine başvurun](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="Abonelik bulunamadı sayfası" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>Aboneliğinizin süresi doldu

Erişim sırasında Microsoft 365 Defender Aboneliğinizin süresi doldu **iletisi** alırsanız, çevrimiçi hizmet aboneliğinizin süresi dolmaz. Uç Nokta için Microsoft Defender diğer çevrimiçi hizmet abonelikleri gibi bir aboneliğin son kullanma tarihi vardır.

Lisansı istediğiniz zaman yenilemeyi veya genişletmeyi seçebilirsiniz. Sona erme tarihinden sonra portala erişirken Aboneliğinizin süresi doldu iletisi cihaz çıkarımı paketini indirme seçeneğiyle birlikte, lisansı yenilemeyi seçmeyseniz de size bir seçenek sunulacaktır.

> [!NOTE]
> Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="Abonelik süresi doldu bildirim iletisi" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>Portala erişim yetkisine sahip değilsiniz

Portala erişim için yetkili değilsiniz şeklinde bir bildirim alırsanız Uç Nokta için Microsoft Defender'in bir güvenlik izlemesi, olay soruşturması ve yanıt ürünü olduğunu ve bu şekilde buna erişimin kısıtlanmış ve kullanıcı tarafından denetlenen bir ürün olduğunu fark edebilirsiniz.
Daha fazla bilgi için bkz. [**Portala kullanıcı erişimi atama**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="Erişime izin verilmeyen bildirim iletisi" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Veriler şu anda portalın bazı bölümlerinde kullanılamıyor

Portal panosunda ve diğer bölümlerde "Veriler şu anda kullanılamıyor" gibi bir hata iletisi görüntülenirse:

:::image type="content" source="images/atp-data-not-available.png" alt-text="Veri kullanılamaması bildirim iletisi" lightbox="images/atp-data-not-available.png":::

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
