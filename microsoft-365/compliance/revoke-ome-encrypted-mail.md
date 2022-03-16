---
title: Gelişmiş İleti Şifrelemesi ile şifrelenen e-postaları iptal etme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Yönetici ve ileti gönderen olarak, bir e-posta adresiyle şifrelenmiş bazı e-postaları iptal Office 365 Gelişmiş İleti Şifrelemesi.
ms.openlocfilehash: bf793dce23c91e8b45f96114e6c4a56c866adc32
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512260"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Gelişmiş İleti Şifrelemesi ile şifrelenen e-postaları iptal etme

E-posta iptali, e-posta iptal Office 365 Gelişmiş İleti Şifrelemesi. Office 365 Gelişmiş İleti Şifrelemesi [E5, Microsoft 365 Kurumsal, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home) Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatları) ve diğer Office 365 Kurumsal  E5 (Kar Amacı Gütmeyen Personel Fiyatları) ve A5 Office 365 Eğitim. Organizasyonda herhangi bir aboneliği olmayan bir Office 365 Gelişmiş İleti Şifrelemesi, satın almak için Microsoft 365 E5 Uyumluluk için SKU Microsoft 365 E3, Microsoft 365 E3  (Kar Amacı Gütmeyen Personel Fiyatları) Office 365 Gelişmiş Uyumluluk veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatları) veya SKU için SKU Office 365.

Bu makale, bu makaleyle ilgili daha geniş bir makale dizisinin [Office 365 İleti Şifrelemesi](ome.md).

Bir ileti Office 365 Gelişmiş İleti Şifrelemesi kullanılarak şifrelenirse ve Microsoft 365 yöneticisiyseniz veya iletinin göndereni sizseniz, belirli koşullar altında iletiyi iptalebilirsiniz. Yöneticiler PowerShell'in kullanıldığı iletileri iptal ediyor. Gönderen olarak, doğrudan posta gönderenden gelen bir iletiyi iptal Web üzerinde Outlook. Bu makalede, hangi iptalin mümkün olduğu ve bunun nasıl olduğu açıklanmıştır.

