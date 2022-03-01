---
title: Genel sağlık denetim verilerini içeri aktaracak bir bağlayıcı ayarlama
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
description: Yöneticiler, elektronik sağlık kayıtlarının (EHR) verilerini sağlık sisteminden içeri aktarması için bir veri bağlayıcısı Microsoft 365. Bu sayede, çalışanlarının hasta verilerine yetkisiz erişim etkinliğini algılamanıza yardımcı olmak için Insider risk yönetimi ilkelerde EHR verilerini kullanabilirsiniz.
ms.openlocfilehash: 1be80dea0bd5692f07edbe34df1bf61cd85f3337
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010144"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Sağlık EHR denetim verilerini (önizleme) içeri aktarma için bir bağlayıcı ayarlama

Web günlüğünde, Microsoft 365 uyumluluk merkezi Elektronik Sağlık Kayıtları (EHR) sisteminde kullanıcı etkinliğinin denetim verilerini içeri aktaracak bir veri bağlayıcısı kurabilirsiniz. Sağlık EHR sisteminiz üzerinden verileri denetleme, hastanın sağlık kayıtlarına erişmeyle ilgili olaylara yönelik veriler içerir. Sağlık EHR denetim verileri, kuruluş Microsoft 365 hasta bilgilerine yetkisiz erişime karşı korunmasına yardımcı olmak için [insider risk](insider-risk-management.md) yönetimi çözümü tarafından kullanılabilir.

Sağlık bağlayıcısı ayarlama, aşağıdaki görevlerden oluşur:

- Azure Active Directory EHR denetim verilerini içeren sekmeyle ayrılmış metin dosyasını kabul eden bir API uç noktasına erişmek için Azure Active Directory'ta (Azure AD) uygulama oluşturma.

- Bağlayıcı şemasında tanımlandığı gibi tüm gerekli alanlarla bir metin dosyası oluşturma.

- Çalışma sayfalarında bir Sağlık bağlayıcısı Microsoft 365 uyumluluk merkezi.

- Sağlık EHR denetim verilerini API uç noktasına itmek için bir betik çalıştırma.

- İsteğe bağlı olarak, betiği, denetim verilerini içeri aktaracak şekilde otomatik olarak çalıştıracak şekilde zamanlayarak.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- Adım 3'te Sağlık bağlayıcısı oluşturan kullanıcıya, bu bağlayıcıda Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Verilerinizin, kuruma yönelik sağlık EHR sisteminden (günlük olarak) nasıl alın ya da dışarı aktarın, sonra da 2. Adımda açıklanan bir metin dosyası oluşturmanız gerekir. 4. Adımda çalıştırdınız betik, metin dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdınız örnek betik, metin dosyasındaki sağlık EHR denetim verilerini bağlayıcı API'sinde sunar ve böylelikle Insider risk yönetimi çözümü tarafından kullanılabilir. Bu örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'da (Azure AD) yeni uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluştursanız da Sağlık bağlayıcısı'ne karşılık gelecek. Bu uygulamanın oluşturulması, Azure AD'nin sağlık EHR denetim verilerini içeren metin dosyası için anında istekte kimlik doğrulaması yapmalarını sağlar. Bu Azure AD uygulamasını oluşturma işlemi sırasında, aşağıdaki bilgileri kaydetmeyi deneyin. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (uygulama kimliği *veya istemci kimliği olarak da* *adlandırılan*)

- Azure AD uygulama sırrı (istemci sırrı olarak *da adlandırılan*)

- Kiracı Kimliği (dizin kimliği olarak *da adlandırılan*)

Azure AD'de uygulama oluşturmayla ilgili adım adım yönergeler için bkz[.](\azure\active-directory\develop\quickstart-register-app) Uygulamayı şu Microsoft kimlik platformu.

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>2. Adım: Sağlık EHR denetim verileriyle metin dosyası hazırlama

