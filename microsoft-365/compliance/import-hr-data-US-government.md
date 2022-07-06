---
title: İk verilerini ABD Kamu buluta aktarmak için bağlayıcı ayarlama
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
ms.custom: admindeeplinkCOMPLIANCE
ROBOTS: NOINDEX, NOFOLLOW
description: ABD Kamu bulutundaki yöneticiler, çalışan verilerini kuruluşlarının insan kaynakları (İk) sisteminden Microsoft 365'e aktarmak için bir veri bağlayıcısı ayarlayabilir. Bu, kuruluşunuz için iç tehdit oluşturabilecek belirli kullanıcıların etkinliklerini algılamanıza yardımcı olmak için şirket içi risk yönetimi ilkelerinde İk verilerini kullanmanıza olanak tanır.
ms.openlocfilehash: df9932af0588e95ea35fef24c8b9508676433d22
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634323"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>ABD Kamu'da İk verilerini içeri aktarmak için bağlayıcı ayarlama

İnsan kaynakları (İk) verilerini ABD Kamu kuruluşunuza aktarmak için Microsoft Purview uyumluluk portalı bir veri bağlayıcısı ayarlayabilirsiniz. İk ile ilgili veriler, bir çalışanın istifasını gönderdiği tarihi ve çalışanın son gününü içerir. Bu İk verileri daha sonra kuruluşunuzun kuruluşunuzdaki kötü amaçlı etkinliklerden veya veri hırsızlığından korunmasına yardımcı olmak için [insider risk yönetimi çözümü](insider-risk-management.md) gibi Microsoft bilgi koruma çözümleri tarafından kullanılabilir. İk bağlayıcısı ayarlamak, Azure Active Directory'de bağlayıcı tarafından kimlik doğrulaması için kullanılan bir uygulama oluşturmak, İk verilerinizi içeren bir CSV eşleme dosyaları oluşturmak, uyumluluk merkezinde bir veri bağlayıcısı oluşturmak ve ardından CSV dosyasındaki İk verilerini Microsoft buluta alan bir betik (zamanlanmış olarak) çalıştırmaktır. Ardından veri bağlayıcısı, Insider risk yönetimi aracı tarafından Microsoft 365 US Government kuruluşunuza aktarılan İk verilerine erişmek için kullanılır.

## <a name="before-you-begin"></a>Başlamadan önce

