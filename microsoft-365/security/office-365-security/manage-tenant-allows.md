---
title: Kiracı İzin Ver/Engelle Listesinde izinlerinizi yönetme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: Yöneticiler, güvenlik portalında yer alan Kiracı İzin Ver/Engelleme Listesi'ni nasıl yapılandırlayabileceklerini öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3823290e9f239b14e4bf97fe1ae8ef7020561697
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314120"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesi'ne izin verme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yöneticiler doğrudan Kiracı İzin Ver/Engelleme Listesi'ne izin ekleyemz. Bunun yerine, yönetici gönderim işlemini kullanarak engellenmiş iletiyi gönderirsiniz; böylece ilgili URL, dosya ve/veya gönderenler Kiracı İzin Verme/Engelleme Listesi'ne eklenecektir. Dosya, URL veya gönderenin engeli henüz oluşturulmamışsa izinler oluşturulmaz. İletinin hatalı bir şekilde engellenmiş yanlış pozitif sonuç olarak belirlen olduğu çoğu durumda, sisteme doğal bir şekilde izin vermek için gereken süre boyunca izinler tutulur.

> [!IMPORTANT]
> Microsoft sizin, gönderenin, URL'nin veya dosyanın izinlerini yönetmesi gerekli veya kötü olduğu kabul edilen izinler kaldırılır. Bunun en iyi yöntem ortamınızı korumak ve izinlerin yanlış yapılandırılmasını önlemektir. Bu gibi durumlarda, bir iletinin neden hala kötü kabul edilir olduğunu belirlemeye yardımcı olması için bir destek davaları gerekli olabilir.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Gönderen ekleme, Gönderiler portalını kullanmaya izin verir 

Web'de, Gönderiler sayfasında **gönderenlere (veya etki** alanlarına) Microsoft 365 Defender. 

1. Microsoft 365 Defender portalında, Eylemler ve <https://security.microsoft.com>**Gönderiler &** \> **gidin**. Gönderiler sayfasına doğrudan **gitmek için de** bunu kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında** , E-posta sekmesinin seçili **olduğunu** doğrulayın ve ardından çözümleme simgesi için Microsoft'a ![Gönder'e tıklayın.](../../media/m365-cc-sc-create-icon.png) **Çözümleme için Microsoft'a gönderin**.

3. Ağ ileti **kimliğini ekleyerek veya e-posta** dosyasını karşıya yükerek ileti göndermek üzere gözden geçirmek üzere Microsoft'a Gönder uç güncelleştirmesini kullanın. 

4. **Microsoft'a gönderme için bir neden seçin bölümünde** Engellenmiş olmalı (hatalı pozitif)**'i seçin**. 

5. Bu gibi **iletilere izin ver seçeneğini** açabilirsiniz. 

6. Sonra **kaldır açılan** listesinde, izin ver seçeneğinin ne kadar süreyle çalışmasını istediğiniz belirtin.

7. Bitirdikten sonra **Gönder düğmesine tıklayın** .

