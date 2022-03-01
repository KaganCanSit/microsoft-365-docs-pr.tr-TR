---
title: Bir olay oluştuğunda bekletmeyi başlatma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: Normalde, kayıt yönetimi çözümünün bir parçası olarak, tanım olası bir olayla bekletme dönemini başlatmak için bir bekletme etiketi yapılandırabilirsiniz.
ms.openlocfilehash: c4195f7e5a859cf5a1078566728be5b8567cf5b9
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016528"
---
# <a name="start-retention-when-an-event-occurs"></a>Bir olay oluştuğunda bekletmeyi başlatma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

İçeriği alıkoyma süreniz genellikle içeriğin yaşına göre olur. Örneğin, oluşturulduktan sonra yedi yıl süreyle belgeleri koruyabilirsiniz ve sonra bunları silebilirsiniz. Ancak bekletme etiketlerini [yapılandırıldığında](retention.md#retention-labels), bekletme sürelerini belirli bir olay türünün ne zaman oluştuğuna da temellandırabilirsiniz. Olay bekletme döneminin başlangıcını tetikler ve bu tür bir olay için bekletme etiketi uygulanmış tüm içerik etiketin bekletme eylemlerini zorlar.
  
Olay tabanlı bekletme kullanımına örnekler:
  
- **Kuruluşdan ayrılmakta olan çalışanlar** Bir çalışanın kuruluştan ayrıldığından bu süre boyunca çalışan kayıtlarının 10 yıl tutul olması gerektiğini varsayalım. 10 yıl kullandıktan sonra, bu çalışanın işe alım, performans ve sonlandırma ile ilgili tüm belgeleri atılması gerekir. 10 yıllık bekletme dönemini tetikleyen olay, kuruluştan ayrılmakta olan çalışandır. 
    
- **Sözleşmenin sona erme tarihi** Sözleşmelerle ilgili tüm kayıtların, sözleşmenin sona erer süresi dolduğundan itibaren beş yıl boyunca tutulacaklarını varsayalım. Beş yıllık bekletme süresini tetikleyen olay, sözleşmenin sona erme tarihidir. 
    
- **Ürün yaşam süresi** Kuruluşta, teknik belirtimler gibi içeriğin son üretim tarihiyle ilgili bekletme gereksinimleri olabilir. Bu durumda, bekletme dönemini tetikleyen son üretim tarihidir. 
    
Olay tabanlı bekletme genellikle kayıt yönetimi işleminin bir parçası olarak kullanılır. Bu, şu anlama gelir:
  
- Olaylara dayalı bekletme etiketleri de çoğunlukla öğeleri kayıt olarak, kayıt yönetimi çözümünün bir parçası olarak işaretlemektedir. Daha fazla bilgi için bkz[. Kayıt yönetimi hakkında bilgi.](records-management.md)

- Kayıt olarak bildirmiş ancak olay tetikleyicisi henüz olmayan belge, bir olay o belgenin bekletme dönemini tetikleyene kadar süresiz olarak korunur (kayıtlar kalıcı olarak silinemez).
    
- Olaylara dayalı bekletme etiketleri genellikle bekletme döneminin sonunda bir imha gözden geçirmesini tetikler; böylelikle kayıt yöneticisi içeriği el ile gözden geçirebilir ve atılabilir. Daha fazla bilgi için bkz [. İçeriğin konumlandırması](disposition.md).
    

Olayı temel alan bir bekletme etiketi, bekletme etiketi veya herhangi bir bekletme etiketiyle Microsoft 365. Daha fazla bilgi için bkz [. Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinebilirsiniz](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Olay türleri, etiketler, olaylar ve varlık kimlikleri arasındaki ilişkiyi anlama

Olay tabanlı bekletmeyi başarıyla kullanmak için, diyagramlarda ve aşağıdaki açıklamada gösterildiği gibi olay türleri, bekletme etiketleri, olaylar ve varlık kimlikleri arasındaki ilişkiyi anlamak önemlidir: 
  
![Diyagram 1 / 2: Olay türü, etiketler, olaylar ve varlık kimlikleri.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![2'den Diyagram 2: Olay türü, etiketler, olaylar ve varlık kimlikleri.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Farklı içerik türleri için bekletme etiketleri oluşturabilir ve bunları bir etkinlik türüyle ilişkilendirmeniz gerekir. Örneğin, farklı türdeki ürün dosyası ve kayıtlarına yönelik bekletme etiketleri Ürün Yaşam Süresi adlı olay türüyle ilişkilendirilır, çünkü ürünün kullanım süresi sonuna ulaştığı 10 yıl boyunca bu kayıtların korunması gerekir.
    
2. Kullanıcılar (genellikle kayıt yöneticileri), bu bekletme etiketlerini içeriğe uygulatır ve (SharePoint ve Kaynak Belge'deki belgeler OneDrive) her öğe için bir varlık kimliği girerler. Bu örnekte, varlık kimliği kuruluş tarafından kullanılan ürün adı veya kodudur. Ardından, her ürünün kayıtlarına bir bekletme etiketi atanır ve her kaydın bir varlık kimliği içeren bir özelliği vardır. Diyagram, **kuruluşta tüm** ürün kayıtlarının tüm içeriğini temsil eder ve her öğe kaydı bulunan ürünün varlık kimliğini okur. 
    
3. Ürün Yaşam Süresi, etkinlik t type'tir; Hayat sonuna ulaşan belirli bir ürün bir etkinliktir. Bu olay türünde bir olay oluştuğunda (bu durumda, bir ürün yaşam sonuna ulaştığında) şunları belirten bir olay oluştur olur:
    
   - Varlık kimliği (kimlik SharePoint belgeleri OneDrive için)
    
   - Anahtar sözcükler (belirli Exchange için). Bu örnekte, kuruluş ürün kayıtlarını içeren iletilerde ürün kodu kullandığı için Exchange öğelerinin anahtar sözcüğü, SharePoint ve OneDrive öğelerinin varlık kimliğiyle işlevsel olarak aynıdır.
    
   - Olayın olduğu tarih. Bu tarih, bekletme döneminin başlangıcı olarak kullanılır. Bu tarih geçerli, geçmiş veya gelecekteki bir tarih olabilir.

4. Bir olay oluşturduktan sonra, bu olay tarihi o olay türünde bir bekletme etiketi olan ve belirtilen varlık kimliği veya anahtar sözcüğünü içeren tüm içerikle eşitlenir. Herhangi bir bekletme etiketi gibi, bu eşitleme de yedi gün kadar zaman alabiliyor. Önceki diyagramda, kırmızı daire içine alan tüm öğelerin bekletme süresi bu olay tarafından tetiklenir. Başka bir deyişle, bu ürün ömür sonuna ulaştığında, bu olay o ürünün kayıtları için bekletme dönemini tetikler.

Bir olay için varlık kimliği veya anahtar sözcükler belirtmezseniz **, bekletme** etiketi bu olay türünde olan tüm içeriğin bekletme süresi olay tarafından tetiklenir. Bu, önceki diyagramda tüm içeriğin korunarak başlatıla başlayacağı anlamına gelir. Sizin için bu sizin için önemli bir durum değil.

Son olarak, her bekletme etiketinin kendi bekletme ayarları olduğunu unutmayın. Bu örnekte, hepsi 10 yıl belirtir, ancak bir olayın her etiketin bekletme süresi farklı olan bekletme etiketlerini tetiklemesi de mümkündür.
  
## <a name="how-to-set-up-event-driven-retention"></a>Olay tarafından yönlendirilen bekletme nasıl ayarlanır

Olay odaklı bekletme için üst düzey iş akışı:
  
![Olay odaklı bekletmeyi ayarlamaya uygun iş akışının diyagramı.](../media/event-based-retention-process.png)
  
> [!TIP]
> SharePoint'ta yönetilen özelliklerin kullanımı ve olay odaklı bekletmeyi uygulama hakkında ayrıntılı bir senaryo için bkz. [SharePoint'de](auto-apply-retention-labels-scenario.md) depolanan belgelerin yaşam döngüsünü yönetmek için bekletme etiketlerini kullanma.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>1. Adım: Bekletme süresi bir olayı temel alan bir etiket oluşturma

Bekletme etiketinizi oluşturmak ve yapılandırmak için, Kayıt yönetimi için bekletme [](file-plan-manager.md#create-retention-labels) etiketleri oluşturma veya Bilgi yönetimi için bekletme [etiketleri oluşturma yönergelerine bakın](create-retention-labels-information-governance.md). Ancak, olay tabanlı bekletmeye özel olarak, bekletme  etiketini ekleyebilirsiniz bekletme etiketini ekleyebilirsiniz sayfasında Bekletme dönemini temel alarak başlat'tan **sonra, açılan** listeden varsayılan olay türlerinden birini seçin veya Yeni olay türü oluştur'a seçerek kendi olay türlerinizi **oluşturun:**

![Bekletme etiketi için yeni bir olay türü oluşturun.](../media/SPRetention6.png)

Olay türü, yalnızca bir bekletme etiketiyle ilişkilendirmek istediğiniz olayın genel açıklamasıdır.

Varsayılan olay türlerinin, daha kolay tanımlanması için açılan listede adının yanında (olay türü **)** vardır. Ayrıca,  >  Kayıt **yönetimiEvents** sekmesinde Olay türlerini yönet'> de olay türü görebilir ve **oluşturabilirsiniz**.

Olay tabanlı bekletme için aşağıdaki bekletme ayarları gerekir:
  
- İçeriği koruma.
    
- İçeriği otomatik olarak silin veya bekletme döneminin sonunda bir disposition gözden geçirmeyi tetikler.
  
Olay tabanlı bekletme normalde kayıt olarak bildirilen içerik için kullanılır, bu nedenle şimdi içeriği kayıt olarak işaret eden seçeneği de seçmeniz gerekip gerekip gerek olmadığını kontrol etmek için [uygun bir zamandır](records-management.md#records).

Yeni bir olay türü oluşturmak yerine var olan bir olay türü kullanıyorsanız, 3. adıma geçin.

> [!NOTE]
> Bir olay türü seçtikten ve bekletme etiketini kaydeddikten sonra, olay türü değiştirilemez.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>2. Adım: Etiketiniz için yeni bir olay türü oluşturma

Bekletme ayarları için, Yeni olay türü **oluştur'i seçtiysanız**, olay türünüz için bir ad ve açıklama girin. Sonra Sonraki **, Gönder** **ve Bitti'yi** **seçin**.

Bekletme ayarlarını **tanımla sayfasına geri** dönerek, Bekletme dönemini temel alarak başlatma **için, oluşturduğunuz** olay türünü seçmek üzere açılan listeyi kullanın.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>3. Adım: Olay tabanlı bekletme etiketlerini yayımlama veya otomatik olarak uygulama

Aynı herhangi bir bekletme etiketi gibi, el ile veya otomatik olarak içeriğe uygulanması için olay tabanlı bir etiketi yayımlamanız veya otomatik olarak uygulamanız gerekir:
- [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>4. Adım: Varlık kimliği girme

İçeriklere olay tabanlı etiket uygulandıktan sonra, her öğe için bir varlık kimliği girebilirsiniz. Örneğin, organizasyonunız şunları kullanabilir:
  
- Yalnızca belirli bir ürünün içeriğini korumak için kullanabileceğiniz ürün kodları.
    
- Project belirli bir projenin içeriğini korumak için kullanabileceğiniz tüm kodları içerir.
    
- Yalnızca belirli bir kişinin içeriğini korumak için kullanabileceğiniz çalışan kimlikleri.
    
Varlık Kimliği, yalnızca hem kendi dosyalarında hem de başka bir SharePoint OneDrive. Organizasyonunız içeriği sınıflandırmak için başka belge özellikleri ve kimlikleri zaten kullanıyor olabilir. Bu durumda, bir olay sanız bu özellikleri ve değerleri de kullanabilirsiniz; aşağıdaki 6. adıma bakın. Önemli olan, belge özelliklerinde bir *özellik:değer* bileşimi kullanarak bu öğeyi olay türüyle ilişkilendirmenizdir.
  
![Bir Varlık Kimliği girmek için metin kutusu.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>5. Adım: Olay oluşturma

Bu olay türünün belirli bir örneği olduğunda, örneğin bir ürün yaşam sonuna ulaştığında,  >  olay oluşturmak için Microsoft 365 uyumluluk merkezi'te Kayıt yönetimiEvents sayfasına gidin ve **+ Oluştur'a** tıklayın. Olayı burada oluşturarak tetiklersiniz.

![Olay tabanlı bekletme etiketleri için bekletme başlangıcını tetikleyen bir olay oluşturun.](../media/create-event-records-management.png)

Kiracı başına en fazla bir milyon olay destek sağlar.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>6. Adım: 2. adımda etiket tarafından kullanılan etkinlik türünü seçme

Olayı  oluşturduktan sonra, 2. adımda bekletme etiketi ayarlarında belirtilen olay türünü seçin. Örneğin, etiket ayarları için etkinlik **türünüz** olarak Ürün Yaşam Süresi'ne seçtiysiniz,  etkinliği 7 2013'e 30 gün önce 7 kez 365 gün olarak ayarlarsanız, etkinliği 36/2013'e ayarlarsanız, ürün yaşam süresi'ne tıklayın. Yalnızca bu olay türüne bekletme etiketleri uygulanmış olan içerikte bekletme süresi tetiklenir.

![Olay ayarlarında bir olay türü seçme seçeneği.](../media/choose-event-type-records-management.png)

Alternatif olarak, farklı olay türlerine sahip birden çok bekletme etiketi için olay oluşturmanız gerekirse Varolan Etiketleri Seç **seçeneğini** belirleyin. Ardından, bu etkinlikle ilişkilendirmek istediğiniz olay türleri için yapılandırılmış etiketleri seçin.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>7. Adım: Kimlik bilgileri, kimlik Exchange kimlik bilgileri ve kimlik SharePoint sorgusunu OneDrive

Şimdi, içeriğin kapsamını daraltabilirsiniz. Daha Exchange için, bunu anahtar sözcükleri veya sorguyu belirterek yapabilirsiniz. Daha SharePoint ve OneDrive için bunu varlık kimliklerini belirterek yapar.

Daha Exchange için anahtar sözcükler veya Anahtar Sözcük Sorgu Dili (KQL) kullanan bir sorgu kullanın. Sorgu söz dizimi hakkında daha fazla bilgi için bkz. [Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). Bu özellik için kullanabileceğiniz aranabilir özellikler hakkında daha fazla bilgi Exchange bkz. Anahtar sözcük sorguları ve [İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).

Varlık kimlikleri için, bekletme yalnızca belirtilen özellik:değer çifti ile *içerik üzerinde zorunlu* kılınacak. Örneğin, Varlık Kimliği özelliğini kullanıyorsanız, aşağıdaki `ComplianceAssetID:<value>` resimde gösterilen varlık kimlikleri kutusuna girin.

Bir varlık kimliği girilirse, o olay türünde etiketleri olan tüm içeriklere aynı bekletme tarihi uygulanır.

Bu olay türüyle ilgili belgelere, sizin başka özellikler ve kimlikler de uygulanmış olabilir. Örneğin, belirli bir ürünün kayıtlarını algılamanız gerekirse, Kimlik özel özellik ÜrünKimlik değeriyle "XYZ" değerinin bir bileşimi olabilir. Bu durumda, aşağıdaki resimde gösterilen `ProductID:XYZ` varlık kimlikleri kutusuna girebilirsiniz.

Son olarak, olayın olduğu tarihi seçin; bu tarih, bekletme döneminin başlangıcı olarak kullanılır. Bir olay oluşturduktan sonra, bu olay tarihi o olay türü, varlık kimliği, anahtar sözcükler veya sorguların bekletme etiketiyle tüm içerikle eşitlenir. Herhangi bir bekletme etiketinde olduğu gibi, bu eşitleme de yedi gün kadar zaman alabiliyor.
  
![Olay ayarları sayfasına gidin.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Olay oluşturduktan sonra, önceden etiketlenmiş ve dizinelenmiş içerik için bekletme ayarları etkin olur. Bekletme etiketi, etkinlik oluşturulduktan sonra yeni içeriğe eklenirse, aynı ayrıntılara sahip yeni bir olay oluşturmanız gerekir.

Bir olayın silinmesi, zaten etiketlenmiş içerik için şu anda etkin olan bekletme ayarlarını iptal etmez. Şu anda, olayları tetikledikten sonra iptal edebilirsiniz.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Belirli bir etiket veya varlık kimliğine sahip tüm içeriği bulmak için İçerik Arama'ya kullanma

Bekletme etiketleri içeriğe atandıktan sonra, belirli bir bekletme etiketiyle sınıflandırılmış veya belirli bir varlık kimliği içeren tüm içeriği bulmak için içerik arama kullanabilirsiniz:
  
- Belirli bir bekletme etiketine sahip tüm içeriği bulmak için, Bekletme  etiketi koşullarını seçin, etiket adının tam etiket adını veya bir bölümünü girin ve joker karakter kullanın. 
    
- Belirli bir varlık kimliğine sahip tüm içeriği bulmak için, **bu biçimi kullanarak ComplianceAssetID** özelliğini ve bir değer girin `ComplianceAssetID:<value>`. 
    
Daha fazla bilgi için bkz [. Anahtar Sözcük sorguları ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>PowerShell kullanarak olayları otomatikleştirme

İş uygulamalarınız için olay tabanlı bekletmeyi otomatikleştirmek üzere bir PowerShell betiği kullanabilirsiniz. Olay tabanlı bekletme için powershell cmdlet'leri kullanılabilir:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>REST API kullanarak etkinlikleri otomatikleştirme

Bekletmenin başlamasını tetikleyen olayları otomatik olarak oluşturmak için REST API'sini kullanabilirsiniz.

REST API, hizmetin kaynakları için oluşturma/alma/güncelleştirme/silme erişimi sağlayan HTTP işlemi kümelerini (yöntemler) destekleyen bir hizmet uç noktasıdır. Daha fazla bilgi için bkz [. REST API isteğinin/yanıtlarının bileşenleri](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). REST API'Microsoft 365 kullanılarak, olaylar POST ve GET yöntemleri kullanılarak oluşturulabilir ve alınabilirsiniz.

REST API'yi kullanmak için iki seçenek vardır:

- **Microsoft Power Automate veya benzer bir uygulamayı kullanarak** olayın otomatik olarak yine olaylarını tetikler. Microsoft Power Automate başka sistemlere bağlanan birtor olduğu için özel bir çözüm yazmanız gerekmektedir. Daha fazla bilgi için bu web [Power Automate bakın](https://flow.microsoft.com/en-us/).

- **PowerShell veya HTTP istemcisiyle REST API'yi** çağırarak, özel bir çözümün parçası olan PowerShell (sürüm 6 veya daha sonraki bir sürüm) kullanarak olay oluşturabilirsiniz.

REST API'sini kullanmadan önce genel yönetici olarak, bekletme olay çağrısında kullanmak üzere URL'yi onaylayın. Bunu yapmak için REST API URL'sini kullanarak bir GET bekletme olayı çağrısı çalıştırın:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Yanıt kodunu kontrol edin. Bu 302 ise, yanıt üstbilgisinin Konum özelliğinden yeniden yönlendirilen URL'yi alır ve aşağıdaki yönergeler yerine bu URL'yi `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` kullanın.

Otomatik olarak oluşturulan olaylar, Kayıt yönetimiEvents içinde görüntü Microsoft 365 uyumluluk merkezi >  >  **onaylanır**.

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Olayı Power Automate için Microsoft Power Automate'i kullanma

REST API'sini kullanarak etkinlik Microsoft 365 oluşturun:

![Flow oluşturmak için E-postayı kullanma.](../media/automate-event-driven-retention-flow-1.png)

![REST API'sini çağrı yapmak için akış kullanma.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Olay oluşturma

REST API'sini çağrı yapmak için örnek kod:

- **Yöntem**: POST
- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Üst Bilgiler**: Key = Content-Type, Value = application/atom+xml
- **Gövde**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'?>
    
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'
    
    xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'
    
    xmlns='http://www.w3.org/2005/Atom'>
    
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />
    
    <updated>9/9/2017 10:50:00 PM</updated>
    
    <content type='application/xml'>
    
    <m:properties>
    
    <d:Name>Employee Termination </d:Name>
    
    <d:EventType>99e0ae64-a4b8-40bb-82ed-645895610f56</d:EventType>
    
    <d:SharePointAssetIdQuery>1234</d:SharePointAssetIdQuery>
    
    <d:EventDateTime>2018-12-01T00:00:00Z </d:EventDateTime>
    
    </m:properties>
    
    </content>
    
    </entry>
    ```

- **Kimlik Doğrulaması**: Temel
- **Kullanıcı** adı: "Complianceuser"
- **Parola**: "Compliancepassword"


##### <a name="available-parameters"></a>Kullanılabilir parametreler


|Parametreler|Açıklama|Notlar|
|--- |--- |--- |
|<d:Ad></d:Name>|Etkinlik için benzersiz bir ad girin|İzleyen boşluklar veya şu karakterleri içeremez: % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Olay türü adını (veya Guid) girin,|Örnek: "Çalışan sonlandırma". Olay türü bir bekletme etiketiyle ilişkili olmalı.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|"ComplianceAssetId:" + çalışan kimliğini girin|Örnek: "ComplianceAssetId:12345"|
|<:EventDateTime></d:EventDateTime>|Etkinlik Tarihi ve Saati|Biçim: yyyy-AA-ddTHH:dd:ssZ, Örnek: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Yanıt kodları

| Yanıt Kodu | Açıklama       |
| ----------------- | --------------------- |
| 302               | Yeniden yönlendirme              |
| 201               | Oluşturuldu               |
| 403               | Yetkilendirme Başarısız Oldu  |
| 401               | Kimlik Doğrulaması Başarısız |

##### <a name="get-events-based-on-a-time-range"></a>Etkinlikleri bir zaman aralığına göre elde edin

- **Yöntem**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Üst Bilgiler**: Key = Content-Type, Value = application/atom+xml

- **Kimlik Doğrulaması**: Temel

- **Kullanıcı** adı: "Complianceuser"

- **Parola**: "Compliancepassword"

###### <a name="response-codes"></a>Yanıt kodları

| Yanıt Kodu | Açıklama                   |
| ----------------- | --------------------------------- |
| 200               | Tamam, atom+ xml'de olayların listesi |
| 404               | Bulunamadı                         |
| 302               | Yeniden yönlendirme                          |
| 401               | Yetkilendirme Başarısız Oldu              |
| 403               | Kimlik Doğrulaması Başarısız             |

##### <a name="get-an-event-by-id"></a>Olayı kimliğine göre al

- **Yöntem**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Üst Bilgiler**: Key = Content-Type, Value = application/atom+xml

- **Kimlik Doğrulaması**: Temel

- **Kullanıcı** adı: "Complianceuser"

- **Parola**: "Compliancepassword"

###### <a name="response-codes"></a>Yanıt kodları

| Yanıt Kodu | Açıklama                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | Tamam, yanıt gövdesi atom+xml'de olayı içeriyor |
| 404               | Bulunamadı                                            |
| 302               | Yeniden yönlendirme                                             |
| 401               | Yetkilendirme Başarısız Oldu                                 |
| 403               | Kimlik Doğrulaması Başarısız                                |

##### <a name="get-an-event-by-name"></a>Olayı adına göre al

- **Yöntem**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Üst Bilgiler**: Key = Content-Type, Value = application/atom+xml

- **Kimlik Doğrulaması**: Temel

- **Kullanıcı** adı: "Complianceuser"

- **Parola**: "Compliancepassword"

###### <a name="response-codes"></a>Yanıt kodları

| Yanıt Kodu | Açıklama                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | Tamam, yanıt gövdesi atom+xml'de olayı içeriyor |
| 404               | Bulunamadı                                            |
| 302               | Yeniden yönlendirme                                             |
| 401               | Yetkilendirme Başarısız Oldu                                 |
| 403               | Kimlik Doğrulaması Başarısız                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Olayı oluşturmak için PowerShell veya herhangi bir HTTP istemcisini kullanma

PowerShell sürüm 6 veya daha sonraki bir sürümde olmalı.

PowerShell oturumunda aşağıdaki betiği çalıştırın:

```powershell
param([string]$baseUri)

$userName = "UserName"

$password = "Password"

$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)

$EventName="EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))"

Write-Host "Start to create an event with name: $EventName"

$body = "<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'

xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'

xmlns='http://www.w3.org/2005/Atom'>

<category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />

<updated>7/14/2017 2:03:36 PM</updated>

<content type='application/xml'>

<m:properties>

<d:Name>$EventName</d:Name>

<d:EventType>e823b782-9a07-4e30-8091-034fc01f9347</d:EventType>

<d:SharePointAssetIdQuery>'ComplianceAssetId:123'</d:SharePointAssetIdQuery>

</m:properties>

</content>

</entry>"

$event = $null

try

{

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri "$baseUri/ComplianceRetentionEvent" -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

catch

{

$response = $_.Exception.Response

if($response.StatusCode -eq "Redirect")

{

$url = $response.Headers.Location

Write-Host "redirected to $url"

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

}

$event | fl *
```
