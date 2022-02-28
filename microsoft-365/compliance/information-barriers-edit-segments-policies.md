---
title: Bilgi engeli ilkelerini yönetme
description: Bilgi engellerine yönelik ilkeleri düzenlemeyi veya kaldırmayı öğrenin.
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
ms.openlocfilehash: e5a8eac15ebb76d9b3c2c95b3eff2cf3bd29772e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985361"
---
# <a name="manage-information-barrier-policies"></a>Bilgi engeli ilkelerini yönetme

Bilgi [engeli ilkelerini tanımdikten](information-barriers-policies.md) sonra, sorun gidermenin bir parçası olarak veya düzenli bakım olarak bu ilkelerde veya kullanıcı kesimleriniz [](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) üzerinde değişiklik yapabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|**Eylem**|**Açıklama**|
|:---------|:--------------|
| [Kullanıcı hesabı özniteliklerini düzenleme](#edit-user-account-attributes) | Segmentleri tanımlamak Azure Active Directory özelliklerde öznitelikler doldurun.<br/>Kullanıcılar olması gereken kesimlere dahil değilken kullanıcı hesabı özniteliklerini düzenleyin, kullanıcıların hangi kesimlerde olduğunu değiştirebilir veya farklı öznitelikler kullanarak kesimler tanımlayabilirsiniz. |
| [Segmenti düzenleme](#edit-a-segment) | Segmentin tanımlandığı şekilde değiştirmek istediğiniz kesimleri düzenleyin. <br/>Örneğin, başlangıçta Department kullanan kesimler tanımlanmış olabilir ve şimdi *MemberOf* gibi başka bir öznitelik kullanmak *istiyor olabilir*. |
| [İlkeyi düzenleme](#edit-a-policy) | Bir ilkenin çalışmasini değiştirmek istediğiniz zaman, bilgi engeli ilkesi düzenleyin.<br/>Örneğin, iki kesim arasındaki iletişimi engellemek yerine, yalnızca belirli kesimler arasında iletişimin gerçekleşmesine izin vermek istediğinize karar ve verirsiniz. |
| [İlkeyi etkin değil durumuna ayarlama](#set-a-policy-to-inactive-status) |Bir ilkede değişiklik yapmak istediğiniz veya ilkenin etkin durumda etkin olmadığınız bir durumda ilkeyi etkin olmayacak şekilde ayarlayın. |
| [İlkeyi kaldırma](#remove-a-policy) | Belirli bir ilkeye artık gerek kalmadan, bilgi engeli politikasını kaldırın. |
| [İlke uygulamasını durdurma](#stop-a-policy-application) | Bilgi engeli ilkelerini uygulama sürecini durdurmak istediğiniz zaman bu eylemi benimsersiniz.<br/> İlke uygulamasının durdurulması anında olmaz ve kullanıcılara önceden uygulanmış olan ilkeleri geri almaz. |
| [Bilgi engellerine yönelik ilkeleri tanımlama](information-barriers-policies.md) | Bu tür ilkeler henüz karşılanmazsa ve belirli kullanıcı grupları arasındaki iletişimleri kısıtlamanız veya sınırlandırmanız gerekirken, bilgi engeli ilkesi tanımlayın. |
| [Bilgi engellerini giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Bilgi engelleriyle ilgili beklenmeyen sorunlar ile karşılaş karşı karşıyayken bu makaleye bakın. |

> [!IMPORTANT]
> Bu makalede açıklanan görevleri gerçekleştirmek için, size uygun bir rol atanmalı, örneğin:<br/>- Microsoft 365 Kurumsal Yönetici<br/>- Genel Yönetici<br/>- Uyumluluk Yöneticisi<br/>- IB Uyumluluk Yönetimi (bu yeni bir rol!)<br><br>Bilgi engeli önkoşulları hakkında daha fazla bilgi edinmek için bkz. [Önkoşullar (bilgi engeli ilkeleri için).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Güvenlik ve Uyumluluk [Merkezi PowerShell'e & emin olun](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Kullanıcı hesabı özniteliklerini düzenleme

Kullanıcıların bölüm oluşturmada kullanılan özniteliklerini düzenlemek için bu yordamı kullanın. Örneğin, bir Department özniteliği kullanıyorsanız ve şu anda bir veya birden çok kullanıcı hesabında Department için hiçbir değer listelenmiyorsa, o kullanıcı hesaplarını Departman bilgilerini içerecek şekilde düzenlemeniz gerekir. Kullanıcı hesabı öznitelikleri, bilgi engeli ilkelerinin atanabilir olması için bölümleri tanımlamak için kullanılır.

1. Öznitelik değerleri ve atanmış segmentler gibi belirli bir kullanıcı hesabının ayrıntılarını görüntülemek için Identity parametreleriyle **Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her bir kişiyi benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. <p> (Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Bu örnekte, Office 365'de iki kullanıcı hesabına başvururuz: *İbrhan için ayses* *ve* *Alex* *için alexw*. |

2. Kullanıcı hesabı profilleriniz için hangi öznitelikleri düzenlemek istediğinize karar olun. Daha fazla bilgi için bkz [. Bilgi engeli ilkeleri için öznitelikler](information-barriers-attributes.md). 

3. Bir veya birden çok kullanıcı hesabını, önceki adımda seçtiğiniz özniteliğin değerlerini içerecek şekilde düzenleyin. Bu eylemi gerçekleştirmek için aşağıdaki yordamlardan birini kullanın:

    - Tek bir hesabı düzenlemek için bkz. Hesap bilgilerini kullanarak [kullanıcının profil bilgilerini ekleme Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Birden çok hesabı düzenlemek için (veya tek bir hesabı düzenlemek için PowerShell kullanarak), bkz. [PowerShell'i kullanarak kullanıcı Office 365 yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Segmenti düzenleme

Bir kullanıcı kesiminin tanımını düzenlemek için bu yordamı kullanın. Örneğin, bir segmentin adını veya segmente kimlerin dahil olduğunu belirlemek için kullanılan filtreyi değiştirebilirsiniz.

1. Var olan tüm kesimleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Söz dizimi: `Get-OrganizationSegment`

    Segment türü, kullanıcı GrubuFiltresi değeri, bunu oluşturan veya en son değiştiren, GUID gibi her kesim için bir kesimler ve ayrıntılar listesi görüntülenir.

    > [!TIP]
    > Daha sonra referans olarak etmek üzere kesimler listenizi yazdırarak veya kaydedin. Örneğin, bir segmenti düzenlemek için segmentin adını bilmek veya değeri tanımlamaniz gerekir (Identity parametresiyle kullanılır).

2. Bir segmenti düzenlemek için **Set-OrganizationSegment** cmdlet'ini Identity parametresi ve **ilgili** ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <p> Bu örnekte, GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd* olan segment için bölüm adını "HRDept" olarak güncellemiştir. |

Kuruluş için kesimleri düzenlemeyi bitirdikten sonra, bilgi engeli ilkelerini [tanımlayabilir](information-barriers-policies.md#step-3-define-information-barrier-policies) [veya](#edit-a-policy) düzenleyebilirsiniz.

## <a name="edit-a-policy"></a>İlkeyi düzenleme

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **, Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun.

2. **Bir Identity parametresiyle Set-InformationBarrierPolicy** cmdlet'ini kullanın ve yapmak istediğiniz değişiklikleri belirtin.

    Örnek: Araştırma kesiminin Satış ve Pazarlama segmentleriyle *iletişim* kurmalarını engellemek için bir *ilkenin tanımlandığı* *varsayalım* . İlke şu cmdlet kullanılarak tanımlanmıştır: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Araştırma segmentinde yer alan kişilerin yalnızca İk *segmentinde yer* alan kişiler ile iletişim kuracak şekilde değiştirmesini *istediğiniz varsayalım* . Bu değişikliği yapmak için şu cmdlet'i kullanıruz: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    Bu örnekte, "SegmentsBlocked" ifadesini "SegmentsAllowed" olarak değiştirdik ve *İk segmentini belirttik* .

3. İlkeyi düzenlemeyi bitirdikten sonra, değişikliklerinizi uygulamak için emin olun. (Bkz [. Bilgi engeli ilkelerini uygulama](information-barriers-policies.md#step-4-apply-information-barrier-policies).)

## <a name="set-a-policy-to-inactive-status"></a>İlkeyi etkin değil durumuna ayarlama

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **, Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek (veya kaldırmak) istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun.

2. İlkenin durumunu etkin değil olarak ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini Identity parametresi ve Etkin Değil olarak ayarlanmış State parametresini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <p> Bu örnekte, GUID *43c37853-ea10-4b90-a23d-ab8c9377247* olan bir bilgi engeli ilkesi etkin olmayan durumuna ayarladık. |

3. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler, kullanıcıya göre kuruluş için uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir. (Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.)

Bu noktada, bir veya daha fazla bilgi engeli ilkeleri etkin olmayan durum olarak ayarlanır. Buradan, aşağıdaki işlemlerden herhangi birini yapabilirsiniz:

- Olduğu gibi tut (etkin olmayan durum olarak ayarlanmış bir ilkenin kullanıcılar üzerinde hiçbir etkisi yoktur)
- [İlkeyi düzenleme](#edit-a-policy) 
- [İlkeyi kaldırma](#remove-a-policy)

## <a name="remove-a-policy"></a>İlkeyi kaldırma

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **, Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, kaldırmak istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun. İlkenin etkin değil durumuna ayarlanmış olduğundan emin olun.

2. **Bir Identity parametresiyle Remove-InformationBarrierPolicy** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <p> Bu örnekte, GUID *43c37853-ea10-4b90-a23d-ab8c93772471 ilkeyi kaldırmıştık*. |

    Sorulsa, değişikliği onaylayın.

3. Kaldırmak istediğiniz her ilke için 1-2. adımları yinelayın.

4. İlkeleri kaldırmayı bitirdikten sonra, değişikliklerinizi uygulama. Bu eylemi yapmak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler, kullanıcıya göre kuruluş için uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir.

## <a name="stop-a-policy-application"></a>İlke uygulamasını durdurma

Bilgi engeli ilkelerini uygulamaya başladıktan sonra, bu ilkelerin uygulanmalarını durdurmak için aşağıdaki yordamı kullanın. İşlem yaklaşık 30-35 dakika sürer.

1. En son bilgi engeli ilke uygulamasının durumunu görüntülemek için **, Get-InformationBarrierPoliciesApplicationStatus** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPoliciesApplicationStatus`

    Uygulamanın GUID bilgi notunu unutmayın.

2. **Bir Identity parametresiyle Stop-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> Bu örnekte, bilgi engeli ilkelerinin uygulanmalarını durduruyoruz. |

## <a name="resources"></a>Kaynaklar

- [Bilgi engellerine genel bir bakış elde edin](information-barriers.md)
- [Bilgi engellerine yönelik ilkeleri tanımlama](information-barriers-policies.md)
- [Bu konuda bilgi engelleri hakkında daha fazla Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'daki bilgi engelleri hakkında daha fazla bilgi](/sharepoint/information-barriers)
- [Bu konuda bilgi engelleri hakkında daha fazla OneDrive](/onedrive/information-barriers)
- [Bilgi engeli ilkeleri için öznitelikler](information-barriers-attributes.md)
- [Bilgi engellerini giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)