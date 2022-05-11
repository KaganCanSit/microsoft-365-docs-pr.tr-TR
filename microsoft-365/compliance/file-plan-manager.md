---
title: Bekletme etiketlerini yönetmek için dosya planını kullanma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
ms.assetid: af398293-c69d-465e-a249-d74561552d30
description: Dosya planı bekletme etiketleri için gelişmiş yönetim özellikleri sağlar.
ms.openlocfilehash: d509d878b244054138e4e95329d00759719e131d
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319058"
---
# <a name="use-file-plan-to-create-and-manage-retention-labels"></a>Bekletme etiketleri oluşturmak ve yönetmek için dosya planını kullanma

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı **Veri yaşam döngüsü yönetiminden** bekletme etiketleri oluşturup yönetebilirsiniz ancak **Kayıtlar yönetiminin** dosya planı ek yönetim özelliklerine sahiptir:

- İlgili bilgileri bir elektronik tablodan içeri aktararak bekletme etiketlerini toplu olarak oluşturabilirsiniz.

- Analiz ve çevrimdışı işbirliği için mevcut bekletme etiketlerinden bilgileri dışarı aktarabilirsiniz.

- Bekletme etiketleri hakkında daha fazla bilgi, tüm bekletme etiketlerinizin ayarlarını tek bir görünümden görmenizi ve bunları daha kolay görebilmenizi sağlamak için görüntülenir.

- Dosya planı tanımlayıcıları her etiket için ek ve isteğe bağlı bilgileri destekler.

Dosya planı, içeriği kayıt olarak işaretlemeseler bile tüm bekletme etiketleri için kullanılabilir.

Bekletme etiketlerinin ne olduğu ve nasıl kullanılacağı hakkında bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

## <a name="accessing-file-plan"></a>Dosya planına erişme

Dosya planına erişmek için aşağıdaki yönetici rollerinden birine sahip olmanız gerekir:
    
- Bekletme Yöneticisi

- Yalnızca görüntüleme bekletme yöneticisi

[Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **ÇözümlerKayıt** >  **yönetimiDosya** >  **planı'na** gidin.

**Kayıt yönetimi** gezinti bölmesinde görüntülenmiyorsa, önce aşağı kaydırın ve **Tümünü göster'i** seçin.

## <a name="navigating-your-file-plan"></a>Dosya planınızda gezinme

Microsoft Purview uyumluluk portalı **Veri yaşam döngüsü yönetiminden** bekletme etiketleri oluşturduysanız, bu etiketler dosya planınızda otomatik olarak görüntülenir. 

Benzer şekilde, artık dosya planında bekletme etiketleri oluşturursanız, etiketler içeriği kayıt olarak işaretlemek üzere yapılandırılmadıysa **Veri yaşam döngüsü yönetiminden** de kullanılabilir.

**Dosya planı** sayfasında, durum ve ayarlarıyla birlikte tüm etiketlerinizi, isteğe bağlı dosya planı tanımlayıcılarını, etiketlerinizin çevrimdışı gözden geçirmelerini analiz etmek veya etkinleştirmek için bir dışarı aktarma seçeneği ve bekletme etiketleri oluşturmak için içeri aktarma seçeneğini görürsünüz. 

### <a name="label-settings-columns"></a>Etiket ayarları sütunları

Sütunları özelleştir seçeneği seçilerek **Etiket Adı** dışındaki tüm **sütunlar** görüntülenebilir veya gizlenebilir. Ancak varsayılan olarak, ilk birkaç sütun etiket durumu ve ayarları hakkındaki bilgileri görüntüler: 

- **Durum** , etiketin bir etiket ilkesine mi yoksa otomatik uygulama ilkesine mi (**Etkin**) eklenip eklenmediğini (**Etkin değil**) tanımlar.

- **Saklama** süresinin nasıl veya ne zaman başladığını tanımlar. Geçerli değerler:
    - Olay
    - Oluşturulduğunda
    - Son değiştirme
    - Etiketlendiğinde

- **Kayıt,** etiket uygulandığında öğenin kayıt olarak işaretlenip işaretlenmediğini tanımlar. Geçerli değerler:
    - Hayır
    - Evet
    - Evet(Mevzuat)

- **Varsayılan olarak kilidinin açık olması** (şu anda kullanıma sunılıyor), etiket uygulandığında kayıt olarak işaretlenmiş öğenin kilidinin açık olup olmadığını belirler. Geçerli değerler:
    - Hayır
    - Evet

- **Şu** anda kullanıma sunulan öğesine yeniden etiketleme, etiketin saklama süresinin sonunda başka bir etiket uygulayacak şekilde yapılandırılıp yapılandırılmamış olduğunu tanımlar. Geçerli değerler:
    - Boş veya seçili etiket adı

- **Bekletme süresi** , saklama süresini tanımlar. Geçerli değerler:
    - Gün
    - Ay
    - Yıl
    - Sonsuza kadar
    - Yok

- **Değerlendirme türü** , saklama süresinin sonunda içeriğe ne olduğunu tanımlar. Geçerli değerler:
    - Eylem yok
    - Otomatik silme
    - Gözden geçirme gerekli

### <a name="file-plan-descriptors-columns"></a>Dosya planı tanımlayıcıları sütunları

Dosya planı, bekletme etiketlerinizin bir parçası olarak daha fazla bilgi eklemenize olanak tanır. Bu dosya planı tanımlayıcıları, etiketlemeniz gereken içeriğin yönetilebilirliğini ve düzenlenmesini geliştirmek için daha fazla seçenek sağlar.

Varsayılan olarak, **Başvuru Kimliği** ile başlayarak, sonraki birkaç sütunda bekletme etiketi oluşturduğunuzda veya var olan bir etiketi düzenlerken belirtebileceğiniz bu isteğe bağlı dosya planı tanımlayıcıları görüntülenir. 

Başlamak için aşağıdaki dosya planı tanımlayıcıları için kullanıma hazır bazı değerler vardır: 
- İş işlevi/departman
- Kategori
- Yetkili türü
- Sağlama/alıntı 

Bekletme etiketi oluştururken veya düzenlerken dosya planı tanımlayıcıları örneği:

![Bekletme etiketi oluştururken veya düzenlerken dosya planı tanımlayıcıları.](../media/file-plan-descriptors.png)

Bu isteğe bağlı tanımlayıcıların her biri için **Seç'i** seçtiğinizde, kullanıma hazır değerlerden birini seçebilir veya kendi değerlerinizi oluşturup seçebilirsiniz. Örneğin: 

![Sağlama/alıntı için yeni dosya planı tanımlayıcısı oluşturun.](../media/file-plan-descriptors-create.png)

## <a name="create-retention-labels"></a>Bekletme etiketleri oluşturma

1. **Dosya planı** sayfasında **+ Etiket** >  **oluşturYeni etiket oluştur'u** seçin

2. Yapılandırma işlemi istemlerini izleyin. Etiket kaydedildikten sonra değiştirilemediğinden, hangi adı seçtiğinize dikkat edin.
    
    Bekletme ayarları hakkında daha fazla bilgi için bkz. [İçeriği saklama ve silme Ayarlar](retention-settings.md#settings-for-retaining-and-deleting-content).
    
    Kayıtları bildirmek için bekletme etiketini kullanmak için **Öğeleri kayıt olarak işaretle'yi** veya **Öğeleri mevzuat kayıtları olarak işaretle'yi** seçin. Daha fazla bilgi için bkz [. Kayıtları bildirmek için bekletme etiketlerini yapılandırma](declare-records.md#configuring-retention-labels-to-declare-records).

3. Etiketi oluşturduktan ve etiketi yayımlama seçeneklerini gördükten sonra etiketi otomatik olarak uygulayın veya yalnızca etiketi kaydedin: **Yalnızca şimdilik etiketi kaydet'i** ve ardından **Bitti'yi** seçin.

4. Daha fazla etiket oluşturmak için bu adımları yineleyin.

## <a name="edit-retention-labels"></a>Bekletme etiketlerini düzenleme

Mevcut bir bekletme etiketini düzenlemek için **Dosya Planı** sayfasından etiketi seçin ve ardından **etiketi düzenle** seçeneğini belirleyerek etiket açıklamasını ve uygun ayarları değiştirmenize olanak tanıyan bekletmeyi düzenleme işlemini başlatın.

Etiket oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez; bunlar şunlardır:
- Bekletme süresi dışında bekletme etiketi adı ve bekletme ayarları. Ancak, bekletme süresinin öğelerin etiketlendiği zamanlara göre olduğu saklama süresini değiştiremezsiniz.
- Öğeleri kayıt olarak işaretleme seçeneği.

## <a name="delete-retention-labels"></a>Bekletme etiketlerini silme

Şu anda [yayımlanmış](create-apply-retention-labels.md) veya [otomatik uygulama](apply-retention-labels-automatically.md) bekletme etiketi ilkelerine dahil olmayan, olay tabanlı saklama için yapılandırılmamış bekletme etiketlerini silebilir veya öğeleri mevzuat kayıtları olarak işaretleyebilirsiniz.

Silebileceğiniz bekletme etiketleri için, öğelere uygulanmışsa silme işlemi başarısız olur ve etiketlenmiş öğeleri tanımlamak için içerik gezgininin bağlantısını görürsünüz.

Ancak, içerik gezgininin etiketlenmiş öğeleri göstermesi iki gün kadar sürebilir. Bu senaryoda, bekletme etiketi içerik gezgini bağlantısını göstermeden silinebilir.

## <a name="export-all-retention-labels-to-analyze-or-enable-offline-reviews"></a>Çevrimdışı incelemeleri analiz etmek veya etkinleştirmek için tüm bekletme etiketlerini dışarı aktarma

Dosya planınızdan, kuruluşunuzdaki veri idaresi paydaşlarıyla düzenli uyumluluk gözden geçirmelerini kolaylaştırmanıza yardımcı olmak için tüm bekletme etiketlerinin ayrıntılarını bir .csv dosyasına aktarabilirsiniz.

Tüm bekletme etiketlerini dışarı aktarmak için: **Dosya planı** sayfasında **Dışarı Aktar'a** tıklayın.

Tüm mevcut bekletme etiketlerini içeren bir *.csv dosyası açılır. Örneğin:

![Tüm bekletme etiketlerini gösteren CSV dosyası.](../media/file-plan-csv-file.png)

## <a name="import-retention-labels-into-your-file-plan"></a>Bekletme etiketlerini dosya planınıza aktarma

Dosya planında, belirli bir biçime sahip bir .csv dosyası kullanarak yeni bekletme etiketlerini toplu olarak içeri aktarabilirsiniz: 

1. **Dosya planı** sayfasında **İçeri Aktar**: ![Dosya planını içeri aktarma seçeneğine tıklayın](../media/compliance-file-plan-import-labels.png)

2. **Dosya planınızı doldur ve içeri aktar** bölmesinde **Boş şablon indir'i** seçin:

   ![Boş bir dosya planı şablonu indirme seçeneği](../media/file-plan-blank-template-option.png)

3. Şablon indirildikten sonra her etiket için bir satır ekleyin ve dosyayı kaydedin. Her özelliğin özelliklerini ve geçerli değerlerini açıklayan bilgiler için [sonraki bölüme](#information-about-the-label-properties-for-import) bakın.
    
    Doldurulmuş şablon örneği:
    
    ![Bilgilerin doldurulduğu dosya planı şablonu.](../media/file-plan-filled-out-template.png)

4. Doldurulmuş şablonu karşıya yüklemek için **bir dosya Upload** seçin.
    
   Dosya planı dosyayı karşıya yükler ve girişleri doğrular.

5. Doğrulama sonuçlarına bağlı olarak:
    
    - Doğrulama başarısız olursa: İçeri aktarma dosyasında düzeltilen satır numarasını ve sütun adını not edin. Dosyadaki hataları düzeltip kaydedin ve 4. adımı yineleyin.
    
    - Doğrulama başarılı olursa: Bir **dosya planını başarıyla içeri aktardığınız** ve girdilerin başarıyla bekletme etiketlerine dönüştürüldüğünü görürsünüz. **Bitti'yi** seçerek bölmeyi kapatın ve yeni etiketlerinizi görüntülemek için **Dosya planı** sayfasını otomatik olarak yenileyin.

Artık yeni bekletme etiketlerinizi yayımlayabilir veya otomatik olarak uygulayabilirsiniz. **Etiket ilkeleri sekmesinde Etiketleri** **yayımla'yı** veya **Etiketi otomatik olarak uygula'yı** seçerek her ikisini de yapabilirsiniz.

### <a name="information-about-the-label-properties-for-import"></a>İçeri aktarma için etiket özellikleri hakkında bilgi

yeni bekletme etiketlerini içeri aktarmak için indirilen şablonu doldurmanıza yardımcı olması için aşağıdaki bilgileri kullanın. Bazı değerlerin içeri aktarma için uzunluk üst sınırı vardır:

- **LabelName**: En fazla 64 karakter uzunluğunda
- **Açıklama** ve **Notlar**: En fazla 1024 karakter uzunluğunda
- Diğer tüm değerler: Sınırsız uzunluk
<br/>

|Özellik|Tür|Gerekli|Geçerli değerler|
|:-----|:-----|:-----|:-----|
|LabelName|Dize|Evet|Bu özellik, bekletme etiketinin adını belirtir ve kiracınızda benzersiz olmalıdır. İçeri aktarma için desteklenen karakterler: a-z, A-Z, 0-9, kısa çizgi (-) ve boşluk karakteri.|
|Açıklama ekleme|Dize|Hayır|Yöneticiler için bekletme etiketi hakkında bir açıklama eklemek için bu özelliği kullanın. Bu açıklama yalnızca Microsoft Purview uyumluluk portalı bekletme etiketini yöneten yöneticilere görünür.|
|Notlar|Dize|Hayır|Kullanıcılar için bekletme etiketi hakkında bir açıklama eklemek için bu özelliği kullanın. Kullanıcılar Outlook, SharePoint ve OneDrive gibi uygulamalarda etiketin üzerine geldiğinde bu açıklama görüntülenir. Bu özelliği boş bırakırsanız, etiketin bekletme ayarlarını açıklayan varsayılan bir açıklama görüntülenir. |
|IsRecordLabel|Dize|**Hayır, Mevzuat** **DOĞRU** değilse|Bu özellik, etiketin içeriği kayıt olarak işaretleyip işaretlemediğini belirtir. Geçerli değerler şunlardır: </br>**DOĞRU**: Etiket öğeyi kayıt olarak işaretler ve sonuç olarak öğe silinemez. </br>**YANLIŞ**: Etiket içeriği kayıt olarak işaretlemez. Bu, varsayılan değerdir. </br> </br> Grup bağımlılıkları: Bu özellik belirtildiğinde RetentionAction, RetentionDuration ve RetentionType da belirtilmelidir.|
|RetentionAction|Dize|Hayır, **RetentionDuration**, **RetentionType** veya **ReviewerEmail** belirtilmediği sürece|Bu özellik, RetentionDuration özelliği (belirtildiyse) tarafından belirtilen değerin süresi dolduktan sonra hangi eylemin gerçekleştireceğini belirtir. Geçerli değerler şunlardır: </br>**Sil**: RetentionDuration özelliği tarafından belirtilen değerden eski öğeler silinir.</br>**Koru**: Öğeleri RetentionDuration özelliği tarafından belirtilen süre boyunca tutun ve süre dolduğunda hiçbir şey yapma. </br>**KeepAndDelete**: Öğeleri RetentionDuration özelliği tarafından belirtilen süre boyunca tutun ve süre dolduğunda silin. </br> </br> Grup bağımlılıkları: Bu özellik belirtildiğinde, RetentionDuration ve RetentionType da belirtilmelidir. |
|RetentionDuration|Dize|Hayır, **RetentionAction** veya **RetentionType** belirtilmediği sürece|Bu özellik, içeriğin tutulacak gün sayısını belirtir. Geçerli değerler şunlardır: </br>**Sınırsız**: Öğeler süresiz olarak korunur. </br>**_n_*: Gün olarak pozitif bir tamsayı; örneğin, **365**. Desteklenen maksimum sayı 68 yıl olan 24.855'tir. Bu üst sınırdan daha uzun bir süreye ihtiyacınız varsa, bunun yerine Sınırsız'ı kullanın.</br> </br> Grup bağımlılıkları: Bu özellik belirtildiğinde, RetentionAction ve RetentionType da belirtilmelidir.
|RetentionType|Dize|Hayır, **RetentionAction** veya **RetentionDuration** belirtilmediği sürece|Bu özellik, bekletme süresinin (belirtildiyse) içerik oluşturma tarihi, olay tarihi, etiketlenme tarihi veya son değiştirme tarihinden hesaplanıp hesaplanmadığını belirtir. Geçerli değerler şunlardır: </br>**CreationAgeInDays**</br>**EventAgeInDays**</br>**TaggedAgeInDays**</br>**ModificationAgeInDays** </br> </br> Grup bağımlılıkları: Bu özellik belirtildiğinde RetentionAction ve RetentionDuraction da belirtilmelidir.|
|Gözden GeçirenE-posta|SmtpAddress|Hayır|Bu özellik belirtildiğinde, bekletme süresi dolduğunda bir değerlendirme gözden geçirmesi tetiklenir. Bu özellik **, Kiracınızda KeepAndDelete** bekletme eylemi için gözden geçirenin e-posta adresini belirtir. </br> </br> Kiracınıza tek tek kullanıcıların, dağıtım gruplarının veya güvenlik gruplarının e-posta adresini ekleyebilirsiniz. Birden çok e-posta adresini noktalı virgülle ayırarak belirtin. </br> </br> Grup bağımlılıkları: Bu özellik belirtildiğinde **RetentionAction** ( **KeepAndDelete**, **RetentionDuration** ve **RetentionType** da belirtilmelidir.|
|ReferenceId|Dize|Hayır|Bu özellik, kuruluşunuz için benzersiz bir değer olarak kullanabileceğiniz **Başvuru Kimliği** dosya planı tanımlayıcısında görüntülenen değeri belirtir.| 
|DepartmentName|Dize|Hayır|Bu özellik **, İşlev/departman** dosya planı tanımlayıcısında görüntülenen değeri belirtir.|
|Kategori|Dize|Hayır|Bu özellik **, Kategori** dosya planı tanımlayıcısında görüntülenen değeri belirtir.|
|Alt kategori|Dize|Hayır|Bu özellik **, Alt kategori** dosya planı tanımlayıcısında görüntülenen değeri belirtir.|
|AuthorityType|Dize|Hayır|Bu özellik **, Yetkili türü** dosya planı tanımlayıcısında görüntülenen değeri belirtir.|
|CitationName|Dize|Hayır|Bu özellik **, Sağlama/** alıntı dosya planı tanımlayıcısında görüntülenen alıntının adını belirtir. Örneğin, "Sarbanes-Oxley Act of 2002". |
|CitationUrl|Dize|Hayır|Bu özellik **, Sağlama/alıntı** dosya planı tanımlayıcısında görüntülenen URL'yi belirtir.|
|CitationJurisdiction|Dize|Hayır|Bu özellik **, Sağlama/alıntı** dosya planı tanımlayıcısında görüntülenen yargı yetkisini veya kuruluşu belirtir. Örneğin, "ABD Menkul Kıymetler ve Exchange Komisyonu (SEC)".|
|Düzenleyici|Dize|Hayır|Bu özellik, etiketin içeriği bir kayıttan [daha kısıtlayıcı](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) olan bir düzenleme kaydı olarak işaretleyip işaretlemediğini belirtir. Bu etiket yapılandırmasını kullanmak için kiracınızın [içeriği yasal kayıt olarak işaretleme seçeneğini görüntüleyecek şekilde yapılandırılması](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record) gerekir, aksi takdirde içeri aktarma doğrulaması başarısız olur. Geçerli değerler şunlardır: </br>**DOĞRU**: Etiket, öğeyi yasal kayıt olarak işaretler. **IsRecordLabel** özelliğini DE TRUE olarak ayarlamanız gerekir.</br>**YANLIŞ**: Etiket içeriği düzenleyici kayıt olarak işaretlemez. Bu, varsayılan değerdir.|
|Eventtype|Dize|**Hayır, RetentionType** **EventAgeInDays** değilse|Bu özellik, olay [tabanlı saklama](event-driven-retention.md) için kullanılan bir olay türünü belirtir. **Kayıt** **yönetimiEventsManage** >  >  olay türleri bölümünde görüntülenen mevcut **bir olay türünü** belirtin. Alternatif olarak, kullanılabilir olay türlerini görüntülemek için [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype) cmdlet'ini kullanın. **Çalışan etkinliği** ve **Ürün ömrü** gibi bazı yerleşik olay türleri olsa da, kendi olay türlerinizi de oluşturabilirsiniz. </br> </br> Kendi olay türünüzü belirtirseniz, ad içeri aktarma işleminin bir parçası olarak doğrulandığından içeri aktarma işleminden önce var olması gerekir.|

Şu anda içeri aktarma için desteklenmeyen etiket ayarları:

- Çok aşamalı değerlendirme: Bekletme etiketlerini bir şablonla içeri aktardığınızda tek bir değerlendirme gözden geçirme aşamasının ayarlarını yapılandırabilirsiniz ancak ek gözden geçirme aşamaları belirtemezsiniz. Bunun yerine, içeri aktarma başarılı olduktan sonra bunları uyumluluk portalında yapılandırın.

- Bu kaydın kilidini varsayılan olarak açın (şu anda önizleme aşamasında): Bu ayar şablonda içeri aktarılamaz ve içeri aktarma işlemi başarılı olduktan sonra uyumluluk portalında bu ayarı seçemezsiniz.

- Değiştirme etiketi (şu anda önizleme aşamasında): Bu ayar şablonda içeri aktarılamaz, ancak içeri aktarma işlemi başarılı olduktan sonra uyumluluk portalında bu ayarı seçebilirsiniz.


## <a name="next-steps"></a>Sonraki adımlar

Artık bekletme etiketleri oluşturdunuz, etiketleri yayımlayarak veya otomatik olarak uygulayarak öğelere eklenmeye hazırlar:
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)
