---
title: Microsoft 365 İş Ekstra'da cihaz gruplarıyla çalışma
description: Microsoft 365 İş Ekstra'de cihaz grupları hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/16/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2c218cd2b0f04201f46155a72a916cc7676aaddb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320828"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra'da cihaz grupları

Microsoft 365 İş Ekstra, İş için Microsoft Defender aracılığıyla uç nokta korumasını içerir. Cihaz koruma ilkeleri, cihaz grupları olarak adlandırılan belirli koleksiyonlar aracılığıyla cihazlara uygulanır. 

**Bu kılavuzda aşağıdakiler açıklanmaktadır**:  

- [Cihaz grupları nelerdir?](#whats-a-device-group)
- [Yeni cihaz grubu oluşturma](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Cihaz grubu nedir?

Cihaz grubu, işletim sistemi sürümü gibi belirli ölçütler nedeniyle birlikte gruplandırılmış bir cihaz koleksiyonudur. Ölçütleri karşılayan cihazlar, siz hariç tutmadığınız sürece bu cihaz grubuna dahil edilir. 

Aboneliğinizle, kullanabileceğiniz varsayılan cihaz gruplarınız vardır. Varsayılan cihaz grupları, İş için Defender'a eklenen tüm cihazları içerir. Ancak, belirli cihazlara belirli ayarlarla cihaz koruma ilkeleri atamak için yeni cihaz grupları da oluşturabilirsiniz. 

Varsayılan cihaz gruplarınız ve tanımladığınız tüm özel cihaz grupları dahil olmak üzere tüm cihaz grupları [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD) içinde depolanır.

## <a name="how-do-i-create-a-new-device-group"></a>Nasıl yaparım? yeni bir cihaz grubu oluşturacak mısınız?

Cihaz koruma ilkesi oluşturma veya düzenleme sürecindeyken yeni bir cihaz grubu oluşturabilirsiniz. 

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. 

3. Aşağıdaki eylemlerden birini gerçekleştirin:

    1. Var olan bir ilkeyi seçin ve ardından **Düzenle'yi** seçin.
    
    2. Yeni bir ilke oluşturmak için **+ Ekle'yi** seçin.

    > [!TIP]
    > İlke oluşturma veya düzenleme konusunda yardım almak için bkz. [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](m365bp-view-edit-create-mdb-policies.md).

4. **Genel bilgiler** adımında bilgileri gözden geçirin, gerekirse düzenleyin ve ardından **İleri'yi** seçin.

5. **+ Yeni grup oluştur'u** seçin. 

6. Cihaz grubu için bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

7. Gruba eklenecek cihazları seçin ve ardından **Grup oluştur'u** seçin.

8. **Cihaz grupları** adımında, ilke için cihaz gruplarının listesini gözden geçirin. Gerekirse, listeden bir grubu kaldırın. Ardından **İleri'yi** seçin.

9. **Yapılandırma ayarları** sayfasında, ayarları gerektiği gibi gözden geçirin ve düzenleyin ve **ardından İleri'yi** seçin. Bu ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'deki yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. **İlkenizi gözden geçirin** adımında tüm ayarları gözden geçirin, gerekli düzenlemeleri yapın ve ardından **İlke oluştur veya İlkeyi** **güncelleştir'i** seçin.

## <a name="next-steps"></a>Sonraki adımlar

Birincil görevlerinizi tamamladığınıza göre [, yanıt ekiplerinizi](m365bp-security-incident-management.md) ayarlayın ve [ortamınızı koruyun](m365bp-maintain-environment.md).

