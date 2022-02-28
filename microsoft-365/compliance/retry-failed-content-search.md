---
title: İçerik konumu hatasını çözmek için İçerik Aramasını yeniden deneyin
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: ''
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Araştırma sırasında, içerik konumu hataları olan İçerik Aramalarını çözümlemek için Yeniden Dene düğmesini kullanabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3c433dfa6bf842f1d62350e3b518177d1bdca6d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985027"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>İçerik konumu hatasını çözmek için İçerik Aramasını yeniden deneyin

Güvenlik ve uyumluluk merkezinde çok fazla sayıda posta kutusunda arama yapmak için İçerik Arama'ya baksanız, hataya benzer arama hataları alabilirsiniz:

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Bu hatalar (CS001-002, CS003-002, CS008-009, CS012-002 hatalarının ve CS0XX-0XX formunun diğer hataları, İçerik Arama'nın belirli içerik konumlarında arama başarısız olduğunu gösterir; bu örnekte, iki posta kutusunda arama yoktu. Bu hatalar, İçerik Arama'nın durum ayrıntıları uç sayfasında görüntülenir.

## <a name="cause-of-content-location-errors"></a>İçerik konumu hatalarının nedeni

Çok fazla sayıda posta kutusu aranıyorsa, arama bir Microsoft veri merkezinde binlerce sunucuya dağıtılır. Herhangi bir zamanda, belirli sunucular yeniden başlatma durumuna veya artıklı kopyalara başarısız olurken olabilir. Bu durumlardan herhangi biri, İçerik Arama'nın verileri alma isteğinin zaman zaman dışında olur. Önceki örnekte, başarısız olan posta kutularının hataları arama zamanlamasının sonucudur.

## <a name="resolving-content-location-errors"></a>İçerik konumu hatalarını çözme

Aramanın yeniden başlatılması çoğunlukla farklı sunucularda benzer hatalara neden olur. Aramanızı yeniden başlatmak yerine, **arama** sonuçları sayfasının en üstünde görüntülenen Yeniden Dene düğmesine tıklayın.

![İçerik konumu hatalarını çözmek için Yeniden Dene düğmesine tıklayın.](../media/retrycontentsearch3.png)

Böylece yalnızca başarısız olan posta kutuları için arama yeniden denenecek. Arama işlemini yeniden deneyken, başarıyla döndürülen diğer sonuçlar korunur.

## <a name="tips-to-avoid-content-location-errors"></a>İpuçları konumu hatalarını önlemeyi sağlar

Burada, içerik konumu hatalarının bazı ek nedenleri ve çok fazla sayıda posta kutusunda arama yapmaktan kaçınmanıza yardımcı olacak bazı ipuçları yer alın.

- Kullanıcı etkinliği nedeniyle arama yapılan posta kutusu meşgul olabilir. Bu durumda, arama hizmeti posta kutusunun kullanılamaz duruma ulaşması için kendisinde kısıtlamaya neden olabilir. Bunu önlemek için, iş dışı saatler boyunca arama çalıştırmayı deneyin.

- Arama sorgusu posta kutusundan çok fazla içerik geliyor olabilir. Mümkünse anahtar sözcükleri, tarih aralıklarını ve arama koşullarını kullanarak aramanın kapsamını daraltmayı deneyin.

- Anahtar sözcükler listesini kullanarak bir arama sorgusu ekleyebilirsiniz.[](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches) Anahtar sözcükler listesini kullanan bir arama sorgusu çalıştırırken, hizmet temelde anahtar sözcük listesinin her satırı için ayrı bir arama çalıştırır ve böylece istatistikler oluşturulur. Arama sorgularında anahtar sözcükler listesini kullanıyorsanız, anahtar sözcük listesinde satır sayısını en aza bölün veya anahtar sözcükleri daha küçük listelere bölün ve her anahtar sözcük listesi için farklı bir arama oluşturun.

  > [!NOTE]
  > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için, artık arama sorgusunun anahtar sözcük listesinde en çok 20 satırla sınırlandırabilirsiniz.

- Aynı posta kutusunda aynı anda çok fazla arama yapılıyor. Mümkünse, herhangi bir posta kutusunda bir defada tek bir arama çalıştırmayı deneyin.

- Tek bir aramada çok fazla posta kutusu arama. Çok fazla sayıda posta kutusunda arama sırasında içerik konumu hataları olasılığı artar. Mümkünse, birden çok arama çalıştırmayı deneyin; böylece her aramada, kuruluşta posta kutularının bir alt kümesi vardır.

- Posta kutusunda gerekli bakım yapılıyor. Bu neden büyük olasılıkla seyrek ortaya çıkar, ancak içerik konumu hatası aldıktan sonra biraz bekleyin ve sonra arama işlemini yeniden deneyin.
