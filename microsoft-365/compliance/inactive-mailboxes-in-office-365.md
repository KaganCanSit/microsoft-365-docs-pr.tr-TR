---
title: Etkin olmayan posta kutuları hakkında daha fazla bilgi edinme
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
description: Posta kutusunu etkin olmayan bir posta kutusuna dönüştürerek eski çalışanlar için posta kutusu içeriğini korumayı öğrenin.
ms.openlocfilehash: 981675f64015e0320805e2be8e955cbd6d98769a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627227"
---
# <a name="learn-about-inactive-mailboxes"></a>Etkin olmayan posta kutuları hakkında daha fazla bilgi edinme

Kuruluşunuzun, kuruluştan ayrıldıktan sonra eski çalışanların e-postalarını tutması gerekebilir. Kuruluşunuzun bekletme gereksinimlerine bağlı olarak, çalışma sona erdikten sonra posta kutusu içeriğini birkaç ay veya yıl boyunca saklamanız veya posta kutusu içeriğini süresiz olarak saklamanız gerekebilir. E-postayı ne kadar süre saklamanız gerektiğinden bağımsız olarak, eski çalışanların posta kutusunu korumak için etkin olmayan posta kutuları oluşturabilirsiniz.

## <a name="what-are-inactive-mailboxes"></a>Etkin olmayan posta kutuları nedir?

Bir çalışan kuruluşunuzdan ayrıldığında (veya uzun süre izinli olduğunda) Microsoft 365 hesabını kaldırabilirsiniz. Çalışanın posta kutusu verileri, hesap kaldırıldıktan sonra 30 gün boyunca saklanır. Bu süre boyunca, hesabın işaretini kaldırarak posta kutusu verilerini kurtarmaya devam edebilirsiniz. 30 gün sonra veriler kalıcı olarak kaldırılır.

Ancak Microsoft 365 hesabı silinmeden önce posta kutusuna bir ayrı tutma uygulanırsa, posta kutusu etkin olmayan bir posta kutusuna dönüştürülür. Aşağıdaki bölümlerde, Microsoft 365 saklama ve eBulma saklama ile uygulanabilecek saklamalar hakkında bilgiler yer almaktadır.

