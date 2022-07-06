---
title: SharePoint belge yaşam döngüsünü yönetmek için bekletme etiketlerini kullanma
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
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
search.appverid:
- MOE150
- MET150
description: İçeriği sınıflandırmak, etiketleri otomatik olarak uygulamak ve bekletme süresini başlatmak için olay tabanlı saklamayı kullanmak üzere meta verileri kullanarak SharePoint'teki belgelerin yaşam döngüsünü yönetmek için bekletme etiketlerini nasıl kullanabilirsiniz?
ms.openlocfilehash: ed054995943fc5366539fb6bc524757a6a6f820e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632981"
---
# <a name="use-retention-labels-to-manage-the-lifecycle-of-documents-stored-in-sharepoint"></a>SharePoint'te depolanan belgelerin yaşam döngüsünü yönetmek için bekletme etiketlerini kullanma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Bu makalede, otomatik olarak uygulanan bekletme etiketlerini ve olay tabanlı saklamayı kullanarak SharePoint'te depolanan belgelerin yaşam döngüsünü nasıl yönetebileceğiniz açıklanır.

Otomatik uygulama işlevi, belge sınıflandırması için SharePoint meta verilerini kullanır. Bu makaledeki örnek, ürünle ilgili belgelere yöneliktir, ancak aynı kavramlar diğer senaryolar için de kullanılabilir. Örneğin, petrol ve gaz sektöründe, petrol platformları, kuyu günlükleri veya üretim lisansları gibi fiziksel varlıklarla ilgili belgelerin yaşam döngüsünü yönetmek için kullanabilirsiniz. Finansal hizmetler sektöründe, banka hesabı, ipotek veya sigorta sözleşmesi belgelerini yönetebilirsiniz. Kamu sektöründe inşaat izinlerini veya vergi formlarını yönetebilirsiniz.

Bu makalede bilgi mimarisine ve bekletme etiketlerinin tanımına göz atacağız. Ardından etiketleri otomatik olarak uygulayarak belgeleri sınıflandıracağız. Son olarak bekletme süresini başlatan olayları oluşturacağız.

## <a name="information-architecture"></a>Bilgi mimarisi

Senaryomuz, şirketin geliştirdiği ürünlerle ilgili tüm belgeleri depolamak için SharePoint kullanan bir üretim şirketidir. Bu belgeler ürün belirtimlerini, tedarikçilerle yapılan sözleşmeleri ve kullanıcı kılavuzlarını içerir. Bu belgeler Kurumsal İçerik Yönetimi ilkeleri aracılığıyla SharePoint'te depolandığında, belge meta verileri tanımlanır ve bunları sınıflandırmak için kullanılır. Her belge aşağıdaki meta veri özelliklerine sahiptir:

- **Belge Türü** (ürün belirtimi, sözleşme veya kullanım kılavuzu gibi)

- **Ürün Adı**

- **Durum** (taslak veya son)

Bu meta veriler, tüm belgeler için *Üretim Belgesi* adlı bir temel içerik türü oluşturur.

![Ürün belgeleri meta verileri tablosu.](../media/SPRetention1.png)

> [!NOTE]
> **Belge Türü** ve **Durum** özellikleri, bekletme etiketlerini sınıflandırmak ve otomatik olarak uygulamak için bu senaryonun devamında bekletme ilkeleri tarafından kullanılır.

Farklı belge türlerini temsil eden çeşitli içerik türlerimiz olabilir, ancak şimdi ürün belgelerine odaklanalım.

Bu senaryoda, *Belge Türü* için bir terim kümesi ve *Ürün Adı* için bir terim kümesi oluşturmak için Yönetilen Meta Veri hizmetini ve Terim Deposu'nı kullanırız. Her terim kümesi için her değer için bir terim oluştururuz. SharePoint kuruluşunuz için Terim Deposu'nda şuna benzer olacaktır:

