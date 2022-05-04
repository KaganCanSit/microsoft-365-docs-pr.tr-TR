---
title: Gelişmiş İleti Şifrelemesi ile şifrelenen e-postayı iptal etme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/02/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Yönetici olarak ve ileti gönderen olarak, Microsoft Purview Gelişmiş İleti Şifrelemesi ile şifrelenen bazı e-postaları iptal edebilirsiniz.
ms.openlocfilehash: 79d09c13755c0c73e4d68598e83ac41344b9281a
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65187953"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Gelişmiş İleti Şifrelemesi ile şifrelenen e-postayı iptal etme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

E-posta iptali, Microsoft Purview Gelişmiş İleti Şifrelemesi'nin bir parçası olarak sunulur. Microsoft Purview Gelişmiş İleti Şifrelemesi [Microsoft 365 Kurumsal E5, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home), Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması), Office 365 Kurumsal E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması) ve Office 365 Eğitim A5. Gelişmiş İleti Şifrelemesi iptali ve süre sonu işlevlerini kullanmak için E5 lisansınızda **Premium Şifreleme Office 365** seçeneğini etkinleştirin.

Kuruluşunuzun Microsoft Purview Gelişmiş İleti Şifrelemesi içermeyen bir aboneliği varsa, Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için Microsoft 365 E5 Uyumluluk SKU eklentisiyle veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) veya SKU'ları Office 365 için SKU eklentisini Office 365 Gelişmiş Uyumluluk.

Bu makale, [Office 365 İleti Şifrelemesi](ome.md) hakkında daha büyük bir makale serisinin bir parçasıdır.

Bir ileti Microsoft Purview Gelişmiş İleti Şifrelemesi kullanılarak şifrelendiyse ve Microsoft 365 yöneticisiyseniz veya iletiyi gönderen sizseniz, iletiyi belirli koşullar altında iptal edebilirsiniz. Yöneticiler PowerShell kullanarak iletileri iptal eder. Gönderen olarak, doğrudan Web üzerinde Outlook gönderdiğiniz bir iletiyi iptal edebilirsiniz. Bu makalede iptalin mümkün olduğu koşullar ve bunun nasıl gerçekleştirildiği açıklanmaktadır.

