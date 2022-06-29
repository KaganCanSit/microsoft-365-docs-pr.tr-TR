---
title: Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma
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
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, desteklenen belirli senaryolarda (üçüncü taraf kimlik avı simülasyonları ve güvenlik işlemleri (SecOps) posta kutularına teslim edilen iletiler) filtrelenmemesi gereken iletileri belirlemek için Exchange Online Protection (EOP) içinde gelişmiş teslim ilkesini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 109d711623d2a0355851414af3ef0cb1beadf6af
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490453"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Üçüncü taraf kimlik avı simülasyonlarının kullanıcılara ve filtrelenmemiş iletilerin SecOps posta kutularına teslimini yapılandırma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Kuruluşunuzun varsayılan olarak güvenli](secure-by-default.md) kalmasını sağlamak için Exchange Online Protection (EOP), kötü amaçlı yazılım veya yüksek güvenilirlikli kimlik avı olarak tanımlanan iletiler için güvenli listelere veya filtreleme atlamalarına izin vermez. Ancak, filtrelenmemiş iletilerin teslimini gerektiren belirli senaryolar vardır. Örneğin:

- **Üçüncü taraf kimlik avı simülasyonları: Sanal saldırılar**, kuruluşunuzu gerçek bir saldırı etkilemeden önce savunmasız kullanıcıları belirlemenize yardımcı olabilir.
- **Güvenlik işlemleri (SecOps) posta kutuları**: Güvenlik ekipleri tarafından filtrelenmemiş iletileri (hem iyi hem de kötü) toplamak ve çözümlemek için kullanılan ayrılmış posta kutuları.

_Bu belirli senaryolardaki_ gelen iletilerin filtrelenmesini önlemek için Microsoft 365'teki _gelişmiş teslim ilkesini_ kullanırsınız.<sup>\*</sup> Gelişmiş teslim ilkesi, bu senaryolardaki iletilerin aşağıdaki sonuçları elde etmesini sağlar:

