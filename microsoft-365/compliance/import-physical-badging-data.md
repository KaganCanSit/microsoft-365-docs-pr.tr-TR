---
title: Fiziksel badging verilerini içeri aktarmak için bağlayıcı ayarlama
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
description: Yöneticiler, kuruluşlarının fiziksel badging sisteminden Microsoft 365 verileri içeri aktarmak için bir veri bağlayıcısı ayarlayabilir. Bu, bu verileri, kuruluşunuz için olası bir iç tehdit oluşturabilecek belirli kullanıcılar tarafından fiziksel binalarınıza erişimi algılamanıza yardımcı olmak için şirket içi risk yönetimi ilkelerinde kullanmanıza olanak tanır.
ms.openlocfilehash: 7b6161cfc8f712082303641f9da7345edf5e24df
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937949"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Fiziksel badging verilerini içeri aktarmak için bağlayıcı ayarlama (önizleme)

Çalışanın ham fiziksel erişim olayları veya kuruluşunuzun badging sistemi tarafından oluşturulan fiziksel erişim alarmları gibi fiziksel badging verilerini içeri aktarmak için Microsoft Purview uyumluluk portalında bir veri bağlayıcısı ayarlayabilirsiniz. Fiziksel erişim noktalarına örnek olarak bir bina veya sunucu odası ya da veri merkezine giriş verilebilir. Fiziksel badging verileri, kuruluşunuzun kuruluşunuzdaki kötü amaçlı etkinliklerden veya veri hırsızlığından korunmasına yardımcı olmak için Microsoft 365 [insider risk yönetimi çözümü](insider-risk-management.md) tarafından kullanılabilir.

Fiziksel bir badging bağlayıcısı ayarlamak aşağıdaki görevlerden oluşur:

- fiziksel badging verileri içeren bir JSON yükünü kabul eden bir API uç noktasına erişmek için Azure Active Directory 'de (Azure AD) bir uygulama oluşturma.

- Fiziksel badging veri bağlayıcısı tarafından tanımlanan bir şema ile JSON yükünü oluşturma.

- Uyumluluk portalında fiziksel bir badging veri bağlayıcısı oluşturma.

- Fiziksel badging verilerini API uç noktasına göndermek için bir betik çalıştırma.

- İsteğe bağlı olarak, şu anda fiziksel badging verilerini içeri aktarmak için betiği otomatik olarak çalışacak şekilde zamanlama.

## <a name="before-you-set-up-the-connector"></a>Bağlayıcıyı ayarlamadan önce

