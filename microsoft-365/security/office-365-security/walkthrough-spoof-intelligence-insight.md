---
title: Bilgi e-postası ilkesi ve bilgi e-postası kimliğine sahip kimliği doğru ile birlikte kullanarak kimliği doğru bilgiye sahip olan gönderenleri yönetme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Yöneticiler, kimliği doğrulanmadı olarak algılanan gönderenlere izin vermek veya engellemek için ifade kullanma ilkesi ve bilgi tespit edilemedi içgörülerini nasıl kullanabileceğini öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 62be716a9663820f90d5c4f125f4634b3b399547
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010784"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>EOP'de akıllı ifade ilkesi ve kimliği doğruya gizli bilgi içgörü kullanarak kimliği doğru bilgiye sahip olan gönderenleri yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makalede, yerine yeni alınan kimliği doğru olmayan eski gönderen yönetim deneyimi (İstenmeyen posta önleme ilkeleri sayfasındaki kimlik bilgisi **ilkesi) açıklanmıştır**. Yeni deneyim hakkında daha fazla bilgi için (Kiracı  İzin Ver/Engelleme Listesi'nin Bilgi Yoklama sekmesi), bkz. [EOP'de Bilgi Yoklama ile ilgili bilgi.](learn-about-spoof-intelligence.md)

Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu Exchange Online olan Exchange Online e-posta iletileri, Ekim 2018'den sonra EOP tarafından yapılan izinsiz girişlere karşı otomatik olarak korunur. EOP, **kimlik avına karşı** genel savunmanın bir parçası olarak kimlik sahtesi kullanır. Daha fazla bilgi için bkz [. EOP'de anti-poing protection](anti-spoofing-protection.md).

Varsayılan (ve **yalnızca) kimlik** sahtesi ilkesi, geçerli gönderenler tarafından gönderilen sahte e-postanın EOP istenmeyen posta filtrelerine yakalanmaması için kullanıcılarınızı istenmeyen posta veya kimlik avı saldırılarından korumaya yardımcı olur. Ayrıca, kimlik doğrulaması olmayan e-postaları ( **SPF** , DKIM veya DMARC denetimlerini geçiremeyen etki alanlarından gelen iletiler) doğru olmayan hangi dış gönderenlerin gönderici olduğunu hızla belirlemek için kimlik bilgisi bilgilerinden de kullanabilirsiniz.

