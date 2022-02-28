---
title: Posta kutularına gereksiz e-Exchange Online yapılandırma
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- M365-security-compliance
description: Yöneticiler, posta kutularında gereksiz e-posta ayarlarını yapılandırmayı Exchange Online öğrenebilir. Bu ayarların birçoğu aynı anda veya başka bir Outlook kullanıcıların Web üzerinde Outlook.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d3a55b1f49430d3c2a61b0db44e3ce8f8a060093
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "62988840"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Posta kutularına gereksiz e-Exchange Online yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Aynı Microsoft 365 posta kutuları olan kuruluşlarda Exchange Online istenmeyen posta önleme ayarları Exchange Online Protection (EOP) tarafından denetlenmiştir. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md).

Ancak, yöneticilerin belirli posta kutularında yapılandırılan belirli istenmeyen posta önleme ayarları da Exchange Online:

> [!NOTE]
> EOP artık iletileri gereksiz e-posta kuralı yerine Gereksiz E-posta klasörüne yönlendirecek kendi posta akışı teslim aracısını kullanıyor. **Set-MailboxJokEmailConfiguration** cmdlet'inde _Enabled_ parametresi artık posta akışını hiçbir şekilde etkilemeyecektir. EOP, istenmeyen posta önleme ilkelerde ayarlanmış eylemlere dayalı olarak iletileri yönlendiriyor. Kullanıcının Posta Gönderen Kasa ve Engellenen Gönderenler listesi her zamanki gibi çalışmaya devam edecektir.

- İstenmeyen posta önleme ilkelerine dayalı olarak iletileri Gereksiz E-posta klasörüne taşıma: İstenmeyen posta filtreleme kararını almak için  İletiyi Gereksiz E-posta klasörüne taşı eylemiyle yapılandırılmışsa, ileti posta kutusuna teslim edildikten sonra Gereksiz **E-posta** klasörüne taşınır. İstenmeyen posta filtreleme kararlarını istenmeyen posta önleme ilkeleri hakkında daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md). Benzer şekilde, sıfır saatlik otomatik temizleme (ZAP) teslim edilen bir iletinin istenmeyen posta veya kimlik avı iletisi olduğunu belirlerse, ileti İletiyi Gereksiz E-posta klasörüne taşıma istenmeyen posta filtresi karar eylemleri için Önemsiz E-posta klasörüne taşınır. ZAP hakkında daha fazla bilgi için bkz. Aynı saatte sıfır saatlik [otomatik temizleme (ZAP) Exchange Online](zero-hour-auto-purge.md).

- **kullanıcıların Outlook veya Web üzerinde Outlook'te** kendileri için yapılandırılan gereksiz e-posta ayarları: Güvenilir liste koleksiyonu Kasa  Gönderenler listesi, Kasa Alıcıları listesi ve her posta kutusunda Engellenen Gönderenler listesidir. Bu listelerde yer alan girdiler, iletinin Gelen Kutusu'na mı yoksa Gereksiz E-posta klasörüne mi taşındığını belirler. Kullanıcılar liste veya posta kutusunda (eski adıyla Outlook Web üzerinde Outlook) kendi posta kutuları için güvenilir liste koleksiyonunu Outlook Web App. Yöneticiler herhangi bir kullanıcının posta kutusunda güvenilir liste koleksiyonunu yapılandırabilirsiniz.

EOP, iletiyi gereksiz e-posta filtreleme karar eylemi olan Gereksiz E-posta klasörüne veya posta  kutusunda Engellenen Gönderenler listesine taşıma eylemine dayalı olarak iletileri Gereksiz E-posta klasörüne taşıyabiliyor ve iletilerin Gereksiz E-posta klasörüne (posta kutusunda Kasa Gönderenler listesi temel alınarak) teslim ekleyebilirsiniz.

Yöneticiler Exchange Online kutuları (Kasa Gönderenler listesi, Kasa Alıcılar listesi ve Engellenen Gönderenler listesi) güvenilir liste koleksiyonunda yer alan girdileri yapılandırmak için Kasa PowerShell kullanabilir.

