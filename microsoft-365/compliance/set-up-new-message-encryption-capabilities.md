---
title: Yeni İleti Şifreleme özelliklerini ayarlama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/30/2019
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
description: Kuruluş içindeki ve dışındaki Office 365 İleti Şifrelemesi korumalı e-posta iletişimini etkinleştiren yeni özellik hakkında bilgi alın.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 006bef8a78a50e3cc47bfcfe7910621a3fa9ef85
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018798"
---
# <a name="set-up-new-message-encryption-capabilities"></a>Yeni İleti Şifreleme özelliklerini ayarlama

Yeni özellik Office 365 İleti Şifrelemesi (OME) özellikleri, kuruluşların korumalı e-postayı herhangi bir cihazda herkesle paylaşmasına olanak sağlar. Kullanıcılar, Outlook.com, Gmail Microsoft 365 diğer e-posta hizmetlerini kullanan, diğer e-posta kuruluşlarının yanı sıra, başka kuruluşlarla da korumalı iletiler alışverişi olabilir.

Yeni OME özelliklerinin kurumda kullanılabilir olduğundan emin olmak için aşağıdaki adımları izleyin.

## <a name="verify-that-azure-rights-management-is-active"></a>Azure Hak Yönetimi'nin etkin olduğunu doğrulama

Yeni OME özellikleri, şifreleme ve erişim denetimleri aracılığıyla e-postaları ve belgeleri korumak için [Azure Information Protection](/azure/information-protection/what-is-azure-rms) tarafından kullanılan Azure [Rights Management Services'ın (Azure RMS)](/azure/information-protection/what-is-information-protection) koruma özelliklerinden faydalanın.

Yeni OME özelliklerini kullanmanın tek önkoşulları, [Azure Hak](/azure/information-protection/what-is-azure-rms) Yönetimi'nin kurum kiracıda etkinleştirilmesidir. Etkinse, Microsoft 365 OME özelliklerini otomatik olarak etkinleştirir ve herhangi bir şey yapmaya gerek yok.

Azure RMS de çoğu uygun plan için otomatik olarak etkinleştirilir, dolayısıyla büyük olasılıkla bu konuda da bir şey yapmak zorunda değildir. Daha [fazla bilgi için bkz. Azure Hak Yönetimini](/azure/information-protection/activate-service) etkinleştirme.

> [!IMPORTANT]
> Exchange Online'da Active Directory Rights Management hizmetini (AD RMS) kullanıyorsanız, yeni OME özelliklerini kullanabilmek için önce [Azure Information Protection'a](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) geçişlisiniz. OME, AD RMS ile uyumlu değildir.

Daha fazla bilgi için bkz.:

