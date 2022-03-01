---
title: SharePoint ve Office dosyaları için duyarlılık OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Yöneticiler Word, Excel ve PowerPoint dosyaları için Word, SharePoint duyarlılık OneDrive.
ms.openlocfilehash: a77721175962acbddbaae393aef49d16b96a9215
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999092"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>SharePoint ve Office dosyaları için duyarlılık OneDrive

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Kullanıcıların duyarlılık etiketlerinizi [SharePoint'da Office için](sensitivity-labels-office-apps.md#office-file-types-supported) SharePoint dosyaları OneDrive yerleşik etiketlemeyi Web için Office.[](sensitivity-labels.md) Bu özellik etkinleştirildiğinde, kullanıcılar şeritte Duyarlılık düğmesini  görebilirler; böylelikle etiket uygulayabilirler ve durum çubuğunda uygulanan etiket adını görebilirler.

Bu özelliğin etkinleştirilmesi, SharePoint ve OneDrive bir duyarlılık etiketi kullanılarak şifrelenmiş Office dosyalarının içeriğinin işlenmelerine de neden olur. Etiket, Web için Office'Web için Office veya Office masaüstü uygulamalarına uygulanabilir ve SharePoint OneDrive. Bu özelliği etkinleştirene kadar, bu hizmetler şifrelenmiş dosyaları işleyemeksizin bu dosyalar için birlikte yazar, eKbulma, Veri Kaybı Önleme, arama ve diğer işbirliği özelliklerini işlemez.

SharePoint ve OneDrive'te Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra bulut tabanlı bir anahtarla şifrelemesi uygulanan (ve Çift Anahtar Şifrelemesi kullanmayan[) bir](double-key-encryption.md) duyarlılık etiketine sahip olan yeni ve değiştirilmiş dosyalar için:

- Word, Excel ve PowerPoint dosyalarında, SharePoint OneDrive etiketi tanır ve artık şifreli dosyanın içeriğini işler.

- Kullanıcılar dosya veya klasörleri kullanarak bu SharePoint veya OneDrive, duyarlılık etiketi ve etiketten alınan tüm şifreleme ayarları zorunlu kılınır ve depolandığı her yerde dosyada kalır. Yalnızca belgeleri korumak için etiketleri kullanmak üzere kullanıcı kılavuzu sağlarken emin olmak. Daha fazla bilgi için bkz [. Bilgi Hakları Yönetimi (IRM) seçenekleri ve duyarlılık etiketleri](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Kullanıcılar etiketli ve şifrelenmiş dosyaları e-posta SharePoint OneDrive, bu dosyalar için en azından görüntüleme hakları olması gerekir. Örneğin, dosyaların dış tarafından açılmasını SharePoint. Bu minimum kullanım hakkı yoksa, karşıya yükleme başarılı olur ancak hizmet etiketi tanımaz ve dosya içeriğini işleyer.

- Şifreleme Web için Office duyarlılık etiketleri olan Office dosyaları açmak ve düzenlemek için Word (Word, Excel, PowerPoint) kullanın. Şifrelemeyle atanmış olan izinler zorunlu kılındı. Bu belgeler için [otomatik etiketleme de](apply-sensitivity-label-automatically.md) kullanabilirsiniz.

- Dış kullanıcılar, konuk hesaplarını kullanarak şifreleme ile etiketlenmiş belgelere erişim sağlar. Daha fazla bilgi için bkz [. Dış kullanıcılar ve etiketli içerik desteği](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eBulma, bu dosyalar için tam metin araması ve Veri Kaybı Önleme (DLP) ilkelerinin bu dosyalarda içeriği desteklemesini destekler.

> [!NOTE]
> Şifreleme bir şirket içi anahtarla (çoğunlukla "kendi anahtarınızı tutma" veya HYOK) olarak adlandırılan bir anahtar yönetim topolojisi) ile veya Çift Anahtar Şifrelemesi kullanılarak uygulanmışsa [, dosya](double-key-encryption.md) içeriğini işlemeye yönelik hizmet davranışı değişmez. Dolayısıyla, bu dosyalar için birlikte yazarlık, eBulma, Veri Kaybını Önleme, arama ve diğer işbirliği özellikleri işe yaramadı.
>
> Bu SharePoint OneDrive tek Azure tabanlı anahtar kullanılarak şifreleme ile etiketlenmiş bu konumlarda var olan dosyalar için de değişiklik değildir. Bu dosyaların SharePoint ve OneDrive'ta Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra yeni özelliklerden yararlanabilmek için dosyaların indirildikten ve karşıya yükleniyor olması ya da düzenleniyor olması gerekir.

SharePoint ve OneDrive'Office dosyalarında duyarlılık etiketlerini etkinleştirdikten sonra, SharePoint ve OneDrive'ta belgelere uygulanan duyarlılık etiketlerini [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) izlemek için SharePoint üç yeni denetim OneDrive:

- **Dosyaya duyarlılık etiketi uygulandı**
- **Dosyaya uygulanan duyarlılık etiketi değiştirildi**
- **Duyarlılık etiketi dosyadan kaldırıldı**

Yeni özellikleri iş akışında görmek için aşağıdaki videoyu (ses yok) izleyin:

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

SharePoint ve OneDrive dosyalarında Office için duyarlılık etiketlerini devre dışı bırakma seçeneğine her zaman sahip oluruz.[](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)

Şu anda SharePoint'de SharePoint Bilgi Hakları Yönetimi'ni (IRM) kullanarak belgeleri koruyorsanız, bu sayfada SharePoint Bilgi Hakları Yönetimi [(IRM)](#sharepoint-information-rights-management-irm-and-sensitivity-labels) ve duyarlılık etiketleri bölümünü kontrol edin.

## <a name="requirements"></a>Gereksinimler

Bu yeni özellikler yalnızca duyarlılık [etiketleriyle](sensitivity-labels.md) çalışır. Şu anda Azure Information Protection etiketleriniz varsa, önce bunları duyarlılık etiketlerine geçirin; böylelikle karşıya yüklediğiniz yeni dosyalar için bu özellikleri etkinleştirebilirsiniz. Yönergeler için bkz [. Azure Information Protection etiketlerini birleştirilmiş duyarlılık etiketlerine geçirme](/azure/information-protection/configure-policy-migrate-labels).

Windows'ta OneDrive eşitleme uygulamasının 19.002.0121.0008 veya sonraki sürümünü ve Mac'te 19.002.0107.0008 veya sonraki bir sürümünü kullanın. Bu sürümlerin her ikisi de 28 Ocak 2019'da yayınlanacak ve tüm halkalarda yayımlanacak. Daha fazla bilgi için sürüm [OneDrive bakın](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Office ve SharePoint OneDrive dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, eşitleme uygulamasının daha eski bir sürümünü çalıştıran kullanıcılardan bu dosyaları güncelleştirmeleri istenir.

## <a name="limitations"></a>Sınırlamalar

- SharePoint ve OneDrive, bu dosyalar PowerQuery verileri, özel eklentiler tarafından depolanan veriler ya da Kapak Sayfası Özellikleri, içerik türü şemaları, özel Belge Bilgileri Paneli ve Özel XSN gibi özel XML bölümleri içeriyorsa, Office masaüstü uygulamaları tarafından etiketlenen ve şifrelenmiş bazı dosyaları işleyebilirsiniz. Bu sınırlama, karşıya yüklendiklerine Belge [Kimliği eklenmiş](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) olan dosyalar için de geçerlidir.

    Bu dosyalar için, daha sonra dosyalarda açılmaları için şifreleme olmadan bir etiket Web üzerinde Office veya kullanıcılardan dosyaları kendi masaüstü uygulamaları içinde açmalarını talimat edin. Yalnızca iş dosyalarında etiketlenen ve Web üzerinde Office dosyalar etkilenmez.

- SharePoint ve OneDrive, Azure Information Protection etiketlerini kullanarak zaten şifrelenmiş olan mevcut dosyalara otomatik olarak duyarlılık etiketleri uygulamaz. Bunun yerine, SharePoint ve Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra OneDrive için şu görevleri gerçekleştirin:

    1. [Azure Information Protection etiketlerini duyarlılık etiketlerine](/azure/information-protection/configure-policy-migrate-labels) geçirmeyi ve bunları etiketten [yayımlayın](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) Microsoft 365 uyumluluk merkezi.
    2. Etiketli dosyaları indirin ve etiketli dosyaları Dosya veya Klasör'de SharePoint OneDrive.

- SharePoint uygulanan OneDrive şifreleme için aşağıdaki yapılandırmalardan herhangi biri olduğunda, e-posta ve güvenlik dosyalarınız şifrelenmiş [dosyaları işleyenene kadar geçerlidir](encryption-sensitivity-labels.md#configure-encryption-settings):
  - **Word,** PowerPoint ve Excel'da etiket ve onay kutusunu uygulayan kullanıcıların izin atamasına izin verin. PowerPoint onay **kutusunun seçili olduğunu** belirtin. Bu ayar bazen "kullanıcı tanımlı izinler" olarak da adlandırılır.
  - **kullanıcının içeriğe erişiminin süresi hiçbir** zaman'dan farklı bir değere **ayarlanır**.
  - **Çift Anahtar Şifrelemesi** seçilidir.

    Bu şifreleme yapılandırmalarının herhangi birini içeren etiketler, başka bir şifreleme Web için Office. Buna ek olarak, yeni özellikler zaten bu şifreleme ayarlarına sahip etiketli belgelerle kullanılamaz. Örneğin, bu belgeler güncelleştirilse bile arama sonuçlarında döndürülmez.

- Performans nedenleriyle, bir belgeyi SharePoint'a yüklediğiniz veya kaydedtiyebilirsiniz ancak dosyanın etiketi şifreleme uygulamazsa, belge kitaplığında Duyarlılık  sütununu etiket adını görüntülemek biraz zaman alabiliyor. Bu sütunda etiket adına bağlı olan betikler veya otomasyonlar kullanırsanız, bu gecikmede faktör.

- Belge SharePoint'de kullanıma alınmışken etiketleniyorsa[, belge](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de) iade ve bir sonraki belge başka bir  dosyada açılana kadar belge kitaplığının Duyarlılık sütunu etiket adını SharePoint.

- Etiketli ve şifrelenmiş bir belge, SharePoint veya OneDrive hizmet asıl adını kullanan bir uygulama veya hizmet tarafından indirilir ve farklı şifreleme ayarlarının uygulandığı etiketle yeniden karşıya yüklenirse, karşıya yükleme başarısız olur. Örnek bir senaryoda Bulut Uygulamaları için Microsoft Defender, dosyanın duyarlılık etiketini Gizli'den Çok Gizli'ye veya Gizli'den **Genel'e** **değiştirir**.
    
    Etiketli belge için şifrelemeyi kaldırma bölümünde anlatıldı gibi, uygulama veya hizmet [önce Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'ini çalıştırırsa, karşıya yükleme [başarısız olmaz.](#remove-encryption-for-a-labeled-document) Ya da karşıya yüklemeden önce, özgün dosya silinir veya dosya adı değiştirilir.

- Kullanıcılar, şu Farklı Kaydet senaryosunda şifrelenmiş belgeleri açmada gecikmeler yaşanıyor olabilir: kullanıcı Office'in masaüstü sürümünü kullanırken, kullanıcı şifrelemeyi uygulanan duyarlılık etiketine sahip bir belge için Farklı Kaydet'i seçer. Kullanıcı konum SharePoint veya OneDrive öğesini seçer ve hemen bu belgeyi kendi kitaplığında açmayı Web için Office. Hizmet hala şifrelemeyi işleme devam ediyorsa, kullanıcı belgenin masaüstü uygulamasında açılması gerektiğinin bir iletisi görür. Birkaç dakika içinde yeniden denerse, belge başarılı bir şekilde Web için Office.

- Şifreli belgelerde, yazdırma bu dosyalarda Web için Office.

- E-posta Web için Office şifrelenmiş belgeler için panoya kopyalama ve ekran yakalamaları engellenmez. Daha fazla bilgi için bkz [. Hak Yönetimi ekran yakalamalarını önler mi?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Varsayılan olarak Office uygulamaları ve mobil uygulamalar şifreleme ile etiketlenmiş dosyalar için birlikte yazma özelliği desteklemez. Bu uygulamalar etiketli ve şifrelenmiş dosyaları özel kullanım modunda açmaya devam eder.
    
    > [!NOTE]
    > Birlikte yazma artık hem macOS hem de Windows için de destek gerektir. Daha fazla bilgi için bkz [. Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma özelliği etkinleştirme](sensitivity-labels-coauthoring.md).

- Yönetici, kullanıcıların eşitleme istemcisine indirilen dosyalara zaten uygulanmış olan yayımlanmış etiketin ayarlarını değiştirirse, kullanıcılar dosyada yaptıkları değişiklikleri OneDrive Eşitle klasörüne kaydede kadar. Bu senaryo, şifreleme ile etiketlenmiş olan dosyalara ve aynı zamanda etiket değişikliğinin şifreleme uygulanan bir etikete şifreleme uygulaymayacak bir etiketten geldiğinde de geçerlidir. Kullanıcılar beyaz [çarpı simgesi hatası olan kırmızı bir daire görüyor](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3) ve yeni değişiklikleri ayrı bir kopya olarak kaydetmeleri isten ediyor. Bunun yerine, dosyayı kapatıp yeniden açabilirsiniz veya dosyayı Web için Office.

- Kullanıcılar, Web için Office kullanmak yerine Word, Excel veya PowerPoint için masaüstü ve mobil uygulamaları kullanırken, çevrimdışı veya uyku moduna PowerPoint. Bu kullanıcılar Office uygulaması oturumlarına devam edebilir ve değişiklikleri kaydetmeyi denerse, karşıya yükleme hatası iletisiyle birlikte özgün dosyayı kaydetmek yerine bir kopyasını kaydetme seçeneğiyle karşıdan yükleme hatası alırlar.

- Aşağıdaki yollarla şifrelenmiş belgeler e-posta iletisinde Web için Office:
  - Şirket içi anahtar kullanan şifreleme ("kendi anahtarınızı tutma" veya HYOK)
  - Çift Anahtar Şifrelemesi kullanılarak [uygulanan şifreleme](double-key-encryption.md)
  - Örneğin, bir etiketten bağımsız olarak, doğrudan bir Hak Yönetimi koruma şablonu uygulayarak uygulanan şifreleme.

- Diğer diller için [yapılandırılmış etiketler](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-center-powershell) desteklenmiyor ve yalnızca özgün dili görüntüleniyor.

- geçerli etiket ilkesinden etiketi kaldırmak yerine SharePoint veya OneDrive'de belgeye uygulanmış olan etiketi silerseniz, indirdiğiniz belge etiketlenmez veya şifrelenmez. Buna karşılık, etiketli belge şirket dışında SharePoint OneDrive, etiket silinirse belge şifrelenmiş olarak kalır. Bir test aşamasında etiketleri silebilirsiniz, ancak üretim ortamında bir etiketi silmek çok seyrek görülen bir durumdur.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>E-posta ve posta SharePoint duyarlılık OneDrive etkinleştirme (kabul et)

Dosya veya PowerShell kullanarak yeni Microsoft 365 uyumluluk merkezi etkinleştirabilirsiniz. Kiracı ve kiracı düzeyindeki tüm yapılandırma SharePoint OneDrive olduğu gibi, değişikliğin etkili olacak şekilde yaklaşık 15 dakika sürer.

### <a name="use-the-compliance-center-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketlerinin desteğini etkinleştirmek için uyumluluk merkezini kullanma

Bu seçenek, SharePoint ve OneDrive duyarlılık etiketlerini etkinleştirmenin en kolay yolu OneDrive, ancak kiracınız için genel yönetici olarak oturum açmanız gerekir.

1. Genel yönetici olarak [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) oturum açın ve **SolutionsInformation** >  **protection'a gidin**

    Bu seçeneği hemen görmüyorsanız önce Hepsini **göster'i seçin**.

2. Çevrimiçi dosyalarda içeriği işleme olanağını açmak için bir ileti Office Şimdi **aç'ı seçin**:

    ![Office Online için duyarlılık etiketlerini etkinleştirmek Office aç düğmesi.](../media/sensitivity-labels-turn-on-banner.png)

    Komut hemen çalışır ve sayfa bir sonraki yenilendiğinde iletiyi veya düğmeyi göremeyeceksiniz.

> [!NOTE]
> Multi-Geo Microsoft 365 varsa, tüm coğrafi konumlarda bu özellikleri etkinleştirmek için PowerShell kullan gerekir. Ayrıntılar için sonraki bölüme bakın.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketlerinin desteğini etkinleştirmek için PowerShell kullanma

Uyumluluk merkezini kullanmaya alternatif olarak, SharePoint Online PowerShell'in [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanarak duyarlılık etiketleri desteğini etkinleştirebilirsiniz.

Multi-Geo Microsoft 365 varsa, tüm coğrafi konumlarda bu desteği etkinleştirmek için PowerShell kullan gerekir.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>Çevrimiçi Yönetim SharePoint Kabuğu'nu hazırlama

SharePoint ve OneDrive'ta Office dosyalarının duyarlılık etiketlerini etkinleştirmek için PowerShell komutunu çalıştırmadan önce, SharePoint Çevrimiçi Yönetim Kabuğu sürüm 16.0.19418.12000 veya sonraki bir sürümü çalıştırarak bu dosyaları çalıştırabilirsiniz. En son sürüme zaten sahipsinizse, PowerShell komutunu [çalıştırmak](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) için sonraki yordama geçebilirsiniz.

1. SharePoint Online Yönetim Kabuğu'nın PowerShell galerisinden önceki bir sürümünü yüklemişsanız, aşağıdaki cmdlet'i çalıştırarak modülü güncelleştirebilirsiniz.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Alternatif olarak, Microsoft İndirme Merkezi'nden SharePoint Çevrimiçi Yönetim Kabuğu'un önceki bir sürümünü yüklemişsanız, Program ekleme veya kaldırma'ya gidebilir ve SharePoint  Yönetim Kabuğu'SharePoint kaldırabilirsiniz.

3. Web tarayıcısında İndirme Merkezi sayfasına gidin ve Çevrimiçi Yönetim [Kabuğu'SharePoint en son sürümü indirin](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Dilinizi seçin ve ardından İndir'e **tıklayın**.

5. x64 ile x86 dosya arasında .msi seçin. Windows'un 64 bit sürümünü veya 32 bit sürümü çalıştırdıysanız x86 dosyasını çalıştırdıysanız x64 dosyasını indirin. Bilmiyorsanız, bkz. [Hangi Windows işletim sistemini çalıştır çalıştıryım?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Dosyayı indirdikten sonra, dosyayı çalıştırın ve Kurulum Sihirbazı'nın adımlarını izleyin.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteğini etkinleştirmek için PowerShell komutunu çalıştırma

Yeni özellikleri etkinleştirmek için [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini *EnableAIPIntegration parametresiyle* kullanın:

1. Microsoft 365'ta genel yönetici veya yönetici ayrıcalıklarına SharePoint iş veya okul hesabı Microsoft 365, SharePoint. Nasıl olduğunu öğrenmek için bkz[. Çevrimiçi Yönetim Kabuğu SharePoint başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > Microsoft 365 Multi-Geo kullanıyorsanız, [Bağlan-SPOService](/powershell/module/sharepoint-online/connect-sposervice) ile -Url parametresini kullanın ve coğrafi konumlardan biri için SharePoint Online Administration Center site URL'sini belirtin.

2. Aşağıdaki komutu çalıştırın ve onaylamak için **Y tuşuna** basın:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. Örneğin Microsoft 365 Multi-Geo: Kalan coğrafi konumların her biri için 1. ve 2. adımları yinele.

## <a name="publishing-and-changing-sensitivity-labels"></a>Duyarlılık etiketlerini yayımlama ve değiştirme

SharePoint ve OneDrive ile duyarlılık etiketlerini kullanıyorsanız, yeni duyarlılık etiketleri yayımlarken veya var olan duyarlılık etiketlerini güncellerken çoğaltma süresine izin vermeniz gerekmektedir. Bu, özellikle şifreleme uygulayan yeni etiketler için önemlidir.

Örneğin: Şifreleme uygulanan yeni bir duyarlılık etiketi oluşturabilir ve yayımlarsanız, bu etiket kullanıcının masaüstü uygulamasında çok hızlı bir şekilde görüntülenir. Kullanıcı bu etiketi belgeye uygular ve belgeyi başka bir SharePoint OneDrive. Hizmet için etiket çoğaltması tamamlanmamışsa, karşıya yükleme sırasında bu belgeye yeni özellikler uygulanmaz. Sonuç olarak, belge aramada veya eBulma'da iade Web için Office.

Aşağıdaki değişiklikler bir saat içinde yineler: Yeni ve silinen duyarlılık etiketleri ve ilkede hangi etiketlerin yer alan duyarlılık etiketi ilkesi ayarları.

Aşağıdaki değişiklikler 24 saat içinde yineler: Mevcut etiketler için duyarlılık etiketi ayarlarında yapılan değişiklikler.

Yineleme gecikmesi yeni duyarlılık etiketleri için yalnızca bir saat olduğundan, örnekteki senaryoyla çalışma ihtimaliniz çok düşük değildir. Ancak, yeni etiketleri ilk birkaç test kullanıcısına yayımlamak için, bir saat beklemenizi ve ardından etiket davranışını güvenlik önlemi SharePoint OneDrive. Son adım olarak, var olan etiket ilkesine daha fazla kullanıcı ekleyerek etiketi daha fazla kullanıcının kullanabilir hale getirebilirsiniz veya standart kullanıcılarınız için var olan bir etiket ilkesine etiketi  eklersiniz. Standart kullanıcılarınız etiketi gördüğünüzde, zaten Etiket Eşitleme ve Eşitleme SharePoint OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint Hakları Yönetimi (IRM) ve duyarlılık etiketlerini ekleme

[SharePoint Hakları Yönetimi (IRM),](set-up-irm-in-sp-admin-center.md) dosyalar indirilirken şifreleme ve kısıtlamalar uygulayarak liste ve kitaplık düzeyinde dosyaları koruyan eski bir teknolojidir. Bu eski koruma teknolojisi yetkisiz kullanıcıların dosyanın dışındayken açmasını engellemek için SharePoint.

Buna karşılık, duyarlılık etiketleri şifrelemenin yanı sıra görsel işaretlere (üst bilgiler, alt bilgiler, filigranlar) koruma ayarlarını da sağlar. Şifreleme ayarları, kullanıcıların içerikle neler yaplarını kısıtlamak için tüm kullanım hakları yelpazesini destekler ve aynı duyarlılık etiketleri birçok senaryoda [desteklenir](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels).[](/azure/information-protection/configure-usage-rights) Aynı koruma yöntemini iş yükleri ve uygulamalar genelinde tutarlı ayarlarla kullanmak tutarlı bir koruma stratejisine neden olur.

Bununla birlikte, hem koruma çözümlerini birlikte kullanabilirsiniz hem de davranış şöyledir:

- Şifrelemesi uygulanan bir duyarlılık etiketine sahip bir dosya yüklersiniz SharePoint birlikte yazın, eKbulma, DLP ve arama bu dosyalar için desteklensin diye bu dosyaların içeriğini işleyemz.

- Dosyayı E-posta Web için Office, etiketten gelen tüm şifreleme ayarları uygulanır. Bu dosyalar için birlikte kimlik doğrulaması, eKbulma, DLP ve arama de desteklene.

- WEB IÇIN OFFICE kullanılarak etiketlenmiş bir dosyayı indirirsanız, etiket korunur ve IRM kısıtlama ayarları yerine etiketten gelen tüm şifreleme ayarları uygulanır.

- Duyarlılık Office ile şifrelenmiş bir PDF veya PDF dosyası indirirken IRM ayarları uygulanır.

- Kullanıcıların IRM desteği olan belgeleri karşıya yüklemelerini önlemeyi de içeren ek IRM kitaplığı ayarlarından herhangi birini etkinleştirdiyseniz, bu ayarlar zorunlu kılındı.

Bu davranışla, tüm PDF Office dosyalar etiketli değil olsalar bile indirilirse yetkisiz erişimden korunacaklarından emin olabilirsiniz. Ancak, karşıya yüklenen etiketli dosyalar yeni özelliklerden yararlanz.


## <a name="search-for-documents-by-sensitivity-label"></a>Duyarlılık etiketine göre belgeleri arama

Belirli bir duyarlılık etiketine sahip bir belge veya belge üzerinde SharePoint tüm OneDrive bulmak için **InformationProtectionLabelId** yönetilen özelliğini kullanın. Aşağıdaki söz dizimlerini kullanın: `InformationProtectionLabelId:<GUID>`

Örneğin, "Gizli" olarak etiketlenmiş tüm belgeleri aramak ve bu etiketin GUID'si "8faca7b8-8d20-48a3-8ea2-0f96310a848e" olan tüm belgeleri aramak için, arama kutusuna şunları yazın:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

Arama, sıkıştırılmış bir dosyada etiketli belgeleri (.zip bulamaz.

Duyarlılık etiketlerinizin GUID'lerini almak için [, Get-Label cmdlet'ini](/powershell/module/exchange/get-label) kullanın:

1. İlk olarak, [Office 365 Güvenlik ve Uyumluluk & PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    Örneğin, yönetici olarak çalıştırdınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın.

2. Sonra aşağıdaki komutu çalıştırın:

    ```powershell
    Get-Label |ft Name, Guid
    ```

Yönetilen özellikleri kullanma hakkında daha fazla bilgi için bkz[.](/sharepoint/manage-search-schema) SharePoint.

## <a name="remove-encryption-for-a-labeled-document"></a>Etiketli belge için şifrelemeyi kaldırma

Sık görülen bazı durumlarda, yöneticinin SharePoint bir dosyada depolanan belgeden şifrelemeyi kaldırması SharePoint. Bu belge için O belgeye Atanan Dışarı Aktarma veya Tam Denetim'in Hak Yönetimi kullanım hakkı olan tüm kullanıcılar, Azure Rights Management hizmeti tarafından uygulanan şifrelemeyi Azure Information Protection'dan kaldırabilir.[](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Örneğin, bu kullanım haklarından herhangi birini kullanan kullanıcılar, şifrelemesi uygulanan etiketin yerine şifreleme olmayan bir etiket kullanabilir. Süper [bir kullanıcı](/azure/information-protection/configure-super-users) da dosyayı indirebilir ve şifreleme olmadan yerel bir kopyasını kaydedebilir.

Alternatif olarak, genel yönetici veya [SharePoint](/sharepoint/sharepoint-admin-role) [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'ini çalıştırarak hem duyarlılık etiketini hem de şifrelemeyi kaldırır. Yöneticinin site veya dosyaya erişim izinleri yoksa veya Azure Hak Yönetimi hizmeti kullanılamıyorsa bile bu cmdlet çalışır.

Örneğin:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Gereksinimler:

- SharePoint 16.0.20616.12000 veya sonraki bir sürümüne sahip olabilir.

- Şifreleme yönetici tanımlı şifreleme ayarlarına sahip bir duyarlılık etiketi tarafından uygulanmıştır ( [İzinleri şimdi ata etiket](encryption-sensitivity-labels.md#assign-permissions-now) ayarları). [Bu](encryption-sensitivity-labels.md#double-key-encryption) cmdlet için Çift Anahtar Şifrelemesi desteklenmiyor.

Gerekçe metni Dosyadan duyarlılık etiketi kaldırıldı denetim [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) olayına eklenir ve şifre çözme eylemi Azure Information Protection için koruma kullanım günlüğüne [de kaydedilir](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>Daha fazla ve daha fazla SharePoint (geri OneDrive) için duyarlılık etiketlerini devre dışı bırakma

Bu yeni özellikleri devre dışı bıraksanız bile, SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirdikten sonra yüklediğiniz dosyalar etiket tarafından korunmaya devam eder çünkü etiket ayarları zorunlu kılınmaya devam eder. Bu yeni özellikleri devre dışı bırakarak yeni dosyalara duyarlılık etiketleri uygulayabilirsiniz; tam metin araması, eBulma ve birlikte yazarlık özellikleri artık çalışmaz.

Bu yeni özellikleri devre dışı bırakmak için PowerShell kullanabilirsiniz. SharePoint Online Yönetim Kabuğu'nun ve [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanarak, Duyarlılık etiketleri desteğini etkinleştirmek için [PowerShell](#use-powershell-to-enable-support-for-sensitivity-labels) kullanma bölümünde açıklanan *EnableAIPIntegration* parametresinin aynısını belirtin. Ancak bu kez, parametre değerini yanlış olarak ayarlayın ve onaylamak için **Y tuşuna** basın:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Multi-Geo Microsoft 365, coğrafi konumların her biri için bu komutu çalıştırmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

SharePoint ve OneDrive'da Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, otomatik etiketleme ilkelerini kullanarak bu dosyaları otomatik olarak etiketlemeyi göz önünde bulundurabilirsiniz. Daha fazla bilgi için bkz [. içeriğe otomatik olarak duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md).

Etiketli ve şifrelenmiş belgelerinizi kuruluş dışındaki kişiler ile paylaşmanız mı gerekiyor?  Bkz [. Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
