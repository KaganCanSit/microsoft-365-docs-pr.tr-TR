---
title: eBulma (Standart) durumunda eBulma tutmaları oluşturma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Bir soruşturma veya yasal davayla ilgili içeriği korumak için Microsoft 365 bir eBulma (Standart) olayıyla ilişkili bir ayrı tutma oluşturabilirsiniz.
ms.openlocfilehash: ddd1b2e62c2ec63dbd2303cadcef6a1d12f4dfc7
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130921"
---
# <a name="create-an-ediscovery-hold"></a>eBulma ayrı tutma oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Servis talebiyle ilgili olabilecek içeriği korumak üzere ayrı tutmalar oluşturmak için Microsoft Purview eBulma (Standart) servis talebi kullanabilirsiniz. Olayda araştırdığınız kişilerin Exchange posta kutularına ve OneDrive İş hesaplarına ayrı tutabilirsiniz. Ayrıca, Microsoft Teams, Office 365 Grupları ve Yammer Grupları ile ilişkili posta kutularına ve sitelere ayrı tutabilirsiniz. İçerik konumlarını ayrı tutarak yerleştirdiğinizde, içerik konumu ayrı tutmadan kaldırılana kadar veya siz saklamayı silene kadar içerik korunur.

Bir eBulma ayrı tutması oluşturduktan sonra ayrı tutmanın etkili olması 24 saat kadar sürebilir.

Ayrı tutma oluşturduğunuzda, belirtilen içerik konumlarında korunan içeriğin kapsamını belirlemeye ilişkin aşağıdaki seçeneklere sahip olursunuz:
  
- Belirtilen konumlardaki tüm içeriğin ayrı tutulduğu sonsuz bir ayrı tutma oluşturun. Alternatif olarak, yalnızca belirtilen konumlardaki bir arama sorgusuyla eşleşen içeriğin beklemeye alındığı sorgu tabanlı bir ayrı tutma oluşturabilirsiniz.

- Yalnızca bu tarih aralığında gönderilen, alınan veya oluşturulan içeriği korumak için bir tarih aralığı belirtin. Alternatif olarak, ne zaman gönderildiğine, alındığına veya oluşturulduğuna bakılmaksızın tüm içeriği belirtilen konumlarda tutabilirsiniz.
  
## <a name="how-to-create-an-ediscovery-hold"></a>eBulma ayrı tutma oluşturma

eBulma (Standart) olayıyla ilişkili bir eBulma tutması oluşturmak için:
  
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalına</a> gidin ve uygun eBulma izinlerine atanmış kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın.

2. Sol gezinti bölmesinde **Tümünü göster'e** tıklayın ve ardından **eBulma > Çekirdeği'ne** tıklayın.

3. **eBulma (Standart)** sayfasında, ayrı tutmayı oluşturmak istediğiniz servis talebinin adına tıklayın.

4. Servis talebi için **Giriş** sayfasında **Ayrı Tut** sekmesine tıklayın.
  
5. **Ayrı Tut** sayfasında **Oluştur'a** tıklayın.

6. **Ayrı tutma sihirbazınızı adlandırın** sayfasında, ayrı tutmaya bir ad verin ve isteğe bağlı bir açıklama ekleyin ve **ardından İleri'ye** tıklayın. Ayrı tutmanın adı kuruluşunuzda benzersiz olmalıdır.

