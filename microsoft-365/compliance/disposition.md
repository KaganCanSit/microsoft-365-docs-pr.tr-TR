---
title: İçeriğin yok olanı
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
description: Bir imha gözden geçirmesi kullanırken içeriğin silinmesini izleme ve yönetme veya kayıt olarak işaretlenen öğeler, yapılandırılan ayarlara göre otomatik olarak silinir.
ms.openlocfilehash: dbc713c665367bb973fb8faded24015ad6c2d5c3
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594828"
---
# <a name="disposition-of-content"></a>İçeriğin yok olanı

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Kayıt **Yönetimi'nin Disposition** sayfasını kullanarak Microsoft 365 uyumluluk merkezi incelemelerini yönetin ve bekletme sürelerinin sonunda otomatik olarak silinen kayıtların meta verilerini [](records-management.md#records) görüntüleyebilirsiniz.

## <a name="prerequisites-for-viewing-content-dispositions"></a>İçerik dispositionlarını görüntülemenin önkoşulları

Yoklama incelemelerini yönetmek ve kayıtların silinmiş olduğunu onaylamak için, yeterli izinlere sahip olmak ve denetimin etkinleştirilmesi gerekir. Ayrıca, yok olacak her [türlü sınırlamaya](retention-limits.md#maximum-number-of-items-for-disposition) da dikkat edin.

### <a name="permissions-for-disposition"></a>Yok olmak için izinler

Metinde **Disposition sekmesine** başarıyla Microsoft 365 uyumluluk merkezi, kullanıcıların **Disposition Management rolüne sahip olması** gerekir. Aralık 2020'den itibaren bu rol artık Kayıt Yönetimi varsayılan **rol grubuna** dahil edilecektir.

> [!NOTE]
> Varsayılan olarak, genel yöneticiye **Disposition Management rolü verilmez** . 

Bekletme ve kayıt yönetimiyle ilgili diğer özellikleri görüntüleme ve yapılandırma izinleri vermeden kullanıcılara yalnızca, inceleme incelemeleri için gereken izinleri vermek için, özel bir rol grubu oluşturun (örneğin, "Disposition Reviewers" olarak adlandırılır) ve bu gruba **Disposition Management rolü** verin.

Kullanıcıları varsayılan rollere ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için [bkz. Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md).

Ayrıca:

- Yokma işlemi sırasında öğelerin içeriğini görüntülemek için, İçerik Gezgini İçerik **Görüntüleyicisi rol grubuna kullanıcı** ekleyin. Kullanıcılar bu rol grubundan izinlere sahip değilse, yine de konumlandırma incelemesini tamamlamak için bir konumlandırma gözden geçirme eylemi seçseler de, uyumluluk merkezinde mini önizleme bölmesinde öğenin içeriğini görüntüleyemeden bunu yapmaları gerekir.

- Varsayılan olarak, **Disposition sayfasına erişen** herkes yalnızca gözden geçirmek için atandığı öğeleri görür. Kayıt yönetimi yöneticisinin tüm kullanıcılara atanan tüm öğeleri ve yok etmek üzere yapılandırılmış tüm bekletme etiketlerini görmeleri için:  >  Kayıt yönetimi ayarlarıDisposition seçeneğine gidin ve yönetici hesaplarını içeren posta özellikli bir güvenlik grubunu seçin ve etkinleştirin.
    
    Microsoft 365 etkin olmayan grup ve güvenlik grupları bu özelliği desteklemez ve seçmek için listede görüntülenmez. Posta özelliği etkin yeni bir güvenlik grubu oluşturmanız gerekirse, posta <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi bağlantısını kullanarak</a> yeni grubu oluşturun. 
    
    > [!IMPORTANT]
    > Grubu etkinleştirdikten sonra, uyumluluk merkezinde değiştiremezsiniz. PowerShell kullanarak farklı bir grubu etkinleştirmeyle ilgili sonraki bölüme bakın.

- Kayıt **yönetimi ayarları** seçeneği yalnızca kayıt yönetimi yöneticileri tarafından görülebilir. 

#### <a name="enabling-another-security-group-for-disposition"></a>Yok olmak için başka bir güvenlik grubunu etkinleştirme

Uyumluluk merkezinde Kayıt yönetimi ayarlarından bırakma için bir güvenlik grubunu etkinleştirdikten Microsoft 365 uyumluluk merkezi, grup için bu izni devre dışı bırakamaz veya uyumluluk merkezinde seçili grubu değiştiramazsınız. Bununla birlikte, [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) cmdlet'ini kullanarak posta özellikli başka bir güvenlik grubunu etkinleştirebilirsiniz.

Örneğin: 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Denetimi etkinleştirme

Denetimin ilk konumlandırma eylemden en az bir gün önce etkinleştirildiğinden emin olun. Daha fazla bilgi için [bkz. Uyumluluk merkezinde denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md) 

## <a name="disposition-reviews"></a>İncelemeleri incelemeyi inceleme

İçerik bekletme döneminin sonuna ulaştığında, bu içeriği gözden geçirmek ve kalıcı olarak silinip silinemediklerini ("atılır") onaylamak istemeniz için birçok neden vardır. Örneğin, içeriği silmek yerine şunları da ihtiyacınız olabilir:
  
- Dava veya denetimle ilgili içeriğin silinmesini askıya alın.

- belki de özgün bekletme ayarları geçici veya geçici bir çözüm olduğundan içeriğe farklı bir bekletme süresi attayabilirsiniz.

- Örneğin, bu içeriğin araştırma değeri veya geçmiş değeri varsa, içeriği var olan bulunduğu konumdan bir arşiv konuma taşıma.

Bekletme döneminin sonunda bir disposition gözden geçirmesi tetiklendiğinde, seçtiğiniz gözden geçirenler gözden geçirilmesi gereken içerikleri olduğunu haber içeren bir e-posta bildirimi alırlar. Bu gözden geçirenler tek tek kullanıcılar veya posta etkin güvenlik grupları olabilir.

Farklı dillerdeki yönergeler dahil olmak üzere, gözden geçirenlerin bildirim e-postalarını özelleştirebilirsiniz. Çok dilli destek için çevirileri kendiniz belirtmeniz gerekir ve bu özel metin yerel seçimleri ne olursa olsun gözden geçiren tüm gözden geçirenlere gösterilir.

Kullanıcılar, öğenin bekletme döneminin sonunda etiket başına bir ilk e-posta bildirimi alır ve bu bildirime atanan tüm konumlandırma incelemeleri için haftada bir etiket başına bir anımsatıcı gönderilir. Bildirim ve anımsatıcı  >  e-postalarında bağlantıya tıklayarak içeriği gözden geçirmek ve bir eylem Microsoft 365 uyumluluk merkezi için doğrudan Kayıt **yönetimiDisposition** sayfasına gidebilirler. Alternatif olarak, gözden geçirenler uyumluluk merkezinde bu **Disposition** sayfasına da gezinebilirsiniz. Ardından:

- Gözden geçirenler yalnızca onlara atanmış olan incelemeleri görebilirken, kayıt yöneticisi için seçilen güvenlik grubuna eklenen yöneticiler tüm yorum incelemelerini görebilir.

- Gözden geçirenler aynı incelemeye yeni kullanıcılar ekleyebilir. Bu eylemin eklenen kullanıcılara otomatik olarak gerekli izinleri ver [olmadığını unutmayın](#permissions-for-disposition).

- Disposition review process için, her öğe için bir mini gözden geçirme bölmesinde içeriği görme izinleri varsa önizlemesi gösterilir. Bu kullanıcıların izinleri yoksa, içerik bağlantısını seçerek izin isteğide olabilir. Bu mini gözden geçirme bölmesinde içerik hakkında ek bilgi için sekmeler de bulunur:
   - **Dizine** oluşturulmuş özellikleri, nerede bulunduğu, kimin, ne zaman ve en son ne zaman değiştir olduğunu görüntülemek için ayrıntılar.
   - **Bugüne** kadarki tüm yorum gözden geçirme eylemlerinin geçmişini ve varsa gözden geçirenlerin açıklamalarını gösteren geçmiş.

Disposition review can include content in Exchange mailboxes, SharePoint sites, and OneDrive accounts. Bu konumlarda incelemeyi bekleyen içerik, ancak yorum son aşamasında gözden geçiren kişi içeriği kalıcı olarak silmeyi seçtikten sonra kalıcı olarak silinir.

> [!NOTE]
> Posta kutusunun, konumlandırma incelemelerini desteklemek için en az 10 MB verisi olmalıdır.

Yöneticiler, Genel Bakış sekmesinde bekleyen tüm disposition'lara genel **bir bakış** görebilirler. Gözden geçirenler yalnızca bekleyen yok olan öğelerini görebilir. Örneğin:

![Kayıt yönetimine genel bakış'ta bekleyen dispositions.](../media/dispositions-overview.png)

Tüm bekleyen değişiklikleri **görüntüle'yi seçerek**, **Disposition sayfasına oluruz** . Örneğin:

![Sayfayı Microsoft 365 uyumluluk merkezi.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Yok durumu incelemesi için iş akışı

Aşağıdaki diyagramda, bir bekletme etiketi yayımlanır ve kullanıcı tarafından el ile uygulandığında, incelemeyi gözden geçirmenin (tek aşamalı) temel iş akışı açıklanmaktadır. Alternatif olarak, disposition review için yapılandırılmış bir bekletme etiketi otomatik olarak içeriğe uygulanabilir.
  
![Disposition'in nasıl çalıştığını gösteren grafik.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Saklamayı gözden geçirmek için bekletme etiketini yapılandırma

Bekletme döneminin sonunda bir disposition gözden geçirmesini tetiklemek, yalnızca bir bekletme etiketiyle kullanılabilen bir yapılandırma seçeneğidir. Saklama ilkesi için disposition review kullanılamaz. Bu iki bekletme çözümü hakkında daha fazla bilgi için bkz. Bekletme [ilkeleri ve bekletme etiketleri hakkında bilgi.](retention.md)

Bekletme **etiketi için bekletme** ayarlarını tanımla sayfasından:

![Bir etiket için bekletme ayarları.](../media/disposition-review-option.png)
 
Bu Disposition gözden geçirmeyi tetikleme seçeneğini belirttiğinizde, yapılandırmanın bir sonraki sayfasında, art arda kaç **disposition** aşamasından istediğiniz belirtin ve her aşama için incelemeyi gözden geçirenleri belirtin:

![Yorum yorumlarını belirtme.](../media/disposition-reviewers.png) 

Aşama **ekle'yi** seçin ve aşamayı tanımlama amacıyla adlayın. Ardından bu aşama için gözden geçirenleri belirtin.

Gözden geçirenler için, bir kullanıcı veya posta etkin bir güvenlik grubu belirtin. Microsoft 365 grupların ([Office 365 grupları](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) bu seçenekte desteklenemz.

Bekletme döneminin sonunda bir öğeyi gözden geçirmek için birden fazla kişiye ihtiyacınız varsa, Bir aşama daha ekle'yi seçin ve size gereken aşama sayısı için yapılandırma işlemini en fazla beş aşamalı olarak yinelayın. 

Ayrı bir disposition aşamasında, bu aşama için belirttiğiniz kullanıcılardan herhangi biri bekletme döneminin sonunda öğe için bir sonraki eylemi alma yetkisine sahiptir. Bu kullanıcılar ayrıca, yokma gözden geçirme aşamasına başka kullanıcılar da ekleyebilir.

> [!NOTE]
> Çok aşamalı yok etme gözden geçirme öncesinde bekletme etiketlerini yapılandırdısanız, şu özelliği desteklemek için etiketlerinizi yükseltebilirsiniz: Etiket sihirbazında Aşama ekle'yi seçin veya var olan gözden geçirenleri düzenleyin veya yeni gözden geçirenleri ekleyin.

Yapılandırma aşamasında, belirtilen her aşama için bunu yeniden adlandırabilirsiniz, yeniden sıralarını kaldırabilir veya Aşama eylemleri seçeneğini (**...**) seçerek kaldırabilirsiniz: 

![Yokma incelemeleri için evre eylemleri.](../media/stage-actions-disposition-review.png)

Bununla birlikte, bekletme etiketini oluşturduktan sonra aşamayı yeniden sıralayama veya kaldırmaz.

Gözden geçirenlerinizi belirttikten sonra, onlara **Disposition Management rol iznini ver verilmeyi** unutmayın. Daha fazla bilgi için bu [sayfada Disposition izinleri](#permissions-for-disposition) bölümüne bakın.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>E-posta iletilerini, incelemeyi yok etmek için özelleştirme

Gözden geçirene gönderilen varsayılan e-posta bildirimi örneği:

![Öğe, incelemeyi incelemeye hazır olduğunda varsayılan metni içeren e-posta bildirimi örneği.](../media/disposition-review-email.png)

İlk bildirim ve anımsatıcılar için gözden geçirenlere gönderilen e-posta iletilerini özelleştirebilirsiniz.

Uyumluluk merkezi'nde bulunan Kayıt yönetimi sayfalarından herhangi biri için Kayıt yönetimi **ayarları'ı seçin**:  

![Kayıt yönetimi ayarları.](../media/record-management-settings.png)

Disposition **sekmesindeki** Email **notifications for disposition reviews** bölümünde, yalnızca varsayılan e-posta iletisi kullanmak mı istediğinize karar ve belirtin veya varsayılan iletiye kendi metninizi ekleyin. E-posta yönergelerine, bekletme etiketiyle ilgili bilgiden sonra ve sonraki adım yönergelerinden önce özel metniniz eklenir.

Tüm dillerin metinleri eklenebilir, ancak biçimlendirme ve resimler desteklenmez. URL'ler ve e-posta adresleri metin olarak girilebilir ve e-posta istemcisine bağlı olarak, özelleştirilmiş e-postada köprüler veya biçimlendirilmemiş metin olarak biçimlendirilmiş metin olarak biçimlendirilmiş olarak görüntülenir.

Eklemek için örnek metin:

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Değişiklikleri **kaydetmek için** Kaydet'i seçin.

### <a name="viewing-and-disposing-of-content"></a>İçeriği görüntüleme ve görüntüleme

Gözden geçirene içeriğin gözden geçir gitmeye hazır olduğunu e-postayla bildirse, e-postada yer alan ve doğrudan kaynakta yer alan Kayıt yönetiminden **Disposition** sayfasına ulaşacak bir Microsoft 365 uyumluluk merkezi. Orada, gözden geçirenler Tür'de Beklemede konumlandırmayı görüntüleyerek, her bir bekletme etiketi için  kaç öğenin yok **bekleyen olduğunu görebilir**. Ardından bir bekletme etiketi seçerler ve **bu etikete sahip tüm içeriği görmek** için Yeni pencerede aç'ı seçerler:

![Disposition review için yeni pencerede aç.](../media/open-in-new-window.png)

Bekleyen **dispositions sayfasında** , bu etiket için tüm bekleyen değişiklikleri görebilirler. Bir veya birden çok öğe seçildiğinde, üzerinde işlem öncesinde içeriği incelemek için mini önizleme bölmesini ve **Kaynak, Ayrıntılar** ve Geçmiş sekmesini  kullanabilirler: 

![Disposition options.](../media/retention-disposition-options.png)

Yatay kaydırma çubuğunu kullanırsanız veya min gözden geçirme bölmesini kapatırsanız, son kullanma tarihini ve inceleme aşamasının adını içeren daha fazla sütun görebilirsiniz.

Gösterilen örnekte gördüğünüz gibi, desteklenen eylemler: 
  
- **Tasfiyeyi onayla**:
    - Bu eylem, disposition gözden geçirmenin geçici aşaması için seçildiğinde (birden çok aşama yapılandırdıyabilirsiniz): Öğe bir sonraki konumlandırma aşamasına taşınır.
    - Bu eylem, yok sayma incelemesinin son aşaması için seçildiğinde veya bir kez yok sayma yalnızca bir aşamadır: Öğe kalıcı olarak silinmeye uygun olarak işaretlenir ve bu süreölçer işi 7 gün içinde işlem gösterir. Öğenin kalıcı olarak silinecek olan zamanlaması iş yüküne bağlıdır. Daha fazla bilgi için bkz[.](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive) SharePoint ve OneDrive için bekletme [nasıl çalışır ve Exchange](retention-policies-exchange.md#how-retention-works-for-exchange).

- **Yeniden Etiketle**:
    - Bu eylem seçildiğinde, öğe özgün etiket için konumlandırma gözden geçirme sürecinden çıkar. Ardından öğe, yeni seçilen bekletme etiketinin bekletme ayarlarına tabi olur.

- **Uzat**:
    - Bu eylem seçildiğinde, uzatılmış sürenin sonuna kadar etkili bir şekildeposition gözden geçirme askıya alınır ve ilk aşamadan sonra yeniden konumlandırma incelemesi tetiklenir.

- **Gözden geçirenleri ekleme**:
    - Bu eylem seçildiğinde, kullanıcıdan gözden geçirme için başka kullanıcılar belirtmesi ve eklemesi istenir.
    > [!NOTE]
    > Bu eylem, eklenen [kullanıcılara gerekli izinleri](#permissions-for-disposition) otomatik olarak atamaz. Bu izinleri yoksa, yok etme incelemesine katılamaz.

Yapılan her eylemin, [Disposition review activities auditing activities](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) grubunda karşılık gelen bir denetim olayı vardır.

Disposition gözden geçirme sırasında, içerik hiçbir zaman özgün konumdan hareket eder ve son veya yalnızca silme aşamasında bu eylem gözden geçiren tarafından seçilene kadar kalıcı olarak silinmek üzere işaretlanmaz.

## <a name="disposition-of-records"></a>Kayıtların yok olarak kaydın yokğları

Kayıt **yönetimi ana** sayfasından > **sekmesinde** şunları tanımlayabilirsiniz:

- Silme incelemesi sonucunda silinen öğeler.
- Kayıt veya mevzuat kaydı olarak işaretlenmiş ve bekletme döneminin sonunda otomatik olarak silinen öğeler.

Bu öğeler, **Tür sütununa** At edilmiş Olan **Kayıtları** görüntüler. Örneğin:

![Imha incelemesi olmadan at edilmiş öğeler.](../media/records-disposed2.png)

> [!NOTE]
> Bu işlev birleşik denetim günlüğünden alınan bilgileri kullanır ve [dolayısıyla](search-the-audit-log-in-security-and-compliance.md) buna karşılık gelen olayların yakalanması için [denetimin](turn-audit-log-search-on-or-off.md) etkinleştirilmesi ve aranabilir olması gerekir.

Kayıt veya mevzuat kaydı olarak işaretlenmiş silinmiş öğelerin denetimi için, Dosya ve sayfa etkinlikleri kategorisinde Kayıt  olarak işaretlenmiş Silinmiş **dosya için arama**. Bu denetim olayı belgeler ve e-postalar için geçerlidir.

## <a name="filter-and-export-the-views"></a>Görünümleri filtreleme ve dışarı aktarma

Imha sayfasından bir bekletme etiketi seçerek, Bekleyen imha sekmesi (varsa) ve Atilen öğeler sekmesi, öğeleri daha kolay  bu seçmenize yardımcı olmak için görünümleri filtrelemenizi sağlar.

Bekleyen dispositions için, zaman aralığı son kullanma tarihini temel alarak. At alınan öğeler için zaman aralığı silme tarihine göredir.
  
Her iki görünümdeki öğelerle ilgili bilgileri bir .csv olarak dışarı aktarabilirsiniz ve bu dosyayı kullanarak sıralamayı ve Excel.