- 3. Adımda fiziksel badging bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

   > [!NOTE]
   > Veri Bağlayıcısı Yönetici rolü şu anda ABD Kamu GCC Yüksek ve DoD ortamlarında desteklenmemaktadır. Bu nedenle, GCC Yüksek ve DoD ortamlarında İk bağlayıcısını oluşturan kullanıcıya Exchange Online'da Posta Kutusu İçeri Aktarma İçeri Aktarma rolü atanmalıdır. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Exchange Online'deki Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilirsiniz. Daha fazla bilgi için "[Exchange Online rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) yönetme" makalesindeki Rol grupları oluşturma veya [Rol gruplarını değiştirme](/Exchange/permissions-exo/role-groups#modify-role-groups) bölümlerine bakın.

- Kuruluşunuzun fiziksel badging sisteminden (günlük olarak) verilerin nasıl alınacağını veya dışarı aktarıldığını belirlemeniz ve 2. Adım'da açıklanan bir JSON dosyası oluşturmanız gerekir. 4. Adımda çalıştırdığınız betik, JSON dosyasındaki verileri API uç noktasına iletir.

- 4. Adımda çalıştırdığınız örnek betik, fiziksel badging verilerini JSON dosyasından bağlayıcı API'sine göndererek iç risk yönetimi çözümü tarafından kullanılabilmesini sağlar. Bu örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

- Bu bağlayıcı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'de (Azure AD) yeni bir uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturduğunuz fiziksel badging bağlayıcısına karşılık gelir. Bu uygulamanın oluşturulması, Azure AD'nin fiziksel badging verileri içeren JSON yükü için anında iletme isteğinin kimliğini doğrulamasını sağlar. Bu Azure AD uygulamasını oluştururken aşağıdaki bilgileri kaydettiğinizden emin olun. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği ( *uygulama kimliği* veya *istemci kimliği* olarak da adlandırılır)

- Azure AD uygulama gizli dizisi ( *istemci gizli dizisi* olarak da adlandırılır)

- Kiracı Kimliği ( *dizin kimliği* olarak da adlandırılır)

Azure AD'de uygulama oluşturmaya yönelik adım adım yönergeler için bkz. [Uygulamayı Microsoft kimlik platformu kaydetme](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>2. Adım: Fiziksel badging verileriyle JSON dosyası hazırlama

Sonraki adım, çalışanların fiziksel erişim verileri hakkında bilgi içeren bir JSON dosyası oluşturmaktır. Başlamadan önce bölümünde açıklandığı gibi, bu JSON dosyasını kuruluşunuzun fiziksel badging sisteminden nasıl oluşturabileceğinizi belirlemeniz gerekir.

JSON dosyası bağlayıcının gerektirdiği şema tanımına uygun olmalıdır. JSON dosyası için gerekli şema özelliklerinin açıklamaları şunlardır:

|Özellik|Açıklama|Veri türü|
|---|---|---|
|Userıd|Bir çalışanın sistemlerde birden çok dijital kimliği olabilir. Girişin Azure AD kimliğinin kaynak sistem tarafından zaten çözümlenmiş olması gerekir.|UPN veya e-posta adresi|
|AssetId|Fiziksel varlığın veya fiziksel erişim noktasının başvuru kimliği.|Alfasayısal dize|
|AssetName|Fiziksel varlığın veya fiziksel erişim noktasının kolay adı.|Alfasayısal dize|
|EventTime|Erişimin zaman damgası.|UTC biçiminde tarih ve saat|
|AccessStatus|veya değeri `Success``Failed`|Dize|
|||

Gerekli şemaya uyan bir JSON dosyası örneği aşağıda verilmiştir:

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

3. Adımda fiziksel badging bağlayıcısını oluştururken sihirbazdan JSON dosyası için aşağıdaki şema tanımını da indirebilirsiniz.

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

## <a name="step-3-create-the-physical-badging-connector"></a>3. Adım: Fiziksel badging bağlayıcısını oluşturma

Sonraki adım, uyumluluk portalında fiziksel bir badging bağlayıcısı oluşturmaktır. Betiği 4. Adımda çalıştırdıktan sonra, 3. Adımda oluşturduğunuz JSON dosyası işlenir ve 1. Adımda yapılandırdığınız API uç noktasına iletilir. Bu adımda, bağlayıcıyı oluştururken oluşturulan JobId değerini kopyaladığınızdan emin olun. Betiği çalıştırdığınızda JobId değerini kullanacaksınız.

1. Uyumluluk portalına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Veri bağlayıcıları'nı**</a> seçin.

2. **Veri bağlayıcıları** sayfasında **, Fiziksel badging'in** altında **Görünüm'e** tıklayın.

3. **Fiziksel badging** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Kimlik doğrulama kimlik bilgileri** sayfasında aşağıdakileri yapın ve **İleri'ye** tıklayın:

   1. 1. Adımda oluşturduğunuz Azure uygulaması için Azure AD uygulama kimliğini yazın veya yapıştırın.

   2. JSON dosyasını oluşturmak için başvurunuzun örnek şemasını indirin.

   3. Fiziksel badging bağlayıcısı için benzersiz bir ad yazın.

5. **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

6. Bağlayıcının oluşturulduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfa iş kimliğini de içerir. İş kimliğini bu sayfadan veya bağlayıcının açılır sayfasından kopyalayabilirsiniz. Betiği çalıştırırken bu iş kimliğine ihtiyacınız vardır.

   Durum sayfası betiğin bağlantısını da içerir. JSON dosyasını API uç noktasına göndermeyi anlamak için bu betike bakın.

7. **Bitti'ye** tıklayın.

   Yeni bağlayıcı **Bağlayıcılar** sekmesindeki listede görüntülenir.

8. Bağlayıcının özelliklerini ve diğer bilgilerini içeren açılır sayfayı görüntülemek için yeni oluşturduğunuz fiziksel badging bağlayıcısına tıklayın.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>4. Adım: Fiziksel badging verileri içeren JSON dosyanızı POST yapmak için betiği çalıştırın

Fiziksel bir badging bağlayıcısı ayarlamanın sonraki adımı, JSON dosyasındaki (2. Adımda oluşturduğunuz) fiziksel badging verilerini 1. Adımda oluşturduğunuz API uç noktasına gönderecek bir betik çalıştırmaktır. Başvurunuz için örnek bir betik sağlıyoruz ve JSON dosyasını API uç noktasına göndermek için bu betiği kullanmayı veya kendi betiğinizi oluşturmayı seçebilirsiniz.

Betiği çalıştırdıktan sonra, fiziksel badging verilerini içeren JSON dosyası Microsoft 365 kuruluşunuza gönderilerek şirket içi risk yönetimi çözümü tarafından erişilebilir. Fiziksel badging verilerini günlük olarak göndermenizi öneririz. Bunu yapmak için, fiziksel badging sisteminizden her gün JSON dosyasını oluşturma işlemini otomatikleştirebilir ve ardından verileri göndermek için betiği zamanlayabilirsiniz.

> [!NOTE]
> API tarafından işlenebilen JSON dosyasındaki kayıt sayısı üst sınırı 50.000 kayıttır.

1. Örnek betike erişmek için [bu GitHub sitesine](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) gidin.

2. Betiği metin görünümünde görüntülemek için **Ham** düğmesine tıklayın

3. Örnek betikteki tüm satırları kopyalayın ve bir metin dosyasına kaydedin.

4. Gerekirse kuruluşunuzun örnek betiğini değiştirin.

5. .ps1 dosya adı soneki kullanarak metin dosyasını Windows PowerShell betik dosyası olarak kaydedin; örneğin, PhysicalBadging.ps1.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydettiğiniz dizine gidin.

7. JSON dosyasındaki fiziksel badging verilerini Microsoft buluta göndermek için aşağıdaki komutu çalıştırın; örneğin:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   Aşağıdaki tabloda, bu betikle kullanılacak parametreler ve bunların gerekli değerleri açıklanmaktadır. Önceki adımlarda elde ettiğiniz bilgiler, bu parametrelerin değerlerinde kullanılır.

   |Parametre|Açıklama|
   |---|---|
   |tenantId|Bu, 1. Adımda aldığınız Microsoft 365 kuruluşunuzun kimliğidir. Ayrıca Azure AD yönetim merkezindeki **Genel Bakış** dikey penceresinde kuruluşunuzun tenantId değerini de alabilirsiniz. Bu, kuruluşunuzu tanımlamak için kullanılır.|
   |Appıd|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliğidir. Bu, betik Microsoft 365 kuruluşunuza erişmeye çalıştığında Azure AD tarafından kimlik doğrulaması için kullanılır.|
   |appSecret|Bu, 1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama gizli dizisidir. Bu, kimlik doğrulaması için de kullanılır.|
   |Jobıd|Bu, 3. Adımda oluşturduğunuz fiziksel badging bağlayıcısının İş Kimliğidir. Bu, Microsoft buluta gönderilen fiziksel badging verilerini fiziksel badging bağlayıcısıyla ilişkilendirmek için kullanılır.|
   |JsonFilePath|Bu, 2. Adımda oluşturduğunuz JSON dosyasının yerel bilgisayardaki dosya yoludur (betiği çalıştırmak için kullandığınız dosya). Bu dosya, 3. Adım'da açıklanan örnek şemayı izlemelidir.|
   |||

   Burada, her parametre için gerçek değerleri kullanan fiziksel badging bağlayıcı betiğinin söz dizimi örneği verilmiştir:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Karşıya yükleme başarılı olursa, betik **Upload Başarılı** iletisini görüntüler.

   Birden çok JSON dosyanız varsa, her dosya için betiği çalıştırmanız gerekir.

> [!NOTE]
> Fiziksel badging verilerini API uç noktasına önceki betiği çalıştırma dışında yöntemlerle göndermeyi de seçebilirsiniz. Örneğin, verilerinizi API uç noktasına göndermek için Postman'i kullanmaya yönelik bir örnek aşağıda verilmiştir.

## <a name="step-5-monitor-the-physical-badging-connector"></a>5. Adım: Fiziksel badging bağlayıcısını izleme

Fiziksel badging bağlayıcısını oluşturduktan ve fiziksel badging verilerinizi gönderdikten sonra bağlayıcıyı görüntüleyebilir ve uyumluluk portalında karşıya yükleme durumunu karşıya yükleyebilirsiniz. Betiği düzenli olarak otomatik olarak çalışacak şekilde zamanlarsanız, betiğin son çalıştırıldığından sonra geçerli durumu da görüntüleyebilirsiniz.

1. Uyumluluk portalına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Veri bağlayıcıları'nı**</a> seçin.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için fiziksel badging bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

   ![Fiziksel badging bağlayıcısı için durum açılır sayfası.](..\media\PhysicalBadgingStatusFlyout.png)

3. **Son içeri aktarma'nın** altında Günlüğü **indir** bağlantısına tıklayarak bağlayıcının durum günlüğünü açın (veya kaydedin). Bu günlük, betiğin çalıştırılıp JSON dosyasındaki verileri Microsoft buluta her yükleyişi hakkında bilgi içerir.

   ![Fiziksel badging bağlayıcısı günlük dosyası, JSON dosyasından karşıya yüklenen nesne sayısını görüntüler.](..\media\PhysicalBadgingConnectorLogFile.png)

   **RecordsSaved** alanı, JSON dosyasında karşıya yüklenen nesne sayısını gösterir. Örneğin, JSON dosyası dört nesne içeriyorsa, betik JSON dosyasındaki tüm nesneleri başarıyla karşıya yüklediyse **RecordsSaved** alanlarının değeri 4 olur.

4. Adımda betiği çalıştırmadıysanız, **Son içeri aktarma** altında betiği indirme bağlantısı görüntülenir. Betiği indirebilir ve ardından çalıştırmak için 4. Adım'daki adımları izleyebilirsiniz.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama

Kuruluşunuzdaki en son fiziksel badging verilerinin insider risk yönetimi çözümü gibi araçlar tarafından kullanılabildiğinden emin olmak için, betiği günde bir kez gibi yinelenen bir şekilde otomatik olarak çalışacak şekilde zamanlamanızı öneririz. Bu, fiziksel badging verilerini JSON dosyasına benzer bir zamanlamaya göre (aynı değilse) güncelleştirmenizi de gerektirir, böylece kuruluşunuzdan ayrılan çalışanlar hakkında en son bilgileri içerir. Amaç, fiziksel badging bağlayıcısının bunu insider risk yönetimi çözümü için kullanılabilir hale getirebilmesi için en güncel fiziksel badging verilerini karşıya yüklemektir.

Betiği her gün otomatik olarak çalıştırmak için Windows'da Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda, Windows **Başlat** düğmesine tıklayın ve görev **zamanlayıcı** yazın.

2. **Görev Zamanlayıcı** uygulamasına tıklayarak uygulamayı açın.

3. **Eylemler** bölümünde **Görev Oluştur'a** tıklayın.

4. **Genel** sekmesinde, zamanlanan görev için açıklayıcı bir ad yazın; örneğin, **fiziksel badging bağlayıcı betiği**. İsteğe bağlı bir açıklama da ekleyebilirsiniz.

5. **Güvenlik seçenekleri'nin** altında aşağıdakileri yapın:

   1. Betiğin yalnızca bilgisayarda oturum açtığınızda mı yoksa oturum açtığınızda mı çalıştırılmadığını mı belirleyebilirsiniz.

   2. **En yüksek ayrıcalıklarla çalıştır** onay kutusunun seçili olduğundan emin olun.

6. **Tetikleyiciler** sekmesini seçin, **Yeni'ye** tıklayın ve aşağıdaki işlemleri yapın:

   1. **Ayarlar** altında **Günlük** seçeneğini belirleyin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün belirtilen saatte çalıştırılır.

   2. **Gelişmiş ayarlar'ın** altında **Etkin** onay kutusunun seçili olduğundan emin olun.

   3. **Tamam'a** tıklayın.

7. **Eylemler** sekmesini seçin, **Yeni'ye** tıklayın ve ardından aşağıdaki işlemleri yapın:

   ![Fiziksel badging bağlayıcısı betiği için yeni bir zamanlanmış görev oluşturmak için eylem ayarları.](..\media\SchedulePhysicalBadgingScript1.png)

   1. **Eylem** açılan listesinde **Program başlat'ın** seçili olduğundan emin olun.

   2. **Program/betik** kutusunda **Gözat'a** tıklayın ve aşağıdaki konuma gidin ve yolu kutuda görüntülenecek şekilde seçin: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. **Bağımsız değişken ekle (isteğe bağlı)** kutusunda, 4. Adımda çalıştırdığınız betik komutunu yapıştırın. Örneğin, .\PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. Başlangıç yeri **(isteğe bağlı)** kutusuna, 4. Adımda çalıştırdığınız betiğin klasör konumunu yapıştırın. Örneğin, C:\Users\contosoadmin\Desktop\Scripts.

   5. Yeni eylemin ayarlarını kaydetmek için **Tamam'a** tıklayın.

8. **Görev Oluştur** penceresinde **Tamam'a** tıklayarak zamanlanmış görevi kaydedin. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilir.

   Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.

   ![Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.](..\media\SchedulePhysicalBadgingScript2.png)

Betiğin en son çalıştırıldığı ve bir sonraki çalıştırma zamanlaması görüntülenir. Görevi düzenlemek için çift tıklayabilirsiniz.

Ayrıca, uyumluluk merkezindeki ilgili fiziksel badging bağlayıcısının açılır sayfasında betiğin en son ne zaman çalıştığını da doğrulayabilirsiniz.
