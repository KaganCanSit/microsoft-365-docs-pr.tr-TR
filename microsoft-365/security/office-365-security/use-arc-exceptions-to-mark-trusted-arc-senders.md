---
title: Güvenilir ARC gönderenlerini gönderen ve alıcı arasındaki geçerli cihazlar ve hizmetler için kullanma
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Kimliği Doğrulanmış Alınan Zincir (ARC), cihazlarda ve gönderen ile alıcı arasında gelen dolaylı posta akışlarında kimlik doğrulama sonuçlarını korumaya çalışan e-posta kimlik doğrulamasıdır. Güvenilir ARC Gönderenleriniz için şu şekilde özel durumlar yapabilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 625dd27ff59fca6a0e156bd65296e407e22005a6
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663914"
---
# <a name="make-a-list-of-trusted-arc-senders-to-trust-legitimate-indirect-mailflows"></a>*Meşru* dolaylı posta akışlarına güvenmek için güvenilir ARC Gönderenlerinin listesini oluşturma

**Uygulandığı öğe**

- Exchange Online Protection
- Office 365 için Microsoft Defender plan 1 ve plan 2
- Microsoft 365 Defender

[SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md) gibi e-posta kimlik doğrulama mekanizmaları, e-posta alıcılarının *güvenliği* için e-posta gönderenleri doğrulamak için kullanılır, ancak bazı meşru hizmetler gönderen ile alıcı arasında e-postada değişiklik yapabilir. **Microsoft 365 Defender'da ARC, *meşru* dolaylı posta akışlarından kaynaklanan SPF, DKIM ve DMARC teslim hatalarını azaltmaya yardımcı olacaktır.**

## <a name="authenticated-received-chain-arc-for-legitimate-indirect-mailflows-in-microsoft-365-defender-for-office"></a>Office için Microsoft 365 Defender'da *geçerli* dolaylı posta akışları için Kimliği Doğrulanmış Alınan Zincir (ARC)

Postaları filtreleyen veya iletilen posta listeleri ve hizmetler, kuruluşun posta akışının iyi bilinen ve normal bir özelliğidir. Ancak e-postanın içe doğru ilerletilmesi SPF'yi ihlal eder. Hizmetler ayrıca e-posta üst bilgilerini değiştirerek, virüs tarama bilgileri ekleyerek veya ekleri kaldırarak DKIM e-posta kimlik doğrulamasını ihlal edebilir. Bu e-posta kimlik doğrulama yöntemlerinden birinin başarısız olması DMARC'nin geçememesine neden olabilir.

Meşru hizmetlerden gelen planlı posta akışı müdahaleleri genellikle *dolaylı posta akışı* olarak adlandırılır ve alıcıya giden bir sonraki cihaz veya hizmetten geçerken iletilerin *yanlışlıkla* e-posta kimlik doğrulamasının başarısız olmasına neden olabilir.

**Güvenilen ARC mühürleyicileri yöneticilerin Microsoft 365 Defender portalına *güvenilir* aracıların listesini eklemesine olanak tanır.** Güvenilir ARC mühürleyicileri, Microsoft'un güvenilir aracılardan gelen ARC imzalarını kabul etmesini sağlayarak bu meşru iletilerin kimlik doğrulama zincirinde başarısız olmasını önler.

> [!NOTE]
> ***Güvenilir ARC mühürleyicileri, işlemleri dolaylı posta akışıyla sonuçlanan ve ARC sızdırmazlığı uygulayan tüm etki alanları için yönetici tarafından oluşturulan bir listedir.*** Bir e-posta Office 365 kiracısının Office 365 ve ARC paslı aracısına yönlendirildiğinde, Microsoft ARC imzasını doğrular ve ARC sonuçlarına bağlı olarak sağlanan kimlik doğrulama ayrıntılarına uyar.

## <a name="when-to-use-trusted-arc-sealers"></a>Güvenilir ARC sızdırmazlıkları ne zaman kullanılır?

Güvenilir ARC mühürleyicilerinin listesi yalnızca cihazların ve sunucuların kuruluşun e-posta akışına müdahale ettiği durumlarda gereklidir ve:

1. E-posta üst bilgisini veya diğer e-posta içeriğini değiştirebilir.
2. Kimlik doğrulamasının başka nedenlerle başarısız olmasına neden olabilir (örneğin, ekleri kaldırarak).
 
