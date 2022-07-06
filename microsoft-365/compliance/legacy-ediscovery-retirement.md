---
title: Eski eBulma araçları kullanımdan kaldırıldı
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: Exchange Online In-Place eBulma ve In-Place Tutma (ve ilgili PowerShell cmdlet'leri) 2020'nin ilk yarısında kullanımdan kaldırılacaktır. Search-Mailbox cmdlet ve Microsoft Purview eKeşif (Premium) v1.0 da aynı süre içinde kullanımdan kaldırılıyor.
ms.openlocfilehash: 630d72c75f318e6d4f9e68b01c61d5069958a0a1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636083"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Eski eKeşif araçlarını kullanımdan kaldırma

> [!IMPORTANT]
> Bu makalede açıklanan eski eBulma araçlarının işlevselliği Microsoft 365 hizmetinden kaldırılmıştır veya hala kullanılabilir durumdadır ancak artık desteklenmez. Hala kullanılabilir olan tüm işlevler bildirimde bulunulmadan kaldırılabilir. Bu eski araçlardan herhangi birini kullanmaya devam ediyorsanız, Microsoft Purview uyumluluk portalı veya bu makalede açıklanan alternatiflerden biri olan eBulma araçlarına geçiş yapmayı göz önünde bulundurun.

Microsoft, yıllar içinde e-posta içeriğini Exchange Online aramanıza, önizlemenize ve dışarı aktarmanıza olanak sağlayan eBulma araçları sağlamıştır. Ancak bu araçlar artık SharePoint Online ve Microsoft 365 Grupları gibi diğer Microsoft 365 hizmetlerinde Exchange dışı içerik aramanın etkili bir yolunu sunmaz. Bu sorunu çözmek için Microsoft, çok çeşitli Microsoft 365 içeriği aramanıza yardımcı olan diğer eBulma araçları sunar. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalında</a> en güncel ve güçlü eBulma işlevselliğini birleştirmek için çok çalışıyoruz. Bu, kuruluşların Exchange Online dahil olmak üzere birçok Microsoft 365 hizmeti genelindeki içerikle ilgili yasal, dahili ve diğer belge isteklerine yanıt vermelerini sağlar.

Uyumluluk portalındaki bu yeni ve geliştirilmiş eBulma işlevinin bir sonucu olarak, Exchange Online ve Microsoft 365'te e-posta içeriğini aramayla ilgili aşağıdaki eBulma ile ilgili özellikleri ve işlevleri kullanımdan kaldırıyoruz:

- Exchange yönetim merkezinde [Yerinde eKeşif](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) ve [Yerinde Tutmalar](/exchange/security-and-compliance/create-or-remove-in-place-holds).

- In-Place eBulma ve In-Place Tutmalarını destekleyen Exchange Online PowerShell cmdlet'leri (bu cmdlet'ler topluca **-MailboxSearch* cmdlet'leri olarak tanımlanır). Bu, aşağıdaki cmdlet'leri içerir:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Diğer ***-MailboxSearch** cmdlet'leri kullanımdan kaldırıldıktan sonra [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) ve [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) cmdlet'leri kullanılabilir. Böylece bunları kullanarak diğer eBulma ve saklama araçlarına geçişinizde yardımcı olabilirsiniz. Ancak, belirli bir tarihten sonra (aşağıda belirtilmiştir) Microsoft Desteği artık bu iki cmdlet'i desteklemeyecektir.

- Exchange Online PowerShell'deki [Search-Mailbox](/powershell/module/exchange/search-mailbox) cmdlet'i.

- Exchange Web Hizmetleri API'sinde aşağıdaki işlemler:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [Arama Posta Kutuları](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- uyumluluk portalındaki bir Microsoft Purview eKeşif (Standart) durum üzerinden erişilen ilk eBulma (Premium) sürümü olan Microsoft Purview eKeşif ([Premium) v1.0](./overview-ediscovery-20.md). eKeşif (Premium) v1.0'ın kullanımdan kaldırılması, eBulma (Standart) servis taleplerini oluşturma ve yönetme becerinizi etkilemez.

> [!NOTE]
> Kullanımdan kaldırılan eBulma işlevi yalnızca Microsoft 365 ve Office 365'nin bulut tabanlı sürümleri için geçerlidir. Exchange ve SharePoint'in şirket içi sürümlerindeki eBulma işlevselliği bir sonraki bildirime kadar desteklenmeye devam edecektir.

Bu makaledeki aşağıdaki bölümler, kullanımdan kaldırılan her özellik hakkında rehberlik sağlar. Kullanımdan kaldırılacak araç yerine kullanabileceğiniz zaman çizelgeleri ve alternatif araçlar da dahil olmak üzere bu bilgiler.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>Exchange yönetim merkezinde eBulma ve In-Place Tutma In-Place 

1 Temmuz 2017'deki özgün duyuruya göre, Exchange yönetim merkezindeki (EAC) In-Place eBulma & Tutma işlevi kullanımdan kaldırılıyor. EAC'deki In-Place eBulma & Tutmalar sayfası, Exchange Online içeriği aramanıza, tutmanıza ve dışarı aktarmanıza olanak sağladı. In-Place eBulma, siz veya diğer eBulma yöneticilerinin içeriği gözden geçirip yasal, mevzuat ve genel istekler için kullanılabilir hale getirmeniz için arama sonuçlarını bulma posta kutusuna kopyalamanıza da olanak tanır.

Bu özelliklerin tümü (arama sonuçlarını bulma posta kutusuna kopyalama dışında) uyumluluk [portalındaki](./microsoft-365-compliance-center.md) içerik arama, eBulma ve eBulma (Premium) araçlarında (geliştirilmiş işlevsellik, güvenilirlik ve çok çeşitli Microsoft 365 hizmetleri için destek ile) artık kullanılabilir olduğundan, bu araçları en kısa sürede kullanmaya başlamanızı öneririz. Aşağıdaki tabloda, bu diğer eBulma araçlarına geçişte size yardımcı olmak için eBulma ve In-Place Ayrı Tutma In-Place yerine kullanabileceğiniz araçlar listelenmiştir.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşları

- Office 365 ve Microsoft 365 Eğitim kuruluşları

- Office 365 ve Microsoft 365 Kamu kuruluşları; bunlara GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline-for-retirement"></a>Kullanımdan kaldırma zaman çizelgesi

- 1 Temmuz 2020: Yeni aramalar ve ayrı tutmalar oluşturamazsınız, ancak mevcut aramaları kendi riskinizle çalıştırmaya, düzenlemeye ve silmeye devam edebilirsiniz. Microsoft Desteği artık EAC'de eBulma & Tutma In-Place.

- 1 Ekim 2020: EAC'deki In-Place eBulma & Tutma işlevi salt okunur moda yerleştirilir. Bu, yalnızca mevcut aramaları ve ayrı tutmaları kaldırabileceğiniz anlamına gelir.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırılmakta olan mevcut işlevselliği değiştirmek için kullanabileceğiniz diğer araçlar açıklanmaktadır.

<table>
<thead>
<tr class="header">
<th>Işlevsel -liği</th>
<th>Alternatif araç</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Yasal amaçlarla arama, dışarı aktarma ve saklama</td>
<td>Uyumluluk portalında eBulma (Standart) durumları </td>
<td><p>eBulma (Standart) durumlarının özelliklerini kullanmak, eBulma ve In-Place Tutma In-Place işlevsel eşlik sağlar. Bu, aşağıdakileri içerir:</p>
<ul>
<li>
<p>Arama, milyonlarca konuma ölçeklendirilir</p>
</li>
<li>
<p>İçeriği arama, dışarı aktarma ve beklemeye alma için daha yüksek güvenilirlik</p>
</li>
<li>
<p>Exchange Online, SharePoint Online, OneDrive İş, Skype Kurumsal, Microsoft Teams, Yammer Grupları, Microsoft 365 Grupları ve Office 365 uygulamalarında depolanan diğer içerikler için içerik arama</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Bekletme amacıyla saklama</td>
<td>Uyumluluk portalında bekletme ilkeleri</td>
<td><p>İçeriği korumak ve isterseniz saklama süresi dolduktan sonra silmek için Bekletme ilkelerini kullanabilirsiniz. Diğer özellikler şunlardır:</p>
<ul>
<li>
<p>İlkeleri kuruluşunuzun tamamına uygulama </p>
</li><li>
<p>Exchange Online, SharePoint Online, OneDrive İş, Skype Kurumsal, Microsoft Teams ve Office 365 Grupları gibi belirli içerik konumlarına ilke uygulama</p></li>
<li>
<p>Belirli kullanıcılara ilke uygulama</p></li></ul>
<p>Daha fazla bilgi için bkz. <a href="/microsoft-365/compliance/retention-policies"> Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin</a>.</td>
</tr>
<tr class="odd">
<td>E-posta arama sonuçlarını gözden geçirilecek bulma posta kutusuna kopyalama</td><td>eKeşif (Premium) v2.0'da kümeleri gözden geçirme</td>
<td><p>Microsoft 365'te içeriği gözden geçirmek hiç bu kadar kolay olmamıştı. Gözden geçirme kümelerinin gözden geçirmek için gereken süreyi ve verileri azaltmaya yardımcı olacak birçok harika özelliği vardır, örneğin:</p>
<ul>
<li><p>Bir gözden geçirme kümesinde hızlı arama sorguları gerçekleştirme ve içeriği filtreleme</p></li>
<li><p>Gözden geçirme kümesindeki içeriği analiz etme; Buna e-posta yazışması oluşturma, neredeyse yinelenen algılama, Temalar analizi ve Tahmine dayalı kodlama dahildir</p></li>
<li><p>Bir inceleme setindeki belgeleri etiketleme</p></li>
<li><p>Avukat istemcisi ayrıcalık içeriğini tanımlamaya yardımcı olacak etiketleme önerileri</p></li></ul>
<p>Daha fazla bilgi için bkz. <a href="/microsoft-365/compliance/overview-ediscovery-20">Microsoft 365'te eKeşif (Premium) çözümüne genel bakış</a>.</p>
<p>
<p>Alternatif olarak, arama sonuçlarını PST dosyalarına aktarabilir ve ardından Microsoft 365 İçeri Aktarma hizmetini kullanarak PST'leri bulma posta kutusuna aktarabilirsiniz. Adım adım yönergeler için bkz. <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">PST dosyalarını Office 365 içeri aktarmak için ağ yüklemesini kullanma</a>.
</tr>
<tr class=even>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postasına erişim izni vermek için (örneğin, bir çalışan kuruluşunuzdan ayrıldığında ve başka bir kişiye eski çalışanın e-postasına erişim vermeniz gerektiğinde), söz konusu kişiye eski çalışanın posta kutusuna erişim izni atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kullanıcıya kaynak posta kutusuna erişmek için gereken izinleri atamanız yeterlidir.</td>
  
  </tr>
<tr class="odd">
<td>Kurtarılabilir Öğeler klasöründeki öğeleri geri yükleme</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Bir öğenin silinmiş öğe saklama süresi dolmadığı sürece posta kutularında kalıcı olarak silinen öğeleri ( <i>geçici olarak silinen</i> öğeler olarak da bilinir) geri yükleyebilirsiniz. Daha fazla bilgi için bkz. <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">Exchange Online'da Kurtarılabilir Öğeler klasörü</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>In-Place eBulma ve In-Place Tutma hakkında SSS

**EAC'de In-Place eBulma & Tutma özelliğinin arama sonuçlarını avukatlar tarafından incelenmek üzere bulma posta kutusuna kopyalamak için kopyalama arama sonuçları işlevini kullanıyorum. Şu anda hangi seçeneklerim var?**

Bu işlevi bugün çoğaltmanın iki yolu vardır. İlki [, eBulma (Premium) v2.0'da gözden geçirme kümelerini kullanmaktır](./view-documents-in-review-set.md). Gözden geçirme kümeleri, belgelerde hızlı arama, etiketleme, e-posta yazışması, neredeyse yinelenen gruplandırma, tema analizi ve tahmine dayalı kodlama gibi geleneksel bir inceleme aracında gördüğünüz özelliklerin birçoğuna sahiptir. İnceleme için bulma posta kutularını kullanmaya devam etmek istiyorsanız, ikinci seçenek arama sonuçlarını PST dosyalarına dışarı aktarmak ve ardından Microsoft uyumluluk merkezindeki [PST içeri aktarma özelliğini kullanarak PST](use-network-upload-to-import-pst-files.md) dosyalarını bulma posta kutusuna aktarmaktır.

**eBulma yöneticisinin yeni araçları kullanarak arama yapabilecek içerik konumlarını (posta kutuları veya siteler gibi) Nasıl yaparım? denetler?**

Uyumluluk portalı, eBulma Yöneticisi'nin hangi içerik konumlarını arayabileceğini denetlemek için [uyumluluk sınırlarını](set-up-compliance-boundaries.md) da kullanır. Uyumluluk sınırları, kuruluş sınırları içinde kalması gereken kamu kuruluşları veya coğrafi boarder'lara saygı göstermek için gereken çok uluslu kuruluşlarda yararlıdır.

**Geçerli aramalarımı ve tutmalarımı Microsoft Purview uyumluluk portalı nasıl taşıyabilirim?**

PowerShell kullanarak eKeşif aramalarını ve tutmalarını EAC'den In-Place geçirmek mümkündür. Yönergeler için bkz [. Arama ve ayrı tutmaları EAC'den uyumluluk portalına geçirme](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlet'leri

Exchange yönetim merkezinde 1 Temmuz 2017'de duyurulan özgün bildirime göre, In-Place eBulma & Tutma işlevi ve ilgili **\*-MailboxSearch** cmdlet'leri kullanımdan kaldırılıyor. Bu cmdlet'ler kullanıcılara yasal, mevzuat ve genel istekler için posta kutusu içeriğini arama, saklama ve dışarı aktarma olanağı sağlar.

Bu özellikler artık [<span class="underline">uyumluluk portalında</span>](./microsoft-365-compliance-center.md) ve gelişmiş performans ve ölçeklenebilirlikle Güvenlik & Uyumluluk PowerShell'i Office 365 için bu geliştirilmiş cmdlet'leri kullanmanız gerekir. Bu cmdlet'ler -ComplianceCase, [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) ve [<span class="underline">\*-ComplianceSearchAction'ı</span>](/powershell/module/exchange/get-compliancesearchaction) içerir[<span class="underline">\*</span>](/powershell/module/exchange/get-compliancecase).

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşları

- Office 365 ve Microsoft 365 Eğitim kuruluşları

- Office 365 ve Microsoft 365 Kamu kuruluşları; bunlara GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: Yeni In-Place eBulma aramaları ve In-Place Tutmaları oluşturmak için **New-MailboxSearch'i** kullanamazsınız, ancak mevcut aramaları ve tutmaları çalıştırmak, düzenlemek ve silmek için cmdlet'leri kullanmaya devam edebilirsiniz. Microsoft Desteği artık bu tür aramalar ve tutmalar için yardım sağlamaz.

- 1 Ekim 2020: Daha önce belirtildiği gibi EAC'deki In-Place eBulma & Tutma işlevi salt okunur moda yerleştirilir. Bu ayrıca **New-MailboxSearch, Start-MailboxSearch** veya **Set-MailboxSearch** cmdlet'lerini kullanamayacağınız anlamına gelir.  Yalnızca mevcut aramaları ve ayrı tutmaları alabilir ve kaldırabilirsiniz.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırılmakta olan mevcut işlevselliği değiştirmek için kullanabileceğiniz diğer araçlar açıklanmaktadır.

<table>
<thead>
<tr class="header">
<th>Işlevsel -liği</th>
<th>Alternatif araçlar</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Arama ve dışarı aktarma</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>ComplianceSearch ve ComplianceSearchAction cmdlet'leri, içeriği aramanıza ve dışarı aktarmanıza yardımcı olmak için birlikte çalışır. <strong>New-, Get-ve</strong> <strong>Start-ComplianceSearch</strong> cmdlet'lerini kullanarak <strong></strong>yeni bir arama oluşturabilir ve arama tahminini görüntüleyebilirsiniz. Ardından Arama sonuçlarını dışarı aktarmak için <strong>New-ComplianceSearchAction</strong> cmdlet'ini kullanabilirsiniz. Bu arama sonuçlarını yerel bilgisayarınıza indirmek için uyumluluk portalında eBulma (Standart) aracını kullanmanız gerekir.</p>
<p>
<p><strong>Not:</strong> Bu cmdlet'leri bir eBulma (Standart) olayıyla ilişkilendirilmemiş aramalar oluşturmak için kullanırsanız, bu aramalar uyumluluk portalındaki <strong>İçerik arama</strong> sayfasında yer alır.</p></td>
</tr>
<tr class="even">
<td>Posta kutusunda içerik tutma</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Uyumluluk portalındaki tutmalar bir ComplianceCase ile ilişkilendirilmelidir. İlk olarak, uyumluluk servis talebini oluşturun ve sonra bir CaseHoldPolicy ve bir CaseHoldRule oluşturun.</p>
<p><strong>Not:</strong> CaseHoldRule oluşturmadan CaseHoldPolicy oluşturulması, CaseHoldRule oluşturulana ve CaseHoldPolicy ile ilişkilendirilene kadar bekletmeyi kullanılamaz hale getirir. Daha fazla bilgi için cmdlet belgelerine bakın.</p></td>
</tr>
<tr class="odd">
<td>Arama sonuçlarını bulma posta kutusuna kopyalama</td>
<td>Yok</td>
<td>Tüm Microsoft 365 hizmetlerine erişim sağlamadığından, bu işlevselliğin doğrudan yerini almaz. Alternatif çözümler için aşağıdaki SSS bölümüne bakın.</td>
</tr>
  <tr class=even>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postasına erişim izni vermek için (örneğin, bir çalışan kuruluşunuzdan ayrıldığında ve başka bir kişiye eski çalışanın e-postasına erişim vermeniz gerektiğinde), söz konusu kişiye eski çalışanın posta kutusuna erişim izni atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kaynak posta kutusuna erişmek için bir kullanıcı izinleri atamanız yeterlidir.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>***-MailboxSearch** cmdlet'leri hakkında SSS

**E-posta iletilerini veya anlık iletileri diğer eKeşif ve yasal araştırma amacıyla dışarı aktarmak için Aramayı Kopyala'yı kullanırız. Bu cmdlet'ler kullanımdan kaldırıldıktan sonra başka hangi seçeneklerimiz var?**

[<span class="underline">Microsoft Graph API'leri</span>](https://developer.microsoft.com/en-us/graph), **-MailboxSearch cmdlet'lerini kullanmaktan\*** çok daha dayanıklı ve ölçeklenebilir olan analiz ve diğer amaçlar için verileri ayıklamaya yönelik bir dizi yöntem sağlar.

**Aramalarımı ve ayrı tutmalarımı uyumluluk portalına nasıl geçirebilirim?**

In-Place eBulma aramalarını ve ayrı tutmalarını Bir PowerShell betiği kullanarak Exchange yönetim merkezinden geçirmek mümkündür. Daha fazla bilgi için bkz [. Eski eBulma aramalarını ve tutmalarını uyumluluk portalına geçirme](migrate-legacy-eDiscovery-searches-and-holds.md).

**Cmdlet'ler kullanımdan kaldırıldıktan sonra aramaları kaldırmaya veya almaya devam edebilecek miyim?**

Evet, arama oluşturma ve değiştirme özelliğini kaldırsak da, bir sonraki bildirime kadar **Get-MailboxSearch** ve **Remove-MailboxSearch'i** kullanmaya devam edebilirsiniz. Ancak, bu cmdlet'lerin kullanımı, kullanımdan kaldırma tarihlerinden sonra kendi riski altındadır ve Microsoft Desteği artık yardım sağlayamayacaktır.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

Exchange Online PowerShell'deki **Search-Mailbox** cmdlet'i, ilk olarak 2018'den başlayarak cmdlet çıkışındaki bir uyarıda duyurulduğu gibi kullanımdan kaldırılıyor. **Search-Mailbox** cmdlet'i başlangıçta kullanıcının posta kutusunda arama yapmak ve kötü amaçlı içeriği temizlemek için kullanılmıştır. İçeriği aramak ve temizlemek için Office 365 Security & Compliance PowerShell'de **New-ComplianceSearch** ve **New-ComplianceSearchAction** cmdlet'lerini kullanmaya başlamanızı öneririz. Yerleşik güvenlik deneyimi için [<span class="underline">Microsoft 365 güvenlik özellikleri</span>](../security/index.yml) , e-posta ve diğer birçok Microsoft hizmeti için güçlü tehdit koruması sağlar.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşları

- Office 365 ve Microsoft 365 Eğitim kuruluşları

- Office 365 ve Microsoft 365 Kamu kuruluşları; bunlara GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

-  1 Temmuz 2020: **Search-Mailbox** cmdlet'i artık kullanılamayacak ve Microsoft Desteği artık yardım sağlamayacaktır.

### <a name="alternative-tools"></a>Alternatif araçlar

Aşağıdaki tabloda, kullanımdan kaldırılmakta olan mevcut işlevselliği değiştirmek için kullanabileceğiniz diğer araçlar açıklanmaktadır.

<table>
<thead>
<tr class="header">
<th>Işlevsel -liği</th>
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
<td><p>ComplianceSearch ve ComplianceSearchAction cmdlet'leri, içeriği aramanıza ve dışarı aktarmanıza yardımcı olmak için birlikte çalışır. <strong>New-, Get-ve</strong> <strong>Start-ComplianceSearch</strong> cmdlet'lerini kullanarak <strong></strong>yeni bir arama oluşturabilir ve arama tahminini görüntüleyebilirsiniz. Ardından Arama sonuçlarını dışarı aktarmak için <strong>New-ComplianceSearchAction -Export</strong> komutunu kullanabilirsiniz. Bu arama sonuçlarını yerel bilgisayarınıza indirmek için uyumluluk portalında eBulma (Standart) aracını kullanmanız gerekir.</p></p>
</td>
</tr>
<tr class="even">
<td>Posta kutusundan toplu e-postayı silme</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Posta kutuları için arşiv ve silme ilkesi ayarlama</span></a></p>
<p></p></td>
<td><p>Yöneticiler, öğeleri otomatik olarak kullanıcının arşiv posta kutusuna taşıyan ve posta kutusundan öğeleri otomatik olarak silecek bir arşivleme ve silme ilkesi oluşturabilir.</p>
</td>
</tr>
<tr class="even">
<td>Arama sonuçlarını bulma posta kutusuna kopyalama</td>
<td> </td>
<td>Tüm Microsoft 365 hizmetlerine erişim sağlamadığından, bu işlevselliğin doğrudan yerini almaz. Alternatif çözümler için <strong>*-MailboxSearch cmdlet'leri bölümündeki SSS</strong> bölümüne bakın. </td>
</tr>
<tr class=odd>
  <td>İletileri bir posta kutusundan farklı bir posta kutusuna kopyalama</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
  <td>Bir kişiye başka bir kullanıcının e-postasına erişim izni vermek için (örneğin, bir çalışan kuruluşunuzdan ayrıldığında ve başka bir kişiye eski çalışanın e-postasına erişim vermeniz gerektiğinde), söz konusu kişiye eski çalışanın posta kutusuna erişim izni atamanızı öneririz. Bu nedenle, posta kutusu öğelerini başka bir kullanıcı posta kutusuna veya paylaşılan posta kutusuna kopyalamak yerine, kaynak posta kutusuna erişmek için bir kullanıcı izni atamanız yeterlidir.</td>
</tr>
<tr class=even>
  <td>İletileri posta kutusundan temizleme</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>ComplianceSearch ve ComplianceSearchAction cmdlet'leri, içeriği aramanıza ve temizlemenize yardımcı olmak için birlikte çalışır. <strong>New-ComplianceSearch</strong> ve <strong>New-ComplianceSearch</strong> cmdlet'leriyle bir arama oluşturup çalıştırabilir ve ardından <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> komutunu kullanarak içeriği temizleyebilirsiniz. Daha fazla bilgi için bkz <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">. İletileri arama ve silme</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>İletileri posta kutusundan temizleme</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Posta kutusuna izin atama</a></td>
<td>İletileri posta kutusundan temizlemek için çalışanın posta kutusuna erişmek için yönetici izinleri atayın. Outlook'taki yerleşik arama ve görüntüleme özelliklerinden yararlanarak iletiler gerektiğinde silinebilir ve geri dönüştürülebilir.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange Web Services API işlemleri

Exchange Web Hizmetleri API'sindeki bu işlemler, Exchange yönetim merkezindeki In-Place eBulma & Tutmaları özelliği ve Exchange Online PowerShell'deki ilgili **\*-MailboxSearch** cmdlet'leri tarafından kullanılır. Diğer eski eKeşif araçlarını kullanımdan kaldırma işlemi kapsamında da kullanımdan kaldırılacaktır.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşları

- Office 365 ve Microsoft 365 Eğitim kuruluşları

- Office 365 ve Microsoft 365 Kamu kuruluşları; bunlara GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes ve GetHoldOnMailboxes işlemleri artık kullanılamayacak ve Microsoft Desteği artık yardım sağlamayacaktır.

## <a name="ediscovery-premium-v10"></a>eBulma (Premium) v1.0

eKeşif 'e Geç (Premium) seçeneğine tıklayarak bir eBulma (Standart) durumunda kullanılabilen eBulma (Premium) sürümü olan **eKeşif (Premium**) v1.0 kullanımdan kaldırılıyor. İşlevselliği, uyumluluk portalındaki yeni [eBulma (Premium) çözümüyle](./ediscovery.md) değiştirilmiştir.

Kuruluşunuzun eBulma (Premium) v1.0 kullanıp kullanmadığını belirlemek için:

1. Uyumluluk portalına gidin, **eBulma Çekirdeği'ni** >  seçin ve bir eBulma (Standart) servis talebi açın.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. **eBulmaya Geç (Premium)** düğmesini görürseniz, bu düğmeye tıkladığınızda kullanımdan kaldırılmakta olan eBulma 'nın (Premium) 1.0 sürümüne gidersiniz. eBulma 'da (Standart) servis talepleri oluşturma ve yönetme özelliği bundan etkilenmez. Yalnızca eBulma (Premium) v1.0'da büyük/küçük harf verilerini ekleme ve analiz etme özelliği ( **eBulmaya geç (Premium)**) seçeneği kullanımdan kaldırılıyor.

Microsoft 365'teki yeni eBulma (Premium) çözümü ( *eBulma (Premium) v2.0* olarak da bilinir) özgün çözümün tüm özelliklerini sağlar, ancak şimdi diğer Microsoft 365 hizmetlerindeki içeriği tanımlama, bu içeriği toplama ve gözden geçirenlerin hızlı arama sorgularından yararlanabileceği bir gözden geçirme kümesine eklemeye yönelik koruyucu tabanlı bir yaklaşım içerir.  ilgili belgeleri iptal etmeye yardımcı olmak için etiketleme ve analiz özellikleri. eBulma (Premium) artık hem Microsoft hem de Microsoft dışı dosya türleri için geliştirilmiş işleme ve yerel görüntüleyiciler içeriyor, dosya türlerinin tam listesi [burada](./supported-filetypes-ediscovery20.md) ve desteklenen meta veri alanları [burada](./document-metadata-fields-in-advanced-ediscovery.md). Ayrıca yeni eBulma (Premium) çözümü, eBulma (Premium) durumunda farklı hizmetlerdeki içeriğe ayrı tutmalar uygulamanıza, kullanıcıları ayrı tutmaları bildirmenize ve koruyucu yanıtlarını izlemenize olanak tanıyan güçlü bir koruyucu tutma yönetimi özelliği sağlar.

eKeşif (Premium) v2.0'a erişmek için:

Uyumluluk portalına gidin, **eBulma Gelişmiş'i** >  seçin ve bir eBulma (Standart) servis talebi açın.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

Şu anda, eBulma iş akışınızı yeni eBulma (Premium) işlevine geçirmenizi öneririz. Gerekirse, içeriği dışarı aktarıp çevrimdışı olarak depolayarak eBulma (Premium) 1.0 servis talebinizi arşivleyebilirsiniz. 31 Aralık 2020'ye kadar mevcut durumlarda eBulma (Premium) v1.0'a erişmeye devam edebilirsiniz ancak Microsoft Desteği 1 Ekim 2020'ye kadar destek sağlamaz. Diğer ayrıntılar için aşağıdaki zaman çizelgesine bakın.

### <a name="scope-of-affected-organizations"></a>Etkilenen kuruluşların kapsamı

- Office 365 ve Microsoft 365 Kurumsal kuruluşları

- Office 365 ve Microsoft 365 Eğitim kuruluşları

- Office 365 ve Microsoft 365 Kamu kuruluşları; bunlara GCC, GCC High ve DoD dahildir

- Office 365 Almanya

### <a name="timeline"></a>Zaman çizelgesi

- 1 Temmuz 2020: Yeni eBulma (Premium) v1.0 servis talepleri oluşturamazsınız.

- 1 Ekim 2020: Hiçbir servis talebine yeni veri (Arama sonuçlarını eBulma (Premium) için hazırlama) ekleyemezsiniz. Mevcut durumlarda verilerle çalışmaya kendi riskinizle devam edebilirsiniz. Microsoft Desteği artık yardım sağlamaz. 

- 31 Aralık 2020: eBulma (Premium) v1.0 servis talebine erişemezsiniz.

### <a name="alternative-tools"></a>Alternatif araçlar

Uyumluluk portalında [eBulma (Premium) çözümü](./overview-ediscovery-20.md) .
