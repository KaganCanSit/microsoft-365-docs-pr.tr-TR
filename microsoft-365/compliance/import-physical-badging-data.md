---
title: Fiziksel badging verilerini içeri aktaracak şekilde bağlayıcı ayarlama
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
description: Yöneticiler, teknik destek almak için kuruluşlarının fiziksel destek sisteminden verileri içeri aktaracak bir veri bağlayıcısı Microsoft 365. Bu sayede, bu verileri Insider risk yönetimi ilkelerde kullanarak, belirli kullanıcılar tarafından organizasyon için olası bir iç tehdit olduğunu belirten belirli kullanıcılar tarafından fiziksel binalara erişimi algılamanıza yardımcı olur.
ms.openlocfilehash: e70217fa98e283883ab70bbe924d6f01f27613b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312229"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Fiziksel belgeleme verilerini içeri aktaracak şekilde bağlayıcı ayarlama (önizleme)

Microsoft 365 uyumluluk merkezi'ta, çalışanın ham fiziksel erişim olayları veya kuruma destek sistemi tarafından oluşturulan fiziksel erişim alarmları gibi fiziksel badging verilerini içeri aktaracak bir veri bağlayıcısı kurabilirsiniz. Fiziksel erişim noktalarına örnek olarak bina girişleri ya da sunucu odası veya veri merkezine girişler örnek olarak gösterilir. Fiziksel badging verileri, kuruluşta kötü amaçlı etkinliklerden veya Microsoft 365 hırsızlıklarından korunmanıza yardımcı olmak için Microsoft 365 [Insider risk](insider-risk-management.md) yönetimi çözümü tarafından kullanılabilir.

Fiziksel bir bağlantı bağlayıcısı ayarlama, aşağıdaki görevlerden oluşur:

- Fiziksel balama verileri Azure Active Directory JSON yüklerini kabul eden bir API uç noktasına erişmek için Azure Active Directory'de (Azure AD) uygulama oluşturma.

- JSON yükünü, fiziksel badging veri bağlayıcısı tarafından tanımlanan bir şemayla oluşturma.

- Köprüde fiziksel bir badging veri bağlayıcısı Microsoft 365 uyumluluk merkezi.

- Fiziksel badging verilerini API uç noktasına itmek için bir betik çalıştırma.

- İsteğe bağlı olarak, betiğin şu anda fiziksel ba badging verilerini içeri aktarması için otomatik olarak çalıştırmayı zamanlama.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- 3. Adımda fiziksel badging bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Data Connector Yönetici rolü şu anda US Government GCC High ve DoD ortamlarında desteklenmiyor. Bu nedenle, GCC High ve DoD ortamlarında İk bağlayıcısını oluşturan kullanıcıya, çalışma alanı içinde Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Verilerinizin, kurumnizin fiziksel belgeleme sisteminden (günlük olarak) nasıl alın ya da dışarı aktarın, sonra da 2. Adımda açıklanan bir JSON dosyası oluşturmanız gerekir. 4. Adımda çalıştırdınız betik, JSON dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdınız örnek betik, JSON dosyasındaki fiziksel koruma verilerini bağlayıcı API'sinde dışarı doğru iletir; böylelikle insider risk yönetimi çözümü tarafından kullanılabilir. Bu örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

- Bu bağlayıcı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'da (Azure AD) yeni uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturmanız gereken fiziksel bağlantı bağlayıcısı ile karşılık gelecektir. Bu uygulamanın oluşturulması, Azure AD'nin fiziksel depolama verileri içeren JSON yük itme isteğinin kimliğini doğrulamasını sağlar. Bu Azure AD uygulamasını oluşturma işlemi sırasında, aşağıdaki bilgileri kaydetmeyi deneyin. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (uygulama kimliği *veya istemci kimliği olarak da* *adlandırılan*)

- Azure AD uygulama sırrı (istemci sırrı olarak *da adlandırılan*)

- Kiracı Kimliği (dizin kimliği olarak *da adlandırılan*)

Azure AD'de uygulama oluşturmayla ilgili adım adım yönergeler için bkz[.](/azure/active-directory/develop/quickstart-register-app) Uygulamayı şu Microsoft kimlik platformu.

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>2. Adım: Fiziksel bajman verileri olan bir JSON dosyası hazırlama

Sonraki adım, çalışanların fiziksel erişim verileri hakkında bilgi içeren bir JSON dosyası oluşturmaktır. Başlamadan önce bölümde de anlatıldı gibi, bu JSON dosyasının, kuruma uygun fiziksel bajman sisteminden nasıl oluşturulacı olduğunu belirlemeniz gerekir.

JSON dosyası, bağlayıcının gereken şema tanımına uygun olmalıdır. JSON dosyası için gereken şema özelliklerinin açıklamaları:

