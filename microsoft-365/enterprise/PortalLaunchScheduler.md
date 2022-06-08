---
title: Portal başlatma zamanlayıcısını kullanarak portalınızı başlatma
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Bu makalede Portal başlatma zamanlayıcısını kullanarak portalınızı nasıl başlatabileceğiniz açıklanmaktadır.
ms.openlocfilehash: 2eef7a8488db579f4ba946342213b822227229d1
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941074"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>SharePoint Portal başlatma zamanlayıcısını kullanarak portalınızı başlatma

Portal, intranetinizdeki yüksek trafikli bir SharePoint iletişim sitesidir ve birkaç hafta boyunca 10.000 ile 100.000 arasında görüntüleyicisi olan bir sitedir. Kullanıcıların yeni SharePoint portalınıza erişirken sorunsuz bir görüntüleme deneyimi yaşamasını sağlamak için portalınızı başlatmak için Portal başlatma zamanlayıcısını kullanın.
<br>
<br>
Portal başlatma zamanlayıcısı, izleyicileri dalgalar halinde toplu olarak toplayarak ve yeni portal için URL yeniden yönlendirmelerini yöneterek aşamalı bir dağıtım yaklaşımını izlemenize yardımcı olmak üzere tasarlanmıştır. Her dalganın başlatılması sırasında kullanıcı geri bildirimi toplayabilir, portal performansını izleyebilir ve sonraki dalgaya geçmeden önce sorunları çözmek için başlatmayı duraklatabilirsiniz. [SharePoint'te portal başlatmayı planlama](/microsoft-365/Enterprise/Planportallaunchroll-out) hakkında daha fazla bilgi edinin.

**İki tür yeniden yönlendirme vardır:**

- **çift yönlü**: Mevcut bir SharePoint klasik veya modern portalını değiştirmek için yeni bir modern SharePoint portalı başlatın
- **Geçici bir sayfaya yeniden yönlendirme**: Mevcut SharePoint portalı olmadan yeni bir modern SharePoint portalı başlatın

Site izinleri fırlatmanın bir parçası olarak dalgalardan ayrı olarak ayarlanmalıdır. Örneğin, kuruluş genelinde bir portal yayınlıyorsanız, izinleri "Dış kullanıcılar dışında herkes" olarak ayarlayabilir ve ardından güvenlik gruplarını kullanarak kullanıcılarınızı dalgalara ayırabilirsiniz. Bir dalgaya güvenlik grubu eklemek, bu güvenlik grubunun siteye erişmesine izin vermez.

> [!NOTE]
>
> - Bu özelliğe SharePoint iletişim sitelerinin giriş sayfasındaki **Ayarlar** panelinden erişilebilir.
> - Bu özellik, portallar için kullanılacak varsayılan ve önerilen tür olduğundan, yalnızca site sayfalarını kullanan modern SharePoint iletişim sitelerinde kullanılabilir.
> - Portalın başlatılmasını özelleştirmek ve zamanlamak için sitenin site sahibi izinlerine sahip olmanız gerekir.
> - Fırlatmalar en az yedi gün önceden zamanlanmalıdır ve her dalga bir ila yedi gün sürebilir.
> - Gerekli dalga sayısı, beklenen kullanıcı sayısına göre otomatik olarak belirlenir.
> - Portal başlatmayı zamanlamadan önce, sitenin giriş sayfasının iyi durumda olduğunu doğrulamak [için SharePoint için Sayfa Tanılama aracının](https://aka.ms/perftool) çalıştırılması gerekir.
> - Başlatmanın sonunda, siteye izinleri olan tüm kullanıcılar yeni siteye erişebilir.
> - Kuruluşunuz [Viva Bağlantıları](https://microsoft.sharepoint.com/teams/MicrosoftViva/SitePages/Viva-Connections.aspx) kullanıyorsa, kullanıcılar Microsoft Teams uygulama çubuğunda kuruluşunuzun simgesini görebilir, ancak simge seçildiğinde kullanıcılar dalgası başlatılana kadar portala erişemez.
> - Bu özellik Office 365 Germany, 21Vianet (Çin) tarafından sağlanan Office 365 veya Microsoft 365 ABD Kamu planlarında kullanılamaz.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Portal başlatma zamanlayıcı seçenekleri arasındaki farkları anlayın:

Önceden portal başlatmaları yalnızca SharePoint PowerShell aracılığıyla zamanlanabilirdi. Artık portalınızın başlatmasını zamanlamanıza ve yönetmenize yardımcı olacak iki seçeneğiniz vardır. Her iki araç arasındaki temel farklar hakkında bilgi edinin:

**SharePoint PowerShell sürümü:**

- [SharePoint PowerShell'i](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) kullanmak için yönetici kimlik bilgileri gereklidir
- Bir dalganın minimum gereksinimi
- Başlatmanızı Eşgüdümlü Evrensel Saat (UTC) saat dilimine göre zamanlama

**Ürün içi sürüm:**

- Site sahibi kimlik bilgileri gereklidir
- İki dalganın minimum gereksinimi
- Başlatmanızı, bölgesel ayarlarda gösterildiği gibi portalın yerel saat dilimine göre zamanlayın

## <a name="get-started-using-the-portal-launch-scheduler"></a>Portal başlatma zamanlayıcısını kullanmaya başlama

1. Portal başlatma zamanlayıcı aracını kullanmadan önce, Site sahibi, Site üyesi veya Ziyaretçi olarak **Site izinleri** aracılığıyla [bu siteye erişmesi gereken tüm kullanıcıları ekleyin](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658).

2. Ardından, portal başlatma zamanlayıcıya iki yoldan biriyle erişerek portalınızın başlatmasını zamanlamaya başlayın:

   **1. Seçenek**: Giriş sayfanızdaki değişiklikleri ilk birkaç kez düzenleyip yeniden yayımladığınızda (veya giriş sayfası sürüm 3.0'a kadar) Portal başlatma zamanlayıcı aracını kullanmanız istenir. Zamanlama ile ilerlemek için **Başlatmayı zamanla'yı** seçin. Sayfa düzenlemelerinizi başlatmayı zamanlamadan yeniden yayımlamak için **Yeniden Yayımla'yı** da seçebilirsiniz.

   ![Giriş sayfası yeniden yayımlanırken portal başlatma zamanlayıcısını kullanma isteminin görüntüsü.](../media/portal-launch-republish-2.png)

   **2. Seçenek**: İstediğiniz zaman SharePoint iletişim sitesi giriş sayfasına gidebilir, **Ayarlar'ı** seçebilir ve portalınızın başlatmasını zamanlamak için **Site başlatmayı zamanla'yı** seçebilirsiniz.

   ![Site başlatmayı zamanla seçeneğinin vurgulandığı Ayarlar bölmesinin görüntüsü.](../media/portal-launch-settings-2.png)

3. Daha sonra portalın sistem durumu puanını onaylayın ve gerekirse portalınız **sağlıklı** puan alana kadar [SharePoint için Sayfa Tanılama](https://aka.ms/perftool) aracını kullanarak portalda iyileştirmeler yapın. Ardından, **Sonraki**'yi seçin.

   ![Portal başlatma zamanlayıcı aracının görüntüsü.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Site adı ve açıklaması Portal başlatma zamanlayıcısından düzenlenemez ve bunun yerine **ayarlar** ve ardından giriş **sayfasından Site bilgileri** seçilerek değiştirilebilir.

4. Açılan **listeden Beklenen kullanıcı sayısı'nı** seçin. Bu şekil, siteye erişmesi gereken kullanıcıların sayısını temsil eder. Portal başlatma zamanlayıcısı, aşağıdaki gibi beklenen kullanıcılara bağlı olarak ideal dalga sayısını otomatik olarak belirler:

   - 10 binden az kullanıcı: İki dalga
   - 10k - 30k kullanıcıları: Üç dalga
   - 30k+ ile 100 bin arasında kullanıcı: Beş dalga
   - 100 binden fazla kullanıcı: Beş dalga ve 100 binden fazla kullanıcıyla portalı başlat bölümünde listelenen adımlar aracılığıyla Microsoft desteğine başvurun.

5. Ardından, gereken **yeniden yönlendirme türünü** belirleyin:

   **Seçenek 1: Kullanıcıları mevcut bir SharePoint sayfasına gönderme (çift yönlü) – Mevcut bir SharePoint** portalını değiştirmek için yeni bir modern SharePoint portalı başlatırken bu seçeneği kullanın. Etkin dalgalardaki kullanıcılar, eski veya yeni siteye gitmelerine bakılmaksızın yeni siteye yönlendirilir. Yeni siteye erişmeye çalışan, başlatılmamış bir dalgadaki kullanıcılar, dalga başlatılana kadar eski siteye geri yönlendirilir.

   > [!NOTE]
   > Çift yönlü seçeneği kullanırken, başlatmayı zamanlayan kişinin diğer SharePoint portalında site sahibi izinleri de olmalıdır.

   **Seçenek 2: Kullanıcıları otomatik olarak oluşturulan geçici sayfaya gönderme (geçici sayfa yeniden yönlendirme)** – Mevcut SharePoint portalı olmadığında geçici sayfa yeniden yönlendirme kullan seçeneği kullanılmalıdır. Kullanıcılar yeni bir modern SharePoint portalına yönlendirilir ve bir kullanıcı başlatılmamış bir dalgadaysa, geçici bir sayfaya yönlendirilir.

   **Seçenek 3: Kullanıcıları dış sayfaya gönderme** – Kullanıcının dalgası başlatılana kadar geçici bir giriş sayfası deneyimi için dış URL sağlayın.

6. hedef kitlenizi dalgalara ayırabilirsiniz. Dalga başına en fazla 20 güvenlik grubu ekleyin. Dalga ayrıntıları, her dalganın fırlatılışına kadar düzenlenebilir. Her dalga en az bir gün (24 saat) ve en fazla yedi gün sürebilir. Bu, SharePoint'in ve teknik ortamınızın site kullanıcılarının büyük hacmine sahip olması ve ölçeklendirilmesi için bir fırsat sağlar. Kullanıcı arabirimi aracılığıyla başlatma zamanlarken, saat dilimi sitenin bölgesel ayarlarını temel alır.

   > [!NOTE]
   >
   > - Portal başlatma zamanlayıcısı otomatik olarak en az 2 dalga olarak varsayılan olarak ayarlanır. Ancak, bu aracın PowerShell sürümü 1 dalgaya izin verir.
   > - Microsoft 365 grupları Portal başlatma zamanlayıcısının bu sürümü tarafından desteklenmez.

7. Siteyi kimlerin hemen görüntülemesi gerektiğini belirleyin ve **dalgalardan muaf kullanıcılar** alanına bilgilerini girin. Bu kullanıcılar dalgaların dışında tutulur ve başlatma öncesinde, sırasında veya sonrasında yeniden yönlendirilmeyecektir.

    >[!NOTE]
    > En fazla 50 ayrı kullanıcı veya güvenlik grubu eklenebilir. Dalgalar başlatılmadan önce portala erişmek için 50'den fazla kişiye ihtiyacınız olduğunda güvenlik gruplarını kullanın.

8. Portal başlatma ayrıntılarını onaylayın ve **Zamanla'yı** seçin. Başlatma zamanlandıktan sonra, portalın başlatılması devam etmeden önce SharePoint portalı giriş sayfasında yapılan tüm değişikliklerin iyi durumda bir tanılama sonucu alması gerekir.

### <a name="launch-a-portal-with-over-100k-users"></a>100 binden fazla kullanıcı içeren bir portal başlatma

100.000'den fazla kullanıcı içeren bir portal başlatmayı planlıyorsanız, aşağıda listelenen adımları izleyerek bir destek isteği gönderin. İstenen tüm bilgileri eklediğinizden emin olun.

> [!NOTE]
>
> - Bu işlem yalnızca aşağıdaki gereksinimleri karşılıyorsanız izlenmelidir:
> - Başlatma Sayfası tamamlandı.
> - [Portal Sistem Durumu Kılavuzu](https://aka.ms/portalhealth) izlendi.
> - Fırlatma tarihi 14 gün içindedir.

**Şu adımları izleyin:**

1. Yönetici olarak, yönetim merkezinde bir yardım sorgusu dolduracak aşağıdaki bağlantıya tıklayın.

[SharePoint Portal'ı 100 bin kullanıcıyla başlatma](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. Bölmenin alt kısmında **Desteğe Başvurun'a** ve ardından **Yeni Hizmet İsteği'ne** tıklayın.

3. **Açıklama'nın** altında "SharePoint Portalını 100 bin kullanıcıyla başlat" yazın.

4. Kalan bilgileri doldurun ve **Benimle iletişime geçin'i** seçin.

5. Bilet oluşturulduktan sonra destek temsilcisine aşağıdaki bilgileri sağladığından emin olun:
   - Portal URL'si
   - Beklenen kullanıcı sayısı
   - Tahmini fırlatma zamanlaması (dalga boyutlarının ayrıntıları)
   - Başlatma sayfasının "HAR dosyasını dışarı aktarmak" için Sayfa Tanılama aracını kullanın ve dosyayı destekle paylaşın

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Zamanlanmış portal başlatmada değişiklik yapma

Fırlatma ayrıntıları, dalganın fırlatma tarihine kadar her dalga için düzenlenebilir.

1. Portal başlatma ayrıntılarını düzenlemek için **Ayarlar'a** gidin ve **Site başlatmayı zamanla'yı** seçin.
2. Ardından **Düzenle'yi** seçin.
3. Düzenlemelerinizi yapmayı bitirdiğinizde **Güncelleştir'i** seçin.

## <a name="delete-a-scheduled-portal-launch"></a>Zamanlanmış portal başlatmayı silme

Portal başlatma zamanlayıcı aracı kullanılarak zamanlanan başlatmalar, bazı dalgalar zaten başlatılmış olsa bile herhangi bir zamanda iptal edilebilir veya silinebilir.

1. Portalınızın başlatılmasını iptal etmek için **Ayarlar** ve **Site başlatmayı zamanla'ya** gidin.

2. Ardından **Sil'i** seçin ve ardından aşağıdaki iletiyi gördüğünüzde **sil'i** yeniden seçin.

   ![Zamanlanmış başlatmayı silmek mi yoksa tutmak mı istediğinizi soran istemin görüntüsü.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>PowerShell Portal başlatma zamanlayıcısını kullanma

SharePoint Portal başlatma zamanlayıcı aracı başlangıçta yalnızca [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) aracılığıyla kullanılabilirdi ve bu yöntemi tercih eden müşteriler için PowerShell aracılığıyla desteklenmeye devam edecektir. Bu makalenin başındaki notlar Portal başlatma zamanlayıcısının her iki sürümü için de geçerlidir.

> [!NOTE]
> SharePoint PowerShell'i kullanmak için yönetici izinlerine sahip olmanız gerekir.
> PowerShell'de oluşturulan başlatmalar için portal başlatma ayrıntıları görünür ve SharePoint'teki yeni Portal başlatma zamanlayıcı aracında yönetilebilir.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Uygulama kurulumu ve SharePoint Online'a bağlanma

1. [En son SharePoint Online Yönetim Kabuğu'nı indirin](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > SharePoint Online Yönetim Kabuğu'nun önceki bir sürümünü yüklediyseniz, Program ekle veya kaldır'a gidin ve "SharePoint Online Yönetim Kabuğu" öğesini kaldırın.
    >
    > İndirme Merkezi sayfasında dilinizi seçin ve ardından İndir düğmesine tıklayın. x64 ve x86 .msi dosyası indirme arasında seçim yapmanız istenir. Windows'un 64 bit sürümünü çalıştırıyorsanız x64 dosyasını veya 32 bit sürümünü çalıştırıyorsanız x86 dosyasını indirin. Bilmiyorsanız bkz [. Windows işletim sisteminin hangi sürümünü kullanıyorum?](https://support.microsoft.com/help/13443/windows-which-operating-system). Dosya indirildikten sonra çalıştırın ve Kurulum Sihirbazı'ndaki adımları izleyin.

2. Microsoft 365'te [SharePoint'e genel yönetici veya SharePoint yöneticisi](/sharepoint/sharepoint-admin-role) olarak bağlanın. Nasıl yapılacağını öğrenmek için bkz. [SharePoint Online Yönetim Kabuğu'na başlarken](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Mevcut portal başlatma kurulumlarını görüntüleme

Mevcut portal başlatma yapılandırmaları olup olmadığını görmek için:

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Sitede portal başlatma zamanlama

Gerekli dalgaların sayısı beklenen fırlatma boyutuna bağlıdır.

- 10 binden az kullanıcı: Bir dalga
- 10k - 30k kullanıcıları: Üç dalga
- 30k+ ile 100 bin arasında kullanıcı: Beş dalga
- 100 binden fazla kullanıcı: Beş dalga ve Microsoft hesabı ekibinize başvurun

#### <a name="steps-for-bidirectional-redirection"></a>Çift yönlü yeniden yönlendirme adımları

Çift yönlü yeniden yönlendirme, mevcut bir SharePoint klasik veya modern portalını değiştirmek için yeni bir modern SharePoint Online portalı başlatmayı içerir. Etkin dalgalardaki kullanıcılar, eski veya yeni siteye gitmelerine bakılmaksızın yeni siteye yönlendirilir. Yeni siteye erişmeye çalışan, başlatılmamış bir dalgadaki kullanıcılar, dalga başlatılana kadar eski siteye geri yönlendirilir.

Yalnızca eski sitedeki varsayılan giriş sayfası ile yeni sitedeki varsayılan giriş sayfası arasında yeniden yönlendirmeyi destekliyoruz. Yeniden yönlendirilmeden eski ve yeni sitelere erişmesi gereken yöneticileriniz veya sahipleriniz varsa, parametresi kullanılarak `WaveOverrideUsers` listelendiklerinden emin olun.

Kullanıcıları mevcut bir SharePoint sitesinden yeni bir SharePoint sitesine aşamalı olarak geçirmek için:

1. Portal başlatma dalgalarını ayarlamak için aşağıdaki komutu çalıştırın.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType Bidirectional -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Örneğin:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType Bidirectional -RedirectUrl "https://contoso.sharepoint.com/teams/oldsite" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Doğrulamayı tamamlayın. Yeniden yönlendirmenin hizmet genelinde yapılandırmasını tamamlaması 5-10 dakika sürebilir.

#### <a name="steps-for-redirection-to-temporary-page"></a>Geçici sayfaya yeniden yönlendirme adımları

Mevcut SharePoint portalı olmadığında geçici sayfa yeniden yönlendirme kullanılmalıdır. Kullanıcılar yeni bir modern SharePoint Online portalına aşamalı olarak yönlendirilir. Kullanıcı başlatılmamış bir dalgadaysa, geçici bir sayfaya (herhangi bir URL) yönlendirilir.

1. Portal başlatma dalgalarını ayarlamak için aşağıdaki komutu çalıştırın.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType ToTemporaryPage -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Örneğin:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType ToTemporaryPage -RedirectUrl "https://portal.contoso.com/UnderConstruction.aspx" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Doğrulamayı tamamlayın. Yeniden yönlendirmenin hizmet genelinde yapılandırmasını tamamlaması 5-10 dakika sürebilir.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Sitede portalı başlatmayı duraklatma veya yeniden başlatma

1. Devam eden bir portalı duraklatmak ve yaklaşan dalga ilerlemelerinin gerçekleşmesini geçici olarak önlemek için aşağıdaki komutu çalıştırın:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Tüm kullanıcıların eski siteye yönlendirildiğini doğrulayın.

3. Duraklatılmış bir portal başlatmasını yeniden başlatmak için aşağıdaki komutu çalıştırın:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Yeniden yönlendirmenin artık geri yüklendiğini doğrulayın.

### <a name="delete-a-portal-launch-on-the-site"></a>Sitedeki portal başlatmasını silme

1. Bir site için zamanlanmış veya devam eden bir portalı silmek için aşağıdaki komutu çalıştırın.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Tüm kullanıcılar için yeniden yönlendirme gerçekleşmediğini doğrulayın.

## <a name="learn-more"></a>Daha fazla bilgi

[SharePoint Online'da portalı başlatma dağıtım planınızı planlama](./planportallaunchroll-out.md)

[İletişim sitenizi planlama](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
