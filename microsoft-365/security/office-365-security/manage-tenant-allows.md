---
title: Kiracı İzin Ver/Engelle Listesinde izinlerinizi yönetin
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
description: Yöneticiler, güvenlik portalındaki Kiracı İzin Ver/Engelle Listesi'nde izin vermeleri yapılandırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 413209bdecef19c4d101162f0e23f24ff1a2903e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129254"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Kiracı İzin Verilenler/Engellenenler Listesine izinler ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yöneticiler izin veremiyor izinlerini doğrudan Kiracı İzin Ver/Engelle Listesine ekleyemiyor. Bunun yerine, engellenen iletiyi göndermek için yönetici gönderme işlemini kullanırsınız; böylece ilgili URL, dosya ve/veya gönderenler Kiracı İzin Ver/Engelle Listesine eklenir. Dosya, URL veya gönderen bloğu gerçekleşmediyse, izin verme oluşturulmaz. İletinin yanlış engellenmiş hatalı bir pozitif olduğu belirlendiği çoğu durumda, sisteme doğal olarak izin vermek için gereken süre boyunca izinler tutulur.

> [!IMPORTANT]
> Microsoft tarafından yönetildiğinden, size, gönderene, URL'ye veya dosyaya izin verdiğinden, gerekli değildir veya hatalı olarak kabul edilir kaldırılacaktır. Bu, ortamınızı korumak ve izinlerin yanlış yapılandırılmasını önlemektir. Katılmıyor olabileceğiniz durumlarda, iletinin neden hala kötü olarak kabul edildiğini saptamaya yardımcı olmak için bir destek talebi gerekebilir.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Gönderen ekleme, Gönderimler portalının kullanılmasına izin verir

Microsoft 365 Defender **Gönderiler sayfasında gönderenlere** (veya etki alanlarına) izin verin.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler &** **Gönderimler'e**\> gidin. Veya doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **, E-postalar** sekmesinin seçili olduğunu doğrulayın ve analiz için Microsoft'a gönder simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Analiz için Microsoft'a gönderin**.

3. Ağ iletisi kimliğini ekleyerek veya e-posta dosyasını karşıya yükleyerek ileti göndermek **için Gözden geçirmek üzere Microsoft'a gönder** açılır penceresini kullanın.

4. **Microsoft'a göndermek için bir neden seçin** bölümünde **Engellenmemiş olmalıdır (hatalı pozitif)** seçeneğini belirleyin.

5. Bu seçenek **gibi iletilere izin ver'i** açın.

6. **Sonra kaldır** açılan listesinden, izin verme seçeneğinin ne kadar süreyle çalışmasını istediğinizi belirtin.

7. İşiniz bittiğinde **Gönder** düğmesine tıklayın.