|Özellik|Açıklama|Veri türü|
|---|---|---|
|UserId|Bir çalışan, sistemler arasında birden çok dijital kimlikli olabilir. Girişte, Azure AD Kimliği'nin kaynak sistem tarafından zaten çözümlenmiş olması gerekir.|UPN veya e-posta adresi|
|AssetId|Fiziksel varlık veya fiziksel erişim noktasının başvuru kimliği.|Alfasayısal dize|
|AssetName|Fiziksel varlığın veya fiziksel erişim noktasının kolay adı.|Alfasayısal dize|
|EventTime|Erişim zaman damgasıdır.|TARIH ve saat, UTC biçiminde|
|AccessStatus|Veya değeri `Success``Failed`|Dize|
|||

Burada, gerekli şemaya uygun bir JSON dosyası örneği ve şöyledir:

```json
[
    {
        "UserId":"sarad@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T01:57:49",
        "AccessStatus":"Failed"
    },
    {
        "UserId":"pilarp@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T02:57:49",
        "AccessStatus":"Success"
    }
]
```

Ayrıca, 3. Adım'da fiziksel badging bağlayıcısı esnayı  sihirbazından JSON dosyası için aşağıdaki şema tanımını da indirebilirsiniz.

```text
{
   "title" : "Physical Badging Signals",
   "description" : "Access signals from physical badging systems",
   "DataType" : {
      "description" : "Identify what is the data type for input signal",
      "type" : "string",
   },
   "type" : "object",
   "properties": {
      "UserId" : {
         "description" : "Unique identifier AAD Id resolved by the source system",
         "type" : "string",
      },
      "AssetId": {
         "description" : "Unique ID of the physical asset/access point",
         "type" : "string",
      },
      "AssetName": {
         "description" : "friendly name of the physical asset/access point",
         "type" : "string",
      },
      "EventTime" : {
         "description" : "timestamp of access",
         "type" : "string",
      },
      "AccessStatus" : {
         "description" : "what was the status of access attempt - Success/Failed",
         "type" : "string",
      },
   }
   "required" : ["UserId", "AssetId", "EventTime" "AccessStatus"]
}
```

## <a name="step-3-create-the-physical-badging-connector"></a>3. Adım: Fiziksel bağlantı bağlayıcısı oluşturma

Sonraki adım, bağlantı bağlantılarında fiziksel bir badging bağlayıcısı Microsoft 365 uyumluluk merkezi. 4. Adımda betiği çalıştırdikten sonra, 3. Adımda oluşturduğunuz JSON dosyası işlenir ve 1. Adımda yapılandırılan API uç noktasına gönderilir. Bu adımda, bağlayıcıyı  oluşturmak için oluşturulan JobId'i kopyalayıp kopyalamayı dikkat edin. Betiği çalıştıracakken JobId'i kullanıcaz.

1. Veri bağlayıcıları'Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**seçin**</a>.

2. Veri **bağlayıcıları sayfasında,** Fiziksel **bağlantı'nın altında Görünüm'e** **tıklayın**.

3. Fiziksel bağlantı **sayfasında Bağlayıcı ekle'ye** **tıklayın**.

4. Kimlik doğrulama **kimlik bilgileri sayfasında** , şunları yapın ve ardından Sonraki'ye **tıklayın**:

   1. 1. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

   2. JSON dosyasını oluşturmak için başvurun örnek şemasını indirin.

   3. Fiziksel bağlantı bağlayıcısı için benzersiz bir ad yazın.

5. Gözden Geçir **sayfasında** ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

6. Bağlayıcının oluşturulmuş olduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfa iş kimliğini de içerir. İş kimliğini bu sayfadan veya bağlayıcının uç noktadan kopyaleyebilirsiniz. Betiği çalıştırarak bu iş kimliğine ihtiyacınız vardır.

   Durum sayfası betiğin bağlantısını da içerir. JSON dosyasının API uç noktasına nasıl gönderile ilgili olduğunu anlamak için bu betike bakın.

7. **Bitti'ye tıklayın**.

   Yeni bağlayıcı, Bağlayıcılar sekmesindeki **listede** görüntülenir.

8. Özellikleri ve bağlayıcı hakkında diğer bilgileri içeren uçarak çıkış sayfasını görüntülemek için, az önce oluşturduğunuz fiziksel bağlantı bağlayıcısı bağlayıcıya tıklayın.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>4. Adım: Fiziksel badging verileri içeren JSON dosyanızı POST için betiği çalıştırın

