---
title: Core eKovery durumunda eKbulma ayrımları oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Bir soruşturma veya davayla ilgili içeriği korumak için Microsoft 365 çekirdek eKbulma durumuyla ilişkilendirilmiş bir tutma oluşturabilirsiniz.
ms.openlocfilehash: 976c0e47195c520620cfa57e996cee42df509593
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63406043"
---
# <a name="create-an-ediscovery-hold"></a>eBulma ayrımı oluşturma

Olayla ilgili olabileceğiniz içeriği korumak üzere bir Core eKbulma durumu oluşturabilirsiniz. Bu durumda, posta Exchange yerinde tutabilir OneDrive İş ve bu olayda araştırıyorsanız kişilerin hesaplarını kullanabilirsiniz. Ayrıca posta kutularını ve sitelerle ilişkilendirilmiş posta kutularını ve siteleri Microsoft Teams Office 365 gruplarına Yammer. İçerik konumlarını yerinde tutarken içerik, siz içeriğin bulunduğu konumu tutmadan kaldırana kadar veya siz tutma konumunu silene kadar korunur.

eBulma ayrımı oluşturdukktan sonra, ayrı ayrı tutmanın etkili bir şekilde 24 saate kadar sürebilir.

Bir tutma  oluşturmada, belirtilen içerik konumlarında korunan içeriğin kapsamını aşağıdaki seçeneklere göre görüntülersiniz:
  
- Belirtilen konumlarda yer alan tüm içeriğin bulunduğu sonsuz bir tutma oluşturun. Alternatif olarak, yalnızca belirtilen konumlarda yer alan ve arama sorgusuyla eşleşen içeriğin yerine basılı tutma için sorgu tabanlı bir tutma oluşturabilirsiniz.

- Yalnızca bu tarih aralığında gönderilmiş, alınan veya oluşturulmuş olan içeriği korumak için bir tarih aralığı belirtin. Alternatif olarak, ne zaman gönderildiğine, alınsa veya oluşturulduktan bağımsız olarak tüm içeriği belirtilen konumlarda tutabilirsiniz.
  
## <a name="how-to-create-an-ediscovery-hold"></a>eBulma ayrımı oluşturma

Çekirdek eBulma durumuyla ilişkilendirilmiş bir eBulma ayrımı oluşturmak için:
  
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Varsayılan'Microsoft 365 uyumluluk merkezi</a> gidin ve uygun eBulma izinleri atanmış olan kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın.

2. Sol gezinti bölmesinde, Hepsini **göster'e tıklayın** ve sonra **da eBulma** Dört > tıklayın.

3. **Core eDiscovery sayfasında**, ayrı tutma için oluşturmak istediğiniz vakanın adını tıklatın.

4. Vakanın  Giriş sayfasında, Bekle **sekmesine** tıklayın.
  
5. Bekle sayfasında **Oluştur'a** **tıklayın**.

6. Tutma **sihirbazını adla** sayfasında, tutma adına bir ad verin, isteğe bağlı bir açıklama ekleyin ve ardından Sonraki'ye **tıklayın**. Tutma adı, kurum içinde benzersiz olmalıdır.

