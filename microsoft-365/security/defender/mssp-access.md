---
title: Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) erişimi sağlama
description: Web portalında yapılan Microsoft Defender Güvenlik Merkezi hakkında Microsoft 365 Defender öğrenin
keywords: Microsoft 365 Defender portalı, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, MDO, MDE, tek cam bölmesi, yakınsaan portal, güvenlik portalı, defender güvenlik portalı ile çalışmaya başlama
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
manager: dansimp
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.openlocfilehash: f0148a8bfe18c7636e95ceae7b268cc70b2e58ed
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500426"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) erişimi sağlama 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Çok kiracılı bir temsilcili erişim çözümü uygulamak için aşağıdaki adımları izleyin:

1. Microsoft 365 Defender portalı [üzerinden](/windows/security/threat-protection/microsoft-defender-atp/rbac) Uç Nokta için Defender için rol tabanlı erişim denetimi etkinleştirin ve Azure Active Directory (Azure AD) gruplarıyla bağlanın.

2. Erişim [isteği ve hazırlama](/azure/active-directory/governance/identity-governance-overview) için Yönetim Erişim Paketlerini yapılandırabilirsiniz.

3. Microsoft Myaccess'te erişim isteklerini ve [denetimlerini yönetin](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında yer alan Uç Nokta için Microsoft Defender tabanlı erişim denetimlerini etkinleştirme

1. **Müşteri Hizmetleri'ne MSSP kaynakları için erişim grupları AAD grupları: Gruplar**

    Bu gruplar, Microsoft 365 Defender portalında Uç nokta için Defender'da Microsoft 365 Defender bağlantısındadır. Bunu yapmak için, müşteri AD kiracıda üç grup oluşturun. Örnek yaklaşımımızda, aşağıdaki grupları oluşturduk:

    - Katman 1 Analisti
    - Katman 2 Analisti
    - MSSP Analisti Onaylayanlar  

2. Portal rol ve gruplarında, Uç Nokta için Customer Defender'da uygun erişim düzeyleri Microsoft 365 Defender Için Uç nokta rolleri için Defender oluşturun.

    RBAC'yi müşteri Microsoft 365 Defender portalında etkinleştirmek için, Genel Yönetici veya Güvenlik Yöneticisi hakları olan bir kullanıcı **hesabıyla & grupların İzinler >** Uç Noktaları rollerine > Rollerine erişin.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Microsoft 365 Defender portalında MSSP erişiminin ayrıntıları" lightbox="../../media/mssp-access.png":::

    Ardından, MSSP SOC Katman  ihtiyaçlarını karşılamak için RBAC rolleri oluşturun. Bu rolleri "Atanan kullanıcı grupları" aracılığıyla oluşturulan kullanıcı gruplarına bağlama.

    İki olası rol:

    - **Katman 1 Analistleri** <br>
      Canlı yanıt dışında tüm eylemleri gerçekleştirin ve güvenlik ayarlarını yönetin.

    - **Katman 2 Analistleri** <br>
      Canlı yanıt ekleme ile Katman 1 [özellikleri](/windows/security/threat-protection/microsoft-defender-atp/live-response)

    Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi kullanma](/windows/security/threat-protection/microsoft-defender-atp/rbac).

## <a name="configure-governance-access-packages"></a>Yönetim Erişimi Paketlerini Yapılandırma

1. **MÜŞTERI Hizmetleri'ne MSSP'yi Bağlı Kuruluş AAD: Kimlik Yönetimi**

    MSSP'yi bağlantılı kuruluş olarak eklemek, MSSP'nin istekte olmasına ve sağlanan erişimlere sahip olmasına olanak sağlar. 

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Bağlı kuruluş'a erişin. Kiracı Kimliği veya Etki Alanı aracılığıyla yeni bir kuruluş ekleyin ve MSSP Analisti kiracınızı arama. MSSP Analistleriniz için ayrı bir AD kiracısı oluşturmanızı öneririz.

2. **Müşteri Hizmetleri'nin içinde kaynak AAD oluşturma: Kimlik Yönetimi**

    Kaynak katalogları, müşteri AD kiracısı içinde oluşturulmuş mantıksal bir erişim paketleri koleksiyonudur.

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Kataloglar'a erişin ve Yeni Katalog **ekleyin**. Örneğimizde, biz buna **MSSP Erişimi 1222 02/2013 2013 2013'te izin ve daha sonra MSSP Erişimleri**

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Web portalında yeni Microsoft 365 Defender kataloğu" lightbox="../../media/goverance-catalog.png":::


    Daha fazla bilgi için bkz [. Kaynak kataloğu oluşturma](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **MSSP kaynakları için erişim paketleri oluşturma Müşteri AAD: Kimlik Yönetimi**

    Erişim paketleri, onay üzerine istekte bulunduracak olan hakların ve erişimin koleksiyonudur. 

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Access Paketleri ve Yeni Erişim Paketi **ekleyin**. MSSP onaylayanlar ve her analist katmanı için bir erişim paketi oluşturun. Örneğin, aşağıdaki Katman 1 Analisti yapılandırması aşağıdaki gibi bir erişim paketi oluşturur:

    - YENI istekleri yetkilendirmek için AD grubunun **MSSP Analisti** Onaylayanlar üyesi gerekir
    - SOC analistleri erişim uzantısını talep  edildiklerine yönelik yıllık erişim incelemelerine sahip
    - YALNıZCA MSSP SOC Kiracısı'nın kullanıcıları tarafından istenenler
    - Access'in otomatik kullanım süresi 365 gün sonra dolacak

    :::image type="content" source="../../media/new-access-package.png" alt-text="Portalda yeni bir erişim paketinin Microsoft 365 Defender." lightbox="../../media/new-access-package.png":::

    Daha fazla bilgi için bkz [. Yeni erişim paketi oluşturma](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Müşteri Yönetimi'den MSSP kaynaklarına erişim isteği AAD: Kimlik Yönetimi**

    Erişimim portalı bağlantısı MSSP SOC analistleri tarafından, oluşturulan erişim paketleri üzerinden erişim isteğide kullanılmaktadır. Bağlantı dayanıklıdır, başka bir ifadeyle aynı bağlantı zaman içinde yeni analistler için kullanılabilir. Analist isteği, MSSP Analisti Onaylayanlar tarafından onay **almak için sıraya girdi**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Microsoft 365 Defender portalında erişim özellikleri" lightbox="../../media/access-properties.png":::

    Bağlantı, her erişim paketinin genel bakış sayfasında yer almaktadır.

## <a name="manage-access"></a>Erişimi yönetin

1. Müşteri ve/veya MSSP myaccess'te erişim isteklerini gözden geçirip yetkilendiin.

    Erişim istekleri, MSSP Analisti Onaylayanlar grubunun üyeleri tarafından Müşteri Erişimim'de yönetilir.

    Bunu yapmak için müşterinin erişimine erişmek için şunları kullanın: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Örnek: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Kullanıcı arabiriminin En **Son Onaylar istekleri** onaylar veya reddedin.

     Bu noktada, analist erişimi sağlandı ve her analist müşterinin müşteri portalına Microsoft 365 Defender:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` atanmış olan izinler ve rollerle ilgili bilgi içerir.

> [!IMPORTANT]
> Şu anda portalda Uç Nokta için Microsoft Defender posta Microsoft 365 Defender temsilci erişimi, tarayıcı penceresi başına tek bir kiracıya erişime izin verir.
