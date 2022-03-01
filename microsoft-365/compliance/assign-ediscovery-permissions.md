---
title: EBulma izinleri atama Microsoft 365 uyumluluk merkezi
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
search.appverid:
- MOE150
- MET150
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: eBulma ile ilgili görevleri gerçekleştirmek için gereken izinleri, çalışma Microsoft 365 uyumluluk merkezi.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 129363fe614bafef653fe65b39fa15d50a3b1c8a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034264"
---
# <a name="assign-ediscovery-permissions-in-the-microsoft-365-compliance-center"></a>EBulma izinleri atama Microsoft 365 uyumluluk merkezi

Kişilerin eBulma ile ilgili [araçlardan](ediscovery.md) herhangi birini Microsoft 365 uyumluluk merkezi, onlara uygun izinleri atamanız gerekir. Bunu yapmanın en kolay yolu, uyumluluk merkezi'nin İzinler sayfasında ilgili **kişiyi** rol grubuna eklemektir. Bu konuda, eBulma görevlerini gerçekleştirmek için gereken izinler açıklanmıştır.
  
EBulma ile ilgili birincil rol grubu Microsoft 365 uyumluluk merkezi **, eBulma Yöneticisi olarak adlandırılan bir gruptır**. Bu rol grubunun içinde iki alt grup vardır.
  
- **eBulma Yöneticisi** - eBulma Yöneticisi, kuruluşta içerik konumlarında arama yapmak ve arama sonuçlarını önizleme ve dışarı aktarma gibi aramayla ilgili çeşitli eylemler gerçekleştirmek için eBulma Yöneticisi'ni kullanabilir. Üyeler ayrıca Çekirdek eKbulma ve Servis Advanced eDiscovery'da vakalar oluşturabilir ve yönetebilir, bir vakaya üye ekleyebilir ve kaldırabilir, servislarına yönelik arama oluşturabilir ve vaka verilerine erişim sağlarlar. eBulma Yöneticileri yalnızca oluşturdukları vakalara erişim iznine sahip olabilir ve bu vakaları yönetebilir. Diğer eBulma Yöneticileri tarafından oluşturulan vakalara erişemeksizin veya bu vakaları yöneterek erişemmektedir.
  
