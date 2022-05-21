---
title: Office dosyaları için duyarlılık etiketlerini etkinleştirme
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
description: Yöneticiler, SharePoint ve OneDrive'da Word, Excel ve PowerPoint dosyaları için duyarlılık etiketi desteğini etkinleştirebilir.
ms.openlocfilehash: ee24663fd5fe1de1bdce8b2d210174a05f156394
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621356"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>SharePoint ve OneDrive'daki Office dosyaları için hassasiyet etiketlerini etkinleştirme

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kullanıcıların [duyarlılık etiketlerinizi](sensitivity-labels.md) Web için Office uygulayabilmesi için SharePoint ve OneDrive'da [desteklenen Office dosyaları](sensitivity-labels-office-apps.md#office-file-types-supported) için yerleşik etiketlemeyi etkinleştirin. Bu özellik etkinleştirildiğinde, kullanıcılar şeritte **Duyarlılık** düğmesini görür ve böylece etiketleri uygulayabilir ve durum çubuğunda uygulanan etiket adlarını görebilir.

Bu özelliğin etkinleştirilmesi, SharePoint ve OneDrive duyarlılık etiketi kullanılarak şifrelenmiş Office dosyaların içeriğini işleyebilmesine de neden olur. Etiket Web için Office veya Office masaüstü uygulamalarına uygulanabilir ve SharePoint ve OneDrive yüklenebilir veya kaydedilebilir. Bu özelliği etkinleştirene kadar bu hizmetler şifrelenmiş dosyaları işleyemez; bu da birlikte yazma, eBulma, Microsoft Purview veri kaybını önleme, arama ve diğer işbirliğine dayalı özelliklerin bu dosyalar için çalışmayabileceği anlamına gelir.

SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, bulut tabanlı bir anahtarla şifreleme uygulayan (ve [Çift Anahtarlı Şifreleme](double-key-encryption.md) kullanmayan) duyarlılık etiketine sahip yeni ve değiştirilmiş dosyalar için:

- Word, Excel ve PowerPoint dosyaları için SharePoint ve OneDrive etiketi tanır ve artık şifrelenmiş dosyanın içeriğini işleyebilir.

