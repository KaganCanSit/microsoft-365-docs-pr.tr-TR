---
title: SharePoint Online'da SharePoint ve büyütme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Web Essentials ile azaltma ve büyütme tekniklerini kullanarak HTTP isteklerini ve SharePoint Online'da sayfa yükleme süresini azaltmayı öğrenin.
ms.openlocfilehash: fabf690f523cabf67fe775bbd1a10251a477f633
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015192"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online'da SharePoint ve büyütme

Bu makalede, Web Essentials ile azaltma ve taşıma tekniklerini kullanarak HTTP isteklerinin sayısını ve SharePoint Online'da sayfa yükleme süresini azaltabilirsiniz.
  
Web sitenizi özelleştirerek, özelleştirmeyi desteklemek için sunucuya çok sayıda ek dosya abilirsiniz. Fazladan JavaScript, CSS ve resimler eklemek sunucuya yapılan HTTP isteklerini artırır ve bu da bir web sayfasının görüntülenme süresinde artar. Aynı türde birden çok dosya varsa, indirmeyi daha hızlı hale yüklemek için bu dosyaları paketebilirsiniz.
  
JavaScript ve CSS dosyaları için, boşluk boşluklarını ve gerekli olmayan diğer karakterleri kaldırarak dosyaların toplam boyutunu azaltmaya da neden olan, azaltma adı verilen bir yaklaşım da kullanabilirsiniz.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Web Essentials ile JavaScript ve CSS dosyalarını düzenleme ve düzenleme

CSS ve JavaScript dosyalarını paket etmek için Web Essentials gibi üçüncü taraf yazılımları kullanabilirsiniz.
  
> [!IMPORTANT]
> Web Essentials üçüncü taraf, açık kaynaklı ve topluluk tabanlı bir projedir. Yazılım, Visual Studio 2012 ve Visual Studio 2013 yazılımına sahip bir uzantıdır ve Microsoft tarafından destek desteklemez. Web Essentials'ı indirmek için web sitesini ziyaret edin: [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).
  
Web Essentials iki şekildendling sunar:
  
- .bundle: CSS ve JavaScript dosyaları için
- .sprite: resimler için (yalnızca Visual Studio 2013)

Özel bir ana sayfa içinde başvurulan bazı markalama öğeleri bulunan mevcut bir özelliğiniz varsa, Web Essentials'i kullanabilirsiniz. Örneğin:
  
![Özel ana sayfada marka öğesinin ekran görüntüsü.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Web Essentials'ta bir TE000127218 ve CSS paketi oluşturmak için
  
1. Çözüm Visual Studio'de pakete eklemek istediğiniz dosyaları seçin.
2. Seçili dosyalara sağ tıklayın ve bağlam **menüsünden Web Essentials** \> **JavaScript paket dosyası oluştur'u** seçin. Örneğin:

    ![Web Essentials menü seçeneklerini gösteren ekran görüntüsü.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>JavaScript ve CSS dosyalarını düzenlemenin sonuçlarını görüntüleme

Bir JavaScript ve CSS paketi  oluşturursanız Web Essentials, JavaScript ve CSS dosyalarının yanı sıra diğer bazı yapılandırma bilgilerini tanımlayan, tarif dosyası olarak adlandırılan bir XML dosyası oluşturur:
  
![JavaScript ve CSS yemek tarifi dosyasının ekran görüntüsü.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Ayrıca,ndling tarifinde minify bayrağı true olarak ayarlanmışsa dosyalar boyut olarak azalır ve birlikte paketli olarak ayarlanır. Bu, JavaScript dosyalarının ana sayfanıza başvurabilirsiniz yeni ve simge durumuna inen sürümlerinin oluşturulmuş olduğu anlamına gelir.
  
![Minify bayrağının true olarak ayarlandı olarak ekran görüntüsü.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Web siteden bir sayfayı yükleyseniz, sunucuya gönderilen istek sayısını ve her dosyanın ne kadar sürede yük süreden olduğunu görmek için web tarayıcınızdan (Internet Explorer 11 gibi) geliştirici araçlarını kullanabilirsiniz.
  
Aşağıdaki şekil, JavaScript ve CSS dosyalarının, minimumdan önce yüklenmesinin sonucudır.
  
![Screenshot showing 80 items being downloaded.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
CSS ve JavaScript dosyalarının birlikte sevk edildikten sonra isteklerin sayısı 74'e bırakılır ve her dosyanın tek tek indirileme işlemi özgün dosyalardan yalnızca biraz daha uzun sürer:
  
![Screenshot showing 74 items being downloaded.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Paketledikten sonra JavaScript paket dosyası 815 KB'tan 365 KB'a indirildi:
  
![azaltılmış indirme boyutunu gösteren ekran görüntüsü.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Resim sprite'ı oluşturarak resimlerinndneleme

JavaScript ve CSS dosyalarını paketle benzer şekilde, çok sayıda küçük simgeyi ve diğer yaygın resimleri daha büyük bir sprite sayfası olarak bir araya kullanabilir ve sonra CSS kullanarak bu resimleri ayrı ayrı gösterebilirsiniz. Kullanıcının web tarayıcısı, her bir resmi tek tek indirmek yerine sprite sayfasını bir kez indirir ve yerel bilgisayarda önbelleğe kullanır. Bu, indirme sayısını ve web sunucusuna gidiş dönüş sayısını keserek sayfa yükleme performansını iyiler.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Web Essentials** içinde bir resim sprite'i oluşturmak için**
  
1. Çözüm Visual Studio'de pakete eklemek istediğiniz dosyaları seçin.
2. Seçili dosyalara sağ tıklayın ve ardından bağlam **menüsünden Web Essentials** \> **Resim sprite'ı** oluştur'u seçin. Örneğin:

    ![Bir resim sprite'ın nasıl oluşturulunu gösteren ekran görüntüsü.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Sprite dosyasının kaydedil için bir konum seçin. .sprite dosyası, sprite'ın ayarlarını ve dosyalarını açıklayan bir XML dosyasıdır. Aşağıdaki şekiller, sprite PNG dosyası ve ilgili .sprite XML dosyasının bir örneğini gösterir.

    ![Sprite dosyasının ekran görüntüsü.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Sprite XML dosyasının ekran görüntüsü.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