7. **Konum seçme** sihirbazı sayfasında, beklemeye almak istediğiniz içerik konumlarını seçin. Posta kutularını, siteleri ve ortak klasörleri ayrı tutabilirsiniz.

    ![Ayrı tutulacak içerik konumlarını seçin.](../media/eDiscoveryHoldLocations.png)
  
   1. **posta kutularını Exchange**: İki durumlu düğmeyi **Açık** olarak ayarlayın ve ardından **Kullanıcıları, grupları veya ekipleri seç'e** tıklayarak beklemeye eklenecek posta kutularını belirtin. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın (grup üyelerinin posta kutularına ayrı tutma yerleştirmek için). Ayrıca microsoft ekibi, Office 365 Grubu ve Yammer Grubu için ilişkili posta kutusuna ayrı tutabilirsiniz. Posta kutusu beklemeye alındığında korunan uygulama verileri hakkında daha fazla bilgi için bkz. [eBulma için posta kutularında depolanan içerik](what-is-stored-in-exo-mailbox.md).

   2. **siteleri SharePoint**: İki durumlu düğmeyi **Açık** olarak ayarlayın ve ardından **Siteleri seç'e** tıklayarak SharePoint siteleri ve OneDrive hesapları beklemeye alacak şekilde belirtin. Beklemeye almak istediğiniz her sitenin URL'sini yazın. Microsoft Ekibi, Office 365 Grubu veya Yammer Grubu için SharePoint sitesinin URL'sini de ekleyebilirsiniz.
  
   3. **Ortak klasörleri Exchange**: Exchange Online kuruluşunuzdaki tüm ortak klasörleri beklemeye almak için iki durumlu düğmeyi **Açık** olarak ayarlayın. Beklemeye almak için belirli ortak klasörleri seçemezsiniz. Ortak klasörleri bekletmek istemiyorsanız iki durumlu düğmeyi kapalı bırakın.

   > [!IMPORTANT]
   > Ayrı tutmaya Exchange posta kutuları veya SharePoint siteleri eklerken, ayrı tutmaya açıkça en az bir içerik konumu eklemeniz gerekir. Başka bir deyişle, posta kutuları veya siteler için iki durumlu düğmeyi **Açık** olarak ayarlarsanız, ayrı tutmaya eklemek üzere belirli posta kutularını veya siteleri seçmeniz gerekir. Aksi takdirde, eBulma ayrı tutması oluşturulur, ancak ayrı tutmaya hiçbir posta kutusu veya site eklenmez.

8. Ayrı tutmaya konum eklemeyi bitirdiğinizde **İleri'ye** tıklayın.

9. Anahtar sözcükleri veya koşulları kullanarak sorgu tabanlı ayrı tutma oluşturmak için aşağıdaki adımları tamamlayın. Belirtilen içerik konumlarındaki tüm içeriği korumak için **İleri'ye** tıklayın.

    ![Anahtar sözcük ve koşullarla sorgu tabanlı bir ayrı tutma oluşturun.](../media/eDiscoveryHoldQuery.png)
  
    1. Anahtar Sözcükler altındaki kutuya, yalnızca sorgu **ölçütleriyle** eşleşen içeriği korumak için bir sorgu yazın. Anahtar sözcükleri, e-posta iletisi özelliklerini veya dosya adları gibi site özelliklerini belirtebilirsiniz. Ayrıca **VE**, **OR** veya **NOT** gibi boole işleci kullanan daha karmaşık sorgular da kullanabilirsiniz.

    2. Ayrı tutma sorgusunu daraltmak üzere bir veya daha fazla koşul eklemek için **Koşul ekle'ye** tıklayın. Her koşul, ayrı tutma oluşturduğunuzda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler. Örneğin, tarih aralığı içinde oluşturulan e-posta veya site belgelerinin korunması için bir tarih aralığı belirtebilirsiniz. Koşul, anahtar sözcük sorgusuna ( **Anahtar Sözcükler** kutusunda belirtilir) ve **AND** işleci tarafından diğer koşullara mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de korunacak koşulu karşılaması gerektiğini gösterir.

    Arama sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

10. Sorgu tabanlı ayrı tutmayı yapılandırdıktan sonra **İleri'ye** tıklayın.

11. Ayarlarınızı gözden geçirin (ve gerekirse düzenleyin) ve **gönder'e** tıklayın.

> [!NOTE]
> Sorgu tabanlı ayrı tutma oluşturduğunuzda, seçilen konumlardaki tüm içerik başlangıçta beklemeye alınır. Daha sonra, belirtilen sorguyla eşleşmeyen tüm içerikler her yedi ila 14 günde bir ayrı tutmadan temizlenir. Ancak, bir içerik konumuna herhangi bir türde beşten fazla ayrı tutma uygulandığında veya herhangi bir öğede dizin oluşturma sorunları varsa sorgu tabanlı ayrı tutma içeriği temizlemez.