7. Konumları **seçin sihirbazı** sayfasında, yerinde tutmak istediğiniz içerik konumlarını seçin. Posta kutularını, siteleri ve ortak klasörleri yerinde tutabilirsiniz.

    ![Yerinde tutacak içerik konumlarını seçin.](../media/eDiscoveryHoldLocations.png)
  
   1. **Exchange kutularını ayarlama**: Düğmeyi Açık olarak **ayarlayın** ve ardından posta kutularını yerinde tutmak için Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını (grup üyelerinin posta kutularını yerinde tutmak için) yerinde tutmak için arama kutusunu kullanın. Ayrıca, Microsoft Ekibi, Posta Grubu ve Grup Grubu için ilişkili posta Office 365 yerinde Yammer tutabilirsiniz. Posta kutusu saklanan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint:** Sitelerin ve hesapların yerinde basılı SharePoint belirtmek  için iki durum OneDrive  lu düğmeyi Açık SharePoint Siteleri seç'e tıklayın. Yerinde tutmak istediğiniz her sitenin URL'sini yazın. Ayrıca, bir Microsoft Team, SharePoint Grubu veya Bir Ekip Grubu için Office 365 URL'sini Yammer edebilirsiniz.
  
   3. **Exchange klasörleri ayarlama**: Exchange Online klasörünüzdeki tüm ortak klasörleri tutmak  için iki durumlu düğmeyi Açık olarak ayarlayın. Belirli ortak klasörlerin 9'da 9'da 11'inin 11'ini seçesiniz. Ortak klasörlerde  basılı tutmak istemiyorsanız iki durumlu düğmeyi kapalı bırakın.

   > [!IMPORTANT]
   > Bir Exchange posta kutularını veya SharePoint siteyi yerinde tutarken, yerinde tutma için açıkça en az bir içerik konumu eklemeniz gerekir. Başka bir deyişle, posta kutuları veya siteler için iki durumlu düğmeyi Açık olarak ayarladısanız, tutma için belirli posta kutularını veya siteleri seçmeniz gerekir. Aksi takdirde, eBulma ayrımı oluşturulur, ancak bu tutma için hiçbir posta kutusu veya site eklenmez ve istatistikler hiçbir içerik konumunun veya öğenin tutn durumda olmadığını gösterir.

8. Hold'a konum eklemeyi bitirerek, Sonraki'ne **tıklayın**.

9. Anahtar sözcükleri veya koşulları kullanarak sorgu tabanlı bir  tutma oluşturmak için, aşağıdaki adımları tamamlayın. Belirtilen içerik konumlarında yer alan tüm içeriği korumak için, Sonraki'ne **tıklayın**.

    ![Anahtar sözcük ve koşullarla sorgu tabanlı bir tutma oluşturun.](../media/eDiscoveryHoldQuery.png)
  
    1. Anahtar Sözcükler'in **altındaki** kutuya, yalnızca sorgu ölçütleriyle eşleşen içeriği korumak için bir sorgu yazın. Anahtar sözcükleri, e-posta iletisi özelliklerini veya dosya adları gibi site özelliklerini belirtebilirsiniz. Ayrıca, VE, YADA veya NOT gibi Boole işleci **kullanan daha karmaşık** **sorgular da** **kullanabilirsiniz**.

    2. **Sorguyu tutma** için daraltmak istediğiniz bir veya birden çok koşul eklemek için Koşul ekle'ye tıklayın. Her koşul, ayrı tutma oluşturulduğunda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler. Örneğin, tarih aralığı içinde oluşturulmuş e-posta veya site belgelerinin korunması için bir tarih aralığı belirtebilirsiniz. Koşul, AND işleci tarafından anahtar sözcük sorgusuna (Anahtar sözcükler kutusunda **belirtilen** sorgu) ve diğer koşullarla mantıksal **olarak** bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de korunma koşullarını karşılaması gereken anlamına gelir.

    Arama sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz. eBulma için anahtar sözcük sorguları [ve arama koşulları](keyword-queries-and-search-conditions.md).

10. Sorgu tabanlı bir tutma yapılandırdıktan sonra, Sonraki'ne **tıklayın**.

11. Ayarlarınızı gözden geçirin (ve gerekirse düzenleyin) ve sonra Gönder'e **tıklayın**.

> [!NOTE]
> Sorgu tabanlı bir tutma  oluştururken, seçilen konumlardan alınan tüm içerik başlangıçta basılı tutar. Daha sonra, belirtilen sorguyla eşleşmemiş olan içerik her yedi ile 14 günde bir temizlemeyi sağlar. Bununla birlikte, içerik yerine herhangi bir türde beşten fazla 0'dan fazla 10 000 000 000 0000 yer varsa veya herhangi bir öğede dizin oluşturma sorunları varsa, sorgu tabanlı tutma içeriği temizlemez.