- 3. Adımda İk bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

   > [!NOTE]
   > Veri Bağlayıcısı Yönetici rolü şu anda US Government GCC High ve DoD ortamlarında desteklenmiyor. Bu nedenle, GCC High ve DoD ortamlarında İk bağlayıcısını oluşturan kullanıcıya Exchange Online'da Posta Kutusu İçeri Aktarma Dışarı Aktarma rolü atanmalıdır. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Exchange Online'deki Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilirsiniz. Daha fazla bilgi için "[Exchange Online rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) yönetme" makalesindeki Rol grupları oluşturma veya [Rol gruplarını değiştirme](/Exchange/permissions-exo/role-groups#modify-role-groups) bölümlerine bakın.

- Kuruluşunuzun İk sisteminden (düzenli olarak) verileri nasıl alabileceğinizi veya dışarı aktarabileceğinizi belirlemeniz ve 2. Adımda açıklanan CSV dosyasına eklemeniz gerekir. 4. Adımda çalıştırdığınız betik, CSV dosyasındaki İk verilerini Microsoft buluta yükler.

- 4. Adımda çalıştırdığınız örnek betik, İk verilerini Microsoft buluta yükleyerek insider risk yönetimi çözümü gibi diğer Microsoft araçları tarafından kullanılabilmesini sağlar. Bu örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'de (Azure AD) yeni bir uygulama oluşturmak ve kaydetmektir. Uygulama, 3. Adımda oluşturduğunuz İk bağlayıcısına karşılık gelir. Bu uygulamanın oluşturulması, Azure AD çalıştığında ve kuruluşunuza erişmeye çalıştığında İk bağlayıcısının kimliğini doğrulamasını sağlar. Bu uygulama, İk verilerinizi Microsoft buluta yüklemek için 4. Adımda çalıştırdığınız betiğin kimliğini doğrulamak için de kullanılır. Bu Azure AD uygulamasını oluştururken aşağıdaki bilgileri kaydettiğinizden emin olun. Bu değerler sonraki adımlarda kullanılacaktır.

- Azure AD uygulama kimliği (*uygulama kimliği* veya *istemci kimliği* olarak da adlandırılır)

- Azure AD uygulama gizli dizisi (*istemci gizli dizisi* olarak da adlandırılır)

- Kiracı Kimliği ( *dizin kimliği* olarak da adlandırılır)

Azure AD'da uygulama oluşturmaya yönelik adım adım yönergeler için bkz. [Uygulamayı Microsoft kimlik platformu kaydetme](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>2. Adım: İk verilerinizle CSV dosyası hazırlama

Sonraki adım, kuruluşunuzdan ayrılan çalışanlar hakkında bilgi içeren bir CSV dosyası oluşturmaktır. Başlamadan Önce bölümünde açıklandığı gibi, bu CSV dosyasını kuruluşunuzun İk sisteminden nasıl oluşturabileceğinizi belirlemeniz gerekir. Aşağıdaki örnekte, gerekli üç parametreyi (sütunlar) içeren tamamlanmış bir CSV dosyası (Not Defteri'nde açılır) gösterilmektedir. Csv dosyasını Microsoft Excel'de düzenlemek çok daha kolaydır.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

CSV dosyasının ilk satırı veya üst bilgi satırı, gerekli sütun adlarını listeler. Her sütun üst bilgisinde kullanılan ad size bağlı (önceki örnektekiler önerilerdir). Ancak, 3. Adımda İk bağlayıcısını oluştururken CSV dosyasında kullandığınız sütun adlarının aynılarının *belirtilmesi gerekir* . Sütun adlarında boşluk eklemeyin.

Aşağıdaki tabloda CSV dosyasındaki her sütun açıklanmaktadır:

| Sütun adı | Açıklama |
|:-----|:-----|
| **Emailaddress** <br/> |Sonlandırılan çalışanın e-posta adresini belirtir.|
| **SonlandırmaTarihi** <br/> |Kuruluşunuzda kişinin istihdamı resmi olarak sonlandırıldığı tarihi belirtir. Örneğin, bu, çalışanın kuruluşunuzdan ayrılma hakkında bildirimde bulunacağı tarih olabilir. Bu tarih, kişinin son iş günü tarihinden farklı olabilir. Şu tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Sonlandırılan çalışanın son çalışma gününü belirtir. Şu tarih biçimini kullanın: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`[ISO 8601 tarih ve saat biçimidir](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Gerekli İk verileriyle CSV dosyasını oluşturduktan sonra, 4. Adımda çalıştırdığınız betikle aynı sistemde depolayın. CSV dosyasının her zaman en güncel bilgileri içermesi için bir güncelleştirme stratejisi uyguladığından emin olun. Bunu yaptığınızda betiği çalıştırdığınız her şey, en güncel çalışan sonlandırma verilerinin Microsoft buluta yüklenmesini sağlar.

## <a name="step-3-create-the-hr-connector"></a>3. Adım: İk bağlayıcısını oluşturma

Sonraki adım, uyumluluk portalında bir İk bağlayıcısı oluşturmaktır. Betiği 4. Adımda çalıştırdıktan sonra, oluşturduğunuz İk bağlayıcısı CSV dosyasındaki İk verilerini Microsoft 365 kuruluşunuza alır. Bu adımda, bağlayıcıyı oluştururken oluşturulan iş kimliğini kopyaladığınızdan emin olun. Betiği çalıştırdığınızda iş kimliğini kullanacaksınız.

1. Uyumluluk portalına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Veri bağlayıcıları** sayfasını</a> seçin.

2. **İk** altındaki **Veri bağlayıcıları** sayfasında **Görünüm'e** tıklayın.

3. **İk** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Kimlik doğrulama kimlik bilgileri** sayfasında aşağıdakileri yapın ve **İleri'ye** tıklayın:

   1. 1. Adımda oluşturduğunuz Azure uygulamasının Azure AD uygulama kimliğini yazın veya yapıştırın.

   1. İk bağlayıcısı için bir ad yazın.

5. **Dosya eşleme** sayfasında, 2. Adımda oluşturduğunuz CSV dosyasındaki üç sütun başlığının (*parametreler* olarak da adlandırılır) adlarını uygun kutuların her birine yazın. Adlar büyük/küçük harfe duyarlı değildir. Daha önce açıklandığı gibi, bu kutulara yazdığınız adlar CSV dosyanızdaki parametre adlarla eşleşmelidir. Örneğin, aşağıdaki ekran görüntüsü 2. Adımda gösterilen örnek CSV dosyasındaki örnekteki parametre adlarını gösterir.

   ![Sütun başlığı adları CSV dosyasındaki adlarla eşleşiyor.](../media/HRConnectorWizard3.png)

6. **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

   Bağlayıcının oluşturulduğunu onaylayan bir durum sayfası görüntülenir. Bu sayfa, İk verilerinizi karşıya yüklemek için örnek betiği çalıştırmak için sonraki adımı tamamlamanız gereken iki önemli öğe içerir.

   ![örnek betik için iş kimliğini ve github bağlantısını içeren sayfayı gözden geçirin.](../media/HRConnector_Confirmation.png)

   1. **İş Kimliği.** Sonraki adımda betiği çalıştırmak için bu iş kimliğine ihtiyacınız olacaktır. Bu sayfadan veya bağlayıcı açılır sayfasından kopyalayabilirsiniz.
   
   1. **Örnek betiğin bağlantısı.** Örnek betike erişmek için GitHub sitesine gitmek için **buraya** tıklayın (bağlantı yeni bir pencere açar). 4. Adım'da betiği kopyalayabilmeniz için bu pencereyi açık tutun. Alternatif olarak, 4. Adımda yeniden erişebilmek için hedefe yer işareti ekleyebilir veya URL'yi kopyalayabilirsiniz. Bu bağlantı bağlayıcı açılır sayfasında da kullanılabilir.

7. **Bitti'ye** tıklayın.

   Yeni bağlayıcı **Bağlayıcılar** sekmesindeki listede görüntülenir. 

8. Yeni oluşturduğunuz İk bağlayıcısına tıklayarak bağlayıcıyla ilgili özellikleri ve diğer bilgileri içeren açılır sayfayı görüntüleyin.

   ![Yeni İk bağlayıcısı için açılır sayfa.](../media/HRConnectorWizard7.png)

   Henüz yapmadıysanız **, Azure Uygulaması Kimliği** ve **Bağlayıcı iş kimliği** değerlerini kopyalayabilirsiniz. Sonraki adımda betiği çalıştırmak için bunlara ihtiyacınız olacaktır. Betiği açılır sayfadan da indirebilirsiniz (veya sonraki adımda bağlantıyı kullanarak indirebilirsiniz.)

   **Dosya eşleme** sayfasında tanımladığınız Azure Uygulaması kimliğini veya sütun üst bilgisi adlarını değiştirmek için **Düzenle'ye** de tıklayabilirsiniz.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>4. Adım: İk verilerinizi karşıya yüklemek için örnek betiği çalıştırın

İk bağlayıcısını ayarlamanın son adımı, CSV dosyasındaki (2. Adımda oluşturduğunuz) İk verilerini Microsoft buluta yükleyecek örnek bir betik çalıştırmaktır. Özellikle betik, verileri İk bağlayıcısına yükler. Betiği çalıştırdıktan sonra, 3. Adımda oluşturduğunuz İk bağlayıcısı İk verilerini Microsoft 365 kuruluşunuza aktarır ve burada Insider risk yönetimi çözümü gibi diğer uyumluluk araçları tarafından erişilebilir. Betiği çalıştırdıktan sonra, en güncel çalışan sonlandırma verilerinin Microsoft buluta yüklenmesi için günlük olarak otomatik olarak çalıştırılacak bir görev zamanlamayı göz önünde bulundurun. Bkz. [Betiği otomatik olarak çalışacak şekilde zamanlama](#optional-step-6-schedule-the-script-to-run-automatically).

1. GitHub sitesine örnek betikle erişmek için önceki adımda açık bıraktığınız pencereye gidin. Alternatif olarak, yer işaretli siteyi açın veya kopyaladığınız URL'yi kullanın.

2. Betiği metin görünümünde görüntülemek için **Ham** düğmesine tıklayın.

3. Örnek betikteki tüm satırları kopyalayın ve bir metin dosyasına kaydedin.

4. Gerekirse kuruluşunuzun örnek betiğini değiştirin.

5. metin dosyasını Windows PowerShell betik dosyası olarak kaydetmek için ; örneğin, `HRConnector.ps1`bir dosya adı soneki `.ps1`kullanın.

6. Yerel bilgisayarınızda bir Komut İstemi açın ve betiği kaydettiğiniz dizine gidin.

7. CSV dosyasındaki İk verilerini Microsoft buluta yüklemek için aşağıdaki komutu çalıştırın; örneğin:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   Aşağıdaki tabloda, bu betikle kullanılacak parametreler ve bunların gerekli değerleri açıklanmaktadır. Önceki adımlarda elde ettiğiniz bilgiler bu parametrelerin değerlerinde kullanılır.

   | Parametre | Açıklama |
   |:-----|:-----|:-----|
   |`tenantId`|1. Adımda edindiğiniz Microsoft 365 kuruluşunuzun kimliği. Ayrıca, Azure AD yönetim merkezindeki **Genel Bakış** dikey penceresinde kuruluşunuzun kiracı kimliğini de alabilirsiniz. Bu, kuruluşunuzu tanımlamak için kullanılır.|
   |`appId` |1. Adımda Azure AD'da oluşturduğunuz uygulamanın Azure AD uygulama kimliği. Bu, Azure AD tarafından betik Microsoft 365 kuruluşunuza erişmeye çalıştığında kimlik doğrulaması için kullanılır. |
   |`appSecret`|1. Adımda Azure AD oluşturduğunuz uygulamanın Azure AD uygulama gizli dizisi. Bu, kimlik doğrulaması için de kullanılır.|
   |`jobId`|3. Adımda oluşturduğunuz İk bağlayıcısının iş kimliği. Bu, Microsoft buluta yüklenen İk verilerini İk bağlayıcısıyla ilişkilendirmek için kullanılır.|
   |`csvFilePath`|2. Adımda oluşturduğunuz CSV dosyasının (betikle aynı sistemde depolanan) dosya yolu. Dosya yolunda boşluklardan kaçınmaya çalışın; aksi takdirde tek tırnak işareti kullanın.|
   |||
   
   Aşağıda, her parametre için gerçek değerleri kullanan İk bağlayıcı betiğinin söz dizimi örneği verilmiştir:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Karşıya yükleme başarılı olursa, betik **Karşıya Yükleme Başarılı** iletisini görüntüler.

   > [!NOTE]
   > Yürütme ilkeleri nedeniyle önceki komutu çalıştırırken sorun yaşıyorsanız, yürütme ilkelerini ayarlama hakkında yönergeler için [Bkz. Yürütme İlkeleri Hakkında](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ve [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) .

## <a name="step-5-monitor-the-hr-connector"></a>5. Adım: İk bağlayıcısını izleme

İk bağlayıcısını oluşturduktan ve İk verilerinizi karşıya yüklemek için betiği çalıştırdıktan sonra bağlayıcıyı görüntüleyebilir ve uyumluluk portalında karşıya yükleme durumunu karşıya yükleyebilirsiniz. Betiği düzenli olarak otomatik olarak çalışacak şekilde zamanlarsanız, betiğin son çalıştırıldığından sonra geçerli durumu da görüntüleyebilirsiniz.

1. Uyumluluk portalına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Veri bağlayıcıları'nı**</a> seçin.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için İk bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

   ![Özellikler ve durum ile İk bağlayıcı açılır sayfası.](../media/HRConnectorFlyout1.png)

3. **İlerleme Durumu** altında, Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Günlüğü indir** bağlantısına tıklayın. Bu günlük, betiğin her çalıştırıldığında ve CSV dosyasındaki verileri Microsoft buluta yükleyişiyle ilgili bilgileri içerir. 

   ![İk bağlayıcısı günlük dosyası, karşıya yüklenen CSV dosyasındaki sayı satırlarını görüntüler.](../media/HRConnectorLogFile.png)

   alanı, `RecordsSaved` karşıya yüklenen CSV dosyasındaki satır sayısını gösterir. Örneğin, CSV dosyası dört satır içeriyorsa, betik CSV dosyasındaki `RecordsSaved` tüm satırları başarıyla karşıya yüklediyse alanların değeri 4 olur.

4. Adımda betiği çalıştırmadıysanız, **Son içeri aktarma** altında betiği indirme bağlantısı görüntülenir. Betiği indirebilir ve ardından çalıştırmak için 4. Adım'daki adımları izleyebilirsiniz.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(İsteğe bağlı) 6. Adım: Betiği otomatik olarak çalışacak şekilde zamanlama

Kuruluşunuzdaki en son İk verilerinin insider risk yönetimi çözümü gibi araçlar tarafından kullanılabildiğinden emin olmak için, betiği günde bir kez gibi yinelenen bir şekilde otomatik olarak çalışacak şekilde zamanlamanızı öneririz. Bu, kuruluşunuzdan ayrılan çalışanlar hakkında en son bilgileri içermesi için CSV dosyasındaki İk verilerini benzer (aynı değilse) bir zamanlamayla güncelleştirmenizi de gerektirir. Amaç, İk bağlayıcısının bunu insider risk yönetimi çözümüne sunabilmesi için en güncel İk verilerini karşıya yüklemektir.

Betiği her gün otomatik olarak çalıştırmak için Windows'ta Görev Zamanlayıcı uygulamasını kullanabilirsiniz.

1. Yerel bilgisayarınızda, Windows **Başlat** düğmesine tıklayın ve görev **zamanlayıcı** yazın.

2. **Görev Zamanlayıcı** uygulamasına tıklayarak uygulamayı açın.

3. **Eylemler** bölümünde **Görev Oluştur'a** tıklayın.

4. **Genel** sekmesinde, zamanlanan görev için açıklayıcı bir ad yazın; örneğin İk **BağlayıcıSı Betiği**. İsteğe bağlı bir açıklama da ekleyebilirsiniz.

5. **Güvenlik seçenekleri'nin** altında aşağıdakileri yapın:

   1. Betiğin yalnızca bilgisayarda oturum açtığınızda mı yoksa oturum açtığınızda mı çalıştırılmadığını mı belirleyebilirsiniz.
   
   1. **En yüksek ayrıcalıklarla çalıştır** onay kutusunun seçili olduğundan emin olun.

6. **Tetikleyiciler** sekmesini seçin, **Yeni'ye** tıklayın ve aşağıdaki işlemleri yapın:

   1. **Ayarlar'ın** altında **Günlük** seçeneğini belirleyin ve ardından betiği ilk kez çalıştırmak için bir tarih ve saat seçin. Betik her gün belirtilen saatte çalıştırılır.
   
   1. **Gelişmiş ayarlar'ın** altında **Etkin** onay kutusunun seçili olduğundan emin olun.
   
   1. **Tamam'a** tıklayın.

7. **Eylemler** sekmesini seçin, **Yeni'ye** tıklayın ve ardından aşağıdaki işlemleri yapın:

   ![İk bağlayıcısı betiği için yeni bir zamanlanmış görev oluşturmak için eylem ayarları.](../media/HRConnectorScheduleTask1.png)

   1. **Eylem** açılan listesinde **Program başlat'ın** seçili olduğundan emin olun.

   1. **Program/betik** kutusunda **Gözat'a** tıklayın ve aşağıdaki konuma gidin ve yolun kutuda görüntülenmesi için seçin: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. **Bağımsız değişken ekle (isteğe bağlı)** kutusunda, 4. Adımda çalıştırdığınız betik komutunu yapıştırın. Örneğin, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Başlangıç yeri **(isteğe bağlı)** kutusuna, 4. Adımda çalıştırdığınız betiğin klasör konumunu yapıştırın. Örneğin, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Yeni eylemin ayarlarını kaydetmek için **Tamam'a** tıklayın.

8. **Görev Oluştur** penceresinde **Tamam'a** tıklayarak zamanlanmış görevi kaydedin. Kullanıcı hesabı kimlik bilgilerinizi girmeniz istenebilir.

   Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.

   ![Yeni görev Görev Zamanlayıcı Kitaplığı'nda görüntülenir.](../media/HRConnectorTaskSchedulerLibrary.png)

   Betiğin en son çalıştırıldığı ve bir sonraki çalıştırma zamanlaması görüntülenir. Görevi düzenlemek için çift tıklayabilirsiniz.

   Ayrıca, uyumluluk merkezindeki ilgili İk bağlayıcısının açılır sayfasında betiğin en son ne zaman çalıştığını da doğrulayabilirsiniz.