---
title: İletişim uyumluluğunu kullanmaya başlama
description: Kullanıcı iletişimini gözden geçirmek üzere yapılandırmak için iletişim uyumluluk ilkelerini ayarlayın.
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
ms.openlocfilehash: d9d418cee35976e621c173b3563b04ee8bdce7ca
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595328"
---
# <a name="get-started-with-communication-compliance"></a>İletişim uyumluluğunu kullanmaya başlama

İç veya dış gözden geçirenlerin kullanıcı iletişimlerini incelemeye yönelik tanımlamak için iletişim uyumluluk ilkelerini kullanın. İletişim uyumluluğu ilkelerinin, kurum içinde iletişimi izlemenize nasıl yardımcı olduğu hakkında daha fazla bilgi için, [Microsoft 365.](communication-compliance.md) Contoso'nın Microsoft Teams, Exchange Online ve Yammer iletişim bağlantılarında uygunsuz içeriği izlemek üzere bir iletişim uyumluluk ilkesi nasıl yapılandırdı diye gözden geçirmek Yammer bu örnek olay [incelemesine göz atabilirsiniz](communication-compliance-case-study.md).

## <a name="subscriptions-and-licensing"></a>Abonelikler ve lisanslar

İletişim uyumluluğunu başlamadan önce, Microsoft 365 [aboneliğinizi ve](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) tüm eklentileri onaylamanız gerekir. İletişim uyumluluğuna erişmek ve bu uyumluluğu kullanmak için, organizasyon aşağıdaki aboneliklerden veya eklentilerden birini kullanıyor olması gerekir:

- Microsoft 365 E5/A5/F5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Uyumluluk eklentiniz
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Insider Risk Yönetimi eklentisi
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 A5 (ücretli veya deneme sürümü)
- Office 365 Kurumsal E3 aboneliği + Office 365 Gelişmiş Uyumluluk eklentiyi içerir (artık yeni abonelikler için kullanılamaz, nota bakın)

