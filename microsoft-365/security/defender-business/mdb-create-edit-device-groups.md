---
title: Microsoft Defender İş'te cihaz grupları
description: Microsoft Defender İş'te cihaz grupları hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 340d696d2fbc6b698821c54962d04502d6781701
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525924"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Microsoft Defender İş'te cihaz grupları

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender'da ilkeler, cihaz grupları olarak adlandırılan bazı koleksiyonlar aracılığıyla cihazlara uygulanır. 

**Bu makalede şu açıklanmıştır**:  

- [Cihaz grupları hangileridir?](#what-is-a-device-group)   
- [Defender For Business'da cihaz grupları oluşturma](#create-a-new-device-group)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="what-is-a-device-group"></a>Cihaz grubu nedir?

Cihaz grubu, işletim sistemi sürümü gibi belirli ölçütler nedeniyle birlikte grup olunan cihazlar koleksiyonudur. Ölçütleri karşılanan cihazlar, siz dışlamadıysanız bu cihaz grubuna dahil edilir. İş için Microsoft Defender'da ilkeler cihaz grupları kullanılarak cihazlara uygulanır. 

İş için Defender, kullanabileceğiniz varsayılan cihaz gruplarını içerir. Varsayılan cihaz grupları, İş için Defender'a ekli tüm cihazları içerir. Bununla birlikte, bazı cihazlara belirli ayarlarla ilkeler atamak için yeni cihaz grupları da oluşturabilirsiniz. 

Varsayılan cihaz gruplarınız ve tanımladığınız tüm özel cihaz grupları da dahil olmak üzere tüm cihaz grupları tüm cihaz grupları [Azure Active Directory (Azure](/azure/active-directory/fundamentals/active-directory-whatis) AD) içinde depolanır.

## <a name="create-a-new-device-group"></a>Yeni cihaz grubu oluşturma

Şu anda, aşağıdaki yordamda açıklandığı gibi, İş için Defender'da ilke oluşturma veya düzenleme sürecindeyken yeni bir cihaz grubu oluşturabilirsiniz: 

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. 

3. Aşağıdaki işlemlerden birini yapın:

    1. Var olan bir ilkeyi seçin ve sonra da Düzenle'yi **seçin**.
    2. Yeni **bir ilke oluşturmak için +** Ekle'yi seçin.

    > [!TIP]
    > İlkeyi oluşturma veya düzenleme konusunda yardım almak için bkz. [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md).

4. Genel bilgiler **adımını** takip edin, bilgileri gözden geçirin, gerekirse düzenleyin ve ardından Sonraki'yi **seçin**.

5. **+ Yeni grup oluştur'a seçin**. 

6. Cihaz grubu için bir ad ve açıklama belirtin ve ardından Sonraki'yi **seçin**.

7. Gruba dahil etmek istediğiniz cihazları seçin ve ardından Grup **oluştur'a seçin**.

8. Cihaz **grupları adımlarında** , ilkeye yönelik cihaz grupları listesini gözden geçirebilirsiniz. Gerekirse, listeden bir grubu kaldırın. Sonra, **Sonraki'yi seçin**.

9. Yapılandırma ayarları **sayfasında,** ayarları gerektiğinde gözden geçirin ve düzenleyin, sonra da Sonraki'yi **seçin**. Bu ayarlar hakkında daha fazla bilgi için bkz. [Yapılandırma ayarları](mdb-next-gen-configuration-settings.md).

10. **İlkenizi gözden geçirme** adımını takip edin, tüm ayarları gözden geçirin, gerekli düzenlemeleri yapın ve ardından İlke **oluştur'a veya İlkeyi** **güncelleştir'e tıklayın**.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden birini veya daha fazlasını seçin:

- [İlkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md)

- [Yeni ilke oluşturma](mdb-create-new-policy.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)