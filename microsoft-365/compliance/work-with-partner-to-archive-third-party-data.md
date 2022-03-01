---
title: Üçüncü taraf verilerini arşivlemek için iş ortağıyla çalışma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Salesforce Chatter, Yahoo Messenger veya Yammer gibi veri kaynaklarından üçüncü taraf verilerini içeri aktaracak özel bir bağlayıcı ayarlamayı Yammer.
ms.openlocfilehash: 53c6cae76327c7a8fb8ca89de464ad8a63e75d6a
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018790"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Üçüncü taraf verilerini arşivlemek için iş ortağıyla çalışma

Üçüncü taraf bir veri kaynağından gelen verileri içeri aktararak veya arşiv olarak bir Microsoft İş Ortağıyla birlikte Microsoft 365. Bir iş ortağı size üçüncü taraf veri kaynağından öğeleri ayıklar (düzenli olarak) ve sonra bu öğeleri içeri aktaran özel bir bağlayıcı sağlar. İş ortağı bağlayıcısı, veri kaynağından bir öğenin içeriğini e-posta iletisi biçimine dönüştürür ve sonra da öğeleri posta kutularında depolar. Üçüncü taraf verileri alındıktan sonra, bu Microsoft 365 Saklama, eBulma, In-Place Arşivleme, Denetim ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz.