İletişim uyumluluk ilkelerine dahil olan kullanıcılara yukarıdaki lisanslardan biri atanmalıdır. Abonelikler ve lisanslar hakkında daha fazla bilgi için, [güvenlik Microsoft 365 uyumluluğu için yol & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> İletişim uyumluluğu şu anda, Azure hizmet bağımlılıkları tarafından desteklenen coğrafi bölgelerde ve ülkelerde barındırılan kiracılarda kullanılabilir. İletişim uyumluluğunun organizasyonunız için destek olduğunu doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

Mevcut bir Office 365 Kurumsal E5 planınız yoksa ve iletişim uyumluluğunu denemek için mevcut aboneliğinize [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) ekleyebilir veya Office 365 Kurumsal'in deneme sürümüne kaydolabilirsiniz.[](https://www.microsoft.com/microsoft-365/enterprise)

> [!NOTE]
> Office 365 Gelişmiş Uyumluluk artık tek başına abonelik olarak satılmaz. Geçerli aboneliklerin süresi dolduğunda, müşteriler aynı veya ek uyumluluk özelliklerini içeren yukarıdaki aboneliklerden birini kullanmalı.

## <a name="recommended-actions-preview"></a>Önerilen eylemler (önizleme)

Önerilen eylemler, iletişim uyumluluğu özellikleriyle çalışmaya başlamanıza ve var olan ilkeleriniz arasında en iyi şekilde çalışmanıza yardımcı olabilir. İlkeler **sayfasında** yer alan önerilen eylemler içgörüler sağlar ve kuruluş iletişimlerinde hassas bilgi türlerini ve uygunsuz içerik etkinliklerini özetler. Analizler sınıflandırması [ve duyarlılık](data-classification-overview.md) etiketleri, bekletme etiketleri ve hassas bilgi türü sınıflandırması uygulaması tarafından desteklenen bir uygulamadır. Bu içgörüler, organizasyonu kullanan kullanıcılar için kişisel olarak tanınmayı sağlayacak hiçbir bilgiyi (PII) içermemektedir.

![İletişim uyumluluğu için önerilen eylemler.](../media/communication-compliance-recommended-actions.png)

Uygunsuz içerik içeren iletilerde etkinlik, uygunsuz içerik için [](/microsoft-365/compliance/communication-compliance-policies#classifiers) sınıflandırıcıları kullanan mevcut ilkelerden veya uygunsuz içerik için sınıflayıcıları kullanan özel ilkelerden sınıflandırıcı türle toplanır. İlkelerinize yönelik uyarı panosunda bu iletiler için uyarıları araştırabilirsiniz.

Var olan [ilkelerde ele](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) alınan iletilerde ve var olan ilkeler kapsamında olmayan iletilerde hassas bilgi türlerinin yer aldığı etkinlikler algılanır. Analizler, daha önce var olan bir iletişim uyumluluk ilkesinde tanımlanmamış olanlar da dahil olmak üzere tüm hassas bilgi türleri için veriler toplanır. Yeni bir iletişim uyumluluk ilkesi oluşturmak veya var olan ilkeleri güncelleştirmek için bu içgörüleri kullanın.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>1. Adım (gerekli): İletişim uyumluluğu için izinleri etkinleştirme

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdikten sonra, rol grubu izinlerin kuruluş genelinde atanan kullanıcılara uygulamak 30 dakika kadar sürebilir.

İletişim uyumluluğu özelliklerini yönetmek için başlangıç izinlerini yapılandırmak için kullanılan altı rol grubu vardır. İletişim **uyumluluğunun** E-Microsoft 365 uyumluluk merkezi menü seçeneği olarak kullanılabilir olması ve bu yapılandırma adımlarına devam etmek için, aşağıdaki rollerden veya rol gruplarından biri size atanmış olması gerekir:

- Azure Active Directory [*Yönetici rolü*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*Uyumluluk Yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolü
- Microsoft 365 uyumluluk merkezi [*Yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- Microsoft 365 uyumluluk merkezi [*Yöneticisi rol*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) grubu
- *İletişim Uyumluluğu* rol grubu
- *İletişim Uyumluluğu Yöneticisi* rol grubu

Aşağıdaki rollerin üyeleri, İletişim Uyumluluğu Yöneticisi rol grubuyla *aynı çözüm izinlerine* sahip olur:

- Azure Active Directory *Yönetici*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft 365 uyumluluk merkezi *Yönetimi*
- Microsoft 365 uyumluluk merkezi *Uyumluluk Yöneticisi*

> [!IMPORTANT]
> İletişim Uyumluluğu veya İletişim Uyumluluğu Yöneticisi rol gruplarında her zaman  en az bir  kullanıcınız olduğundan emin olun (seçtiğiniz seçen bağlı olarak), iletişim uyumluluk yapılandırmanız belirli kullanıcılar kuruluşlarından ayrılırsa 'sıfır yönetici' senaryosuna uymaz.

İletişim uyumluluk ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı iletişim uyumluluk özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Farklı iletişim uyumluluk özellikleri alanlarını yönetmek için, farklı uyumluluk sorumluluklarına sahip kullanıcıları belirli rol gruplarına atama seçeneğiniz vardır. Ya da belirli yöneticiler, analistler, analistler ve izleyiciler için tüm kullanıcı hesaplarını İletişim Uyumluluğu *rol grubuna atamaya karar* veabilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun şekilde tek bir rol grubu veya birden çok rol grubu kullanın.

İletişim uyumluluğunu yapılandıran ve yöneten şu çözüm rol grubu seçeneklerinden birini belirleyin:

| Rol | Rol izinleri |
|:-----|:-----------------|
| **İletişim Uyumluluğu** | Tek bir grupta, organizasyona iletişimi uyumluluğu yönetmek için bu rol grubunu kullanın. Belirlenen yöneticiler, analistler, analistler ve görüntüleyiciler için tüm kullanıcı hesaplarını ekleyerek, iletişim uyumluluk izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu tüm iletişim uyumluluğu izin rollerini içerir. bu yapılandırma, iletişim uyumluluğuyla hızla çalışmaya başlamanın en kolay yoludur ve ayrı kullanıcı grupları için tanımlanmış ayrı izinlere gerekmayan kuruluşlara iyi uyum sağlar. İletişim uyumluluk yöneticisi olarak ilkeler oluşturmaları için, posta kutularının Posta Kutusu'Exchange Online.|
| **İletişim Uyumluluğu Yöneticisi** | Bu rol grubunu ilk başta iletişim uyumluluğunu yapılandırmak ve daha sonra iletişim uyumluluk yöneticilerini tanımlı bir grup haline çekmek için kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluk ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirabilir ve silebilir. Bu rol grubuna atanan kullanıcılar ileti uyarılarını görüntüleyem. İletişim uyumluluk yöneticisi olarak ilkeler oluşturmaları için, posta kutularının Posta Kutusu'Exchange Online.|
| **İletişim Uyumluluğu Analisti** | İletişim uyumluluğu analistleri olarak görevecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanmış olan kullanıcılar, Gözden Geçiren olarak atandığı ilkeleri abilir, ileti meta verilerini (ileti içeriğine değil)  bakabilir, ek gözden geçirenlere gönderebilir veya kullanıcılara bildirim gönderebilir. Analistler bekleyen uyarıları çözümleyemezse. |
| **İletişim Uyumluluğu Uyumluluk Uyumlulukları** | İletişim uyumluluğu uyumluluk uyumluluk uyumlulukları gibi davranacak kullanıcılara izinler atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar ileti meta verilerini ve içeriğini  neleri iletiyi gözden geçirenlere iletir, Advanced eDiscovery durumuna iyileştirmeyi, kullanıcılara bildirim gönderebilir ve uyarıyı çözebilir. |
| **İletişim Uyumluluğu Görüntüleyicisi** | İletişim raporlarını yönetecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluğu giriş sayfasında tüm raporlama pencere öğelerine erişim sağlar ve tüm iletişim uyumluluk raporlarını  görebilirsiniz. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>1. Seçenek: Tüm uyumluluk kullanıcılarını İletişim Uyumluluğu rol grubuna atama

1. Bir yönetici [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) hesabının kimlik bilgilerini kullanarak oturum Microsoft 365.

2. Güvenlik Uyumluluk Merkezi'nde &amp; İzinler'e **gidin**. Aynı dosyada rolleri görüntülemek ve yönetmek için Office 365.

3. İletişim Uyumluluğu *rol grubunu* seçin ve sonra da Rol grubunu **düzenle'yi seçin**.

4. Sol **gezinti bölmesinde Üye** seç'i, ardından Düzenle'yi **seçin**.

5. **Ekle'yi** seçin ve sonra İletişim Uyumluluğu rol grubuna eklemek istediğiniz tüm kullanıcıların *onay kutusunu* seçin.

6. **Ekle'yi** ve ardından **Bitti'yi seçin**.

7. Kullanıcıları **rol** grubuna eklemek için Kaydet'i seçin. Adımları **tamamlamak için** Kapat'ı seçin

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>2. Seçenek: Kullanıcıları belirli iletişim uyumluluk rol gruplarına atama

Kullanıcıları belirli rol gruplarına atamak için bu seçeneği kullanarak, kuruluşta yer alan farklı kullanıcılar arasında iletişim uyumluluğu erişimini ve sorumluluklarını bölüme belirleyin.

1. [E-Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) yönetici hesabının kimlik bilgilerini kullanarak Microsoft 365 ve ardından İzinler'e **gidin**</a>.

2. Aynı dosyada rolleri görüntülemek ve yönetmek için Office 365.

3. İletişim uyumluluk rol gruplarından birini seçin ve sonra da Rol grubunu **düzenle'yi seçin**.

4. Sol **gezinti bölmesinde Üye** seç'i, ardından Düzenle'yi **seçin**.

5. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcıların onay kutusunu seçin.

6. **Ekle'yi** ve ardından **Bitti'yi seçin**.

7. Kullanıcıları **rol** grubuna eklemek için Kaydet'i seçin.

8. Sonraki iletişim uyumluluk rol grubunu seçin ve sonra 4-7 arasındaki adımları gerekli her rol grubu için yineler.

9. Adımları **tamamlamak** için Kapat'ı seçin.

Rol grupları ve izinler hakkında daha fazla bilgi için bkz. [Uyumluluk Merkezi'nde İzinler](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>2. Adım (gerekli): Denetim günlüğünü etkinleştirme

İletişim uyumluluğu, uyarıları göstermek ve gözden geçirenlerin sındırma eylemlerini izlemek için denetim günlükleri gerektirir. Denetim günlükleri, tanımlı bir kuruluş ilkesiyle ilişkilendirilmiş tüm etkinliklerin özetidir veya bir iletişim uyumluluk ilkesi her değiştiklerinde özetler.

Bu kuruluşlarda denetim Microsoft 365 varsayılan olarak etkinleştirilir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmıştır. If auditing is disabled for your organization, it might be because another administrator has turned it. Bu adımı tamamlarken denetimi yeniden açmanın bir sorun olduğunu doğrulamanızı öneririz.

Denetimi açma adım adım yönergeler için bkz. [Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açmak için denetim günlüğünün hazır olduğunu ve birkaç saat içinde hazırlık tamamlandıktan sonra arama çalıştırabilirsiniz iletisi görüntülenir. Bu eylemi yalnızca bir kez yapmak gerekir. Denetim günlüğünü kullanma hakkında daha fazla bilgi için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>3. Adım (isteğe bağlı): İletişim uyumluluğu için grupları ayarlama

 Bir iletişim uyumluluk ilkesi seniz, kimlerin iletişimleri gözden geçir olduğunu ve kimin incelemeler yapanı tanımlarsiniz. İlkede, tek tek veya kişi gruplarını tanımlamak için e-posta adreslerini kullanırsınız. Kurulumlarınızı basitleştirmek için, iletişimleri gözden geçirilen kişiler için gruplar ve bu iletişimleri gözden geçiren kişiler için gruplar oluşturabilirsiniz. Grupları kullanıyorsanız, birkaç gruba ihtiyacınız olabilir. Örneğin, iki ayrı kişi grubu arasındaki iletişimi izlemek veya denetlenecek bir grup belirtmek istemiyorsanız.

Aşağıdaki grafiği kullanarak, iletişim uyumluluk ilkeleri için organizasyonu grupları yapılandırmanıza yardımcı olun:

| **İlke Üyesi** | **Desteklenen Gruplar** | **Desteklenmeyen Gruplar** |
|:-----|:-----|:-----|
|Denetimli kullanıcılar <br> Dışlanan kullanıcılar | Dağıtım grupları <br> Microsoft 365 Grupları | Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları <br> Microsoft 365 üyeliği olan gruplarla çalışma |
| Gözden Geçirenler | Yok | Dağıtım grupları <br> Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları |

İlkede bir *dağıtım grubu atadığınız* zaman, ilke tüm e-postaları Teams ve dağıtım grubunda yer alan her kullanıcının *sohbetlerini izler*. İlkede *bir Microsoft 365* grubu atadığınız zaman, ilke her grup üyesinin aldığı tek tek e-postaları ve sohbetleri değil, * Microsoft 365 grubuna gönderilen tüm e-postaları ve *Teams* sohbetlerini izler. Her kullanıcıdan gelen tek tek e-postaların ve sohbetlerin otomatik olarak izlen Teams dağıtım gruplarının iletişim uyumluluk ilkeleri içinde kullanılması önerilir.

Exchange şirket içi dağıtımına veya dış e-posta sağlayıcısına sahip bir kuruluşsanız ve kullanıcılarınız için Microsoft Teams sohbetlerini izlemek için, şirket içi veya dış posta kutuları olan kullanıcılar için bir dağıtım grubu oluşturmanız gerekir. Bu adımların devamlarında, bu dağıtım grubunu ilke sihirbazında Denetimli kullanıcılar **ve** gruplar seçimi olarak atarsınız. Bulut tabanlı depolamayı etkinleştirme gereksinimleri ve sınırlamaları hakkında daha fazla bilgi Teams için bkz. Şirket içi kullanıcılar için [Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

Büyük kurumsal kuruluşlarda denetlenen kullanıcıları yönetmek için, büyük gruplarda tüm kullanıcıları izlemeniz gerekiyor olabilir. PowerShell kullanarak atanan gruba genel iletişim uyumluluk ilkesi için bir dağıtım grubu yapılandırabilirsiniz. Bu, binlerce kullanıcıyı tek bir ilkeyle izlemenizi ve yeni çalışanların kuruluşa katılmasını sağlayan iletişim uyumluluk ilkesi güncelleştirmelerini tutmanıza olanak sağlar.

1. Aşağıdaki özelliklerle[, genel](/powershell/module/exchange/new-distributiongroup) iletişim uyumluluk ilkeniz için ayrılmış bir dağıtım grubu oluşturun: Bu dağıtım grubunun başka amaçlar veya diğer hizmetlerde kullanılma Office 365 olun.

    - **MemberDepartRestriction = Closed**. Kullanıcıların kendilerini dağıtım grubundan çıkarmalarını sağlar.
    - **MemberJoinRestriction = Closed**. Kullanıcıların kendilerini dağıtım grubuna ekleyemalarını sağlar.
    - **ModerationEnabled = True**. Bu gruba gönderilen tüm iletilerin onaya tabi olduğunu ve grubun iletişim uyumluluk ilkesi yapılandırması dışında iletişim kurmak için kullanılmamalarını sağlar.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Kullanılmayan bir özel [Exchange öznitelik seçerek](/Exchange/recipients/mailbox-custom-attributes), kurum içinde iletişim uyumluluğu ilkesine eklenen kullanıcıları izleyebilirsiniz.

3. İletişim uyumluluğu ilkesine kullanıcı eklemek için, yinelenen bir zamanlamada aşağıdaki PowerShell betiği çalıştırın:

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
- [Genel bakış Microsoft 365 Grupları](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>4. Adım (isteğe bağlı): Yammer Yerel Modda olduğunu doğrulama

Yerel Modda, Yammer tüm kullanıcılar Azure Active Directory (Azure AD), tüm gruplar Office 365 Grupları olarak ve tüm dosyalar da SharePoint Online'da depolanır. İletişim Yammer uyumluluk Yammer ilkelerinin, özel iletilerde ve topluluk konuşmalarında riskli konuşmaları taray tanımlay için Yerel Modda olması gerekir.

Yerel Modda yeni bir Yammer daha fazla bilgi için bkz:

- [Microsoft 365'Yammer Yerel Mod'a genel Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Yerel Yammer için Yerel Mod için yerel ağına Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>5. Adım (gerekli): İletişim uyumluluk ilkesi oluşturma

>[!IMPORTANT]
>İletişim uyumluluk ilkeleri oluşturmak ve yönetmek için PowerShell kullanımı desteklenemektedir. Bu ilkeleri oluşturmak ve yönetmek için, uyumluluk çözümünde ilke yönetim [Microsoft 365 kullanmalıdır](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Yeni bir iletişim uyumluluk ilkesi ayarlama ve uyarı düzeltme hakkında ayrıntılı bir yol mu görmeksiniz? İletişim uyumluluk ilkelerinin uygunsuz iletileri algılamanıza, olası ihlalleri araştırmanıza ve uyumluluk sorunlarını düzeltmeye nasıl yardımcı olduğunu göstermeyi görmek için [bu 15 dakikalık videoyu](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) izleyin.

1. Bir [Microsoft 365 uyumluluk merkezi yönetici hesabının](https://compliance.microsoft.com) kimlik bilgilerini kullanarak oturum Microsoft 365.

2. Uyumluluk iletişim **Microsoft 365 uyumluluk merkezi'yi seçin**.

3. **İlkeler sekmesini** seçin.

4. **Şablondan yeni** ilke oluşturmak ve yapılandırmak veya özel bir ilke oluşturmak ve yapılandırmak için İlke oluştur'a seçin.

    İlke oluşturmak için bir ilke şablonu seçerseniz, şunları da oluşturursunuz:

    - İlke adını onaylayın veya güncelleştirin. İlke oluşturulduktan sonra ilke adları değiştirilemez.

    - Denetleme için, hariç tutmak istediğiniz kullanıcıları veya grupları seçme dahil olmak üzere kullanıcıları veya grupları seçin. İlgi alanı çakışması şablonunu kullanırken, iç iletişimleri izlemek için iki grup veya iki kullanıcı seçersiniz.

    - İlke için gözden geçirenleri seçin. Gözden geçirenler bireysel kullanıcılardır ve tüm gözden geçirenlerin e-posta kutusunda barındırılan posta Exchange Online. Buraya eklenen gözden geçirenler, araştırma ve düzeltme iş akışında uyarıyı yukarıya ilerlerken seçerek seçebilirsiniz. Gözden geçirenler bir ilkeye ekli olduğunda, otomatik olarak ilkeye atamayı haber veren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını veren bir e-posta iletisi alırlar.

    - İlkeye uygulamak için sınırlı bir koşul alanı, genellikle hassas bir bilgi türü veya anahtar sözcük sözlüğü seçin.

    > [!NOTE]
    > Optik karakter tanımanın (OCR) iletilerde, ilke koşullarına uygun, yazdırılmış veya el yazısıyla yazılmış metinleri taramasını sağlamak için Optik karakter [tanımayı (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr)  >  etkinleştirmek ve Değerlendirme için görüntülerden yazdırılan veya el yazısıyla yazılmış metinleri ayıkla seçeneğini **etkinleştirin.**

    Özel bir ilke oluşturmak için ilke sihirbazını kullanmayı seçerseniz, şunları da kullanırsınız:

    - İlkeye bir ad ve açıklama girin. İlke oluşturulduktan sonra ilke adları değiştirilemez.

    - Denetlemek istediğiniz kullanıcıları veya grupları seçin; bunlar, kuruluş dahil tüm kullanıcılar, belirli kullanıcılar ve gruplar ya da dışarıda tutmak istediğiniz diğer kullanıcılar ve gruplar olabilir.

    - İlke için gözden geçirenleri seçin. Gözden geçirenler bireysel kullanıcılardır ve tüm gözden geçirenlerin e-posta kutusunda barındırılan posta Exchange Online. Buraya eklenen gözden geçirenler, araştırma ve düzeltme iş akışında uyarıyı yukarıya ilerlerken seçerek seçebilirsiniz. Gözden geçirenler bir ilkeye ekli olduğunda, otomatik olarak ilkeye atamayı haber veren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını veren bir e-posta iletisi alırlar.

    - Taramak için, taramak istediğiniz iletişim Exchange, Microsoft Teams, Yammer, bağlantı Skype Kurumsal. Ayrıca, bu bağlantıda bir bağlayıcı yapılandırdınız üçüncü taraf kaynaklarını taramayı Microsoft 365.

    - Gelen, giden veya iç iletişim de dahil olmak üzere izlecek iletişim yönünü seçin.

    - İletişim uyumluluğu ilkesi koşullarını [tanımlayın](communication-compliance-policies.md#ConditionalSettings). İleti adresi, anahtar sözcük, dosya türleri ve boyut eşleşme koşulları arasında seçim seçebilirsiniz.

    - Hassas bilgi türlerini eklemek mi istediğinize seçin. Bu adım, varsayılan ve özel hassas bilgi türlerini seç alanıdır. İletişim uyumluluk ilkesi sihirbazında var olan özel hassas bilgi türlerinden veya özel anahtar sözcük sözlüklerinden birini seçin. Gerekirse, sihirbazı çalıştırmadan önce bu öğeleri oluşturabilirsiniz. Ayrıca, iletişim uyumluluk ilkesi sihirbazından yeni hassas bilgi türleri de oluşturabilirsiniz.

    - Sınıflayıcıları etkinleştirmek istediğinize seçin. Sınıflayıcılar, e-posta iletilerinin gövdesinde veya diğer metin türlerinde gönderilen veya alınan uygunsuz dili ve resimleri algılanabilir. Şu yerleşik sınıflayıcıları seçebilirsiniz: *Tehdit*, *Küfür**,* Hedefli taciz, *Yetişkin* resimleri, *Racy* resimleri ve *Gory resimleri*.

    - [İlke koşullarına uygun yazdırılan veya el yazısıyla](communication-compliance-policies.md#optical-character-recognition-ocr) yazılmış metinler için iletilerde eklenmiş veya eklenmiş resimleri taramak için optik karakter tanımayı (OCR) etkinleştirin. Özel ilkeler için, metinle, anahtar sözcüklerle, sınıflayıcılarla veya hassas bilgi türleriyle ilişkilendirilmiş bir veya birden çok koşullu ayarın, optik karakter tanıma taramasının seçimini etkinleştirmek üzere ilke içinde yapılandırılması gerekir.

    - Gözden geçirlecek iletişim yüzdesini tanımlayın.

    - İlke seçimlerinizi gözden geçirme ve ilkeyi oluşturma.

5. Şablonları **kullanırken İlke** oluştur'ı veya özel **ilke sihirbazını** kullanırken Gönder'i seçin.

6. **İlkeniz oluşturuldu sayfası**, ilkenin ne zaman etkinleştirildikten ve hangi iletişimlerin yakalanır yönergeleriyle görüntülenir.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>6. Adım (isteğe bağlı): İletişim uyumluluk ilkeleri için uyumluluk sınırlarını güncelleştirme

[Uyumluluk sınırları](/microsoft-365/compliance/set-up-compliance-boundaries), eBulma yöneticilerinin aray kontrolü yaptığı kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve site SharePoint gibi) denetimi altına alan bir kuruluş içinde mantıksal sınırlar oluşturabilir.

Kuruluşta uyumluluk sınırlarını yapılandırdınız, bazı kullanıcıların iletişim uyumluluk ilkelerini destekleyen posta kutularına erişmesine izin vermek için uyumluluk sınırlarını güncelleştirmeniz gerekir. İlke yönetiminiz ve araştırmanız ve düzeltme eylemlerinizin düzgün çalışması için, iletişim uyumluluğu yöneticilerine ve iletişim uyumluluğu gözden geçirenlerine erişim izni verseniz gerekir.

İletişim uyumluluğu yöneticilerine ve gözden geçirenlere erişim izni vermek için, aşağıdaki PowerShell komutlarını çalıştırın. Gelecekte yeni iletişim uyumluluk ilkeleri eklese bile bu komutları yalnızca bir kez çalıştırmanıza gerek vardır:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

cmdlet söz dizimi hakkında daha fazla bilgi için bkz [. New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>7. Adım (isteğe bağlı): Bildirim şablonları oluşturma ve kullanıcı anonimliğini yapılandırma

İlişkili kullanıcıya bir anımsatıcı bildirimi göndererek ilke uyarılarını yanıtla seçeneğine sahip olmak için, kurumda en az bir bildirim şablonu oluşturmanız gerekir. Uyarı düzeltme işlemi kapsamında gönderilmeden önce bildirim şablonu alanları düzenlenebilir ve her iletişim uyumluluk ilkesi için özelleştirilmiş bir bildirim şablonu oluşturulması önerilir.

ayrıca, ilke eşleşmelerini araştırırken ve iletiler üzerinde eyleme ilerlerken görüntülenen kullanıcı adları için anonimliği etkinleştirmeyi de seçebilirsiniz.

1. Bir [Microsoft 365 uyumluluk merkezi yönetici hesabının](https://compliance.microsoft.com) kimlik bilgilerini kullanarak oturum Microsoft 365.

2. aşağıdaki Microsoft 365 uyumluluk merkezi **uyumluluğu'ne gidin**.

3. Kullanıcı adları anonimleştirmeyi yapılandırmak için Gizlilik **sekmesini** seçin.

4. Anonimliği etkinleştirmek için Kullanıcı **adlarının anonimleştirilmiş sürümlerini göster'i seçin**.

5. **Kaydet**'i seçin.

6. Bildirim şablonları **sekmesine gidin ve** Bildirim şablonu **oluştur'a tıklayın**.

7. Bildirim **şablonunu değiştirme sayfasında** aşağıdaki alanları doldurun:

    - Şablon adı (gerekli)
    - Gönderme : (gerekli)
    - Bilgi ve Gizli (isteğe bağlı)
    - Konu (gerekli)
    - İleti gövdesi (gerekli)

8. Bildirim **şablonunu** oluşturmak ve kaydetmek için Kaydet'i seçin.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>8. Adım (isteğe bağlı): İletişim uyumluluk ilkenizi test edin

İletişim uyumluluk ilkesi oluşturdukktan sonra, tanımlandığı koşulların ilke tarafından düzgün bir şekilde zorunlu kılın olduğundan emin olmak için ilkeyi test etmek iyi bir fikirdir. ayrıca, iletişim uyumluluk [ilkeleriniz hassas bilgi türleri de içermesi durumlarında veri kaybı önleme (DLP)](create-test-tune-dlp-policy.md) ilkelerinizi test etmek de istiyor olabilir. Test etmek istediğiniz iletişimlerin yakalanması için ilkelerinize etkinleştirmek için zaman vermeye emin olun.

İletişim uyumluluk ilkenizi test etmek için şu adımları izleyin:

1. Test etmek istediğiniz ilkede Microsoft Teams denetimli bir kullanıcı olarak oturum açıkken bir e-posta istemcisi, kimlik bilgileri veya Yammer açın.

2. İletişim uyumluluğu Microsoft Teams ölçütlerine uyan bir Yammer e-posta gönderin, sohbet edin veya Yammer iletisi gönderin. Bu test bir anahtar sözcük, ek boyutu, etki alanı vb. olabilir. İlkede yapılandırılan koşullu ayarlarınızın çok kısıtlayıcı mı yoksa çok uygun olup olmadığını belirlemeye emin olun.

    > [!NOTE]
    > E-posta iletilerinin bir ilkede tam olarak işlemesi 24 saat kadar sürebilir. Dış Microsoft Teams, Yammer üçüncü taraf platformlarda iletişimlerin ilkelerde tam olarak işlemesi 48 saate kadar sürebilir.

3. İletişim uyumluluk Microsoft 365 bir gözden geçiren olarak oturum açma. **İlkelerinize yönelik** >  **uyarıları görüntülemek için İletişim uyumluluğuAlerts'leri'ne** gidin.

4. Düzeltme denetimlerini kullanarak uyarıyı düzeltin ve uyarının düzgün bir şekilde çözümlenmiş olduğunu doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar

İlk iletişim uyumluluk ilkenizi oluşturmak için bu adımları tamamlandıktan sonra, 24-48 saat sonra etkinlik göstergelerinden uyarı almaya başlarsınız. Bu makalenin 5. Adım'daki kılavuzu kullanarak ek ilkeleri gerektiğinde yapılandırabilirsiniz.

İletişim uyumluluğu uyarılarını inceleme hakkında daha fazla bilgi edinmek için, bkz [. İletişim uyumluluk uyarılarını araştırma ve düzeltme](communication-compliance-investigate-remediate.md).

En son iletişim uyumluluk güncelleştirmelerini takip etmek için, **Organizasyonun iletişim uyumluluğu** [ile ilgili tüm gelişmeleri](https://compliance.microsoft.com/) seçin.
