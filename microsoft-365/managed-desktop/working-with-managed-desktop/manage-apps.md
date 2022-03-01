---
title: Microsoft Yönetilen Masaüstü'nden uygulamaları yönetme
description: Microsoft Yönetilen Masaüstü cihazlarına dağıtılan iş hattı uygulamalarını güncelleştirme hakkında bilgi
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: a51be2521924164a8c90a51fcf99328ecf511877
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014295"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'nden iş hattı uygulamalarını yönetme

<!--Application management -->

Uygulama güncelleştirmelerini yönetmenin ve güncelleştirmeleri Microsoft Yönetilen Masaüstü cihazlarınıza dağıtmanın birkaç yolu vardır. Uygulama güncelleştirmelerini Microsoft Yönetilen Masaüstü portalında veya Intune'da açabilirsiniz.

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'de iş hattı uygulamalarını güncelleştirme

**İş hattı uygulamalarınızı Microsoft Yönetilen Masaüstü portalında güncelleştirmek için:**

1. Microsoft Yönetilen Masaüstü [Yöneticisi portalında oturum açın](https://aka.ms/mmdportal).
1. **Stok'ın** altında **Uygulamalar'ı seçin**.  
1. Güncellemek istediğiniz uygulamayı ve sonra Düzenle'yi **seçin**.
1. **Yönet'in** altında **Özellikler'i seçin**.
1. Uygulama **paketi dosyası'ı** seçin ve ardından yeni uygulama paketi dosyasını karşıya yüklemek için göz atabilirsiniz.
1. Uygulama **paketi dosyası'ı seçin**.
1. Klasör simgesini seçin ve güncelleştirilmiş uygulama dosyanız konumunu bulun. **Aç**'ı seçin. Uygulama bilgileri paket bilgileriyle güncelleştirilir.
1. Uygulama **sürümünün güncelleştirilmiş** uygulama paketini yansıtdığını doğrulayın.

Güncelleştirilmiş uygulama, kullanıcı cihazlarınızı dağıtılacaktır.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Intune'da iş hattı uygulamalarını güncelleştirme

**Intune'da iş hattı uygulamalarınızı güncelleştirmek için:**

1. [Azure portalda oturum açın](https://portal.azure.com).
2. Tüm **ServicesIntune'ı** >  seçin. Intune, İzleme **+ Yönetim bölümünde** yer almaktadır.
3. İstemci **Uygulamaları ve > seçin**.
4. Uygulama listesinden uygulamanızı bulun ve seçin.
5. Genel Bakış **bölümünde** Özellikler'i **seçin**.
6. Uygulama **paketi dosyası'ı seçin**.
7. Klasör simgesini seçin ve güncelleştirilmiş uygulama dosyanız konumunu bulun. **Aç**'ı seçin. Uygulama bilgileri paket bilgileriyle güncelleştirilir.
8. Uygulama **sürümünün güncelleştirilmiş** uygulama paketini yansıtdığını doğrulayın.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Bir uygulamayı önceki bir sürüme geri alma

Uygulamanın yeni sürümü dağıtıldığında ve hata olduğunda, önceki bir sürüme geri dönebilirsiniz. Aşağıda açıklanan işlem, türün **MSI** iş Windows uygulama veya Windows uygulaması **(Win 32) - önizleme olarak listelenmiş uygulamalara yöneliktir**

**İş hattı uygulamasını önceki bir sürüme geri almak için:**

1. Microsoft Yönetilen Masaüstü [Yöneticisi portalında oturum açın](https://aka.ms/mmdportal).
2. **Stok'ın** altında **Uygulamalar'ı seçin**.  
3. Geri almak istediğiniz uygulamayı seçin ve sonra da Düzenle'yi **seçin**.
4. **Yönet'in** altında **Özellikler'i seçin**.
    - **MSI Windows uygulamaları hakkında** daha fazla bilgi için, Uygulama bilgileri'ne ve sonra Uygulama sürümünü yoksay'ın **altında Evet'i** **seçin**.
    - Uygulama **Windows (Win 32) - önizleme** uygulamaları için **Uygulama bilgileri,** Algılama kuralları'nın ardından Ekle'yi **seçin**.
    MSI kuralı varsa, MSI ürün sürüm denetimi'nin **Hayır olarak** ayar olduğunu **doğrulayın**.
5. [Upload dosyasının önceki bir sürümünü Microsoft Yönetilen Masaüstü](../get-started/deploy-apps.md) Yöneticisi portalına içerir.  
