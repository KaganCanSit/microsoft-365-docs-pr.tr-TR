---
title: Bilgi yönetimi ilkeleri oluşturma ve uygulama
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 8ccac9e4-3a50-49fa-a95b-d186032a6ee3
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom:
- seo-marvel-apr2020
description: Bilgilerin ne kadar süreyle tutulacaklarını denetlemek ve bilgileri kimin kullandığını izlemek için bilgi yönetimi ilkesi ayarlamayı öğrenin.
ms.openlocfilehash: d62eea4c43e6c171bf8c640e341933e81a23e0d0
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758981"
---
# <a name="create-and-apply-information-management-policies"></a>Bilgi yönetimi ilkeleri oluşturma ve uygulama

Bilgi yönetimi ilkeleri, kuruluşunuzun içeriği ne kadar süreyle saklayacaklarını denetlemesine, kişilerin içerikle ne yaptığını denetlemesine ve belgelere barkod veya etiket eklemesine olanak tanır. Bir ilke, yasal ve resmi düzenlemelere veya iç iş süreçlerine uyumluluğun uygulanmasına yardımcı olabilir. Yönetici olarak, belgelerin nasıl izleyebileceğinizi ve belgelerin ne kadar süreyle tutulabileceğini denetlemek için bir ilke ayarlayabilirsiniz.

Site hiyerarşisinde en genişten en dara kadar üç farklı konumda bilgi yönetimi ilkesi oluşturabilirsiniz:

- Site koleksiyonundaki birden çok içerik türünde kullanılacak bir ilke oluşturun.
- Site içerik türü için bir ilke oluşturun.
- Liste veya kitaplık için bir ilke oluşturun.

Daha fazla bilgi için bkz. [Bilgi yönetimi ilkelerine giriş](intro-to-info-mgmt-policies.md).

## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Site koleksiyonu içinde birden çok içerik türü için ilke oluşturma
<a name="__toc261001590"> </a>

Bir bilgi ilkesinin site koleksiyonu içindeki belirli bir türdeki tüm belgelere uygulandığından emin olmak için, ilkeyi site koleksiyonu düzeyinde oluşturmayı ve daha sonra ilkeyi içerik türlerine uygulamayı göz önünde bulundurun. Bunlar site koleksiyonu ilkeleri olarak adlandırılır.

