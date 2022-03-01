---
title: İçerik yaşam döngüsü boyunca bekletme etiketlerini yönetmek için dosya planı kullanma
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
search.appverid:
- MOE150
- MET150
ms.assetid: af398293-c69d-465e-a249-d74561552d30
description: Dosya planı, bekletme etiketleri için gelişmiş yönetim özellikleri sağlar.
ms.custom: seo-marvel-may2020
ms.openlocfilehash: 464cbe5af7ea08755ec3d49949d4707448566b27
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010840"
---
# <a name="use-file-plan-to-create-and-manage-retention-labels"></a>Bekletme etiketlerini oluşturmak ve yönetmek için dosya planını kullanma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

İlk e-postada Bilgi yönetiminden bekletme  etiketleri oluşturabiliyor Microsoft 365 uyumluluk merkezi, ancak Kayıt yönetiminden dosya planı **ek** yönetim özelliklerine sahiptir:

- Bir elektronik tablodan ilgili bilgileri içeri aktararak bekletme etiketlerini toplu olarak oluşturabilirsiniz.

- Çözümleme ve çevrimdışı işbirliği yapmak için var olan bekletme etiketlerinden bilgileri dışarı aktarabilirsiniz.

- Tüm bekletme etiketlerinizin ayarlarını tek bir görünümde görmenizi kolaylaştırmak için bekletme etiketleri hakkında daha fazla bilgi görüntülenir.

- Dosya planı tanımlayıcıları, her etiket için ek ve isteğe bağlı bilgileri destekler.

Dosya planı, içeriği kayıt olarak işaretlemeseler bile tüm bekletme etiketleri için kullanılabilir.

Bekletme etiketlerinin ne olduğu ve nasıl kullanılırları hakkında bilgi için bkz. Bekletme ilkeleri [ve bekletme etiketleri hakkında bilgi.](retention.md)

## <a name="accessing-file-plan"></a>Dosya planına erişme

Dosya planına erişmek için, aşağıdaki yönetici rollerinden biri gerekir:
    
- Bekletme Yöneticisi

- Yalnızca görüntüleme Bekletme Yöneticisi

Aşağıdaki Microsoft 365 uyumluluk merkezi **SolutionsRecords** >  **managementFile plan'a** >  **gidin**:

![Dosya planı sayfası](../media/compliance-file-plan.png). 

Gezinti **bölmesinde** Kayıt yönetimi görüntülenmezse, önce aşağı kaydırın ve Hepsini **göster'i seçin**.

## <a name="navigating-your-file-plan"></a>Dosya planında gezinme

İlk gün içinde Bilgi idaresi'ne göre **önceden bekletme** etiketleri oluşturdu Microsoft 365 uyumluluk merkezi, bu etiketler otomatik olarak dosya planınız içinde görüntülenir. 

Benzer şekilde, dosya planında artık bekletme etiketleri oluşturmanıza benzer şekilde, etiketler içeriği kayıt olarak  işaretlemek üzere yapılandırılmamışsa, Bilgi yönetimi tarafından da kullanılabilir.

Dosya **planı** sayfasında, etiketlerinizin durum ve ayarlarıyla birlikte tüm etiketlerinizi, isteğe bağlı dosya planı tanımlayıcılarını, etiketlerinizin çevrimdışı incelemelerini çözümlemeye veya etkinleştirmeye yönelik dışarı aktarma seçeneğini ve bekletme etiketleri oluşturma seçeneğini de görebilirsiniz. 

### <a name="label-settings-columns"></a>Etiket ayarları sütunları

Sütunları özelleştir **seçeneği seçerek** Ad etiketi dışındaki tüm sütunlar görüntülenebilir **veya gizlenir** . Ancak varsayılan olarak, ilk birkaç sütunda etiket durumu ve ayarlarıyla ilgili bilgiler görüntülenir: 

- **Durum**, etiketin bir etiket ilkesine mi yoksa otomatik uygulama ilkesine mi (**Etkin**) dahil olup olmadığını tanımlar. (Etkin **Değil)**

- **Bekletme döneminin** nasıl veya ne zaman başladığını tanımlar. Geçerli değerler:
    - Olay
    - Oluşturulduğunda
    - Son değiştirme
    - Etiketli olduğunda

