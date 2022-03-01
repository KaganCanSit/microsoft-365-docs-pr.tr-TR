---
title: Etkin olmayan posta kutuları hakkında bilgi alın
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 1fbd74e8-7a60-4157-afe8-fe79f05d2038
ms.custom:
- seo-marvel-apr2020
description: Posta kutusunu etkin olmayan bir posta kutusuna dönüştürerek eski çalışanların posta kutusu içeriğini korumayı öğrenin.
ms.openlocfilehash: 72d048bc99876c0f252feffe3159d3ce01303028
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010859"
---
# <a name="learn-about-inactive-mailboxes"></a>Etkin olmayan posta kutuları hakkında bilgi alın

Kuruluşdan ayrıldıktan sonra, eski çalışanların e-postalarını tutmaları gerekiyor olabilir. Kuruluşun bekletme gereksinimlerine bağlı olarak, çalışma sona erdikten sonra birkaç ay veya yıl süreyle posta kutusu içeriğini tutmanız veya posta kutusu içeriğini süresiz olarak saklamanız gerekir. E-postayı ne kadar süre tutmanız gerekene bakılmaksızın, eski çalışanların posta kutusunu tutmak için etkin olmayan posta kutuları oluşturabilirsiniz.

## <a name="what-are-inactive-mailboxes"></a>Etkin olmayan posta kutuları nedir?

Bir çalışan organizasyondan ayrıldığında (veya uzun bir süre izne ayrıldığında) bu çalışanın Microsoft 365 kaldırabilirsiniz. Hesabın kaldırılmasının ardından çalışanın posta kutusu verileri 30 gün boyunca korunur. Bu süre boyunca, hesabın posta kutusu verilerini geri alamadan kurtarabilirsiniz. 30 gün sonra, veriler kalıcı olarak kaldırılır.

Ancak hesabı silmeden önce posta kutusuna bir Microsoft 365 uygulanırsa, posta kutusu etkin olmayan bir posta kutusuna dönüştürülür. Aşağıdaki bölümlerde, bekletmelerle ve eBulma bekletmeleriyle Microsoft 365 hakkında bilgi vardır.

