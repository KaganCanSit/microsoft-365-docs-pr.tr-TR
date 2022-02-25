---
title: Bilgi engellerini giderme
description: Bilgi engellerini gidermek için bu makaleyi kılavuz olarak kullanın.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de415ba7b68df786ead038bb72465c445a86ba5a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2021
ms.locfileid: "62959915"
---
# <a name="troubleshooting-information-barriers"></a>Bilgi engellerini giderme

[Bilgi engelleri](information-barriers.md) , yasal gereksinimler ve endüstri düzenlemeleriyle uyumlu kalmalarına yardımcı olabilir. Örneğin, bilgi engelleriyle, ilgi alanı çakışması veya başka sorunlar önlemek için belirli kullanıcı grupları arasındaki iletişimi kısıtabilirsiniz. (Bilgi engellerini ayarlama hakkında daha fazla bilgi edinmek için bkz. [Bilgi engelleri için ilkeler tanımlama](information-barriers-policies.md).)

Bilgi engelleri gerçekleştikten sonra kişilerin beklenmedik sorunlar ile karşılaşması durumunda, bu sorunları çözmek için bazı adımlar atabilirsiniz. Bu makaleyi kılavuz olarak kullanın.

> [!IMPORTANT]
> Bu makalede açıklanan görevleri gerçekleştirmek için, size uygun bir rol atanmalı, örneğin:<br/>- Microsoft 365 Kurumsal Yönetici'ye başvurun<br/>- genel yönetici<br/>- Uyumluluk Yöneticisi<br/>- IB Uyumluluk Yönetimi (bu yeni bir rol!)<p>Bilgi engeli önkoşulları hakkında daha fazla bilgi edinmek için bkz. [Önkoşullar (bilgi engeli ilkeleri için).](information-barriers-policies.md#prerequisites)<p>Güvenlik ve Uyumluluk [Merkezi PowerShell& e bağlanın](/powershell/exchange/connect-to-scc-powershell).

## <a name="issue-users-are-unexpectedly-blocked-from-communicating-with-others-in-microsoft-teams"></a>Sorun: Kullanıcıların iş yerlerinde başka kullanıcılarla iletişim kurmaları beklenmedik bir Microsoft Teams 

Bu durumda, kişiler iş yerlerinde diğerleriyle iletişim kurarken beklenmeyen Microsoft Teams. Bazı örnekler:

- Bir kullanıcı arama yaptı ancak bulamıyor; diğer bir kullanıcı Microsoft Teams.
- Bir kullanıcı belgesinde başka bir kullanıcı bulabilir, ancak Microsoft Teams.
- Kullanıcı başka bir kullanıcı görebilir, ancak başka bir kullanıcıya kendisinde ileti Microsoft Teams.

### <a name="what-to-do"></a>Ne yapmalı?

Kullanıcıların bir bilgi engeli ilkesiden etkilendiğini saptayın. İlkelerin nasıl yapılandırıldıklerine bağlı olarak, bilgi engelleri beklendiği gibi çalışıyor olabilir. Ya da, kurum ilkelerinizi geliştirmeniz de gerekir.