![Terim Deposu'ndaki ürün belgeleri için örnek terim kümesi.](../media/SPRetention2.png)

*İçerik Türü* , [İçerik Türü Hub'ı](https://support.office.com/article/manage-content-type-publishing-06f39ac0-5576-4b68-abbc-82b68334889b) kullanılarak oluşturulabilir ve yayımlanabilir. Ayrıca [, PnP sağlama çerçevesi](/sharepoint/dev/solution-guidance/pnp-provisioning-framework) veya site [tasarımı JSON şeması](/sharepoint/dev/declarative-customization/site-design-json-schema#define-a-new-content-type) gibi site sağlama araçlarını kullanarak içerik türü oluşturabilir ve yayımlayabilirsiniz.

Her ürün, doğru içerik türlerinin etkinleştirildiği bir belge kitaplığı içeren ayrılmış bir SharePoint sitesine sahiptir. Tüm belgeler bu belge kitaplığında depolanır.

[![Ürün belgeleri için belge kitaplığı.](../media/SPRetention3.png) ](../media/SPRetention3.png#lightbox)

> [!NOTE]
> Bu senaryoda üretim şirketi, ürün başına bir SharePoint sitesi kullanmak yerine, kalıcı sohbet gibi ekip üyeleri arasında işbirliğini desteklemek için ürün başına Bir Microsoft Team kullanabilir ve belge yönetimi için Teams'deki **Dosyalar** sekmesini kullanabilir. Bu makalede yalnızca belgelere odaklanacağız, bu nedenle yalnızca bir site kullanacağız.

Dönen Pencere Öğesi ürününün belge kitaplığının bir görünümü aşağıdadır:

[![Dönen Pencere Öğesi belge kitaplığı.](../media/SPRetention4.png) ](../media/SPRetention4.png#lightbox)

Belge yönetimi için temel bilgi mimarisini hazırladığımıza göre, meta verileri kullanan belgelerin saklama ve elden çıkarma stratejisine ve bu belgeleri nasıl sınıflandırdığımıza bakalım.

## <a name="retention-and-disposition"></a>Bekletme ve elden çıkarma

Üretim şirketinin uyumluluk ve veri idare ilkeleri, verilerin nasıl korunup atıldığını belirler. Ürünle ilgili belgeler, ürün üretildiği sürece ve belirli bir ek süre boyunca saklanmalıdır. Ek süre ürün belirtimleri, sözleşmeler ve kullanım kılavuzları için farklılık gösterir. Aşağıdaki tabloda saklama ve bırakma gereksinimleri gösterilir:

|   Belge türü            |   Saklama                            |   Disposition                                |
| -------------------------- | -------------------------------------- | -------------------------------------------- |
| Ürün belirtimleri      | Üretim durduktan 5 yıl sonra  | Silme                                       |
| Ürün sözleşmeleri          | Üretim durduktan 10 yıl sonra | Gözden geçirin                                       |
| Kullanıcı kılavuzları                | Üretim durduktan 5 yıl sonra  | Silme                                       |
| Diğer tüm belge türleri | Etkin bir şekilde saklama  | Belge 3 yıldan eskiyse sil <br /><br /> Belge son 3 yıl içinde değiştirilmediyse 3 yıldan eski kabul edilir. |
|||

Aşağıdaki [bekletme etiketlerini](retention.md#retention-labels) oluşturmak için Microsoft Purview uyumluluk portalı kullanırız:

  - Ürün Belirtimi

  - Ürün Sözleşmesi

  - Kullanıcı Kılavuzu

Bu makalede yalnızca Ürün Belirtimi saklama etiketinin nasıl oluşturulacağını ve otomatik olarak uygulanacağını göstereceğiz. Senaryonun tamamını uygulamak için diğer iki belge türü için bekletme etiketleri oluşturup otomatik olarak uygulayabilirsiniz.

### <a name="settings-for-the-product-specification-retention-label"></a>Ürün Belirtimi bekletme etiketi ayarları

Ürün Belirtimi bekletme etiketi için [dosya planı](file-plan-manager.md) aşağıdadır:

- **Adı:** Ürün Belirtimi

- **Kullanıcılar için açıklama:** Üretim durduktan sonra 5 yıl boyunca bekletin.

- **Yöneticiler için açıklama:** Üretim durduktan sonra 5 yıl boyunca tutun, otomatik silme, olay tabanlı saklama, olay türü *Ürün Durdurma'dır*.

- **Bekletme eylemi:** Saklama ve silme.

- **Bekletme süresi:** 5 yıl (1.825 gün).

- **Kayıt etiketi**: Bekletme etiketini öğeleri [kayıt](records-management.md#records) olarak işaretlenecek şekilde yapılandırın; bu da etiketlenen belgelerin kullanıcılar tarafından değiştirilebileceği veya silinemeyecek olduğu anlamına gelir.

- **Dosya planı tanımlayıcıları:** Senaryoyu basitleştirmek için isteğe bağlı dosya tanımlayıcıları sağlanmamaktadır.

Aşağıdaki ekran görüntüsü, Microsoft Purview uyumluluk portalı Ürün Belirtimi bekletme etiketini oluşturduğunuzda ayarları gösterir. Bekletme etiketini oluştururken *Product Cessation* olay türünü oluşturabilirsiniz. Aşağıdaki bölümdeki yordama bakın.

![Ürün Belirtimi etiketi için bekletme ayarları.](../media/SPRetention5.png)

> [!NOTE]
> Belgenin silinmesi için 5 yıllık beklemeyi önlemek için, bu senaryoyu bir test ortamında yeniden oluşturacaksanız bekletme süresini ***1 gün*** olarak ayarlayın.

### <a name="create-an-event-type-when-you-create-a-retention-label"></a>Bekletme etiketi oluşturduğunuzda olay türü oluşturma

1. Bekletme etiketi oluşturma sihirbazının **Bekletme ayarlarını tanımla** sayfasında, **Bekletme süresini temel alarak başlat'ın** ardından **Yeni olay türü oluştur'u** seçin:

    ![Ürün Belirtimi etiketi iletişim kutusu için yeni bir olay türü oluşturun.](../media/SPRetention6.png)

3. **Olay türünüzü adlandırın** sayfasında **Ürün Bırakma** ve isteğe bağlı bir açıklama girin. Ardından **İleri**, Gönder ve **Bitti'yi** seçin. 

4. **Bekletme ayarlarını tanımla** sayfasına dönün ve **Bekletme süresini şunu temel alarak başlatın** için açılan kutuyu kullanarak oluşturduğunuz **Ürün Bırakma** olay türünü seçin.

    Ürün Belirtimi bekletme etiketi için ayarlar şöyle görünür:

   ![Yeni Ürün Belirtimi etiketi için ayarlar.](../media/SPRetention7.png)

6. **Etiket oluştur'u** seçin ve sonraki sayfada etiketi yayımlama, etiketi otomatik uygulama veya yalnızca etiketi kaydetme seçeneklerini gördüğünüzde: **Şimdilik etiketi kaydet'i** ve ardından **Bitti'yi** seçin.

    > [!TIP]
    > Daha ayrıntılı adımlar için bkz. [Saklama süresi bir olayı temel alan bir etiket oluşturma](event-driven-retention.md#step-1-create-a-label-whose-retention-period-is-based-on-an-event).

Şimdi bekletme etiketini ürün belirtimi içeriğine otomatik olarak nasıl uygulayacağımıza bakalım.

## <a name="auto-apply-retention-labels-to-documents"></a>Belgelere bekletme etiketlerini otomatik uygulama

Oluşturduğumuz bekletme etiketlerini [otomatik olarak uygulamak](apply-retention-labels-automatically.md) için Anahtar Sözcük Sorgu Dili'ni (KQL) kullanacağız. KQL, arama sorguları oluşturmak için kullanılan dildir. KQL'de anahtar sözcükleri veya yönetilen özellikleri kullanarak arama yapabilirsiniz. Daha fazla bilgi için bkz [. Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Temel olarak, Microsoft 365'e "Son **Durumu** **ve** Belge **Türü** **Ürün Belirtimi** olan tüm belgelere **Ürün Belirtimi** bekletme etiketini uygulama" ifadesini vermek istiyoruz. **Durum** ve **Belge Türü'nü**, [Bilgi mimarisi](#information-architecture) bölümünde Ürün Belgeleri içerik türü için tanımladığımız site sütunları olduğunu hatırlayın. Bunu yapmak için arama şemasını yapılandırmamız gerekir.

SharePoint içeriği dizine eklediğinde, her site sütunu için gezinilen özellikleri otomatik olarak oluşturur. Bu senaryo için **Belge Türü** ve **Durum** özellikleriyle ilgileniyoruz. Kitaplıkta doğru içerik türü olan ve gezinilen özellikleri oluşturmak için arama için site sütunlarının doldurulduğu belgelere ihtiyacımız var.

<a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezinde</a> Arama yapılandırmasını açın ve gezinilen özellikleri görüntülemek ve yapılandırmak için **Arama Şemasını Yönet'i** seçin.

![Arama şemasında gezinilen özellikler.](../media/SPRetention8.png)

_ *Gezinilen özellikler** kutusuna ***status** _ yazıp yeşil oku seçersek şuna benzer bir sonuçla karşılaşırız:

![gezinilen ows_Status özelliği.](../media/SPRetention9.png)

**ows\_\_Status** özelliği (çift alt çizgiye dikkat edin) ilgimizi çeken özelliktir. Üretim Belgesi içerik türünün **Status** özelliğine eşler.

Şimdi ***ows\_doc*** yazıp yeşil oku seçersek şuna benzer bir şey görmemiz gerekir:

![gezinilen ows_Doc_Type özelliği.](../media/SPRetention10.png)

**ows\_Doc\_x0020\_Type** özelliği, ilgimizi çeken ikinci özelliktir. Üretim Belgesi içerik türünün **Belge Türü** özelliğine eşler.

> [!TIP]
> Bu senaryo için gezinilen özelliğin adını belirlemek için üretim belgelerini içeren belge kitaplığına gidin. Ardından kitaplık ayarlarına gidin. **Sütunlar** için, site sütunu sayfasını açmak için sütunun adını (örneğin, **Durum** veya **Belge Türü**) seçin. Bu sayfanın URL'sindeki *Field* parametresi alanın adını içerir. "ows_" ön ekli bu alan adı, gezinilen özelliğin adıdır. Örneğin URL, `https://tenantname.sharepoint.com/sites/SpinningWidget/_layouts/15/FldEdit.aspx?List=%7BC38C2F45-3BD6-4C3B-AA3B-EF5DF6B3D172%7D&Field=_Status` *ows\_\_Durumu* gezinilen özelliğine karşılık gelir.

Aradığınız gezinilen özellikler SharePoint yönetim merkezindeki Arama Şemasını Yönet bölümünde görünmüyorsa:

- Belki belgeler dizine eklenemedi. Belge kitaplığı ayarları  > **Gelişmiş Ayarlar'a** giderek **kitaplığın** yeniden dizine alınmasını zorlayabilirsiniz.

- Belge kitaplığı modern bir sitedeyse, SharePoint yöneticisinin de site koleksiyonu yöneticisi olduğundan emin olun.

Gezinilen ve yönetilen özellikler hakkında daha fazla bilgi için bkz. [SharePoint Server'da otomatik olarak oluşturulan yönetilen özellikler](/sharepoint/technical-reference/automatically-created-managed-properties-in-sharepoint).

### <a name="map-crawled-properties-to-pre-defined-managed-properties"></a>Gezinilen özellikleri önceden tanımlanmış yönetilen özelliklerle eşleme

KQL, arama sorgularında gezinilen özellikleri kullanamaz. Yönetilen bir özellik kullanması gerekir. Tipik bir arama senaryosunda yönetilen bir özellik oluşturur ve bunu ihtiyacımız olan gezinilen özelliğe eşleriz. Ancak, bekletme etiketlerini otomatik olarak uygulamak için özel yönetilen özellikleri değil, yalnızca KQL'de önceden tanımlanmış yönetilen özellikleri belirtebilirsiniz. Sistemde, kullanabileceğiniz *RefinableString00* ile *RefinableString199* dizesi için önceden tanımlanmış bir dizi yönetilen özellik vardır. Tam liste için bkz. [Varsayılan kullanılmayan yönetilen özellikler](/sharepoint/manage-search-schema#default-unused-managed-properties). Bu varsayılan yönetilen özellikler genellikle arama iyileştiricilerini tanımlamak için kullanılır.

KQL sorgusunun ürün belgesi içeriğine doğru bekletme etiketini otomatik olarak uygulaması için **, Doc\_x0020\_Type ve ows\_* *\_\_Status** ile iki iyileştirilebilir yönetilen özellik arasında gezinilen özellikleri eşleriz. Bu senaryo için test ortamımızda **RefinableString00** ve **RefinableString01** kullanılmıyor. Bunu <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">, SharePoint yönetim merkezindeki</a> **Arama Şemasını Yönet'teki** **Yönetilen Özellikler'e** bakarak belirledik.

[![Arama şemasındaki yönetilen özellikler.](../media/SPRetention12.png) ](../media/SPRetention12.png#lightbox)

Önceki ekran görüntüsündeki **Eşlenmiş Gezinilen Özellikler** sütununun boş olduğuna dikkat edin.

**ows\_Doc\_x0020\_Type** gezinilen özelliğini eşlemek için şu adımları izleyin:

1. **Yönetilen özellik** filtresi kutusuna **_RefinableString00_** yazın ve yeşil oku seçin.

2. Sonuçlar listesinde **RefinableString00** bağlantısını seçin ve **gezinilen özelliklere eşlemeler** bölümüne kadar aşağı kaydırın.

3. **Eşleme Ekle'yi** seçin ve **gezinilen** **_\_özellik seçimi penceresindeki _Gezinilen özellik adı ara kutusuna Doc\_x0020\_Type_*_*** yazın. **Bul'u** seçin.

4. Sonuçlar listesinde **, Belge\_x0020\_Türü'nü seçip\_** **Tamam'ı** seçin.

   **Eşlenen Gezinilen Özellikler** bölümünde bu ekran görüntüsüne benzer bir şey görmeniz gerekir:

   [![Eşlenen gezinilen özellikler bölümünde Eşleme ekle'yi seçin.](../media/SPRetention13.png) ](../media/SPRetention13.png#lightbox)


5. Sayfanın en altına kaydırın ve eşlemeyi kaydetmek için **Tamam'ı** seçin.

**RefinableString01** ve **ows Durumunu eşlemek\_\_** için bu adımları yineleyin.

Şimdi gezinilen iki özelliğe eşlenmiş iki yönetilen özelliğiniz olmalıdır:

[![Gezinilen özelliklerle eşlenmiş olarak gösterilen yönetilen özellikler.](../media/SPRetention14.png) ](../media/SPRetention14.png#lightbox)

Şimdi kurumsal bir arama çalıştırarak kurulumumuzun doğru olduğunu doğrulayalım. Tarayıcıda *https://\<your_tenant>.sharepoint.com/search* gidin. Arama kutusuna ***RefinableString00:"Product Specification"** _ yazın ve Enter tuşuna basın. Bu arama, _ *Ürün Belirtimi** **_belge türüne_** sahip tüm belgeleri döndürmelidir.

Şimdi arama kutusuna **RefinableString00:"Product Specification" AND RefinableString01:Final** yazın ve Enter tuşuna basın. Bu, **_Belge Türü_*_*** **Ürün Belirtimi** ve _ **_Son_** Durumu olan tüm belgeleri döndürmelidir.

### <a name="create-auto-apply-label-policies"></a>Etiket ilkelerini otomatik uygulama oluşturma

KQL sorgusunun çalıştığını doğruladığımıza göre, ürün belirtimi bekletme etiketini uygun belgelere otomatik olarak uygulamak için KQL sorgusu kullanan bir otomatik uygulama etiketi ilkesi oluşturalım.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> **Kayıt yönetimi** > **Etiket ilkeleri** > **Etiketi otomatik uygulama'ya** gidin.

   [![Etiketler sayfasında "Etiketi otomatik uygulama" seçeneğini belirleyin](../media/SPRetention16.png) ](../media/SPRetention16.png#lightbox)

2. Otomatik etiketleme ilkesi oluşturma sihirbazının **Otomatik etiketleme ilkenizi adlandırın** sayfasında, **Ürün Belirtimini Otomatik Uygula etiketi** gibi bir ad ve isteğe bağlı bir açıklama girin. Ardından **İleri'yi** seçin.

3. **Bu etiketi uygulamak istediğiniz içerik türünü seçin** sayfasında, **Belirli sözcükler veya tümcecikler veya özellikler içeren içeriğe etiket uygula'yı** ve ardından **İleri'yi** seçin.

   [![Belirli sözcükler, tümcecikler veya özellikler içeren içeriğe etiket uygula'yı seçin.](../media/SPRetention17.png) ](../media/SPRetention17.png#lightbox)

   Bu seçenek, önceki bölümde test ettiğimiz aynı KQL arama sorgusunu sağlamamıza olanak tanır. Sorgu, *durumu Son* olan tüm Ürün Belirtimi belgelerini döndürür. Otomatik uygulama etiketi ilkesinde aynı sorguyu kullandığımızda, Ürün Belirtimi bekletme etiketi, bu sorguyla eşleşen tüm belgelere otomatik olarak uygulanır.

4. **Bu sorguyla eşleşen içeriğe etiket uygula** sayfasında **, RefinableString00:"Product Specification" AND RefinableString01:Final** yazın ve **İleri'yi** seçin.

   ![Anahtar sözcük sorgu düzenleyicisi kutusunda sorguyu belirtin.](../media/SPRetention19.png)

5. **İlkenin uygulanacağı konumları seçin sayfasında, ilkeyi** uygulamak istediğiniz içerik konumlarını seçersiniz. Bu senaryoda, tüm üretim belgeleri SharePoint belge kitaplıklarında depolandığından ilkeyi yalnızca SharePoint konumlarına uygularız. **Exchange e-postası**, **OneDrive hesapları** ve **Microsoft 365 Grupları** durumunu **Kapalı olarak değiştirin**. **İleri'yi** seçmeden önce SharePoint sitelerinin durumunun **Açık** olarak ayarlandığından emin olun:

    ![Etiketlerin otomatik olarak uygulanacağı belirli siteleri seçin.](../media/SPRetentionSPlocations.png)

   > [!TIP]
   > İlkeyi tüm SharePoint sitelerine uygulamak yerine **Site seç'i** seçip belirli SharePoint sitelerinin URL'lerini ekleyebilirsiniz.

6. **Otomatik uygulanacak etiket seçin** sayfasında **Etiket ekle'yi** seçin.

7. Bekletme etiketleri listesinden **Ürün Belirtimi'ni** seçin. Ardından **Ekle ve** **İleri'yi** seçin.

8. Ayarlarınızı gözden geçirin:

    ![Etiketi otomatik uygulama ayarları.](../media/SPRetention18.png)

9. Etiket ilkesini otomatik olarak uygulamak için **Gönder'i** seçin.

   > [!NOTE]
   > Ürün Belirtimi etiketinin KQL arama sorgusuyla eşleşen tüm belgelere otomatik olarak uygulanması 7 güne kadar sürer.

### <a name="verify-that-the-retention-label-was-automatically-applied"></a>Bekletme etiketinin otomatik olarak uygulandığını doğrulayın

7 gün sonra, oluşturduğumuz otomatik uygulama etiketi ilkesinin ürün belgelerine bekletme etiketlerini otomatik olarak uyguladığını doğrulamak için Microsoft Purview uyumluluk portalı [etkinlik gezginini](data-classification-activity-explorer.md) kullanın.

Belge Kitaplığı'ndaki belgelerin özelliklerine de bakın. Bilgi panelinde, bekletme etiketinin seçili belgeye uygulandığını görebilirsiniz.

[![Belge Kitaplığı'ndaki belge özelliklerine bakarak etiketin uygulandığını doğrulayın.](../media/SPRetention21.png) ](../media/SPRetention21.png#lightbox)

Bekletme etiketleri belgelere otomatik olarak uygulandığından, bekletme etiketi belgeleri *kayıt* olarak bildirmek üzere yapılandırıldığından bu belgeler silinmeye karşı korunur. Bu korumanın bir örneği olarak, bu belgelerden birini silmeye çalışırken aşağıdaki hata iletisini alacağız:

[![Etiket belgelerin kayıt olduğunu bildirdiğinden belgelerin silineebileceğini gösteren bir hata iletisi.](../media/SPRetention22.png) ](../media/SPRetention22.png#lightbox)

## <a name="generate-the-event-that-triggers-the-retention-period"></a>Bekletme süresini tetikleyen olayı oluşturma

Artık bekletme etiketleri uygulandığına göre, belirli bir ürün için üretim sonunu gösteren olaya odaklanalım. Bu olay, bekletme etiketlerinde tanımlanan bekletme süresinin başlangıcını tetikler. Örneğin, ürün belirtimi belgeleri için 5 yıllık saklama süresi "üretim sonu" olayının tetiklenmesiyle başlar.

**Kayıt Yönetimi** > **Olayları'na** giderek olayı Microsoft Purview uyumluluk portalı el ile oluşturabilirsiniz. Olay türünü seçer, doğru varlık kimliklerini ayarlar ve olay için bir tarih girersiniz. Daha fazla bilgi için bkz. [Olay gerçekleştiğinde bekletmeyi başlatma](event-driven-retention.md).

Ancak bu senaryo için olayı otomatik olarak bir dış üretim sisteminden oluşturacağız. Sistem, bir ürünün üretimde olup olmadığını gösteren basit bir SharePoint listesidir. Listeyle ilişkilendirilmiş bir [Power Automate](/power-automate/getting-started) akışı olayı tetikler. Gerçek dünya senaryosunda olayı oluşturmak için İk veya CRM sistemi gibi çeşitli sistemleri kullanabilirsiniz. Power Automate; Microsoft Exchange, SharePoint, Teams ve Dynamics 365 gibi Microsoft 365 iş yükleri için birçok kullanıma hazır etkileşim ve yapı taşının yanı sıra Twitter, Box, Salesforce ve Workdays gibi üçüncü taraf uygulamaları içerir. Bu özellik, Power Automate'i çeşitli sistemlerle tümleştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Olay temelli saklamayı otomatikleştirme](./event-driven-retention.md#automate-events-by-using-a-rest-api).

Aşağıdaki ekran görüntüsünde, olayı tetikleyen kullanılacak SharePoint listesi gösterilmektedir:

[![Bekletme olayını tetikleyecek liste.](../media/SPRetention23.png) ](../media/SPRetention23.png#lightbox)

Şu anda üretimde olan ve _ *In Production** sütunundaki ***Yes** _ ile belirtilen iki ürün vardır. Bu sütundaki değer bir ürün için **_Hayır_** olarak ayarlandığında, listeyle ilişkili akış olayı otomatik olarak oluşturur. Olay, ilgili ürün belgelerine otomatik olarak uygulanan bekletme etiketi için bekletme süresinin başlangıcını tetikler.

Bu senaryoda, olayı tetikleme amacıyla aşağıdaki akışı kullanırız:

[![Olayı tetikleyecek akışı yapılandırma.](../media/SPRetention24.png) ](../media/SPRetention24.png#lightbox)

Bu akışı oluşturmak için bir SharePoint bağlayıcısından başlayın ve **Öğe oluşturulduğunda veya değiştirildiğinde** tetikleyicisini seçin. Site adresini ve liste adını belirtin. Ardından **Üretimde** liste sütun değerinin **_Hayır_* _ (veya koşul kartındaki _false* değerine eşit) olarak ayarlanmasına bağlı olarak bir koşul ekleyin. Ardından yerleşik HTTP şablonunu temel alan bir eylem ekleyin. HTTP eylemini yapılandırmak için aşağıdaki bölümdeki değerleri kullanın. Aşağıdaki bölümden **URI** ve **Gövde** özellikleri için değerleri kopyalayıp şablona yapıştırabilirsiniz.

- **Yöntem**: POST
- **URI**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Üst Bilgiler**: Key = content-Type, Value = application/atom+xml
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

Bu listede, bu senaryo için yapılandırılması gereken eylemin **Body** özelliğindeki parametreler açıklanmaktadır:

- **Ad**: Bu parametre, Microsoft Purview uyumluluk portalı oluşturulacak olayın adını belirtir. Bu senaryo için ad "Cessation Production *xxx*" şeklindedir; burada *xxx* , daha önce oluşturduğumuz **ProductName** yönetilen özelliğinin değeridir.
- **EventType**: Bu parametrenin değeri, oluşturulan olayın uygulanacağı olay türüne karşılık gelir. Bu olay türü, bekletme etiketini oluşturduğunuzda tanımlanmıştır. Bu senaryo için olay türü "Ürün Bırakma" olur.
- **SharePointAssetIdQuery**: Bu parametre olayın varlık kimliğini tanımlar. Olay tabanlı saklama için belge için benzersiz bir tanımlayıcı gerekir. Belirli bir olayın uygulandığı belgeleri veya bu senaryoda olduğu gibi meta veri sütununun **Ürün Adı'nı** tanımlamak için varlık kimliklerini kullanabiliriz. Bunu yapmak için KQL sorgusunda kullanılabilecek yeni bir **ProductName** yönetilen özelliği oluşturmamız gerekir. (Alternatif olarak, yeni bir yönetilen özellik oluşturmak yerine **RefinableString00** kullanabiliriz). Ayrıca bu yeni yönetilen özelliği **gezinilen ows_Product_x0020_Name** özelliğiyle eşlememiz gerekir. Bu yönetilen özelliğin ekran görüntüsü aşağıdadır.

    [![Rentention tarafından yönetilen tesis.](../media/SPRetention25.png) ](../media/SPRetention25.png#lightbox)

- **EventDateTime**: Bu parametre, olayın gerçekleştiği tarihi tanımlar. Geçerli tarih biçimini kullanın:<br/><br/>*formatDateTime(utcNow(),'yyyy-MM-dd'*)

### <a name="putting-it-all-together"></a>Hepsini bir araya getiriyoruz

Şimdi bekletme etiketi oluşturulur ve otomatik olarak uygulanır ve akış yapılandırılır ve oluşturulur. Ürünler listesindeki Dönen Pencere Öğesi ürününün **Üretimde** sütunundaki değer **_Evet_*_ yerine _*_No_ _ olarak değiştirildiğinde *, akış olayı oluşturmak için tetikler. Bu olayı Microsoft Purview uyumluluk portalı görmek için _* Kayıt yönetimi** > **Olayları'na** gidin.

[![Akış tarafından tetiklenen olay, Microsoft Purview uyumluluk portalı Olaylar sayfasında görüntülenir.](../media/SPRetention28.png) ](../media/SPRetention28.png#lightbox)

Açılır sayfada ayrıntıları görüntülemek için olayı seçin. Olay oluşturulduğunda bile, olay durumu hiçbir SharePoint sitesi veya belgesinin işlenmediğini gösterir.

![Olay ayrıntıları.](../media/SPRetention29.png)

Ancak bir gecikmeden sonra, olay durumu bir SharePoint sitesinin ve bir SharePoint belgesinin işlendiğini gösterir.

![Olay ayrıntıları belgelerin işlendiğini gösterir.](../media/SPRetention31.png)

Bu, Dönen Pencere Öğesi ürün belgesine uygulanan etiketin saklama süresinin *, Bırakma Üretim Dönen Pencere Öğesi* olayının olay tarihine göre başlatıldığını gösterir. Test ortamınızda bir günlük saklama süresi yapılandırarak senaryoyu uyguladığınızı varsayarsak, olay oluşturulduktan birkaç gün sonra ürün belgelerinizin belge kitaplığına gidebilir ve belgenin silindiğini doğrulayabilirsiniz (SharePoint'teki silme işi çalıştırıldıktan sonra).

### <a name="more-about-asset-ids"></a>Varlık kimlikleri hakkında daha fazla bilgi

[Olay gerçekleştiğinde bekletmeyi başlatma](event-driven-retention.md) makalesinde açıklandığı gibi, olay türleri, bekletme etiketleri, olaylar ve varlık kimlikleri arasındaki ilişkiyi anlamak önemlidir. Varlık kimliği yalnızca SharePoint ve OneDrive'daki bir belge özelliğidir. Saklama süresi olay tarafından tetiklenecek belgeleri belirlemenize yardımcı olur. Varsayılan olarak, SharePoint'te olay temelli saklama için kullanabileceğiniz bir **Varlık Kimliği** özelliği vardır:

![Varlık Kimliği özelliği belge özellikleri ayrıntı sayfasında görüntülenir.](../media/SPRetention26.png)

Aşağıdaki ekran görüntüsünde gösterildiği gibi varlık kimliği yönetilen **özelliğiNe ComplianceAssetId** adı verilir.

[![ComplianceAssetId yönetilen özelliği.](../media/SPRetention27.png) ](../media/SPRetention27.png#lightbox)

Bu senaryoda yaptığımız gibi varsayılan **Varlık Kimliği** özelliğini kullanmak yerine başka herhangi bir özelliği kullanabilirsiniz. Ancak bir olay için varlık kimliği veya anahtar sözcükler belirtmezseniz, söz konusu olay türü etiketine sahip tüm içeriğin, olay tarafından tetiklenen saklama süresine sahip olacağını anlamanız önemlidir.

### <a name="using-advanced-search-in-sharepoint"></a>SharePoint'te gelişmiş aramayı kullanma

Önceki ekran görüntüsünde, gezinilen bir özelliğe eşlenmiş **ComplianceTag** adlı bekletme etiketleriyle ilgili başka bir yönetilen özellik olduğunu görebilirsiniz. **ComplianceAssetId** yönetilen özelliği de gezinilen bir özelliğe eşlenir. Bu, bekletme etiketiyle etiketlenmiş tüm belgeleri almak için gelişmiş aramada bu yönetilen özellikleri kullanabileceğiniz anlamına gelir.
