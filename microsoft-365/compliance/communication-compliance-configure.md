---
title: İletişim uyumluluğunu kullanmaya başlama
description: Kullanıcı iletişimlerini gözden geçirmek üzere yapılandırmak için iletişim uyumluluk ilkelerini ayarlayın.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, iletişim uyumluluğu
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: cd7ff5819f2d3927c9315e96b440a215a6e889eb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633773"
---
# <a name="get-started-with-communication-compliance"></a>İletişim uyumluluğunu kullanmaya başlama

İç veya dış gözden geçirenler tarafından incelenmek üzere kullanıcı iletişimlerini tanımlamak için iletişim uyumluluk ilkelerini kullanın. İletişim uyumluluk ilkelerinin kuruluşunuzdaki iletişimleri algılamanıza nasıl yardımcı olabileceği hakkında daha fazla bilgi için bkz. [iletişim uyumluluk ilkeleri](communication-compliance.md). Contoso'nun Microsoft Teams, Exchange Online ve Yammer iletişimlerindeki uygunsuz içeriği algılamak için iletişim uyumluluk ilkesini nasıl hızlı bir şekilde yapılandırmış olduğunu gözden geçirmek isterseniz bu [örnek olay incelemesine](communication-compliance-case-study.md) göz atın.

## <a name="subscriptions-and-licensing"></a>Abonelikler ve lisanslama

İletişim uyumluluğunu kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ve tüm eklentileri onaylamanız gerekir. İletişim uyumluluğuna erişmek ve bu uyumluluğu kullanmak için kuruluşunuzun aşağıdaki aboneliklerden veya eklentilerden birine sahip olması gerekir:

- Microsoft 365 E5/A5/F5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Insider Risk Management eklentisi
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 Kurumsal E3 aboneliği + Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz, nota bakın)

