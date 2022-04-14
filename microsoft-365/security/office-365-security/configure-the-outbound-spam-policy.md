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
description: Yöneticiler, Exchange Online Protection (EOP) içinde giden istenmeyen posta ilkelerini görüntülemeyi, oluşturmayı, değiştirmeyi ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9ab8585a0671f9c62ec2015d91486539c84004db
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847475"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>EOP'de giden istenmeyen posta filtrelemeyi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, EOP aracılığıyla gönderilen giden e-posta iletileri istenmeyen posta ve olağan dışı gönderme etkinliği için otomatik olarak denetlenir.

Kuruluşunuzdaki bir kullanıcıdan gelen istenmeyen postalar genellikle güvenliği aşılmış bir hesabı gösterir. Şüpheli giden iletiler istenmeyen posta olarak işaretlenir (istenmeyen posta güvenilirlik düzeyine veya SCL'ye bakılmaksızın) ve hizmetin itibarını korumaya yardımcı olmak için [yüksek riskli teslim havuzu](high-risk-delivery-pool-for-outbound-messages.md) üzerinden yönlendirilir (yani, kaynak e-posta sunucularını IP blok listelerinin dışında Microsoft 365). Yöneticilere şüpheli giden e-posta etkinliği otomatik olarak bildirilir ve [uyarı ilkeleri](../../compliance/alert-policies.md) aracılığıyla kullanıcılar engellenir.

EOP, kuruluşunuzun istenmeyen postalara karşı genel savunmasının bir parçası olarak giden istenmeyen posta ilkelerini kullanır. Daha fazla bilgi için bkz [. İstenmeyen posta önleme koruması](anti-spam-protection.md).

Yöneticiler varsayılan giden istenmeyen posta ilkesini görüntüleyebilir, düzenleyebilir ve yapılandırabilir (ancak silemez). Daha fazla ayrıntı düzeyi için, kuruluşunuzdaki belirli kullanıcılar, gruplar veya etki alanları için geçerli olan özel giden istenmeyen posta ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliklidir, ancak özel ilkelerinizin önceliğini (çalıştırma sırasını) değiştirebilirsiniz.

Giden istenmeyen posta ilkelerini Microsoft 365 Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell Exchange Online de yapılandırabilirsiniz; için tek başına EOP PowerShell Exchange Online posta kutusu olmayan kuruluşlar).

EOP'de giden istenmeyen posta ilkesinin temel öğeleri şunlardır:

- **Giden istenmeyen posta filtresi ilkesi: Giden istenmeyen posta** filtreleme kararlarının eylemlerini ve bildirim seçeneklerini belirtir.
- **Giden istenmeyen posta filtresi kuralı: Giden istenmeyen posta filtresi** ilkesi için öncelik ve gönderen filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında giden istenmeyen posta ilkelerini yönettiğinizde bu iki öğe arasındaki fark belirgin değildir:

- İlke oluşturduğunuzda, her ikisi için de aynı adı kullanarak bir giden istenmeyen posta filtresi kuralı ve ilişkili giden istenmeyen posta filtresi ilkesini aynı anda oluşturursunuz.
- bir ilkeyi değiştirdiğinizde ad, öncelik, etkin veya devre dışı ayarları ve gönderen filtreleri giden istenmeyen posta filtresi kuralını değiştirir. Diğer tüm ayarlar ilişkili giden istenmeyen posta filtresi ilkesini değiştirir.
- bir ilkeyi kaldırdığınızda, giden istenmeyen posta filtresi kuralı ve ilişkili giden istenmeyen posta filtresi ilkesi kaldırılır.

Exchange Online PowerShell veya tek başına EOP PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu makalenin devamında [yer alan Giden istenmeyen posta ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell Exchange Online kullanma](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) bölümüne bakın.

Her kuruluşun Şu özelliklere sahip Varsayılan adlı yerleşik bir giden istenmeyen posta ilkesi vardır:

- İlkeyle ilişkilendirilmiş giden istenmeyen posta filtresi kuralı (gönderen filtreleri) olmasa bile, ilke kuruluştaki tüm gönderenlere uygulanır.
- İlke, değiştiremezseniz **en düşük** özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Oluşturduğunuz tüm özel ilkeler her zaman Varsayılan adlı ilkeden daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **IsDefault** özelliği değerine `True`sahiptir) ve varsayılan ilkeyi silemezsiniz.