Güvenilir bir ARC sealer ekleyerek Office 365, Office 365 kiracınıza posta teslim ederken, filtreleyicinin sağladığı kimlik doğrulama sonuçlarını doğrular ve güvener.

**Yöneticiler *yalnızca geçerli hizmetleri* güvenilir ARC sızdırmazları olarak eklemelidir.** Yalnızca kuruluşun açıkça kullandığı ve bildiği hizmetleri eklemek, önce e-posta kimlik doğrulama denetimlerini geçirmek için bir hizmetten geçmesi gereken iletilerin yardımcı olur ve kimlik doğrulama hataları nedeniyle meşru iletilerin *Gereksiz'e* gönderilmesini önler.

## <a name="steps-to-add-a-trusted-arc-sealer-to-microsoft-365-defender"></a>Microsoft 365 Defender güvenilir bir ARC sealer ekleme adımları

Microsoft 365 Defender portalındaki güvenilir ARC mühürleyicileri, kiracınız tarafından onaylanan ve kiracınıza eklenen tüm ARC sızdırmazlık işaretlerini gösterir.

**Yönetim portalına yeni bir Güvenilir ARC sealer eklemek için:**

1. [E-posta kimlik doğrulaması ayarları](https://security.microsoft.com/authentication?viewid=ARC) sayfasına gidin.

2. Güvenilir bir ARC sealer'ı ilk kez eklediyseniz Ekle düğmesine tıklayın.
3. Gösterilen metin kutusuna güvenilir ARC sızdırmazlık elemanları ekleyin.
    1. Etki alanlarını eklediğinize dikkat edin (örnek fabrikam.com).
    1. Buraya girdiğiniz etki alanı adı, ARC-Seal ve ARC-Message-Signature üst bilgilerinde (iletinin e-posta üst bilgilerinde) 'd' etki alanı etiketinde gösterilen etki alanıyla *eşleşmelidir* .
    1. Bunları Outlook'daki iletinin özelliklerinde görebilirsiniz.

## <a name="steps-to-validate-your-trusted-arc-sealer"></a>Güvenilir ARC sealer'ınızı doğrulama adımları

İleti Microsoft 365 Defender ulaşmadan önce üçüncü taraflardan bir ARC contası varsa, **e-posta alındıktan sonra üst bilgileri denetleyin ve en son ARC üst bilgilerini görüntüleyin**.

Son ***ARC-Authentication-Results header_ içinde** ARC doğrulamasının _*pass** olarak listelenip listelenmediğini denetleyin.

1'in 'oda'sını listeleyen bir ARC üst bilgisi, önceki ARC'ın *doğrulandığını*, önceki ARC sealer'ın *güvenilir* olduğunu ve önceki *geçiş sonucunun* geçerli DMARC hatasını geçersiz kılmak için kullanılabileceğini gösterir.

**oda=1'i gösteren bir ARC geçiş üst bilgisi**

Oda sonucu için bu üst bilgi bloğunun sonundaki e-posta kimlik doğrulama yöntemlerine bakın.

``
ARC-Authentication-Results: i=2; mx.microsoft.com 1; spf=pass (sender ip is
40.107.65.78) smtp.rcpttodomain=microsoft.com
smtp.mailfrom=o365e5test083.onmicrosoft.com; dmarc=bestguesspass action=none
header.from=o365e5test083.onmicrosoft.com; dkim=none (message not signed);
arc=pass (0 oda=1 ltdi=1
spf=[1,1,smtp.mailfrom=o365e5test083.onmicrosoft.com]
dkim=[1,1,header.d=o365e5test083.onmicrosoft.com]
dmarc=[1,1,header.from=o365e5test083.onmicrosoft.com])
``

ARC sonucunun DMARC hatasını geçersiz kılmak için kullanılıp kullanılmadığını denetlemek için üst bilgide *compauth* sonucunu ve *kod nedenini (130)* arayın.

*Compauth'u* ve *nedeni* bulmak için bu üst bilgi bloğundaki son girdiye bakın.

``
Authentication-Results: spf=fail (sender IP is 51.163.158.241)
smtp.mailfrom=contoso.com; dkim=fail (body hash did not verify)
header.d=contoso.com;dmarc=fail action=none
header.from=contoso.com;compauth=pass reason=130
``

## <a name="powershell-steps-to-add-or-remove-a-trusted-arc-sealer"></a>Güvenilir bir ARC sealer eklemek veya kaldırmak için PowerShell adımları

**Yöneticiler Exchange Online PowerShell ile ARC yapılandırmaları da ayarlayabilir.**

1. Çevrimiçi powershell'i Exchange Bağlan.
2. Bağlan-ExchangeOnline.
3. Etki alanını güvenilir bir ARC sealer'a eklemek veya güncelleştirmek için:
</br>
``
Set-ArcConfig -Identity default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>veya</br>
``
Set-ArcConfig -Identity {tenant name/tenanid}\default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>*Set-ArcConfig* çalıştırırken *-Identity* default kimlik parametresini sağlamanız gerekir. Güvenilir sızdırmazlık elemanları *ARC-Seal üst bilgisindeki* 'd' etiketinin değeriyle eşleştirilmelidir.

4. Güvenilir ARC sızdırmazlıklarını görüntüleyin:
</br>
``
Get-ArcConfig
`` Veya ``
Get-ArcConfig - Organization {tenant name}
``

## <a name="trusted-arc-sealer-mailflow-graphics"></a>Güvenilir ARC sealer posta akışı grafikleri

Bu diyagramlar SPF, DKIM ve DMARC e-posta kimlik doğrulamasından herhangi birini kullanırken posta akışı işlemlerini güvenilir bir ARC sealer ile ve olmadan karşıtlık sağlar. Her iki grafikte de, şirket tarafından posta akışına müdahale etmesi gereken, bazen IP'leri göndererek ve e-posta üst bilgisine yazarak e-posta kimlik doğrulama standartlarını ihlal eden meşru hizmetler vardır. **İlk durumda, dolaylı posta akışı trafiği, yöneticiler güvenilir bir ARC sealer *eklemeden önce* sonucu gösterir.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-without-trusted-arc-sealer.PNG" alt-text="Bu grafikte Contoso standart e-posta güvenliğinin bir parçası olarak SPF, DKIM ve DMARC yayımlar. SPF kullanan bir gönderen contoso.com içinden fabrikam.com'a posta gönderir ve bu posta Contoso'nun işe aldığı üçüncü taraf bir hizmetten geçer ve bu hizmet e-posta üst bilgisindeki gönderen IP adresini değiştirir. EOP'deki DNS denetimi sırasında içerik üçüncü bir taraf tarafından değiştirildiği için posta, değiştirilen IP nedeniyle SPF ve DKIM başarısız olur. SPF ve DKIM hataları nedeniyle DMARC başarısız oluyor. İleti Gereksiz, Karantina veya Reddedildi'ye gönderilir.":::

Burada, **güvenilir bir ARC sealer oluşturma özelliğinden yararlandıktan sonra** aynı kuruluşu görürsünüz.

:::image type="content" source="../../media/m365d-indirect-traffic-flow-with-trusted-arc-sealer.PNG" alt-text="İkinci grafikte Contoso şirketi güvenilir ARC sızdırmazlık elemanlarının listesini oluşturmuştur. Aynı kullanıcı contoso.com fabrikam.com ikinci bir posta gönderir. Contoso tarafından işe alınan üçüncü taraf hizmeti, postanın üst bilgisindeki gönderenin IP adresini değiştirir. Ancak bu kez hizmet ARC sızdırmazlık uyguladı ve kiracı yöneticisi üçüncü tarafın etki alanını güvenilir ARC mühürleyicilerine zaten eklediğinden, değişiklik kabul edilir. SPF yeni IP adresi için başarısız olur; İçerik değişikliği nedeniyle DKIM başarısız olur; Önceki hatalar nedeniyle DMARC başarısız olur; ancak ARC değişiklikleri tanır, Bir Geçiş yayınlar ve değişiklikleri kabul eder. Spoof ayrıca bir geçiş alır. İleti Gelen Kutusu'na gönderilir.":::

## <a name="next-steps-after-you-set-up-arc-for-microsoft-365-defender-for-office"></a>Sonraki adımlar: Office için Microsoft 365 Defender için ARC'i ayarladıktan sonra

Kurulumdan sonra ARC Üst Bilgilerinizi [İleti Üst Bilgisi Çözümleyicisi](/connectivity-analyzer/message-header-analyzer) ile denetleyin.

[SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md), yapılandırma adımlarını gözden geçirin.
