---
title: Microsoft Purview İleti Şifreleme'yi ayarlama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/16/2022
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 7ff0c040-b25c-4378-9904-b1b50210d00e
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Kuruluşunuzun içindeki ve dışındaki kişilerle korumalı e-posta iletişimi sağlayan Microsoft Purview İleti Şifrelemesi hakkında bilgi edinin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 828588491c3efbc696994f6073ca4ce849a64be5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622139"
---
# <a name="set-up-message-encryption"></a>İleti Şifrelemeyi Ayarlama

Microsoft Purview İleti Şifrelemesi kuruluşların korumalı e-postaları herhangi bir cihazdaki herkesle paylaşmasına olanak tanır. Kullanıcılar diğer Microsoft 365 kuruluşlarının yanı sıra Outlook.com, Gmail ve diğer e-posta hizmetlerini kullanarak üçüncü taraflarla korumalı ileti alışverişinde bulunabilir.

Kuruluşunuzda Microsoft Purview İleti Şifrelemesi kullanılabilir olduğundan emin olmak için aşağıdaki adımları izleyin.

## <a name="verify-that-azure-rights-management-is-active"></a>Azure Rights Management'ın etkin olduğunu doğrulama

Microsoft Purview İleti Şifrelemesi, Azure Information Protection tarafından şifreleme ve erişim denetimleri aracılığıyla e-postaları ve belgeleri korumak için kullanılan [azure](/azure/information-protection/what-is-azure-rms) [rights management services (Azure RMS)](/azure/information-protection/what-is-information-protection) teknolojisindeki koruma özelliklerinden yararlanıyor.

