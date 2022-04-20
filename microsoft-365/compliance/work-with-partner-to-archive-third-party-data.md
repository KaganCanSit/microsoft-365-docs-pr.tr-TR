---
title: Üçüncü taraf verilerini arşivlemek için bir iş ortağıyla çalışma
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
description: Salesforce Chatter, Yahoo Messenger veya Yammer gibi veri kaynaklarından üçüncü taraf verileri içeri aktarmak için özel bağlayıcı ayarlamayı öğrenin.
ms.openlocfilehash: eb557f43b97f343c45a7eaf21268ac6218d2e1c0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995326"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>Üçüncü taraf verilerini arşivlemek için bir iş ortağıyla çalışma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Üçüncü taraf veri kaynağındaki verileri Microsoft 365 içeri aktarmak ve arşivlemek için bir Microsoft İş Ortağı ile çalışabilirsiniz. İş ortağı, üçüncü taraf veri kaynağından öğeleri ayıklamak (düzenli olarak) ve ardından bu öğeleri içeri aktarmak için yapılandırılmış özel bir bağlayıcı sağlayabilir. İş ortağı bağlayıcısı, bir öğenin içeriğini veri kaynağından e-posta iletisi biçimine dönüştürür ve sonra öğeleri posta kutularında depolar. Üçüncü taraf verileri içeri aktarıldıktan sonra, bu verilere Dava Tutma, eBulma, In-Place Arşivleme, Denetim ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz.

> [!IMPORTANT]
> Microsoft 365'deki [İletişim uyumluluğu](communication-compliance.md) çözümü, bu makalede bahsedilen iş ortağı bağlayıcıları tarafından içeri aktarılan üçüncü taraf verilere uygulanamaz.

Burada, üçüncü taraf verileri içeri aktarmak için bir Microsoft İş Ortağı ile çalışmak için gerekli işlemlere ve adımlara genel bir bakış bulabilirsiniz.