- [Yeni OME özelliklerini kullanmak için hangi aboneliklere ihtiyacım var?](ome-faq.yml#what-subscriptions-do-i-need-to-use-the-new-ome-capabilities-) ve abonelik planınız Azure Information Protection'i (Azure RMS işlevselliğini içerir) dahil olup olmadığını kontrol edin.
- [Uygun bir abonelik](https://azure.microsoft.com/services/information-protection/) satın alma hakkında bilgi için Azure Information Protection.

### <a name="manually-activating-azure-rights-management"></a>Azure Hak Yönetimi'ne el ile etkinleştirme

Azure RMS'yi devre dışı bırakıldıysanız veya herhangi bir nedenden dolayı otomatik olarak etkinleştirilmediyse, şu işlemden el ile etkinleştirebilirsiniz:

- **Microsoft 365 yönetim merkezi**: Yönergeler [için bkz. Yönetim merkezinden Azure Hak Yönetimi'ni](/azure/information-protection/activate-office365) etkinleştirme.
- **Azure portalı**: Yönergeler [için bkz. Azure portalında Azure Hak Yönetimi'nin nasıl](/azure/information-protection/activate-azure) etkinleştirildi.

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Azure Information Protection kiracı anahtarınızı yapılandırma

Bu isteğe bağlı bir adımdır. Azure Information Protection için kök anahtarın Microsoft tarafından yönetimine izin verme, varsayılan ayardır ve çoğu kuruluş için önerilen en iyi uygulamadır. Böyle bir durumda, bir şey yapmaya gerek yok.

Uyumluluk gereksinimleri gibi, kendi kök anahtarınızı (kendi anahtarınızı getirme olarak da bilinir) oluşturmanızı ve yönetmenizi zorunlulaştıracak birçok neden vardır. Böyle bir durumda, yeni OME özelliklerini ayarlamadan önce gerekli adımları tamamlamanız önerilir. Daha [fazla bilgi için bkz. Azure Information Protection kiracı anahtarınızı planlama](/information-protection/plan-design/plan-implement-tenant-key) ve uygulama.

## <a name="verify-new-ome-configuration-in-exchange-online-powershell"></a>Exchange Online PowerShell'de yeni OME yapılandırmasını doğrulama

Microsoft 365 kiracının, Microsoft 365 PowerShell'de yeni OME özelliklerini kullanmak üzere [doğru Exchange Online doğru şekilde yapılandırıldı](/powershell/exchange/exchange-online-powershell).

1. [Bağlan yönetici Exchange Online izinlerine](/powershell/exchange/connect-to-exchange-online-powershell) sahip bir hesap kullanarak PowerShell'i Microsoft 365 seçin.

2. Get-IRMConfiguration cmdlet'ini çalıştırın.

     Kiracınız OME'nin $True olduğunu gösteren AzureRMSLicensingEnabled parametresi için değer görüyor olmalıdır. Ayarlanmazsa, OME'Set-IRMConfiguration etkinleştirmek için AzureRMSLicensingEnabled değerini $True'i kullanın.

3. Aşağıdaki söz Test-IRMConfiguration kullanarak Test-IRMConfiguration cmdlet'ini çalıştırın:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Örnek**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - Gönderen ve alıcı için, bir kiracıda yer alan herhangi bir kullanıcının e-Microsoft 365 kullanın.

     Sonuçlarınız aşağıdakine benzer olmalı:

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

   - Kuruluş adınız *Contoso'nın yerini alır*.

   - Varsayılan şablon adları yukarıda gösterilenden farklı olabilir. Daha [fazla bilgi için bkz. Azure Information Protection için şablonları yapılandırma ve](/azure/information-protection/configure-policy-templates) yönetme.

4. Hak Yönetimi Remove-PSSession bağlantısını kesmek için aşağıdaki cmdlet'i çalıştırın.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-new-ome-capabilities"></a>Sonraki adımlar: Yeni OME özelliklerini kullanmak için posta akışı kurallarını tanımlama

Daha önce kurumda e-postaları şifrelemek için yapılandırılmış posta akışı kuralları varsa, yeni OME özelliklerini kullanmak için var olan kuralları güncelleştirmeniz gerekir. Yeni dağıtımlarda, yeni posta akışı kuralları oluşturmanız gerekir.

> [!IMPORTANT]
> Var olan posta akışı kurallarını güncelleştirin, kullanıcılarınız yeni sorunsuz OME deneyimi yerine önceki HTML ek biçimini kullanan şifrelenmiş posta almaya devam eder.

Posta akış kuralları, hem e-posta iletilerinin şifrelenmeleri gereken koşullar hem de bu şifrelemenin kaldırılması için koşullar belirler. Kural için bir eylem ayarsanız, kural koşullarına uygun tüm iletiler gönderildikleri zaman şifrelenir.

OME için posta akış kuralları oluşturma adımları için bkz. E-posta [iletilerinizi](define-mail-flow-rules-to-encrypt-email.md) şifrelemek için posta akış kurallarını tanımlama Office 365.

Yeni OME özelliklerini kullanmak üzere var olan kuralları güncelleştirmek için:

1. Genel Microsoft 365 yönetim merkezi Yönetim **merkezleri'ne gidin Exchange** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>
2. Yönetim Exchange, Posta akışı ve **Kurallar'> gidin**.
3. Her kural için, **Şunları yapın**:
    - İleti **güvenliğini değiştir'i seçin**.
    - Kullanıcı **hakları ve Office 365 İleti Şifrelemesi uygula'ya seçin**.
    - Listeden bir RMS şablonu seçin.
    - **Kaydet**'i seçin.
    - **Tamam**'ı seçin.