Sonraki adım, çalışanların kurum sağdan sağlık EHR sisteminde hasta durumu kayıtlarına erişmesi hakkında bilgi içeren bir metin dosyası oluşturmaktır. Daha önce de belirtildiği gibi, bu metin dosyasının sağlık EHR sisteminiz tarafından nasıl oluşturulacını belirlemeniz gerekir. Sağlık bağlayıcısı iş akışı, metin dosyasındaki verileri gerekli bağlayıcı şemasıyla eşlemek için sekmeyle ayrılmış değerlere sahip bir metin dosyası gerektirir. Desteklenen dosya biçimi virgül (.csv), boru (.psv) veya sekme (.tsv) ayrılmış metin dosyasıdır.

> [!NOTE]
> Denetim verilerini içeren metin dosyasının boyut üst boyutu 3 GB'tır. En fazla satır sayısı 5 milyon'luk bir sayıdır. Ayrıca, yalnızca sağlık EHR sisteminiz tarafından ilgili denetim verilerini de dahil etmek için bu verileri dahil etmek gerekir.

Aşağıdaki tabloda, Insider risk yönetimi senaryolarını etkinleştirmek için gereken alanlar listelemektedir. Bu alanların bir alt kümesi zorunludur. Bu alanlar yıldız (*) ile vurgulanır. Metin dosyasında zorunlu alanlardan herhangi biri eksikse, dosya doğrulanmaz ve dosyada yer alan veriler aktarılmaz.

|Alan|Kategori|
|:----|:----------|
| Oluşturma *TimeEvent<br/> Name*<br/>İş Istasyonu Kimliği<br/>Olay Bölümü<br/>Etkinlik Kategorisi |Bu alanlar sağlık EHR sisteminize erişim etkinliği etkinliklerini tanımlamak için kullanılır.|
| Hasta Kayıt Kimliği<br/>Patient First *NameEnt<br/> Middle Name <br/>Patient Last Name* <br/>Hasta Adresi Satırı 1* <br/>Hasta Adresi Satırı 2<br/>Patient City* <br/>Hasta Posta Kodu*  <br/>Patient State <br/>Hasta Ülkesi <br/>Patient Department              | Bu alanlar hasta profili bilgilerini tanımlamak için kullanılır.|
| Kısıtlı Erişim Nedeni*<br/> Kısıtlı Erişim Açıklaması | Bu alanlar, kısıtlanmış kayıtlara erişimi tanımlamak için kullanılır.|
| E-posta Adresi (UPN) veya SamAccountName*<br/>Çalışan Kullanıcı Adı <br/> Çalışan Kimliği <br/> Çalışan Soyadı <sup>1</sup> <br/> Çalışan Adı <sup>1</sup> | Bu alanlar Aile/Komşu/Çalışan kayıtlarına erişimi belirlemek üzere gerekli adres ve ad eşleştirmesi için çalışan profili bilgilerini tanımlamak üzere kullanılır. |
|||

> [!NOTE] 
> <sup>1</sup> Bu alan sağlık EHR sisteminiz için varsayılan olarak kullanılamıyor olabilir. Metin dosyasında bu alanın olduğundan emin olmak için dışarı aktarmayı yapılandırmanız gerekir.

## <a name="step-3-create-the-healthcare-connector"></a>3. Adım: Sağlık bağlayıcısı oluşturma

Sonraki adım, bu bağlantıda bir Sağlık bağlayıcısı Microsoft 365 uyumluluk merkezi. 4. Adımda betiği çalıştırdikten sonra, 2. Adımda oluşturduğunuz metin dosyası işlenir ve 1. Adımda ayar oluşturduğunuz API uç noktasına gönderilir. Bu adımda, bağlayıcıyı  oluşturmak için oluşturulan JobId'i kopyalayıp kopyalamayı dikkat edin. Betiği çalıştıracakken JobId'i kullanıcaz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda Veri **bağlayıcıları'na gidin** ve bu bağlayıcılara tıklayın.

2. Genel Bakış **sekmesinde** Sağlık (önizleme **)'ye tıklayın**.

3. Sağlık ( **önizleme) sayfasında Bağlayıcı** **ekle'ye tıklayın**.

4. Hizmet koşullarını kabul eder.