[1. Adım: Üçüncü taraf veri iş ortağı bulma](#step-1-find-a-third-party-data-partner)

[2. Adım: Üçüncü taraf veri posta kutusu oluşturma ve yapılandırma](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[3. Adım: Üçüncü taraf veriler için kullanıcı posta kutularını yapılandırma](#step-3-configure-user-mailboxes-for-third-party-data)

[4. Adım: İş ortağınıza bilgi sağlayın](#step-4-provide-your-partner-with-information)

[5. Adım: Üçüncü taraf veri bağlayıcısını Azure Active Directory'ye kaydetme](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>Üçüncü taraf veri içeri aktarma işlemi nasıl çalışır?

Aşağıdaki çizim ve açıklama, bir iş ortağıyla çalışırken üçüncü taraf veri içeri aktarma işleminin nasıl çalıştığını açıklar.

![Üçüncü taraf veri içeri aktarma işleminin işleyişi.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. Müşteri, üçüncü taraf veri kaynağından öğeleri ayıklayacak ve ardından bu öğeleri Microsoft 365 aktaracak bir bağlayıcı yapılandırmak için tercih ettikleri iş ortağıyla birlikte çalışır.

2. İş ortağı bağlayıcısı üçüncü taraf veri kaynaklarına bir üçüncü taraf API aracılığıyla bağlanır (zamanlanmış veya yapılandırılmış olarak) ve veri kaynağından öğeleri ayıklar. İş ortağı bağlayıcısı bir öğenin içeriğini e-posta iletisi biçimine dönüştürür. İleti biçimi şemasının açıklaması için [Daha fazla bilgi](#more-information) bölümüne bakın.

3. İş ortağı bağlayıcısı, Exchange Web Hizmeti'ni (EWS) iyi bilinen bir uç nokta aracılığıyla kullanarak Microsoft 365'da Azure hizmetine bağlanır.

4. Öğeler belirli bir kullanıcının posta kutusuna veya "tümünü yakala" üçüncü taraf veri posta kutusuna aktarılır. Bir öğenin belirli bir kullanıcı posta kutusuna mı yoksa üçüncü taraf veri posta kutusuna mı içeri aktarılıp aktarılmadığı aşağıdaki ölçütlere bağlıdır:

   1. **Kullanıcı hesabına karşılık gelen kullanıcı kimliğine sahip öğeler:** İş ortağı bağlayıcısı üçüncü taraf veri kaynağındaki öğenin kullanıcı kimliğini Microsoft 365'deki belirli bir kullanıcı kimliğiyle eşleyebilirse, öğe kullanıcının Kurtarılabilir Öğeler klasöründeki **Temizleme** klasörüne kopyalanır. Kullanıcılar Temizleme klasöründeki öğelere erişemez. Ancak, Temizleme klasöründeki öğeleri aramak için eBulma araçlarını kullanabilirsiniz.

   1. **Kullanıcı hesabına karşılık gelen kullanıcı kimliği olmayan öğeler:** İş ortağı bağlayıcısı bir öğenin kullanıcı kimliğini belirli bir kullanıcı kimliğiyle eşleyemezse, öğe üçüncü taraf veri posta kutusunun **Gelen Kutusu** klasörüne kopyalanır. Öğeleri gelen kutusuna aktarma, sizin veya kuruluşunuzdaki bir kişinin bu öğeleri görüntülemek ve yönetmek için üçüncü taraf posta kutusunda oturum açmanızı ve iş ortağı bağlayıcı yapılandırmasında herhangi bir ayarlama yapılması gerekip gerekmediğini görmenizi sağlar.

## <a name="step-1-find-a-third-party-data-partner"></a>1. Adım: Üçüncü taraf veri iş ortağı bulma

Microsoft 365'da üçüncü taraf verileri arşivlemenin önemli bileşenlerinden biri, üçüncü taraf veri kaynağından verileri yakalama ve Microsoft 365 içeri aktarma konusunda uzmanlaşmış bir Microsoft iş ortağı bulmak ve bu iş ortağıyla çalışmaktır. Veriler içeri aktarıldıktan sonra, Exchange gelen e-posta ve SharePoint ve OneDrive İş belgeleri gibi kuruluşunuzun diğer Microsoft verileriyle birlikte arşivlenebilir ve korunabilir. İş ortağı, kuruluşunuzun üçüncü taraf veri kaynaklarından (BlackBerry, Facebook, Google+, Thomson Reuters, Twitter ve YouTube gibi) verileri ayıklayan ve bu verileri Exchange posta kutularına e-posta iletisi olarak aktaran bir Microsoft 365 API'sine geçiren bir bağlayıcı oluşturur.

Aşağıdaki bölümlerde, Microsoft 365'da üçüncü taraf verilerini arşivleme programına katılan Microsoft iş ortakları (ve destekledikleri üçüncü taraf veri kaynakları) listelenir.

[17a-4 LLC](#17a-4-llc)

[ArşivSosyal](#archivesocial)

[Veritas](#veritas)

[OpenText](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[17a-4 LLC](https://www.17a-4.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Blackberry

- Bloomberg Veri Akışlar

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- MessageLabs Veri Akışlar

- OpenText

- Oracle/ATG 'tıkla-ara' Canlı Yardımı

- Özet IMTRADER

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype Kurumsal (Lync/OCS)

- Skype Kurumsal Online (Lync Online)

- veritabanlarını SQL

- Squawker

- Thomson Reuters Eikon Messenger

### <a name="archivesocial"></a>ArşivSosyal

[ArchiveSocial](https://www.archivesocial.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Facebook

- Flickr

- Instagram

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[Veritas](https://www.globanet.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Pivot Client ile AOL

- BlackBerry Çağrı Günlükleri (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Sohbeti

- Bloomberg Mail

- Kutusu

- Salesforce Chatter için CipherCloud

- Cisco IM &amp; İletişim Durumu Sunucusu (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- Özel olarak sınırlandırılmış metin dosyaları

- Özel XML dosyaları

- Facebook (Sayfalar)

- Olgu Kümesi

- FXConnect

- ICE Sohbeti/YellowJacket

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive İş

- Microsoft Teams

- Microsoft Yammer

- Mobile Guard

- Pivot

- Salesforce Chatter

- Skype Kurumsal Çevrimiçi

- Skype Kurumsal, sürüm 2007 R2 - 2016 (şirket içi)

- Slack Enterprise Kılavuzu

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Thomson Reuters Dealings 3000 / FX Trading

- Twitter

- UBS Sohbeti

- YouTube

### <a name="opentext"></a>OpenText

[OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Axs Encrypted

- Axs Exchange

- Axs Yerel Arşivi

- Axs PlaceHolder

- Axs İmzalı

- Bloomberg

- Thomson Reuters

### <a name="smarsh"></a>Smarsh

[Smarsh](https://www.smarsh.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- AMACI

- Amerikan Idol

- Elma Suyu

- Pivot istemcisi ile AOL

- Ares

- Çarşı Sesi

- Ayı Payı

- Bit Torrent

- BlackBerry Çağrı Günlükleri (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- Bloomberg Mail

- CellTrust

- Sohbet İçeri Aktarma

- Gerçek Zamanlı Sohbet Günlüğü ve İlkesi

- Sohbet

- Cisco IM &amp; İletişim Durumu Sunucusu (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (v8.6.3, v8.6.4, v8.6.5)

- İşbirliği İçeri Aktarma

- İşbirliği Gerçek Zamanlı Günlüğe Kaydetme

- Doğrudan Bağlan

- Facebook

- FactSet

- FastTrack

- Gnutella

- Google+

- GoToMyPC

- Hopster

- HubConnex

- IBM Bağlantıları (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowJacket

- Anlık İleti İçeri Aktarma

- Anlık İleti Gerçek Zamanlı Günlüğe Kaydetme ve İlke

- Indii Messenger

- Instant Bloomberg

- IRC

- Jive

- Jive 6 Gerçek Zamanlı Günlüğe Kaydetme (v6, v7)

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

- Lync Ayrılmış Microsoft 365

- Paylaşılan anlık Microsoft 365

- Pinterest

- Pivot

- QQ

- Skype Kurumsal 2015

- SoftEther

- Symphony

- Thomson Reuters Eikon

- Thomson Reuters Messenger

- Tor

- TTT

- Twitter

- Winmx

- Winny

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[Verba](https://www.verba.com) aşağıdaki üçüncü taraf veri kaynaklarını destekler:

- Avaya Aura Video

- Avaya Aura Sesi

- Avtec Radyo

- Bosch/Telex Radio

- BroadSoft Video

- BroadSoft Voice

- Centile Voice

- Cisco Jabber anlık ileti

- Cisco UC Videosu

- Cisco UC Voice

- Cisco UCCX/UCCE Video

- Cisco UCCX/UCCE Voice

- ESChat Radyo

- Geoman Contact Expert

- IP Ticaret Sesi

- Luware LUCS İletişim Merkezi

- Microsoft UC (Birleşik İletişim)

- Lync için Mitel MiContact Merkezi (prairieFyre)

- Oracle / Acme Paket Oturumu Sınır Denetleyicisi Videosu

- Oracle / Acme Paket Oturumu Sınır Denetleyicisi Sesi

- Singtel Mobile Voice

- SIPREC Video

-  SIPREC Voice

- Skype Kurumsal / Lync Anlık İletisi

- Skype Kurumsal / Lync Video

- Skype Kurumsal / Lync Voice

- Speakerbus Voice

- Standart SIP/H.323 Video

- Standart SIP/H.323 Ses

- Truphone Voice

- TwistedPair Radyo

- masaüstü bilgisayar ekranını Windows

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>2. Adım: Microsoft 365'de üçüncü taraf veri posta kutusu oluşturma ve yapılandırma

Verileri Microsoft 365 aktarmak için üçüncü taraf veri posta kutusu oluşturma ve yapılandırma adımları aşağıdadır. Daha önce açıklandığı gibi, iş ortağı bağlayıcısı öğenin kullanıcı kimliğini bir kullanıcı hesabıyla eşleyemiyorsa öğeler bu posta kutusuna aktarılır.

 **Bu görevleri Microsoft 365 yönetim merkezi**

1. Bir kullanıcı hesabı oluşturun ve Exchange Online Plan 2 lisansı atayın; bkz. [Microsoft 365 kullanıcı ekleme](../admin/add-users/add-users.md). Posta kutusunu Dava Tutma'ya yerleştirmek veya depolama kotası 1,5 TB'a kadar olan bir arşiv posta kutusunu etkinleştirmek için Plan 2 lisansı gerekir.

2. Üçüncü taraf veri posta kutusunun kullanıcı hesabını **Microsoft 365'daki Exchange yönetici** yönetici rolüne ekleyin; bkz. [Microsoft 365'da yönetici rolleri atama](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > Bu kullanıcı hesabının kimlik bilgilerini not edin. Bunları 4. Adımda açıklandığı gibi iş ortağınıza sağlamanız gerekir.

 **Bu görevleri Exchange yönetim merkezinde tamamlayın**

1. Üçüncü taraf veri posta kutusunu kuruluşunuzdaki adres defterinden ve diğer adres listelerinden gizleyin; bkz. [Kullanıcı posta kutularını yönetme](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). Alternatif olarak, aşağıdaki PowerShell komutunu çalıştırabilirsiniz:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. Yöneticilerin veya uyumluluk görevlilerinin üçüncü taraf veri posta kutusunu Outlook masaüstü istemcisinde açabilmesi için üçüncü taraf veri posta kutusuna **FullAccess** iznini atayın; bkz. [Alıcılar için izinleri yönetme](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. Üçüncü taraf veri posta kutusu için aşağıdaki uyumlulukla ilgili özellikleri etkinleştirin:

    - Arşiv posta kutusunu etkinleştirin; Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) ve [Arşivlemeyi otomatik genişletmeyi etkinleştirme](enable-autoexpanding-archiving.md). Bu, üçüncü taraf veri öğelerini arşiv posta kutusuna taşıyan bir arşiv ilkesi ayarlayarak birincil posta kutusunda depolama alanı boşaltmanıza olanak tanır. Bu, üçüncü taraf veriler için 1,5 TB'a kadar depolama alanı sağlar.

    - Üçüncü taraf veri posta kutusunu Dava Tutma'ya yerleştirin. Güvenlik ve uyumluluk merkezinde Microsoft 365 bekletme ilkesi de uygulayabilirsiniz. Bu posta kutusunu beklemeye almak, üçüncü taraf veri öğelerini (süresiz veya belirtilen süre boyunca) korur ve bunların posta kutusundan temizlenmesini önler. Aşağıdaki konulardan birine bakın:

      - [Dava Tutma'ya posta kutusu yerleştirme](./create-a-litigation-hold.md)

      - [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md)

    - Üçüncü taraf veri posta kutusuna sahip, temsilci ve yönetici erişimi için posta kutusu denetim günlüğünü etkinleştirin; bkz [. Posta kutusu denetimini etkinleştirme](enable-mailbox-auditing.md). Bu, üçüncü taraf veri posta kutusuna erişimi olan tüm kullanıcılar tarafından gerçekleştirilen tüm etkinlikleri denetlemenize olanak tanır.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>3. Adım: Üçüncü taraf veriler için kullanıcı posta kutularını yapılandırma

Sonraki adım, kullanıcı posta kutularını üçüncü taraf verileri destekleyecek şekilde yapılandırmaktır. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini</a> veya ilgili Windows PowerShell cmdlet'lerini kullanarak bu görevleri tamamlayın.

1. Her kullanıcı için arşiv posta kutusunu etkinleştirin; Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) ve [Arşivlemeyi otomatik genişletmeyi etkinleştirme](enable-autoexpanding-archiving.md).

2. Kullanıcı posta kutularını Dava Tutma'ya yerleştirin veya Microsoft 365 bekletme ilkesi uygulayın; aşağıdaki konulardan birine bakın:

    - [Dava Tutma'ya posta kutusu yerleştirme](./create-a-litigation-hold.md)

    - [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md)

    Daha önce belirtildiği gibi, posta kutularını beklemeye aldığınızda, üçüncü taraf veri kaynağındaki öğelerin ne kadar süreyle tutulabileceği için bir süre ayarlayabilir veya öğeleri süresiz olarak saklamayı seçebilirsiniz.

## <a name="step-4-provide-your-partner-with-information"></a>4. Adım: İş ortağınıza bilgi sağlayın

Son adım, bağlayıcıyı kuruluşunuza bağlanıp verileri kullanıcı posta kutularına ve üçüncü taraf veri posta kutusuna aktaracak şekilde yapılandırabilmesi için iş ortağınıza aşağıdaki bilgileri sağlamaktır.

- Microsoft 365'de Azure hizmetine bağlanmak için kullanılan uç nokta:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- 2. Adımda oluşturduğunuz üçüncü taraf veri posta kutusunun oturum açma kimlik bilgileri (Microsoft 365 kullanıcı kimliği ve parolası). Bu kimlik bilgileri, iş ortağı bağlayıcısının kullanıcı posta kutularına ve üçüncü taraf veri posta kutularına erişip öğeleri içeri aktarabilmesi için gereklidir.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>5. Adım: Üçüncü taraf veri bağlayıcısını Azure Active Directory'ye kaydetme

30 Eylül 2018'den itibaren Microsoft 365'deki Azure hizmeti, verileri içeri aktarmak için kuruluşunuza bağlanmaya çalışan üçüncü taraf veri bağlayıcılarının kimliğini doğrulamak için Exchange Online'de modern kimlik doğrulamasını kullanmaya başlayacaktır. Bu değişikliğin nedeni, modern kimlik doğrulamasının geçerli yöntemden daha fazla güvenlik sağlamasıdır. Bu, Azure hizmetine bağlanmak için daha önce açıklanan uç noktayı kullanan üçüncü taraf bağlayıcılar için izin verilenler listesini temel alır.

Bir üçüncü taraf veri bağlayıcısının yeni modern kimlik doğrulama yöntemini kullanarak Microsoft 365 bağlanmasına olanak tanımak için, kuruluşunuzdaki bir yöneticinin bağlayıcıyı Azure Active Directory'de güvenilir bir hizmet uygulaması olarak kaydetmeyi onaylaması gerekir. Bu, bağlayıcının Azure Active Directory'da kuruluşunuzun verilerine erişmesine izin vermek için bir izin isteği kabul ederek yapılır. Bu isteği kabul ettikten sonra, üçüncü taraf veri bağlayıcısı Azure Active Directory kurumsal bir uygulama olarak eklenir ve hizmet sorumlusu olarak temsil edilir. Onay işlemi hakkında daha fazla bilgi için bkz.  [Kiracı Yöneticisi Onayı](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

Bağlayıcıyı kaydetme isteğine erişme ve kabul etme adımları şunlardır:

1. [Bu sayfaya](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) gidin ve genel yöneticinin kimlik bilgilerini kullanarak oturum açın.

   Aşağıdaki iletişim kutusu görüntülenir. Bağlayıcıya atanacak izinleri gözden geçirmek için giriş çizgilerini genişletebilirsiniz.

   ![İzin isteği iletişim kutusu görüntülenir.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. **Kabul Et'e** tıklayın.

İsteği kabul ettikten sonra [Azure portal](https://portal.azure.com) görüntülenir. Kuruluşunuzun uygulama listesini görüntülemek için **Azure Active Directory** >  **Enterprise uygulamaları'na** tıklayın. Microsoft 365 üçüncü taraf veri bağlayıcısı **, Enterprise uygulamalar** dikey penceresinde listelenir.

> [!IMPORTANT]
> 30 Eylül 2018'in ardından, Azure Active Directory üçüncü taraf veri bağlayıcısı kaydetmezseniz üçüncü taraf veriler artık kuruluşunuzdaki posta kutularına aktarılmayacaktır. Mevcut üçüncü taraf veri bağlayıcılarının (30 Eylül 2018'de oluşturulanlar) 5. Adım'daki yordamı izleyerek Azure Active Directory'ye de kaydedilmesi gerektiğini unutmayın.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>Üçüncü taraf veri bağlayıcısı için onayı iptal etme

Kuruluşunuz Azure Active Directory bir üçüncü taraf veri bağlayıcısını kaydetme izni isteğine onay verdikten sonra, kuruluşunuz bu onayı istediğiniz zaman iptal edebilir. Bununla birlikte, bağlayıcı için onayın iptal edilmesi, üçüncü taraf veri kaynağındaki verilerin artık Microsoft 365 içeri aktarılmayacağı anlamına gelir.

Üçüncü taraf veri bağlayıcısının onayını iptal etmek için, Azure portal Enterprise **uygulamaları** dikey penceresini kullanarak veya Microsoft 365'da [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) kullanarak uygulamayı Azure Active Directory silebilirsiniz (karşılık gelen hizmet sorumlusunu silerek) Powershell. Azure Active Directory PowerShell'de [Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) cmdlet'ini de kullanabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

- Daha önce açıklandığı gibi, üçüncü taraf veri kaynaklarından gelen öğeler Exchange posta kutularına e-posta iletisi olarak aktarılır. İş ortağı bağlayıcısı, Microsoft 365 API'sinin gerektirdiği bir şemayı kullanarak öğeyi içeri aktarır. Aşağıdaki tabloda, e-posta iletisi olarak bir Exchange posta kutusuna aktarıldıktan sonra üçüncü taraf veri kaynağındaki bir öğenin ileti özellikleri açıklanmaktadır. Tablo ayrıca ileti özelliğinin zorunlu olup olmadığını gösterir. Zorunlu özellikler doldurulmalıdır. Bir öğede zorunlu bir özellik eksikse öğe Microsoft 365'a aktarılamaz. İçeri aktarma işlemi, bir öğenin neden içeri aktarılamadığı ve hangi özelliğin eksik olduğunu açıklayan bir hata iletisi döndürür.<br/><br/>

    |**İleti özelliği**|**Zorunlu?**|**Açıklama**|**Örnek değer**|
    |:-----|:-----|:-----|:-----|
    |**KAYNAK** <br/> |Evet  <br/> |Öğeyi ilk olarak üçüncü taraf veri kaynağında oluşturan veya gönderen kullanıcı. İş ortağı bağlayıcısı, kaynak öğedeki kullanıcı kimliğini (örneğin Twitter tanıtıcısı) tüm katılımcılar için bir kullanıcı hesabıyla (KIMDEN ve TO alanlarındaki kullanıcılar) eşlemeyi dener. İletinin bir kopyası her katılımcının posta kutusuna aktarılır. Öğedeki katılımcıların hiçbiri bir kullanıcı hesabıyla eşlenemezse, öğe Microsoft 365 üçüncü taraf arşivleme posta kutusuna aktarılır.  <br/> <br/> Öğenin göndereni olarak tanımlanan katılımcının, öğenin içeri aktarıldığı kuruluşta etkin bir posta kutusu olmalıdır. Gönderenin etkin bir posta kutusu yoksa aşağıdaki hata döndürülür:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**HEDEF** <br/> |Evet  <br/> |Veri kaynağındaki bir öğe için uygunsa bir öğe alan kullanıcı.  <br/> | `bob@contoso.com` <br/> |
    |**KONU** <br/> |Hayır  <br/> |Kaynak öğedeki konu.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**TARİH** <br/> |Evet  <br/> |Öğenin ilk oluşturulduğu veya müşteri veri kaynağında deftere nakledildiği tarih. Örneğin, twitter iletisinin tweetlendiği tarih.  <br/> | `01 NOV 2015` <br/> |
    |**VÜCUT** <br/> |Hayır  <br/> |İletinin veya gönderinin içeriği. Bazı veri kaynakları için bu özelliğin içeriği **SUBJECT** özelliğinin içeriğiyle aynı olabilir. İçeri aktarma işlemi sırasında, iş ortağı bağlayıcısı içerik kaynağından mümkün olduğunca tam uygunluk sağlamaya çalışır. Kaynak öğenin gövdesindeki olası dosyalar, grafikler veya diğer içerikler bu özelliğe dahil edilir. Aksi takdirde, kaynak öğedeki içerik **ATTACHMENT** özelliğine eklenir. Bu özelliğin içeriği, iş ortağı bağlayıcısı ve kaynak platformun özelliğine bağlıdır.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**EKİ** <br/> |Hayır  <br/> |Veri kaynağındaki bir öğenin (Twitter'daki bir tweet veya anlık ileti konuşması gibi) ekli bir dosyası varsa veya görüntüler eklerse, iş ortağı bağlantısı önce **BODY** özelliğine ekleri eklemeyi dener. Bu mümkün değilse** EK ** özelliğine eklenir. Diğer ek örnekleri arasında Facebook'taki Beğeniler, içerik kaynağından meta veriler ve bir ileti veya gönderiye verilen yanıtlar yer alır.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |Evet  <br/> | Bu, iş ortağı bağlayıcısı tarafından oluşturulan ve doldurulan çok değerli bir özelliktir. Bu özelliğin biçimi şeklindedir  `IPM.NOTE.Source.Event`. (Bu özellik ile  `IPM.NOTE`başlamalıdır. Bu biçim, ileti sınıfına  `IPM.NOTE.X` benzer.) Bu özellik aşağıdaki bilgileri içerir:  <br/><br/>`Source`: Üçüncü taraf veri kaynağını gösterir; örneğin, Twitter, Facebook veya BlackBerry.  <br/> <br/>  `Event`: Öğeleri üreten üçüncü taraf veri kaynağında gerçekleştirilen etkinliğin türünü gösterir; örneğin, Twitter'da bir tweet veya Facebook'ta bir gönderi. Olaylar veri kaynağına özeldir.  <br/> <br/>  Bu özelliğin bir amacı, belirli öğeleri bir öğenin kaynaklandığı veri kaynağına veya olay türüne göre filtrelemektir. Örneğin, eBulma aramasında belirli bir kullanıcı tarafından gönderilen tüm tweet'leri bulmak için bir arama sorgusu oluşturabilirsiniz.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- öğeler Microsoft 365'daki posta kutularına başarıyla aktarıldığında, HTTP yanıtının bir parçası olarak çağırana benzersiz bir tanımlayıcı döndürülür. adlı  `x-IngestionCorrelationID`bu tanımlayıcı, öğelerin uçtan uca izlenmesi için iş ortakları tarafından sonraki sorun giderme amacıyla kullanılabilir. İş ortaklarının bu bilgileri yakalaması ve sonunda uygun şekilde günlüğe kaydetmesi önerilir. Bu tanımlayıcıyı gösteren bir HTTP yanıtı örneği aşağıda verilmişti:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- Üçüncü taraf veri kaynağından posta kutularına aktarılan öğeleri aramak için güvenlik ve uyumluluk merkezindeki İçerik Arama aracını kullanabilirsiniz. Bu içeri aktarılan öğeleri özel olarak aramak için, bir İçerik Araması için anahtar sözcük kutusunda aşağıdaki ileti özellik-değer çiftlerini kullanabilirsiniz.

  - **`kind:externaldata`**: Tüm üçüncü taraf veri türlerini aramak için bu özellik-değer çifti kullanın. Örneğin, üçüncü taraf veri kaynağından içeri aktarılan ve içeri aktarılan öğenin Subject özelliğinde "contoso" sözcüğünü içeren öğeleri aramak için anahtar sözcük sorgusunu  `kind:externaldata AND subject:contoso`kullanabilirsiniz.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: Bu özellik-değer çiftini yalnızca bir üçüncü taraf veri türünü belirtmek için kullanın. Örneğin, yalnızca Subject özelliğinde "contoso" sözcüğünü içeren Facebook verilerinde arama yapmak için anahtar sözcük sorgusunu  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`kullanırsınız.

  Özelliğin üçüncü taraf veri türleri için kullanılacak değerlerin tam listesi için `itemclass` bkz. [İçerik Arama'yı kullanarak Microsoft 365 içeri aktarılan üçüncü taraf verileri arama](use-content-search-to-search-third-party-data-that-was-imported.md).

   İçerik Arama'yı kullanma ve anahtar sözcük arama sorguları oluşturma hakkında daha fazla bilgi için bkz:

  - [İçerik Arama](content-search.md)

  - [İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)