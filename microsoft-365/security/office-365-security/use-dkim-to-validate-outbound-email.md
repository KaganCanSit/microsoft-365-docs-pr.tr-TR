---
title: Özel etki alanınızda e-posta için DKIM kullanma
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Özel etki alanınızdan gönderilen iletilerin hedef e-posta sistemleri tarafından güvenilir olduğundan emin olmak için DomainKeys Identified Mail'i (DKIM) Microsoft 365 kullanmayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 87f565d5058edff9ebde5af6e2cf84ca3e8262b4
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772160"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM'yi kullanma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Bu makalede, hedef e-posta sistemlerinin özel etki alanınızdan giden gönderilen iletilere güvendiğinden emin olmak için Microsoft 365 ile DomainKeys Identified Mail (DKIM) kullanma adımları listeleniyor.

Bu makalede:

- [Kötü amaçlı kimlik sahtekarlıklarını önlemek için DKIM yalnızca SPF'den daha iyi nasıl çalışır?](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Microsoft 365 Defender portalından DKIM oluşturma, etkinleştirme ve devre dışı bırakma adımları](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [1024 bit anahtarlarınızı 2048 bit DKIM şifreleme anahtarlarına el ile yükseltme adımları](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [DKIM'i el ile ayarlama adımları](#steps-to-manually-set-up-dkim)
- [DKIM'i birden fazla özel etki alanı için yapılandırma adımları](#to-configure-dkim-for-more-than-one-custom-domain)
- [Özel etki alanı için DKIM imzalama ilkesini devre dışı bırakma](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [DKIM ve Microsoft 365 için varsayılan davranış](#default-behavior-for-dkim-and-microsoft-365)
- [DKIM'i, üçüncü taraf bir hizmetin özel etki alanınız adına e-posta gönderebilmesi veya yanıltabilmesi için ayarlayın](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Sonraki adımlar: Microsoft 365 için DKIM'i ayarladıktan sonra](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365, ilk 'onmicrosoft.com' etki alanları için DKIM'i otomatik olarak ayarlar. Bu, herhangi bir ilk etki alanı adı (örneğin, litware.onmicrosoft.com) için DKIM ayarlamak için hiçbir şey yapmanız gerekmeyecek anlamına gelir. Etki alanları hakkında daha fazla bilgi için bkz [. Etki Alanları SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM, saldırganların etki alanınızdan gelmiş gibi görünen iletiler göndermesini önlemeye yardımcı olan Kimlik Doğrulama yöntemlerinin (SPF, DKIM ve DMARC) üçlülerinden biridir.

DKIM, ileti üst bilgisindeki giden e-posta iletilerine dijital imza eklemenize olanak tanır. DKIM'yi yapılandırırken, etki alanınızı şifreleme kimlik doğrulaması kullanarak bir e-posta iletisiyle ilişkilendirme veya imzalama yetkisi alırsınız. Etki alanınızdan e-posta alan e-posta sistemleri, gelen e-postanın meşru olup olmadığını doğrulamaya yardımcı olmak için bu dijital imzayı kullanabilir.

Temel olarak, özel anahtar bir etki alanının giden e-postasında üst bilgiyi şifreler. Ortak anahtar etki alanının DNS kayıtlarında yayımlanır ve alıcı sunucular imzanın kodunu çözmek için bu anahtarı kullanabilir. DKIM doğrulaması, alıcı sunucuların postanın gerçekten etki alanınızdan geldiğini onaylamalarına yardımcı olur ve etki alanınızı *sahtekarlık eden* biri değil.

> [!TIP]
>Özel etki alanınız için DKIM hakkında hiçbir şey yapmamayı da seçebilirsiniz. Özel etki alanınız için DKIM'yi ayarlamazsanız Microsoft 365 özel ve ortak anahtar çifti oluşturur, DKIM imzalamayı etkinleştirir ve özel etki alanınız için varsayılan Microsoft 365 ilkesini yapılandırır.

 Microsoft-365'in yerleşik DKIM yapılandırması çoğu müşteri için yeterli kapsama alanıdır. Ancak, aşağıdaki durumlarda özel etki alanınız için DKIM'i el ile yapılandırmanız gerekir:

- Microsoft 365'de birden fazla özel etki alanınız var
- DMARC'yi de ayarlayacaksınız (**önerilir**)
- Özel anahtarınız üzerinde denetime sahip olmak istiyorsunuz
- CNAME kayıtlarınızı özelleştirmek istiyorsunuz
- Örneğin, üçüncü taraf toplu postacı kullanıyorsanız, üçüncü taraf etki alanı dışından gelen e-postalar için DKIM anahtarları ayarlamak istiyorsunuz.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Kötü amaçlı kimlik sahtekarlıklarını önlemek için DKIM yalnızca SPF'den daha iyi nasıl çalışır?
<a name="HowDKIMWorks"> </a>

SPF bir ileti zarfa bilgi ekler, ancak DKIM ileti üst bilgisindeki bir imzayı *şifreler* . bir iletiyi ilettiğiniz zaman, iletinin zarfının bazı kısımları iletilen sunucu tarafından kaldırılabilir. Dijital imza, e-posta üst bilgisinin bir parçası olduğu için e-posta iletisinde kaldığından, aşağıdaki örnekte gösterildiği gibi iletilse bile DKIM çalışır.

![SPF denetiminin başarısız olduğu DKIM kimlik doğrulamasını geçiren iletilen bir iletiyi gösteren diyagram.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

Bu örnekte, etki alanınız için yalnızca bir SPF TXT kaydı yayımladıysanız, alıcının posta sunucusu e-postanızı istenmeyen posta olarak işaretlemiş ve hatalı bir pozitif sonuç oluşturmuş olabilir. **Bu senaryoda DKIM eklenmesi *hatalı pozitif* istenmeyen posta raporlamasını azaltır.** DKIM yalnızca IP adreslerinin değil kimlik doğrulamasının ortak anahtar şifrelemesine bağlı olduğundan, DKIM SPF'den çok daha güçlü bir kimlik doğrulama biçimi olarak kabul edilir. Dağıtımınızda hem SPF hem de DKIM'nin yanı sıra DMARC kullanmanızı öneririz.

> [!TIP]
> DKIM, ileti üst bilgilerine şifreli imza eklemek için özel bir anahtar kullanır. İmzalama etki alanı veya giden etki alanı, üst bilgideki **d=** alanının değeri olarak eklenir. Doğrulayan etki alanı veya alıcının etki alanı, DNS'den ortak anahtarı aramak ve iletinin kimliğini doğrulamak için **d=** alanını kullanır. İleti doğrulanırsa, DKIM denetimi geçer.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalından DKIM oluşturma, etkinleştirme ve devre dışı bırakma adımları

Kiracınızın kabul edilen tüm etki alanları DKIM sayfasının altındaki Microsoft 365 Defender portalında gösterilir. Bunu görmüyorsanız, [etki alanları sayfasından](/microsoft-365/admin/setup/add-domain#add-a-domain) kabul edilen etki alanınızı ekleyin.
Etki alanınız eklendikten sonra, DKIM'i yapılandırmak için aşağıda gösterildiği gibi adımları izleyin.

1. Adım: DKIM sayfasında (https://security.microsoft.com/dkimv2 veya https://protection.office.com/dkimv2)) DKIM'i yapılandırmak istediğiniz etki alanına tıklayın.

:::image type="content" source="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png" alt-text="Microsoft 365 Defender portalında etki alanının seçili olduğu DKIM sayfası" lightbox="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png":::

2. Adım: İki durumlu düğmeyi **Etkinleştir'e** kaydırın. CNAME kayıtlarını eklemeniz gerektiğini belirten bir açılır pencere görürsünüz.

:::image type="content" source="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png" alt-text="DKIM anahtarları oluştur düğmesiyle Etki alanı ayrıntıları açılır öğesi" lightbox="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png":::

3. Adım: Açılan pencerede gösterilen CNAMES'yi kopyalayın

:::image type="content" source="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png" alt-text="Kopyalanacak iki CNAME kaydını içeren CNAMEs Yayımla açılır penceresi" lightbox="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png":::

4. Adım: Kopyalanan CNAME kayıtlarını DNS hizmet sağlayıcınızda yayımlayın.

DNS sağlayıcınızın web sitesinde, etkinleştirmek istediğiniz DKIM için CNAME kayıtları ekleyin. Her birinde alanların aşağıdaki değerlere ayarlandığından emin olun:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

5. Adım: DKIM'i etkinleştirmek için DKIM sayfasına dönün.

:::image type="content" source="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png" alt-text="DKIM'yi etkinleştirme iki durumlu düğmesi" lightbox="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png":::

CNAME kaydı yok hatası görürseniz, bunun nedeni şu olabilir:

1. Dns sunucusuyla eşitleme( sorun devam ederse birkaç saniye ile saat arasında sürebilir) adımları tekrarlayın
2. Ek alan veya sekmeler gibi kopyalama yapıştırma hatalarını denetleyin.

DKIM'i devre dışı bırakmak istiyorsanız yeniden devre dışı bırakma moduna geçin

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>1024 bit anahtarlarınızı 2048 bit DKIM şifreleme anahtarlarına el ile yükseltme adımları
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 *onmicrosoft.com* etki alanları için DKIM'i otomatik olarak ayarlar. Herhangi bir ilk etki alanı adı için (litware gibi) DKIM kullanmak için hiçbir adıma gerek yoktur.*onmicrosoft.com*). Etki alanları hakkında daha fazla bilgi için bkz [. Etki Alanları SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM anahtarları için hem 1024 hem de 2048 bitlik değerler desteklendiği için, bu yönergeler [powershell'de](/powershell/exchange/connect-to-exchange-online-powershell) 1024 bit anahtarınızı 2048'e yükseltmeyi Exchange Online. Aşağıdaki adımlar iki kullanım örneğine yöneliktir. Lütfen yapılandırmanıza en uygun olanı seçin.

- **DKIM zaten yapılandırılmışsa**, aşağıdaki komutu çalıştırarak bitlik değerini döndürürsiniz:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **Veya**

- **DKIM'in yeni bir uygulaması** için aşağıdaki komutu çalıştırın:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Aşağıdaki komutu çalıştırarak yapılandırmayı *doğrulamak* için Exchange Online PowerShell'e bağlı kalın:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Bu yeni 2048 bit anahtar RotateOnDate üzerinde etkili olur ve arada 1024 bit anahtarla e-postalar gönderir. Dört gün sonra, 2048 bit anahtarla (yani, döndürme ikinci seçiciye etkili olduktan sonra) yeniden test edebilirsiniz.

Dört gün sonra ikinci seçiciye döndürmek ve 2048 bitlik kullanımda olduğunu onaylamak istiyorsanız, yukarıda listelenen uygun cmdlet'i kullanarak ikinci seçici anahtarını el ile döndürün.

Ayrıntılı söz dizimi ve parametre bilgileri için şu makalelere bakın: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) ve [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>DKIM'i el ile ayarlama adımları
<a name="SetUpDKIMO365"> </a>

DKIM'i yapılandırmak için şu adımları tamamlayacağız:

- [DNS'de özel etki alanınız için iki CNAME kaydı yayımlama](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Özel etki alanınız için DKIM imzalamayı etkinleştirme](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>DNS'de özel etki alanınız için iki CNAME kaydı yayımlama
<a name="Publish2CNAME"> </a>

DNS'de DKIM imzası eklemek istediğiniz her etki alanı için iki CNAME kaydı yayımlamanız gerekir.

> [!NOTE]
> Makalenin tamamını okumadıysanız bu zaman kazandıran PowerShell bağlantı bilgilerini kaçırmış olabilirsiniz: [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

Seçici kayıtlarını oluşturmak için Exchange Online PowerShell'de aşağıdaki komutları çalıştırın:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Microsoft 365'da ilk etki alanına ek olarak özel etki alanları sağladıysanız, her ek etki alanı için iki CNAME kaydı yayımlamanız gerekir. Bu nedenle, iki etki alanınız varsa, iki ek CNAME kaydı yayımlamanız gerekir ve bu şekilde devam eder.

CNAME kayıtları için aşağıdaki biçimi kullanın.

> [!IMPORTANT]
> GCC High müşterilerimizden biriyseniz _customDomainIdentifier'ı_ farklı hesaplayacağız! _customDomainIdentifier_ değerini hesaplamak için _initialDomain'inizin_ MX kaydını aramak yerine doğrudan özelleştirilmiş etki alanından hesaplıyoruz. Örneğin, özelleştirilmiş etki alanınız "contoso.com" ise _customDomainIdentifier'ınız_ "contoso-com" olur, tüm noktalarda tire kullanılır. Bu nedenle, _initialDomain'inizin_ hangi MX kaydını gösterdiğinden bağımsız olarak, CNAME kayıtlarınızda kullanılacak _customDomainIdentifier_ değerini hesaplamak için her zaman yukarıdaki yöntemi kullanırsınız.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Konum:

- Microsoft 365 için seçiciler her zaman "seçici1" veya "seçici2" olur.
- _customDomainIdentifier_ , mail.protection.outlook.com önce görüntülenen özel etki alanınız için özelleştirilmiş MX kaydındaki _customDomainIdentifier_ ile aynıdır. Örneğin, etki alanı contoso.com için aşağıdaki MX kaydında _customDomainIdentifier_ contoso-com şeklindedir:

  > contoso.com.  3600 IN MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain_, Microsoft 365 kaydolduğunda kullandığınız etki alanıdır. İlk etki alanları her zaman onmicrosoft.com biter. İlk etki alanınızı belirleme hakkında bilgi için bkz [. Etki Alanları SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Örneğin, cohovineyardandwinery.onmicrosoft.com ilk etki alanınız ve cohovineyard.com ve cohowinery.com iki özel etki alanınız varsa, her ek etki alanı için toplam dört CNAME kaydı için iki CNAME kaydı ayarlamanız gerekir.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector1._domainkey
Points to address or value:    selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

> [!NOTE]
> İkinci kaydı oluşturmak önemlidir, ancak oluşturma sırasında seçicilerden yalnızca biri kullanılabilir. Temelde, ikinci seçici henüz oluşturulmamış bir adrese işaret edebilir. Anahtar döndürme işleminiz sorunsuz olacağı için ikinci CNAME kaydını yine de oluşturmanızı öneririz.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Özel etki alanınız için DKIM imzalamayı etkinleştirme adımları
<a name="EnableDKIMinO365"> </a>

CNAME kayıtlarını DNS'de yayımladıktan sonra, Microsoft 365 aracılığıyla DKIM imzalamayı etkinleştirmeye hazır olursunuz. Bunu Microsoft 365 yönetim merkezi aracılığıyla veya PowerShell kullanarak yapabilirsiniz.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında özel etki alanınız için DKIM imzalamayı etkinleştirmek için

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **DKIM'e** gidin. Doğrudan DKIM sayfasına gitmek için kullanın <https://security.microsoft.com/dkimv2>.

2. **DKIM** sayfasında, ada tıklayarak etki alanını seçin.

3. Görüntülenen ayrıntılar açılır penceresinde **DKIM imzalarıyla bu etki alanı için iletileri imzala** ayarını **Etkin** (![Açık) olarak değiştirin.](../../media/scc-toggle-on.png)

   İşiniz bittiğinde **DKIM tuşlarını döndür'e** tıklayın.

4. Her özel etki alanı için bu adımı yineleyin.

5. DKIM'i ilk kez yapılandırıyorsanız ve 'Bu etki alanı için DKIM anahtarı kaydedilmedi' hatasını görüyorsanız, sonraki adımda açıklandığı gibi DKIM imzalamayı etkinleştirmek için Windows PowerShell kullanmanız gerekir.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>PowerShell kullanarak özel etki alanınız için DKIM imzalamayı etkinleştirmek için

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Bu etki alanı için kaydedilmiş DKIM anahtarı yok hatası" lightbox="../../media/dkim.png":::
> DKIM'i ilk kez yapılandırıyorsanız ve 'Bu etki alanı için DKIM anahtarı kaydedilmedi' hatasını görüyorsanız, anahtarı görmek için aşağıdaki 2. adımda (örneğin, `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`) komutu tamamlayın.

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> , DKIM imzalamasını etkinleştirmek istediğiniz özel etki alanının adıdır.

   Bu örnek, etki alanı contoso.com için DKIM imzalamasını etkinleştirir:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>DKIM imzalamanın Microsoft 365 için düzgün yapılandırıldığını onaylamak için

DKIM'i doğru yapılandırdığınızdan emin olmak için bu adımları izlemeden önce birkaç dakika bekleyin. Bu, etki alanı hakkındaki DKIM bilgilerinin ağa yayılmasına izin verir.

- Microsoft 365 DKIM özellikli etki alanınızdaki bir hesaptan outlook.com veya Hotmail.com gibi başka bir e-posta hesabına ileti gönderin.
- Test amacıyla aol.com hesabı kullanmayın. AOL, SPF denetiminin geçip geçmediğini DKIM denetimini atlayabilir. Bu, testinizi geçersiz hale getirecektir.
- İletiyi açın ve üst bilgisine bakın. İletinin üst bilgisini görüntüleme yönergeleri, mesajlaşma istemcinize bağlı olarak değişir. Outlook'da ileti üst bilgilerini görüntüleme yönergeleri için bkz. [Outlook'de internet iletisi üst bilgilerini görüntüleme](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  DKIM imzalı ileti, CNAME girdilerini yayımladığınızda tanımladığınız ana bilgisayar adını ve etki alanını içerir. İleti şu örneğe benzer olacaktır:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Authentication-Results üst bilgisini arayın. Her alıcı hizmet, gelen postayı damgalamak için biraz farklı bir biçim kullansa da, sonuç **DKIM=pass** veya **DKIM=Ok** gibi bir değer içermelidir.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>DKIM'i birden fazla özel etki alanı için yapılandırmak için
<a name="DKIMMultiDomain"> </a>

Gelecekte başka bir özel etki alanı eklemeye karar verirseniz ve yeni etki alanı için DKIM'yi etkinleştirmek istiyorsanız, her etki alanı için bu makaledeki adımları tamamlamanız gerekir. Özellikle, [DKIM'i el ile ayarlamak için yapmanız gerekenler'deki](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365) tüm adımları tamamlayın.

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Özel etki alanı için DKIM imzalama ilkesini devre dışı bırakma
<a name="DisableDKIMSigningPolicy"> </a>

İmzalama ilkesinin devre dışı bırakılması DKIM'ı tamamen devre dışı bırakmaz. Bir süre sonra, varsayılan ilke hala etkin durumdaysa Microsoft 365 etki alanınız için varsayılan ilkeyi otomatik olarak uygular. DKIM'i tamamen devre dışı bırakmak istiyorsanız, DKIM'i hem özel hem de varsayılan etki alanlarında devre dışı bırakmanız gerekir. Daha fazla bilgi için bkz. [DKIM ve Microsoft 365 için varsayılan davranış](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Windows PowerShell kullanarak DKIM imzalama ilkesini devre dışı bırakmak için

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

2. DKIM imzalamasını devre dışı bırakmak istediğiniz her etki alanı için aşağıdaki komutlardan birini çalıştırın.

   ```powershell
   $p = Get-DkimSigningConfig -Identity <Domain>
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Örneğin:

   ```powershell
   $p = Get-DkimSigningConfig -Identity contoso.com
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Veya

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   Burada _sayı_ , ilkenin dizinidir. Örneğin:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>DKIM ve Microsoft 365 için varsayılan davranış
<a name="DefaultDKIMbehavior"> </a>

DKIM'yi etkinleştirmezseniz Microsoft 365 Microsoft Çevrimiçi E-posta Yönlendirme Adresiniz (MOERA)/ilk etki alanınız ve veri merkezimizde dahili olarak depoladığımız ilişkili özel anahtar için otomatik olarak 2048 bit DKIM ortak anahtarı oluşturur. varsayılan olarak, Microsoft 365 ilkeye sahip olmayan etki alanları için varsayılan imzalama yapılandırmasını kullanır. Başka bir deyişle, DKIM'i kendiniz ayarlamazsanız, Microsoft 365 etki alanınız için DKIM'yi etkinleştirmek için varsayılan ilkesini ve oluşturduğu anahtarları kullanır.

Ayrıca, DKIM'i etkinleştirdikten sonra özel etki alanınızda oturum açmayı devre dışı bırakırsanız, belirli bir süre sonra Microsoft 365 özel etki alanınız için MOERA/ilk etki alanı ilkesini otomatik olarak uygular.

Aşağıdaki örnekte, fabrikam.com için DKIM'in etki alanının yöneticisi tarafından değil Microsoft 365 tarafından etkinleştirildiğini varsayalım. Bu, gerekli CNAM'lerin DNS'de mevcut olmadığı anlamına gelir. Bu etki alanından gelen e-postalar için DKIM imzaları şuna benzer olacaktır:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

Bu örnekte ana bilgisayar adı ve etki alanı, fabrikam.com için DKIM imzalaması etki alanı yöneticisi tarafından etkinleştirildiyse CNAME'nin işaret edeceği değerleri içerir. Sonunda, Microsoft 365 gönderilen her ileti DKIM imzalı olur. DKIM'i kendiniz etkinleştirirseniz, etki alanı Kimden: adresindeki etki alanıyla aynı olur ve bu durumda fabrikam.com. Bunu yapmazsanız uyumlu olmaz ve bunun yerine kuruluşunuzun ilk etki alanını kullanır. İlk etki alanınızı belirleme hakkında bilgi için bkz [. Etki Alanları SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>DKIM'i, üçüncü taraf bir hizmetin özel etki alanınız adına e-posta gönderebilmesi veya yanıltabilmesi için ayarlayın
<a name="SetUp3rdPartyspoof"> </a>

Bazı toplu e-posta hizmet sağlayıcıları veya hizmet olarak yazılım sağlayıcıları, hizmetlerinden kaynaklanan e-postalar için DKIM anahtarlarını ayarlamanıza olanak sağlar. Bu, gerekli DNS kayıtlarını ayarlamak için kendinizle üçüncü taraf arasında koordinasyon gerektirir. Bazı üçüncü taraf sunucuların farklı seçicilere sahip kendi CNAME kayıtları olabilir. Hiçbir kuruluş bunu tam olarak aynı şekilde yapmaz. Bunun yerine, süreç tamamen kuruluşa bağlıdır.

contoso.com ve bulkemailprovider.com için düzgün yapılandırılmış bir DKIM'yi gösteren örnek ileti şöyle görünebilir:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

Bu örnekte, bu sonucu elde etmek için:

1. Toplu E-posta Sağlayıcısı Contoso'ya genel bir DKIM anahtarı verdi.

2. Contoso, DNS kaydında DKIM anahtarını yayımladı.

3. E-posta gönderirken Toplu E-posta Sağlayıcısı anahtarı ilgili özel anahtarla imzalar. Bunu yaptığınızda Toplu E-posta Sağlayıcısı DKIM imzasını ileti üst bilgisine eklemiş olur.

4. Alıcı e-posta sistemleri, iletinin Kimden: (5322.Kimden) adresindeki etki alanında DKIM-Signature d=\<domain\> değerini doğrulayarak bir DKIM denetimi gerçekleştirir. Bu örnekte değerler şu şekildedir:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>E-posta göndermeyen etki alanlarını belirleme

Bir etki alanı, bu etki alanları için DKIM kaydında belirterek `v=DKIM1; p=` e-posta göndermezse kuruluşlar açıkça belirtmelidir. Bu, e-posta sunucularının etki alanı için geçerli ortak anahtar olmadığını ve bu etki alanından olduğunu iddia eden tüm e-postaların reddedilmesi gerektiğini önerir. Bunu her etki alanı ve alt etki alanı için joker karakter DKIM kullanarak yapmalısınız.

Örneğin, DKIM kaydı şöyle görünür:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Sonraki adımlar: Microsoft 365 için DKIM'i ayarladıktan sonra
<a name="DKIMNextSteps"> </a>

**DKIM kimlik sahtekarlığı önlemeye yardımcı olmak için tasarlanmış olsa da, DKIM SPF ve DMARC ile daha iyi çalışır.**

DKIM'i ayarladıktan sonra SPF'yi henüz ayarlamadıysanız bunu yapmanız gerekir. SPF'ye hızlı bir giriş yapmak ve hızla yapılandırılmasını sağlamak için, kimlik [**sahtekarlıklarını önlemeye yardımcı olmak için bkz. Microsoft 365'de SPF'yi ayarlama**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Microsoft 365 SPF'yi nasıl kullandığını daha ayrıntılı bir şekilde anlamak veya karma dağıtımlar gibi sorun giderme veya standart olmayan dağıtımlar için Microsoft 365 [sahtekarlık önlemek için Sender Policy Framework'ün (SPF) nasıl kullanıldığı](how-office-365-uses-spf-to-prevent-spoofing.md) ile başlayın.

Ardından bkz. [**E-postayı doğrulamak için DMARC kullanma**](use-dmarc-to-validate-email.md). [İstenmeyen postadan koruma iletisi üst bilgileri](anti-spam-message-headers.md), DKIM denetimleri için Microsoft 365 tarafından kullanılan söz dizimi ve üst bilgi alanlarını içerir.

**Bu test** , DKIM imzalama yapılandırmasının doğru yapılandırıldığını ve uygun DNS girişlerinin yayımlandığını doğrular.

> [!NOTE]
> Bu özellik, bir Microsoft 365 yönetici hesabı gerektirir. Bu özellik, Microsoft 365 Government, 21Vianet tarafından yürütülen Microsoft 365 veya Microsoft 365 Almanya'da kullanılamaz.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Testleri Çalıştırma: DKIM</a></p>
</div>

## <a name="more-information"></a>Daha fazla bilgi

PowerShell aracılığıyla anahtar döndürme: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[E-postayı doğrulamak için DMARC kullanma](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?view=o365-worldwide&preserve-view=true)

[Güvenilir ARC Gönderenleri'ni geçerli posta akışları için kullanma](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)