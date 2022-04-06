---
title: Microsoft 365 Defender portalında izinler
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Yöneticiler güvenlikle ilgili tüm görevler için portalda Microsoft 365 Defender yönetmeyi öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e819a9de9d5ccd66caab4bc13d8b11c1a95ab03
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681732"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında izinler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm yeni hizmetlerde yer alan güvenlik senaryolarını yönetmeniz Microsoft 365 gerekir. Ayrıca, organizasyonda doğru kullanıcılara doğru yönetici izinlerini verme esnekliğine de ihtiyacınız vardır.

At Microsoft 365 Defender portalı, <https://security.microsoft.com> iş yerinde güvenlik görevleri gerçekleştiren kullanıcılar için izinleri doğrudan Microsoft 365. İzinleri yönetmek Microsoft 365 Defender bir portal kullanarak, güvenlikle ilgili tüm görevler için izinleri merkezi olarak yönetebilirsiniz.

Portalda izinleri yönetmek Microsoft 365 Defender, Roller veya **& gidin**<https://security.microsoft.com/securitypermissions>. Web portalında **genel yönetici** veya Kuruluş **Yönetimi rol grubunun** bir üyesi Microsoft 365 Defender gerekir. Özel olarak, **Rol** Yönetimi rolü kullanıcıların Microsoft 365 Defender portalında rol gruplarını görüntülemelerini, oluşturmalarını ve değiştirmelerini sağlar ve varsayılan olarak, bu rol yalnızca Kuruluş Yönetimi rol grubuna atanır.

