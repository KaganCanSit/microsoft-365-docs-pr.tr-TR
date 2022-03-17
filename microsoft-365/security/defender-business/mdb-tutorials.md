---
title: İş için Microsoft Defender'daki öğreticiler ve benzetimler
description: İş için Defender kullanmaya başlamanıza yardımcı olacak çeşitli öğreticiler hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: b28e28b2504ed2234f2f48a9763827fc7b063af8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525508"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'daki öğreticiler ve benzetimler

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender'ı ayarlamayı yeni bitirdiyseniz, İş için Defender'ın nasıl çalıştığını nereden öğrenmeye başlayacağını merak ediyor olabilir. Bu makalede deneme senaryoları ve İş için Defender ile kullanılabilen çeşitli öğreticiler ve benzetimler açıklanmıştır. Bu kaynaklar, Defender For Business'ın şirketinize nasıl yardımcı olduğunu görmenizi sağlar.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="try-these-preview-scenarios"></a>Bu önizleme senaryolarını deneyin

Aşağıdaki tabloda, İş için Defender ile denemeniz gereken birkaç senaryo özetlenmiştir. 
<br/><br/>


| Senaryo  | Açıklama  |
|---------|---------|
| Yerel betik kullanarak cihazları ekleme <br/>(*üretim dağıtımı için değil*)     | İş için Defender'da, indiren ve her cihaza çalıştıracak bir betik kullanarak en fazla on Windows 10 ve 11 cihaz indirebilirsiniz. Defender for Business'ın ortamınızı nasıl çalıştıracaklarını değerlendirmek için uygun olan betik, Azure Active Directory (Azure AD) ile bir güven oluşturur ve cihazı Microsoft Intune. Daha fazla bilgi edinmek için bkz [. İş için Defender'da yerel betik](mdb-onboard-devices.md#local-script-in-defender-for-business).         |
| Microsoft Intune kullanarak cihazları Microsoft Intune     | Uç nokta için Defender'ı Microsoft Intune önceden Microsoft Intune kullanıyorsanız cihaz eklemeye devam edin. Farklı işletim sistemli macOS, iOS ve Android Microsoft Intune. Daha fazla bilgi edinmek için bkz[. Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Güvenlik ilkelerini düzenleme     | Defender For Business'da güvenlik ilkelerinizi yönetiyorsanız, ilkelerinizi görüntülemek ve **düzenlemek için Cihaz** yapılandırma sayfasını kullanın. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md).        |
| Benzetimi yapılan saldırıyı yürütün   | İş için Defender'da çeşitli öğreticiler ve benzetimler mevcuttur. Bu öğreticiler ve benzetimler, Defender for Business'ın tehdit koruması özelliklerinin şirketinize nasıl yararlı olduğunu ilk elden göstermek için tasarlanmıştır. Öğreticilerden birini veya daha fazlasını denemek için bkz. İş [için Microsoft Defender'a yönelik önerilen öğreticiler](#recommended-tutorials-for-defender-for-business).         |
| Olay görünümünde Microsoft 365 Lighthouse     | Microsoft 365 Lighthouse [Microsoft Bulut Çözümü Sağlayıcısı](/partner-center/enrolling-in-the-csp-program) kullanıyorsanız, yakın zamanda Microsoft 365 Lighthouse portalında müşterilerin kiracılarında olayları görüntüebilirsiniz. Daha fazla bilgi edinmek için bkz[. Microsoft 365 Lighthouse İş için Microsoft Defender](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>defender for Business için önerilen öğreticiler

Aşağıdaki tabloda, İş için Defender müşterileri için önerilen öğreticiler açık almaktadır:
<br/><br/>


| Öğretici  | Açıklama  |
|---------|---------|
| **Belge Backdoor'a düşer**     | Test cihazında dosya tabanlı kötü amaçlı yazılıma neden olan saldırının benzetimini yapmak. Öğreticide benzetim dosyasını alma ve kullanma ve bu dosyada neleri izlemeniz Microsoft 365 Defender açık almaktadır. <br/><br/>Bu öğretici, Microsoft Word cihazınıza yüklenmemiş olması gerekir.   |
| **Canlı Yanıt öğreticisi**     | Canlı Yanıt ile temel ve gelişmiş komutları kullanmayı öğrenin. Şüpheli bir dosyayı nasıl bu şekilde bulup düzeltmeyi ve cihazda bilgi toplamayı öğrenin.   |
| **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**     | Üç senaryoyu Tehdit ve Güvenlik Açığı Yönetimi hakkında bilgi edinmek için: <br/><br/>1. Şirketinizi tehdit ve güvenlik açığına maruz kalma süresini azaltma. <br/>2. Düzeltme isteğide bulundur. <br/>3. Güvenlik önerileri için bir özel durum oluşturun. <br/><br/> Tehdit güvenlik açığı yönetimi kimlik açıkları ve hatalı yapılandırmaları bulma, önceliklendirme ve düzeltme için risk tabanlı bir yaklaşım kullanır.      |

Her öğreticide senaryoyu, bunların nasıl çalıştığını ve ne yaptığını açıklayan yol gösterir.

> [!TIP]
> Yol gösterilen belgelerde Uç Nokta için Microsoft Defender'a başvurular vardır. Bu makalede listelenen öğreticiler, Uç Nokta için Defender veya İş için Defender ile kullanılabilir.

## <a name="how-to-access-the-tutorials"></a>Öğreticilere erişme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesindeki Uç **Noktalar'ın altında Öğreticiler'i** **seçin**.

3. Aşağıdaki öğreticilerden birini seçin:

   - **Belge Backdoor'a düşer**
   - **Canlı Yanıt öğreticisi**
   - **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)