---
title: Microsoft Defender for Business'ı (önizleme) ayarlamak için sihirbazı kullanma
description: İş için Defender, sihirbaz gibi bir kurulum ve yapılandırma işlemi içerir. Zaman ve emek tasarrufu yapmak için sihirbazı kullanın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/16/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 26bf8e46ba79094f74fe542f932921d4f1c2a50d
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015326"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business-preview"></a>Microsoft Defender for Business'ı (önizleme) ayarlamak için sihirbazı kullanma

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender (önizleme), küçük ve orta ölçekli işletmeler için zaman ve çabadan ilk kurulum ve yapılandırma için sihirbaz benzer bir deneyimle tasarruf etmek üzere tasarlanmıştır. Bu makalede, sihirbazın adımları ve İş için Defender'ı el ile ayarlama ve yapılandırma seçenekleriniz açıklanmıştır.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="İş için Defender'ı ayarlamak için sihirbazın giriş ekranı ekran görüntüsü.":::

## <a name="overview-of-the-wizard"></a>Sihirbaza genel bakış

Sihirbaz, İş için Defender'ı hızla ve verimli bir şekilde ayarlamanıza ve yapılandırmanıza yardımcı olacak şekilde tasarlanmıştır. Sihirbaz aşağıdaki adımlarda size yol sağlar:

1. **Kullanıcı izinleri atama**. Bu adımda, güvenlik ekibinize posta portalına () Microsoft 365 Defender ve yetkinsiniz[https://security.microsoft.com](https://security.microsoft.com). Portal erişimine, belirli izinleri ima ediyor olan roller aracılığıyla erişim izni verilmiş olur. [Roller ve izinler hakkında daha fazla bilgi edinmek için](mdb-roles-permissions.md):

   - Genel Yönetici, kendi kiracınız genelinde tüm ayarları  görüntü Microsoft 365 düzenleyebilir. 
   - Güvenlik Yöneticisi güvenlik ayarlarını  görüntüleyemez ve düzenleyebilir. 
   - Güvenlik Okuyucusu bilgileri yalnızca raporlarda  görüntüde olabilir. 

2. **E-posta bildirimlerini ayarlayın**. Bu adımda, algılanan bir güvenlik açığı veya yeni bir uyarı olması durumunda e-posta bildirimlerini kimlerin alabilmesi gerektiğini belirlersiniz. E-posta bildirimleri, masasından uzakta olsalar bile güvenlik ekibinizi haberdar etmeye yardımcı olabilir. [E-posta bildirimleri hakkında daha fazla bilgi alın](mdb-email-notifications.md). 

3. **Cihaz ekleme ve Windows yapılandırma**. Bu adımda, İşletmeler için Defender'a Windows mobil cihazlarınızı  onboard. Cihazları hemen işe ekleme, bu cihazları ilk günden korumanıza yardımcı olur. 

   - Zaten Microsoft Intune (Microsoft Endpoint Manager'in bir parçası) kullanıyorsanız ve kuruluşta Endpoint Manager'e kayıtlı cihazları varsa, kaydolan Windows cihazlarının bir bölümü veya hepsi için otomatik ekleme kullanmak isteyip Windows sorabilirsiniz. Otomatik ekleme, Endpoint Manager Defender İş arasında bir bağlantı ayarlar ve ardından Windows Defender İş'e cihaz ayarlar.

   - henüz Endpoint Manager kullanıyorsanız veya Endpoint Manager'a kayıtlı Windows olmayan cihazlarınız varsa cihazları Defender for Business (önizleme) sürümüne el ile ekleyebilirsiniz. 

   - Bkz [. Cihazları İş için Microsoft Defender'a (önizleme) ekleme](mdb-onboard-devices.md).
   
4. **Güvenlik ilkelerinizi yapılandırma**. İş için Defender, kuruluş cihazlarına uygulanan varsayılan güvenlik ilkeleri içerir. Bu varsayılan ilkeler önerilen ayarları kullanır ve cihazlarınıza güçlü bir koruma sağlamak üzere tasarlanmıştır. Bununla birlikte, isterseniz kendi güvenlik ilkelerinizi de oluşturabilirsiniz. Zaten Endpoint Manager kullanıyorsanız, güvenlik ilkelerinizi yönetmek için bunu kullanmaya devam edersiniz. 

   - [Basitleştirilmiş yapılandırma hakkında daha fazla bilgi öğrenin](mdb-simplified-configuration.md).
   - [Güvenlik ilkelerini ve cihazlarını yönetecek yeri seçin](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Sihirbazı kullana olursam ne olur?

Sihirbazı kullanmamanızı tercih ediyorsanız veya kurulum işleminiz tamamlamadan önce sihirbazdan çıkarsanız, yine de kurulum ve yapılandırma işleminizi kendi başına tamamabilirsiniz. Adımları [takip etmek için bkz. İş için Microsoft Defender'ı (önizleme)](mdb-setup-configuration.md) ayarlama ve yapılandırma.

## <a name="next-steps"></a>Sonraki adımlar

- [Microsoft 365 Defender portalını kullanmaya başlama](mdb-get-started.md)

- [Threat & Vulnerability Management panoyu kullanma](mdb-view-tvm-dashboard.md)