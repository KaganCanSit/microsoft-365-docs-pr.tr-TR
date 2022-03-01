---
title: Desya EHR verilerini içeri aktaracak şekilde bağlayıcı ayarlama
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
description: Yöneticiler, elektronik sağlık kayıtlarının (EHR) verilerini, organizasyon unser sisteminden Içeri Aktarması için bir veri bağlayıcısı Microsoft 365. Bu, çalışanlarının hasta verilerine yetkisiz erişim etkinliğini algılamanıza yardımcı olmak için Insider risk yönetimi ilkelerde Destan EHR verilerini kullanmanızı sağlar.
ms.openlocfilehash: 0da7386aa2b230492fedd5fdac5477d204aa63a8
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010166"
---
# <a name="set-up-a-connector-to-import-epic-ehr-audit-data-preview"></a>DestanSı EHR denetim verilerini (önizleme) içeri aktaracak bir bağlayıcı ayarlama

Kuruluş yönetim sisteminde, Microsoft 365 uyumluluk merkezi Electronic Healthcare Records (EHR) sisteminde kullanıcı etkinliğinin denetim kayıtlarını içeri aktaracak bir veri bağlayıcısı kurabilirsiniz. Destan EHR sisteminiz tarafından denetlenen kayıtlar, hastanın sağlık kayıtlarına erişmeyle ilgili olayların kayıtlarını içerir. Destan EHR denetim kayıtları, Microsoft 365 hasta bilgilerine yetkisiz erişime karşı korunmasına yardımcı olmak için en iyi [Insider risk](insider-risk-management.md) yönetimi çözümü tarafından kullanılabilir.

Destansı bağlayıcısı ayarlama, aşağıdaki görevlerden oluşur:

- Destani EHR denetim kayıtlarının bulunduğu sekmeyle ayrılmış metin dosyasını kabul eden BIR API uç noktasına erişmek için Azure Active Directory'de (Azure AD) uygulama oluşturma.

- Bağlayıcı şemasında tanımlandığı gibi tüm gerekli alanlarla bir metin dosyası oluşturma.

- Birden çok öğede bir Destansı bağlayıcı örneği Microsoft 365 uyumluluk merkezi.

- Destan EHR denetim kayıtlarını API uç noktasına itmek için bir betik çalıştırma.

- İsteğe bağlı olarak, betiği, denetim kayıtlarını içeri aktaracak şekilde otomatik olarak çalıştıracak şekilde zamanlayarak.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- 3. Adımda Mikser bağlayıcısı oluşturan kullanıcıya, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Verilerinizin, kurumnizin Destan EHR sisteminden (günlük olarak) nasıl alın- alın ya da dışarı aktarın ve 2. Adımda açıklanan bir metin dosyası oluşturun. 4. Adımda çalıştırdınız betik, metin dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdınız örnek betik, metin dosyasından Destan EHR denetim kayıtlarını bağlayıcı API'sinde iletir; böylelikle insider risk yönetimi çözümü tarafından kullanılabilir. Bu örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'da (Azure AD) yeni uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturmakta istediğiniz Destansı bağlayıcıya karşılık gelecek. Bu uygulama oluşturmak, Azure AD'nin Destan EHR denetim kayıtlarını içeren metin dosyası için anında istekte kimlik doğrulaması yapmalarını sağlar. Bu Azure AD uygulamasını oluşturma işlemi sırasında, aşağıdaki bilgileri kaydetmeyi deneyin. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (uygulama kimliği *veya istemci kimliği olarak da* *adlandırılan*)

- Azure AD uygulama sırrı (istemci sırrı olarak *da adlandırılan*)

- Kiracı Kimliği (dizin kimliği olarak *da adlandırılan*)

Azure AD'de uygulama oluşturmayla ilgili adım adım yönergeler için bkz[.](\azure\active-directory\develop\quickstart-register-app) Uygulamayı şu Microsoft kimlik platformu.

## <a name="step-2-prepare-a-text-file-with-epic-ehr-audit-records"></a>2. Adım: Destan EHR denetim kayıtlarıyla metin dosyası hazırlama

