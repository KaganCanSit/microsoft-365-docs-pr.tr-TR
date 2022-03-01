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
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b13275a68a80cee52a756ef9b9464b5402749c27
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027500"
---
# <a name="device-groups-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da cihaz grupları (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender(önizleme) içinde, ilkeler cihaz grupları olarak adlandırılan bazı koleksiyonlar aracılığıyla cihazlara uygulanır. 

**Bu makalede şu açıklanmıştır**:  

- [Cihaz grupları hangileridir?](#what-is-a-device-group)   
- [Defender For Business'da cihaz grupları oluşturma](#create-a-new-device-group)

## <a name="what-is-a-device-group"></a>Cihaz grubu nedir?

Cihaz grubu, işletim sistemi sürümü gibi belirli ölçütler nedeniyle birlikte grup olunan cihazlar koleksiyonudur. Ölçütleri karşılanan cihazlar, siz dışlamadıysanız bu cihaz grubuna dahil edilir. İş için Microsoft Defender(önizleme) içinde, ilkeler cihaz grupları kullanılarak cihazlara uygulanır. 

İş için Defender (önizleme), kullanabileceğiniz varsayılan cihaz gruplarını içerir. Varsayılan cihaz grupları, İş için Defender'a (önizleme) ekli tüm cihazları içerir. Bununla birlikte, bazı cihazlara belirli ayarlarla ilkeler atamak için yeni cihaz grupları da oluşturabilirsiniz. 

Varsayılan cihaz gruplarınız ve tanımladığınız tüm özel cihaz grupları da dahil olmak üzere tüm cihaz grupları tüm cihaz grupları [Azure Active Directory (Azure](/azure/active-directory/fundamentals/active-directory-whatis) AD) içinde depolanır.

## <a name="create-a-new-device-group"></a>Yeni cihaz grubu oluşturma

Şu anda, aşağıdaki yordamda açıklandığı gibi, İş için Defender'da (önizleme) ilke oluşturma veya düzenleme sürecindeyken yeni bir cihaz grubu oluşturabilirsiniz: 

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

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)