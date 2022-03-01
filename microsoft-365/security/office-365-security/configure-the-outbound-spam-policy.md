---
title: Giden istenmeyen posta filtrelemeyi yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) giden istenmeyen posta ilkelerini görüntülemeyi, Exchange Online Protection ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7f635eb17d458ca707f7a18d3eb1f7fe655bd2b9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033369"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>EOP'de giden istenmeyen posta filtrelemeyi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu olan Exchange Online kuruluşlarında, EOP aracılığıyla gönderilen giden e-posta iletileri otomatik olarak istenmeyen posta ve olağan dışı gönderme etkinliği için denetlenir.

Normalde, kuruluşta yer alan bir kullanıcıdan giden istenmeyen posta güvenliği ihlal edilmiş bir hesabı gösterir. Şüpheli giden iletiler istenmeyen posta olarak (istenmeyen posta güven düzeyine veya SCL'ye bakılmaksızın) olarak işaretlenir ve hizmetin itibarını korumaya yardımcı olmak için (başka bir ifadeyle, Microsoft 365 kaynak [e-posta](high-risk-delivery-pool-for-outbound-messages.md) sunucularını IP engelleme listelerinden uzak tutabilirsiniz) yüksek riskli teslim havuzu üzerinden yönlendirilen iletiler. Yöneticilere, uyarı ilkeleri aracılığıyla şüpheli giden e-posta etkinliği ve engellenen kullanıcılar hakkında otomatik [olarak bilgi gönderilir](../../compliance/alert-policies.md).

EOP, giden istenmeyen posta ilkelerini, kuruluşta istenmeyen postalara karşı genel savunmanın bir parçası olarak kullanır. Daha fazla bilgi için bkz. [İstenmeyen posta koruması](anti-spam-protection.md).

Yöneticiler varsayılan giden istenmeyen posta ilkesi  görüntüleyemez, düzenleyebilir ve yapılandırabilirsiniz (ancak silemezler). Daha ayrıntılı bilgi için, ayrıca, organizasyonu belirli kullanıcılara, gruplara veya etki alanlarına uygulanacak özel giden istenmeyen posta ilkeleri oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliğe sahiptir, ancak özel ilkelerinizin önceliğini (çalışma sırası) değiştirebilirsiniz.

Microsoft 365 Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 için PowerShell'de; Exchange Online için bağımsız EOP PowerShell'de giden istenmeyen posta ilkelerini yapılandırabilirsiniz. e-posta Exchange Online kuruluşlar).

EOP'de giden istenmeyen posta ilkesinde temel öğeler:

- **Giden istenmeyen posta filtresi ilkesi**: Giden istenmeyen posta filtreleme kararlarını ve bildirim seçeneklerinin eylemlerini belirtir.
- **Giden istenmeyen posta filtresi kuralı**: Giden istenmeyen posta filtresi ilkesi için önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Bu iki öğe arasındaki fark, portalda giden istenmeyen posta İlkelerini yönetirken belirgin Microsoft 365 Defender değildir:

- İlke  oluştururken, aslında giden istenmeyen posta filtresi kuralı ve ilişkili giden istenmeyen posta filtresi ilkesi aynı anda her ikisi için de aynı adı kullanır.
- Bir ilkeyi değiştirdikten sonra ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri giden istenmeyen posta filtresi kuralını değiştirir. Diğer tüm ayarlar ilişkili giden istenmeyen posta filtresi ilkesine değişiklik sağlar.
- Bir ilkeyi kaldıran, giden istenmeyen posta filtresi kuralı ve ilişkili giden istenmeyen posta filtresi ilkesi kaldırılır.

PowerShell Exchange Online tek başına EOP PowerShell'de, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin devam Exchange Online giden istenmeyen posta ilkelerini yapılandırmak için PowerShell veya tek başına [EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) kullanma bölümüne bakın.

Her kuruluşun, şu özelliklere sahip Varsayılan adlı yerleşik bir giden istenmeyen posta ilkesi vardır:

- İlkeyle ilişkilendirilmiş giden istenmeyen posta filtresi kuralı (alıcı filtreleri) yok olsa bile, ilke kuruluşta tüm alıcılara uygulanır.
- İlke, değiştiriy **olmadığınız** en düşük özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Kendi oluştur ilkeleriniz her zaman Varsayılan adlı ilkeden daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **değeri IsDefault** özelliğine `True`sahip) ve varsayılan ilkeyi silemezsiniz.