Sonraki adım, çalışanların kurum un Destan EHR sisteminde hasta durumu kayıtlarına erişmesi hakkında bilgi içeren bir metin dosyası oluşturmaktır. Daha önce de belirtildiği gibi, Bu metin dosyasının Netantanya EHR sisteminden nasıl oluşturulacaklarını belirlemeniz gerekir. Destansı bağlayıcı iş akışı, metin dosyasındaki verileri gerekli bağlayıcı şemasıyla eşlemek için sekmeyle ayrılmış değerlere sahip bir metin dosyası gerektirir. Desteklenen dosya biçimi, sekmeyle veya sekmeyle ayrılmış bir .txt biçimidir.

> [!NOTE]
> Denetim verilerini içeren metin dosyasının boyut üst boyutu 3 GB'tır. En fazla satır sayısı 5 milyon'luk bir sayıdır. Ayrıca, yalnızca sağlık EHR sisteminiz tarafından ilgili denetim verilerini de dahil etmek için bu verileri dahil etmek gerekir.

Aşağıdaki tabloda, Insider risk yönetimi senaryolarını etkinleştirmek için gereken alanlar listelemektedir. Bu alanların bir alt kümesi zorunludur. Bu alanlar yıldız (*) ile vurgulanır. Metin dosyasında zorunlu alanlardan herhangi biri eksikse, dosya doğrulanmaz ve dosyada yer alan veriler aktarılmaz.

|Alan|Kategori|
|:----|:----------|
| ACCESS_LOG. *<br/>ACCESS_TIME ACCESS_LOG_METRIC. METRIC_NAME*<br/>ACCESS_LOG. WORKSTATION_ID<br/>ZCMETRIC\_\_ GROUP.NAME<br/>ZCACCESS\_\_ ACTION.NAME |Bu alanlar, Destan EHR sisteminize erişim etkinliği etkinliklerini tanımlamak için kullanılır.|
| HASTA. PAT_MRN_ID<br/>HASTA. PAT_FIRST_NAME* <br/>HASTA. PAT_MIDDLE_NAME <br/>HASTA. PAT_LAST_NAME* <br/>HASTA. ADD_LINE_1* <br/>HASTA. ADD_LINE_2  <br/>HASTA. ŞEHIR* <br/>PATIENT.ZIP*  <br/>ZC_STATE.AD <br/>ZC_COUNTRY.AD <br/>CLARITY_DEP. DEPARTMENT_NAME              | Bu alanlar hasta profili bilgilerini tanımlamak için kullanılır.|
| ZC_BTG_REASON.AD*<br/> PAT_BTG_AUDIT. BTG_EXPLANATION | Bu alanlar, kısıtlanmış kayıtlara erişimi tanımlamak için kullanılır.|
| EMP. SYSTEM_LOGIN*<br/>CLARITY_EMP. USER_ID <br/> employee_last_name <sup>1</sup> <br/> employee_first_name <sup>1</sup>                | Bu alanlar Aile/Komşu/Çalışan kayıtlarına erişimi belirlemek üzere gerekli adres ve ad eşleştirmesi için çalışan profili bilgilerini tanımlamak üzere kullanılır. |
|||

> [!NOTE]
> Destansı'dan yalnızca ilgili Günlük ölçülerini dışarı aktarıyor olun. 
> <sup>1</sup> Bu alan Destansı'da varsayılan olarak kullanılamaz. Metin dosyasında bu alanın olduğundan emin olmak için dışarı aktarmayı yapılandırmanız gerekir.

## <a name="step-3-create-the-epic-connector"></a>3. Adım: Destansı bağlayıcısı oluşturma

Sonraki adım, bu bağlantıda bir Destansı bağlayıcısı Microsoft 365 uyumluluk merkezi. 4. Adımda betiği çalıştırdikten sonra, 2. Adımda oluşturduğunuz metin dosyası işlenir ve 1. Adımda ayar oluşturduğunuz API uç noktasına gönderilir. Bu adımda, bağlayıcıyı  oluşturmak için oluşturulan JobId'i kopyalayıp kopyalamayı dikkat edin. Betiği çalıştıracakken JobId'i kullanıcaz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda Veri **bağlayıcıları'na gidin** ve bu bağlayıcılara tıklayın.