## <a name="query-based-holds-placed-on-sites"></a>Sitelere yerleştirilen sorgu tabanlı tutmalar

SharePoint sitelerde bulunan belgelere sorgu tabanlı eBulma ayrılığı yerleştirdiğinizde aşağıdakileri göz önünde bulundurun:

- Sorgu tabanlı ayrı tutma başlangıçta sitedeki tüm belgeleri silindikten sonra kısa bir süre korur. Başka bir deyişle, bir belge silindiğinde sorgu tabanlı saklama ölçütlerine uymasa bile Koruma Bekletme kitaplığına taşınacaktır. Ancak, sorgu tabanlı ayrı tutmayla eşleşmeyen silinen belgeler, Koruma Bekletme kitaplığını işleyen bir zamanlayıcı işi tarafından kaldırılır. Zamanlayıcı işi düzenli aralıklarla çalışır ve Koruma Bekletme kitaplığındaki tüm belgeleri sorgu tabanlı eKeşif tutmalarınızla (ve diğer saklama ve saklama ilkeleri türleriyle) karşılaştırır. Zamanlayıcı işi, sorgu tabanlı ayrı tutmayla eşleşmeyen belgeleri siler ve eşleşen belgeleri korur.

- Belirli bir klasör veya sitedeki belgeleri korumak veya diğer konum tabanlı saklama ölçütlerini kullanmak gibi hedeflenen korumayı gerçekleştirmek için sorgu tabanlı tutmalar kullanılmamalıdır. Bunun yapılması istenmeyen sonuçlara neden olabilir. Site belgelerini korumak için anahtar sözcükler, tarih aralıkları veya diğer belge özellikleri gibi konum tabanlı olmayan saklama ölçütleri kullanmanızı öneririz.

## <a name="search-locations-on-ediscovery-hold"></a>eBulma ayrı tutmada arama konumları

eBulma (Standart) durumunda [içerik aradığınızda](search-for-content-in-core-ediscovery.md) , aramayı hızlı bir şekilde yalnızca servis talebiyle ilişkili ayrı tutma konumuna yerleştirilmiş içerik konumlarında arama yapacak şekilde yapılandırabilirsiniz.

Beklemeye alınmış tüm içerik konumlarında arama yapmak için Beklemedeki **konumlar** seçeneğini belirleyin. Servis talebi birden çok eBulma ayrı tutması içeriyorsa, bu seçeneği belirlediğinizde tüm ayrı tutmalardaki içerik konumları aranacaktır. Buna ek olarak, bir içerik konumu sorgu tabanlı ayrı tutmaya yerleştirilmişse, aramayı çalıştırdığınızda yalnızca ayrı tutma sorgusuyla eşleşen öğeler aranacaktır. Başka bir deyişle, arama sonuçlarıyla yalnızca hem ayrı tutma ölçütleriyle hem de arama ölçütleriyle eşleşen içerik döndürülür. Örneğin, bir kullanıcı belirli bir tarihten önce gönderilmiş veya oluşturulmuş öğeleri koruyan sorgu tabanlı servis talebi saklamaya yerleştirilmişse, yalnızca bu öğeler aranır. Bu, servis talebi saklama sorgusunu ve arama sorgusunu bir **AND** işleci tarafından bağlayarak gerçekleştirilir.

eKeşif ayrı tutmada konumları ararken göz önünde bulundurmak istediğiniz diğer bazı noktalar şunlardır:

- İçerik konumu aynı durumda birden çok ayrı tutmanın parçasıysa, tüm servis talebi içerik seçeneğini kullanarak içerik konumunda arama yaptığınızda, bekletme sorguları **OR** işleçleri tarafından birleştirilir. Benzer şekilde, bir içerik konumu iki farklı ayrı tutmanın parçasıysa ve biri sorgu tabanlı, diğeri sonsuz ayrı tutma ise (tüm içeriğin ayrı tutulduğu yer), tüm içerik sonsuz ayrı tutma nedeniyle aramadır.