1. **Identity parametresiyle Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın. 

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity` <p> Ad, Diğer Ad, Ayırt Edici ad (DN), Kurallı DN, E-posta adresi veya GUID gibi her alıcıyı benzersiz olarak tanımlayan herhangi bir kimlik değerini kullanabilirsiniz. |`Get-InformationBarrierRecipientStatus -Identity meganb` <p> Bu örnekte, Identity parametresi için bir diğer ad (*herb*) kullanıyoruz. Bu cmdlet, kullanıcının bir bilgi engeli ilkesiten etkilendiğini gösteren bilgileri sağlar. (*ExoPolicyId: \<GUID>.) |

    **Kullanıcılar bilgi engeli ilkelerine dahil değilse destekle iletişime geçin**. Aksi takdirde, sonraki adıma geçin.

2. Bir bilgi engeli ilkesinde hangi kesimlerin yer alıyor olduğunu bulun. Bunu yapmak için, `Get-InformationBarrierPolicy` cmdlet'i Identity parametresiyle birlikte kullanın. 

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierPolicy` <p> Önceki adımda alınan GUID (ExoPolicyId) ilkesi gibi ayrıntıları bir kimlik değeri olarak kullanın. | `Get-InformationBarrierPolicy -Identity b42c3d0f-49e9-4506-a0a5-bf2853b5df6f` <p> Bu örnekte, ExoPolicyId *b42c3d0f-49e9-4506-a0a5-bf2853b5df6f* ile ilgili bilgi engeli ilkesi hakkında ayrıntılı bilgi aacağız. |

    Cmdlet'i çalıştırdikten sonra, sonuçlarda **AtananSegment**, **SegmentsAllowed** ve **SegmentsBlocked değerlerine** bakın.

    Örneğin, `Get-InformationBarrierPolicy` cmdlet'i çalıştırdikten sonra sonuç listemizde şunları gördük:

    ```powershell
    AssignedSegment : Sales
    SegmentsAllowed : {}
    SegmentsBlocked : {Research}
    ```

    Bu durumda, bir bilgi engeli ilkesiyle Satış ve Araştırma segmentlerinde yer alan kişilerin etkileyeceğini görebiliriz. Bu durumda, Satış ekibinde yer alan kişilerin Araştırma'daki insanlarla iletişim kurması engel oluyor.

    Bu doğru görünüyorsa, bilgi engelleri beklendiği gibi çalışıyor olur. Düzelmemişse, sonraki adıma geçin.

