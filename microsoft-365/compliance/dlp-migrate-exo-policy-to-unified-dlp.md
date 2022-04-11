---
title: Exchange Online veri kaybı önleme ilkelerini Uyumluluk merkezine taşıma
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
description: Exchange çevrimiçi veri kaybı önleme ilkelerinizi planlamayı ve Microsoft 365 DLP'ye geçirmeyi öğrenin.
ms.openlocfilehash: c6b941a0dd1f66e2f44494fded9ba47e8c3d7230
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760877"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Exchange Online veri kaybı önleme ilkelerini Uyumluluk merkezine taşıma

[Exchange Online veri kaybı önleme (DLP) ilkeleri](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) kullanım dışı bırakılıyor. Exchange Online DLP de dahil olmak üzere [çok daha zengin](dlp-learn-about-dlp.md) DLP işlevleri[, Microsoft 365 Uyumluluk merkezinde](https://compliance.microsoft.com/datalossprevention?viewid=policies) sunulur. Exchange Online DLP ilkelerinizi yöneteceğiniz Uyumluluk merkezine getirmenize yardımcı olması için DLP ilkesi geçiş sihirbazını kullanabilirsiniz.

Geçiş sihirbazı, DLP ilkelerinizin yapılandırmasını Exchange okuyup Uyumluluk merkezinde yinelenen ilkeler oluşturarak çalışır. Varsayılan olarak sihirbaz, ilkelerin yeni sürümlerini **Test** modunda oluşturur, böylece herhangi bir eyleme gerek kalmadan ortamınızdaki etkilerini görebilirsiniz. Uyumluluk merkezi sürümlerine tamamen geçiş yapmaya hazır **_olduğunuzda şunları yapın_**:

1. Exchange Yönetim Merkezi'nde (EAC) kaynak ilkesini devre dışı bırakın veya silin.
1. İlkenin Uyumluluk merkezi sürümünü düzenleyin ve durumunu **Test'ten** **Zorla** olarak değiştirin.

> [!WARNING]
> Uyumluluk merkezi sürümünü Her iki ilke kümesini de **zorla** olarak ayarlamadan önce EAC'deki kaynak ilkeyi silmez veya devre dışı bırakmazsanız, her iki ilke kümesi de eylemleri zorunlu kılmaya çalışır ve yinelenen olaylar alırsınız. **_Bu desteklenmeyen bir yapılandırmadır._**

Geçiş sihirbazı yalnızca EXO ilkelerini ve ilişkili posta akışı kurallarını geçirir. Tek başına Exchange posta akışı kuralları geçirilmez.

## <a name="migration-workflow"></a>Geçiş iş akışı

DLP ilkelerini Exchange'dan Uyumluluk merkezindeki Birleşik DLP yönetim konsoluna geçirmenin dört aşaması vardır.

1. Geçişe hazırlanma
    1. Yinelenen işlevler için Exchange Online (EXO) DLP ilkelerinizi ve Uyumluluk Merkezi DLP ilkelerinizi değerlendirin ve karşılaştırın.
    1. Hangi EXO DLP ilkelerini tam olarak olduğu gibi getirmek istediğinize karar verin, bunları geçirmek için sihirbazı kullanabilirsiniz.
    1. Exchange yönetim merkezinde hangi EXO DLP ilkelerini birleştirmek ve birleştirmek istediğinize karar verin, sonra bunları Uyumluluk merkezine getirmek için geçiş sihirbazını kullanın.
1. Geçişi gerçekleştirme - sihirbazı kullanma
1. Test ve doğrulama - sonuçları inceleme
1. Geçirilen ilkeleri etkinleştirme

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="licensing-and-versions"></a>Lisanslama ve sürümler

DLP ilkelerini geçirmeye başlamadan önce[, Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) ve tüm eklentileri onaylamanız gerekir.

İlke geçiş sihirbazına erişmek ve bunu kullanmak için bu aboneliklerden veya eklentilerden birine sahip olmanız gerekir

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 uyumluluğu
- Microsoft 365 A5 uyumluluğu
- Microsoft 365 E5 bilgi koruma ve idare
- Microsoft 365 A5 bilgi koruma ve idare

DLP lisans gereksinimlerinin ayrıntılı listesi için bkz. [Microsoft 365 Güvenlik & uyumluluğu, veri kaybı önleme için lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>İzinler

Geçiş sihirbazını çalıştırmak için kullandığınız hesabın hem Exchange Yönetici Konsolu DLP sayfasına hem de Uyumluluk merkezindeki Birleşik DLP konsoluna erişimi olmalıdır.

## <a name="prepare-for-migration"></a>Geçişe hazırlanma

1. DLP, Uyumluluk merkezi DLP konsolu veya Exchange Yönetim merkezi DLP konsolu hakkında bilgi sahibi değilseniz, ilke geçişini denemeden önce kendinizi tanımanız gerekir.
    1. [Exchange Online veri kaybı önleme (DLP) ilkeleri](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [uç nokta veri kaybı önleme Microsoft 365 hakkında bilgi edinin](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [DLP ilkesi oluşturma, test ve ayarlama](create-test-tune-dlp-policy.md)
1. Aşağıdaki soruları sorarak Exchange DLP ve Uyumluluk merkezi ilkelerinizi değerlendirin:

|Soru|Eylem|Geçiş yordamı|
|---|---|---|
|İlke hala gerekli mi?|Aksi takdirde, silin veya devre dışı bırakın|geçiş yapma|
|Diğer Exchange veya Uyumluluk merkezi DLP ilkeleriyle çakışıyor mu?|Evet ise, çakışan ilkeleri birleştirebilir misiniz?|- Başka bir Exchange ilkesiyle çakışıyorsa, Exchange Yönetim merkezinde birleştirilmiş DLP ilkesini el ile oluşturun ve geçiş sihirbazını kullanın. </br> - Mevcut bir Uyumluluk Merkezi ilkesiyle çakışıyorsa, mevcut Uyumluluk merkezi ilkesini eşleşecek şekilde değiştirebilirsiniz, Exchange sürümünü geçirmeyin|
|Exchange DLP ilkesi sıkı kapsamlı mı ve iyi tanımlanmış koşullara, eylemlere, eklemelere ve dışlamalara sahip mi?|Evet ise, sihirbazla geçiş yapmak için iyi bir adaydır, ilkeyi not alın, böylece daha sonra silmek için geri gelmeyi unutmayın|sihirbazla geçiş|

## <a name="migration"></a>Geçiş

Tüm Exchange ve Uyumluluk merkezi DLP ilkelerinizi ihtiyaç ve uyumluluk açısından değerlendirdikten sonra geçiş sihirbazını kullanabilirsiniz.

1. [Microsoft 365 Uyumluluk merkezi](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP konsolunu açın.
2. Geçirilebilen Exchange DLP ilkesi varsa, sayfanın en üstünde size haber veren bir başlık görünür.
3. Geçiş sihirbazını açmak için başlıkta **İlkeleri geçir'i** seçin. Tüm Exchange DLP ilkeleri listelenir. Önceden geçirilen ilkeler seçilemez.
4. Geçirmek istediğiniz ilkeleri seçin. Bunları tek tek veya aşamalı bir yaklaşım kullanarak gruplar halinde ya da aynı anda geçirebilirsiniz. **İleri**'yi seçin.
5. Uyarılar veya iletiler için açılır pencere bölmesini gözden geçirin. Devam etmeden önce sorunları çözün.
6. Yeni Uyumluluk merkezi ilkesinin **etkin,** **test** veya **devre dışı** olarak oluşturulmasını istediğiniz modu seçin.  Varsayılan değer **Test'tir**. **İleri**'yi seçin.
7. İsterseniz, diğer birleşik DLP konumları için Exchange DLP ilkelerini temel alan daha fazla ilke oluşturabilirsiniz. Bu, geçirilen Exchange ilkesi için yeni bir birleşik DLP ilkesine ve burada seçtiğiniz diğer konumlar için yeni bir birleşik DLP ilkesine neden olur.

   > [!IMPORTANT]
   > Cihazlar, SharePoint, OneDrive, Şirket içi, MCAS veya Teams sohbet ve kanal iletileri gibi diğer DLP konumları tarafından desteklenmeyen tüm Exchange DLP ilkesi koşulları ve eylemleri ek ilkeden bırakılır. Ayrıca, diğer konumlar için yapılması gereken ön çalışmalar da vardır. Bkz:
   >
   > - [uç nokta veri kaybı önleme Microsoft 365 hakkında bilgi edinin](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
   > - [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
   > - [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
   > - [şirket içi tarayıcı Microsoft 365 veri kaybı önleme hakkında bilgi edinin](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
   > - [Şirket içi tarayıcıda veri kaybı önleme ile Kullanmaya başlayın](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
   > - [Microsoft 365 veri kaybı önleme şirket içi tarayıcısını kullanma](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
   > - [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)

8. Geçiş sihirbazı oturum ayarlarını gözden geçirin. **İleri**'yi seçin.
9. Geçiş raporunu gözden geçirin. Exchange posta akışı kurallarını içeren hatalara dikkat edin. Bunları düzeltebilir ve ilişkili ilkeleri yeniden dağıtabilirsiniz.

Geçirilen ilkeler artık Uyumluluk merkezi DLP konsolundaki DLP ilkeleri listesinde görünür.

## <a name="common-errors-and-mitigation"></a>Yaygın hatalar ve risk azaltma

|Hata iletisi|Neden|Azaltma/Önerilen adımlar|
|---|---|---|
|Adlı `<Name of the policy>` bir uyumluluk ilkesi senaryolarda `Dlp`zaten var.|Bu ilke geçişi daha önce yapılmış ve aynı oturumda yeniden atılmış olabilir|Geçiş için kullanılabilen ilkelerin listesini güncelleştirmek için oturumu yenileyin. Daha önce geçirilen tüm ilkeler durumunda olmalıdır `Already migrated` .|
|Adlı `<Name of the policy>` bir uyumluluk ilkesi senaryolarda `Hold`zaten var.|Aynı kiracıda aynı ada sahip bir bekletme ilkesi var.|- EAC'deki DLP ilkesini farklı bir adla yeniden adlandırın. </br> - Etkilenen ilke için geçişi yeniden deneyin.|
|`DLP-group@contoso.com` bir dağıtım grubu veya posta özellikli bir güvenlik grubu olduğundan, Paylaşılan koşulu için değer olarak kullanılamaz. Belirli grupların üyelerine göre etkinlikleri algılamak için Koşulun Üyesi Tarafından Paylaşılan'ı kullanın.|Aktarım kuralları, grupların `sender is` koşulda kullanılmasına izin verir, ancak birleştirilmiş DLP buna izin vermez.|Tüm grup e-posta adreslerini koşuldan kaldırmak için taşıma kuralını güncelleştirin `sender is` ve gerekirse grubu koşula `sender is a member of` ekleyin. Etkilenen ilke için geçişi yeniden deneyin|
|Alıcı `DLP-group@contoso.com`bulunamadı. Yeni oluşturulduysa, işlemi bir süre sonra yeniden deneyin. Silindiyse veya süresi dolduysa lütfen geçerli değerlerle sıfırlayın ve yeniden deneyin.|veya koşulunda `sender is a member of` `recipient is a member of` kullanılan grup adresinin süresi dolmuş veya geçersiz olabilir.|- Exchange yönetim merkezindeki aktarım kuralındaki tüm geçersiz grup e-posta adreslerini kaldırın/değiştirin. </br> - Etkilenen ilke için geçişi yeniden deneyin.|
|Koşulda `FromMemberOf` belirtilen değer posta özellikli güvenlik grubu olmalıdır.|Aktarım kuralları, tek tek kullanıcıların koşulda `sender is a member of` kullanılmasına izin verir, ancak birleştirilmiş DLP buna izin vermez.|- Taşıma kuralını güncelleştirerek koşuldan `sender is a member of` tüm bireysel kullanıcı e-posta adreslerini kaldırın ve gerekirse kullanıcıları koşula `sender is` ekleyin. </br> - Etkilenen ilke için geçişi yeniden deneyin.|
|Koşulda `SentToMemberOf` belirtilen değer posta özellikli güvenlik grubu olmalıdır.|Aktarım kuralları, tek tek kullanıcıların koşul altında `recipient is a member of` kullanılmasına izin verir, ancak birleştirilmiş DLP buna izin vermez.|- Taşıma kuralını güncelleştirerek koşuldan `recipient is a member of` tüm bireysel kullanıcı e-posta adreslerini kaldırın ve gerekirse kullanıcıları koşula `recipient is` ekleyin. </br> - Etkilenen ilke için geçişi yeniden deneyin.|
|parametresinin `<Name of condition>` kullanılması yalnızca Exchange için desteklenir. Bu parametreyi kaldırın veya yalnızca Exchange konumu açın.|Uyumluluk merkezinde, belirtilen koşulun desteklenmediği SPO/ODB/Teams gibi diğer konumlarla aynı ada sahip başka bir ilke olması olasıdır.|Exchange yönetim merkezinde DLP ilkesini yeniden adlandırın ve geçişi yeniden deneyin.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test ve doğrulama <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

İlkelerinizi test edin ve gözden geçirin.

1. [DLP ilkesi](create-test-tune-dlp-policy.md#test-a-dlp-policy) test yordamlarını izleyin.
2. [etkinlik gezgininde](data-classification-activity-explorer.md) ilke tarafından oluşturulan olayları gözden geçirin.

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Exchange Yönetim Merkezi DLP ile Microsoft 365 Birleşik DLP arasındaki ilke eşleşmelerini gözden geçirin

Geçirilen ilkelerin beklendiği gibi davrandığından emin olmak için, raporları her iki yönetim merkezinden dışarı aktarabilir ve ilke eşleşmelerinin karşılaştırmasını yapabilirsiniz.

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).
2. [EAC DLP raporunu](/powershell/module/exchange/get-maildetaildlppolicyreport) dışarı aktarın. Bu cmdlet'i kopyalayıp uygun değerleri ekleyebilirsiniz:

   ```powershell
   Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

3. [Birleşik DLP raporunu](/powershell/module/exchange/get-dlpdetailreport) dışarı aktarın. Bu cmdlet'i kopyalayıp uygun değerleri ekleyebilirsiniz:

   ```powershell
   Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

## <a name="activate-your-migrated-policies"></a>Geçirilen ilkelerinizi etkinleştirme

Geçirilen ilkelerinizin nasıl çalıştığından memnun olduktan sonra bunları **Zorla** olarak ayarlayabilirsiniz.

1. Exchange Yönetim Merkezi DLP konsolunu açın.
2. Kaynak ilkesini devre dışı bırakın veya silin.
3. [Microsoft 365 Uyumluluk merkezi](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP konsolunu açın ve düzenlemek için etkin hale getirmek istediğiniz ilkeyi seçin.
4. Durumu **Aç** olarak değiştirin.

## <a name="related-articles"></a>İlgili makaleler

- [Exchange Online veri kaybı önleme (DLP) ilkeleri](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Etkinlik gezgini ile Kullanmaya başlayın](data-classification-activity-explorer.md)
- [DLP ilkesi oluşturma, test ve ayarlama](create-test-tune-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [Exchange Online veri kaybı önleme (DLP) ilkeleri](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
