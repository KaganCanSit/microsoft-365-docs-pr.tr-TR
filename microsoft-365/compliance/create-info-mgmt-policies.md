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
description: Bilgilerin ne kadar süreyle tutul tutulacaklarını kontrol etmek ve bu bilgileri kimlerin kullananları izlemek için bilgi yönetimi ilkesi ayarlamayı öğrenin.
ms.openlocfilehash: f8a4400e890e02ecd7ac57011770ff4a23a1a5e1
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014337"
---
# <a name="create-and-apply-information-management-policies"></a>Bilgi yönetimi ilkeleri oluşturma ve uygulama

Bilgi yönetimi ilkeleri, kuruluşlarının içeriği ne kadar süre boyunca tutması, içerikle insanların neler yaptığını denetlemesi ve belgelere barkod veya etiket eklemesi gibi birçok denetime olanak sağlar. Bir ilke yasal ve resmi düzenlemelere veya şirket içi iş süreçlerine uyumluluğun zorunlu kılınmalarına yardımcı olabilir. Yönetici olarak, belgeleri izleme ve belgelerin ne kadar süreyle korunacaklarını denetlemeyi altına alan bir ilke kurabilirsiniz.

Bilgi yönetimi ilkesi oluşturmak için, site hiyerarşisinde en geniş konumdan en dar konuma kadar üç farklı konumda yer alan bir ilke oluşturabilirsiniz:

- Site koleksiyonu içinde birden çok içerik türü kullanmak üzere bir ilke oluşturun.
- Site içerik türü için ilke oluşturma.
- Liste veya kitaplık için ilke oluşturma.

Daha fazla bilgi için bkz [. Bilgi yönetimi ilkelerine giriş](intro-to-info-mgmt-policies.md).

## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Site koleksiyonu içinde birden çok içerik türü için ilke oluşturma
<a name="__toc261001590"> </a>

Bilgi ilkesi'nin site koleksiyonu içinde belirli bir türe sahip tüm belgelere uygulandığından emin olmak için, site koleksiyonu düzeyinde bir ilke oluşturmayı göz önünde bulundurabilirsiniz ve sonra bu ilkeyi içerik türlerine uygulayabilirsiniz. Bunlara site koleksiyonu ilkeleri de denmektedir.

