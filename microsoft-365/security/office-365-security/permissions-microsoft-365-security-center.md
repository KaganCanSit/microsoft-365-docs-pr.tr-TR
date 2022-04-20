---
title: Microsoft 365 Defender portalındaki izinler
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
description: Yöneticiler, güvenlikle ilgili tüm görevler için Microsoft 365 Defender portalında izinleri yönetmeyi öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3381d3eb823b818aec01a181f176cb56f6af310c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939201"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalındaki izinler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm Microsoft 365 hizmetleri kapsayan güvenlik senaryolarını yönetmeniz gerekir. Ayrıca kuruluşunuzdaki doğru kişilere doğru yönetici izinlerini verme esnekliğine sahip olmanız gerekir.

konumundaki <https://security.microsoft.com> Microsoft 365 Defender portalı, Microsoft 365'da güvenlik görevlerini gerçekleştiren kullanıcılar için izinleri doğrudan yönetmeyi destekler. İzinleri yönetmek için Microsoft 365 Defender portalını kullanarak, güvenlikle ilgili tüm görevler için izinleri merkezi olarak yönetebilirsiniz.

Microsoft 365 Defender portalındaki izinleri yönetmek için **İzinler & rolleri** veya <https://security.microsoft.com/securitypermissions>bölümüne gidin. Microsoft 365 Defender portalında **genel yönetici** veya **Kuruluş Yönetimi** rol grubunun üyesi olmanız gerekir. Özellikle, **Rol Yönetimi** rolü kullanıcıların Microsoft 365 Defender portalında rol gruplarını görüntülemesine, oluşturmasına ve değiştirmesine olanak tanır ve bu rol varsayılan olarak yalnızca **Kuruluş Yönetimi** rol grubuna atanır.

