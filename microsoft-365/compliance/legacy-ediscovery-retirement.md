---
title: Eski eBulma araçlarının emeklilik
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place'daki eBulma ve In-Place Tutma (ve ilgili PowerShell cmdlet'leri) Exchange Online, 2020'nin ilk yarısında devreden kaldıracağız. AyrıcaSearch-Mailbox v1.0 cmdlet'i ve Advanced eDiscovery cmdlet'i de aynı süre içinde kaldıracak.
ms.openlocfilehash: f778a31580bb908205c707c1f613f49bd6a576d1
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990596"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Eski eBulma araçlarının emeklilik

> [!IMPORTANT]
> Bu makalede açıklanan eski eBulma araçlarının işlevselliği, Microsoft 365 hizmetten kaldırılmış veya hala kullanılabilir ancak artık desteklenmiyor. Hala kullanılabilir durumda olan tüm işlevler bildirim olmadan kaldırılabilir. Bu eski araçlardan birini kullanmaya devam ediyorsanız, aşağıdaki makaledeki eBulma araçlarına Microsoft 365 uyumluluk merkezi alternatiflerden birini kullanmayı göz önünde bulundurabilirsiniz.

Microsoft yıllar boyunca, Microsoft bu sitelerden e-posta içeriğini aramanızı, önizlemenizi ve dışarı aktarmanızı Exchange Online. Bununla birlikte, bu araçlar artık SharePoint Online ve Microsoft 365 Grupları gibi diğer Microsoft 365 hizmetlerde yer alan ve Exchange olmayan içerikleri aramanın etkili bir yolunu sunamaz. Microsoft bu konuda bilgi için çok çeşitli eBulma araçları sunmaktadır. Bu araçlar, çeşitli eBulma Microsoft 365 sunar. Ayrıca bu yılki en güncel ve güçlü eKbulma işlevini de bir bütün olarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi.</a> Bu, kuruluşların birçok kuruluş hizmeti genelinde içerikle ilgili yasal, şirket içi ve diğer belge isteklerine (örneğin, şirket içi Microsoft 365 yanıt Exchange Online.

Microsoft 365 uyumluluk merkezi'daki bu yeni ve geliştirilmiş eBulma işlevinin sonucu olarak, Exchange Online ve Exchange Online'ta e-posta içeriği aramayla ilgili aşağıdaki eBulma ile ilgili özellikleri ve işlevleri kullanımdan Microsoft 365:

- [Yönetim merkezinde Yerinde eKbulma](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) [ve Yerinde](/exchange/security-and-compliance/create-or-remove-in-place-holds) 1 Exchange 1.

- eK Exchange Online ve In-Place Holds'i destekleyen PowerShell cmd In-Place let'leridir (bu cmdlet'ler toplu olarak **-MailboxSearch* cmdlet'leri olarak tanımlanır). Bu cmdlet'ler şunları içerir:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) and [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) cmdlet'leri diğer ****-MailboxSearch*** cmdlet'leri kullanımdan kaldırıldıktan sonra kullanılabilir, böylece diğer eBulma ve tutma araçlarına geçişken yardımcı olması için bunları kullanabilirsiniz. Ancak, belirli bir tarihten (aşağıdan aya anın) sonra Microsoft Desteği artık bu iki cmdlet'i desteklemez.

- [PowerShell'de Search-Mailbox](/powershell/module/exchange/search-mailbox) cmdlet'Exchange Online.

- Web Hizmetleri API'sinde Exchange işlemler:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Office 365 Gelişmiş eKeşif v1.0](./overview-ediscovery-20.md), bu sürümde Advanced eDiscovery Çekirdek eKbulma durumu aracılığıyla erişilen ilk Microsoft 365 uyumluluk merkezi. Advanced eDiscovery v1.0'ın emeklilik, Çekirdek eKbulma olaylarını oluşturma ve yönetme becerinizi etkilemez.

> [!NOTE]
> Kullanımdan kaldırilen eBulma işlevselliği yalnızca bulut tabanlı Microsoft 365 sürümleri ve Office 365. Exchange ve SharePoint şirket içi sürümlerindeki eKbulma işlevselliği, daha fazla bildirime kadar desteklanmaya devam destekleyecektir.

Bu makalenin aşağıdaki bölümlerinde, her özelliğin devre dışı bırakıldıktan sonraki bölümleri sağlanmıştır. Bu bilgiler arasında, kullanımdan kaldıran araç yerine kullanabileceğiniz zaman çizelgeleri ve alternatif araçlar da yer almaktadır.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place merkezinde eBulma ve In-Place 10 Exchange 1 

1 Temmuz 2017'de yapılan özgün duyuruda olduğu gibi In-Place Yönetim Merkezi'nde (EAC) Exchange & eBulma veya Tutma işlevselliği kullanımdan kaldır ediliyor. EACIn-Place yer alan & Bulma Bulma Ve Tutma sayfası, EAC'den içeriği aramanızı, tutmanızı ve dışarı aktarmanızı Exchange Online. In-Place eBulma, sizin veya diğer eBulma yöneticilerinin içeriği gözden geçirebilirsiniz ve yasal, mevzuatla ilgili ve genel taleplerde kullanılabilir hale gelebilirsiniz.

Tüm bu özellikler (arama sonuçlarını bulma posta kutusuna kopyalama dışında) artık içerik aramalarında da sağ olduğundan, [Microsoft 365 uyumluluk merkezi'te](./microsoft-365-compliance-center.md) eBulma ve Advanced eDiscovery araçları (gelişmiş işlevsellik, güvenilirlik ve çok çeşitli özelliklerle) Microsoft 365  hizmetleri için en kısa zamanda bu araçları kullanmaya başlamayı öneririz. Diğer eBulma araçlarına geçişte size yardımcı olmak için, aşağıdaki tabloda eBulma ve Askıya In-Place yerine kullanabileceğiniz In-Place listelenmiştir.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşlar

- Office 365 ve Microsoft 365 Eğitim için

- Office 365 ve Microsoft 365 Kamu kuruluşları için; buna GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline-for-retirement"></a>Emeklilik için zaman çizelgesi

- 1 Temmuz 2020: Yeni arama ve 1 Temmuz 2020 oluşturamanıza rağmen, var olan aramaları çalıştırmaya, düzenlemeye ve silmeye devam etme riski size aittir. Microsoft Desteği artık EAC'In-Place eKbulma ve & 12/2013'te Destek hizmetine sahip olmayacaktır.

- 1 Ekim 2020: EAC'In-Place eBulma & 12 Ekim 1916'da salt okunur moda yerleştirilir. Bu, yalnızca var olan aramaları ve 1.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırilen mevcut işlevleri değiştirmek için kullanabileceğiniz diğer araçlar açık almaktadır.

<table>
<thead>
<tr class="header">
<th>İşlevsellik</th>
<th>Alternatif araç</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Yasal amaçlarla arama, dışarı aktarma ve tutma</td>
<td>Çalışma 2013'te temel eKbulma Microsoft 365 uyumluluk merkezi </td>
<td><p>Çekirdek eBulma servis durumlarının özelliklerini kullanmak, eKbulma ve 10 12/1 11'In-Place işlevsel In-Place sağlar. Bu şunları içerir:</p>
<ul>
<li>
<p>Arama milyonlarca konuma ölçeklendir ediliyor</p>
</li>
<li>
<p>Yüksek güvenilirlikte arama, dışarı aktarma ve içeriği tutma</p>
</li>
<li>
<p>Exchange Online, SharePoint Online, OneDrive İş, Skype Kurumsal, Microsoft Teams, Yammer Grupları, Microsoft 365 grupları ve diğer içerik için içerik arama Office 365 uygulamalarında depolanan</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Bekletme amacıyla tutma</td>
<td>Microsoft 365 uyumluluk merkezi'de bekletme Microsoft 365 uyumluluk merkezi</td>
<td><p>İçeriği korumak ve  istediklerinizi bekletme süresi dolduktan sonra silmek için Bekletme ilkelerini kullanabilirsiniz. Diğer özellikler şunlardır:</p>
<ul>
<li>
<p>Tüm kuruluşa ilke uygulama </p>
</li><li>
<p>Exchange Online, SharePoint Online, OneDrive İş, Skype Kurumsal, Microsoft Teams ve Office 365 grupları gibi belirli içerik konumlarına ilke Office 365</p></li>
<li>
<p>Belirli kullanıcılara ilke uygulama</p></li></ul>
<p>Daha fazla bilgi için bkz <a href="/microsoft-365/compliance/retention-policies"> . Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinebilirsiniz</a>.</td>
</tr>
<tr class="odd">
<td>E-posta arama sonuçlarını gözden geçirme için bir bulma posta kutusuna kopyalama</td><td>v2.0 Advanced eDiscovery gözden geçirme kümeleri</td>
<td><p>E-Microsoft 365 gözden geçirmek hiç bu kadar kolay olmamıştı. Gözden geçirme kümeleri, gözden geçirmeniz gereken zaman ve veri miktarını azaltmaya yardımcı olmak için birçok harika özellik içerir:</p>
<ul>
<li><p>Hızlı arama sorguları gerçekleştirme ve gözden geçirme kümesinde içeriği filtreleme</p></li>
<li><p>Gözden geçirme kümesi içeriğini çözümleme; bu, e-posta dizisini, yakın yineleme algılamayı, Temalar çözümlemesini ve Tahmine Dayalı kodlamayı içerir</p></li>
<li><p>Gözden geçirme kümesinde belgeleri etiketleme</p></li>
<li><p>Avukat istemcisi ayrıcalık içeriğini belirlemeye yardımcı olmak için önerileri etiketleme</p></li></ul>
<p>Daha fazla bilgi için bkz<a href="/microsoft-365/compliance/overview-ediscovery-20">. Advanced eDiscovery çözüme genel Microsoft 365</a>.</p>
<p>
<p>Alternatif olarak, arama sonuçlarını PST dosyalarına aktarabilirsiniz ve ardından PST Microsoft 365 aktarma hizmetini kullanarak PST'leri bir bulma posta kutusuna aktarabilirsiniz. Adım adım yönerge için bkz. <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">PST dosyalarını içeri aktararak ağ karşıya Office 365</a>.
</tr>
<tr class=even>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postası için erişim vermek için (örneğin, bir çalışan kuruluşdan ayrıldığında ve başka bir kişiye eski çalışanın e-postası için erişim izni vermeniz gibi), o kişiye eski çalışanın posta kutusuna erişim izinleri atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kullanıcıya kaynak posta kutusuna erişmek için gereken izinleri atamanız yeterli olur.</td>
  
  </tr>
<tr class="odd">
<td>Kurtarılabilir Öğeler klasöründen öğeleri geri yükleme</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Bir öğenin silinmiş öğe bekletme süresi dolmamışsa, <i></i> posta kutularında kalıcı olarak silinmiş öğeleri (geçici silinmiş öğeler olarak da bilinir) geri yükleyebilirsiniz. Daha fazla bilgi için bkz<a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">. Dosya'daki Kurtarılabilir Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>eBulma ve In-Place Hakkında SSS In-Place

**EAC'de eBulma ve 1In-Place bulma posta kutusuna arama sonuçlarını kopyalamak için EAC'de eBulma ve 1& Sahibi olmak için arama sonuçlarını kopyalama işlevini kullanabilirim. Şu anda hangi seçeneklerim var?**

Bugün bu işlevi çoğaltmanın iki yolu vardır. İlki [v2.0'da Advanced eDiscovery kümelerini kullanmak.](./view-documents-in-review-set.md) Gözden geçirme kümeleri; belgeleri hızlı arama, etiketleme, e-posta zincirleme, yinelenen gruplama, temalar çözümlemesi ve tahmine dayalı kodlama gibi geleneksel gözden geçirme araçlarında gördüğünüz becerilerin birçoğunu içerir. İncelemek üzere bulma posta kutularını kullanmaya devam etmek istemiyorsanız, ikinci seçenek arama sonuçlarını PST dosyalarına dışarı aktararak daha sonra Microsoft uyumluluk merkezinde PST içeri aktarma özelliğini kullanarak [bu PST](use-network-upload-to-import-pst-files.md) dosyalarını bir bulma posta kutusuna aktarmanızdır.

**eBulma yöneticisinin yeni araçları kullanarak hangi içerik konumlarını (örneğin, posta kutuları veya siteler) aray olaylarını nasıl kontrol  yapabilirim?**

Bu Microsoft 365 uyumluluk merkezi, bir [eBulma](set-up-compliance-boundaries.md) Yöneticisi'nin hangi içerik konumlarını aray az önce alıktır diğer içerik konumlarını kontrol etmek için uyumluluk sınırlarını da kullanır. Uyumluluk sınırları, coğrafi okurya saygı göstermesi gereken, aracı sınırları içinde kalması gereken kamu kuruluşlarında veya çok uluslu kuruluşlarda yararlıdır.

**Geçerli aramalarımı ve 10. sayfayı nasıl Microsoft 365 uyumluluk merkezi?**

PowerShell kullanarak eBulma In-Place ve 10 AAC'den de ayrı olarak geçiş yapmak mümkündür. Yönergeler için bkz[. EAC'den arama ve 100'e Microsoft 365 uyumluluk merkezi](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlet'leri

Exchange yönetim merkezinde 1 Temmuz 2017'de duyuru yapılan özgün bildirime göre, In-Place eBulma & **\*** Hold işlevselliği ve ilgili -MailboxSearch cmdlet'leri kullanımdan kaldır ediliyor. Bu cmdlet'ler kullanıcılara yasal, mevzuat ve genel istekler için posta kutusu içeriğini arama, tutma ve dışarı aktarma olanağı sağlar.

Bu özellikler artık gelişmiş performans ve [<span class="underline">ölçeklenebilirlik özellikleriyle Microsoft 365 uyumluluk merkezi</span>](./microsoft-365-compliance-center.md) ve Office 365 Güvenlik & Uyumluluk Merkezi PowerShell'de de mevcut olduğundan, bu geliştirilmiş cmdlet'leri kullanabillisiniz. Bu cmdlet'ler [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) ve [<span class="underline">\*-ComplianceSearchAction'dır</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşlar

- Office 365 ve Microsoft 365 Eğitim için

- Office 365 ve Microsoft 365 Kamu kuruluşları için; buna GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: Yeni In-Place **eBulma** aramaları ve In-Place 12020 araması oluşturmak için Yeni Posta Kutusu Arama'yı kullanamayabilirsiniz, ancak cmdlet'leri kullanarak var olan arama ve 3. Microsoft Desteği artık bu tür aramalar ve sıyrılar için yardım sağlamaz.

- 1 Ekim 2020: Daha önce de belirtildiği gibi, EAC'In-Place eBulma veya 1& 100 1000 100127 tarihinde salt okunur moda yerleştirilir. Bu, Yeni Posta Kutusu Araması, Posta Kutusu Arama Başlat veya **Set-MailboxSearch** cmdlet'lerini **de** kullanmayacak anlamına gelir. Yalnızca var olan aramaları ve 6.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırilen mevcut işlevleri değiştirmek için kullanabileceğiniz diğer araçlar açık almaktadır.

<table>
<thead>
<tr class="header">
<th>İşlevsellik</th>
<th>Alternatif araçlar</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Arama ve verme</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>İçeriği aramanıza ve dışarı aktarmanıza yardımcı olmak için ComplianceSearch ve ComplianceSearchAction cmdlet'leri birlikte çalışır. Yeni, Get<strong>-, Start-ComplianceSearch</strong> cmdlet'lerini <strong></strong>kullanarak yeni bir <strong></strong>arama oluşturabilir ve arama tahminini görüntüabilirsiniz. Ardından, arama sonuçlarını <strong>dışarı aktaran New-ComplianceSearchAction</strong> cmdlet'ini kullanabilirsiniz. Bu arama sonuçlarını yerel bilgisayarınıza indirmek için çalışma Microsoft 365 uyumluluk merkezi temel eBulma aracını kullanmaya devam etmek zorunda kaldınız.</p>
<p>
<p><strong>Not:</strong> Bu cmdlet'leri çekirdek eBulma durumuyla ilişkili olmayan aramalar oluşturmak için kullanırsanız, bu aramalar çalışma sayfasının İçerik arama Microsoft 365 uyumluluk merkezi.<strong></strong></p></td>
</tr>
<tr class="even">
<td>Posta kutusunda içeriği tutma</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Uyumluluk Microsoft 365 uyumluluk merkezi Bir ComplianceCase ile ilişkilendirilmek gerekir. İlk olarak uyumluluk durumu oluşturun ve ardından bir CaseHoldPolicy ve CaseHoldRule oluşturun.</p>
<p><strong>Not:</strong> CaseHoldRule oluşturmadan CaseHoldPolicy oluşturmak, CaseHoldRule oluşturulana ve CaseHoldPolicy ile ilişkilendirilene kadar tutmada çalışmaz duruma gelir. Daha fazla bilgi için cmdlet belgelerine bakın.</p></td>
</tr>
<tr class="odd">
<td>Arama sonuçlarını bulma posta kutusuna kopyalama</td>
<td>Yok</td>
<td>Bu işlevin yerine doğrudan hiçbir değişiklik olmaz, çünkü tüm posta hizmetleri için Microsoft 365 sağlamaz. Alternatif çözümler için aşağıdaki SSS bölümüne bakın.</td>
</tr>
  <tr class=even>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postası için erişim vermek için (örneğin, bir çalışan kuruluşdan ayrıldığında ve başka bir kişiye eski çalışanın e-postası için erişim izni vermeniz gibi), o kişiye eski çalışanın posta kutusuna erişim izinleri atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kaynak posta kutusuna erişim için kullanıcı izinlerini atamanız yeterli olur.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>***-MailboxSearch cmdlet'leri** hakkında SSS

**Diğer eBulma ve yasal soruşturmalar amacıyla e-posta iletilerini veya anlık mesajları dışarı göndermek için Arama Kopyala'ya kullanıyoruz. Bu cmdlet'ler kaldırıldıktan sonra başka hangi seçeneklerimiz var?**

[<span class="underline">Microsoft Graph API'leri</span>](https://developer.microsoft.com/en-us/graph)**\*, -MailboxSearch** cmdlet'lerinin kullanımına göre çok daha esnek ve ölçeklenebilir olan çözümleme amacıyla ve diğer amaçlarla verileri ayıklamak için bir dizi yöntem sağlar.

**Aramalarımı ve aramalarımı diğer kullanıcıya Microsoft 365 uyumluluk merkezi?**

Bir PowerShell betiği In-Place eBulma aramalarını ve Exchange yönetim merkezinden geçirmeniz mümkündür. Daha fazla bilgi için bkz[. Eski eBulma aramalarını ve 12 Microsoft 365 uyumluluk merkezi](migrate-legacy-eDiscovery-searches-and-holds.md).

**Cmdlet'ler kaldırıldıktan sonra da aramaları kaldırabilir miyim veya alabilir miyim?**

Evet, arama oluşturma ve değiştirme becerisini kaldır olsak da, daha fazla bildirime kadar **Get-MailboxSearch** ve **Remove-MailboxSearch** özelliklerini kullanmaya devamabileceksiniz. Bununla birlikte, kullanımdan kalma tarihlerinin ardından bu cmdlet'lerin kullanımı sizin riskinize girer ve Microsoft Desteği artık yardım sağyamaz.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet'i

Exchange Online PowerShell'de **Search-Mailbox** cmdlet'i, 2018'den başlayarak cmdlet çıktısinde ilk olarak duyurulmuştu. **Search-Mailbox** cmdlet'i ilk olarak kullanıcının posta kutusunda arama yapmak ve kötü amaçlı içeriği temizlemek için kullanılır. İçeriği aramak ve temizlemek için, Office 365  Güvenlik & ve Uyumluluk Merkezi PowerShell'de Yeni Uyumluluk Arama ve Yeni Uyumluluk **içinSearchAction** cmdlet'lerini kullanmaya başlamanızı öneririz. Yerleşik güvenlik deneyimi için, güvenlik [<span class="underline">Microsoft 365 e-posta</span>](../security/index.yml) için güçlü tehdit koruması ve diğer birçok özellik Microsoft hizmetleri.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşlar

- Office 365 ve Microsoft 365 Eğitim için

- Office 365 ve Microsoft 365 Kamu kuruluşları için; buna GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

-  1 Temmuz 2020: Artık **Arama-Posta** Kutusu cmdlet'i kullanılamaz ve Microsoft Desteği artık yardım sağlamaz.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırilen mevcut işlevleri değiştirmek için kullanabileceğiniz diğer araçlar açık almaktadır.

<table>
<thead>
<tr class="header">
<th>İşlevsellik</th>
<th>Alternatif araçlar</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Posta kutusunda arama</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>İçeriği aramanıza ve dışarı aktarmanıza yardımcı olmak için ComplianceSearch ve ComplianceSearchAction cmdlet'leri birlikte çalışır. Yeni, Get<strong>-, Start-ComplianceSearch</strong> cmdlet'lerini <strong></strong>kullanarak yeni bir <strong></strong>arama oluşturabilir ve arama tahminini görüntüabilirsiniz. Ardından, arama sonuçlarını <strong>dışarı aktarmayı sağlamak için New-ComplianceSearchAction -Export</strong> komutunu kullanabilirsiniz. Bu arama sonuçlarını yerel bilgisayarınıza indirmek için çalışma Microsoft 365 uyumluluk merkezi temel eBulma aracını kullanmaya devam etmek zorunda kaldınız.</p></p>
</td>
</tr>
<tr class="even">
<td>Posta kutusundan toplu e-postayı silme</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Posta kutuları için arşivleme ve silme ilkesi ayarlama</span></a></p>
<p></p></td>
<td><p>Yöneticiler, öğeleri otomatik olarak kullanıcının arşiv posta kutusuna taşır ve öğeleri posta kutusundan otomatik olarak silen bir arşivleme ve silme ilkesi oluşturabilir.</p>
</td>
</tr>
<tr class="even">
<td>Arama sonuçlarını bulma posta kutusuna kopyalama</td>
<td> </td>
<td>Bu işlevin yerine doğrudan hiçbir değişiklik olmaz, çünkü tüm posta hizmetleri için Microsoft 365 sağlamaz. Alternatif çözümler için <strong>*-MailboxSearch cmdlet'leri bölümünde SSS</strong> bölümüne bakın. </td>
</tr>
<tr class=odd>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postası için erişim vermek için (örneğin, bir çalışan kuruluşdan ayrıldığında ve başka bir kişiye eski çalışanın e-postası için erişim izni vermeniz gibi), o kişiye eski çalışanın posta kutusuna erişim izinleri atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kullanıcıya kaynak posta kutusuna erişim izni atamanız gerekir.</td>
</tr>
<tr class=even>
  <td>İletileri posta kutusundan temizleme</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>İçeriği aramanıza ve temizlemenizi sağlamak için ComplianceSearch ve ComplianceSearchAction cmdlet'leri birlikte çalışır. Yeni Uyumluluk arama ve Yeni Uyumluluklu <strong>Arama cmdlet'leriyle</strong> arama oluşturabilir ve çalıştırabilirsiniz, ardından <strong>New-ComplianceSearchAction -PurgeType</strong> komutunu kullanarak içeriği temizebilirsiniz.<strong></strong> Daha fazla bilgi için bkz <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">. İletileri arama ve silme</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>İletileri posta kutusundan temizleme</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
<td>İletileri bir posta kutusundan temizlemek için, yönetici izinlerini çalışanın posta kutusuna erişme izni verin. İletiler silinebilir ve gerektiğinde içinde yerleşik arama ve görüntüleme özelliklerini kullanarak geri Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange Hizmetleri API işlemlerini kullanma

Exchange Web Hizmetleri API'sinde bulunan bu işlemler, Exchange yönetim merkezinde In-Place eBulma & **\*** 100 10 711 cmdlet'leri ve Exchange Online PowerShell'de bunlara karşılık gelen -MailboxSearch cmdlet'leri tarafından kullanılır. Ayrıca, diğer eski eKbulma araçlarının bir parçası olarak da kaldır kaldır olurlar.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşlar

- Office 365 ve Microsoft 365 Eğitim için

- Office 365 ve Microsoft 365 Kamu kuruluşları için; buna GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes ve GetHoldOnMailboxes işlemleri artık kullanılamaz ve Microsoft Desteği artık yardım sağlamaz.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery v1.0

Advanced eDiscovery Advanced eDiscovery'e tıklayarak temel bir eKbulma durumunda kullanılabilen Advanced eDiscovery v1.0 sürümü devre Advanced eDiscovery kaldır ediliyor. İşlevselliği, yeni çözüm [Advanced eDiscovery tarafından](./ediscovery.md) Microsoft 365 uyumluluk merkezi.

Kuruluş v1.0 için Advanced eDiscovery belirlemek için:

1. Çalışma Microsoft 365 uyumluluk merkezi **, eKoveryCore** >  öğesini seçin ve Core eKovery case'i açın.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. Yeni sürüme **geç Advanced eDiscovery** düğmesini görüyorsanız bu düğmeye tıklarsanız, Advanced eDiscovery'in 1.0 sürümüne ulaşabilirsiniz. Core eKover'da vakaları oluşturma ve yönetme özelliği bundan etkilenmez. v1.0'da yalnızca Advanced eDiscovery verileri ekleme ve çözümleme özelliği (Geçiş'e **Advanced eDiscovery seçeneğine** tıklayarak) devreden kaldır edilir.

Microsoft 365'daki yeni Advanced eDiscovery çözümü (*Advanced eDiscovery v2.0* olarak da bilinir), özgün çözümün tüm özelliklerini sağlar, ancak şimdi diğer çözümlerde içeriği tanımlamaya yönelik özel özellik tabanlı bir yaklaşım Microsoft 365  hakkında daha fazla bilgi sağlar, içeriği toplar ve gözden geçirenlerin uygun belgeleri gözlerden geçirmelerine yardımcı olmak için hızlı arama sorgularının, etiketlemenin ve çözümleme özelliklerinin avantajlarını elde edecekleri bir gözden geçirme kümesine ekler. Advanced eDiscovery hem Microsoft hem de Microsoft dışı dosya türleri için gelişmiş işleme ve yerel görüntüleyiciler içeren dosya türlerinin tam listesi hazır ve desteklenen meta veri alanları [burada](./document-metadata-fields-in-advanced-ediscovery.md).[](./supported-filetypes-ediscovery20.md) Ayrıca yeni Advanced eDiscovery çözümü, farklı hizmetlerde bulunan içeriğe göz adanma uygulama, kullanıcılara mızrı bildirme ve özel durum durumlarının hepsini izlemenizi sağlayan güçlü bir custo bir yönetim özelliği Advanced eDiscovery sağlar.

v2.0 Advanced eDiscovery erişmek için:

Seçenekler'e Microsoft 365 uyumluluk merkezi **, eDiscoveryAdvanced'i** >  seçin ve Core eKovery olaylarını açın.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

Şu anda, eBulma iş akışınızı yeni çalışma haftası işlevselliğine Advanced eDiscovery öneririz. Gerekirse, içeriği dışarı aktararak ve Advanced eDiscovery depolayarak 1.0 servis Advanced eDiscovery arşivlayabilirsiniz. 31 Aralık 2020'ye kadar mevcut durumlarda Advanced eDiscovery v1.0'a erişmeye devam etmene rağmen, Microsoft Desteği 1 Ekim 2020'den sonra destek sağlamaz. Daha fazla ayrıntı için aşağıdaki zaman çizelgesine bakın.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşlar

- Office 365 ve Microsoft 365 Eğitim için

- Office 365 ve Microsoft 365 Kamu kuruluşları için; buna GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: v1.0 için yeni Advanced eDiscovery dosya oluşturabileceksiniz.

- 1 Ekim 2020: Herhangi bir vakaya yeni veri (Arama sonuçlarını Özel arama Advanced eDiscovery) ekleyemz. Mevcut durumlarda verilerle çalışmaya devam etmek için riski size aittir. Microsoft Desteği artık yardım sağlamaz. 

- 31 Aralık 2020: v1.0 Advanced eDiscovery erişesiniz.

### <a name="alternative-tools"></a>Alternatif araçlar

En [Advanced eDiscovery çözüm](./overview-ediscovery-20.md) Microsoft 365 uyumluluk merkezi.