> [!NOTE]
> OME iletilerini izleyebilme ve iptal etme olanağını garanti etmek için, özel bir markalama şablonu eklemeniz gerekir. Bkz [. Şifreli iletilerinize kurum markanızı ekleme](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>İptal edildiğiniz şifreli e-postalar

Alıcı bağlantı tabanlı, markalı bir şifreli e-posta alırsa, yöneticiler ve ileti gönderenler şifreli e-postaları iptal e-posta olarak iptal edilebilir. Alıcı desteklenen bir istemcide yerel bir satır içi deneyim Outlook, iletiyi iptal Outlook.

Alıcının bağlantı tabanlı deneyim mi yoksa satır içi deneyim mi aldığı, alıcı kimlik türüne bağlıdır: Office 365 ve Microsoft hesabı alıcıları (örneğin, outlook.com kullanıcıları) desteklenen Outlook istemcilerde satır içi deneyim alır. Gmail ve Yahoo alıcıları gibi diğer tüm alıcı türleri bağlantı tabanlı bir deneyim elde edin.

Yöneticiler ve ileti gönderenleri, doğrudan posta iletilerinden uygulanan şifreleme kullanılarak şifrelenmiş iletileri Web üzerinde Outlook. Örneğin, Yalnızca Şifrele seçeneğiyle şifrelenmiş iletiler.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="E-postada Yalnızca Şifrele seçeneğini gösteren Web üzerinde Outlook.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>İptal edilmiş şifreli e-postalar için alıcı deneyimi

E-posta iptal edildiktan sonra, alıcı Office 365 İleti Şifrelemesi portalı üzerinden şifrelenmiş e-postaya erişerek bir hata alır: "İleti gönderen tarafından iptal edildi".

![İptal edilmiş şifreli e-postayı gösteren ekran görüntüsü.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Gönderdiğiniz şifreli bir iletiyi iptal etme

E-posta hesaplarını veya posta hesaplarınız gibi sosyal hesapları kullanan tek bir alıcıya gmail.com yahoo.com. Başka bir deyişle, bağlantı tabanlı deneyime sahip tek bir alıcıya gönderilen e-postayı iptalebilirsiniz.

Office 365, Microsoft 365 veya Microsoft hesabı kullanan bir kullanıcının (örneğin, iş veya okul hesabı) iş veya okul hesabı kullanan bir alıcıya gönderdiği bir postayı iptal outlook.com. 

Şifrelenmiş bir iletiyi iptal etmek için bu adımları tamamlayın

1. Web üzerinde Outlook'de, **Gönderilmiş** klasörünüzdeki iptal etmek istediğiniz iletiye göz atabilirsiniz.

   Postanız yenilenebilirse, iletinin en üstünde "Dış erişimi kaldır" bağlantısını alırsınız.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Bir e-postada iptal etmek istediğiniz şifreli postayı gösteren Web üzerinde Outlook.":::

2. **İletiyi iptal etmek için Dış** erişimi kaldır'a tıklayın.

   İletide, durumunun iptal edildiği gösterir.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Web üzerinde Outlook'da iptal edilen şifrelenmiş iletiyi gösteren Web üzerinde Outlook.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Şifreli bir iletiyi yönetici olarak iptal etme

Microsoft 365 uygun şifreli e-postaları iptal etmek için bu genel adımları izleyin:

- E-postanın İleti Kimliğini alın.
- İletiyi iptal edildiğini doğrulayın.
- Postayı iptal etme.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Adım 1. E-postanın İleti Kimliğini Alma

Şifreli bir postayı iptal etmek için, önce postanın İleti Kimliğini toplayın. MessageId genellikle şu biçimdedir:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

İptal etmek istediğiniz e-postanın İleti Kimliğini bulmanın çeşitli yolları vardır. Bu bölümde birkaç seçenek açıklasa da, kimlik sağlayan herhangi bir yöntemi kullanabilirsiniz.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Güvenlik Uyumluluk Merkezi'nde İleti İzleme'i kullanarak iptal etmek istediğiniz e-postanın İleti Kimliğini &amp; tanımlamak için

1. Güvenlik ve Uyumluluk Merkezi'nde Yeni İleti İzleme'i [kullanarak gönderene veya & araması.](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/)

2. E-postayı bu kez bu adrese getirerek İleti izleme **ayrıntıları bölmesini açın** . İleti **Kimliğini bulmak için** Daha Fazla Bilgi'ye genişletin.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>Güvenlik Uyumluluk Merkezi'nde İleti Şifreleme raporlarını kullanarak iptal etmek istediğiniz e-Office İleti Kimliğini &amp; belirlemek için

1. Güvenlik Uyumluluk Merkezi'nde &amp; İleti şifreleme **raporuna gidin**. Bu rapor hakkında bilgi için bkz. [Güvenlik Uyumluluk Merkezi'nde e-posta güvenlik &amp; raporlarını görüntüleme](../security/office-365-security/view-email-security-reports.md).

2. Ayrıntıları **görüntüle tabloyu** seçin ve iptal etmek istediğiniz iletiyi seçin.

3. İleti Kimliğini içeren ayrıntıları görüntülemek için iletiye çift tıklayın.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Adım 2. Postanın yenilenebilir olduğunu doğrulama

İletiyi iptal edip edip etmeyiş olup olmadığınızı doğrulamak için, Şifreleme raporunda, Güvenlik Uyumluluk Merkezi'nin Ayrıntılar tablosunda  İptal Durumu alanını görünür durumda olup &amp; olmadığını kontrol edin.

E-postanızı kullanarak belirli bir e-posta iletiyi iptal Windows PowerShell için, bu adımları tamamlayın.

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Get-OMEMessageStatus cmdlet'ini aşağıdaki gibi çalıştırın:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Bu komut iletinin konusunu ve iletinin geçerli olup olmadığını döndürür. Örneğin,

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Adım 3. Postayı iptal etme

İptal etmek istediğiniz e-postanın İleti Kimliği'ne ve iletinin iptal edilebilir olduğunu doğruladıktan sonra, &amp; Güvenlik Uyumluluk Merkezi'ne veya Posta'ya bakarak e-postayı iptal Windows PowerShell.

Güvenlik Uyumluluk Merkezi'i kullanarak iletiyi iptal &amp; etmek için

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak Güvenlik ve Uyumluluk Merkezi'& bağlanabilirsiniz.

2. Şifreleme **raporunda**, iletinin **Ayrıntılar** tablosunda İletiyi iptal **edin'i seçin**.

E-postayı E-posta Windows PowerShell için, Set-OMEMessageRevocation cmdlet'ini kullanın.

1. Genel yönetici izinleri olan bir iş veya okul hesabı kullanarak[, PowerShell'Bağlan Exchange Online sahip olun](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-OMEMessageRevocation cmdlet'ini aşağıdaki gibi çalıştırın:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. E-postanın iptal edilip edilmediğini kontrol etmek için, aşağıdaki Get-OMEMessageStatus cmdlet'ini çalıştırın:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    İptal başarılı olursa, cmdlet aşağıdaki sonucu verir:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Daha fazla bilgi Office 365 Gelişmiş İleti Şifrelemesi

- [Office 365 Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md)

- [Office 365 Gelişmiş İleti Şifrelemesi - e-postanın süre sonu](ome-advanced-expiration.md)

- [İleti ilkesi ve uyumluluk hizmeti açıklaması](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)