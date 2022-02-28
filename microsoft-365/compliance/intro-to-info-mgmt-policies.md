---
title: Bilgi yönetimi ilkelerine giriş
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2014
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- WSU150
- SPO160
- OSU150
- MET150
ms.assetid: 63a0b501-ba59-44b7-a35c-999f3be057b2
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: İçeriğin ne kadar korundu bilgisi olduğu veya bu içerikle kullanıcıların hangi eylemleri gerçekleştireci yoksaymalarını denetleme ve izleme gibi işlemleri izlemek için bilgi yönetimi ilkelerini nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: 98eae2a08aa246a1f0ebe7d037103a82c132d060
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987310"
---
# <a name="introduction-to-information-management-policies"></a>Bilgi yönetimi ilkelerine giriş

Bilgi yönetimi ilkesi, bir içerik türüne ilişkin kurallar kümesidir. Bilgi yönetimi ilkeleri, kuruluşların, içeriğin ne kadar korun olduğu veya bu içerikle kullanıcıların hangi eylemleri gerçekleştireci olduğu gibi eylemleri denetlemelerini ve izlemelerini sağlar. Bilgi yönetimi ilkeleri kuruluşların yasal veya resmi düzenlemelere uymalarına yardımcı olabilir ya da basitçe şirket içi iş işlemlerini zorunlu edebilir. 
  
Örneğin, mali tablolarında "yeterli denetimleri" göstermelerini gerektiren resmi düzenlemelere uyması gereken bir kuruluş, mali dosyalarla ilgili tüm belgeler için yazma ve onay sürecinde belirli eylemleri denetleen bir veya birden çok bilgi yönetim ilkesi oluşturabilir.
  
Nasıl yapılır bilgileri için bkz. [Bilgi yönetimi ilkelerini oluşturma ve uygulama](create-info-mgmt-policies.md).
  
## <a name="features-of-information-management-policies"></a>Bilgi yönetimi ilkelerinin özellikleri
<a name="__top"> </a>

Kuruluşların içeriği ve süreçleri yönetmek için tek tek veya birlikte kullanabileceği, önceden tanımlanmış ilke özelliklerinin dört temel kategorisi vardır. 
  
![İçerik ilkelerinin türleri.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)
  
Denetim ilkesi özelliği, kuruluşların belgeler ve liste öğeleri üzerinde gerçekleştirilen olayları ve işlemleri günlüğe kaydetmesi ile içerik yönetim sistemlerinin nasıl kullanışlarını çözümlemelerine yardımcı olur. Denetim ilkesi özelliğini, bir belge veya öğenin düzenlendiğinde, görüntülendiğinde, iadeıldığında, kullanıma alınmış durumda olduğu, silindiğinde veya izinlerini değiştirdiğinde olduğu gibi olayları günlüğe günlüğeecek şekilde yapılandırabilirsiniz. Tüm denetim bilgileri, sunucu üzerinde tek bir denetim günlüğünde depolanır ve site yöneticileri bu bilgiler üzerinde raporlar çalıştırabilir. 
  
Süre sonu ilkesi özelliği, kuruluşların sitelerinden güncel olmayan içeriği tutarlı ve izlenebilir bir yolla silmelerine veya kaldırmalarına yardımcı olur. Bu, güncel olmayan içeriği tutmayla ilişkilendirilmiş hem maliyeti hem de riski yönetmenize yardımcı olur. Belirli içerik türlerinin belirli bir tarihte veya belge oluşturulduktan ya da son değiştirilmeden sonra belirli bir süre içinde sona ermesi için Bir Süre Sonu ilkesi yapılandırabilirsiniz.
  
Ayrıca kuruluşlar, belirli ihtiyaçları karşılamak üzere özel ilke özellikleri oluşturabilir ve dağıtıyor. Örneğin, bir üretim kuruluşu, kullanıcıların güvenli olmayan yazıcılarda bu belgelerin kopyalarını yazdırmasını yasaklayan tüm taslak ürün tasarımı belirtim belgeleri için bir bilgi yönetimi ilkesi tanımlamak istiyor olabilir. Bu tür bilgi yönetimi ilkesi tanımlamak için, ürün tasarım belirtimi içerik türüyle ilgili bilgi yönetimi ilkesine eklen bir Yazdırma Kısıtlaması ilkesi özelliği oluşturabilir ve dağıtabilirsiniz.
  
## <a name="locations-to-use-an-information-management-policy"></a>Bilgi yönetimi ilkesi kullanmak için konumlar
<a name="__toc340213528"> </a>

Bilgi yönetimi ilkesi uygulamak için, bunu bir siteye liste, kitaplık veya içerik türüne eklemeniz gerekir. Bilgi yönetimi ilkesi oluşturmak veya eklemek, ilkenin ne kadar geniş bir şekilde uygulandığını veya ne kadar geniş kullanılab olacağını etkiler. Şunları yapabilirsiniz:
  
 **Site koleksiyonu ilkesi oluşturma ve sonra bu ilkeyi içerik türüne, listesine veya kitaplığına ekleme** Site koleksiyonunun en üst düzey sitesinde, İlkeler listesinde bir site koleksiyonu ilkesi oluşturabilirsiniz. Site koleksiyonu ilkesi oluşturduktan sonra, bu ilkeyi dışarı aktararak diğer site koleksiyonlarının yöneticilerinin bu ilkeyi İlkeler listesine almalarını sekleyebilirsiniz. Dışarı aktarılabilir site koleksiyonu ilkesi oluşturmak, kuruluş genelinde bilgi yönetimi ilkelerini standart hale getirebilirsiniz. 
  
