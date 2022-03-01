---
title: İş için Microsoft Defender'daki öğreticiler ve benzetimler (önizleme)
description: İş için Defender(önizleme) kullanmaya başlamanıza yardımcı olacak çeşitli öğreticiler hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 570313132367ad591944d87959cff538cd5b75e8
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015343"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'daki öğreticiler ve benzetimler (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender'ı (önizleme) ayarlamayı yeni bitirdiyseniz, İş için Defender'ın (önizleme) nasıl çalıştığını nereden öğrenmeye başlayacağını merak ediyor olabilirsiniz. Bu makalede deneme senaryoları ve İş için Defender (önizleme) ile kullanılabilen çeşitli öğreticiler ve benzetimler açıklanmıştır. Bu kaynaklar, Defender For Business (önizleme) ile organizasyona nasıl yardımcı olduğunu görmenizi sağlar.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="try-these-preview-scenarios"></a>Bu önizleme senaryolarını deneyin

Aşağıdaki tabloda, İş için Defender (önizleme) önizlemesi sırasında denemeniz gereken birkaç senaryo özetlenmiştir. 
<br/><br/>


| Senaryo  | Açıklama  |
|---------|---------|
| Yerel betik kullanarak cihazları ekleme     | İş için Defender (önizleme) ile her Windows 10 indirip çalıştıracak bir betik kullanarak 11 cihaz ve 11 cihaz indirebilirsiniz. Betik, Azure Active Directory (Azure AD) ile bir güven oluşturur ve cihazı Microsoft Intune. Daha fazla bilgi edinmek için bkz [. İş için Defender'da yerel bir betik kullanarak cihazları ekleme](mdb-onboard-devices.md#onboard-devices-using-a-local-script-in-defender-for-business).         |
| Microsoft Intune kullanarak cihazları Microsoft Intune     | Uç nokta için Defender'ı Microsoft Intune önceden Microsoft Intune kullanıyorsanız cihazları Microsoft Intune kullanabilirsiniz. Farklı işletim sistemli macOS, iOS, Linux ve Android Microsoft Intune. Daha fazla bilgi edinmek için bkz[. Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Güvenlik ilkelerini düzenleme     | Güvenlik ilkelerinizi Defender for Business (önizleme) üzerinde yönetiyorsanız, ilkelerinizi görüntülemek ve düzenlemek  için Cihaz yapılandırması sayfasını kullanın. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da (önizleme) ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md).        |
| Benzetimi yapılan saldırıyı yürütün   | İş için Defender'da (önizleme) çeşitli öğreticiler ve benzetimler mevcuttur. Bu öğreticiler ve benzetimler, Defender for Business (önizleme) tehdit koruması özelliklerinin organizasyonunıza nasıl yararlı olduğunu ilk elden göstermek için tasarlanmıştır. Öğreticilerden birini veya daha fazlasını denemek için bkz. İş için [Microsoft Defender (önizleme) için önerilen öğreticiler](#recommended-tutorials-for-defender-for-business).         |
| Olay görünümünde Microsoft 365 Lighthouse     | Microsoft 365 Lighthouse [Microsoft Bulut Çözümü Sağlayıcısı](/partner-center/enrolling-in-the-csp-program) kullanıyorsanız, yakın zamanda Microsoft 365 Lighthouse portalında müşterilerin kiracılarında olayları görüntüebilirsiniz. Daha fazla bilgi edinmek için bkz[. Microsoft 365 Lighthouse Ve İş için Microsoft Defender (önizleme)](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>defender for Business için önerilen öğreticiler

Aşağıdaki tabloda, İş için Defender (önizleme) müşterileri için önerilen öğreticiler açık almaktadır:
<br/><br/>


| Öğretici  | Açıklama  |
|---------|---------|
| **Belge Backdoor'a düşer**     | Test cihazında dosya tabanlı kötü amaçlı yazılıma neden olan saldırının benzetimini yapmak. Öğreticide benzetim dosyasını alma ve kullanma ve bu dosyada neleri izlemeniz Microsoft 365 Defender açık almaktadır. <br/><br/>Bu öğretici, Microsoft Word cihazınıza yüklenmemiş olması gerekir.   |
| **Canlı Yanıt öğreticisi**     | Canlı Yanıt ile temel ve gelişmiş komutları kullanmayı öğrenin. Şüpheli bir dosyayı nasıl bu şekilde bulup düzeltmeyi ve cihazda bilgi toplamayı öğrenin.   |
| **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**     | Üç senaryoyu Tehdit ve Güvenlik Açığı Yönetimi hakkında bilgi edinmek için: <br/><br/>1. Kuruluş tehditini ve güvenlik açığına maruz kalma süresini azaltma. <br/>2. Düzeltme isteğide bulundur. <br/>3. Güvenlik önerileri için bir özel durum oluşturun. <br/><br/> Tehdit güvenlik açığı yönetimi kimlik açıkları ve hatalı yapılandırmaları bulma, önceliklendirme ve düzeltme için risk tabanlı bir yaklaşım kullanır.      |

Her öğreticide senaryoyu, bunların nasıl çalıştığını ve ne yaptığını açıklayan yol gösterir.

> [!TIP]
> Yol gösterilen belgelerde Uç Nokta için Microsoft Defender'a başvurular vardır. Bu makalede listelenen öğreticiler, Uç Nokta için Defender veya İş için Defender (önizleme) ile kullanılabilir.

## <a name="how-to-access-the-tutorials"></a>Öğreticilere erişme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesindeki Uç **Noktalar'ın altında Öğreticiler'i** **seçin**.

3. Aşağıdaki öğreticilerden birini seçin:

   - **Belge Backdoor'a düşer**
   - **Canlı Yanıt öğreticisi**
   - **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da cihazları yönetme (önizleme)](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)