---
title: Microsoft Defender for Business'ı ayarlamak için sihirbazı kullanma
description: İş için Defender, sihirbaz gibi bir kurulum ve yapılandırma işlemi içerir. Zaman ve emek tasarrufu yapmak için sihirbazı kullanın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
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
ms.openlocfilehash: b55af496881489279a7a6f96ed386ab2a26c2fa5
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512608"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>Microsoft Defender for Business'ı ayarlamak için sihirbazı kullanma

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender küçük ve orta ölçekli işletmeler için zaman ve çabadan ilk kurulum ve yapılandırma için sihirbaza benzer bir deneyimle tasarruf etmek üzere tasarlanmıştır. Bu makalede, sihirbazın adımları ve İş için Defender'ı el ile ayarlama ve yapılandırma seçenekleriniz açıklanmıştır.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="İş için Defender'ı ayarlamak için sihirbazın giriş ekranı ekran görüntüsü.":::

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="overview-of-the-wizard"></a>Sihirbaza genel bakış

Sihirbaz, İş için Defender'ı hızla ve verimli bir şekilde ayarlamanıza ve yapılandırmanıza yardımcı olacak şekilde tasarlanmıştır. Sihirbaz aşağıdaki adımlarda size yol sağlar:

1. **Kullanıcı izinleri atama**. Bu adımda, güvenlik ekibinize posta portalına () Microsoft 365 Defender ve yetkinsiniz[https://security.microsoft.com](https://security.microsoft.com). Portal erişimine, belirli izinleri ima ediyor olan roller aracılığıyla erişim izni verilmiş olur. [Roller ve izinler hakkında daha fazla bilgi edinmek için](mdb-roles-permissions.md):

   - Genel Yönetici, kendi kiracınız genelinde tüm ayarları  görüntü Microsoft 365 düzenleyebilir. 
   - Güvenlik Yöneticisi güvenlik ayarlarını  görüntüleyemez ve düzenleyebilir. 
   - Güvenlik Okuyucusu bilgileri yalnızca raporlarda  görüntüde olabilir. 

2. **Cihaz ekleme ve Windows yapılandırma**. Bu adımda, şirketinizin cihaz ve cihazlarını Defender Windows Defender for Business'a hızlıca  yanitabilirsiniz. Cihazları hemen işe ekleme, bu cihazları ilk günden korumanıza yardımcı olur. Daha [fazla bilgi için bkz. Cihazları İş için Microsoft Defender'a](mdb-onboard-devices.md) ekleme.

   - Zaten Microsoft Intune kullanıyorsanız (Microsoft Endpoint Manager'in bir parçası) ve şirketinde Endpoint Manager'e kayıtlı cihazları varsa, kaydolan Windows cihazlarının bir bölümü veya hepsi için otomatik ekleme kullanmak isteyip Windows sorabilirsiniz.[](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) Otomatik ekleme, Endpoint Manager Defender İş arasında bir bağlantı ayarlar ve ardından Windows Defender İş'e cihaz ayarlar.

   - henüz Endpoint Manager'i Windows cihazlarınız yoksa Endpoint Manager [Defender for Business'a el ile ekleyebilirsiniz](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
3. **Güvenlik ilkelerinizi yapılandırma**. defender for Business, yeni nesil koruma ve güvenlik duvarı koruması için, şirketin cihazlarına uygulanan varsayılan güvenlik ilkelerini içerir. Bu varsayılan ilkeler önerilen ayarları kullanır ve cihazlarınıza güçlü bir koruma sağlamak üzere tasarlanmıştır. 

   Ayrıca isterseniz kendi güvenlik ilkelerinizi de oluşturabilirsiniz. Zaten Endpoint Manager kullanıyorsanız, güvenlik ilkelerinizi yönetmek için bunu kullanmaya devam edersiniz. 

   Daha fazla bilgi edinmek için bkz [. Güvenlik ilkelerinizi ve ayarlarınızı görüntüleme ve düzenleme](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Sihirbazı kullana olursam ne olur?

Sihirbazı kullanmamanızı tercih ediyorsanız veya kurulum işleminiz tamamlandıktan önce sihirbaz kapalı olursa, yine de kurulum ve yapılandırma işleminizi kendi başına tamamabilirsiniz. 

Şu [adımları takip etmek için bkz. İş için Microsoft Defender'ı](mdb-setup-configuration.md) ayarlama ve yapılandırma:

1. [Güvenlik ekibinin portala ()](mdb-roles-permissions.md) erişmesi ve bu portalı Microsoft 365 Defender attayın[https://security.microsoft.com](https://security.microsoft.com).

2. [Güvenlik ekibinin yeni uyarılar veya güvenlik açıkları](mdb-email-notifications.md) konusunda döngüde olacak şekilde e-posta bildirimlerini ayarlayın.

3. [Cihazları,](mdb-onboard-devices.md) İş için Defender ile korunmaları için kullanın.

4. [Yeni nesil koruma](mdb-configure-security-settings.md), güvenlik duvarı koruması ve web içeriği filtrelemesi içeren güvenlik ilkelerinizi yönetin.

## <a name="next-steps"></a>Sonraki adımlar

- [Güvenlik ekipleriniz için e-posta bildirimlerini ayarlama](mdb-email-notifications.md)

- [Microsoft 365 Defender portalını kullanmaya başlama](mdb-get-started.md)

- [Threat & Vulnerability Management panoyu kullanma](mdb-view-tvm-dashboard.md)