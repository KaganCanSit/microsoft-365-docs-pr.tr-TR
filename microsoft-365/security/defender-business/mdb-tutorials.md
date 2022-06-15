---
title: İş için Microsoft Defender'deki öğreticiler ve simülasyonlar
description: İş için Defender'ı kullanmaya başlamanıza yardımcı olacak çeşitli öğreticiler hakkında bilgi edinin.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e491e6d093396e54983e96eb1ca96c5e713565ba
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089186"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'deki öğreticiler ve simülasyonlar

İş için Microsoft Defender ayarlamayı yeni tamamladıysanız, İş için Defender'ın nasıl çalıştığı hakkında nereden bilgi edineceğinizi merak ediyor olabilirsiniz. Bu makalede deneyebileceğiniz bazı senaryolar ve İş için Defender'da kullanılabilen çeşitli öğreticiler ve simülasyonlar açıklanmaktadır. Bu kaynaklar, İş için Defender'ın şirketiniz için nasıl çalışabileceğini görmenize yardımcı olmak için tasarlanmıştır.


## <a name="try-these-scenarios"></a>Bu senaryoları deneyin

Aşağıdaki tabloda, İş için Defender ile deneyebileceğiniz çeşitli senaryolar özetlemektedir:

| Senaryo  | Açıklama  |
|---------|---------|
| Yerel betik kullanarak cihazları ekleme     | İş için Defender'da, indirdiğiniz ve her cihazda çalıştırdığınız bir betik kullanarak Windows ve macOS cihazları ekleyebilirsiniz. Betik, Azure Active Directory (Azure AD) ile bir güven oluşturur (bu güven yoksa), cihazı Microsoft Intune ile kaydeder (Intune varsa) ve cihazı İş için Defender'a ekler. Daha fazla bilgi edinmek için bkz[. Cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md).         |
| Microsoft Endpoint Manager yönetim merkezini kullanarak cihazları ekleme     | İş için Defender'ı almadan önce zaten Intune kullanıyorsanız cihazları eklemek için Endpoint Manager yönetim merkezini kullanmaya devam edebilirsiniz. Windows, macOS, iOS ve Android cihazlarınızı Microsoft Intune eklemeyi deneyin. Daha fazla bilgi için bkz. [Microsoft Intune'de cihaz kaydı](/mem/intune/enrollment/device-enrollment).        |
| Güvenlik ilkelerini düzenleme     | İş için Defender'da güvenlik ilkelerinizi yönetiyorsanız, ilkelerinizi görüntülemek ve gerekirse düzenlemek için **Cihaz yapılandırma** sayfasını kullanın. İş için Defender, şirketinizin cihazlarının eklendikleri anda güvenliğini sağlamak için önerilen ayarları kullanan varsayılan ilkelerle birlikte gelir. Varsayılan ilkelerinizi koruyabilir, düzenleyebilir ve iş gereksinimlerinize uyacak şekilde kendi ilkelerinizi tanımlayabilirsiniz. Daha fazla bilgi için bkz. [İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md).        |
| Simülasyon saldırısı çalıştırma   | İş için Defender'da çeşitli öğreticiler ve simülasyonlar mevcuttur. Bu öğreticiler ve simülasyonlar, İş için Defender'ın tehdit koruması özelliklerinin şirketiniz için nasıl çalışabileceğini ilk elden gösterecek şekilde tasarlanmıştır. Ekibiniz için eğitim alıştırması olarak simülasyon saldırısı da kullanabilirsiniz. Öğreticilerden birini veya daha fazlasını denemek için bkz. [İş için Microsoft Defender için önerilen öğreticiler](#recommended-tutorials-for-defender-for-business).         |
| Microsoft 365 Lighthouse'da olayları görüntüleme     | Microsoft 365 Lighthouse kullanan bir [Microsoft Bulut Çözümü Sağlayıcısı](/partner-center/enrolling-in-the-csp-program) iseniz, Microsoft 365 Lighthouse portalınızda müşterilerinizin kiracıları genelinde olayları görüntüleyebilirsiniz. Daha fazla bilgi edinmek için bkz. [Microsoft 365 Lighthouse ve İş için Microsoft Defender](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>İş için Defender için önerilen öğreticiler

Aşağıdaki tabloda, İş için Defender müşterileri için önerilen öğreticiler açıklanmaktadır:

| Öğretici  | Açıklama  |
|---------|---------|
| **Belge arka kapı bırakıldığında**     | Bir test cihazına dosya tabanlı kötü amaçlı yazılım getiren bir saldırının benzetimini yapmak. Öğreticide simülasyon dosyasının nasıl alınıp kullanılacağı ve Microsoft 365 Defender portalında nelerin izlenip izlendiği açıklanır. <br/><br/>Bu öğretici, test cihazınıza Microsoft Word yüklenmesini gerektirir.   |
| **Canlı Yanıt öğreticisi**     | Canlı Yanıt ile temel ve gelişmiş komutları kullanmayı öğrenin. Şüpheli bir dosyayı bulmayı, dosyayı düzeltmeyi ve bir cihazda bilgi toplamayı öğrenin.   |
| **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**     | Üç senaryodan Tehdit ve Güvenlik Açığı Yönetimi hakkında bilgi edinin: <br/><br/>1. Şirketinizin tehdidini ve güvenlik açığına maruz kalmasını azaltın. <br/>2. Bir düzeltme isteyin. <br/>3. Güvenlik önerileri için bir özel durum oluşturun. <br/><br/> Tehdit ve güvenlik açığı yönetimi, uç nokta güvenlik açıklarını ve yanlış yapılandırmalarını bulma, öncelik belirleme ve düzeltme konusunda risk tabanlı bir yaklaşım kullanır.      |

Her öğreticide senaryoyu, nasıl çalıştığını ve ne yapılacağını açıklayan bir izlenecek yol belgesi bulunur.

> [!TIP]
> İzlenecek belgelerde Uç Nokta için Microsoft Defender başvurularını görürsünüz. Bu makalede listelenen öğreticiler Uç Nokta için Defender veya İş için Defender ile kullanılabilir.

## <a name="how-to-access-the-tutorials"></a>Öğreticilere erişme

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesindeki **Uç Noktalar'ın** altında **Öğreticiler'i** seçin.

3. Aşağıdaki öğreticilerden birini seçin:

   - **Belge arka kapı bırakıldığında**
   - **Canlı Yanıt öğreticisi**
   - **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)