Giden istenmeyen posta filtrelemenin etkisini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha sıkı ayarlarla özel giden istenmeyen posta ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan İstenmeyen posta **önleme ayarları sayfasına gitmek** için , kullanın <https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Giden istenmeyen posta ilkeleri eklemek, değiştirmek ve silmek için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olun**.
  - Giden istenmeyen posta ilkelerine salt okunur erişim için, Genel Okuyucu veya Güvenlik **Okuyucu** rol **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Giden istenmeyen posta ilkeleri için önerilen ayarlarımız için bkz. [EOP giden istenmeyen posta filtresi ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- E-posta gönderme sınırı adlı varsayılan uyarı ilkeleri aşıldı **, Şüpheli** e-posta gönderme modelleri algılandı  ve Kullanıcı e-posta gönderme kısıtlaması zaten **TenantAdmins** (**Genel** yöneticiler) grubunun üyelerine olağandışı giden e-posta etkinliği ve giden istenmeyen posta nedeniyle engellenen kullanıcılar hakkında e-posta bildirimleri gönderiyor.[](../../compliance/alert-policies.md) Daha fazla bilgi için [bkz. Kısıtlanmış kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Giden istenmeyen posta ilkelerde bildirim seçenekleri yerine bu uyarı ilkelerini öneririz.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Giden Microsoft 365 Defender ilkeleri oluşturmak için posta portalına kullanma

Microsoft 365 Defender portalında özel bir giden istenmeyen posta ilkesi oluşturmak, istenmeyen posta filtresi kuralını ve ilişkili istenmeyen posta filtresi ilkesi aynı anda her ikisi için de aynı adı kullanarak oluşturur.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ayarları sayfasına gitmek** için , kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri sayfasında** Simge oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **İlke** oluşturun ve **ardından açılan listeden** Giden'i seçin.

3. İlke sihirbazı açılır. **İlkenizi adla sayfasında** şu ayarları yapılandırabilirsiniz:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Görüntülenen **Kullanıcılar, gruplar ve etki** alanları sayfasında, ilkenin geçerli olduğu iç alıcıları (alıcı koşulları) bulun:
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya kuruluşta posta kişileri.
   - **Gruplar**: Belirtilen dağıtım grupları, posta etkin güvenlik grupları veya Microsoft 365 Grupları.
   - **Etki** alanları: Belirtilen kabul edilen etki [alanlarındaki tüm](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşulda birden çok değer IÇIN VEYA mantığını kullanın (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar, AND mantığını (örneğin, _\<recipient1\>_ ve ) kullanır _\<member of group 1\>_.

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar (geçerli özel durumlar) eklemek için, bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Açılan **Koruma ayarları** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **İleti sınırları**: Bu bölümdeki ayarlar, posta kutularından gelen giden e-posta **Exchange Online** yapılandırabilirsiniz:
     - **Dış ileti sınırı ayarlama**: Bir saat içinde en fazla dış alıcı sayısı.
     - **Bir iç ileti sınırı ayarlama**: Bir saat içinde iç alıcı sayısı üst sınırı.
     - **Günlük ileti sınırı ayarlama**: Günde en fazla toplam alıcı sayısı.

     Geçerli bir değer 0 - 10000 olur. Varsayılan değer 0'dır; yani hizmet varsayılanları kullanılır. Daha fazla bilgi için bkz. [Gönderme sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Kutuya bir değer girin veya kutudeki artırma/azaltma oklarını kullanın.

   - **İleti sınırına ulaşan kullanıcılar için** kısıtlama: Koruma ayarları bölümündeki sınırlardan herhangi biri aşılırken açılan listeden bir eylem seçin.

     Tüm eylemler için, Kullanıcı tarafından e-posta uyarısı  gönderme ilkesinde belirtilen alıcılar (ve artık yedekli olan Bu sayfada daha  sonra giden istenmeyen posta gönderme ayarı nedeniyle engellenmişse bu kullanıcıları ve grupları bilgilendirin) e-posta bildirimleri alır.

     - **Kullanıcının şu güne kadar posta göndermesi kısıtlama**: Bu varsayılan değerdir. E-posta bildirimleri gönderilir ve kullanıcı UTC saatlerine göre sonraki güne kadar başka ileti gönderamaz. Yöneticinin bu bloğu geçersiz k bunun bir yolu yoktur.
       - Kullanıcı adlı uyarı ilkesi **, yöneticilere** e-posta gönderilmesini kısıtlar ( \> e-posta yoluyla ve Olaylar sayfasında& Uyarıları görüntüle **sayfasında**).
       - İlkede **, Gönderenin** giden istenmeyen posta göndermesi nedeniyle engellenmişse bunu belirli bir kişi olarak bildir ayarında belirtilen tüm alıcılara da bildirim gönderilir.
       - Kullanıcı, UTC saatlerine göre sonraki güne kadar ileti gönderamaz. Yöneticinin bu bloğu geçersiz k bunun bir yolu yoktur.
     - Kullanıcının posta göndermesi  için **kısıtlama:** E-posta bildirimleri gönderilir,  <https://security.microsoft.com/restrictedusers> kullanıcı Microsoft 365 Defender portalında Kısıtlanmış kullanıcılar'a eklenir ve kullanıcı bir yönetici tarafından Kısıtlanmış kullanıcılar'dan kaldırılana kadar e-posta gönderebilirsiniz. Yönetici tarafından listeden kullanıcı kaldırılmıştır, kullanıcı o gün için yeniden kısıtlanmamıştır. Yönergeler için bkz [. İstenmeyen e-posta gönderen bir kullanıcının Kısıtlanmış Kullanıcılar portaldan kaldırılması](removing-user-from-restricted-users-portal-after-spam.md).
     - **Eylem yok, yalnızca uyarı**: E-posta bildirimleri gönderilir.

   - **Yönlendirme kuralları**: Posta kutularını dış gönderenlere göndererek otomatik e-posta iletmeyi **Exchange Online için** bu bölümdeki ayarları kullanın. Daha fazla bilgi için bkz[. Dış posta iletisinde otomatik dış e-Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Otomatik iletme devre dışı bırakılacaksa, dış gönderenler iletmenin olduğu bir posta kutusuna e-posta gönderiyorsa, alıcı bir teslim edil raporundan (NDR veya geri dönen ileti olarak da bilinir) alır. İleti bir iç gönderen tarafından gönderilir ve iletme yöntemi  posta kutusu [iletme (](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding)_SMTP_ iletme olarak da bilinir), iç gönderen NDR'yi alır. Yönlendirme bir gelen kutusu kuralı nedeniyle ortaya çıktı ise, iç gönderenden NDR alınmz.

     Otomatik iletme kuralları açılan listesinde **aşağıdaki eylemlerden** birini seçin:

     - **Otomatik - Sistem tarafından denetlenen**: Giden istenmeyen posta filtrelemenin, otomatik dış e-posta iletmeyi denetlemeye olanak sağlar. Bu, varsayılan değerdir.
     - **Açık**: Otomatik dış e-posta iletme ilke tarafından devre dışı bırakılamaz.
     - **Kapalı**: Tüm otomatik dış e-posta iletme, ilke tarafından devre dışı bırakılır.

   - **Bildirimler**: Şüpheli giden e-posta iletilerinin kopyalarını ve bildirimlerini alacak ek alıcıları yapılandırmak için bölümdeki ayarları kullanın:

     - **Bu kullanıcılar ve gruplara bu** sınırları aşan şüpheli giden bağlantıların bir kopyasını gönderin: Bu ayar, belirtilen alıcıları şüpheli giden iletilerin Gizli alanına ekler.

       > [!NOTE]
       > Bu ayar yalnızca varsayılan giden istenmeyen posta ilkesinde çalışır. Sizin oluşturan özel giden istenmeyen posta ilkelerde işe yaramadı.

       Bu ayarı etkinleştirmek için onay kutusunu seçin. Görüntülenen kutuda, kutuya tıklayın, geçerli bir e-posta adresi girin ve ardından Enter tuşuna basın veya kutunun altında gösterilen tam değeri seçin.

       Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   - **Gönderenin giden istenmeyen posta göndermesi nedeniyle engellenmişse, bu kullanıcıları ve grupları bilgilendirin**

     > [!IMPORTANT]
     >
     > - Bu ayar, giden istenmeyen posta ilkelerinden kullanımdan çıkma sürecindedir.
     >
     > - Kullanıcı e-posta gönderme  kısıtlaması adlı varsayılan uyarı ilkesi, kullanıcılar Alıcı Sınırları bölümündeki sınırları aştıklarından dolayı engellenmiş **durumdayken TenantAdmins** (**Genel** yöneticiler) grubunun üyelerine zaten e-posta **bildirimleri** gönderir.[](../../compliance/alert-policies.md) **Yöneticileri ve diğer kullanıcıları bilgilendirmek için giden** istenmeyen posta ilkesinde bu ayar yerine uyarı ilkesi kullanmalarını kesinlikle öneririz. Yönergeler için bkz [. Kısıtlanmış kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Oluştur'a **tıklayın**.

7. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Giden Microsoft 365 Defender ilkelerini görüntülemek için posta portalına tıklayın

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ayarları sayfasına gitmek** için , kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, aşağıdaki değerlerden birini bulun:
   - Tür **değeri** Özel giden **istenmeyen posta ilkesidir**
   - Ad **değeri** **İstenmeyen posta önleme giden bağlantı ilkesidir (Varsayılan)**

   İstenmeyen posta önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Tür**

3. Adına tıklayarak giden bir istenmeyen posta ilkesi işaretlendiğinde, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Giden Microsoft 365 Defender ilkelerini değiştirmek için posta portalına kullanma

1. Microsoft 365 Defender portalında, İlkeler bölümündeki **&** \> İşbirliği **İlkeleri ve &** \>  \> için E-posta ve İşbirliği İlkeleri'ne & Tehdit ilkeleri **İstenmeyen** **postayla mücadele** bölümüne gidin.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden bir giden istenmeyen posta ilkesi seçin:
   - Tür sütunundaki değerin Özel giden istenmeyen posta ilkesi **olduğu****, oluşturduğunuz özel ilke**.
   - İstenmeyen posta giden **bağlantı ilkesi (Varsayılan) adlı varsayılan ilke**.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin Microsoft 365 Defender posta ilkelerini oluşturmak için [E-posta portalını kullanma](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) bölümüne bakın.

   Varsayılan giden istenmeyen posta ilkesi için, Uygulanan bölümü  kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandırılamaz.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak, ilke öncelik sırası ayarlamak veya son kullanıcı bildirimlerini yapılandırmak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Özel giden istenmeyen posta ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan giden istenmeyen posta ilkesi devre dışı bırakamaz.

1. Microsoft 365 Defender portalında, İlkeler bölümündeki **&** \> İşbirliği **İlkeleri ve &** \>  \> için E-posta ve İşbirliği İlkeleri'ne & Tehdit ilkeleri **İstenmeyen** **postayla mücadele** bölümüne gidin.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel giden istenmeyen posta ilkesi Tür değerine sahip bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Özel giden istenmeyen posta ilkelerinin önceliğini ayarlama

Varsayılan olarak, giden istenmeyen posta ilkelerine oluşturulduklarına dayalı bir öncelik verilir (daha yeni ilkeler, eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, giden istenmeyen posta ilkesi önceliğini ancak oluşturduktan sonra değiştirebilirsiniz. PowerShell'de, istenmeyen posta filtresi kuralı  oluşturmak (var olan kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- Giden istenmeyen posta ilkeleri görüntülenme sırasına göre işlenir (ilk ilkenin Öncelik değeri 0'dır). Varsayılan giden istenmeyen posta ilkesi En **düşük öncelik** değerine sahiptir ve bunu değiştiremezsiniz.

1. Microsoft 365 Defender portalında, İlkeler bölümündeki **&** \> İşbirliği **İlkeleri ve &** \>  \> için E-posta ve İşbirliği İlkeleri'ne & Tehdit ilkeleri **İstenmeyen** **postayla mücadele** bölümüne gidin.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel giden istenmeyen posta ilkesi Tür değerine sahip bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, geçerli öncelik değerine ve özel ilke  sayısına göre  Önceliği artır veya Önceliği azalt'a bakın:
   - Öncelik değeri **0** **olan giden istenmeyen** posta ilkesi yalnızca Öncelik azalt **seçeneğine** sahiptir.
   - En düşük Öncelik değerine (örneğin,  **3**) sahip giden istenmeyen posta ilkesi yalnızca Öncelik artır **seçeneğine** sahiptir.
   - Üç veya daha fazla giden istenmeyen posta ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliği  artır hem de Öncelik azalt **seçenekleri** kullanılabilir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Özel giden Microsoft 365 Defender ilkelerini kaldırmak için posta portalına tıklayın

Özel bir giden Microsoft 365 Defender kaldırmak için Posta Portalı'nın kullanımında, istenmeyen posta filtresi kuralı ve buna karşılık gelen istenmeyen posta filtresi ilkesi de silinir. Varsayılan giden istenmeyen posta ilkesi kaldıramayr.

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ayarları sayfasına gitmek** için , kullanın <https://security.microsoft.com/antispam>.

2.   **İstenmeyen posta önleme ilkeleri** sayfasında, adı tıklatarak listeden Özel giden istenmeyen posta ilkesi Tür değerine sahip bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

3. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Giden Exchange Online ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell kullanma

Daha önce açıklandığı gibi, giden istenmeyen posta ilkesi giden istenmeyen posta filtresi ilkesi ve giden istenmeyen posta filtresi kuralıdan oluşur.

Aynı Exchange Online tek başına EOP PowerShell'de, giden istenmeyen posta filtresi ilkeleriyle giden istenmeyen posta filtresi kuralları arasındaki fark görünür hale gelir. Giden istenmeyen posta filtresi ilkelerini **yönetmek için -HostedOutboundSpamFilterPolicy cmdlet'lerini kullanır ve -HostedOutboundSpamFilterRule cmdlet'lerini kullanarak giden istenmeyen posta filtresi kurallarını yönetirsiniz.\*** **\***

- PowerShell'de, önce giden istenmeyen posta filtresi ilkesi, ardından da kuralın geçerli olduğu ilkeyi tanımlayan giden istenmeyen posta filtresi kuralını oluşturun.
- PowerShell'de, giden istenmeyen posta filtresi ilkesi ve giden istenmeyen posta filtresi kuralı ayarlarını ayrı ayrı değiştirirsiniz.
- PowerShell'den giden istenmeyen posta filtresi ilkesi kaldırılmışsa, buna karşılık gelen giden istenmeyen posta filtresi kuralı otomatik olarak kaldırmaz ve bunun tersi de geçerlidir.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Giden istenmeyen posta ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de giden istenmeyen posta ilkesi oluşturmak iki adımlık bir işlemdir:

1. Giden istenmeyen posta filtresi ilkesi oluşturun.
2. Kuralın geçerli olduğu giden istenmeyen posta filtresi ilkesi'nin belirten giden istenmeyen posta filtresi kuralını oluşturun.

   **Notlar**:

   - Yeni bir giden istenmeyen posta filtresi kuralı oluşturabilir ve bu kurala var olan, ilişkilendirilmemiş bir giden istenmeyen posta filtresi ilkesi attaysanız. Giden istenmeyen posta filtresi kuralı birden çok giden istenmeyen posta filtresi ilkesiyle ilişkilendirilz.
   - İlkeyi oluşturmadan önce, PowerShell portalında yer alan ve Microsoft 365 Defender portalında olmayan yeni giden istenmeyen posta filtresi ilkelarında aşağıdaki ayarları yapılandırabilirsiniz:
     - Yeni ilkeyi devre dışı _olarak oluşturun (_ `$false` **New-HostedOutboundSpamFilterRule cmdlet'inde** Etkin).
     - **New-HostedOutboundSpamFilterRule** cmdlet'inde oluşturma sırasında ilkenin önceliğini _ayarlayın (__\<Number\>_ Öncelik).
   - PowerShell'de yeni bir giden istenmeyen posta filtresi ilkesi, siz giden istenmeyen posta filtresi kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>1. Adım: Giden istenmeyen posta filtresi ilkesi oluşturmak için PowerShell kullanma

Giden istenmeyen posta filtresi ilkesi oluşturmak için şu söz dizimi kullanın:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarları içeren Contoso Yöneticiler adında yeni bir giden istenmeyen posta filtresi ilkesi oluşturur:

- Alıcı oranı sınırları, varsayılan olarak daha küçük değerlerle sınırlıdır. Daha fazla bilgi için bkz[. Tüm Seçenekler Microsoft 365 gönderme](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Sınırlardan bire ulaştıktan sonra kullanıcının ileti göndermesi engel olur.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>2. Adım: Giden istenmeyen posta filtresi kuralı oluşturmak için PowerShell kullanma

Giden istenmeyen posta filtresi kuralı oluşturmak için şu söz dizimi kullanın:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, şu ayarları içeren Contoso Yöneticiler adında yeni bir giden istenmeyen posta filtresi kuralı oluşturur:

- Contoso Executives adlı giden istenmeyen posta filtresi ilkesi kuralla ilişkilendirildi.
- Kural, Contoso Executives Group adlı grubun üyeleri için geçerlidir.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini görüntülemek için PowerShell kullanma

Tüm giden istenmeyen posta filtresi ilkelerinin özet listesini geri dönmek için, şu komutu çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Belirli bir giden istenmeyen posta filtresi ilkesi hakkında ayrıntılı bilgi dönmek için, şu söz dizimi kullanın:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Yöneticiler adlı giden istenmeyen posta filtresi ilkesi için tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını görüntülemek için PowerShell kullanma

Var olan giden istenmeyen posta filtresi kurallarını görüntülemek için aşağıdaki söz dizimi kullanın:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Tüm giden istenmeyen posta filtresi kurallarının özet listesini geri dönmek için, şu komutu çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Belirli bir giden istenmeyen posta filtresi kuralı hakkında ayrıntılı bilgi almak için şu söz dizimi kullanın:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Contoso Yöneticiler adlı giden istenmeyen posta filtresi kuralı için tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de kötü amaçlı yazılım filtresi ilkesinde değişiklik yapmak için, 1. Adım: Bu makalenin önceki kısımlarında yer alan Giden istenmeyen posta filtresi ilkesi oluşturmak için [PowerShell](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) kullanma bölümünde açıklandığı gibi, aynı ayarlar kullanılabilir.

> [!NOTE]
> Giden istenmeyen posta filtresi ilkesi yeniden adlandırılamaz ( **Set-HostedOutboundSpamFilterPolicy** cmdlet'in _Name_ parametresi yoktur). Bir istenmeyen posta portalında giden istenmeyen posta Microsoft 365 Defender yeniden adlandırıyorken, yalnızca giden istenmeyen posta filtresi kuralını yeniden _adlandırıyor olursunuz_.

Giden istenmeyen posta filtresi ilkesi değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını değiştirmek için PowerShell kullanma

PowerShell'de giden istenmeyen posta filtresi kuralını değiştirirken kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza  olanak sağlayan Enabled parametresidir. Var olan giden istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Bunun dışında, PowerShell'de giden istenmeyen posta filtresi kuralını değiştirerek ek ayarlar kullanılamaz. 2. Adım: Bu makalenin önceki kısımlarında yer alan Giden istenmeyen posta filtresi kuralı oluşturmak için [PowerShell](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) kullanma bölümünde açıklandığı gibi, aynı ayarlara da sahip oluruz.

Giden istenmeyen posta filtresi kuralını değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de giden istenmeyen posta filtresi kuralını etkinleştirme veya devre dışı bırakma, tüm giden istenmeyen posta ilkesi (giden istenmeyen posta filtresi kuralı ve atanmış giden istenmeyen posta filtresi ilkesi) etkinleştirir veya devre dışı bırakarak. Varsayılan giden istenmeyen posta ilkesi (her zaman tüm alıcılara uygulanır) etkinleştir veya devre dışı bırakasınız.

PowerShell'de giden istenmeyen posta filtresi kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimi kullanın:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Bölümü adlı giden istenmeyen posta filtresi kuralı devre dışıdır.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Enable-HostedOutboundSpamFilterRule ve](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de giden istenmeyen posta filtresi kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı irken önceliğini ayarlamak için, onun yerine **New-HostedOutboundSpamFilterRule** cmdlet'inde Öncelik parametresini kullanın.
- Giden varsayılan istenmeyen posta filtresi ilkesine karşılık gelen bir istenmeyen posta filtresi kuralı yoktur ve her zaman En Düşük değiştirilmez öncelik **değerine sahiptir**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini kaldırmak için PowerShell kullanma

PowerShell kullanarak giden istenmeyen posta filtresi ilkesi kaldırırken, buna karşılık gelen giden istenmeyen posta filtresi kuralı kaldırılamaz.

PowerShell'de giden istenmeyen posta filtresi ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Bölümü adlı giden istenmeyen posta filtresi ilkesi kaldır).

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını kaldırmak için PowerShell kullanma

PowerShell kullanarak giden istenmeyen posta filtresi kuralını kaldırırken, buna karşılık gelen giden istenmeyen posta filtresi ilkesi kaldırılamaz.

PowerShell'de giden istenmeyen posta filtresi kuralını kaldırmak için şu söz dizimi kullanın:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Bölümü adlı giden istenmeyen posta filtresi kuralını kaldırır.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Daha fazla bilgi için

[Engellenen kullanıcıları Kısıtlanmış Kullanıcılar portaldan kaldırma](removing-user-from-restricted-users-portal-after-spam.md)

[Giden iletiler için yüksek riskli teslim havuzu](high-risk-delivery-pool-for-outbound-messages.md)

[İstenmeyen posta koruması hakkında SSS](anti-spam-protection-faq.yml)

[Otomatik iletili iletiler raporu](mfi-auto-forwarded-messages-report.md)
