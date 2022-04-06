---
title: Mobil cihazda cihaz gruplarıyla Microsoft 365 İş Ekstra
description: Microsoft 365 İş Ekstra'de cihaz grupları hakkında bilgi Microsoft 365 İş Ekstra
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: a5a0b932e88fb4c4232e4afca8f2307e40088e6b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705522"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra'da cihaz Microsoft 365 İş Ekstra

Microsoft 365 İş Ekstra, İş için Microsoft Defender aracılığıyla uç nokta korumasını içerir. Cihaz koruma ilkeleri, cihaz grupları olarak adlandırılan bazı koleksiyonlar aracılığıyla cihazlara uygulanır. 

**Bu makalede şu açıklanmıştır**:  

- [Cihaz grupları hangileridir?](#whats-a-device-group)
- [Yeni cihaz grubu oluşturma](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Cihaz grubu nedir?

Cihaz grubu, işletim sistemi sürümü gibi belirli ölçütler nedeniyle birlikte grup olunan cihazlar koleksiyonudur. Ölçütleri karşılanan cihazlar, siz dışlamadıysanız bu cihaz grubuna dahil edilir. 

Aboneliğiniz ile, kullanabileceğiniz varsayılan cihaz grupları vardır. Varsayılan cihaz grupları, İş için Defender'a ekli tüm cihazları içerir. Bununla birlikte, bazı cihazlara belirli ayarlarla cihaz koruma ilkeleri atamak için yeni cihaz grupları da oluşturabilirsiniz. 

Varsayılan cihaz gruplarınız ve tanımladığınız tüm özel cihaz grupları da dahil olmak üzere tüm cihaz grupları tüm cihaz grupları [Azure Active Directory (Azure](/azure/active-directory/fundamentals/active-directory-whatis) AD) içinde depolanır.

## <a name="how-do-i-create-a-new-device-group"></a>Yeni bir cihaz grubunu nasıl oluşturabilirim?

Cihaz koruma ilkesi oluşturma veya düzenleme sürecindeyken yeni bir cihaz grubu oluşturabilirsiniz. 

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. 

3. Aşağıdaki işlemlerden birini yapın:

    1. Var olan bir ilkeyi seçin ve sonra da Düzenle'yi **seçin**.
    2. Yeni **bir ilke oluşturmak için +** Ekle'yi seçin.

    > [!TIP]
    > İlkeyi oluşturma veya düzenleme konusunda yardım almak için bkz. [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](m365bp-view-edit-create-mdb-policies.md).

4. Genel bilgiler **adımını** takip edin, bilgileri gözden geçirin, gerekirse düzenleyin ve ardından Sonraki'yi **seçin**.

5. **+ Yeni grup oluştur'a seçin**. 

6. Cihaz grubu için bir ad ve açıklama belirtin ve ardından Sonraki'yi **seçin**.

7. Gruba dahil etmek istediğiniz cihazları seçin ve ardından Grup **oluştur'a seçin**.

8. Cihaz **grupları adımlarında** , ilkeye yönelik cihaz grupları listesini gözden geçirebilirsiniz. Gerekirse, listeden bir grubu kaldırın. Sonra, **Sonraki'yi seçin**.

9. Yapılandırma ayarları **sayfasında,** ayarları gerektiğinde gözden geçirin ve düzenleyin, sonra da Sonraki'yi **seçin**. Bu ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'da yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. **İlkenizi gözden geçirme** adımını takip edin, tüm ayarları gözden geçirin, gerekli düzenlemeleri yapın ve ardından İlke **oluştur'a veya İlkeyi** **güncelleştir'e tıklayın**.


