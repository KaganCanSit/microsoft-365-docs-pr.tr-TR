---
title: İk verilerini içeri aktaracak bir bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: Yöneticiler kendi kuruluşlarının insan kaynakları (İk) sisteminden çalışan verilerini içeri aktaracak bir veri bağlayıcısı kurarak çalışan verilerini Microsoft 365. Bu sayede, insider risk yönetimi ilkelerde İk verilerini kullanarak, belirli kullanıcıların kurum açısından iç tehditlere neden olan etkinliklerini algılayabilirsiniz.
ms.openlocfilehash: 31dd1ff904796c2ac59405a1e07e65f924d3ef88
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010042"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>İk verilerini içeri aktaracak bir bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi'de bir veri bağlayıcısı kurarak, kullanıcının sn. sn. veya bir kullanıcının iş düzeyindeki bir değişiklik gibi olaylarla ilgili insan kaynakları (İk) verilerini içeri aktarabilirsiniz. İk verileri daha sonra [Insider risk yönetimi](insider-risk-management.md) çözümü tarafından, kuruluş içindeki kullanıcıların olası kötü amaçlı etkinliklerini veya veri hırsızlığını kimlikle doğrulamanıza yardımcı olacak risk göstergeleri oluşturmak için kullanılabilir.

Insider risk yönetimi ilkelerinin risk göstergeleri oluşturmak için kullanabileceği İk verileri için bağlayıcı ayarlama, İk verilerini içeren bir CSV dosyası oluşturmak, kimlik doğrulaması için kullanılan Azure Active Directory'te bir uygulama oluşturmak, kaynakta İk veri bağlayıcısı oluşturmak Microsoft 365 uyumluluk merkezi ve ardından, CSV dosyalarında İk verilerini Microsoft bulutuna alan bir betik çalıştırarak (zamanlanmış bir esasla) insider risk yönetimi çözümünün kullanımına sunar.