3. Kesimlerinizi doğru tanımlandığından emin olun. Bunu yapmak için, `Get-OrganizationSegment` cmdlet'i kullanın ve sonuç listesini gözden geçirin.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-OrganizationSegment`<p> Bu cmdlet'i Bir Identity parametresiyle kullanın. | `Get-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <p> Bu örnekte, GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd'a* sahip olan segment hakkında bilgi alıyoruz. |

    Segmentin ayrıntılarını gözden geçirebilirsiniz. Gerekirse, [bir segmenti](information-barriers-edit-segments-policies.md#edit-a-segment) düzenleyin ve ardından cmdlet'i `Start-InformationBarrierPoliciesApplication` yeniden kullanın.

    **Bilgi engeli ilkeniz ile ilgili sorunlarınız devam ediyorsa destek ile iletişime geçin**.

## <a name="issue-communications-are-allowed-between-users-who-should-be-blocked-in-microsoft-teams"></a>Sorun: aynı anda engellenmiş olması gereken kullanıcılar arasındaki iletişim Microsoft Teams

Bu durumda, bilgi engelleri tanımlanmış, etkin ve uygulanmış olsa da, bir şekilde birbirleriyle iletişim kurmasını engelleyen kişiler bir şekilde iletişim kurmadan sohbet edip birbirlerine çağrı Microsoft Teams.

### <a name="what-to-do"></a>Ne yapmalı?

Söz konusu kullanıcıların bilgi engeli ilkesine dahil olduğunu doğrulayın. 

1. **Identity parametreleriyle Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın.

    |**Söz dizimi** _|_ *Örnek**|
    |:----------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her bir kişiyi benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Bu örnekte, Office 365'te iki kullanıcı hesabına başvururuz: İbrhan için *asi* ve *Alex* *için alexw*. |

    > [!TIP]
    > Bu cmdlet'i tek bir kullanıcı için de kullanabilirsiniz: `Get-InformationBarrierRecipientStatus -Identity <value>`

2. Bulguları gözden geçirin. **Get-InformationBarrierRecipientStatus** cmdlet'i, öznitelik değerleri ve uygulanan herhangi bir bilgi engeli ilkeleri gibi kullanıcılar hakkında bilgi döndürür.

    Sonuçları gözden geçirin ve aşağıdaki tabloda açıklandığı gibi sonraki adımları uygulayın:

    |**Sonuçlar**|**Sırada ne var?**|
    |:----------|:------------------|
    | Seçilen kullanıcılar için hiçbir kesim listelenmiyor | Şunlardan birini yapın:<br/>- Kullanıcıların profillerini farklı bir bölümde düzenleyerek mevcut bir segmente Azure Active Directory. (Bkz[. Kullanıcı hesabı özelliklerini Office 365 PowerShell ile yapılandırma](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).)<br/>- Bilgi engelleri için desteklenen [bir özniteliği kullanarak bir segment tanımlayın](information-barriers-attributes.md). Ardından, yeni [bir ilke tanımlayın veya](information-barriers-policies.md#part-2-define-information-barrier-policies) mevcut [bir ilkeyi bu segmenti](information-barriers-edit-segments-policies.md#edit-a-policy) içerecek şekilde düzenleyin. |
    | Kesimler listelenir, ancak bu kesimlere bilgi engeli ilkeleri atanmaz | Şunlardan birini yapın:<br/>- [Söz konusu her bölüm için yeni](information-barriers-policies.md#part-2-define-information-barrier-policies) bir bilgi engeli ilkesi tanımlama <br/>- [Mevcut bilgi engeli politikasını düzenleyemez](information-barriers-edit-segments-policies.md#edit-a-policy) ve doğru segmente atama |
    | Kesimler listelenir ve her biri bir bilgi engeli ilkesine dahil edilir | - Bilgi engeli `Get-InformationBarrierPolicy` ilkelerinin etkin olduğunu doğrulamak için cmdlet'i çalıştırın<br/>- İlkelerin `Get-InformationBarrierPoliciesApplicationStatus` uygulandığını onaylamak için cmdlet'i çalıştırın<br/>- Tüm etkin bilgi `Start-InformationBarrierPoliciesApplication` engeli ilkelerini uygulamak için cmdlet'i çalıştırın |

## <a name="issue-i-need-to-remove-a-single-user-from-an-information-barrier-policy"></a>Sorun: Bilgi engeli ilkesinden tek bir kullanıcıyı kaldırmam gerekiyor

Bu durumda, bilgi engeli ilkelerinin yürürlüğe girecek ve bir veya birden çok kullanıcının iş yerlerinde diğer kullanıcılarla iletişim kurması Microsoft Teams. Bilgi engeli ilkelerini tamamen kaldırmak yerine, bir veya birden çok kullanıcının bilgi engeli ilkelerini kaldırabilirsiniz.

### <a name="what-to-do"></a>Ne yapmalı?

Bilgi engeli ilkeleri, kullanıcıların kesimlerine atanır. Kesimler, kullanıcı hesabı [profillerinde bazı öznitelikler kullanılarak tanımlanır](information-barriers-attributes.md). Tek bir kullanıcıdan ilkeyi kaldırmanız gerekirse, kullanıcının profillerini Azure Active Directory engellerinden etkilenen bir segmente artık dahil olmayacak şekilde düzenlemeyi düşünebilirsiniz.

1. **Identity parametreleriyle Get-InformationBarrierRecipientStatus** cmdlet'ini kullanın. Bu cmdlet, öznitelik değerleri ve uygulanan herhangi bir bilgi engeli ilkeleri gibi kullanıcılarla ilgili bilgileri döndürür.

    |**Söz dizimi**|**Örnek**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi her bir kişiyi benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz. | `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Bu örnekte, Office 365'te iki kullanıcı hesabına başvururuz: İbrhan için *asi* ve *Alex* *için alexw*.          |
    | `Get-InformationBarrierRecipientStatus -Identity <value>` <p> Ad, diğer ad, ayırt edici ad, kurallı etki alanı adı, e-posta adresi veya GUID gibi kullanıcıyı benzersiz olarak tanımlayan herhangi bir değeri kullanabilirsiniz.|`Get-InformationBarrierRecipientStatus -Identity jeanp`<p> Bu örnekte, Office 365: zaman içinde tek bir hesaba *başvururuz*. |

