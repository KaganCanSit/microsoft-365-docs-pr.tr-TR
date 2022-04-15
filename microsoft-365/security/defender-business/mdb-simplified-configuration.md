---
title: İş için Microsoft Defender'de basitleştirilmiş yapılandırma işlemi
description: İş için Microsoft Defender'da basitleştirilmiş yapılandırma işlemi hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 68ebf170fa351d63e943a2c4c7a920d3e243ddbe
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862642"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de basitleştirilmiş yapılandırma işlemi

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

İş için Microsoft Defender, özellikle küçük ve orta ölçekli işletmeler için tasarlanmış basitleştirilmiş bir yapılandırma işlemine sahiptir. Bu deneyim, şirketinizin cihazlarını ilk günden korumak için tasarlanmış sihirbaz benzeri bir deneyim ve varsayılan ilkelerle cihazları ekleme ve yönetme konusunda tahminde bulunur. **Basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz; ancak bu seçenekle sınırlı değilsiniz**.

Söz konusu cihazları ekleme ve şirketinizin cihazları için güvenlik ayarlarını yapılandırma olduğunda, çeşitli deneyimler arasından seçim yapabilirsiniz: 

- İş için Microsoft Defender basitleştirilmiş yapılandırma işlemi (*önerilir*) 
- Microsoft Intune içeren Microsoft Endpoint Manager ([Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil)
- Cihazları yönetmek için Microsoft dışı çözümünüz 

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
| Microsoft 365 Defender portalında basitleştirilmiş yapılandırma deneyimi ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Bu, çoğu müşteri için önerilen seçenektir*)  | Basitleştirilmiş yapılandırma deneyimi, İş için Defender'ı ayarlamanıza ve yapılandırmanıza yardımcı olacak sihirbaz benzeri bir deneyim içerir. Basitleştirilmiş yapılandırma, şirketinizin cihazlarını İş için Defender'a eklendikleri anda korumanıza yardımcı olacak varsayılan güvenlik ayarları ve ilkeleri de içerir. <br/><br/>Bu deneyimle, güvenlik ekibiniz Microsoft 365 Defender portalını kullanarak: <br/>- İş için Defender'ı ayarlama ve yapılandırma <br/>- Olayları görüntüleme ve yönetme<br/>- Tehditlere yanıt verme ve tehditleri azaltma<br/>- Raporları görüntüleme<br/>- Bekleyen veya tamamlanan eylemleri gözden geçirme <br/><br/> Microsoft 365 Defender portalı, şirketinizin güvenlik ayarları ve tehdit koruması özellikleri için tek durağınızdır. Hızlı ve verimli bir şekilde çalışmaya başlamanıza yardımcı olacak basitleştirilmiş bir deneyim elde edersiniz. Daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender ayarlamak için sihirbazı kullanma](mdb-use-wizard.md).<br/><br/>Ayrıca ayarlarınızı düzenleyebilir veya şirketinizin gereksinimlerine uygun yeni ilkeler tanımlayabilirsiniz.<br/><br/>Daha fazla bilgi için bkz. [İş için Microsoft Defender'de cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager Microsoft Intune, bulut tabanlı bir mobil cihaz yönetimi (MDM) ve uygulamalar ve cihazlar için mobil uygulama yönetimi (MAM) sağlayıcısı içerir. [Microsoft 365 İş Ekstra](../../business-premium/index.md) müşterilerin zaten Endpoint Manager var. <br/><br/>Birçok şirket cep telefonları, tabletler ve dizüstü bilgisayarlar gibi cihazlarını yönetmek için Intune kullanır. Daha fazla bilgi edinmek için bkz. [Microsoft Intune cihazlarınız için bir MDM ve MAM sağlayıcısıdır](/mem/intune/fundamentals/what-is-intune). <br/><br/>Zaten Microsoft Intune veya Microsoft Endpoint Manager kullanıyorsanız bu çözümü kullanmaya devam edebilirsiniz. |
| Microsoft dışı cihaz yönetimi çözümünüz  | Microsoft dışı bir üretkenlik ve cihaz yönetimi çözümü kullanıyorsanız, bu çözümü İş için Defender ile kullanmaya devam edebilirsiniz. <br/><br/>Cihazlar İş için Defender'a eklendiğinde, Microsoft 365 Defender portalında durumlarını ve uyarılarını görürsünüz. Daha fazla bilgi için bkz [. Uç Nokta için Defender için ekleme ve yapılandırma aracı seçenekleri](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Neden basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz?

Çoğu müşteri için **İş için Microsoft Defender basitleştirilmiş yapılandırma işlemini kullanmanızı öneririz**. Basitleştirilmiş yapılandırma süreci özellikle küçük ve orta ölçekli işletmeler için kolaylaştırılır. İş için Defender, derin teknik uzmanlığa veya özel bilgiye gerek kalmadan şirketinizin cihazlarını ilk günde korumanıza yardımcı olmak için tasarlanmıştır. Varsayılan güvenlik ayarları ve ilkeleriyle, cihazlarınız eklenir eklenmez korunur.

İş için Defender, güvenlik ayarlarınızı yapılandırmada size zaman ve çaba tasarrufu sağlarken güçlü bir koruma sağlamak üzere tasarlanmıştır. Microsoft 365 Defender portalındaki kolaylaştırılmış deneyim, cihazları eklemeyi ve yönetmeyi kolaylaştırır. Ayrıca, şirketinizin cihazlarının eklendikleri anda korunması için varsayılan ilkeler de dahil edilir. Varsayılan ayarlarınızı olduğu gibi tutabilir veya iş gereksinimlerinize uygun değişiklikler yapabilirsiniz. Cihazları gerektiği gibi yönetmek için yeni ilkeler de ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender ayarlama ve yapılandırma](mdb-setup-configuration.md)
- [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md)
