---
title: Başka bir veritabanında depolanan belgelerin yaşam döngüsünü yönetmek için bekletme SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: SharePoint'ta belgelerin yaşam döngüsünü yönetmek için içeriği sınıflandırmak, etiketleri otomatik olarak uygulamak ve bekletme dönemini başlatmak için olay tabanlı bekletmeyi kullanmak üzere meta verileri kullanarak bekletme etiketlerini nasıl kullanabilirsiniz?
ms.openlocfilehash: 586f9074628ed3c4c272715378b1ba413ebdd3ec
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990017"
---
# <a name="use-retention-labels-to-manage-the-lifecycle-of-documents-stored-in-sharepoint"></a>Başka bir veritabanında depolanan belgelerin yaşam döngüsünü yönetmek için bekletme SharePoint

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bu makalede, otomatik olarak uygulanan bekletme etiketlerini ve olay tabanlı bekletmeyi kullanarak SharePoint belgelerin yaşam döngüsünü nasıl yönetebilirsiniz?

Otomatik uygulama işlevselliği, belge sınıflandırması SharePoint meta verilerini kullanır. Bu makaledeki örnek ürünle ilgili belgelere yöneliktir, ancak diğer senaryolarda da aynı kavramlar kullanılabilir. Örneğin, yağ ve yakıt sektörü içinde, yağ platformları, iyi günlükler veya üretim lisansları gibi fiziksel varlıklarla ilgili belgelerin yaşam döngüsünü yönetmek için onu kullanabilirsiniz. Finansal hizmetler sektöründe, banka hesabı, konut kredisi veya sigorta sözleşme belgelerini yönetebilirsiniz. Kamu sektöründe, inşaat izinlerini veya vergi formlarını yönetesiniz.

Bu makalede, bilgi mimarisine ve bekletme etiketlerinin tanımına bakabilirsiniz. Ardından, etiketleri otomatik olarak uygulayarak belgeleri sınıflandırın. Son olarak da bekletme dönemini başlatan olayları oluşturuz.

## <a name="information-architecture"></a>Bilgi mimarisi

Bizim senaryomuz, şirket tarafından SharePoint ürünlerle ilgili tüm belgeleri depolamak için Yeni Depolama alanı kullanan bir üretim şirketidir. Bu belgeler ürün belirtimlerini, sağlayıcılarla yapılan sözleşmeleri ve kullanıcı el kitaplarını içerir. Bu belgeler İçerik Yönetimi ilkeleri SharePoint Enterprise depolanıyorsa, bunları sınıflandırmak için kullanılan belge meta verileri tanımlanır. Her belgede aşağıdaki meta veri özellikleri vardır:

- **Belge Türü** (ürün belirtimi, sözleşme veya kullanıcı el kitabı gibi)

- **Ürün Adı**

- **Durum** (taslak veya son)

Bu meta veri, tüm belgeler için Üretim Belgesi *adlı temel* bir içerik türü oluşturur.

![Ürün belgeleri meta verileri tablosu.](../media/SPRetention1.png)

> [!NOTE]
> Belge **Türü ve** Durum **özellikleri** , bu senaryonun ilerleyen sayfalarında bekletme etiketlerini sınıflandırmak ve otomatik olarak uygulamak için bekletme ilkeleri tarafından kullanılır.

Farklı türde belgeleri temsil eden birkaç içerik türümiz olabilir, ancak şimdi ürün belgelerine odaklanın.

Bu senaryoda, Yönetilen Meta Veri hizmetini ve Terim Deposu'bulundurarak Belge Türü için bir terim kümesi  ve Ürün Adı için başka bir terim *kümesi oluşturacağız*. Her terim kümesi için her değer için bir terim oluşturuz. Büyük bir kuruluş için Terim Deposu'SharePoint benzer:

![Terim Deposu'daki ürün belgeleri için örnek terim kümesi.](../media/SPRetention2.png)

*İçerik Türü* , İçerik Türü Merkezi kullanılarak oluşturulabilir [ve yayımlanamaz](https://support.office.com/article/manage-content-type-publishing-06f39ac0-5576-4b68-abbc-82b68334889b). Ayrıca, [PnP](/sharepoint/dev/solution-guidance/pnp-provisioning-framework) sağlama çerçevesi veya site tasarımı JSON şeması gibi site sağlama araçlarını kullanarak da içerik türü [oluşturabilir ve yayım edebilirsiniz](/sharepoint/dev/declarative-customization/site-design-json-schema#define-a-new-content-type).

Her ürünün, SharePoint türleri etkinleştirilmiş tek bir belge kitaplığı içeren ayrılmış bir site vardır. Tüm belgeler bu belge kitaplığında depolanır.

[![Ürün belgeleri için belge kitaplığı.](../media/SPRetention3.png) ](../media/SPRetention3.png#lightbox)

> [!NOTE]
> Bu senaryoda üretim şirketi ürün başına bir SharePoint sitesine sahip olmak yerine, kalıcı sohbet aracılığıyla ekibin üyeleri arasında işbirliğini desteklemek için ürün başına microsoft ekibi kullanabilir ve belge yönetimi için Teams'de Dosyalar sekmesini kullanabilir. Bu makalede yalnızca belgelere odaklanan bir site, yani yalnızca bir site kullanıyoruz.

Dönen Widget ürünü için belge kitaplığının görünümü şöyledir:

[![Dönen Pencere Öğesi belge kitaplığı.](../media/SPRetention4.png) ](../media/SPRetention4.png#lightbox)

Artık belge yönetimi için temel bilgi mimarisine sahip olduğunu göre, meta verileri kullanan belgeler ve bu belgeleri nasıl sınıflandıracağız?

## <a name="retention-and-disposition"></a>Bekletme ve yokuzma

Üretim şirketinin uyumluluk ve veri yönetimi ilkeleri, verilerin nasıl korunarak atılması gerektiğinine dikte ediyor. Ürün üretimi ve belirli bir ek dönem boyunca ürünle ilgili belgeler tutulmalıdır. Ek süre ürün belirtimleri, sözleşmeler ve kullanıcı el kitabına göre farklılık gösterir. Aşağıdaki tablo, bekletme ve yok durumu gereksinimlerini gösterir:

|   Belge türü            |   Bekletme                            |   Disposition                                |
| -------------------------- | -------------------------------------- | -------------------------------------------- |
| Ürün belirtimleri      | Üretim duraklarını 5 yıl sonra  | Silme                                       |
| Ürün sözleşmeleri          | Üretim duraklarını 10 yıl sonra | Gözden Geçir                                       |
| Kullanıcı el kılavuzları                | Üretim duraklarını 5 yıl sonra  | Silme                                       |
| Diğer tüm belge türleri | Etkin olarak korumayın  | Belge 3 yıllıktan eski olduğunda silme <br /><br /> Son 3 yıl içinde değiştirilmemiş olan bir belge, 3 yıl önce kabul edilir. |
|||

Aşağıdaki bekletme Microsoft 365 uyumluluk merkezi oluşturmak için aşağıdaki adımları [kullanıruz](retention.md#retention-labels):

  - Ürün Belirtimi

  - Ürün Sözleşmesi

  - Kullanıcı El Kitabı

Bu makalede yalnızca Ürün Belirtimi bekletme etiketinin nasıl oluşturulacak ve otomatik olarak nasıl uygulanacakları açıklanmıştır. Tam senaryoyu uygulamak için, diğer iki belge türü için de bekletme etiketleri oluşturabilir ve otomatik olarak uygulayabilirsiniz.

### <a name="settings-for-the-product-specification-retention-label"></a>Ayarlar Belirtimi bekletme etiketi için veri etiketi

Ürün Belirtimi [bekletme etiketi](file-plan-manager.md) için dosya planı şöyledir:

- **Ad:** Ürün Belirtimi

- **Kullanıcılar için açıklama:** Üretim durakları 5 yıl boyunca korunur.

- **Yöneticiler için açıklama:** Üretim durakları, otomatik silme, olay tabanlı bekletme ve olay türü Ürün *Cessation olmak 5 yıl boyunca korunur*.

- **Bekletme eylemi:** Koruma ve silme.

- **Bekletme süresi:** 5 yıl (1.825 gün).

- **Kayıt etiketi**: Bekletme etiketini öğeleri kayıt olarak işaretle olacak şekilde [yapılandırarak etiketli](records-management.md#records) belgeler bundan sonra kullanıcılar tarafından değiştirilemez veya silinemez.

- **Dosya planı tanımlayıcıları:** Senaryoyu basitleştirmek için, isteğe bağlı dosya tanımlayıcıları sağ verilmez.

Aşağıdaki ekran görüntüsünde, Ürün Belirtimi bekletme etiketini ilk oluşturma sayfasında Microsoft 365 uyumluluk merkezi. Bekletme etiketini *oluşturma sırasında Ürün Cessation* olay türünü oluşturabilirsiniz. Aşağıdaki bölümde yer alan yordama bakın.

![Ürün Belirtimi etiketi için bekletme ayarları.](../media/SPRetention5.png)

> [!NOTE]
> Belge silme işleminin 5 yıllık bekleme süresini önlemek için, test ortamında bu senaryoyu yeniden ediyorsanız bekletme süresini ***1*** gün olarak ayarlayın.

### <a name="create-an-event-type-when-you-create-a-retention-label"></a>Bekletme etiketi 2010'da bir olay türü oluşturma

1. Bekletme etiketi **oluştur sihirbazının** Bekletme ayarlarını tanımla sayfasında, Bekletme dönemini temel alan başlatma'nın **ardından Yeni olay** **türü oluştur'a tıklayın**:

    ![Ürün Belirtimi etiketi iletişim kutusu için yeni bir olay türü oluşturun.](../media/SPRetention6.png)

3. Etkinlik **türlerinizi yazın sayfasında** Ürün **Cessation girin ve isteğe** bağlı olarak bir açıklama girin. Sonra Sonraki **, Gönder** **ve Bitti'yi** **seçin**.

4. Bekletme ayarlarını **tanımla sayfasına geri** dönüp Bekletme dönemini temel alan başlatma **için, açılan** kutuyu kullanarak oluşturduğunuz Ürün **Cessation** olay türünü seçin.

    Ürün Belirtimi bekletme etiketi için ayarlar şöyle olur:

   ![Ayarlar Belirtimi etiketi için bir başlık.](../media/SPRetention7.png)

6. Etiket **oluştur'a** tıklayın ve etiketi yayımlama seçeneklerini gördüğünüzde bir sonraki sayfada etiketi otomatik olarak uygulama veya yalnızca etiketi kaydetme: Yalnızca şimdilik kaydet'i ve sonra Bitti'yi **seçin**.

    > [!TIP]
    > Daha ayrıntılı adımlar için bkz [. Bekletme süresi bir olayı temel alan bir etiket oluşturma](event-driven-retention.md#step-1-create-a-label-whose-retention-period-is-based-on-an-event).

Şimdi de bekletme etiketini ürün belirtimi içeriğine otomatik olarak nasıl uygulayacaklarına bakalım.

## <a name="auto-apply-retention-labels-to-documents"></a>Belgelere bekletme etiketlerini otomatik olarak uygulama

Oluşturduğumız bekletme etiketlerini otomatik olarak uygulamak [için Anahtar Sözcük](apply-retention-labels-automatically.md) Sorgu Dili'ne (KQL) kullan kullan aynı olacak. KQL, arama sorguları oluşturmak için kullanılan dildir. KQL'de, anahtar sözcükleri veya yönetilen özellikleri kullanarak arama yapabilirsiniz. Daha fazla bilgi için bkz [. Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Temel olarak, "son Microsoft 365 Durumu ve Belge Türü Ürün Belirtimi olan  tüm belgelere Ürün Belirtimi bekletme etiketini uygulamamız  **gerekir**." Durum ve **Belge** **Türü'nin,** Bilgi mimarisi bölümündeki Ürün Belgeleri içerik türü için tanımlanmamış site [sütunları olduğunu anımsatabilirsiniz](#information-architecture) . Bunu yapmak için, arama şemasını yapılandırmamız gerekir.

İçerik SharePoint olduğunda, her site sütunu için otomatik olarak gezinilen özellikler üretir. Bu senaryo için, Belge Türü ve **Durum özellikleriyle** **ilgileniyoruz** . Kitaplıkta doğru içerik türüne sahip belgelere ve gezinilen özellikleri oluşturmak için site sütunlarının arama için doldurulması gerekiyor.

SharePoint merkezinde Arama yapılandırmasını açın ve gezinilen özellikleri görüntülemek ve yapılandırmak için Arama Şemasını  Yönet'i seçin.

![Arama şemasında gezinilen özellikler.](../media/SPRetention8.png)

_ **Gezinilen özellikler*** kutusuna **status* _ yazın ve yeşil oku seçeriz, aşağıdakine benzer bir sonuçla görmemiz gerekir:

![Gezinilen ows_Status özelliktir.](../media/SPRetention9.png)

**owsStatus\_\_** özelliği (çift alt çizgi), ilgimizi alan özelliktir. Üretim Belgesi içerik **türünün** Durum özelliğiyle eşler.

Şimdi, ***owsdoc\_ yazın*** ve yeşil oku seçerek aşağıdakine benzer bir şey görüyoruz:

![Gezinilen ows_Doc_Type özelliktir.](../media/SPRetention10.png)

**owsDocx0020Type\_\_\_** özelliği, ilgimizi alan ikinci özelliktir. Üretim Belgesi içerik **türünün Belge Türü** özelliğiyle eşler.

> [!TIP]
> Bu senaryoya ait gezinilen özelliğin adını tanımlamak için, üretim belgelerini içeren belge kitaplığına gidin. Sonra da kitaplık ayarlarına gidin. Sütunlar **için**, site sütun sayfasını açmak için sütunun **adını** (**örneğin, Durum** veya Belge Türü) seçin. Bu *sayfanın* URL'sinde Field parametresi alanın adını içerir. "Alan adı" ile ön ekli ows_, gezinilen özelliğin adıdır. Örneğin, URL `https://tenantname.sharepoint.com/sites/SpinningWidget/_layouts/15/FldEdit.aspx?List=%7BC38C2F45-3BD6-4C3B-AA3B-EF5DF6B3D172%7D&Field=_Status` *owsStatus\_\_ gezinilen özeline* karşılık gelir.

Bulmak istediğiniz gezinilen özellikler, yönetim merkezinin Arama Şemasını Yönet bölümünde SharePoint:

- Belgeler dizine henüz oluşturmamış olabilir. Belge kitaplığı **ayarlarıAdvanced** Kitaplığı ayarlarına gidip **kitaplığın yeniden** >  Ayarlar.

- Belge kitaplığı modern bir sitede yer alıyorsa, site yöneticisinin aynı SharePoint koleksiyonu yöneticisi olduğundan emin olun.

Gezinilen ve yönetilen özellikler hakkında daha fazla bilgi için bkz. [SharePoint Server'da yönetilen özellikler.](/sharepoint/technical-reference/automatically-created-managed-properties-in-sharepoint)

### <a name="map-crawled-properties-to-pre-defined-managed-properties"></a>Gezinilen özellikleri önceden tanımlanmış yönetilen özelliklerle eşleme

KQL, arama sorgularında gezinilen özellikleri kullanmaz. Yönetilen özelliği kullanmaktadır. Normal bir arama senaryosunda, bir yönetilen özellik oluşturduk ve bu özelliği ihtiyacımız olan gezinilen özellik ile eşleriz. Bununla birlikte, bekletme etiketlerini otomatik uygularken, özel yönetilen özellikler değil, yalnızca KQL'de önceden tanımlanmış yönetilen özellikler belirtebilirsiniz. Kullanabileceğiniz *RefinableString00* - *RefinableString199* dizesi için sistemde önceden tanımlanmış bir dizi yönetilen özellik vardır. Tam liste için varsayılan [kullanılmamış yönetilen özellikler'e bakın](/sharepoint/manage-search-schema#default-unused-managed-properties). Bu varsayılan yönetilen özellikler genellikle arama iyileştiricileri tanımlamak için kullanılır.

KQL sorgusunun ürün belgesi içeriğine otomatik olarak doğru bekletme etiketini uygulaması için, **gezinilen özellikleri owsDocx0020Type\_\_\_* ve *owsStatus\_\_** ile iki iyileştirilebilir yönetilen özellikle eşleyiz. Bu senaryoya uygun test ortamımızda **RefinableString00** ve **RefinableString01** kullanılamaz. Bunu, genel yönetim merkezinde **Arama Şemasını** **Yönetme'de** Yönetilen SharePoint bakarak belirledik.

[![Arama şemasında yönetilen özellikler.](../media/SPRetention12.png) ](../media/SPRetention12.png#lightbox)

Önceki ekran **görüntüsünde Eşlenen Gezinilen Özellikler** sütununu boş olduğunu görebilirsiniz.

**owsDocx0020Type\_\_\_** gezinilen özelliğini eşlemek için şu adımları izleyin:

1. Yönetilen özellik **filtresi** kutusuna **_RefinableString00 yazın_** ve yeşil oku seçin.

2. Sonuç listesinde **RefinableString00** bağlantısını seçin ve ardından Gezinilen özelliklere **eşlemeler bölümüne kadar aşağı kaydırın** .

3. Eşleme **Ekle'yi** seçin ve ardından Gezinilen özellik seçimi penceresindeki _Search arama kutusuna **_owsDocx0020Type\_\_\__*_*** **yazın.** **Bul'a seçin**.

4. Sonuç listesinde **owsDocx0020Type\_\_\_ öğesini seçin ve** sonra da Tamam'ı **seçin**.

   Eşlenen **Gezinilen Özellikler bölümünde** , şu ekran görüntüsüne benzer bir şey görüyor gerekir:

   [![Eşlenen gezinilen özellikler bölümünde Eşleme ekle'yi seçin.](../media/SPRetention13.png) ](../media/SPRetention13.png#lightbox)


5. Sayfayı en altına kadar kaydırın ve eşlemeyi **kaydetmek için** Tamam'ı seçin.

**RefinableString01 ve** **owsStatus'u\_\_ eşlemek için bu adımları yinelayın**.

Şimdi, iki gezinilen özellikle eşlenmiş iki yönetilen özelliğin olması gerekir:

[![Gezinilen özelliklerle eşlenmiş olarak gösterilen yönetilen özellikler.](../media/SPRetention14.png) ](../media/SPRetention14.png#lightbox)

Kurumsal bir arama çalıştırarak kurulumlarımızın doğru olduğunu doğrularız. Tarayıcıda https://*\<your_tenant>.sharepoint.com/search*. Arama kutusuna ***RefinableString00:"Ürün** Belirtimi"_ yazın ve Enter tuşuna basın. Bu arama, _Ürün Belirtimi* olan *ve Belge Türü değeri olan* tüm **_belgeleri geri dönecektir_**.

Şimdi arama kutusuna **RefinableString00:"Ürün Belirtimi" AND RefinableString01:Final yazın ve** Enter tuşuna basın. Bu, Ürün Belirtimi Doc **_Type_ _ ve _Status of Final *olan tüm* belgeleri** **_geri dönecektir_**.

### <a name="create-auto-apply-label-policies"></a>Etiket ilkelerini otomatik uygulama oluşturma

Artık KQL sorgusunun çalıştığını doğruladıktan sonra, uygun belgelere Ürün Belirtimi bekletme etiketini otomatik olarak uygulamak için KQL sorgusu kullanan bir otomatik uygulama etiket ilkesi oluştursun.

1. Kayıt <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> Records **managementLabel** >  **policiesAuto-apply** >  a label (Etiket uygulamak için) gidin.

   [![Etiketler sayfasında "Otomatik olarak etiket uygula" öğesini seçin](../media/SPRetention16.png) ](../media/SPRetention16.png#lightbox)

2. Otomatik etiket ilkesi oluştur sihirbazının Otomatik etiketleme ilkenizi adla  sayfasında, Otomatik Olarak Uygula Ürün Belirtimi etiketi gibi bir ad ve isteğe bağlı bir açıklama girin. Sonra Da **Sonraki'yi seçin**.

3. Bu **etiketi uygulamak istediğiniz** içerik türünü seçin sayfasında Belirli sözcükleri veya tümcecikleri veya özellikleri içeren içeriğe etiket uygula'ya tıklayın ve sonra da Sonraki'yi **seçin**.

   [![Belirli sözcükleri veya tümcecikleri veya özellikleri içeren içeriğe etiket uygula'ya tıklayın.](../media/SPRetention17.png) ](../media/SPRetention17.png#lightbox)

   Bu seçenek, önceki bölümde test edilen KQL arama sorgusunu bize de sağlar. Sorgu, Son durumuna sahip tüm Ürün Belirtimi belgelerini *döndürür*. Aynı sorguyu otomatik uygulama etiketi ilkesinde de kullanır kullanıruz; Ürün Belirtimi bekletme etiketi, bu etiketle eşleşmeye neden olan tüm belgelere otomatik olarak uygulanır.

4. Bu **sorguyla** eşleşen içeriğe etiket uygula sayfasında **RefinableString00:"Ürün Belirtimi" AND RefinableString01:Final** yazın ve ardından Sonraki'yi **seçin**.

   ![Sorguyu Anahtar sözcük sorgusu düzenleyicisi kutusunda belirtin.](../media/SPRetention19.png)

5. **İlkenin uygulanacak konumları** seçin sayfasında, ilkeyi uygulamak istediğiniz içerik konumlarını seçin. Bu senaryoda, ilkeyi yalnızca bu konumlara SharePoint, çünkü tüm üretim belgeleri SharePoint depolanıyor. E-posta, hesap **Exchange durumunu** **OneDrive Grupları** Kapalı **Microsoft 365 geçiş****.** Sonraki seçeneğini seçmeden önce SharePoint sitelerinin durumunun **On** olarak ayar olduğundan emin **olun**:

    ![Etiketleri otomatik olarak uygulamak için belirli siteleri seçin.](../media/SPRetentionSPlocations.png)

   > [!TIP]
   > İlkeyi tüm sitelere uygulamak SharePoint, **Site** seç'i seçebilir ve belirli site sitelerinin URL'lerini SharePoint ebilirsiniz.

6. Otomatik **uygulanacak etiket seçin sayfasında Etiket ekle'yi** **seçin**.

7. Bekletme etiketleri listesinden Ürün **Belirtimi'ne tıklayın**. Ardından Ekle ve **Sonraki'yi** **seçin**.

8. Ayarlarınızı gözden geçirme:

    ![Ayarlar otomatik olarak uygulamak için tıklatın.](../media/SPRetention18.png)

9. Otomatik **uygulama** etiket ilkesi oluşturmak için Gönder'i seçin.

   > [!NOTE]
   > Ürün Belirtimi etiketinin KQL arama sorgusuyla eşleşmesi için tüm belgelere otomatik olarak uygulama 7 gün kadar sürer.

### <a name="verify-that-the-retention-label-was-automatically-applied"></a>Bekletme etiketinin otomatik olarak uygulandığını doğrulama

7 gün sonra, oluşturduğumız [](data-classification-activity-explorer.md) otomatik uygula etiket politikasının bekletme etiketlerini ürün belgelerine otomatik olarak uygulay yaptığını doğrulamak için uyumluluk merkezinde etkinlik gezginini kullanın.

Ayrıca, Belge Kitaplığı'nda belgelerin özelliklerine de bakın. Bilgi panelinde, bekletme etiketinin seçilen belgeye uygulandığını görebilirler.

[![Belge Kitaplığı'nda belge özelliklerine bakarak etiketin uygulandığını doğrulayın.](../media/SPRetention21.png) ](../media/SPRetention21.png#lightbox)

Bekletme etiketleri belgelere otomatik olarak uygulandığından, bekletme etiketi belgeleri kayıt olarak bildirecek şekilde yapılandırıldığından bu belgeler silinmeye karşı *korunur*. Bu koruma örneği olarak, bu belgelerden birini silmeyi denemizde aşağıdaki hata iletisini alıruz:

[![Etiket belgelerin kayıt olduğunu bildirdikten sonra belgelerin siline olmadığını gösteren bir hata iletisi.](../media/SPRetention22.png) ](../media/SPRetention22.png#lightbox)

## <a name="generate-the-event-that-triggers-the-retention-period"></a>Bekletme dönemini tetikleyen olayı oluşturma

Artık bekletme etiketleri uygulandığına göre, belirli bir ürün için üretimin sona erer olduğunu belirten etkinliğe odaklanın. Bu olay, bekletme etiketlarında tanımlanan bekletme döneminin başlangıcını tetikler. Örneğin, ürün belirtimi belgeleri için 5 yıllık bekletme süresi "üretim sonu" olayı tetiklendiğinde başlar.

Kayıt Yönetimi Olayları'Microsoft 365 uyumluluk merkezi etkinlik etkinliklerini **el ile oluşturabilirsiniz** > . Olay türünü seçer, doğru varlık kimliklerini seçer ve olay için bir tarih girersiniz. Daha fazla bilgi için bkz [. Olay oluştuğunda bekletmeyi başlatma](event-driven-retention.md).

Ancak bu senaryo için, etkinliği dış üretim sisteminden otomatik olarak oluşturacaktır. Sistem, SharePoint üretimde olup olmadığını gösteren basit bir veri kaynağı listesidir. [Listeyle Power Automate](/power-automate/getting-started) bir veri akışı olayı tetikler. Gerçek bir senaryoda, İk veya CRM sistemi gibi etkinliği oluşturmak için çeşitli sistemleri kullanabilirsiniz. Power Automate Microsoft Exchange, SharePoint, Teams ve Dynamics 365 gibi Microsoft 365 iş yükleri için kullanıma hazır birçok etkileşim ve yapı taşının yanı sıra Twitter, Box, Salesforce ve İş Günleri gibi üçüncü taraf uygulamalarını içerir. Bu özellik, kimlikleri çeşitli sistemlerle Power Automate kolay bir şekilde tümleştirin. Daha fazla bilgi için bkz [. Olay tarafından yönlendirilen bekletmeyi otomatikleştirme](./event-driven-retention.md#automate-events-by-using-a-rest-api).

Aşağıdaki ekran görüntüsünde SharePoint tetikte kullanılacak olan tablo listesi görüntülenir:

[![Bekletme olaylarını tetikleyen liste.](../media/SPRetention23.png) ](../media/SPRetention23.png#lightbox)

Üretimde şu anda _In Production* sütunundaki ***Evet** _ tarafından belirtilen iki *ürün* vardır. Bu sütundaki değer bir ürün için **_Hayır_** olarak ayarlanmışsa, listeyle ilişkili akış olayı otomatik olarak üretir. Olay, ilgili ürün belgelerine otomatik olarak uygulanan bekletme etiketi için bekletme döneminin başlangıcını tetikler.

Bu senaryo için, olayı tetiklemek için aşağıdaki akışı kullanıruz:

[![Olayı tetikleyen akışı yapılandırma.](../media/SPRetention24.png) ](../media/SPRetention24.png#lightbox)

Bu akışı oluşturmak için, bir bağlayıcıdan SharePoint ve **Öğe oluşturulduğunda veya değiştirildiğinde tetikleyiciyi** seçin. Site adresini ve liste adını belirtin. Ardından, Üretimde liste sütunundaki değerin koşul kartında **_Hayır_* _ (veya bu değere eşit _false* olarak) durumuna dayalı bir koşul ekleyin. Ardından, yerleşik HTTP şablonunu temel alan bir eylem ekleyin. HTTP eylemlerini yapılandırmak için aşağıdaki bölümde yer alan değerleri kullanın. URI ve Gövde **özellikleriyle** ilgili **değerleri aşağıdaki** bölümden kopyalayıp şablona yapıştırabilirsiniz.

- **Yöntem**: POST
- **URI**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Üst Bilgiler**: Key = Content-Type, Value = application/atom+xml
- **Gövde**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'>
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices' xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata' xmlns='https://www.w3.org/2005/Atom'>
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent'>
    <updated>9/9/2017 10:50:00 PM</updated>
    <content type='application/xml'>
    <m:properties>
    <d:Name>Cessation Production @{triggerBody()?['Product_x0020_Name']?['Value']}</d:Name>
    <d:EventType>Product Cessation&lt;</d:EventType>
    <d:SharePointAssetIdQuery>ProductName:&quot;@{triggerBody()?['Product_x0020_Name']?['Value']}<d:SharePointAssetIdQuery>
    <d:EventDateTime>@{formatDateTime(utcNow(),'yyyy-MM-dd')}</d:EventDateTime>
    </m:properties>
    </content&gt>
    </entry>
    ```

Bu listede, bu senaryo için **yapılandırılması** gereken eylemin Gövde özelliğinde yer alan parametreler açıklandı:

- **Ad**: Bu parametre, dosyada oluşturulacak olayın adını Microsoft 365 uyumluluk merkezi. Bu senaryoda ad "Cessation Production xxx" olur; *burada xxx*, daha  önce oluşturduğumız **ProductName** yönetilen özelliğinin değeridir.
- **EventType**: Bu parametrenin değeri, oluşturulan olayın geçerli olduğu olay türüne karşılık gelen değerdir. Bu olay türü, bekletme etiketini oluşturulduğunda tanımlanmıştır. Bu senaryo için olay türü "Ürün Cessation"tır.
- **SharePointAssetIdQuery**: Bu parametre, olayın varlık kimliğini tanımlar. Olay tabanlı bekletme, belge için benzersiz bir tanımlayıcıya sahip olmalıdır. Varlık Kimliklerini, belirli bir olayın geçerli olduğu belgeleri tanımlamak veya bu senaryoda olduğu gibi, Meta Veri Sütunu Ürün **Adı'na kullanabiliriz**. Bunu yapmak için, KQL sorgusunda kullanılmaktadır ve yeni bir **ProductName** yönetilen özelliği oluşturmamız gerekir. (Alternatif olarak, yeni bir yönetilen özellik **oluşturmak yerine RefinableString00'i** kullanabiliriz). Ayrıca, bu yeni yönetilen özelliği de gezinilen **ows_Product_x0020_Name** eşlememiz gerekir. Bu yönetilen özelliğin ekran görüntüsü:

    [![Rentention yönetilen özelliği.](../media/SPRetention25.png) ](../media/SPRetention25.png#lightbox)

- **EventDateTime**: Bu parametre, olayın oluştuğu tarihi tanımlar. Geçerli tarih biçimini kullanma:<br/><br/>*formatDateTime(utcNow(),'yyyy-MM-dd'*)

### <a name="putting-it-all-together"></a>Hepsini bir araya

Artık bekletme etiketi oluşturulur, otomatik uygulanır; akış yapılandırılır ve oluşturulur. Ürünler listesinde Dönen Widget ürünü  için Üretimde sütunundaki değer **_Evet_*_ ile _*_No_ _arasında değiştirlendiğinde, olayı oluşturmak için akış *tetiklenir. Bu olayı uyumluluk merkezinde görmek için_* Records managementEvents sayfasına** >  **gidin**.

[![Akış tarafından tetiklenen olay, uyumluluk merkezinin Olaylar sayfasında görüntülenir.](../media/SPRetention28.png) ](../media/SPRetention28.png#lightbox)

Uçarak çıkış sayfasında ayrıntıları görüntülemek için etkinliği seçin. Olay oluşturulsa bile, olay durumunda herhangi bir sitenin veya SharePoint işlenmedi ifadesinin yer olmadığını fark edin.

![Olay ayrıntıları.](../media/SPRetention29.png)

Ancak bir gecikmeden sonra, olay durumu SharePoint sitesi ve SharePoint işlenmiş olduğunu gösterir.

![Olay ayrıntıları belgelerin işlenmiş olduğunu gösterir.](../media/SPRetention31.png)

Bu, Dönen Widget ürün belgesine uygulanan etiket için bekletme döneminin, *Cessation Production Spinning Widget* olay tarihine bağlı olarak başlatıldığını gösterir. Bir günlük bekletme süresi yapılandırarak test ortamınıza senaryoyu uygulamanızı varsayarak, etkinlik oluşturulduktan birkaç gün sonra ürün belgeleriniz için belge kitaplığına gidebilir ve belgenin silindikten sonra (SharePoint'te silme işi çalıştırıldıktan sonra) belge kitaplığına gidebilirsiniz.

### <a name="more-about-asset-ids"></a>Varlık kimlikleri hakkında daha fazla bilgi

Olay [oluştuğunda bekletmeyi](event-driven-retention.md) başlat makalesi şöyledir: Olay türleri, bekletme etiketleri, olaylar ve varlık kimlikleri arasındaki ilişkiyi anlamanız önemlidir. Varlık kimliği yalnızca SharePoint ve OneDrive. Bekletme süresi olay tarafından tetiklenen belgeleri tanımlamanıza yardımcı olur. Varsayılan olarak, SharePoint odaklı **bekletme için** kullanabileceğiniz bir Varlık Kimliği özelliği vardır:

![Varlık Kimliği özelliği, belge özellikleri ayrıntı sayfasında görüntülenir.](../media/SPRetention26.png)

Aşağıdaki ekran görüntüsünde de olduğu gibi, varlık kimliği yönetilen özelliği **ComplianceAssetId olarak adlandırılan özelliktir**.

[![ComplianceAssetId yönetilen özelliği.](../media/SPRetention27.png) ](../media/SPRetention27.png#lightbox)

Bu senaryoda olduğu gibi **varsayılan** Varlık Kimliği özelliğini kullanmak yerine, diğer herhangi bir özelliği kullanabilirsiniz. Ancak, bir olay için bir varlık kimliği veya anahtar sözcükler belirtmezseniz, bu olay türü etiketinin yer alan tüm içerikte bekletme süresi olayın tetiklenir.

### <a name="using-advanced-search-in-sharepoint"></a>Gelişmiş Arama'da SharePoint

Önceki ekran görüntüsünde, bir gezinilen özelle eşlenen **Bekletme** Etiketleri adlı bekletme etiketleriyle ilgili başka bir yönetilen özellik olduğunu görebilirsiniz. **ComplianceAssetId** yönetilen özelliği de gezinilen özelle eşlenmiştir. Başka bir ifadeyle, gelişmiş aramada bu yönetilen özellikleri kullanarak bir bekletme etiketiyle etiketlenmiş tüm belgeleri bulabilirsiniz.