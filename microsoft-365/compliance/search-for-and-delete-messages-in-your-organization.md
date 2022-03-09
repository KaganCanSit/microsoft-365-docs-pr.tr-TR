---
title: Organizasyonda e-posta iletilerini arama ve silme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: E-posta iletisi aramak ve Microsoft 365 uyumluluk merkezi tüm posta kutularından silmek için, ileti iletişim kutusunda arama ve temizleme özelliğini kullanın.
ms.openlocfilehash: 9361f7dea0e1b12d50733b9b1d1e91ac15577ab9
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401000"
---
# <a name="search-for-and-delete-email-messages"></a>E-posta iletilerini arama ve silme

**Bu makale yöneticilere aittir. Posta kutunuzda silmek istediğiniz öğeleri bulmaya mı çalışıyorsunuz? Bkz [. Hızlı Arama ile ileti veya öğe bulma](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

İçerik arama özelliğini kullanarak, e-posta iletilerini, organizasyonu tüm posta kutularından arayabilir ve silebilirsiniz. Bu, zararlı olabilecek veya yüksek riskli e-postaları bu e-posta gibi bulup kaldırmanıza yardımcı olabilir:

- Tehlikeli ekler veya virüs içeren iletiler

- Kimlik avı iletileri

- Hassas veriler içeren iletiler

> [!TIP]
> Kuruluşta Office 365 Plan 2 aboneliği için Bir Defender varsa, bu makalede açıklanan yordamı takip etmek yerine, [Kötü amaçlı e-postaları Office 365'de](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) teslim etme konusunda ayrıntılı olarak açıklanan yordamın kullanılması önerilir.

## <a name="before-you-begin"></a>Başlamadan önce

- Bu makalede açıklanan arama ve temizleme iş akışı, sohbet iletilerini veya diğer içerikleri Microsoft Teams. 2. Adımda oluşturduktan sonra İçerik arama Microsoft Teams döndüren içerik aramalarında, 3. Adımda öğeleri temizledikten sonra bu öğeler silinmez.

- İçerik araması oluşturmak ve çalıştırmak için, **eBulma** Yöneticisi rol grubunun bir üyesi olmalı veya ilgili grupta Uyumluluk Araması rolüne Microsoft 365 uyumluluk merkezi. İletileri silmek için, Kuruluş Yönetimi rol grubunun bir üyesi olmak  veya uyumluluk merkezinde Arama ve Temizleme rolüne atanmış  olmak gerekir. Rol grubuna kullanıcı ekleme hakkında bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

  > [!NOTE]
  > Kuruluş **Yönetimi rol** grubu hem kuruluşta hem de Exchange Online içinde yer Microsoft 365 uyumluluk merkezi. Bunlar, farklı izinler vermek için ayrı rol gruplarıdır. Aynı kuruluşta **Kuruluş Yönetimi'ne** Exchange Online e-posta iletilerini silmek için gerekli izinleri verilemez. Uyumluluk merkezinde Size Arama ve Temizleme rolü atanmamışsa (doğrudan veya Kuruluş Yönetimi gibi bir rol grubu **aracılığıyla),** **New-ComplianceSearchAction** cmdlet'ini "'Temizleme' parametre adıyla eşleşen bir parametre bulunamadı" iletisini çalıştırarak 3. Adımda bir hata alırsınız.

- İletileri silmek için Güvenlik & Uyumluluk Merkezi PowerShell'i kullanasınız. Bağlanma [yönergeleri için 1](#step-1-connect-to-security--compliance-center-powershell) . Adım'a bakın.

- Aynı anda posta kutusu başına en fazla 10 öğe kaldırılabilir. İletileri arama ve kaldırma özelliği bir olay yanıt aracı olarak amaçlanan bir özellik olduğundan, bu sınır iletilerin posta kutularından hızla kaldırılmasını sağlamaya yardımcı olur. Bu özellik, kullanıcı posta kutularını temizlemeyi amaçlamadı.

- İçerik aramalarında, arama yaparak ve temizleme eylemlerini yaparak öğeleri silmek için kullanabileceğiniz en fazla posta kutusu sayısı 50.000'tir. [Arama (2](#step-2-create-a-content-search-to-find-the-message-to-delete). Adımda oluşturduktan sonra 50.000'den fazla posta kutusu aranıyorsa, temizleme eylemi (3. Adımda oluşturduktan) başarısız olur. Aramayı genelde, tüm posta kutularını içermesi için yapılandırıldığında, tek bir aramada 50.000'den fazla posta kutusunda arama yapmak gerekir. Bu kısıtlama, 50.000'den az posta kutusunun arama sorgusuyla eşleşmesi için bile geçerlidir. Öğeleri 50.000'den fazla posta kutusundan aramak ve temizlemek için arama izinleri filtrelerini kullanma hakkında yol gösterici bilgiler bölümüne bakın.[](#more-information)

- Bu makaledeki yordam, yalnızca posta kutularında ve ortak Exchange Online öğeleri silmek için kullanılabilir. Bu sitelerden veya sitelerden içerik SharePoint OneDrive İş.

- Bir çalışma e-postasında yer alan Advanced eDiscovery-posta öğeleri, bu makaledeki yordamlar kullanılarak silinemez. Bunun nedeni, gözden geçirme kümesinde yer alan öğelerin canlı hizmette değil, Depolama Bir Azure depolama Depolama depolanmış olabilir. Bu, 1. Adımda oluşturdukları içerik arama tarafından döndürül olmayacakları anlamına gelir. Gözden geçirme kümesinde öğeleri silmek için, gözden geçirme kümesi Advanced eDiscovery büyük/küçük harflerini silmeniz gerekir. Daha fazla bilgi için bkz[. Vakayı kapatma Advanced eDiscovery silme](close-or-delete-case.md).

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>1. Adım: Bağlan ve Uyumluluk & PowerShell'e geçin

İlk adım, güvenlik ve uyumluluk & PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz. Güvenlik [Bağlan Uyumluluk Merkezi PowerShell& e geçin](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>2. Adım: Silinecek iletiyi bulmak için İçerik Arama oluşturma

İkinci adım, kuruluş posta kutularından kaldırmak istediğiniz iletiyi bulmak için İçerik araması oluşturmak ve çalıştırmaktır. Arama oluşturmak için Güvenlik ve Uyumluluk Microsoft 365 uyumluluk merkezi PowerShell'de Yeni Uyumluluk Araması ve Başlangıç  **Uyumluluğu** Araması cmdlet'lerini & oluşturabilirsiniz. Bu aramanın sorgusuyla eşleşmeye neden olan iletiler, 3. **Adım'daki Yeni Uyumluluk AramaAction -Temizleme** [komutu çalıştırarak silinir](#step-3-delete-the-message). İçerik araması oluşturma ve arama sorgularını yapılandırma hakkında bilgi için, aşağıdaki konulara bakın:

- [web'de içerik Office 365](content-search.md)

- [İçerik arama anahtar sözcük sorguları](keyword-queries-and-search-conditions.md)

- [New-ComplianceSearch](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> Bu adımda oluştur konumunuz olan İçerik arama özelliğinde arama yapılan içerik konumları, bu SharePoint veya OneDrive İş içerebilir. İçerik aramalarına yalnızca e-posta iletileri için kullanılacak posta kutularını ve ortak klasörleri  dahilebilirsiniz. İçerik aramada siteler varsa, Yeni Uyumluluk AramaAction cmdlet'ini çalıştırarak 3. **Adım'da bir** hata alırsınız.

### <a name="tips-for-finding-messages-to-remove"></a>İpuçları iletileri bulma hakkında daha fazla yardım

Arama sorgusunun amacı, arama sonuçlarını yalnızca kaldırmak istediğiniz iletiye veya iletilere göre daraltmaktır. Bazı ipuçları:

- İletinin konu satırlarında kullanılan tam metni veya tümceciği biliyorsanız, arama **sorgusunda Konu** özelliğini kullanın.

- İletinin tam tarihini (veya tarih aralığını) biliyorsanız, arama sorgusuna **Received** özelliğini dahil edin.

- İletiyi kimin gönderdiğini biliyorsanız, **From özelliğini** arama sorgusuna dahil etmek için bu özelliği kullanın.

- Aramanın yalnızca silmek istediğiniz iletiyi (veya iletileri) geri döndürüleni doğrulamak için arama sonuçlarını önizleme.

- Toplam sonuç sayısını bulmak için, arama tahmin istatistiklerini (Microsoft 365 uyumluluk merkezi'de aramanın ayrıntılar bölmesinde görüntülenir) veya [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch) cmdlet'ini kullanarak kullanın.

Burada, şüpheli e-posta iletilerini bulmak için 2 sorgu örneği verilmiştir.

- Bu sorgu, 13 Nisan 2016 ile 14 Nisan 2016 arasında kullanıcılar tarafından alınan ve konu satırlarında "eylem" ve "gerekli" sözcüklerini içeren iletileri döndürür.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- Bu sorgu, chatsuwloginsset12345@outlook.com tarafından gönderilen ve konu satırlarında tam olarak "Hesap bilgilerini güncelleştirme" tümceciği bulunan iletileri döndürür.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

İşte, kuruluşta tüm posta kutularında arama yapmak için Yeni Uyumluluk arama ve **Başlangıç-Uyumluluk** Arama cmdlet'lerini çalıştırarak arama oluşturmak ve başlatmak için bir sorgu kullanma örneği:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>3. Adım: İletiyi silme

Kaldırmak istediğiniz iletileri geri göndermek için İçerik aramalarını oluşturduktan ve bu özelliği geliştirdikten sonra, son adım iletiyi silmek için Güvenlik & Compliance PowerShell'de **New-ComplianceSearchAction -Purge** komutunu çalıştırmaktır. İletiyi yumuşak veya zor silebilirsiniz. Yumuşak silinmiş ileti kullanıcının Kurtarılabilir Öğeler klasörüne taşınır ve silinen öğe bekletme süresi dolana kadar korunur. Kalıcı olarak silinen iletiler, posta kutusundan kalıcı olarak kaldırılması için işaretlenir ve posta kutusunun Yönetilen Klasör Yardımcısı tarafından bir sonraki işlemde kalıcı olarak kaldırılır. Posta kutusunda tek öğe kurtarma etkinleştirildiyse, silinmiş öğe bekletme süresi sona erdiğinde, kalıcı olarak silinmiş öğeler de kalıcı olarak kaldırılır. Posta kutusu yerine basılı tutarsa, silinen iletiler öğenin süresi dolana kadar veya posta kutusundan tutma kaldırılana kadar korunur.

> [!NOTE]
> Daha önce de belirtildiği gibi Microsoft Teams Arama tarafından döndürülen öğeler, **New-ComplianceSearchAction -Purge komutunu çalıştıracak şekilde silinmez**.

İletileri silmek için aşağıdaki komutları çalıştırmak için, Güvenlik ve Uyumluluk Merkezi [PowerShell'e & emin olun](/powershell/exchange/connect-to-scc-powershell).

### <a name="soft-delete-messages"></a>İletileri yumuşak silme

Aşağıdaki örnekte komut, "Kimlik Avı İletisini Kaldır" adlı İçerik arama tarafından döndürülen arama sonuçlarını yumuşak olarak siler.

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>İletileri zor silme

"Kimlik Avı İletilerini Kaldır" içerik arama tarafından döndürülen öğeleri zor silmek için şu komutu çalıştırabilirsiniz:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

İletileri yumuşak veya zor silmek için önceki komutları çalıştırsanız,  *SearchName*  parametresi tarafından belirtilen arama 1. Adımda oluşturduğunuz İçerik aramasıdır.

Daha fazla bilgi için bkz [. Yeni Uyumluluk IçinSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Daha fazla bilgi

- **Arama ve kaldırma işlemiyle ilgili durumu nasıl alısınız?**

  Silme **işlemiyle ilgili durumu almak için Get-ComplianceSearchAction'ı** çalıştırın. **New-ComplianceSearchAction cmdlet'ini** çalıştırarak oluşturulan nesnenin adı şu biçimdedir: `<name of Content Search>_Purge`.

- **Bir iletiyi sildikten sonra ne olur?**

  Komutla birlikte silinen bir ileti  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` Temizleyiciler klasörüne taşınır ve kullanıcı bu klasöre erişemez. İleti Temizleyiciler klasörüne taşındıktan sonra, posta kutusunda tek öğe kurtarma etkinleştirildiyse ileti, silinmiş öğe bekletme süresi boyunca korunur. (Yeni Microsoft 365 kutusu oluşturulduğunda tek öğe kurtarma varsayılan olarak etkinleştirilir.) Silinmiş öğe bekletme süresi dolduğunda, ileti kalıcı olarak silinmek üzere işaretlenir ve posta kutusunun Yönetilen Klasör yardımcısı tarafından bir sonraki işlenmesinde Microsoft 365 yeniden temizlenir.

  Komutu kullanırsanız `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` , iletiler kullanıcının Kurtarılabilir Öğeler klasöründeki Silmeler klasörüne taşınır. Bu, diğer e-Microsoft 365. Kullanıcı, posta kutusu için yapılandırılmış silinmiş öğe bekletme süresine bağlı olarak, silinmiş Öğeler klasöründeki iletileri bir süre için kurtarabilirsiniz. Bu bekletme süresinin süresi dolduktan (veya kullanıcı iletiyi süresi dolmadan önce temizlerse), ileti Temizler klasörüne taşınır ve artık kullanıcı tarafından erişilemez. Temizleyiciler klasörüne devredildiğinde, posta kutusunda tek öğe kurtarma etkinleştirildiyse, ileti, posta kutusu için yapılandırılmış silinmiş öğe bekletme süresine bağlı olarak süre boyunca korunur. (Yeni Microsoft 365 kutusu oluşturulduğunda tek öğe kurtarma varsayılan olarak etkinleştirilir.) Silinmiş öğe bekletme süresi dolduktan sonra, ileti kalıcı silme için işaretlenir ve posta kutusunun Yönetilen Klasör yardımcısı tarafından bir sonraki işlemde Microsoft 365 yeniden temizlenir.

- **50.000'den fazla posta kutusundan bir iletiyi silmeniz gerekirse ne olur?**

  Daha önce de belirtildiği gibi, en çok 50.000 posta kutusu üzerinde arama ve temizleme işlemi gerçekleştirebilirsiniz (50.000'den az bile arama sorgusuyla eşleşmesi olan öğeler içerir). 50.000'den fazla posta kutusunda arama ve temizleme işlemi yapmak zorundaysanız, 50.000'den az posta kutusuna aranacak posta kutusu sayısını azaltan geçici arama izinleri filtreleri oluşturmayı göz önünde bulundurabilirsiniz. Örneğin, kuruluşun farklı departmanlar, eyaletler veya ülkelerde posta kutuları içeriyorsa, bu posta kutusu özelliklerine dayalı olarak bir posta kutusu arama izinleri filtresi oluşturabilir ve bu filtreyi kullanarak, kuruluşta posta kutularının bir alt kümesinde arama oluşturabilirsiniz. Arama izinleri filtresini oluşturduktaktan sonra, arama oluşturabilir (1. Adımda açıklanmıştır) ve sonra iletiyi silersiniz (3. Adım'da açıklanmıştır). Ardından, filtreyi düzen kullanarak farklı bir posta kutuları kümesinde arama ve temizleme. Arama izinleri filtreleri oluşturma hakkında daha fazla bilgi için bkz. [İçerik Arama için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md).

- **Arama sonuçlarına dahil edilen satırsız öğeler silinir mi?**

  Hayır, 'New-ComplianceSearchAction -Purge komutu, 'unindexed olmayan öğeleri silemez.

- **Bir ileti, bir saklama veya Mahkeme tutma ilkesine In-Place posta kutusundan silinirse Microsoft 365 olur?**

  İleti temizlendikten ve Temizilenler klasörüne taşındıktan sonra, iletinin süresi dolana kadar ileti korunur. Tutma süresi sınırsızsa, tutma kaldırılana veya tutma süresi değiştirilene kadar öğeler korunur.

- **Arama ve kaldırma iş akışı neden farklı güvenlik ve uyumluluk merkezi rol gruplarına bölünmüş?**

  Daha önce de belirtildiği gibi, bir kişi eBulma Yöneticisi rol grubunun bir üyesi olmalı veya posta kutularını aramak için Uyumluluk Arama yönetimi rolüne atanmıştır. İletileri silmek için, kişinin Kuruluş Yönetimi rol grubunun bir üyesi olması veya Arama ve Temizleme yönetimi rolüne atanmalı. Bu, kuruluşta kimlerin posta kutularında arama ve ileti silebilir olduğunu denetlemenizi sağlar.
