---
title: Epic EHR verilerini içeri aktarmak için bağlayıcı ayarlama
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
description: Yöneticiler, kuruluşunuzun Epic sisteminden Microsoft 365 elektronik sağlık kayıtlarını (EHR) içeri aktarmak için bir veri bağlayıcısı ayarlayabilir. Bu, çalışanlarınız tarafından hasta verilerine yetkisiz erişim etkinliğini algılamanıza yardımcı olmak için iç risk yönetimi ilkelerinde Epic EHR verilerini kullanmanıza olanak tanır.
ms.openlocfilehash: 55f33358af7b53dc6042fce94b1ddc92e9f130fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078011"
---
# <a name="set-up-a-connector-to-import-epic-ehr-audit-data-preview"></a>Epic EHR denetim verilerini içeri aktarmak için bağlayıcı ayarlama (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşunuzun Epic Elektronik Sağlık Kayıtları (EHR) sistemindeki kullanıcı etkinliği için denetim kayıtlarını içeri aktarmak için Microsoft Purview uyumluluk portalında bir veri bağlayıcısı ayarlayabilirsiniz. Epic EHR sisteminizdeki denetim kayıtları, hastanın sağlık kayıtlarına erişmeyle ilgili olayların kayıtlarını içerir. Epic EHR denetim kayıtları, kuruluşunuzun hasta bilgilerine yetkisiz erişimden korunmasına yardımcı olmak için Microsoft 365 [insider risk yönetimi çözümü](insider-risk-management.md) tarafından kullanılabilir.

Epic bağlayıcısının ayarlanması aşağıdaki görevlerden oluşur:

- Epic EHR denetim kayıtlarını içeren sekmeyle ayrılmış metin dosyasını kabul eden bir API uç noktasına erişmek için Azure Active Directory 'de (Azure AD) bir uygulama oluşturma.

- Bağlayıcı şemasında tanımlanan tüm gerekli alanları içeren bir metin dosyası oluşturma.

- Uyumluluk portalında Epic bağlayıcı örneği oluşturma.

- Epic EHR denetim kayıtlarını API uç noktasına göndermek için bir betik çalıştırma.

- İsteğe bağlı olarak, denetim kayıtlarını içeri aktarmak için betiği otomatik olarak çalışacak şekilde zamanlama.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- 3. Adımda Epic bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Kuruluşunuzun Epic EHR sisteminden (günlük olarak) verilerin nasıl alınacağını veya dışarı aktarıldığını belirlemeniz ve 2. Adımda açıklanan bir metin dosyası oluşturmanız gerekir. 4. Adımda çalıştırdığınız betik, metin dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdığınız örnek betik, insider risk yönetimi çözümü tarafından kullanılabilmesi için metin dosyasındaki Epic EHR denetim kayıtlarını bağlayıcı API'sine iletir. Bu örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'de (Azure AD) yeni bir uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturduğunuz Epic bağlayıcısına karşılık gelir. Bu uygulamayı oluşturmak, Azure AD'nin Epic EHR denetim kayıtlarını içeren metin dosyası için anında iletme isteğinin kimliğini doğrulamasını sağlar. Bu Azure AD uygulamasını oluştururken aşağıdaki bilgileri kaydettiğinizden emin olun. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği ( *uygulama kimliği* veya *istemci kimliği* olarak da adlandırılır)

- Azure AD uygulama gizli dizisi ( *istemci gizli dizisi* olarak da adlandırılır)

- Kiracı Kimliği ( *dizin kimliği* olarak da adlandırılır)

Azure AD'de uygulama oluşturmaya yönelik adım adım yönergeler için bkz. [Uygulamayı Microsoft kimlik platformu kaydetme](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-epic-ehr-audit-records"></a>2. Adım: Epic EHR denetim kayıtlarıyla metin dosyası hazırlama