> [!IMPORTANT]
> İş [Ortağı Yönetimi'Microsoft 365](communication-compliance.md) bu makalede adı geçen iş ortağı bağlayıcıları tarafından alınan üçüncü taraf verilerine uygulanamıyor.

Burada, işleme genel bir bakış ve bir Microsoft İş Ortağı ile birlikte çalışılması gereken üçüncü taraf verilerini içeri aktarma adımları ve açık bir şekilde açıkmektedir.

[1. Adım: Üçüncü taraf bir veri ortağı bulma](#step-1-find-a-third-party-data-partner)

[2. Adım: Üçüncü taraf bir veri posta kutusunu oluşturma ve yapılandırma](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[3. Adım: Üçüncü taraf verileri için kullanıcı posta kutularını yapılandırma](#step-3-configure-user-mailboxes-for-third-party-data)

[4. Adım: İş ortağınıza bilgi sağlama](#step-4-provide-your-partner-with-information)

[5. Adım: Üçüncü taraf veri bağlayıcılarını Yeni'ye Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Üçüncü taraf veri içeri aktarma işlemi nasıl çalışır?

Aşağıdaki çizim ve açıklama, bir iş ortağıyla çalışırken üçüncü taraf veri aktarma işleminin nasıl çalıştığını açıklamaya yarar.

![Üçüncü taraf veri içeri aktarma işlemi nasıl çalışır.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Müşteri, üçüncü taraf veri kaynağından öğeleri ayıkacak ve sonra bu öğeleri başka bir öğeye aktaracak bir bağlayıcı yapılandırmak için tercih olduğu iş ortağıyla Microsoft 365.

2. İş ortağı bağlayıcısı üçüncü taraf veri kaynaklarına üçüncü taraf bir API üzerinden bağlanır (zamanlanmış veya yapılandırılmış olarak) ve veri kaynağından öğeleri ayıklar. İş ortağı bağlayıcısı öğenin içeriğini e-posta iletisi biçimine dönüştürür. İleti [biçimi şemasının](#more-information) açıklaması için Daha fazla bilgi bölümüne bakın.

3. İş ortağı bağlayıcısı, iyi bilinen bir bitiş noktası aracılığıyla Microsoft 365 Web Hizmeti (EWS) aracılığıyla Exchange'te Azure hizmetine bağlanır.

4. Öğeler, belirli bir kullanıcının posta kutusuna veya bir "hepsi bu" üçüncü taraf veri posta kutusuna aktarılır. Öğenin belirli bir kullanıcı posta kutusuna mı yoksa üçüncü taraf veri posta kutusuna mı aktarılmış olduğu aşağıdaki ölçütlere göre temel alınır:

   1. **Kullanıcı hesabına karşılık gelen kullanıcı kimliğine sahip öğeler:** İş ortağı bağlayıcısı üçüncü taraf veri kaynağında öğenin kullanıcı kimliğini Microsoft 365'ta belirli bir kullanıcı kimliğiyle eşleyene kadar, öğe kullanıcının Kurtarılabilir Öğeler klasöründeki Temizlenebilir  klasörüne kopyalanır. Kullanıcılar Temiz temiz klasörünün öğelerine erişe değildir. Bununla birlikte, Temizleme klasöründe öğeleri aramak için eBulma araçlarını kullanabilirsiniz.

   1. **Kullanıcı hesabına karşılık gelen kullanıcı kimliğine sahip değil öğeler:** İş ortağı bağlayıcısı öğenin kullanıcı kimliğini belirli bir kullanıcı kimliğiyle eşleyenene kadar, öğe üçüncü taraf veri posta kutusunun Gelen  Kutusu klasörüne kopyalanır. Öğeleri gelen kutusuna aktarmanız, sizin veya organizasyonudaki birinin bu öğeleri görüntülemek ve yönetmek için üçüncü taraf posta kutusunda oturum açmanızı ve iş ortağı bağlayıcısı yapılandırmasında herhangi bir ayarlamanın gerekli olup olduğunu görmenizi sağlar.

## <a name="step-1-find-a-third-party-data-partner"></a>1. Adım: Üçüncü taraf bir veri ortağı bulma

Microsoft 365'ta üçüncü taraf verilerini arşivlemek için önemli bir bileşen, üçüncü taraf bir veri kaynağından verileri yakalama ve verileri Microsoft 365'e aktarma konusunda özelleştirilmiş bir Microsoft iş ortağını bulmak ve Microsoft 365. Veriler aktarıldıktan sonra, Exchange'tan gelen e-posta ve SharePoint ve belgelerin e-postası gibi diğer Microsoft verileriyle birlikte SharePoint OneDrive İş. Bir iş ortağı, organizasyon üçüncü taraf veri kaynaklarından (BlackBerry, Facebook, Google+, Thomson Reuters, Twitter ve YouTube gibi) veri ayıklanan ve bu verileri e-posta iletileri olarak Exchange posta kutularına aktaran bir Microsoft 365 API'sine aktaran bir bağlayıcı oluşturur.

Aşağıdaki bölümlerde, microsoft iş ortakları (ve bunların desteklemektedir olduğu üçüncü taraf veri kaynakları) bu programda üçüncü taraf verilerini arşivlemek için Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[ArchiveSocial](#archivesocial)

[Veritas](#veritas)

[OpenText](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[17a-4 LLC](https://www.17a-4.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- BlackBerry

- Bloomberg Data Akışlar

- Cisco Cisco Ciscober

- Bilgi Kümesi

- HipChat

- InvestEdge

- LivePerson

- MessageLabs Data Akışlar

- OpenText

- Oracle/ATG 'tıkla-çağır' Canlı Yardım

- Özet IM BIRAYI

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype Kurumsal (Lync/OCS)

- Skype Kurumsal Online (Lync Online)

- SQL Veritabanları

- Squawker

- Thomson Reuters E ilgili Messenger

### <a name="archivesocial"></a>ArchiveSocial

[ArchiveSocial](https://www.archivesocial.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Facebook

- Flickr

- Bur kadar, Türkiye

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Veritas](https://www.globanet.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Pivot Client ile AOL

- BlackBerry Arama Günlükleri (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN'i (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Sohbeti

- Bloomberg Mail

- Box

- Salesforce Sohbetter için CipherCloud

- Cisco IM &amp; Presence Server (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- Özel sınırlandırılmış metin dosyaları

- Özel XML dosyaları

- Facebook (Sayfalar)

- Bilgi Kümesi

- FXConnect

- ICE Sohbeti/YellowEt

- Jive

- Mac gregoryen XIP

- Microsoft Exchange Server

- Microsoft OneDrive Kurumsal

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Özet

- Salesforce SohbetTeri

- Skype Kurumsal Çevrimiçi

- Skype Kurumsal, sürüm 2007 R2 - 2016 (şirket içi)

- Slack Enterprise Kılavuzu

- Burya

- Thomson Reuters Efunn

- Thomson Reuters Messenger

- Thomson Reuters Dealings 3000 / FX Yatırım

- Twitter

- UBS Sohbeti

- YouTube

### <a name="opentext"></a>OpenText

[OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Axs Encrypted

- Axs Exchange

- Axs Local Archive

- Axs Yer Tutucu

- Axs İmzalı

- Bloomberg

- Thomson Reuters

### <a name="smarsh"></a>Smarsh

[Smarsh](https://www.smarsh.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- AIM

- Amerikan Burdan

- Elma Suyu

- Pivot istemcisiyle AOL

- Ares

- Bazaar Voice

- Bear Share

- Bit Taşkın

- BlackBerry Arama Günlükleri (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN'i (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Mail

- CellTrust

- Sohbet İçeri Aktarma

- Sohbet Gerçek Zamanlı Günlüğe Kaydetme ve İlke

- SohbetTer

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Birleşik İletişim Durumu Sunucusu (v8.6.3, v8.6.4, v8.6.5)

- İşbirliğini İçeri Aktarma

- İşbirliği Gerçek Zamanlı Günlüğe Kaydetme

- Doğrudan Bağlan

- Facebook

- Bilgi Kümesi

- FastTrack

- Ltella

- Google+

- GoToMyPC

- Hopster

- HubConnex

- IBM Connections (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowEt

- IM İçeri Aktarma

- IM Gerçek Zamanlı Günlüğe Kaydetme ve İlke

- Indii Messenger

- Instant Bloomberg

- IRC

- Jive

- Jive 6 Gerçek Zamanlı Günlük (v6, v7)

- Jive İçeri Aktarma

- JXTA

- LinkedIn

- Microsoft Lync (2010, 2013)

- MFTP

- Microsoft Lync 2013 Voice

- Microsoft SharePoint (2010, 2013)

- Microsoft Office SharePoint Online

- Microsoft UC (Birleşik İletişim)

- MindAlign

- Mobile Guard

- MSN

- Alanım

- NEONetwork

- Microsoft 365 Lync Dedicated

- Microsoft 365 Paylaşılan IM

- Pinterest

- Özet

- QQ

- Skype Kurumsal 2015

- SoftEther

- Burya

- Thomson Reuters Efunn

- Thomson Reuters Messenger

- Tor

- TTT

- Twitter

- WinMX

- Winie

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[Verba](https://www.verba.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Avaya Aura Video

- Avaya Aura Voice

- Avtec Radyo

- Radio/Telex Radyo

- BroadSoft Video

- BroadSoft Voice

- Centile Voice

- Cisco Cisco Ciscober IM

- Cisco UC Video

- Cisco UC Voice

- Cisco UCCX/UCCE Video

- Cisco UCCX/UCCE Voice

- ESChat Radyo

- Geoman İletişim Uzmanı

- IP Trade Voice

- Luware LUCIAS Kişi Merkezi

- Microsoft UC (Birleşik İletişim)

- Lync için Mitel MiContact Center (prairieFyre)

- Oracle / Acme Paket Oturum Sınırı Denetleyicisi Videosu

- Oracle / Acme Paket Oturum Sınırı Denetleyicisi Ses

- Singtel Mobile Voice

- SIPREC Video

-  SIPREC Ses

- Skype Kurumsal / Lync IM

- Skype Kurumsal / Lync Video

- Skype Kurumsal / Lync Voice

- Hoparlör Ses

- Standart SIP/H.323 Video

- Standart SIP/H.323 Ses

- Truphone Voice

- 2010 Radyo

- Windows Masaüstü Bilgisayar Ekranı

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>2. Adım: Posta kutusunda üçüncü taraf bir veri posta kutusu oluşturma Microsoft 365

Verileri bu posta kutusuna içeri aktarma işlemi için üçüncü taraf bir veri posta kutusu oluşturma ve yapılandırma Microsoft 365. Daha önce de açıklanan gibi, iş ortağı bağlayıcısı öğenin kullanıcı kimliğini kullanıcı hesabıyla eşleyenene kadar öğeler bu posta kutusuna aktarılır.

 **Aşağıdaki görevleri çalışma Microsoft 365 yönetim merkezi**

1. Bir kullanıcı hesabı oluşturun ve bu hesaba Exchange Online Plan 2 lisansı attaynın; bkz. Kullanıcı [ekleme Microsoft 365](../admin/add-users/add-users.md). Posta kutusunu Mahkeme Tutma'ya almak veya en çok 1,5 TB depolama kotası olan bir arşiv posta kutusunu etkinleştirmek için Plan 2 lisansı gereklidir.

2. Üçüncü taraf veri posta kutusunun kullanıcı hesabını, Exchange'de yönetici rolüne Microsoft 365; bkz. [Microsoft 365.](../admin/add-users/assign-admin-roles.md)

    > [!TIP]
    > Bu kullanıcı hesabının kimlik bilgilerini bir yere yazın. 4. Adımda açıklandığı gibi iş ortağınıza bu bilgileri sağlaym gerekir.

 **Yönetim merkezinde bu Exchange tamamlama**

1. Üçüncü taraf veri posta kutusunu adres defterine ve organizasyon daki diğer adres listelerinden gizleme; bkz [. Kullanıcı posta kutularını yönetme](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Alternatif olarak, aşağıdaki PowerShell komutunu da çalıştırabilirsiniz:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Yöneticilerin veya uyumluluk görevlilerinin Outlook masaüstü istemcisinde üçüncü taraf veri posta kutusunu açlarını sağlamak için üçüncü taraf veri posta kutusuna **FullAccess** izni atamazsınız. Bkz. Alıcılar için [izinleri yönetme](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Üçüncü taraf veri posta kutusu için aşağıdaki uyumlulukla ilgili özellikleri etkinleştirin:

    - Arşiv posta kutusunu etkinleştirin; Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) [ve Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md). Bu, üçüncü taraf veri öğelerini arşiv posta kutusuna taşırken bir arşiv ilkesi ayarek birincil posta kutusunda depolama alanını serbest bırakır. Bu, üçüncü taraf veriler için size 1,5 TB'a kadar depolama alanı sağlar.

    - Üçüncü taraf veri posta kutusunu Mahkeme Tutma'ya alın. Güvenlik ve uyumluluk Microsoft 365 bekletme ilkesi de uygulayabilirsiniz. Bu posta kutusunun beklemeye alınması, üçüncü taraf veri öğelerini (süresiz veya belirtilen süre boyunca) korur ve bu öğelerin posta kutusundan temizkodunulmalarını önler. Aşağıdaki konulardan birini bakın:

      - [Mahkeme Tutma'ya posta kutusu](./create-a-litigation-hold.md)

      - [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi](retention.md)

    - Üçüncü taraf veri posta kutusuna sahip, temsilci ve yönetici erişimi için posta kutusu denetim günlüğünü etkinleştirin; Bkz [. Posta kutusu denetimini etkinleştirme](enable-mailbox-auditing.md). Bu, üçüncü taraf veri posta kutusuna erişimi olan tüm kullanıcılar tarafından gerçekleştirilen tüm etkinlikleri denetlemeye olanak sağlar.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>3. Adım: Üçüncü taraf verileri için kullanıcı posta kutularını yapılandırma

Sonraki adım, kullanıcı posta kutularını üçüncü taraf verilerini destekleyecek şekilde yapılandırmaktır. Yönetim merkezini veya ilgili <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> cmdlet'lerini kullanarak bu Windows PowerShell gerçekleştirin.

1. Arşiv posta kutusunu her kullanıcı için etkinleştirme; Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) [ve Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).

2. Kullanıcı posta kutularını Mahkeme Tutma'ya alın veya Microsoft 365 bekletme ilkesi uygulamak için aşağıdaki konulardan birini kullanın:

    - [Mahkeme Tutma'ya posta kutusu](./create-a-litigation-hold.md)

    - [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi](retention.md)

    Daha önce de belirtildiği gibi, posta kutularını yerinde tutarken üçüncü taraf veri kaynağından gelen öğelerin ne kadar süreyle tutulacaklarını ayarlayın veya öğeleri süresiz olarak tutmayı seçebilirsiniz.

## <a name="step-4-provide-your-partner-with-information"></a>4. Adım: İş ortağınıza bilgi sağlama

Son adım, iş ortağınıza aşağıdaki bilgileri sağlamak, böylelikle bağlayıcıyı kuruluşa bağlanarak kullanıcı posta kutularına ve üçüncü taraf veri posta kutularına veri aktaracak şekilde yapılandırmalarını sağlamaktır.

- Azure'da Azure hizmetine bağlanmak için kullanılan uç Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- 2. Adımda oluşturduğunuz üçüncü taraf veri posta kutusunun oturum açma kimlik bilgileri (Microsoft 365 kullanıcı kimliği ve paroladır). İş ortağı bağlayıcısı öğeleri kullanıcı posta kutularına ve üçüncü taraf veri posta kutusuna erişesin ve içeri aktarsın için bu kimlik bilgileri gereklidir.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>5. Adım: Üçüncü taraf veri bağlayıcılarını Yeni'ye Azure Active Directory

Microsoft 365'daki Azure hizmeti, 30 Eylül 2018'den başlayarak, verileri içeri aktarmaya çalışan üçüncü taraf veri bağlayıcılarının kimliğini doğrulamak için Exchange Online'te modern kimlik doğrulamayı kullanmaya başlayacaktır. Bu değişikliğin nedeni, modern kimlik doğrulamanın Azure hizmetine bağlanmak için daha önce açıklanan uç noktayı kullanan üçüncü taraf bağlayıcıların izin listesine dayalı olan geçerli yöntemden daha fazla güvenlik sağladığıdır.

Yeni modern kimlik doğrulama yöntemini kullanarak üçüncü taraf bir veri bağlayıcısını Microsoft 365'e bağlamak için, kuruluş yöneticinizin bağlayıcıyı Azure Active Directory'te güvenilir bir hizmet uygulaması olarak kaydettirdiğini kabul Azure Active Directory. Bu, bağlayıcının belirli bir süre içinde kuruluş verilerinize erişmesine izin vermek için bir izin isteği kabul Azure Active Directory. Bu isteği kabul ettikten sonra, üçüncü taraf veri bağlayıcısı kurumsal uygulama olarak eklenir ve Azure Active Directory sorumlusu olarak temsil edilir. İzin süreci hakkında daha fazla bilgi için bkz.  [Kiracı Yöneticisi İzini](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Bağlayıcıyı kaydetme isteğine erişmek ve isteği kabul etmek için gereken adımlar:

1. Bu [sayfaya gidin](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) ve genel yöneticinin kimlik bilgilerini kullanarak oturum açın.

   Aşağıdaki iletişim kutusu görüntülenir. Bağlayıcıya atanacak izinleri gözden geçirmek için bağlayıcıları genişletebilirsiniz.

   ![İzin isteği iletişim kutusu görüntülenir.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. Kabul **Et'e tıklayın**.

İsteği kabul ettikten sonra [Azure portalı](https://portal.azure.com) görüntülenir. Kuruma uygulama listesini görüntülemek için Uygulama ekle'yi **Azure Active Directory** >  **Enterprise tıklayın**. En Microsoft 365 üçüncü taraf veri bağlayıcısı, Enterprise **blade üzerinde** listelenir.

> [!IMPORTANT]
> 30 Eylül 2018'den sonra, Azure Active Directory'te üçüncü taraf veri bağlayıcısı kaydetmezsanız, üçüncü taraf verileri artık kuruluş posta kutularına aktarılmaz. Var olan üçüncü taraf veri bağlayıcıları (30 Eylül 2018'den önce oluşturulmuş olanlar) ayrıca 5. Adım'daki yordam Azure Active Directory bu bağlayıcıların da Azure Active Directory kaydedilmiş olması gerektiğini unutmayın.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Üçüncü taraf veri bağlayıcısı için onayı iptal

Organizasyonunız izin isteğini kabul ettikten sonra Azure Active Directory'da üçüncü taraf veri bağlayıcısı kaydetmek için izin isteğine onay verdikten sonra, bu izni istediğiniz zaman iptal etmek için bu izni kullanabilir. Bununla birlikte, bağlayıcının rızasını geri almak, üçüncü taraf veri kaynağından gelen verilerin artık üçüncü taraf veri kaynağına aktarılamay anlamına Microsoft 365.

Üçüncü taraf veri bağlayıcısı onayını iptal etmek için, uygulamayı Azure Active Directory (ilgili hizmet sorumlusunı silerek) Azure portalında Enterprise uygulamaları blade kullanarak **veya Microsoft 365** PowerShell'de [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) kullanarak Microsoft 365 silebilirsiniz. Ayrıca, Azure Active Directory PowerShell'de [Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) cmdlet'ini de kullanabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

- Daha önce de açıklanan gibi, üçüncü taraf veri kaynaklarından gelen öğeler e-Exchange olarak bu posta kutularına aktarılır. İş ortağı bağlayıcısı, Microsoft 365 API için gereken bir şema kullanarak öğeyi içeri Microsoft 365. Aşağıdaki tabloda, üçüncü taraf bir veri kaynağından bir öğe bir Exchange e-posta iletisi olarak aktarıldıktan sonra bu öğenin ileti özellikleri açık almaktadır. Tablo ileti özelliğinin zorunlu olup olduğunu da gösterir. Zorunlu özellikler doldurulması gerekir. Bir öğenin zorunlu bir özelliği yoksa, bu öğe başka bir öğeye Microsoft 365. İçeri aktarma işlemi, bir öğenin neden içeri aktarıla olmadığını ve hangi özelliğin eksik olduğunu açıklayan bir hata iletisi döndürür.<br/><br/>

    |**İleti özelliği**|**Zorunlu mu?**|**Açıklama**|**Örnek değer**|
    |:-----|:-----|:-----|:-----|
    |**KAYNAK** <br/> |Evet  <br/> |Öğeyi ilk oluşturan veya üçüncü taraf veri kaynağında gönderdi. İş ortağı bağlayıcısı kaynak öğeden (örneğin Twitter tutamacı) kullanıcı kimliğini, tüm katılımcılar için bir kullanıcı hesabına (FROM ve TO alanlarındaki kullanıcılar) eşlemeye çalışır. İletinin bir kopyası, her katılımcının posta kutusuna aktarılır. Öğeden hiçbir katılımcı kullanıcı hesabına eşlenmemişse, öğe aynı anda üçüncü taraf arşivleme posta kutusuna Microsoft 365.  <br/> <br/> Öğenin göndereni olarak tanımlanan katılımcının, öğenin aktarıldı olduğu kuruluşta etkin bir posta kutusu olması gerekir. Gönderenin etkin bir posta kutusu yoksa aşağıdaki hata döndürülür:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**HEDEF** <br/> |Evet  <br/> |Veri kaynağında bir öğe için uygunsa, öğeyi alan kullanıcı.  <br/> | `bob@contoso.com` <br/> |
    |**KONU** <br/> |Hayır  <br/> |Kaynak öğeden gelen konu.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**DATE** <br/> |Evet  <br/> |Öğenin ilk oluşturulma veya müşteri veri kaynağına gönderilen tarih. Örneğin, bir Twitter iletisine tweet atılan tarih.  <br/> | `01 NOV 2015` <br/> |
    |**GÖVDE** <br/> |Hayır  <br/> |İletinin veya gönderinin içeriği. Bazı veri kaynaklarında, bu özelliğin içeriği SUBJECT özelliğinin içeriğiyle **aynı** olabilir. İçeri aktarma işlemi sırasında, iş ortağı bağlayıcısı içerik kaynağından mümkün olduğunca tam uygunluk korumaya çalışır. Kaynak öğenin gövdesinde yer alan olası dosyalar, grafikler veya başka içerikler bu özele dahil edilirse. Aksi takdirde, kaynak öğeden gelen içerik ATTACHMENT **özelliğine** dahil edilir. Bu özelliğin içeriği iş ortağı bağlayıcıya ve kaynak platformun kapasitesine bağlıdır.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**EK** <br/> |Hayır  <br/> |Veri kaynağında (Twitter'daki bir tweet veya anlık ileti konuşması gibi) bir öğenin ekli bir dosyası varsa veya resim varsa, iş ortağı bağlantısı önce **BODY** özelliğine ekleri dahil etmek ister. Bu mümkün değilse ** ATTACHMENT ** özelliğine eklenir. Eklerin diğer örnekleri arasında Facebook'ta Beğeniler, içerik kaynağından gelen meta veriler ve iletiye veya gönderiye verilen yanıtlar yer alır.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |Evet  <br/> | Bu, iş ortağı bağlayıcısı tarafından oluşturulan ve doldurulan çok değerli bir özelliktir. Bu özelliğin biçimidir  `IPM.NOTE.Source.Event`. (Bu özellik ile başlasın  `IPM.NOTE`. Bu biçim ileti sınıfındaki biçime  `IPM.NOTE.X` benzer.) Bu özellik aşağıdaki bilgileri içerir:  <br/><br/>`Source`: Üçüncü taraf veri kaynağını gösterir; örneğin, Twitter, Facebook veya BlackBerry.  <br/> <br/>  `Event`: Öğeleri üreten üçüncü taraf veri kaynağında gerçekleştirilen etkinlik türünü gösterir; örneğin, Twitter'da bir tweet veya Facebook'ta bir gönderi. Olaylar veri kaynağına özeldir.  <br/> <br/>  Bu özelliğin bir amacı, bir öğenin kaynaklandığı veya olayın türüne dayalı olarak belirli öğelere filtre uygulamadır. Örneğin, eBulma aramalarında belirli bir kullanıcı tarafından gönderilen tüm tweet'leri bulmak için bir arama sorgusu oluşturabilirsiniz.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- Öğeler Microsoft 365'ta posta kutularına başarıyla aktarıldıklarında, benzersiz bir tanımlayıcı HTTP yanıtının bir parçası olarak arayana geri döndürülür. olarak adlandırılan bu  `x-IngestionCorrelationID`tanımlayıcı, iş ortakları tarafından öğelerin 4-4 bit izlemesi için sonradan sorun giderme amacıyla kullanılabilir. İş ortaklarının bu bilgileri kendileriyle yakalamaları ve bilgileri kendi sonunda günlüğe açmaları önerilir. Bu tanımlayıcıyı gösteren http yanıtı örneği:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Güvenlik ve uyumluluk merkezinde bulunan İçerik Arama aracını kullanarak, üçüncü taraf bir veri kaynağından posta kutularına aktarılmış olan öğeleri arayabilirsiniz. Özel olarak bu alınan öğeleri aramak için, İçerik Arama'nın anahtar sözcük kutusunda aşağıdaki ileti özellik-değer çiftlerini kullanabilirsiniz.

  - **`kind:externaldata`**: Tüm üçüncü taraf veri türlerinde arama yapmak için bu özellik değeri çiftini kullanın. Örneğin, üçüncü taraf bir veri kaynağından aktarılan ve alınan öğenin Konu özelliğinde "contoso" sözcüğünü içeren öğeleri aramak için anahtar sözcük sorgusunu kullanabilirsiniz  `kind:externaldata AND subject:contoso`.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: Bu özellik-değer çiftini yalnızca belirli bir üçüncü taraf veri türünü aramak için kullanın. Örneğin, Konu özelliğinde yalnızca "contoso" sözcüğünü içeren Facebook verisinde arama yapmak için anahtar sözcük sorgusunu kullanabilirsiniz  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`.

  Özellikte üçüncü taraf `itemclass` veri türlerinde kullanmak üzere değerlerin tam listesi için, bkz. İçerik Arama'ya aktarılmış olan üçüncü taraf verilerinde [arama Microsoft 365](use-content-search-to-search-third-party-data-that-was-imported.md).

   İçerik Arama'nın kullanımı ve anahtar sözcük arama sorguları oluşturma hakkında daha fazla bilgi için bkz:

  - [İçerik Arama](content-search.md)

  - [İçerik Arama için Anahtar Sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)