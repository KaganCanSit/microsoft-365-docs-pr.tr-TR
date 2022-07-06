---
title: Bilgi engelleri öznitelikleri
description: Bu makale, bilgi engelleri segmentlerini tanımlamak için kullanabileceğiniz Azure Active Directory kullanıcı hesabı özniteliklerine yönelik bir başvurudur.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, bilgi engelleri
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
ms.openlocfilehash: a1549a0cb3bf03056b37a75175c3b24416bec7b5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639786"
---
# <a name="information-barriers-attributes"></a>Bilgi engelleri öznitelikleri

Azure Active Directory'deki belirli öznitelikler, kullanıcıları bilgi engellerinde (IB) segmentlere ayırmak için kullanılabilir. Segmentler tanımlandıktan sonra, bu segmentler IB ilkeleri için filtre olarak kullanılabilir. Örneğin, kuruluşunuzdaki departmanlara göre kullanıcı segmentlerini tanımlamak için **Departman'ı** kullanabilirsiniz (tek bir çalışanın aynı anda iki departmanda çalışmadığı varsayılır).

Bu makalede, bilgi engelleri olan özniteliklerin nasıl kullanılacağı açıklanır ve kullanılabilecek özniteliklerin listesi sağlanır. Bilgi engelleri hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Bilgi engelleri](information-barriers.md)
- [Microsoft Teams'de bilgi engelleri için ilke tanımlama](information-barriers-policies.md)
- [IB ilkelerini düzenleme (veya kaldırma)](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-ib-policies"></a>IB ilkelerinde öznitelikleri kullanma

Bu makalede listelenen öznitelikler, kullanıcı segmentlerini tanımlamak veya düzenlemek için kullanılabilir. Tanımlanan segmentleriniz [, IB ilkelerinde](information-barriers-policies.md) parametre (*UserGroupFilter* değerleri olarak adlandırılır) olarak görev alır.

1. Segmentleri tanımlamak için hangi özniteliği kullanmak istediğinizi belirleyin. (Bu makalenin [Başvuru](#reference) bölümüne bakın.)

2. 1. Adım'da seçtiğiniz öznitelikler için kullanıcı hesaplarının değerlerinin doldurulduğundan emin olun. Kullanıcı hesabı ayrıntılarını görüntüleyin ve gerekirse kullanıcı hesaplarını öznitelik değerlerini içerecek şekilde düzenleyin. 

    - Birden çok hesabı düzenlemek (veya tek bir hesabı düzenlemek için PowerShell'i kullanmak) için bkz[. Office 365 PowerShell ile kullanıcı hesabı özelliklerini yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Tek bir hesabı düzenlemek için bkz. [Azure Active Directory kullanarak kullanıcının profil bilgilerini ekleme veya güncelleştirme](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. Aşağıdaki örneklere benzer şekilde [PowerShell kullanarak segmentleri tanımlayın](information-barriers-policies.md#define-segments-using-powershell):

    |**Örnek**|**Cmdlet**|
    |:----------|:---------|
    | Department özniteliğini kullanarak Segment1 adlı bir segment tanımlama | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | MemberOf özniteliğini kullanarak SegmentA adlı bir segment tanımlayın (bu özniteliğin "BlueGroup" gibi grup adları içerdiğini varsayalım) | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | ExtensionAttribute1 kullanarak DayTraders adlı bir kesim tanımlayın (bu özniteliğin "DayTrader" gibi iş başlıkları içerdiğini varsayalım") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Segmentleri tanımlarken, tüm segmentleriniz için aynı özniteliği kullanın. Örneğin, *Departman* kullanarak bazı segmentler tanımlarsanız, *Bölüm* kullanarak tüm segmentleri tanımlayın. Bazı segmentleri *Department* ve diğerlerini *MemberOf kullanarak tanımlamayın*. Segmentlerinizin çakışmadığından emin olun; her kullanıcı tam olarak bir segmente atanmalıdır.

## <a name="reference"></a>Başvuru

Aşağıdaki tabloda, bilgi engelleriyle kullanabileceğiniz öznitelikler listelemektedir.

|**Azure Active Directory özellik adı<br/> (LDAP görünen adı)**|**Exchange özellik adı**|
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
| Mailnickname | Diğer ad |
| PhysicalDeliveryOfficeName | Office |
| Postakodu | Postakodu |
| Proxyaddresses | EmailAddresses |
| Streetaddress | Streetaddress |
| Targetaddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| Userprincipalname | Userprincipalname |
| Posta | WindowsEmailAddress |
| Açıklama | Açıklama |
| Memberof | MemberOfGroup |

## <a name="resources"></a>Kaynaklar

- [Microsoft Teams'de bilgi engelleri için ilke tanımlama](information-barriers-policies.md)
- [Sorun giderme bilgileri engelleri](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Bilgi engelleri](information-barriers.md)