Sonraki adım, çalışanların kuruluşunuzun Epic EHR sistemindeki hasta sağlığı kayıtlarına erişimi hakkında bilgi içeren bir metin dosyası oluşturmaktır. Daha önce açıklandığı gibi, bu metin dosyasını Epic EHR sisteminizden nasıl oluşturabileceğinizi belirlemeniz gerekir. Epic bağlayıcısı iş akışı, metin dosyasındaki verileri gerekli bağlayıcı şemasıyla eşlemek için sekmeyle ayrılmış değerlere sahip bir metin dosyası gerektirir. Desteklenen dosya biçimi, kanal veya sekmeyle ayrılmış bir .txt dosyasıdır.

> [!NOTE]
> Denetim verilerini içeren metin dosyasının boyutu üst sınırı 3 GB'tır. En fazla satır sayısı 5 milyondur. Ayrıca, yalnızca sağlık EHR sisteminizdeki ilgili denetim verilerini eklediğinizden emin olun.

Aşağıdaki tabloda, insider risk yönetimi senaryolarını etkinleştirmek için gereken alanlar listelenmektedir. Bu alanların bir alt kümesi zorunludur. Bu alanlar yıldız (*) ile vurgulanır. Metin dosyasında zorunlu alanlardan herhangi biri eksikse, dosya doğrulanmaz ve dosyadaki veriler içeri aktarılamaz.

|Alan|Kategori|
|:----|:----------|
| ACCESS_LOG. *<br/>ACCESS_TIME ACCESS_LOG_METRIC. METRIC_NAME*<br/>ACCESS_LOG. WORKSTATION_ID<br/>ZCMETRIC\_\_ GROUP.NAME<br/>ZCACCESS\_\_ ACTION.NAME |Bu alanlar, Epic EHR sisteminizdeki erişim etkinliği olaylarını tanımlamak için kullanılır.|
| HASTA. PAT_MRN_ID<br/>HASTA. PAT_FIRST_NAME* <br/>HASTA. PAT_MIDDLE_NAME <br/>HASTA. PAT_LAST_NAME* <br/>HASTA. ADD_LINE_1* <br/>HASTA. ADD_LINE_2  <br/>HASTA. ŞEHİr* <br/>PATIENT.ZIP*  <br/>ZC_STATE.NAME <br/>ZC_COUNTRY.NAME <br/>CLARITY_DEP. DEPARTMENT_NAME              | Bu alanlar hasta profili bilgilerini tanımlamak için kullanılır.|
| ZC_BTG_REASON.NAME*<br/> PAT_BTG_AUDIT. BTG_EXPLANATION | Bu alanlar kısıtlı kayıtlara erişimi tanımlamak için kullanılır.|
| EMP. SYSTEM_LOGIN*<br/>CLARITY_EMP. USER_ID <br/> employee_last_name <sup>1</sup> <br/> employee_first_name <sup>1</sup>                | Bu alanlar, Aile/Komşu/Çalışan kayıtlarına erişimi belirlemek için gereken adres ve ad eşleştirme için çalışan profili bilgilerini tanımlamak için kullanılır. |
|||

> [!NOTE]
> Epic'ten yalnızca ilgili Günlük ölçümlerini dışarı aktardığınızdan emin olun. 
> <sup>1</sup> Bu alan Epic'te varsayılan olarak kullanılamaz. Metin dosyasının bu alanı içerdiğinden emin olmak için dışarı aktarmayı yapılandırmanız gerekir.

## <a name="step-3-create-the-epic-connector"></a>3. Adım: Epic bağlayıcısını oluşturma

Sonraki adım, uyumluluk portalında bir Epic bağlayıcısı oluşturmaktır. 4. Adımda betiği çalıştırdıktan sonra, 2. Adımda oluşturduğunuz metin dosyası işlenir ve 1. Adımda ayarladığınız API uç noktasına iletilir. Bu adımda, bağlayıcıyı oluştururken oluşturulan JobId değerini kopyaladığınızdan emin olun. Betiği çalıştırdığınızda JobId değerini kullanacaksınız.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Epic bağlayıcısı altındaki Veri bağlayıcıları** sayfasında **Görünüm'e** tıklayın.