## <a name="query-based-holds-placed-on-sites"></a>Sitelere yerleştirilen sorgu tabanlı 10

Bir web sitesi içinde bulunan belgelere sorgu tabanlı bir eBulma  yer değiştirirken aşağıdaki SharePoint göz SharePoint kullanın:

- Sorgu tabanlı bir tutma, başlangıçta sitenin tüm belgelerini silindikten sonra kısa bir süre için korur. Bu, bir belge silindiğinde, sorgu tabanlı saklama ölçütüne eşleşmese bile Saklama kitaplığına taşınacak anlamına gelir. Ancak, sorgu tabanlı saklamayla eşleşmemiş olan silinmiş belgeler, Saklama Kitaplığı'nı işlemeye devam ediyor bir süreölçer işi tarafından kaldırılır. Süreölçer işi düzenli olarak çalışır ve Saklama Kitaplığı'nın tüm belgelerini sorgu tabanlı eKbulma bekletmeleri (ve diğer bekletme ve bekletme ilkeleri türleri) ile karşılar. Süreölçer işi, sorgu tabanlı tutmayla eşleşmeden belgeleri siler ve bunu yapacak belgeleri korur.

- Sorgu tabanlı saklama, belirli bir klasör veya sitedeki belgeleri tutma ya da başka bir konum tabanlı saklama ölçütleri kullanma gibi hedefli saklamayı gerçekleştirmek için kullanılmaması gerekir. Bunu yapmak için size gereken sonuçları elde edemeyen sonuçlar olabilir. Site belgelerini korumak için anahtar sözcükler, tarih aralıkları veya diğer belge özellikleri gibi konum tabanlı olmayan tutma ölçütleri kullanmalarını öneririz.

## <a name="ediscovery-hold-statistics"></a>eBulma tutma istatistikleri

eBulma ayrımı oluşturduktaktan sonra, seçilen tutma için uç sayfada yeni tutma hakkında bilgiler görüntülenir. Bu bilgiler, durumdaki posta kutularının ve sitelerin sayısını ve basılı durumdaki öğelerin toplam sayısı ve boyutu ve tutma istatistiklerinin son hesaplanma zamanı gibi, basılı durumdaki içerikle ilgili istatistikleri içerir. Bu tutma istatistikleri, vakayla ilgili içeriğin korunarak miktarını tanımlamanıza yardımcı olur.
  
![İstatistikleri tutma.](../media/eDiscoveryHoldStatistics.png)
  
eBulma tutma istatistikleri hakkında aşağıdaki bilgileri unutmayın:
  
- Tutmadaki toplam öğe sayısı, tüm içerik kaynaklarından alınan ve bir o kadar da tutuldu olan öğe sayısını gösterir. Sorgu tabanlı bir tutma oluşturduysanız, bu istatistiği sorguyla eşleşmesi için kaç öğe olduğunu gösterir.

- Aynı zamanda, içeriğin konumlarında bulunan, bağımsız olmayan öğeleri de içerir. Sorgu tabanlı bir tutma oluşturursanız, içerik konumlarına yerleştirilemeyen tüm öğeler basılı olarak yerleştirilir. Bu, sorgu tabanlı bir tutmanın arama ölçütleriyle eşleşmemiş, ya da tarih aralığı koşulunun dışında yer alan, ya da tek satırlık olmayan öğeleri içerir. Bu, arama sorgusuyla eşleşmemiş veya tarih aralığı koşulu tarafından dışlanan ya da arama sonuçlarına dahil olmayan, dizisiz öğelerin olduğu bir aramada yapılanlardan farklıdır. Dizine eksiz öğeler hakkında daha fazla bilgi için bkz [. Kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md).

- Tutmadaki öğelerin geçerli sayısını hesapan bir arama tahminini yeniden aramak için İstatistikleri güncelleştir'e tıklayarak en son tutma istatistiklerini eldeebilirsiniz.

