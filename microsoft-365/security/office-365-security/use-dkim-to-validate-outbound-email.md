---
title: DkIM'i özel etki alanınız içinde e-posta için kullanma
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
description: Özel etki alanınız üzerinden gönderilen iletilerin hedef e-posta sistemleri tarafından güveni sağ Microsoft 365 etki alanıyla birlikte DomainKeys Identified Mail (DKIM) kullanmayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25333a1616bb1f4e4e529c17813bdd58f4c768b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312957"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Bu makalede, hedef e-posta sistemlerinin özel etki alanınız üzerinden giden iletilere güven güveni sağlamak için, etki alanıyla birlikte DomainKeys Identified Mail (DKIM Microsoft 365) kullanma adımları listelemektedir.

Bu makalede:

- [Kötü amaçlı birpoofing önlemek için DKIM tek başına SPF'den daha iyi nasıl çalışır?](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Portalda DKIM oluşturma, etkinleştirme ve devre dışı Microsoft 365 Defender adımları](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [1024 bit anahtarlarınızı 2048 bit DKIM şifreleme tuşlarına el ile yükseltme adımları](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [DKIM'i el ile ayarlama adımları](#steps-to-manually-set-up-dkim)
- [Birden fazla özel etki alanı için DKIM'yi yapılandırma adımları](#to-configure-dkim-for-more-than-one-custom-domain)
- [Özel bir etki alanı için DKIM imzalama ilkesi devre dışı bırakma](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [DKIM ve Microsoft 365 için varsayılan davranış](#default-behavior-for-dkim-and-microsoft-365)
- [DkIM'i, üçüncü taraf bir hizmetin özel etki alanınız adına e-posta gönderebi veya e-posta gönder yetkisine sahip olacak şekilde ayarlama](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Sonraki adımlar: DkIM for Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 'otomatik olarak' alan adları için DKIM'onmicrosoft.com ayarlar. Bu, DKIM'i ilk etki alanı adlar için ayarlamak için bir şey (örneğin, DkIM) bir şey litware.onmicrosoft.com. Etki alanları hakkında daha fazla bilgi için bkz. Etki Alanları [SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM, kimlik doğrulama yöntemlerinin (SPF, DKIM ve DMARC) bir diğer yöntemdir ve saldırganların etki alanınız üzerinden geliyor gibi gelen iletiler göndermesini önlemeye yardımcı olur.

DKIM, ileti üst bilgisinde giden e-posta iletilerine dijital imza eklemenize olanak sağlar. DKIM'yi yapılandırarak, etki alanınızı şifreleme kimlik doğrulaması kullanarak bir e-posta iletisiyle ilişkilendirmek veya imzalamak üzere yetkilendirin. Etki alanınıza e-posta alan e-posta sistemleri, gelen e-postanın meşru olup olmadığını doğrulamaya yardımcı olmak için bu dijital imzayı kullanabilir.

Temel olarak, özel anahtar etki alanının giden e-postasndaki üst bilgiyi şifreler. Ortak anahtar etki alanının DNS kayıtlarında yayımlanır ve alıcı sunucular bu anahtarı kullanarak imzanın kodunu çözebilirsiniz. DKIM doğrulama, alıcı sunucuların e-postanın gerçekten etki alanınıza geldiğini doğrulamasına ve etki alanınıza kimlik doğrulaması eden birinin değil, gerçekten *etki alanınıza geldiğini doğrulamasına* yardımcı olur.

> [!TIP]
>DkIM hakkında özel etki alanınız için de hiçbir şey yapmaya seçebilirsiniz. Özel etki alanınız için DKIM'yi ayarlamazsanız, Microsoft 365 özel ve ortak anahtar çifti oluşturur, DKIM imzalamasını etkinleştirir ve özel Microsoft 365 alanınız için varsayılan ilkeyi yapılandırr.

 Microsoft-365'in yerleşik DKIM yapılandırması çoğu müşteri için yeterli kapsamdadır. Bununla birlikte, aşağıdaki durumlarda özel etki alanınız için DKIM'yi el ile yapılandırmanız gerekir:

- Microsoft 365'da birden fazla özel etki Microsoft 365
- DMARC'ı da kuracaksiniz (**önerilir**)
- Özel anahtarınızı kontrol etmek istiyor
- CNAME kayıtlarınızı özelleştirmek istiyorum
- Örneğin üçüncü taraf bir toplu postacı kullanıyorsanız, üçüncü taraf bir etki alanından kaynaklanan e-posta için DKIM anahtarlarını ayarlamak istiyor olun.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Kötü amaçlı birpoofing önlemek için DKIM tek başına SPF'den daha iyi nasıl çalışır?
<a name="HowDKIMWorks"> </a>

SPF ileti zarfına bilgi ekler, ancak DKIM *ileti* üst bilgisinde imzayı şifreler. bir iletiyi ileterek, bu iletinin zarfın bir bölümü iletme sunucusu tarafından silinerek çıkarabilirsiniz. Dijital imza e-posta iletisinin bir parçası olduğundan ve e-posta üst bilgisinde olduğu için DKIM, aşağıdaki örnekte gösterildiği gibi bir ileti ilet olsa bile çalışır.

![SPF denetimi başarısız olduğunda DKIM kimlik doğrulamasını geçen bir ileti gösteren diyagram.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

Bu örnekte, etki alanınız için yalnızca bir SPF TXT kaydı yayımladıysanız, alıcının posta sunucusu e-postanızı istenmeyen posta olarak işaretlemış ve hatalı bir pozitif sonuç oluşturmış olabilir. **Bu senaryoda DKIM eklemesi hatalı pozitif istenmeyen *posta raporlamasını* azaltır.** DKIM, yalnızca IP adreslerini değil, ortak anahtar şifrelemesini temel kullandığından, DKIM SPF'ye göre çok daha güçlü bir kimlik doğrulama biçimi olarak kabul edilir. Dağıtımda hem SPF hem de DKIM'nin yanı sıra DMARC'yi de öneririz.

> [!TIP]
> DKIM, ileti üst bilgilerine şifreli bir imza eklemek için özel anahtar kullanır. İmzalayan etki alanı veya giden etki alanı, üst bilgide **d=** alanının değeri olarak eklenir. Etki alanını veya alıcının etki alanını doğrulamak, ardından **d=** alanını kullanarak DNS'den ortak anahtarı görüntüler ve iletiyi doğrular. İleti doğrulandığında DKIM denetimi geçer.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Portalda DKIM oluşturma, etkinleştirme ve devre dışı Microsoft 365 Defender adımları

Kiracının tüm kabul edilen etki alanları, DKIM Microsoft 365 Defender kiracı portalında gösterilir. Bunu görmüyorsanız, etki alanları sayfasından kabul edilen etki [alanınızı ekleyin](/microsoft-365/admin/setup/add-domain#add-a-domain).
DkIM'yi yapılandırmak için etki alanınız eklendiktan sonra aşağıdaki adımları izleyin.

1. Adım: DKIM sayfasında DKIM'yi yapılandırmak istediğiniz etki alanına tıklayın ( veyahttps://security.microsoft.com/dkimv2 https://protection.office.com/dkimv2).

![Seçilen bir etki alanıyla Microsoft 365 Defender portalında DKIM sayfası.](../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png)

2. Adım: Iki durumlu düğmeyi Etkinleştir'e **kaydırın**. CNAME kayıtlarını eklemenizi belirten bir açılır pencere görüntülenir.

![DKIM'yi etkinleştirmek için iki durumlu düğmeyi Etkin'e kaydırın.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

3. Adım: Açılan pencerede gösterilen CNAMES'i kopyalama

4. Adım: Kopyalanan CNAME kayıtlarını DNS hizmet sağlayıcınızda yayımlayın.

DNS sağlayıcınızın web sitesinde, etkinleştirmek istediğiniz DKIM için CNAME kayıtlarını ekleyin. Alanların her biri için aşağıdaki değerlere ayarlanmış olduğundan emin olun:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

5. Adım: DKIM'yi etkinleştirmek için DKIM sayfasına geri dönme.

![DKIM'yi etkinleştirmek için iki durumlu düğmeyi Etkin'e kaydırın.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

CNAME kaydı yok hatası görüyorsanız, bunun nedeni şu olabilir:

1. DNS sunucusuyla eşitleme, sorun devam ederse birkaç saniyeyle saat arasında sürebilir ve sorun tekrarlayın
2. Ek boşluk veya sekme gibi kopyalama yapıştırma hatalarını denetleyin.

DKIM'yi devre dışı bırakmak isterseniz, devre dışı bırakma moduna geri dönebilirsiniz

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>1024 bit anahtarlarınızı 2048 bit DKIM şifreleme tuşlarına el ile yükseltme adımları
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 etki alanları için *DKIM'onmicrosoft.com* ayarlar. BAŞLANGıÇTAki etki alanı adlardan (litware gibi) DKIM'i kullanmak için hiçbir adım gerekmez.*onmicrosoft.com*). Etki alanları hakkında daha fazla bilgi için bkz. Etki Alanları [SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM tuşları hem 1024 hem de 2048 bit olarak desteklensin, bu yol tarifleri size Exchange Online PowerShell'de 1024 bit anahtarınızı [2048'e nasıl yükselteceklerini açıklar](/powershell/exchange/connect-to-exchange-online-powershell). Aşağıdaki adımlar iki kullanım sorunu için, lütfen yapılandırmanıza en uygun olanı seçin.

- DKIM **yapılandırıldığında, bitliğini** döndürmek için aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **veya**

- **DKIM'nin yeni uygulanması** için aşağıdaki komutu çalıştırın:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Aşağıdaki komutu çalıştırarak Exchange Online *doğrulamak için* PowerShell ile bağlantıda kalın:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Bu yeni 2048 bit anahtar RotateOnDate üzerinde etkili olur ve arada 1024 bit tuşu olan e-postalar gönderir. Dört gün sonra, 2048 bit tuşuyla yeniden test etmek için (yani, döndürme ikinci seçiciye bir kez) sınr.

İkinci seçiciye döndürmek için, dört gün sonra 2048 bitlik olduğunu onaylamak için, yukarıda listelenen uygun cmdlet'i kullanarak ikinci seçici anahtarını el ile döndürün.

Ayrıntılı söz dizimi ve parametre bilgileri için şu makalelere [bakın: Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) ve [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>DKIM'i el ile ayarlama adımları
<a name="SetUpDKIMO365"> </a>

DKIM'yi yapılandırmak için şu adımları tamamlayabilirsiniz:

- [DNS'de özel etki alanınız için iki CNAME kaydı yayımlama](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Özel etki alanınız için DKIM imzalamayı etkinleştirme](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>DNS'de özel etki alanınız için iki CNAME kaydı yayımlama
<a name="Publish2CNAME"> </a>

DNS'de DKIM imzasını eklemek istediğiniz her etki alanı için iki CNAME kaydı yayımlamanız gerekir.

> [!NOTE]
> Makalenin tamamını okumadıysanız, bu zaman tasarrufu sağlayan PowerShell bağlantı bilgilerini atlemiş Bağlan [PowerShell'Exchange Online olabilir](/powershell/exchange/connect-to-exchange-online-powershell).

Seçici kayıtlarını oluşturmak için Exchange Online PowerShell'de şu komutları çalıştırın:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Microsoft 365'de ilk etki alanına ek olarak özel etki alanları da sağdıysanız, her ek etki alanı için iki CNAME kaydı yayımlamanız gerekir. Dolayısıyla, iki etki alanınız varsa, iki CNAME kaydı daha yayımlamanız gerekir.

CNAME kayıtları için aşağıdaki biçimi kullanın.

> [!IMPORTANT]
> GCC High müşterilerinden biriysanız, _customDomainIdentifier değerini farklı hesaplarız_! _CustomDomainIdentifier_ değerini hesaplamak üzere ilk  Etki Alanınız için MX kaydına bakmanız yerine, bunu doğrudan özelleştirilmiş etki alanı üzerinden hesaplarız. Örneğin, özelleştirilmiş etki alanınız "contoso.com" ise _, customDomainIdentifier_ "contoso-com" olur, tüm dönemler kısa çizgiyle değiştirilir. Dolayısıyla, başlangıçtaki Etki Alanı'nın _hangi_ MX kaydına bakılmaksızın, CNAME kayıtlarında kullanmak üzere _özelDomainIdentifier_ değerini hesaplamak için her zaman yukarıdaki yöntemi kullanırsınız.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Burada:

- Daha Microsoft 365 için, seçiciler her zaman "seçici1" veya "seçici2" olur.
- _customDomainIdentifier_ , özel etki alanınız için özel etki alanınız için özelleştirilmiş MX kaydında görüntülenen _customDomainIdentifier_ ile mail.protection.outlook.com. Örneğin, etki alanı kimliği için aşağıdaki MX kaydında contoso.com _DomainIdentifier_ contoso-com'dur:

  > contoso.com.  MX 5'TE 3600 contoso-com.mail.protection.outlook.com

- _initialDomain_, etki alanına kayıt olurken kullanılan Microsoft 365. İlk etki alanları her zaman en onmicrosoft.com. İlk etki alanınızı belirleme hakkında bilgi için bkz. Etki Alanları [SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Örneğin, cohovineyardandwinery.onmicrosoft.com'in ilk etki alanı ve cohovineyard.com ile cohowinery.com olmak üzere iki özel etki alanınız varsa, ek her etki alanı için toplam dört CNAME kaydı için iki CNAME kaydı ayarlamanız gerekir.

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
> İkinci kaydı oluşturmak önemlidir, ancak oluşturma sırasında bu kayıtlardan yalnızca biri kullanılabilir. Öz olarak, ikinci seçici henüz oluşturulmamış bir adresi işaret edeyor olabilir. Tuş döndürme deneyiminiz sorunsuz olduğundan ikinci CNAME kaydını oluşturmanızı öneririz.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Özel etki alanınız için DKIM imzalamayı etkinleştirme adımları
<a name="EnableDKIMinO365"> </a>

DNS'de CNAME kayıtlarını yayımladıktan sonra, KAYıTlarda DKIM imzalamayı etkinleştirmeye Microsoft 365. Bunu yapmak için Microsoft 365 yönetim merkezi PowerShell'i de kullanabilirsiniz.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Yeni portalda özel etki alanınız için DKIM Microsoft 365 Defender etkinleştirmek için

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, Kurallar bölümünde, **E-posta &** \> İşbirliği **& Kurallar** \>  \> tehdit ilkeleri **DKIM'ye** gidin. Doğrudan DKIM sayfasına gitmek için, kullanın <https://security.microsoft.com/dkimv2>.

2. **DKIM sayfasında**, adına tıklayarak etki alanını seçin.

3. Görüntülenen ayrıntılar açılır iletisinde, **DKIM** imzaları ile bu etki alanı için iletileri imzala ayarını **Etkin olarak değiştir** (![Açık olarak değiştir.](../../media/scc-toggle-on.png))

   Bitirdikten sonra **DKIM tuşlarını döndür'e tıklayın**.

4. Her özel etki alanı için bu adımı yineler.

5. DKIM'yi ilk kez yapılandırıyorsanız ve 'Bu etki alanı için hiçbir DKIM anahtarı kaydedilemiyor' hatasını görüyorsanız, bir sonraki adımda anlatımlı olarak DKIM imzalamayı etkinleştirmek için DKIM Windows PowerShell'ı kullanabilirsiniz.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>PowerShell kullanarak özel etki alanınız için DKIM imzalamasını etkinleştirmek için

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="'Bu etki alanı için hiçbir DKIM anahtarı kaydedilemiyor.' hatası.":::
> DKIM'i ilk kez yapılandırıyorsanız ve anahtarı görmek için aşağıdaki 2. adımda (örneğin, `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`) 'Bu etki alanı için kayıtlı DKIM anahtarı yok' hatasını görüyorsanız.

1. [Bağlan PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> DKIM imzalamasını etkinleştirmek istediğiniz özel etki alanının adıdır.

   Bu örnekte, etki alanı için DKIM imzalama özelliği contoso.com:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>DKIM imzalamanın ekip için düzgün yapılandırıldığından emin Microsoft 365

DKIM'yi düzgün şekilde yapılandırmış olduğunu onaylamak için bu adımları izlemeden önce birkaç dakika bekleyin. Bu işlem DKIM bilgileri için etki alanıyla ilgili bilgilerin ağa yayılmasına olanak sağlar.

- DKIM destekli etki alanınız içindeki bir hesaptan, Microsoft 365 outlook.com veya hesap gibi başka bir e-posta hesabına Hotmail.com.
- Test aol.com bir hesap kullanmayın. SPF denetimi geçtikten sonra AOL DKIM denetimi atlar. Bu, testini geçersiz kılınacak.
- İletiyi açın ve üst bilgiye bakın. İletinin üst bilgilerini görüntüleme yönergeleri, ileti istemcinize bağlı olarak değişir. E-postada ileti üst bilgilerini görüntüleme Outlook için bkz[. E-postada internet iletisi üstbilgilerini Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  DKIM imzalı ileti, CNAME girdilerini yayımlarken tanımlandığı ana bilgisayar adını ve etki alanını içerir. İleti aşağıdakine benzer şekilde olur:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Üst bilgi Authentication-Results bakın. Her alıcı hizmeti gelen postayı damgak için biraz farklı bir biçim kullanır ama sonuçta **DKIM=pass** veya **DKIM=OK gibi bir şey olmalıdır**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>DKIM'yi birden fazla özel etki alanında yapılandırmak için
<a name="DKIMMultiDomain"> </a>

Gelecekte bir noktada başka bir özel etki alanı eklemeye karar verdiysiniz ve yeni etki alanı için DKIM'yi etkinleştirmek istediğiniz her etki alanı için bu makaledeki adımları tamamlamanız gerekir. Özellikle [DKIM'i el ile ayarlamak için ne yapmak gerekir? konusunda yer alan tüm adımları tamamlayın](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Özel bir etki alanı için DKIM imzalama ilkesi devre dışı bırakma
<a name="DisableDKIMSigningPolicy"> </a>

İmzalama ilkesini devre dışı bırakmak DKIM'yi tamamen devre dışı bırakmaz. Bir süre sonra, Microsoft 365 varsayılan ilke hala etkin durumda ise, etki alanınız için varsayılan ilke otomatik olarak uygulanır. DKIM'yi tamamen devre dışı bırakmak isterseniz, hem özel hem de varsayılan etki alanlarında DKIM'yi devre dışı bırakmanız gerekir. Daha fazla bilgi için bkz. [DKIM ve MICROSOFT 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>DKIM imzalama ilkesini devre dışı bırakmak için, Windows PowerShell

1. [Bağlan PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)

2. DKIM imzalamayı devre dışı bırakmak istediğiniz her etki alanı için aşağıdaki komutlardan birini çalıştırın.

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

DKIM'yi etkinleştirmezsiniz, Microsoft 365 Microsoft Çevrimiçi E-posta Yönlendirme Adresi (MOERA)/ilk etki alanınız ve veri merkezimizde dahili olarak depolalarımızın ilişkili özel anahtarı için otomatik olarak bir 2048 bit DKIM ortak anahtarı oluşturur. Varsayılan olarak, Microsoft 365 ilkesi olan etki alanları için varsayılan imzalama yapılandırması kullanılır. Başka bir ifadeyle, DKIM'yi kendiniz ayarlayamayacaksanız, Microsoft 365 alanınız için DKIM'yi etkinleştirmek üzere oluşturduğu varsayılan ilkeyi ve anahtarları kullanır.

Ayrıca, etkinleştirdikten sonra özel etki alanınız üzerinde DKIM imzalamayı devre dışı bıraksanız bile, bir süre Microsoft 365, özel etki alanınız için MOERA/ilk etki alanı ilkesi otomatik olarak uygulanır.

Aşağıdaki örnekte, etki alanının yöneticisi tarafından değil, fabrikam.com için DKIM'Microsoft 365 etkinleştirilmiştir. Bu, gerekli CNAM'lerin DNS'de yer alamay olduğu anlamına gelir. Bu etki alanındaki e-posta için DKIM imzaları şuna benzer:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

Bu örnekte, ana bilgisayar adı ve etki alanı, etki alanı yöneticisi tarafından DKIM-signing for fabrikam.com etkinleştirilmişse CNAME'nin işaret edecek değerleri içerir. Daha sonra, bir ekipten gönderilen Microsoft 365 tek tek DKIM imzalanmış olur. DKIM'yi kendiniz etkinleştirirsiniz, etki alanı Ilk: adreste yer alan etki alanıyla aynı olur (bu durumda fabrikam.com. Hizalanmazsanız, hizalanmaz ve bunun yerine kuruma uygun olan ilk etki alanını kullanır. İlk etki alanınızı belirleme hakkında bilgi için bkz. Etki Alanları [SSS](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>DkIM'i, üçüncü taraf bir hizmetin özel etki alanınız adına e-posta gönderebi veya e-posta gönder yetkisine sahip olacak şekilde ayarlama
<a name="SetUp3rdPartyspoof"> </a>

Bazı toplu e-posta servis sağlayıcıları veya hizmet olarak yazılım sağlayıcıları, hizmetlerinden kaynaklanan e-posta için DKIM anahtarları ayarlamanızı sağlar. Bu, gerekli DNS kayıtlarını ayarlamak için kendinizle üçüncü taraf arasında koordinasyon gerektirir. Bazı üçüncü taraf sunucuların, farklı seçicileri olan kendi CNAME kayıtları olabilir. İki kuruluş tam olarak aynı şeyi yapmaz. Bunun yerine, işlem tamamen kuruluşa bağlıdır.

Şu şekilde yapılandırılmış bir DKIM ve dkIM contoso.com bulkemailprovider.com ileti şöyle olabilir:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

Bu örnekte, bu sonucu elde etmek için:

1. Toplu E-posta Sağlayıcısı Contoso'ya genel bir DKIM anahtarı verdi.

2. Contoso, DKIM anahtarını DNS kaydında yayımlar.

3. E-posta gönderirken, Toplu E-posta Sağlayıcısı anahtarı ilgili özel anahtarla imzalar. Bunu yaparak Toplu E-posta Sağlayıcısı DKIM imzasını ileti üst bilgisinde ekli olarak gösterir.

4. E-posta sistemleri alıcı, iletinin From: (5322.From) DKIM-Signature d=\<domain\> değerinin etki alanı için kimlik doğru kullanarak DKIM denetimi gerçekleştirin. Bu örnekte, değerler eşler:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>E-posta göndermeyen etki alanlarını belirleme

Kuruluşların, bir etki alanının DKIM kaydında bu etki `v=DKIM1; p=` alanları için belirterek e-posta gönderemezseniz bunu açıkça belirtmesi gerekir. Bu, e-posta sunucularını alıcıya etki alanı için geçerli bir ortak anahtar olmadığını ve bu etki alanında yer aldığını iddia eden tüm e-postaların reddedilmesi önerir. Bunu, her etki alanı ve alt etki alanı için joker karakterli DKIM kullanarak yapabilirsiniz.

Örneğin, DKIM kaydı şöyle olabilir:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Sonraki adımlar: DkIM for Microsoft 365
<a name="DKIMNextSteps"> </a>

**DKIM, spopoing önlemeye yardımcı olmak için tasarlanmış olsa da, DKIM SPF ve DMARC ile daha iyi çalışır.**

DKIM'yi bir kez ayardan sonra, SPF'yi daha önce ayarlamadıysanız bunu yapsanız iyi olur. SPF'ye hızlı bir giriş yapmak ve SPF'yi hızla yapılandırmak için bkz Kimlik Microsoft 365 için [**SPF'yi**](set-up-spf-in-office-365-to-help-prevent-spoofing.md) ayarlama. Microsoft 365'un SPF'yi nasıl kullandığı hakkında daha ayrıntılı bilgi için veya sorun gidermek ya da karma dağıtımlar gibi standart olmayan dağıtımlarda, Microsoft 365, spoing'yi engellemek için [Sender Policy Framework'i (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) nasıl kullanır? ile başlayabilirsiniz.

Ardından, bkz. [**E-postayı doğrulamak için DMARC kullanma**](use-dmarc-to-validate-email.md). [İstenmeyen posta önleme iletisi üst bilgileri](anti-spam-message-headers.md), DKIM denetimlerinden Microsoft 365 kullanılan söz dizimi ve üst bilgi alanlarını içerir.

**Bu test DKIM** imzalama yapılandırmasının doğru yapılandırıldığından ve doğru DNS girdilerinin yayımlanmış olduğunu doğrular.

> [!NOTE]
> Bu özellik, bir Microsoft 365 yönetici hesabı gerektirir. Bu özellik, Microsoft 365 Government, 21Vianet tarafından yürütülen Microsoft 365 veya Microsoft 365 Almanya'da kullanılamaz.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Testleri Çalıştırma: DKIM</a></p>
</div>

## <a name="more-information"></a>Daha fazla bilgi

PowerShell aracılığıyla tuş döndürme: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[E-postayı doğrulamak için DMARC kullanma](use-dmarc-to-validate-email.md)
