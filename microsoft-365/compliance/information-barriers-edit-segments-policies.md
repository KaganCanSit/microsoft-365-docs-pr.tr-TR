---
title: Bilgi engellerini yönetme ilkeleri
description: Bilgi engellerini ortadan kaldırmak için ilkeleri ve kesimleri düzenlemeyi ve kaldırmayı öğrenin.
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
ms.openlocfilehash: fc8cc7e4fcbfb9fe9c2ee0f1c531511d9c2fa0b6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634371"
---
# <a name="manage-information-barriers-policies"></a>Bilgi engellerini yönetme ilkeleri

Bilgi [engellerini tanımdikten sonra](information-barriers-policies.md), sorun gidermenin bir parçası olarak veya düzenli bakım için ilkelerde veya kullanıcı [kesimlerinde değişiklik](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) yapabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|**Eylem**|**Açıklama**|
|:---------|:--------------|
| [Kullanıcı hesabı özniteliklerini düzenleme](#edit-user-account-attributes) | Segmentleri tanımlamak Azure Active Directory özelliklerde öznitelikler doldurun. <br> Kullanıcılar olması gereken kesimlere dahil olmayan kullanıcı hesabı özniteliklerini düzenleyebilir, kullanıcıların hangi segmentlere sahip olacağını değiştirebilir veya farklı öznitelikler kullanarak kesimler tanımlayabilirsiniz. |
| [Segmenti düzenleme](#edit-a-segment) | Segmentin tanımlandığı şekilde değiştirmek istediğiniz kesimleri düzenleyin. <br> Örneğin, başlangıçta Department kullanan kesimler tanımlanmış olabilir ve şimdi *MemberOf* gibi başka bir öznitelik kullanmak *istiyor olabilir*. |
| [İlkeyi düzenleme](#edit-a-policy) | Bir ilkenin çalışma nasıl çalıştığını değiştirmek istediğiniz zaman, bilgi engeli ilkesini düzenleyin.<br> Örneğin, iki kesim arasındaki iletişimi engellemek yerine, yalnızca belirli kesimler arasında iletişimin gerçekleşmesine izin vermek istediğinize karar ve verirsiniz. |
| [İlkeyi etkin değil durumuna ayarlama](#set-a-policy-to-inactive-status) |Bir ilkede değişiklik yapmak istediğiniz veya ilkenin etkin durumda etkin olmadığınız bir durumda ilkeyi etkin olmayacak şekilde ayarlayın. |
| [İlkeyi kaldırma](#remove-a-policy) | Belirli bir ilkeye artık ihtiyacınız kalmadan, bilgi engellerini ortadan kaldırın. |
| [Segmenti kaldırma](#remove-a-segment) | Belirli bir segmente artık ihtiyacınız kalmadan, bilgi engellerini ortadan kaldırın. |
| [İlkeyi ve segmenti kaldırma](#remove-a-policy-and-segment) | Aynı anda bir bilgi engeli ilkesi ve segmenti kaldırın. |
| [İlke uygulamasını durdurma](#stop-a-policy-application) | Bilgi engeli ilkelerini uygulama sürecini durdurmak istediğiniz zaman bu eylemi benimsersiniz. <br> İlke uygulamasının durdurulması anında değildir ve kullanıcılara önceden uygulanmış olan ilkeleri geri almaz. |
| [Bilgi engellerine yönelik ilkeleri tanımlama](information-barriers-policies.md) | Bu tür ilkeler henüz yoksa ve belirli kullanıcı grupları arasındaki iletişimleri kısıtlamanız veya sınırlandırmanız gereken bir bilgi engeli ilkesi tanımlayın. |
| [Bilgi engellerini giderme](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Bilgi engelleriyle ilgili beklenmeyen sorunlar ile karşılaş karşı karşıyayken bu makaleye bakın. |

>[!IMPORTANT]
>Bu makalede açıklanan görevleri gerçekleştirmek için, size uygun bir rol atanmalı, örneğin:<br>- Microsoft 365 Kurumsal Yönetici<br>- Genel Yönetici<br>- Uyumluluk Yöneticisi<br>- IB Uyumluluk Yönetimi (bu yeni bir rol!)<br><br>Bilgi engeli önkoşulları hakkında daha fazla bilgi edinmek için, Önkoşullar [(bilgi engeli ilkeleri için) bakın](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met).<br><br> Güvenlik ve Uyumluluk [Merkezi PowerShell'e & emin olun](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Kullanıcı hesabı özniteliklerini düzenleme

Kullanıcıların bölüm oluşturmada kullanılan özniteliklerini düzenlemek için bu yordamı kullanın. Örneğin, bir Department özniteliği kullanıyorsanız ve şu anda bir veya birden çok kullanıcı hesabında Department için hiçbir değer listelenmiyorsa, o kullanıcı hesaplarını Departman bilgilerini içerecek şekilde düzenlemeniz gerekir. Kullanıcı hesabı öznitelikleri, bilgi engeli ilkelerinin atanabilir olması için kesimleri tanımlamak için kullanılır.

1. Öznitelik değerleri ve atanmış segmentler gibi belirli bir kullanıcı hesabının ayrıntılarını görüntülemek için Identity parametreleriyle **Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her bir kişiyi benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. <br> (Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> Bu örnekte, Office 365'de iki kullanıcı hesabına başvururuz: *İbrhan için ayses* *ve* *Alex* *için alexw*. |

2. Kullanıcı hesabı profilleriniz için hangi öznitelikleri düzenlemek istediğinize karar olun. Daha fazla bilgi için bkz [. Bilgi engeli ilkeleri için öznitelikler](information-barriers-attributes.md).

3. Bir veya birden çok kullanıcı hesabını, önceki adımda seçtiğiniz özniteliğin değerlerini içerecek şekilde düzenleyin. Bu eylemi gerçekleştirmek için aşağıdaki yordamlardan birini kullanın:

    - Tek bir hesabı düzenlemek için bkz. Hesap bilgilerini kullanarak [kullanıcının profil bilgilerini ekleme Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Birden çok hesabı düzenlemek için (veya tek bir hesabı düzenlemek için PowerShell kullanarak), bkz. [PowerShell'i kullanarak kullanıcı Office 365 yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Segmenti düzenleme

Bir kullanıcı kesiminin tanımını düzenlemek için bu yordamı kullanın. Örneğin, bir segmentin adını veya segmente kimlerin dahil olduğunu belirlemek için kullanılan filtreyi değiştirebilirsiniz.

1. Var olan tüm kesimleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Söz dizimi: `Get-OrganizationSegment`

    Segment türü, kullanıcı GrubuFiltresi değeri, bunu en son oluşturan veya en son değiştiren, GUID gibi her kesim için bir kesimler ve ayrıntılar listesi görüntülenir.

    > [!TIP]
    > Daha sonra referans olarak etmek üzere kesimler listenizi yazdırarak veya kaydedin. Örneğin, bir segmenti düzenlemek için segmentin adını bilmek veya değeri tanımlamaniz gerekir (Identity parametresiyle kullanılır).

2. Bir segmenti düzenlemek için **Set-OrganizationSegment** cmdlet'ini Identity parametresi ve **ilgili** ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> Bu örnekte, bölüm adını GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd* ile segment için *HRDept* olarak güncellemiştir. |

3. Kuruluş için kesimleri düzenlemeyi bitirdikten sonra, [bilgi engeli](information-barriers-policies.md#step-3-define-information-barrier-policies) ilkelerini [tanımlayabilir veya](#edit-a-policy) düzenleyebilirsiniz.

## <a name="edit-a-policy"></a>İlkeyi düzenleme

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun.

2. **Bir Identity parametresiyle Set-InformationBarrierPolicy** cmdlet'ini kullanın ve yapmak istediğiniz değişiklikleri belirtin.

    Örnek: Araştırma kesiminin Satış ve Pazarlama segmentleriyle *iletişim* kurmalarını engellemek için bir *ilkenin tanımlandığı* *varsayalım* . İlke şu cmdlet kullanılarak tanımlanmıştır: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Araştırma segmentinde yer alan kişilerin yalnızca İk *segmentinde yer* alan kişiler ile iletişim kuracak şekilde değiştirmesini *istediğiniz varsayalım* . Bu değişikliği yapmak için şu cmdlet'i kullanıruz: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    Bu örnekte, *SegmentsBlocked'i SegmentsAllowed* *olarak değiştirdik* ve *İk segmentini* belirttik.

3. İlkeyi düzenlemeyi bitirdikten sonra, değişikliklerinizi uygulamak için emin olun. (Bkz [. Bilgi engeli ilkelerini uygulama](information-barriers-policies.md#step-4-apply-information-barrier-policies).)

## <a name="set-a-policy-to-inactive-status"></a>İlkeyi etkin değil durumuna ayarlama

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, değiştirmek (veya kaldırmak) istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun.

2. İlkenin durumunu etkin değil olarak ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini Identity parametresi ve *Etkin* Değil olarak ayarlanmış *State* *parametresini kullanın*.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Bu örnekte, GUID *43c37853-ea10-4b90-a23d-ab8c9377247* ile ilgili bilgi engeli ilkesi etkin değil durumuna ayarlanmıştır. |

3. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler, kurum için kullanıcı tarafından uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.

4. Bu noktada, bir veya birden çok bilgi engeli ilkeleri etkin olmayan durum olarak ayarlanmıştır. Buradan, aşağıdaki işlemlerden herhangi birini yapabilirsiniz:

    - Olduğu gibi tut (etkin olmayan durum olarak ayarlanmış bir ilkenin kullanıcılar üzerinde hiçbir etkisi yoktur)
    - [İlkeyi düzenleme](#edit-a-policy) 
    - [İlkeyi kaldırma](#remove-a-policy)

## <a name="remove-a-policy"></a>İlkeyi kaldırma

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, kaldırmak istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun. 

2. İlkenin etkin değil durumuna ayarlanmış olduğundan emin olun. İlkenin durumunu etkin değil olarak ayarlamak için, identity parametresiyle birlikte Set-InformationBarrierPolicy ve State parametresi DeActive olarak ayarlanmış olan cmdlet'i kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Bu örnekte, etkin olmayan durumu guid *43c37853-ea10-4b90-a23d-ab8c9377247* olan bir bilgi engeli ilkesi ayarladık. |

3. Değişikliklerinizi ilkeye uygulamak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication`

    Değişiklikler, kurum için kullanıcı tarafından uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.

4. **Bir Identity parametresiyle Remove-InformationBarrierPolicy** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Bu örnekte, GUID *43c37853-ea10-4b90-a23d-ab8c93772471 ilkeyi kaldırmıştık*. |

    Sorulsa, değişikliği onaylayın.

## <a name="remove-a-segment"></a>Segmenti kaldırma

1. Var olan tüm kesimleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Söz dizimi: `Get-OrganizationSegment`

    Segment türü, kullanıcı GrubuFiltresi değeri, bunu en son oluşturan veya en son değiştiren, GUID gibi her kesim için bir kesimler ve ayrıntılar listesi görüntülenir.

    >[!TIP]
    >Daha sonra referans olarak etmek üzere kesimler listenizi yazdırarak veya kaydedin. Örneğin, bir segmenti düzenlemek için segmentin adını bilmek veya değeri tanımlamaniz gerekir (Identity parametresiyle kullanılır).

2. Kaldırılacak segmenti belirleyin ve segmentle ilişkilendirilmiş IB ilkesi'nin kaldırılmış olduğundan emin olun. Ayrıntılar için [İlkeyi kaldırma](#remove-a-policy) yordamına bakın.

3. Kullanıcıların bu segmentle ilişkisini kaldırmak için kaldırılacak olan segmenti düzenleyin. Bu eylem segment tanımını günceller ve segmentten tüm kullanıcıları kaldırır. Kaldırmadan önce segmentten kullanıcıların ilişkilendirilmelerini için UserGroupFilter parametresini kullanacağız.

    Bir segmenti düzenlemek için **Set-OrganizationSegment** cmdlet'ini Identity parametresi ve *ilgili* ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan segment için bölüm adını, segmentden kullanıcıları çıkarmak için *Sahte* Bölüm olarak tanımlamıştık. Bu örnekte *Department özniteliği* uygundur, ancak uygun olan başka öznitelikler de kullanabilirsiniz. Bu örnekte *SahteDept* kullanımı vardır, çünkü bu yoktur ve herhangi bir kullanıcı içermeyer. |

4. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*CleanupGroupSegmentLink* özniteliği, kullanıcı ilişkisi olmayan segmentle grup ilişkilendirmelerini kaldırır.

    Değişiklikler, kurum için kullanıcı tarafından uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.

5. Segmenti kaldırmak için **Remove-OrganizationSegment** cmdlet'ini *Identity* parametresi ve ilgili ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan segment kaldırılmıştır. |

## <a name="remove-a-policy-and-segment"></a>İlkeyi ve segmenti kaldırma

1. Geçerli bilgi engeli ilkelerinin listesini görüntülemek için **Get-InformationBarrierPolicy** cmdlet'ini kullanın.

    Söz dizimi: `Get-InformationBarrierPolicy`

    Sonuç listesinde, kaldırmak istediğiniz ilkeyi seçin. İlkenin GUID ve adını notun.

2. Var olan tüm kesimleri görüntülemek için **Get-OrganizationSegment** cmdlet'ini kullanın.

    Söz dizimi: `Get-OrganizationSegment`

    Segment türü, *UserGroupFilter* parametre değeri, bunu en son oluşturan veya değiştiren, GUID gibi her kesim için bir kesimler ve ayrıntılar listesi görüntülenir.

    >[!TIP]
    >Daha sonra referans olarak etmek üzere kesimler listenizi yazdırarak veya kaydedin. Örneğin, bir segmenti düzenlemek için segmentin adını bilmek veya değeri tanımlamaniz gerekir (Identity parametresiyle kullanılır).

3. Devre dışı olarak kaldırılacak ilkenin durumunu ayarlamak için **Set-InformationBarrierPolicy** cmdlet'ini *Identity* parametresi ve Etkin Değil olarak ayarlanmış *State* *parametresiyle kullanın*.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> Bu örnekte, etkin olmayan durumu GUID 43c37853-ea10-4b90-a23d-ab8c93772471 olan bir bilgi engeli ilkesi ayarladık. |

4. Kullanıcıların bu segmentle ilişkisini kaldırmak için kaldırılacak olan segmenti düzenleyin. Bu eylem segment tanımını günceller ve segmentten tüm kullanıcıları kaldırır. Kaldırmadan önce segmentten kullanıcıların ilişkilendirilmelerini için *UserGroupFilter* parametresini kullanacağız.

    Bir segmenti düzenlemek için **Set-OrganizationSegment** cmdlet'ini Identity parametresi ve *ilgili* ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Bu örnekte, GUID c96e0837-c232-4a8a-841e-ef45787d8fcd olan segment için, bölüm adını Sahte Bölüm olarak güncelledirerek segmentten kullanıcıları  çıkarabilirsiniz. Bu örnekte *Department özniteliği* uygundur, ancak uygun olan başka öznitelikler de kullanabilirsiniz. Bu yoktur *ve kullanıcı içermeye* kesin olduğu için örnekte SahteDept 2013 2013 2013 2013 02/2013 07/2013 |

5. Değişikliklerinizi uygulamak için **Start-InformationBarrierPoliciesApplication** cmdlet'ini kullanın.

    Söz dizimi: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*CleanupGroupSegmentLink* özniteliği, kullanıcı ilişkisi olmayan segmentle grup ilişkilendirmelerini kaldırır.

    Değişiklikler, kurum için kullanıcı tarafından uygulanır. Büyük bir kurumsanız, bu sürecin tamamlanması 24 saat (veya daha uzun) sürebilir. Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.

6. **Bir Identity parametresiyle Remove-InformationBarrierPolicy** cmdlet'ini kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Bu örnekte, GUID *43c37853-ea10-4b90-a23d-ab8c93772471* ilke kaldırılmıştır. |

    Sorulsa, değişikliği onaylayın.

7. Segmenti kaldırmak için **Remove-OrganizationSegment** cmdlet'ini *Identity* parametresi ve ilgili ayrıntılarla kullanın.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Bu örnekte GUID c96e0837-c232-4a8a-841e-ef45787d8fcd ile segment kaldırılmıştır. |

## <a name="stop-a-policy-application"></a>İlke uygulamasını durdurma

Bilgi engeli ilkeleri uygulamaya başladıktan sonra, bu ilkelerin uygulanmalarını durdurmak için aşağıdaki yordamı kullanın. İşlem yaklaşık 30-35 dakika sürer.

1. En son bilgi engellerinin ilke uygulamasının durumunu görüntülemek için **, Get-InformationBarrierPoliciesApplicationStatus** cmdlet'ini kullanın.

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