5. Kimlik doğrulama **kimlik bilgileri sayfasında** , şunları yapın ve ardından Sonraki'ye **tıklayın**:

    1. 1. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

    2. Sağlık bağlayıcısı için bir ad yazın.

6. Dosya eşleme **yöntemi sayfasında** , aşağıdaki seçeneklerden birini belirleyin ve ardından Sonraki'ye **tıklayın**.

   - **Upload dosyayı seçin**. Bu seçeneği belirtirseniz, 2 **. Upload hazırlığında** karşıya yüklemek için örnek dosyaya tıklayın. Bu seçenek, sütunları sağlık bağlayıcısı için gerekli şemayla eşlemek için, metin dosyanız içinde bir açılan listeden sütun adlarını hızla seçmenizi sağlar. 

    Veya

   - **Eşleme ayrıntılarını el ile girin**. Bu seçeneği belirtirseniz, sütunları sağlık bağlayıcısı için gerekli şemayla eşlemek için metin dosyanıza sütunların adını yazmanız gerekir.

7. Dosya **eşleme ayrıntıları sayfasında** , önceki adımda örnek bir dosya yük isteyip yüklemenize bağlı olarak, aşağıdaki işlemlerden birini yapın:

   - Örnek dosyanın sütunlarını sağlık bağlayıcısı için gerekli her alanla eşlemek için açılan listeleri kullanın.

    Veya

   - Her alan için, 2. Adımda hazırlarsanız ve sağlık bağlayıcısı alanıyla ilgili dosyanın sütun adını yazın.

8. Gözden Geçir **sayfasında** ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

   Bağlayıcının oluşturulmuş olduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfada, sağlık EHR denetim verilerinizi karşıya yüklemek üzere örnek betiği çalıştırmak üzere bir sonraki adımı tamamlamanız gereken iki önemli şey vardır.

    - **İş Kimliği.** Bir sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacak. Bu sayfadan veya bağlayıcı uçarak çıkış sayfasından kopyaleyebilirsiniz.

    - **Örnek betik bağlantısı.** Örnek **betikle** erişmek için GitHub sitesine gitmek için buraya bağlantısına tıklayın (bağlantı yeni bir pencere açar). 4. Adımda betiği kopyalayıp açabilirsiniz. Alternatif olarak, betiği çalıştırınca yeniden erişmek için hedef yer işaretine yer işareti veya URL'yi kopyalayıp kopyalayabilirsiniz. Bu bağlantı bağlayıcı uç noktada da kullanılabilir.

9. **Bitti'ye tıklayın**.

   Yeni bağlayıcı, Bağlayıcılar sekmesindeki **listede** görüntülenir.

10. Özellikleri ve bağlayıcıyla ilgili diğer bilgileri içeren sayfayı görüntülemek için, az önce oluşturduğunuz Sağlık bağlayıcısı'ne tıklayın.

