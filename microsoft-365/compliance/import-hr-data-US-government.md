---
title: İk verilerini ABD Kamu bulutuna içeri aktaracak bir bağlayıcı ayarlama
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
ROBOTS: NOINDEX, NOFOLLOW
description: ABD Kamu bulutu yöneticileri, kendi kuruluşlarının insan kaynakları (İk) sisteminden çalışan verilerini kendi insan kaynakları sisteminden içeri aktaracak bir veri bağlayıcısı Microsoft 365. Bu sayede, insider risk yönetimi ilkelerde İk verilerini kullanarak, belirli kullanıcıların kurum açısından iç tehditlere neden olan etkinliklerini algılayabilirsiniz.
ms.openlocfilehash: c342499c2ea18f4d6ad2f737db3d1dc32bb9fb3f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330517"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>ABD Kamu'da İk verilerini içeri aktaracak bir bağlayıcı ayarlama

İnsan kaynakları (İK) verilerini ABD Microsoft 365 uyumluluk merkezi'ne içeri aktarmayı ayarlamak için, çalışma sayfalarında bir veri bağlayıcısı kurabilirsiniz. İk ile ilgili veriler, çalışanın personele gönderilen tarih ve çalışanın son tarihini içerir. Bu İk verileri daha sonra, Microsoft bilgi koruması kötü amaçlı etkinliklerden veya organizasyon içi veri hırsızlığından korunmasına yardımcı olmak için [Insider risk](insider-risk-management.md) yönetimi çözümü gibi farklı çözümler tarafından kullanılabilir. İk bağlayıcısı ayarlama, Azure Active Directory'da bağlayıcıyla kimlik doğrulaması için kullanılan bir uygulama oluşturmak, İk verilerinizi içeren CSV eşleme dosyalarını oluşturmak, uyumluluk merkezinde veri bağlayıcısı oluşturmak ve ardından CSV dosyasındaki İk verilerini Microsoft bulutuna alan bir betik çalıştırmadan oluşur. Daha sonra veri bağlayıcısı, Insider risk yönetim aracı tarafından ABD Kamu Kuruluşu'Microsoft 365 alınan İk verilerine erişmek için kullanılır.

## <a name="before-you-begin"></a>Başlamadan önce

- Adım 3'te İk bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Data Connector Yönetici rolü şu anda US Government GCC High ve DoD ortamlarında desteklenmiyor. Bu nedenle, GCC High ve DoD ortamlarında İk bağlayıcısını oluşturan kullanıcıya, çalışma alanı içinde Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Verilerinizin kurum İk sisteminden (düzenli olarak) nasıl alın ya da dışarı aktarın, sonra da 2. Adımda açıklanan CSV dosyasına nasıl ek gerekmektedir. 4. Adımda çalıştırdınız betik, CSV dosyasındaki İk verilerini Microsoft buluta yükler.

- Adım 4'te çalıştırdınız örnek betik İk verilerini Microsoft bulutuna yükler ve böylelikle insider risk yönetimi çözümü gibi diğer Microsoft araçları tarafından kullanılabilir. Bu örnek betik, hiçbir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'da (Azure AD) yeni uygulama oluşturmak ve kaydetmektir. Uygulama 3. Adımda oluştursanız da İk bağlayıcısını ifade edin. Bu uygulamayı oluşturmak, Azure AD'nin çalışan ve organizasyona erişmeye çalışan İk bağlayıcısı kimliğini doğrulamasını sağlayacaktır. Bu uygulama, 4. Adımda çalıştırarak İk verilerinizi Microsoft bulutuna yüklemek için betiğin kimliğini doğrulamak için de kullanılır. Bu Azure AD uygulamasını oluşturma işlemi sırasında, aşağıdaki bilgileri kaydetmeyi deneyin. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (uygulama kimliği *veya istemci kimliği olarak da* *adlandırılan*)

- Azure AD uygulama sırrı (istemci sırrı olarak *da adlandırılan*)

- Kiracı Kimliği (dizin kimliği olarak *da adlandırılan*)

Azure AD'de uygulama oluşturmayla ilgili adım adım yönergeler için bkz[.](/azure/active-directory/develop/quickstart-register-app) Uygulamayı şu Microsoft kimlik platformu.

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>2. Adım: İk verilerinizle bir CSV dosyası hazırlama

