---
title: Microsoft Purview uyumluluk portalında eBulma izinleri atama
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
description: Microsoft Purview uyumluluk portalını kullanarak eBulma ile ilgili görevleri gerçekleştirmek için gereken izinleri atayın.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 1f19c43e65993652628703f002b9537c71066013
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946539"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>Uyumluluk portalında eBulma izinleri atama

Kişilerin Microsoft Purview uyumluluk portalındaki [eBulma ile ilgili araçlardan](ediscovery.md) herhangi birini kullanmasını istiyorsanız, onlara uygun izinleri atamanız gerekir. Bunu yapmanın en kolay yolu, kişiyi uyumluluk merkezindeki **İzinler** sayfasında uygun rol grubuna eklemektir. Bu konuda, eBulma görevlerini gerçekleştirmek için gereken izinler açıklanmaktadır.
  
Uyumluluk portalındaki birincil eBulma ile ilgili rol grubu **eBulma Yöneticisi** olarak adlandırılır. Bu rol grubu içinde iki alt grup vardır.
  
- **eBulma Yöneticisi** - eBulma Yöneticisi, kuruluştaki içerik konumlarında arama yapmak ve arama sonuçlarını önizleme ve dışarı aktarma gibi aramayla ilgili çeşitli eylemleri gerçekleştirmek için eBulma arama araçlarını kullanabilir. Üyeler ayrıca Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) içinde servis talepleri oluşturabilir ve yönetebilir, servis talebine üye ekleyip kaldırabilir, servis talebi tutmaları oluşturabilir, servis talebiyle ilişkili aramaları çalıştırabilir ve servis talebi verilerine erişebilir. eBulma Yöneticileri yalnızca oluşturdukları servis taleplerine erişebilir ve bu servis taleplerini yönetebilir. Diğer eBulma Yöneticileri tarafından oluşturulan servis taleplerini erişemez veya yönetemezler.
  
