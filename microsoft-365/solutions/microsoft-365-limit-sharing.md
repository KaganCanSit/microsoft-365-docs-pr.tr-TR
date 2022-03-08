---
title: Dosyada paylaşımı Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
search.appverid:
- SPO160
- MET150
f1.keywords: NOCSH
ms.custom:
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Aynı dosyada paylaşımı sınırlama veya devre dışı bırakma Microsoft 365.
ms.openlocfilehash: b2e327d5a5c670ada389a3dfceb2775e516ac2aa
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323479"
---
# <a name="limit-sharing-in-microsoft-365"></a>Dosyada paylaşımı Microsoft 365

İç paylaşımı tamamen devre dışı bırakamanıza veya sitelerden Paylaş düğmesini kaldıramanıza gerek yoktur, ancak Microsoft 365'te paylaşımı, kuruluş  ihtiyaçlarını karşılayacak şekilde sınırlandırabilirsiniz.

Dosya paylaşma yöntemleri aşağıdaki tabloda listelenmiştir. Ayrıntılı bilgi için Paylaşım **yöntemi sütunundaki** bağlantıya tıklayın.

|Paylaşım yöntemi|Açıklama|Sınırlama seçenekleri|
|:-------------|:----------|:-------------|
|[Microsoft 365 veya ekibin üyeleri](#microsoft-365-group-or-team)|Bir ekip veya grup Microsoft Teams erişim izni Microsoft 365 kişiler, ilişkili ekip sitesinde yer alan dosyalara düzenleme SharePoint sahip olur.|Grup veya ekip özelse, ekiple katılma davetlerini paylaşmak onay için sahibine gider. Yöneticiler konuk erişimini devre dışı bırakarak veya kuruluşun dışındaki kişilerin erişimini engellemek için duyarlılık etiketlerini kullanabilir.|
|[SharePoint sitesi](#sharepoint-site)|Kullanıcılara sitenin Sahibi, Üyesi veya Ziyaretçisi SharePoint ve sitenin dosyalarına bu düzeyde erişim olur.|Site izinleri kısıtlanabilir ve böylelikle siteyi yalnızca site sahipleri paylaşabilir. Yöneticiler bir siteyi salt okunur olarak veya erişimi tamamen engel olarak ayarlamayı sağlar.|
|[Belirli kişilerle paylaşma](#sharing-with-specific-people)|Site üyeleri ve düzenleme izinleri olan kişiler dosyalara ve klasörlere doğrudan izinler veya Belirli kişiler bağlantılarını kullanarak *bunları paylaşabilir* .|Site izinleri, yalnızca site sahiplerinin dosya ve klasör paylaşama iznine sahip olacak şekilde kısıtlanabilir. Bu durumda, doğrudan erişim ve *Site üyeleri tarafından* belirli kişiler bağlantısı paylaşımı onay için site sahibine gider.|
|[SharePoint ve OneDrive paylaşma](#sharepoint-guest-sharing)|SharePoint sahipleri ve üyeleri OneDrive kuruluş dışındaki kişiler ile dosya ve klasör paylaşabilir.|Konuk paylaşımı tüm kuruluş için veya tek tek siteler için devre dışı bırakılabilir.|
|[*Kuruluşlarda bağlantı paylaşan* kişiler](#people-in-your-organization-sharing-links)|SharePoint site sahipleri ve üyeleri, kuruluş içindeki herkes için uygun olan, kuruluş bağlantılarında yer alan Kişiler'i kullanarak dosyaları paylaşabilir.|*Kuruluş bağlantılarınız site* düzeyinde devre dışı bırakılabilir.|
|[Site, grup ve ekip oluşturma](#create-sites-groups-and-teams)|Varsayılan olarak, kullanıcılar içerik paylaş oluşturdukları yeni siteler, gruplar ve ekipler oluşturabilir.|Yöneticiler kimlerin site, grup ve ekip oluştura etkileyeyi kısıtlar.|
|[E-posta](#email)|Dosyaya erişimi olan kişiler dosyayı e-posta yoluyla başkalarına gönderebilir.|Yöneticiler, yetkisiz kullanıcılarla paylaşılmalarını önlemek için duyarlılık etiketleri kullanarak dosyaları şifreler.|
|[İndir veya dosya kopyası](#download-or-file-copy)|Dosyaya erişimi olan kişiler dosyayı indirebilir veya kopyalayıp dosya kapsamının dışında başka Microsoft 365.|Yöneticiler, yetkisiz kullanıcılarla paylaşılmalarını önlemek için duyarlılık etiketleri kullanarak dosyaları şifreler.|

Ayrıca, kişilerin paylaşılan içeriğe erişimlerini kısıtlamak için koşulları da kısıtabilirsiniz. Daha [fazla bilgi için](#conditional-access) bu makalenin devam daki koşullu erişime bakın.

Bu makalede açıklanan yönetici denetimlerini kullanarak kuruluş paylaşımını sınırlandırabilirsiniz, ancak güvenli bir paylaşım ortamı oluşturmak için Microsoft 365'de bulunan güvenlik ve uyumluluk özelliklerini kullanmayı göz önünde bulundurmanızı kesinlikle öneririz. Daha [fazla bilgi için bkz. SharePoint'de dosya Microsoft 365](/sharepoint/deploy-file-collaboration) [ve Güvenlik yalıtlığı olan bir](secure-teams-security-isolation.md) ekibi yapılandırma.

Kuruluşta paylaşımın nasıl kullanılır olduğunu anlamak için dosya [ve klasör paylaşımıyla ilgili bir rapor çalıştırın](/sharepoint/sharing-reports).

## <a name="microsoft-365-group-or-team"></a>Microsoft 365 veya ekibin üyeleri

Bir grup veya ekipte Microsoft 365 sınırlamak Microsoft Teams, grubu veya ekibi özel yapmak önemlidir. Kurum içindeki kişiler istediğiniz zaman genel gruba veya takıma katılabilir. Grup veya ekip özel değilse, ekibin veya dosyaların kuruluş içinde paylaşımını sınırlamanın hiçbir yolu yoktur.

### <a name="guest-sharing"></a>Konuk paylaşımı

E-postada konuk erişimini engellemek Teams yönetim merkezinde konuk paylaşımını Teams kapatmış olursanız.

Bir ekipte konuk paylaşımını kapatmak Teams
1. Genel Teams <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**ayarlarıGuest erişim sekmesi'ni**</a> >  genişletin.
2. **E-postada konuk erişimine izin ver Teams**.
3. **Kaydet**'e tıklayın.

Gruplarda konuk erişimini engellemek Microsoft 365, grup gruplarında konuk erişimi ayarlarını Microsoft 365 yönetim merkezi.

Gruplarda konuk paylaşımını Microsoft 365 için
1. Görünüm Microsoft 365 yönetim merkezi **, Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services sekmesine** tıklayın</a>.
2. Grupları Ekle **Microsoft 365 i tıklatın**.
3. Grup üyelerinin **kuruluş dışından grup içeriğine erişmesine izin ver ve** Grup sahiplerinin kuruluş dışındakileri gruplara **eklemesine izin ver onay** kutularını temizleyin.
4. **Değişiklikleri kaydet**’e tıklayın.

    ![Çalışma sayfasında Microsoft 365 Grupları paylaşma ayarlarının Microsoft 365 yönetim merkezi.](../media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> Belirli bir grup veya ekipte konuk paylaşımını engellemek için [Microsoft PowerShell](per-group-guest-access.md) veya duyarlılık etiketlerini [kullanarak bunu kullanabilirsiniz](../compliance/sensitivity-labels-teams-groups-sites.md).

Konuk paylaşımını, belirli etki alanlarındaki etki alanlarına izin vererek veya engelleyerek, belirli etki alanlarındaki kullanıcılarla Azure Active Directory. Bu durum, Azure [AD B2B ile SharePoint tümleştirmeyi etkinleştirdiyseniz SharePoint konuk paylaşımını da OneDrive etki edecek](/sharepoint/sharepoint-azureb2b-integration-preview).

Yalnızca belirli etki alanlarından paylaşım davetlerine izin vermek için
1. Genel Azure Active Directory sayfasında Kuruluş **ilişkileri'ne tıklayın**.
2. **Ekle'Ayarlar**.
3. İşbirliği **kısıtlamaları'nın** altında Belirtilen etki alanları için **davetleri** reddet'i veya Yalnızca belirtilen etki alanlarına davetlere izin ver'i seçin ve kullanmak istediğiniz etki alanlarını yazın.
4. **Kaydet**'e tıklayın.

    ![çalışma sayfasında işbirliği kısıtlamaları ayarlarının ekran Azure Active Directory.](../media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>SharePoint sitesi

Site paylaşımını yalnızca SharePoint sahipleriyle sınırlandırabilirsiniz. Bu, site üyelerinin siteyi paylaşmasını önler. Site bir grupla bağlantılı ise Microsoft 365 üyelerinin gruba başkalarını davet etseler de bu kullanıcıların site erişimi olur.

Site paylaşımını sahiplerle sınırlamak için
1. Sitede, dişli simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
2. Paylaşım **ayarları'nın** altında Paylaşım ayarlarını **değiştir'e tıklayın**.
3. Site **sahipleri ve üyeleri'ne tıklayın; Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir, ancak yalnızca site sahipleri siteyi paylaşabilir**.
4. **Kaydet**'e tıklayın.

    ![Bir siteden izin paylaşma ayarlarının ekran SharePoint görüntüsü.](../media/sharepoint-site-sharing-permissions-level-two.png)

Erişim isteklerini kapatarak, sitenin üyesi olan kullanıcıların erişim isteğite bulunanları engellemeniz gerekir.

Erişim isteklerini kapatmak için
1. Sitede, dişli simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
2. Paylaşım **ayarları'nın** altında Paylaşım ayarlarını **değiştir'e tıklayın**.
3. Erişim **isteklerine izin ver'i kapatın** ve Kaydet'e **tıklayın**.

Site için etki alanlarına izin vererek veya engelleyerek site paylaşımını belirli etki alanlarıyla sınırlandırabilirsiniz.

Site paylaşımını etki alanına göre sınırlamak için

1. Yönetim merkezinde SharePoint altında Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. Yapılandırmak istediğiniz siteyi seçin.
3. İlkeler **sekmesinde** , Dış **paylaşım'ın altında Düzenle'yi** **seçin**.
4. Dış **paylaşım için gelişmiş ayarlar'ın** altında Etki alanına **göre paylaşımı sınırla'ya tıklayın**.
5. İzin vermek veya engellemek istediğiniz etki alanlarını ekleyin ve ardından Kaydet'i **seçin**.
6. **Kaydet**'i seçin.

    ![İzin verilen etki alanları site düzeyi ayarının ekran görüntüsü.](../media/limit-site-sharing-by-domain.png)

### <a name="block-access-to-a-site"></a>Siteye erişimi engelleme

Sitenin kilit durumunu değiştirerek siteye erişimi engelleyebilir veya siteyi salt okunur hale edebilirsiniz. Ayrıntılar için bkz. [Siteleri kilitleme ve kilidini açma](/sharepoint/manage-lock-status).

### <a name="permissions-inheritance"></a>İzin devralma

Önerilmez, ancak sitelere ve alt [sitelere SharePoint düzeyleri](/sharepoint/what-is-permissions-inheritance) özelleştirmek için izin devralmayı kullanabilirsiniz.

## <a name="sharing-with-specific-people"></a>Belirli kişilerle paylaşma

Sitenin veya içeriğinin paylaşımını sınırlamak için siteyi, yalnızca site sahiplerinin dosyaları, klasörleri ve siteyi paylaşmasına izin verecek şekilde yapılandırabilirsiniz. Bu yapılandırıldığında, site üyeleri Belirli kişiler bağlantılarını kullanarak dosya veya klasör paylaşmayı dener ve onay  için site sahibine gider.

Site, dosya ve klasör paylaşımını sahiplerle sınırlamak için
1. Sitede, dişli simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
2. Paylaşım **ayarları'nın** altında Paylaşım ayarlarını **değiştir'e tıklayın**.
3. Yalnızca **site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir öğesini seçin**.
4. **Kaydet**'e tıklayın.

    ![Sitenin yalnızca sahiplere özel SharePoint izin ayarlarının ekran görüntüsü.](../media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>SharePoint paylaşımı

Dosyaların ve klasörlerin kuruluş SharePoint veya OneDrive paylaşımını engellemek için, tüm kuruluşta veya tek bir site için konuk paylaşımını kapatabilirsiniz.

Bir konuk SharePoint paylaşımını kapatmak için

1. Yönetim merkezinde SharePoint İlkeler'in **altında** Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
2. Dış **paylaşım'ın** altında, SharePoint için Yalnızca **kuruluşta yer alan kişiler'e sürükleyin**.
3. **Kaydet**'i seçin.

    ![Kuruluş SharePoint olarak ayarlanmış paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-tenant-sharing-off.png)


Sitede konuk paylaşımını kapatmak için
1. Yönetim merkezinde SharePoint altında Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. Yapılandırmak istediğiniz siteyi seçin.
3. İlkeler **sekmesinde** , Dış **paylaşım'ın altında Düzenle'yi** **seçin**.
4. Dış **paylaşım'ın** altında Yalnızca **kuruluşta olan kişiler'i seçin ve** sonra da Kaydet'i **seçin**.

    ![Yalnızca SharePoint olarak ayarlanmış site düzeyinde paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings-off.png)

Kullanıcıya sol üst bilgi sekmesinden kullanıcıya OneDrive ve Dış paylaşımı yönet'i seçerek, tek bir Microsoft 365 yönetim merkezi paylaşımı **OneDrive** kapatabilirsiniz.

Kuruluş dışındaki kullanıcılarla paylaşıma izin vermek istiyor, ancak herkesin kimlik doğrulamasından emin olmak için tüm kuruluş için veya tek bir site için *Herkes (anonim* paylaşım) bağlantılarını devre dışı edebilirsiniz.

Kuruluş *düzeyindeki herkes* bağlantılarını kapatmak için

1. Yönetim merkezinde SharePoint İlkeler'in **altında** Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
2. Dış **paylaşım'ın** altında Yer SharePoint yeni ve mevcut **konuklar'a sürükleyin**.
3. **Kaydet**'i seçin.

    ![Yeni ve SharePoint olarak ayarlanmış kuruluş düzeyi paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-guest-sharing-new-existing-guests.png)

Site için *herkes* bağlantılarını kapatmak için

1. Yönetim merkezinde SharePoint altında Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. Yapılandırmak istediğiniz siteyi seçin.
3. İlkeler **sekmesinde** , Dış **paylaşım'ın altında Düzenle'yi** **seçin**.
4. Dış **paylaşım'ın** altında Yeni **ve mevcut konuklar'ı** ve ardından Kaydet'i **seçin**.

    ![Yeni ve SharePoint olarak ayarlanmış site düzeyinde paylaşım ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings-new-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*Kuruluşlarda bağlantı paylaşan* kişiler

Varsayılan olarak, sitenin üyeleri dosyaları ve klasörleri, kuruluş bağlantınızı kullanan diğer kişiler *ile paylaşabilir* . PowerShell kullanarak *, kuruluş bağlantılarında yer alan* Kişiler'i devre dışı abilirsiniz:

```powershell
Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks Disabled
```

Örneğin:

```powershell
Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks Disabled
```

## <a name="create-sites-groups-and-teams"></a>Site, grup ve ekip oluşturma

Varsayılan olarak, kullanıcılar içerik paylaşabilecekleri (paylaşım ayarlarınıza bağlı olarak) yeni siteler, gruplar ve ekipler oluşturabilir. Kimlerin site, grup ve ekip oluştura kişilerini kısıtlayan bir sınırlama oluşturabilirsiniz. Aşağıdaki başvurulara bakın:

- [Web sitesinde site SharePoint](/sharepoint/manage-site-creation)
- [Gruplarda kimlerin oluştur Microsoft 365 yönetme](./manage-creation-of-groups.md)

> [!NOTE]
> Grup oluşturulmasını kısıtlamak, ekip oluşturma kısıtlamalarını kısıtlar.

## <a name="email"></a>E-posta

Şifreleme kullanarak e-postaların istenmeyen paylaşımını önebilirsiniz. Bu, e-postaların yetkisiz kullanıcılarla ilet ileriye veya başka bir şekilde paylaşılmasını önler. E-posta şifreleme, duyarlılık etiketleri kullanılarak etkinleştirilebilir. Ayrıntılar [için bkz. Duyarlılık etiketlerini şifreleme kullanarak içeriğe erişimi](../compliance/encryption-sensitivity-labels.md) kısıtlama.

## <a name="download-or-file-copy"></a>İndir veya dosya kopyası

Aynı dosya ve klasörlerde erişim iznine sahip Microsoft 365 dosyaları indirebilir ve dış medyaya kopyaladık. İstenmeyen dosya paylaşımı riskini azaltmak için, duyarlılık etiketlerini kullanarak içeriği şifreebilirsiniz.

## <a name="conditional-access"></a>Koşullu erişim

Azure Active Directory erişimi ağ konumu, cihaz durumu, oturum açma riski ve diğer faktörlere dayalı olarak kullanıcılarla paylaşımı sınırlandırma veya engelleme seçenekleri sağlar. Koşullu [Erişim nedir?](/azure/active-directory/conditional-access/overview)

SharePoint yönetsiz cihazlar ve ağ konumu için Azure AD koşullu erişimiyle doğrudan tümleştirme sağlar. Ayrıntılar için aşağıdaki başvurulara bakın:

- [Yönetilmeyen cihazlardan erişimi denetleme](/sharepoint/control-access-from-unmanaged-devices)
- [Ağ konumu temel SharePoint veriye OneDrive ve verilere erişimi denetleme](/sharepoint/control-access-based-on-network-location)

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 konuk paylaşımı ayarları başvurusu](microsoft-365-guest-settings.md)
