---
title: Genel sağlık denetim verilerini içeri aktarmak için bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Yöneticiler, elektronik sağlık kayıtlarını (EHR) sağlık sisteminden Microsoft 365'e aktarmak için bir veri bağlayıcısı ayarlayabilir. Bu, çalışanlarınız tarafından hasta verilerine yetkisiz erişim etkinliğini algılamanıza yardımcı olmak için iç risk yönetimi ilkelerinde EHR verilerini kullanmanıza olanak tanır.
ms.openlocfilehash: be5429ea1a5fb4e2e2be6a7029f2401fcbdab94e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641394"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Sağlık EHR denetim verilerini içeri aktarmak için bağlayıcı ayarlama (önizleme)

Kuruluşunuzun Elektronik Sağlık Kayıtları (EHR) sisteminde kullanıcı etkinliği için denetim verilerini içeri aktarmak için Microsoft Purview uyumluluk portalı bir veri bağlayıcısı ayarlayabilirsiniz. Sağlık EHR sisteminizdeki denetim verileri, hastanın sağlık kayıtlarına erişmeyle ilgili olaylara ilişkin verileri içerir. Healthcare EHR denetim verileri, kuruluşunuzun hasta bilgilerine yetkisiz erişimden korunmasına yardımcı olmak için Microsoft 365 [insider risk yönetimi çözümü](insider-risk-management.md) tarafından kullanılabilir.

Healthcare bağlayıcısının ayarlanması aşağıdaki görevlerden oluşur:

- Azure Active Directory'de (Azure AD) sağlık EHR denetim verilerini içeren sekmeyle ayrılmış metin dosyasını kabul eden bir API uç noktasına erişmek için uygulama oluşturma.

- Bağlayıcı şemasında tanımlanan tüm gerekli alanları içeren bir metin dosyası oluşturma.

- Uyumluluk portalında bir Healthcare bağlayıcı örneği oluşturma.

- Sağlık EHR denetim verilerini API uç noktasına göndermek için bir betik çalıştırma.

- İsteğe bağlı olarak, denetim verilerini içeri aktarmak için betiği otomatik olarak çalışacak şekilde zamanlama.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- 3. Adımda Healthcare bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Kuruluşunuzun sağlık EHR sisteminden (günlük olarak) verilerin nasıl alınacağını veya dışarı aktarıldığını belirlemeniz ve 2. Adımda açıklanan bir metin dosyası oluşturmanız gerekir. 4. Adımda çalıştırdığınız betik, metin dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdığınız örnek betik, iç risk yönetimi çözümü tarafından kullanılabilmesi için sağlık ehr denetim verilerini metin dosyasından bağlayıcı API'sine iletir. Bu örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'de (Azure AD) yeni bir uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturduğunuz Healthcare bağlayıcısına karşılık gelir. Bu uygulamanın oluşturulması, Azure AD sağlık EHR denetim verilerini içeren metin dosyası için anında iletme isteğinin kimliğini doğrulamasını sağlar. Bu Azure AD uygulamasını oluştururken aşağıdaki bilgileri kaydettiğinizden emin olun. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (*uygulama kimliği* veya *istemci kimliği* olarak da adlandırılır)

- Azure AD uygulama gizli dizisi (*istemci gizli dizisi* olarak da adlandırılır)

- Kiracı Kimliği ( *dizin kimliği* olarak da adlandırılır)

Azure AD'da uygulama oluşturmaya yönelik adım adım yönergeler için bkz. [Uygulamayı Microsoft kimlik platformu kaydetme](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>2. Adım: Sağlık EHR denetim verileriyle metin dosyası hazırlama

Sonraki adım, çalışanların kuruluşunuzun sağlık EHR sistemindeki hasta sağlığı kayıtlarına erişimi hakkında bilgi içeren bir metin dosyası oluşturmaktır. Daha önce açıklandığı gibi, bu metin dosyasını sağlık EHR sisteminizden nasıl oluşturabileceğinizi belirlemeniz gerekir. Healthcare bağlayıcısı iş akışı, metin dosyasındaki verileri gerekli bağlayıcı şemasıyla eşlemek için sekmeyle ayrılmış değerler içeren bir metin dosyası gerektirir. Desteklenen dosya biçimi virgül (.csv), kanal (.psv) veya sekme (.tsv) ile ayrılmış metin dosyasıdır.