1. Site koleksiyonu giriş sayfasında \> başlık çubuğundaki **Ayarlar**![ SharePoint 2016 Ayarlar düğmesi.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Site Ayarlar**.

    Gruba bağlı SharePoint bir sitede **, Ayarlar'a** tıklayın, **Site İçeriği'ne** tıklayın ve ardından **Site Ayarlar'ne** tıklayın.

2. Site Ayarlar sayfasında, **Site Koleksiyonu Yönetimi** \> **İçerik Türü İlke Şablonları** altında.

   ![Site Ayarlar sayfasındaki İçerik Türü İlkesi Şablonu bağlantısı.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. İlkeler sayfasında \> **Oluştur'u seçin**.

4. İlke için bir ad ve açıklama girin ve kullanıcılara ilkenin ne için olduğunu açıklayan kısa bir ilke deyimi yazın.

5. İlkeyle ilişkilendirmek istediğiniz özellikleri ayarlamayı öğrenmek için bir site içerik türü için ilke oluşturma ile ilgili sonraki bölüme bakın.

6. **Tamam**'ı seçin.

## <a name="create-a-policy-for-a-site-content-type"></a>Site içerik türü için ilke oluşturma
<a name="__create_a_policy"> </a>

İçerik türüne bilgi yönetimi ilkesi eklemek, ilke özelliklerini birden çok liste veya kitaplıkla ilişkilendirmeyi kolaylaştırır. İçerik türüne mevcut bir bilgi yönetimi ilkesi eklemeyi veya tek bir içerik türüne özgü benzersiz bir ilke oluşturmayı seçebilirsiniz.

 Ayrıca, listelere özgü bir içerik türüne bilgi yönetimi ilkesi de ekleyebilirsiniz. Bu, ilkeyi yalnızca bu listedeki içerik türünü kullanan öğelere uygulama etkisine sahiptir.

1. Site koleksiyonu giriş sayfasında \> başlık çubuğundaki **Ayarlar**![ SharePoint 2016 Ayarlar düğmesi.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Site Ayarlar**.

    Gruba bağlı SharePoint bir sitede **, Ayarlar'a** tıklayın, **Site İçeriği'ne** tıklayın ve ardından **Site Ayarlar'ne** tıklayın.

2. Site Ayarlar sayfasında, **Web Tasarımcısı Galerileri** \> **Site içerik türleri** altında.

   ![Site Ayarlar sayfasında site içerik türleri bağlantısı.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)

3. Site İçerik Türü Ayarlar sayfasında, ilke eklemek istediğiniz içerik türünü seçin.

4. Site İçerik Türü sayfasında, **Ayarlar** \> **Bilgi yönetimi ilkesi ayarları** altında.

5. İlkeyi Düzenle sayfasında, ilke için bir ad ve açıklama girin ve kullanıcılara ilkenin ne için olduğunu açıklayan kısa bir açıklama yazın.

6. Sonraki bölümlerde, bilgi yönetimi ilkenize eklemek istediğiniz tek tek ilke özelliklerini seçin.

   ![İçerik ilkesi türleri.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)

7. Bu ilkeye tabi olan belgeler ve öğeler için bir bekletme süresi belirtmek için **Bekletmeyi Etkinleştir'i** seçin ve ardından öğelerin süresi dolduğunda gerçekleşmesini istediğiniz bekletme süresini ve eylemleri belirtin.

   Bekletme süresi belirtmek için:

   1. **Kayıtlar için bekletme aşaması ekle'yi** seçin.

   2. Belgelerin veya öğelerin süresinin ne zaman dolacağını belirtmek için bir bekletme süresi seçeneği belirleyin. Aşağıdaki adımlardan birini yapın:
      - Son kullanma tarihini bir tarih özelliğine göre ayarlamak için, **Olay** \> **Bu aşama öğedeki bir tarih özelliğini temel alır** altında, belge veya öğe eylemini (örneğin, Oluşturuldu veya Değiştirildi) ve öğenin süresinin dolmasını istediğiniz bu eylemden sonraki süreyi (örneğin, gün, ay veya yıl sayısı) seçin.
      - Süre sonunu belirlemek üzere özel saklama formülü kullanmak için **Bu sunucuda yüklü olan özel saklama formülüyle ayarla'yı** seçin.

        > [!NOTE]
        > Bu seçenek yalnızca yöneticiniz tarafından özel bir formül ayarlandıysa kullanılabilir.

   3. İş akışı başlat seçeneği yalnızca kendisiyle ilişkilendirilmiş bir **iş akışına** sahip olan bir liste, kitaplık veya içerik türü için ilke tanımlıyorsanız kullanılabilir. Ardından, aralarından seçim yapabileceğiniz bir iş akışı seçeneği sunulur.

   4. **Yinelenme** bölümünde **Bu aşamanın eylemini yinele...** öğesini seçin ve eylemin ne sıklıkta yeniden yinelemesini istediğinizi girin.

      > [!NOTE]
      >  Bu seçenek yalnızca seçtiğiniz eylemin yinelenebilir olması durumunda kullanılabilir. Örneğin, **Kalıcı Olarak Sil** eylemi için yinelenme ayarlayamazsınız.

   5. **Tamam**'ı seçin.

8. Bu ilkeye tabi belgeler ve öğeler için denetimi etkinleştirmek için **Denetimi Etkinleştir'i** seçin ve ardından denetlemek istediğiniz olayları belirtin.

   Denetimi etkinleştirmek için:

   1. İlkeyi Düzenle sayfasında **Denetim** altında **Denetimi etkinleştir'i** seçin ve ardından denetim kaydını tutmak istediğiniz olayların yanındaki onay kutularını seçin.

   2. Kullanıcılardan bu barkodları belgelere eklemelerini iste seçeneğini belirlemek **için Kullanıcılardan kaydetmeden veya yazdırmadan önce barkod eklemelerini iste'yi** seçin.

   3. Denetim özelliğini ilkeye uygulamak için **Tamam'ı** seçin.

   Denetim İlkesi özelliği, kuruluşların belgeler için denetim izleri oluşturmasına ve çözümlemesine ve görev listeleri, sorun listeleri, tartışma grupları ve takvimler gibi öğeleri listelemesine olanak tanır. Bu ilke özelliği, içeriğin görüntülendiği, düzenlendiği veya silindiği durumlar gibi olayları kaydeden bir denetim günlüğü sağlar.

   Denetim bir bilgi yönetimi ilkesinin parçası olarak etkinleştirildiğinde, yöneticiler denetim verilerini Microsoft Excel temel alan ve geçerli kullanımı özetleyen ilke kullanım raporlarında görüntüleyebilir. Yöneticiler, bilgilerin kuruluş içinde nasıl kullanıldığını belirlemek için bu raporları kullanabilir. Bu raporlar, kuruluşların mevzuat uyumluluğunu doğrulamalarına ve belgelemelerine veya olası endişeleri araştırmalarına da yardımcı olabilir.

   Denetim günlüğü şu bilgileri kaydeder: olay adı, olayın tarih ve saati ve eylemi gerçekleştiren kullanıcının sistem adı.

9. Barkodlar bir ilkenin parçası olarak etkinleştirildiğinde belge özelliklerine eklenir ve barkodun uygulandığı belgenin üst bilgi alanında görüntülenir. Etiketler gibi barkodlar da belgeden el ile kaldırılabilir. Bir öğeyi yazdırırken veya kaydederken kullanıcılardan barkodu eklemelerinin istenip istenmeyeceğini veya barkodu 2010 Office yayın programlarındaki **Ekle** sekmesi kullanılarak el ile eklenip eklenmeyeceğini belirtebilirsiniz.

   Barkodları etkinleştirmek için:

   1. **Barkodlar** altındaki **İlkeyi Düzenle** sayfasında **Barkodları Etkinleştir'i** seçin.

   2. Kullanıcılardan bu barkodları belgelere eklemelerini iste seçeneğini belirlemek **için Kullanıcılardan kaydetmeden veya yazdırmadan önce barkod eklemelerini iste'yi** seçin.

   3. Barkod özelliğini ilkeye uygulamak için **Tamam'ı** seçin.

   Barkod ilkesi Code 39 standart barkodları oluşturur. Her barkod görüntüsü, barkod değerini temsil eden barkod simgesinin altında metin içerir. Bu, barkod verilerinin donanım tarama özelliği kullanılamadığında bile kullanılmasını sağlar. Kullanıcılar, sitedeki öğeyi bulmak için barkod numarasını arama kutusuna el ile yazabilir.  <br/> |

10. Bu ilkeye tabi olan belgelerin etiketleri olmasını zorunlu kılmak için **Etiketleri Etkinleştir'i** seçin ve etiketler için istediğiniz ayarları belirtin.

    Etiketleri etkinleştirmek için:

    1. Kullanıcıların belgeye etiket eklemesini istemek için **Kaydetmeden veya yazdırmadan önce kullanıcılardan etiket eklemelerini iste'yi** seçin.

       > [!NOTE]
       > Etiketlerin isteğe bağlı olmasını istiyorsanız, bu onay kutusunu seçmeyin.

    2. Etiket eklendikten sonra değiştirilemeyecek şekilde kilitlemek için Etiket **eklendikten sonra etiket değişikliklerini engelle'yi** seçin.

       Bu ayar, etiket word, Excel veya PowerPoint gibi bir istemci uygulaması içindeki bir öğeye eklendikten sonra etiket metninin güncelleştirilmesini engeller. Bu belgenin veya öğenin özellikleri güncelleştirildiğinde etiketin güncelleştirilmesini istiyorsanız, bu onay kutusunu seçmeyin.

    3. Etiket biçimi kutusuna etiketin metnini görüntülenmesini istediğiniz şekilde girin. Etiketler en fazla 10 sütun başvurusu içerebilir ve bunların her biri en fazla 255 karakter uzunluğunda olabilir. Etiketinizin biçimini oluşturmak için aşağıdaki adımları uygulayın:
       - Etikete eklemek istediğiniz sütunların adlarını, görünmesini istediğiniz sırayla yazın. İlkeyi Düzenle sayfasındaki örnekte gösterildiği gibi sütun adlarını köşeli ayraçlar ({} ) içine alın.
       - İlkeyi Düzenle sayfasındaki örnekte gösterildiği gibi köşeli ayraçların dışındaki sütunları tanımlamak için sözcükler yazın.

    4. Satır sonu eklemek için, satır sonunun görünmesini istediğiniz **yere\n** girin.

    5. İstediğiniz yazı tipi boyutunu ve stilini seçin ve etiketin belgenin içinde sola mı, ortaya mı yoksa sağa mı konumlandırılacağını belirtin.

       Kullanıcıların bilgisayarlarında kullanılabilen bir yazı tipi ve stil seçin. Yazı tipinin boyutu, etikette ne kadar metin görüntülenebileceğini etkiler.

    6. Etiketin yüksekliğini ve genişliğini girin. Etiket yüksekliği 0,25 inç ile 20 inç arasında, etiket genişliği ise 0,25 inç ile 20 inç arasında değişebilir. Etiket metni her zaman etiket resmi içinde dikey olarak ortalanır.

    7. Etiket içeriğini önizlemek için **Yenile'yi** seçin.

11. **Tamam**'ı seçin.

## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Liste, kitaplık veya klasör için ilke oluşturma (konum tabanlı bekletme ilkesi)
<a name="__create_a_policy"> </a>

Yalnızca belirli bir liste, kitaplık veya klasör için geçerli olan bir bekletme ilkesi tanımlayabilirsiniz. Ancak, bu şekilde bir bekletme ilkesi oluşturursanız, bu ilkeyi diğer listelerde, kitaplıklarda, klasörlerde veya sitelerde yeniden kullanamazsınız ve konum tabanlı bir ilkeye site koleksiyonu ilkesi uygulayamazsınız.

Tek bir konumdaki tüm içerik türlerine tek bir bekletme ilkesi uygulamak istiyorsanız, büyük olasılıkla konum tabanlı saklamayı kullanmak istersiniz. Diğer çoğu durumda, tüm içerik türleri için bir bekletme ilkesinin belirtildiğini doğrulamak istersiniz.

Devralmayı kesmeyi ve alt düzeyde yeni bir bekletme ilkesi tanımlamayı seçmediğiniz sürece, her alt klasör üst öğesinin bekletme ilkesini devralır.

Bir liste veya kitaplıkta bekletme dışında bir bilgi yönetimi ilkesi tanımlamak istiyorsanız, bu liste veya kitaplıkla ilişkilendirilmiş her bir liste içerik türü için bir bilgi yönetimi ilkesi tanımlamanız gerekir.

Herhangi bir noktada bir liste veya kitaplık için içerik türünden konum tabanlı ilkelere geçmeye karar verirseniz, konum tabanlı ilke olarak yalnızca bekletme ilkesi kullanılır. Diğer tüm yönetim ilkeleri (denetimler, barkodlar ve barkodlar) ilişkili içerik türlerinden devralınır.

Kitaplık ve Klasör Tabanlı Saklama özelliği devre dışı bırakılarak site koleksiyonu için konum tabanlı ilkeler devre dışı bırakılabilir. Bu, site koleksiyonu yöneticilerinin içerik türü ilkelerinin liste yöneticisinin konum tabanlı ilkeleri tarafından geçersiz kılınmadığından emin olmasını sağlar.

Liste veya kitaplığın bilgi yönetimi ilkesi ayarlarını değiştirmek için en azından Listeleri Yönet iznine sahip olmanız gerekir.

1. Bilgi yönetimi ilkesi belirtmek istediğiniz listeye veya kitaplığa gidin.

2. Şeritte **Kitaplık** veya **Liste** sekmesi \> **Kitaplık Ayarlar** veya **Liste Ayarlar** seçin.

   SharePoint Online'da **Ayarlar** ve ardından **Liste ayarları'nı** veya **Kitaplık ayarları'nı** tıklatın.

3. **İzinler ve Yönetim**\> **Bilgileri yönetim ilkesi ayarları** altında.

   ![Belge kitaplığının ayarlar sayfasında bilgi yönetimi ilkeleri bağlantısı.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Bilgi Yönetimi İlkesi Ayarlar sayfasında, liste veya kitaplık için bekletme kaynağının Kitaplık ve Klasörler olarak ayarlandığından emin olun.

   Kaynak olarak **İçerik Türü** görünüyorsa **, Kaynağı Değiştir'e** ve ardından **Kitaplık ve Klasörler'e** tıklayın. İçerik türü saklama ilkelerinin yoksayılacağı konusunda uyarılırsınız. **Tamam**'ı seçin.

5. İlkeyi Düzenle sayfasında, **Kitaplık Tabanlı Bekletme Zamanlaması'nın** altında, oluşturduğunuz ilke için kısa bir açıklama girin.

6. **Bekletme aşaması ekle...** öğesini seçin.

   Kayıtlar'ın altında Kayıtlar için farklı bekletme aşamaları tanımla seçeneğini belirleyerek kayıtlar için farklı bekletme ilkeleri tanımlamayı seçebilirsiniz.

7. Aşama özellikleri iletişim kutusunda, belgelerin veya öğelerin süresinin ne zaman dolacağını belirtmek için bir bekletme süresi seçeneği belirleyin. Şunlardan birini yapın:

   - Son kullanma tarihini bir tarih özelliğine göre ayarlamak için, **Olay** \> **Bu aşama öğedeki bir tarih özelliğini temel alır** altında, belge veya öğe eylemini (örneğin, Oluşturuldu veya Değiştirildi) ve öğenin süresinin dolmasını istediğiniz bu eylemden sonraki süreyi (örneğin, gün, ay veya yıl sayısı) seçin.

   - Süre sonunu belirlemek üzere özel saklama formülü kullanmak için **Bu sunucuda yüklü olan özel saklama formülüyle ayarla'yı** seçin.

     > [!NOTE]
     >  Bu seçenek yalnızca yöneticiniz tarafından özel bir formül ayarlandıysa kullanılabilir.

   - **Eylem'in** altında, belgenin veya öğenin süresi dolduğunda ne olmasını istediğinizi belirtin. Belge veya öğeye belirli bir eylemin gerçekleşmesini (silme gibi) etkinleştirmek için listeden bir eylem seçin.

8. İş akışı başlat seçeneği yalnızca kendisiyle ilişkilendirilmiş bir **iş akışına** sahip olan bir liste, kitaplık veya içerik türü için ilke tanımlıyorsanız kullanılabilir. Ardından, aralarından seçim yapabileceğiniz bir iş akışı seçeneği sunulur.

9. **Yinelenme'nin** altında **Bu aşamanın eylemini yinele...** öğesini seçin ve eylemin ne sıklıkta yinelenmek istediğinizi girin.

   > [!NOTE]
   >  Bu seçenek yalnızca seçtiğiniz eylemin yinelenebilir olması durumunda kullanılabilir. Örneğin, **Kalıcı Olarak Sil** eylemi için yinelenme ayarlayamazsınız.

10. **Tamam**'ı seçin.

## <a name="apply-a-site-collection-policy-to-a-content-type"></a>İçerik türüne site koleksiyonu ilkesi uygulama
<a name="__apply_a_site"> </a>

Siteniz için bilgi yönetimi ilkeleri site koleksiyonu ilkeleri olarak zaten oluşturulduysa, ilkelerden birini bir içerik türüne uygulayabilirsiniz. Bunu yaparak, aynı ilkeyi aynı üst içerik türünü paylaşmayan bir site koleksiyonundaki birden çok içerik türüne uygulayabilirsiniz.

 Bir site koleksiyonundaki birden çok içerik türüne ilke uygulamak istiyorsanız ve yapılandırılmış bir Yönetilen Meta Veri Hizmetiniz varsa, bilgi yönetimi ilkelerini birden çok site koleksiyonuna yayımlamak için İçerik Türü Yayımlama'yı kullanabilirsiniz. Daha fazla bilgi için [Site koleksiyonları arasında ilke uygulama](#apply-a-policy-across-site-collections) bölümüne bakın.

1. İlke uygulamak istediğiniz içerik türünü içeren listeye veya kitaplığa gidin.

2. Şeritte **Kitaplık** veya **Liste** sekmesi \> **Kitaplık Ayarlar** veya **Liste Ayarlar** seçin.

   SharePoint Online'da **Ayarlar** ve ardından **Liste ayarları'nı** veya **Kitaplık ayarları'nı** tıklatın.

3. **İzinler ve Yönetim** \> **Bilgileri yönetim ilkesi ayarları** altında.

   ![Belge kitaplığının ayarlar sayfasında bilgi yönetimi ilkeleri bağlantısı.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. İlke kaynağının **İçerik Türleri** olarak ayarlandığını doğrulayın ve **İçerik Türü İlkeleri'nin** altında ilkeyi uygulamak istediğiniz içerik türünü seçin.

5. **İlke** \> Belirtin **Site koleksiyonu ilkesi kullan'ın** altında, listeden uygulamak istediğiniz ilkeyi seçin.

   > [!NOTE]
   >  **Site koleksiyonu ilkesi kullan** seçeneği kullanılamıyorsa, site koleksiyonu için hiçbir site koleksiyonu ilkesi tanımlanmamıştır.

6. **Tamam**'ı seçin.

   Çalıştığınız liste veya kitaplık birden çok içerik türünün yönetimini destekliyorsa, **İçerik Türleri'nin** altında bilgi yönetimi ilkesi belirtmek istediğiniz içerik türünü seçebilirsiniz. Bu sizi doğrudan yukarıdaki 5. adıma götürür.

## <a name="apply-a-policy-across-site-collections"></a>Site koleksiyonları arasında ilke uygulama
<a name="__toc260646789"> </a>

İçerik türü yayımlamayı ayarlamak için Yönetilen Meta Veri hizmeti uygulamasını kullanarak site koleksiyonları arasında içerik türlerini paylaşın. İçerik türleri merkezi olarak oluşturulup güncelleştirilebileceğinden ve güncelleştirmeler birden çok abone site koleksiyonunda veya Web uygulamasında yayımlanabildiği için içerik türü yayımlama, içeriği ve meta verileri siteleriniz arasında tutarlı bir şekilde yönetmenize yardımcı olur.

## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Site koleksiyonları arasında kullanmak üzere mevcut bir ilkeden şablon oluşturma
<a name="__toc262125409"> </a>

Bir bilgi yönetimi ilkesi tanımlayabilir ve ardından birden çok site koleksiyonunda gerektiği gibi kullanmak üzere bu ilkeden bir şablon oluşturabilirsiniz. Bu yöntem, bilgi ilkelerinizin yedeğini almak istiyorsanız veya site koleksiyonları arasında bir ilke uygulamak için içerik türü yayımlamayı kullanmak için alternatif bir yöntem olarak da kullanılabilir. İlkeyi bir site koleksiyonundan dışarı aktarıp kaydedilmiş bir konuma veya başka bir site koleksiyonuna aktararak ilkenin şablonunu veya yedeğini oluşturursunuz.

> [!IMPORTANT]
> İlke şablonları kümesi oluşturmanın bir yolu olarak dışarı/içeri aktarma özelliğini kullanıyorsanız, ilke .xml dosyasında benzersiz bir tanımlayıcı olduğunu unutmayın. Bu nedenle, bu benzersiz tanımlayıcıyı değiştirmeden bu ilkeyi bir siteye birden çok kez aktaramazsınız.

### <a name="export-a-policy"></a>İlkeyi dışarı aktarma
<a name="__toc260646790"> </a>

1. Site koleksiyonu giriş sayfasında, **Site Ayarlar** yerini alan Ayarlar ![Small Ayarlar dişlisini seçin.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Site Ayarlar**.

   Gruba bağlı SharePoint bir sitede **, Ayarlar'a** tıklayın, **Site İçeriği'ne** tıklayın ve ardından **Site Ayarlar'ne** tıklayın.

2. Site Ayarlar sayfasında, **Site Koleksiyonu Yönetimi** \> **İçerik Türü İlke Şablonları** altında.

   ![Site Ayarlar sayfasındaki İçerik Türü İlkesi Şablonu bağlantısı.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Dışarı \> aktarmak istediğiniz ilkeyi seçerek en alttaki \> **Dışarı Aktar'a** gidin.

4. Dosyayı kaydetme veya açma isteminde **Kaydet'i** seçin ve ardından dosyayı kaydetmek için bir konum seçin. İlkeyi içeri aktaran site koleksiyonlarının kullanabileceği bir konum seçtiğinizden emin olun.

5. İndirme Tamamlandı iletişim kutusu görüntülendiğinde **Kapat'ı** seçin.

### <a name="import-a-policy-to-a-different-site-collection"></a>İlkeyi farklı bir site koleksiyonuna aktarma
<a name="__toc260646791"> </a>

Bilgi yönetimi ilkesini içeri aktarmak, bu ilkeyi belirli bir site koleksiyonundaki site veya liste düzeyindeki birden çok içerik türüne uygulamanızı sağlar. Bunu yapmanın avantajları iki katına çıkar: her içerik türünde ilkeyi yeniden tanımlamanız ve uygulamanız gerekmez ve ilkede tek bir yerde değişiklik yaparak ilke değişikliklerini daha kolay yönetebilirsiniz.

1. İlkeyi uygulamak istediğiniz site koleksiyonunun giriş sayfasında Site Ayarlar yerini alan **Ayarlar**![ Tüm Ayarlar dişlisini seçin.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Site Ayarlar**.

   Gruba bağlı SharePoint bir sitede **, Ayarlar'a** tıklayın, **Site İçeriği'ne** tıklayın ve ardından **Site Ayarlar'ne** tıklayın.

2. Site Ayarlar sayfasında, **Site Koleksiyonu Yönetimi** \> **İçerik Türü İlke Şablonları** altında.

3. İlkeler sayfasında\>, ilkenin XML dosyasını bulmak için **Gözat'ı** **içeri aktarın**\>.

4. İlkenin kaydedildiği \> XML dosyasını **Aç'ı** seçin.

5. site koleksiyonuna ilke eklemek için Site Koleksiyonu **İlkesini İçeri Aktar** sayfasında \> İçeri Aktar'ı seçin.

İçeri aktarılan ilkeniz artık site veya liste düzeyinde bir veya birden çok içerik türüne uygulanabilir.

Bilgi yönetimi ilkeleri, kuruluşunuzun içeriği ne kadar süreyle saklayacaklarını denetlemesine, kişilerin içerikle ne yaptığını denetlemesine ve belgelere barkod veya etiket eklemesine olanak tanır. Bir ilke, yasal ve resmi düzenlemelere veya iç iş süreçlerine uyumluluğun uygulanmasına yardımcı olabilir. Yönetici olarak, belgelerin nasıl izleyebileceğinizi ve belgelerin ne kadar süreyle tutulabileceğini denetlemek için bir ilke ayarlayabilirsiniz.

Site hiyerarşisinde en genişten en dara kadar üç farklı konumda bilgi yönetimi ilkesi oluşturabilirsiniz:

- Site koleksiyonundaki birden çok içerik türünde kullanılacak bir ilke oluşturun.
- Site içerik türü için bir ilke oluşturun.
- Liste veya kitaplık için bir ilke oluşturun.

Daha fazla bilgi için bkz. [Bilgi yönetimi ilkelerine giriş](intro-to-info-mgmt-policies.md).