- **Kayıt,** etiket uygulandığında öğenin kayıt olarak işaretlenirse bunu tanımlar. Geçerli değerler:
    - Hayır
    - Evet
    - Evet(Mevzuat)

- **Bekletme süresi** , bekletme süresini tanımlar. Geçerli değerler:
    - Gün
    - Ay
    - Yıl
    - Sonsuza kadar
    - Yok

- **Disposition type** , bekletme döneminin sonunda içeriğe ne olduğunu tanımlar. Geçerli değerler:
    - Eylem yok
    - Otomatik silme
    - İnceleme gerekli

### <a name="file-plan-descriptors-columns"></a>Dosya planı tanımlayıcıları sütunları

Dosya planı, bekletme etiketlerinizin bir parçası olarak daha fazla bilgi eklemenizi sağlar. Bu dosya planı tanımlayıcıları, etiketlemeniz gereken içeriğin yönetilebilirliğini ve kuruluşuni geliştirmek için daha fazla seçenek sağlar.

Varsayılan olarak, Başvuru **Kimliği'den** başlayarak, sonraki birkaç sütunda bekletme etiketi ekleyebilirsiniz veya var olan bir etiketi düzenlerken belirtebilirsiniz bu isteğe bağlı dosya planı tanımlayıcıları görüntülenir. 

Başlamanız için, aşağıdaki dosya planı tanımlayıcılarının bazı hazır değerleri vardır: 
- İş işlevi/bölümü
- Kategori
- Yetkili türü
- Sağlama/alıntı 

Bekletme etiketi ekleyebilirsiniz veya bu etiketi düzenlerken dosya planı tanımlayıcıları örneği:

![Bekletme etiketi ekleyebilirsiniz veya bu etiketi düzenlerken dosya planı tanımlayıcıları.](../media/file-plan-descriptors.png)

Bu **isteğe bağlı** tanımlayıcıların her biri için Seç'i seçerseniz, ilk hazır değerlerden birini seçebilir veya kendi tanımlayıcınızı oluşturabilir ve sonra da bunu seçebilirsiniz. Örneğin: 

![Sağlama/alıntı için yeni dosya planı tanımlayıcıları oluşturma.](../media/file-plan-descriptors-create.png)

## <a name="create-retention-labels"></a>Bekletme etiketleri oluşturma

1. Dosya planı **sayfasında +** Etiket **oluşturRetention etiketi'ne tıklayın**  > 

2. Yapılandırma işleminin yönergelerini izleyin.
    
    
    
    Kayıtları beyan etmek üzere bekletme etiketini kullanmak için **Öğeleri kayıt olarak** işaretle veya Öğeleri mevzuat kaydı **olarak işaretle'yi seçin**. Daha fazla bilgi için bkz [. Bekletme etiketlerini kayıtları bildir olacak şekilde yapılandırma](declare-records.md#configuring-retention-labels-to-declare-records).

3. Etiketi oluşturduktan ve etiketi yayımlama seçeneklerini gördüğünüzde, etiketi otomatik olarak uygulama veya yalnızca etiketi kaydetme: Yalnızca şimdilik kaydet'i ve sonra Bitti'yi **seçin**.

4. Daha fazla etiket oluşturmak için bu adımları yinele.

## <a name="edit-retention-labels"></a>Bekletme etiketlerini düzenleme

Mevcut bir bekletme etiketini düzenlemek için, Dosya Planı sayfasından  etiketi seçin ve ardından Etiket açıklamasını ve uygun  ayarları değiştirmenizi sağlayan Bekletmeyi düzenle işlemini başlatmak için Etiketi düzenle seçeneğini belirleyin.

Etiket oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez. Bu ayarlar şunlardır:
- Bekletme süresi dışında bekletme etiketi adı ve bekletme ayarları. Bununla birlikte, bekletme süresi öğelerin etiketli olduğu zamanların dayandır olduğu bekletme dönemini değiştiremezsiniz.
- Öğeleri kayıt olarak işaretleme seçeneği.

## <a name="delete-retention-labels"></a>Bekletme etiketlerini silme

