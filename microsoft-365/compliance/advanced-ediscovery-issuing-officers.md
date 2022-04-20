---
title: eBulma'da veren memurları yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Kuruluşunuzdaki her durumda herhangi bir gözetim iletişimine eklenebilmeleri için eBulma'da (Premium) kuruluş genelinde veren memurlar ekleyebilirsiniz.
ms.openlocfilehash: 076e6ea8b8dbef18c6c34221937a039fc43fad75
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943007"
---
# <a name="manage-issuing-officers-in-ediscovery-premium"></a>eBulma'da veren memurları yönetme (Premium)

Siz veya diğerleri saklama bildirimi veya koruyucu olan bir kullanıcıya gönderilen başka bir iletişim türü oluşturduğunuzda, veren bir memur belirtmeniz gerekir. Bildirim, belirtilen veren memur adına koruyucuya gönderilir. Örneğin, kuruluşunuzdaki bir avukat, bir olayda koruyuculara ayrı tutma bildirimleri oluşturmak ve göndermekle sorumlu olabilir. Bu senaryoda, paralegal kuruluşta veren memur olarak bir avukat belirtebilir. Who veren bir memur olarak belirtilebilir? Koruyucu iletişim için veren bir memur olarak seçilebilen iki tür kullanıcı vardır:

- İletişimin adına gönderildiği özel servis talebinin herhangi bir üyesi.

- Kuruluş genelinde veren memurlar listesine eklenen tüm kullanıcılar. Bu listedeki kullanıcılar, kuruluşunuzdaki herhangi bir duruma veren bir memur eklenebilir.

Bu makalede, kuruluş genelinde veren memurlar listesine kullanıcı ekleme ve kaldırma adımları açıklanmaktadır.

## <a name="before-you-add-an-issuing-officer"></a>Veren bir memur eklemeden önce

- Veren memurları eklemek veya kaldırmak için kuruluşunuzda eBulma Yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft Purview uyumluluk portalında eBulma izinleri atama](assign-ediscovery-permissions.md)  

- Veren memur olarak eklenen kullanıcının Microsoft 365 kuruluşunuzda etkin bir posta kutusu olmalıdır.

- Kuruluşunuzda en fazla 15 veren memur olabilir. Veren memur olarak belirtilebilen bir davanın üyeleri bu sınıra doğru sayılmaz. Bu sınır yalnızca eBulma'daki (Premium) **Veren memurlar** sayfasına eklenebilen kullanıcı sayısı için geçerlidir.

## <a name="add-an-issuing-officer"></a>Veren bir memur ekleme

1. Uyumluluk portalında [eBulma (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) bölümüne gidin ve **eBulma (Premium) ayarlarına** tıklayın.

   ![eBulma (Premium) ayarlarını seçin](..\media\HistoricalVersions1.png)

2. **Ayarlar** sayfasında Veren **memurları** yönet sayfasını görüntülemek için Veren **memurlar** sekmesini seçin.

   ![Veren memurlar ayarları sayfası.](..\media\AeDIssuingOfficers1.png)

3. **Ekle'ye** tıklayın ve bir veya daha fazla kullanıcıyı arayıp veren memurlar listesine ekleyin.

Kullanıcıları veren memur olarak ekledikten sonra, siz veya diğer kullanıcılar bu kullanıcıları kuruluşunuzdaki herhangi bir durum için koruyucu iletişim için veren bir memur olarak belirtebilirsiniz. Koruyucu iletişim oluşturma hakkında daha fazla bilgi için bkz. [Yasal tutma bildirimi oluşturma](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Veren bir memuru kaldırma

1. Uyumluluk portalında [eBulma (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) bölümüne gidin ve **eBulma (Premium) ayarlarına** tıklayın.

2. **Ayarlar** sayfasında Veren **memurlar** sekmesini seçin.

3. Veren memurlar listesinden bir veya daha fazla kullanıcı seçin ve **sil'e** tıklayın.

Kullanıcıları veren memurlar listesinden sildikten sonra, kullanıcı iletişimin verildiği olayın bir üyesi olmadığı sürece, bu kullanıcılar artık yeni koruyucu iletişimlerde veren bir memur olarak belirtilemez. Ayrıca, veren bir memurun kaldırılması, kullanıcı veren bir memur olarak kaldırılmadan önce gönderilen hiçbir iletişimi etkilemez.
