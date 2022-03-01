---
title: Veri Exchange Online önleme ilkelerini Uyumluluk merkezine geçirme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Çevrimiçi veri kaybı önleme ilkelerinizi planlamayı ve Exchange DLP'de Microsoft 365 öğrenin.
ms.openlocfilehash: 07d0eb19155a7f91b30feb8d7938ea574b0e75f9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019483"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Veri Exchange Online önleme ilkelerini Uyumluluk merkezine geçirme

[Exchange Online kaybı önleme (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) ilkeleri kullanım dışı ediliyor. [Uyumluluk Merkezi'nde, DLP](dlp-learn-about-dlp.md) dahil Exchange Online çok daha zengin DLP [Microsoft 365 sunulmaktadır](https://compliance.microsoft.com/datalossprevention?viewid=policies). DLP ilkesi geçiş sihirbazını kullanarak, Exchange Online DLP ilkelerinizi yöneteceğiz uyumluluk merkezine getirebilirsiniz.

Geçiş sihirbazı, İlke'de DLP ilkelerinizin yapılandırmasını Exchange sonra da Uyumluluk merkezinde yinelenen ilkeler oluşturarak çalışır. Varsayılan olarak sihirbaz, ilkelerin yeni sürümlerini **Test** modunda oluşturur; böylelikle, hiçbir eylemi zorlamadan ortamınıza bunların ortamınıza etkisini gösterebilirsiniz. Uyumluluk merkezi sürümlerine tam olarak geçiş yapmaya hazır olduktan **_sonra:_**

1. Kaynak Yönetim Merkezi'nde (EAC) kaynak Exchange devre dışı bırakma veya silme.
1. İlkenin Uyumluluk merkezi sürümünü düzenleyin ve test olan **durumunu Zorunlu olarak** **değiştirir.** 

> [!WARNING]
> Her iki ilke kümesinde de Zorla olarak ayarlamadan önce EAC'de kaynak ilkeyi silemez veya devre  dışı bırakamazsanız, eylemleri uygulamaya çalışırken yinelenen olaylar alırsınız. **_Bu desteklenmeyen bir yapılandırmadır._**


Geçiş sihirbazı yalnızca EXO ilkelerini ve ilişkili posta akış kurallarını geçirir. Tek Exchange posta akışı kuralları geçirilmez.

## <a name="migration-workflow"></a>Geçiş iş akışı

DLP ilkelerini Uyumluluk merkezinde Birleşik DLP yönetim konsoluna Exchange dört aşama vardır.  

1. Geçişe hazırlanma
    1. Yinelenen işlevler için Exchange Online (EXO) DLP ilkelerinizi ve Uyumluluk Merkezi DLP ilkelerinizi değerlendirin ve karşılaştırın.
    1. Tam olarak hangi EXO DLP ilkelerini geçirmek istediğinize karar verin, bunları geçirmek için sihirbazı kullanabilirsiniz.
    1. İlke yönetim merkezinde hangi EXO DLP ilkelerini birleştirmek ve birleştirmek istediğinize karar Exchange sonra, geçiş sihirbazını kullanarak bunları Uyumluluk Merkezi'ne getirin.
1. Geçişi gerçekleştirme - sihirbazı kullanma
1. Test ve doğrulama - sonuçları inceleme
1. Geçirilen ilkeleri etkinleştirme

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="licensing-and-versions"></a>Lisanslar ve sürümler

DLP ilkelerini ve diğer tüm eklentileri almaya başlamadan önce Microsoft 365 [doğrulamanız](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) gerekir. 

İlke geçiş sihirbazına erişmek ve sihirbazı kullanmak için, bu aboneliklerden veya eklentilerden birini kullan

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 uyumluluğu
- Microsoft 365 A5 uyumluluğu
- Microsoft 365 E5 koruma ve yönetim bilgilerini koruma
- Microsoft 365 A5 koruma ve yönetim bilgilerini koruma

DLP lisans gereksinimlerinin ayrıntılı listesi için bkz. Güvenlik Microsoft 365 uyumluluğu ve veri kaybını önleme [için lisanslama & kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)


### <a name="permissions"></a>İzinler

Geçiş sihirbazını çalıştırmak için kullanabileceğiniz hesabın hem Genel Yönetici Konsolu DLP sayfasına Exchange, hem de Uyumluluk merkezi'nde Birleşik DLP konsoluna erişimi olması gerekir.

## <a name="prepare-for-migration"></a>Geçişe hazırlanma

1. DLP'ye, Uyumluluk merkezi DLP konsoluna veya Exchange Yönetim merkezi DLP konsoluna yabancı değilseniz, ilke geçişini denemeden önce kendinizi tanımanız gerekir.
    1. [Exchange Online kaybı önleme (DLP) ilkelerini engelleme](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
1. Şu soruları Exchange DLP ve Uyumluluk merkezi ilkelerinizi değerlendirin:


|Soru  |Eylem  | Geçiş yordamı|
|---------|---------|---------|
|İlke hala gerekli mi?    |Yoksa, silin veya devre dışı bırakma |geçirme|
|Başka herhangi bir Uyumluluk Merkezi veya Uyumluluk Exchange DLP ilkeleriyle çakışıyor mu?     |Evet ise, örtüşen ilkeleri bir misiniz?         |- Başka bir DLP ilkesiyle Exchange çakışıyorsa, yönetim merkezinde birleştirilmiş DLP Exchange el ile oluşturun ve geçiş sihirbazını kullanın. </br> - Var olan bir Uyumluluk Merkezi ilkesiyle örtüşüyorsa, var olan Uyumluluk Merkezi ilkesine uyması için değiştirebilirsiniz, uyumluluk Exchange geçirme|
|Son Exchange DLP ilkesi sıkı bir kapsamdadır ve iyi tanımlanmış koşulları, eylemleri, eklemeleri ve dışlamaları vardır mı?     |Evet ise, sihirbazın geçiş yapmak için iyi bir aday olduğunu varsa, daha sonra silmek için geri dönmeyi anımsayacak şekilde ilkeyi not etme         | sihirbazla geçiş|

## <a name="migration"></a>Geçiş

Uyumluluk ve uyumluluk için tüm Exchange Uyumluluk Merkezi DLP ilkelerinizi değerlendirdikten sonra, geçiş sihirbazını kullanabilirsiniz.

1. Uyumluluk Microsoft 365 DLP [konsolunu](https://compliance.microsoft.com/datalossprevention?viewid=policies) açın.
2. Geçir geçir Exchange başka DLP ilkeleri varsa, sayfanın en üstünde bunu size haber eden bir başlık görüntülenir.
3. Geçiş **sihirbazını açmak** için başlıkta İlkeleri geçir'i seçin. Tüm Exchange DLP ilkeleri listelenir. Daha önce geçirilen ilkeler seçilmez.
4. Geçirmek istediğiniz ilkeleri seçin. Aşamalı bir yaklaşım kullanarak bunları tek tek veya grup olarak veya bir kerede geçirsiniz. **İleri**'yi seçin.
5. Tüm uyarılar veya iletiler için uçarak çıkış bölmesini gözden geçirme. Devam etmeden önce tüm sorunları giderin.
6. Yeni Uyumluluk merkezi ilkesinin içinde, Etkin, Test veya Devre Dışı **olarak oluşturması** **istediğiniz** modu **seçin**.  Varsayılan değer **Sına'dır**. **İleri**'yi seçin.
7. İsterseniz, diğer birleşik DLP konumları için DLP ilkelerini Exchange başka ilkeler de oluşturabilirsiniz. Bu, geçirilen DLP ilkesi için yeni bir birleşik DLP ilkesi ve burada Exchange konumlar için yeni bir birleşik DLP ilkesine neden olur.

> [!IMPORTANT]
> Cihazlar Exchange SharePoint, OneDrive, Şirket içi, MCAS veya Teams sohbeti ve kanal iletileri gibi diğer DLP konumları tarafından desteklenen tüm DLP ilkesi koşulları ve eylemleri ek ilkeye bırakılır. Ayrıca, diğer konumlar için yapılması gereken ön çalışmalar da vardır. Bkz:
>- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
>- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
>- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
>- [Şirket içi Microsoft 365 önleme hakkında bilgi](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Şirket içi tarayıcıda veri kaybı önlemeye başlama](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
>- [Şirket Microsoft 365 kaybı önlemeyi kullanma](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)
 
8. Geçiş sihirbazı oturum ayarlarını gözden geçirme. **İleri**'yi seçin.
9. Geçiş raporunu gözden geçirme. Posta akışı kurallarında yer alan ve Exchange hatalara dikkatin. Bunları düzeltebilir ve ilişkili ilkeleri yeniden gidersiniz.

Geçirilen ilkeler artık Uyumluluk merkezi DLP konsolunda DLP ilkeleri listesinde görünür. 

## <a name="common-errors-and-mitigation"></a>Yaygın hatalar ve risk azaltma
|Hata iletisi  |Neden  | Azaltma/Önerilen adımlar|
|---------|---------|---------|
|Adı olan bir uyumluluk ilkesi `<Name of the policy>` , senaryoları içinde zaten vardır `Dlp`.    |Büyük olasılıkla bu ilke geçişi daha önce yapılır ve daha sonra aynı oturumda yeniden atlandı |Geçiş için kullanılabilir ilke listesini güncelleştirmek için oturumu yenileyin. Daha önce geçirilen tüm ilkeler durum bilgisinde `Already migrated` olmalıdır.|
|Adı olan bir uyumluluk ilkesi `<Name of the policy>` , senaryoları içinde zaten vardır `Hold`.     |Aynı kiracıda aynı adı olan bir bekletme ilkesi vardır.       |- EAC'de DLP İlkesini farklı bir adla yeniden adlandırın. </br> - Etki durumdaki ilke için geçişi yeniden deneyin. |
|`DLP-group@contoso.com` bir dağıtım grubu veya posta etkin bir güvenlik grubu olduğundan, Paylaşılan koşulu için değer olarak kullanılamaz. Belirli grupların üyeleri tarafından etkinlikleri algılamak için Üyenin Paylaştığı Yüklem bilgisini kullanın.     |Aktarım kuralları grupların koşulda kullanılabilir olmasına izin `sender is` vermez, ancak birleşik DLP buna izin vermez.         | Aktarım kuralını güncelleştirin ve tüm grup e-posta adreslerini koşuldan kaldırın `sender is` ve gerekirse grubu koşula `sender is a member of` ekleyin. Etki durumdaki ilke için geçişi yeniden deneme|
|Alıcı bulun bulundu `DLP-group@contoso.com`. Yeni oluşturulduktan sonra işlemi bir süre sonra yeniden deneyin. Silindi veya süresi dolduğunda lütfen geçerli değerlerle sıfırlayın ve yeniden deneyin.     |Kullanılan veya koşulda kullanılan grup adresinin `sender is a member of` süresi `recipient is a member of` dolmuş ya da geçersiz olabilir.         | - Yönetim merkezinde aktarım kuralında bulunan tüm geçersiz grup e-posta adreslerini Exchange kaldırın. </br> - Etki durumdaki ilke için geçişi yeniden deneyin.|
|Yüklemde belirtilen `FromMemberOf` değer posta özelliği etkin güvenlik grubu olmalıdır.     |Aktarım kuralları tek tek kullanıcıların koşulda kullanılabilir olmasına olanak sağlar `sender is a member of` , ancak birleşik DLP buna izin vermez.         | - Tek tek tüm kullanıcı e-posta adreslerini koşuldan kaldırmak `sender is a member of` için aktarım kuralını güncelleştirin ve gerekirse kullanıcıları koşula `sender is` ekleyin. </br> - Etki durumdaki ilke için geçişi yeniden deneyin.|
|Yüklemde belirtilen `SentToMemberOf` değer posta özelliği etkin güvenlik grubu olmalıdır.    |Aktarım kuralları tek tek kullanıcıların koşul altında kullanılmaktadır `recipient is a member of` , ancak birleşik DLP izin vermez.         | - Tek tek tüm kullanıcı e-posta adreslerini koşuldan kaldırmak `recipient is a member of` için aktarım kuralını güncelleştirin ve gerekirse kullanıcıları koşula `recipient is` ekleyin. </br> - Etki durumdaki ilke için geçişi yeniden deneyin.|
|Parametrenin `<Name of condition>` kullanımı yalnızca bu parametre Exchange. Bu parametreyi kaldırın veya yalnızca konum Exchange açabilirsiniz.         | Büyük olasılıkla, Uyumluluk Merkezi'nde bahsedilen koşulun destekçisi Teams SPO/ODB/Teams konumlarla aynı adlı başka bir ilke vardır. | Yönetim merkezinde DLP Exchange yeniden adlandırarak geçişi yeniden deneyin.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test ve doğrulama <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

İlkelerinizi test etmek ve gözden geçirmek.

1. [DLP ilkesi yordamlarını test edin](create-test-tune-dlp-policy.md#test-a-dlp-policy).
2. Etkinlik gezgininde ilke tarafından oluşturulan [olayları gözden geçirebilirsiniz](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Exchange Yönetim Merkezi DLP ile Birleşik DLP arasındaki Microsoft 365 gözden geçirme

Geçirilen ilkelerin beklendiği gibi davran olduğundan emin olmak için, her iki yönetim merkezinden raporları dışarı aktararak ilke eşleşmelerinin karşılaştırmasını da yapma.

1. [Bağlan'Exchange Online PowerShell'e geri Exchange Online.](/powershell/exchange/connect-to-exchange-online-powershell)
2. [EAC DLP raporunu dışarı aktarın](/powershell/module/exchange/get-maildetaildlppolicyreport). Bu cmdlet'i kopyalayıp uygun değerleri ebilirsiniz:

```powershell
Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv"> 
```

3. Birleşik [DLP raporunu dışarı aktarın](/powershell/module/exchange/get-dlpdetailreport). Bu cmdlet'i kopyalayıp uygun değerleri ebilirsiniz:

```powershell
Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">  
```

## <a name="activate-your-migrated-policies"></a>Geçirilen ilkelerinizi etkinleştirme

Geçirilen ilkelerinizin çalışmalarından memnun olduktan sonra, bunları Zorunlu **olarak ayarlayın.**

1. Exchange Admin Center DLP konsolunu açın.
2. Kaynak ilkeyi devre dışı bırakma veya silme.
3. Uyumluluk [Microsoft 365](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP konsolunu açın ve düzenlemek için etkin yapmak istediğiniz ilkeyi seçin.
4. Durumu Aç olarak **değiştirme**.

## <a name="related-articles"></a>İlgili makaleler

- [Exchange Online kaybı önleme (DLP) ilkelerini engelleme](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [Exchange Online kaybı önleme (DLP) ilkelerini engelleme](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
