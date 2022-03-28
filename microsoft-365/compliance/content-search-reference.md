---
title: İçerik arama için özellik referansı
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Bu makale, İçerik arama hakkında birçok ayrıntıyı öğrenmene yardımcı olmak için Microsoft 365 uyumluluk merkezi araştırma belgesinde İçerik arama eBulma aracı hakkında başvuru bilgileri içerir.
ms.openlocfilehash: 3f2918c378d94fd65d4a89afed50957a2da40a7d
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716386"
---
# <a name="feature-reference-for-content-search"></a>İçerik arama için özellik referansı

Bu makalede, İçerik arama özelliklerinin ve işlevleri açıklanmıştır.

## <a name="content-search-limits"></a>İçerik arama sınırları

İçerik aramalarına uygulanan sınırların açıklaması için bkz. İçerik [arama sınırları](limits-for-content-search.md).

## <a name="building-a-search-query"></a>Arama sorgusu oluşturma

Arama sorgusu oluşturma, Boole arama işleçlerini ve arama koşullarını kullanma ve kuruluş dışındaki kullanıcılarla paylaşılan hassas bilgi türlerini ve içeriği arama hakkında ayrıntılı bilgi için bkz. Anahtar sözcük sorguları ve İçerik Arama için arama [koşulları](keyword-queries-and-search-conditions.md).

Arama sorgusu oluşturmak için anahtar sözcük listesini kullanırken aşağıdaki şeyleri unutmayın.

- Anahtar sözcük **listesini göster onay** kutusunu seçmeniz ve her satırdaki anahtar sözcüklerin (veya anahtar sözcük tümceciklerin) OR işleci tarafından bağlı olduğu bir arama sorgusu oluşturmak için her anahtar sözcüğü ayrı bir satıra **yazmalısınız** . Anahtar sözcükler listesini anahtar sözcük kutusuna yapıştırdıktan sonra **Enter** tuşuna basın; bunlar OR işleciyle **bağlantılı olmayacaktır** . Burada, bir anahtar sözcük listesinin nasıl ek birçok yanlış ve doğru şekilde ek örnekleri verilmiştir.

    **Yanlış**

    ![Anahtar sözcük listesini biçimlendirmenin yanlış yolu (listeyi anahtar sözcük kutusuna yapıştırarak).](../media/fb54e3df-232a-439a-b3d7-27a60ec76a4c.png)

    **Doğru**

    ![Anahtar sözcük listesini biçimlendirmenin doğru yolu (onay kutusunu seçerek ve listeyi yapıştırarak).](../media/5d511a7b-c1f9-499c-bffe-e075bfc9adec.png)

- Ayrıca bir çalışma dosyasındaki Excel veya düz metin dosyasındaki anahtar sözcüklerin veya anahtar sözcük tümceciklerinin listesini hazırlayıp, ardından listenizi kopyalayıp anahtar sözcük listesine yapıştırabilirsiniz. Bunu yapmak için Anahtar sözcük listesini **göster onay kutusunu seçmeniz** gerekir. Ardından, anahtar sözcük listesinin ilk satırına tıklayın ve listenizi yapıştırın. Metin veya Excel dosyasındaki her satır anahtar sözcük listesinde ayrı satıra yapıştırır.

- Anahtar sözcük listesini kullanarak bir sorgu oluşturduktaktan sonra, arama sorgusunun tam olarak bunu yapmak için arama sorgusu söz dizimlerini doğrulamak iyi bir fikirdir. Ayrıntılar bölmesinde sorgu altında gösterilen arama **sorgusunda** anahtar sözcükler **metinle (c:s) ayrılır**. Bu, anahtar sözcüklerin OR işlecine benzer bir mantıksal işleçle **bağlı olduğunu** gösterir. Benzer şekilde, arama sorgunuz koşullar içerirse, anahtar sözcükler ve koşullar **metinle (c:c) ayrılır**. Bu, anahtar sözcüklerin AND işlecine benzer bir işleve sahip mantıksal bir işleçle koşullarla bağlantılı **olduğunu** gösterir. Burada, anahtar sözcük listesi ve bir koşul kullanırken sonuç olarak sonuç alan arama sorgusu örneği (Ayrıntılar bölmesinde görüntülenir) ve ve bir örnek gösterilir.

    ![Anahtar sözcük listesi ve koşul kullanılarak oluşturulan sorgu örneği.](../media/b463750c-57fa-4602-9fed-0d5a420db3ad.png)

