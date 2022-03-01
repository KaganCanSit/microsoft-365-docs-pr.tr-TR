---
title: Portal başlatma zamanlayıcıyı kullanarak portalınızı başlatma
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
description: Bu makalede Portal başlatma zamanlayıcıyı kullanarak portalınızı nasıl başlatabilirsiniz?
ms.openlocfilehash: 99462adb9deb19ec54d9679451877b5398c9c820
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005029"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Portal başlatma zamanlayıcıyı kullanarak SharePoint başlatma

Portal, intraneti üzerinde SharePoint trafiğin yüksek olduğu bir SharePoint iletişim sitesidir; birkaç hafta boyunca 10.000 ile 100.000'den fazla görüntüleyiciye sahip bir sitedir. Kullanıcıların yeni kullanıcı portalınıza erişirken sorunsuz bir görüntüleme deneyimi yaşamak için portalınızı başlatmak için Portal başlatma zamanlayıcısını SharePoint kullanın.
<br>
<br>
Portal başlatma zamanlayıcısı, görüntüleyicileri dalgalarda toplu olarak gruplarken ve yeni portal için URL yönlendirmelerini yöneterek aşamalı bir devre dışı yaklaşımdan sonra size yardımcı olacak şekilde tasarlanmıştır. Her dalganın başlatması sırasında, sonraki dalgayla devam etmeden önce kullanıcı geri bildirimlerini topabilir, portal performansını izleyebilir ve sorunları çözmek için başlatmayı duraklatabilirsiniz. Aynı uygulama içinde portal [başlatmayı planlama hakkında daha fazla SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**İki tür yeniden yönlendirme vardır:**

- **Çift yönlü**: Mevcut bir klasik veya modern SharePoint yerine yeni bir modern SharePoint portalı başlatma
- **Geçici bir sayfaya yönlendirme: Var** olan bir portala sahip SharePoint modern bir portal SharePoint başlatma

Başlatmanın bir parçası olarak site izinleri dalgalardan ayrı olarak ayarilmelidir. Örneğin, kuruluş genelinde bir portal kullanıyorsanız, "Dış kullanıcılar hariç herkes" izinlerini ayarlayabilecek ve sonra güvenlik gruplarını kullanarak kullanıcılarınızı dalgalara ayırabilirsiniz. Dalgaya güvenlik grubu eklemek, o güvenlik grubunun siteye erişmesi için bu gruba erişim izni vermez.

> [!NOTE]
>
> - Bu özeliklere, **Ayarlar sitelerinin** giriş sayfasındaki Yer SharePoint erişebilirsiniz.
> - Bu özellik yalnızca portallarda SharePoint varsayılan ve önerilen tür olduğu için site sayfalarını kullanarak modern iletişim sitelerinde kullanılabilir.
> - Portalın başlatılmasını özelleştirmeniz ve zamanlamanız için sitenin site sahibi izinlerine sahip olması gerekir.
> - Başlatmaların en az yedi gün önceden zamanlanmış olması gerekir ve her dalga bir ile yedi gün arasında olabilir.
> - Gereken dalga sayısı beklenen kullanıcı sayısına göre otomatik olarak belirlenir.
> - Portalı başlatmayı zamanlamadan önce, [sitenin giriş sayfasının iyi SharePoint](https://aka.ms/perftool) için Sayfa Tanılama aracının çalıştır olması gerekir.
> - Başlatma sonunda, site üzerinde izinleri olan tüm kullanıcılar yeni siteye erişim iznine sahip olabilir.
> - Organizasyonunız [Viva Connections](/SharePoint/viva-connections) kullanıyorsa, kullanıcılar Microsoft Teams uygulama çubuğunda kuruluş simgesini görebilir, ancak simge seçildiğinde kullanıcılar dalga başlatılana kadar portala erişilemez.
> - Bu özellik, 21Vianet (Çin Office 365 tarafından Office 365 veya ABD Kamu planları Microsoft 365 için kullanılamaz.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Portal başlatma zamanlayıcı seçenekleri arasındaki farkları anlama:

Önceden portal başlatmaları yalnızca SharePoint PowerShell üzerinden zamanlanıyordı. Şimdi, portalında lansmanı zamanlamanıza ve yönetmenize yardımcı olacak iki seçenek vardır. Her iki araç arasındaki temel farklar hakkında bilgi edinebilirsiniz:

**SharePoint PowerShell sürümü:**

- [SharePoint PowerShell kullanmak için yönetici kimlik bilgileri gereklidir](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Tek dalgalı en düşük gereksinim
- Başlatmanızı Eşgüdümli Evrensel Saat (UTC) saat dilimine göre zamanlama

**Ürün içinde sürümü:**

- Site sahibi kimlik bilgileri gereklidir
- İki dalganın en düşük gereksinimi
- Lansman planlamanızı, portalın bölgesel ayarlarda belirtilen yerel saat dilimine göre zamanlama

## <a name="get-started-using-the-portal-launch-scheduler"></a>Portal başlatma zamanlayıcıyı kullanmaya başlama

1. Portal başlatma zamanlayıcı aracını kullanmadan [önce,](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) Site izinleri aracılığıyla bu siteye erişmesi gereken tüm kullanıcıları **Site** sahibi, Site üyesi veya Ziyaretçi olarak ekleyin.

2. Ardından, portal başlatma zamanlayıcıya iki şekilden birini kullanarak portal lansmanını zamanlamaya başlayabilirsiniz:

   **1**. Seçenek: Giriş sayfanız için veya giriş sayfası sürüm 3.0'a kadar yaptığınız değişiklikleri ilk birkaç kez düzenleyemez ve yeniden yayımlarsanız, Portal başlatma zamanlayıcı aracını kullanırsınız. **Zamanlamada ilerlemek** için Başlat başlat'ı seçin. Ya da **sayfa düzenlemelerinizi başlatmayı** zamanlamadan yeniden yayımlamak için Yeniden Yayımla'ya tıklayın.

   ![Giriş sayfasını yeniden yayımlarken portal başlatma zamanlayıcıyı kullanma isteminin resmi.](../media/portal-launch-republish-2.png)

   **2**. Seçenek: İstediğiniz zaman SharePoint iletişim sitesi giriş sayfasına gidip Ayarlar'yi ve portala başlatmayı zamanlamayı  zamanlaması için **Site** başlatmayı zamanla'ya bakabilirsiniz.

   ![Site başlatma Ayarlar vurgulanmış olarak Gezinti Bölmesi'nin resmi.](../media/portal-launch-settings-2.png)

3. Ardından portalın sistem durumu puanını onaylayın ve portal iyi bir puan alana kadar SharePoint Sistem Durumu [](https://aka.ms/perftool) aracı için Sayfa Tanılama'yı kullanarak portalda **geliştirmeler** edin. Ardından, **Sonraki**'yi seçin.

   ![Portal başlatma zamanlayıcı aracının resmi.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Site adı ve açıklaması Portal başlatma zamanlayıcısı'dan düzenlenemez ve bunun yerine Giriş sayfasından Site Ayarlar ve Site bilgileri seçerek  değiştirilebilir.

4. Açılan **listeden Beklenen kullanıcı** sayısı'ı seçin. Bu şekil, büyük olasılıkla siteye erişmesi gereken kullanıcıların sayısını temsil eder. Portal başlatma zamanlayıcısı, beklenen kullanıcılara bağlı olarak aşağıdaki gibi ideal dalga sayısını otomatik olarak belirler:

   - 10.000'den az kullanıcı: İki dalga
   - 10.000 - 30.000 kullanıcı: Üç dalga
   - 30.000'den 100.000 kullanıcıya: Beş dalga
   - 100.000'den fazla kullanıcı: 100.000'den fazla kullanıcıyla portalı başlatma bölümünde listelenen adımları kullanarak beş dalga ve Microsoft desteğine başvurun.

5. Ardından, gereken **yeniden yönlendirme türünü** seçin:

   **1. Seçenek:** Kullanıcıları var olan bir SharePoint sayfasına (çift yönlü) gönderme – Var olan bir SharePoint portalını değiştirmek için yeni bir modern SharePoint başlatmada bu SharePoint kullanın. Etkin dalga kullanan kullanıcılar, ister eski ister yeni siteye gitseler de, yeni siteye yönlendirilmezler. Yeni siteye erişmeye çalışan ve başlatilmeyen bir dalgada bulunan kullanıcılar, kendi dalga başlatılana kadar eski siteye yeniden yönlendirilene kadar geri yönlendirilenler.

   > [!NOTE]
   > Çift yönlü seçeneğini kullanırken, başlatmayı zamanlaması yapılan kişinin diğer kullanıcı portalında da site sahibi SharePoint gerekir.

   2. Seçenek: Kullanıcıları otomatik olarak yeniden ortaya konan bir geçici sayfaya (geçici sayfa yeniden **yönlendirmesi)** gönderme – Portalda var olan hiçbir geçici sayfa yoksa, geçici SharePoint kullanın. Kullanıcılar yeni modern bir SharePoint portalına yönlendiriliyor ve kullanıcı henüz başlatılan bir dalgada ise, geçici bir sayfaya yeniden yönlendiriliyor.

   **3. Seçenek: Kullanıcıları** bir dış sayfaya gönderme – Kullanıcının dalga başlatana kadar geçici giriş sayfası deneyimi için dış URL girin.

6. Dinleyicilerinizi dalgalara ayrılarak parça alın. Dalga başına 20'ye kadar güvenlik grubu ekleyin. Dalga ayrıntıları, her dalganın başlatılmasına kadar düzenlenebilir. Her dalga en az bir gün (24 saat) ve en çok yedi gün sürebilir. Bu, SharePoint ortamınıza büyük miktarda site kullanıcılarının tahakkuk etme ve ölçeklendirme fırsatı verir. Kullanıcı arabirimi aracılığıyla bir başlatma zamanlaması zamanlaması için, saat dilimi sitenin bölgesel ayarlarına göre olur.

   > [!NOTE]
   >
   > - Portal başlatma zamanlayıcısı otomatik olarak en az 2 dalga olarak varsayılan olarak kullanılır. Bununla birlikte, bu aracın PowerShell sürümü 1 dalgaya izin verecek.
   > - Microsoft 365 grupları Portal başlatma zamanlayıcının bu sürümü tarafından destek desteklemez.

7. Kimlerin siteyi hemen görüntülemesi gerektiğini belirleme ve bu bilgileri Dalgalardan muaf **kullanıcılar alanına** girme. Bu kullanıcılar dalgalardan hariçtir ve başlatma öncesinde, başlatma sırasında veya sonrasında yeniden yönlendirlanmaz.


    >[!NOTE]
    > En fazla 50 farklı kullanıcı veya güvenlik grubu eklenebilir. Dalgalar başlatmadan önce portala erişmek için 50'den fazla kişinin yer almalarına gerek olduğunda güvenlik gruplarını kullanın. 

8.  Portalın başlatma ayrıntılarını onaylayın ve **Zamanlama'ya tıklayın**. Başlatma zamanlanmışsa, portalın SharePoint devam edecekse, sağlıklı bir tanılama sonucu elde etmek için portalda yapılan tüm değişikliklerin yapılması gerekir.


### <a name="launch-a-portal-with-over-100k-users"></a>100.000'den fazla kullanıcılı bir portal başlatma

100.000'den fazla kullanıcısı olan bir portal başlatmayı planlıyorsanız, aşağıda listelenen adımları takip eden bir destek isteği gönderin. Tüm istenen bilgileri dahil etmek için emin olun.

> [!NOTE]
>
> - Bu işlem yalnızca aşağıdaki gereksinimleri karşılarsanız takip edilecektir:
> - Başlatma Sayfası tamamlandı.
> - [Portal Durum Kılavuzu](https://aka.ms/portalhealth) takip edildi.
> - Başlatma tarihi 14 gün içinde olur.

**Şu adımları izleyin:**

1. Yönetici olarak, yönetim merkezinde bir yardım sorgusu doldurmak için aşağıdaki bağlantıya tıklayın. 

[100 SharePoint kullanıcılı Portal'da Başlatma](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. Bölmenin en altında Dehaya **Başvurun'ı ve** sonra Yeni Hizmet **İsteği'ni seçin**. 

3. **Açıklama'nın** altında "100.000 kullanıcılı SharePoint Başlat Portalı" girin. 

4. Kalan bilgileri doldurun ve Bana **ulaşın'ı seçin**.

5. Bilet oluşturulduktan sonra destek temsilcisine aşağıdaki bilgileri sağlamakta emin olmak için:
   - Portal URL'si
   - Beklenen kullanıcı sayısı
   - Tahmini başlatma zamanlaması (dalga boyutlarının ayrıntılarıyla)
   - Başlatma sayfasının "HAR dosyasını dışarı aktarma" için Sayfa Tanılama aracını kullanın ve dosyayı destekle paylaşın

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Zamanlanmış bir portal başlatması üzerinde değişiklik yapma

Başlatma ayrıntıları, dalga başlatma tarihine kadar her dalga için düzenlenebilir.

1. Portal başlatma ayrıntılarını düzenlemek için, Site başlatma  **Ayarlar'ı seçin**.
2. Ardından **Düzenle'yi seçin**.
3. Düzenlemelerinizi bitirdikten sonra Güncelleştir'i **seçin**.

## <a name="delete-a-scheduled-portal-launch"></a>Zamanlanmış bir portal başlatmayı silme

Portal başlatma zamanlayıcı aracı kullanılarak zamanlanan başlatmalar, bazı dalgalar zaten başlatmış olsa bile herhangi bir zamanda iptal edebilir veya silinebilir.

1. Portalınız başlatmayı iptal etmek için, Gezinti'ye **Ayarlar** **Başlat'a ve Site başlatmayı planla'ya gidin**.

2. Ardından **Sil'i seçin** ve aşağıdaki iletiyi gördüğünüzde tekrar Sil'i seçin.

   ![Zamanlanmış bir başlatmayı silmek mi yoksa tutmak mı istediğiniz soran istemin görüntüsü.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>PowerShell Portalı başlat zamanlayıcıyı kullanma

SharePoint Portal başlatma zamanlayıcı aracı ilk başta yalnızca [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) aracılığıyla kullanılabilir durumdadır ve bu yöntemi tercih eden müşteriler için PowerShell aracılığıyla desteklenmye devam eder. Bu makalenin başındaki aynı notlar Portal başlatma zamanlayıcının her iki sürümü için de geçerlidir.

> [!NOTE]
> PowerShell'i kullanmak için yönetici SharePoint gerekir.
> PowerShell'de oluşturulan başlatmalar için portal başlatma ayrıntıları görünür ve PowerShell'de yeni Portal başlatma zamanlayıcı aracında SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Uygulama kurulumu ve SharePoint Online'a bağlanma

1. [Çevrimiçi Yönetim Kabuğu'SharePoint en son sürümünü indirin](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > SharePoint Online Yönetim Kabuğu'un önceki bir sürümünü yüklemişsiniz, Program ekleme veya kaldırma'ya gidin ve "Çevrimiçi Yönetim Kabuğu'SharePoint" kaldırın.
    > 
    > İndirme Merkezi sayfasında dilinizi seçin ve ardından İndir düğmesine tıklayın. X64 ile x86 dosya indirme arasında seçim .msi. Windows'un 64 bit sürümünü veya 32 bit sürümüyle çalışıyorsanız x86 dosyasını çalıştıran x64 dosyasını indirin. Bilmiyorsanız, bkz. Hangi [işletim Windows çalıştırım?](https://support.microsoft.com/help/13443/windows-which-operating-system). Dosya indirildikten sonra, dosyayı çalıştırın ve Kurulum Sihirbazı'nın adımlarını izleyin.

2. Bağlan yönetici SharePoint veya Genel Yönetici [olarak SharePoint yönetici Microsoft 365](/sharepoint/sharepoint-admin-role). Nasıl olduğunu öğrenmek için bkz[. Çevrimiçi Yönetim Kabuğu SharePoint başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Mevcut portal başlatma kurulumlarını görüntüleme

Mevcut portal başlatma yapılandırmaları olup olduğunu görmek için:

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Sitede bir portal başlatması zamanlama

Gereken dalga sayısı beklenen başlatma boyutuna bağlıdır.

- 10.000'den az kullanıcı: Bir dalga
- 10.000 - 30.000 kullanıcı: Üç dalga 
- 30.000'den 100.000 kullanıcıya: Beş dalga
- 100.000'den fazla kullanıcı: Beş dalga ve Microsoft hesabı ekibiyle iletişime geçin

#### <a name="steps-for-bidirectional-redirection"></a>Çift yönlü yeniden yönlendirme adımları

Çift yönlü yönlendirme, var olan klasik veya modern SharePoint yerine yeni bir modern SharePoint Online portalı başlatmayı içerir. Etkin dalga kullanan kullanıcılar, ister eski ister yeni siteye gitseler de, yeni siteye yönlendirilmezler. Yeni siteye erişmeye çalışan ve başlatilmeyen bir dalgada bulunan kullanıcılar, kendi dalga başlatılana kadar eski siteye yeniden yönlendirilene kadar geri yönlendirilenler.

Yalnızca eski sitenin varsayılan giriş sayfasıyla yeni sitenin varsayılan giriş sayfası arasında yeniden yönlendirmeyi destekleriz. Eski ve yeni sitelere yeniden yönlendirilmesi gerekmeden erişmesi gereken yöneticilerinizin veya sahiplerin olması gerekirse, bunların parametre kullanılarak listelenmiş olduğundan emin `WaveOverrideUsers` olursunuz.

Kullanıcıları varolan bir SharePoint siteden yeni bir kullanıcı sitesine aşamalı SharePoint şekilde geçirmek için:

1. Portal başlatma dalgalarını tasarlamak için aşağıdaki komutu çalıştırın.

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

2. Doğrulamayı tamamlar. Yeniden yönlendirmenin hizmet genelinde yapılandırmasını tamamlaması 5-10 dakika sürebilir.

#### <a name="steps-for-redirection-to-temporary-page"></a>Geçici sayfaya yeniden yönlendirme adımları

Geçici sayfa yeniden yönlendirmesi, portalında var olan bir SharePoint kullanılmalıdır. Kullanıcılar aşamalı olarak yeni bir modern SharePoint Online portalına yönlendiriliyor. Kullanıcı henüz başlatılan bir dalgada olursa, geçici bir sayfaya (herhangi bir URL) yeniden yönlendirilmesine neden olur.

1. Portal başlatma dalgalarını tasarlamak için aşağıdaki komutu çalıştırın.

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

2. Doğrulamayı tamamlar. Yeniden yönlendirmenin hizmet genelinde yapılandırmasını tamamlaması 5-10 dakika sürebilir.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Sitede bir portal başlatmayı duraklatma veya yeniden başlatma

1. Portal başlatmasını duraklatmak ve yaklaşan dalga ilerlemelerinin geçici olarak ortaya çıkacaklarını önlemek için aşağıdaki komutu çalıştırın:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Tüm kullanıcıların eski siteye yeniden yönlendirildiklerini doğrulama.

3. Duraklatılmış bir portal başlatmayı yeniden başlatmak için aşağıdaki komutu çalıştırın:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Yeniden yönlendirmenin artık geri yüklenebilir olduğunu onaylar.

### <a name="delete-a-portal-launch-on-the-site"></a>Sitede portal başlatmayı silme

1. Site için zamanlanmış veya devam eden bir portal başlatmayı silmek için aşağıdaki komutu çalıştırın.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Tüm kullanıcılar için yeniden yönlendirme olmadığını doğrulama.

## <a name="learn-more"></a>Daha fazla bilgi

[SharePoint Online'da portal lansman planınızı planlama](./planportallaunchroll-out.md)

[İletişim sitenizi planlama](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