> [!NOTE]
> Site İzinleri hakkında daha fazla Microsoft 365 uyumluluk merkezi için aşağıdaki [İzinler Microsoft 365 uyumluluk merkezi](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

Web Microsoft 365 Defender, rol tabanlı erişim denetimi (RBAC) izin modeline dayalıdır. RBAC, çoğu Microsoft 365 hizmeti tarafından kullanılan izinler modelidir; dolayısıyla bu hizmetlerde izin yapısını biliyorsanız, Microsoft 365 Defender portalında izin vermek çok tanıdıktır.

Bir **rol** , bir dizi görevi gerçekleştirme iznini size sunar.

Rol **grubu,** kişilerin portalda işlerini yapmalarına olanak sağlayan Microsoft 365 Defender dir.

Aşağıdaki Microsoft 365 Defender portalı>, atamanız gereken en yaygın görevler ve işlevler için varsayılan rol gruplarını içerir. Genel olarak, varsayılan rol gruplarına tek **tek kullanıcıları üye** olarak eklemenizi öneririz.

![Rol gruplarıyla roller ve üyeler arasındaki ilişkiyi gösteren diyagram.](../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Portalda yer alan roller Microsoft 365 Defender grupları

Aşağıdaki rol ve rol grubu türlerine, Microsoft 365 Defender portalında yer alan  İzinler <https://security.microsoft.com/securitypermissions> & rol Microsoft 365 Defender vardır:

- **Azure AD rolleri**: Rolleri ve atanmış kullanıcıları görüntüebilirsiniz, ancak doğrudan kullanıcı portalında yönet Microsoft 365 Defender. Azure AD rolleri, tüm kullanıcı hizmetleri için **izinler atayanın** Microsoft 365 rollerdir.

- **E&-posta** ve işbirliği rolleri: Bunlar, Güvenlik ve Uyumluluk Merkezi'nde bulunan & rol gruplarıyla aynıdır; ancak bunları doğrudan Microsoft 365 Defender yönetebilirsiniz. Burada atadığınız izinler Microsoft 365 Defender portalına, Microsoft 365 uyumluluk merkezi'ye ve Güvenlik & Uyumluluk Merkezi'ne özeldir ve diğer iş yükleri için gereken tüm izinleri Microsoft 365 değildir.

![& portalında izinler ve Microsoft 365 Defender sayfası.](../../media/m365-sc-permissions-and-roles-page.png)

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Azure AD rolleri

Microsoft 365 Defender portalını <https://security.microsoft.com> açıp **E-posta &** işbirliği rolleri E-posta & \>  \> **roller Azure AD** \> rol **rolleri (**<https://security.microsoft.com/aadpermissions>veya doğrudan üzerinde) bölümüne gidip bu bölümde açıklanan Azure AD rollerini bulabilirsiniz.

Bir rol seçin, rolün açıklamasını ve kullanıcı atamalarını içeren ayrıntılar açılır öğesini görünür. Ancak bu atamaları yönetmek için ayrıntılar ayrıntılarında **, Azure AD'de üyeleri** yönet'e tıklamanız gerekir.

![E-postada izinleri yönetmek Azure Active Directory.](../../media/permissions-manage-in-azure-ad-link.png)

Daha fazla bilgi için bkz[. 2010'da yönetici rollerini görüntüleme Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rol|Açıklama|
|---|---|
|**Genel yönetici**|Tüm hizmetlerde, tüm yönetim Microsoft 365 erişim. Yalnızca genel yöneticiler diğer yönetici rollerini atayır. Daha fazla bilgi için bkz [. Genel Yönetici / Şirket Yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Uyumluluk veri yöneticisi**|Tüm dünya genelinde verilerinizi takip edin, Microsoft 365 korunmasına yardımcı olun ve riskleri azaltmak için tüm sorunlar hakkında içgörüler elde edin. Daha fazla bilgi için bkz. [Uyumluluk Veri Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Uyumluluk yöneticisi**|Tüm yasal düzenleme gereksinimleriyle uyumlu kalmalarına, eBulma olaylarını yönetmelerine ve farklı konumlarda Microsoft 365, kimliklerde ve uygulamalarda veri yönetimi ilkelerini korumalarına yardımcı olun. Daha fazla bilgi için bkz. [Uyumluluk Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Güvenlik operatörü**|Kullanıcılarınızı, cihazlarınızı ve içeriğinizi görüntüleme, araştırma ve Microsoft 365 tehditlere yanıt verme. Daha fazla bilgi için bkz. [Güvenlik İşleci](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Güvenlik gözetmeni**|Kullanıcılarınıza, cihazlarınıza ve Microsoft 365 yönelik etkin tehditleri  görüntüp araştırabilirsiniz, ancak (Güvenlik işlecinin aksine) herhangi bir işlem gerçekleştirerek bu izinleri olmaz. Daha fazla bilgi için bkz. [Güvenlik Okuyucu](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Güvenlik yöneticisi**|Güvenlik ilkelerini yöneterek, Microsoft 365 ürünlerinde güvenlik analizini ve raporlarını gözden geçirerek ve tehdit ortamında hızlendirerek, kuruluş genel güvenliğini kontrol edin. Daha fazla bilgi için bkz. [Güvenlik Yöneticisi](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Genel okuyucu**|Genel yönetici rolünün salt **okunur sürümü** . Tüm ayarları ve yönetim bilgilerini tüm Microsoft 365. Daha fazla bilgi için bkz. [Genel Okuyucu](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Saldırı benzetimi yöneticisi**|Saldırı benzetimi oluşturma [, benzetim](attack-simulation-training.md) başlatma/zamanlama ve benzetim sonuçlarının gözden geçirmesi gibi her yönüyle oluşturun ve yönetin. Daha fazla bilgi için bkz [. Saldırı Benzetimi Yöneticisi](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Saldırı yükü yazarı**|Saldırı yüklemeleri oluşturun ancak aslında bunları başlatamaz veya zamanlamayın. Daha fazla bilgi için bkz [. Saldırı Yük Yazarı](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>E& portalda e-posta Microsoft 365 Defender işbirliği rolleri

Microsoft 365 Defender portalını <https://security.microsoft.com> açıp **E-posta &** işbirliği rolleri E-posta & \> rolleri E-posta **&** \>  \> işbirliği rolleri **Roller'e** (<https://security.microsoft.com/emailandcollabpermissions>veya doğrudan) gidip Güvenlik ve Uyumluluk Merkezi'nde bulunan rol gruplarının aynılarını & alırsınız.

Bu rol grupları hakkında tam bilgi için bkz. [Güvenlik ve Uyumluluk &'nde İzinler](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Yeni portalda &-posta ve işbirliği rolü Microsoft 365 Defender değiştirme

1. aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve **&-posta** \> işbirliği rollerine gidin İzinler **& rolleri** \> **E-& rollerini** \> **gönderin**. Doğrudan İzinler sayfasına **gitmek** için kullanın <https://security.microsoft.com/emailandcollabpermissions>.

2. İzinler  sayfasında, listeden değiştirmek istediğiniz rol grubunu seçin. Ad sütun başlığına **tıklar** ve listeyi adına göre sıralar veya Ara Ara **simgesine** ![tıklarsanız.](../../media/m365-cc-sc-search-icon.png) rol grubunu bulun.

3. Görüntülenen rol grubu ayrıntıları açılır öğesinin Üyeler bölümünde **Düzenle'ye** tıklayın.

4. Görüntülenen **Düzenleme üyelerini** seçin sayfasında, aşağıdaki adımlardan birini uygulayın:
   - Rol grubu üyesi yoksa Üye **seç'e tıklayın**.
   - Mevcut rol grubu üyeleri varsa Düzenle'ye **tıklayın.**

5. Görüntülenen **Üyeleri seçin** açılır menüsünde, aşağıdaki adımlardan birini uygulayın:

   - **Ekle**'ye tıklayın. Görüntülenen kullanıcılar listesinde bir veya birden çok kullanıcı seçin. Ya da Arama Arama **simgesine** ![de tıkabilirsiniz.](../../media/m365-cc-sc-search-icon.png) öğesini seçerek kullanıcıları bulun ve seçin.

     Eklemek istediğiniz kullanıcıları seçtikten sonra Ekle'ye **tıklayın**.

   - **Kaldır**'a tıklayın. Mevcut üyelerin birini veya daha fazlasını seçin. Ya da Arama Arama **simgesine** ![de tıkabilirsiniz.](../../media/m365-cc-sc-search-icon.png) öğesini seçerek üyeleri bulup seçin.

     Kaldırmak istediğiniz kullanıcıları seçtikten sonra Kaldır'a **tıklayın**.

6. Üye seç uç **menüsünde** Bitti'ye **tıklayın**.

7. Düzenleme üyeleri seçme **sayfasına geri dönüp** Kaydet'e **tıklayın**.

8. Rol grubu ayrıntıları uçmaya geri dönüp Bitti'ye **tıklayın**.
