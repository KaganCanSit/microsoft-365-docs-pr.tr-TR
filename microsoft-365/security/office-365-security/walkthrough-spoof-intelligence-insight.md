---
title: Kimlik sahtekarlığına neden olan gönderenleri kimlik sahtekarlık zekası ilkesini ve kimlik sahtekarı zeka içgörülerini kullanarak yönetme
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
description: Yöneticiler, kimlik sahtekarlığına neden olan gönderenlere izin vermek veya bunları engellemek için kimlik sahtekarlık zekası ilkesini ve sahte zeka içgörülerini kullanmayı öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 59f52e7fe10030283601aad86a1aa49ed91255ab
ms.sourcegitcommit: 363bdc517bd2564c6420cf21f352e97079f950e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2022
ms.locfileid: "65031833"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>EOP'de sahte zeka ilkesini ve sahte zeka içgörülerini kullanarak sahte gönderenleri yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makalede, değiştirilen eski sahte gönderen yönetimi deneyimi (**istenmeyen posta önleme ilkeleri** sayfasındaki **kimlik sahtekarlığı zekası ilkesi**) açıklanmaktadır. Yeni deneyim hakkında daha fazla bilgi için (Kiracı İzin Ver/Engelle Listesindeki Kimlik Sahtekarlık **sekmesi),** bkz. [EOP'de kimlik sahtekarı zekası içgörüleri](learn-about-spoof-intelligence.md).

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, gelen e-posta iletileri Ekim 2018 itibarıyla EOP tarafından kimlik sahtekarlığına karşı otomatik olarak korunur. EOP, kuruluşunuzun kimlik avına karşı genel savunmasının bir parçası olarak kimlik **sahtekarlığı zekasını** kullanır. Daha fazla bilgi için bkz. [EOP'de kimlik sahtekarlığı koruması](anti-spoofing-protection.md).

Varsayılan (ve yalnızca) kimlik **sahtekarlığı zeka ilkesi** , yasal gönderenler tarafından gönderilen sahte e-postaların EOP istenmeyen posta filtrelerine yakalanmamasını sağlarken kullanıcılarınızı istenmeyen posta veya kimlik avı saldırılarına karşı korur. Kimlik doğrulaması yapılmamış e-postaları (SPF, DKIM veya DMARC denetimlerinden geçmeyen etki alanlarından gelen iletiler) hangi dış gönderenlerin size meşru olarak gönderdiğini hızla belirlemek için De Kimlik **Sahtekarı zekası içgörülerini** kullanabilirsiniz.

Kimlik sahtekarlık zekasını Microsoft 365 Defender portalında veya Exchange Online'da posta kutuları olan Microsoft 365 kuruluşlar için PowerShell'de (Exchange Online PowerShell Exchange Online olmayan kuruluşlar için tek başına EOP PowerShell'de yönetebilirsiniz  posta kutuları).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Kimlik sahtekarlık zekası ilkesini değiştirmek veya kimlik sahtekarlık zekasını etkinleştirmek veya devre dışı bırakmak için 
    -   **Kuruluş Yönetimi**
    -   **Güvenlik Yöneticisi** <u>ve</u> **Yalnızca Görüntüleme Yapılandırması** veya **Yalnızca Görüntüleme Kuruluş Yönetimi**.
  - Kimlik sahtekarı zeka ilkesine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Kimlik sahtekarlığı zekası seçenekleri [kimlik avı önleme ilkelerindeki kimlik sahtekarlığı ayarlarında](set-up-anti-phishing-policies.md#spoof-settings) açıklanmıştır.

- Kimlik avı önleme ilkelerinde kimlik sahtekarlığı zekası ayarlarını etkinleştirebilir, devre dışı bırakabilir ve yapılandırabilirsiniz. Aboneliğinizi temel alan yönergeler için aşağıdaki konulardan birine bakın:

  - [EOP'de kimlik avı önleme ilkelerini yapılandırın](configure-anti-phishing-policies-eop.md).
  - [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırın](configure-mdo-anti-phishing-policies.md).

- Kimlik sahtekarlığı zekası için önerilen ayarlarımız için bkz. [EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Sahte gönderenleri yönetme

Sahte gönderenlere izin vermenin ve bunları engellemenin iki yolu vardır:

- [Kimlik sahtekarlık zekası ilkesini kullanma](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Sahte zeka içgörülerini kullanma](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Kimlik sahtekarlığına neden olan gönderenleri kimlik bilgileri ilkesinde yönetme

> [!IMPORTANT]
> Bu makalede, değiştirilen eski sahte gönderen yönetimi deneyimi (**istenmeyen posta önleme ilkeleri** sayfasındaki **kimlik sahtekarlığı zekası ilkesi**) açıklanmaktadır. Yeni deneyim hakkında daha fazla bilgi için (Kiracı İzin Ver/Engelle Listesindeki Kimlik Sahtekarlık **sekmesi),** bkz. [EOP'de kimlik sahtekarı zekası içgörüleri](learn-about-spoof-intelligence.md).

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında ada tıklayarak **Kimlik sahtekarlığı zeka ilkesi'ni** seçin.

   :::image type="content" source="../../media/anti-spam-settings-spoof-intelligence-policy.png" alt-text="Kimlik sahtekarlık zekası ilkesini seçme seçeneği" lightbox="../../media/anti-spam-settings-spoof-intelligence-policy.png":::

3. Görüntülenen **Kimlik sahtekarı zeka ilkesi** açılır öğesinde aşağıdaki seçimlerden birini yapın:
   - **Daha önce incelediğim gönderenleri göster**
   - **Yeni gönderenleri gözden geçirme**

4. **Görüntülenen Bu gönderenlerin kullanıcılarınızı sahtekarlık etmesine izin verilip verilmediğini** belirleyin açılır penceresinde aşağıdaki sekmelerden birini seçin:
   - **Etki Alanlarınız**: İç etki alanlarınızdaki kullanıcıları sahtekarlık eden gönderenler.
   - **Dış Etki Alanları**: Dış etki alanlarındaki kullanıcıları sahtekarlık eden gönderenler.

5. Genişlet simgesine tıklayın ![.](../../media/scc-expand-icon.png) kimlik **sahtekarlığına izin verilsin mi?** sütununda aşağıdaki seçimlerden birini yapın:
   - **Evet**: Sahte gönderene izin verin.
   - **Hayır**: İletiyi sahte olarak işaretleyin. Eylem varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetleniyor. Daha fazla bilgi için bkz. [Kimlik avı önleme ilkelerindeki kimlik sahtekarlığı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

   :::image type="content" source="../../media/spoof-allow-block-flyout.png" alt-text="Sahte gönderenler açılır öğesi ve gönderenin kimlik sahtekarlığına izin verilip verilmediği" lightbox="../../media/spoof-allow-block-flyout.png":::

   Gördüğünüz sütunlar ve değerler aşağıdaki listede açıklanmıştır:

   - **Kimlik sahtekarlığına sahip kullanıcı**: Kimlik sahtekarlığına neden olan kullanıcı hesabı. Bu, e-posta istemcilerinde gösterilen Kimden adresinde (adres olarak `5322.From` da bilinir) ileti gönderendir. Bu adresin geçerliliği SPF tarafından denetlenmiyor.
     - **Etki Alanlarınız** sekmesinde, değer tek bir e-posta adresi içerir veya kaynak e-posta sunucusu birden çok kullanıcı hesabı sahtekarlığına neden oluyorsa, **birden çok** e-posta adresi içerir.
     - **Dış Etki Alanları** sekmesinde, değer tam e-posta adresini değil, sahte kullanıcının etki alanını içerir.

   - **Gönderme Altyapısı**: Kaynak e-posta sunucusunun IP adresinin ters DNS aramasında (PTR kaydı) bulunan etki alanı. Kaynak IP adresinin PTR kaydı yoksa, gönderen altyapı /24 olarak \<source IP\>tanımlanır (örneğin, 192.168.100.100/24).

     İleti kaynakları ve ileti gönderenler hakkında daha fazla bilgi için bkz. [E-posta iletisi standartlarına genel bakış](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **# of messages**: Son 30 gün içinde kuruluşunuza gönderilen altyapıdan belirtilen sahte göndereni veya gönderenleri içeren ileti sayısı.

   - **# of user complaints**: Son 30 gün içinde kullanıcılarınız tarafından bu gönderene karşı yapılan şikayetler. Şikayetler genellikle Microsoft'a gereksiz gönderimler biçimindedir.

   - **Kimlik doğrulama sonucu**: Aşağıdaki değerlerden biri:
      - **Başarılı**: Gönderen, gönderen e-posta kimlik doğrulama denetimlerini (SPF veya DKIM) geçirdi.
      - **Başarısız**: Gönderen, EOP gönderen kimlik doğrulaması denetimlerini başarısız oldu.
      - **Bilinmiyor**: Bu denetimlerin sonucu bilinmiyor.

   - **Son görülen**: Sahte kullanıcıyı içeren gönderen altyapıdan iletinin alındığı son tarih.

   - **Kimlik sahtekarlığına izin veriliyor mu?**: Burada gördüğünüz değerler şunlardır:
     - **Evet**: Sahte kullanıcı ve gönderme altyapısı birleşiminden gelen iletilere izin verilir ve sahte e-posta olarak kabul edilmez.
     - **Hayır**: Sahte kullanıcı ve gönderme altyapısı birleşiminden gelen iletiler sahte olarak işaretlenir. Eylem varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir (varsayılan değer **İletiyi Gereksiz E-posta klasörüne taşı'dır**). Daha fazla bilgi için sonraki bölüme bakın.

     - **Bazı kullanıcılar** (Yalnızca **Etki Alanlarınız** sekmesi): Gönderen bir altyapı, bazı sahte kullanıcılara izin verilen ve bazılarının izin verilmediği birden çok kullanıcıyı yanıltıyor. Belirli adresleri görmek için **Ayrıntılı** sekmesini kullanın.

6. Bitirdiğinizde, **Kaydet**'i tıklatın.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Sahte gönderenleri yönetmek için PowerShell kullanma

> [!IMPORTANT]
> Bu makalede, değiştirilen eski sahte gönderen yönetimi deneyimi (**istenmeyen posta önleme ilkeleri** sayfasındaki **kimlik sahtekarlığı zekası ilkesi**) açıklanmaktadır. Yeni deneyim hakkında daha fazla bilgi için (Kiracı İzin Ver/Engelle Listesindeki Kimlik Sahtekarlık **sekmesi),** bkz. [EOP'de kimlik sahtekarı zekası içgörüleri](learn-about-spoof-intelligence.md).

Kimlik sahtekarlık zekasında izin verilen ve engellenen gönderenleri görüntülemek için aşağıdaki söz dizimini kullanın:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Bu örnek, etki alanlarınızdaki kullanıcıları yanıltmalarına izin verilen tüm gönderenler hakkında ayrıntılı bilgiler döndürür.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Kimlik sahtekarlığına izin verilen ve engellenen gönderenleri yapılandırmak için şu adımları izleyin:

1. Aşağıdaki komutu çalıştırarak **Get-PhishFilterPolicy** cmdlet'inin çıkışını csv dosyasına yazarak algılanan sahte gönderenlerin geçerli listesini yakalayın:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Aşağıdaki değerleri eklemek veya değiştirmek için CSV dosyasını düzenleyin:
   - **Gönderen** (kaynak sunucunun PTR kaydındaki etki alanı veya IP/24 adresi)
   - **SpoofedUser**: Aşağıdaki değerlerden biri:
     - İç kullanıcının e-posta adresi.
     - Dış kullanıcının e-posta etki alanı.
     - Sahte e-posta adresinden bağımsız olarak belirtilen **Gönderenden** gelen tüm sahte iletileri engellemek veya bu iletilere izin vermek istediğinizi belirten boş bir değer.
   - **AllowedToSpoof** (Evet veya Hayır)
   - **SpoofType** (İç veya Dış)

   Dosyayı kaydedin, dosyayı okuyun ve aşağıdaki komutu çalıştırarak içeriği adlı `$UpdateSpoofedSenders` bir değişken olarak depolayın:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. `$UpdateSpoofedSenders` Aşağıdaki komutu çalıştırarak kimlik sahtekarlığı zeka ilkesini yapılandırmak için değişkenini kullanın:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Sahtekarlık zekası içgörülerinde sahte gönderenleri yönetme

> [!IMPORTANT]
> Bu makalede, değiştirilen eski sahte gönderen yönetimi deneyimi (**istenmeyen posta önleme ilkeleri** sayfasındaki **kimlik sahtekarlığı zekası ilkesi**) açıklanmaktadır. Yeni deneyim hakkında daha fazla bilgi için (Kiracı İzin Ver/Engelle Listesindeki Kimlik Sahtekarlık **sekmesi),** bkz. [EOP'de kimlik sahtekarı zekası içgörüleri](learn-about-spoof-intelligence.md).

1. Güvenlik & Uyumluluk Merkezi'nde **Tehdit Yönetimi** \> **Panosu'na** gidin.

2. **Analizler** satırında aşağıdaki öğelerden birini arayın:

   - **Son yedi gün içinde muhtemelen sahte etki alanları**: Bu içgörü, kimlik sahtekarlık zekasının etkinleştirildiğini gösterir (varsayılan olarak etkindir).
   - **Kimlik Sahtekarlığına Karşı Korumayı Etkinleştir**: Bu içgörü, sahte zekanın devre dışı bırakıldığını gösterir ve içgörüye tıklandığında kimlik sahtekarlığına olanak sağlanır.

3. Panodaki içgörüde aşağıdaki gibi bilgiler gösterilir:

   :::image type="content" source="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png" alt-text="Sahte zeka içgörüleri" lightbox="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png":::

   Bu içgörü iki moda sahiptir:

   - **İçgörü modu**: Kimlik sahtekarı zekası etkinleştirildiyse içgörü, son yedi gün içinde kimlik sahtekarı zekası özelliklerimizden kaç iletinin etkilendiğini gösterir.
   - **Durum modu**: Kimlik sahtekarı zekası devre dışı bırakılırsa, içgörü size son yedi gün içinde kimlik sahtekarı zekası özelliklerimizden *kaç iletinin* etkilendiğini gösterir.

   Her iki durumda da, içgörüde görüntülenen sahte etki alanları iki kategoriye ayrılır: **Şüpheli etki alanları** ve **Şüpheli olmayan etki alanları**.

   - **Şüpheli etki alanları**:
     - **Yüksek güvenilirlik sahtekarlığı**: Geçmiş gönderme desenlerine ve etki alanlarının saygınlık puanına bağlı olarak, etki alanlarının kimlik sahtekarlığından ve bu etki alanlarından gelen iletilerin kötü amaçlı olma olasılığının daha yüksek olduğundan eminiz.
     - **Orta düzeyde güvenilirlik sahtekarlığı**: Geçmiş gönderme desenlerine ve etki alanlarının saygınlık puanına bağlı olarak, etki alanlarının kimlik sahtekarlığından ve bu etki alanlarından gönderilen iletilerin meşru olduğundan oldukça eminiz. Bu kategoride hatalı pozitifler, yüksek güvenilirlik sahtekarlığına göre daha olasıdır.
   - **Şüpheli olmayan etki alanları**: Etki alanı başarısız olan açık e-posta kimlik doğrulaması [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC'yi](use-dmarc-to-validate-email.md) denetler. Ancak, etki alanı örtük e-posta kimlik doğrulaması denetimlerimizi ([bileşik kimlik doğrulaması](email-validation-and-authentication.md#composite-authentication)) geçti. Sonuç olarak, iletide kimlik sahtekarlığı önleme eylemi yapılmadı.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Şüpheli ve kötü amaçlı olmayan etki alanları hakkında ayrıntılı bilgileri görüntüleme

1. Kimlik sahtekarı zeka içgörüleri sayfasında **Şüpheli etki alanları** veya **Şüpheli olmayan etki alanları'na** tıklayarak **Sahte zeka içgörüleri** sayfasına gidin. **Spoof Intelligence içgörü** sayfası aşağıdaki bilgileri içerir:

   - **Kimlik sahtekarlığına sahip etki alanı**: E-posta istemcilerindeki **Kimden** kutusunda görüntülenen sahte kullanıcının etki alanı. Bu adres, adres olarak `5322.From` da bilinir.
   - **Altyapı**: _Gönderme altyapısı_ olarak da bilinir. Kaynak e-posta sunucusunun IP adresinin ters DNS aramasında (PTR kaydı) bulunan etki alanı. Kaynak IP adresinin PTR kaydı yoksa, gönderen altyapı /24 olarak \<source IP\>tanımlanır (örneğin, 192.168.100.100/24).
   - **İleti sayısı**: Kuruluşunuza gönderilen altyapıdan son 7 gün içinde belirtilen sahte etki alanını içeren ileti sayısı.
   - **Son görülen**: Sahte etki alanını içeren gönderen altyapıdan iletinin alındığı son tarih.
   - **Kimlik sahtekarı türü**: Bu değer **Dış** değeridir.
   - **Kimlik sahtekarlığına izin veriliyor mu?**: Burada gördüğünüz değerler şunlardır:
     - **Evet**: Sahte kullanıcının etki alanı ve gönderme altyapısı birleşiminden gelen iletilere izin verilir ve sahte e-posta olarak kabul edilmez.
     - **Hayır**: Sahte kullanıcının etki alanı ve gönderme altyapısı birleşiminden gelen iletiler sahte olarak işaretlenir. Eylem varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir (varsayılan değer **İletiyi Gereksiz E-posta klasörüne taşı'dır**).

2. Açılır listeden bir öğe seçerek etki alanı/gönderme altyapısı çifti hakkındaki ayrıntıları görüntüleyin. Bilgiler şunları içerir:
   - Bunu neden yakaladığımızı.
   - Yapmanız gerekenler.
   - Etki alanı özeti.
   - WhoIs verileri gönderen hakkında.
   - Kiracınızda aynı gönderenden gelen benzer iletiler.

   Buradan, etki alanı/gönderen altyapı çiftini gönderenin kimlik **sahtekarlığına izin verilenler** listesine eklemeyi veya kaldırmayı da seçebilirsiniz. İki durumlu düğmeyi buna göre ayarlamanız yeterlidir.

   :::image type="content" source="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png" alt-text="Spoof intelligence insight details bölmesindeki bir etki alanı" lightbox="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png":::

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Kimlik sahtekarlığına izin verilen ve kimlik sahtekarlığına izin verilmeyen gönderenlerle kimlik sahtekarlık zekası yapılandırdığınızdan emin olmak için aşağıdaki adımlardan birini kullanın:

- **E-posta & İşbirliği** \> **İlkeler & Kuralları** \> **Tehdit ilkeleri** \> **İlkeler** bölümünden \> **İstenmeyen posta** önleme **bilgileri ilkesi**\>' nde **Zaten gözden geçirdiğim** \> gönderenleri göster'i seçin **, Etki Alanlarınız** veya **Dış Etki Alanlarınız** sekmesini seçin ve gönderen için **Kimlik sahtekarlığına izin verilsin mi?** değerini doğrulayın.

- PowerShell'de, kimlik sahtekarlığına izin verilen ve kimlik sahtekarlığına izin verilmeyen gönderenleri görüntülemek için aşağıdaki komutları çalıştırın:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- PowerShell'de, tüm sahte gönderenlerin listesini bir CSV dosyasına aktarmak için aşağıdaki komutu çalıştırın:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