Fiziksel bir badging bağlayıcısı ayarlamanın bir sonraki adımı, JSON dosyasındaki (2. Adımda oluşturduğunuz) fiziksel badging verilerini 1. Adımda oluşturduğunuz API uç noktasına ileten bir betik çalıştırmaktır. Başvurunız için bir örnek betik sağlariz. JSON dosyasını API uç noktasına göndermeniz için bu betiği kullanabileceğiniz gibi kendi betiğinizi de oluşturabilirsiniz.

Betiği çalıştırdikten sonra, fiziksel badging verilerini içeren JSON dosyası, Microsoft 365 risk yönetimi çözümü tarafından erişililebilen Microsoft 365 kuruluşa itilir. Fiziksel bajman verilerini günlük olarak postamanizi öneririz. Bunu, fiziksel bajing sisteminden her gün JSON dosyasını oluşturma işlemini otomatik başlatarak ve ardından betiği verileri itmek için zamanlayarak, bunuabilirsiniz.

> [!NOTE]
> JSON dosyasında API tarafından işlenebilir kayıt sayısı üst sayısı 50.000 kayıttır.

1. Örnek [betiği GitHub için](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) bu siteyi ziyaret edin.

2. Betiği **metin** görünümünde görüntülemek için Ham düğmesine tıklayın

3. Örnek betikte yer alan tüm satırları kopyalayın ve sonra bunları bir metin dosyasına kaydedin.

4. Gerekiyorsa, kurum için örnek betiği değiştirin.

5. Metin dosyasını, Windows PowerShell dosya adı soneki kullanarak .ps1 dosyası olarak kaydedin; örneğin, PhysicalBadging.ps1.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydeden dizine gidin.

7. JSON dosyasındaki fiziksel koruma verilerini Microsoft buluta itmek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   Aşağıdaki tabloda, bu betikle birlikte  kullanmak üzere parametreler ve bunların gerekli değerleri açık almaktadır. Önceki adımlarda elde edilen bilgiler bu parametrelerin değerlerde kullanılır.

   |Parametre|Açıklama|
   |---|---|
   |tenantId|Bu, 1. Adımda Microsoft 365 kuruluş kimliğidir. Ayrıca, Azure AD yönetim merkezinde Genel **Bakış** blade'inde, organizasyon için kiracıki bir kiracıkimlik anahtarına da sahip oluruz. Bu, kurumlarınızı tanımlamak için kullanılır.|
   |appId|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Betik, kimlik doğrulaması için Azure AD tarafından Microsoft 365 kullanılır.|
   |appSecret|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama sırrıdır. Bu, kimlik doğrulama için de kullanılır.|
   |jobId|Bu, 3. Adımda oluşturduğunuz fiziksel bağlantı bağlayıcısı için İş Kimliğidir. Bu, Microsoft bulutuna gönderilirken fiziksel badging verilerini fiziksel bağlantı bağlayıcısı ile ilişkilendirmek için kullanılır.|
   |JsonFilePath|Bu, 2. Adımda oluşturduğunuz JSON dosyasının yerel bilgisayarın (betiği çalıştırmak için kullanmakta olduğunuz yol) dosya yoludur. Bu dosyanın 3. Adımda açıklanan örnek şemayı izlemesi gerekir.|
   |||

   Her parametre için gerçek değerler kullanan fiziksel badging bağlayıcı betiği söz dizimi örneği:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Karşıya yükleme başarılı olursa, betik Başarılı **Upload** görüntüler.

   Birden çok JSON dosyanız varsa, her dosya için betiği çalıştırmanız gerekir.

> [!NOTE]
> Ayrıca, fiziksel badging verilerini önceki betiği çalıştırma dışında yöntemlerle API uç noktasına da basabilirsiniz. Örneğin, verilerinizi API uç noktasına itmek için Postman'ı kullanmaya örnek olarak bu örneği kullanabilirsiniz.

## <a name="step-5-monitor-the-physical-badging-connector"></a>5. Adım: Fiziksel bağlantı bağlayıcılarını izleme

Fiziksel bajman bağlayıcısı oluşturduk ve fiziksel bajman verilerinizi ittirdikten sonra, bağlayıcıyı 24 saat içinde  görüntüip karşıya Microsoft 365 uyumluluk merkezi. Betiği düzenli aralıklarla otomatik olarak çalıştıracak şekilde zamanlarsanız, betiğin son çalıştırıı sonunda geçerli durumu da görüntüabilirsiniz.

1. Veri bağlayıcıları'Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**seçin**</a>.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır sayfayı görüntülemek için fiziksel bağlantı bağlayıcısı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

   ![Fiziksel bağlantı bağlayıcısı için durum uçarak çıkış sayfası.](..\media\PhysicalBadgingStatusFlyout.png)