1. 2016 site \> **koleksiyonunun Ayarlar**![ SharePoint giriş Ayarlar düğmesi.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Site Ayarlar**.

    Grup bağlantılı SharePoint, Site İçeriği'ne Ayarlar Site İçeriği'ne **ve** ardından Site **İçeriği'ne Ayarlar**.

2. Site Koleksiyonu sayfasında Ayarlar **Koleksiyonu** \> Yönetimi **İçerik Türü İlkesi Şablonları'nın altında**.

   ![Site Web Sitesi sayfasında İçerik Türü İlke Ayarlar bağlantısı.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. İlkeler sayfasında **Oluştur'a**\> tıklayın.

4. İlke için bir ad ve açıklama girin, sonra da kullanıcılara ilkenin ne için olduğunu açıklayan kısa bir ilke bildirimi yazın.

5. İlkeyle ilişkilendirmek istediğiniz özellikleri ayarlamayı öğrenmek için, site içerik türü için ilke oluşturmayla ilgili sonraki bölüme bakın.

6. **Tamam**'ı seçin.

## <a name="create-a-policy-for-a-site-content-type"></a>Site içerik türü için ilke oluşturma
<a name="__create_a_policy"> </a>

İçerik türüne bilgi yönetimi ilkesi eklemek, ilke özelliklerini birden çok liste veya kitaplıkla ilişkilendirmeyi kolaylaştırır. Var olan bir bilgi yönetimi ilkesini içerik türüne eklemeyi veya tek tek içerik türüne özgü benzersiz bir ilke oluşturmayı seçebilirsiniz.

 Ayrıca, listelere özel içerik türüne bilgi yönetimi ilkesi de ebilirsiniz. Bu, ilkenin yalnızca o listede içerik türünü kullanan öğelere uygulanmasına neden olur.

1. 2016 site \> **koleksiyonunun Ayarlar**![ SharePoint giriş Ayarlar düğmesi.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Site Ayarlar**.

    Grup bağlantılı SharePoint, Site İçeriği'ne Ayarlar Site İçeriği'ne **ve** ardından Site **İçeriği'ne Ayarlar**.

2. Site Tasarımcısı Ayarlar, **Web Tasarımcısı Galerileri** \> **Site içerik türleri altında**.

   ![Site sayfası sayfasında site Ayarlar bağlantısı.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)

3. Site İçerik Türü Ayarlar sayfasında, ilke eklemek istediğiniz içerik türünü seçin.

4. Site İçerik Türü sayfasında, İçerik Yönetimi **Ayarlar** \> **ayarlarına tıklayın**.

5. İlkeyi Düzenle sayfasında, ilke için bir ad ve açıklama girin, sonra da kullanıcılara ilkenin ne için olduğunu açıklayan kısa bir açıklama yazın.

6. Sonraki bölümlerde, bilgi yönetimi ilkenize eklemek istediğiniz tek tek ilke özelliklerini seçin.

   ![İçerik ilkelerinin türleri.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)

7. Bu ilkeye tabi belgeler ve öğeler için bir bekletme süresi belirtmek için, Bekletmeyi Etkinleştir'i seçin, ardından bekletme süresini ve öğeler sona erdiğinde gerçekleşmesini istediğiniz eylemleri belirtin.

   Bekletme süresi belirtmek için:

   1. Kayıtlar **için bekletme aşaması ekle'yi seçin**.

   2. Belgelerin veya öğelerin süresinin ne zaman dolsa geçe ayarlan hazır olduğunu belirtmek için bir bekletme süresi seçeneği belirtin. Aşağıdaki adımlardan birini yapın:
      - Bir tarih özelliğine dayalı olarak son kullanma tarihini ayarlamak için,  \> Olay Bu aşama'nın altında öğenin tarih özelliğini temel alan bir belge veya öğe eylemi (örneğin, Oluşturuldu veya Değiştirildi) ve bu eylemden sonra gelen zaman artımını (örneğin, gün, ay veya yıl sayısı) seçin.
      - Süre dolmayı belirlemek üzere özel bir bekletme formülü kullanmak için, **Bu sunucuda yüklü özel bir bekletme formülüyle ayarla'ya seçin**.

        > [!NOTE]
        > Bu seçenek yalnızca yöneticiniz tarafından özel bir formül ayarlanmışsa kullanılabilir.

   3. İş **akışı başlat** seçeneği yalnızca, zaten ilişkili bir iş akışı olan bir liste, kitaplık veya içerik türü için ilke tanımlarsanız kullanılabilir. Bundan sonra size seçim yapmak için bir iş akışı seçeneği verilir.

   4. Yinelenme **bölümünde** Bu aşamanın **eylemini yinele... öğesini** seçin ve sonra eylemin yinelenme sıklıklarını girin.

      > [!NOTE]
      >  Bu seçenek yalnızca seçtiğiniz eylem yinelenirse kullanılabilir. Örneğin, eylem için yinelenmeyi Kalıcı Olarak Sil **olarak ayarilemez**.

   5. **Tamam**'ı seçin.

8. Bu ilkeye tabi belgeler ve öğeler için denetimi etkinleştirmek için, Denetimi Etkinleştir'i seçin ve ardından denetlenecek olayları belirtin.

   Denetimi etkinleştirmek için:

   1. Denetim altındaki İlkeyi Düzenle **sayfasında,** Denetimi etkinleştir'i seçin ve sonra da denetim izi tutmak istediğiniz olayların yanındaki onay kutularını seçin.

   2. Kullanıcılardan bu barkodları belgelere eklemelerini istemi için, Kaydetmeden veya yazdırmadan önce barkod eklemek **için kullanıcılara sor'ı seçin**.

   3. Denetim **özelliğini** ilkeye uygulamak için Tamam'ı seçin.

   Denetim İlkesi özelliği, kuruluşların belgelerle ilgili denetim izleri oluşturmalarını ve görev listeleri, sorun listeleri, tartışma grupları ve takvimler gibi öğeleri listeleyişlerini oluşturmalarını ve çözümlemelerini sağlar. Bu ilke özelliği, içerik görüntülenemez, düzenlenemez veya silindiğinde olduğu gibi olayları kaydeden bir denetim günlüğü sağlar.

   Bilgi yönetimi ilkesi kapsamında denetim etkinleştirildiğinde, yöneticiler denetim verilerini MICROSOFT EXCEL'de temel alan ve geçerli kullanımı özetleyen ilke kullanım raporlarında ilebilir. Yöneticiler bu raporları, kuruluşun içinde bilgilerin nasıl kullanıla olduğunu belirlemek için kullanabilir. Bu raporlar, kuruluşların yasal düzenlemelere uyumlarını doğrulamalarına, belgelelerine veya olası kaygıları araştırmalarına da yardımcı olabilir.

   Denetim günlüğü şu bilgileri kayıtlar: olay adı, olayın tarihi ve saati ve eylemi yapan kullanıcının sistem adı.

9. Barkodlar bir ilkenin parçası olarak etkinleştirildiğinde, belge özelliklerine eklenir ve barkodların uygulandığı belgenin üst bilgi alanında görüntülenir. Etiketler gibi, barkodlar da belgeden el ile kaldırılabilir. Bir öğeyi yazdırırken veya yazdırırken kullanıcılardan barkod eklemesi istenip sorulmay olacağını veya 2010 veya sürüm programlarında  Ekle sekmesi kullanılarak barkodların el ile ek isteyip Office belirtebilirsiniz.

   Barkodları etkinleştirmek için:

   1. **Barkodlar'ın altındaki** İlkeyi **Düzenle sayfasında Barkodları** **Etkinleştir'i seçin**.

   2. Kullanıcılardan bu barkodları belgelere eklemelerini istemi için, Kaydetmeden veya yazdırmadan önce barkod eklemek **için kullanıcılara sor'ı seçin**.

   3. Barkod **özelliğini** ilkeye uygulamak için Tamam'ı seçin.

   Barkod ilkesi Kod 39 standart barkodları üretir. Her barkod resmi, barkod değerini temsil eden barkod simgesinin altında metin içerir. Bu, donanım tarama özelliği kullanılabilir durumda değilken bile barkod verilerinin kullanılmaktadır. Kullanıcılar site üzerindeki öğeyi bulmak için arama kutusuna barkod numarasını el ile yazılabilir.  <br/> |

10. Bu ilkeye tabi belgelerin etiketlerinin olduğunu gerektirmek için, Etiketleri Etkinleştir'i seçin ve sonra etiketler için istediğiniz ayarları belirtin.

    Etiketleri etkinleştirmek için:

    1. Kullanıcıların belgeye etiket eklemelerini gerektirmek için, Kaydetmeden veya yazdırmadan önce etiket eklemek **için kullanıcılara sor'ı seçin**.

       > [!NOTE]
       > Etiketlerin isteğe bağlı olması için, bu onay kutusunu seçme.

    2. Etiketi, eklendikten sonra değiştiri önlemek için, Etiketlerin eklendikten sonra **değişmesini engelle'yi seçin**.

       Bu ayar, etiket Word, Excel veya Word gibi bir istemci uygulamasındaki bir öğeye eklendikten sonra etiket metninin güncelleştiril PowerPoint. Bu belge veya öğenin özellikleri güncelleştirildiğinde etiketin güncelleştiril istiyorsanız, bu onay kutusunu seçmeyin.

    3. Etiket biçimi kutusuna, etiketin biçimlendirilmiş olarak biçimlendirilmiş olan metnini girin. Etiketler en fazla 10 sütun başvurusu içerebilir ve bunların her biri en çok 255 karakter uzunluğunda olabilir. Etiketinizin biçimini oluşturmak için aşağıdaki adımları izleyin:
       - Etikete, görünmelerini istediğiniz sırada eklemek istediğiniz sütunların adlarını yazın. İlkeyi Düzenle sayfasındaki örnekte gösterildiği gibi{}, sütun adlarını kıvrımlı ayraç () içine alın.
       - İlkeyi Düzenle sayfasındaki örnekte gösterildiği gibi köşeli ayraçların dışındaki sütunları tanımlamak için sözcükler yazın.

    4. Satır sonu eklemek için, **satır\n** görünmesini istediğiniz yere satır sonu ifadesini girin.

    5. İstediğiniz yazı tipi boyutunu ve stilini seçin ve etiketin belgenin içinde sola mı, orta mı yoksa sağa mı konumlu olacaklarını belirtin.

       Kullanıcıların bilgisayarlarında kullanılabilen bir yazı tipi ve stil seçin. Yazı tipinin boyutu etikette ne kadar metnin görüntüleneyeceğini etkiler.

    6. Etiketin yüksekliğini ve genişliğini girin. Etiket yüksekliği 0,25 x 20 inç arasında, etiket genişliği de 0,25 x 20 inç arasında olabilir. Etiket metni, etiket görüntüsü içinde her zaman dikey olarak orta olur.

    7. Etiket **içeriğinin** önizlemesini görüntülemek için Yenile'yi seçin.

11. **Tamam**'ı seçin.

## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Liste, kitaplık veya klasör için ilke oluşturma (konum tabanlı bekletme ilkesi)
<a name="__create_a_policy"> </a>

Yalnızca belirli bir liste, kitaplık veya klasör için geçerli olan bir bekletme ilkesi tanımlayabilirsiniz. Öte yandan, bu şekilde bekletme ilkesi oluşturursanız, bu ilkeyi başka listelerde, kitaplıklarda, klasörlerde veya sitelerde yeniden kullanabilir ve konum tabanlı bir ilkeye site koleksiyonu ilkesi uygulayamazsınız.

Tek bir konumdaki tüm içerik türlerine tek bir bekletme ilkesi uygulamak için, büyük olasılıkla konum tabanlı bekletmeyi kullanmak istersiniz. Diğer çoğu durumda, tüm içerik türleri için bir bekletme ilkesi belirtilmiş olduğunu doğrulamak istersiniz.

Devralmayı kesmeyi ve alt düzeyde yeni bir bekletme ilkesi tanımlamayı seçmedikçe, her alt klasör üst klasörü bekletme ilkesi devralır.

Bir liste veya kitaplıkta bekletme dışında bir bilgi yönetimi ilkesi tanımlamak istemiyorsanız, bu liste veya kitaplıkla ilişkilendirilmiş tek tek her liste içerik türü için bir bilgi yönetimi ilkesi tanımlamanız gerekir.

Herhangi bir noktada içerik türünden liste veya kitaplık için konum tabanlı ilkelere geçmeye karar verdiyseniz, konum tabanlı ilke olarak yalnızca bekletme ilkesi kullanılır. Diğer tüm yönetim ilkeleri (denetimler, barkodlar ve barkodlar) ilişkili içerik türlerinden devralınabilir.

Konum tabanlı ilkeler, Kitaplık ve Klasör Tabanlı Bekletme özelliğini devre dışı bırakarak site koleksiyonunda devre dışı bırakılabilir. Bu, site koleksiyonu yöneticilerinin içerik türü ilkelerinin liste yöneticisinin konum tabanlı ilkeleri tarafından geçersiz kılınmalarını sağlamaya olanak sağlar.

Bir liste veya kitaplığın bilgi yönetimi ilkesi ayarlarını değiştirmek için en azından Listeleri Yönetme iznine ihtiyacınız vardır.

1. Bilgi yönetimi ilkesi belirtmek istediğiniz listeye veya kitaplıma gidin.

2. Şeritte Kitaplık veya Liste **sekmesi Kitaplık** **Kitaplığı'Ayarlar** \> **veya** **Liste** Ayarlar.

   Çevrimiçi SharePoint'de **Ekle'Ayarlar** liste **ayarları'nın veya Kitaplık ayarları'nın** **üzerine tıklayın**.

3. **İzinler ve Yönetim Bilgileri**\> **yönetimi ilkesi ayarları altında**.

   ![Belge kitaplığının ayarlar sayfasında bilgi yönetimi ilkeleri bağlantısı.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Bilgi Yönetimi İlkesi Ayarlar, liste veya kitaplık için bekletme kaynağının Kitaplık ve Klasörler olarak ayarlanmış olduğundan emin olun.

   Kaynak **olarak İçerik Türü** görünüyorsa, Kaynağı **Değiştir'e tıklayın ve** sonra da Kitaplık **ve Klasörler'e tıklayın**. İçerik türü bekletme ilkelerinin yok sayılacakları uyarısı gelir. **Tamam**'ı seçin.

5. İlkeyi Düzenle sayfasında, Kitaplık **Tabanlı Bekletme Zamanlaması'nın** altında, oluşturmakta olduğu ilke için kısa bir açıklama girin.

6. Bekletme **aşaması ekle... 'yi seçin.**

   Kayıtlar altında, Kayıtlar için farklı bekletme evreleri tanımla seçeneğini belirleyerek kayıtlar için farklı bekletme ilkeleri tanımlamayı seçebilirsiniz.

7. Aşama özellikleri iletişim kutusunda, belgelerin veya öğelerin süresinin ne zaman dolacak şekilde ayar olduğunu belirtmek için bir bekletme süresi seçeneği belirleyin. Şunlardan birini yapın:

   - Bir tarih özelliğine dayalı olarak son kullanma tarihini ayarlamak için,  \> Olay Bu aşama'nın altında öğenin tarih özelliğini temel alan bir belge veya öğe eylemi (örneğin, Oluşturuldu veya Değiştirildi) ve bu eylemden sonra gelen zaman artımını (örneğin, gün, ay veya yıl sayısı) seçin.

   - Süre dolmayı belirlemek üzere özel bir bekletme formülü kullanmak için, **Bu sunucuda yüklü özel bir bekletme formülüyle ayarla'ya seçin**.

     > [!NOTE]
     >  Bu seçenek yalnızca yöneticiniz tarafından özel bir formül ayarlanmışsa kullanılabilir.

   - **Eylem'in** altında, belgenin veya öğenin kullanım süresi dolduğunda ne olmasını istediğiniz belirtin. Belirli bir eylemin belge veya öğeye (silme işlemi gibi) olmasını sağlamak için, listeden bir eylem seçin.

8. İş **akışı başlat** seçeneği yalnızca, zaten ilişkili bir iş akışı olan bir liste, kitaplık veya içerik türü için ilke tanımlarsanız kullanılabilir. Bundan sonra size seçim yapmak için bir iş akışı seçeneği verilir.

9. **Yinelenme'nin** altında **Bu aşamanın eylemini yinele... 'yi seçin.** ve eylemin ne sıklıkta tekrar aşıllarını istediğiniz girin.

   > [!NOTE]
   >  Bu seçenek yalnızca seçtiğiniz eylem yinelenirse kullanılabilir. Örneğin, eylem için yinelenmeyi Kalıcı Olarak Sil **olarak ayarilemez**.

10. **Tamam**'ı seçin.

## <a name="apply-a-site-collection-policy-to-a-content-type"></a>İçerik türüne site koleksiyonu ilkesi uygulama
<a name="__apply_a_site"> </a>

Siteniz için bilgi yönetimi ilkeleri önceden site koleksiyonu ilkeleri olarak oluşturulmuşsa, ilkelerden birini içerik türüne uygulayabilirsiniz. Bunu yaparak, aynı ilkeyi bir site koleksiyonunda aynı üst içerik türünü paylaşmadan birden çok içerik türüne uygulayabilirsiniz.

 Bir site koleksiyonunda birden çok içerik türüne ilke uygulamak istiyorsanız ve yapılandırılmış bir Yönetilen Meta Veri Hizmetiniz varsa, bilgi yönetimi ilkelerini birden çok site koleksiyonuna yayımlamak için İçerik Türü Yayımlama'yı kullanabilirsiniz. Daha fazla bilgi [için Site koleksiyonları arasında ilke](#apply-a-policy-across-site-collections) uygulama bölümüne bakın.

1. İlkeyi uygulamak istediğiniz içerik türünü içeren listeye veya kitapa gidin.

2. Şeritte Kitaplık veya Liste **sekmesi Kitaplık** **Kitaplığı'Ayarlar** \> **veya** **Liste** Ayarlar.

   Çevrimiçi SharePoint'de **Ekle'Ayarlar** liste **ayarları'nın veya Kitaplık ayarları'nın** **üzerine tıklayın**.

3. **İzinler ve Yönetim Bilgileri** \> **yönetimi ilkesi ayarları altında**.

   ![Belge kitaplığının ayarlar sayfasında bilgi yönetimi ilkeleri bağlantısı.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. İlke kaynağının İçerik Türleri olarak ayar **olduğunu doğrulayın** ve İçerik Türü  İlkeleri altında, ilkeyi uygulamak istediğiniz içerik türünü seçin.

5. **İlkeyi Belirtin** \> **altında Site koleksiyonu ilkesi** kullan'ı seçin ve ardından listeden uygulamak istediğiniz ilkeyi seçin.

   > [!NOTE]
   >  Site **koleksiyonu ilkesi kullan seçeneği** kullanılamıyorsa, site koleksiyonu için hiçbir site koleksiyonu ilkesi tanımlanmamıştır.

6. **Tamam**'ı seçin.

   Birlikte çalıştığınız liste veya kitaplık birden çok içerik türünün yönetimini destekliyorsa, İçerik Türleri'nin  altında, bilgi yönetimi ilkesi belirtmek istediğiniz içerik türünü seçebilirsiniz. Bu sizi doğrudan yukarıdaki 5. Adıma götürmeyi sağlar.

## <a name="apply-a-policy-across-site-collections"></a>Site koleksiyonları arasında ilke uygulama
<a name="__toc260646789"> </a>

İçerik türü yayımlamayı ayarlamak için Yönetilen Meta Veri hizmeti uygulamasını kullanarak site koleksiyonları arasında içerik türlerini paylaşın. İçerik türü yayımlama, içeriği ve meta verileri siteleriniz genelinde tutarlı bir şekilde yönetmenize yardımcı olur, çünkü içerik türleri merkezi olarak oluşturulabilir ve güncelleştirilebilir ve güncelleştirmeler birden çok abone site koleksiyonunda veya Web uygulamalarında yayımlanır.

## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Site koleksiyonları arasında kullanmak üzere var olan bir ilkeden şablon oluşturma
<a name="__toc262125409"> </a>

Birden çok site koleksiyonunda gerektiğinde kullanmak üzere bir bilgi yönetimi ilkesi tanımlayabilir ve sonra ilkeden bir şablon oluşturabilirsiniz. Bu yöntem, bilgi ilkelerinizin bir yedeğini almak istediğiniz zaman veya site koleksiyonları arasında bir ilkeyi uygulamak için içerik türü yayımlamayı kullanmak için alternatif bir yöntem olarak da kullanılabilir. İlkeyi bir site koleksiyonundan dışarı aktararak ve sonra kaydedilmiş bir konuma veya başka bir site koleksiyonuna aktararak, ilkenin şablonunu veya yedeğini oluşturursunuz.

> [!IMPORTANT]
> Dışarı aktarma/içeri aktarma özelliğini bir dizi ilke şablonu oluşturmanın bir yolu olarak kullanıyorsanız, bu dosyanın ilke şablonunda benzersiz bir tanımlayıcının yer .xml unutmayın. Bu nedenle, bu benzersiz tanımlayıcıyı değiştirmeden bu ilkeyi bir siteye birden çok kez aktaramazsiniz.

### <a name="export-a-policy"></a>İlkeyi dışarı aktarma
<a name="__toc260646790"> </a>

1. Site koleksiyonu giriş sayfasında, Site **koleksiyonu'Ayarlar**![ yerini alan Ayarlar Small Ayarlar **dişlisi'Ayarlar**](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\>.

   Grup bağlantılı SharePoint, Site İçeriği'ne Ayarlar Site İçeriği'ne **ve** ardından Site **İçeriği'ne Ayarlar**.

2. Site Koleksiyonu sayfasında Ayarlar **Koleksiyonu** \> Yönetimi **İçerik Türü İlkesi Şablonları'nın altında**.

   ![Site Web Sitesi sayfasında İçerik Türü İlke Ayarlar bağlantısı.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Dışarı aktarmayı istediğiniz ilkeyi seçin, ekranı \> alttaki Dışarı Aktar seçeneğine \> **kaydırın**.

4. Dosyayı kaydetme veya açma isteminde Kaydet'i **seçin** ve sonra da dosyanın kayded silinecek konumunu seçin. İlkeyi içeri aktaran site koleksiyonlarının kullanmakta olduğu bir konum seçmeye emin olun.

5. İndirme Tamamlandı iletişim kutusu görüntülendiğinde Kapat'ı **seçin**.

### <a name="import-a-policy-to-a-different-site-collection"></a>İlkeyi farklı bir site koleksiyonuna aktarma
<a name="__toc260646791"> </a>

Bilgi yönetimi ilkesi içeri aktarıldı. Bu ilkeyi, herhangi bir site koleksiyonu içinde site veya liste düzeyinde birden çok içerik türüne uygulayabilirsiniz. Bunu iki klasörle yapma avantajları vardır: her içerik türüne ilkeyi yeniden tanımlamanız ve uygulamanız gerekli değildir ve tek bir yerde ilkede değişiklikler yaparak ilke değişikliklerini daha kolay yönetebilirsiniz.

1. İlkeyi uygulamak istediğiniz site koleksiyonunun giriş sayfasında, Site **Ayarlar'in**![ yerini alan Ayarlar Small Ayarlar dişlisi'Ayarlar](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\>.

   Grup bağlantılı SharePoint, Site İçeriği'ne Ayarlar Site İçeriği'ne **ve** ardından Site **İçeriği'ne Ayarlar**.

2. Site Koleksiyonu sayfasında Ayarlar **Koleksiyonu** \> Yönetimi **İçerik Türü İlkesi Şablonları'nın altında**.

3. İlkeler sayfasında, \> **ilkeye** \> **yönelik** XML dosyasını bulmak için İçeri Aktar Gözat'ı seçin.

4. İlkenin Aç olarak kaydedil olduğu XML dosyasını \> **seçin**.

5. İlkeyi site koleksiyonuna eklemek için \> **Site** Koleksiyonu İlkesini İçeri Aktar sayfasında.

Alınan ilkeniz artık site veya liste düzeyindeki bir veya birçok içerik türüne uygulanabilir.

Bilgi yönetimi ilkeleri, kuruluşlarının içeriği ne kadar süre boyunca tutması, içerikle insanların neler yaptığını denetlemesi ve belgelere barkod veya etiket eklemesi gibi birçok denetime olanak sağlar. Bir ilke yasal ve resmi düzenlemelere veya şirket içi iş süreçlerine uyumluluğun zorunlu kılınmalarına yardımcı olabilir. Yönetici olarak, belgeleri izleme ve belgelerin ne kadar süreyle korunacaklarını denetlemeyi altına alan bir ilke kurabilirsiniz.

Bilgi yönetimi ilkesi oluşturmak için, site hiyerarşisinde en geniş konumdan en dar konuma kadar üç farklı konumda yer alan bir ilke oluşturabilirsiniz:

- Site koleksiyonu içinde birden çok içerik türü kullanmak üzere bir ilke oluşturun.
- Site içerik türü için ilke oluşturma.
- Liste veya kitaplık için ilke oluşturma.

Daha fazla bilgi için bkz [. Bilgi yönetimi ilkelerine giriş](intro-to-info-mgmt-policies.md).