- Posta kutusu veya site yerindeki kullanıcılar genellikle yeni e-posta iletisi göndererek veya alırken SharePoint ve OneDrive'ta yeni belgeler gönderdiği için, yerindeki öğelerin sayısının zaman içinde artacak olması normal OneDrive.

- Exchange posta kutusu, SharePoint sitesi veya OneDrive hesabı çok coğrafi bir ortamda farklı bir bölgeye taşınırsa, bu sitenin istatistikleri tutma istatistiklerine dahil edilir. Ancak bu konumlarda bulunan içerik yine de korunur. Ayrıca, posta kutusu veya site farklı bir bölgeye taşınırsa, yerinde aramada görüntülenen SMTP adresi veya URL otomatik olarak güncelleştirilmez. İçerik konumlarını yeniden tutma istatistiklerine dahil etmek için, güncelleştirmeyi ve URL'yi veya SMTP adresini güncelleştirmeniz gerekir

## <a name="search-locations-on-ediscovery-hold"></a>eBulma ayrımı'nın arama konumları

Core eKovery durumunda içerik aramanızı, yalnızca durumla ilişkilendirilmiş bir ayrı tutma durumunda yerleştirilen içerik konumlarında arama yapmak için hızlı şekilde yapılandırabilirsiniz.[](search-for-content-in-core-ediscovery.md)

Basılı **olarak yerleştirilen tüm** içerik konumlarını aramak için Konumda tutuldu seçeneğini belirleyin. Olay birden çok eBulma ayrımı içeriyorsa, bu seçeneği tercih ettiyseniz, tüm beklemelerin içerik konumlarını arayabilirsiniz. Buna ek olarak, içerik konumu sorgu tabanlı bir tutma üzerine yerleştirilse, aramanızı çalıştırsanız yalnızca tutma sorgusuyla aynı olan öğelerde arama olur. Başka bir deyişle, yalnızca hem tutma ölçütleriyle hem de arama ölçütleriyle eşleşen içerik arama sonuçlarıyla döndürülür. Örneğin, bir kullanıcı belirli bir tarihten önce gönderilmiş veya oluşturulmuş olan öğeleri koruyan sorgu tabanlı bir durumda tutma durumuna yerleştirilse, yalnızca bu öğelerde arama gerçek olur. Bu, büyük/harf tutma sorgusuyla arama sorgusunu AND işleciyle birbirine **bağlayarak** başarabilirsiniz.

eBulma ayrımı yapan konumları ararken gözlerde tutma gereken diğer bazı şeyler:

- İçerik konumu aynı durumda birden çok tutmanın parçası ise, tüm büyük/küçük harf içeriği seçeneğini kullanarak içerik konumunu aramanızı onaylarsanız, tutma sorguları **OR** işleçleri tarafından bir araya olur. Benzer şekilde, içerik konumu iki farklı tutmanın parçası ise, bu konum sorgu tabanlı ve diğeri de sonsuz bir tutmadır (tüm içerik sonsuz bir tutma nedeniyle) tüm içerik arama olur.

- Bir arama, ayrı konumda arama yapmak üzere yapılandırılırsa ve bu durumda eBulma ayrım konumunu değiştirirsiniz (konum ekleyerek veya kaldırarak ya da bir tutma sorgusunu değiştirerek), arama yapılandırması bu değişikliklerle güncelleştirilir. Bununla birlikte, arama sonuçlarını güncelleştirmek için, aramada beklendikten sonra yeniden arama çalıştırmayı gerekir.

- Bir eBulma durumunda birden çok eBulma 100 100 anahtar kelimesine sahipse ve bir eBulma durumunda arama konumlarını aramak için bu arama sorgusunun en fazla 500 anahtar sözcük sayısını seçersiniz. Bunun nedeni, aramanın OR işleci kullanarak tüm sorgu tabanlı 100'leri **birleştirmesidir** . Birleştirilmiş tutma sorgularında ve arama sorgusunda 500'den fazla anahtar sözcük varsa, yalnızca sorgu tabanlı büyük/küçük harf tutma ile eşleşen içerikle değil posta kutusunda yer alan tüm içerikte arama yapabilirsiniz.