Henüz bunu yaptısanız, Azure Uygulama Kimliği ve Bağlayıcı iş **kimliği değerlerini** **kopyalayın**. Bir sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacak. Betiği, çıkış sayfasından da indirebilirsiniz (veya bir sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

Ayrıca, **Düzenle'ye** tıklar ve Dosya eşleme sayfasında tanımlandığı gibi Azure Uygulama Kimliği veya sütun başlığı **adlarını da değiştirebilirsiniz** .

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>4. Adım: Sağlık EHR denetim verilerinizi karşıya yüklemek için örnek betiği çalıştırma

Sağlık bağlayıcısı ayarlamanın son adımı, sağlık EHR denetim verilerini metin dosyasına (1. Adımda oluşturduğunuz) Microsoft buluta yükecek örnek bir betik çalıştırmaktır. Betik, verileri Sağlık bağlayıcısı'nına yükler. Betiği çalıştırdikten sonra, 3. Adımda oluşturduğunuz Sağlık bağlayıcısı, sağlık EHR denetim verilerini Microsoft 365 sisteminize aktararak Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilir. Betiği çalıştırdikten sonra, en güncel çalışan sonlandırma verileri Microsoft bulutuna yüklenmek için görevi günlük olarak otomatik olarak çalıştıracak şekilde zamanlamayı göz önünde bulundurabilirsiniz. Bkz [. (İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Daha önce de belirtildiği gibi, denetim verilerini içeren metin dosyasının boyut üst boyutu 3 GB'tır. En fazla satır sayısı 5 milyon'luk bir sayıdır. Bu adımda çalıştıracak olan betiğin, denetim verilerini büyük metin dosyalarından içeri aktarması yaklaşık 30 - 40 dakika sürer. Buna ek olarak, betik büyük metin dosyalarını 100.000 satırlık daha küçük bloklara böler ve sonra bu blokları sırayla içeri aktarın.

1. Siteye örnek betikle erişmek için önceki adımda açık GitHub pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyalanmış URL'yi kullanın. Betike buradan da [erişsiniz](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Betiği **metin** görünümünde görüntülemek için Ham düğmesine tıklayın.

3. Örnek betikte yer alan tüm satırları kopyalayın ve sonra bunları bir metin dosyasına kaydedin.

4. Gerekiyorsa, kurum için örnek betiği değiştirin.

5. Örneğin, bir dosya Windows PowerShell kullanarak metin dosyasını bir betik dosyası `.ps1`olarak kaydedin`HealthcareConnector.ps1`.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydeden dizine gidin.

7. Metin dosyasındaki sağlık denetim verilerini Microsoft buluta yüklemek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Aşağıdaki tabloda, bu betikle birlikte  kullanmak üzere parametreler ve bunların gerekli değerleri açık almaktadır. Önceki adımlarda elde edilen bilgiler, bu parametrelerin değerlerde kullanılır.

|Parametre  |Açıklama|
|:----------|:----------|
|tenantId|Bu, 1. Adımda Microsoft 365 kuruluş kimliğidir. Ayrıca, Azure AD yönetim merkezinde Genel Bakış blade'inde **bulunan** kiracı kimliğine de bakabilirsiniz. Bu, kurumlarınızı tanımlamak için kullanılır.|
|appId|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Betik, kimlik doğrulaması için Azure AD tarafından Microsoft 365 kullanılır.|
|appSecret|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama sırrıdır. Bu, kimlik doğrulama için de kullanılır.|
|jobId|Bu, 3. Adımda oluşturduğunuz Sağlık bağlayıcısı için iş kimliğidir. Bu, Microsoft bulutuna yüklenen sağlık EHR denetim verilerini Sağlık bağlayıcısı ile ilişkilendirmek için kullanılır.|
|filePath|Bu, 2. Adımda oluşturduğunuz metin dosyasının (betikle aynı sistemde depolanan) dosya yoludur. Dosya yolunda boşluklardan kaçınmaya çalışma; aksi takdirde tek tırnak işareti kullanın.|
|||

Her parametre için gerçek değerleri kullanan Sağlık bağlayıcısı betiği söz dizimi örneği:

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Karşıya yükleme başarılı olursa, betik Başarılı **Upload** görüntüler.

> [!NOTE]
> Yürütme ilkeleri nedeniyle önceki komutu çalıştırmada sorun ediyorsanız, yürütme ilkelerini ayarlama [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) hakkında yol gösterici bilgi için bkz. Yürütme İlkeleri hakkında ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy).

## <a name="step-5-monitor-the-healthcare-connector"></a>5. Adım: Sağlık bağlayıcılarını izleme

Sağlık bağlayıcısı oluşturduk ve EHR denetim verilerinizi iletirken, bağlayıcıyı 2013'te sın Microsoft 365 uyumluluk merkezi. Betiği düzenli aralıklarla otomatik olarak çalıştıracak şekilde zamanlarsanız, betiğin son çalıştırıı sonunda geçerli durumu da görüntüabilirsiniz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra sağlık bağlayıcısı öğesini seçerek açılır sayfayı görüntüleyin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. Son **içeri aktarma'nın** **altında, Bağlayıcının** durum günlüğünü açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, betiğin her çalıştırısı ve metin dosyasındaki verileri Microsoft bulutuna yüklemesi ile ilgili bilgileri içerir.

    Bu `RecordsSaved` alan, karşıya yüklenen metin dosyasındaki satır sayısını gösterir. Örneğin, metin dosyasında dört satır varsa ve `RecordsSaved` betik metin dosyasındaki tüm satırları başarıyla karşıya yükledikten sonra alanların değeri 4 olur.