- İçerik aramanızı çalıştırarak, Microsoft 365 sorgunuza desteklenmeyen karakterler veya büyük harfle başlanmamış Boole işleçleri olup olmadığını otomatik olarak denetler. Desteklenmeyen karakterler çoğunlukla gizlidir ve genellikle arama hatasına neden olur veya desteklenmeyen sonuçlar döndürür. Denetlenen desteklenmeyen karakterler hakkında daha fazla bilgi için bkz. [İçerik Arama sorgunuza hataları denetleme](check-your-content-search-query-for-errors.md).

- İngilizce olmayan karakterlere (Çince karakterler gibi) anahtar sözcükler içeren bir arama sorgunuz varsa, İçerik arama'da Sorgu **dili-ülke/bölgeQuery**![ dili-ülke/bölge simgesine tıkekleyebilirsiniz.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) ve arama için bir dil ülke kültür kodu değeri seçin. Varsayılan dil/bölge nötr olur. İçerik arama için dil ayarını değiştirmenin gerek olup olduğunu nasıl değiştirebilirsiniz? İçerik konumlarına İngilizce olmayan karakterlerin bulunduğuna eminseniz, ancak arama hiçbir sonuç döndüreni bilmiyorsa, nedeni dil ayarı olabilir.

## <a name="partially-indexed-items"></a>Kısmen dizine eklenen öğeler