- eBulma ayrımı durumunda Açık (Beklemede **)** varsa, ayrı tutma açıkken de beklemedeki konumlarda aramaabilirsiniz.

## <a name="preserve-content-in-microsoft-teams"></a>İçerik içeriğini Microsoft Teams

Bir kanalın parçası olan Microsoft Teams, Microsoft Ekibi ile ilişkilendirilmiş posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin bir kanalda paylaştığı dosyalar da ekibin SharePoint depolanır. Bu nedenle, kanalda konuşmaları ve dosyaları SharePoint için Ekip posta kutusunu ve siteyi eBulma'ya alın.

Alternatif olarak, Teams'daki Sohbet listesinin parçası olan konuşmalar (*1:1* sohbetler veya *1:N* grup sohbetleri olarak adlandırılan) sohbete katılan kullanıcıların posta kutularında depolanır. Kullanıcıların sohbet görüşmelerde paylaştığı dosyalar ise, OneDrive paylaşan kullanıcının hesaplarında depolanır. Bu nedenle, sohbet listesinde konuşmaları ve dosyaları OneDrive için tek tek kullanıcı posta kutularını ve kullanıcı hesaplarını eBulma'ya eklemeniz gerekir. Ekip posta kutusunu ve siteyi yerinde tutmanın yanı sıra Microsoft Team üyelerinin posta kutularını da yerinde tutmak iyi bir fikirdir.