> [!NOTE]
> Denetim verilerini içeren metin dosyasının boyutu üst sınırı 3 GB'tır. En fazla satır sayısı 5 milyondur. Ayrıca, yalnızca sağlık EHR sisteminizdeki ilgili denetim verilerini eklediğinizden emin olun.

Aşağıdaki tabloda, insider risk yönetimi senaryolarını etkinleştirmek için gereken alanlar listelenmektedir. Bu alanların bir alt kümesi zorunludur. Bu alanlar yıldız (*) ile vurgulanır. Metin dosyasında zorunlu alanlardan herhangi biri eksikse, dosya doğrulanmaz ve dosyadaki veriler içeri aktarılamaz.

|Alan|Kategori|
|:----|:----------|
| Oluşturma Zamanı *<br/>Olay Adı*<br/>İş İstasyonu Kimliği<br/>Olay Bölümü<br/>Olay Kategorisi |Bu alanlar, sağlık EHR sisteminizdeki erişim etkinliği olaylarını tanımlamak için kullanılır.|
| Hasta Kayıt Defteri Kimliği<br/>Hasta Adı *<br/>Hasta İkinci Adı <br/>Hastanın Soyadı* <br/>Hasta Adres Satırı 1* <br/>Hasta Adres Satırı 2<br/>Patient City* <br/>Hasta Posta Kodu*  <br/>Hasta Durumu <br/>Hasta Ülke <br/>Hasta Bölümü              | Bu alanlar hasta profili bilgilerini tanımlamak için kullanılır.|
| Kısıtlı Erişim Nedeni*<br/> Kısıtlı Erişim Açıklaması | Bu alanlar kısıtlı kayıtlara erişimi tanımlamak için kullanılır.|
| E-posta Adresi (UPN) veya SamAccountName*<br/>Çalışan Kullanıcı Adı <br/> Çalışan Kimliği <br/> Çalışan Soyadı <sup>1</sup> <br/> Çalışan Adı <sup>1</sup> | Bu alanlar, Aile/Komşu/Çalışan kayıtlarına erişimi belirlemek için gereken adres ve ad eşleştirme için çalışan profili bilgilerini tanımlamak için kullanılır. |
|||

> [!NOTE] 
> <sup>1</sup> Bu alan sağlık EHR sisteminizde varsayılan olarak kullanılamayabilir. Metin dosyasının bu alanı içerdiğinden emin olmak için dışarı aktarmayı yapılandırmanız gerekir.

## <a name="step-3-create-the-healthcare-connector"></a>3. Adım: Healthcare bağlayıcısını oluşturma

Sonraki adım, uyumluluk portalında bir Healthcare bağlayıcısı oluşturmaktır. 4. Adımda betiği çalıştırdıktan sonra, 2. Adımda oluşturduğunuz metin dosyası işlenir ve 1. Adımda ayarladığınız API uç noktasına iletilir. Bu adımda, bağlayıcıyı oluştururken oluşturulan JobId değerini kopyaladığınızdan emin olun. Betiği çalıştırdığınızda JobId değerini kullanacaksınız.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Genel Bakış** sekmesinde **Sağlık (önizleme)** seçeneğine tıklayın.

3. **Healthcare (önizleme)** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. Hizmet koşullarını kabul edin.

5. **Kimlik doğrulama kimlik bilgileri** sayfasında aşağıdakileri yapın ve **İleri'ye** tıklayın:

    1. 1. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

    2. Sağlık bağlayıcısı için bir ad yazın.