> [!div class="mx-imgBorder"]
> ![Çözümleme için kötü amaçlı yazılımı Microsoft'a gönderin.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>URL Ekle, Gönderiler portalının kullanımına izin verir

web sayfasındaki Gönderiler **sayfasında URL'lere** izin Microsoft 365 Defender.

1. Microsoft 365 Defender portalında, Eylemler ve <https://security.microsoft.com>**Gönderiler &** \> **gidin**. Gönderiler sayfasına doğrudan **gitmek için de** bunu kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında** URL'ler sekmesini **seçin ve ardından** çözümleme simgesi için Microsoft'a ![Gönder'e tıklayın.](../../media/m365-cc-sc-create-icon.png) **Çözümleme için Microsoft'a gönderin**.

3. **URL'yi ekleyerek ileti göndermek için** Gözden geçirmek üzere Microsoft'a Gönder uç güncelleştirmesini kullanın.

4. **Microsoft'a gönderme için bir neden seçin bölümünde** Engellenmiş olmalı (hatalı pozitif)**'i seçin**.

5. Bu gibi **URL'lere izin ver seçeneğini** açma.

6. Sonra **kaldır açılan** listesinde, izin ver seçeneğinin ne kadar süreyle çalışacaklarını belirtin.

7. Bitirdikten sonra **Gönder düğmesine tıklayın** .

> [!div class="mx-imgBorder"]
> ![Çözümleme için URL'yi gönderin.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>Dosya Ekle, Gönderiler portalının kullanımına olanak sağlar

sayfanın Gönderiler **sayfasındaKimlik** sayfasında Dosyalara İzin Microsoft 365 Defender.

Microsoft 365 Defender portalında, Eylemler ve <https://security.microsoft.com>**Gönderiler &** \> **gidin**. Gönderiler sayfasına doğrudan **gitmek için de** bunu kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında** E-posta **ekleri sekmesini seçin** ve ardından çözümleme için Microsoft'a ![Gönder simgesine tıklayın.](../../media/m365-cc-sc-create-icon.png) **Çözümleme için Microsoft'a gönderin**.

3. Dosya veya **dosyaları ekleyerek ileti göndermek üzere** gözden geçirmek üzere Microsoft'a Gönder uç güncelleştirmesini kullanın.

4. **Microsoft'a gönderme için bir neden seçin bölümünde** Engellenmiş olmalı (hatalı pozitif)**'i seçin**.

5. Bu gibi dosyalara **izin ver seçeneğini** açma.

6. Sonra **kaldır açılan** listesinde, izin ver seçeneğinin ne kadar süreyle çalışacaklarını belirtin.

7. Bitirdikten sonra **Gönder düğmesine tıklayın** .

> [!div class="mx-imgBorder"]
> ![Çözümleme için e-posta gönderin.](../../media/submit-email-for-analysis.png)


## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>E-posta kullanarak girişlere izin vermek için kimliği doğru Microsoft 365 Defender

> [!NOTE]
> 
> - Yalnızca _kimlik_ doğrulanmamış kullanıcının ve etki alanı çifti  içinde tanımlandığı üzere gönderme altyapısının birleşimine özel olarak kimlik doğrulama izni verilir veya bu altyapı engellenir.
> - Bir etki alanı çifti için bir izin verme veya engelleme girdisi yapılandırıldığında, bu etki alanı çiftinin iletileri artık kimlik bilgileri bilgisinde görünmez.
> - Kimliği doğru gönderenlerin girdilerinin süresi hiçbir zaman dolmaz.
> - Poof, hem izin verme hem de engellemeyi destekler. URL yalnızca izin ver'i destekler.

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>E-posta **& işbirliği İlkeleri'ne** \> **& kuralları** \> **Kurallar bölümündeki Tehdit** \> ilkeleri **Kiracı İzin Ver/Engelleme** **Listeleri'ne** gidin. Ya da doğrudan Kiracı İzin Ver **/Listeleri Engelleme sayfasına gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** , Bilgi Verme **sekmesini seçin ve** Ekle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **ekle'yi seçin**.

3. Görüntülenen **Yeni etki alanı çiftleri** ekle açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Joker karakterlerle yeni etki alanı çiftleri ekleme**: Satır başına bir etki alanı çifti (en çok 20) girin. Hatalı gönderen girişlerinin söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
   - **Poof türü**: Aşağıdaki değerlerden birini seçin:
     - **İç**: Kimliği doğru olmayan gönderen, organizasyona ait bir etki alanında (kabul edilen etki [alanı) yer alır](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
     - **Dış**: Gönderenin kimliği doğru değil dış etki alanında.
   - **Eylem**: İzin **Ver'i veya** **Engelle'yi seçin**.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>PowerShell kullanarak kimliği doğru gönderene izin verme girişleri ekleme

Exchange Online PowerShell'de Kiracı İzin Ver/Engelleme [Listesi'ne hatalı gönderen](/exchange/connect-to-exchange-online-powershell) girdileri eklemek için aşağıdaki söz dizimlerini kullanın:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>İlgili makaleler

- [Yönetici gönderimleri](admin-submission.md)
- [Hatalı pozitif ve yanlış negatifleri bildirme](report-false-positives-and-false-negatives.md)
