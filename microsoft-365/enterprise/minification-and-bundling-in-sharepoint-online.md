---
title: SharePoint Online'da küçültme ve paketleme
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
description: HTTP isteklerini ve SharePoint Online'da sayfaları yükleme süresini azaltmak için Web Essentials ile küçültme ve paketleme tekniklerini kullanmayı öğrenin.
ms.openlocfilehash: b02cf095b1d7f05a82df1cf98a590ff762453f8a
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637637"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online'da küçültme ve paketleme

Bu makalede, HTTP isteklerinin sayısını azaltmak ve SharePoint Online'da sayfaları yüklemek için gereken süreyi azaltmak için Web Essentials ile küçültme ve paketleme tekniklerinin nasıl kullanılacağı açıklanmaktadır.
  
Web sitenizi özelleştirdiğinizde, özelleştirmeyi desteklemek için sunucuya çok sayıda ek dosya ekleyebilirsiniz. Ek JavaScript, CSS ve görüntülerin eklenmesi, sunucuya yapılan HTTP isteklerinin sayısını artırır ve bu da bir web sayfasının görüntülenmesi için gereken süreyi artırır. Aynı türde birden çok dosyanız varsa, bu dosyaları daha hızlı indirmek için bu dosyaları paketleyebilirsiniz.
  
JavaScript ve CSS dosyaları için, boşluk ve gerekli olmayan diğer karakterleri kaldırarak dosyaların toplam boyutunu azalttığınız küçültme adlı bir yaklaşım da kullanabilirsiniz.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Web Essentials ile JavaScript ve CSS dosyalarını küçültme ve paketleme

CSS ve JavaScript dosyalarını paketlemek için Web Essentials gibi üçüncü taraf yazılımları kullanabilirsiniz.
  
> [!IMPORTANT]
> Web Essentials üçüncü taraf, açık kaynaklı, topluluk tabanlı bir projedir. Yazılım, Visual Studio 2012 ve Visual Studio 2013 için bir uzantıdır ve Microsoft tarafından desteklenmez. Web Essentials'ı indirmek için [Web Essentials 2012'deki](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebEssentials2012) web sitesini ziyaret edin.
  
Web Essentials iki tür paketleme sunar:
 
- .bundle: CSS ve JavaScript dosyaları için
- .sprite: görüntüler için (yalnızca Visual Studio 2013)

Özel bir ana sayfada başvuruda bulunan bazı marka öğelerine sahip mevcut bir özelliğiniz varsa Web Essentials'ı kullanabilirsiniz, örneğin:
  
![Özel ana sayfadaki marka öğesinin ekran görüntüsü.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Web Essentials'ta TE000127218 ve CSS paketi oluşturmak için
  
1. Visual Studio,Çözüm Gezgini'da pakete eklemek istediğiniz dosyaları seçin.
2. Seçili dosyalara sağ tıklayın ve bağlam **menüsünden Web Essentials** \> **JavaScript paket dosyası oluştur'u** seçin. Örneğin:

    ![Web Temel Parçalar menü seçeneklerini gösteren ekran görüntüsü.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>JavaScript ve CSS dosyalarını paketlemenin sonuçlarını görüntüleme

JavaScript ve CSS paketi oluşturduğunuzda Web Essentials, JavaScript ve CSS dosyalarının yanı sıra diğer bazı yapılandırma bilgilerini tanımlayan tarif dosyası adlı bir XML dosyası oluşturur:
  
![JavaScript ve CSS yemek tarifi dosyasının ekran görüntüsü.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Buna ek olarak, paketleme tarifinde küçültme bayrağı true olarak ayarlanırsa dosyaların boyutu küçültülmüş ve birlikte paketlenmiştir. Bu, ana sayfanızda başvurabileceğiniz JavaScript dosyalarının yeni, küçültüldü sürümlerinin oluşturulduğu anlamına gelir.
  
![True olarak ayarlanan küçültme bayrağının ekran görüntüsü.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Web sitenizden bir sayfa yüklediğinizde, sunucuya gönderilen istek sayısını ve her dosyanın yüklenmesinin ne kadar sürdüğünü görmek için web tarayıcınızdan Internet Explorer 11 gibi geliştirici araçlarını kullanabilirsiniz.
  
Aşağıdaki şekil, küçültmeden önce JavaScript ve CSS dosyalarının yüklenmesinin sonucudur.
  
![İndirilen 80 öğeyi gösteren ekran görüntüsü.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
CSS ve JavaScript dosyalarını birlikte birleştirdikten sonra, istek sayısı 74'e düştü ve her dosya özgün dosyaların tek tek indirilmesinden yalnızca biraz daha uzun sürdü:
  
![İndirilen 74 öğeyi gösteren ekran görüntüsü.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Paketleme sonrasında JavaScript paket dosyası önemli ölçüde 815 KB'tan 365 KB'a düşürüldü:
  
![İndirilen indirme boyutunu gösteren ekran görüntüsü.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Görüntü sprite oluşturarak görüntüleri paketleme

JavaScript ve CSS dosyalarını nasıl paketlediğinize benzer şekilde, birçok küçük simgeyi ve diğer yaygın görüntüleri daha büyük bir sprite sayfasında birleştirebilir ve ardından css kullanarak görüntüleri tek tek görüntüleyebilirsiniz. Kullanıcının web tarayıcısı, her görüntüyü tek tek indirmek yerine sprite sayfasını bir kez indirir ve ardından yerel bilgisayarda önbelleğe alır. Bu, indirme sayısını ve web sunucusuna gidiş dönüş sayısını azaltarak sayfa yükleme performansını artırır.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Web Essentials'ta görüntü sprite'i oluşturmak için**
  
1. Visual Studio,Çözüm Gezgini'da pakete eklemek istediğiniz dosyaları seçin.
2. Seçili dosyalara sağ tıklayın ve bağlam **menüsünden Web Essentials** \> **Görüntü sprite oluştur'u** seçin. Örneğin:

    ![Görüntü sprite'i oluşturmayı gösteren ekran görüntüsü.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Sprite dosyasını kaydetmek için bir konum seçin. .sprite dosyası, sprite içindeki ayarları ve dosyaları açıklayan bir XML dosyasıdır. Aşağıdaki şekiller, bir sprite PNG dosyasının ve buna karşılık gelen .sprite XML dosyasının bir örneğini gösterir.

    ![Sprite dosyasının ekran görüntüsü.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![sprite XML dosyasının ekran görüntüsü.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
