---
title: Dağıtım grubuna cihaz atama
description: Cihazların hangi dağıtım grubunda yer almak istediğiniz nasıl belirtebilirsiniz?
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6f3d2c79c23a37e1e1a965f9a3f416052a49fa76
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "63010087"
---
# <a name="assign-devices-to-a-deployment-group"></a>Dağıtım grubuna cihaz atama

Microsoft Yönetilen Masaüstü cihazları çeşitli dağıtım gruplarına atar. Bir cihazın atandığı grubu Yönetici portalını kullanarak belirtebilirsiniz veya değiştirebilirsiniz. Bir cihaz kaydedildikten veya kullanıcı kaydol kaydettikten sonra ödevi değiştirebilirsiniz.

> [!IMPORTANT]
> Ödevi değiştirirsiniz, cihaza o gruba özgü ilkeler uygulanır. Değişiklik, uygulamanın en son sürümünü (tüm yeni Windows 10 veya kalite güncelleştirmeleri dahil) yükleyebilir. En iyisi önce yalnızca birkaç cihazı taşımak ve ardından sonuçta elde edilen kullanıcı deneyimini kontrol etmektir. Bazı güncelleştirmelerin cihazı yeniden başlat olacağının farkında olun. Atamak için doğru cihazları seçtiğinizi bir kez daha kontrol edin. Ödevin etkili bir şekilde hepsi 24 saat sürebilir.

**Cihazları dağıtım grubuna atamak için:**

Farklı cihazlar farklı gruplara taşımak için her grup için bu adımları yinelayın.

1. Yeni Microsoft Endpoint Manager sol **bölmede** Cihazlar'ı seçin.
1. Microsoft Yönetilen **Masaüstü bölümünde Cihazlar'ı** **seçin**.
1. Atamak istediğiniz cihazları seçin. Seçilen tüm cihazlar, belirttiğiniz gruba atanır.
1. **Menüden Cihaz** eylemleri'ne tıklayın.
1. Cihaz **gruba ata'ya seçin**. Bir açılır pencere açılır.
1. Cihazları taşımak istediğiniz grubu seçmek için açılan menüyü kullanın ve ardından Kaydet'i **seçin**. **Sütuna göre atanan grup** Bekliyor olarak **değişir**.

Ödev **tamamlandığında,** Sütuna göre atanan grup Yönetici **olarak değişir (** değişikliği sizin yapmış olduğunuz belirtilmiştir) ve Grup sütunu yeni grup atamasını gösterir.

> [!NOTE]
> "Hata" veya "beklemede" kayıt halinde olan cihazları diğer gruplara taşıyasınız.
>
>Cihaz düzgün bir şekilde çıkarılmışsa, "hazır" durumu göstermeyebilir. Böyle bir cihazı taşısanız, taşıma işlemi tamamlanmadı olabilir. 5. Adımda Sütuna göre  atanan grup değişikliğini Beklemede olarak  görmüyorsanız, Intune'da arayarak cihazın kullanılabilir olup olmadığını kontrol edin. Daha fazla bilgi için bkz [. Intune'da cihaz ayrıntılarına bakın](/mem/intune/remote-actions/device-inventory).