4. Adımda betiği çalıştırmadısanız, Son içeri aktarma altında betiği indirme bağlantısı **görüntülenir**. Betiği indirebilir ve ardından betiği çalıştırmak için adımları izleyin.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama

Sağlık EHR sisteminiz ile ilgili en son denetim verilerini, Insider risk yönetim çözümü gibi araçların kullanılabilir olduğundan emin olmak için betiği günlük olarak otomatik olarak çalıştıracak şekilde zamanlamanızı öneririz. Bu ayrıca, aynı metin dosyasındaki EHR denetim verilerini benzer bir zamanlamada (aynı değil de) güncelleştirerek çalışanlarının hasta kayıtlarına erişim etkinlikleriyle ilgili en son bilgileri içerdiğini de gerektirir. Sağlık bağlayıcısı tarafından Insider risk yönetimi çözümünün kullanılabilir hale getirisinde en güncel denetim verilerini karşıya yükleme hedefi vardır.

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda Başlat düğmesine Windows **ve** Görev Zamanlayıcı **yazın**.

2. Görev Zamanlayıcı **uygulamasını açmak** için tıklatın.

3. Eylemler bölümünde **Görev** **Oluştur'a tıklayın**.

4. Genel **sekmesinde** , zamanlanmış görev için açıklayıcı bir ad yazın; örneğin, **Sağlık bağlayıcısı betiği**. ayrıca, isteğe bağlı bir açıklama da  eklersiniz.

5. Güvenlik **seçenekleri'nin** altında şunları yapın:

    1. Betiği yalnızca bilgisayarda oturum açtığınızda mı, yoksa oturum açtığınızda mı çalıştırmadıysanız çalıştırıp çalıştırmayıp çalıştırmaycasınız.

    2. En yüksek **ayrıcalıklarla çalıştır onay kutusunun** seçili olduğundan emin olun.

6. Tetikleyiciler **sekmesini** seçin, **Yeni'ye** tıklayın ve sonra şunları yapın:

    1. Komut **Ayarlar**, Günlük **seçeneğini** belirtin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün, belirtilen zamanda çalıştırın.

    2. Gelişmiş **ayarlar'ın** altında Etkin **onay kutusunun** seçili olduğundan emin olun.

    3. **Tamam'a tıklayın**.

7. Eylemler sekmesini **seçin** , **Yeni'ye** tıklayın ve sonra aşağıdaki işlemleri yapın:

   ![Sağlık bağlayıcısı betiği için yeni bir zamanlanmış görev oluşturmak üzere eylem ayarları.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. Eylem **açılan** listesinde Program başlat'ın **seçili olduğundan** emin olun.

    2. **Program/betik** kutusunda Gözat'a tıklayın ve aşağıdaki konuma gidin ve yolu şu kutuda görüntülenecek şekilde seçin: C:.0.exe.

    3. Bağımsız değişken **ekle (isteğe bağlı)** kutusuna, 4. Adımda çalıştırdınız betik komutunun aynısını yapıştırın. Örneğin, `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. Başlangıç **(isteğe bağlı) kutusuna** , 4. Adımda çalıştırdınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Healthcare\audit.

    5. Yeni **eylemin** ayarlarını kaydetmek için Tamam'a tıklayın.

8. Zamanlanmış **görevi kaydetmek** için Görev Oluştur **penceresinde** Tamam'a tıklayın. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilirsiniz.

   Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.

   ![Sağlık bağlayıcısı betiği için yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştır zamanı ve çalıştırmanın zamanlandığı bir sonraki zaman görüntülenir. Görevi düzenlemek için çift tıkebilirsiniz.

   Ayrıca, betiğin uyumluluk merkezinde ilgili Sağlık bağlayıcısı uç sayfa üzerinde en son ne zaman çalıştığını da doğruleyebilirsiniz.