> [!IMPORTANT]
> İk bağlayıcılarının yeni bir sürümü artık genel önizleme için kullanılabilir. Insider risk yönetimine yönelik sağlık ilkesi senaryosuna yönelik yeni [](#csv-file-for-employee-profile-data-preview) bir İk bağlayıcısı oluşturmak veya yeni çalışan profili senaryosuna yönelik verileri içeri aktaracak şekilde, Microsoft 365 uyumluluk merkezi'ta Veri bağlayıcıları sayfasına gidin, Bağlayıcılar sekmesini seçin ve  ayarlamayı başlatmak için **> İk (önizleme)** bağlayıcısı ekle'ye tıklayın. Mevcut İk bağlayıcıları hiçbir kesinti olmadan çalışmaya devam edecektir.

## <a name="before-you-begin"></a>Başlamadan önce

- Hangi İk senaryolarını ve verileri bu Microsoft 365. Bu, oluşturmanız gereken csv dosyası ve İk bağlayıcılarının kaç tane olduğunu ve CSV dosyalarını nasıl oluşturacaklarını ve yapılandıracaklarını belirlemenize yardımcı olur. İçeri aktardığınız İk verileri uygulamak istediğiniz Insider risk yönetimi ilkeleri tarafından belirlenir. Daha fazla bilgi için bkz. 1. Adım.

- Verilerinizin kurum İk sisteminden (ve düzenli olarak) nasıl alın ya da dışarı aktarın, sonra da 1. Adımda oluşturdukları CSV dosyalarına nasıl ekley olasını seçin. 4. Adımda çalıştırdınız betik, CSV dosyalarında yer alan İk verilerini Microsoft buluta yükler.

- Adım 3'te İk bağlayıcısını oluşturan kullanıcıya İk'da Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Adım 4'te çalıştırdınız örnek betik, İk verilerinizi Microsoft bulutuna yükler ve böylelikle Insider risk yönetimi çözümü tarafından kullanılabilir. Bu örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

- Bu bağlayıcı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder. Yeni bir ortamda İk bağlayıcısı ayarlamaya ilişkin adım GCC için bkz. ABD Kamu'da İk verilerini içeri aktaracak [bir bağlayıcı ayarlama](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>1. Adım: İk verilerinizle bir CSV dosyası hazırlama

İlk adım, bağlayıcının kendi verilerine aktaracakları İk verilerini içeren bir CSV dosyası Microsoft 365. Bu veriler, olası risk göstergeleri oluşturmak için Insider risk çözümü tarafından kullanılır. Aşağıdaki İk senaryolarına uygun veriler Microsoft 365:

- Çalışan çalışan çalışanı çalışanı. Kuruluştan ayrıldıklarınızı veren çalışanlar hakkında bilgiler.

- İş düzeyi değişiklikleri. Çalışanların iş düzeyindeki değişiklikleri, örneğin promosyonlar ve indirgeme bilgileri.

- Performans değerlendirmeleri. Çalışan performansı hakkında bilgiler.

- Performans geliştirme planları. Çalışanlar için performans geliştirme planları hakkında bilgiler.

- Çalışan profili (önizleme). Çalışan hakkında genel bilgiler.

İçeri aktar yapılacak İk verileri türü, uygulamak istediğiniz Insider risk yönetimi ilkesine ve buna karşılık gelen ilke şablonuna bağlıdır. Aşağıdaki tablo, her ilke şablonu için hangi İk veri türünün gerekli olduğunu gösterir:

|  İlke şablonu |  İk veri türü |
|:------------------------------|:--------------------------------|
| Ayrılan kullanıcılarla veri hırsızlığı | Çalışan çalışan adayları|
| Genel veri sızıntıları                             | Uygulanamaz|
| Öncelikli kullanıcıların veri sızıntıları                   | Uygulanamaz |
| Göz korkutucu kullanıcıların veri sızıntıları                | İş düzeyinde değişiklikler, Performans değerlendirmeleri, Performans geliştirme planları|
| Genel güvenlik ilkesi ihlalleri             | Uygulanamaz |
| Ayrılan kullanıcılarla güvenlik ilkesi ihlalleri  | Çalışan çalışan adayları|
| Öncelikli kullanıcıların güvenlik ilkesi ihlalleri   | Uygulanamaz|
| Korkutucu kullanıcıların güvenlik ilkesi ihlalleri| İş düzeyinde değişiklikler, Performans değerlendirmeleri, Performans geliştirme planları |
| E-postada rahatsız edici dil                    | Geçerli değil |
| Sağlık ilkesi| Çalışan profili |
|||

Insider risk yönetimine yönelik ilke şablonları hakkında daha fazla bilgi için bkz. [Insider risk yönetimi ilkeleri](insider-risk-management-policies.md#policy-templates).

Her İk senaryosu için, ilgili İk verilerini bir veya birden çok CSV dosyasında sağlaymanız gerekir. Insider risk yönetimi uygulamanız için  kullanmak üzere CSV dosyalarının sayısı bu bölümün devam bölümünde ele alınmıştır.

Gerekli İk verileriyle CSV dosyasını oluşturduktaktan sonra, bu dosyayı 4. Adımda betiği üzerinde çalıştırabilirsiniz. Ayrıca, CSV dosyasının her zaman en güncel bilgileri içerdiğindan emin olmak için bir güncelleştirme stratejisi uygulamanız gerekir; böylelikle betiği çalıştırsanız bile en güncel İk verileri Microsoft buluta yük olur ve insider risk yönetimi çözümüne erişilebilir olur.

> [!IMPORTANT]
> Aşağıdaki bölümlerde açıklanan sütun adları parametre değildir; yalnızca örnekler içerir. CSV dosyalarında herhangi bir sütun adını kullanabilirsiniz. Ancak, CSV dosyasında kullanabileceğiniz sütun adlarının, 3. Adımda İk bağlayıcısını oluştursanız veri türüyle eşlenmiş olması gerekir. Aşağıdaki bölümlerde yer alan örnek CSV dosyalarının Not Defteri görünümünde de görüntü olduğunu unutmayın. CSV dosyalarını aynı dosyalarda görüntülemek ve düzenlemek çok Microsoft Excel.

Aşağıdaki bölümlerde her İk senaryosu için gerekli CSV verileri açıklanmaktadır.

### <a name="csv-file-for-employee-resignation-data"></a>Çalışanlara örnek veriler için CSV dosyası

Çalışan çalışan verilerinde bir CSV dosyası örneği.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Aşağıdaki tabloda, çalışan çalışan çalışan verileri için CSV dosyasındaki her sütun açıklanır.

|  Sütun   |   Açıklama |
|:------------|:----------------|
|**EmailAddress**| Sonlandırılan kullanıcının e-posta adresini (UPN) belirtir.|
| **Tekdüdüz** | Kullanıcının, kuruluşta görevin resmi olarak sonlandırılma tarihini belirtir. Örneğin, bu, kullanıcının kuruluşdan ayrılma konusunda bildirim verdiği tarih olabilir. Bu tarih, kişinin son iş günü olan tarihten farklı olabilir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Son kullanıcı için çalışma son günü belirtir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>İş düzeyi değişiklik verileri için CSV dosyası

İşte, iş düzeyi değişiklik verileri için bir CSV dosyası örneği.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 – Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 – Director,Level 60- Sr. Manager
```

Aşağıdaki tabloda, iş düzeyi değişiklik verileri için CSV dosyasındaki her sütun açıklanır.

|  Sütun | Açıklama |
|:--------- |:------------- |
| **EmailAddress**  | Kullanıcının e-posta adresini (UPN) belirtir.|
| **EffectiveDate** | Kullanıcının iş düzeyinin resmi olarak değiştir başlangıç tarihini belirtir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Açıklamalar**| Değerlendirenin iş düzeyinin değişikliği hakkında sağladığı açıklamaları belirtir. 200 karakterlik bir sınır girebilirsiniz. Bu parametre isteğe bağlıdır. Csv dosyasına eklemek zorunda değilsiniz.|
| **OldLevel**| Kullanıcının, değiştirmeden önce iş düzeyini belirtir. Bu serbest metinli bir parametredir ve kurumuz için hiyerarşik taksonomi içerebilir. Bu parametre isteğe bağlıdır. Csv dosyasına eklemek zorunda değilsiniz.|
| **NewLevel**| Değiştirildikten sonra kullanıcının iş düzeyini belirtir. Bu serbest metinli bir parametredir ve kurumuz için hiyerarşik taksonomi içerebilir. Bu parametre isteğe bağlıdır. Csv dosyasına eklemek zorunda değilsiniz.|
|||

### <a name="csv-file-for-performance-review-data"></a>Performans gözden geçirme verileri için CSV dosyası

Performans verileri için bir CSV dosyası örneği.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Aşağıdaki tabloda, performans gözden geçirme verileri için CSV dosyasındaki her sütun açıklanır.

|  Sütun | Açıklama |
|:----------|:--------------|
| **EmailAddress**  | Kullanıcının e-posta adresini (UPN) belirtir.|
| **EffectiveDate** | Kullanıcının, performans değerlendirme sonucu hakkında resmi olarak bilgi sahibi olduğu tarihi belirtir. Bu, performans gözden geçirme döngüsünün sona er olduğu tarih olabilir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Açıklamalar**| Değerlendirenin performans incelemesi için kullanıcıya sağladığı tüm açıklamaları belirtir. Bu, 200 karakter sınırlaması olan bir metin parametresidir. Bu parametre isteğe bağlıdır. Csv dosyasına eklemek zorunda değilsiniz.|
| **Derecelendirme**| Performans incelemesi için sağlanan derecelendirmeyi belirtir. Bu bir metin parametresidir ve değerlendirmeyi tanımak için kuruluş tarafından herhangi bir serbest biçimli metin içerebilir. Örneğin, "3 Beklentileri karşıla" veya "Ortalamanın altında 2" olabilir. Bu, 25 karakter sınırlaması olan bir metin parametresidir. Bu parametre isteğe bağlıdır. Csv dosyasına eklemek zorunda değilsiniz.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>Performans geliştirme planı verileri için CSV dosyası

Performans geliştirme planı verilerine için veriler için bir CSV dosyası örneği.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Aşağıdaki tabloda, performans gözden geçirme verileri için CSV dosyasındaki her sütun açıklanır.

|  Sütun |  Açıklama |
|:----------|:---------------|
| **EmailAddress**  | Kullanıcının e-posta adresini (UPN) belirtir.|
| **EffectiveDate** | Kullanıcının performans geliştirme planı hakkında resmi olarak bilgi sahibi olduğu tarihi belirtir. Aşağıdaki tarih biçimini kullanabilirsiniz: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Açıklamalar**| Değerlendirenin performans geliştirme planı hakkında sağladığı tüm açıklamaları belirtir. Bu, 200 karakter sınırlaması olan bir metin parametresidir. Bu isteğe bağlı bir parametredir. Csv dosyasına eklemek zorunda değilsiniz. |
| **Derecelendirme**| Performans incelemesiyle ilgili derecelendirmeyi veya diğer bilgileri belirtir. Bu bir metin parametresidir ve değerlendirmeyi tanımak için kuruluş tarafından herhangi bir serbest biçimli metin içerebilir. Örneğin, "3 Beklentileri karşıla" veya "Ortalamanın altında 2" olabilir. Bu, 25 karakter sınırlaması olan bir metin parametresidir. Bu isteğe bağlı bir parametredir. Csv dosyasına eklemek zorunda değilsiniz.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>Çalışan profil verileri için CSV dosyası (önizleme)

> [!NOTE]
> Çalışan profili verileri için İk bağlayıcısı oluşturma özelliği genel önizlemededir. Çalışan profili verilerini destekleyen bir İk bağlayıcısı oluşturmak için, çalışma sayfasındaki  Veri bağlayıcıları sayfasına Microsoft 365 uyumluluk merkezi, Bağlayıcılar sekmesini seçin ve **Ardından Bağlayıcı** >  **ekleHR (önizleme)** seçeneğine tıklayın. 3. Adım: İk bağlayıcısı [oluşturma'da bağlayıcı oluşturmak için adımları izleyin](#step-3-create-the-hr-connector).

Çalışan profili verileri için bir CSV dosyası örneği.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

Aşağıdaki tabloda, çalışan profili verileri için CSV dosyasındaki her sütun açıklanır.

|  Sütun |  Açıklama |
|:----------|:---------------|
| EmailAddress<sup>*</sup>    | Çalışanın kullanıcı asıl adı (UPN) veya e-posta adresi.|
| EmployeeFirstName<sup>*</sup>   | Çalışanın adı.|
| EmployeeLastName<sup>*</sup>   | Çalışanın soyadı.|
| EmployeeAddressLine1<sup>*</sup>    | Çalışanın sokak adresi.|
| EmployeeAddressLine2   | Çalışan için daire numarası gibi ikincil adres bilgileri.|
| EmployeeCity | Çalışanın ikamet yeri.|
| EmployeeState | Çalışan için ikamet yeri.|
| Çalışan SıkıştırmaKodu<sup>*</sup>  | Çalışanın posta kodu. |
| EmployeeCountry| Çalışanın ikamet yeri.|
| EmployeeDepartment | Kuruluşta çalışanın bölümü.|
| EmployeeType |Normal, Muaf veya Yüklenici gibi çalışan için işe ilgili tür.|
| EmployeeRole |Kuruluşta çalışanların rolü, ataması veya iş unvanı.|
|||

> [!NOTE]
> <sup>*</sup> Bu sütun zorunludur. Zorunlu bir sütun yoksa, CSV dosyası doğrulanmaz ve dosyadaki diğer veriler içeri aktarılmaz.

Yalnızca çalışan profili verilerini içeri aktaran bir İk bağlayıcısı oluşturmanızı öneririz. Bu bağlayıcı için, tercihen her 15 - 20 günde bir çalışan profili verilerini sık sık yenileye doğru emin olun. Çalışan profili kayıtları, son 30 gün içinde güncelleştirilmezse silinir.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>İk verileri için kaç CSV dosyası kullanıcayı belirleme

3. Adımda, her İk veri türü için ayrı bağlayıcılar oluşturmayı seçebilir veya tüm veri türleri için tek bağlayıcı oluşturabilirsiniz. Bir İk senaryosu için veri içeren ayrı CSV dosyaları kullanabilirsiniz (önceki bölümlerde açıklanan CSV dosyaları örnekleri gibi). Alternatif olarak, iki veya daha fazla İk senaryosunu içeren tek bir CSV dosyası da kullanabilirsiniz. İk verileri için kaç CSV dosyası kullanıcanızı belirlemenize yardımcı olacak bazı yönergelere buradan bakabilirsiniz.

- Uygulamak istediğiniz Insider risk yönetimi ilkesi birden çok İk veri türü gerektiriyorsa, tüm gerekli veri türlerini içeren tek bir CSV dosyası kullanmayı göz önünde bulundurabilirsiniz.

- İk verilerini oluşturma veya toplama yöntemi CSV dosyalarının sayısını belirler. Örneğin, İk bağlayıcısını yapılandırmak için kullanılan farklı İk veri türleri kurum içinde tek bir İk sisteminde yer alıyorsa verileri tek bir CSV dosyasına aktarabilirsiniz. Ancak veriler farklı İk sistemleri arasında dağıtılıyorsa, verileri farklı CSV dosyalarına dışarı aktarmanız daha kolay olabilir. Örneğin, Çalışan çalışan verileri, İş düzeyinden veya Performans gözden geçirme veriden farklı bir İk sisteminde yer alıyor olabilir. Bu durumda, verileri tek bir CSV dosyasında el ile birleştirmek yerine, ayrı CSV dosyalarına sahip olmak daha kolay olabilir. Dolayısıyla, İk sistemlerinize veri alma veya verme biçiminiz, ihtiyacınız olacak CSV dosyalarının sayısını nasıl belirleyecek.

- Genel bir kural olarak, oluşturmanız gereken İk bağlayıcılarının sayısı CSV dosyasındaki veri türlerine göre belirlenir. Örneğin, bir CSV dosyası insider risk yönetimi uygulamanızı desteklemek için gereken tüm veri türlerini içeriyorsa, yalnızca bir İk bağlayıcısı gerekir. Ancak, her biri tek bir veri türü içeren iki ayrı CSV dosyanız varsa, iki İk bağlayıcısı oluşturmanız gerekir. Bunun bir istisnası, bir CSV dosyasına **HRScenario** sütunu eklerken (sonraki bölüme bakın), farklı CSV dosyalarını iş binecek tek bir İk bağlayıcısı yapılandırabilirsiniz.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Birden çok İk veri türü için tek bir CSV dosyası yapılandırma

Tek bir CSV dosyasına birden çok İk veri türü  eklersiniz. Uygulamaya devam ediyorsanız insider risk yönetimi çözümünün birden çok İk veri türü gerektirdiğinde veya veri türleri kurumda tek bir İk sisteminde yer alıyorsa, bu yararlı olur. CSV dosyalarının daha az olması her zaman daha az İk bağlayıcısı oluşturmanıza ve yönetmenize olanak sağlar.

İşte, birden çok veri türü içeren bir CSV dosyasını yapılandırma gereksinimleri:

- Her veri türü için gerekli sütunları (ve kullanıyorsanız isteğe bağlı olarak) ve üstbilgi satırına karşılık gelen sütun adını eklemeniz gerekir. Bir veri türü bir sütuna karşılık gelen bir değerse, değeri boş bırakabilirsiniz.

- Birden çok İk veri türüyle bir CSV dosyası kullanmak için, İk bağlayıcısı, CSV dosyasındaki hangi satırların İk veri türünü içerdiğini bilsin. Bu, CSV dosyasına ek **bir HRScenario** sütunu ek olarak işler. Bu sütundaki değerler her bir satırdaki İk veri türünü gösterir. Örneğin, dört İk senaryosunu karşılık gelen değerler \`İs'de, İş düzeyinde değişiklik\`, \`Performans incelemesi, \`\`\`Performans geliştirme planı\` ve Çalışan profili \`olabilir\`.\`

- HRScenario** sütunu içeren birden çok CSV dosyanız varsa, her dosyanın aynı sütun adını ve belirli İk senaryolarını tanımlamak için aynı değerleri kullandığından emin olun.

Aşağıdaki örnekte, **HRScenario sütununu içeren bir CSV dosyası** görüntülenir. HRScenario sütunundaki değerler, ilgili satırdaki verilerin türünü gösterir.

```text
HRScenario,EmailAddress,ResignationDate,LastWorkingDate,EffectiveDate,Remarks,Rating,OldLevel,NewLevel
Resignation,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30,,,,
Resignation,pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540,,,,
Job level change,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 61 Sr. Manager, Level 60 Manager
Job level change,pillarp@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 62 Director,Level 60 Sr Manager
Performance review,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2 Below expectations,,
Performance review,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team,,
Performance improvement plan,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2 Below expectations,,
Performance improvement plan,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Multiple conflicts with the team,,
```

> [!NOTE]
> İk veri türünü tanımlayan sütun için herhangi bir ad kullanabilirsiniz, çünkü 3. Adımda bağlayıcıyı ayarlayınca CSV dosyanızdaki sütunun adını İk veri türünü tanımlayan sütun olarak eşlersiniz. Ayrıca, bağlayıcıyı ayar takımıken veri türü sütunu için kullanılan değerleri de eşlersiniz.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Tek veri türü içeren bir CSV dosyasına HRScenario sütunu ekleme

Kurum gerektirilen İk sistemlerine ve İk verilerini CSV dosyasına nasıl aktaracaknıza bağlı olarak, tek bir İk veri türü içeren birden çok CSV dosyası oluşturmanız gerekir. Bu durumda, farklı CSV dosyalarından verileri içeri aktaran tek bir İk bağlayıcısı oluşturabilirsiniz. Bunu yapmak için, CSV dosyasına bir HRScenario sütunu eklemeniz ve İk veri türünü belirtmeniz gerekir. Ardından, her CSV dosyası için betiği çalıştırabilirsiniz, ancak bağlayıcı için aynı iş kimliğini kullanabilirsiniz. Bkz [. Adım 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>2. Adım: Azure Active Directory'de uygulama oluşturma

Sonraki adım, Azure Active Directory 'da (Azure AD) yeni uygulama oluşturmak ve kaydetmektir. Uygulama 3. Adımda oluştursanız da İk bağlayıcısını ifade edin. Bu uygulamayı oluşturmak, Azure AD'nin çalışan ve organizasyona erişmeye çalışan İk bağlayıcısı kimliğini doğrulamasını sağlayacaktır. Bu uygulama, 4. Adımda çalıştırarak İk verilerinizi Microsoft bulutuna yüklemek için betiğin kimliğini doğrulamak için de kullanılır. Bu Azure AD uygulamasını oluşturma işlemi sırasında, aşağıdaki bilgileri kaydetmeyi deneyin. Bu değerler 3. Adım ve 4. Adım'da kullanılacaktır.

- Azure AD uygulama kimliği (uygulama kimliği *veya istemci kimliği olarak da* *adlandırılan*)

- Azure AD uygulama sırrı (istemci sırrı olarak *da adlandırılan*)

- Kiracı Kimliği (dizin kimliği olarak *da adlandırılan*)

Azure AD'de uygulama oluşturmayla ilgili adım adım yönergeler için bkz[.](/azure/active-directory/develop/quickstart-register-app) Uygulamayı şu Microsoft kimlik platformu.

## <a name="step-3-create-the-hr-connector"></a>3. Adım: İk bağlayıcısını oluşturma

Sonraki adım, çalışma haftası içinde bir İk bağlayıcısı Microsoft 365 uyumluluk merkezi. 4. Adımda betiği çalıştırdıktan sonra, oluşturanız İk bağlayıcısı CSV dosyasından Microsoft 365 bilgi sağlar. Bağlayıcı oluşturmadan önce İk senaryolarının listesinin ve her birinin CSV sütun adlarının olduğundan emin olun. Bağlayıcıyı yapılandırırken, her senaryo için gereken verileri CSV dosyadaki gerçek sütun adlarına eşlemeniz gerekir. Alternatif olarak, bağlayıcıyı yapılandırırken örnek bir CSV dosyası yükleyebilirsiniz ve sihirbaz sütunların adını gerekli veri türleriyle eşlemeye yardımcı olur.

Bu adımı tamamlandıktan sonra, bağlayıcıyı musunuz? Betiği çalıştıracakken iş kimliğini kullanıcaz.

1. Veri bağlayıcıları'Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**seçin**</a>.

2. Veri **bağlayıcıları sayfasında İk** **(önizleme) öğesini tıklatın**.

3. İk **(önizleme) sayfasında Bağlayıcı** **ekle'ye tıklayın**.

4. Bağlantı **kur sayfasında,** şunları yapın ve ardından Sonraki'ne **tıklayın**:

   1. 2. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

   2. İk bağlayıcısı için bir ad yazın.

5. İk senaryoları sayfasında, verilerini içeri aktarmasını istediğiniz bir veya birden çok İk senaryosunu seçin ve ardından Sonraki'ye **tıklayın**.

   ![Bir veya daha fazla İk senaryosu seçin.](../media/HRConnectorScenarios.png)

6. Dosya eşleme yöntemi sayfasında, gerekirse bir dosya türü seçin, sonra aşağıdaki seçeneklerden birini belirleyin ve Ardından Sonraki'ye **tıklayın**.

   - **Upload dosyayı seçin**. Bu seçeneği belirtirseniz, 1 **. Upload'de** hazır yüklediğiniz CSV dosyasını karşıya yüklemek için örnek dosyaya tıklayın. Bu seçenek, bir açılan listeden CSV dosyanız içinde sütun adlarını hızla seçerek bunları daha önce seçtiğiniz İk senaryolarına uygun veri türleriyle eşlemenize olanak sağlar.

   VEYA

   - **Eşleme ayrıntılarını el ile girin**. Bu seçeneği belirtirseniz, bunları daha önce seçtiğiniz İk senaryolarına uygun veri türleriyle eşlemek için CSV dosyanıza sütunların adını yazmanız gerekir.

7. Dosya eşleme ayrıntıları sayfasında, örnek bir CSV dosyası yük isteyip yüklemenize ve bağlayıcıyı tek bir İk senaryosu için mi yoksa birden çok senaryo için mi yapılandırdınıza bağlı olarak, aşağıdakilerden birini yapın. Örnek bir dosya yükledikten sonra sütun adlarını yazmanız gerekir. Bunları açılan listeden seçersiniz.

    - Önceki adımda tek bir İk senaryosu seçtiysanız, 1. Adımda oluşturduğunuz CSV dosyasındaki uygun kutuların her biri için sütun üst bilgisi adlarını (parametreler olarak da *denir) yazın*. Yazınız sütun adları büyük/harfe duyarlı değildir, ancak CSV dosyanızdaki sütun adları boşluk içeriyorsa boşluk da içermeye emin olun. Daha önce de belirtildiği gibi, bu kutulara yazacak adların CSV dosyanız içinde yer alan parametre adlarla eşleşmesi gerekir. Örneğin, aşağıdaki ekran görüntüsü 1. Adımda gösterilen çalışan ve İk senaryolarına uygun örnek CSV dosyasındaki parametre adlarını gösterir.

    - Yukarıdaki adımda birden çok veri türü seçtiysanız, CSV dosyanıza İk veri türünü belirleyecek tanımlayıcı sütun adını girmeniz gerekir. Tanımlayıcı sütun adını girdikten sonra, bu İk veri türünü tanımlayan değeri yazın ve 1. Adımda oluşturduğunuz CSV dosyalarından seçilen veri türlerinin sütun üst bilgilerini her seçilen veri türü için uygun kutulara yazın. Daha önce de belirtildiği gibi, bu kutulara yazarak adların CSV dosyadaki sütun adlarla eşleşmesi gerekir.

8. Gözden Geçir **sayfasında** ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

   Bağlayıcının oluşturulmuş olduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfada, İk verilerinizi karşıya yüklemek üzere örnek betiği çalıştırmak üzere bir sonraki adımı tamamlamanız gereken iki önemli şey vardır.

   ![İş kimliği içeren sayfayı gözden geçirme ve örnek betik için github bağlantısı.](../media/HRConnector_Confirmation.png)

   1. **İş Kimliği.** Bir sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacak. Bu sayfadan veya bağlayıcı uçarak çıkış sayfasından kopyaleyebilirsiniz.

   2. **Örnek betik bağlantısı.** Örnek **betikle** erişmek için GitHub sitesine gitmek için buraya bağlantısına tıklayın (bağlantı yeni bir pencere açar). 4. Adımda betiği kopyalayıp açabilirsiniz. Alternatif olarak, betiği çalıştırınca yeniden erişmek için hedef yer işaretine yer işareti veya URL'yi kopyalayıp kopyalayabilirsiniz. Bu bağlantı bağlayıcı uç noktada da kullanılabilir.

9. **Bitti'ye tıklayın**.

   Yeni bağlayıcı, Bağlayıcılar sekmesindeki **listede** görüntülenir.

10. Özellikleri ve bağlayıcıyla ilgili diğer bilgileri içeren çıkış sayfasını görüntülemek için az önce oluşturduğunuz İk bağlayıcısını tıklatın.

   ![Yeni İk bağlayıcısı için uç uçarak çıkış sayfası.](../media/HRConnectorWizard7.png)

Henüz bunu yaptısanız, Azure Uygulama Kimliği ve Bağlayıcı iş **kimliği değerlerini** **kopyalayın**. Bir sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacak. Betiği, çıkış sayfasından da indirebilirsiniz (veya bir sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

Ayrıca, **Düzenle'ye** tıklar ve Dosya eşleme sayfasında tanımlandığı gibi Azure Uygulama Kimliği veya sütun başlığı **adlarını da değiştirebilirsiniz** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>4. Adım: İk verilerinizi karşıya yüklemek için örnek betiği çalıştırma

İk bağlayıcısını ayarlamanın son adımı, İk verilerini CSV dosyasında (1. Adımda oluşturduğunuz) Microsoft buluta yükecek örnek bir betik çalıştırmaktır. Betik, verileri özel olarak İk bağlayıcısı üzerinden karşıya yükler. Betiği çalıştırdikten sonra 3. Adımda oluşturduğunuz İk bağlayıcısı, İk verilerini Microsoft 365 kuruluşa aktararak Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilirsiniz. Betiği çalıştırdikten sonra, en güncel çalışan sonlandırma verileri Microsoft bulutuna yüklenmek için görevi günlük olarak otomatik olarak çalıştıracak şekilde zamanlamayı göz önünde bulundurabilirsiniz. Bkz [. Betiği otomatik olarak çalıştıracak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

1. Siteye örnek betikle erişmek için önceki adımda açık GitHub pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyalanmış URL'yi kullanın. Betike buradan da [erişsiniz](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Betiği **metin** görünümünde görüntülemek için Ham düğmesine tıklayın.

3. Örnek betikte yer alan tüm satırları kopyalayın ve sonra bunları bir metin dosyasına kaydedin.

4. Gerekiyorsa, kurum için örnek betiği değiştirin.

5. Örneğin, bir dosya Windows PowerShell kullanarak metin dosyasını bir betik dosyası `.ps1`olarak kaydedin`HRConnector.ps1`. Alternatif olarak, betiğin GitHub adı olarak da kullanabilirsiniz`upload_termination_records.ps1`.

6. Yerel bilgisayarınızda bir komut istemi açın ve betiği kaydedttiğiniz dizine gidin.

7. CSV dosyasındaki İk verilerini Microsoft bulutuna yüklemek için aşağıdaki komutu çalıştırın; örneğin:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   Aşağıdaki tabloda, bu betikle birlikte  kullanmak üzere parametreler ve bunların gerekli değerleri açık almaktadır. Önceki adımlarda elde edilen bilgiler, bu parametrelerin değerlerde kullanılır.

   | Parametre | Açıklama |
   |:-----|:-----|:-----|
   |`tenantId`|Bu, 2. Adımda Microsoft 365 kuruluş kimliğidir. Ayrıca, Azure AD yönetim merkezinde Genel Bakış blade'inde **bulunan** kiracı kimliğine de bakabilirsiniz. Bu, kurumlarınızı tanımlamak için kullanılır.|
   |`appId` |Bu, 2. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Betik, kimlik doğrulaması için Azure AD tarafından Microsoft 365 kullanılır. | 
   |`appSecret`|Bu, 2. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama sırrıdır. Bu, kimlik doğrulama için de kullanılır.|
   |`jobId`|Bu, 3. Adımda oluşturduğunuz İk bağlayıcısı için iş kimliğidir. Bu, Microsoft bulutuna yüklenen İk verilerini İk bağlayıcısı ile ilişkilendirmek için kullanılır.|
   |`filePath`|Bu, 1. Adımda oluşturduğunuz dosyanın (betikle aynı sistemde depolanan) dosya yoludur. Dosya yolunda boşluklardan kaçınmaya çalışma; aksi takdirde tek tırnak işareti kullanın.|
   |||

   Her parametre için gerçek değerlerin kullanılarak İk bağlayıcısı betiği söz dizimi örneği:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Karşıya yükleme başarılı olursa, betik Başarılı **Upload** görüntüler.

   > [!NOTE]
   > Yürütme ilkeleri nedeniyle önceki komutu çalıştırmada sorun ediyorsanız, yürütme ilkelerini ayarlama [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) hakkında yol gösterici bilgi için bkz. Yürütme İlkeleri hakkında ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy).

## <a name="step-5-monitor-the-hr-connector"></a>5. Adım: İk bağlayıcısını izleme

İk bağlayıcısını oluşturduk ve İk verilerinizi karşıya yüklemek için betiği çalıştırdıktan sonra bağlayıcıyı 24 saat içinde görüntü ve karşıya Microsoft 365 uyumluluk merkezi. Betiği düzenli aralıklarla otomatik olarak çalıştıracak şekilde zamanlarsanız, betiğin son çalıştırıı sonunda geçerli durumu da görüntüabilirsiniz.

1. Veri bağlayıcıları'Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**seçin**</a>.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır sayfayı görüntülemek için İk bağlayıcısını seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

   ![Özellikleri ve durumuyla İk bağlayıcısı çıkış sayfası.](../media/HRConnectorFlyout1.png)

3. İlerleme **Durumu'nın** **altında, Bağlayıcının** durum günlüğünü açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, betiğin her çalıştırısı ve CSV dosyasındaki verileri Microsoft bulutuna yüklemesi ile ilgili bilgileri içerir. 

   ![İk bağlayıcısı günlük dosyası, karşıya yüklenen CSV dosyasından sayı satırlarını görüntüler.](../media/HRConnectorLogFile.png)

   Bu `RecordsSaved` alan, karşıya yüklenen CSV dosyasındaki satır sayısını gösterir. Örneğin, CSV dosyasında dört satır varsa ve `RecordsSaved` betik CSV dosyasındaki tüm satırları başarıyla karşıya yükledikten sonra alanların değeri 4 olur.

4. Adımda betiği çalıştırmadısanız, Son içeri aktarma altında betiği indirme bağlantısı **görüntülenir**. Betiği indirebilir ve ardından betiği çalıştırmak için adımları izleyin.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama

Organizasyondan gelen en son İk verilerini Insider risk yönetimi çözümü gibi araçların kullanılabilir durumda olduğundan emin olmak için betiği günde bir gibi düzenli olarak otomatik olarak çalıştıracak şekilde zamanlamanızı öneririz. Bu ayrıca, CSV dosyasındaki İk verilerini benzer bir zamanlamada (aynı değil de) güncelleştirin, böylece organizasyondan ayrılmak isteyen çalışanlar hakkında en son bilgileri içerir. Amaç, İk bağlayıcısı tarafından Insider risk yönetimi çözümünün kullanılabilir hale getirilene kadar en güncel İk verilerini karşıya yüklemektir.

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda Başlat düğmesine Windows **ve** Görev Zamanlayıcı **yazın**.

2. Görev Zamanlayıcı **uygulamasını açmak** için tıklatın.

3. Eylemler bölümünde **Görev** **Oluştur'a tıklayın**.

4. Genel **sekmesinde** , zamanlanmış görev için açıklayıcı bir ad yazın; örneğin, **İk Bağlayıcısı Betiği**. ayrıca, isteğe bağlı bir açıklama da  eklersiniz.

5. Güvenlik **seçenekleri'nin** altında şunları yapın:

   1. Betiği yalnızca bilgisayarda oturum açtığınızda mı, yoksa oturum açtığınızda mı çalıştırmadıysanız çalıştırıp çalıştırmayıp çalıştırmaycasınız.

   1. En yüksek **ayrıcalıklarla çalıştır onay kutusunun** seçili olduğundan emin olun.

6. Tetikleyiciler **sekmesini** seçin, **Yeni'ye** tıklayın ve sonra şunları yapın:

   1. Komut **Ayarlar**, Günlük **seçeneğini** belirtin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün, belirtilen zamanda çalıştırın.

   1. Gelişmiş **ayarlar'ın** altında Etkin **onay kutusunun** seçili olduğundan emin olun.

   1. **Tamam'a tıklayın**.

7. Eylemler sekmesini **seçin** , **Yeni'ye** tıklayın ve sonra aşağıdaki işlemleri yapın:

   ![İk bağlayıcısı betiği için yeni bir zamanlanmış görev oluşturmak üzere eylem ayarları.](../media/HRConnectorScheduleTask1.png)

   1. Eylem **açılan** listesinde Program başlat'ın **seçili olduğundan** emin olun.

   1. **Program/betik** kutusunda Gözat'a tıklayın ve aşağıdaki konuma gidin ve yolu kutuda görüntülenecek şekilde seçin: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. Bağımsız değişken **ekle (isteğe bağlı)** kutusuna, 4. Adımda çalıştırdınız betik komutunun aynısını yapıştırın. Örneğin, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Başlangıç **(isteğe bağlı) kutusuna** , 4. Adımda çalıştırdınız betiğin klasör konumunu yapıştırın. Örneğin, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Yeni **eylemin** ayarlarını kaydetmek için Tamam'a tıklayın.

8. Zamanlanmış **görevi kaydetmek** için Görev Oluştur **penceresinde** Tamam'a tıklayın. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilirsiniz.

   Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.

   ![Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.](../media/HRConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştır zamanı ve çalıştırmanın zamanlandığı bir sonraki zaman görüntülenir. Görevi düzenlemek için çift tıkebilirsiniz.

   Ayrıca, betiğin uyumluluk merkezinde ilgili İk bağlayıcısını uç öğe sayfasında en son ne zaman çalıştır çalıştığını da doğruleyebilirsiniz.

## <a name="existing-hr-connectors"></a>Mevcut İk bağlayıcıları

13 Aralık 2021'de İk bağlayıcıları için çalışan profili verileri senaryosu yayınlandı. Bu tarihten önce bir İk bağlayıcısı oluşturduysanız, İk verilerinizin Microsoft bulutuna aktarmaya devam olması için mevcut örnekleri veya kuruluş İk bağlayıcılarını geçiririz. Bu işlevselliği korumak için hiçbir şey yapmak zorunda değilsiniz. Bu bağlayıcıları kesinti olmadan kullanmaya devam etmek için kullanabilirsiniz.

Çalışan profili veri senaryosunu uygulamak için yeni bir İk bağlayıcısı oluşturabilir ve bunu gereken şekilde yapılandırabilirsiniz. Yeni bir İk bağlayıcısı oluşturduklardan sonra, betiği bu makalede daha önce açıklanan çalışan profili verileriyle yeni bağlayıcının ve CSV [dosyalarının iş kimliğini](#csv-file-for-employee-profile-data-preview) kullanarak çalıştırın.