- Kullanıcılar bu dosyaları SharePoint veya OneDrive indirdiğinde veya bu dosyalara eriştiğinde duyarlılık etiketi ve etiketten tüm şifreleme ayarları zorunlu tutulur ve depolandığı her yerde dosyada kalır. Belgeleri korumak için yalnızca etiketleri kullanmak için kullanıcı kılavuzu sağladığınızı doğrulayın. Daha fazla bilgi için bkz[. Bilgi Rights Management (IRM) seçenekleri ve duyarlılık etiketleri](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Kullanıcılar etiketli ve şifrelenmiş dosyaları SharePoint veya OneDrive karşıya yüklediğinde, en azından bu dosyalar üzerinde görüntüleme haklarına sahip olmaları gerekir. Örneğin, dosyaları SharePoint dışında açabilirler. Bu minimum kullanım haklarına sahip değilse karşıya yükleme başarılı olur ancak hizmet etiketi tanımaz ve dosya içeriğini işleyemez.

- Şifreleme uygulayan duyarlılık etiketlerine sahip Office dosyalarını açmak ve düzenlemek için Web için Office (Word, Excel, PowerPoint) kullanın. Şifreleme ile atanan izinler zorlanır. Bu belgeler için [otomatik etiketlemeyi](apply-sensitivity-label-automatically.md) de kullanabilirsiniz.

- Dış kullanıcılar, konuk hesaplarını kullanarak şifreleme ile etiketlenmiş belgelere erişebilir. Daha fazla bilgi için bkz. [Dış kullanıcılar ve etiketli içerik desteği](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eBulma, bu dosyalar için tam metin aramayı destekler ve veri kaybı önleme (DLP) ilkeleri bu dosyalardaki içeriği destekler.

> [!NOTE]
> Şifreleme bir şirket içi anahtarla (genellikle "kendi anahtarını tutma" veya HYOK olarak adlandırılan bir anahtar yönetimi topolojisi) veya [Çift Anahtar Şifrelemesi](double-key-encryption.md) kullanılarak uygulanmışsa, dosya içeriğini işlemeye yönelik hizmet davranışı değişmez. Bu nedenle bu dosyalar için birlikte yazma, eBulma, veri kaybı önleme, arama ve diğer işbirliğine dayalı özellikler çalışmaz.
>
> SharePoint ve OneDrive davranışı, bu konumlarda tek bir Azure tabanlı anahtar kullanılarak şifrelemeyle etiketlenen mevcut dosyalar için de değişmez. bu dosyaların SharePoint ve OneDrive Office dosyalar için duyarlılık etiketlerini etkinleştirdikten sonra yeni özelliklerden yararlanması için dosyaların yeniden indirilip karşıya yüklenmesi veya düzenlenmesi gerekir.

SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, SharePoint ve OneDrive belgelere uygulanan duyarlılık etiketlerini izlemek için üç yeni [denetim olayı](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) sağlanır:

- **Dosyaya duyarlılık etiketi uygulandı**
- **Dosyaya uygulanan duyarlılık etiketi değiştirildi**
- **Dosyadan duyarlılık etiketi kaldırıldı**

Yeni özelliklerin nasıl çalıştığını görmek için aşağıdaki videoyu izleyin (ses yok):

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

her zaman SharePoint ve OneDrive Office dosyalar için duyarlılık etiketlerini istediğiniz zaman devre dışı bırakma seçeneğiniz vardır.[](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)

Şu anda SharePoint'daki belgeleri SharePoint Bilgi Rights Management (IRM) kullanarak koruyorsanız, bu sayfadaki [SharePoint Bilgi Rights Management (IRM) ve duyarlılık etiketleri](#sharepoint-information-rights-management-irm-and-sensitivity-labels) bölümünü denetlediğinizden emin olun.

## <a name="requirements"></a>Gereksinimler

Bu yeni özellikler yalnızca [duyarlılık etiketleriyle](sensitivity-labels.md) çalışır. Şu anda Azure Information Protection etiketleriniz varsa, karşıya yüklediğiniz yeni dosyalar için bu özellikleri etkinleştirebilmek için önce bunları duyarlılık etiketlerine geçirin. Yönergeler için bkz. [Azure Information Protection etiketlerini birleşik duyarlılık etiketlerine geçirme](/azure/information-protection/configure-policy-migrate-labels).

Windows'da OneDrive eşitleme uygulama sürümü 19.002.0121.0008 veya üzerini ve Mac'te 19.002.0107.0008 veya sonraki bir sürümü kullanın. Bu sürümlerin her ikisi de 28 Ocak 2019'da yayımlandı ve şu anda tüm halkalarda yayınlanıyor. Daha fazla bilgi için [OneDrive sürüm notları](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0) bölümüne bakın. SharePoint ve OneDrive'da Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, eşitleme uygulamasının eski bir sürümünü çalıştıran kullanıcılardan bunu güncelleştirmeleri istenir.

## <a name="limitations"></a>Sınırlamalar

- SharePoint ve OneDrive, bu dosyalar PowerQuery verileri, özel eklentiler tarafından depolanan veriler veya Kapak Sayfası Özellikleri, içerik türü şemaları, özel Belge Bilgileri Paneli ve Özel XSN gibi özel XML bölümleri içerdiğinde Office masaüstü uygulamalarından etiketlenen ve şifrelenen bazı dosyaları işleyemez. Bu sınırlama, [kaynakça](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5) içeren dosyalar ve karşıya yüklendiklerinde [Belge Kimliği](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) eklenmiş dosyalar için de geçerlidir.

    Bu dosyalar için, daha sonra Web üzerinde Office açılabilmesi için şifreleme olmadan bir etiket uygulayın veya kullanıcılara dosyaları kendi masaüstü uygulamalarında açmalarını sağlayın. Yalnızca Web üzerinde Office etiketlenmiş ve şifrelenmiş dosyalar etkilenmez.

- SharePoint ve OneDrive, Azure Information Protection etiketlerini kullanarak zaten şifrelediğiniz mevcut dosyalara otomatik olarak duyarlılık etiketleri uygulamaz. Bunun yerine, SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra özelliklerin çalışması için şu görevleri tamamlayın:

    1. [Azure Information Protection etiketlerini duyarlılık etiketlerine geçirdiğinizden](/azure/information-protection/configure-policy-migrate-labels) ve [bunları Microsoft Purview uyumluluk portalı yayımladığınızdan](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) emin olun.
    2. Etiketli dosyaları indirin ve SharePoint veya OneDrive özgün konumlarına yükleyin.

- SharePoint ve OneDrive, şifrelemeyi uygulayan etiket şifreleme [için aşağıdaki yapılandırmalardan](encryption-sensitivity-labels.md#configure-encryption-settings) herhangi birine sahip olduğunda şifrelenmiş dosyaları işleyemiyor:
  - **Word, PowerPoint ve Excel'da etiket ve** onay kutusunu **uygularken kullanıcıların izinleri atamasına izin verin**. Bu ayar bazen "kullanıcı tanımlı izinler" olarak adlandırılır.
  - **İçeriğe kullanıcı erişiminin süresi doluyor** , **Hiçbir Zaman** dışında bir değere ayarlanır.
  - **Çift Anahtar Şifrelemesi** seçildi.

    Bu şifreleme yapılandırmalarından herhangi birine sahip etiketler için, etiketler Web için Office kullanıcılara gösterilmez. Ayrıca, yeni özellikler bu şifreleme ayarlarına sahip etiketli belgelerle kullanılamaz. Örneğin, bu belgeler güncelleştirilse bile arama sonuçlarında döndürülmeyecektir.

- Performans nedenleriyle, belgeyi SharePoint karşıya yüklediğinizde veya kaydettiğinizde ve dosyanın etiketi şifreleme uygulamadığında, belge kitaplığındaki **Duyarlılık** sütununun etiket adını görüntülemesi biraz zaman alabilir. Bu sütundaki etiket adına bağlı betikler veya otomasyon kullanıyorsanız bu gecikmeyi dikkate alın.

- Belge SharePoint kullanıma alınmışken etiketlenmişse, belge iade edilene ve [SharePoint'da](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de) açılana kadar belge kitaplığındaki **Duyarlılık** sütunu etiket adını görüntülemez.

- Etiketli ve şifrelenmiş bir belge, hizmet sorumlusu adı kullanan bir uygulama veya hizmet tarafından SharePoint veya OneDrive indirilirse ve ardından farklı şifreleme ayarları uygulayan bir etiketle yeniden karşıya yüklenirse, karşıya yükleme başarısız olur. Örnek bir senaryo, Microsoft Defender for Cloud Apps dosyadaki duyarlılık etiketini Gizli **olandan Çok Gizli'ye** veya **Gizli'den** **Genel'e** değiştirir.
    
    Uygulama veya hizmet [etiketli belge için şifrelemeyi kaldırma](#remove-encryption-for-a-labeled-document) bölümünde açıklandığı gibi [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'ini çalıştırırsa karşıya yükleme başarısız olmaz. Alternatif olarak, karşıya yüklemeden önce özgün dosya silinir veya dosya adı değiştirilir.

- Kullanıcılar, aşağıdaki Farklı Kaydet senaryosunda şifrelenmiş belgeleri açabilmekte gecikmeler yaşayabilir: Office masaüstü sürümünü kullanan kullanıcı, şifreleme uygulayan duyarlılık etiketine sahip bir belge için Farklı Kaydet'i seçer. Kullanıcı konum için SharePoint veya OneDrive seçer ve sonra bu belgeyi hemen Web için Office'da açmaya çalışır. Hizmet şifrelemeyi işlemeye devam ediyorsa, kullanıcı belgenin masaüstü uygulamasında açılması gerektiğini belirten bir ileti görür. Birkaç dakika içinde yeniden denerlerse, belge Web için Office'da başarıyla açılır.

- Şifrelenmiş belgeler için yazdırma Web için Office desteklenmez.

- Web için Office'daki şifrelenmiş belgeler için panoya ve ekran yakalamalarına kopyalama engellenmez. Daha fazla bilgi için bkz. [Ekran yakalamaları Rights Management engelleyebilir mi?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Varsayılan olarak, Office masaüstü uygulamaları ve mobil uygulamalar, şifreleme ile etiketlenmiş dosyalar için birlikte yazmayı desteklemez. Bu uygulamalar etiketli ve şifrelenmiş dosyaları özel düzenleme modunda açmaya devam ediyor.
    
    > [!NOTE]
    > Birlikte yazma artık Windows ve macOS için desteklenmektedir. Daha fazla bilgi için bkz. [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirme](sensitivity-labels-coauthoring.md).

- Yönetici, kullanıcıların eşitleme istemcisine indirilen dosyalara zaten uygulanmış yayımlanmış bir etiketin ayarlarını değiştirirse, kullanıcılar dosyada yaptıkları değişiklikleri OneDrive Eşitleme klasörüne kaydedemeyebilir. Bu senaryo, şifreleme ile etiketlenen dosyalara ve ayrıca etiket değişikliği şifreleme uygulayan bir etikete şifreleme uygulanmayan bir etiketten geldiğinde geçerlidir. Kullanıcılar [beyaz çapraz simge hatası içeren kırmızı bir daire](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3) görür ve yeni değişiklikleri ayrı bir kopya olarak kaydetmeleri istenir. Bunun yerine dosyayı kapatıp yeniden açabilir veya Web için Office kullanabilirler.

- Kullanıcılar, Web için Office kullanmak yerine Word, Excel veya PowerPoint için masaüstü ve mobil uygulamaları kullandıklarında çevrimdışı veya uyku moduna geçtikten sonra kaydetme sorunlarıyla karşılaşabilir. Bu kullanıcılar, Office uygulaması oturumlarını sürdürürken ve değişiklikleri kaydetmeye çalıştıklarında, özgün dosyayı kaydetmek yerine bir kopyasını kaydetme seçeneği içeren bir karşıya yükleme hatası iletisi görürler.

- Aşağıdaki yollarla şifrelenmiş belgeler Web için Office açılamaz:
  - Şirket içi anahtar kullanan şifreleme ("kendi anahtarını tut" veya HYOK)
  - [Çift AnahtarLı Şifreleme](double-key-encryption.md) kullanılarak uygulanan şifreleme
  - Bir etiketten bağımsız olarak uygulanan şifreleme, örneğin doğrudan bir Rights Management koruma şablonu uygulanarak.

- [Diğer diller](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-center-powershell) için yapılandırılmış etiketler desteklenmez ve yalnızca özgün dili görüntüler.

- SharePoint veya OneDrive'da bir belgeye uygulanmış olan bir etiketi, ilgili etiket ilkesinden kaldırmak yerine silerseniz, indirildiğinde belge etiketlenmez veya şifrelenmez. Buna karşılık, etiketlenen belge SharePoint veya OneDrive dışında depolanıyorsa, etiket silinirse belge şifrelenmiş olarak kalır. Bir test aşamasında etiketleri silebilirsiniz ancak üretim ortamında etiket silmenin çok nadir olduğunu unutmayın.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirme (kabul etme)

yeni özellikleri etkinleştirmek için Microsoft Purview uyumluluk portalı veya PowerShell kullanabilirsiniz. SharePoint ve OneDrive için tüm kiracı düzeyindeki yapılandırma değişikliklerinde olduğu gibi, değişikliğin geçerli olması yaklaşık 15 dakika sürer.

### <a name="use-the-microsoft-purview-compliance-portal-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteğini etkinleştirmek için Microsoft Purview uyumluluk portalı kullanın

Bu seçenek, SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirmenin en kolay yoludur, ancak kiracınız için genel yönetici olarak oturum açmanız gerekir.

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) genel yönetici olarak oturum açın ve **ÇözümlerFormasyon** >  **korumasıBeller'e** >  gidin

2. Office çevrimiçi dosyalarda içerik işleme özelliğini açmak için bir ileti görürseniz **Şimdi aç'ı** seçin:

    ![Office Online için duyarlılık etiketlerini etkinleştirmek için şimdi aç düğmesi.](../media/sensitivity-labels-turn-on-banner.png)

    Komut hemen çalışır ve sayfa bir sonraki yenilendiğinde artık iletiyi veya düğmeyi görmezsiniz.

> [!NOTE]
> Microsoft 365 Multi-Geo kullanıyorsanız, tüm coğrafi konumlarınızda bu özellikleri etkinleştirmek için PowerShell'i kullanmanız gerekir. Ayrıntılar için sonraki bölüme bakın.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteğini etkinleştirmek için PowerShell kullanma

Microsoft Purview uyumluluk portalı kullanmaya alternatif olarak, SharePoint Online [PowerShell'den Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanarak duyarlılık etiketleri desteğini etkinleştirebilirsiniz.

Microsoft 365 Multi-Geo kullanıyorsanız, tüm coğrafi konumlarınızda bu desteği etkinleştirmek için PowerShell'i kullanmanız gerekir.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>SharePoint Online Management Shell'i hazırlama

SharePoint ve OneDrive'da Office dosyalar için duyarlılık etiketlerini etkinleştirmek üzere PowerShell komutunu çalıştırmadan önce, Çevrimiçi Yönetim Kabuğu sürüm 16.0.19418.12000 veya üzerini SharePoint çalıştırdığınızdan emin olun. En son sürüme zaten sahipseniz, PowerShell komutunu çalıştırmak için [sonraki yordama](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) atlayabilirsiniz.

1. PowerShell galerisinden SharePoint Online Management Shell'in önceki bir sürümünü yüklediyseniz, aşağıdaki cmdlet'i çalıştırarak modülü güncelleştirebilirsiniz.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Alternatif olarak, Microsoft İndirme Merkezi'nden SharePoint Online Management Shell'in önceki bir sürümünü yüklediyseniz, **Program ekleme veya kaldırma'ya** gidebilir ve SharePoint Online Management Shell'i kaldırabilirsiniz.

3. Web tarayıcısında İndirme Merkezi sayfasına gidin ve [En son SharePoint Online Management Shell'i indirin](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Dilinizi seçin ve ardından **İndir'e** tıklayın.

5. x64 ve x86 .msi dosyası arasında seçim yapın. Windows 64 bit sürümünü çalıştırıyorsanız x64 dosyasını veya 32 bit sürümü çalıştırıyorsanız x86 dosyasını indirin. Bilmiyorsanız bkz[. Windows işletim sisteminin hangi sürümünü kullanıyorum?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Dosyayı indirdikten sonra, dosyayı çalıştırın ve Kurulum Sihirbazı'ndaki adımları izleyin.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Duyarlılık etiketleri desteğini etkinleştirmek için PowerShell komutunu çalıştırın

Yeni özellikleri etkinleştirmek için *EnableAIPIntegration* parametresiyle [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanın:

1. Microsoft 365'da genel yönetici veya SharePoint yönetici ayrıcalıklarına sahip bir iş veya okul hesabı kullanarak SharePoint bağlanın. Nasıl yapılacağını öğrenmek için bkz[. SharePoint Online Management Shell'i kullanmaya başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > Microsoft 365 Multi-Geo kullanıyorsanız [Bağlan-SPOService](/powershell/module/sharepoint-online/connect-sposervice) ile -Url parametresini kullanın ve coğrafi konumlarınızdan biri için SharePoint Çevrimiçi Yönetim Merkezi site URL'sini belirtin.

2. Aşağıdaki komutu çalıştırın ve onaylamak için **Y tuşuna** basın:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. Microsoft 365 Multi-Geo için: Kalan coğrafi konumlarınızın her biri için 1. ve 2. adımları yineleyin.

## <a name="publishing-and-changing-sensitivity-labels"></a>Duyarlılık etiketlerini yayımlama ve değiştirme

duyarlılık etiketlerini SharePoint ve OneDrive kullanırken, yeni duyarlılık etiketleri yayımlarken veya mevcut duyarlılık etiketlerini güncelleştirirken çoğaltma süresine izin vermeniz gerektiğini unutmayın. Bu özellikle şifreleme uygulayan yeni etiketler için önemlidir.

Örneğin: Şifreleme uygulayan yeni bir duyarlılık etiketi oluşturup yayımlarsınız ve bu etiket kullanıcının masaüstü uygulamasında çok hızlı bir şekilde görünür. Kullanıcı bu etiketi bir belgeye uygular ve ardından SharePoint veya OneDrive yükler. Hizmet için etiket çoğaltması tamamlanmadıysa, yeni özellikler karşıya yüklemede bu belgeye uygulanmaz. Sonuç olarak, belge arama veya eBulma için döndürülmeyecek ve belge Web için Office açılamaz.

Etiketlerin zamanlaması hakkında daha fazla bilgi için bkz. [Yeni etiketlerin ve değişikliklerin etkin hale gelmesini bekleme](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect) zamanı.

Güvenlik önlemi olarak, önce yalnızca birkaç test kullanıcısına yeni etiketler yayımlamanızı, en az bir saat beklemenizi ve ardından SharePoint ve OneDrive etiket davranışını doğrulamanızı öneririz. Mevcut etiket ilkesine daha fazla kullanıcı ekleyerek veya etiketi standart kullanıcılarınız için mevcut bir etiket ilkesine ekleyerek etiketi daha fazla kullanıcının kullanımına sunabilmek için en az bir gün bekleyin. Standart kullanıcılarınız etiketi gördüğünde, etiket zaten SharePoint ve OneDrive ile eşitlenmiş durumdadır.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint Bilgi Rights Management (IRM) ve duyarlılık etiketleri

[SharePoint Bilgi Rights Management (IRM),](set-up-irm-in-sp-admin-center.md) dosyalar indirildiğinde şifreleme ve kısıtlamalar uygulayarak liste ve kitaplık düzeyindeki dosyaları korumaya yönelik eski bir teknolojidir. Bu eski koruma teknolojisi, yetkisiz kullanıcıların SharePoint dışındayken dosyayı açmasını önlemek için tasarlanmıştır.

Buna karşılık, duyarlılık etiketleri şifrelemeye ek olarak görsel işaretlerin (üst bilgiler, alt bilgiler, filigranlar) koruma ayarlarını sağlar. Şifreleme ayarları, kullanıcıların içerikle yapabileceklerini kısıtlamak için tüm [kullanım haklarını](/azure/information-protection/configure-usage-rights) destekler ve [birçok senaryoda](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) aynı duyarlılık etiketleri desteklenir. İş yükleri ve uygulamalar arasında tutarlı ayarlarla aynı koruma yönteminin kullanılması, tutarlı bir koruma stratejisine neden olur.

Ancak, hem koruma çözümlerini birlikte kullanabilirsiniz hem de davranış aşağıdaki gibidir:

- Şifreleme uygulayan duyarlılık etiketine sahip bir dosyayı karşıya yüklerseniz, SharePoint bu dosyaların içeriğini işleyemiyorsanız bu dosyalar için birlikte yazma, eBulma, DLP ve arama desteklenmez.

- Bir dosyayı Web için Office kullanarak etiketlerseniz, etiketten tüm şifreleme ayarları zorlanır. Bu dosyalar için birlikte yazma, eBulma, DLP ve arama desteklenir.

- Web için Office kullanarak etiketlenmiş bir dosyayı indirirseniz, etiket korunur ve IRM kısıtlama ayarları yerine etiketten tüm şifreleme ayarları uygulanır.

- Duyarlılık etiketiyle şifrelenmemiş bir Office veya PDF dosyası indirirseniz IRM ayarları uygulanır.

- Kullanıcıların IRM'yi desteklemeyen belgeleri karşıya yüklemesini engelleme de dahil olmak üzere ek IRM kitaplık ayarlarından herhangi birini etkinleştirdiyseniz, bu ayarlar uygulanır.

Bu davranışla, etiketlenmemiş olsalar bile tüm Office ve PDF dosyalarının indirilirse yetkisiz erişime karşı korunduğundan emin olabilirsiniz. Ancak, karşıya yüklenen etiketli dosyalar yeni özelliklerden yararlanamaz.

## <a name="search-for-documents-by-sensitivity-label"></a>Belgeleri duyarlılık etiketine göre arama

SharePoint veya OneDrive belirli bir duyarlılık etiketine sahip tüm belgeleri bulmak için **InformationProtectionLabelId** yönetilen özelliğini kullanın. Aşağıdaki söz dizimini kullanın: `InformationProtectionLabelId:<GUID>`

Örneğin, "Gizli" olarak etiketlenmiş ve bu etiketin GUID'i "8faca7b8-8d20-48a3-8ea2-0f96310a848e" olan tüm belgeleri aramak için, arama kutusuna şunu yazın:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

Arama, .zip dosyası gibi sıkıştırılmış bir dosyada etiketlenmiş belgeleri bulamaz.

Duyarlılık etiketlerinizin GUID'lerini almak için [Get-Label](/powershell/module/exchange/get-label) cmdlet'ini kullanın:

1. İlk olarak [Office 365 Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    Örneğin, yönetici olarak çalıştırdığınız bir PowerShell oturumunda genel yönetici hesabıyla oturum açın.

2. Ardından aşağıdaki komutu çalıştırın:

    ```powershell
    Get-Label |ft Name, Guid
    ```

Yönetilen özellikleri kullanma hakkında daha fazla bilgi için bkz. [SharePoint arama şemasını yönetme](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>Etiketli belge için şifrelemeyi kaldırma

bir SharePoint yöneticisinin SharePoint'da depolanan bir belgeden şifrelemeyi kaldırması gereken nadir durumlar olabilir. Bu belge için kendisine atanan Dışarı Aktarma veya Tam Denetim [Rights Management kullanım hakkı](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) olan tüm kullanıcılar, Azure Rights Management hizmeti tarafından uygulanan şifrelemeyi Azure Information Protection'dan kaldırabilir. Örneğin, bu kullanım haklarından herhangi birini kullanan kullanıcılar şifreleme uygulayan bir etiketi şifreleme olmadan bir etiketle değiştirebilir. [Bir süper kullanıcı](/azure/information-protection/configure-super-users) da dosyayı indirebilir ve şifreleme olmadan yerel bir kopya kaydedebilir.

Alternatif olarak, genel yönetici veya [SharePoint yöneticisi](/sharepoint/sharepoint-admin-role) [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet'ini çalıştırarak hem duyarlılık etiketini hem de şifrelemeyi kaldırabilir. Yöneticinin site veya dosyaya erişim izinleri olmasa veya Azure Rights Management hizmeti kullanılamıyor olsa bile bu cmdlet çalışır.

Örneğin:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Gereksinimler:

- SharePoint Online Management Shell sürüm 16.0.20616.12000 veya üzeri.

- Şifreleme, yönetici tanımlı şifreleme ayarlarına sahip bir duyarlılık etiketi tarafından uygulandı ( [şimdi izin ata](encryption-sensitivity-labels.md#assign-permissions-now) etiket ayarları). Bu cmdlet için [Çift Anahtar Şifrelemesi](encryption-sensitivity-labels.md#double-key-encryption) desteklenmiyor.

Gerekçe metni **dosyadan duyarlılık etiketi kaldırıldı** [denetim olayına](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) eklenir ve şifre çözme eylemi azure [Information Protection için koruma kullanımı günlüğüne](/azure/information-protection/log-analyze-usage) de kaydedilir.

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>SharePoint ve OneDrive için duyarlılık etiketlerini devre dışı bırakma (geri çevirme)

Bu yeni özellikleri devre dışı bırakırsanız, SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirdikten sonra karşıya yüklediğiniz dosyalar etiket tarafından korunmaya devam eder çünkü etiket ayarları uygulanmaya devam eder. Bu yeni özellikleri devre dışı bırakdıktan sonra yeni dosyalara duyarlılık etiketleri uyguladığınızda, tam metin araması, eBulma ve birlikte yazma artık çalışmaz.

Bu yeni özellikleri devre dışı bırakmak için PowerShell'i kullanmanız gerekir. SharePoint Online Management Shell ve [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet'ini kullanarak [, Duyarlılık etiketleri desteğini etkinleştirmek için PowerShell kullanma](#use-powershell-to-enable-support-for-sensitivity-labels) bölümünde açıklandığı gibi aynı *EnableAIPIntegration* parametresini belirtin. Ancak bu kez parametre değerini false olarak ayarlayın ve onaylamak için **Y tuşuna** basın:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Microsoft 365 Multi-Geo'nuz varsa, coğrafi konumlarınızın her biri için bu komutu çalıştırmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra, otomatik etiketleme ilkelerini kullanarak bu dosyaları otomatik olarak etiketlemeyi göz önünde bulundurun. Daha fazla bilgi için bkz. [İçeriğe otomatik olarak duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md).

Etiketli ve şifrelenmiş belgelerinizi kuruluşunuzun dışındaki kişilerle paylaşmanız mı gerekiyor?  Bkz. [Şifrelenmiş belgeleri dış kullanıcılarla paylaşma](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