Olay tabanlı bekletme için yapılandırılmamış, yayımlanmış veya otomatik olarak uygulama bekletme [](create-apply-retention-labels.md) etiketi ilkeleri [](apply-retention-labels-automatically.md) arasında yer alan bekletme etiketlerini silebilir veya öğeleri yasal düzenleme kayıtları olarak işaretebilirsiniz.

Öğelere uygulanmışsa silebilirsiniz bekletme etiketleri için silme işlemi başarısız olur ve etiketli öğeleri tanımlamak için içerik gezginine bir bağlantı elde edersiniz.

Bununla birlikte, içerik gezgininin etiketlenmiş öğeleri göstermesi iki gün kadar zaman alır. Bu senaryoda, bekletme etiketi içerik gezgininin bağlantısını göstermeden silinebilir.

## <a name="export-all-retention-labels-to-analyze-or-enable-offline-reviews"></a>Çevrimdışı incelemeleri çözümlemek veya etkinleştirmek için tüm bekletme etiketlerini dışarı aktarma

Dosya planınızdan, tüm bekletme etiketlerinin ayrıntılarını bir .csv dosyasına aktararak, düzenli olarak uyumluluk incelemelerini kurum içinde veri yönetimi katılımcıları ile kolaylaştırabilirsiniz.

Tüm bekletme etiketlerini dışarı aktarma: Dosya **planı sayfasında Dışarı Aktar'a** **tıklayın**:

![Dosya planı dışarı aktarma seçeneği.](../media/compliance-file-plan-export-labels.png)

Var .csv bekletme etiketlerini içeren bir *dosya açılır. Örneğin:

![Tüm bekletme etiketlerini gösteren CSV dosyası.](../media/file-plan-csv-file.png)

## <a name="import-retention-labels-into-your-file-plan"></a>Bekletme etiketlerini dosya planınıza aktarma

Dosya planında, belirli bir biçime sahip bir .csv kullanarak yeni bekletme etiketlerini toplu olarak içeri aktarabilirsiniz: 