- **eBulma** Yöneticisi - eBulma Yöneticisi eBulma Yöneticisi rol grubunun bir üyesidir ve eBulma Yöneticisi'nin gerçekleştirebilir olduğu içerik arama ve olay yönetimiyle ilgili görevlerle aynı görevleri gerçekleştirebilir. Buna ek olarak, eBulma Yöneticisi şunları da olabilir:
  
  - Çalışma sayfalarındaki Core **eKbulma** ve **Advanced eDiscovery servis Microsoft 365 uyumluluk merkezi**.

  - Kuruluşta herhangi bir Advanced eDiscovery için örnek olay verilerine erişin.
  
  - eBulma olaylarını, kendilerini davanın üyesi olarak ekledikten sonra yönetin.
  
  - eBulma durumundan üyeleri kaldırma. Yalnızca eBulma Yöneticisi vakadan üyeleri kaldırabilir. eBulma Yöneticisi alt grubu üyesi olan kullanıcılar, durumu kullanıcı oluşturduğunda bile vakadan üye kaldıramıyor.
  
  eBulma Yöneticilerinin kurum içinde yer istemenizi nedenleriyle, daha fazla [bilgi'ye bakın](#more-information).

> [!NOTE]
> Advanced eDiscovery kullanarak kullanıcının verilerini çözümlemek için, kullanıcıya (verilerin koruyucu) bir Office 365 E5 veya Microsoft 365 E5 atanabilir. Alternatif olarak, Office 365 E1 ya da Office 365 veya Microsoft 365 E3 lisansı olan kullanıcılara Microsoft 365 E5 Uyumluluk veya Microsoft 365 eKbulma ve Denetim eklenti lisansı atanabilir. Davalara üye olarak atanan ve E5 lisansına gerek yoktur ve verileri toplamak, görüntülemek ve çözümlemek için Advanced eDiscovery'i kullanan yöneticiler, uyumluluk görevlileri veya yasal personel. Lisanslama hakkında daha fazla Advanced eDiscovery için bkz. [Web'de abonelikler ve Advanced eDiscovery](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>İzinleri atamadan önce

- Kuruluş Yönetimi rol grubunun bir üyesi olmalı veya kuruluşta eBulma izinleri atamak için Rol Yönetimi rolüne Microsoft 365 uyumluluk merkezi.

- Posta özellikli bir güvenlik grubunu eBulma Yöneticisi rol grubunda eBulma Yöneticileri alt grubuna üye olarak eklemek için Güvenlik & Uyumluluk Merkezi PowerShell'de [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) cmdlet'ini kullanabilirsiniz. Bununla birlikte, eBulma Yöneticileri alt grubuna posta özelliği etkin bir güvenlik grubu eke değildir. Ayrıntılar için daha fazla [bilgi'ye bakın](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>eBulma izinleri atama

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> ve izin atayabilirsiniz bir hesap kullanarak oturum açın.
  
2. Sol bölmede İzinler'i **seçin**.

3. İzinler **Merkezi & Uyumluluk** merkezi altında **Roller'e** **tıklayın**.

4. Uyumluluk merkezi **rolleri sayfasında eBulma** **Yöneticisi'ni seçin**.
  
5. **eBulma Yöneticisi** uç uç sayfasında, atamak istediğiniz eBulma izinlerine bağlı olarak aşağıdakilerden birini yapın.
  
    **Bir kullanıcıya eBulma Yöneticisi yapmak için:** **eBulma Yöneticisi'nin yanında** Düzenle'yi **seçin**. **eBulma Yöneticisi Seç sihirbazı sayfasında** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **ekle'yi seçin**. eBulma yöneticisi olarak eklemek istediğiniz kullanıcı (veya kullanıcıları) seçin ve sonra da Ekle'yi **seçin**. Kullanıcı eklemeyi bitirdikten sonra Bitti'yi **seçin**. Ardından,  **eBulma Yöneticisi Seç sihirbazı** sayfasında, değişiklikleri eBulma Yöneticisi üyeliğine kaydetmek için Kaydet'i seçin.
  
    **Bir kullanıcıya eBulma Yöneticisi yapmak için:** **eBulma Yöneticisi'nin yanında Düzenle'yi** **seçin**. **eBulma Yöneticisi Seç sayfasında Simge** Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **ekle'yi seçin**. eBulma Yöneticisi olarak eklemek istediğiniz kullanıcı (veya kullanıcıları **) seçin ve sonra da**  **Ekle'yi seçin**. Kullanıcı eklemeyi bitirdikten sonra Bitti'yi **seçin**. Ardından,  **eBulma Yöneticisi Seç** sihirbazı sayfasında, değişiklikleri eBulma Yöneticisi üyeliğine kaydetmek için Kaydet'i seçin.
  
> [!NOTE]
> Ayrıca, kullanıcıya **eBulma Yöneticisi yapmak için Add-eDiscoveryCaseAdmin** cmdlet'ini de kullanabilirsiniz. Bununla birlikte, bu cmdlet'i kullanarak onu eBulma Yöneticisi yapmak için önce kullanıcıya Olay Yönetimi rolü atanabilir. Daha fazla bilgi için [bkz. Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin). 
  
İzinler **sayfasının** Microsoft 365 uyumluluk merkezi, kullanıcıları Uyumluluk Yöneticisi, Kuruluş Yönetimi ve Gözden Geçiren rol gruplarına ekleyerek, eBulma ile ilgili izinler atabilirsiniz. Bu rol gruplarının her biri için atanmış eBulma ile ilgili RBAC rollerinin açıklaması için bkz. [eKbulma ile ilgili RBAC rolleri](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>eKbulma ile ilgili RBAC rolleri

Aşağıdaki tabloda, çalışma sayfalarında eKbulma ile ilgili RBAC rolleri liste Microsoft 365 uyumluluk merkezi ve her bir rolün varsayılan olarak atandığı yerleşik rol gruplarını gösterir.
  
| Rol | Uyumluluk Yöneticisi | eBulma Yöneticisi & Yönetici | Kuruluş Yönetimi | Gözden geçiren |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Vaka Yönetimi <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|İletişim <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Uyumluluk Araması <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|Custo bire bir <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Dışarı aktarma <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Bekle <br/>  |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|Önizleme <br/>  | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Gözden Geçir <br/>  | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |![Onay işareti](../media/checkmark.png) <br/> |
|RMS Şifre Çözme <br/>  ||![Onay işareti](../media/checkmark.png) <br/> |||
|Arama ve Temizleme <br/> | <br/> | <br/> |![Onay işareti](../media/checkmark.png)           <br/> | <br/> |
||||
  
Aşağıdaki bölümlerde, önceki tabloda listelenen eKbulma ile ilgili RBAC rollerinin her biri açıklanmaktadır.

### <a name="case-management"></a>Vaka Yönetimi

Bu rol, kullanıcıların aynı dosyalarda Çekirdek eKbulma ve temel Advanced eDiscovery oluşturmalarına, düzenlemelerine, silmelerine ve denetim Microsoft 365 uyumluluk merkezi. Daha önce de belirtildiği gibi, **eBulma Yöneticisi yapmak üzere Add-eDiscoveryCaseAdmin** cmdlet'ini kullanamadan önce bir kullanıcıya Olay Yönetimi rolü atanabilir.

Daha fazla bilgi için bkz.:

- [Core eDiscovery ile çalışmaya başlama](get-started-core-ediscovery.md)

- [Advanced eDiscovery'i Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>İletişim

Bu rol, kullanıcıların herhangi bir durumda tanımlanan koruyucularla olan tüm iletişimi yönetme Advanced eDiscovery sağlar. Bu, tutma bildirimleri, anımsatıcılar tutma ve yönetime yükseltmeleri içerir. Kullanıcı ayrıca, custo custo cust bildirimlerinin bildirimini izleyebilir ve custo bir olarak tanımlanlan durumlar için iletişimleri izlemek için her custo cust portalında erişimi yönetebilir.

Daha fazla bilgi için bkz[. E-postada iletişim Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Uyumluluk Araması

Bu rol kullanıcıların posta kutularını ve ortak klasörleri, SharePoint Çevrimiçi siteleri, OneDrive İş sitelerini, Skype Kurumsal konuşmalarını veya diğer klasörleri aramak için Microsoft 365 uyumluluk merkezi'te İçerik Arama aracını Microsoft 365 grupları, Microsoft Teams ve Yammer. Bu rol, kullanıcının arama sonuçlarıyla ilgili bir tahminde bulundurarak dışarı aktarma raporları oluşturmasine olanak sağlar, ancak arama sonuçlarını önizleme, dışarı aktarma veya silme gibi içerik arama eylemlerini başlatmak için başka roller de gereklidir.

İçerik aramasında ve Çekirdek eKbulma'da, Uyumluluk Araması rolüne atanmış olan ancak Önizleme rolüne sahip olan kullanıcılar önizleme eyleminin başlatıldığı aramanın sonuçlarını önizler. Önizleme rolüne sahip olmayan kullanıcı, ilk önizleme eylemi oluşturulduktan sonra en fazla iki hafta boyunca sonuçları önizler.

Benzer şekilde, İçerik aramasında ve Çekirdek eBulma'da yer alan ve Uyumluluk Araması rolüne atanmış olan ancak Dışarı Aktarma rolüne sahip olan kullanıcılar, Dışarı Aktarma rolüne atanmış bir kullanıcı tarafından dışarı aktarma eyleminin başlatıldığı aramanın sonuçlarını indirebilir. Dışarı Aktarma rolü olmayan kullanıcı, ilk dışarı aktarma eylemi oluşturulduktan sonra en fazla iki hafta boyunca aramanın sonuçlarını indirebilir. Bundan sonra, Dışarı Aktarma rolüne sahip biri dışarı aktarmayı yeniden başlatmadıkça sonuçları indireler.

Arama sonuçlarının önizlemesi ve dışarı aktarması için (ilgili arama ve dışarı aktarma rolleri olmadan) iki haftalık yetkisiz kullanım süresi, Advanced eDiscovery. Kullanıcıların, aynı dosyada içeriği önizlemek ve dışarı aktarması için Önizleme ve Dışarı Aktarma rollerine Advanced eDiscovery.

### <a name="custodian"></a>Custo bire bir

Bu rol, kullanıcıların özel durumlar için koruyucuları tanımlamalarına ve yönetmelarına Advanced eDiscovery koruyucularla ilişkilendirilmiş veri kaynaklarını bulmak için Azure Active Directory ve diğer kaynaklardan gelen bilgileri kullanmalarına olanak sağlar. Kullanıcı posta kutuları, posta kutuları ve site SharePoint diğer veri kaynaklarını Teams bir durumda koruyucularla iş ortağı olabilir. Ayrıca kullanıcı, bir dava bağlamında içeriği korumak için koruyucularla ilişkilendirilmiş veri kaynaklarını yasal olarak tutabilir.

Daha fazla bilgi için bkz[. Bu çalışma sayfalarında koruyucularla Advanced eDiscovery](managing-custodians.md).

### <a name="export"></a>Dışarı aktarma

Rol, kullanıcıların İçerik Arama sonuçlarını yerel bir bilgisayara aktarmalarına olanak sağlar. Ayrıca, kullanıcıların kendi içinde arama sonuçlarını çözümleme için hazırlamalarına da Advanced eDiscovery.

Arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz. Arama [sonuçlarını dışarı aktarma Microsoft 365 uyumluluk merkezi](export-search-results.md).

### <a name="hold"></a>Bekle

Bu rol kullanıcıların posta kutularına, ortak klasörlere, sitelere, sitelere ve Skype Kurumsal gruplara içerik Microsoft 365 sağlar. İçerik tutmada olduğunda, içerik sahipleri özgün içeriği değiştirmeye veya silebilir, ancak içerik, tutma kaldırılana kadar veya tutma süresi dolana kadar korunur.

1. 1. Dakikalar hakkında daha fazla bilgi için bkz:

- [Core eDiscovery'de ayrı tutma oluşturma](create-ediscovery-holds.md) 

- [E-Advanced eDiscovery](add-custodians-to-case.md)

### <a name="preview"></a>Önizleme

Bu rol, kullanıcıların İçerik Arama'dan döndürülen öğelerin listesini görüntülemelerini sağlar. Ayrıca, içeriği görüntülemek için listeden her öğeyi açabilir ve  bakabilirsiniz.

### <a name="review"></a>Gözden Geçir

Bu rol, kullanıcıların gözden geçirme kümelerine aynı [Advanced eDiscovery.](overview-ediscovery-20.md) Bu role atanan kullanıcılar, üyesi olduğu **eBulma sayfasındaki eBulma > Gelişmiş** sayfasında vakaların listesini Microsoft 365 uyumluluk merkezi ve açabilirler. Kullanıcı çalışma durumuna erişdikten Advanced eDiscovery büyük/harfe erişmek için **Kümeleri gözden geçir'i** seçer. Bu rol, kullanıcının olayla ilişkilendirilmiş koleksiyon aramalarının sonuçlarını önizlemesine veya başka arama ya da olay yönetimi görevleri gerçekleştirmesine izin vermez. Bu role sahip kullanıcılar yalnızca gözden geçirme kümesinde yer alan verilere erişim sağlar.

### <a name="rms-decrypt"></a>RMS Şifre Çözme

Bu rol, kullanıcıların arama sonuçlarının önizlemesini görüntülerken ve şifreleri çözülmüş hak korunan e-posta iletilerini dışarı aktararak hakları korunan e-posta iletilerini görüntülemelerine olanak sağlar. Bu rol, şifrelenmiş dosya bir eBulma aramasında bulunan bir e-posta iletisine ekli olduğunda, kullanıcıların [Microsoft](encryption.md) şifreleme teknolojisiyle şifrelenmiş bir dosyayı görüntülemesine (ve dışarı aktarmalarına) da olanak sağlar. Buna ek olarak, bu rol kullanıcıların e-posta içinde bir gözden geçirme kümesine eklenen şifrelenmiş e-posta eklerini gözden geçirmelerine ve sorgulamalarına Advanced eDiscovery. eBulma'da şifre çözme hakkında daha fazla bilgi için bkz. [eBulma araçlarında Microsoft 365 çözme](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Arama ve Temizleme

Bu rol, kullanıcıların içerik arama ölçütleriyle eşleşen verileri toplu olarak kaldırma işlemi gerçekleştirmelerini sağlar. Daha fazla bilgi için bkz [. Kurumda e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>eBulma olaylarının üyeleri olarak rol grupları ekleme

Rol gruplarının üyelerinin atanan vakalarda görevlere erişmesi ve görevleri gerçekleştirmesi için Çekirdek eKbulma ve proje Advanced eDiscovery örneklerine üye olarak rol grupları ebilirsiniz. Rol grubuna atanan roller, rol grubunun üyelerinin neler yapa bir şeyler yapa bir şeyler yapa bir tanımlaması yapar. Ardından bir rol grubunu vakanın üyesi olarak eklemek, üyelerin bu görevlere belirli bir durumda erişmelerine ve gerçekleştirmelerine olanak sağlar. Vakaların üyeleri olarak rol grupları ekleme hakkında daha fazla bilgi için bkz:

- [Core eDiscovery ile çalışmaya başlama](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

- [Olayda üye ekleme veya Advanced eDiscovery kaldırma](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Bu nedenle, bir rol bir rol grubuna eklenir veya gruptan kaldırılırsa, rol grubunun herhangi bir üye olarak otomatik olarak kaldırılacak olması gerekir. Bunun nedeni, kurumlarınızı bir davanın üyelerine yanlışlıkla ek izinler sağlamaktan korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlarda gruptan kaldırılır.

eBulma çalışmasına üye olan bir rol grubuna rol eklemeden veya kaldırmadan önce, rol grubunun üyesi olduğu durumların listesini almak için Güvenlik [& Compliance PowerShell'de](/powershell/exchange/connect-to-scc-powershell) aşağıdaki komutları çalıştırabilirsiniz. Rol grubunu güncelleştirdikten sonra, rol grubunu bu durumlarda tekrar üye olarak eklersiniz.

### <a name="get-a-list-of-core-ediscovery-cases-a-role-group-is-assigned-to"></a>Bir rol grubunun atandığı Çekirdek eKbulma durumlarının listesini al

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-advanced-ediscovery-cases-a-role-group-is-assigned-to"></a>Bir rol Advanced eDiscovery ilgili durumların listesini al

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Daha fazla bilgi

- **eBulma Yöneticisi neden oluşturulsun?** Daha önce de belirtildiği gibi, eBulma Yöneticisi, eBulma Yöneticisi rol grubunun üyesidir ve bu grup, kuruluşta tüm eBulma olaylarını  görüntüp bu vakalara erişim sağlar. Bu özelliğin tüm eBulma olaylarına erişmenin iki önemli amacı vardır:

  - eBulma davalarının tek üyesi olan bir kişi sizin kuruluşundan ayrılırsa, kimse (Kuruluş Yönetimi rol grubunun üyeleri veya eBulma Yöneticisi rol grubunun başka bir üyesi de dahil) bu eBulma durumuna erişemz çünkü onlar bir davanın üyesi değildir. Bu durumda, bu durumda verilere erişmenin hiçbir yolu yoktu. Ancak eBulma Yöneticisi kuruluşta tüm eBulma olaylarına erişim iznine sahip olduğundan, kendilerini veya başka bir eBulma yöneticisini davanın üyesi olarak ekleyebilir.

  - eBulma Yöneticisi tüm Çekirdek eBulma ve Erişim durumlarını görüntüleye Advanced eDiscovery, tüm vakaları ve ilişkili uyumluluk aramalarını denetleyebilir ve denetleyebilir. Bu, uyumluluk aramalarının veya eBulma olaylarının kötüye kullanılmasını önlemeye yardımcı olabilir. Ayrıca eBulma Yöneticileri, uyumluluk aramalarının sonuçlarında hassas olabilecek bilgilere erişeler olduğundan, eBulma Yöneticisi olan kişi sayısını sınırlandırmanız gerekir.

- **Bir grubu eBulma Yöneticisi rol grubunun bir üyesi olarak ekleyebilir miyim?** Daha önce de belirtildiği gibi, Güvenlik & Uyumluluk Merkezi PowerShell'inde **Add-RoleGroupMember** cmdlet'ini kullanarak eBulma Yöneticisi rol grubuna eBulma Yöneticileri alt grubunun üyesi olarak posta etkin bir güvenlik grubu eklersiniz. Örneğin, eBulma Yöneticisi rol grubuna posta özelliği etkin bir güvenlik grubu eklemek için aşağıdaki komutu çalıştırabilirsiniz. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange grupları Microsoft 365 grupları destek desteklemez. 'i çalıştırarak, PowerShell'de oluşturabilirsiniz ve posta Exchange Online bir güvenlik grubu kullan gerekir`New-DistributionGroup -Type Security`. Ayrıca, yönetim merkezinde veya posta merkezinde posta özellikli bir güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">grubu Exchange</a> (ve üye [ekleme) Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339). Yeni posta özelliği etkin bir güvenlik grubunun eBulma Yöneticileri rol grubuna eklen kullanılabilir olması, 60 dakika kadar sürebilir.

    Ayrıca, daha önce de belirtildiği gibi, Güvenlik ve Uyumluluk Merkezi PowerShell'de **Add-eDiscoveryCaseAdmin** cmdlet'ini kullanarak posta etkin bir güvenlik grubunu eBulma Yöneticisi &. eBulma Yöneticileri olarak yalnızca tek tek kullanıcılar  eklemeniz gerekir.

    Ayrıca posta etkin bir güvenlik grubunu vakanın üyesi olarak ekeyesiniz.