> [!NOTE]
> Kullanıcıların kendi listelerine ekli olarak gönderenlerden gelen Kasa Gönderenler listeleri EOP'nin bir parçası olarak içerik filtrelemeyi atlar (SCL -1'tir). Kullanıcıların Outlook'ta Kasa Gönderenler listesine giriş eklemesini önlemek için, bu makalenin devam konusu olan Outlook Gereksiz [e-posta](#about-junk-email-settings-in-outlook) ayarları hakkında bölümünde belirtildiği gibi Grup İlkesi'ni kullanın. İlke filtreleme, İlke filtreleme, Office 365 için Defender denetimleri iletilere uygulanmaya devam ediyor.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Exchange Online PowerShell'i yalnızca bu makaledeki yordamları yapmak için kullanabilirsiniz. Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları yerine Exchange Online önce Bu makalede izinlerin atanmamış olması gerekir. Özel olarak, Posta Alıcıları  rolüne (Varsayılan olarak Kuruluş **Yönetimi, Alıcı** Yönetimi ve Özel Posta Alıcıları rol gruplarına atanır) veya Kullanıcı Seçenekleri rolüne (varsayılan olarak Kuruluş Yönetimi  ve **Yardım** Masası rol gruplarına atanır) ihtiyacınız vardır. Bir yıl içinde rol gruplarına kullanıcı Exchange Online için [bkz. Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Varsayılan izinlere sahip kullanıcılar, PowerShell'e erişimleri olduğu sürece bu yordamları kendi [posta kutularında Exchange Online unutmayın](/powershell/exchange/disable-access-to-exchange-online-powershell).

- EOP'nin şirket içi veya posta kutularını Exchange karma ortamlarda, şirket içi posta kutularında posta akış kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız Exchange. Bu posta akış kuralları EOP istenmeyen posta filtreleme kararını çevirerek, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşımasini sağlar. Ayrıntılar için bkz. [EOP'yi karma ortamlarda gereksiz E-posta klasörüne istenmeyen posta teslim edecek şekilde yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Kasa posta kutularının gönderenleri, tasarım tarafından Azure AD ve EOP ile eşitlenmez.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Posta Exchange Online güvenilir liste koleksiyonunu yapılandırmak için PowerShell'i kullanma

Posta kutusu güvenilir liste koleksiyonunda Kasa Gönderenler listesi, Kasa Listesi ve Engellenen Gönderenler listesi yer almaktadır. Varsayılan olarak, kullanıcılar güvenli liste koleksiyonunu Kendi Posta Kutuları veya Posta Kutuları Outlook Web üzerinde Outlook. Yöneticiler, kullanıcının posta kutusunda güvenilir liste koleksiyonunu yapılandırmak için **Set-Mailbox BirEmailConfiguration** cmdlet'inde buna karşılık gelen parametreleri kullanabilir. Bu parametreler aşağıdaki tabloda açıklanmıştır.

<br>

****

|Parametre Set-MailboxJunkEmailConfiguration|Web üzerinde Outlook ayarı|
|---|---|
|_BlockedSendersAndDomains_|**Bu gönderenlerden veya etki alanlarından e-postaları Gereksiz E-posta klasörüme taşıma**|
|_ContactsTrusted_|**Kişilerimin e-postaya güven**|
|_TrustedListsOnly_|**Yalnızca sitemin gönderenleri ve etki alanları Kasa e-postalarına güven ve Kasa listelerine güven**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Bu gönderenlerden gelen e-postaları Gereksiz E-posta klasörüme taşıma**|
|

<sup>\*</sup>**Notlar**:

- Bu **Exchange Online, Kasa** Senders listesinde veya _TrustedSendersAndDomains_ parametresinde yer alan etki alanı girdileri tanınmaz, dolayısıyla yalnızca e-posta adreslerini kullanın. Dizin eşitlemesi olan tek başına EOP'de etki alanı girdileri varsayılan olarak eşitlenmez, ancak etki alanları için eşitlemeyi etkinleştirebilirsiniz. Daha fazla bilgi için [bkz. KB3019657](https://support.microsoft.com/help/3019657).
- **Set-MailboxJunkEmailConfiguration** cmdlet'ini kullanarak Kasa Alıcıları listesini doğrudan değiştiremezsiniz (_TrustedRecipientsAndDomains_ parametresi çalışmıyor). Varsayılan Gönderenler Kasa değiştirirsiniz ve bu değişiklikler en çok Kasa listesine eşitlenir.