- Arama, beklemedeki konumları aramak üzere yapılandırılırsa ve servis talebindeki bir eBulma ayrı tutmasını değiştirirseniz (konum ekleyerek veya kaldırarak ya da ayrı tutma sorgusunu değiştirerek), arama yapılandırması bu değişikliklerle güncelleştirilir. Ancak, arama sonuçlarını güncelleştirmek için ayrı tutma değiştirildikten sonra aramayı yeniden çalıştırmanız gerekir.

- eBulma durumunda tek bir konuma birden çok eBulma ayrılığı yerleştirilirse ve beklemedeki konumları aramayı seçerseniz, söz konusu arama sorgusu için anahtar sözcük sayısı üst sınırı 500'dür. Bunun nedeni, aramanın **OR** işlecini kullanarak tüm sorgu tabanlı ayrı tutmaları birleştirmesidir. Birleştirilmiş saklama sorgularında ve arama sorgusunda 500'den fazla anahtar sözcük varsa, yalnızca sorgu tabanlı servis talebiyle eşleşen içerikle değil, posta kutusundaki tüm içerikte arama yapılır.

- Bir eBulma ayrı tutmasının durumu **Açık (Beklemede)** ise, ayrı tutma açıkken beklemedeki konumlarda arama yapabilirsiniz.

## <a name="preserve-content-in-microsoft-teams"></a>Microsoft Teams içeriği koruma

Microsoft Teams kanalının parçası olan konuşmalar, Microsoft Ekibi ile ilişkili posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin kanalda paylaştığı dosyalar ekibin SharePoint sitesinde depolanır. Bu nedenle, kanaldaki konuşmaları ve dosyaları korumak için Ekip posta kutusunu ve SharePoint sitesini eBulma bekletmeye yerleştirmeniz gerekir.

Alternatif olarak, Teams Sohbet listesinin bir parçası olan *konuşmalar (1:1 sohbetler* veya *1:N grup sohbetleri* olarak adlandırılır) sohbete katılan kullanıcıların posta kutularında depolanır. Ayrıca kullanıcıların sohbet konuşmalarında paylaştığı dosyalar, dosyayı paylaşan kullanıcının OneDrive hesabında depolanır. Bu nedenle, sohbet listesindeki konuşmaları ve dosyaları korumak için tek tek kullanıcı posta kutularını ve OneDrive hesaplarını bir eBulma bekletmesine eklemeniz gerekir. Ekip posta kutusunu ve siteyi beklemeye almanın yanı sıra Bir Microsoft Ekibi üyelerinin posta kutularını ayrı tutmak iyi bir fikirdir.