6. **Dosya eşleme yöntemi** sayfasında, aşağıdaki seçeneklerden birini seçin ve **İleri'ye** tıklayın.

   - **Örnek bir dosyayı karşıya yükleyin**. Bu seçeneği seçerseniz, 2. Adımda hazırladığınız dosyayı karşıya yüklemek için **Örnek dosyayı karşıya yükle'ye** tıklayın. Bu seçenek, sütunları sağlık bağlayıcısı için gerekli şemaya eşlemek için bir açılan listeden metin dosyanızdaki sütun adlarını hızla seçmenize olanak tanır. 

    Veya

   - **Eşleme ayrıntılarını el ile sağlayın**. Bu seçeneği belirlerseniz, sütunları sağlık bağlayıcısı için gerekli şemaya eşlemek için metin dosyanızdaki sütunların adını yazmanız gerekir.

7. **Dosya eşleme ayrıntıları** sayfasında, önceki adımda örnek bir dosyayı karşıya yükleyip yüklemediğinize bağlı olarak aşağıdakilerden birini yapın:

   - Örnek dosyadaki sütunları sağlık bağlayıcısı için gerekli her alanla eşlemek için açılan listeleri kullanın.

    Veya

   - Her alan için, 2. Adımda hazırladığınız ve sağlık bağlayıcısı alanına karşılık gelen dosyadan sütun adını yazın.

8. **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

   Bağlayıcının oluşturulduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfa, sağlık hizmetleri EHR denetim verilerinizi karşıya yüklemek için örnek betiği çalıştırmak için bir sonraki adımı tamamlamanız gereken iki önemli öğe içerir.

    - **İş Kimliği.** Sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacaktır. Bu sayfadan veya bağlayıcı açılır sayfasından kopyalayabilirsiniz.

    - **Örnek betiğin bağlantısı.** Örnek betike erişmek için GitHub sitesine gitmek için **buraya** tıklayın (bağlantı yeni bir pencere açar). 4. Adım'da betiği kopyalayabilmeniz için bu pencereyi açık tutun. Alternatif olarak, betiği çalıştırdığınızda yeniden erişebilmek için hedefe yer işareti ekleyebilir veya URL'yi kopyalayabilirsiniz. Bu bağlantı bağlayıcı açılır sayfasında da kullanılabilir.

9. **Bitti'ye** tıklayın.

   Yeni bağlayıcı **Bağlayıcılar** sekmesindeki listede görüntülenir.

10. Bağlayıcıyla ilgili özellikleri ve diğer bilgileri içeren açılır sayfayı görüntülemek için yeni oluşturduğunuz Healthcare bağlayıcısına tıklayın.