3. **Epic bağlayıcısı** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Bağlantıyı kur** sayfasında aşağıdakileri yapın ve **İleri'ye** tıklayın:

    1. 2. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

    2. Epic bağlayıcısı için bir ad yazın.

5. **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

   Bağlayıcının oluşturulduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfa, Epic EHR denetim kayıtları verilerinizi karşıya yüklemek için örnek betiği çalıştırmak için bir sonraki adımı tamamlamanız gereken iki önemli öğe içerir.

    örnek betik için iş kimliğini ve github bağlantısını içeren gözden geçirme sayfası

    1. **İş Kimliği.** Sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacaktır. Bu sayfadan veya bağlayıcı açılır sayfasından kopyalayabilirsiniz.

    2. **Başvuru şeması.** Epic sisteminizdeki hangi alanların bağlayıcı tarafından kabul edildiği anlamak için şemaya bakın. Bu, gerekli tüm Epic veritabanı alanlarını içeren bir dosya oluşturmanıza yardımcı olur.

    3. **Örnek betiğin bağlantısı.** Örnek betike erişmek için GitHub sitesine gitmek için **buraya** tıklayın (bağlantı yeni bir pencere açar). 4. Adım'da betiği kopyalayabilmeniz için bu pencereyi açık tutun. Alternatif olarak, betiği çalıştırdığınızda yeniden erişebilmek için hedefe yer işareti ekleyebilir veya URL'yi kopyalayabilirsiniz. Bu bağlantı bağlayıcı açılır sayfasında da kullanılabilir.

6. **Bitti'ye** tıklayın.

   Yeni bağlayıcı **Bağlayıcılar** sekmesindeki listede görüntülenir.

7. Yeni oluşturduğunuz Epic bağlayıcısına tıklayarak bağlayıcıyla ilgili özellikleri ve diğer bilgileri içeren açılır sayfayı görüntüleyin.