> [!NOTE]
> Kuruluşunuzun Exchange karma dağıtımı varsa (veya kuruluşunuz şirket içi Exchange kuruluşunu Office 365 ile eşitlediyse) ve Microsoft Teams etkinleştirdiyse, şirket içi kullanıcılar Teams sohbet uygulamasını kullanabilir ve 1:1 sohbetlere ve 1:N grup sohbetlerine katılabilir. Bu konuşmalar, şirket içi kullanıcıyla ilişkili bulut tabanlı depolamada depolanır. Şirket içi bir kullanıcı eBulma ayrı tutmaya yerleştirilirse, bulut tabanlı depolama alanındaki Teams sohbet içeriği korunur. Daha fazla bilgi için bkz[. Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

Teams içeriği koruma hakkında daha fazla bilgi için bkz[. Microsoft Teams bir kullanıcıyı veya ekibi yasal saklamaya alma](/MicrosoftTeams/legal-hold).

### <a name="preserve-card-content"></a>Kart içeriğini koru

Benzer şekilde, Teams kanallarında, 1:1 sohbetlerinde ve 1:N grup sohbetlerinde uygulamalar tarafından oluşturulan kart içeriği posta kutularında depolanır ve bir eBulma ayrı tutmaya bir posta kutusu yerleştirildiğinde korunur. *Kart*, kısa içerik parçaları için bir kullanıcı arabirimi kapsayıcısıdır. Kartların birden çok özelliği ve eki olabilir ve kart eylemlerini tetikleyen düğmeler içerebilir. Daha fazla bilgi için bkz. [Kartlar](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Diğer Teams içeriğinde olduğu gibi, kart içeriğinin depolandığı yer de kartın kullanıldığı yere bağlıdır. Teams kanalında kullanılan kartların içeriği Teams grup posta kutusunda depolanır. 1:1 ve 1xN sohbetler için kart içeriği, sohbet katılımcılarının posta kutularında depolanır.

### <a name="preserve-meeting-and-call-information"></a>Toplantı ve arama bilgilerini koruma

Teams kanalındaki toplantılar ve aramalar için özet bilgiler, toplantıyı veya aramayı arayan kullanıcıların posta kutularında da depolanır. Bu içerik, kullanıcı posta kutularına bir eBulma ayrılığı yerleştirildiğinde de korunur.

### <a name="preserve-content-in-private-channels"></a>Özel kanallarda içeriği koruma

Şubat 2020'den itibaren özel kanallardaki içeriği koruma özelliğini de açtık. Özel kanal sohbetleri sohbet katılımcılarının posta kutularında depolandığından, eKeşif beklemesine bir kullanıcı posta kutusu yerleştirmek özel kanal sohbetlerini korur. Ayrıca, bir kullanıcı posta kutusu Şubat 2020'den önce bir eBulma ayrı tutmasına yerleştirilmişse, bekletme artık bu posta kutusunda depolanan özel kanal iletilerine otomatik olarak uygulanır. Özel kanallarda paylaşılan dosyaların korunması da desteklenir.

### <a name="preserve-wiki-content"></a>Wiki içeriğini koruma

Her Ekip veya ekip kanalı, not alma ve işbirliği için bir Wiki de içerir. Wiki içeriği otomatik olarak .mht biçiminde bir dosyaya kaydedilir. Bu dosya, ekibin SharePoint sitesindeki Teams Wiki Verileri belge kitaplığında depolanır. Ekibin SharePoint sitesini eBulma ayrı tutmaya ekleyerek wiki içeriğini koruyabilirsiniz.

> [!NOTE]
> Ekip veya ekip kanalının Wiki içeriğini koruma özelliği (ekibin SharePoint sitesini beklemeye aldığınızda) 22 Haziran 2017'de yayımlandı. Bir ekip sitesi beklemedeyse, Wiki içeriği bu tarihten itibaren korunur. Ancak bir ekip sitesi beklemedeyse ve Wiki içeriği 22 Haziran 2017'dan önce silinmişse Wiki içeriği korunmaz.

### <a name="office-365-groups"></a>Office 365 Grupları

Teams Office 365 Grupları'nda oluşturulur. Bu nedenle, Office 365 Gruplarını eBulma ayrı tutmaya yerleştirmek, Teams içeriği ayrı tutmaya benzer.

Bir eBulma saklamaya hem Teams hem de Office 365 Grupları yerleştirirken aşağıdakileri göz önünde bulundurun:

- Daha önce açıklandığı gibi, Teams ve Office 365 Grupları'nda bulunan içeriği ayrı tutmak için, bir grup veya ekiple ilişkili posta kutusunu ve SharePoint sitesini belirtmeniz gerekir.

- Teams ve Office 365 Gruplarının özelliklerini görüntülemek için [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) **Get-UnifiedGroup** cmdlet'ini çalıştırın. Bu, bir Ekip veya Office 365 Grubu ile ilişkili sitenin URL'sini almak için iyi bir yoldur. Örneğin, aşağıdaki komut Kıdemli Liderlik Ekibi adlı bir Office 365 Grubu için seçili özellikleri görüntüler:

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > **Get-UnifiedGroup** cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir. 
  
- Kullanıcının posta kutusu arandığında, kullanıcının üyesi olduğu hiçbir Ekip veya Office 365 Grubu aranamaz. Benzer şekilde, eBulma ayrı tutmaya bir Ekip veya Office 365 Grubu yerleştirdiğinizde, yalnızca grup posta kutusu ve grup sitesi beklemeye alınır. Grup üyelerinin posta kutuları ve OneDrive İş siteleri, eBulma ayrı tutmaya açıkça eklemediğiniz sürece ayrı tutmaz. Bu nedenle, yasal bir nedenden dolayı bir Ekibi veya Office 365 Grubunu beklemeye almanız gerekiyorsa, ekip veya grup üyelerinin posta kutularını ve OneDrive hesaplarını aynı ayrı tutmaya eklemeyi göz önünde bulundurun.

- Ekip veya Office 365 Grubu üyelerinin listesini almak için, özellikleri Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Gruplar**</a> sayfasında görüntüleyebilirsiniz. Alternatif olarak, Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir.

## <a name="preserve-content-in-onedrive-accounts"></a>OneDrive hesaplarındaki içeriği koruma

Kuruluşunuzdaki OneDrive İş sitelerin URL'lerinin listesini toplamak ve böylece bunları eBulma olayıyla ilişkili bir ayrı tutma veya aramaya eklemek için bkz. [Kuruluşunuzdaki tüm OneDrive konumlarının listesini oluşturma](/onedrive/list-onedrive-urls). Bu makaledeki betik, kuruluşunuzdaki tüm OneDrive sitelerin listesini içeren bir metin dosyası oluşturur. Bu betiği çalıştırmak için SharePoint Online Management Shell'i yüklemeniz ve kullanmanız gerekir. Arama yapmak istediğiniz her OneDrive sitesine kuruluşunuzun Sitem etki alanının URL'sini eklediğinizden emin olun. Bu, tüm OneDrive içeren etki alanıdır; örneğin, `https://contoso-my.sharepoint.com`. Kullanıcının OneDrive sitesinin URL'sine bir örnek aşağıda verilmiştır: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> Kullanıcının OneDrive hesabının URL'si, kullanıcı asıl adını (UPN) içerir (örneğin, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Bir kişinin UPN'sinin değişmesi nadir durumlarda, OneDrive URL'si de yeni UPN'yi içerecek şekilde değişir. Kullanıcının OneDrive hesabı bir eBulma ayrı tutmasının parçasıysa, eskiyse ve UPN'si değiştirilirse, ayrı tutmayı güncelleştirmeniz ve ayrı tutmayı güncelleştirmeniz ve kullanıcının yeni OneDrive URL'sini eklemeniz ve eskisini kaldırmanız gerekir. Daha fazla bilgi için bkz[. UPN değişiklikleri OneDrive URL'sini nasıl etkiler](/onedrive/upn-changes)?

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>eBulma ayrılığından içerik konumlarını kaldırma

Bir posta kutusu, SharePoint site veya OneDrive hesabı eBulma ayrılığından kaldırıldıktan sonra *gecikmeli saklama* uygulanır. Bu, verilerin içerik konumundan kalıcı olarak silinmesini (temizlenmesini) önlemek için saklama işleminin gerçek kaldırılmasının 30 gün ertelendiği anlamına gelir. Bu, yöneticilere eBulma ayrı tutma kaldırıldıktan sonra temizlenecek içeriği arama veya kurtarma fırsatı verir. Posta kutuları ve siteler için gecikme saklamanın nasıl çalıştığına ilişkin ayrıntılar farklıdır.

- **Posta kutu -ları:** Yönetilen Klasör Yardımcısı posta kutusunu bir sonraki işlediğinde ve bir eBulma ayrılığının kaldırıldığını algılayışında bir posta kutusuna gecikmeli saklama yerleştirilir. Özellikle, Yönetilen Klasör Yardımcısı aşağıdaki posta kutusu özelliklerinden birini **True** olarak belirlediğinde bir posta kutusuna gecikmeli saklama uygulanır:

   - **DelayHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan e-postayla ilgili içerik (Outlook ve Web üzerinde Outlook kullanan kişiler tarafından oluşturulur) için geçerlidir.

   - **DelayReleaseHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan bulut tabanlı içerik (Microsoft Teams, Microsoft Forms ve Microsoft Yammer gibi Outlook olmayan uygulamalar tarafından oluşturulur) için geçerlidir. Microsoft uygulaması tarafından oluşturulan bulut verileri genellikle kullanıcının posta kutusunda gizli bir klasörde depolanır.

   Posta kutusuna bir gecikmeli saklama yerleştirildiğinde (önceki özelliklerden biri **True** olarak ayarlandığında), posta kutusu, dava ayrı tutmadaymış gibi, sınırsız bir saklama süresi boyunca beklemede olarak kabul edilir. 30 gün sonra gecikme saklama süresi dolar ve Microsoft 365 gecikme saklamayı kaldırmayı otomatik olarak dener (DelayHoldApplied veya DelayReleaseHoldApplied özelliğini **False** olarak ayarlayarak) böylece bekletme kaldırılır. Bu özelliklerden biri **False** olarak ayarlandıktan sonra, posta kutusu Yönetilen Klasör Yardımcısı tarafından bir sonraki işlendiğinde, kaldırılmak üzere işaretlenmiş ilgili öğeler temizlenir.

   Daha fazla bilgi için bkz. [Gecikmeli beklemede posta kutularını yönetme](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **SharePoint ve OneDrive siteleri:** Koruma Bekletme kitaplığında tutulan SharePoint veya OneDrive içeriği, site bir eBulma ayrılığından kaldırıldıktan sonraki 30 günlük gecikme süresi boyunca silinmez. Bu, bir site bir bekletme ilkesinden yayınlandığında gerçekleşene benzer. Ayrıca, 30 günlük gecikme süresi boyunca Bu içeriği Koruma Bekletme kitaplığında el ile silemezsiniz. 

   Daha fazla bilgi için bkz. [Bekletme için ilke yayımlama](retention.md#releasing-a-policy-for-retention).

Bir servis talebi kapatıldığında ayrı tutmalar kapatıldığından, eBulma (Standart) servis talebini kapattığınızda beklemedeki içerik konumlarına da gecikmeli saklama uygulanır. Servis talebini kapatma hakkında daha fazla bilgi için bkz. [EBulma (Standart) servis talebini kapatma, yeniden açma ve silme](close-reopen-delete-core-ediscovery-cases.md).

## <a name="ediscovery-hold-limits"></a>eBulma tutma sınırları

Aşağıdaki tabloda eBulma durumları ve servis talebi tutma sınırları listeleniyor.

  | Sınırın açıklaması | Sınırı |
  |:-----|:-----|
  |Bir kuruluş için en fazla servis talebi sayısı.  <br/> |Sınır yok  <br/> |
  |Bir kuruluş için en fazla eBulma saklama ilkesi sayısı. Bu sınır, eBulma (Standart) ve eBulma (Premium) durumlarında birleştirilmiş saklama ilkelerinin toplamını içerir.  <br/> |10.0001<sup></sup>  <br/> |
  |Tek bir eBulma ayrılığındaki en fazla posta kutusu sayısı. Bu sınır, kullanıcı posta kutularının toplamını ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili posta kutularını içerir.  <br/> |1,000  <br/> |
  |Tek bir eBulma ayrılığındaki en fazla site sayısı. Bu sınır, OneDrive İş sitelerin, SharePoint sitelerin ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili sitelerin toplamını içerir.  <br/> |100  <br/> |
  |eBulma giriş sayfasında görüntülenen en fazla servis talebi sayısı ve servis talebi içindeki Tutmalar, Aramalar ve Dışarı Aktarma sekmelerinde görüntülenen en fazla öğe sayısı.  |1.0001<sup></sup>|

   > [!NOTE]
   > <sup></sup> 1.000'den fazla servis talebi, ayrı tutma, arama veya dışarı aktarma listesini görüntülemek için ilgili Güvenlik & Uyumluluğu PowerShell cmdlet'ini kullanabilirsiniz:
   >
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)