2. Veri **bağlayıcıları sayfasında, Destansı** bağlayıcısı'nın **altında Görünüm'e** **tıklayın**.

3. **Destansı bağlayıcısı** sayfasında Bağlayıcı **ekle'ye tıklayın**.

4. Bağlantı **kur sayfasında,** şunları yapın ve ardından Sonraki'ne **tıklayın**:

    1. 2. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

    2. Destansı bağlayıcısı için bir ad yazın.

5. Gözden Geçir **sayfasında** ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

   Bağlayıcının oluşturulmuş olduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfada, Destan EHR denetim kayıtları verilerinizi karşıya yüklemek üzere örnek betiği çalıştırmak üzere bir sonraki adımı tamamlamanız gereken iki önemli şey vardır.

    İş kimliği içeren sayfayı gözden geçirme ve örnek betik için github bağlantısı

    1. **İş Kimliği.** Bir sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacak. Bu sayfadan veya bağlayıcı uçarak çıkış sayfasından kopyaleyebilirsiniz.

    2. **Başvuru şeması.** Destansı sisteminiz tarafından bağlayıcı tarafından hangi alanların kabul edilmeye baş olduğunu anlamak için şemaya bakın. Bu, gerekli tüm Destansı veritabanı alanlarıyla bir dosya oluşturmanıza yardımcı olur.

    3. **Örnek betik bağlantısı.** Örnek **betikle** erişmek için GitHub sitesine gitmek için buraya bağlantısına tıklayın (bağlantı yeni bir pencere açar). 4. Adımda betiği kopyalayıp açabilirsiniz. Alternatif olarak, betiği çalıştırınca yeniden erişmek için hedef yer işaretine yer işareti veya URL'yi kopyalayıp kopyalayabilirsiniz. Bu bağlantı bağlayıcı uç noktada da kullanılabilir.

6. **Bitti'ye tıklayın**.

   Yeni bağlayıcı, Bağlayıcılar sekmesindeki **listede** görüntülenir.

7. Özellikleri ve bağlayıcıyla ilgili diğer bilgileri içeren uç uç sayfayı görüntülemek için az önce oluşturduğunuz Destansı bağlayıcısı'ne tıklayın.