Kuruluşunuzun yasal düzenlemeler veya başka nedenlerle eski çalışanların posta kutusu içeriğini saklaması gerektiğinde etkin olmayan posta kutuları kullanışlıdır. Bu belgede listelenen herhangi bir saklama türü, bir kullanıcı nesnesi silindiğinde posta kutusunun devre dışı bırakılmaya zorlanmasıyla birlikte, bunu bir Microsoft 365 bekletme ilkesi veya bekletme etiketleri uygulayarak gerçekleştirmenizi, [bekletmenin uygulandığını onaylamanızı](#confirming-a-hold-is-applied-to-a-mailbox) ve ardından ilgili Microsoft 365 hesabını kaldırmanızı öneririz. Bu noktada, etkin olmayan posta kutusunun içeriği, kullanıcı hesabı silinmeden önce belirtilen saklama süresi boyunca saklanır. 30 günlük bir süre boyunca ilgili kullanıcı hesabını yine de kurtarabilirsiniz, ancak 30 gün sonra, bekletme ilkesi veya bekletme etiketleri kaldırılana kadar posta kutusu Microsoft 365'te etkin olmayan bir posta kutusu olarak tutulur.

> [!IMPORTANT]
> Daha önce de belirttiğimiz gibi, etkin olmayan bir posta kutusu oluşturmak için Microsoft 365 saklamayı kullanmanızı öneririz:
> - Exchange yönetim merkezindeki In-Place Tutmalar artık kullanımdan kaldırılmıştır. 1 Temmuz 2020 itibarıyla yeni In-Place Tutmalar Exchange Online'da oluşturulamadı. 1 Ekim 2020 itibarıyla yerinde tutma süresi artık değiştirilemedi. In-Place Ayrı Tutma uygulanmış etkin olmayan posta kutuları yalnızca In-Place Ayrı Tutma kaldırılarak silinebilir. In-Place Ayrı Tutma'da bulunan etkin olmayan posta kutuları, ayrı tutma kaldırılana kadar korunmaya devam eder. In-Place Tutmaları kullanımdan kaldırma hakkında daha fazla bilgi için bkz. [Eski eKeşif araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md).
> 
> - [Bir](create-a-litigation-hold.md) posta kutusunda içeriği tutmak ve kullanıcı hesabı silindikten sonra etkin olmayan hale getirmek için alternatif bir yöntem olarak dava tutma desteği devam eder. Ancak, eski bir teknoloji olarak bunun yerine Microsoft 365 saklama kullanmanızı öneririz.

Aynı içerikte birden çok ayrı tutma olduğunda [, saklama ilkesi uygulanır](retention.md#the-principles-of-retention-or-what-takes-precedence) ve içerik en uzun süre korunur.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Bir saklamanın posta kutusuna uygulandığını onaylama

Microsoft 365 bekletme ilkesi, bekletme etiketleri, eBulma ayrı tutma, Dava tutma veya mevcut bir In-Place Ayrı Tutma uygulamanız fark etmeksizin, PowerShell kullanarak bekletmenin posta kutusuna başarıyla uygulandığını onaylayabilirsiniz. Saklamayı kısa süre önce yapılandırdıysanız, posta kutusuna uygulanana kadar beklemeniz gerekebilir.

Yanlışlıkla veya yanlışlıkla silinmesini önlemek için, kullanıcı hesabını silmeden önce saklamayı onaylamanızı öneririz. Ayrı tutma uygulanmazsa, posta kutusu etkin olmayan posta kutusuna dönüştürülemez.

Yönergeler için bkz. [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Etkin olmayan posta kutuları ve Microsoft 365 saklama

Posta kutusuna Bir Microsoft 365 bekletme ilkesi uygulanırsa veya posta kutusunda bir veya daha fazla e-posta öğesinde bekletme etiketi uygulanmışsa ve Microsoft 365 kullanıcı hesabı silinirse, posta kutusu etkin olmayan posta kutusuna dönüştürülür. Etkin olmayan posta kutusunun oluşturulması için:

- Bekletme ayarlarının [içeriği saklayacak veya içeriği saklayıp silecek şekilde yapılandırılması](retention-settings.md#settings-for-retaining-and-deleting-content) gerekir. Bekletme eylemi yalnızca içeriği silmek üzere yapılandırılmışsa, kullanıcı hesabı silindiğinde posta kutusu devre dışı kalmaz. Etkin olmayan posta kutuları için saklama ve silme seçeneğini kullanmanızı öneririz.

- Bekletme ayarları, Exchange posta kutusuyla ilişkili [bir bekletme konumuna](retention-settings.md#locations) uygulanmalıdır:
    - Exchange e-postası
    - Microsoft 365 Grupları
    - Skype Kurumsal
    - Exchange ortak klasörleri
    - Teams kanal iletileri
    - Teams sohbetleri
    - Teams özel kanal iletileri
    - Yammer topluluk iletileri
    - Yammer kullanıcı iletileri

Microsoft bekletme hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

Etkin olmayan posta kutusu oluşturmak için Microsoft 365 bekletme kullanılıyorsa, bekletme ilkesinden veya bekletme etiketlerinden elde tutma ayarları etkin olmayan posta kutusuna uygulanmaya devam edilir. Bu, bekletme ayarlarının içeriği saklayacak ve silecek şekilde yapılandırıldıysa, bekletme süresi dolduğunda öğelerin Kurtarılabilir Öğeler klasörüne taşınacağı ve ardından sonunda etkin olmayan posta kutusundan temizlendiği anlamına gelir. Bekletme ayarları silinmiş öğeler için yapılandırılmamışsa, kullanıcı tarafından kalıcı olarak silinmemiş olan öğeler (posta kutusu devre dışı bırakılmadan önce) Kurtarılabilir Öğeler klasörüne taşınmaz ve posta kutusu devre dışı bırakıldıktan sonra süresiz olarak korunur.

> [!TIP]
> *ComplianceTagHoldApplied* özelliğini kullanarak, bir posta kutusunun içeriği saklamak veya saklamak ve silmek için bir veya daha fazla bekletme etiketi uygulanmış öğeleri olup olmadığını belirleyebilirsiniz. Daha fazla bilgi için bkz. Bir [klasöre veya öğeye bekletme etiketi uygulandığından, beklemedeki posta kutularını tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Etkin olmayan posta kutularının elde tutulmasını yönetmek için uyarlamalı ilke kapsamları kullanma

[Uyarlamalı ilke kapsamlarıyla](retention.md#adaptive-or-static-policy-scopes-for-retention), saklama ayarlarını özellikle etkin olmayan posta kutularına uygulayabilirsiniz. Bu yapılandırmanın avantajları şunlardır:

- Kuruluşunuzun etkin çalışanlar ve eski çalışanlar için farklı saklama süreleri gerektiren düzenlemelerini veya ilkelerini karşılayabilirsiniz.

- Bekletme ayarlarını, kuruluşunuzun eski çalışanlara yönelik gereksinimini karşılamak için yalnızca gerekli olduğu sürece posta kutusu içeriğini koruyacak şekilde yapılandırabilirsiniz.

- Kuruluşunuzdaki etkin olmayan posta kutularına atanan bekletme ilkesini hızla belirleyebilirsiniz ve bu da gerekirse bekletme ayarlarının değiştirilmesini kolaylaştırır. 

- Etkin olmayan posta kutusunun özniteliklerine veya özelliklerine göre [uyarlamalı kapsamı](retention-settings.md#to-configure-an-adaptive-scope) dışlamak üzere yapılandırarak ilkeden kaldırabileceğinizden, etkin olmayan posta kutusunu kalıcı olarak silmek daha kolaydır. Aksi takdirde, [posta kutusunu silmeden](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox) önce [powershell Exchange Online](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy) kullanmanız gerekir.

> [!NOTE]
> Uyarlamalı ilke kapsamınızın yapılandırmasına bağlı olarak, etkin olmayan posta kutuları dahil edilebilir veya içermeyebilir.  Etkin olmayan posta kutularını uyarlamalı bir ilke kapsamından özellikle hedeflemek veya dışlamak için bkz. [Exchange e-posta ve Exchange ortak klasörleri için yapılandırma bilgileri](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Statik ilke kapsamlarını ve etkin olmayan posta kutularını kullanma

Microsoft 365 saklama ile [uyarlamalı ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) kullanmıyorsanız ve bunun yerine [statik bir kapsam](retention.md#adaptive-or-static-policy-scopes-for-retention) kullanıyorsanız aşağıdakileri göz önünde bulundurun:

- Statik ilke kapsamları, varsayılan **Tüm alıcılar** yapılandırmasını kullandığınızda etkin olmayan posta kutularını içerir, ancak [belirli eklemeler veya dışlamalar](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) için desteklenmez. Ancak, ilke uygulandığı sırada etkin posta kutusu olan bir alıcıyı dahil ederseniz veya dışlarsanız ve posta kutusu daha sonra devre dışı kalırsa, bekletme ayarları uygulanmaya veya dışlamaya devam eder. Bu senaryoda [, belirli ekleme ve dışlama sınırları](retention-limits.md) hala geçerlidir.
    
    > [!NOTE]
    > Bu, varsayılan **Tüm alıcılar** seçimine uygulanan statik bir kapsam kullanan tüm yeni Microsoft 365 bekletme ayarlarının otomatik olarak tüm mevcut etkin olmayan posta kutularını içereceği anlamına gelir.

- **Varsayılan Tüm alıcılar seçimini belirli alıcıları** içerecek şekilde değiştirirseniz, ilkenin bekletme ayarları artık etkin olmayan posta kutularına uygulanmaz ve bu da artık otomatik silme için uygun hale gelir.

- Etkin olmayan bir posta kutusuna uygulanan bir bekletme ilkesini serbest bırakmak istiyorsanız bkz. [Bekletme için ilke yayımlama](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Posta kutusunu devre dışı yapmak için Microsoft 365 saklamayı kullandığınızda, ilgili kullanıcı hesabını silmeden önce posta kutusunun kullanıcı asıl adını (UPN) değiştirmeyin veya kaldırmayın. Ayrıca, posta kutusunu devre dışı bırakmadan önce birincil SMTP adresini (UPN'den türetilen) değiştirmeyin veya bu e-posta adresini posta kutusuyla ilişkili ikincil SMTP adresleri listesinden kaldırmayın.
> 
> UPN veya e-posta adreslerini (bekletme ayarları uygulandığı sırada posta kutusuna atanmış olan) değiştirir ve sonra posta kutusunu devre dışı bırakılacak şekilde kullanıcı hesabını silerseniz, artık saklamanız gerekmiyorsa etkin olmayan posta kutusunu silemezsiniz. Bunun nedeni, bekletme ayarları başlangıçta posta kutusuna uygulandığında var olan posta kutusundan farklı bir UPN veya e-posta adresi (etkin olmayan posta kutusunu tanımlamak için) kullanarak ilkeden etkin olmayan posta kutusunu kaldıramamanızdır. Etkin olmayan posta kutularını silme hakkında daha fazla bilgi için bkz. [Office 365'de etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Etkin olmayan posta kutuları ve eBulma servis talebi tutmaları

Microsoft Purview uyumluluk portalı bir [eBulma olayıyla](./get-started-core-ediscovery.md) ilişkili bir ayrı tutma bir posta kutusuna yerleştirilirse ve posta kutusu veya kullanıcının hesabı silinirse, posta kutusu etkin olmayan bir posta kutusuna dönüşür. Ancak, posta kutusunun devre dışı olması için eBulma servis talebi tutmalarının kullanılmasını önermeyiz. Bunun nedeni, eBulma servis taleplerinin yasal bir sorunla ilgili belirli, zamana bağlı davalara yönelik olmasıdır. Bir noktada, yasal bir dava büyük olasılıkla sona erer ve servis talebiyle ilişkili tutmalar kaldırılır ve eBulma olayı kapatılır. Aslında, etkin olmayan bir posta kutusuna yerleştirilen bir ayrı tutma bir eBulma olayıyla ilişkilendirilirse ve bekletme serbest bırakılırsa veya eBulma olayı kapatılırsa (veya silinirse), etkin olmayan posta kutusu kalıcı olarak silinir. Ayrıca, zamana dayalı eBulma ayrı tutması oluşturamazsınız. Bu, etkin olmayan bir posta kutusunda bulunan içeriğin sonsuza kadar veya ayrı tutma kaldırılana ve etkin olmayan posta kutusu silinene kadar tutulduğunu gösterir. Bu nedenle, etkin olmayan posta kutuları için Microsoft 365 saklama kullanmanızı öneririz.

eBulma tutmaları ile Microsoft 365 saklama arasındaki farklar hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri veya eBulma tutmaları ne zaman kullanılır](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds)?

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Etkin olmayan posta kutuları ve otomatik olarak genişleten arşivler

Otomatik olarak genişletilen arşivle yapılandırılmış etkin olmayan bir posta kutusu kurtarılamaz veya geri yüklenemez. Otomatik olarak genişletilen bir arşivle etkin olmayan bir posta kutusundan veri kurtarmanın gerekli olduğu durumlarda, verileri posta kutusundan dışarı aktarmak ve sonra başka bir posta kutusuna aktarmak için içerik arama aracını kullanmanızı öneririz. Etkin olmayan bir posta kutusunda arama yapmak ve arama sonuçlarını dışarı aktarmak için adım adım yönergeler için bkz:

- [İçerik arama](content-search.md)

- [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Etkin olmayan posta kutuları ve Exchange MRM saklama ilkeleri

Kullanıcı hesabı silindiğinde Exchange bekletme ilkesi (Exchange Online'daki Microsoft Mesajlaşma Kayıt Yönetimi veya MRM özelliği) etkin olmayan bir posta kutusu oluşturmaz.

Ancak, bu MRM bekletme ilkesi devre dışı bırakılmadan önce bir posta kutusuna uygulandıysa, tüm silme ilkeleri ( **Silme** eylemiyle yapılandırılmış MRM bekletme etiketleri) etkin olmayan posta kutusunda işlenmeye devam eder. Bu, MRM silme ilkesiyle etiketlenmiş öğelerin saklama süresi dolduğunda [Kurtarılabilir Öğeler klasörüne](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) taşınacağı anlamına gelir. Saklama süresi dolduğunda bu öğeler etkin olmayan posta kutusundan temizlenir. Etkin olmayan posta kutusu için ayrı tutma süresi belirtilmezse, Öğeleri Kurtar klasöründeki öğeler süresiz olarak korunur.

Buna karşılık, etkin olmayan bir posta kutusuna atanan MRM saklama ilkesine dahil edilen tüm arşiv ilkeleri ( **MoveToArchive** eylemiyle yapılandırılmış MRM bekletme etiketleri) yoksayılır. Bu, arşiv ilkesiyle etiketlenmiş etkin olmayan posta kutusunda bulunan öğelerin saklama süresi dolduğunda birincil posta kutusunda kaldığı anlamına gelir. Bunlar arşiv posta kutusuna veya arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınmaz. Süresiz olarak tutulacaklardır.

## <a name="next-steps"></a>Sonraki adımlar

Posta kutusunu devre dışı yapmak ve kurtarmak, geri yüklemek ve silmek gibi yönetmek için bkz [. Etkin olmayan posta kutuları oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md).
