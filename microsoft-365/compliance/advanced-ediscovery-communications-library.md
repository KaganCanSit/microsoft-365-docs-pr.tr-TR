---
title: eBulma'daki İletişim kitaplığında koruyucu iletişim şablonlarını yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Kuruluşunuzda her durumda kullanılabilmesi için eKeşif'e (Premium) koruyucu iletişim şablonları (bekletme bildirimi şablonu gibi) ekleyebilirsiniz.
ms.openlocfilehash: 0ae8496178cd27a395de66e18355ccd675006486
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630829"
---
# <a name="manage-custodian-communications-templates-in-ediscovery-premium"></a>eBulma'da koruyucu iletişim şablonlarını yönetme (Premium)

Siz veya diğer kullanıcılar ayrı tutma bildirimi veya başka türde koruyucu iletişimler oluşturduğunuzda, eBulma (Premium) durumunda **İletişimler** sekmesindeki iletişim düzenleyicisini kullanarak iletişim belgesini sıfırdan oluşturmanız gerekiyordu. Şimdi, kuruluşunuzda her durumda iletişim oluşturmak için kullanılabilecek iletişim şablonları oluşturmanıza olanak tanıyan yeni bir özellik yayımladık. İletişim şablonları oluşturulduktan sonra, bir durumda kullanılabilir. Bu, avukatların veya koruyucu iletişim oluşturan diğer kullanıcıların bildirim oluşturmak için sıfırdan başlaması gerekmeyecek anlamına gelir. Bunun yerine, bir koruyucuya gönderilen bildirimi oluşturmak için bir şablon seçebilirler.

Bu makalede, belirli bir eBulma (Premium) olayı için yeni bir koruyucu bildirimi oluştururken kuruluş genelinde iletişim şablonları oluşturma ve bunları seçme işlemleri açıklanmaktadır.

## <a name="before-you-create-templates-in-the-communications-library"></a>İletişim kitaplığında şablon oluşturmadan önce

- eKeşif (Premium) içindeki İletişim kitaplığına şablon eklemek veya kaldırmak için kuruluşunuzda eBulma Yöneticisi olmanız gerekir. Daha fazla bilgi için bkz[. Microsoft Purview uyumluluk portalı eBulma izinleri atama](assign-ediscovery-permissions.md)  

- Kuruluşunuzun İletişim kitaplığında en fazla 50 şablonu olabilir.

## <a name="create-a-communications-template"></a>İletişim şablonu oluşturma

1. Uyumluluk portalında [eBulma (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) seçeneğine gidin ve **ardından eBulma (Premium) ayarları'na** tıklayın.

   ![eBulma (Premium) ayarlarını seçin](..\media\HistoricalVersions1.png)

2. **Ayarlar** sayfasında **İletişim kitaplığı** sekmesini seçin.

3. **İletişim kitaplığı** sayfasında **Oluştur'a** tıklayın.

4. Koruyucu iletişim oluşturmak için yordamı izleyin. Adım adım yönergeler için bkz. [Yasal tutma bildirimi oluşturma](create-hold-notification.md).

   > [!NOTE]
   > İletişim şablonu oluşturma adımları, bir servis talebi içinde bildirim oluşturmak için kullanılan iş akışıyla aynıdır. Tek fark, şablon oluşturduğunuzda veren bir memur belirtmediğiniz ve koruyucu atamadığınızdır. Bir servis talebi için koruyucu bildirimi oluşturmak üzere iletişim şablonu kullandığınızda, veren bir memur belirtme ve koruyucu atama işlemi yapılır.

5. Bir şablon oluşturduktan sonra, **bu şablon İletişim kitaplığı** sayfasında görüntülenir.

   ![İletişim kitaplığında görüntülenen şablonlar](..\media\AeDCommunicationsLibrary1.png)

Siz veya diğer eBulma Yöneticileri bir iletişim şablonunu düzenleyebilirsiniz. Şablonda yaptığınız değişiklikler, daha önce bu şablon kullanılarak oluşturulmuş bildirimleri etkilemez veya değiştirmez. Bu değişiklikler yalnızca güncelleştirilmiş şablon kullanılarak oluşturulan yeni bildirimler için geçerlidir.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Koruyucu bildirim oluşturmak için iletişim şablonu kullanma

İletişim kitaplığında bir veya daha fazla iletişim şablonu oluşturulduktan sonra, bu şablonlar bir durumda koruyucu bildirimi oluşturmak için seçilebilir.

Şablon seçmek için:

1. Kuruluşunuzdaki servis taleplerinin listesini görüntülemek için uyumluluk portalında **eBulma > Gelişmiş'e** gidin.

2. Bir servis talebi seçin, **İletişimler** sekmesine ve ardından **Yeni iletişim'e** tıklayın.

3. **İletişimi adlandır** sayfasında İletişim **şablonunu seçin** açılan listesini kullanarak, koruyucu bildirimini oluşturmak için kullanılacak iletişim şablonunu seçin.

   Kuruluşunuzun İletişim kitaplığındaki şablonların listesi açılan listede görüntülenir.

   ![İletişim kitaplığındaki şablonlar açılan listede görüntülenir.](..\media\AeDCommunicationsTemplates1.png)