> [!NOTE]
> OME iletilerini izleme ve iptal etme özelliğinin kullanılabildiğini garanti etmek için özel bir markalama şablonu eklemeniz gerekir. Bkz. [Şifrelenmiş iletilerinize kuruluşunuzun markasını ekleme](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>İptal edebilirsiniz şifrelenmiş e-postalar

Alıcı bağlantı tabanlı, markalı bir şifreli e-posta aldıysa yöneticiler ve ileti gönderenler şifrelenmiş e-postaları iptal edebilir. Alıcı desteklenen bir Outlook istemcisinde yerel bir satır içi deneyim aldıysa, iletiyi iptal yapamazsınız.

Alıcının bağlantı tabanlı bir deneyim veya satır içi deneyim alıp almadığı, alıcının kimlik türüne bağlıdır: Office 365 ve Microsoft hesabı alıcıları (örneğin, outlook.com kullanıcılar) desteklenen Outlook istemcilerinde satır içi deneyim elde eder. Gmail ve Yahoo alıcıları gibi diğer tüm alıcı türleri bağlantı tabanlı bir deneyim elde eder.

Yöneticiler ve ileti gönderenler, doğrudan Web üzerinde Outlook şifreleme kullanılarak şifrelenmiş iletileri iptal edebilir. Örneğin, Yalnızca Şifrele seçeneğiyle şifrelenen iletiler.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Web üzerinde Outlook'de Yalnızca Şifrele seçeneğini gösteren ekran görüntüsü.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>İptal edilen şifrelenmiş e-postalar için alıcı deneyimi

Bir e-posta iptal edildikten sonra, alıcı şifrelenmiş e-postaya Office 365 İleti Şifreleme portalı üzerinden eriştiğinde bir hata alır: "İleti gönderen tarafından iptal edildi".

![İptal edilen şifrelenmiş e-postayı gösteren ekran görüntüsü.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Gönderdiğiniz şifrelenmiş iletiyi iptal etme

gmail.com veya yahoo.com gibi bir sosyal hesap kullanan tek bir alıcıya gönderdiğiniz postayı iptal edebilirsiniz. Başka bir deyişle, bağlantı tabanlı deneyimi alan tek bir alıcıya gönderilen e-postayı iptal edebilirsiniz.

Office 365 veya Microsoft 365 ya da outlook.com hesabı gibi bir Microsoft hesabı kullanan bir kullanıcıdan iş veya okul hesabı kullanan bir alıcıya gönderdiğiniz postayı iptal edemezsiniz. 

Gönderdiğiniz şifrelenmiş iletiyi iptal etmek için şu adımları tamamlayın

1. Web üzerinde Outlook, **Gönderilmiş** klasörünüzde iptal etmek istediğiniz iletiye göz atın.

   Posta iptal edilebilirse, iletinin üst kısmında "Dış erişimi kaldır" bağlantısını görürsünüz.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Web üzerinde Outlook iptal etmek istediğiniz şifreli postayı gösteren ekran görüntüsü.":::

2. İletiyi iptal etmek için **Dış erişimi kaldır'a** tıklayın.

   İleti, durumunun iptal olduğunu gösterir.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Web üzerinde Outlook iptal edilen şifrelenmiş iletiyi gösteren ekran görüntüsü.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Yönetici olarak şifrelenmiş iletiyi iptal etme

Microsoft 365 yöneticileri, uygun bir şifrelenmiş e-postayı iptal etmek için şu genel adımları izler:

- E-postanın İleti Kimliğini alın.
- İletiyi iptal edilebildiğinizi doğrulayın.
- Postayı iptal edin.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Adım 1. E-postanın İleti Kimliğini alma

Şifrelenmiş bir postayı iptal etmeden önce, postanın İleti Kimliğini toplayın. MessageId genellikle şu biçimdedir:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

İptal etmek istediğiniz e-postanın İleti Kimliğini bulmanın birden çok yolu vardır. Bu bölümde birkaç seçenek açıklanmaktadır, ancak kimliği sağlayan herhangi bir yöntemi kullanabilirsiniz.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Güvenlik &amp; Uyumluluk Merkezi'nde İleti İzleme'yi kullanarak iptal etmek istediğiniz e-postanın İleti Kimliğini belirlemek için

1. [Güvenlik & Uyumluluk Merkezi'nde Yeni İleti İzleme'yi](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/) kullanarak gönderene veya alıcıya göre e-postayı arayın.

2. E-postayı bulduktan sonra **, İleti izleme ayrıntıları** bölmesini açmak için e-postayı seçin. İleti Kimliğini bulmak için **Daha Fazla Bilgi'yi** genişletin.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-encryption-reports-in-the-security-amp-compliance-center"></a>Güvenlik &amp; Uyumluluk Merkezi'nde İleti Şifreleme raporlarını kullanarak iptal etmek istediğiniz e-postanın İleti Kimliğini belirlemek için

1. Güvenlik &amp; Uyumluluk Merkezi'nde **İleti şifreleme raporuna** gidin. Bu rapor hakkında bilgi için bkz. [Güvenlik &amp; Uyumluluk Merkezi'nde e-posta güvenlik raporlarını görüntüleme](../security/office-365-security/view-email-security-reports.md).

2. **Ayrıntıları görüntüle** tablosunu seçin ve iptal etmek istediğiniz iletiyi belirleyin.

3. İleti kimliğini içeren ayrıntıları görüntülemek için iletiye çift tıklayın.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Adım 2. Postanın iptal edilebilir olduğunu doğrulayın

bir iletiyi iptal edip etmediğinizi doğrulamak için İptal Durumu alanının Güvenlik &amp; Uyumluluk Merkezi'ndeki **Ayrıntılar** tablosundaki Şifreleme raporunda görünüp görünmediğini denetleyin.

Windows PowerShell kullanarak belirli bir e-posta iletisini iptal edip etmediğinizi doğrulamak için bu adımları tamamlayın.

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak bir Windows PowerShell oturumu başlatın ve Exchange Online bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Get-OMEMessageStatus cmdlet'ini aşağıdaki gibi çalıştırın:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Bu komut iletinin konusunu ve iletinin iptal edilebilir olup olmadığını döndürür. Örneğin,

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Adım 3. Postayı iptal etme

İptal etmek istediğiniz e-postanın İleti Kimliğini bildiğinizde ve iletinin iptal edilebilir olduğunu doğruladıktan sonra, Güvenlik &amp; Uyumluluk Merkezi'ni veya Windows PowerShell kullanarak e-postayı iptal edebilirsiniz.

Güvenlik &amp; Uyumluluk Merkezi'ni kullanarak iletiyi iptal etmek için

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Güvenlik & Uyumluluk Merkezi'ne bağlanın.

2. **Şifreleme raporunda**, iletinin **Ayrıntılar** tablosunda İletiyi **iptal et'i** seçin.

Windows PowerShell kullanarak e-postayı iptal etmek için Set-OMEMessageRevocation cmdlet'ini kullanın.

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-OMEMessageRevocation cmdlet'ini aşağıdaki gibi çalıştırın:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. E-postanın iptal edilip edilmediğini denetlemek için Get-OMEMessageStatus cmdlet'ini aşağıdaki gibi çalıştırın:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    İptal başarılı olursa, cmdlet aşağıdaki sonucu döndürür:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifrelemesi hakkında daha fazla bilgi

- [Microsoft Purview Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md)

- [Microsoft Purview Gelişmiş İleti Şifrelemesi - e-posta süre sonu](ome-advanced-expiration.md)

- [İleti ilkesi ve uyumluluk hizmeti açıklaması](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