Henüz yapmadıysanız **, Azure Uygulaması Kimliği** ve **Bağlayıcı iş kimliği** değerlerini kopyalayabilirsiniz. Sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacaktır. Betiği açılır sayfadan da indirebilirsiniz (veya sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

**Dosya eşleme** sayfasında tanımladığınız Azure Uygulaması kimliğini veya sütun üst bilgisi adlarını değiştirmek için **Düzenle'ye** de tıklayabilirsiniz.

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>4. Adım: Sağlık ehr denetim verilerinizi karşıya yüklemek için örnek betiği çalıştırın

Healthcare bağlayıcısını ayarlamanın son adımı, metin dosyasındaki (1. Adımda oluşturduğunuz) sağlık EHR denetim verilerini Microsoft buluta yükleyecek örnek bir betik çalıştırmaktır. Özellikle betik verileri Healthcare bağlayıcısına yükler. Betiği çalıştırdıktan sonra, 3. Adımda oluşturduğunuz Healthcare bağlayıcısı, sağlık ehr denetim verilerini Microsoft 365 kuruluşunuza aktarır ve burada Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilir. Betiği çalıştırdıktan sonra, en güncel çalışan sonlandırma verilerinin Microsoft buluta yüklenmesi için günlük olarak otomatik olarak çalıştırılacak bir görev zamanlamayı göz önünde bulundurun. Bkz. [(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Daha önce belirtildiği gibi, denetim verilerini içeren metin dosyasının boyutu üst sınırı 3 GB'tır. En fazla satır sayısı 5 milyondur. Bu adımda çalıştırdığınız betiğin büyük metin dosyalarından denetim verilerini içeri aktarması yaklaşık 30 ila 40 dakika sürer. Ayrıca betik, büyük metin dosyalarını 100 bin satırlık daha küçük bloklara böler ve ardından bu blokları sırayla içeri aktarır.

1. GitHub sitesine örnek betikle erişmek için önceki adımda açık bıraktığınız pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyaladığınız URL'yi kullanın. Betike [buradan](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1) da erişebilirsiniz.

2. Betiği metin görünümünde görüntülemek için **Ham** düğmesine tıklayın.

3. Örnek betikteki tüm satırları kopyalayın ve bir metin dosyasına kaydedin.

4. Gerekirse kuruluşunuzun örnek betiğini değiştirin.

5. metin dosyasını Windows PowerShell betik dosyası olarak kaydetmek için ; örneğin, `HealthcareConnector.ps1`bir dosya adı soneki `.ps1`kullanın.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydettiğiniz dizine gidin.

7. Metin dosyasındaki sağlık denetim verilerini Microsoft buluta yüklemek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Aşağıdaki tabloda, bu betikle kullanılacak parametreler ve bunların gerekli değerleri açıklanmaktadır. Önceki adımlarda elde ettiğiniz bilgiler bu parametrelerin değerlerinde kullanılır.

|Parametre  |Açıklama|
|:----------|:----------|
|tenantId|Bu, 1. Adımda edindiğiniz Microsoft 365 kuruluşunuzun kimliğidir. Ayrıca, Azure AD yönetim merkezindeki **Genel Bakış** dikey penceresinde kuruluşunuzun kiracı kimliğini de alabilirsiniz. Bu, kuruluşunuzu tanımlamak için kullanılır.|
|Appıd|Bu, 1. Adımda Azure AD oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Bu, Azure AD tarafından betik Microsoft 365 kuruluşunuza erişmeye çalıştığında kimlik doğrulaması için kullanılır.|
|appSecret|Bu, 1. Adımda Azure AD oluşturduğunuz uygulamanın Azure AD uygulama gizli dizisidir. Bu, kimlik doğrulaması için de kullanılır.|
|Jobıd|Bu, 3. Adımda oluşturduğunuz Healthcare bağlayıcısının iş kimliğidir. Bu, Microsoft buluta yüklenen sağlık ehr denetim verilerini Healthcare bağlayıcısı ile ilişkilendirmek için kullanılır.|
|Filepath|Bu, 2. Adımda oluşturduğunuz metin dosyasının (betikle aynı sistemde depolanan) dosya yoludur. Dosya yolunda boşluklardan kaçınmaya çalışın; aksi takdirde tek tırnak işareti kullanın.|
|||

Aşağıda, her parametre için gerçek değerleri kullanan Healthcare bağlayıcısı betiğinin söz dizimi örneği verilmiştir:

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Karşıya yükleme başarılı olursa, betik **Karşıya Yükleme Başarılı** iletisini görüntüler.

> [!NOTE]
> Yürütme ilkeleri nedeniyle önceki komutu çalıştırırken sorun yaşıyorsanız, yürütme ilkelerini ayarlama hakkında yönergeler için [Bkz. Yürütme İlkeleri Hakkında](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) .

## <a name="step-5-monitor-the-healthcare-connector"></a>5. Adım: Healthcare bağlayıcısını izleme

Healthcare bağlayıcısını oluşturduktan ve EHR denetim verilerinizi gönderdikten sonra bağlayıcıyı görüntüleyebilir ve uyumluluk portalında karşıya yükleme durumunu karşıya yükleyebilirsiniz. Betiği düzenli olarak otomatik olarak çalışacak şekilde zamanlarsanız, betiğin son çalıştırıldığından sonra geçerli durumu da görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılan sayfayı görüntülemek için Healthcare bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. **Son içeri aktarma'nın** altında Günlüğü **indir** bağlantısına tıklayarak bağlayıcının durum günlüğünü açın (veya kaydedin). Bu günlük, betiğin her çalıştırıldığında ve metin dosyasındaki verileri Microsoft buluta yükleyişiyle ilgili bilgileri içerir.

    alanı, `RecordsSaved` karşıya yüklenen metin dosyasındaki satır sayısını gösterir. Örneğin, metin dosyası dört satır içeriyorsa, betik metin dosyasındaki `RecordsSaved` tüm satırları başarıyla karşıya yüklediyse alanların değeri 4 olur.

4. Adımda betiği çalıştırmadıysanız, **Son içeri aktarma** altında betiği indirme bağlantısı görüntülenir. Betiği indirebilir ve ardından betiği çalıştırmak için adımları izleyebilirsiniz.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama

Sağlık hizmetleri EHR sisteminizdeki en son denetim verilerinin insider risk yönetimi çözümü gibi araçlar tarafından kullanılabildiğinden emin olmak için betiği günlük olarak otomatik olarak çalışacak şekilde zamanlamanızı öneririz. Bu, aynı metin dosyasındaki EHR denetim verilerini benzer bir zamanlamada (aynı değilse) güncelleştirmenizi ve böylece çalışanlarınızın hasta kayıtlarına erişim etkinlikleriyle ilgili en son bilgileri içermesini de gerektirir. Amaç, Healthcare bağlayıcısının bunu insider risk yönetimi çözümünün kullanımına sunabilmesi için en güncel denetim verilerini karşıya yüklemektir.

Betiği her gün otomatik olarak çalıştırmak için Windows'ta Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda, Windows **Başlat** düğmesine tıklayın ve görev **zamanlayıcı** yazın.

2. **Görev Zamanlayıcı** uygulamasına tıklayarak uygulamayı açın.

3. **Eylemler** bölümünde **Görev Oluştur'a** tıklayın.

4. **Genel** sekmesinde, zamanlanan görev için açıklayıcı bir ad yazın; örneğin, **Healthcare bağlayıcı betiği**. İsteğe bağlı bir açıklama da ekleyebilirsiniz.

5. **Güvenlik seçenekleri'nin** altında aşağıdakileri yapın:

    1. Betiğin yalnızca bilgisayarda oturum açtığınızda mı yoksa oturum açtığınızda mı çalıştırılmadığını mı belirleyebilirsiniz.

    2. **En yüksek ayrıcalıklarla çalıştır** onay kutusunun seçili olduğundan emin olun.

6. **Tetikleyiciler** sekmesini seçin, **Yeni'ye** tıklayın ve aşağıdaki işlemleri yapın:

    1. **Ayarlar'ın** altında **Günlük** seçeneğini belirleyin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün belirtilen saatte çalıştırılır.

    2. **Gelişmiş ayarlar'ın** altında **Etkin** onay kutusunun seçili olduğundan emin olun.

    3. **Tamam'a** tıklayın.

7. **Eylemler** sekmesini seçin, **Yeni'ye** tıklayın ve ardından aşağıdaki işlemleri yapın:

   ![Sağlık bağlayıcısı betiği için yeni bir zamanlanmış görev oluşturmak için eylem ayarları.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. **Eylem** açılan listesinde **Program başlat'ın** seçili olduğundan emin olun.

    2. **Program/betik** kutusunda **Gözat'a** tıklayın ve aşağıdaki konuma gidin ve yolu kutuda görüntülenecek şekilde seçin: C:.0.exe.

    3. **Bağımsız değişken ekle (isteğe bağlı)** kutusunda, 4. Adımda çalıştırdığınız betik komutunu yapıştırın. Örneğin, `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. Başlangıç yeri **(isteğe bağlı)** kutusuna, 4. Adımda çalıştırdığınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Healthcare\audit.

    5. Yeni eylemin ayarlarını kaydetmek için **Tamam'a** tıklayın.

8. **Görev Oluştur** penceresinde **Tamam'a** tıklayarak zamanlanmış görevi kaydedin. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilir.

   Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.

   ![Sağlık bağlayıcısı betiği için yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştırıldığı ve bir sonraki çalıştırma zamanlaması görüntülenir. Görevi düzenlemek için çift tıklayabilirsiniz.

   Ayrıca, uyumluluk merkezindeki ilgili Healthcare bağlayıcısının açılır sayfasında betiğin en son ne zaman çalıştığını da doğrulayabilirsiniz.