> ![Analiz örneği için Microsoft'a kötü amaçlı yazılım gönderin.](../../media/admin-submission-allow-messages.png)


> [!NOTE]
>
> - Hangi filtrelerin postayı kötü amaçlı olarak belirlediği temelinde, posta akışı sırasında izinler eklenir. Örneğin, filtreler hem gönderen hem de URL'nin hatalı olduğunu bulduysa, her birine bir izin eklenir. 
> - Bu varlık (gönderen, etki alanı, URL, dosya) yeniden karşılaştığında, bu varlıkla ilişkili tüm filtreler atlanır.
> - Bu nedenle, bir e-posta (bu varlığı içeren) için, posta akışı sırasında filtrelerin geri kalanı e-postanın temiz olduğunu bulursa e-posta teslim edilecek.

## <a name="add-url-allows-using-the-submissions-portal"></a>URL ekleme, Gönderimler portalının kullanılmasına izin verir

Microsoft 365 Defender'daki **Gönderimler sayfasında URL'lere** izin verin.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler &** **Gönderimler'e**\> gidin. Veya doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **URL'ler** sekmesini seçin ve analiz için Microsoft'a gönder simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Analiz için Microsoft'a gönderin**.

3. URL'yi ekleyerek ileti göndermek **için Gözden geçirmek üzere Microsoft'a gönder** açılır penceresini kullanın.

4. **Microsoft'a göndermek için bir neden seçin** bölümünde **Engellenmemiş olmalıdır (hatalı pozitif)** seçeneğini belirleyin.

5. **Bu tür URL'lere izin ver** seçeneğini açın.

6. **Sonra kaldır** açılan listesinden, izin verme seçeneğinin ne kadar süreyle çalışmasını istediğinizi belirtin.

7. İşiniz bittiğinde **Gönder** düğmesine tıklayın.

> [!div class="mx-imgBorder"]
> ![Analiz için URL'yi gönderin.](../../media/submit-url-for-analysis.png)


> [!NOTE]
>
> -  URL ile yeniden karşılaşıldığında, URL patlama veya saygınlık denetimleri için gönderilmez ve diğer tüm URL tabanlı filtreler atlanır.
> -  Bu nedenle, e-posta (bu URL'yi içeren) için, posta akışı sırasında, filtrelerin geri kalanı e-postanın temiz olduğunu bulursa e-posta teslim edilecek.


## <a name="add-file-allows-using-the-submissions-portal"></a>Dosya Ekle, Gönderimler portalının kullanılmasına izin verir

Microsoft 365 Defender **Gönderiler** sayfasında Dosyalara İzin Ver.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler &** **Gönderimler'e**\> gidin. Veya doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderiler** sayfasında **E-posta ekleri** sekmesini seçin ve analiz için Microsoft'a gönder simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Analiz için Microsoft'a gönderin**.

3. Dosyayı veya dosyaları ekleyerek ileti göndermek **için Gözden geçirmek üzere Microsoft'a gönder** açılır penceresini kullanın.

4. **Microsoft'a göndermek için bir neden seçin** bölümünde **Engellenmemiş olmalıdır (hatalı pozitif)** seçeneğini belirleyin.

5. **Bu gibi dosyalara izin ver** seçeneğini açın.

6. **Sonra kaldır** açılan listesinden, izin verme seçeneğinin ne kadar süreyle çalışmasını istediğinizi belirtin.

7. İşiniz bittiğinde **Gönder** düğmesine tıklayın.

> [!div class="mx-imgBorder"]
> ![Analiz için e-posta gönderin.](../../media/submit-email-for-analysis.png)


> [!NOTE]
>
> - Dosyayla yeniden karşılaşıldığında, patlama veya itibar denetimleri için gönderilmez ve diğer tüm dosya tabanlı filtreler atlanır.
> - Bu nedenle, bir e-posta (bu dosyayı içeren) için, posta akışı sırasında, filtrelerin geri kalanı e-postanın temiz olduğunu bulursa, e-posta teslim edilecek. 

## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Microsoft 365 Defender kullanarak sahte gönderen izin girdileri oluşturma

> [!NOTE]
>
> - Yalnızca kimlik sahtekarlığına neden olan kullanıcı _ile_ etki alanı çiftinde tanımlanan gönderme _altyapısının birleşimine_ özellikle izin verilir veya kimlik sahtekarlığına engellenir.
> - Bir etki alanı çifti için izin ver veya engelle girdisi yapılandırdığınızda, bu etki alanı çiftinden gelen iletiler artık kimlik sahtekarı zeka içgörülerinde görünmez.
> - Sahte gönderenlerin girdilerinin süresi hiçbir zaman dolmaz.
> - Kimlik sahtekarı hem izin verme hem de engellemeyi destekler. URL yalnızca izin ver'i destekler.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümündeki **E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** \> **Kiracı İzin Ver/Engelle Listeleri'ne** gidin. İsterseniz, doğrudan **Kiracı İzin Ver/Listeleri Engelle** sayfasına gitmek için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. **Kiracı İzin Ver/Engelle Listesi** sayfasında Kimlik **Sahtekarlık** sekmesini seçin ve ekle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Ekle'yi seçin**.

3. Görüntülenen **Yeni etki alanı çiftleri ekle** açılır penceresinde aşağıdaki ayarları yapılandırın:
   - **Joker karakterlerle yeni etki alanı çiftleri ekleyin**: Satır başına en fazla 20 etki alanı çifti girin. Kimlik sahtekarlığına neden olan gönderen girdilerinin söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
   - **Kimlik sahtekarı türü**: Aşağıdaki değerlerden birini seçin:
     - **İç**: Sahte gönderen, kuruluşunuza ait bir etki alanındadır ( [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Dış**: Sahte gönderen bir dış etki alanında.
   - **Eylem**: **İzin Ver'i** seçin.

4. İşiniz bittiğinde **Ekle'ye** tıklayın.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>PowerShell kullanarak sahte gönderen izin girdileri ekleme

[Exchange Online PowerShell'de](/exchange/connect-to-exchange-online-powershell) Kiracı İzin Ver/Engelle Listesi'ne sahte gönderen girdileri eklemek için aşağıdaki söz dizimini kullanın:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>İlgili makaleler

- [Yönetici gönderimleri](admin-submission.md)
- [Hatalı pozitifleri ve hatalı negatifleri raporlama](report-false-positives-and-false-negatives.md)
