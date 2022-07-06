---
title: Bilgi engeli ilkelerini yönetme
description: Bilgi engelleri için ilkeleri düzenlemeyi veya kaldırmayı öğrenin.
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
ms.openlocfilehash: a84b8e712de53b0abae81a05bbe1b2bef3237beb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635315"
---
# <a name="manage-information-barriers-policies"></a>Bilgi engeli ilkelerini yönetme

[Bilgi engelleri (IB) ilkelerini tanımladıktan](information-barriers-policies.md) sonra, [sorun giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) veya düzenli bakım kapsamında bu ilkelerde veya kullanıcı segmentlerinizde değişiklik yapmanız gerekebilir.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|**Eylem**|**Açıklama**|
|:---------|:--------------|
| [Kullanıcı hesabı özniteliklerini düzenleme](#edit-user-account-attributes) | Azure Active Directory'de segmentleri tanımlamak için kullanılabilecek öznitelikleri doldurun. <br> Kullanıcılar olması gereken segmentlere dahil olmadığında, kullanıcıların hangi segmentlerde olduğunu değiştirmek veya farklı öznitelikler kullanarak segmentleri tanımlamak için kullanıcı hesabı özniteliklerini düzenleyin. |
| [Segmenti düzenleme](#edit-a-segment) | Segmentin tanımlanma şeklini değiştirmek istediğinizde segmentleri düzenleyin. <br> Örneğin, *başlangıçta Department* kullanarak segmentleri tanımlamış ve şimdi *MemberOf* gibi başka bir öznitelik kullanmak isteyebilirsiniz. |
| [İlkeyi düzenleme](#edit-a-policy) | İlkenin çalışma şeklini değiştirmek istediğinizde bilgi engelleri ilkesini düzenleyin.<br> Örneğin, iki segment arasındaki iletişimi engellemek yerine yalnızca belirli segmentler arasında iletişimin gerçekleşmesine izin vermek istediğinize karar vekleyebilirsiniz. |
| [İlkeyi etkin değil durumuna ayarlama](#set-a-policy-to-inactive-status) |bir ilkede değişiklik yapmak istediğinizde veya bir ilkenin etkin olmasını istemediğinizde ilkeyi etkin değil durumuna ayarlayın. |
| [İlkeyi kaldırma](#remove-a-policy) | Belirli bir ilkeye artık ihtiyacınız kalmadığında bilgi engelleri ilkesini kaldırın. |
| [Segmenti kaldırma](#remove-a-segment) | Artık belirli bir segmente ihtiyacınız kalmadığında bilgi engellerini ortadan kaldırın. |
| [İlkeyi ve segmenti kaldırma](#remove-a-policy-and-segment) | Bilgi engelleri ilkesini ve bir segmenti aynı anda kaldırın. |
| [İlke uygulamasını durdurma](#stop-a-policy-application) | Bilgi engeli ilkelerini uygulama işlemini durdurmak istediğinizde bu eylemi gerçekleştirin. <br> İlke uygulamasının durdurulması anında gerçekleşmez ve kullanıcılara zaten uygulanmış olan ilkeleri geri almaz. |
| [Bilgi engelleri için ilke tanımlama](information-barriers-policies.md) | Bu tür ilkelere sahip değilseniz ve belirli kullanıcı grupları arasındaki iletişimi kısıtlamanız veya sınırlamanız gerektiğinde bir bilgi engeli ilkesi tanımlayın. |
| [Sorun giderme bilgileri engelleri](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Bilgi engelleriyle ilgili beklenmeyen sorunlarla karşılaştığınızda bu makaleye bakın. |

>[!IMPORTANT]
>Bu makalede açıklanan görevleri gerçekleştirmek için size aşağıdakilerden biri gibi uygun bir rol atanmalıdır:<br>- Microsoft 365 Kurumsal Genel Yöneticisi<br>- Genel Yönetici<br>- Uyumluluk Yöneticisi<br>- IB Uyumluluk Yönetimi (bu yeni bir roldür!)<br><br>Bilgi engellerine yönelik önkoşullar hakkında daha fazla bilgi edinmek için bkz[. Önkoşullar (bilgi engeli ilkeleri için).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> [Güvenlik & Uyumluluğu PowerShell'e bağlandığınızdan](/powershell/exchange/connect-to-scc-powershell) emin olun.

## <a name="edit-user-account-attributes"></a>Kullanıcı hesabı özniteliklerini düzenleme

Kullanıcıları segmentlere ayırmak için kullanılan öznitelikleri düzenlemek için bu yordamı kullanın. Örneğin, Bir Departman özniteliği kullanıyorsanız ve bir veya daha fazla kullanıcı hesabında Şu anda Departman için listelenen herhangi bir değer yoksa, bu kullanıcı hesaplarını Departman bilgilerini içerecek şekilde düzenlemeniz gerekir. Kullanıcı hesabı öznitelikleri, bilgi engeli ilkelerinin atanabilmesi için segmentleri tanımlamak için kullanılır.

1. Öznitelik değerleri ve atanan segmentler gibi belirli bir kullanıcı hesabının ayrıntılarını görüntülemek için, Kimlik parametreleriyle **Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her kullanıcıyı benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. <br> (Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> Bu örnekte, Office 365'de iki kullanıcı hesabına başvuracağız: *Megan* için *meganb* ve *Alex* için *alexw*. |

2. Kullanıcı hesabı profilleriniz için hangi özniteliği düzenlemek istediğinizi belirleyin. Daha fazla bilgi için bkz [. Bilgi engelleri ilkeleri için öznitelikler](information-barriers-attributes.md).

3. Bir veya daha fazla kullanıcı hesabını, önceki adımda seçtiğiniz özniteliğin değerlerini içerecek şekilde düzenleyin. Bu eylemi uygulamak için aşağıdaki yordamlardan birini kullanın:

    - Tek bir hesabı düzenlemek için bkz. [Azure Active Directory kullanarak kullanıcının profil bilgilerini ekleme veya güncelleştirme](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Birden çok hesabı düzenlemek (veya tek bir hesabı düzenlemek için PowerShell'i kullanmak) için bkz[. Office 365 PowerShell ile kullanıcı hesabı özelliklerini yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Segmenti düzenleme

Kullanıcı kesiminin tanımını düzenlemek için bu yordamı kullanın. Örneğin, bir segmentin adını veya segmente kimlerin dahil olduğunu belirlemek için kullanılan filtreyi değiştirebilirsiniz.

1. Mevcut tüm segmentleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Sözdizimi: `Get-OrganizationSegment`

    Segment türü, UserGroupFilter değeri, onu oluşturan veya en son değiştiren, GUID gibi segmentlerin ve her birinin ayrıntılarının listesini görürsünüz.

    > [!TIP]
    > Segment listenizi daha sonra başvurmak üzere yazdırın veya kaydedin. Örneğin, bir segmenti düzenlemek istiyorsanız, onun adını bilmeniz veya değeri tanımlamanız gerekir (bu, Identity parametresiyle kullanılır).

2. Bir segmenti düzenlemek için **, Identity** parametresi ve ilgili ayrıntılarla **Set-OrganizationSegment** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> Bu örnekte bölüm adını GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd* olan segment için *HRDept* olarak güncelleştirdik. |

3. Kuruluşunuz için segmentleri düzenlemeyi bitirdiğinizde, bilgi engelleri ilkelerini [tanımlayabilir](information-barriers-policies.md#step-3-create-ib-policies) veya [düzenleyebilirsiniz](#edit-a-policy) .

## <a name="edit-a-policy"></a>İlkeyi düzenleme

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Sözdizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek istediğiniz ilkeyi belirleyin. İlkenin GUID'sini ve adını not edin.

2. **Bir Identity** parametresiyle **Set-InformationBarrierPolicy** cmdlet'ini kullanın ve yapmak istediğiniz değişiklikleri belirtin.

    Örnek: *Araştırma* segmentinin *Satış* ve *Pazarlama* segmentleriyle iletişim kurmasını engellemek için bir ilke tanımlandığını varsayalım. İlke şu cmdlet kullanılarak tanımlanmıştır: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    *Araştırma* segmentindeki kişilerin yalnızca *İk* segmentindeki kişilerle iletişim kurabilmesi için bunu değiştirmek istediğimizi varsayalım. Bu değişikliği yapmak için şu cmdlet'i kullanırız: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    Bu örnekte *SegmentlerBlocked* öğesini *SegmentlerAllowed* olarak değiştirdik ve İk kesimini *belirttik* .

3. İlkeyi düzenlemeyi bitirdiğinizde değişikliklerinizi uyguladığınızdan emin olun. (Bkz [. Bilgi engeli ilkelerini uygulama](information-barriers-policies.md#step-4-apply-ib-policies).)

## <a name="set-a-policy-to-inactive-status"></a>İlkeyi etkin değil durumuna ayarlama

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Sözdizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek (veya kaldırmak) istediğiniz ilkeyi belirleyin. İlkenin GUID'sini ve adını not edin.

2. İlkenin durumunu etkin değil olarak ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini bir *Identity* parametresiyle ve *State* parametresi *Etkin Değil* olarak ayarlayın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Bu örnekte GUID *43c37853-ea10-4b90-a23d-ab8c9377247* olan bilgi engelleri ilkesi etkin değil durumuna ayarlanmıştır. |

3. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication cmdlet'ini** kullanın.

    Sözdizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler kuruluşunuz için kullanıcıya göre uygulanır. Kuruluşunuz büyükse, bu işlemin tamamlanması 24 saat (veya daha fazla) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlenmesi yaklaşık bir saat sürer.

4. Bu noktada, bir veya daha fazla bilgi engeli ilkesi etkin değil durumuna ayarlanır. Buradan aşağıdaki eylemlerden herhangi birini yapabilirsiniz:

    - Olduğu gibi tutun (etkin olmayan duruma ayarlanmış bir ilkenin kullanıcılar üzerinde hiçbir etkisi yoktur)
    - [İlkeyi düzenleme](#edit-a-policy) 
    - [İlkeyi kaldırma](#remove-a-policy)

## <a name="remove-a-policy"></a>İlkeyi kaldırma

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Sözdizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, kaldırmak istediğiniz ilkeyi belirleyin. İlkenin GUID'sini ve adını not edin. 

2. İlkenin etkin değil durumuna ayarlandığından emin olun. İlkenin durumunu etkin değil olarak ayarlamak için Set-InformationBarrierPolicy cmdlet'ini bir Identity parametresiyle ve State parametresi Etkin Değil olarak ayarlayın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Bu örnekte GUID *43c37853-ea10-4b90-a23d-ab8c9377247* olan bir bilgi engeli ilkesini etkin olmayan bir duruma ayarlayacağız. |

3. İlkedeki değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication cmdlet'ini** kullanın.

    Sözdizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler kuruluşunuz için kullanıcıya göre uygulanır. Kuruluşunuz büyükse, bu işlemin tamamlanması 24 saat (veya daha fazla) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlenmesi yaklaşık bir saat sürer.

4. **Remove-InformationBarrierPolicy** cmdlet'ini bir Identity parametresiyle kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Bu örnekte GUID *43c37853-ea10-4b90-a23d-ab8c93772471* olan ilkeyi kaldırıyoruz. |

    İstendiğinde değişikliği onaylayın.

## <a name="remove-a-segment"></a>Segmenti kaldırma

1. Mevcut tüm segmentleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Sözdizimi: `Get-OrganizationSegment`

    Segment türü, UserGroupFilter değeri, onu oluşturan veya en son değiştiren, GUID gibi segmentlerin ve her birinin ayrıntılarının listesini görürsünüz.

    >[!TIP]
    >Segment listenizi daha sonra başvurmak üzere yazdırın veya kaydedin. Örneğin, bir segmenti düzenlemek istiyorsanız, onun adını bilmeniz veya değeri tanımlamanız gerekir (bu, Identity parametresiyle kullanılır).

2. Kaldırılacak segmenti belirleyin ve segmentle ilişkilendirilmiş IB ilkesinin kaldırıldığından emin olun. Ayrıntılar için [bkz. İlkeyi kaldırma](#remove-a-policy) yordamı.

3. Kullanıcıların bu segmentle ilişkisini kaldırmak için kaldırılacak segmenti düzenleyin. Bu eylem segment tanımını güncelleştirir ve tüm kullanıcıları segmentten kaldırır. Kaldırmadan önce kullanıcıları segmentten ayırmak için UserGroupFilter parametresini kullanacaksınız.

    Bir segmenti düzenlemek için *, Identity* parametresi ve ilgili ayrıntılarla **Set-OrganizationSegment** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan segment için bölüm adını, kullanıcıları segmentten kaldırmak için *FakeDept* olarak tanımladık. Bu örnek *Department* özniteliğini kullanır, ancak diğer öznitelikleri uygun şekilde kullanabilirsiniz. Örnekte *FakeDept* kullanılır çünkü bu mevcut değildir ve kullanıcı içermediğinden emindir. |

4. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication cmdlet'ini** kullanın.

    Sözdizimi: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*CleanupGroupSegmentLink* özniteliği, kullanıcı ilişkilendirmesi olmayan kesimle grup ilişkilendirmelerini kaldırır.

    Değişiklikler kuruluşunuz için kullanıcıya göre uygulanır. Kuruluşunuz büyükse, bu işlemin tamamlanması 24 saat (veya daha fazla) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlenmesi yaklaşık bir saat sürer.

5. Bir segmenti kaldırmak için *, Kimlik* parametresi ve ilgili ayrıntılarla **Remove-OrganizationSegment** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan kesim kaldırılmıştır. |

## <a name="remove-a-policy-and-segment"></a>İlkeyi ve segmenti kaldırma

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Sözdizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, kaldırmak istediğiniz ilkeyi belirleyin. İlkenin GUID'sini ve adını not edin.

2. Mevcut tüm segmentleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Sözdizimi: `Get-OrganizationSegment`

    Segment türü, *UserGroupFilter* parametre değeri, bunu oluşturan veya en son değiştiren, GUID vb. gibi segmentlerin ve ayrıntıların listesini görürsünüz.

    >[!TIP]
    >Segment listenizi daha sonra başvurmak üzere yazdırın veya kaydedin. Örneğin, bir segmenti düzenlemek istiyorsanız, onun adını bilmeniz veya değeri tanımlamanız gerekir (bu, Identity parametresiyle kullanılır).

3. Kaldırılacak ilkenin durumunu devre dışı olarak ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini bir *Identity* parametresiyle ve *State* parametresi *Etkin Değil* olarak ayarlayın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> Bu örnekte GUID 43c37853-ea10-4b90-a23d-ab8c93772471 olan bir bilgi engeli ilkesini etkin olmayan bir duruma ayarlayacağız. |

4. Kullanıcıların bu segmentle ilişkisini kaldırmak için kaldırılacak segmenti düzenleyin. Bu eylem segment tanımını güncelleştirir ve tüm kullanıcıları segmentten kaldırır. Kaldırmadan önce kullanıcıları segmentten ayırmak için *UserGroupFilter* parametresini kullanacaksınız.

    Bir segmenti düzenlemek için *, Identity* parametresi ve ilgili ayrıntılarla **Set-OrganizationSegment** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan segment için bölüm adını *FakeDept* olarak güncelleştirerek kullanıcıları segmentten kaldırdık. Bu örnek *Department* özniteliğini kullanır, ancak diğer öznitelikleri uygun şekilde kullanabilirsiniz. Örnekte *FakeDept* kullanılır çünkü bu mevcut değildir ve kullanıcı içermediğinden emindir. |

5. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication cmdlet'ini** kullanın.

    Sözdizimi: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*CleanupGroupSegmentLink* özniteliği, kullanıcı ilişkilendirmesi olmayan kesimle grup ilişkilendirmelerini kaldırır.

    Değişiklikler kuruluşunuz için kullanıcıya göre uygulanır. Kuruluşunuz büyükse, bu işlemin tamamlanması 24 saat (veya daha fazla) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlenmesi yaklaşık bir saat sürer.

6. **Remove-InformationBarrierPolicy** cmdlet'ini bir *Identity* parametresiyle kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Bu örnekte GUID *43c37853-ea10-4b90-a23d-ab8c93772471* olan ilke kaldırılmıştır. |

    İstendiğinde değişikliği onaylayın.

7. Bir segmenti kaldırmak için *, Kimlik* parametresi ve ilgili ayrıntılarla **Remove-OrganizationSegment** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan kesim kaldırıldı. |

## <a name="stop-a-policy-application"></a>İlke uygulamasını durdurma

Bilgi engeli ilkelerini uygulamaya başladıktan sonra, bu ilkelerin uygulanmasını durdurmak istiyorsanız aşağıdaki yordamı kullanın. İşlemin başlaması yaklaşık 30-35 dakika sürer.

1. En son bilgi engelleri ilkesi uygulamasının durumunu görüntülemek için **Get-InformationBarrierPoliciesApplicationStatus cmdlet'ini** kullanın.

    Sözdizimi: `Get-InformationBarrierPoliciesApplicationStatus`

    Uygulamanın GUID değerini not edin.

2. Bir Identity parametresiyle **Stop-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    |**Sözdizimi**|**Örnek**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> Bu örnekte, bilgi engeli ilkelerinin uygulanmasını durduruyoruz. |

## <a name="resources"></a>Kaynaklar

- [Bilgi engellerine genel bakış edinin](information-barriers.md)
- [Bilgi engelleri için ilke tanımlama](information-barriers-policies.md)
- [Microsoft Teams'de bilgi engelleri hakkında daha fazla bilgi edinin](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'daki bilgi engelleri hakkında daha fazla bilgi edinin](/sharepoint/information-barriers)
- [OneDrive'daki bilgi engelleri hakkında daha fazla bilgi edinin](/onedrive/information-barriers)
- [IB ilkeleri için öznitelikler](information-barriers-attributes.md)
- [Sorun giderme bilgileri engelleri](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
