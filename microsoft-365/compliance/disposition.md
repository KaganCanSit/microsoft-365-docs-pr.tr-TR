---
title: İçeriğin konumu
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
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Bir değerlendirme gözden geçirmesi kullandığınızda veya kayıt olarak işaretlenen öğeler yapılandırdığınız ayarlara göre otomatik olarak silinirken içerik elden çıkarma işlemini izleyin ve yönetin.
ms.openlocfilehash: 34ac1a9d3b62cd0806318582f7baef76947d7670
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463274"
---
# <a name="disposition-of-content"></a>İçeriğin konumu

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı **Kayıt Yönetimi'ndeki** **Ayrıştırma** sayfasını kullanarak değerlendirme gözden geçirmelerini yönetin ve saklama döneminin sonunda otomatik olarak silinen [kayıtların](records-management.md#records) meta verilerini görüntüleyin.

## <a name="prerequisites-for-viewing-content-dispositions"></a>İçerik eğilimlerini görüntüleme önkoşulları

Değerlendirme gözden geçirmelerini yönetmek ve kayıtların silindiğini onaylamak için yeterli izinlere sahip olmanız ve denetimin etkinleştirilmesi gerekir. Ayrıca, [edatla ilgili sınırlamaları](retention-limits.md#maximum-number-of-items-for-disposition) da unutmayın.

### <a name="permissions-for-disposition"></a>Değerlendirme izinleri

Microsoft Purview uyumluluk portalı'daki **Disposition** sekmesine başarıyla erişmek için kullanıcıların **Disposition Management** rolüne sahip olması gerekir. Aralık 2020'den itibaren bu rol artık **Kayıt Yönetimi** varsayılan rol grubuna dahil edilir.

> [!NOTE]
> Varsayılan olarak genel yöneticiye **Disposition Management** rolü verilmez. 

Kullanıcılara, bekletme ve kayıt yönetimi için diğer özellikleri görüntüleme ve yapılandırma izinleri vermeden yalnızca ayrıştırma gözden geçirmeleri için gereken izinleri vermek için, özel bir rol grubu oluşturun (örneğin, "Değerlendirmeyi Gözden Geçirenler" olarak adlandırılır) ve bu gruba **Disposition Management** rolünü verin.

Varsayılan rollere kullanıcı ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için bkz. [Microsoft Purview uyumluluk portalı izinler](microsoft-365-compliance-center-permissions.md).

Ayrıca:

- Değerlendirme işlemi sırasında öğelerin içeriğini görüntülemek için, kullanıcıları **İçerik Gezgini İçerik Görüntüleyicisi** rol grubuna ekleyin. Kullanıcılar bu rol grubundan izinlere sahip değilse, değerlendirme gözden geçirmesini tamamlamak için yine de bir değerlendirme gözden geçirme eylemi seçebilirler, ancak bunu Microsoft Purview uyumluluk portalı mini önizleme bölmesinden öğenin içeriğini görüntüleyemeden yapmalıdır.

- Varsayılan olarak, **Disposition** sayfasına erişen her kişi yalnızca gözden geçirmek üzere atanan öğeleri görür. Kayıt yönetimi yöneticisinin tüm kullanıcılara atanan tüm öğeleri ve edat için yapılandırılmış tüm bekletme etiketlerini görebilmesi için gözden geçirme: **Kayıt yönetimi ayarlarıEşit'e** >  **gidip** yönetici hesaplarını içeren posta özellikli bir güvenlik grubu seçin ve etkinleştirin.
    
    posta etkin olmayan Microsoft 365 grupları ve güvenlik grupları bu özelliği desteklemez ve seçmek için listede görüntülenmez. Posta özellikli yeni bir güvenlik grubu oluşturmanız gerekiyorsa, yeni grubu oluşturmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> bağlantısını kullanın. 
    
    > [!IMPORTANT]
    > Grubu etkinleştirdikten sonra Microsoft Purview uyumluluk portalı değiştiremezsiniz. PowerShell kullanarak farklı bir grubu etkinleştirme hakkında bilgi için sonraki bölüme bakın.

- **Kayıt yönetimi ayarları** seçeneği yalnızca kayıt yönetimi yöneticileri tarafından görülebilir. 

#### <a name="enabling-another-security-group-for-disposition"></a>Başka bir güvenlik grubunu ayrıştırma için etkinleştirme

Microsoft Purview uyumluluk portalı **Kayıt yönetimi ayarlarından** bir güvenlik grubunu kullanıma açmak üzere etkinleştirdikten sonra, grup için bu izni devre dışı bırakamaz veya Microsoft Purview uyumluluk portalı seçili grubu değiştiremezsiniz. Ancak [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) cmdlet'ini kullanarak başka bir posta özellikli güvenlik grubunu etkinleştirebilirsiniz.

Örneğin: 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Denetimi etkinleştirme

İlk değerlendirme eyleminden en az bir gün önce denetimin etkinleştirildiğinden emin olun. Daha fazla bilgi için bkz[. Microsoft Purview uyumluluk portalı denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma. 

## <a name="disposition-reviews"></a>Değerlendirme değerlendirmeleri

İçerik saklama süresinin sonuna ulaştığında, bu içeriği gözden geçirmek ve kalıcı olarak silinip silinemeyeceğini ("atılmış") onaylamak istemenizin çeşitli nedenleri vardır. Örneğin, içeriği silmek yerine şunları yapmanız gerekebilir:
  
- Dava veya denetim için ilgili içeriğin silinmesini askıya alın.

- özgün saklama ayarları geçici veya geçici bir çözüm olduğundan içeriğe farklı bir saklama süresi atayın.

- İçeriği var olan konumundan arşiv konumuna (örneğin, bu içeriğin araştırma veya geçmiş değeri varsa) taşıyın.

Bekletme süresinin sonunda bir değerlendirme gözden geçirmesi tetiklendiğinde, seçtiğiniz gözden geçirenler gözden geçirebilecekleri içeriğe sahip olduklarına dair bir e-posta bildirimi alır. Bu gözden geçirenler tek tek kullanıcılar veya posta özellikli güvenlik grupları olabilir.

Gözden geçirenlerin aldığı bildirim e-postasını, farklı dillerde yönergeler de dahil olmak üzere özelleştirebilirsiniz. Çok dilli destek için çevirileri kendiniz belirtmeniz gerekir ve bu özel metin yerel ayarlarına bakılmadan tüm gözden geçirenlere görüntülenir.

Kullanıcılar, öğenin saklama süresinin sonunda etiket başına bir ilk e-posta bildirimi alır ve bunların atandığı tüm değerlendirmelerin haftada bir etiket başına anımsatıcısı olur. İçeriği gözden geçirmek ve eyleme geçmek için bildirim ve anımsatıcı e-postalarındaki bağlantıya tıklayarak doğrudan Microsoft Purview uyumluluk portalı **Kayıtlar yönetimiDisposition** >  sayfasına gidebilirler. Alternatif olarak, gözden geçirenler Microsoft Purview uyumluluk portalı bu **Değerlendirme** sayfasına gidebilir. Sonra:

- Gözden geçirenler yalnızca kendilerine atanan değerlendirme gözden geçirmelerini görürken, kayıt yöneticisi için seçilen güvenlik grubuna eklenen yöneticiler tüm değerlendirme gözden geçirmelerini görür.

- Gözden geçirenler, aynı değerlendirme gözden geçirmesine yeni kullanıcılar ekleyebilir. Bu eylemin bu eklenen kullanıcılara [gerekli izinleri](#permissions-for-disposition) otomatik olarak vermediğini unutmayın.

- Değerlendirme gözden geçirme işlemi için, her öğe için bir mini gözden geçirme bölmesi, içeriği görme izinleri varsa içeriğin önizlemesini gösterir. İzinleri yoksa içerik bağlantısını seçip izin isteyebilirler. Bu mini gözden geçirme bölmesinde içerik hakkında ek bilgi için sekmeler de vardır:
   - Dizine alınan özellikleri, bulunduğu yeri, onu kimin, ne zaman ve en son kimin değiştirdiği ve ne zaman görüntüleyeceğinize ilişkin **ayrıntılar**.
   - Herhangi bir değerlendirme gözden geçirme eylemlerinin geçmişini ve varsa gözden geçiren açıklamalarını gösteren **geçmiş**.

Bir değerlendirme, Exchange posta kutularına, SharePoint sitelere ve OneDrive hesaplarına içerik içerebilir. Bu konumlarda bir değerlendirme gözden geçirmesi bekleyen içerik kalıcı olarak silinir, ancak değerlendirmenin son aşaması için gözden geçiren içeriği kalıcı olarak silmeyi seçtikten sonra silinir.

> [!NOTE]
> Bir posta kutusu, değerlendirme incelemelerini desteklemek için en az 10 MB veriye sahip olmalıdır.

Yöneticiler, **Genel Bakış** sekmesinde bekleyen tüm eğilimlere genel bir bakış görebilir. Gözden geçirenler yalnızca beklemede olan öğelerini görür. Örneğin:

![Kayıt yönetimine genel bakış bölümünde bekleyen konumlar.](../media/dispositions-overview.png)

**Bekleyen tüm değerlendirmeleri görüntüle'yi** seçtiğinizde, **Değerlendirme** sayfasına yönlendirilirsiniz. Örneğin:

![Microsoft Purview uyumluluk portalı'daki Dispositions sayfası.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Değerlendirme gözden geçirmesi için iş akışı

Aşağıdaki diyagramda, bekletme etiketi yayımlandığında ve ardından kullanıcı tarafından el ile uygulandığında bir değerlendirme gözden geçirmesinin (tek aşamalı) temel iş akışı gösterilmektedir. Alternatif olarak, bir değerlendirme gözden geçirmesi için yapılandırılmış bir bekletme etiketi içeriğe otomatik olarak uygulanabilir.
  
![Eğilimin nasıl çalıştığını gösteren grafik.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Değerlendirme gözden geçirmesi için bekletme etiketi yapılandırma

Bekletme süresinin sonunda bir değerlendirme gözden geçirmesinin tetiklenmesi, yalnızca bekletme etiketiyle kullanılabilen bir yapılandırma seçeneğidir. Bekletme ilkesi için değerlendirme gözden geçirmesi kullanılamaz. Bu iki bekletme çözümü hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

Bekletme etiketi için **bekletme süresinden sonra ne olacağını seçin** sayfasından:

![Etiket için bekletme ayarları.](../media/disposition-review-option.png)
 
**Değerlendirme gözden geçirmesi başlat** seçeneğini seçtikten sonra **+ Aşama oluştur'u seçin ve gözden geçirenleri atayın**. Yapılandırmanın sonraki sayfasında, kaç ardışık değerlendirme aşaması istediğinizi ve her aşama için değerlendirme gözden geçirenlerini belirteceksiniz:

![Değerlendirme gözden geçirenlerini belirtme.](../media/disposition-reviewers.png) 

**+ Aşama ekle'yi** seçin ve aşamanızı tanımlama amacıyla adlandırınız. Ardından bu aşama için gözden geçirenleri belirtin.

Gözden geçirenler için en fazla 10 bireysel kullanıcı veya posta etkin güvenlik grubu belirtin. Microsoft 365 grupları ([eski adıyla Office 365 grupları](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) bu seçenek için desteklenmez.

Saklama süresinin sonunda bir öğeyi gözden geçirmek için birden fazla kişiye ihtiyacınız varsa **, Başka bir aşama ekle'yi** seçin ve yapılandırma işlemini ihtiyacınız olan aşama sayısı için en fazla beş aşama olacak şekilde yineleyin. 

Ayrı ayrı her bir değerlendirme aşamasında, bu aşama için belirttiğiniz kullanıcılardan herhangi biri, saklama süresinin sonunda öğe için bir sonraki eylemi gerçekleştirme yetkisine sahiptir. Bu kullanıcılar, başka kullanıcıları da değerlendirme aşamalarına ekleyebilir.

> [!NOTE]
> Çok aşamalı değerlendirme kullanılabilir olmadan önce bekletme etiketlerini yapılandırdıysanız, etiketlerinizi şu özelliği destekleyecek şekilde yükseltebilirsiniz: Etiketi düzenleyin ve **Bekletme döneminden sonra ne olacağını seçin** sayfasında **Aşamaları ve gözden geçirenleri düzenle'yi** seçin.

Yapılandırma aşaması sırasında, belirtilen her aşama için yeniden adlandırabilir, yeniden sıralayabilir veya Şimdi bir **değerlendirme gözden geçirmesi başlat** seçeneği için görüntülenen **Aşamaları ve gözden geçirenleri düzenle'yi** seçerek kaldırabilirsiniz. Ardından her aşama için Aşama eylemleri seçeneğini (**...**) belirleyebilirsiniz: 

![Değerlendirme gözden geçirmeleri için eylemleri hazırlama.](../media/stage-actions-disposition-review.png)

Ancak bekletme etiketini oluşturduktan sonra aşamayı yeniden sıralayamaz veya kaldıramazsınız. Yalnızca **Aşama ekle ve Aşamayı** **yeniden adlandır** seçeneklerini görürsünüz. Gözden geçirenleri düzenlemeye devam edebilirsiniz.

Gözden geçirenlerinizi belirttikten sonra, onlara **Disposition Management** rol iznini vermeyi unutmayın. Daha fazla bilgi için bu sayfadaki [Disposition izinleri](#permissions-for-disposition) bölümüne bakın.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>E-posta iletilerini değerlendirme için özelleştirme

Gözden geçirene gönderilen örnek varsayılan e-posta bildirimi:

![Bir öğe değerlendirme gözden geçirmeye hazır olduğunda varsayılan metin içeren e-posta bildirimi örneği.](../media/disposition-review-email.png)

İlk bildirim ve ardından anımsatıcılar için değerlendirme gözden geçirenlere gönderilen e-posta iletilerini özelleştirebilirsiniz.

Microsoft Purview uyumluluk portalı kayıt yönetimi sayfalarından herhangi birinden **Kayıt yönetimi ayarları'nı** seçin:  

![Kayıt yönetimi ayarları.](../media/record-management-settings.png)

**Değerlendirme** sekmesindeki **Değerlendirme gözden geçirmeleri için e-posta bildirimleri** bölümünde, yalnızca varsayılan e-posta iletisini kullanmak isteyip istemediğinizi seçin ve belirtin veya varsayılan iletiye kendi metninizi ekleyin. Özel metniniz, bekletme etiketi hakkındaki bilgilerin ardından ve sonraki adım yönergelerinden önce e-posta yönergelerine eklenir.

Tüm diller için metin eklenebilir, ancak biçimlendirme ve resimler desteklenmez. URL'ler ve e-posta adresleri metin olarak girilebilir ve e-posta istemcisine bağlı olarak, özelleştirilmiş e-postada köprü veya biçimlendirilmemiş metin olarak görüntülenebilir.

Eklenecek örnek metin:

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Değişiklikleri kaydetmek için **Kaydet'i** seçin.

### <a name="viewing-and-disposing-of-content"></a>İçeriği görüntüleme ve yok etme

Bir gözden geçirene içeriğin gözden geçirilmeye hazır olduğu e-postayla bildirildiğinde, e-postadaki bir bağlantıya tıklayarak doğrudan Microsoft Purview uyumluluk portalı **Kayıt yönetimi'ndeki** **Disposition** sayfasına gidebilir. Burada gözden geçirenler, **Tür'de** **Bekleyen değerlendirme** görüntülendiğinde her bekletme etiketi için kaç öğenin değerlendirmeyi beklediğini görebilir. Ardından bir bekletme etiketi seçer ve bu etikete sahip tüm içeriği görmek için **Yeni pencerede aç'ı** seçer:

![Değerlendirme gözden geçirmesi için yeni pencerede açın.](../media/open-in-new-window.png)

**Bekleyen değerlendirmeler** sayfasında, bu etiket için bekleyen tüm eğilimleri görürler. Bir veya daha fazla öğe seçildiğinde, üzerinde işlem yapmadan önce içeriği incelemek için mini önizleme bölmesini ve **Kaynak**, **Ayrıntılar** ve **Geçmiş** sekmesini kullanabilirler:

![Değerlendirme seçenekleri.](../media/retention-disposition-options.png)

Yatay kaydırma çubuğunu kullanırsanız veya min-review bölmesini kapatırsanız, sona erme tarihini ve değerlendirme gözden geçirme aşamasının adını içeren daha fazla sütun görürsünüz.

Gösterilen örnekte görebileceğiniz gibi desteklenen eylemler şunlardır: 
  
- **Elden çıkarmayı onayla**:
    - Bu eylem, bir değerlendirme gözden geçirmesinin geçici aşaması için seçildiğinde (birden çok aşama yapılandırdıysanız): Öğe bir sonraki değerlendirme aşamasına geçer.
    - Bu eylem, değerlendirme gözden geçirmesinin son aşaması için seçildiğinde veya yalnızca bir değerlendirme aşaması varsa: Öğe kalıcı silme için uygun olarak işaretlenir ve bu süreölçer işi 7 gün içinde gerçekleştirilen eylemlerdir. Öğenin kalıcı olarak silinecek tam zamanlaması iş yüküne bağlıdır. Daha fazla bilgi için bkz[. SharePoint ve OneDrive için bekletme nasıl çalışır](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive) ve [Exchange için bekletme nasıl çalışır](retention-policies-exchange.md#how-retention-works-for-exchange)?

- **Yeniden etiketleme**:
    - Bu eylem seçildiğinde, öğe özgün etiket için değerlendirme gözden geçirme işleminden çıkar. Daha sonra öğe, yeni seçilen bekletme etiketinin bekletme ayarlarına tabidir.

- **Genişlet**:
    - Bu eylem seçildiğinde, değerlendirme gözden geçirmesi uzun sürenin sonuna kadar etkin bir şekilde askıya alınır ve ardından ilk aşamadan itibaren değerlendirme gözden geçirmesi yeniden tetiklenir.

- **Gözden geçirenleri ekleyin**:
    - Bu eylem seçildiğinde, kullanıcıdan gözden geçirilecek diğer kullanıcıları belirtmesi ve eklemesi istenir.
    > [!NOTE]
    > Bu eylem, eklenen kullanıcılara [otomatik olarak gerekli izinleri](#permissions-for-disposition) vermez. Bu izinlere sahip değilse, değerlendirme gözden geçirmesine katılamaz.

Gerçekleştirilen her eylemin [, Disposition gözden geçirme etkinlikleri denetim etkinlikleri](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) grubunda karşılık gelen bir denetim olayı vardır.

Bir değerlendirme gözden geçirmesi sırasında içerik hiçbir zaman özgün konumundan taşınmaz ve bu eylem son veya yalnızca değerlendirme aşaması için gözden geçiren tarafından seçilene kadar kalıcı silme için işaretlenmez.

## <a name="disposition-of-records"></a>Kayıtların konumu

**Kayıt yönetimi** ana sayfasından > **Eğilimi** sekmesinde şunları tanımlayabilirsiniz:

- Bir değerlendirme gözden geçirmesi sonucunda silinen öğeler.
- Kayıt veya mevzuat kaydı olarak işaretlenen ve saklama sürelerinin sonunda otomatik olarak silinen öğeler.

Bu öğeler **Tür** sütununda **Atılan Kayıtları** görüntüler. Örneğin:

![Değerlendirme gözden geçirmesi yapılmadan atılan öğeler.](../media/records-disposed2.png)

> [!NOTE]
> Bu işlev [birleşik denetim günlüğündeki](search-the-audit-log-in-security-and-compliance.md) bilgileri kullanır ve bu nedenle ilgili olayların yakalanması için denetimin [etkinleştirilmesini ve aranabilir olmasını](turn-audit-log-search-on-or-off.md) gerektirir.

Kayıt veya mevzuat kaydı olarak işaretlenmiş silinmiş öğelerin denetimi için Dosya **ve sayfa etkinlikleri** kategorisinde **kayıt olarak işaretlenmiş Silinmiş dosya** için arama yapın. Bu denetim olayı belgeler ve e-postalar için geçerlidir.

## <a name="filter-and-export-the-views"></a>Görünümleri filtreleme ve dışarı aktarma

**Değerlendirme** sayfasından bir bekletme etiketi seçtiğinizde, **Bekleyen değerlendirme** sekmesi (varsa) ve **Atılan öğeler** sekmesi, öğeleri daha kolay bulmanıza yardımcı olmak için görünümleri filtrelemenize olanak sağlar.

Bekleyen eğilimler için zaman aralığı son kullanma tarihine göre belirlenir. Atılan öğeler için zaman aralığı silme tarihine göre belirlenir.
  
Öğelerle ilgili bilgileri her iki görünümde de .csv dosyası olarak dışarı aktarabilir ve Excel kullanarak sıralayabilir ve yönetebilirsiniz.