Site içerik türüne bir site koleksiyonu ilkesi ekleniyorsa ve bu site içerik türünün bir örneği liste veya kitaplıma ekleniyorsa, bu liste veya kitaplığın sahibi liste veya kitaplık için site koleksiyonu ilkesi değiştiremez. Site içerik türüne site koleksiyonu ilkesi eklemek, site koleksiyonu ilkelerinin site hiyerarşinizin her düzeyinde zorunlu kılınması için iyi bir yol sağlar.
  
![Site Web Sitesi sayfasında İçerik Türü İlke Ayarlar bağlantısı.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
 **En üst düzey sitenin Site İçerik Türü Galerisi'nde site** içerik türü için bilgi yönetimi ilkesi oluşturma ve sonra bu içerik türünü bir veya birden çok liste veya kitaplıka ekleme Ayrıca, doğrudan bir site içerik türü için bilgi yönetimi ilkesi oluşturabilir ve bu site içerik türünün bir örneğini birden çok liste veya kitaplıkla ilişkilendirmeniz de gerekir. Bu şekilde bir bilgi yönetimi ilkesi sanız, site koleksiyonunda yer alan ve bu içerik türünden veya içerik türünden devralan içerik türlerinden her öğenin ilkesi vardır. Bununla birlikte, doğrudan bir site içerik türü için bilgi yönetimi ilkesi oluşturdusanız, bu bilgi yönetimi ilkesi diğer site koleksiyonlarında yeniden kullanmak daha zordur çünkü bu yolla oluşturulan ilkeler dışarı aktaramaz. 
  
![Site sayfası sayfasında site Ayarlar bağlantısı.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)
  
![Site içerik türünün ayarlar sayfasında bilgi yönetimi ilkesi bağlantısı.](../media/15d83a34-6c8f-4b6e-b6ee-e9b0a70cbb4b.png)
  
Not Site koleksiyonunda kullanılacak ilkeleri kontrol etmek için, site koleksiyonu yöneticileri ilke özelliklerini doğrudan bir içerik türü üzerinde ayarlama özelliğini devre dışı bırakabilirsiniz. Bu kısıtlama geçerli olduğunda, içerik türü oluşturan kullanıcılar site koleksiyonu İlkeler listesinden ilke seçmekle sınırlıdır.
  
 **Liste veya kitaplık için bilgi yönetimi ilkesi oluşturma** Çok sınırlı bir içerik kümesine kurum için belirli bir bilgi yönetimi ilkesi uygulamanız gerekirse, yalnızca tek bir liste veya kitaplık için geçerli olan bir bilgi yönetimi ilkesi oluşturabilirsiniz. Bilgi yönetimi ilkesi oluşturma yöntemi en az esnektir, çünkü ilke tek bir konum için geçerlidir ve diğer konumlarda dışarı aktaramaz veya yeniden kullanılamaz. Bununla birlikte, bazen belirli durumlarla ilgili geçerliliği sınırlı olan benzersiz bilgi yönetimi ilkeleri oluşturmanız gerekir. 
  
![Belge kitaplığının ayarlar sayfasında bilgi yönetimi ilkeleri bağlantısı.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
Notlar 
  
Bir liste veya kitaplık için, ancak bu liste veya kitaplık birden çok içerik türlerini desteklemezse, bilgi yönetimi ilkesi oluşturabilirsiniz. Bir liste veya kitaplık birden çok içerik türünü destekliyorsa, bu liste veya kitaplıkla ilişkilendirilmiş tek tek her liste içerik türü için bir bilgi yönetimi ilkesi tanımlamanız gerekir. (Belirli bir liste veya kitaplıkla ilişkilendirilmiş site içerik türünün örnekleri, liste içerik türleri olarak bilinir.)
  
Site koleksiyonunda kullanılacak ilkeleri kontrol etmek için, site koleksiyonu yöneticileri doğrudan liste veya kitaplıkta ilke özellikleri ayarlama özelliğini devre dışı bırakabilirsiniz. Bu kısıtlama geçerli olduğunda, listeleri veya kitaplıkları yöneten kullanıcılar site koleksiyonu İlkeler listesinden ilke seçmekle sınırlıdır.
  
[Bilgi yönetimi ilkesi, bir içerik türüne ilişkin kurallar kümesidir. Bilgi yönetimi ilkeleri, kuruluşların, içeriğin ne kadar korun olduğu veya bu içerikle kullanıcıların hangi eylemleri gerçekleştireci olduğu gibi eylemleri denetlemelerini ve izlemelerini sağlar. Bilgi yönetimi ilkeleri kuruluşların yasal veya resmi düzenlemelere uymalarına yardımcı olabilir ya da basitçe şirket içi iş işlemlerini zorunlu edebilir. Örneğin, mali tablolarında "yeterli denetimleri" göstermelerini gerektiren resmi düzenlemelere uyması gereken bir kuruluş, mali dosyalarla ilgili tüm belgeler için yazma ve onay sürecinde belirli eylemleri denetleen bir veya birden çok bilgi yönetim ilkesi oluşturabilir. Nasıl yapılır bilgileri için bkz. Bilgi yönetimi ilkelerini oluşturma ve uygulama.](intro-to-info-mgmt-policies.md#__top)
  

