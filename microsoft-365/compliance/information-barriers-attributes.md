---
title: Bilgi engelleri öznitelikleri
description: Bu makale, bilgi engeli Azure Active Directory kullanabileceğiniz kullanıcı hesabı özniteliklerine başvuru sağlar.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 33143e85bf17a707ade6dd0d6d0c66886fd85373
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985323"
---
# <a name="information-barriers-attributes"></a>Bilgi engelleri öznitelikleri

Azure Active Directory'daki bazı öznitelikler, kullanıcıları segmentlere alıt etmek için kullanılabilir. Kesimler tanımlandığı zaman, bu kesimler bilgi engeli ilkeleri için filtre olarak kullanılabilir. Örneğin, Department'i kullanarak  kullanıcıların kurum içindeki bölümlere göre kesimlerini tanımlayabilirsiniz (tek bir çalışanın aynı anda iki departmanda çalışma olduğu varsayıldı).

Bu makalede, bilgi engelleriyle birlikte özniteliklerin nasıl kullanımı açıklanmıştır ve kullanılmaktadır. Bilgi engelleri hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Bilgi engelleri](information-barriers.md)
- [Proje içinde bilgi engellerine yönelik ilkeler Microsoft Teams](information-barriers-policies.md)
- [Bilgi engeli ilkelerini düzenleme (veya kaldırma)](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-information-barrier-policies"></a>Bilgi engeli ilkelerde öznitelikleri kullanma

Bu makalede listelenen öznitelikler, kullanıcıların kesimlerini tanımlamak veya düzenlemek için kullanılabilir. Tanımlı kesimleriniz, bilgi engeli ilkelerinde parametre ( *UserGroupFilter* değerleri olarak adlandırılan) [işlevi karşılar](information-barriers-policies.md).

1. Kesimleri tanımlamak için hangi özniteliği kullanmak istediğinize karar kullanın. (Bu [makalenin](#reference) Başvuru bölümüne bakın.)

2. 1. Adım'da seçtiğiniz öznitelikler için kullanıcı hesaplarında değerlerin doldurulmuş olduğundan emin olun. Kullanıcı hesabı ayrıntılarını görüntüleme ve gerekirse kullanıcı hesaplarını öznitelik değerlerini içerecek şekilde düzenleme. 

    - Birden çok hesabı düzenlemek için (veya tek bir hesabı düzenlemek için PowerShell kullanarak), bkz. [PowerShell'i kullanarak kullanıcı Office 365 yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Tek bir hesabı düzenlemek için bkz. Hesap bilgilerini kullanarak [kullanıcının profil bilgilerini ekleme Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Aşağıdaki örneklere benzer şekilde, PowerShell](information-barriers-policies.md#define-segments-using-powershell) kullanarak kesimleri tanımlayın:

    |**Örnek**|**Cmdlet**|
    |:----------|:---------|
    | Department özniteliğini kullanarak Segment1 adlı bir segment tanımlama | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | MemberOf özniteliğini kullanarak SegmentA adlı bir segment tanımlayın (bu özniteliğin grup adlarını içerdiğini, örneğin "BlueGroup") olduğunu varsayalım | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | ExtensionAttribute1 kullanarak Day Varsayılanlar adlı bir segment tanımlama (bu özniteliğin "Day Bira" gibi iş unvanları içerdiğini varsayalım) | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Kesimler tanımlarken, tüm kesimler için aynı özniteliği kullanın. Örneğin, Bölüm'i kullanarak bazı kesimler *tanımlarsanız, Department'ı* kullanarak tüm kesimleri *tanımlayın*. Departman ve diğerlerini MemberOf kullanarak *bazı* kesimler *tanımlamayın*. Kesimlerin çakışmay olduğundan emin olun; her kullanıcıya tam olarak tek bir segmente atanabilir.

## <a name="reference"></a>Başvuru

Aşağıdaki tabloda, bilgi engelleriyle kullanabileceğiniz öznitelikler liste almaktadır.

|**Azure Active Directory adı<br/>(LDAP görünen adı)**|**Exchange adı**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| Şirket | Şirket |
| Bölüm | Bölüm |
| ExtensionAttribute1 | CustomAttribute1 |
| ExtensionAttribute2 | CustomAttribute2 |
| ExtensionAttribute3 | CustomAttribute3 |
| ExtensionAttribute4 | CustomAttribute4 |
| ExtensionAttribute5 | CustomAttribute5 |
| ExtensionAttribute6 | CustomAttribute6 |
| ExtensionAttribute7 | CustomAttribute7 |
| ExtensionAttribute8 | CustomAttribute8 |
| ExtensionAttribute9 | CustomAttribute9 |
| ExtensionAttribute10 | CustomAttribute10 |
| ExtensionAttribute11 | CustomAttribute11 |
| ExtensionAttribute12 | CustomAttribute12 |
| ExtensionAttribute13 | CustomAttribute13 |
| ExtensionAttribute14 | CustomAttribute14 |
| ExtensionAttribute15 | CustomAttribute15 |
| MSExchExtensionCustomAttribute1 | ExtensionCustomAttribute1 |
| MSExchExtensionCustomAttribute2 | ExtensionCustomAttribute2 |
| MSExchExtensionCustomAttribute3 | ExtensionCustomAttribute3 |
| MSExchExtensionCustomAttribute4 | ExtensionCustomAttribute4 |
| MSExchExtensionCustomAttribute5 | ExtensionCustomAttribute5 |
| MailNickname | Diğer Ad |
| PhysicalDeliveryOfficeName | Office |
| PostalCode | PostalCode |
| ProxyAddresses | EmailAddresses |
| StreetAddress | StreetAddress |
| TargetAddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| UserPrincipalName | UserPrincipalName |
| Posta | WindowsEmailAddress |
| Açıklama | Açıklama |
| MemberOf | MemberOfGroup |

## <a name="resources"></a>Kaynaklar

- [Proje içinde bilgi engellerine yönelik ilkeler Microsoft Teams](information-barriers-policies.md)
- [Bilgi engellerini giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Bilgi engelleri](information-barriers.md)