---
title: İş için Microsoft Defender'de basitleştirilmiş yapılandırma işlemi
description: İş için Defender, basitleştirilmiş bir yapılandırma işlemiyle iş zamanınızı kurtarır. nasıl çalıştığını görün ve işinizi ilk günden koruyun.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 0662ab458a3163e998de7b054926ceff31559a9e
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174422"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de basitleştirilmiş yapılandırma işlemi

İş için Microsoft Defender, özellikle küçük ve orta ölçekli işletmeler için tasarlanmış basitleştirilmiş bir yapılandırma işlemine sahiptir. Bu deneyim, şirketinizin cihazlarını ilk günden korumak için tasarlanmış sihirbaz benzeri bir deneyim ve varsayılan ilkelerle cihazları ekleme ve yönetme konusunda tahminde bulunur. **Basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz; ancak bu seçenekle sınırlı değilsiniz**.

Söz konusu cihazları ekleme ve şirketinizin cihazları için güvenlik ayarlarını yapılandırma olduğunda, çeşitli deneyimler arasından seçim yapabilirsiniz: 

- İş için Microsoft Defender basitleştirilmiş yapılandırma işlemi (*önerilir*) 
- Microsoft Intune ([Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil)

## <a name="what-to-do"></a>Yapılması gerekenler

1. [Kurulum ve yapılandırma seçeneklerinizi gözden geçirin](#review-your-setup-and-configuration-options)
2. [İş için Defender'da basitleştirilmiş yapılandırma süreci hakkında daha fazla bilgi edinin](#why-we-recommend-using-the-simplified-configuration-process)
3. [Sonraki adımlarınıza geçin](#next-steps)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="review-your-setup-and-configuration-options"></a>Kurulum ve yapılandırma seçeneklerinizi gözden geçirin

Aşağıdaki tabloda her deneyim açıklanmaktadır:

| Portal deneyimi  | Açıklama  |
|---------|---------|
| Microsoft 365 Defender portalında basitleştirilmiş yapılandırma deneyimi ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Bu, çoğu müşteri için önerilen seçenektir*)  | Basitleştirilmiş yapılandırma deneyimi, İş için Defender'ı ayarlamanıza ve yapılandırmanıza yardımcı olacak sihirbaz benzeri bir deneyim içerir. Daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender ayarlamak için sihirbazı kullanma](mdb-use-wizard.md).<br/><br/>Basitleştirilmiş yapılandırma, şirketinizin cihazlarını İş için Defender'a eklendikleri anda korumanıza yardımcı olacak varsayılan güvenlik ayarları ve ilkeleri de içerir. Varsayılan ilkelerinizi görüntüleyebilir ve gerekirse ilkelerinizi iş gereksinimlerinize uyacak şekilde düzenleyebilirsiniz. Daha fazla bilgi için bkz. [İş için Microsoft Defender'de cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md).<br/><br/>Basitleştirilmiş deneyim sayesinde, güvenlik ekibiniz Microsoft 365 Defender portalını tek noktadan alışveriş yapmak için kullanır: <br/>- İş için Defender'ı ayarlama ve yapılandırma <br/>- Olayları görüntüleme ve yönetme<br/>- Tehditlere yanıt verme ve tehditleri azaltma<br/>- Raporları görüntüleme<br/>- Bekleyen veya tamamlanan eylemleri gözden geçirme  |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Intune, uygulamalar ve cihazlar için bulut tabanlı bir mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) sağlayıcısıdır. Intune, İş için Defender'ın tek başına sürümüne dahil değildir; ancak [Microsoft 365 İş Ekstra](../../business-premium/index.md) Intune içerir.<br/><br/>Zaten Intune kullanıyorsanız cep telefonları, tabletler ve dizüstü bilgisayarlar gibi cihazları yönetmek için Endpoint Manager yönetim merkezini kullanabilirsiniz. Bkz[. Microsoft Intune: Cihaz yönetimi](/mem/intune/fundamentals/what-is-device-management). |

## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Neden basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz?

Çoğu müşteri için **İş için Microsoft Defender basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz**. 

- Basitleştirilmiş yapılandırma süreci özellikle küçük ve orta ölçekli işletmeler için kolaylaştırılır. 
- İş için Defender derin teknik uzmanlığa veya özel bilgiye ihtiyaç duymaz. 
- Varsayılan güvenlik ayarları ve ilkeleriyle, cihazlarınız eklenir eklenmez korunur.
- Microsoft 365 Defender portalındaki kolaylaştırılmış deneyim, cihazları eklemeyi ve yönetmeyi kolaylaştırır. 
- Varsayılan ilkeler dahil edilir, böylece şirketinizin cihazları eklenir eklenmez korunur.
- Varsayılan ayarlarınızı olduğu gibi tutabilir veya iş gereksinimlerinize uygun değişiklikler yapabilirsiniz. 
- İş gereksinimlerinize uygun yeni ve özel ilkeler ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender ayarlama ve yapılandırma](mdb-setup-configuration.md)
- [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md)
