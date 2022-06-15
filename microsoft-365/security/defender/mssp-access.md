---
title: Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) erişimi sağlama
description: Microsoft Defender Güvenlik Merkezi Microsoft 365 Defender portalındaki değişiklikler hakkında bilgi edinin
keywords: Microsoft 365 Defender portalı, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, MDO, MDE, tek bölmeli cam, yakınsanmış portal, güvenlik portalı, defender güvenlik portalı ile çalışmaya başlama
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
ms.openlocfilehash: 4eccd4d6140810bae4caef5e194082aeb3054217
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102382"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) erişimi sağlama 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Şunlar için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Çok kiracılı bir temsilci erişim çözümü uygulamak için aşağıdaki adımları izleyin:

1. Microsoft 365 Defender portalı aracılığıyla Uç Nokta için Defender için [rol tabanlı erişim denetimini](/microsoft-365/security/defender-endpoint/rbac) etkinleştirin ve Azure Active Directory (Azure AD) gruplarına bağlanın.

2. Erişim isteklerini ve sağlamayı etkinleştirmek için Azure AD Kimlik İdaresi içindeki [dış kullanıcılar için yetkilendirme yönetimini](/azure/active-directory/governance/entitlement-management-external-users) yapılandırın.

3. [Microsoft Myaccess'te](/azure/active-directory/governance/entitlement-management-request-approve) erişim isteklerini ve denetimlerini yönetin.

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Uç Nokta için Microsoft Defender rol tabanlı erişim denetimlerini etkinleştirme

1. **Müşteri AAD'sinde MSSP kaynakları için erişim grupları oluşturma: Gruplar**

    Bu gruplar, Microsoft 365 Defender portalında Uç Nokta için Defender'da oluşturduğunuz Rollere bağlanır. Bunu yapmak için müşteri AD kiracısında üç grup oluşturun. Örnek yaklaşımımızda aşağıdaki grupları oluştururuz:

    - Katman 1 Analisti
    - Katman 2 Analisti
    - MSSP Analist Onaylayanları  

2. Microsoft 365 Defender portalı rollerinde ve gruplarında Uç Nokta için Customer Defender'da uygun erişim düzeyleri için Uç Nokta için Defender rolleri oluşturun.

    Müşteri Microsoft 365 Defender portalında RBAC'yi etkinleştirmek için, Genel Yönetici veya Güvenlik Yöneticisi haklarına sahip bir kullanıcı hesabıyla > **Rolleri & Gruplar > Uç Noktalar rollerine** erişin.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Microsoft 365 Defender portalında MSSP erişiminin ayrıntıları" lightbox="../../media/mssp-access.png":::

    Ardından MSSP SOC Katmanı gereksinimlerini karşılamak için RBAC rolleri oluşturun. Bu rolleri "Atanan kullanıcı grupları" aracılığıyla oluşturulan kullanıcı gruplarına bağlayın.

    İki olası rol:

    - **Katman 1 Analistleri** <br>
      Canlı yanıt dışındaki tüm eylemleri gerçekleştirin ve güvenlik ayarlarını yönetin.

    - **Katman 2 Analistleri** <br>
      [Canlı yanıta](/microsoft-365/security/defender-endpoint/live-response) ek olarak Katman 1 özellikleri.

    Daha fazla bilgi için bkz. [Rol tabanlı erişim denetimini kullanarak portal erişimini yönetme](/microsoft-365/security/defender-endpoint/rbac).

## <a name="configure-governance-access-packages"></a>İdare Erişim Paketlerini Yapılandırma

1. **Müşteri AAD'sinde BAĞLı Kuruluş olarak MSSP Ekleme: Kimlik İdaresi**

    MSSP'nin bağlı bir kuruluş olarak eklenmesi, MSSP'nin istekte bulunmasını ve erişim sağlamasını sağlar. 

    Bunu yapmak için, müşteri AD kiracısında Kimlik İdaresi: Bağlı kuruluş'a erişin. Yeni bir kuruluş ekleyin ve Kiracı Kimliği veya Etki Alanı aracılığıyla MSSP Analisti kiracınızı arayın. MSSP Analistleriniz için ayrı bir AD kiracısı oluşturmanızı öneririz.

2. **Müşteri AAD'sinde kaynak kataloğu oluşturma: Kimlik İdaresi**

    Kaynak katalogları, müşteri AD kiracısında oluşturulan mantıksal bir erişim paketleri koleksiyonutur.

    Bunu yapmak için, müşteri AD kiracısında Kimlik İdaresi: Kataloglar'a erişin ve **Yeni Katalog** ekleyin. Örneğimizde **buna MSSP Erişimleri** adını diyoruz.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Microsoft 365 Defender portalında yeni bir katalog" lightbox="../../media/goverance-catalog.png":::


    Daha fazla bilgi için bkz. [Kaynak kataloğu oluşturma](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **MSSP kaynakları için erişim paketleri oluşturma Customer AAD: Identity Governance**

    Erişim paketleri, istekte bulunana onay üzerine verilecek hakların ve erişimlerin toplanmasıdır. 

    Bunu yapmak için müşteri AD kiracısında Kimlik İdaresi: Erişim Paketleri'ne erişin ve **Yeni Erişim Paketi** ekleyin. MSSP onaylayanları ve her analist katmanı için bir erişim paketi oluşturun. Örneğin, aşağıdaki Katman 1 Analist yapılandırması şu şekilde bir erişim paketi oluşturur:

    - YENI istekleri yetkilendirmek için **AD grubu MSSP Analist Onaylayanlarının** bir üyesini gerektirir
    - SOC analistlerinin erişim uzantısı isteyebileceği yıllık erişim gözden geçirmeleri vardır
    - Yalnızca MSSP SOC Kiracısı'ndaki kullanıcılar tarafından istenebilir
    - Erişimin otomatik süresi 365 gün sonra doluyor

    :::image type="content" source="../../media/new-access-package.png" alt-text="Microsoft 365 Defender portalında yeni erişim paketinin ayrıntıları" lightbox="../../media/new-access-package.png":::

    Daha fazla bilgi için bkz. [Yeni erişim paketi oluşturma](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Müşteri AAD'den MSSP kaynaklarına erişim isteği bağlantısı sağlama: Kimlik İdaresi**

    Erişimim portalı bağlantısı, MSSP SOC analistleri tarafından oluşturulan erişim paketleri aracılığıyla erişim istemek için kullanılır. Bağlantı dayanıklıdır, yani aynı bağlantı zaman içinde yeni analistler için kullanılabilir. Analist isteği **, MSSP Analist Onaylayanları** tarafından onay için bir kuyruğa girer.

    :::image type="content" source="../../media/access-properties.png" alt-text="Microsoft 365 Defender portalındaki erişim özellikleri" lightbox="../../media/access-properties.png":::

    Bağlantı, her erişim paketinin genel bakış sayfasında bulunur.

## <a name="manage-access"></a>Erişimi yönetin

1. Müşteri ve/veya MSSP myaccess'te erişim isteklerini gözden geçirin ve yetkilendirin.

    Erişim istekleri, MSSP Analist Onaylayanları grubunun üyeleri tarafından Erişimim müşterisinde yönetilir.

    Bunu yapmak için aşağıdakini kullanarak müşterinin myaccess'ine erişin: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Örnek: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Kullanıcı arabiriminin **Onaylar** bölümünde istekleri onaylayın veya reddedin.

     Bu noktada analist erişimi sağlanmıştır ve her analistin müşterinin Microsoft 365 Defender portalına erişebilmesi gerekir:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` atanmış izinler ve rollerle birlikte.