Microsoft Purview İleti Şifrelemesi kullanmanın tek önkoşulu[, Azure Rights Management'ın](/azure/information-protection/what-is-azure-rms) kuruluşunuzun kiracısında etkinleştirilmesi gerektiğidir. Bu durumda, Microsoft 365 ileti şifrelemesini otomatik olarak etkinleştirir ve hiçbir şey yapmanız gerekmez.

Azure RMS çoğu uygun plan için de otomatik olarak etkinleştirilir, bu nedenle büyük olasılıkla bu konuda da hiçbir şey yapmanız gerekmez. Daha fazla bilgi için bkz. [Azure Rights Management'ı etkinleştirme](/azure/information-protection/activate-service) .

> [!IMPORTANT]
> Exchange Online ile Active Directory Rights Management hizmetini (AD RMS) kullanıyorsanız, ileti [şifrelemesini kullanabilmek için önce Azure Information Protection'a geçmeniz](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) gerekir. Microsoft Purview İleti Şifrelemesi AD RMS ile uyumlu değildir.

Daha fazla bilgi için bkz.:

- Abonelik planınızın Azure Information Protection (Azure RMS işlevselliğini içerir) içerip içermediğini denetlemek için [İleti Şifrelemesi SSS](ome-faq.yml).
- Uygun bir abonelik satın alma hakkında bilgi için [Azure Information Protection](https://azure.microsoft.com/services/information-protection/).

### <a name="manually-activating-azure-rights-management"></a>Azure Rights Management'ı el ile etkinleştirme

Azure RMS'yi devre dışı bırakdıysanız veya herhangi bir nedenle otomatik olarak etkinleştirilmediyse, bu özelliği şu şekilde el ile etkinleştirebilirsiniz:

- **Microsoft 365 yönetim merkezi**: Yönergeler için bkz. [Yönetim merkezinden Azure Rights Management'ı etkinleştirme](/azure/information-protection/activate-office365).
- **Azure portal**: Yönergeler için bkz. [Azure portal Azure Rights Management'ı etkinleştirme](/azure/information-protection/activate-azure).

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Azure Information Protection kiracı anahtarınızın yönetimini yapılandırma

Bu, isteğe bağlı bir adımdır. Microsoft'un Azure Information Protection kök anahtarını yönetmesine izin vermek varsayılan ayardır ve çoğu kuruluş için önerilen en iyi yöntemdir. Böyle bir durum söz konusuysa, hiçbir şey yapmanız gerekmez.

Uyumluluk gereksinimleri gibi kendi kök anahtarınızı oluşturmanızı ve yönetmenizi gerektirebilecek birçok neden vardır (kendi anahtarını getir (BYOK) olarak da bilinir). Bu durumda, Microsoft Purview İleti Şifrelemesi ayarlamadan önce gerekli adımları tamamlamanızı öneririz. Daha fazla bilgi için bkz. [Azure Information Protection kiracı anahtarınızı planlama ve uygulama](/information-protection/plan-design/plan-implement-tenant-key).

## <a name="verify-microsoft-purview-message-encryption-configuration-in-exchange-online-powershell"></a>Exchange Online PowerShell'de Microsoft Purview İleti Şifrelemesi yapılandırmasını doğrulama

Microsoft 365 kiracınızın [Exchange Online PowerShell'de](/powershell/exchange/exchange-online-powershell) Microsoft Purview İleti Şifrelemesi kullanacak şekilde düzgün yapılandırıldığını doğrulayabilirsiniz.

1. Microsoft 365 kiracınızda genel yönetici izinlerine sahip bir hesap kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Get-IRMConfiguration cmdlet'ini çalıştırın.

     Kiracınızda Microsoft Purview İleti Şifrelemesi yapılandırıldığını gösteren AzureRMSLicensingEnabled parametresi için $True değerini görmeniz gerekir. Değilse, Microsoft Purview İleti Şifrelemesi etkinleştirmek için Set-IRMConfiguration kullanarak AzureRMSLicensingEnabled değerini $True olarak ayarlayın.

3. Aşağıdaki söz dizimini kullanarak Test-IRMConfiguration cmdlet'ini çalıştırın:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Örnek**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - Gönderen ve alıcı için, Microsoft 365 kiracınızdaki herhangi bir kullanıcının e-posta adresini kullanın.

     Sonuçlarınız şuna benzer olmalıdır:

     ```console
     Results : Acquiring RMS Templates ...
                - PASS: RMS Templates acquired.  Templates available: Contoso  - Confidential View Only, Contoso  - Confidential, Do Not
            Forward.
            Verifying encryption ...
                - PASS: Encryption verified successfully.
            Verifying decryption ...
                - PASS: Decryption verified successfully.
            Verifying IRM is enabled ...
                - PASS: IRM verified successfully.

            OVERALL RESULT: PASS
     ```

   - Kuruluşunuzun adı *Contoso'nın* yerini alır.

   - Varsayılan şablon adları yukarıda görüntülenenlerden farklı olabilir. Daha fazla bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/azure/information-protection/configure-policy-templates).

4. Test **, RMS şablonları alınamadı** hata iletisiyle başarısız olursa aşağıdaki komutları yürütün ve geçtiğini doğrulamak için Test-IRMConfiguration cmdlet'ini çalıştırın.

   ```powershell
   $RMSConfig = Get-AadrmConfiguration
   $LicenseUri = $RMSConfig.LicensingIntranetDistributionPointUrl
   Set-IRMConfiguration -LicensingLocation $LicenseUri
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```
5. Rights Management hizmetiyle bağlantıyı kesmek için Remove-PSSession cmdlet'ini çalıştırın.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-microsoft-purview-message-encryption"></a>Sonraki adımlar: Microsoft Purview İleti Şifrelemesi kullanmak için posta akışı kuralları tanımlama

Kuruluşunuzda e-postayı şifrelemek için önceden yapılandırılmış posta akışı kuralları varsa, Microsoft Purview İleti Şifrelemesi kullanmak için mevcut kuralları güncelleştirmeniz gerekir. Yeni dağıtımlar için yeni posta akışı kuralları oluşturmanız gerekir.

> [!IMPORTANT]
> Mevcut posta akışı kurallarını güncelleştirmezseniz, kullanıcılarınız yeni sorunsuz deneyim yerine önceki HTML eki biçimini kullanan şifrelenmiş postaları almaya devam eder.

Posta akışı kuralları, e-posta iletilerinin şifrelenmesi gereken koşulların yanı sıra bu şifrelemeyi kaldırma koşullarını belirler. Kural için bir eylem ayarladığınızda, kural koşullarıyla eşleşen tüm iletiler gönderildiğinde şifrelenir.

Posta akışı kuralları ileti şifrelemesi oluşturma adımları için bkz. [Office 365 e-posta iletilerini şifrelemek için posta akışı kurallarını tanımlama](define-mail-flow-rules-to-encrypt-email.md).

Mevcut kuralları Microsoft Purview İleti Şifrelemesi kullanacak şekilde güncelleştirmek için:

1. Microsoft 365 yönetim merkezi Yönetici **merkezleri** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange'e**</a> gidin.
2. Exchange yönetim merkezinde **Posta akışı > Kuralları'na** gidin.
3. Her kural için **Aşağıdakileri yapın bölümünde:**
    - **İleti güvenliğini değiştir'i** seçin.
    - **İleti Şifrelemesi ve hak koruması Office 365 Uygula'yı** seçin.
    - Listeden bir RMS şablonu seçin.
    - **Kaydet**'i seçin.
    - **Tamam**'ı seçin.