Microsoft 365 Defender portalında ya da Microsoft 365 Exchange Online'ta posta kutuları olan Microsoft 365 kuruluşları için Exchange Online PowerShell'de ya da bağımsız EOP PowerShell'de (Exchange Online  posta kutuları).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Kullanıcı hesabı zekası ilkesinde değişiklik yapmak veya bilgi oturumlarını devre dışı bırakmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olmak** gerekir.
  - Akıllı ifade ilkesine salt okunur erişim için, **Genel** Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olmak gerekir.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Kimlik sahtesi zekası seçenekleri kimlik avı önleme [ilkelerde Kimlik sahtesi ayarlarında açıklanmıştır](set-up-anti-phishing-policies.md#spoof-settings).

- Kimlik avı önleme ilkelerde kimlik sahte e-postası ayarlarını etkinleştirebilirsiniz, devre dışı bırakır ve yapılandırabilirsiniz. Aboneliğinize bağlı yönergeler için aşağıdaki konulardan birini izleyin:

  - [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).
  - [Kimlik avıyla mücadele ilkelerini Microsoft Defender'da kimlik Office 365](configure-mdo-anti-phishing-policies.md).

- Kimlik sahtesi koruması için önerilen ayarlarımız için bkz. [EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Gizli e-posta gönderenleri yönetme

Kimliği doğruyla engellenen gönderenlere izin vermenin ve engellemenin iki yolu vardır:

- [Akıllı ifade ilkeyi kullanma](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Akıllı ifade içgörülerini kullanma](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Bilgi e-postası ilkesinde kimliği doğruya sahip gönderenleri yönetme

> [!IMPORTANT]
> Bu makalede, yerine yeni alınan kimliği doğru olmayan eski gönderen yönetim deneyimi (İstenmeyen posta önleme ilkeleri sayfasındaki kimlik bilgisi **ilkesi) açıklanmıştır**. Yeni deneyim hakkında daha fazla bilgi için (Kiracı  İzin Ver/Engelleme Listesi'nin Bilgi Yoklama sekmesi), bkz. [EOP'de Bilgi Yoklama ile ilgili bilgi.](learn-about-spoof-intelligence.md)

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, **adı tıklatarak Kimlik bilgisi** ilkesi'ne tıklayın.

   ![Akıllı ifade ilkeyi seçin.](../../media/anti-spam-settings-spoof-intelligence-policy.png)

3. Görüntülenen **Bilgi Yok ayarı ilkesi** açılırken, aşağıdaki seçimlerden birini yapın:
   - **Gözden geçirmem olan gönderenleri göster**
   - **Yeni gönderenleri gözden geçirme**

4. Görüntülenen **Bu gönderenlerin kullanıcılarınızı** gizleme izni olup olduğuna karar verin açılır iletisinde, aşağıdaki sekmelerden birini seçin:
   - **Etki Alanlarınız**: Gönderenler, iç etki alanlarınız içinde kullanıcıları kullanarak e-posta gönderir.
   - **Dış Etki** Alanları: Dış etki alanlarındaki kullanıcıları kullanarak e-posta gönderenler.

5. Genişlet simgesine ![tıklayın.](../../media/scc-expand-icon.png) ve **aşağıdaki seçimlerden birini yapın** :
   - **Evet**: Kimliği doğru iletinin gönderene izin verme.
   - **Hayır**: İletiyi yanıltılı olarak işaretleme. Eylem, varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir. Daha fazla bilgi için bkz [. Kimlik avı önleme ilkelerde kimlik avı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

   ![Göndericilerin kimliği doğru çıktısı alma ve gönderene ifadeyle birlikte ifadeyi gösterme izni olup olmadığını gösteren ekran görüntüsü.](../../media/spoof-allow-block-flyout.png)

   Gördüğünüz sütunlar ve değerler aşağıdaki listede açıklanmıştır:

   - **Kimlik hesabı doğrulandı** kullanıcı: Kimlikleri kimlikle yapılan kullanıcı hesabı. Bu, Gönderen adresi (adres olarak da bilinir) içinde `5322.From` yer alan ve e-posta istemcisinde gösterilen ileti gönderendir. Bu adresin geçerliliği SPF tarafından denetlenir.
     - Etki **Alanlarınız** sekmesinde, değer tek bir e-posta adresi içeriyorsa veya kaynak e-posta sunucusu birden çok kullanıcı hesabı kimlik doğru içeriyorsa, birden **çok hesap içerir**.
     - Dış **Etki Alanları** sekmesinde değer, tam e-posta adresini değil, kimlikli kullanıcının etki alanını içerir.

   - **Altyapı Gönderme**: Kaynak e-posta sunucusunun IP adresinin ters DNS araması (PTR kaydı) içinde bulunan etki alanı. Kaynak IP adresinin PTR kaydı yoksa, \<source IP\>gönderme altyapısı /24 olarak tanımlanır (örneğin, 192.168.100.100/24).

     İleti kaynakları ve ileti gönderenleri hakkında daha fazla bilgi için bkz. [E-posta iletisi standartlarına genel bakış](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **İleti sayısı**: Son 30 gün içinde belirtilen kimliği doğru adresli gönderen veya gönderenleri içeren, gönderme altyapısından organizasyona gönderilen iletilerin sayısı.

   - **Kullanıcı şikayetlerinin sayısı**: Son 30 gün içinde kullanıcılarınızı bu gönderene yönelik şikayetler. Şikayetler genellikle Microsoft'a gereksiz gönderimler şeklindedir.

   - **Kimlik doğrulama** sonucu: Aşağıdaki değerlerden biri:
      - **Geçti**: Gönderenin e-posta kimlik doğrulamasını gönderenin kimlik doğrulamasını kontrol etti (SPF veya DKIM).
      - **Başarısız**: Gönderen, EOP gönderen kimlik doğrulamasını denetlerken başarısız oldu.
      - **Bilinmiyor**: Bu denetimlerin sonucu bilinmiyor.

   - **Son görülme**: Kimlik doğrulandı kullanıcı içeren gönderme altyapısından bir iletinin alınma tarihi.

   - **İlkeyi ifade etmek için izin verildi mi?**: Burada gördüğünüz değerler:
     - **Evet**: Kimlik doğrulu kullanıcı ve gönderme altyapısı bileşiminden gelen iletilere izin verilir ve bu iletiler kimlik e-postası olarak kabul edilir.
     - **Hayır**: Kimlik doğrulu kullanıcı ve gönderme altyapısının bileşiminden gelen iletiler kimlik doğrulandı olarak işaretlenir. Eylem, varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir (varsayılan değer İletiyi Gereksiz E-posta **klasörüne taşı'dır**). Daha fazla bilgi için sonraki bölüme bakın.

     - **Bazı kullanıcılar** (**yalnızca** Etki Alanları sekmeniz): Gönderme altyapısı birden çok kullanıcıya hesap verir; bu altyapıda bazı kullanıcıya izin verilir ve bazı kullanıcılara izin verilmez. Belirli adresleri **görmek** için Ayrıntılı sekmesini kullanın.

6. Bitirdiğinizde, **Kaydet**'i tıklatın.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>PowerShell kullanarak kimliği doğruya sahip gönderenleri yönetme

> [!IMPORTANT]
> Bu makalede, yerine yeni alınan kimliği doğru olmayan eski gönderen yönetim deneyimi (İstenmeyen posta önleme ilkeleri sayfasındaki kimlik bilgisi **ilkesi) açıklanmıştır**. Yeni deneyim hakkında daha fazla bilgi için (Kiracı  İzin Ver/Engelleme Listesi'nin Bilgi Yoklama sekmesi), bkz. [EOP'de Bilgi Yoklama ile ilgili bilgi.](learn-about-spoof-intelligence.md)

İzin verilen ve engellenen gönderenleri gizli bilgilerde görüntülemek için aşağıdaki söz dizimi kullanın:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Bu örnekte, etki alanlarınıza kullanıcı kimliğiyle girmesine izin verilen tüm gönderenler hakkında ayrıntılı bilgiler verilir.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Kimlik bilgisinde izin verilen ve engellenen gönderenleri yapılandırmak için şu adımları izleyin:

1. **Get-PhishFilterPolicy** cmdlet'inin çıktısını CSV dosyasına yazarak kimlik sahtesi algılanan gönderenlerin geçerli listesini yakalamak için aşağıdaki komutu çalıştırma:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Aşağıdaki değerleri eklemek veya değiştirmek için CSV dosyasını düzenleyin:
   - **Gönderen** (kaynak sunucunun PTR kaydında veya IP/24 adresinde etki alanı)
   - **KullanıcıpoofedUser**: Aşağıdaki değerlerden biri:
     - İç kullanıcının e-posta adresi.
     - Dış kullanıcının e-posta etki alanı.
     - Kimliği doğru olmayan e-posta adresi ne olursa **olsun, belirtilen** Gönderen'den gelen kimliği doğru olmayan tüm iletileri engellemek veya bu iletilere izin vermek istediğinizi belirten boş bir değer.
   - **AllowedToSpoof** (Evet veya Hayır)
   - **PoofType** (İç veya Dış)

   Aşağıdaki komutu çalıştırarak dosyayı kaydedin, dosyayı okuyun ve içeriği değişken `$UpdateSpoofedSenders` olarak depo edin:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Aşağıdaki komutu `$UpdateSpoofedSenders` çalıştırarak kimlik bilgileri ilkesi yapılandırmak için değişkeni kullanın:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Bilgi e-postası içgörüsinde kimliği doğruya sahip gönderenleri yönetme

> [!IMPORTANT]
> Bu makalede, yerine yeni alınan kimliği doğru olmayan eski gönderen yönetim deneyimi (İstenmeyen posta önleme ilkeleri sayfasındaki kimlik bilgisi **ilkesi) açıklanmıştır**. Yeni deneyim hakkında daha fazla bilgi için (Kiracı  İzin Ver/Engelleme Listesi'nin Bilgi Yoklama sekmesi), bkz. [EOP'de Bilgi Yoklama ile ilgili bilgi.](learn-about-spoof-intelligence.md)

1. Güvenlik ve Uyumluluk &'nde Tehdit Yönetimi **Panosu'ne** \> **gidin**.

2. Tablo **Analizler**, aşağıdaki öğelerden birini seçin:

   - **Son yedi gün içinde** olası iddialı etki alanları: Bu içgörü, akıllı ifadenin etkinleştirilmiştir (varsayılan olarak etkinleştirilmiştir).
   - **Spoof Protection'ı** etkinleştirme: Bu içgörü, ifadenin devre dışı bırak bırakılmıştır ve içgörüye tıklamak ise bilgi bilgisinde akıllı ifadeyi etkinleştirmenizi sağlar.

3. Panoya ilişkin içgörü, aşağıdaki gibi bilgileri gösterir:

   ![Akıllı bilgi bilgisinde bir bilgi almama ekran görüntüsü.](../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png)

   Bu içgörüde iki mod vardır:

   - **Insight mode**: If spoof intelligence is enabled, the insight shows you were how many messages were impact by ourpoof intelligence capabilities over the past7 days.
   - **Eğer mod**: Bilgi yok ise, bu içgörü size son yedi gün içinde akıllı ifademizi kullanarak  kaç ibarenin etki olacağını gösteriyor.

   Her iki durumda da, bilgilerde görüntülenen şüpheli etki alanları iki kategoriye **ayrılır: Şüpheli** etki alanları **ve Şüpheli olmayan etki alanları**.

   - **Şüpheli etki alanları**:
     - **Yüksek** güven düzeni: Geçmiş gönderme düzenlerine ve etki alanlarının itibar puanına bağlı olarak, etki alanlarının ele geçmiş olduğunu ve bu etki alanlarındaki iletilerin kötü amaçlı olma olasılığının daha yüksek olduğunu kesinlikle güveniyoruz.
     - **Güven** kalıbını ortalama: Geçmiş gönderme düzenlerine ve etki alanlarının itibar puanına bağlı olarak, etki alanlarının ifadelerinin doğru gönderildiğine ve bu etki alanlarından gönderilen iletilerin meşru olduğu konusunda oldukça güveniyoruz. Bu kategorideki hatalı pozitif sonuçlar, yüksek güven sahte e-postalarına göre daha olasıdır.
   - **Şüpheli olmayan etki alanları**: Etki alanı [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC](use-dmarc-to-validate-email.md) için açık e-posta kimlik doğrulaması başarısız oldu. Ancak etki alanı, örtülü e-posta kimlik doğrulama denetimlerimizi (bileşik kimlik [doğrulama) geçti](email-validation-and-authentication.md#composite-authentication). Bunun sonucunda iletide, herhangi bir ifadeyle yapılan bir ifade yok.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Şüpheli ve açık olmayan etki alanları hakkında ayrıntılı bilgileri görüntüleme

1. Spoof Intelligence içgörü sayfasında,  Şüpheli etki alanları  veya Şüpheli olmayan etki alanları'nın üzerine tıklar ve **Ardından Bilgi Yok bilgi sayfasına** gidin. **Spoof Intelligence içgörü** sayfası aşağıdaki bilgileri içerir:

   - **Kimlik doğrulu etki** alanı: E-posta istemcilerinin From kutusunda görüntülenen, kimlik doğrulu **kullanıcının** etki alanı. Bu adres, adres olarak da `5322.From` bilinir.
   - **Altyapı**: Gönderme altyapısı olarak _da bilinir_. Kaynak e-posta sunucusunun IP adresinin ters DNS araması (PTR kaydı) içinde bulunan etki alanı. Kaynak IP adresinin PTR kaydı yoksa, \<source IP\>gönderme altyapısı /24 olarak tanımlanır (örneğin, 192.168.100.100/24).
   - **İleti sayısı**: Son 7 gün içinde, gönderen altyapıdan, belirtilen doğru adresli etki alanını içeren, kuruluşuma gönderilen iletilerin sayısı.
   - **Son görülme**: E-posta gönderme altyapısından e-postanın e-postayla teslim tarihi: Geçersiz etki alanı içeren bir ileti.
   - **Poof türü**: Bu değer **Dış'tır**.
   - **İlkeyi ifade etmek için izin verildi mi?**: Burada gördüğünüz değerler:
     - **Evet**: Kimlik doğrulu kullanıcının etki alanı ve gönderme altyapısının bileşiminden gelen iletilere izin verilir ve kimlik e-postası olarak işlem olmaz.
     - **Hayır**: Kimlik e-postası ile kullanıcı etki alanı ve gönderme altyapısının bileşiminden gelen iletiler kimlik doğrulandı olarak işaretlenir. Eylem, varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir (varsayılan değer İletiyi Gereksiz E-posta **klasörüne taşı'dır**).

2. Bir çıkışta etki alanı/gönderme altyapısı çifti hakkında ayrıntıları görüntülemek için listeden bir öğe seçin. Bu bilgiler şunları içerir:
   - Bunu neden yakaladığımız.
   - Ne yapmak gerekir?
   - Etki alanı özeti.
   - Gönderen hakkında WhoIs verileri.
   - Kiracıda aynı gönderenden gelen benzer iletiler.

   Buradan, İzin verilenler ve gönderen izin verilenler listesinden etki alanı/gönderme altyapısı çiftini ekleme **veya kaldırmayı** da seçebilirsiniz. Geçiş düğmeyi buna uygun olarak ayarlayın.

   ![Spoof Intelligence içgörü ayrıntıları bölmesinde bir etki alanının ekran görüntüsü.](../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png)

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Kimlik doğrulama için izin verilen ve kimlik bilgilerine izin verilmiyor gönderenlerle kimlik bilgileri yapılandırıldığından emin olmak için, aşağıdaki adımlardan herhangi birini kullanın:

- **E-posta & İşbirliği** \> **İlkeler & Kuralları** \> **Tehdit ilkeleri** \> **İlkeler**  \>  \>  \> bölümündeki Kimlik doğrulama ilkesi, Gözden geçirmem gereken gönderenleri göster'i seçin, Etki Alanlarınız veya  Dış Etki Alanlarınız sekmesini seçin ve gönderen için Kimlik e-postasına izin ve verili **?** değerini doğrulayın.

- PowerShell'de, izin verilen ve kimliği doğrulanmaz gönderenleri görüntülemek için aşağıdaki komutları çalıştırın:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- PowerShell'de, aşağıdaki komutu çalıştırarak tüm kimliği doğrunmış gönderenler listesini BIR CSV dosyasına aktarın:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
