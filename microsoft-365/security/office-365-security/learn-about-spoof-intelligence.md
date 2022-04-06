---
title: Bilgi yok denen bilgi içgörü
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection (EOP) bilgi Exchange Online Protection bilgi edinebiliyor.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ba31c5022cb8f449ce9e1e1a4ba65e87afd0b464
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471461"
---
# <a name="spoof-intelligence-insight-in-eop"></a>EOP'de akıllı Spoof Intelligence içgörü

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve tüm kuruluşlarda kullanılamaz. Bu makalede açıklanan özelliklere sahip olmadığınız için bkz. [EOP'de](walkthrough-spoof-intelligence-insight.md) akıllı ifade ilkesi ve bilgimliği spoof intelligence içgörü kullanarak kimliği doğrulanıyor gönderenleri yönetme.

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu Exchange Online, gelen e-posta iletileri otomatik olarak izinsiz girişlere karşı korunur. EOP, **kimlik avına karşı** genel savunmanın bir parçası olarak kimlik sahtesi kullanır. Daha fazla bilgi için bkz [. EOP'de anti-poing protection](anti-spoofing-protection.md).

Gönderen bir e-posta adresinin kimliklerini doğrularsa, bunlar, kuruma e-posta gönderen etki alanlarından bir kullanıcı veya dış etki alanında yer alan bir kullanıcı gibi görünür. Kimlik avı dolandırıcılığı yapan ve istenmeyen posta veya kimlik avı e-postası gönderenleri engellenmiş olması gerekir. Ancak, geçerli gönderenlerin e-postalarını kullanarak bilgi e-postalarını doğru bir şekilde ifade edin. Örneğin:

- İç etki alanlarına yapılan yasal senaryolar:
  - Üçüncü taraf gönderenler, şirket anketleri için kendi çalışanlarınıza toplu posta göndermek için etki alanınızı kullanır.
  - Bir dış şirket sizin adına reklam veya ürün güncelleştirmeleri üretir ve gönderir.
  - Bir asistanın düzenli olarak kurum içindeki başka bir kişiye e-posta göndermesi gerekir.
  - İç uygulama, e-posta bildirimleri gönderir.

- Dış etki alanlarının yasal senaryoları:
  - Gönderen bir posta listesindedir (tartışma listesi olarak da bilinir) ve posta listesi e-postayı özgün gönderenden posta listesinde tüm katılımcılara iletir.
  - Dış şirket başka bir şirket (örneğin, otomatik rapor veya hizmet olarak yazılım şirketi) adına e-posta gönderir.

Size kimliği doğrulanmamış  e-posta gönderenleri (SPF, DKIM veya DMARC denetimlerini geçemeyen etki alanlarından gelen iletiler) kimliksiz gönderenleri hızla tanımlamak ve bu gönderenlere el ile izin vermek için Microsoft 365 Defender portalında kimliksiz kimlik bilgisi içgörülerini kullanabilirsiniz.

Bilinen gönderenlerin bilinen konumlardan sahte e-posta göndermelerine izin vererek, hatalı pozitif sonuç iletilerini (iyi e-posta kötü olarak işaretlenir) azaltabilirsiniz. İzin verilen kimliği doğru olmayan gönderenleri izlemeniz, güvenli olmayan iletilerin organizasyona gelmeye devamsını önlemek için ek bir güvenlik katmanı sağlarsınız.

Benzer şekilde, bilgi e-postasına izin verilen kimliği doğru gönderenleri inceleyebilirsiniz ve bu gönderenleri ele geçirme kimliği bilgilerinden el ile engelleyebilirsiniz.

Bu makalenin kalan bölümü, Microsoft 365 Defender portalında ve PowerShell'de (Exchange Online'te posta kutusu olan Microsoft 365 kuruluşları için Exchange Online PowerShell; bağımsız EOP PowerShell'in kullanıldığı kuruluşlar için Exchange Online kutularını da) kullanın.

> [!NOTE]
>
> - Yalnızca bilgi e-postası bilgisinde, bilgi e-postası kimliği doğrulandığında kimliği doğrulanmadı olarak algılanan gönderenler. Bilgide, izin verme veya engelleme kararını geçersiz kılabilirsiniz; kimliği doğruya sahip olan gönderen, yalnızca Kiracı İzin Ver/Engelleme Listesi'nin Giriş Kimliği  sekmesinde görüntülenen bir el ile izin verme veya engelleme girişi haline gelir. Ayrıca, kimliği doğru hesabıyla alınan gönderenler için, kimliği doğrulandığından önce bu gönderenlere yönelik girişlere izin verme veya engellemeyi el ile oluşturabilirsiniz. Daha fazla bilgi için bkz [. EOP'de Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
>
> - Kimlik bilgisi içgörüleri ve  Kiracı İzin Ver/Engelle listesinde kimlik bilgileri sekmesi, Güvenlik ve Uyumluluk Merkezi'nde bulunan istenmeyen posta önleme ilkesi sayfasında bulunan kimlik bilgisi ilkesi işlevselliğinin yerini & değiştirir.
>
>- Akıllı bilgi bilgisinde 7 günlük veri ortaya çıktı. **Get-SpoofIntelligenceInsight** cmdlet'i 30 günlük veri gösterir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kiracı İzin Ver/ **Engelleme Listesi sayfasındaki** Bilgi Yoklama **sekmesine gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. Doğrudan **Spoof Intelligence içgörü sayfasına gitmek** için , kullanın <https://security.microsoft.com/spoofintelligence>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Kullanıcı hesabı zekası ilkesinde değişiklik yapmak veya bilgi oturumlarını devre dışı bırakmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olmak** gerekir.
  - Akıllı ifade ilkesine salt okunur erişim için, **Genel** Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olmak gerekir.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  > - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- EOP ve Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerde kimlik avı zekasını etkinleştirir ve devre dışı Office 365 için Microsoft Defender. Akıllı ifade varsayılan olarak etkinleştirilmiştir. Daha fazla bilgi için, [EOP'de](configure-anti-phishing-policies-eop.md) kimlik avı koruma ilkelerini yapılandırma veya EOP'de kimlik avı [önleme ilkelerini yapılandırma Office 365 için Microsoft Defender](configure-mdo-anti-phishing-policies.md).

- Kimlik sahtesi koruması için önerilen ayarlarımız için bkz. [EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında bilgi Microsoft 365 Defender açma

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, Kurallar bölümündeki **E-posta &** \> İşbirliği **İlkeleri'ne & Tehdit** \>  \> ilkeleri **Kiracı İzin Verme/Engelleme** Listeleri **bölümüne** gidin. Doğrudan Kiracı İzin Ver/ **Engelleme Listesi sayfasındaki** Bilgi Yoklama **sekmesine gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. Kiracı İzin **Ver/Engelle Listeleri sayfasında** , bilgi yok gibi bir bilgi bilgisi şu şekilde görünür:

   :::image type="content" source="../../media/m365-sc-spoof-intelligence-insight.png" alt-text="Kimlik avıyla mücadele ilkesi sayfasındaki Kimlik sahtesi bilgileri içgörü" lightbox="../../media/m365-sc-spoof-intelligence-insight.png":::

   Bu içgörüde iki mod vardır:

   - **Insight mode**: If spoof intelligence is enabled, the insight shows you how many messages isdetected by spoof intelligence during the past seven days.
   - **Eğer mod**: Akıllı ifade devre dışı bırakılırsa bu içgörü, son yedi gün içinde akıllı ifade  kullanarak kaç ileti tespit edilemedi bilgisinde olduğunu gösterir.

Akıllı ifade algılamaları hakkında bilgi görüntülemek için, Bilgi yoklama bilgisinde Bilgi yoklama etkinliğini görüntüle'ye tıklayın.

### <a name="view-information-about-spoofed-messages"></a>E-posta iletilerini görüntüleme

> [!NOTE]
> Unutmayın, bu sayfada yalnızca kimliği doğruya sahip olduğu için kimliği doğru tespit edilen gönderenler görünür. Bilgide, izin verme veya engelleme kararını geçersiz kılabilirsiniz; kimliği doğruya sahip olan gönderen, yalnızca Kiracı İzin Ver/Engelleme Listesi'nin Giriş Kimliği  sekmesinde görüntülenen bir el ile izin verme veya engelleme girişi haline gelir.

Bilgi **bankasında** Bilgi Yoklama etkinliğini görüntüle'ye tıklarken  görüntülenen Bilgi yoklama bilgileri sayfasında aşağıdaki bilgiler yer aldı:

- **Kimlikfli kullanıcı**: **E-posta** istemcilerinin From kutusunda görüntülenen kimlik doğrulu **kullanıcının** etki alanı. From adresi adres olarak da `5322.From` bilinir.
- **Altyapı gönderme**: Altyapı olarak da _bilinir_. Gönderme altyapısı aşağıdaki değerlerden biri olur:
  - Kaynak e-posta sunucusunun IP adresinin ters DNS araması (PTR kaydı) içinde bulunan etki alanı.
  - Kaynak IP adresinin PTR kaydı yoksa, \<source IP\>gönderme altyapısı /24 olarak tanımlanır (örneğin, 192.168.100.100/24).
- **İleti sayısı**: Son 7 gün içinde, e-posta etki alanı ve gönderme altyapısı birlikten kuruluşa gönderilen ileti sayısı.
- **Son görülme**: E-posta gönderme altyapısından e-postanın e-postayla teslim tarihi: Geçersiz etki alanı içeren bir ileti.
- **Poof türü**: Aşağıdaki değerlerden biri:
  - **İç**: Kimliği doğru olmayan gönderen, organizasyona ait bir etki alanında (kabul edilen etki [alanı) yer alır](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
  - **Dış**: Gönderenin kimliği doğru değil dış etki alanında.
- **Eylem**: Bu değere **İzin Verildi** veya **Engellendi**:
  - **İzin** Verildi: Etki alanı, [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve DMARC için açık e-posta kimlik [doğrulaması başarısız oldu.](use-dmarc-to-validate-email.md) Ancak etki alanı, örtülü e-posta kimlik doğrulama denetimlerimizi (bileşik kimlik [doğrulama) geçti](email-validation-and-authentication.md#composite-authentication). Bunun sonucunda iletide, herhangi bir ifadeyle yapılan bir ifade yok.
  - **Engellendi**: Hatalı etki alanı ve gönderme altyapısı bileşiminden gelen iletiler, bilgi  hatalı bilgi tarafından kötü olarak işaretlenir. Sahte adresli iletilere yönelik eylem, varsayılan kimlik avı önleme ilkesi veya özel kimlik avı koruma ilkeleri tarafından denetlenmektedir (varsayılan değer İletiyi Gereksiz E-posta klasörüne **taşı'dır**). Daha fazla bilgi için bkz[. Kimlik avından korunma ilkelerini Office 365 için Microsoft Defender](configure-mdo-anti-phishing-policies.md).

Sonuçları sıralamak için seçili sütun başlıklarına tıkebilirsiniz.

Sonuçları filtrelemek için aşağıdaki seçenekleri kullanabilirsiniz:

- Filtre **düğmesine** tıklayın. Görüntülenen **Filtre** açılır yapısında, sonuçları filtrelemek için:
  - **Poof türü**
  - **Eylem**
- Sonuçları **filtrelemek** üzere kimliksüz etki alanı değerlerinin virgülle ayrılmış listesini veya altyapı değerlerini göndermek için Arama kutusunu kullanın.

### <a name="view-details-about-spoofed-messages"></a>Bilgi e-postalarını görüntüleme

Listeden bir girdiyi seçin, aşağıdaki bilgileri ve özellikleri içeren bir ayrıntılar açılır noktası görüntülenir:

-  Kopyalanmasına veya kopyalanması engellemeye izin **verme: İlk** kopyalı karar kararını geçersiz kılmak ve bu girişi, kopyalanmasına izin verme veya engelleme olarak Kiracı İzin Verilenler/Engelleme Listesi'ne taşımak için bu değerlerden birini seçin.
- Bunu neden yakaladığımız.
- Ne yapmak gerekir?
- Ana bilgi e-postası sayfasındaki bilgilerin çoğunu içeren etki alanı özeti.
- Gönderen hakkında WhoIs verileri.
- Threat [Explorer'ı açıp Gönderen hakkında Daha](threat-explorer.md) fazla ayrıntı görmek  \> için Tehdit Explorer'da Kimlik Avını **Görüntüle Office 365 için Microsoft Defender**.
- Kiracıda aynı gönderenden gelen benzer iletiler.

### <a name="about-allowed-spoofed-senders"></a>İzin verilen kimliği doğrulandı gönderenler hakkında

Kimliği doğrulandı bilgisinde yer alan izin verilen kimliği doğrulandı bilgisine veya el ile kimliği doğrulandı olarak değiştirmiş ve kimliği doğrulandı olarak  değiştirmiş bir gönderen, yalnızca kimliği doğrulandı olan etki alanı ve gönderme altyapısının bileşiminden  gelen iletilere izin verir. Herhangi bir kaynaktan e-posta yoluyla, ayrıca herhangi bir kaynaktan e-postaya izin vermez ve gönderen altyapıdan herhangi bir etki alanı için e-postaya izin vermez.

Örneğin, aşağıdaki kimliği doğru olan gönderenin ifadeyle birlikte girmesine izin verilir:

- **Etki** alanı: gmail.com
- **Altyapı**: tms.mx.com

Yalnızca bu etki alanı/gönderme altyapısı çiftinin e-postasına hesap yanızma izni verilir. Bu e-postayı kullanarak bilgi gmail.com diğer gönderenlere otomatik olarak izin verilmez. Diğer etki alanlarındaki gönderenlerden gelen ve e-tms.mx.com alınan iletiler yine de bilgi e-postası tarafından denetlenir ve engellenmiş olabilir.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>PowerShell veya tek başına EOP PowerShell'Exchange Online akıllı telefon bilgisinde ifade kullanma

PowerShell'de, **get-SpoofIntelligenceInsight** cmdlet'ini  kullanarak, akıllı ifadeyle algılanan izin verilen ve engellenen kimliği doğru olmayan gönderenleri görüntülersiniz. Kimliği doğru olmayan gönderenlere el ile izin vermek veya engellemek için **New-TenantAllowBlockListSpoofItems** cmdlet'ini kullanmalısınız. Daha fazla bilgi için bkz [. PowerShell kullanarak Kiracı İzin Ver/Engelleme Listesi'ne yapılan kimliği doğru gönderen girişlerini yönetme](tenant-allow-block-list.md).

Bilgi yok bilgi isteminde bilgileri görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-SpoofIntelligenceInsight
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Kimlik sahtesi ve kimlik avını yönetmenin diğer yolları

Kimlik avı ve kimlik avına karşı dikkatli olmak. Etki alanınızı kullanarak e-postanızı gönderenleri denetlemenin ve bunları organizasyona zarar vermeden önlemenin ilgili yolları:

- Adres **Mektup Birleştirme Raporu'nun ne olduğunu kontrol edin**. Bu raporu, kimliği doğruya sahip gönderenleri görüntülemek ve yönetmeye yardımcı olmak için sık sık kullanabilirsiniz. Bilgi için bkz [. Spoof Algılamaları raporu](view-email-security-reports.md#spoof-detections-report).

- Sender Policy Framework (SPF) yapılandırmanızı gözden geçirme. SPF'ye hızlı bir giriş yapmak ve SPF'yi hızla yapılandırmak için bkz Kimlik Microsoft 365 için [SPF'yi](set-up-spf-in-office-365-to-help-prevent-spoofing.md) ayarlama. Office 365'in SPF'yi nasıl kullandığı hakkında daha ayrıntılı bilgi için veya sorun giderme işlemi yapmak veya karma dağıtımlar gibi standart olmayan dağıtımlarda, Office 365, spoing'i engellemek için [Sender Policy Framework'i (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) nasıl kullanır? ile başlayabilirsiniz.

- DomainKeys Identified Mail (DKIM) yapılandırmanızı gözden geçirme. Saldırganların etki alanınıza geliyor gibi gelen iletiler göndermesini önlemeye yardımcı olmak için SPF ve DMARC'nin yanı sıra DKIM kullansanız da gerekir. DKIM, ileti üst bilgisinde yer alan e-posta iletilerine dijital imza eklemenize olanak sağlar. Bilgi için bkz. [Belirli bir yıl içinde özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM Office 365](use-dkim-to-validate-outbound-email.md).

- Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC) yapılandırmanızı gözden geçirme. DMARC'ın SPF ve DKIM ile uygulanması kimlik avı ve kimlik avı e-postalarına karşı ek koruma sağlar. DMARC, posta sistemlerinin SPF veya DKIM denetimlerini başarısız olan etki alanınız üzerinden gönderilen iletilerle ne olacağını belirlemesine yardımcı olur. Bilgi için bkz. [DMARC kullanarak E-postayı doğrulamak için Office 365](use-dmarc-to-validate-email.md).