Sonraki adım, kuruluştan ayrıldıklarıyla ilgili bilgilerin bulunduğu bir CSV dosyası oluşturmaktır. Başlamadan Önce bölümünde de açıklanmıştır; bu CSV dosyasını, kurumnizin İk sisteminden nasıl oluştur belirleyebilirsiniz. Aşağıdaki örnekte, gerekli üç parametreyi (sütunlar) içeren tamamlanmış bir CSV dosyası (Not Defteri'ne açılır) göstermektedir. CSV dosyasını aynı dosya üzerinde düzenlemek çok daha Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

CSV dosyasının ilk satırı veya üst bilgi satırı gerekli sütun adlarını listeler. Her sütun başlığında kullanılan ad size göredir (önceki örnektekiler önerilerdir). Bununla birlikte, 3. Adımda İk bağlayıcısını oluşturmak için CSV  dosyasında aynı sütun adlarının belirtilmelidir. Sütun adlarında boşluk yok.

Aşağıdaki tabloda, CSV dosyasındaki her sütun açıklanır:

| Sütun adı | Açıklama |
|:-----|:-----|
| **EmailAddress** <br/> |Sonlandırılan çalışanın e-posta adresini belirtir.|
| **FesihDalığı** <br/> |Kişinin, kuruluşta görevin resmi olarak sonlandırılma tarihini belirtir. Örneğin, bu, çalışanın kuruluşdan ayrılma bildirimini verdiği tarih olabilir. Bu tarih, kişinin son iş günü olan tarihten farklı olabilir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Sonlandırılan çalışanın çalışması için son günü belirtir. Aşağıdaki tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Gerekli İk verileriyle CSV dosyasını oluşturduktaktan sonra, dosyayı 4. Adımda çalıştıracak olan betikle aynı sistemde depolayın. CSV dosyasının her zaman en güncel bilgileri içerdiği için bir güncelleştirme stratejisi uygulamanız gerekir. Bu sayede betiği çalıştıracak en güncel çalışan sonlandırma verileri Microsoft buluta yük olur.

## <a name="step-3-create-the-hr-connector"></a>3. Adım: İk bağlayıcısını oluşturma

Sonraki adım, çalışma haftası içinde bir İk bağlayıcısı Microsoft 365 uyumluluk merkezi. 4. Adımda betiği çalıştırdıktan sonra, oluşturanız İk bağlayıcısı CSV dosyasından Microsoft 365 bilgi sağlar. Bu adımda, bağlayıcıyı  oluşturmadan önce oluşturulan iş kimliğini kopyalayıp kopyalamaya dikkat edin. Betiği çalıştıracakken iş kimliğini kullanıcaz.

1. Bağlayıcılar sayfasına Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**bağlayıcıları sayfasını** seçin</a>.

2. **İk'nın altındaki Veri bağlayıcıları** sayfasında **Görünüm'e** **tıklayın**.

3. İk sayfasında **Bağlayıcı** **ekle'ye tıklayın**.

4. Kimlik doğrulama **kimlik bilgileri sayfasında** , şunları yapın ve ardından Sonraki'ye **tıklayın**:

   1. 1. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

   1. İk bağlayıcısı için bir ad yazın.

5. Dosya **eşleme sayfasında** , uygun kutuların her biri için 2. Adımda oluşturduğunuz CSV dosyasındaki üç sütun başlığının (parametreler olarak da *adlandırılan) adlarını* yazın. Adlar büyük/harfe duyarlı değildir. Daha önce de belirtildiği gibi, bu kutulara yazacak adların CSV dosyanız içinde yer alan parametre adlarla eşleşmesi gerekir. Örneğin, aşağıdaki ekran görüntüsü 2. Adımda gösterilen örnek CSV dosyasındaki örnekteki parametre adlarını gösterir.

   ![Sütun başlığı adları CSV dosyasındaki adlara eşler.](../media/HRConnectorWizard3.png)

6. Gözden Geçir **sayfasında** ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

   Bağlayıcının oluşturulmuş olduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfada, İk verilerinizi karşıya yüklemek üzere örnek betiği çalıştırmak üzere bir sonraki adımı tamamlamanız gereken iki önemli şey vardır.

   ![İş kimliği içeren sayfayı gözden geçirme ve örnek betik için github bağlantısı.](../media/HRConnector_Confirmation.png)

   1. **İş Kimliği.** Bir sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacak. Bu sayfadan veya bağlayıcı uçarak çıkış sayfasından kopyaleyebilirsiniz.
   
   1. **Örnek betik bağlantısı.** Örnek **betikle** erişmek için GitHub sitesine gitmek için buraya bağlantısına tıklayın (bağlantı yeni bir pencere açar). 4. Adımda betiği kopyalayıp açabilirsiniz. Alternatif olarak, 4. Adımda yeniden erişmek için hedefin yer işaretini yer işaretine yer işareti atabilirsiniz veya URL'yi kopyalayıp kopyalayabilirsiniz. Bu bağlantı bağlayıcı uç noktada da kullanılabilir.

7. **Bitti'ye tıklayın**.

   Yeni bağlayıcı, Bağlayıcılar sekmesindeki **listede** görüntülenir. 

8. Özellikleri ve bağlayıcıyla ilgili diğer bilgileri içeren çıkış sayfasını görüntülemek için az önce oluşturduğunuz İk bağlayıcısını tıklatın.

   ![Yeni İk bağlayıcısı için uç uçarak çıkış sayfası.](../media/HRConnectorWizard7.png)

   Henüz bunu yaptısanız, Azure Uygulama Kimliği ve Bağlayıcı iş **kimliği değerlerini** **kopyalayın**. Bir sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacak. Betiği, çıkış sayfasından da indirebilirsiniz (veya bir sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

   Ayrıca, **Düzenle'ye** tıklar ve Dosya eşleme sayfasında tanımlandığı gibi Azure Uygulama Kimliği veya sütun başlığı **adlarını da değiştirebilirsiniz** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>4. Adım: İk verilerinizi karşıya yüklemek için örnek betiği çalıştırma

İk bağlayıcısını ayarlamanın son adımı, İk verilerini CSV dosyasında (2. Adımda oluşturduğunuz) Microsoft buluta yükecek örnek bir betik çalıştırmaktır. Betik, verileri özel olarak İk bağlayıcısı üzerinden karşıya yükler. Betiği çalıştırdikten sonra 3. Adımda oluşturduğunuz İk bağlayıcısı, İk verilerini Microsoft 365 kuruluşa aktararak Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilirsiniz. Betiği çalıştırdikten sonra, en güncel çalışan sonlandırma verileri Microsoft bulutuna yüklenmek için görevi günlük olarak otomatik olarak çalıştıracak şekilde zamanlamayı göz önünde bulundurabilirsiniz. Bkz [. Betiği otomatik olarak çalıştıracak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

1. Siteye örnek betikle erişmek için önceki adımda açık GitHub pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyalanmış URL'yi kullanın.

2. Betiği **metin** görünümünde görüntülemek için Ham düğmesine tıklayın.

3. Örnek betikte yer alan tüm satırları kopyalayın ve sonra bunları bir metin dosyasına kaydedin.

4. Gerekiyorsa, kurum için örnek betiği değiştirin.

5. Örneğin, bir dosya Windows PowerShell kullanarak metin dosyasını bir betik dosyası `.ps1`olarak kaydedin`HRConnector.ps1`.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydeden dizine gidin.

7. CSV dosyasındaki İk verilerini Microsoft bulutuna yüklemek için aşağıdaki komutu çalıştırın; örneğin:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   Aşağıdaki tabloda, bu betikle birlikte  kullanmak üzere parametreler ve bunların gerekli değerleri açık almaktadır. Önceki adımlarda elde edilen bilgiler, bu parametrelerin değerlerde kullanılır.

   | Parametre | Açıklama |
   |:-----|:-----|:-----|
   |`tenantId`|1. Adımda Microsoft 365 kuruluş kimliği. Ayrıca, Azure AD yönetim merkezinde Genel Bakış blade'inde **bulunan** kiracı kimliğine de bakabilirsiniz. Bu, kurumlarınızı tanımlamak için kullanılır.|
   |`appId` |1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama kimliği. Betik, kimlik doğrulaması için Azure AD tarafından Microsoft 365 kullanılır. |
   |`appSecret`|1. Adımda Azure AD'de oluşturduğunuz uygulamanın Azure AD uygulama sırrı. Bu, kimlik doğrulama için de kullanılır.|
   |`jobId`|3. Adımda oluşturduğunuz İk bağlayıcısı için iş kimliği. Bu, Microsoft bulutuna yüklenen İk verilerini İk bağlayıcısı ile ilişkilendirmek için kullanılır.|
   |`csvFilePath`|2. Adımda oluşturduğunuz CSV dosyasının (betikle aynı sistemde depolanan) dosya yolu. Dosya yolunda boşluklardan kaçınmaya çalışma; aksi takdirde tek tırnak işareti kullanın.|
   |||
   
   Her parametre için gerçek değerlerin kullanılarak İk bağlayıcısı betiği söz dizimi örneği:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
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

4. Adımda betiği çalıştırmadısanız, Son içeri aktarma altında betiği indirme bağlantısı **görüntülenir**. Betiği indirebilir ve çalıştırmak için 4. Adım'daki adımları takip edin.

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

   1. Bağımsız değişken **ekle (isteğe bağlı)** kutusuna, 4. Adımda çalıştırdınız betik komutunun aynısını yapıştırın. Örneğin, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Başlangıç **(isteğe bağlı) kutusuna** , 4. Adımda çalıştırdınız betiğin klasör konumunu yapıştırın. Örneğin, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Yeni **eylemin** ayarlarını kaydetmek için Tamam'a tıklayın.

8. Zamanlanmış **görevi kaydetmek** için Görev Oluştur **penceresinde** Tamam'a tıklayın. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilirsiniz.

   Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.

   ![Yeni görev, Görev Zamanlayıcı Kitaplığı'nın içinde görüntülenir.](../media/HRConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştır zamanı ve çalıştırmanın zamanlandığı bir sonraki zaman görüntülenir. Görevi düzenlemek için çift tıkebilirsiniz.

   Ayrıca, betiğin uyumluluk merkezinde ilgili İk bağlayıcısını uç öğe sayfasında en son ne zaman çalıştır çalıştığını da doğruleyebilirsiniz.