- Posta kutularında kısmen dizine alan öğeler, tahmini arama sonuçlarına dahil edilir. Tahmini arama sonuçlarına SharePoint OneDrive kısmen dizine alan öğeler dahil değildir. Daha fazla bilgi için bkz [. eBulma'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md).

## <a name="searching-onedrive-accounts"></a>OneDrive arama

- Kuruluşta yer alan ve OneDrive sitelerinin URL'lerinin listesini toplamak için bkz. OneDrive [konumların listesini oluşturma](/onedrive/list-onedrive-urls). Bu makaledeki bu betik, tüm site sitelerinin listesini içeren bir OneDrive oluşturur. Bu betiği çalıştırmak için, Çevrimiçi Yönetim Kabuğu'SharePoint ve kullananız gerekir. Arama yapmak istediğiniz her sitenin URL'sini, OneDrive Sitem etki alanının URL'sini eklemeye emin olun. Bu, tüm etki alanlarınızı içeren OneDrive, örneğin. `https://contoso-my.sharepoint.com` İşte, kullanıcının site için bir URL OneDrive: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

    Kişinin kullanıcı asıl adının (UPN) değişmesi ender durumlarda, kişinin ad OneDrive URL'si yeni UPN'yi de içine olacak şekilde değiştirilir. Böyle bir durumda, kullanıcının yeni URL'sini ekleyerek ve eskisinin URL'sini OneDrive içerik aramasini değiştirmeniz gerekir. Daha fazla bilgi için BKZ[. UPN değişiklikleri URL'nin OneDrive etkiler](/onedrive/upn-changes).

## <a name="searching-microsoft-teams-and-microsoft-365-groups"></a>Grupları Microsoft Teams ve Microsoft 365 arama

Bir Microsoft Ekibi veya Grup ekibiyle ilişkilendirilmiş posta kutusunda Microsoft 365. Her Microsoft Teams grupların Microsoft 365 olduğundan, arama benzer. Her iki durumda da, yalnızca grup veya ekip posta kutusunda arama yapıldı. Grubun veya ekip üyelerinin posta kutularını aramaz. Bunları aramak için, aramanıza özel olarak eklemeniz gerekir.

GrupLarda ve Gruplarda içerik ararken Microsoft Teams Microsoft 365 göz Microsoft 365 kullanın.

- Teams ve Microsoft 365 Grupları'nda bulunan içeriği aramak için, posta kutusunu ve ekip veya grupla SharePoint ilgili posta kutusunu ve posta kutusunu belirtmeniz gerekir.

- Özel kanallardan gelen içerikler ekip posta kutusunda değil, her kullanıcının posta kutusunda depolanır. Özel kanallarda içerik aramak için bkz. [Özel ve paylaşılan kanalların eBulma](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

- Bir ekibin veya bir Exchange Online Grubunun özelliklerini görüntülemek için **Get-UnifiedGroup** cmdlet'ini Microsoft 365 çalıştırın. Bu, ekip veya grupla ilişkilendirilmiş sitenin URL'sini almak için iyi bir yol sağlar. Örneğin, aşağıdaki komut, Üst Düzey Liderlik Ekibi adlı bir Microsoft 365 özellikler görüntüler:

  ```text
  Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
  DisplayName            : Senior Leadership Team
  Alias                  : seniorleadershipteam
  PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
  SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
  ```

    > [!NOTE]
    > **Get-UnifiedGroup** cmdlet'ini çalıştırmak için, Exchange Online'te View-Only Alıcıları rolüne atanmış bir rol grubuna ya da View-Only Alıcılar rolüne atanmış bir rol grubuna üye View-Only gerekir.

- Kullanıcının posta kutusunda arama geldiğinde, kullanıcının üyesi olduğu Microsoft 365 veya Arama Grubu aranmaz. Benzer şekilde, bir ekip veya grup Microsoft 365 aramada, yalnızca belirttiğiniz grup posta kutusu ve grup sitesinde arama olur. Grup OneDrive İş posta kutuları ve grup üyelerinin posta kutularına, açıkça eklemedikçe hiçbir şeyi aramaz.

- Bir ekibin veya bir Grup üyesinin listesini Microsoft 365 için özellikleri, ekip **sayfasındaki Giriş** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupları Microsoft 365 yönetim merkezi**</a>. Alternatif olarak, Exchange Online PowerShell'de aşağıdaki Exchange Online çalıştırabilirsiniz:

  ```powershell
  Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
  ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'de View-Only Alıcıları rolüne atanmış bir rol grubuna ya da View-Only Alıcılar rolüne atanmış bir rol grubuna üye View-Only gerekir.

- Bir kanalın parçası olan Teams, ekiple ilişkilendirilmiş posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin bir kanalda paylaştığı dosyalar da ekibin SharePoint depolanır. Bu nedenle, bir kanalda konuşmaları ve dosyaları aramak SharePoint için ekip posta kutusunu ve siteyi içerik konumu olarak eklemeniz gerekir.

- Alternatif olarak, Teams'daki Sohbet listesinin bir parçası olan konuşmalar Exchange Online katılan kullanıcıların kendi posta kutusunda saklanır. Sohbet görüşmelerde kullanıcının paylaştığı dosyalar ise dosyayı paylaşan OneDrive İş hesaplarında depolanır. Bu nedenle sohbet listesinde konuşmaları ve dosyaları aramak için tek OneDrive İş posta kutularını ve kullanıcı hesaplarını içerik konumu olarak eklemeniz gerekir.

    > [!NOTE]
    > Karma Exchange dağıtımda, şirket içi posta kutusu olan kullanıcılar şirket içi sohbet listesinde yer alan konuşmalara Teams. Bu durumda, şirket içi posta kutusu olan kullanıcılar için bulut tabanlı bir depolama alanına (şirket içi kullanıcılar için bulut tabanlı posta kutusu olarak *adlandırılan)* kaydedildiklerinden bu konuşmaların içeriğinde de arama gerçekleştirilebilir. Daha fazla bilgi için [bkz. Teams kullanıcıların sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

- Her ekip veya ekip kanalı not alma ve işbirliği için bir Wiki içerir. Wiki içeriği .mht biçimindeki bir dosyaya otomatik olarak kaydedilir. Bu dosya, ekibin Teams sitenin Wiki Verileri belge kitaplığında SharePoint depolanır. Wiki'de arama yapmak için içerik konumu olarak ekibin SharePoint sitesini belirterek İçerik Arama aracını kullanabilirsiniz.

    > [!NOTE]
    > Wiki'de ekip veya kanal arama özelliği (ekibin web sitesinde arama SharePoint) 22 Haziran 2017'de yayınlandı. Bu tarihte veya daha sonra kaydedilen ya da güncellenen wiki sayfalarında arama yapılamaz. Bu tarihten önce kaydedilen veya güncelleştirilen wiki sayfalarında arama yapılamaz.

- Bir kanalda yapılan toplantılar ve Teams özet bilgileri, toplantıya veya aramaya arayarak bağlanılan kullanıcıların posta kutularında da depolanır. Bu, bu özet kayıtlarında arama yapmak için İçerik Arama'nın kullanabileceğiniz anlamına gelir. Özet bilgiler şunları içerir:

  - Toplantı veya aramanın tarihi, başlangıç saati, bitiş saati ve süresi

  - Her katılımcının toplantıya veya aramadan ayrıldığı tarih ve saat

  - Sesli postaya gönderilen aramalar

  - Yanıtsız veya yanıtsız aramalar

  - İki ayrı çağrı olarak temsil edilen arama aktarımları

  Toplantı ve arama özeti kayıtlarının aranma bilgileri 8 saate kadar sürebilir.

  Arama sonuçlarında, toplantı özetleri Tür alanında Toplantı olarak **ve** arama özetleri de Arama olarak **tanımlanır**. Ayrıca, bir Teams ve 1xN sohbetlerinin parçası olan konuşmalar, Tür alanında **IM** **olarak** tanımlanır.

  ![Teams, arama ve 1xN sohbetleri Tür alanında tanımlanır.](../media/O365-ContentSearch-Teams-MessageKind.png)

   Daha fazla bilgi için bkz [Microsoft Teams aramalar ve toplantılar için eKbulma'ı başlatma.](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-launches-ediscovery-for-calling-and-meetings/ba-p/210947)

- Farklı kanallarda uygulamalar tarafından Teams, 1:1 sohbetler ve 1xN sohbetlerde oluşturulan kart içeriği posta kutularında depolanır ve arama da olabilir. Kart *,* içeriğin kısa parçaları için bir kullanıcı arabirimi kapsayıcısıdır. Kartların birden çok özelliği ve eki olabilir ve kart eylemlerini tetikleyen düğmeler içerebilir. Daha fazla bilgi için bkz. [Kartlar](/microsoftteams/platform/task-modules-and-cards/what-are-cards)

  Diğer Teams gibi, kart içeriğinin depolandığı yer de kartın kullanılmış olduğu yere göre olur. Bir kanalda kullanılan kartların Teams, grup posta Teams depolanır. 1:1 ve 1xN sohbetler için kart içeriği sohbet katılımcılarının posta kutularında depolanır.

  Kart içeriği aramak için veya arama koşullarını `kind:microsoftteams` kullanabilirsiniz `itemclass:IPM.SkypeTeams.Message` . Arama sonuçlarını gözden geçirerek bir Teams kanalında botlar tarafından oluşturulan kart içeriğinde **Sender/Author e-posta** `<appname>@teams.microsoft.com``appname` özelliği vardır; burada kart içeriğini oluşturan uygulamanın adı yer alır. Kart içeriği bir kullanıcı tarafından oluşturulmuşsa, Gönderen **/Yazar değeri kullanıcıyı** tanımlar.

  İçerik arama sonuçlarında kart içeriği görüntülenirken, içerik iletiye ek olarak görünür. Ekin adı `appname.html`, burada `appname` kart içeriğini oluşturan uygulamanın adıdır. Aşağıdaki ekran görüntüleri, kart içeriğinin (Asana adlı bir uygulama için) dosya Teams arama sonuçları içinde nasıl göster göstermektedir.

  **Kart içeriği Teams**

  ![Kanal mesajında Teams içeriği.](../media/CardContentTeams.png)

  **Arama sonuçlarında kart içeriği**

  ![İçerik arama sonuçlarında aynı kart içeriği.](../media/CardContentEdiscoverySearchResults.png)

  > [!NOTE]
  > Şu anda arama sonuçlarında kart içeriğinden resimler görüntülemek için (önceki ekran görüntüsünde yer alan onay işaretleri gibi), Teams'da oturum açmalısınız (https://teams.microsoft.com)arama sonuçlarını görüntülemek için aynı tarayıcı oturumunda farklı bir sekmede). Aksi takdirde, resim yer tutucuları görüntülenir.

- İletide özel olarak **içerik** aramak için Tür **e-posta özelliğini** veya İleti türü arama Teams.

  - Tür özelliğini **anahtar** sözcük arama sorgusunun parçası olarak kullanmak için, arama **sorgusunun Anahtar** Sözcükler kutusuna yazın `kind:microsoftteams`.

    ![Anahtar sözcükler kutusunda tür:microsoftteams kullanın.](../media/O365-ContentSearch-Teams-Keywords.png)

  - Arama koşulu kullanmak için İletinin tür **koşullarını ekleyin** ve değerini kullanın `microsoftteams`.

    ![Microsoftteams değeriyle İleti tür koşulunu kullanın.](../media/O365-ContentSearch-Teams-MessageKindCondition.png)

   Koşullar, AND işleci tarafından anahtar sözcük sorgusuna **mantıksal olarak** bağlanır. Bu, bir öğenin arama sonuçlarında döndürülecek anahtar sözcük sorgusuyla ve arama koşuluyla eşleşmesi gereken anlamına gelir. Daha fazla bilgi için Anahtar sözcük sorguları ve İçerik Arama için arama koşulları'nın "Koşulları kullanma [yönergeleri" bölümüne bakın.](keyword-queries-and-search-conditions.md#guidelines-for-using-conditions)

## <a name="searching-yammer-groups"></a>Gruplarda Yammer arama

Gruplarda özel olarak **konuşma öğelerini** aramak için ItemClass  e-posta özelliğini veya Tür arama Yammer kullanabilirsiniz.

  - **ItemClass** özelliğini anahtar sözcük arama sorgusunun parçası olarak kullanmak için, arama sorgusunun  Anahtar Sözcükler kutusuna aşağıdaki özellik:değer çiftlerinin birini (veya hepsini) yazın:

     - ItemClass:IPM.Yammer.message
     - ItemClass:IPM.Yammer.poll
     - ItemClass:IPM.Yammer.praise
     - ItemClass:IPM.Yammer.question

    Örneğin, şu arama sorgusunu kullanarak iletileri geri Yammer övgü Yammer kullanabilirsiniz:

    ![Daha büyük öğeleri aramak için ItemClass Yammer kullanın.](../media/YammerContentSearch1.png)

  - Alternatif olarak, E-posta yazın **koşullarını kullanabilir** ve **iletilerin Yammer dönerek** e-postaların Yammer de olabilir. Örneğin, aşağıdaki arama sorgusu "gizli" Yammer sözcüklerini içeren tüm arama öğelerinin tüm sorgularını geri dönecektir.

    ![Konuşma öğelerini aramak için Tür Yammer kullanın.](../media/YammerContentSearch2.png)

## <a name="searching-inactive-mailboxes"></a>Etkin olmayan posta kutularını arama

İçerik aramalarında etkin olmayan posta kutularında aramaabilirsiniz. Kurumdaki etkin olmayan posta kutularının listesini almak için, PowerShell'de bu `Get-Mailbox -InactiveMailboxOnly` Exchange Online çalıştırın. Alternatif olarak, Güvenlik ve Uyumluluk **Merkezi'nde** \> Bilgi yönetimi Bekletme'& ve ardından **Daha**![ FazlaGizleme Çubuğu üç nokta'ya tıklayabilirsiniz.](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) \>**Etkin olmayan posta kutuları**.

Etkin olmayan posta kutularında arama ararken gözlerde tutmanız gereken birkaç şey vardır.

- Var olan içerik aramalarında bir kullanıcı posta kutusu varsa ve bu posta kutusu etkin değil olarak yapılıyorsa, içerik arama özelliği etkin olmayan duruma geldiğinde yeniden arama yapmaya devam eder.

- Bazen kullanıcının etkin bir posta kutusu ve aynı SMTP adresine sahip etkin olmayan bir posta kutusu olabilir. Bu durumda, yalnızca içerik arama konumu olarak belirli posta kutusunda arama yapılanlar aranır. Başka bir deyişle, aramaya bir kullanıcının posta kutusunu eklerken, hem etkin hem de etkin olmayan posta kutularında arama olduğunu varsaymayabilirsiniz. Yalnızca aramaya açıkça eklemek istediğiniz posta kutusunda arama olur.

- Etkin olmayan bir posta & içerik araması oluşturmak için Güvenlik ve Uyumluluk Merkezi PowerShell'i kullanabilirsiniz. Bunu yapmak için, önceden bir nokta ( . ) etkin olmayan posta kutusunun e-posta adresini girin. Örneğin, aşağıdaki komut etkin olmayan bir posta kutusunda e-posta adresi veya arama pavelb@contoso.onmicrosoft.com:

   ```powershell
   New-ComplianceSearch -Name InactiveMailboxSearch -ExchangeLocation .pavelb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true
   ```

- Etkin bir posta kutusuna ve aynı SMTP adresine sahip etkin olmayan posta kutularına sahip olmaktan kaçınmanızı kesinlikle öneririz. Etkin olmayan bir posta kutusuna atanan SMTP adresini yeniden kullanmanız gerekirse, etkin olmayan posta kutusunu kurtarmanızı veya etkin olmayan posta kutusunun içeriğini etkin bir posta kutusuna (veya etkin bir posta kutusunun arşivini) geri yüklemenizi ve ardından etkin olmayan posta kutusunu silmenizi öneririz. Daha fazla bilgi için aşağıdaki konulardan birini bakın:

  - [E-posta kutusunda etkin olmayan posta Office 365](recover-an-inactive-mailbox.md)

  - [E-posta kutusunda etkin olmayan posta kutusunu Office 365](restore-an-inactive-mailbox.md)

  - [E-posta kutusunda etkin olmayan posta Office 365](delete-an-inactive-mailbox.md)

## <a name="searching-disconnected-or-de-licensed-mailboxes"></a>Bağlantı kesik veya lisansları olmayan posta kutularını arama

Kullanıcı Exchange Online hesabından veya posta kutusundan Microsoft 365 lisansının tamamı) kaldırılırsa, Azure Active Directory kullanıcının posta kutusunun bağlantısı kesilir. Bu, posta kutusunun artık kullanıcı hesabıyla ilişkilendiril olmadığı anlamına gelir. Bağlantısı kesilmiş posta kutularda arama sırasında şöyle olur:

- Posta kutusundan lisans kaldırılırsa, posta kutusunda artık arama kullanılamaz.

- Var olan içerik aramalarında lisansın kaldırıldığı bir posta kutusu varsa, içerik aramasını yeniden çalıştırmanız sonucunda bağlantısı kesik olan posta kutusundan hiçbir arama sonucu döndürül olmaz.

- İçerik araması oluşturmak ve aramanın bağlantı kesik posta kutusunu Exchange içerik konumu olarak belirtmek için Yeni Uyumluluk **arama** cmdlet'ini kullanırsanız, içerik arama bağlantısı kesik posta kutusundan hiçbir arama sonucu dönmez.

Bağlantı kesik posta kutusunda arama yapmak için bu verileri tutmanız gerekirse, lisansı kaldırmadan önce posta kutusunu yerinde tutmanız gerekir. Bu şekilde veriler korunur ve tutma kaldırılana kadar bağlantısı kesik posta kutusunda arama özelliği korunur. Tutma hakkında daha fazla bilgi için bkz. Bir posta [kutusuna yerleştirilen Exchange Online belirleme](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="searching-for-content-in-a-sharepoint-multi-geo-environment"></a>SharePoint Multi-Geo ortamında içerik arama

eBulma yöneticisinin SharePoint [multi-geo](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md) ortamındaki farklı bölgelerde SharePoint ve OneDrive'ta içerik araması gerekiyorsa, bunu yapmak için aşağıdaki şeyleri yapın:

1. eBulma yöneticisinin arama yapmak zorunda olduğu her uydu coğrafi konumu için ayrı bir kullanıcı hesabı oluşturun. Bu coğrafi konumdaki sitelerde içerik aramak için, eBulma yöneticisinin bu konumda oluşturduğunuz hesapta oturum açması ve içerik aramasını çalıştırması gerekir.

2. eBulma yöneticisinin arama yapmak zorunda olduğu her uydu coğrafi konumu (ve buna karşılık gelen kullanıcı hesabı) için bir arama izinleri filtresi oluşturun. Bu arama izinlerinin her biri, eBulma yöneticisi söz konusu konumla ilişkilendirilmiş kullanıcı hesabında oturum alınca içerik aramanın kapsamını belirli bir coğrafi konumla sınırlar.

> [!TIP]
> Arama aracını aynı adreste kullanırken bu stratejiyi [Advanced eDiscovery.](overview-ediscovery-20.md) Bunun nedeni, tüm sitelerde arama SharePoint tüm veri OneDrive arama Advanced eDiscovery. Bölgeye özgü bu kullanıcı hesaplarının stratejisini ve arama izinleri filtrelerini yalnızca İçerik Arama aracını kullanırken ve [eBulma durumleriyle ilişkilendirilmiş aramaları kullanırken kullanasınız](./get-started-core-ediscovery.md).

Örneğin, bir eBulma yöneticisinin Kuzey Amerika, Avrupa ve Asya Pasifik'te uydu konumlarında SharePoint ve OneDrive içeriği araması gerektiğini kabul ediyoruz. İlk adım, her konum için bir hesap olmak olmak zorunda üç kullanıcı hesabı oluşturmaktır. Sonraki adım, her konum ve buna karşılık gelen kullanıcı hesabı için olmak verilen üç arama *izni filtresi* oluşturmaktır. Burada, bu senaryo için üç arama izni filtresine örnek olarak verilmiştir. Bu örneklerin her ikisinde **de Bölge**, SharePoint veri merkezi konumunu belirtir ve **Users** parametresi de buna karşılık gelen kullanıcı hesabını belirtir.

**Kuzey Amerika**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-NAM" -Users ediscovery-nam@contoso.com -Region NAM -Action ALL
```

**Avrupa**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-EUR" -Users ediscovery-eur@contoso.com -Region EUR -Action ALL
```

**Asya Pasifik**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-APC" -Users ediscovery-apc@contoso.com -Region APC -Action ALL
```

Çok coğrafi ortamlarda içerik aramak için arama izinleri filtrelerini kullanırken aşağıdaki şeyleri unutmayın:

- Bölge **parametresi** aramaları belirtilen uydu konuma yönlendirmektedir. eBulma yöneticisi yalnızca arama SharePoint OneDrive dışından arama yaptı ve siteyi ararsa, hiçbir arama sonucu döndürülilmez.

- Bölge **parametresi**, bu posta kutularının Exchange denetlemez. Posta kutularına arama geldiğinde tüm veri merkezlerinde arama olur.

Çok coğrafi ortamda arama izinleri filtrelerini kullanma hakkında daha fazla bilgi için [, eBulma](set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments) soruşturmaları için uyumluluk sınırlarını ayarlama bölümündeki "Multi-Geo ortamlarında içerik arama ve dışarı aktarma" bölümüne bakın.
