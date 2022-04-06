---
title: Yönetilen güvenlik hizmeti sağlayıcısına (MSSP) erişim izni ver
description: SISTEM ayarlarıyla MSSP tümleştirmeyi yapılandırmak için gerekli Uç Nokta için Microsoft Defender
keywords: yönetilen güvenlik hizmeti sağlayıcısı, mssp, yapılandırma, tümleştirme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c8a96f3dba51de09a7237279b4053b9f4ed9b4a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470493"
---
# <a name="grant-managed-security-service-provider-mssp-access-preview"></a>Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) erişimi (önizleme) ver

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Çok kiracılı bir temsilcili erişim çözümü uygulamak için aşağıdaki adımları izleyin:

1. Uç [nokta için Defender'da rol](rbac.md) tabanlı erişim denetimi etkinleştirin ve Active Directory (AD) gruplarıyla bağlanın.

2. Erişim [isteği ve hazırlama](/azure/active-directory/governance/identity-governance-overview) için Yönetim Erişim Paketlerini yapılandırabilirsiniz.

3. Microsoft Myaccess'te erişim isteklerini ve [denetimlerini yönetin](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint"></a>Web'de rol tabanlı erişim denetimlerini Uç Nokta için Microsoft Defender

1. **Müşteri Hizmetleri'ne MSSP kaynakları için erişim grupları AAD grupları: Gruplar**

    Bu gruplar, Uç Nokta için Defender'da oluşturan Roller'e bağlanacak. Bunu yapmak için, müşteri AD kiracıda üç grup oluşturun. Örnek yaklaşımımızda, aşağıdaki grupları oluşturduk:

    - Katman 1 Analisti
    - Katman 2 Analisti
    - MSSP Analisti Onaylayanlar

2. Uç Nokta için Customer Defender'da uygun erişim düzeyleri için Uç nokta rolleri için Defender oluşturun.

    Müşteri Microsoft 365 Defender portalında RBAC'yi etkinleştirmek için, Genel Yönetici  veya Güvenlik Yöneticisi hakları olan bir kullanıcı hesabından Ayarlar > İzinleri ve > Roller'e ve "Rolleri aç" seçeneğine erişin.

    :::image type="content" source="images/mssp-access.png" alt-text="MSSP erişimi" lightbox="images/mssp-access.png":::

    Ardından, MSSP SOC Katman  ihtiyaçlarını karşılamak için RBAC rolleri oluşturun. Bu rolleri "Atanan kullanıcı grupları" aracılığıyla oluşturulan kullanıcı gruplarına bağlama.

    İki olası rol:

    - **Katman 1 Analistleri**

      Canlı yanıt dışında tüm eylemleri gerçekleştirin ve güvenlik ayarlarını yönetin.

    - **Katman 2 Analistleri**

      Canlı yanıt ekleme ile Katman 1 [özellikleri](live-response.md)

    Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi kullanma](rbac.md).

## <a name="configure-governance-access-packages"></a>Yönetim Erişimi Paketlerini Yapılandırma

1. **MÜŞTERI Hizmetleri'ne MSSP'yi Bağlı Kuruluş AAD: Kimlik Yönetimi**

    MSSP'yi bağlantılı kuruluş olarak eklemek, MSSP'nin istekte olmasına ve sağlanan erişimlere sahip olmasına olanak sağlar.

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Bağlı kuruluş'a erişin. Kiracı Kimliği veya Etki Alanı aracılığıyla yeni bir kuruluş ekleyin ve MSSP Analisti kiracınızı arama. MSSP Analistleriniz için ayrı bir AD kiracısı oluşturmanızı öneririz.

2. **Müşteri Hizmetleri'nin içinde kaynak AAD oluşturma: Kimlik Yönetimi**

    Kaynak katalogları, müşteri AD kiracısı içinde oluşturulmuş mantıksal bir erişim paketleri koleksiyonudur.

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Kataloglar'a erişin ve Yeni Katalog **ekleyin**. Örneğimizde, biz buna **MSSP Erişimi 1222 02/2013 2013 2013'te izin ve daha sonra MSSP Erişimleri**

    :::image type="content" source="images/goverance-catalog.png" alt-text="Yeni katalog sayfası" lightbox="images/goverance-catalog.png":::

    Daha fazla bilgi için bkz [. Kaynak kataloğu oluşturma](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **MSSP kaynakları için erişim paketleri oluşturma Müşteri AAD: Kimlik Yönetimi**

    Erişim paketleri, onay üzerine istekte bulunduracak olan hakların ve erişimin koleksiyonudur.

    Bunu yapmak için, müşteri AD kiracısinde Kimlik Yönetimi: Access Paketleri ve Yeni Erişim Paketi **ekleyin**. MSSP onaylayanlar ve her analist katmanı için bir erişim paketi oluşturun. Örneğin, aşağıdaki Katman 1 Analisti yapılandırması aşağıdaki gibi bir erişim paketi oluşturur:

    - YENI istekleri yetkilendirmek için AD grubunun **MSSP Analisti** Onaylayanlar üyesi gerekir
    - SOC analistleri erişim uzantısını talep  edildiklerine yönelik yıllık erişim incelemelerine sahip
    - YALNıZCA MSSP SOC Kiracısı'nın kullanıcıları tarafından istenenler
    - Access'in otomatik kullanım süresi 365 gün sonra dolacak

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/new-access-package.png" alt-text="Yeni erişim paketi sayfası" lightbox="images/new-access-package.png":::

    Daha fazla bilgi için bkz [. Yeni erişim paketi oluşturma](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Müşteri Yönetimi'den MSSP kaynaklarına erişim isteği AAD: Kimlik Yönetimi**

    Erişimim portalı bağlantısı MSSP SOC analistleri tarafından, oluşturulan erişim paketleri üzerinden erişim isteğide kullanılmaktadır. Bağlantı dayanıklıdır, başka bir ifadeyle aynı bağlantı zaman içinde yeni analistler için kullanılabilir. Analist isteği, MSSP Analisti Onaylayanlar tarafından onay **almak için sıraya girdi**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/access-properties.png" alt-text="Özellikler sayfası" lightbox="images/access-properties.png":::

    Bağlantı, her erişim paketinin genel bakış sayfasında yer almaktadır.

## <a name="manage-access"></a>Erişimi yönetin

1. Müşteri ve/veya MSSP myaccess'te erişim isteklerini gözden geçirip yetkilendiin.

    Erişim istekleri, MSSP Analisti Onaylayanlar grubunun üyeleri tarafından Müşteri Erişimim'de yönetilir.

    Bunu yapmak için müşterinin erişimine erişmek için şunları kullanın: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Örnek: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Kullanıcı arabiriminin En **Son Onaylar istekleri** onaylar veya reddedin.

    Bu noktada, analist erişimi sağlandı ve her analist müşterinin müşteri portalına Microsoft 365 Defender:`https://security.microsoft.com/?tid=<CustomerTenantId>`

## <a name="related-topics"></a>İlgili konular

- [MSSP müşteri portalına erişme](access-mssp-portal.md)
- [Uyarı bildirimlerini yapılandırma](configure-mssp-notifications.md)
- [Müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md)
