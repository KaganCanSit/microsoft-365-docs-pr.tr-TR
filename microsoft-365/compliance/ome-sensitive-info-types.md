---
title: Office 365 İleti Şifrelemesi kullanarak hassas bilgi türü ilkesi oluşturma
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
description: Office 365 İleti Şifrelemesi kullanarak kuruluşunuz için hassas bilgi türü ilkesi oluşturmayı öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 0974c30882177eb9fc46c2a2fcf65bc2edb43078
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633443"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>İleti Şifrelemesi'ni kullanarak kuruluşunuz için hassas bilgi türü ilkesi oluşturma

Office 365 İleti Şifrelemesi ile hassas bir bilgi türü ilkesi oluşturmak için Exchange posta akışı kurallarını veya Microsoft Purview veri kaybı önlemeyi (DLP) kullanabilirsiniz. Exchange posta akışı kuralı oluşturmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini (EAC)</a> veya PowerShell'i kullanabilirsiniz.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>EAC'de posta akışı kurallarını kullanarak ilkeyi oluşturmak için

<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> oturum açın ve **Posta akışı** > **Kuralları'na** gidin. Kurallar sayfasında, İleti Şifrelemesi Office 365 uygulayan bir kural oluşturun. İletide veya ekte belirli anahtar sözcüklerin veya hassas bilgi türlerinin varlığı gibi koşulları temel alan bir kural oluşturabilirsiniz.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>PowerShell'de posta akışı kurallarını kullanarak ilke oluşturmak için

Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın, Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell). İlkeyi oluşturmak için Set-IRMConfiguration ve New-TransportRule cmdlet'lerini kullanın.

## <a name="example-mail-flow-rule-created-with-powershell"></a>PowerShell ile oluşturulan örnek posta akışı kuralı

E-postalar veya ekleri aşağıdaki hassas bilgi türlerini içeriyorsa, kuruluşunuzun dışına gönderilen e-postaları yalnızca şifrele seçeneğiyle otomatik olarak şifreleyen bir Exchange posta akışı kuralı oluşturmak için PowerShell'de aşağıdaki komutları çalıştırın:

- ABA yönlendirme numarası
- Kredi kartı numarası
- Uyuşturucu Uygulama Dairesi (DEA) numarası
- Birleşik Krallık / Birleşik Krallık pasaport numarası
- ABD banka hesap numarası
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)
- ABD Sosyal Güvenlik Numarası (SSN)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Daha fazla bilgi için bkz [. Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) ve [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Alıcıların eklere erişme şekli

Microsoft bir iletiyi şifreledikten sonra, alıcıların şifrelenmiş e-postalarına erişip açtıklarında eklere sınırsız erişimi vardır.

## <a name="to-prepare-for-this-change"></a>Bu değişikliğe hazırlanmak için

Kuruluşunuzdaki kişileri bu değişikliğe hazırlamak için geçerli son kullanıcı belgelerini ve eğitim malzemelerini güncelleştirmek isteyebilirsiniz. Bu Office 365 İleti Şifrelemesi kaynaklarını kullanıcılarınızla uygun şekilde paylaşın:

- [Pc için Outlook'ta şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 Essentials Videosu: İleti Şifrelemesi](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Bu değişiklikleri denetim günlüğünde görüntüleyin

Microsoft 365 bu etkinliği denetler ve yöneticilerin kullanımına sağlar. İşlem 'New-TransportRule' işlemidir ve Güvenlik & Uyumluluk Merkezi'nde Denetim Günlüğü Araması'ndan bir örnek denetim girişinin parçacığı aşağıda verilmiştir:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"...etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Hassas bilgi türleri ilkesini devre dışı bırakmak veya özelleştirmek için

Exchange posta akışı kuralını oluşturduktan sonra, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> **Posta akışı** > **Kuralları'na** gidip "*Giden hassas e-postaları şifrele (ilk kural)*" kuralını devre dışı bırakarak kuralı [devre dışı bırakabilir veya düzenleyebilirsiniz](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule).
