---
title: Güvenlik bilgilerini kullanarak hassas bir bilgi türü Office 365 İleti Şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- Strat_O365_Enterprise
description: Güvenlik bilgilerini kullanarak, organizasyonunız için hassas bir bilgi türü ilkesi Office 365 İleti Şifrelemesi.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 8978b1f9faae2e96fa1940bf7663855ec3bb61da
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018774"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>İleti Şifrelemesi kullanarak, organizasyonunız için hassas bir bilgi türü ilkesi oluşturma

Bu konuda hassas bir Exchange türü ilkesi oluşturmak için posta akış kuralları veya Veri Kaybı Önleme (DLP) Office 365 İleti Şifrelemesi. Posta akışı Exchange kuralı oluşturmak için, Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">merkezini (EAC) veya</a> PowerShell'i kullanabilirsiniz.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>EAC'de posta akışı kurallarını kullanarak ilke oluşturmak için

Yönetim merkezinde oturum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange ve</a> **Mail flowRules'e** >  **gidin**. Kurallar sayfasında, geçerli kuralların geçerli olduğu bir Office 365 İleti Şifrelemesi. İletide veya ekte belirli anahtar sözcüklerin veya hassas bilgi türlerinin varlığı gibi koşulları temel alan bir kural oluşturabilirsiniz.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>PowerShell'de posta akışı kurallarını kullanarak ilke oluşturmak için

Genel yönetici izinleri olan bir iş veya okul hesabı kullanın, yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell). İlkeyi Set-IRMConfiguration için New-TransportRule cmdlet'lerini kullanın.

## <a name="example-mail-flow-rule-created-with-powershell"></a>PowerShell ile oluşturulan örnek posta akışı kuralı

E-postalar veya ekleri aşağıdaki hassas bilgi türlerini içeriyorsa, PowerShell'de aşağıdaki komutları çalıştırarak kuruluş dışından gönderilen e-postaları otomatik olarak şifreleyen bir Exchange posta akışı kuralı oluşturun:

- ABA yönlendirme numarası
- Kredi Kartı Numarası
- Enforcement Agency (DEA) numarası
- ABD / U.K. pasaport numarası
- ABD banka hesap numarası
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)
- ABD Sosyal Güvenlik Numarası (SSN)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Daha fazla bilgi için [bkz. Set-IRMConfiguration ve](/powershell/module/exchange/set-irmconfiguration) [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Alıcılar eklere nasıl erişer?

Microsoft bir iletiyi şifreledikten sonra, alıcıların şifreli e-postalarına erişmek ve e-postalarını açmak için eklere sınırsız erişimi olur.

## <a name="to-prepare-for-this-change"></a>Bu değişiklike hazırlanmak için

Tüm geçerli son kullanıcı belgelerini ve eğitim malzemelerini güncelleştirin ve böylece organizasyon'daki diğer kişilerin bu değişiklikle hazırlanmasını sabilirsiniz. Bu Office 365 İleti Şifrelemesi kaynakları kullanıcılarınıza uygun şekilde paylaşın:

- [PC için Outlook'de şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 Temel Video: Office İleti Şifrelemesi](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Bu değişiklikleri denetim günlüğünde görüntüleme

Microsoft 365 denetlemelerini sağlar ve yöneticilerin bunu kullanılabilir durumda sağlar. Bu işlem 'Yeni AktarımRule' işlemidir ve Güvenlik ve Uyumluluk Merkezi'nde Denetim Günlüğü Araması'nın örnek denetim girdilerinden & verilmiştir:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"…etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Hassas bilgi türleri ilkesi devre dışı bırakmak veya özelleştirmek için

Exchange posta akışı kuralını oluşturduktan sonra, Exchange yönetim [](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) merkezinde **Mail** **flowRules'e** >  gidip "Giden hassas e-postaları şifrele (ilk gelen kuralı *)*<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">"</a> kuralını devre dışı bırakarak kuralı devre dışı bırakabilirsiniz.