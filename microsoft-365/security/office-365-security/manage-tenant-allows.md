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
- MET150
ms.collection:
- M365-security-compliance
description: Yöneticiler, güvenlik portalında yer alan Kiracı İzin Ver/Engelleme Listesi'ni nasıl yapılandırlayabileceklerini öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c8bf6f37d837d46bfdcca98296c8ca09747276cc
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005025"
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

## <a name="add-allows-using-the-submissions-portal"></a>Ekleme, Gönderiler portalının kullanımına izin verir 

Dosyaların, URL'lerin ve gönderenlerin, iletilerin Gönderiler bölümüne izin Microsoft 365 Defender. 

1. Microsoft 365 Defender portalında E-posta ve **işbirliği &** \> **gidin**.

2. Gönderiler **sayfasında** Çözümleme için gönderildi **sekmesinin seçili olduğunu doğrulayın** ve Ardından Ad simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Çözümleme için Microsoft'a gönderin**.

3. Ağ ileti **kimliğini ekleyerek veya e-posta** dosyasını karşıya yükerek ileti göndermek üzere gözden geçirmek üzere Microsoft'a Gönder uç güncelleştirmesini kullanın. 

4. **Microsoft'a gönderme için bir neden seçin bölümünde** Engellenmiş olmalı (hatalı pozitif)**'i seçin**. 

5. Bu gibi **iletilere izin ver seçeneğini** açabilirsiniz. 

6. Sonra **kaldır açılan** listesinde, izin ver seçeneğinin ne kadar süreyle çalışmasını istediğiniz belirtin.

7. Bitirdikten sonra **Gönder düğmesine tıklayın** .

> [!div class="mx-imgBorder"]
> ![Hatalı pozitif gönderme örneği.](../../media/admin-submission-allow-messages.png)

## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>E-posta kullanarak girişlere izin vermek için kimliği doğru Microsoft 365 Defender

> [!NOTE]
> 
> - Yalnızca _kimlik_ doğrulanmamış kullanıcının ve etki alanı çifti  içinde tanımlandığı üzere gönderme altyapısının birleşimine özel olarak kimlik doğrulama izni verilir veya bu altyapı engellenir.
> - Bir etki alanı çifti için bir izin verme veya engelleme girdisi yapılandırıldığında, bu etki alanı çiftinin iletileri artık kimlik bilgileri bilgisinde görünmez.
> - Kimliği doğru gönderenlerin girdilerinin süresi hiçbir zaman dolmaz.
> - Poof, hem izin verme hem de engellemeyi destekler. URL yalnızca izin ver'i destekler.

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** , Bilgi Verme **sekmesini seçin ve** ardından Engelle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **ekle'yi seçin**.

3. Görüntülenen **Yeni etki alanı çiftleri** ekle açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Joker karakterlerle yeni etki alanı çiftleri ekleme**: Satır başına bir etki alanı çifti (en çok 20) girin. Hatalı gönderen girişlerinin söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
   - **Poof türü**: Aşağıdaki değerlerden birini seçin:
     - **İç**: Kimliği doğru olmayan gönderen, organizasyona ait bir etki alanında (kabul edilen etki [alanı) yer alır](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
     - **Dış**: Gönderenin kimliği doğru değil dış etki alanında.
   - **Eylem**: İzin **Ver'i veya** **Engelle'yi seçin**.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>PowerShell kullanarak kimliği doğru gönderene izin verme girişleri ekleme

Kiracı İzin Ver/Engelleme Listesi'ne hatalı gönderen girdileri eklemek için aşağıdaki söz dizimlerini kullanın:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>İlgili makaleler

- [Yönetici gönderimleri](admin-submission.md)
- [Hatalı pozitif ve yanlış negatifleri bildirme](report-false-positives-and-false-negatives.md)