Posta kutusunda güvenilir liste koleksiyonunu yapılandırmak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Birden çok değer girmek ve _BlockedSendersAndDomains_ ve _TrustedSendersAndDomains_ parametrelerinde var olan tüm girdilerin üzerine yazmak için aşağıdaki söz dizimi kullanın: `"<Value1>","<Value2>"...`. Var olan diğer girdileri etkilemeden bir veya daha fazla değer eklemek veya kaldırmak için, aşağıdaki söz dizimi kullanın: `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

Bu örnekte, Ori Epstein'ın posta kutusunda safelist collection için aşağıdaki ayarlar yapılandırılmıştır:

- Engellenen Gönderenler shopping@fabrikam.com istediğiniz değeri ekleyin.
- Yeni Gönderenler chris@fourthcoffee.com listesinden ve Kasa Alıcılar listesinden Kasa kaldırın.
- Kişiler klasöründeki kişileri güvenilen gönderenler olarak kabul edilenler olarak yapılandırr.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

Bu örnekte, contoso.com tüm kullanıcı posta kutularında, etki alanı adları Engellenen Gönderenler listesinden kaldırır.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Kullanıcı posta kutusunu hiç açmadı ise, önceki komutları çalıştırmanız sırasında hata alabilirsiniz. Toplu işlemlarda bu hatanın ılması için `-ErrorAction SilentlyContinue` **Set-Mailbox BirKmailConfiguration komutuna** ekleyin.
> - En Outlook E-posta Filtresi'nin ek güvenilir liste koleksiyonu ayarları vardır (örneğin, E-posta gönderenler listesine e-Kasa **kişi ekleme**). Daha fazla bilgi için bkz [. Hangi iletileri göreceğinizi kontrol etmek için Gereksiz E-posta Filtrelerini Kullanma](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

Posta kutusunda güvenilir liste koleksiyonunu başarıyla yapılandırıldığından emin olmak için, aşağıdaki yordamlardan herhangi birini kullanın:

- Posta _\<MailboxIdentity\>_ kutusunun adı, diğer adı veya e-posta adresiyle değiştirin ve özellik değerlerini doğrulamak için aşağıdaki komutu çalıştırın:

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Değer listesi çok uzunsa, şu söz dizimi kullanın:

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>E-posta'daki gereksiz e-posta Outlook

Bu hizmette bulunan istemci tarafı Gereksiz E-posta Filtresi ayarlarını etkinleştirmek, devre dışı bırakmak ve Outlook için Grup İlkesi'ne tıklayın. Daha fazla bilgi için bkz. Yönetim Şablonu dosyaları [(ADMX/ADML) ve Kurumlar için Microsoft 365 Uygulamaları için Office Özelleştirme Aracı, Office 2019 ve Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) ve Grup İlkesini kullanarak [Kasa](https://support.microsoft.com/help/2252421) Gönderenler listesi gibi gereksiz e-posta ayarlarını dağıtma.

Outlook  \>  \> Gereksiz E-posta Filtresi varsayılan değerine ayarlanmışsa, Ev Gereksiz  **E-posta E-posta** \> Seçenekleri seçeneklerinde otomatik filtreleme yok değerine **ayarlanırsa,** Outlook iletileri istenmeyen posta olarak sınıflandırmayı denemez ancak güvenilir liste koleksiyonunu (Kasa Gönderenler listesi, Güvenilir Liste Kasa  İletileri teslimden sonra Gereksiz E-posta klasörüne taşımak için Alıcılar listesi ve Engellenen Gönderenler listesi). Bu ayarlar hakkında daha fazla bilgi için bkz. [Gereksiz E-posta Filtresine Genel Bakış](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

Gereksiz Outlook E-posta Filtresi Düşük veya Yüksek olarak  ayarlanmışsa **, Outlook** Gereksiz E-posta Filtresi istenmeyen postaları tanımlamak ve Gereksiz E-posta klasörüne taşımak için kendi SmartScreen filtre teknolojisini kullanır. Bu istenmeyen posta sınıflandırması, EOP tarafından belirlenen istenmeyen posta güvenlik düzeyinden (SCL) ayrıdır. Aslında, Outlook SCL'i EOP'den yoksayar (EOP istenmeyen posta filtrelemeyi atlamak için iletiyi işaretlediği sürece) ve iletinin istenmeyen posta olup olmadığını belirlemek için kendi ölçütlerini kullanır. Şüphesiz, EOP ve istenmeyen posta kararının Outlook aynı olabilir. Bu ayarlar hakkında daha fazla bilgi için bkz [. Gereksiz E-posta Filtresi'nin koruma düzeyini değiştirme](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> Kasım 2016'da Microsoft, Exchange ve Outlook'de SmartScreen filtreleri için istenmeyen posta tanım güncelleştirmelerini üretmeyi durdurdu. Mevcut SmartScreen istenmeyen posta tanımları olduğu gibi kaldı, ancak bunların etkisinin zaman içinde düşük olması olasıdır. Daha fazla bilgi için bkz[. SmartScreen'de smartscreen desteğini Outlook ve Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Dolayısıyla, Outlook Gereksiz E-posta Filtresi, iletileri Gereksiz E-posta klasörüne taşımak için posta kutusunun güvenilir listesi koleksiyonunu ve kendi istenmeyen posta sınıflandırmasını kullanabilir.

Outlook ve Web üzerinde Outlook güvenilir liste koleksiyonunu destekler. Güvenilir liste koleksiyonu, Exchange Online kutusuna kaydedilir; dolayısıyla, Outlook'de güvenli liste koleksiyonunda yapılan değişiklikler Web üzerinde Outlook olarak görüntülenir.

## <a name="limits-for-junk-email-settings"></a>Gereksiz e-posta ayarları için sınırlar

Kullanıcının posta kutusunda depolanan güvenilir liste koleksiyonu (Kasa Gönderenler listesi, Kasa Alıcıları listesi ve Engellenen Gönderenler listesi) de EOP ile eşitlenir. Dizin eşitlemeyle, güvenilir liste koleksiyonu Azure AD'ye eşitlenir.

- Kullanıcının posta kutusu güvenilir liste koleksiyonunun 510 KB sınırlaması vardır. Bu sınır tüm listeleri ve ek gereksiz e-posta filtresi ayarlarını içerir. Kullanıcı bu sınırı aşarsa, aşağıdakine benzer bir Outlook hata alır:

  > Sunucu Gereksiz E-posta listelerine ekli değil/ekli değil. Sunucuda izin verilen boyutun üzerindesiniz. Gereksiz E-posta listeleriniz sunucu tarafından izin verilen boyuta indirilene kadar, sunucuya verilen Gereksiz E-posta filtresi devre dışı bırakılır.

  Bu sınır ve bu sınırı değiştirme hakkında daha fazla bilgi için bkz. [KB2669081](https://support.microsoft.com/help/2669081).

- EOP'de eşitlenmiş güvenilir liste koleksiyonu aşağıdaki eşitleme sınırlarına sahiptir:
  - Kişilerimin e-postasına güven etkinleştirildiyse Kasa Gönderenler listesinde, Kasa Alıcılar listesinde ve dış kişilerde toplam 1024 **girdi**.
  - Engellenen Gönderenler listesi ve Engellenen Etki Alanları listesinde toplam 500 girdi.

  1024 giriş sınırına ulaşıldı mı, şu şeyler olur:

  - Liste, PowerShell ve Web üzerinde Outlook kabul edilmeyi durdurur, ancak hiçbir hata görüntülenmez.

    Outlook 510 KB'lık bir sınıra ulaşana kadar kullanıcılar 1024'Outlook eklemeye devam edecektir. Outlook EOP filtresi posta kutusuna teslimden önce iletiyi engellememişse (posta akış kuralları, adres mektup birleştirmeyi önleme vb.) bu ek girdileri kullanabilirsiniz.

- Dizin eşitlemeyle, girdiler Azure AD'ye aşağıdaki sırayla eşitlenir:
  1. Kişilerime gelen **e-postaya güven etkinleştirildiyse, posta** kişileri.
  2. İlk Kasa ve Alıcı Kasa listesi, ilk 1024 girdilerinde değişiklik yapıldıklarında birleştirilmiş, yinelenen ve alfabetik olarak sıralanır.

  İlk 1024 girdi kullanılır ve ilgili bilgiler ileti üst bilgilerine damgalanır.

  Azure AD ile eşitlenmemiş 1024'ü geçen girdiler Outlook (Web üzerinde Outlook) tarafından işlenir ve ileti üst bilgilerinde hiçbir bilgi damgalanmaz.

Gördüğünüz gibi, Kişilerim'den e-postaya güven ayarının etkinleştirilmesi, eşitlenebilir gönderen Kasa gönderen Kasa kişi sayısını azaltır. Bu önemli bir sorunsa bu özelliği kapatmak için Grup İlkesi'nin kullanılması önerilir:

- Dosya adı: outlk16.opax
- İlke ayarı: **Kişilerden gelen e-postaya güvenme**