- **eBulma Yöneticisi** - eBulma Yöneticisi, eBulma Yöneticisi rol grubunun bir üyesidir ve eBulma Yöneticisi'nin gerçekleştirebileceği içerik arama ve servis talebi yönetimiyle ilgili görevleri gerçekleştirebilir. Ayrıca, eBulma Yöneticisi şunları yapabilir:
  
  - Uyumluluk portalındaki **eBulma (Standart)** ve **eBulma (Premium)** sayfalarında listelenen tüm servis taleplerine erişin.

  - Kuruluştaki herhangi bir durum için eBulma (Premium) içindeki servis talebi verilerine erişin.
  
  - Kendilerini servis talebine üye olarak ekledikten sonra herhangi bir eBulma servis talebini yönetin.
  
  - eBulma durumundan üyeleri kaldırma. Bir servis talebinin üyelerini yalnızca eBulma Yöneticisi kaldırabilir. eBulma Yöneticisi alt grubunun üyesi olan kullanıcılar, olayı kullanıcı oluşturmuş olsa bile bir servis talebinin üyelerini kaldıramaz.
  
  Kuruluşunuzda eBulma Yöneticileri istemenizin nedenleri için bkz. [Daha fazla bilgi](#more-information).

> [!NOTE]
> eBulma (Premium) kullanarak kullanıcının verilerini analiz etmek için kullanıcıya (verilerin koruyucusu) bir Office 365 E5 veya Microsoft 365 E5 lisansı atanmalıdır. Alternatif olarak, Office 365 E1 veya Office 365 ya da Microsoft 365 E3 lisansına sahip kullanıcılara Microsoft 365 E5 Uyumluluk veya Microsoft 365 eBulma ve Denetim eklentisi lisansı atanabilir. Olaylara üye olarak atanan ve verileri toplamak, görüntülemek ve analiz etmek için eKeşif (Premium) kullanan yöneticilerin, uyumluluk görevlilerinin veya yasal personelin E5 lisansına ihtiyacı yoktur. eKeşif (Premium) lisanslama hakkında daha fazla bilgi için bkz. [eKeşifte abonelikler ve lisanslama (Premium)](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>İzinleri atamadan önce

- Uyumluluk portalında eBulma izinlerini atamak için Kuruluş Yönetimi rol grubunun üyesi olmanız veya Rol Yönetimi rolüne atanmış olmanız gerekir.

- eBulma Yöneticisi rol grubundaki eBulma Yöneticileri alt grubunun üyesi olarak posta özellikli bir güvenlik grubu eklemek için Güvenlik & Uyumluluk Merkezi PowerShell'deki [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) cmdlet'ini kullanabilirsiniz. Ancak, eBulma Yöneticileri alt grubuna posta özellikli bir güvenlik grubu ekleyemezsiniz. Ayrıntılar için bkz. [Daha fazla bilgi](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>eKeşif izinleri atama

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalına</a> gidin ve izin atayabilen bir hesap kullanarak oturum açın.
  
2. Sol bölmede **İzinler'i** seçin.

3. **İzinler & Rolleri** sayfasında, **Uyumluluk merkezi'nin** altında **Roller'e** tıklayın.

4. **Uyumluluk merkezi rolleri** sayfasında **eBulma Yöneticisi'ni** seçin.
  
5. **eBulma Yöneticisi** açılır sayfasında, atamak istediğiniz eBulma izinlerine göre aşağıdakilerden birini yapın.
  
    **Kullanıcıyı eBulma Yöneticisi yapmak için:** **eBulma Yöneticisi'nin** yanında **Düzenle'yi** seçin. **eBulma Yöneticisi Seç** sihirbazı sayfasında Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Ekle'yi seçin**. eBulma yöneticisi olarak eklemek istediğiniz kullanıcıyı (veya kullanıcıları) ve ardından **Ekle'yi** seçin. Kullanıcı eklemeyi bitirdiğinizde **Bitti'yi** seçin. Ardından, **eBulma Yöneticisi'ni Seçin** sihirbazı sayfasında **Kaydet'i** seçerek değişiklikleri eBulma Yöneticisi üyeliğine kaydedin.
  
    **Kullanıcıyı eBulma Yöneticisi yapmak için:** **eBulma Yöneticisi'nin** yanındaki **Düzenle'yi** seçin. **eBulma Yöneticisi Seç** sayfasında Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Ekle'yi seçin**. **eBulma Yöneticisi** olarak eklemek istediğiniz kullanıcıyı (veya kullanıcıları) seçin ve ardından **Ekle'yi** seçin. Kullanıcı eklemeyi bitirdiğinizde **Bitti'yi** seçin. Ardından, **eBulma Yöneticisi'ni Seçin** sihirbazı sayfasında, eBulma Yöneticisi üyeliğindeki değişiklikleri kaydetmek için **Kaydet'i** seçin.
  
> [!NOTE]
> Bir kullanıcıyı **eBulma Yöneticisi yapmak için Add-eDiscoveryCaseAdmin** cmdlet'ini de kullanabilirsiniz. Ancak, bu cmdlet'i kullanarak eBulma Yöneticisi haline getirebilmeniz için önce kullanıcıya Servis Talebi Yönetimi rolü atanmalıdır. Daha fazla bilgi için bkz. [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
Uyumluluk portalındaki **İzinler** sayfasında, kullanıcılara eBulma ile ilgili izinleri Uyumluluk Yöneticisi, Kuruluş Yönetimi ve Gözden Geçiren rol gruplarına ekleyerek de atayabilirsiniz. Bu rol gruplarının her birine atanan eBulma ile ilgili RBAC rollerinin açıklaması için bkz. [eBulma ile ilgili RBAC rolleri](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>eBulma ile ilgili RBAC rolleri

Aşağıdaki tabloda uyumluluk portalında eBulma ile ilgili RBAC rolleri listelenir ve her rolün varsayılan olarak atandığı yerleşik rol grupları gösterilir.
  
| Rol | Uyumluluk Yöneticisi | eBulma Yöneticisi & Yöneticisi | Kuruluş Yönetimi | Inceleme |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Olay Yönetimi <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|İletişim <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Uyumluluk Araması <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|Veli <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Dışarı aktarma <br/> | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Tutun <br/>  |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |
|Önizleme <br/>  | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Gözden geçirin <br/>  | <br/> |![Onay işareti.](../media/checkmark.png) <br/> | <br/> |![Onay işareti](../media/checkmark.png) <br/> |
|RMS Şifre Çözme <br/>  ||![Onay işareti](../media/checkmark.png) <br/> |||
|Arama ve Temizleme <br/> | <br/> | <br/> |![Onay işareti](../media/checkmark.png)<br/> | <br/> |
||||||
  
Aşağıdaki bölümlerde, önceki tabloda listelenen eBulma ile ilgili RBAC rollerinin her biri açıklanmaktadır.

### <a name="case-management"></a>Olay Yönetimi

Bu rol, kullanıcıların uyumluluk portalında eBulma (Standart) ve eBulma (Premium) durumlarına erişimi oluşturmasına, düzenlemesine, silmesine ve denetlemesine olanak tanır. Daha önce açıklandığı gibi, **add-eDiscoveryCaseAdmin cmdlet'ini kullanarak eBulma** Yöneticisi yapabilmeniz için önce kullanıcıya Olay Yönetimi rolü atanmalıdır.

Daha fazla bilgi için bkz.:

- [eBulma ile Kullanmaya başlayın (Standart)](get-started-core-ediscovery.md)

- [eBulma (Premium) ile Kullanmaya başlayın](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>İletişim

Bu rol, kullanıcıların eBulma (Premium) olayında tanımlanan koruyucularla tüm iletişimleri yönetmesine olanak tanır. Bu, ayrı tutma bildirimleri oluşturmayı, anımsatıcıları saklamayı ve yönetime yükseltmeleri içerir. Kullanıcı ayrıca saklama bildirimlerini onaylayan koruyucuyu izleyebilir ve her koruyucu tarafından koruyucu olarak tanımlandığı durumlarla ilgili iletişimleri izlemek için kullanılan koruyucu portalına erişimi yönetebilir.

Daha fazla bilgi için bkz[. eBulma'da iletişimlerle çalışma (Premium)](managing-custodian-communications.md).

### <a name="compliance-search"></a>Uyumluluk Araması

Bu rol, kullanıcıların posta kutularını ve ortak klasörleri, çevrimiçi siteleri, SharePoint OneDrive İş sitelerini, Skype Kurumsal konuşmalarını, Microsoft 365 gruplarını ve Microsoft Teams ve Yammer arama yapmak için uyumluluk portalında İçerik Arama aracını çalıştırmasına olanak tanır  Grup. Bu rol kullanıcının arama sonuçlarıyla ilgili bir tahmin almasına ve dışarı aktarma raporları oluşturmasına olanak tanır, ancak arama sonuçlarını önizleme, dışarı aktarma veya silme gibi içerik arama eylemlerini başlatmak için başka roller gereklidir.

İçerik arama ve eBulma (Standart) bölümünde, Uyumluluk Araması rolüne atanmış ancak Önizleme rolüne sahip olmayan kullanıcılar, Önizleme rolü atanmış bir kullanıcı tarafından önizleme eyleminin başlatıldığı aramanın sonuçlarının önizlemesini görebilir. Önizleme rolü olmayan kullanıcı, ilk önizleme eylemi oluşturulduktan sonra iki haftaya kadar sonuçları önizleyebilir.

Benzer şekilde, İçerik arama ve eBulma (Standart) içinde Uyumluluk Araması rolüne atanmış ancak Dışarı Aktarma rolüne sahip olmayan kullanıcılar, Dışarı Aktarma rolü atanmış bir kullanıcı tarafından dışarı aktarma eyleminin başlatıldığı aramanın sonuçlarını indirebilir. Dışarı Aktarma rolü olmayan kullanıcı, ilk dışarı aktarma eylemi oluşturulduktan sonra iki haftaya kadar aramanın sonuçlarını indirebilir. Bundan sonra, Dışarı Aktarma rolüne sahip biri dışarı aktarmayı yeniden başlatmadığı sürece sonuçları indiremezler.

Arama sonuçlarını önizlemek ve dışarı aktarmak için iki haftalık yetkisiz kullanım süresi (karşılık gelen arama ve dışarı aktarma rolleri olmadan) eBulma (Premium) için geçerli değildir. eKeşif'te (Premium) içeriği önizlemek ve dışarı aktarmak için kullanıcılara Önizleme ve Dışarı Aktarma rolleri atanmalıdır.

### <a name="custodian"></a>Veli

Bu rol, kullanıcıların eBulma (Premium) olaylarında koruyucuları tanımlamasına ve yönetmesine ve Azure Active Directory ve diğer kaynaklardan gelen bilgileri, koruyucularla ilişkili veri kaynaklarını bulmak için kullanmasına olanak tanır. Kullanıcı posta kutuları, SharePoint siteler ve Teams gibi diğer veri kaynaklarını bir durumda koruyucularla ilişkilendirebilir. Kullanıcı, bir olay bağlamında içeriği korumak için koruyucularla ilişkili veri kaynaklarına yasal bir saklama da yapabilir.

Daha fazla bilgi için bkz. [eBulma'da (Premium) koruyucularla çalışma](managing-custodians.md).

### <a name="export"></a>Dışarı aktarma

Rol, kullanıcıların İçerik Aramasının sonuçlarını yerel bir bilgisayara dışarı aktarmasına olanak tanır. Ayrıca eBulma(Premium) içinde analiz için arama sonuçlarını hazırlamalarına da olanak tanır.

Arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz. [Arama sonuçlarını Microsoft Purview uyumluluk portalından dışarı aktarma](export-search-results.md).

### <a name="hold"></a>Tutun

Bu rol, kullanıcıların posta kutularına, ortak klasörlere, sitelere, Skype Kurumsal konuşmalara ve Microsoft 365 gruplarına ayrı tutmalarına olanak tanır. İçerik ayrı tutulduğunda içerik sahipleri özgün içeriği değiştirmeye veya silmeye devam edebilir, ancak ayrı tutma kaldırılana veya saklama süresi dolana kadar içerik korunur.

Ayrı tutmalar hakkında daha fazla bilgi için bkz:

- [eBulma'da ayrı tutma oluşturma (Standart)](create-ediscovery-holds.md) 

- [eBulma'da ayrı tutma oluşturma (Premium)](add-custodians-to-case.md)

### <a name="preview"></a>Önizleme

Bu rol, kullanıcıların İçerik Aramasından döndürülen öğelerin listesini görüntülemesine olanak tanır. Ayrıca, içindekileri görüntülemek için listedeki her öğeyi açabilir ve görüntüleyebilir.

### <a name="review"></a>Gözden geçirin

Bu rol, kullanıcıların [eBulma (Premium)](overview-ediscovery-20.md) içindeki gözden geçirme kümelerine erişmesini sağlar. Bu role atanan kullanıcılar, üyesi oldukları uyumluluk portalındaki **eBulma > Gelişmiş** sayfasında servis taleplerinin listesini görebilir ve açabilir. Kullanıcı bir eBulma (Premium) olayına eriştiğinde, olay verilerine erişmek için **Kümeleri gözden geçir'i** seçebilir. Bu rol, kullanıcının servis talebiyle ilişkili bir koleksiyon aramasının sonuçlarını önizlemesine veya diğer arama veya servis talebi yönetim görevlerini gerçekleştirmesine izin vermez. Bu role sahip kullanıcılar yalnızca bir gözden geçirme kümesindeki verilere erişebilir.

### <a name="rms-decrypt"></a>RMS Şifre Çözme

Bu rol, kullanıcıların arama sonuçlarının önizlemesini görüntülerken ve şifresi çözülmüş hak korumalı e-posta iletilerini dışarı aktarırken hakları korunan e-posta iletilerini görüntülemesini sağlar. Bu rol ayrıca, şifrelenmiş dosya eBulma aramasının sonuçlarına eklenmiş bir e-posta iletisine eklendiğinde kullanıcıların [Microsoft şifreleme teknolojisiyle](encryption.md) şifrelenmiş bir dosyayı görüntülemesine (ve dışarı aktarmasına) olanak tanır. Ayrıca, bu rol kullanıcıların eBulma(Premium) içindeki bir gözden geçirme kümesine eklenen şifrelenmiş e-posta eklerini gözden geçirmesine ve sorgulamasına olanak tanır. eBulma'da şifre çözme hakkında daha fazla bilgi için bkz. [Microsoft 365 eKeşif araçlarında şifre çözme](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Arama ve Temizleme

Bu rol, kullanıcıların içerik arama ölçütlerine uyan verileri toplu olarak kaldırmasını sağlar. Daha fazla bilgi için bkz [. Kuruluşunuzda e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>eBulma servis taleplerinin üyesi olarak rol grupları ekleme

Rol gruplarını eBulma (Standart) ve eBulma (Premium) olaylarının üyeleri olarak ekleyebilirsiniz, böylece rol gruplarının üyeleri atanan durumlarda görevlere erişebilir ve görevleri gerçekleştirebilir. Rol grubuna atanan roller, rol grubunun üyelerinin neler yapabileceğini tanımlar. Ardından bir rol grubunu servis talebinin üyesi olarak eklemek, üyelerin belirli bir durumda bu görevlere erişmesine ve bunları gerçekleştirmesine olanak tanır. Rol gruplarını servis taleplerinin üyesi olarak ekleme hakkında daha fazla bilgi için bkz:

- [eBulma ile Kullanmaya başlayın (Standart)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [eBulma (Premium) olayına üye ekleme veya kaldırma](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Bunu göz önünde bulundurarak, rol grubuna bir rol eklendiğinde veya bir rol grubundan kaldırıldığında, rol grubunun üyesi olduğu herhangi bir durumun üyesi olarak bu rol grubunun otomatik olarak kaldırılacağını bilmek önemlidir. Bunun nedeni, kuruluşunuzun bir olayın üyelerine yanlışlıkla ek izinler sağlamasını korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlardan kaldırılır.

eBulma olayının üyesi olabilecek bir rol grubuna rol eklemeden veya kaldırmadan önce, rol grubunun üyesi olduğu servis taleplerinin listesini almak için [Güvenlik & Uyumluluk PowerShell'de](/powershell/exchange/connect-to-scc-powershell) aşağıdaki komutları çalıştırabilirsiniz. Rol grubunu güncelleştirdikten sonra, rol grubunu bu servis taleplerinin bir üyesi olarak geri eklersiniz.

### <a name="get-a-list-of-ediscovery-standard-cases-a-role-group-is-assigned-to"></a>Rol grubunun atandığı eBulma (Standart) servis taleplerinin listesini alma

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-ediscovery-premium-cases-a-role-group-is-assigned-to"></a>Bir rol grubunun atandığı eBulma (Premium) servis taleplerinin listesini alma

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Daha fazla bilgi

- **Neden eBulma Yöneticisi oluşturasın?** Daha önce açıklandığı gibi, bir eBulma Yöneticisi, kuruluşunuzdaki tüm eBulma servis taleplerini görüntüleyebilen ve erişebilen eBulma Yöneticisi rol grubunun üyesidir. Tüm eBulma olaylarına erişme özelliğinin iki önemli amacı vardır:

  - Bir eBulma olayının tek üyesi olan bir kişi kuruluşunuzdan ayrılırsa, hiç kimse (Kuruluş Yönetimi rol grubunun üyeleri veya eBulma Yöneticisi rol grubunun başka bir üyesi dahil) bu eBulma olayına erişemez çünkü bir servis talebinin üyesi değildir. Bu durumda, bu durumda verilere erişmenin hiçbir yolu yoktur. Ancak bir eBulma Yöneticisi kuruluştaki tüm eBulma olaylarına erişebildiğinden, olayı görüntüleyebilir ve kendisini veya başka bir eBulma yöneticisini davanın üyesi olarak ekleyebilir.

  - Bir eBulma Yöneticisi tüm eBulma (Standart) ve eBulma (Premium) servis taleplerini görüntüleyebilir ve bunlara erişebildiğinden, tüm servis taleplerini ve ilişkili uyumluluk aramalarını denetleyebilir ve denetleyebilir. Bu, uyumluluk aramalarının veya eBulma durumlarının kötüye kullanılmasını önlemeye yardımcı olabilir. eBulma Yöneticileri uyumluluk aramasının sonuçlarında hassas olabilecek bilgilere erişebildiğinden, eBulma Yöneticisi olan kişi sayısını sınırlamanız gerekir.

- **eBulma Yöneticisi rol grubunun üyesi olarak bir grup ekleyebilir miyim?** Daha önce açıklandığı gibi, Güvenlik & Uyumluluk Merkezi PowerShell'de **Add-RoleGroupMember** cmdlet'ini kullanarak eBulma Yöneticisi rol grubundaki eBulma Yöneticileri alt grubunun üyesi olarak posta etkin bir güvenlik grubu ekleyebilirsiniz. Örneğin, eBulma Yöneticisi rol grubuna posta özellikli bir güvenlik grubu eklemek için aşağıdaki komutu çalıştırabilirsiniz. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange dağıtım grupları ve Microsoft 365 Grupları desteklenmez. Exchange Online PowerShell'de komutunu çalıştırarak `New-DistributionGroup -Type Security`oluşturabileceğiniz posta özellikli bir güvenlik grubu kullanmanız gerekir. Ayrıca, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde veya Microsoft 365 yönetim merkezi</a> posta özellikli bir güvenlik grubu oluşturabilir (ve üye ekleyebilirsiniz[).](https://go.microsoft.com/fwlink/p/?linkid=2024339) Yeni posta özellikli bir güvenlik grubunun eBulma Yöneticileri rol grubuna eklenmesi 60 dakika kadar sürebilir.

    Daha önce belirtildiği gibi, Güvenlik & Uyumluluk Merkezi PowerShell'de **Add-eDiscoveryCaseAdmin** cmdlet'ini kullanarak posta özellikli bir güvenlik grubunu eBulma Yöneticisi yapamazsınız. Tek tek kullanıcıları yalnızca eBulma Yöneticileri olarak ekleyebilirsiniz.

    Posta özellikli bir güvenlik grubunu da servis talebinin üyesi olarak ekleyemezsiniz.