- EOP ve Office 365 için Microsoft Defender filtreler bu iletilerde hiçbir işlem gerçekleştirmez.<sup>\*</sup>
- İstenmeyen posta ve kimlik avı için [sıfır saatlik Temizleme (ZAP)](zero-hour-auto-purge.md) bu iletilerde hiçbir işlem gerçekleştirmez.<sup>\*\*</sup>
- [Bu senaryolar için varsayılan sistem uyarıları](/microsoft-365/compliance/alert-policies#default-alert-policies) tetiklenmez.
- [Office 365 için Defender'da AIR ve kümeleme](office-365-air.md) bu iletileri yoksayar.
- Özellikle üçüncü taraf kimlik avı simülasyonları için:
  - [Yönetici gönderimleri](admin-submission.md), iletinin bir kimlik avı simülasyonu kampanyasının parçası olduğunu ve gerçek bir tehdit olmadığını belirten otomatik bir yanıt oluşturur. Uyarılar ve AIR tetiklenmez. Yönetici gönderimleri deneyimi, bu iletileri sanal bir tehdit olarak gösterir.
  - Kullanıcı [Rapor İletisi veya Rapor Kimlik Avı eklentilerini](enable-the-report-message-add-in.md) kullanarak bir kimlik avı simülasyonu iletisi bildirdiğinde sistem uyarı, araştırma veya olay oluşturmaz. Bağlantılar veya dosyalar patlamaz, ancak ileti **Gönderimler** sayfasının **Kullanıcı tarafından bildirilen iletiler** sekmesinde de gösterilir.
  - [Office 365 için Defender'daki Güvenli Bağlantılar](safe-links.md), tıklama sırasında bu iletilerde özel olarak tanımlanan URL'leri engellemez veya patlamaz. URL'ler sarmalanmaya devam eder, ancak engellenmez.
  - [Office 365 için Defender'deki Güvenli Ekler](safe-attachments.md) bu iletilerdeki ekleri patlamaz.

<sup>\*</sup> Kötü amaçlı yazılım filtrelemeyi atlayamazsınız.

<sup>\*\*</sup> Kötü amaçlı yazılım için ZAP'ın kapalı olduğu SecOps posta kutusu için bir kötü amaçlı yazılımdan koruma ilkesi oluşturarak kötü amaçlı yazılım için ZAP'ı atlayabilirsiniz. Yönergeler için bkz [. EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

Gelişmiş teslim ilkesi tarafından tanımlanan iletiler güvenlik tehditleri olmadığından, iletiler sistem geçersiz kılmalarıyla işaretlenir. Yönetici deneyimler, **kimlik avı simülasyon** sistemi geçersiz kılma veya **SecOps posta kutusu** sistemi geçersiz kılma nedeniyle bu iletileri gösterir. Yöneticiler aşağıdaki deneyimlerde bu sistem geçersiz kılmalarını filtreleyebilir ve analiz edebilir:

- [Office 365 için Defender plan 2'deki Tehdit Gezgini/Gerçek zamanlı algılamalar](threat-explorer.md): Yönetici **Sistem geçersiz kılma kaynağında** filtreleyebilir ve **Kimlik Avı simülasyonu** veya **SecOps Posta Kutusu'nda** seçim yapabilir.
- [Tehdit Gezgini'ndeki E-posta varlığı Sayfası/Gerçek zamanlı algılamalar](mdo-email-entity-page.md): Yönetici, **Geçersiz Kılmalar** bölümündeki **Kiracı geçersiz kılma** altında **SecOps posta kutusu** veya **Kimlik Avı benzetimi** tarafından kuruluş ilkesi tarafından izin verilen bir iletiyi görüntüleyebilir.
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report): Yönetici, açılan menüde **Sistem geçersiz kılmaya göre verileri görüntüleyebilir** ve kimlik avı simülasyon sistemi geçersiz kılma nedeniyle izin verilen iletileri görmeyi seçebilir. SecOps posta kutusu geçersiz kılma işleminin izin verdiği iletileri görmek için, **nedene göre grafik dökümü açılan menüsünde teslim konumuna göre** **grafik dökümünü** seçebilirsiniz.
- [Uç Nokta için Microsoft Defender gelişmiş avcılık](../defender-endpoint/advanced-hunting-overview.md): Kimlik avı simülasyonu ve SecOps posta kutusu sistemi geçersiz kılmaları, EmailEvents'teki OrgLevelPolicy içinde seçenekler olarak gösterilir.
- [Kampanya Görünümleri](campaigns.md): Yönetici **Sistem geçersiz kılma kaynağında** filtreleyebilir ve **Kimlik Avı benzetimi** veya **SecOps Posta Kutusu'nı** seçebilir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Gelişmiş teslim** sayfasına gitmek için dosyasını açın <https://security.microsoft.com/advanceddelivery>.

- Güvenlik & Uyumluluğu PowerShell'e bağlanmak için bkz. [Güvenlik & Uyumluluk PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

- Bu makaledeki yordamları gerçekleştirmeden önce size izinler atanmalıdır:
  - Gelişmiş teslim ilkesinde yapılandırılmış ayarları oluşturmak, değiştirmek veya kaldırmak için, **Microsoft 365 Defender portalında** **Güvenlik Yöneticisi** rol grubunun üyesi ve **Exchange Online** **Kuruluş Yönetimi** rol grubunun üyesi olmanız gerekir.
  - Gelişmiş teslim ilkesine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalındaki İzinler](permissions-microsoft-365-security-center.md) ve [Exchange Online'deki İzinler](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > Kullanıcıları ilgili Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365'teki diğer özellikler için izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Gelişmiş teslim ilkesinde SecOps posta kutularını yapılandırmak için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Gelişmiş teslim** bölümüne gidin. Doğrudan **Gelişmiş teslim** sayfasına gitmek için kullanın <https://security.microsoft.com/advanceddelivery>.

2. **Gelişmiş teslim** sayfasında **SecOps posta kutusu** sekmesinin seçili olduğunu doğrulayın ve aşağıdaki adımlardan birini yapın:
   - Düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.
   - Yapılandırılmış kimlik avı benzetimi yoksa **Ekle'ye** tıklayın.

3. Açılan **SecOps posta kutularını düzenle** açılır öğesinde, aşağıdaki adımlardan birini yaparak SecOps posta kutusu olarak ayarlamak istediğiniz mevcut bir Exchange Online posta kutusu girin:
   - Kutuya tıklayın, posta kutusu listesinin çözümlenmesine izin verin ve ardından posta kutusunu seçin.
   - Kutuya tıklayın, posta kutusu için bir tanımlayıcı yazmaya başlayın (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) ve sonuçlardan posta kutusunu (görünen ad) seçin.

     Bu adımı gerektiği kadar tekrarlayın. Dağıtım gruplarına izin verilmez.

     Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

4. Bitirdiğinizde, **Kaydet**'i tıklatın.

Yapılandırdığınız SecOps posta kutusu girişleri **SecOps posta kutusu** sekmesinde görüntülenir. Değişiklik yapmak için Düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) Sekmede **düzenleyin**.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Gelişmiş teslim ilkesinde üçüncü taraf kimlik avı simülasyonlarını yapılandırmak için Microsoft 365 Defender portalını kullanın

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Gelişmiş teslim** bölümüne gidin. Doğrudan **Gelişmiş teslim** sayfasına gitmek için kullanın <https://security.microsoft.com/advanceddelivery>.

2. **Gelişmiş teslim** sayfasında **Kimlik avı simülasyonu** sekmesini seçin ve aşağıdaki adımlardan birini yapın:
   - Düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.
   - Yapılandırılmış kimlik avı benzetimi yoksa **Ekle'ye** tıklayın.

3. Açılan **Üçüncü taraf kimlik avı simülasyonunu düzenle** açılır penceresinde aşağıdaki ayarları yapılandırın:

   - **Etki alanı**: Bu ayarı genişletin ve kutuya tıklayıp bir değer girip Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek en az bir e-posta adresi etki alanı (örneğin, contoso.com) girin. Bu adımı gerektiği kadar tekrarlayın. En fazla 20 giriş ekleyebilirsiniz.

     > [!NOTE]
     > İletinin `5321.MailFrom` SMTP iletiminde kullanılan adresten ( **POSTA GÖNDEREN** adresi, P1 göndereni veya zarf göndereni olarak da bilinir) **etki alanını veya** kimlik avı simülasyonu satıcınız tarafından belirtilen Etki Alanı Anahtarları Tanımlanan Posta (DKIM) etki alanını kullanın.

   - **IP gönderme**: Bu ayarı genişletin ve kutuya tıklayıp bir değer girip Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek en az bir geçerli IPv4 adresi girin. Bu adımı gerektiği kadar tekrarlayın. En fazla 10 giriş ekleyebilirsiniz. Geçerli değerler şunlardır:
     - Tek IP: Örneğin, 192.168.1.1.
     - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
     - CIDR IP: Örneğin, 192.168.0.1/25.
   - **İzin vermek için simülasyon URL'leri**: Bu ayarı genişletin ve isteğe bağlı olarak kutuya tıklayıp bir değer girip Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek engellenmemesi veya patlatılmaması gereken kimlik avı simülasyonu kampanyanızın parçası olan belirli URL'leri girin. En fazla 10 giriş ekleyebilirsiniz. URL söz dizimi biçimi için bkz. [Kiracı İzin Ver/Engelle Listesi için URL söz dizimi](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Bu URL'ler tıklandığında kaydırılır, ancak engellenmez.

   Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   > [!NOTE]
   > Gelişmiş Teslim'de üçüncü taraf kimlik avı benzetimi yapılandırmak için aşağıdaki bilgileri sağlamanız gerekir:
   >
   > - Aşağıdaki kaynaklardan en az bir **Etki Alanı** :
   >   - Adres `5321.MailFrom` (POSTA KIMDEN adresi, P1 gönderen veya zarf gönderen olarak da bilinir).
   >   - DKIM etki alanı.
   > - En az bir **Ip Gönderiliyor**.
   >
   > simülasyon iletilerindeki **URL'lerin** engellenmediğinden emin olmak için isteğe bağlı olarak Simülasyon URL'leri ekleyebilirsiniz.
   > Her alan için en fazla 10 giriş belirtebilirsiniz.
   > En az bir **Etki Alanı** ve bir **Gönderme IP'sinde** eşleşme olması gerekir, ancak değerler arasındaki ilişki korunmaz.

4. İşiniz bittiğinde aşağıdaki adımlardan birini yapın:
   - **İlk kez**: **Ekle'ye** ve ardından **Kapat'a** tıklayın.
   - **Var olanı düzenle**: **Kaydet'e** ve ardından **Kapat'a** tıklayın.

Yapılandırdığınız üçüncü taraf kimlik avı benzetimi girişleri **, Kimlik Avı simülasyonu** sekmesinde görüntülenir. Değişiklik yapmak için Düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) Sekmede **düzenleyin**.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Filtreleme atlama gerektiren ek senaryolar

Gelişmiş teslim ilkesinin size yardımcı olabileceği iki senaryoya ek olarak, filtrelemeyi atlamanızı gerektirebilecek başka senaryolar da vardır:

- **Üçüncü taraf filtreleri**: Etki alanınızın MX kaydı Office 365 işaret _etmiyorsa_ (iletiler önce başka bir yere yönlendirilir), [varsayılan olarak güvenli](secure-by-default.md) _kullanılamaz_. Koruma eklemek isterseniz Bağlayıcılar için Gelişmiş Filtreleme'yi ( _atlama listesi_ olarak da bilinir) etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [Exchange Online ile üçüncü taraf bulut hizmeti kullanarak posta akışını yönetme](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Bağlayıcılar için Gelişmiş Filtreleme istemiyorsanız, üçüncü taraf filtreleme tarafından zaten değerlendirilmiş iletiler için Microsoft filtrelemesini atlamak için posta akışı kurallarını (aktarım kuralları olarak da bilinir) kullanın. Daha fazla bilgi için bkz. [İletilerde SCL'yi ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Gözden geçirilmekte olan hatalı pozitifler**: Microsoft tarafından [yönetici gönderimleri](admin-submission.md) aracılığıyla analiz edilmeye devam eden belirli iletilere geçici olarak izin vererek hatalı olarak Microsoft'a kötü olarak işaretlenen bilinen iyi iletileri (hatalı pozitifler) bildirmek isteyebilirsiniz. Tüm geçersiz kılmalarda olduğu gibi, bu izinlerin de geçici olması _**kesinlikle önerilir**_ .

## <a name="security--compliance-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Gelişmiş teslim ilkesinde SecOps posta kutuları için güvenlik & Uyumluluk PowerShell yordamları

Güvenlik & Uyumluluğu PowerShell'de, gelişmiş teslim ilkesindeki SecOps posta kutularının temel öğeleri şunlardır:

- **SecOps geçersiz kılma ilkesi**: **-SecOpsOverridePolicy cmdlet'leri tarafından\*** denetlendi.
- **SecOps geçersiz kılma kuralı**: **-SecOpsOverrideRule cmdlet'leri tarafından\*** denetlendi.

Bu davranış aşağıdaki sonuçlara sahiptir:

- İlkeyi önce siz oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan kuralı oluşturursunuz.
- PowerShell'den bir ilkeyi kaldırdığınızda, ilgili kural da kaldırılır.
- PowerShell'den bir kuralı kaldırdığınızda, ilgili ilke kaldırılmaz. İlgili ilkeyi el ile kaldırmanız gerekir.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>SecOps posta kutularını yapılandırmak için PowerShell kullanma

PowerShell'de gelişmiş teslim ilkesinde SecOps posta kutusunu yapılandırmak iki adımlı bir işlemdir:

1. SecOps geçersiz kılma ilkesini oluşturun.
2. Kuralın uygulandığı ilkeyi belirten SecOps geçersiz kılma kuralını oluşturun.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>1. Adım: SecOps geçersiz kılma ilkesini oluşturmak için PowerShell kullanma

SecOps geçersiz kılma ilkesini oluşturmak için aşağıdaki söz dizimini kullanın:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Belirttiğiniz Ad değerinden bağımsız olarak, ilke adı _SecOpsOverridePolicy_ olur, bu nedenle bu değeri de kullanabilirsiniz.

Bu örnek SecOps posta kutusu ilkesini oluşturur.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>2. Adım: SecOps geçersiz kılma kuralını oluşturmak için PowerShell kullanma

Bu örnek, belirtilen ayarlarla SecOps posta kutusu kuralını oluşturur.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Belirttiğiniz Ad değerinden bağımsız olarak kural adı _SecOpsOverrideRule_\<GUID\> \<GUID\> olur ve burada benzersiz bir GUID değeri olur (örneğin, 6fed4b63-3563-495d-a481-b24a311f8329).

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesini görüntülemek için PowerShell kullanma

Bu örnek, tek ve tek SecOps posta kutusu ilkesi hakkında ayrıntılı bilgi döndürür.

```powershell
Get-SecOpsOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>SecOps geçersiz kılma kurallarını görüntülemek için PowerShell kullanma

Bu örnek, SecOps geçersiz kılma kuralları hakkında ayrıntılı bilgi döndürür.

```powershell
Get-SecOpsOverrideRule
```

Önceki komutun yalnızca bir kural döndürmesi gerekse de, silinmeyi bekleyen tüm kurallar da sonuçlara eklenebilir.

Bu örnek geçerli kuralı (bir) ve geçersiz kuralları tanımlar.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Geçersiz kuralları tanımladıktan sonra, [bu makalenin devamında](#use-powershell-to-remove-secops-override-rules) açıklandığı gibi **Remove-SecOpsOverrideRule** cmdlet'ini kullanarak bunları kaldırabilirsiniz.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesini değiştirmek için PowerShell kullanma

SecOps geçersiz kılma ilkesini değiştirmek için aşağıdaki söz dizimini kullanın:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

Bu örnek SecOps geçersiz kılma ilkesine eklenir `secops2@contoso.com` .

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> İlişkili, geçerli bir SecOps geçersiz kılma kuralı varsa, kuraldaki e-posta adresleri de güncelleştirilir.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>SecOps geçersiz kılma kuralını değiştirmek için PowerShell kullanma

**Set-SecOpsOverrideRule** cmdlet'i SecOps geçersiz kılma kuralındaki e-posta adreslerini değiştirmez. SecOps geçersiz kılma kuralındaki **e-posta adreslerini değiştirmek için Set-SecOpsOverridePolicy** cmdlet'ini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesini kaldırmak için PowerShell kullanma

Bu örnek SecOps Posta Kutusu ilkesini ve ilgili kuralı kaldırır.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>SecOps geçersiz kılma kurallarını kaldırmak için PowerShell kullanma

SecOps geçersiz kılma kuralını kaldırmak için aşağıdaki söz dizimini kullanın:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

Bu örnek, belirtilen SecOps geçersiz kılma kuralını kaldırır.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Gelişmiş teslim ilkesinde üçüncü taraf kimlik avı simülasyonları için Güvenlik & Uyumluluğu PowerShell yordamları

Güvenlik & Uyumluluğu PowerShell'de, gelişmiş teslim ilkesindeki üçüncü taraf kimlik avı simülasyonlarının temel öğeleri şunlardır:

- **Kimlik avı simülasyonu geçersiz kılma ilkesi**: **-PhishSimOverridePolicy cmdlet'leri tarafından\*** denetleniyor.
- **Kimlik avı benzetimi geçersiz kılma kuralı**: **-PhishSimOverrideRule cmdlet'leri tarafından\*** denetleniyor.
- **İzin verilen (engellenmemiş) kimlik avı benzetimi URL'leri**: **-TenantAllowBlockListItems cmdlet'leri tarafından\*** denetleniyor.

Bu davranış aşağıdaki sonuçlara sahiptir:

- İlkeyi önce siz oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan kuralı oluşturursunuz.
- İlkedeki ve kuraldaki ayarları ayrı ayrı değiştirirsiniz.
- PowerShell'den bir ilkeyi kaldırdığınızda, ilgili kural da kaldırılır.
- PowerShell'den bir kuralı kaldırdığınızda, ilgili ilke kaldırılmaz. İlgili ilkeyi el ile kaldırmanız gerekir.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Üçüncü taraf kimlik avı simülasyonlarını yapılandırmak için PowerShell kullanma

PowerShell'de üçüncü taraf kimlik avı simülasyonu yapılandırmak çok adımlı bir işlemdir:

1. Kimlik avı benzetimi geçersiz kılma ilkesini oluşturun.
2. Aşağıdakileri belirten kimlik avı benzetimi geçersiz kılma kuralını oluşturun:
   - Kuralın uygulandığı ilke.
   - Kimlik avı benzetimi iletilerinin kaynak IP adresi.
3. İsteğe bağlı olarak, izin verilmesi gereken (engellenmeyen veya taranmayan) kimlik avı benzetimi URL'lerini belirleyin.

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>1. Adım: Kimlik avı benzetimi geçersiz kılma ilkesini oluşturmak için PowerShell kullanma

Bu örnek, kimlik avı benzetimi geçersiz kılma ilkesini oluşturur.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Not**: Belirttiğiniz Ad değerinden bağımsız olarak ilke adı _PhishSimOverridePolicy_ olur, bu nedenle bu değeri de kullanabilirsiniz.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>2. Adım: Kimlik avı benzetimi geçersiz kılma kuralını oluşturmak için PowerShell kullanma

Aşağıdaki sözdizimini kullanın:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Belirttiğiniz Ad değerinden bağımsız olarak, kural adı Benzersiz bir GUID değeri olan \<GUID\> _PhishSimOverrideRule_\<GUID\> olur (örneğin, a0eae53e-d755-4a42-9320-b9c6b55c5011).

Geçerli bir IP adresi girişi aşağıdaki değerlerden biridir:

- Tek IP: Örneğin, 192.168.1.1.
- IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
- CIDR IP: Örneğin, 192.168.0.1/25.

Bu örnek, belirtilen ayarlarla kimlik avı benzetimi geçersiz kılma kuralını oluşturur.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>3. Adım: (İsteğe bağlı) İzin vermek üzere kimlik avı benzetimi URL'lerini tanımlamak için PowerShell kullanın

Aşağıdaki sözdizimini kullanın:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

URL söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Ver/Engelle Listesi için URL söz dizimi](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

Bu örnek, belirtilen üçüncü taraf kimlik avı benzetimi URL'si için süre sonu olmayan bir URL izin girişi ekler.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesini görüntülemek için PowerShell kullanma

Bu örnek, tek ve tek kimlik avı benzetimi geçersiz kılma ilkesi hakkında ayrıntılı bilgiler döndürür.

```powershell
Get-PhishSimOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını görüntülemek için PowerShell kullanma

Bu örnek, kimlik avı simülasyonu geçersiz kılma kuralları hakkında ayrıntılı bilgi döndürür.

```powershell
Get-PhishSimOverrideRule
```

Önceki komutun yalnızca bir kural döndürmesi gerekse de, silinmeyi bekleyen tüm kurallar da sonuçlara eklenebilir.

Bu örnek geçerli kuralı (bir) ve geçersiz kuralları tanımlar.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Geçersiz kuralları belirledikten sonra, [bu makalenin devamında](#use-powershell-to-remove-phishing-simulation-override-rules) açıklandığı gibi **Remove-PhishSimOverrideRule** cmdlet'ini kullanarak bunları kaldırabilirsiniz.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girişlerini görüntülemek için PowerShell kullanma

İzin verilen kimlik avı benzetimi URL'lerini görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesini değiştirmek için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma ilkesini değiştirmek için aşağıdaki söz dizimini kullanın:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

Bu örnek, kimlik avı benzetimi geçersiz kılma ilkesini devre dışı bırakır.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını değiştirmek için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma kuralını değiştirmek için aşağıdaki söz dizimini kullanın:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

Bu örnek, belirtilen kimlik avı benzetimi geçersiz kılma kuralını aşağıdaki ayarlarla değiştirir:

- Etki alanı girdisini blueyonderairlines.com ekleyin.
- 192.168.1.55 IP adresi girişini kaldırın.

Bu değişikliklerin var olan girişleri etkilemediğini unutmayın.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girişlerini değiştirmek için PowerShell kullanma

URL değerlerini doğrudan değiştiremezsiniz. [Var olan URL girdilerini kaldırabilir](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) ve bu makalede açıklandığı gibi [yeni URL girdileri ekleyebilirsiniz](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow).

İzin verilen bir kimlik avı benzetimi URL girişinin diğer özelliklerini (örneğin, son kullanma tarihi veya açıklamalar) değiştirmek için aşağıdaki söz dizimini kullanın:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Değiştirileceği girdiyi URL değerlerine ( _Entrys_ parametresi) veya **Get-TenantAllowBlockListItems** cmdlet'inin ( _Ids_ parametresi) çıkışındaki Identity değerine göre tanımlarsınız.

Bu örnek, belirtilen girişin sona erme tarihini değiştirdi.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesini kaldırmak için PowerShell kullanma

Bu örnek, kimlik avı benzetimi geçersiz kılma ilkesini ve ilgili kuralı kaldırır.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını kaldırmak için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma kuralını kaldırmak için aşağıdaki söz dizimini kullanın:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

Bu örnek, belirtilen kimlik avı benzetimi geçersiz kılma kuralını kaldırır.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girişlerini kaldırmak için PowerShell kullanma

Mevcut kimlik avı simülasyonu URL girdisini kaldırmak için aşağıdaki söz dizimini kullanın:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Değiştirileceği girdiyi URL değerlerine ( _Entrys_ parametresi) veya **Get-TenantAllowBlockListItems** cmdlet'inin ( _Ids_ parametresi) çıkışındaki Identity değerine göre tanımlarsınız.

Bu örnek, belirtilen girişin sona erme tarihini değiştirdi.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