> [!NOTE]
> Kuruluşta Exchange karma dağıtımı varsa (veya organizasyonunız şirket içi Exchange kuruluşunu Office 365 ile eşitler) ve Microsoft Teams'i etkinleştirdiyse, şirket içi kullanıcılar Teams sohbet uygulamasını kullanabilir ve bire bir sohbetler ve 1:N grup sohbetleri'ne katılabilir. Bu konuşmalar, şirket içi kullanıcıyla ilişkilendirilmiş bulut tabanlı bir depolamada depolanır. Şirket içi kullanıcı eBulma saklamaya yerleştirilirse, Teams tabanlı depolamada yer alan kullanıcı sohbet içeriği korunur. Daha fazla bilgi için [bkz. Teams kullanıcıların sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

İçeriği koruma hakkında daha fazla Teams için bkz[. Microsoft Teams veya ekibi yasal olarak tutma](/MicrosoftTeams/legal-hold).

### <a name="preserve-card-content"></a>Kart içeriğini koruma

Benzer şekilde, Teams kanallarında uygulamalar tarafından oluşturulan kart içeriği, 1:1 sohbetleri ve 1:N grup sohbetleri posta kutularında depolanır ve bir posta kutusu eBulma ayrımlarına yerleştiril durumlarında korunur. Kart *,* içeriğin kısa parçaları için bir kullanıcı arabirimi kapsayıcısıdır. Kartların birden çok özelliği ve eki olabilir ve kart eylemlerini tetikleyen düğmeler içerebilir. Daha fazla bilgi için bkz. [Kartlar](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Diğer Teams gibi, kart içeriğinin depolandığı yer de kartın kullanılmış olduğu yere göre olur. Bir kanalda kullanılan kartların Teams, grup posta Teams depolanır. 1:1 ve 1xN sohbetler için kart içeriği sohbet katılımcılarının posta kutularında depolanır.

### <a name="preserve-meeting-and-call-information"></a>Toplantı ve arama bilgilerini koruma

Bir grup kanalında yapılan toplantılar ve Teams özet bilgileri, toplantıya veya aramaya arayarak bağlanılan kullanıcıların posta kutularında da depolanır. Bu içerik, kullanıcı posta kutularına eBulma ayrımı yerleştiril olduğunda da korunur.

### <a name="preserve-content-in-private-channels"></a>Özel kanallarda içeriği koruma

Şubat 2020'den başlayarak, özel kanallarda içeriği koruma yeteneğini de kullandık. Özel kanal sohbetleri sohbet katılımcılarının posta kutularında depolandığı için eBulma'ya bir kullanıcı posta kutusu yerleştirilsin, özel kanal sohbetleri korunur. Ayrıca, kullanıcı posta kutusu Şubat 2020'den önce eBulma amaçlı bir tutma durumuna yerleştirilmişse, bu tutma artık posta kutusunda depolanan özel kanal iletileri için de otomatik olarak geçerli olacaktır. Özel kanallarda paylaşılan dosyaların korunması da de desteklemektedir.

### <a name="preserve-wiki-content"></a>Wiki içeriğini koruma

Her Ekip veya ekip kanalında not alma ve işbirliği için bir Wiki de yer almaktadır. Wiki içeriği .mht biçimindeki bir dosyaya otomatik olarak kaydedilir. Bu dosya, ekibin Teams sitenin Wiki Verileri belge kitaplığında SharePoint depolanır. Ekibin web sitesini eBulma tutma SharePoint ekleyerek wiki içeriğini koruyabilirsiniz.

> [!NOTE]
> Ekip veya ekip kanalının Wiki içeriğini koruma özelliği (ekibin SharePoint sitesini yerinde tutabilirsiniz) 22 Haziran 2017'de yayınlanacak. Bir ekip sitesi yerinde basılı tutarsa Wiki içeriği, o tarihten itibaren korunur. Ancak bir ekip sitesi yerinde saklanacaksa ve Wiki içeriği 22 Haziran 2017'den önce silinmişse Wiki içeriği korunmaz.

### <a name="office-365-groups"></a>Office 365 Grupları

Teams Grupları'Office 365 yerleşiktir. Bu nedenle, Office 365 Grupların eBulma'ya yerleştirilmesi, içeriğin Teams yerleştirilmesine benzer.

eBulma'da Gruplara hem Teams hem de Office 365 aşağıdaki şeyleri unutmayın:

- Daha önce de açıklanmıştır; Teams grupların Office 365 yerinde bulunan içeriği yerinde tutmak için, posta kutusunu ve bir grup veya ekiple SharePoint ilgili posta kutusunu ve siteyi belirtmeniz gerekir.

- **Get-UnifiedGroup** cmdlet'ini [Exchange Online Ve](/powershell/exchange/connect-to-exchange-online-powershell) Grupları Yönet cmdlet'inde Teams görüntülemek Office 365 çalıştırın. Bu, bir Ekip veya Ekip Grubu ile ilişkilendirilmiş sitenin URL'sini almak için Office 365 olur. Örneğin, aşağıdaki komut Üst Düzey Liderlik Ekibi adlı bir Office 365 için seçilen özellikleri görüntüler:

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > **Get-UnifiedGroup** cmdlet'ini çalıştırmak için, Exchange Online'te View-Only Alıcıları rolüne atanmış bir rol grubuna ya da View-Only Alıcılar rolüne atanmış bir rol grubuna üye View-Only gerekir. 
  
- Kullanıcının posta kutusunda arama geldiğinde, kullanıcının üyesi olduğu Office 365 Ekip veya Ekip Grubu aranmaz. Benzer şekilde, bir Ekip veya Grup Office 365 eBulma yerinde tutarken, yalnızca grup posta kutusu ve grup sitesi yerinde bekleyin. eBulma OneDrive İş açıkça eklemedikçe, grup üyelerinin posta kutuları ve grup üyelerine ilişkin sitelerde yer alan hiçbir şey yerine yerleştirilmemiştir. Bu nedenle bir Ekip veya Grup Office 365'i yasal bir nedenle yerinde tutmanız gerekirse posta kutularını ve ekip veya grup OneDrive hesaplarını aynı yerde tutabilirsiniz.

- Bir Ekip veya Ekip Grubu Office 365 üyelerinin listesini almak için, özellikler çalışma sayfasındaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Gruplar Microsoft 365 yönetim merkezi**</a>. Alternatif olarak, Exchange Online PowerShell'de aşağıdaki Exchange Online çalıştırabilirsiniz:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'de View-Only Alıcıları rolüne atanmış bir rol grubuna ya da View-Only Alıcılar rolüne atanmış bir rol grubuna üye View-Only gerekir.

## <a name="preserve-content-in-onedrive-accounts"></a>Yeni hesaplarda OneDrive koruma

eBulma durumuyla ilişkilendirilmiş bir tutma veya aramalara eklemek için OneDrive İş sitelerinin listesini toplamak için bkz. Tüm OneDrive konumların listesini [oluşturma](/onedrive/list-onedrive-urls). Bu makaledeki betik, tüm iş sitelerinin listesini içeren bir OneDrive dosyası oluşturur. Bu betiği çalıştırmak için, Çevrimiçi Yönetim Kabuğu'SharePoint ve kullananız gerekir. Arama yapmak istediğiniz her sitenin URL'sini, OneDrive Sitem etki alanının URL'sini eklemeye emin olun. Bu, tüm etki alanlarınızı içeren OneDrive, örneğin. `https://contoso-my.sharepoint.com` İşte, kullanıcının site için bir URL OneDrive: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> Bir kullanıcının anapara hesabının URL'si OneDrive asıl adını (UPN) içerir (örneğin, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Nadiren de olsa kişinin UPN'si değiştirilirse, URL'leri OneDrive UPN'yi de dahil etmek için değişir. Kullanıcının OneDrive hesabı eBulma ayrım kapsamında ise, eski ve UPN'si değiştirilmişse, ayrımı güncelleştirmeniz ve kullanıcının yeni ONEDRIVE URL'sini eklemeniz ve eskisinin URL'sini kaldırmanız gerekir. Daha fazla bilgi için BKZ[. UPN değişiklikleri URL'nin OneDrive etkiler](/onedrive/upn-changes).

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>eBulma ayrımlarından içerik konumlarını kaldırma

Posta kutusu, SharePoint sitesi veya OneDrive hesabı eBulma yerinde tutmadan kaldırıldıktan sonra, *gecikme* süresi uygulanır. Bu, verilerin içerik konumdan kalıcı olarak silinmesini (temizlemesini) önlemek için, fiili olarak 30 gün ertelenmiş olduğu anlamına gelir. Bu, yöneticilere eBulma tutma kaldırıldıktan sonra temizılacak içeriği arama veya kurtarma fırsatı verir. Posta kutuları ve siteler için gecikmenin nasıl çalıştığının ayrıntıları farklıdır.

- **Posta Kutuları:** Yönetilen Klasör Yardımcısı bu posta kutusunu bir sonraki kez işlemesi ve eBulma tutma işleminin kaldırılmış olduğunu algılayan bir gecikme süresi posta kutusuna yerleştirilir. Özel olarak, Yönetilen Klasör Yardımcısı aşağıdaki posta kutusu özelliklerden birini True olarak ayarlarsa, posta kutusuna gecikme ayrımı **uygulanır**:

   - **DelayHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan e-postayla ilgili (Outlook ve Web üzerinde Outlook kullanan kişiler tarafından oluşturulan içerik) için geçerlidir.

   - **DelayReleaseHoldApplied:** Bu özellik kullanıcının posta kutusunda depolanan bulut tabanlı içerik (Microsoft Teams, Microsoft Forms ve Microsoft Yammer gibi Outlook olmayan uygulamalar tarafından oluşturulmuş) için geçerlidir. Microsoft uygulaması tarafından oluşturulan bulut verileri normalde kullanıcının posta kutusunda gizli bir klasörde depolanır.

   Posta kutusuna gecikme süresi yerleştirilse (önceki özelliklerden biri **True** olarak ayarlanmışsa), posta kutusunun mahkeme nedeniyle tutma süresi boyunca olduğu kabul edilir. 30 gün sonra, gecikme nedeniyle tutma süresi dolar ve Microsoft 365, tutmanın kaldırılması için gecikme süresini (DelayHoldApplied veya DelayReleaseHoldApplied özelliğini **False** olarak ayararak) otomatik olarak kaldırmayı denecektir. Bu özelliklerden herhangi biri **False** olarak ayar kullandıktan sonra, posta kutusu Yönetilen Klasör Yardımcısı tarafından bir sonraki işlemde, kaldırma için işaretlenmiş ilgili öğeler temizlenir.

   Daha fazla bilgi için bkz [. Posta kutularını gecikmeli tutmada yönetme](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **SharePoint OneDrive siteleri:** Saklama Kitaplığı'SharePoint bulunan SharePoint veya OneDrive içerikleri, site eBulma saklama nedeniyle kaldırıldıktan sonra 30 günlük gecikme süresince silinmez. Bu, sitenin bekletme ilkesinden çıkarlı olduğu durumlara benzer. Ayrıca, 30 günlük gecikme süresi boyunca Saklama kitaplığında bu içeriği el ile silemezsiniz. 

   Daha fazla bilgi için bkz [. Bekletme için ilke bırakma](retention.md#releasing-a-policy-for-retention).

Ayrıca Core eKovery olay kapatılan içerik konumlara gecikmeli olarak uygulanır, çünkü bir vaka kapatılanda tutma kapalıdır. Vakayı kapatma hakkında daha fazla bilgi için bkz. [Temel eBulma olaylarını kapatma, yeniden açma ve silme](close-reopen-delete-core-ediscovery-cases.md).

## <a name="ediscovery-hold-limits"></a>eKbulma tutma sınırları

Aşağıdaki tabloda eBulma davaları ve vaka ayrımları için sınırlar listelemektedir.

  | Sınırın açıklaması | Sınır |
  |:-----|:-----|
  |Bir kuruluş için en fazla vaka sayısı.  <br/> |Sınır yok  <br/> |
  |Kuruluş için eBulma tutma ilkelerinin sayısı üst sayısı. Bu sınır, Core eKovery ve Advanced eDiscovery durumlarında birleştirilmiş toplam tutma Advanced eDiscovery içerir.  <br/> |10.0001<sup></sup>  <br/> |
  |Tek bir eBulma ayrımsinde en fazla posta kutusu sayısı. Bu sınır, birleştirilmiş toplam kullanıcı posta kutusu ve Kullanıcı Grupları, Posta Microsoft 365, Posta Kutusu Microsoft Teams posta Yammer içerir.  <br/> |1,000  <br/> |
  |Tek bir eBulma ayrımlarında en fazla site sayısı. Bu sınır, birleştirilmiş toplam OneDrive İş sitesi, SharePoint sitesi ve Microsoft 365 Grupları, Site Grupları, Microsoft Teams ve Yammer içerir.  <br/> |100  <br/> |
  |eBulma giriş sayfasında görüntülenen vaka sayısı üst sayısı ve olaydaki 10/1000 ve Üzerinde Arama ve Dışarı Aktar sekmelerinde görüntülenen en fazla öğe sayısı.  |1.0002<sup></sup>|
  |||

   > [!NOTE]
   > <sup>1</sup> Tek tutma ilkesinde 1.000'den fazla posta kutusunu veya 100 siteyi yerine koyarak, sistem gerektiğinde tutma ölçeğini otomatik olarak ölçeklendirin. Bu, sistemin veri konumlarını tek bir tutma ilkesine eklemek yerine, birden çok tutma ilkesine otomatik olarak ekley sayılır. Bununla birlikte, kuruluş başına 10.000 vaka tutma politikası sınırı yine de geçerlidir.
   >
   > <sup>2</sup> 1.000'den fazla olay, 1000'den fazla vaka, arama veya dışarı aktarmanın listesini görüntülemek için ilgili Güvenlik ve Uyumluluk & PowerShell cmdlet'ini kullanabilirsiniz:
   >
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)