> [!NOTE]
> Microsoft Purview uyumluluk portalındaki izinler hakkında bilgi için bkz. [Microsoft Purview uyumluluk portalında İzinler](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

Microsoft 365 Defender portalındaki izinler rol tabanlı erişim denetimi (RBAC) izin modelini temel alır. RBAC, çoğu Microsoft 365 hizmeti tarafından kullanılan izin modeliyle aynıdır, bu nedenle bu hizmetlerdeki izin yapısı hakkında bilgi sahibiyseniz, Microsoft 365 Defender portalında izinler vermek çok tanıdık olacaktır.

**Rol**, bir dizi görevi yerine getirmek için izinler verir.

**Rol grubu**, kişilerin işlerini Microsoft 365 Defender portalında yapmalarına olanak tanıyan bir dizi roldür.

Microsoft 365 Defender portalı>, atamanız gereken en yaygın görevler ve işlevler için varsayılan rol gruplarını içerir. Genel olarak, varsayılan rol gruplarına tek tek kullanıcıları **üye** olarak eklemenizi öneririz.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Rol grubunun rolleri ve üyeleriyle ilişkisi" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalındaki roller ve rol grupları

Aşağıdaki rol ve rol grubu türleri, Microsoft 365 Defender portalındaki **İzinler & rolleri** sayfasında <https://security.microsoft.com/securitypermissions> bulunabilir:

- **Azure AD rolleri**: Rolleri ve atanan kullanıcıları görüntüleyebilirsiniz ancak bunları doğrudan Microsoft 365 Defender portalında yönetemezsiniz. Azure AD rolleri, **tüm** Microsoft 365 hizmetleri için izinler atayan merkezi rollerdir.

- **E-posta & işbirliği rolleri**: Bunlar Güvenlik & Uyumluluk Merkezi'nde bulunan rol gruplarıyla aynıdır, ancak bunları doğrudan Microsoft 365 Defender portalında yönetebilirsiniz. Burada atadığınız izinler Microsoft 365 Defender portalına, Microsoft Purview uyumluluk portalına ve Güvenlik & Uyumluluk Merkezi'ne özgü olup diğer Microsoft 365 iş yüklerinde gerekli olan tüm izinleri kapsamaz.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="Microsoft 365 Defender portalındaki İzinler & rolleri sayfası" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Azure AD rolleri

adresinde Microsoft 365 Defender portalını <https://security.microsoft.com> açıp **E-posta & işbirliği rolleri** \> **İzinleri & roller** \> **Azure AD rolleri** \> **Rolleri** 'ne (veya doğrudan adresine<https://security.microsoft.com/aadpermissions>) gittiğinizde, bu bölümde açıklanan Azure AD rollerini görürsünüz.

Bir rol seçtiğinizde, rolün açıklamasını ve kullanıcı atamalarını içeren ayrıntılar açılır öğesi görüntülenir. Ancak bu atamaları yönetmek için ayrıntılar açılır **öğesinde Azure AD'de üyeleri yönet'e** tıklamanız gerekir.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="Azure Active Directory'de izinleri yönetme bağlantısı" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

Daha fazla bilgi için bkz. [Azure Active Directory'da yönetici rollerini görüntüleme ve atama](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rol|Açıklama|
|---|---|
|**Genel yönetici**|Tüm Microsoft 365 hizmetlerindeki tüm yönetim özelliklerine erişim. Yalnızca genel yöneticiler diğer yönetici rollerini atayabilir. Daha fazla bilgi için bkz. [Genel Yönetici / Şirket Yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Uyumluluk veri yöneticisi**|Kuruluşunuzun verilerini Microsoft 365 takip edin, korunduğundan emin olun ve riskleri azaltmaya yardımcı olacak sorunlarla ilgili içgörüler edinin. Daha fazla bilgi için bkz [. Uyumluluk Verileri Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Uyumluluk yöneticisi**|Kuruluşunuzun tüm mevzuat gereksinimleriyle uyumlu kalmasına, eBulma servis taleplerini yönetmeye ve Microsoft 365 konumlar, kimlikler ve uygulamalar arasında veri idaresi ilkelerini korumalarına yardımcı olun. Daha fazla bilgi için bkz [. Uyumluluk Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Güvenlik operatörü**|Microsoft 365 kullanıcılarınıza, cihazlarınıza ve içeriğinize yönelik etkin tehditleri görüntüleyin, araştırın ve yanıt verin. Daha fazla bilgi için bkz [. Güvenlik İşleci](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Güvenlik gözetmeni**|Microsoft 365 kullanıcılarınıza, cihazlarınıza ve içeriğinize yönelik etkin tehditleri görüntüleyin ve araştırın, ancak (Güvenlik işlecinden farklı olarak) eylem gerçekleştirerek yanıt verme izinleri yoktur. Daha fazla bilgi için bkz [. Güvenlik Okuyucusu](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Güvenlik yöneticisi**|Güvenlik ilkelerini yöneterek, Microsoft 365 ürünleri genelinde güvenlik analizlerini ve raporlarını gözden geçirerek ve tehdit ortamı konusunda güncel kalarak kuruluşunuzun genel güvenliğini kontrol edin. Daha fazla bilgi için bkz [. Güvenlik Yöneticisi](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Genel okuyucu**|**Genel yönetici** rolünün salt okunur sürümü. Microsoft 365 genelinde tüm ayarları ve yönetim bilgilerini görüntüleyin. Daha fazla bilgi için bkz. [Genel Okuyucu](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Saldırı benzetimi yöneticisi**|[Saldırı simülasyonu](attack-simulation-training.md) oluşturma, simülasyon başlatma/zamanlama ve simülasyon sonuçlarının gözden geçirilmesinin tüm yönlerini oluşturun ve yönetin. Daha fazla bilgi için bkz [. Saldırı Benzetimi Yöneticisi](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Saldırı yükü yazarı**|Saldırı yükleri oluşturun, ancak aslında başlatmayı veya zamanlamayı değil. Daha fazla bilgi için bkz [. Saldırı Yükü Yazarı](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında e-posta & işbirliği rolleri

Microsoft 365 Defender portalını adresinde <https://security.microsoft.com> açıp **E-posta & işbirliği rollerine** \> **İzinler & roller** \> **E-posta & işbirliği rolleri** \> **Rolleri** 'ne (veya doğrudan adresine<https://security.microsoft.com/emailandcollabpermissions>) gittiğinizde, Güvenlik & Uyumluluk Merkezi'nde bulunan rol gruplarının aynısını görürsünüz.

Bu rol grupları hakkında tam bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'nde İzinler](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında E-posta & işbirliği rolü üyeliğini değiştirme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği rolleri** \> **İzinler & roller** \> **E-posta & işbirliği rolleri** \> **Rolleri'ne** gidin. **doğrudan İzinler** sayfasına gitmek için kullanın<https://security.microsoft.com/emailandcollabpermissions>.

2. **İzinler** sayfasında, listeden değiştirmek istediğiniz rol grubunu seçin. Listeyi ada göre sıralamak için **Ad** sütunu üst bilgisine veya **Arama Arama** ![simgesine tıklayabilirsiniz.](../../media/m365-cc-sc-search-icon.png) öğesini seçin.

3. Görüntülenen rol grubu ayrıntıları açılır öğesinde **, Üyeler** bölümünde **Düzenle'ye** tıklayın.

4. Görüntülenen **Üyeleri seçmeyi düzenleme** sayfasında aşağıdaki adımlardan birini yapın:
   - Rol grubu üyesi yoksa **Üye seç'e** tıklayın.
   - Mevcut rol grubu üyeleri varsa **Düzenle'ye** tıklayın

5. Görüntülenen **Üyeleri seçin** açılır öğesinde aşağıdaki adımlardan birini yapın:

   - **Ekle**'ye tıklayın. Görüntülenen kullanıcı listesinde bir veya daha fazla kullanıcı seçin. İsterseniz Arama **Arama** ![simgesine de tıklayabilirsiniz.](../../media/m365-cc-sc-search-icon.png) ögesini seçerek kullanıcıları bulun ve seçin.

     Eklemek istediğiniz kullanıcıları seçtiğinizde **Ekle'ye** tıklayın.

   - **Kaldır**'a tıklayın. Mevcut üyelerden birini veya daha fazlasını seçin. İsterseniz Arama **Arama** ![simgesine de tıklayabilirsiniz.](../../media/m365-cc-sc-search-icon.png) ögesini seçerek üyeleri bulun ve seçin.

     Kaldırmak istediğiniz kullanıcıları seçtiğinizde **Kaldır'a** tıklayın.

6. **Üyeleri seçin** açılır menüsüne geri dönüp **Bitti'ye** tıklayın.

7. **Üyeleri seçmeyi düzenleme** sayfasına geri dönüp **Kaydet'e** tıklayın.

8. Rol grubu ayrıntıları açılır menüsüne geri dönüp **Bitti'ye** tıklayın.