Etkin olmayan posta kutuları, kuruluşta düzenleyici veya başka nedenlerle eski çalışanların posta kutusu içeriğini tutması gereken zaman yararlı olur. Bu belgede listelenen her tür saklama, kullanıcı nesnesi silindiğinde posta kutusunun devre dışı tutulmasını zorlar ama bunun için bir Microsoft 365 bekletme ilkesi veya bekletme etiketi uygulamanız[,](#confirming-a-hold-is-applied-to-a-mailbox) saklamanın uygulandığını onaylamanız ve sonra ilgili Microsoft 365 hesabını kaldırmanız önerilir. Bu noktada, etkin olmayan posta kutusunun içeriği kullanıcı hesabı silinmeden önce belirtilen bekletme süresi boyunca korunur. Buna karşılık gelen kullanıcı hesabını 30 gün süreyle kurtarabilirsiniz, ancak 30 gün sonra, bekletme ilkesi veya bekletme etiketleri kaldırılana kadar posta kutusu Microsoft 365'te etkin olmayan posta kutusu olarak korunur.

> [!IMPORTANT]
> Daha önce de belirttiğimiz gibi, etkin olmayan bir posta Microsoft 365 için bekletmeyi kullanmanızı öneririz:
> - In-Place yönetim merkezinde Exchange 10 10 10 artık kaldırıldı. 1 Temmuz 2020'den In-Place 1 Temmuz 2020'den Exchange Online. 1 Ekim 2020'den sonra yerinde tutma süresi değiştirilemez. Tutma Tutma uygulanmış etkin olmayan In-Place posta kutuları yalnızca 1/6 /In-Place kaldırılarak silinebilir. Tutmada olan ve etkin olmayan In-Place, tutma kaldırılana kadar korunmaya devam eder. Eski eBulma araçlarının In-Place hakkında daha fazla bilgi için bkz. [Eski eBulma araçlarının emeklilik](legacy-ediscovery-retirement.md).
> 
> - [Bir kullanıcı hesabı](create-a-litigation-hold.md) silindikten sonra posta kutusunda içeriği tutmak ve devre dışı kalmak için alternatif bir yöntem olarak mahkeme tutma destekleri devam ediyor. Bununla birlikte, daha eski bir teknoloji olarak bu Microsoft 365 öneririz.

Aynı içerikte birden çok bekletme olduğunda, bekletme ilkesi uygulanır [](retention.md#the-principles-of-retention-or-what-takes-precedence) ve içerik en uzun süre boyunca korunur.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Posta kutusuna basılı tutmanın uygulandığını onaylama

Microsoft 365 bekletme ilkesi, bekletme etiketleri, eBulma bekletme, Mahkeme tutma veya var olan bir In-Place Bekletme varsa, PowerShell kullanılarak posta kutusuna başarıyla uygulandığını onaylayın. Beklemeyi yakın zamanda yapılandırdıysanız, posta kutusuna uygulanana kadar beklemenız gerekiyor olabilir.

Yanlışlıkla veya yanlışlıkla silinmesini önlemek için, kullanıcı hesabını silmezken önce  basılı tutma işlemini onaylamanızı öneririz. Tutma uygulanmazsa, posta kutusu etkin olmayan bir posta kutusuna dönüştürülmesiz.

Yönergeler için bkz[. Bir posta kutusuna yerleştirilen tutma Exchange Online belirleme](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Etkin olmayan posta kutuları ve Microsoft 365 bekletme

Bir Microsoft 365 kutusuna bir bekletme ilkesi uygulanmışsa veya posta kutusunda bir veya birden çok e-posta öğesine bekletme etiketi uygulanmışsa ve Microsoft 365 kullanıcı hesabı silinirse, posta kutusu etkin olmayan posta kutusuna dönüştürülür. Etkin olmayan posta kutusunun oluşturulacak olması için:

- Bekletme ayarlarının içeriği korumak veya içeriği [korumak ve sonra da silmek üzere yapılandırılması gerekir](retention-settings.md#settings-for-retaining-and-deleting-content). Bekletme eylemi yalnızca içeriği secek şekilde yapılandırılmışsa, kullanıcı hesabı silindiğinde posta kutusu devre dışı olmayacaktır. Etkin olmayan posta kutuları için, koruma ve ardından silme seçeneğini kullanmanızı öneririz.

- Bekletme ayarları, bir müşteri posta [kutusuyla ilişkilendirilmiş](retention-settings.md#locations) bir bekletme Exchange uygulanmalıdır:
    - Exchange-posta gönderme
    - Microsoft 365 Grupları
    - Skype Kurumsal
    - Exchange klasörleri taşıma
    - Teams iletilerini gönderme
    - Teams sohbetleri geri
    - Teams kanal iletilerini gönderme
    - Yammer iletilerini gönderme
    - Yammer iletilerini gönderme

Microsoft bekletme hakkında daha fazla bilgi için bkz. Bekletme [ilkeleri ve bekletme etiketleri hakkında bilgi.](retention.md)

Etkin Microsoft 365 olmayan bir posta kutusu oluşturmak için bekletme kullanılıyorsa, bekletme ilkesi veya bekletme etiketlerinden gelen bekletme ayarları etkin olmayan posta kutusuna uygulanabilir. Başka bir ifadeyle, bekletme ayarları içeriği alıkoymak ve sonra da silmek üzere yapılandırılırsa, bekletme süresi dolduğunda öğeler Kurtarılabilir Öğeler klasörüne taşınır ve daha sonra etkin olmayan posta kutusundan temizlenebilir. Bekletme ayarları silinmiş öğelere yapılandırılmamışsa, kullanıcı tarafından kalıcı olarak silinmemiş olan öğeler (posta kutusu devre dışı hale gelmeden önce) Kurtarılabilir Öğeler klasörüne taşınmaz ve posta kutusu devre dışı olduğunda süresiz olarak korunur.

> [!TIP]
> Bir posta kutusunda, korumak üzere bir veya daha fazla bekletme etiketi uygulanmış öğe olup olmadığını belirlemek için *ComplianceTagHoldApplied* özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz [. Klasöre veya öğeye bekletme etiketi uygulandığı için tanımlayıcı posta kutuları saklamaya devam ediyor](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Etkin olmayan posta kutularını bekletmeyi yönetmek için uyarlanabilir ilke kapsamlarını kullanma

[Uyarlanabilir ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) sayesinde, bekletme ayarlarını özel olarak etkin olmayan posta kutularına uygulayabilirsiniz. Bu yapılandırmanın avantajları şunlardır:

- Etkin çalışanlar ve eski çalışanlar için farklı bekletme süresi gerektiren kuruluş düzenlemelerine veya ilkelerine uygun şekilde devam edin.

- Bekletme ayarlarını, yalnızca kuruluşun eski çalışanlara olan gereksinimini karşılamak için gereken sürece posta kutusu içeriğini korumak üzere yapılandırabilirsiniz.

- Kuruluşun etkin olmayan posta kutularına atanan bekletme ilkesini hızlı bir şekilde tanımlayabilirsiniz ve bu da gerekirse bekletme ayarlarının değişmesini kolaylaştırır. 

- Etkin olmayan posta kutusunu kalıcı olarak silmek daha kolaydır çünkü uyarlanabilir kapsamı, etkin olmayan posta kutusunun özniteliklerine veya [](retention-settings.md#to-configure-an-adaptive-scope) özelliklerine göre uyarlanabilir kapsamı yapılandırarak ilkeden kaldırabilirsiniz. Aksi takdirde, posta kutusunu [Exchange Online önce Exchange Online PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy) [kullanabilirsiniz](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox).

> [!NOTE]
> Uyarlanabilir ilke kapsamınıza bağlı olarak, etkin olmayan posta kutuları dahil olabilir veya hiç dahil değildir.  Etkin olmayan posta kutularını özel olarak uyarlanabilir bir ilke kapsamına dahil etmek veya dışarıda tutmak için, E-postayı ve ortak Exchange yönelik [yapılandırma bilgilerini Exchange bakın](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Statik ilke kapsamlarını ve etkin olmayan posta kutularını kullanma

Bağımsız bekletmeyle uyarlanabilir [ilke kapsamlarını](retention.md#adaptive-or-static-policy-scopes-for-retention) Microsoft 365 bunun [yerine statik bir](retention.md#adaptive-or-static-policy-scopes-for-retention) kapsam kullanıyorsanız, aşağıdakilere dikkat edin:

- Statik ilke kapsamları, varsayılan Tüm alıcılar yapılandırmasını kullanıyor ancak belirli eklemeler  veya dışlamalar için desteklenmiyor olduğunda etkin olmayan [posta kutularını içerir](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions). Bununla birlikte, ilke uygulandığı sırada etkin posta kutusu olan bir alıcıyı dahil eder veya hariç ayarlarsanız ve posta kutusu daha sonra devre dışı bırakılırsa, bekletme ayarları uygulanmaya veya dışarıda bırakılır. Bu senaryoda, belirli [ekleme ve dışlama sınırları yine](retention-limits.md) de geçerlidir.
    
    > [!NOTE]
    > Bu, varsayılan Tüm alıcılar seçimine Microsoft 365 statik kapsam kullanan tüm yeni bekletme ayarlarının otomatik olarak var olan tüm etkin olmayan posta  kutularını içermesi anlamına da gelir.

- Varsayılan Tüm alıcılar seçimini belirli alıcıları içerecek  şekilde değiştirirseniz, ilkeye yönelik bekletme ayarları artık etkin olmayan posta kutularına uygulanmayacak ve artık otomatik silme için uygun olacak.

- Etkin olmayan bir posta kutusuna uygulanan bir bekletme ilkesi serbest bırakmak için bkz. [Bekletme için bir ilke bırakma](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Bir posta Microsoft 365 etkin olmayan yapmak için bekletme kullanırsanız, ilgili kullanıcı hesabını smeden önce posta kutusunun kullanıcı asıl adını (UPN) değiştirme veya kaldırmayın. Buna ek olarak, birincil SMTP adresini (UPN'den türetilen SMTP adresi) değiştirme veya posta kutusunu devre dışı hale göndermeden önce posta kutusuyla ilişkilendirilmiş ikincil SMTP adresleri listesinden bu e-posta adresini kaldırın.
> 
> UPN'sini veya e-posta adreslerini (bekletme ayarları uygulandığında posta kutusuna atanmış olan) değiştirir ve ardından posta kutusunu devre dışı tutmak için kullanıcı hesabını silersanız, artık saklamanız gerekmiyorsa etkin olmayan posta kutusunu silemezsiniz. Bunun nedeni, etkin olmayan posta kutusunu ilkeden kaldırmak için, bekletme ayarları başlangıçta posta kutusuna uygulandığında var olandan farklı bir UPN veya e-posta adresi (etkin olmayan posta kutusunu tanımlamak için) kullanmanızdır. Etkin olmayan posta kutularını silme hakkında daha fazla bilgi için bkz. Etkin [olmayan posta kutusunu şu Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Etkin olmayan posta kutuları ve eKbulma durumunda 10 ayrım

Microsoft 365 uyumluluk merkezi'daki [bir eBulma](./get-started-core-ediscovery.md) durumuyla ilişkilendirilmiş bir tutma, bir posta kutusuna yerleştirilirse ve posta kutusu veya kullanıcının hesabı silinirse, posta kutusu etkin olmayan bir posta kutusuna olur. Bununla birlikte, bir posta kutusunu devre dışı yapmak için eKbulma olaylarının esnasıda kalmalarını önerilmez. Bunun nedeni eBulma servis durumlarının bir yasal sorunla ilgili belirli, zaman bağlantılı durumlar için tasarlanmış olmasıdır. Bir noktada, büyük olasılıkla bir dava sona erer ve davayla ilişkilendirilmiş esnalar kaldırılır ve eBulma vakası kapatılır. Aslında, etkin olmayan bir posta kutusuna yerleştirilen bir tutma bir eBulma durumuyla ilişkilendirilmişse ve tutma serbest bırakılırsa veya eBulma vakası kapatılır (veya silinirse), etkin olmayan posta kutusu kalıcı olarak silinir. Ayrıca, zaman tabanlı bir eBulma ayrımı oluşturabilirsiniz. Bu, etkin olmayan posta kutuları içeriğinin sonsuza kadar veya tutma kaldırılana ve etkin olmayan posta kutusu silinene kadar korunacakları anlamına gelir. Bu nedenle, etkin olmayan Microsoft 365 kutuları için bekletmeyi devre dışı tutmanızı öneririz.

eBulma bekletmeleri ile bekletme arasındaki farklar hakkında daha fazla Microsoft 365 için bkz. Bekletme ilkelerinin ve bekletme etiketlerinin veya [eBulma](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds) bekletmeleri ne zaman kullanılır?

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Etkin olmayan posta kutuları ve otomatik genişleyen arşivler

Otomatik genişleyen bir arşivle yapılandırılmış etkin olmayan posta kutusu kurtarılamaz veya geri alınılamaz. Otomatik genişleyen bir arşivle etkin olmayan posta kutusundan verileri kurtarmanın gerekli olduğu durumlarda, içerik arama aracını kullanarak verileri posta kutusundan dışarı aktarmanızı ve ardından başka bir posta kutusuna aktarmanızı öneririz. Etkin olmayan posta kutusunda arama yapmak ve arama sonuçlarını dışarı aktarmaya ilişkin adım adım yönergeler için bkz:

- [İçerik arama](content-search.md)

- [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Etkin olmayan posta kutuları ve MRM Exchange ilkeleriyle ilgili sorun

Kullanıcı hesabı Exchange bekletme ilkesi (Exchange Online'te İleti Kayıtları Yönetimi veya MRM özelliği) uygulamak etkin olmayan bir posta kutusu oluşturmaz.

Bununla birlikte, bu MRM bekletme ilkesi posta kutusuna devre dışı gitmeden önce uygulanmışsa, tüm silme ilkeleri ( **Delete** eylemiyle yapılandırılmış MRM bekletme etiketleri) etkin olmayan posta kutusunda işlemeye devam eder. Bu, bekletme süresi sona erdiğinde MRM silme ilkesiyle etiketlenen öğelerin Kurtarılabilir Öğeler [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) klasörüne taşınacak olduğu anlamına gelir. Bu öğeler, tutma süresi sona erdiğinde etkin olmayan posta kutusundan temiz olur. Etkin olmayan posta kutusu için bir tutma süresi belirtilmezse, Öğeleri Kurtar klasöründeki öğeler süresiz olarak korunur.

Buna karşılık, etkin olmayan bir posta kutusuna atanmış MRM bekletme ilkesinde yer alan tüm arşiv ilkeleri ( **MoveToArchive** eylemiyle yapılandırılmış MRM bekletme etiketleri) yoksayılır. Bu, etkin olmayan ve arşiv ilkesiyle etiketlenen öğelerin bekletme süresi dolduğunda birincil posta kutusunda kalacakları anlamına gelir. Bu öğeler arşiv posta kutusuna veya arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınmaz. Bunlar süresiz olarak korunurlar.

## <a name="next-steps"></a>Sonraki adımlar

Posta kutusunu devre dışı yapmak ve kurtarmak, geri yüklemek ve silmek gibi yönetmek için bkz. Etkin olmayan posta kutuları [oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md).