Henüz bunu yaptısanız, Azure Uygulama Kimliği ve Bağlayıcı iş **kimliği değerlerini** **kopyalayın**. Bir sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacak. Betiği, çıkış sayfasından da indirebilirsiniz (veya bir sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

Ayrıca, **Düzenle'ye** tıklar ve Dosya eşleme sayfasında tanımlandığı gibi Azure Uygulama Kimliği veya sütun başlığı **adlarını da değiştirebilirsiniz** .

## <a name="step-4-run-the-sample-script-to-upload-your-epic-ehr-audit-records"></a>4. Adım: DestanSı EHR denetim kayıtlarınızı karşıya yüklemek için örnek betiği çalıştırın

Destansı bağlayıcısı ayarlamanın son adımı, Destan EHR denetim kayıtları verilerini metin dosyasına (1. Adımda oluşturduğunuz) Microsoft buluta yükecek örnek bir betik çalıştırmaktır. Özel olarak, betik, verileri Destan konnektöre yükler. Betiği çalıştırdikten sonra, 3. Adımda oluşturduğunuz Destansı bağlayıcısı, Destan EHR denetim verilerini Microsoft 365 kuruluşuna aktararak Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilirsiniz. Betiği çalıştırdikten sonra, en güncel çalışan sonlandırma verileri Microsoft bulutuna yüklenmek için görevi günlük olarak otomatik olarak çalıştıracak şekilde zamanlamayı göz önünde bulundurabilirsiniz. Bkz [. (İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Daha önce de belirtildiği gibi, denetim verilerini içeren metin dosyasının boyut üst boyutu 3 GB'tır. En fazla satır sayısı 5 milyon'luk bir sayıdır. Bu adımda çalıştıracak olan betiğin, denetim verilerini büyük metin dosyalarından içeri aktarması yaklaşık 30 - 40 dakika sürer. Buna ek olarak, betik büyük metin dosyalarını 100.000 satırlık daha küçük bloklara böler ve sonra bu blokları sırayla içeri aktarın.

1. Siteye örnek betikle erişmek için önceki adımda açık GitHub pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyalanmış URL'yi kullanın. Betike buradan da [erişsiniz](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Betiği **metin** görünümünde görüntülemek için Ham düğmesine tıklayın.

3. Örnek betikte yer alan tüm satırları kopyalayın ve sonra bunları bir metin dosyasına kaydedin.

4. Gerekiyorsa, kurum için örnek betiği değiştirin.

5. Örneğin, bir dosya Windows PowerShell kullanarak metin dosyasını bir betik dosyası `.ps1`olarak kaydedin`EpicConnector.ps1`.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydeden dizine gidin.

7. Metin dosyasındaki Destansı denetim verilerini Microsoft buluta yüklemek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\EpicConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Aşağıdaki tabloda, bu betikle birlikte  kullanmak üzere parametreler ve bunların gerekli değerleri açık almaktadır. Önceki adımlarda elde edilen bilgiler, bu parametrelerin değerlerde kullanılır.

|Parametre  |Açıklama|
|:----------|:----------|
|tenantId|Bu, 1. Adımda Microsoft 365 kuruluş kimliğidir. Ayrıca, Azure AD yönetim merkezinde Genel Bakış blade'inde **bulunan** kiracı kimliğine de bakabilirsiniz. Bu, kurumlarınızı tanımlamak için kullanılır.|
|appId|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Betik, kimlik doğrulaması için Azure AD tarafından Microsoft 365 kullanılır.|
|appSecret|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama sırrıdır. Bu, kimlik doğrulama için de kullanılır.|
|jobId|Bu, 3. Adımda oluşturduğunuz Destan konnektörün iş kimliğidir. Bu, Microsoft bulutuna yüklenen Destan EHR denetim kayıtlarını Destansı bağlayıcısı ile ilişkilendirmek için kullanılır.|
|filePath|Bu, 2. Adımda oluşturduğunuz metin dosyasının (betikle aynı sistemde depolanan) dosya yoludur. Dosya yolunda boşluklardan kaçınmaya çalışma; aksi takdirde tek tırnak işareti kullanın.|
|||

Her parametre için gerçek değerleri kullanan Destansı bağlayıcı betiği söz dizimi örneği:

```powershell
.\EpicConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\epic_audit_records.txt'
```

Karşıya yükleme başarılı olursa, betik Başarılı **Upload** görüntüler.

> [!NOTE]
> Yürütme ilkeleri nedeniyle önceki komutu çalıştırmada sorun ediyorsanız, yürütme ilkelerini ayarlama [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) hakkında yol gösterici bilgi için bkz. Yürütme İlkeleri hakkında ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy).

## <a name="step-5-monitor-the-epic-connector"></a>5. Adım: Destansı bağlayıcıyı izleme

Destansı bağlayıcısı oluşturduktan ve EHR denetim kayıtlarınızı ittükten sonra, bağlayıcıyı 2013'te sın Microsoft 365 uyumluluk merkezi. Betiği düzenli aralıklarla otomatik olarak çalıştıracak şekilde zamanlarsanız, betiğin son çalıştırıı sonunda geçerli durumu da görüntüabilirsiniz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve Destansı bağlayıcıyı seçerek açılır sayfayı görüntüleyin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. Son **içeri aktarma'nın** **altında, Bağlayıcının** durum günlüğünü açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, betiğin her çalıştırısı ve metin dosyasındaki verileri Microsoft bulutuna yüklemesi ile ilgili bilgileri içerir.

    Destansı bağlayıcı günlük dosyası, karşıya yüklenen metin dosyasından sayı satırlarını görüntüler

    Bu `RecordsSaved` alan, karşıya yüklenen metin dosyasındaki satır sayısını gösterir. Örneğin, metin dosyasında dört satır varsa ve `RecordsSaved` betik metin dosyasındaki tüm satırları başarıyla karşıya yükledikten sonra alanların değeri 4 olur.

4. Adımda betiği çalıştırmadısanız, Son içeri aktarma altında betiği indirme bağlantısı **görüntülenir**. Betiği indirebilir ve ardından betiği çalıştırmak için adımları izleyin.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama

Destan EHR sisteminiz ile ilgili en son denetim kayıtlarının Insider risk yönetim çözümü gibi araçların kullanılabilir olduğundan emin olmak için betiği günlük olarak otomatik olarak çalıştıracak şekilde zamanlamanızı öneririz. Bu ayrıca, aynı metin dosyasındaki Destansı denetim kaydı verilerini benzer bir zamanlamada (aynı değil de) güncelleştirerek, çalışanlarının hasta kayıtlarına erişim etkinlikleriyle ilgili en son bilgileri içeren bir zamanlamada güncelleştirmenizi gerektirir. Burada amaç, En güncel denetim kayıtlarını karşıya yük böylelikle Destansı bağlayıcısı tarafından Insider risk yönetimi çözümünün kullanılabilir hale getirilene kadar yüklemektir. 

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda Başlat düğmesine Windows **ve** Görev Zamanlayıcı **yazın**.

2. Görev Zamanlayıcı **uygulamasını açmak** için tıklatın.

3. Eylemler bölümünde **Görev** **Oluştur'a tıklayın**.

4. Genel **sekmesinde** , zamanlanmış görev için açıklayıcı bir ad yazın; örneğin, **Destansı bağlayıcı betiği**. ayrıca, isteğe bağlı bir açıklama da  eklersiniz.

5. Güvenlik **seçenekleri'nin** altında şunları yapın:

    1. Betiği yalnızca bilgisayarda oturum açtığınızda mı, yoksa oturum açtığınızda mı çalıştırmadıysanız çalıştırıp çalıştırmayıp çalıştırmaycasınız.

    2. En yüksek **ayrıcalıklarla çalıştır onay kutusunun** seçili olduğundan emin olun.

6. Tetikleyiciler **sekmesini** seçin, **Yeni'ye** tıklayın ve sonra şunları yapın:

    1. Komut **Ayarlar**, Günlük **seçeneğini** belirtin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün, belirtilen zamanda çalıştırın.

    2. Gelişmiş **ayarlar'ın** altında Etkin **onay kutusunun** seçili olduğundan emin olun.

    3. **Tamam'a tıklayın**.

7. Eylemler sekmesini **seçin** , **Yeni'ye** tıklayın ve sonra aşağıdaki işlemleri yapın:

   ![Destansı bağlayıcı betiği için yeni bir zamanlanmış görev oluşturmak üzere eylem ayarları.](../media/EpicConnectorScheduleTask1.png)

    1. Eylem **açılan** listesinde Program başlat'ın **seçili olduğundan** emin olun.

    2. **Program/betik** kutusunda Gözat'a tıklayın ve aşağıdaki konuma gidin ve yolu şu kutuda görüntülenecek şekilde seçin: C:.0.exe.

    3. Bağımsız değişken **ekle (isteğe bağlı)** kutusuna, 4. Adımda çalıştırdınız betik komutunun aynısını yapıştırın. Örneğin, `.\EpicConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Epic\audit\records.txt"`

    4. Başlangıç **(isteğe bağlı) kutusuna** , 4. Adımda çalıştırdınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Destansı\denetim.

    5. Yeni **eylemin** ayarlarını kaydetmek için Tamam'a tıklayın.

8. Zamanlanmış **görevi kaydetmek** için Görev Oluştur **penceresinde** Tamam'a tıklayın. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilirsiniz.

   Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.

   ![Sağlık bağlayıcısı betiği için yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.](../media/EpicConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştır zamanı ve çalıştırmanın zamanlandığı bir sonraki zaman görüntülenir. Görevi düzenlemek için çift tıkebilirsiniz.

   Ayrıca, betiğin uyumluluk merkezinde ilgili Efsanevi bağlayıcının uç sayfa üzerinde en son ne zaman çalıştığını da doğruleyebilirsiniz.