2. Bilgi engeli ilkelerinin atandığı ve kullanıcının hangi segmentlere ait olduğunu görmek için sonuçları gözden geçirebilirsiniz.

3. Bilgi engellerinden etkilenen bir segmentten kullanıcı kaldırmak için kullanıcının profil bilgilerini güncelleştirmenin ardından bu [bölümde Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

4. FwdSync'in gerçekleşmesi için 30 dakika kadar bekleyin. Veya tüm etkin bilgi engeli `Start-InformationBarrierPoliciesApplication` ilkelerini uygulamak için cmdlet'i çalıştırın.

## <a name="issue-the-information-barrier-application-process-is-taking-too-long"></a>Sorun: Bilgi engeli uygulama süreci çok uzun alıyor

**Start-InformationBarrierPoliciesApplication** cmdlet'ini çalıştırdikten sonra, bu işlemi bitirmek çok uzun zaman alıyor.

### <a name="what-to-do"></a>Ne yapmalı?

İlke uygulaması cmdlet'ini çalıştırsanız, kuruluş tüm hesaplarda bilgi engeli ilkelerinin kullanıcı tarafından kullanıcıya uygulanıyor (veya kaldırılıyor) olduğunu unutmayın. Çok fazla kullanıcınız varsa işlemesi biraz zaman alır. (Genel bir kılavuz olarak, 5.000 kullanıcı hesabının işlemesi yaklaşık bir saat sürer.)

1. En son **ilke uygulamasının durumunu doğrulamak için Get-InformationBarrierPoliciesApplicationStatus** cmdlet'ini kullanın.

    |**En son ilke uygulamasını görüntülemek için**|**Tüm ilke uygulamalarının durumunu görüntülemek için**|
    |:---------------------------------------------|:---------------------------------------------|
    | `Get-InformationBarrierPoliciesApplicationStatus` | `Get-InformationBarrierPoliciesApplicationStatus -All $true` |

    Bu, ilke uygulamasının tamamlandı mı, başarısız mı yoksa devam mı olduğuyla ilgili bilgileri görüntüler.

2. Önceki adımın sonuçlarına bağlı olarak, aşağıdaki adımlardan birini uygulayın:
  
    |**Durum**|**Sonraki adım**|
    |:---------|:------------|
    | **Başlamadı** | **Start-InformationBarrierPoliciesApplication** cmdlet'inden bu yana 45 dakikadan uzun bir süre geçtiyseniz, ilke tanımlarında hata olup olmadığını veya uygulamanın başlamama nedenini görmek için denetim günlüğünizi gözden geçirin. |
    | **Başarısız** | Uygulama başarısız olursa, denetim günlüğünizi gözden geçirebilirsiniz. Ayrıca, kesimlerinizi ve ilkelerinizi gözden geçirebilirsiniz. Birden fazla segmente atanmış kullanıcı var mı? Birden fazla poliic atanmış herhangi bir kesim var mı? Gerekirse, [kesimleri ve](information-barriers-edit-segments-policies.md#edit-a-segment) /veya ilkeleri [düzenleyin](information-barriers-edit-segments-policies.md#edit-a-policy) ve ardından **Start-InformationBarrierPoliciesApplication** cmdlet'ini yeniden çalıştırın. |
    | **Devam ediyor** | Uygulama hala devam ediyorsa, tamamlanması için daha fazla süre bekleyin. Birkaç gün içinde denetim günlüklerinizi toplayın ve sonra destek ile iletişime geçin. |

## <a name="issue-information-barrier-policies-are-not-being-applied-at-all"></a>Sorun: Bilgi engeli ilkeleri uygulanıyor

Bu durumda, tanımlı kesimlere, tanımlı bilgi engeli ilkelerine ve bu ilkeleri uygulamaya çalıştısınız. Bununla birlikte, `Get-InformationBarrierPoliciesApplicationStatus` cmdlet'i çalıştırarak ilke uygulamasının başarısız olduğunu da görüyorsunuz.

### <a name="what-to-do"></a>Ne yapmalı?

Kuruluşta adres defteri ilkelerinin Exchange [emin](/exchange/address-books/address-book-policies/address-book-policies) olun. Bu tür ilkeler, bilgi engeli ilkelerinin uygulanmasını engeller.

1. Bağlan [PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)

2. [Get-AddressBookPolicy](/powershell/module/exchange/get-addressbookpolicy) cmdlet'ini çalıştırın ve sonuçları gözden geçirin.

    |**Sonuçlar**|**Sonraki adım**|
    |:----------|:------------|
    | Exchange defteri ilkeleri listelenir | [Adres defteri ilkelerini kaldırma](/exchange/address-books/address-book-policies/remove-an-address-book-policy) |
    | Adres defteri ilkeleri yok |İlke uygulamasının neden başarısız olduğunu bulmak için denetim günlüklerinizi gözden geçirme |

3. [Kullanıcı hesaplarının, kesimlerin, ilkelerin veya ilke uygulamasının durumunu görüntüleme](information-barriers-policies.md#view-status-of-user-accounts-segments-policies-or-policy-application).

## <a name="issue-information-barrier-policy-not-applied-to-all-designated-users"></a>Sorun: Bilgi engeli ilkesi belirlenen tüm kullanıcılara uygulanmadı

Kesimleri tanımdikten, bilgi engeli ilkelerini tanımdikten ve bu ilkeleri uygulamaya çalıştıktan sonra, ilkenin bazı alıcılara uygulanıyor olduğunu, ancak diğer alıcılara uygulana olmadığını bulabilirsiniz.
Cmdlet'i `Get-InformationBarrierPoliciesApplicationStatus` çalıştırınca, çıktıda bunun gibi bir metin aratır.

> Kimlik: `<application guid>`
>
> Toplam Alıcı Sayısı: 81527
>
> Başarısız Alıcılar: 2
>
> Hata Kategorisi: Yok
>
> Durum: Tamamlandı

### <a name="what-to-do"></a>Ne yapmalı?

1. için denetim günlüğünde arama yapın `<application guid>`. Bu PowerShell kodunu kopyalayıp değişkenlerinizi değiştirebilirsiniz.

```powershell
$DetailedLogs = Search-UnifiedAuditLog -EndDate <yyyy-mm-ddThh:mm:ss>  -StartDate <yyyy-mm-ddThh:mm:ss> -RecordType InformationBarrierPolicyApplication -ResultSize 1000 |?{$_.AuditData.Contains(<application guid>)} 
```

2. Ve alanlarının değerleri için denetim günlüğünden ayrıntılı çıktıyı `"UserId"` `"ErrorDetails"` kontrol edin. Bu, başarısızlığın nedenini size vetir. Bu PowerShell kodunu kopyalayıp değişkenlerinizi değiştirebilirsiniz.

```powershell
   $DetailedLogs[1] |fl
```

Örneğin:

> "UserId": Kullanıcı1
>
>"ErrorDetails":"Durum: IBPolicyConflict. Hata: IB segmenti "segment id1" ve IB segmenti "segment id2" çakışmaya neden olur ve alıcıya atanamaz.

3. Genellikle, bir kullanıcının birden fazla segmente dahil olduğunu buluruz. değerini güncelleştirerek bunu `-UserGroupFilter` düzeltebilir.`OrganizationSegments`

4. Bu yordamlar Bilgi Engelleri ilkelerini kullanarak bilgi [engeli ilkelerini yeniden uygulayabilirsiniz](information-barriers-policies.md#part-3-apply-information-barrier-policies).

## <a name="resources"></a>Kaynaklar

- [Web'de bilgi engellerine yönelik ilkeler Microsoft Teams](information-barriers-policies.md)
- [Bilgi engelleri](information-barriers.md)