Henüz yapmadıysanız **, Azure Uygulaması Kimliği** ve **Bağlayıcı iş kimliği** değerlerini kopyalayabilirsiniz. Sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacaktır. Betiği açılır sayfadan da indirebilirsiniz (veya sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

**Dosya eşleme** sayfasında tanımladığınız Azure Uygulaması kimliğini veya sütun üst bilgisi adlarını değiştirmek için **Düzenle'ye** de tıklayabilirsiniz.

## <a name="step-4-run-the-sample-script-to-upload-your-epic-ehr-audit-records"></a>4. Adım: Epic EHR denetim kayıtlarınızı karşıya yüklemek için örnek betiği çalıştırın

Epic bağlayıcısını ayarlamanın son adımı, Metin dosyasındaki (1. Adımda oluşturduğunuz) Epic EHR denetim kayıtları verilerini Microsoft buluta yükleyecek örnek bir betik çalıştırmaktır. Özellikle betik verileri Epic bağlayıcısına yükler. Betiği çalıştırdıktan sonra, 3. Adımda oluşturduğunuz Epic bağlayıcısı, Epic EHR denetim kayıtlarını Microsoft 365 kuruluşunuza aktarır ve burada Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilir. Betiği çalıştırdıktan sonra, en güncel çalışan sonlandırma verilerinin Microsoft buluta yüklenmesi için günlük olarak otomatik olarak çalıştırılacak bir görev zamanlamayı göz önünde bulundurun. Bkz. [(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Daha önce belirtildiği gibi, denetim verilerini içeren metin dosyasının boyutu üst sınırı 3 GB'tır. En fazla satır sayısı 5 milyondur. Bu adımda çalıştırdığınız betiğin büyük metin dosyalarından denetim verilerini içeri aktarması yaklaşık 30 ila 40 dakika sürer. Ayrıca betik, büyük metin dosyalarını 100 bin satırlık daha küçük bloklara böler ve ardından bu blokları sırayla içeri aktarır.

1. Örnek betikle GitHub sitesine erişmek için önceki adımda açık bıraktığınız pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyaladığınız URL'yi kullanın. Betike [buradan](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1) da erişebilirsiniz.

2. Betiği metin görünümünde görüntülemek için **Ham** düğmesine tıklayın.

3. Örnek betikteki tüm satırları kopyalayın ve bir metin dosyasına kaydedin.

4. Gerekirse kuruluşunuzun örnek betiğini değiştirin.

5. metin dosyasını Windows PowerShell betik dosyası olarak kaydetmek için ; örneğin, `EpicConnector.ps1`bir dosya adı soneki `.ps1`kullanın.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydettiğiniz dizine gidin.

7. Metin dosyasındaki Epic denetim verilerini Microsoft buluta yüklemek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\EpicConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Aşağıdaki tabloda, bu betikle kullanılacak parametreler ve bunların gerekli değerleri açıklanmaktadır. Önceki adımlarda elde ettiğiniz bilgiler bu parametrelerin değerlerinde kullanılır.

|Parametre  |Açıklama|
|:----------|:----------|
|tenantId|Bu, 1. Adımda aldığınız Microsoft 365 kuruluşunuzun kimliğidir. Ayrıca, Azure AD yönetim merkezindeki **Genel Bakış** dikey penceresinde kuruluşunuzun kiracı kimliğini de alabilirsiniz. Bu, kuruluşunuzu tanımlamak için kullanılır.|
|Appıd|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Bu, betik Microsoft 365 kuruluşunuza erişmeye çalıştığında Azure AD tarafından kimlik doğrulaması için kullanılır.|
|appSecret|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama gizli dizisidir. Bu, kimlik doğrulaması için de kullanılır.|
|Jobıd|Bu, 3. Adımda oluşturduğunuz Epic bağlayıcısının iş kimliğidir. Bu, Microsoft buluta yüklenen Epic EHR denetim kayıtlarını Epic bağlayıcısıyla ilişkilendirmek için kullanılır.|
|Filepath|Bu, 2. Adımda oluşturduğunuz metin dosyasının (betikle aynı sistemde depolanan) dosya yoludur. Dosya yolunda boşluklardan kaçınmaya çalışın; aksi takdirde tek tırnak işareti kullanın.|
|||

Her parametre için gerçek değerleri kullanan Epic bağlayıcı betiğinin söz dizimi örneği aşağıda verilmiştir:

```powershell
.\EpicConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\epic_audit_records.txt'
```

Karşıya yükleme başarılı olursa, betik **Upload Başarılı** iletisini görüntüler.

> [!NOTE]
> Yürütme ilkeleri nedeniyle önceki komutu çalıştırırken sorun yaşıyorsanız, yürütme ilkelerini ayarlama hakkında yönergeler için [Bkz. Yürütme İlkeleri Hakkında](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) .

## <a name="step-5-monitor-the-epic-connector"></a>5. Adım: Epic bağlayıcısını izleme

Epic bağlayıcısını oluşturup EHR denetim kayıtlarınızı gönderdikten sonra bağlayıcıyı görüntüleyebilir ve uyumluluk portalında karşıya yükleme durumunu karşıya yükleyebilirsiniz. Betiği düzenli olarak otomatik olarak çalışacak şekilde zamanlarsanız, betiğin son çalıştırıldığından sonra geçerli durumu da görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için Epic bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. **Son içeri aktarma'nın** altında Günlüğü **indir** bağlantısına tıklayarak bağlayıcının durum günlüğünü açın (veya kaydedin). Bu günlük, betiğin her çalıştırıldığında ve metin dosyasındaki verileri Microsoft buluta yükleyişiyle ilgili bilgileri içerir.

    Epic bağlayıcısı günlük dosyası, karşıya yüklenen metin dosyasındaki sayı satırlarını görüntüler

    alanı, `RecordsSaved` karşıya yüklenen metin dosyasındaki satır sayısını gösterir. Örneğin, metin dosyası dört satır içeriyorsa, betik metin dosyasındaki `RecordsSaved` tüm satırları başarıyla karşıya yüklediyse alanların değeri 4 olur.

4. Adımda betiği çalıştırmadıysanız, **Son içeri aktarma** altında betiği indirme bağlantısı görüntülenir. Betiği indirebilir ve ardından betiği çalıştırmak için adımları izleyebilirsiniz.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama

Epic EHR sisteminizdeki en son denetim kayıtlarının insider risk yönetimi çözümü gibi araçlar tarafından kullanılabildiğinden emin olmak için betiği günlük olarak otomatik olarak çalışacak şekilde zamanlamanızı öneririz. Bunun için aynı metin dosyasındaki Epic denetim kaydı verilerini benzer bir zamanlamaya göre (aynı değilse) güncelleştirmeniz de gerekir, böylece hasta kayıtları hakkındaki en son bilgileri çalışanlarınız tarafından erişim etkinliklerine içerir. Amaç, Epic bağlayıcısının bunu insider risk yönetimi çözümünün kullanımına sunabilmesi için en güncel denetim kayıtlarını karşıya yüklemektir. 

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda, Windows **Başlat** düğmesine tıklayın ve görev **zamanlayıcı** yazın.

2. **Görev Zamanlayıcı** uygulamasına tıklayarak uygulamayı açın.

3. **Eylemler** bölümünde **Görev Oluştur'a** tıklayın.

4. **Genel** sekmesinde, zamanlanan görev için açıklayıcı bir ad yazın; örneğin **, Epic bağlayıcı betiği**. İsteğe bağlı bir açıklama da ekleyebilirsiniz.

5. **Güvenlik seçenekleri'nin** altında aşağıdakileri yapın:

    1. Betiğin yalnızca bilgisayarda oturum açtığınızda mı yoksa oturum açtığınızda mı çalıştırılmadığını mı belirleyebilirsiniz.

    2. **En yüksek ayrıcalıklarla çalıştır** onay kutusunun seçili olduğundan emin olun.

6. **Tetikleyiciler** sekmesini seçin, **Yeni'ye** tıklayın ve aşağıdaki işlemleri yapın:

    1. **Ayarlar** altında **Günlük** seçeneğini belirleyin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün belirtilen saatte çalıştırılır.

    2. **Gelişmiş ayarlar'ın** altında **Etkin** onay kutusunun seçili olduğundan emin olun.

    3. **Tamam'a** tıklayın.

7. **Eylemler** sekmesini seçin, **Yeni'ye** tıklayın ve ardından aşağıdaki işlemleri yapın:

   ![Epic bağlayıcı betiği için yeni bir zamanlanmış görev oluşturmak için eylem ayarları.](../media/EpicConnectorScheduleTask1.png)

    1. **Eylem** açılan listesinde **Program başlat'ın** seçili olduğundan emin olun.

    2. **Program/betik** kutusunda **Gözat'a** tıklayın ve aşağıdaki konuma gidin ve yolu kutuda görüntülenecek şekilde seçin: C:.0.exe.

    3. **Bağımsız değişken ekle (isteğe bağlı)** kutusunda, 4. Adımda çalıştırdığınız betik komutunu yapıştırın. Örneğin, `.\EpicConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Epic\audit\records.txt"`

    4. Başlangıç yeri **(isteğe bağlı)** kutusuna, 4. Adımda çalıştırdığınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Epic\audit.

    5. Yeni eylemin ayarlarını kaydetmek için **Tamam'a** tıklayın.

8. **Görev Oluştur** penceresinde **Tamam'a** tıklayarak zamanlanmış görevi kaydedin. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilir.

   Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.

   ![Sağlık bağlayıcısı betiği için yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.](../media/EpicConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştırıldığı ve bir sonraki çalıştırma zamanlaması görüntülenir. Görevi düzenlemek için çift tıklayabilirsiniz.

   Ayrıca, uyumluluk merkezindeki ilgili Epic bağlayıcısının açılır sayfasında betiğin en son ne zaman çalıştığını da doğrulayabilirsiniz.