Giden istenmeyen posta filtrelemenin verimliliğini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha katı ayarlara sahip özel giden istenmeyen posta ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **İstenmeyen posta önleme ayarları** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Giden istenmeyen posta ilkelerini eklemek, değiştirmek ve silmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Giden istenmeyen posta ilkelerine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Giden istenmeyen posta ilkeleri için önerilen ayarlarımız için bkz. [EOP giden istenmeyen posta filtresi ilke ayarları](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- **E-posta gönderme sınırı aşıldı**, **Şüpheli e-posta gönderme desenleri algılandı** ve **Kullanıcının e-posta göndermesi kısıtlandı** adlı varsayılan [uyarı ilkeleri](../../compliance/alert-policies.md), olağan dışı giden e-posta etkinliği ve giden istenmeyen posta nedeniyle engellenen kullanıcılar hakkında **TenantAdmins** (**Genel yöneticiler**) grubunun üyelerine zaten e-posta bildirimleri gönderir. Daha fazla bilgi için bkz [. Kısıtlı kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Giden istenmeyen posta ilkelerindeki bildirim seçenekleri yerine bu uyarı ilkelerini kullanmanızı öneririz.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Giden istenmeyen posta ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel bir giden istenmeyen posta ilkesi oluşturmak, her ikisi için de aynı adı kullanarak istenmeyen posta filtresi kuralını ve ilişkili istenmeyen posta filtresi ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ayarları** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **İlke oluşturun** ve açılan listeden **Giden'i** seçin.

3. İlke sihirbazı açılır. **İlkenizi adlandırın sayfasında** şu ayarları yapılandırın:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. Görüntülenen **Kullanıcılar, gruplar ve etki alanları sayfasında,** ilkenin geçerli olduğu iç gönderenleri tanımlayın (alıcı koşulları):
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya posta kişileri.
   - **Gruplar**:
     - Belirtilen dağıtım gruplarının veya posta özellikli güvenlik gruplarının üyeleri.
     - Belirtilen Microsoft 365 Grupları.
   - **Etki alanları**: Kuruluşunuzda belirtilen [kabul edilen etki alanlarındaki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) tüm gönderenler.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşuldaki birden çok değer OR mantığını kullanır (örneğin, _\<sender1\>_ veya _\<sender2\>_). Farklı koşullar AND mantığını kullanır (örneğin, _\<sender1\>_ ve _\<member of group 1\>_).

   - **Bu kullanıcıları, grupları ve etki alanlarını dışlayın**: İlkenin geçerli olduğu iç gönderenler için özel durumlar eklemek için (alıcı özel durumları), bu seçeneği belirleyin ve özel durumları yapılandırın. Ayarlar ve davranış, koşullara tam olarak benzer.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Açılan **Koruma ayarları** sayfasında aşağıdaki ayarları yapılandırın:
   - **İleti sınırları**: Bu bölümdeki ayarlar, **Exchange Online** posta kutularından giden e-posta iletilerinin sınırlarını yapılandırmaktadır:
     - **Dış ileti sınırı ayarlayın**: Saat başına en fazla dış alıcı sayısı.
     - **İç ileti sınırı ayarlayın**: Saat başına iç alıcı sayısı üst sınırı.
     - **Günlük ileti sınırı ayarlayın**: Günlük toplam alıcı sayısı üst sınırı.

     Geçerli bir değer 0 ile 10000'dir. Varsayılan değer 0'dır, yani hizmet varsayılanları kullanılır. Daha fazla bilgi için bkz [. Sınır gönderme](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Kutuya bir değer girin veya kutudaki artır/azalt oklarını kullanın.

   - **İleti sınırına ulaşan kullanıcılara kısıtlama:** **Koruma ayarları** bölümündeki sınırlardan herhangi biri aşıldığında açılan listeden bir eylem seçin.

     Tüm eylemler için, Kullanıcı'da belirtilen gönderenlerin **e-posta uyarısı göndermesi kısıtlandı** (ve bu sayfanın ilerleyen bölümlerinde giden **istenmeyen posta gönderme nedeniyle bir gönderen engellendiyse bu kullanıcılara ve gruplara artık bildir** ayarında) e-posta bildirimleri alır.

     - **Kullanıcının posta göndermesini şu güne kadar kısıtlayın**: Bu varsayılan değerdir. E-posta bildirimleri gönderilir ve kullanıcı UTC saati temelinde sonraki güne kadar başka ileti gönderemez. Yöneticinin bu bloğu geçersiz kılmasının hiçbir yolu yoktur.
       - Kullanıcı adlı uyarı ilkesi **, e-posta göndermesi kısıtlanmış** olarak yöneticilere bildirim gönderir (e-posta yoluyla ve **Olaylar & uyarıları** \> **görüntüleme** sayfasında).
       - İlkedeki **Giden istenmeyen posta gönderme nedeniyle bir gönderenin engellenmesi durumunda belirli kişilere bildir** ayarında belirtilen tüm alıcılar da bildirilir.
       - Kullanıcı UTC saatine göre sonraki güne kadar başka ileti gönderemeyecektir. Yöneticinin bu bloğu geçersiz kılmasının hiçbir yolu yoktur.
     - **Kullanıcının posta göndermesini kısıtlama**: E-posta bildirimleri gönderilir, kullanıcı Microsoft 365 Defender portalında **Kısıtlı kullanıcılar'a** <https://security.microsoft.com/restrictedusers> eklenir ve kullanıcı, bir yönetici tarafından **Kısıtlanmış kullanıcılardan kaldırılana** kadar e-posta gönderemez. Yönetici kullanıcıyı listeden kaldırdıktan sonra, o gün için kullanıcı yeniden kısıtlanmaz. Yönergeler için bkz. [İstenmeyen posta gönderdikten sonra Kısıtlı Kullanıcılar portalından kullanıcı kaldırma](removing-user-from-restricted-users-portal-after-spam.md).
     - **Eylem yok, yalnızca uyarı**: E-posta bildirimleri gönderilir.

   - **İletme kuralları**: **Posta kutularını** dış gönderenlere Exchange Online otomatik e-posta iletmeyi denetlemek için bu bölümdeki ayarları kullanın. Daha fazla bilgi için bkz. [Microsoft 365'de otomatik dış e-posta iletmeyi denetleme](external-email-forwarding.md).

     > [!NOTE]
     > Otomatik iletme devre dışı bırakıldığında, dış gönderenler iletim uygulanmış bir posta kutusuna e-posta gönderirse, alıcı teslim edilemez bir rapor (NDR veya geri dönen ileti olarak da bilinir) alır. İleti bir iç gönderen tarafından gönderiliyorsa **ve** iletme yöntemi [posta kutusu iletme](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) ise ( _SMTP iletme_ olarak da bilinir), iç gönderen NDR'yi alır. İletme bir gelen kutusu kuralı nedeniyle gerçekleştiyse, iç gönderen NDR almaz.

     **Otomatik iletme kuralları** açılan listesinden aşağıdaki eylemlerden birini seçin:

     - **Otomatik - Sistem denetimi: Otomatik dış e-posta** iletmeyi denetlemek için giden istenmeyen posta filtrelemesine izin verir. Bu, varsayılan değerdir.
     - **Açık**: Otomatik dış e-posta iletme ilke tarafından devre dışı bırakılmaz.
     - **Kapalı**: İlke tarafından tüm otomatik dış e-posta iletme devre dışı bırakılır.

   - **Bildirimler**: Şüpheli giden e-posta iletilerinin kopyalarını ve bildirimlerini alması gereken ek alıcıları yapılandırmak için bölümdeki ayarları kullanın:

     - **Bu kullanıcılara ve gruplara bu sınırları aşan şüpheli gidenlerin bir kopyasını gönderin**: Bu ayar, belirtilen alıcıları şüpheli giden iletilerin Gizli alanına ekler.

       > [!NOTE]
       > Bu ayar yalnızca varsayılan giden istenmeyen posta ilkesinde çalışır. Oluşturduğunuz özel giden istenmeyen posta ilkelerinde çalışmaz.

       Bu ayarı etkinleştirmek için onay kutusunu seçin. Görüntülenen kutuda, kutuya tıklayın, geçerli bir e-posta adresi girin ve enter tuşuna basın veya kutunun altında görüntülenen değerin tamamını seçin.

       Bu adımı gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   - **Bir gönderen giden istenmeyen posta gönderdiği için engellendiyse bu kullanıcıları ve grupları bilgilendirin**

     > [!IMPORTANT]
     >
     > - Bu ayar, giden istenmeyen posta ilkelerinden kullanım dışı bırakılıyor.
     >
     > - **Kullanıcı'nın e-posta göndermesi kısıtlandı** adlı varsayılan [uyarı ilkesi](../../compliance/alert-policies.md), **Kullanıcılar Alıcı Sınırları** bölümündeki sınırları aştığı için engellendiğinde **TenantAdmins** (**Genel yöneticiler**) grubunun üyelerine zaten e-posta bildirimleri gönderir. **Yöneticileri ve diğer kullanıcıları bilgilendirmek için giden istenmeyen posta ilkesinde bu ayar yerine uyarı ilkesini kullanmanızı kesinlikle öneririz**. Yönergeler için bkz [. Kısıtlı kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Oluştur'a** tıklayın.

7. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Giden istenmeyen posta ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ayarları** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında aşağıdaki değerlerden birini arayın:
   - **Tür** değeri **Özel giden istenmeyen posta ilkesidir**
   - **Ad** değeri **, istenmeyen postadan koruma giden ilkesidir (Varsayılan)**

   İstenmeyen posta önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Tür**

3. Bir giden istenmeyen posta ilkesini ada tıklayarak seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Giden istenmeyen posta ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. Microsoft 365 Defender portalında, İlkeler **bölümünde** **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden bir giden istenmeyen posta ilkesi seçin:
   - **Tür** sütunundaki değerin **Özel giden istenmeyen posta ilkesi** olduğu, oluşturduğunuz özel bir ilkedir.
   - **İstenmeyen posta önleme giden ilkesi (Varsayılan)** adlı varsayılan ilke.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için, bu [makaledeki Microsoft 365 Defender portalını kullanarak giden istenmeyen posta ilkeleri oluşturma](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) bölümüne bakın.

   Varsayılan giden istenmeyen posta ilkesi **için Uygulanan** bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandıramazsınız.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak, ilke öncelik sırasını ayarlamak veya son kullanıcı bildirimlerini yapılandırmak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Özel giden istenmeyen posta ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan giden istenmeyen posta ilkesini devre dışı bırakamazsınız.

1. Microsoft 365 Defender portalında, İlkeler **bölümünde** **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden Tür **değeri** **Özel giden istenmeyen posta ilkesi** olan bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Özel giden istenmeyen posta ilkelerinin önceliğini ayarlama

Varsayılan olarak, giden istenmeyen posta ilkelerine oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, giden istenmeyen posta ilkesinin önceliğini yalnızca oluşturduktan sonra değiştirebilirsiniz. PowerShell'de, istenmeyen posta filtresi kuralını oluştururken varsayılan önceliği geçersiz kılabilirsiniz (bu, mevcut kuralların önceliğini etkileyebilir).
- Giden istenmeyen posta ilkeleri, görüntülenme sırasına göre işlenir (ilk **ilkenin Öncelik** değeri 0'dır). Varsayılan giden istenmeyen posta ilkesi **En düşük** öncelik değerine sahiptir ve bunu değiştiremezsiniz.

1. Microsoft 365 Defender portalında, İlkeler **bölümünde** **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden **Özel giden istenmeyen posta ilkesi** **Tür değeriyle** bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve özel ilkelerin sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan giden istenmeyen posta ilkesi yalnızca **Önceliği azalt** seçeneğine sahiptir.
   - En düşük **Öncelik** değerine sahip giden istenmeyen posta ilkesi (örneğin, **3**) yalnızca **Önceliği artır** seçeneği kullanılabilir.
   - Üç veya daha fazla giden istenmeyen posta ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Özel giden istenmeyen posta ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

Özel bir giden istenmeyen posta ilkesini kaldırmak için Microsoft 365 Defender portalını kullandığınızda, istenmeyen posta filtresi kuralı ve ilgili istenmeyen posta filtresi ilkesi silinir. Varsayılan giden istenmeyen posta ilkesini kaldıramazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ayarları** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ada tıklayarak listeden Tür **değeri** **Özel giden istenmeyen posta ilkesi** olan bir ilke seçin. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

3. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Giden istenmeyen posta ilkelerini yapılandırmak için Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Daha önce açıklandığı gibi, giden istenmeyen posta ilkesi bir giden istenmeyen posta filtresi ilkesinden ve giden istenmeyen posta filtresi kuralından oluşur.

Exchange Online PowerShell veya tek başına EOP PowerShell'de, giden istenmeyen posta filtresi ilkeleriyle giden istenmeyen posta filtresi kuralları arasındaki fark belirgindir. Giden istenmeyen posta filtresi ilkelerini **-HostedOutboundSpamFilterPolicy cmdlet'lerini kullanarak\*** yönetirsiniz ve **-HostedOutboundSpamFilterRule cmdlet'lerini kullanarak\*** giden istenmeyen posta filtre kurallarını yönetirsiniz.

- PowerShell'de, önce giden istenmeyen posta filtresi ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan giden istenmeyen posta filtresi kuralını oluşturursunuz.
- PowerShell'de, giden istenmeyen posta filtresi ilkesindeki ayarları ve giden istenmeyen posta filtresi kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den giden istenmeyen posta filtresi ilkesini kaldırdığınızda, ilgili giden istenmeyen posta filtresi kuralı otomatik olarak kaldırılmaz ve tam tersi de geçerlidir.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Giden istenmeyen posta ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de giden istenmeyen posta ilkesi oluşturmak iki adımlı bir işlemdir:

1. Giden istenmeyen posta filtresi ilkesini oluşturun.
2. Kuralın geçerli olduğu giden istenmeyen posta filtresi ilkesini belirten giden istenmeyen posta filtresi kuralını oluşturun.

   **Notlar**:

   - Yeni bir giden istenmeyen posta filtresi kuralı oluşturabilir ve bu kurala var olan ve ilişkilendirilmemiş bir giden istenmeyen posta filtresi ilkesi atayabilirsiniz. Giden istenmeyen posta filtresi kuralı birden fazla giden istenmeyen posta filtresi ilkesiyle ilişkilendirilemiyor.
   - İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni giden istenmeyen posta filtresi ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:
     - Yeni ilkeyi devre dışı olarak oluşturun (**New-HostedOutboundSpamFilterRule** cmdlet'inde _etkindir_`$false`).
     - **New-HostedOutboundSpamFilterRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ ayarlayın (Öncelik _\<Number\>_).
   - PowerShell'de oluşturduğunuz yeni bir giden istenmeyen posta filtresi ilkesi, ilkeyi giden istenmeyen posta filtresi kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>1. Adım: Giden istenmeyen posta filtresi ilkesi oluşturmak için PowerShell kullanma

Giden istenmeyen posta filtresi ilkesi oluşturmak için şu sözdizimini kullanın:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarlarla Contoso Executives adlı yeni bir giden istenmeyen posta filtresi ilkesi oluşturur:

- Alıcı oranı sınırları, varsayılan değerlerden daha küçük değerlerle sınırlıdır. Daha fazla bilgi için bkz[. Microsoft 365 seçenekleri arasında sınır gönderme](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Sınırlardan birine ulaşıldıktan sonra kullanıcının ileti göndermesi engellenir.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>2. Adım: Giden istenmeyen posta filtresi kuralı oluşturmak için PowerShell kullanma

Giden istenmeyen posta filtresi kuralı oluşturmak için şu sözdizimini kullanın:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Sender filters> [<Sender filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, şu ayarlarla Contoso Executives adlı yeni bir giden istenmeyen posta filtresi kuralı oluşturur:

- Contoso Executives adlı giden istenmeyen posta filtresi ilkesi kuralla ilişkilendirilir.
- Kural, Contoso Executives Group adlı grubun üyeleri için geçerlidir.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini görüntülemek için PowerShell kullanma

Tüm giden istenmeyen posta filtresi ilkelerinin özet listesini döndürmek için şu komutu çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Belirli bir giden istenmeyen posta filtresi ilkesi hakkında ayrıntılı bilgi döndürmek için şu söz dizimini kullanın:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Yöneticiler adlı giden istenmeyen posta filtresi ilkesinin tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını görüntülemek için PowerShell kullanma

Mevcut giden istenmeyen posta filtresi kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Tüm giden istenmeyen posta filtresi kurallarının özet listesini döndürmek için şu komutu çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Belirli bir giden istenmeyen posta filtresi kuralı hakkında ayrıntılı bilgi döndürmek için şu sözdizimini kullanın:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Bu örnek, Contoso Executives adlı giden istenmeyen posta filtresi kuralının tüm özellik değerlerini döndürür.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini değiştirmek için PowerShell kullanma

PowerShell'de bir kötü amaçlı yazılım filtresi ilkesini değiştirdiğinizde, ilkeyi [1. Adım: PowerShell kullanarak](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) bu makalenin önceki bölümlerinde yer alan giden istenmeyen posta filtresi ilkesi oluşturma bölümünde açıklandığı gibi aynı ayarlar kullanılabilir.

> [!NOTE]
> Giden istenmeyen posta filtresi ilkesini yeniden adlandıramazsınız ( **Set-HostedOutboundSpamFilterPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında bir giden istenmeyen posta ilkesini yeniden adlandırdığınızda, yalnızca giden istenmeyen posta filtresi _kuralını_ yeniden adlandırırsınız.

Giden istenmeyen posta filtresi ilkesini değiştirmek için şu sözdizimini kullanın:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını değiştirmek için PowerShell kullanma

PowerShell'de giden istenmeyen posta filtresi kuralını değiştirdiğinizde kullanılamayabilecek tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Enabled_ parametresidir. Mevcut giden istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, PowerShell'de giden istenmeyen posta filtresi kuralını değiştirdiğinizde ek ayar kullanılamaz. Bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak giden istenmeyen posta filtresi kuralı oluşturma](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

Giden istenmeyen posta filtresi kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de giden istenmeyen posta filtresi kuralının etkinleştirilmesi veya devre dışı bırakılması, giden istenmeyen posta ilkesinin tamamını (giden istenmeyen posta filtresi kuralı ve atanan giden istenmeyen posta filtresi ilkesi) etkinleştirir veya devre dışı bırakır. Varsayılan giden istenmeyen posta ilkesini etkinleştiremez veya devre dışı bırakamazsınız (her zaman tüm gönderenlere uygulanır).

PowerShell'de giden istenmeyen posta filtresi kuralını etkinleştirmek veya devre dışı bırakmak için şu sözdizimini kullanın:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı giden istenmeyen posta filtresi kuralını devre dışı bırakır.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) ve [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de giden istenmeyen posta filtresi kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-HostedOutboundSpamFilterRule** cmdlet'indeki _Priority_ parametresini kullanın.
- Giden varsayılan istenmeyen posta filtresi ilkesinin karşılık gelen bir istenmeyen posta filtresi kuralı yoktur ve her zaman **değiştirilemez öncelik değeri En Düşük'e** sahiptir.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Giden istenmeyen posta filtresi ilkelerini kaldırmak için PowerShell kullanma

Giden istenmeyen posta filtresi ilkesini kaldırmak için PowerShell kullandığınızda, ilgili giden istenmeyen posta filtresi kuralı kaldırılmaz.

PowerShell'de giden istenmeyen posta filtresi ilkesini kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı giden istenmeyen posta filtresi ilkesini kaldırır.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Giden istenmeyen posta filtresi kurallarını kaldırmak için PowerShell kullanma

Giden istenmeyen posta filtresi kuralını kaldırmak için PowerShell kullandığınızda, ilgili giden istenmeyen posta filtresi ilkesi kaldırılmaz.

PowerShell'de giden istenmeyen posta filtresi kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı giden istenmeyen posta filtresi kuralını kaldırır.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Daha fazla bilgi için

[Engellenen kullanıcıları Kısıtlı Kullanıcılar portalından kaldırma](removing-user-from-restricted-users-portal-after-spam.md)

[Giden iletiler için yüksek riskli teslim havuzu](high-risk-delivery-pool-for-outbound-messages.md)

[İstenmeyen posta önleme SSS](anti-spam-protection-faq.yml)

[Otomatik iletilen iletiler raporu](mfi-auto-forwarded-messages-report.md)