1. Dosya planı **sayfasında İçeri** Aktar: ![Dosya **planı içeri** aktarma seçeneği'ne tıklayın](../media/compliance-file-plan-import-labels.png)

2. Dosya **planınızı doldur ve içeri aktar bölmesinde** Boş şablon **indir'i seçin**:

   ![Boş bir dosya planı şablonu indirme seçeneği](../media/file-plan-blank-template-option.png)

3. Şablon indirildikten sonra, her etiket için bir satır ekleyin ve dosyayı kaydedin. Her [özelliğin](#information-about-the-label-properties-for-import) özelliklerini ve geçerli değerlerini açıklayan bilgiler için bir sonraki bölüme bakın.
    
    Dolu şablon örneği:
    
    ![Bilgileri doldurulmuş dosya planı şablonu.](../media/file-plan-filled-out-template.png)

4. **Doldurulan Upload karşıya** yüklemek için Dosya Seç'i seçin.
    
   Dosya planı dosyayı karşıya yükler ve girişleri doğrular.

5. Doğrulama sonuçlarına bağlı olarak:
    
    - Doğrulama başarısız olursa: İçeri aktarma dosyasında düzeltilmiş satır numarasına ve sütun adına dikkat edin. Dosyada hataları düzeltin ve kaydedin ve sonra 4. adımı yinelayın.
    
    - Doğrulama başarılı olursa: Bir dosya **planını başarıyla aktardınız** ve girişler bekletme etiketlerine başarıyla dönüştürülecek. **Bölmeyi** kapatmak ve yeni etiketlerinizi görüntülemek için **Dosya planı sayfasını otomatik** olarak yenilemek için Bitti'yi seçin.

Artık yeni bekletme etiketlerinizi yayımlar veya bunları otomatik olarak uygulayabilirsiniz. Etiketleri yayımla'yı **veya Etiketi** otomatik uygula'yı **seçerek** her ikisini de Etiket ilkeleri **sekmesinden de uygulayabilirsiniz**.

### <a name="information-about-the-label-properties-for-import"></a>İçeri aktarma için etiket özellikleri hakkında bilgi

İndirilen şablonu yeni bekletme etiketlerini içeri aktarmaya yardımcı olmak için aşağıdaki bilgileri kullanın. Bazı değerlerin içeri aktarma için uzunluk üst uzunluğu vardır:

- **LabelName**: En fazla 64 karakter uzunluğunda
- **Açıklama** ve **Notlar**: En fazla 1024 karakter uzunluğunda
- Diğer tüm değerler: Sınırsız uzunluk
<br/>

|Özellik|Tür|Gerekli|Geçerli değerler|
|:-----|:-----|:-----|:-----|
|LabelName|Dize|Evet|Bu özellik bekletme etiketinin adını belirtir ve kiracınıza benzersiz olması gerekir. İçeri aktarmada desteklenen karakterler: a-z, A-Z, 0-9, kısa çizgi (-) ve boşluk karakteri.|
|Açıklama ekleme|Dize|Hayır|Yöneticilere bekletme etiketi hakkında bir açıklama eklemek için bu özelliği kullanın. Bu açıklama yalnızca uyumluluk merkezinde bekletme etiketini yöneten yöneticilere görünür.|
|Notlar|Dize|Hayır|Kullanıcılara bekletme etiketiyle ilgili bir açıklama eklemek için bu özelliği kullanın. Bu açıklama, kullanıcılar etiket, etiket ve etiket etiketleri gibi Outlook SharePoint üzerine geldiğinde OneDrive. Bu özelliği boş bırakırsanız, bir varsayılan açıklama görüntülenir ve bu açıklama etiketin bekletme ayarlarını açıklar. |
|IsRecordLabel|Dize|Hayır, Mevzuat **DOĞRU** olmadığı **sürece**|Bu özellik, etiketin içeriği kayıt olarak işaret edip edip olmadığını belirtir. Geçerli değerler: </br>**DOĞRU**: Etiket öğeyi kayıt olarak işaretler ve bunun sonucunda öğe silinemez. </br>**YANLIŞ**: Etiket, içeriği kayıt olarak işaretlemez. Bu, varsayılan değerdir. </br> </br> Grup bağımlılıkları: Bu özellik belirtilirken, retentionaction, retentionDuration ve retentionType da belirtilmelidir.|
|RetentionAction|Dize|Hayır, **RetentionDuration**, **RetentionType** veya **Gözden GeçirenEmail belirtilmemişse**|Bu özellik, retentionDuration özelliği tarafından belirtilen değerin süresi dolduktan (belirtilirse) sonra hangi eylemin geçerli olaralları belirtmektedir. Geçerli değerler: </br>**Sil**: RetentionDuration özelliğinde belirtilen değerden daha eski öğeler silinir.</br>**Saklama**: BekletmeDuration özelliği tarafından belirtilen süre boyunca öğeleri alıkoyun ve süre süresi dolduğunda hiçbir şey yapma. </br>**KeepAndDelete**: BekletmeDuration özelliğiyle belirtilen süre boyunca öğeleri alıkoyun ve sürenin süresi dolduğunda bunları silin. </br> </br> Grup bağımlılıkları: Bu özellik belirtilirken, retentionDuration ve retentionType da belirtilmelidir. |
|retentionDuration|Dize|Hayır, **retentionAction veya** **retentionType belirtilmemişse**|Bu özellik, içeriğin korunacak gün sayısını belirtir. Geçerli değerler: </br>**Sınırsız**: Öğeler süresiz olarak korunur. </br>**_n_*: Günlere pozitif bir tamsayı; örneğin, **365**. Desteklenen en fazla sayı 24.855'tir ve bu da 68 yıldır. Bu üst değerden daha uzun süreye ihtiyacınız varsa, bunun yerine Sınırsız kullanın.</br> </br> Grup bağımlılıkları: Bu özellik belirtilirken, RetentionAction ve RetentionType da belirtilmelidir.
|retentionType|Dize|Hayır, **BekletmeAction veya** **BekletmeDuration belirtilmemişse**|Bu özellik, bekletme süresinin (belirtilirse) içerik oluşturma tarihi, olay tarihi, etiket tarihi veya son değiştirme tarihinden hesaplanarak hesaplanma süresinin belirtilmez. Geçerli değerler: </br>**CreationAgeInDays**</br>**EventAgeInDays**</br>**TaggedAgeInDays**</br>**ModificationAgeInDays** </br> </br> Grup bağımlılıkları: Bu özellik belirtilirken, RetentionAction ve RetentionDuraction da belirtilmelidir.|
|Gözden GeçirenEmail|SmtpAddress|Hayır|Bu özellik belirtilirse, bekletme süresi sona erdiğinde bir konumlandırma gözden geçirmesi tetiklenir. Bu özellik **KeepAndDelete** bekletme eylemi için kiracınıza gözden geçirenin e-posta adresini belirtir. </br> </br> Kiracınıza tek tek kullanıcıların, dağıtım gruplarının veya güvenlik gruplarının e-posta adresini ebilirsiniz. Birden çok e-posta adresini noktalı virgülle ayırarak belirtin. </br> </br> Grup bağımlılıkları: Bu özellik belirtilirken, **RetentionAction** ( **KeepAndDelete** olmalı), **RetentionDuration** ve **RetentionType** da belirtilmelidir.|
|ReferenceId|Dize|Hayır|Bu özellik, benzersiz bir değer olarak kullanabileceğiniz Başvuru Kimliği dosya  planı tanımlayıcısını görüntülenen değeri belirtir.| 
|DepartmentName|Dize|Hayır|Bu özellik, İşlev/bölüm dosya planı **tanımlayıcıda görüntülenen** değeri belirtir.|
|Kategori|Dize|Hayır|Bu özellik, Kategori dosya planı tanımlayıcıda **görüntülenen** değeri belirtir.|
|Alt Kategori|Dize|Hayır|Bu özellik, Alt kategori dosya planı tanımlayıcıda **görüntülenen** değeri belirtir.|
|AuthorityType|Dize|Hayır|Bu özellik, Yetkili türü dosya planı tanımlayıcısını **görüntülenen** değeri belirtir.|
|CitationName|Dize|Hayır|Bu özellik, Sağlama/alıntı dosyası plan tanımlayıcılarında **görüntülenen alıntının** adını belirtir. Örneğin, "Sarbanes-Oxley Act of 2002". |
|CitationUrl|Dize|Hayır|Bu özellik, Sağlama/alıntı dosya planı tanımlayıcıda **görüntülenen** URL'yi belirtir.|
|CitationJurisdiction|Dize|Hayır|Bu özellik, Sağlama/alıntı dosyası planı tanımlayıcı alanında **görüntülenen yargı yetkisini veya** daireyi belirtir. Örneğin, "U.S. Securities and Exchange Commission (SEC)".|
|Mevzuat|Dize|Hayır|Bu özellik, etiketin bir kayıttan daha kısıtlayıcı olan bir yasal düzenleme kaydı [olarak işaret edip](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) olmadığını belirtir. Bu etiket yapılandırmasını kullanmak için kiracının içeriği yasal düzenleme kaydı olarak işaretleme seçeneğini görüntüecek şekilde yapılandırılması [gerekir, yoksa](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record) içeri aktarma doğrulaması başarısız olur. Geçerli değerler: </br>**DOĞRU**: Etiket, öğeyi bir yasal düzenleme kaydı olarak işaretler. **IsRecordLabel özelliğini TRUE olarak** da ayarlayabilirsiniz.</br>**YANLIŞ**: Etiket, içeriği bir yasal düzenleme kaydı olarak işaretlemez. Bu, varsayılan değerdir.|
|EventType|Dize|Hayır, **retentionType** **EventAgeInDays olmadığı sürece**|Bu özellik, olay tabanlı bekletme için kullanılan [olay türünü belirtir](event-driven-retention.md). Kayıt **yönetimiEventsManage** olay **türleri'nin içinde** >  gösterilen mevcut  > **bir olay türünü belirtin**. Alternatif olarak, kullanılabilir olay [türlerini görüntülemek için Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype) cmdlet'ini kullanın. Çalışan etkinliği ve Ürün yaşam süresi gibi bazı yerleşik etkinlik türleri olsa  **da kendi etkinlik** türlerinizi de oluşturabilirsiniz. </br> </br> Kendi olay türlerinizi belirtirsiniz, ad içeri aktarma işleminin bir parçası olarak doğrulanır ve içeri aktarma öncesinde var olması gerekir.|
|||

## <a name="next-steps"></a>Sonraki adımlar

Artık bekletme etiketleri oluşturduktan sonra, bunlar etiketleri yayımarak veya otomatik olarak uygulayarak öğelere eklenmeye hazırdır:
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)