İletişim uyumluluk ilkelerine dahil olan kullanıcılara yukarıdaki lisanslardan biri atanmalıdır. Abonelikler ve lisanslama hakkında daha fazla bilgi için bkz. [Güvenlik & uyumluluğu için Microsoft 365 kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> İletişim uyumluluğu şu anda coğrafi bölgelerde ve Azure hizmet bağımlılıkları tarafından desteklenen ülkelerde barındırılan kiracılarda kullanılabilir. Kuruluşunuzda iletişim uyumluluğunu desteklediğini doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

Mevcut bir Office 365 Kurumsal E5 planınız yoksa ve iletişim uyumluluğunu denemek istiyorsanız, [microsoft 365'i](/office365/admin/try-or-buy-microsoft-365) mevcut aboneliğinize ekleyebilir veya Office 365 Kurumsal E5 [deneme sürümüne kaydolabilirsiniz](https://www.microsoft.com/microsoft-365/enterprise).

> [!NOTE]
> Office 365 Gelişmiş Uyumluluk artık tek başına abonelik olarak satılmaz. Geçerli aboneliklerin süresi dolduğunda, müşterilerin aynı veya ek uyumluluk özelliklerini içeren yukarıdaki aboneliklerden birine geçiş yapması gerekir.

## <a name="recommended-actions"></a>Önerilen eylemler

Önerilen eylemler, kuruluşunuzun iletişim uyumluluk özelliklerini kullanmaya başlamasına ve mevcut ilkelerinizden en iyi şekilde yararlanmak için yardımcı olabilir. **İlkeler** sayfasına eklenen önerilen eylemler içgörüler sağlar ve kuruluşunuzdaki iletişimlerdeki hassas bilgi türlerini ve uygunsuz içerik etkinliklerini özetler. İçgörüler [, veri sınıflandırması](data-classification-overview.md) ve duyarlılık etiketlerinin, bekletme etiketlerinin ve hassas bilgi türü sınıflandırmasının uygulanması tarafından desteklenir. Bu içgörüler, kuruluşunuzdaki kullanıcılar için kişisel bilgileri (PII) içermez.

![İletişim uyumluluğu önerilen eylemler.](../media/communication-compliance-recommended-actions.png)

Uygunsuz içerik içeren iletilerdeki etkinlik, uygunsuz içerik şablonunu veya uygunsuz içerik için [sınıflandırıcıları](/microsoft-365/compliance/communication-compliance-policies#classifiers) kullanan özel ilkeleri kullanan mevcut ilkelerden sınıflandırıcı türüne göre toplanır. İlkeleriniz için Uyarı panosunda bu iletilere yönelik uyarıları araştırın.

[Hassas bilgi türlerini](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) içeren etkinlik, mevcut ilkelerde kapsanan iletilerde ve mevcut ilkeler kapsamında olmayan iletiler için algılanır. İçgörüler, kuruluşunuzun daha önce mevcut bir iletişim uyumluluk ilkesinde tanımlanmamış olanlar da dahil olmak üzere tüm hassas bilgi türleri için toplanır. Yeni bir iletişim uyumluluk ilkesi oluşturmak veya mevcut ilkeleri güncelleştirmek için bu içgörüleri kullanın.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>1. Adım (gerekli): İletişim uyumluluğu için izinleri etkinleştirme

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdıktan sonra, rol grubu izinlerinin kuruluşunuz genelinde atanan kullanıcılara uygulanması 30 dakika kadar sürebilir.

İletişim uyumluluk özelliklerini yönetmek için ilk izinleri yapılandırmak için kullanılan altı rol grubu vardır. **İletişim uyumluluğunu** Microsoft Purview uyumluluk portalı menü seçeneği olarak kullanılabilir hale getirmek ve bu yapılandırma adımlarına devam etmek için aşağıdaki rol veya rol gruplarından birine atanmalısınız:

- Azure Active Directory [*Genel Yönetici*](/azure/active-directory/roles/permissions-reference#global-administrator) rolü
- Azure Active Directory [*Uyumluluk Yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolü
- [*kuruluş yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubunu Microsoft Purview uyumluluk portalı
- [*uyumluluk yöneticisi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubunu Microsoft Purview uyumluluk portalı
- *İletişim Uyumluluğu* rol grubu
- *İletişim Uyumluluğu Yönetici* rol grubu

Aşağıdaki rollerin üyeleri *İletişim Uyumluluğu Yönetici* rol grubuna dahil edilen çözüm izinlerine sahiptir:

- Azure Active Directory *Genel Yöneticisi*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft Purview uyumluluk portalı *Kuruluş Yönetimi*
- *Microsoft Purview uyumluluk portalı Uyumluluk Yöneticisi*

> [!IMPORTANT]
> İletişim uyumluluk yapılandırmanızın kuruluşunuzdan ayrılması durumunda iletişim uyumluluk yapılandırmanızın 'sıfır yönetici' senaryosunda yer almaması için İletişim *Uyumluluğu* veya *İletişim Uyumluluğu Yönetici* rol gruplarında (seçtiğiniz seçeneğe bağlı olarak) her zaman en az bir kullanıcınız olduğundan emin olun.

İletişim uyumluluk ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı iletişim uyumluluk özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Farklı uyumluluk özellikleri alanlarını yönetmek için farklı uyumluluk sorumluluklarına sahip kullanıcıları belirli rol gruplarına atama seçeneğiniz vardır. Ya da belirlenen yöneticiler, analistler, araştırmacılar ve görüntüleyiciler için tüm kullanıcı hesaplarını *İletişim Uyumluluğu* rol grubuna atamaya karar vekleyebilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun tek bir rol grubu veya birden çok rol grubu kullanın.

İletişim uyumluluğunu yapılandırırken ve yönetirken şu çözüm rol grubu seçeneklerinden birini belirleyin:

| Rol | Rol izinleri |
|:-----|:-----------------|
| **İletişim Uyumluluğu** | Kuruluşunuz için iletişim uyumluluğunu tek bir grupta yönetmek için bu rol grubunu kullanın. Belirlenen yöneticiler, analistler, araştırmacılar ve görüntüleyiciler için tüm kullanıcı hesaplarını ekleyerek, iletişim uyumluluk izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu tüm iletişim uyumluluk izni rollerini içerir. Bu yapılandırma, iletişim uyumluluğunu hızlı bir şekilde kullanmaya başlamanın en kolay yoludur ve ayrı kullanıcı grupları için ayrı izinlere ihtiyaç duymayan kuruluşlar için uygundur. İletişim uyumluluk yöneticisi olarak ilke oluşturan kullanıcıların posta kutuları Exchange Online barındırılmalıdır.|
| **İletişim Uyumluluğu Yönetici** | İletişim uyumluluğunu başlangıçta yapılandırmak ve daha sonra iletişim uyumluluk yöneticilerini tanımlı bir gruba ayırmak için bu rol grubunu kullanın. Bu rol grubuna atanan kullanıcılar iletişim uyumluluk ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirebilir ve silebilir. Bu rol grubuna atanan kullanıcılar ileti uyarılarını görüntüleyemez. İletişim uyumluluk yöneticisi olarak ilke oluşturan kullanıcıların posta kutuları Exchange Online barındırılmalıdır.|
| **İletişim Uyumluluğu Analisti** | İletişim uyumluluğu analistleri olarak görev yapacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, Gözden Geçiren olarak atandıkları ilkeleri görüntüleyebilir, ileti meta verilerini görüntüleyebilir (ileti içeriği değil), ek gözden geçirenlere iletebilir veya kullanıcılara bildirim gönderebilir. Analistler bekleyen uyarıları çözümleyemez. |
| **İletişim Uyumluluğu Araştırmacısı** | İletişim uyumluluk araştırmacısı olarak görev yapacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar ileti meta verilerini ve içeriğini görüntüleyebilir, ek gözden geçirenlere iletebilir, eBulma (Premium) olayına iletebilir, kullanıcılara bildirim gönderebilir ve uyarıyı çözebilir. |
| **İletişim Uyumluluğu Görüntüleyicisi** | İletişim raporlarını yönetecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluğu giriş sayfasındaki tüm raporlama pencere öğelerine erişebilir ve tüm iletişim uyumluluk raporlarını görüntüleyebilir. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Seçenek 1: Tüm uyumluluk kullanıcılarını İletişim Uyumluluğu rol grubuna atama

1. [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Güvenlik &amp; Uyumluluk Merkezi'nde **İzinler'e** gidin. Office 365 rolleri görüntülemek ve yönetmek için bağlantıyı seçin.

3. *İletişim Uyumluluğu* rol grubunu ve ardından **Rol grubunu düzenle'yi** seçin.

4. Sol gezinti **bölmesinden Üyeleri seç'i** ve ardından **Düzenle'yi** seçin.

5. **Ekle'yi** seçin ve ardından *İletişim Uyumluluğu* rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.

6. **Ekle'yi** ve ardından **Bitti'yi** seçin.

7. Kullanıcıları rol grubuna eklemek için **Kaydet'i** seçin. Adımları tamamlamak için **Kapat'ı** seçin

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>2. Seçenek: Kullanıcıları belirli iletişim uyumluluğu rol gruplarına atama

Kuruluşunuzdaki farklı kullanıcılar arasında iletişim uyumluluğu erişimini ve sorumluluklarını segmentlere ayırmak için kullanıcıları belirli rol gruplarına atamak için bu seçeneği kullanın.

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) oturum açın ve **İzinler'e**</a> gidin.

2. Office 365 rolleri görüntülemek ve yönetmek için bağlantıyı seçin.

3. İletişim uyumluluğu rol gruplarından birini ve ardından **Rol grubunu düzenle'yi** seçin.

4. Sol gezinti **bölmesinden Üyeleri seç'i** ve ardından **Düzenle'yi** seçin.

5. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.

6. **Ekle'yi** ve ardından **Bitti'yi** seçin.

7. Kullanıcıları rol grubuna eklemek için **Kaydet'i** seçin.

8. Sonraki iletişim uyumluluk rol grubunu seçin, ardından gerekli her rol grubu için 4-7 arası adımları yineleyin.

9. Adımları tamamlamak için **Kapat'ı** seçin.

Rol grupları ve izinler hakkında daha fazla bilgi için bkz. [Uyumluluk Merkezi'nde İzinler](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>2. Adım (gerekli): Denetim günlüğünü etkinleştirme

İletişim uyumluluğu için denetim günlüklerinin uyarıları göstermesi ve gözden geçirenler tarafından gerçekleştirilen düzeltme eylemlerini izlemesi gerekir. Denetim günlükleri, tanımlı bir kuruluş ilkesiyle ilişkili tüm etkinliklerin özetidir veya iletişim uyumluluk ilkesi her değiştiğinde.

Denetim, Microsoft 365 kuruluşları için varsayılan olarak etkindir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmış olabilir. Kuruluşunuzda denetim devre dışı bırakıldıysa, bunun nedeni başka bir yöneticinin kapatması olabilir. Bu adımı tamamlarken denetimi yeniden açmanın uygun olduğunu onaylamanızı öneririz.

Denetimi açmak için adım adım yönergeler için bkz. [Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açtıktan sonra, denetim günlüğünün hazırlandığını ve hazırlık tamamlandıktan birkaç saat sonra bir arama çalıştırabileceğinizi belirten bir ileti görüntülenir. Bu eylemi yalnızca bir kez yapmanız gerekir. Denetim günlüğünü kullanma hakkında daha fazla bilgi için bkz [. Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>3. Adım (isteğe bağlı): İletişim uyumluluğu için grupları ayarlama

 İletişim uyumluluk ilkesi oluşturduğunuzda, kimlerin iletişimlerinin gözden geçirilmiş olduğunu ve kimin incelemeler gerçekleştirdiğini tanımlarsınız. İlkede, kişileri veya kişi gruplarını tanımlamak için e-posta adreslerini kullanacaksınız. Kurulumunuzu basitleştirmek için, iletişimleri gözden geçirilmiş kişiler için gruplar ve bu iletişimleri gözden geçiren kişiler için gruplar oluşturabilirsiniz. Grupları kullanıyorsanız, birkaç gruba ihtiyacınız olabilir. Örneğin, iki ayrı kişi grubu arasındaki iletişimi algılamak veya denetlenmeyecek bir grup belirtmek istiyorsanız.

Kuruluşunuzdaki grupları iletişim uyumluluk ilkeleri için yapılandırmanıza yardımcı olması için aşağıdaki grafiği kullanın:

| **İlke Üyesi** | **Desteklenen Gruplar** | **Desteklenmeyen Gruplar** |
|:-----|:-----|:-----|
|Denetimli kullanıcılar <br> Dışlanan kullanıcılar | Dağıtım grupları <br> Microsoft 365 Grupları | Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları <br> Dinamik üyeliği olan Microsoft 365 grupları |
| Yorumcu -lar | Yok | Dağıtım grupları <br> Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları |

İlkeye bir *dağıtım grubu* atadığınızda, ilke *dağıtım grubundaki* her kullanıcıdan gelen tüm e-postaları ve Teams sohbetlerini izler. İlkeye bir *Microsoft 365 grubu* atadığınızda, ilke microsoft *365 grubuna* gönderilen tüm e-postaları ve Teams sohbetlerini algılar,* her grup üyesi tarafından alınan e-postaları ve sohbetleri algılamaz. Her kullanıcıdan gelen tek tek e-postaların ve Teams sohbetlerinin otomatik olarak izlenmesi için iletişim uyumluluk ilkelerindeki dağıtım gruplarının kullanılması önerilir.

Exchange şirket içi dağıtımına veya dış e-posta sağlayıcısına sahip bir kuruluşsanız ve kullanıcılarınız için Microsoft Teams sohbetlerini algılamak istiyorsanız, şirket içi veya dış posta kutuları olan kullanıcılar için izlemesi gereken bir dağıtım grubu oluşturmanız gerekir. Bu adımların ilerleyen bölümlerinde, ilke sihirbazında bu dağıtım grubunu **Denetimli kullanıcılar ve gruplar** seçimi olarak atayacaksınız. Bulut tabanlı depolamayı etkinleştirme gereksinimleri ve sınırlamaları ve şirket içi kullanıcılar için Teams desteği hakkında daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

Büyük kurumsal kuruluşlardaki denetimli kullanıcıları yönetmek için büyük gruplardaki tüm kullanıcıları izlemeniz gerekebilir. PowerShell'i kullanarak, atanan grup için genel iletişim uyumluluk ilkesi için bir dağıtım grubu yapılandırabilirsiniz. Bu, tek bir ilkeyle binlerce kullanıcıyı izlemenize ve kuruluşunuza yeni çalışanlar katıldığında iletişim uyumluluk ilkesini güncel tutmanıza olanak tanır.

1. Aşağıdaki özelliklerle genel iletişim uyumluluk ilkeniz için ayrılmış bir [dağıtım grubu](/powershell/module/exchange/new-distributiongroup) oluşturun: Bu dağıtım grubunun başka amaçlar veya diğer Office 365 hizmetleri için kullanılmadığından emin olun.

    - **MemberDepartRestriction = Kapalı**. Kullanıcıların kendilerini dağıtım grubundan kaldıramamalarını sağlar.
    - **MemberJoinRestriction = Kapalı**. Kullanıcıların kendilerini dağıtım grubuna ekleyememelerini sağlar.
    - **ModerationEnabled = True**. Bu gruba gönderilen tüm iletilerin onaya tabi olmasını ve grubun iletişim uyumluluk ilkesi yapılandırması dışında iletişim kurmak için kullanılmamasını sağlar.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Kuruluşunuzdaki iletişim uyumluluk ilkesine eklenen kullanıcıları izlemek için kullanılmayan bir [Exchange özel özniteliği](/Exchange/recipients/mailbox-custom-attributes) seçin.

3. İletişim uyumluluk ilkesine kullanıcı eklemek için aşağıdaki PowerShell betiğini yinelenen bir zamanlamada çalıştırın:

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

Grupları ayarlama hakkında daha fazla bilgi için bkz:

- [Dağıtım grupları oluşturma ve yönetme](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Microsoft 365 Grupları genel bakış](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>4. Adım (isteğe bağlı): Yammer kiracınızın Yerel Modda olduğunu doğrulayın

Yerel Modda, tüm Yammer kullanıcıları Azure Active Directory'de (Azure AD), tüm gruplar Office 365 Gruplar'dır ve tüm dosyalar SharePoint Online'da depolanır. Yammer'da özel iletilerde ve topluluk konuşmalarında riskli konuşmaları taramak ve tanımlamak için, iletişim uyumluluk ilkeleri için Yammer kiracınızın Yerel Modda olması gerekir.

Yammer'ı Yerel Modda yapılandırma hakkında daha fazla bilgi için bkz:

- [Microsoft 365'te Yammer Yerel Moduna Genel Bakış](/yammer/configure-your-yammer-network/overview-native-mode)
- [Yammer ağınızı Microsoft 365 için Yerel Mod için yapılandırma](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>5. Adım (gerekli): İletişim uyumluluk ilkesi oluşturma

>[!IMPORTANT]
>İletişim uyumluluk ilkeleri oluşturmak ve yönetmek için PowerShell kullanılması desteklenmez. Bu ilkeleri oluşturmak ve yönetmek için [, iletişim uyumluluk çözümünde](https://compliance.microsoft.com/supervisoryreview) ilke yönetimi denetimlerini kullanmanız gerekir.

>[!TIP]  
>Yeni bir iletişim uyumluluk ilkesi ayarlama ve uyarıyı düzeltme konusunda ayrıntılı bir izlenecek yol görmek ister misiniz? İletişim uyumluluk ilkelerinin uygunsuz iletileri algılamanıza, olası ihlalleri araştırmanıza ve uyumluluk sorunlarını düzeltmenize nasıl yardımcı olabileceğini gösteren bir tanıtım görmek için [bu 15 dakikalık videoya](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) göz atın.

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) oturum açın.

2. Microsoft Purview uyumluluk portalı **İletişim uyumluluğu'na** tıklayın.

3. **İlkeler** sekmesini seçin.

4. Şablondan yeni ilke oluşturup yapılandırmak veya özel ilke oluşturup yapılandırmak için İlke oluştur'u **seçin.**

    İlke oluşturmak için bir ilke şablonu seçerseniz şunları yapacaksınız:

    - İlke adını onaylayın veya güncelleştirin. İlke oluşturulduktan sonra ilke adları değiştirilemez.

    - Dışlamak istediğiniz kullanıcıları veya grupları seçmek de dahil olmak üzere denetlenecek kullanıcıları veya grupları seçin. İlgi alanı çakışması şablonunu kullanırken, iç iletişimleri izlemek için iki grup veya iki kullanıcı seçersiniz.

    - İlke için gözden geçirenleri seçin. Gözden geçirenler tek tek kullanıcılardır ve tüm gözden geçirenlerin Exchange Online'da barındırılan posta kutuları olmalıdır. Buraya eklenen gözden geçirenler, araştırma ve düzeltme iş akışında uyarıyı yükseltirken aralarından seçim yapabileceğiniz gözden geçirenlerdir. Gözden geçirenler bir ilkeye eklendiğinde, ilkeye atamayı bildiren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını sağlayan bir e-posta iletisini otomatik olarak alır.

    - İlkeye uygulanacak sınırlı bir koşul alanı (genellikle hassas bir bilgi türü veya anahtar sözcük sözlüğü) seçin.

    > [!NOTE]
    > İletilerdeki eklenmiş veya eklenmiş görüntüleri ilke koşullarıyla eşleşen yazdırılmış veya el yazısı metinler için taramak üzere [optik karakter tanımayı (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) etkinleştirmek istiyorsanız, İlke  > **Koşullarını ve yüzdesini** **özelleştir'i** seçin ve **Değerlendirme için Görüntülerden yazdırılmış veya el yazısı metin ayıkla'yı** etkinleştirin.

    Özel bir ilke oluşturmak için ilke sihirbazını kullanmayı seçerseniz şunları yapacaksınız:

    - İlkeye bir ad ve açıklama verin. İlke oluşturulduktan sonra ilke adları değiştirilemez.

    - Kuruluşunuzdaki tüm kullanıcılar, belirli kullanıcılar ve gruplar veya dışlamak istediğiniz diğer kullanıcılar ve gruplar dahil olmak üzere denetlenecek kullanıcıları veya grupları seçin.

    - İlke için gözden geçirenleri seçin. Gözden geçirenler tek tek kullanıcılardır ve tüm gözden geçirenlerin Exchange Online'da barındırılan posta kutuları olmalıdır. Buraya eklenen gözden geçirenler, araştırma ve düzeltme iş akışında uyarıyı yükseltirken aralarından seçim yapabileceğiniz gözden geçirenlerdir. Gözden geçirenler bir ilkeye eklendiğinde, ilkeye atamayı bildiren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını sağlayan bir e-posta iletisini otomatik olarak alır.

    - Exchange, Microsoft Teams veya Yammer gibi taranacak iletişim kanallarını seçin. Microsoft 365'te bir bağlayıcı yapılandırdıysanız üçüncü taraf kaynakları taramayı da seçebilirsiniz.

    - Gelen, giden veya iç iletişimler dahil olmak üzere algılamak için iletişim yönünü seçin.

    - İletişim uyumluluk ilkesi [koşullarını](communication-compliance-policies.md#ConditionalSettings) tanımlayın. İleti adresi, anahtar sözcük, dosya türleri ve boyut eşleştirme koşulları arasından seçim yapabilirsiniz.

    - Hassas bilgi türlerini dahil etmek isteyip istediğinizi seçin. Bu adım, varsayılan ve özel hassas bilgi türlerini seçebileceğiniz yerdir. İletişim uyumluluk ilkesi sihirbazında var olan özel hassas bilgi türlerinden veya özel anahtar sözcük sözlüklerinden seçim yapın. Gerekirse sihirbazı çalıştırmadan önce bu öğeleri oluşturabilirsiniz. İletişim uyumluluk ilkesi sihirbazından yeni hassas bilgi türleri de oluşturabilirsiniz.

    - Sınıflandırıcıları etkinleştirmek isteyip istediğinizi seçin. Sınıflandırıcılar, e-posta iletilerinin veya diğer metin türlerinin gövdesinde gönderilen veya alınan uygunsuz dil ve görüntüleri algılayabilir. Şu yerleşik sınıflandırıcıları seçebilirsiniz: *Tehdit*, *Küfür*, *Hedeflenen taciz*, *Yetişkin görüntüleri*, *Racy görüntüleri* ve *Gory görüntüleri*.

    - İlke koşullarıyla eşleşen yazdırılmış veya el yazısı metinler için iletilerdeki eklenmiş veya eklenmiş görüntüleri taramak için [optik karakter tanımayı (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) etkinleştirin. Özel ilkeler için, optik karakter tanıma taramasının seçilmesini sağlamak için ilkede metin, anahtar sözcükler, sınıflandırıcılar veya hassas bilgi türleriyle ilişkili bir veya daha fazla koşullu ayar yapılandırılmalıdır.

    - Gözden geçirecek iletişim yüzdesini tanımlayın.

    - İlke seçimlerinizi gözden geçirin ve ilkeyi oluşturun.

5. Şablonları kullanırken **ilke oluştur'u** veya özel ilke sihirbazını kullanırken **gönder'i** seçin.

6. **İlkeniz oluşturuldu sayfası, ilkenin** ne zaman etkinleştirileceğine ve hangi iletişimlerin yakalanacağını gösteren yönergelerle birlikte görüntülenir.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>6. Adım (isteğe bağlı): İletişim uyumluluk ilkeleri için uyumluluk sınırlarını güncelleştirme

[Uyumluluk sınırları](/microsoft-365/compliance/set-up-compliance-boundaries) , eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve SharePoint siteleri gibi) denetleyebilen bir kuruluş içinde mantıksal sınırlar oluşturur.

Kuruluşunuzda uyumluluk sınırlarını yapılandırdıysanız, uyumluluk sınırlarını belirli kullanıcıların iletişim uyumluluk ilkelerini destekleyen posta kutularına erişmesine izin verecek şekilde güncelleştirmeniz gerekir. İlke yönetimi ve araştırma ve düzeltme eylemlerinizin düzgün çalışması için iletişim uyumluluk yöneticilerine ve iletişim uyumluluğu gözden geçirenlerine erişim izni vermeniz gerekir.

İletişim uyumluluğu yöneticilerine ve gözden geçirenlere erişim izni vermek için aşağıdaki PowerShell komutlarını çalıştırın. Gelecekte yeni iletişim uyumluluk ilkeleri ekleseniz bile bu komutları yalnızca bir kez çalıştırmanız gerekir:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Cmdlet söz dizimi hakkında daha fazla bilgi için bkz. [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>7. Adım (isteğe bağlı): Bildirim şablonları oluşturma ve kullanıcı anonimleştirmeyi yapılandırma

İlişkili kullanıcıya anımsatıcı bildirimi göndererek bir ilke uyarısına yanıt verme seçeneğine sahip olmak istiyorsanız, kuruluşunuzda en az bir bildirim şablonu oluşturmanız gerekir. Uyarı şablonu alanları uyarı düzeltme işleminin bir parçası olarak gönderilmeden önce düzenlenebilir ve her iletişim uyumluluk ilkesi için özelleştirilmiş bir bildirim şablonu oluşturulması önerilir.

İlke eşleşmelerini araştırırken ve iletilerde işlem yaparken görüntülenen kullanıcı adları için anonimleştirmeyi etkinleştirmeyi de seçebilirsiniz.

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) oturum açın.

2. Microsoft Purview uyumluluk portalı **İletişim uyumluluğu'na** gidin.

3. Kullanıcı adları için anonimleştirmeyi yapılandırmak için **Gizlilik** sekmesini seçin.

4. Anonimleştirmeyi etkinleştirmek için **Kullanıcı adlarının anonimleştirilmiş sürümlerini göster'i** seçin.

5. **Kaydet**'i seçin.

6. **Bildirim şablonları** sekmesine gidin ve **bildirim şablonu oluştur'u** seçin.

7. **Bildirim şablonunu değiştir** sayfasında aşağıdaki alanları doldurun:

    - Şablon adı (gerekli)
    - Gönderme kimden (gerekli)
    - Bilgi ve Gizli (isteğe bağlı)
    - Konu (gerekli)
    - İleti gövdesi (gerekli)

8. Bildirim şablonunu oluşturmak ve kaydetmek için **Kaydet'i** seçin.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>8. Adım (isteğe bağlı): İletişim uyumluluk ilkenizi test edin

İletişim uyumluluk ilkesi oluşturduktan sonra, tanımladığınız koşulların ilke tarafından düzgün bir şekilde uygulandığından emin olmak için bunu test etmek iyi bir fikirdir. İletişim uyumluluk ilkeleriniz hassas bilgi türleri içeriyorsa [Microsoft Purview Veri Kaybı Önleme (DLP) ilkelerinizi de test](create-test-tune-dlp-policy.md) etmek isteyebilirsiniz. Test etmek istediğiniz iletişimlerin yakalanması için ilkelerinize etkinleştirilmesi için zaman verdiğinizden emin olun.

İletişim uyumluluk ilkenizi test etmek için şu adımları izleyin:

1. Test etmek istediğiniz ilkede tanımlanan denetimli bir kullanıcı olarak oturum açmış durumdayken bir e-posta istemcisi, Microsoft Teams veya Yammer açın.

2. İletişim uyumluluk ilkesinde tanımladığınız ölçütlere uyan bir e-posta, Microsoft Teams sohbeti veya Yammer iletisi gönderin. Bu test anahtar sözcük, ek boyutu, etki alanı vb. olabilir. İlkedeki yapılandırdığınız koşullu ayarların çok kısıtlayıcı mı yoksa çok mu yumuşak olduğunu saptadığınızdan emin olun.

    > [!NOTE]
    > E-posta iletilerinin bir ilkede tam olarak işlenmesi yaklaşık 24 saat sürebilir. Microsoft Teams, Yammer ve üçüncü taraf platformlarındaki iletişimlerin bir ilkede tam olarak işlenmesi yaklaşık 48 saat sürebilir.

3. İletişim uyumluluk ilkesinde belirlenen gözden geçiren olarak Microsoft 365'te oturum açın. İlkelerinizin **uyarılarını** görüntülemek için **İletişim uyumluluğu** >  Uyarıları'na gidin.

4. Düzeltme denetimlerini kullanarak uyarıyı düzeltin ve uyarının düzgün şekilde çözümlendiğini doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar

İlk iletişim uyumluluk ilkenizi oluşturmak için bu adımları tamamladıktan sonra, 24-48 saat sonra etkinlik göstergelerinden uyarılar almaya başlarsınız. Bu makalenin 5. Adımındaki yönergeleri kullanarak ek ilkeleri gerektiği gibi yapılandırın.

İletişim uyumluluğu uyarılarını araştırma hakkında daha fazla bilgi edinmek için bkz. [İletişim uyumluluk uyarılarını araştırma ve düzeltme](communication-compliance-investigate-remediate.md).

En son iletişim uyumluluk güncelleştirmelerini takip etmek için Kuruluşunuz için [iletişim uyumluluğundaki](https://compliance.microsoft.com/) **yenilikler'i** seçin.