3. Son **içeri aktarma'nın** **altında, Bağlayıcının** durum günlüğünü açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, betiğin her çalıştırısı ve JSON dosyasındaki verileri Microsoft bulutuna yüklemesi ile ilgili bilgileri içerir.

   ![Fiziksel badging bağlayıcı günlük dosyası, karşıya yüklenen JSON dosyasındaki nesnelerin sayısını görüntüler.](..\media\PhysicalBadgingConnectorLogFile.png)

   **RecordsSaved** alanı, karşıya yüklenen JSON dosyasındaki nesnelerin sayısını gösterir. Örneğin, JSON dosyasında dört nesne varsa, betik JSON dosyasındaki tüm nesneleri başarıyla karşıya yüklemişse **KayıtSaved** alanlarının değeri 4 olur.

4. Adımda betiği çalıştırmadısanız, Son içeri aktarma altında betiği indirme bağlantısı **görüntülenir**. Betiği indirebilir ve çalıştırmak için 4. Adım'daki adımları takip edin.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalıştıracak şekilde zamanlama

Insider risk yönetimi çözümü gibi araçların en son fiziksel belgeleme verilerini kurumdan almak için betiğin günde bir gibi yinelenen tekrarlı bir şekilde otomatik olarak çalıştırıılamalarını öneririz. Bu ayrıca, fiziksel belgeleme verilerini JSON dosyasına benzer bir zamanlamayla (aynı değil de) güncelleştirin, böylece organizasyondan ayrılmak isteyen çalışanlar hakkında en son bilgileri içerir. Amaç, fiziksel bajman bağlayıcısı tarafından Insider risk yönetimi çözümünün kullanılabilir hale getirilemesinde en güncel fiziksel badging verilerini karşıya yüklemektir.

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda Başlat düğmesine Windows **ve** Görev Zamanlayıcı **yazın**.

2. Görev Zamanlayıcı **uygulamasını açmak** için tıklatın.

3. Eylemler bölümünde **Görev** **Oluştur'a tıklayın**.

4. Genel **sekmesinde** , zamanlanmış görev için açıklayıcı bir ad yazın; örneğin, **fiziksel bağlantı bağlayıcısı Betik**. ayrıca, isteğe bağlı bir açıklama da  eklersiniz.

5. Güvenlik **seçenekleri'nin** altında şunları yapın:

   1. Betiği yalnızca bilgisayarda oturum açtığınızda mı, yoksa oturum açtığınızda mı çalıştırmadıysanız çalıştırıp çalıştırmayıp çalıştırmaycasınız.

   2. En yüksek **ayrıcalıklarla çalıştır onay kutusunun** seçili olduğundan emin olun.

6. Tetikleyiciler **sekmesini** seçin, **Yeni'ye** tıklayın ve sonra şunları yapın:

   1. Komut **Ayarlar**, Günlük **seçeneğini** belirtin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün, belirtilen zamanda çalıştırın.

   2. Gelişmiş **ayarlar'ın** altında Etkin **onay kutusunun** seçili olduğundan emin olun.

   3. **Tamam'a tıklayın**.

7. Eylemler sekmesini **seçin** , **Yeni'ye** tıklayın ve sonra aşağıdaki işlemleri yapın:

   ![Fiziksel bağlantı bağlayıcısı betiği için yeni zamanlanmış görev oluşturmak üzere eylem ayarları.](..\media\SchedulePhysicalBadgingScript1.png)

   1. Eylem **açılan** listesinde Program başlat'ın **seçili olduğundan** emin olun.

   2. **Program/betik** kutusunda Gözat'a tıklayın ve aşağıdaki konuma gidin ve yolu şu kutuda görüntülenecek şekilde seçin: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. Bağımsız değişken **ekle (isteğe bağlı)** kutusuna, 4. Adımda çalıştırdınız betik komutunun aynısını yapıştırın. Örneğin, .\PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. Başlangıç **(isteğe bağlı) kutusuna** , 4. Adımda çalıştırdınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Users\contosoadmin\Desktop\Scripts.

   5. Yeni **eylemin** ayarlarını kaydetmek için Tamam'a tıklayın.

8. Zamanlanmış **görevi kaydetmek** için Görev Oluştur **penceresinde** Tamam'a tıklayın. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilirsiniz.

   Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.

   ![Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.](..\media\SchedulePhysicalBadgingScript2.png)

Betiğin en son çalıştır zamanı ve çalıştırmanın zamanlandığı bir sonraki zaman görüntülenir. Görevi düzenlemek için çift tıkebilirsiniz.

Ayrıca, betiğin uyumluluk merkezinde ilgili fiziksel badging bağlayıcısı üzerinde uç sayfa üzerinde en son ne zaman çalıştığını da doğruleyebilirsiniz.
