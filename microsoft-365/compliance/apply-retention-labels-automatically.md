---
title: Bekletme etiketini otomatik olarak uygulama
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
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: İhtiyacınız olanı korumak ve istemediğinizleri silmek için etiketleri otomatik olarak uygulayabilmeniz için otomatik etiketleme bekletme ilkeleri oluşturun
ms.openlocfilehash: 87328b69f2649a1e6a6c6755892e17e7c04aac53
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128843"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>İçeriği korumak veya silmek için otomatik olarak bekletme etiketi uygulama

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Bu senaryo, SharePoint belge kümesi veya kitaplığı ya da Exchange bir klasör gibi düzenleme yapısı için [düzenleme kayıtları](records-management.md#records) veya varsayılan etiketler için desteklenmez. Bu senaryolar [için yayımlanmış bir bekletme etiketi ilkesi](create-apply-retention-labels.md) gerekir.

[Bekletme etiketlerinin](retention.md) en güçlü özelliklerinden biri, bunları belirtilen koşullarla eşleşen içeriğe otomatik olarak uygulayabilmektir. Bu durumda kuruluşunuzdaki kişilerin bekletme etiketlerini uygulaması gerekmez. Microsoft 365 işi onlar için yapar.

Bekletme etiketlerini otomatik uygulama güçlü bir nedendir çünkü:

- Kullanıcılarınızı tüm sınıflandırmalarınız hakkında eğitmeniz gerekmez.
- Tüm içeriği doğru sınıflandırmak için kullanıcılara güvenmeniz gerekmez.
- Kullanıcıların artık veri idaresi ilkeleri hakkında bilgi sahibi olmaları gerekmez; çalışmalarına odaklanabilir.

Bu içerikte henüz bir bekletme etiketi uygulanmamışsa ve hassas bilgiler, anahtar sözcükler veya aranabilir özellikler ya da [eğitilebilir sınıflandırıcılar](classifier-get-started-with.md) için eşleşme içerdiğinde içeriğe otomatik olarak bekletme etiketleri uygulayabilirsiniz. Artık önizleme aşamasında, SharePoint veya OneDrive depolanan bulut eklerine otomatik olarak bir bekletme etiketi uygulayabilirsiniz.

> [!TIP]
> [Duyarlılık etiketi uygulanmış](#identify-files-and-emails-that-have-a-sensitivity-label) [Teams toplantı kayıtlarını](#microsoft-teams-meeting-recordings) ve öğeleri tanımlamak için aranabilir özellikleri kullanın.

Bu koşullara göre otomatik olarak bir bekletme etiketi uygulama işlemleri:

![Etiketleri otomatik olarak uygulamak için rollerin ve görevlerin diyagramı.](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

İki yönetici adımı için aşağıdaki yönergeleri kullanın.

> [!NOTE]
> Otomatik ilkeler, öğelere bekletme etiketlerini otomatik olarak uygulamak için hizmet tarafı etiketlemesini koşullarla birlikte kullanır. Ayrıca, aşağıdakileri yaptığınızda otomatik olarak etiket ilkesi içeren bir bekletme etiketi uygulayabilirsiniz:
>
> - SharePoint Syntex'da belge anlama modeline bekletme etiketi uygulama
> - SharePoint ve Outlook için varsayılan bekletme etiketi uygulama
> - Outlook kurallarını kullanarak e-postaya bekletme etiketi uygulama
>
> Bu senaryolar için bkz. [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuzun genel yöneticisi, bekletme etiketleri ve ilkelerini oluşturmak ve düzenlemek için tam izinlere sahiptir. Genel yönetici olarak oturum açmadıysanız, kullandığınız çözüme bağlı olarak [kayıt yönetimi](get-started-with-records-management.md#permissions) veya [veri yaşam döngüsü yönetimi](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels) için izin bilgilerine bakın.

Öğelere uygulamak istediğiniz [bekletme etiketlerini oluşturduğunuzdan](file-plan-manager.md#create-retention-labels) emin olun.

## <a name="how-to-create-an-auto-apply-retention-label-policy"></a>Bekletme etiketi ilkesini otomatik uygulama oluşturma

Bekletme etiketi ilkenizi oluşturmadan önce **bunun uyarlamalı** mı yoksa **statik** mi olacağını belirleyin. Daha fazla bilgi için bkz. [Bekletme için uyarlamalı veya statik ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention). Uyarlamalı bir ilke kullanmaya karar verirseniz, bekletme etiketi ilkenizi oluşturmadan önce bir veya daha fazla uyarlamalı kapsam oluşturmanız ve ardından bekletme etiketi oluşturma ilkesi işlemi sırasında bunları seçmeniz gerekir. Yönergeler için bkz [. Uyarlamalı kapsamlar için yapılandırma bilgileri](retention-settings.md#configuration-information-for-adaptive-scopes).

Otomatik uygulama ilkesi oluşturduğunuzda, belirttiğiniz koşullara göre içeriğe otomatik olarak uygulanacak bir bekletme etiketi seçersiniz.

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) aşağıdaki konumlardan birine gidin:

    - Kayıt yönetimi kullanıyorsanız:
        - **Çözümleri** \> **Kayıt yönetimi** \> **Etiket ilkeleri** sekmesi \> **Etiketi otomatik uygulama**

    - Veri yaşam döngüsü yönetimi kullanıyorsanız:
        - **Çözümleri** \> **Veri yaşam döngüsü yönetimi** \> **Etiket ilkeleri** sekmesi \> **Etiketi otomatik uygulama**

    Gezinti bölmesinde çözümünüzü hemen görmüyor musunuz? İlk olarak **Tümünü göster'i** seçin.

2. Bu otomatik etiketleme ilkesi için bir ad ve açıklama girin ve **İleri'yi** seçin.

3. **Bu etiketi uygulamak istediğiniz içerik türünü seçin** için kullanılabilir koşullardan birini seçin. Seçenekler hakkında daha fazla bilgi için bu sayfadaki [Bekletme etiketlerini otomatik uygulama için koşulları yapılandırma](#configuring-conditions-for-auto-apply-retention-labels) bölümüne bakın.

4. **Oluşturulacak bekletme ilkesinin türünü seçin** sayfasında, [Başlamadan önce](#before-you-begin) yönergelerinden yaptığınız seçime bağlı olarak **Uyarlamalı** veya **Statik'i** seçin. Uyarlamalı kapsamlar oluşturmadıysanız **Uyarlamalı'yı** seçebilirsiniz, ancak seçilecek uyarlamalı kapsam olmayacağından, sihirbazı bu seçenekle tamamlayamazsınız.

5. Seçtiğiniz kapsama bağlı olarak:

    - **Uyarlamalı**: **Uyarlamalı ilke kapsamlarını ve konumlarını seçin** sayfasında **Kapsam ekle'yi** seçin ve oluşturulmuş bir veya daha fazla uyarlamalı kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebileceğiniz konumlar eklenen [kapsam türlerine](retention-settings.md#configuration-information-for-adaptive-scopes) bağlıdır. Örneğin, yalnızca bir **Kullanıcı** kapsam türü eklediyseniz, **Exchange e-postayı** seçebilirsiniz, ancak **siteleri SharePoint seçemezsiniz**.

    - **Statik**' i seçtiyseniz: **Konumları seçin** sayfasında konumlardan herhangi birini açın veya kapatın. Her konum için, [ilkeyi konumun tamamına uygulamak için](retention-settings.md#a-policy-that-applies-to-entire-locations) varsayılan olarak bırakabilir veya [ekleme ve dışlamaları belirtebilirsiniz](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)

    Konum seçenekleri hakkında bilgi için bkz [. Konumlar](retention-settings.md#locations).

6. Bir bekletme etiketi seçmek için sihirbazdaki istemleri izleyin ve yapılandırma seçeneklerinizi gözden geçirip gönderin.

Var olan bir bekletme etiketi ilkesini düzenlemek için (ilke türü **Otomatik Uygula'dır**), ilkeyi seçin ve ardından **Düzenleme** seçeneğini belirleyerek **Bekletme ilkesi yapılandırmasını düzenle'yi** başlatın.

İçerik otomatik uygulama etiket ilkesi kullanılarak etiketlendikten sonra, içerik veya ilke değiştirilerek ya da yeni bir otomatik uygulama etiketi ilkesi tarafından uygulanan etiket otomatik olarak kaldırılamaz veya değiştirilemez. Daha fazla bilgi için bkz. [Bir kerede yalnızca bir bekletme etiketi](retention.md#only-one-retention-label-at-a-time).

> [!NOTE]
> Otomatik uygulama bekletme etiketi ilkesi, içeriğe uygulanan mevcut bekletme etiketini asla değiştirmez. Yapılandırdığınız koşulları kullanarak içeriği yeniden etiketlemek istiyorsanız, mevcut saklama etiketini mevcut içerikten el ile kaldırmanız gerekir.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Bekletme etiketlerini otomatik uygulama koşullarını yapılandırma

İçerikte aşağıdakiler olduğunda içeriğe bekletme etiketlerini otomatik olarak uygulayabilirsiniz:

- [Belirli hassas bilgi türleri](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Oluşturduğunuz sorguyla eşleşen belirli anahtar sözcükler veya aranabilir özellikler](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Eğitilebilir sınıflandırıcılar için eşleşme](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Alternatif olarak, yeni paylaşılan [bulut eklerine](#auto-apply-labels-to-cloud-attachments) otomatik olarak bekletme etiketleri uygulayabilirsiniz.

Bekletme etiketlerini hassas bilgilere, anahtar sözcüklere veya aranabilir özelliklere ya da eğitilebilir sınıflandırıcılara göre otomatik olarak uygulanacak şekilde yapılandırdığınızda, bekletme etiketlerinin ne zaman otomatik olarak uygulanabileceğini belirlemek için aşağıdaki tabloyu kullanın.

Exchange:

|Durum|Aktarımdaki öğeler (gönderildi veya alındı) |Mevcut öğeler (bekleyen veriler)|
|:-----|:-----|:-----|
|Hassas bilgi türleri - yerleşik| Evet | Hayır |
|Hassas bilgi türleri - özel| Evet | Hayır |
|Belirli anahtar sözcükler veya aranabilir özellikler| Evet |Evet |
|Eğitilebilir sınıflandırıcılar| Evet | Evet (yalnızca son altı ay) |

SharePoint ve OneDrive:

|Durum|Yeni veya değiştirilmiş öğeler |Mevcut öğeler |
|:-----|:-----|:-----|
|Hassas bilgi türleri - yerleşik| Evet | Evet |
|Hassas bilgi türleri - özel| Evet | Hayır |
|Belirli anahtar sözcükler veya aranabilir özellikler| Evet |Evet |
|Eğitilebilir sınıflandırıcılar| Evet | Evet (yalnızca son altı ay) |

Ayrıca, taslakta yer alan veya hiç yayımlanmamış SharePoint öğeler bu senaryo için desteklenmez.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Belirli türde hassas bilgilere sahip içeriğe etiketleri otomatik uygulama

> [!IMPORTANT]
> Hassas bilgileri tanımlayarak otomatik olarak uyguladığınız e-postalar için, tüm posta kutuları otomatik olarak eklenir ve bu, Microsoft 365 gruplardan gelen posta kutularını içerir.
>
> Grup posta kutuları genellikle **Microsoft 365 Grupları** konumu seçilerek dahil edilse de, bu ilke yapılandırması için grup konumu yalnızca Microsoft 365 grubuna bağlı SharePoint siteleri içerir.

Hassas bilgiler için otomatik uygulama bekletme etiketi ilkeleri oluşturduğunuzda, bir Microsoft Purview Veri Kaybı Önleme (DLP) ilkesi oluştururken kullandığınız ilke şablonlarının listesini görürsünüz. Her şablon, belirli türlerdeki hassas bilgileri aramak için önceden yapılandırılmıştır. Aşağıdaki örnekte, hassas bilgi türleri **Gizlilik** kategorisinden ve **ABD Kişisel Bilgiler (PII) Veri** şablonundan alınmaktadır:

![Hassas bilgi türlerine sahip ilke şablonları.](../media/sensitive-info-configuration.png)

Duyarlılık bilgi türleri hakkında daha fazla bilgi edinmek için bkz. [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types). Şu anda, bu senaryo için [tam veri eşleşmesi tabanlı hassas bilgi türleri](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) ve [belge parmak izi kullanımı](document-fingerprinting.md) desteklenmez.

İlke şablonunu seçtikten sonra, herhangi bir tür hassas bilgi ekleyebilir veya kaldırabilir, güvenilirlik düzeyini ve örnek sayısını değiştirebilirsiniz. Önceki örnek ekran görüntüsünde, bekletme etiketinin yalnızca aşağıdaki durumlarda otomatik olarak uygulanması için bu seçenekler değiştirilmiştir:

- Algılanan hassas bilgi türü, iki hassas bilgi türü için en az **Orta düzeyde bir** eşleşme doğruluğuna (veya [güvenilirlik düzeyine](sensitive-information-type-learn-about.md#more-on-confidence-levels)) ve biri için **Yüksek güvenilirlik** düzeyine sahiptir. Birçok hassas bilgi türü, daha yüksek eşleşme doğruluğuna sahip bir desenin daha fazla kanıt bulunmasını gerektirdiği (anahtar sözcükler, tarihler veya adresler gibi) birden çok desenle tanımlanırken, daha düşük eşleşme doğruluğuna sahip bir desen daha az kanıt gerektirir. Güvenilirlik düzeyi ne kadar düşükse, içeriğin koşulla eşleşmesi o kadar kolay olur, ancak daha fazla hatalı pozitif sonuç olasılığı vardır.

- İçerik, bu üç hassas bilgi türünden herhangi birinin 1 ila 9 örneğini içerir. için **varsayılan değer** **Any'tir**.

Bu seçenekler hakkında daha fazla bilgi için DLP belgelerinin [Eşleştirmesini kolaylaştırmak veya daha zor hale getirmek için kuralları ayarlama](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match) başlığı altında yer alan aşağıdaki kılavuza bakın.

> [!IMPORTANT]
> Hassas bilgi türlerinin en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Bekletme etiketlerini otomatik olarak uygulamak için hassas bilgi türlerini kullanırken dikkate almak için:

- Özel hassas bilgi türleri kullanıyorsanız, bunlar SharePoint ve OneDrive mevcut öğeleri otomatik olarak etiketleyemez.

- E-postalar için dahil etmek veya hariç tutmak üzere belirli alıcıları seçemezsiniz; yalnızca **Tüm alıcılar** ayarı desteklenir ve yalnızca bu yapılandırma için Microsoft 365 gruplarından gelen posta kutularını içerir.

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Anahtar sözcükler veya aranabilir özellikler içeren içeriğe etiketleri otomatik uygulama

Belirli sözcükleri, tümcecikleri veya aranabilir özelliklerin değerlerini içeren bir sorgu kullanarak içeriğe etiketleri otomatik olarak uygulayabilirsiniz. VE, OR ve NOT gibi arama işleçlerini kullanarak sorgunuzu daraltabilirsiniz.

![Sorgu düzenleyicisi.](../media/new-retention-query-editor.png)

Anahtar Sözcük Sorgu Dili (KQL) kullanan sorgu söz dizimi hakkında daha fazla bilgi için bkz[. Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Sorgu tabanlı otomatik uygulama ilkeleri, içeriği tanımlamak için eBulma içerik araması ile aynı arama dizinini kullanır. Kullanabileceğiniz aranabilir özellikler hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

Bekletme etiketlerini otomatik olarak uygulamak için anahtar sözcükler veya aranabilir özellikler kullanılırken dikkat edilmesi gereken bazı noktalar:

- SharePoint için, bu KQL sorgularında gezinilen özellikler ve özel özellikler desteklenmez ve belgeler için yalnızca önceden tanımlanmış yönetilen özellikleri kullanmanız gerekir. Ancak, kiracı düzeyinde eşlemeleri varsayılan olarak iyileştirici olarak etkinleştirilen önceden tanımlanmış yönetilen özelliklerle kullanabilirsiniz (RefinableDate00-19, RefinableString00-99, RefinableInt00-49, RefinableDecimals00-09 ve RefinableDouble00-09). Daha fazla bilgi için bkz. [SharePoint Server'da gezinilen ve yönetilen özelliklere genel bakış](/SharePoint/technical-reference/crawled-and-managed-properties-overview) ve yönergeler için bkz. [Yeni yönetilen özellik oluşturma](/sharepoint/manage-search-schema#create-a-new-managed-property).

- Özel bir özelliği iyileştirici özelliklerinden biriyle eşlerseniz, bekletme etiketi için KQL sorgunuzda kullanmadan önce 24 saat bekleyin.

- SharePoint yönetilen özellikler diğer adlar kullanılarak yeniden adlandırılabilir, ancak etiketlerinizdeki KQL sorgular için bunları kullanmayın. Yönetilen özelliğin gerçek adını her zaman belirtin; örneğin, "RefinableString01".

- Boşluk veya özel karakter içeren değerleri aramak için çift tırnak işareti (`" "`) kullanarak tümceciği (örneğin, `subject:"Financial Statements"`) kullanın.

- Url'sine göre bir öğeyle eşleştirmek için *Path* yerine *DocumentLink* özelliğini kullanın.

- Sonek joker karakter aramaları (örneğin `*cat`) veya alt dize joker karakter aramaları (gibi `*cat*`) desteklenmez. Ancak, ön ek joker karakter aramaları (gibi `cat*`) desteklenir.

- Kısmen dizine alınmış öğelerin beklediğiniz öğeleri etiketlememekten veya NOT işlecini kullanırken etiketlemenin dışında tutulmasını beklediğiniz öğeleri etiketlemeden sorumlu olabileceğini unutmayın. Daha fazla bilgi için bkz. [İçerik Arama'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md).

- Belgelerdeki RefinableStrings değerlerinde sözcükler arasında boşluklar kullanmamanızı öneririz. RefinableString bir sözcük sonu özelliği değildir.

Örnek sorgular:

| Iş yük -ünü | Örnek |
|:-----|:-----|
|Exchange   | `subject:"Financial Statements"` |
|Exchange   | `recipients:garthf@contoso.com` |
|SharePoint | `contenttype:document` |
|SharePoint | `site:https://contoso.sharepoint.com/sites/teams/procurement AND contenttype:document`|
|Exchange veya SharePoint | `"customer information" OR "private"`|

Daha karmaşık örnekler:

SharePoint için aşağıdaki sorgu, söz konusu dosyalar **parola**, **parola** veya **pw** anahtar sözcüklerini içerdiğinde Word belgelerini veya Excel elektronik tablolarını tanımlar:

```KQL
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

Exchange için aşağıdaki sorgu, söz konusu belgeler bir e-postaya eklendiğinde **nda** veya **tümcecik gizlilik sözleşmesi** sözcüğünü içeren herhangi bir Word belgesini veya PDF'sini tanımlar:

```KQL
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

SharePoint için aşağıdaki sorgu, kredi kartı numarası içeren belgeleri tanımlar:

```KQL
sensitivetype:"credit card number"
```

Aşağıdaki sorgu, yasal içerik içeren belgeleri veya e-postaları tanımlamaya yardımcı olacak bazı tipik anahtar sözcükler içerir:

```KQL
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

Aşağıdaki sorgu, insan kaynaklarına yönelik belgeleri veya e-postaları tanımlamaya yardımcı olacak tipik anahtar sözcükler içerir:

```KQL
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

Bu son örnekte anahtar sözcükler arasında her zaman işleçler dahil olmak için en iyi yöntemin kullanıldığına dikkat edin. Anahtar sözcükler (veya iki özellik:değer ifadesi) arasındaki boşluk, AND kullanımıyla aynıdır. Her zaman işleçler ekleyerek, bu örnek sorgunun anahtar sözcüklerden herhangi birini içeren içerik yerine yalnızca tüm bu anahtar sözcükleri içeren içeriği tanımlayacağını görmek daha kolaydır. Amacınız anahtar sözcüklerden herhangi birini içeren içeriği tanımlamaksa AND yerine OR değerini belirtin. Bu örnekte gösterildiği gibi, her zaman işleçleri belirttiğinizde sorguyu doğru yorumlamak daha kolaydır.

##### <a name="microsoft-teams-meeting-recordings"></a>Toplantı kayıtlarını Microsoft Teams

> [!NOTE]
> Kayıtlar OneDrive veya SharePoint kaydedilmeden önce Teams toplantı kayıtlarını tutma ve silme özelliği çalışmaz. Daha fazla bilgi için bkz[. OneDrive İş kullanma ve toplantı kayıtları için Çevrimiçi SharePoint veya Stream](/MicrosoftTeams/tmr-meeting-recording-change).

Kullanıcıların OneDrive hesaplarında veya SharePoint depolanan Microsoft Teams toplantı kayıtlarını belirlemek için **Anahtar Sözcük sorgu düzenleyicisi** için aşağıdakileri belirtin:

```KQL
ProgID:Media AND ProgID:Meeting
```

Çoğu zaman toplantı kayıtları OneDrive kaydedilir. Ancak kanal toplantıları için SharePoint kaydedilir.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Duyarlılık etiketi olan dosyaları ve e-postaları tanımlama

SharePoint veya OneDrive dosyaları tanımlamak ve belirli bir [duyarlılık etiketi](sensitivity-labels.md) uygulanmış e-postaları Exchange için **Anahtar Sözcük sorgu düzenleyicisi** için aşağıdakileri belirtin:

```KQL
InformationProtectionLabelId:<GUID>
```

GUID'yi bulmak için [Güvenlik & Uyumluluğu PowerShell'in](/powershell/exchange/scc-powershell) [Get-Label](/powershell/module/exchange/get-label) cmdlet'ini kullanın:

```powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
```

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Eğitilebilir sınıflandırıcıları kullanarak içeriğe etiketleri otomatik uygulama

Eğitilebilir sınıflandırıcı seçeneğini belirlediğinizde, önceden eğitilmiş veya özel eğitilebilir sınıflandırıcılardan birini veya daha fazlasını seçebilirsiniz:

![Eğitilebilir sınıflandırıcıyı seçin.](../media/retention-label-classifers.png)

> [!CAUTION]
> Çok sayıda hatalı pozitif sonuç ürettiğinden **, Rahatsız Edici Dil** önceden eğitilmiş sınıflandırıcıyı kullanım dışı bırakıyoruz. Bu sınıflandırıcıyı kullanmayın ve şu anda kullanıyorsanız iş süreçlerinizi bundan çıkarmanızı ve bunun yerine **Hedeflenen Taciz**, **Küfür** ve **Tehdit** önceden eğitilmiş sınıflandırıcıları kullanmanızı öneririz.

Bu seçeneği kullanarak otomatik olarak etiket uygulamak için sitelerin ve posta kutularının SharePoint en az 10 MB veriye sahip olması gerekir.

Eğitilebilir sınıflandırıcılar hakkında daha fazla bilgi için bkz. [Eğitilebilir sınıflandırıcılar hakkında bilgi edinin](classifier-learn-about.md).

> [!TIP]
> Exchange için eğitilebilir sınıflandırıcılar kullanıyorsanız bkz. [İçerik gezgininde sınıflandırıcıyı yeniden eğitme](classifier-how-to-retrain-content-explorer.md).

Bekletme etiketlerini otomatik olarak uygulamak için eğitilebilir sınıflandırıcıları kullanırken göz önünde bulundurmak için:

- Altı aydan eski SharePoint ve OneDrive öğeleri otomatik olarak etiketleyemezsiniz.

#### <a name="auto-apply-labels-to-cloud-attachments"></a>Bulut eklerine etiketleri otomatik uygulama

> [!NOTE]
> Bu seçenek önizleme aşamasında aşamalı olarak kullanıma sunulmuştur ve değiştirilebilir.

Kiracınızda kullanıcıların iletişimleri üzerinden gönderilen tüm dosya kopyalarını yakalamanız ve saklamanız gerekiyorsa bu seçeneği kullanmanız gerekebilir. Bu seçeneği iletişim hizmetleri, Exchange ve Teams için bekletme ilkeleriyle birlikte kullanırsınız.

> [!IMPORTANT]
> Bulut ekleri için bekletme etiketlerini otomatik olarak uygulamak için kullanılacak bir etiket seçtiğinizde, etiket bekletme ayarının **Bekletme süresini başlangıç** olarak **ne zaman öğelerinin etiketlendiği** şeklinde olduğundan emin olun.

Bazen modern ekler olarak da bilinen bulut ekleri, bulutta depolanan dosyalara eklenmiş bağlantıları kullanan bir paylaşım mekanizmasıdır. Sürüm denetimi gibi işbirliğine dayalı avantajlara sahip paylaşılan içerik için merkezi depolamayı destekler. Bulut ekleri, dosyanın ekli kopyaları veya dosyaya URL metin bağlantısı değildir. [Outlook](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-outlook) ve [Teams](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-teams) desteklenen bulut ekleri için görsel denetim listelerine başvurmak yararlı olabilir.

Bulut eklerine bekletme etiketi uygulama seçeneğini belirlediğinizde, uyumluluk amacıyla bu dosyanın bir kopyası paylaşım sırasında oluşturulur. Daha sonra seçilen bekletme etiketi kopyaya uygulanır ve bu etiket [eBulma kullanılarak tanımlanabilir](advanced-ediscovery-cloud-attachments.md). Kullanıcılar, Koruma Bekletme kitaplığında depolanan kopyanın farkında değildir. Bekletme etiketi iletinin kendisine veya özgün dosyaya uygulanmaz.

Dosya yeniden değiştirilir ve paylaşılırsa, dosyanın yeni sürüm olarak yeni bir kopyası Koruma Bekletme kitaplığına kaydedilir. **Öğeler etiketlendiğinde** etiket ayarını neden kullanmanız gerektiği de dahil olmak üzere daha fazla bilgi için bkz. [Bulut ekleriyle bekletme nasıl çalışır](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments)?

Bu seçenek için desteklenen bulut ekleri, SharePoint ve OneDrive depolanan belgeler, videolar ve görüntüler gibi dosyalardır. Teams için sohbet iletilerinde paylaşılan bulut ekleri ve standart ve özel kanallar desteklenir. Toplantı davetleri ve Teams veya Outlook dışındaki uygulamalar üzerinden paylaşılan bulut ekleri desteklenmez. Bulut ekleri kullanıcılar tarafından paylaşılmalıdır; botlar aracılığıyla gönderilen bulut ekleri desteklenmez.

Bu seçenek için gerekli olmasa da, paylaşılan sürümün doğru bir şekilde yakalanması için SharePoint siteleriniz ve OneDrive hesaplarınız için sürüm oluşturmanın etkinleştirildiğinden emin olmanız önerilir. Sürüm oluşturma etkin değilse, kullanılabilir son sürüm korunur. Taslaktaki veya hiç yayımlanmamış belgeler desteklenmez.

Bulut ekleri için bekletme etiketlerini otomatik olarak uygulamak için kullanılacak bir etiket seçtiğinizde, Etiket bekletme ayarının **Saklama süresini başlatma ayarının** **Öğeler etiketlendiğinde** olduğundan emin olun.

Bu seçenek için konumları yapılandırırken şunları seçebilirsiniz:

- **SharePoint iletişim sitelerinde** depolanan paylaşılan dosyalar, Microsoft 365 grupları tarafından bağlanmamış ekip siteleri ve klasik siteler için siteleri SharePoint.
- **Microsoft 365** grupları tarafından bağlanan ekip sitelerinde depolanan paylaşılan dosyalar için Microsoft 365 Grupları.
- Kullanıcıların OneDrive depolanan paylaşılan dosyalar için **hesapları** OneDrive.

Özgün dosyaları, e-posta iletilerini veya Teams iletilerini korumak veya silmek istiyorsanız ayrı bekletme ilkeleri oluşturmanız gerekir.

> [!NOTE]
> Tutulan bulut eklerinin süresinin, bunları içeren iletilerle aynı anda dolmasını istiyorsanız, bekletme etiketini aynı saklamaya sahip olacak şekilde yapılandırın ve ardından Exchange ve Teams için bekletme ilkelerinizle eylemleri ve zamanlamaları silin.

Bulut eklerine bekletme etiketlerinin otomatik olarak uygulandığını göz önünde bulundurmak için:

- Yalnızca yeni paylaşılan bulut ekleri bekletme için otomatik olarak etiketlenir.

- Bir kullanıcı bir Teams konuşmasına eklendiğinde ve konuşmanın tam geçmişine erişim verildiğinde, bu geçmiş bulut eklerini içerebilir. Kullanıcı konuşmaya eklendikten sonra 48 saat içinde paylaşıldıysa, bulut eklerinin geçerli kopyaları bekletme için otomatik olarak etiketlenir. Bu zaman aralığından önce paylaşılan bulut ekleri yeni eklenen kullanıcılar için desteklenmez.

- Teams ve Outlook dışında paylaşılan bulut ekleri desteklenmez.

- Aşağıdaki öğeler, saklanabilen bulut ekleri olarak desteklenmez:
  - Siteler, sayfalar, listeler, formlar, klasörler, belge kümeleri ve OneNote sayfaları SharePoint.
  - Bu dosyalara erişimi olmayan kullanıcılar tarafından paylaşılan dosyalar.
  - Bulut eki gönderilmeden önce silinen veya taşınan dosyalar. Örneğin, kullanıcı önce dosyanın hala kullanılabilir olduğunu onaylamadan daha önce paylaşılan bir eki başka bir iletiden kopyalayıp yapıştırır. Ya da dosya silindiğinde birisi eski bir iletiyi iletir.
  - Kuruluşunuz dışındaki konuklar veya kullanıcılar tarafından paylaşılan dosyalar.
  - Taslak e-postalardaki ve gönderilmeyen iletilerdeki dosyalar.
  - Boş dosyalar.

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Bekletme etiketlerinin etkili olması ne kadar sürer?

Hassas bilgilere, anahtar sözcüklere veya aranabilir özelliklere ya da eğitilebilir sınıflandırıcılara göre bekletme etiketlerini otomatik olarak uyguladığınızda, bekletme etiketlerinin uygulanması yedi güne kadar sürebilir:

![Otomatik uygulama etiketlerinin ne zaman etkin olduğunu açıklayan diyagram.](../media/retention-labels-autoapply-timings.png)

Beklenen etiketler yedi gün sonra görünmüyorsa, Microsoft Purview uyumluluk portalı **Etiket ilkeleri** sayfasından seçerek otomatik uygulama ilkesinin **Durumunu** denetleyin. **Kapalı (Hata)** durumunu görürseniz ve konumların ayrıntılarında ilkeyi dağıtmanın (SharePoint için) veya ilkeyi yeniden dağıtmayı (OneDrive için) denemenin beklenenden uzun sürdüğünü belirten bir ileti görürseniz, ilke dağıtımını yeniden denemek için [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell komutunu çalıştırmayı deneyin:

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. Aşağıdaki komutu çalıştırın:

    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Bekletme etiketlerini ve ilkelerini güncelleştirme

Hassas bilgiler, anahtar sözcükler veya aranabilir özellikler için yapılandırılan bekletme etiketi ilkelerini otomatik olarak uygulama veya eğitilebilir sınıflandırıcılarla eşleşme için: İlkedeki bir bekletme etiketi içeriğe zaten uygulanmışsa, yeni tanımlanan içeriğe ek olarak bu içeriğe de otomatik olarak seçili etiket ve ilke yapılandırmasında bir değişiklik uygulanır.

Bulut ekleri için yapılandırılan bekletme etiketi ilkelerini otomatik uygulama için: Bu ilke mevcut dosyalar yerine yeni paylaşılan dosyalar için geçerli olduğundan, seçilen etiket ve ilke yapılandırmasında yapılan bir değişiklik yalnızca yeni paylaşılan içeriğe otomatik olarak uygulanır.

Etiket veya ilke oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez; bunlar şunlardır:

- Bekletme etiketleri ve ilkeleri, kapsam türü (uyarlamalı veya statik) ve bekletme süresi dışında bekletme ayarları için adlar. Ancak, bekletme süresinin öğelerin etiketlendiği zamanlara göre olduğu saklama süresini değiştiremezsiniz.
- Öğeleri kayıt olarak işaretleme seçeneği.

### <a name="deleting-retention-labels"></a>Bekletme etiketlerini silme

Şu anda hiçbir bekletme etiketi ilkesine dahil olmayan, olay tabanlı saklama için yapılandırılmamış bekletme etiketlerini silebilir veya öğeleri düzenleyici kayıt olarak işaretleyebilirsiniz.

Silebileceğiniz bekletme etiketleri için, öğelere uygulanmışsa silme işlemi başarısız olur ve etiketlenmiş öğeleri tanımlamak için içerik gezgininin bağlantısını görürsünüz.

Ancak, içerik gezgininin etiketlenmiş öğeleri göstermesi iki gün kadar sürebilir. Bu senaryoda, bekletme etiketi içerik gezgini bağlantısını göstermeden silinebilir.

## <a name="locking-the-policy-to-prevent-changes"></a>Değişiklikleri önlemek için ilkeyi kilitleme

Kimsenin ilkeyi kapatamadığını, ilkeyi silemediğini veya daha az kısıtlayıcı hale getiremediğini güvence altına almanız gerekiyorsa bkz [. Bekletme ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma](retention-preservation-lock.md).

## <a name="next-steps"></a>Sonraki adımlar

Otomatik etiketleme ilkelerinizden uygulanan etiketleri izlemenize yardımcı olmak için:

- [Bekletme etiketlerini izleme](retention.md#monitoring-retention-labels)
- [Belirli bir bekletme etiketine sahip tüm içeriği bulmak için İçerik Arama'yı kullanma](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Bekletme eylemlerini denetleme](retention.md#auditing-retention-actions)

SharePoint'da yönetilen özelliklere sahip bir otomatik uygulama bekletme etiketi ilkesi ve bekletme süresini başlatmak için olay tabanlı saklama kullanan örnek bir senaryo için bkz. SharePoint [depolanan belgelerin yaşam döngüsünü yönetmek için bekletme etiketlerini kullanma](auto-apply-retention-labels-scenario.md).
