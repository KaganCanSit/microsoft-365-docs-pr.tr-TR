---
title: Uç Nokta için Microsoft Defender Plan 1'i ayarlama ve yapılandırma
description: Uç Nokta Planı 1 için Defender'ı ayarlamayı ve yapılandırmayı öğrenin. Gereksinimleri gözden geçirin, dağıtımınızı planlayın ve ortamınızı ayarlayın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e94a0ee04d45e92d5891c73ba3a70ac2f05cd482
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485967"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Uç Nokta için Microsoft Defender Plan 1'i ayarlama ve yapılandırma

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, Uç Nokta Planı 1 için Defender'ın nasıl ayarlanacağı ve yapılandırıldığı açıklanır. İster yardım ister kendiniz yapın, bu makaleyi dağıtımınız boyunca kılavuz olarak kullanabilirsiniz.  

## <a name="the-setup-and-configuration-process"></a>Kurulum ve yapılandırma işlemi

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Uç Nokta için Microsoft Defender Plan 1 için kurulum ve dağıtım akışı" lightbox="images/mde-p1-deploymentflow.png":::

Uç Nokta Planı 1 için Defender için genel kurulum ve yapılandırma işlemi aşağıdaki gibidir: <br/><br/>


| Sayı  | Adım  | Açıklama  |
|:---------:|:---------|:---------|
| 1 | [Gereksinimleri gözden geçirin](#review-the-requirements)  | Lisanslama, tarayıcı, işletim sistemi ve veri merkezi gereksinimlerini listeler   |
| 2 | [Dağıtımınızı planlayın](#plan-your-deployment) | Dikkate alınacak çeşitli dağıtım yöntemlerini listeler ve hangi yöntemi kullanacağınıza karar vermenize yardımcı olacak daha fazla kaynağa bağlantılar içerir  |
| 3 | [Kiracı ortamınızı ayarlama](#set-up-your-tenant-environment) | Kiracı ortamınızı ayarlamaya yönelik görevleri listeler |
| 4 | [Rol ve izin atama](#assign-roles-and-permissions) | Güvenlik ekibiniz için dikkate alınması gereken rolleri ve izinleri listeler <br/><br/>**İpucu**: Roller ve izinler atandığı anda güvenlik ekibiniz Microsoft 365 Defender portalını kullanmaya başlayabilir. Daha fazla bilgi edinmek için bkz. [Başlarken](mde-plan1-getting-started.md). |
| 5 | [Uç Nokta için Defender'a ekleme](#onboard-to-defender-for-endpoint) | Uç Nokta Planı 1 için Defender'a eklemek üzere işletim sistemine göre çeşitli yöntemleri listeler ve her yöntem için daha ayrıntılı bilgilerin bağlantılarını içerir  |
| 6 | [Yeni nesil korumayı yapılandırma](#configure-next-generation-protection) | Microsoft Endpoint Manager'de yeni nesil koruma ayarlarınızı yapılandırmayı açıklar  |
| 7 | [Saldırı yüzeyi azaltma özelliklerinizi yapılandırma](#configure-your-attack-surface-reduction-capabilities)        | Yapılandırabileceğiniz saldırı yüzeyi azaltma özelliklerinin türlerini listeler ve daha fazla kaynağa bağlantı içeren yordamlar içerir  |
 
## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirin

Aşağıdaki tabloda, Uç Nokta Planı 1 için Defender'ın temel gereksinimleri listeleniyor:<br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Lisans gereksinimleri | Uç Nokta Planı 1 için Defender (tek başına veya Microsoft 365 E3 veya A3'ün bir parçası olarak) |
| Tarayıcı gereksinimleri | Microsoft Edge <br/> Internet Explorer sürüm 11 <br/> Google Chrome |
| İşletim sistemleri | Windows 11 veya Windows 10, sürüm 1709 veya üzeri <br/>macOS (en son üç sürüm desteklenir) <br/>iOS <br/>Android işletim sistemi <br/><br/>Uç Nokta Planı 1 için Defender'ın tek başına sürümünün sunucu lisanslarını içermediğini unutmayın. Sunucuları eklemek için Bulut için Defender teklifinin bir parçası olarak Sunucular için [Defender](/azure/defender-for-cloud/defender-for-cloud-introduction) Plan 1 veya Plan 2 gerekir. Daha fazla bilgi edinmek için. Bkz [. Sunucular için Microsoft Defender'a genel bakış](/azure/defender-for-cloud/defender-for-servers-introduction). |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Birleşik Devletler |


## <a name="plan-your-deployment"></a>Dağıtımınızı planlayın

Dağıtımınızı planlarken, birkaç farklı mimari ve dağıtım yöntemi arasından seçim yapabilirsiniz. Her kuruluş benzersizdir, bu nedenle aşağıdaki tabloda listelendiği gibi dikkate almanız gereken birkaç seçenek vardır: <br/><br/>

| Yöntem | Açıklama |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Microsoft Endpoint Manager dahil) | Buluta özel bir ortamda uç noktaları yönetmek için Intune kullanma |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Configuration Manager](/mem/configmgr/core/understand/introduction) (Microsoft Endpoint Manager dahil) | Şirket içi ve bulut ortamına yayılan uç noktaları ve iş yüklerini yönetmek için Intune ve Configuration Manager kullanma |
| [Yapılandırma Yöneticisi](/mem/configmgr/core/understand/introduction) | Uç Nokta için Defender'ın bulut tabanlı gücüyle şirket içi uç noktaları korumak için Configuration Manager kullanın |
| Microsoft 365 Defender Portalı'ndan indirilen yerel betik | Pilot çalıştırmak veya yalnızca birkaç cihazı eklemek için uç noktalarda yerel betikleri kullanma |

Dağıtım seçenekleriniz hakkında daha fazla bilgi edinmek için bkz [. Uç Nokta dağıtımı için Defender'ınızı planlama](deployment-strategy.md). Ve aşağıdaki posteri indirin: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Dağıtım stratejisi posteri küçük resmi":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Dağıtım posterini alma](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Dağıtımınızı planlama hakkında daha ayrıntılı bilgi için bkz. [Uç Nokta için Microsoft Defender dağıtımınızı planlama](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Kiracı ortamınızı ayarlama

Kiracı ortamınızı ayarlama, aşağıdakiler gibi görevleri içerir:

- Lisanslarınızı doğrulama
- Kiracınızı yapılandırma
- Proxy ayarlarınızı yapılandırma (yalnızca gerekirse)
- Algılayıcıların doğru çalıştığından ve verileri Uç Nokta için Defender'a bildirildiğinden emin olun 

Bu görevler, Uç Nokta için Defender'ın kurulum aşamasına dahil edilir. Bkz. [Uç Nokta için Defender'ı ayarlama](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Rol ve izin atama

Microsoft 365 Defender portalına erişmek, Uç Nokta için Defender ayarlarını yapılandırmak veya algılanan tehditlerde yanıt eylemleri gerçekleştirmek gibi görevleri gerçekleştirmek için uygun izinlerin atanması gerekir. Uç Nokta için Defender [, Azure Active Directory'deki yerleşik rolleri](/azure/active-directory/roles/permissions-reference) kullanır. 

Microsoft, kullanıcılara yalnızca görevlerini gerçekleştirmek için ihtiyaç duydukları izin düzeyini atamanızı önerir. Temel izin yönetimini veya [rol tabanlı erişim denetimini](rbac.md) (RBAC) kullanarak izin atayabilirsiniz. 

- Temel izin yönetimi ile genel yöneticiler ve güvenlik yöneticileri tam erişime sahipken, güvenlik okuyucuları salt okunur erişime sahiptir.
- RBAC ile daha fazla rol aracılığıyla daha ayrıntılı izinler ayarlayabilirsiniz. Örneğin, güvenlik okuyucularınız, güvenlik işleçleriniz, güvenlik yöneticileriniz, uç nokta yöneticileriniz ve daha fazlası olabilir.


Aşağıdaki tabloda, kuruluşunuzda Uç Nokta için Defender için dikkate alınması gereken temel roller açıklanmaktadır: <br/><br/>

| Rol | Açıklama |
|:---|:---|
| Genel yöneticiler (genel yöneticiler olarak da adlandırılır) <br/><br/> *En iyi yöntem olarak genel yönetici sayısını sınırlayın.* | Genel yöneticiler her türlü görevi gerçekleştirebilir. Şirketinizi Microsoft 365 veya Uç Nokta için Microsoft Defender Plan 1 için kaydolan kişi varsayılan olarak genel yöneticidir. <br/><br/> Genel yöneticiler, aşağıdakiler gibi tüm Microsoft 365 portallarında ayarlara erişebilir/ayarları değiştirebilir: <br/>- Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Güvenlik yöneticileri (güvenlik yöneticileri olarak da adlandırılır) | Güvenlik yöneticileri güvenlik işleci görevlerinin yanı sıra aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlikle ilgili ilkeleri izleme <br/>- Güvenlik tehditlerini ve uyarılarını yönetme <br/>- Raporları görüntüleme |
| Güvenlik operatörü | Güvenlik işleçleri güvenlik okuyucusu görevlerinin yanı sıra aşağıdaki görevleri de gerçekleştirebilir: <br/>- Algılanan tehditler hakkındaki bilgileri görüntüleme <br/>- Algılanan tehditleri araştırma ve yanıtlama  |
| Güvenlik gözetmeni | Güvenlik okuyucuları aşağıdaki görevleri gerçekleştirebilir: <br/>- Microsoft 365 hizmetlerinde güvenlikle ilgili ilkeleri görüntüleme <br/>- Güvenlik tehditlerini ve uyarılarını görüntüleme <br/>- Raporları görüntüleme  |


> [!TIP]
> Azure Active Directory'deki roller hakkında daha fazla bilgi edinmek için bkz. [Azure Active Directory ile kullanıcılara yönetici ve yönetici olmayan roller atama](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Uç Nokta için Defender rolleri hakkında daha fazla bilgi için bkz. [Rol tabanlı erişim denetimi](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Uç Nokta için Defender'a ekleme

Kuruluşunuzun uç noktalarını eklemeye hazır olduğunuzda, aşağıdaki tabloda listelendiği gibi çeşitli yöntemler arasından seçim yapabilirsiniz: <br/><br/>

|Uç Nokta İşletim Sistemi | Ekleme yöntemleri|
|---|---|
| Windows 10 | [Yerel betik (en fazla 10 cihaz)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Aygıt Yöneticisi](configure-endpoints-mdm.md) <br> [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md)  |
| macOS | [Yerel betikler](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| iOS |[Uygulama tabanlı](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Ardından, yeni nesil koruma ve saldırı yüzeyi azaltma özelliklerinizi yapılandırmaya devam edin.

## <a name="configure-next-generation-protection"></a>Yeni nesil korumayı yapılandırma

Aşağıdaki görüntüde gösterildiği gibi kuruluşunuzun cihazlarını ve güvenlik ayarlarını yönetmek için [Microsoft Endpoint Manager](/mem) kullanmanızı öneririz:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Micorosft Endpoint Manager portalında uç nokta güvenlik ilkeleri" lightbox="../../media/mde-p1/endpoint-policies.png":::

Microsoft Endpoint Manager'da yeni nesil korumanızı yapılandırmak için şu adımları izleyin:

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Endpoint security** > **Virüsten Koruma'yı** ve ardından mevcut bir ilkeyi seçin. (Mevcut bir ilkeniz yoksa yeni bir ilke oluşturun.)

3. Virüsten koruma yapılandırma ayarlarınızı ayarlayın veya değiştirin. Yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın: <br/>

   - [Microsoft Intune Windows 10 Microsoft Defender Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [iOS özelliklerinde Uç Nokta için Defender'ı yapılandırma](ios-configure-features.md)

4. Ayarlarınızı belirtmeyi bitirdiğinizde **Gözden geçir ve kaydet'i** seçin.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Saldırı yüzeyi azaltma özelliklerinizi yapılandırma

Saldırı yüzeyini azaltma, kuruluşunuzun saldırılara açık olduğu yerleri ve yöntemleri azaltmakla alakalıdır. Uç Nokta Planı 1 için Defender, uç noktalarınızdaki saldırı yüzeylerinizi azaltmanıza yardımcı olacak çeşitli özellikler ve özellikler içerir. Bu özellikler ve özellikler aşağıdaki tabloda listelenmiştir: <br/><br/>

| Özellik/yetenek | Açıklama |
|:---|:---|
| [Saldırı yüzeyini azaltma kuralları](#attack-surface-reduction-rules) | Yazılım tabanlı riskli davranışları kısıtlamak ve kuruluşunuzun güvende kalmasına yardımcı olmak için saldırı yüzeyi azaltma kurallarını yapılandırın. Saldırı yüzeyi azaltma kuralları, örneğin belirli yazılım davranışlarını hedefler<br/>- Dosyaları indirmeye veya çalıştırmaya çalışan yürütülebilir dosyaları ve betikleri başlatma <br/>- Karartılmış veya başka bir şekilde şüpheli betikleri çalıştırma <br/>- Uygulamaların genellikle normal gündelik çalışma sırasında başlatmayabilecekleri davranışlar gerçekleştirme <br/><br/>Bu tür yazılım davranışları bazen meşru uygulamalarda görülür. Ancak bu davranışlar genellikle kötü amaçlı yazılım aracılığıyla saldırganlar tarafından yaygın olarak kötüye kullanıldıklarından riskli olarak kabul edilir.  |
| [Fidye yazılımı azaltma](#ransomware-mitigation) | Kuruluşunuzun değerli verilerini fidye yazılımı gibi kötü amaçlı uygulamalardan ve tehditlerden korumaya yardımcı olan denetimli klasör erişimini yapılandırarak fidye yazılımı azaltmayı ayarlayın. | 
| [Cihaz denetimi](#device-control) | Çıkarılabilir cihazlara (USB sürücüleri gibi) izin vermek veya bunları engellemek için kuruluşunuzun cihaz denetimi ayarlarını yapılandırın. | 
| [Ağ koruması](#network-protection) | Kuruluşunuzdaki kişilerin tehlikeli etki alanlarına veya İnternet'teki kötü amaçlı içeriğe erişen uygulamaları kullanmasını önlemek için ağ koruması ayarlayın. |
| [Web koruması](#web-protection) | Kuruluşunuzun cihazlarını kimlik avı sitelerinden, sitelerden yararlanmaya ve güvenilmeyen veya saygınlığı düşük diğer sitelerden korumak için web tehdit koruması ayarlayın. Web sitelerine erişimi içerik kategorilerine (Boş Zaman, Yüksek bant genişliği, Yetişkin içeriği veya Yasal sorumluluk gibi) göre izlemek ve düzenlemek için web içeriği filtrelemeyi ayarlayın. |
| [Ağ güvenlik duvarı](#network-firewall) | Ağ güvenlik duvarınızı, kuruluşunuzun cihazlarına hangi ağ trafiğinin girmesine veya dışarı çıkmasına izin verilenleri belirleyen kurallarla yapılandırın. |
| [Uygulama denetimi](#application-control)  | Windows cihazlarınızda yalnızca güvenilen uygulamaların ve işlemlerin çalışmasına izin vermek istiyorsanız uygulama denetimi kurallarını yapılandırın.    |

### <a name="attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kuralları

Saldırı yüzeyi azaltma kuralları Windows çalıştıran cihazlarda kullanılabilir. Aşağıdaki resimde gösterildiği gibi Microsoft Endpoint Manager kullanmanızı öneririz:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Microsoft Endpoint Manager portalında saldırı yüzeyi azaltma kuralları" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın.

2. **Uç nokta güvenliği** > **Saldırı yüzeyi azaltma** > **+ İlke oluştur'u** seçin.

3. **Platform** için **Windows 10 ve üzerini** seçin.

4. **Profil** için **Saldırı yüzeyi azaltma kuralları'nı** ve ardından **Oluştur'u** seçin.

5. **Temel Bilgiler** sekmesinde, ilke için bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

6. **Yapılandırma ayarları** sekmesinde **, Saldırı Yüzeyi Azaltma Kuralları'nı** genişletin.

7. Her kural için ayarları belirtin ve ardından **İleri'yi** seçin. (Her kuralın ne yaptığı hakkında daha fazla bilgi için bkz [. Saldırı yüzeyi azaltma kuralları](attack-surface-reduction.md).) 

8. **Kapsam etiketleri** sekmesinde, kuruluşunuz kapsam etiketleri kullanıyorsa **+ Kapsam etiketlerini seçin'i** ve ardından kullanmak istediğiniz etiketleri seçin. Ardından **İleri'yi** seçin. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. [Dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

9. **Atamalar** sekmesinde, ilkenizin uygulanacağı kullanıcıları ve grupları belirtin ve ardından **İleri'yi** seçin. (Atamalar hakkında daha fazla bilgi edinmek için bkz[. Microsoft Intune'de kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).)

10. **Gözden Geçir + oluştur** sekmesinde ayarları gözden geçirin ve **oluştur'u** seçin.

> [!TIP]
> Saldırı yüzeyi azaltma kuralları hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
> - [Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md)
> - [Saldırı yüzeyi azaltma kurallarının listesini görüntüleme](attack-surface-reduction-rules-reference.md)
> - [Saldırı yüzeyi azaltma kuralları dağıtımı 3. Adım: ASR kurallarını uygulama](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Fidye yazılımı azaltma

Yalnızca güvenilen uygulamaların uç noktalarınızdaki korumalı [klasörlere erişmesine izin veren, denetimli klasör erişimi](controlled-folders.md#what-is-controlled-folder-access) aracılığıyla fidye yazılımı azaltmaya sahip olursunuz. 

Denetimli klasör erişimini yapılandırmak için Microsoft Endpoint Manager kullanmanızı öneririz.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Microsoft Endpoint Manager portalında ASR ilkeleri" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın. 

2. **Endpoint Security'yi** ve ardından **Saldırı Yüzeyi Azaltma'yı** seçin.

3. **+ İlke Oluştur'u** seçin. 

4. **Platform** için **Windows 10 ve üzerini** seçin ve **Profil** için **Saldırı yüzeyi azaltma kuralları'yı** seçin. Ardından **Oluştur'u** seçin. 

5. **Temel Bilgiler** sekmesinde ilkeyi adlandırın ve bir açıklama ekleyin. **İleri**'yi seçin. 

6. **Yapılandırma ayarları** sekmesinde, **Saldırı Yüzeyi Azaltma Kuralları** bölümünde aşağı doğru aşağı kaydırın. **Klasör korumasını etkinleştir** açılan listesinde **Etkinleştir'i** seçin. İsteğe bağlı olarak şu diğer ayarları belirtebilirsiniz:

   - **Korunması gereken ek klasörlerin listesi'nin** yanındaki açılan menüyü seçin ve ardından korunması gereken klasörleri ekleyin.
   - **Korumalı klasörlere erişimi olan uygulamalar listesi'nin** yanındaki açılan menüyü seçin ve korumalı klasörlere erişimi olması gereken uygulamaları ekleyin.
   - **Dosyaları ve yolları saldırı yüzeyi azaltma kurallarının dışında tut'un** yanında açılan menüyü seçin ve ardından saldırı yüzeyi azaltma kurallarının dışında tutulması gereken dosyaları ve yolları ekleyin.

   Ardından **İleri'yi** seçin.

7. **Kapsam etiketleri** sekmesinde, kuruluşunuz kapsam etiketleri kullanıyorsa **+ Kapsam etiketlerini seçin'i** ve ardından kullanmak istediğiniz etiketleri seçin. Ardından **İleri'yi** seçin. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. [Dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

8. **Atamalar** sekmesinde **Tüm kullanıcıları ekle** ve **+ Tüm cihazları ekle'yi** ve ardından **İleri'yi** seçin. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

9. **Gözden Geçir + oluştur** sekmesinde ilkenizin ayarlarını gözden geçirin ve **oluştur'u** seçin. İlke, kısa süre içinde Uç Nokta için Defender'a eklenen tüm uç noktalara uygulanır.

### <a name="device-control"></a>Cihaz denetimi

Uç Nokta için Defender'ı çıkarılabilir cihazlardaki çıkarılabilir cihazları ve dosyaları engelleyecek veya izin verecek şekilde yapılandırabilirsiniz. Cihaz denetimi ayarlarınızı yapılandırmak için Microsoft Endpoint Manager kullanmanızı öneririz.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager yönetim şablonları" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın. 

2. **Cihaz** > **Yapılandırma profiller** > **Profil oluştur**’u seçin.

3. **Platform** için **Windows 10 ve üzerini** seçin ve **Profil türü** için **Şablonlar'ı** seçin. 

   **Şablon adı'nın** altında **Yönetim Şablonları'nı** ve ardından **Oluştur'u** seçin. 

4. **Temel Bilgiler** sekmesinde ilkeyi adlandırın ve bir açıklama ekleyin. **İleri**'yi seçin. 

5. **Yapılandırma ayarları** sekmesinde **Tüm Ayarlar'ı** seçin. Ardından, çıkarılabilir cihazlarla ilgili tüm ayarları görmek için arama kutusuna yazın `Removable` .

6. Açılan bölmeyi açmak için **listeden Tüm Çıkarılabilir Depolama Sınıfları: Tüm erişimi reddet** gibi bir öğe seçin. Her ayarın açılır öğesi, etkinleştirildiğinde, devre dışı bırakıldığında veya yapılandırılmadığında ne olacağını açıklar. Bir ayar seçin ve ardından **Tamam'ı** seçin. 

7. Yapılandırmak istediğiniz her ayar için 6. adımı yineleyin. Ardından **İleri'yi** seçin.

8. **Kapsam etiketleri** sekmesinde, kuruluşunuz kapsam etiketleri kullanıyorsa **+ Kapsam etiketlerini seçin'i** ve ardından kullanmak istediğiniz etiketleri seçin. Ardından **İleri'yi** seçin. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. [Dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

9. **Atamalar** sekmesinde **Tüm kullanıcıları ekle** ve **+ Tüm cihazları ekle'yi** ve ardından **İleri'yi** seçin. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

10. **Gözden Geçir + oluştur** sekmesinde ilkenizin ayarlarını gözden geçirin ve **oluştur'u** seçin. İlke, kısa süre içinde Uç Nokta için Defender'a eklenen tüm uç noktalara uygulanır.

> [!TIP]
> Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender kullanarak USB cihazlarını ve diğer çıkarılabilir medyaları denetleme](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Ağ koruması

Ağ koruması sayesinde, kuruluşunuzun İnternet'te kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içerikleri barındırabilecek tehlikeli etki alanlarına karşı korunmasına yardımcı olabilirsiniz. Ağ korumasını açmak için Microsoft Endpoint Manager kullanmanızı öneririz.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Microsoft Endpoint Manager portalında uç nokta koruma profili" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Microsoft Endpoint Manager yönetim merkezine ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) gidin ve oturum açın. 

2. **Cihaz** > **Yapılandırma profiller** > **Profil oluştur**’u seçin.

3. **Platform** için **Windows 10 ve üzerini** seçin ve **Profil türü** için **Şablonlar'ı** seçin. 

   **Şablon adı'nın** altında **Uç nokta koruması'nı** ve ardından **Oluştur'u** seçin. 

4. **Temel Bilgiler** sekmesinde ilkeyi adlandırın ve bir açıklama ekleyin. **İleri**'yi seçin. 

5. **Yapılandırma ayarları** sekmesinde **Microsoft Defender Exploit Guard'ı** ve ardından **Ağ filtreleme'yi** genişletin.

   **Ağ korumasını** **Etkinleştir** olarak ayarlayın. (İlk başta ortamınızda ağ korumasının nasıl çalışacağını görmek için alternatif olarak **Denetim'i** seçebilirsiniz.)

   Ardından **İleri'yi** seçin.

6. **Atamalar** sekmesinde **Tüm kullanıcıları ekle** ve **+ Tüm cihazları ekle'yi** ve ardından **İleri'yi** seçin. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

7. **Uygulanabilirlik Kuralları** sekmesinde bir kural ayarlayın. Yapılandırdığınız profil yalnızca belirttiğiniz birleştirilmiş ölçütleri karşılayan cihazlara uygulanır. 

   Örneğin, ilkeyi yalnızca belirli bir işletim sistemi sürümünü çalıştıran uç noktalara atamayı seçebilirsiniz.

   Ardından **İleri'yi** seçin. 

8. **Gözden Geçir + oluştur** sekmesinde ilkenizin ayarlarını gözden geçirin ve **oluştur'u** seçin. İlke, kısa süre içinde Uç Nokta için Defender'a eklenen tüm uç noktalara uygulanır.

> [!TIP]
> Ağ korumasını etkinleştirmek için Windows PowerShell veya grup ilkesi gibi diğer yöntemleri kullanabilirsiniz. Daha fazla bilgi için bkz [. Ağ korumasını açma](enable-network-protection.md).

### <a name="web-protection"></a>Web koruması

Web koruması ile kuruluşunuzun cihazlarını web tehditlerine ve istenmeyen içeriğe karşı koruyabilirsiniz. Web korumanız [web tehdit koruması](#configure-web-threat-protection) ve [web içeriği filtreleme içerir](#configure-web-content-filtering). Her iki özellik kümesini de yapılandırın. Web koruma ayarlarınızı yapılandırmak için Microsoft Endpoint Manager kullanmanızı öneririz.

#### <a name="configure-web-threat-protection"></a>Web tehdit korumasını yapılandırma

1. Microsoft Endpoint Manager yönetim merkezine ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) gidin ve oturum açın.
 
2. **Uç nokta güvenliği** > **Saldırı yüzeyi azaltma'yı** ve ardından **+ İlke oluştur'u** seçin.

3. **Windows 10 ve üzeri** gibi bir platform seçin, **Web koruma** profilini ve ardından **Oluştur'u** seçin. 

4. **Temel Bilgiler** sekmesinde, bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

5. **Yapılandırma ayarları** sekmesinde **Web Koruması'nı** genişletin, aşağıdaki tabloda ayarları belirtin ve ardından **İleri'yi** seçin. <br/><br/>

   | Ayar | Öneri |
   |:---|:---|
   | **Ağ korumasını etkinleştirme** | **Etkin** olarak ayarlayın. Kullanıcıların kötü amaçlı siteleri veya etki alanlarını ziyaret etmesini engeller. <br/><br/>Alternatif olarak, ortamınızda nasıl çalışacağını görmek için ağ korumasını **Denetim moduna** ayarlayabilirsiniz. Denetim modunda ağ koruması kullanıcıların siteleri veya etki alanlarını ziyaret etmesini engellemez, ancak algılamaları olay olarak izler. |
   | **Microsoft Edge'in eski sürümü için SmartScreen gerektir** | **Evet** olarak ayarlayın. Kullanıcıların olası kimlik avı dolandırıcılığına ve kötü amaçlı yazılımlara karşı korunmasına yardımcı olur. |
   | **Kötü amaçlı site erişimini engelleme** | **Evet** olarak ayarlayın. Kullanıcıların kötü amaçlı olabilecek sitelerle ilgili uyarıları atlamasını engeller. |
   | **Onaylanmamış dosya indirmeyi engelle** | **Evet** olarak ayarlayın. Kullanıcıların uyarıları atlamasını ve onaylanmamış dosyaları indirmesini engeller. |

6. **Kapsam etiketleri** sekmesinde, kuruluşunuz kapsam etiketleri kullanıyorsa **+ Kapsam etiketlerini seçin'i** ve ardından kullanmak istediğiniz etiketleri seçin. Ardından **İleri'yi** seçin. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. [Dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

7. **Atamalar** sekmesinde, web koruma ilkesini alacak kullanıcıları ve cihazları belirtin ve ardından **İleri'yi** seçin.

8. **Gözden Geçir + oluştur** sekmesinde ilke ayarlarınızı gözden geçirin ve **oluştur'u** seçin.

> [!TIP]
> Web tehdit koruması hakkında daha fazla bilgi edinmek için bkz. [Kuruluşunuzu web tehditlerine karşı koruma](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Web içeriği filtrelemeyi yapılandırma

1. Microsoft 365 Defender portalına ([https://security.microsoft.com/](https://security.microsoft.com/)) gidin ve oturum açın.

2. **Ayarlar** > **Uç Noktaları'nı** seçin.

3. **Kurallar'ın** altında **Web içeriği filtreleme'yi** ve ardından **+ İlke ekle'yi** seçin.

4. **İlke ekle** açılır penceresindeki **Genel** sekmesinde ilkeniz için bir ad belirtin ve **İleri'yi** seçin.

5. **Engellenen kategoriler'de**, engellemek istediğiniz bir veya daha fazla kategoriyi seçin ve ardından **İleri'yi** seçin.

6. **Kapsam** sekmesinde, bu ilkeyi almak istediğiniz cihaz gruplarını seçin ve ardından **İleri'yi** seçin.

7. **Özet** sekmesinde ilke ayarlarınızı gözden geçirin ve **kaydet'i** seçin.

> [!TIP]
> Web içeriği filtrelemeyi yapılandırma hakkında daha fazla bilgi edinmek için bkz. [Web içeriği filtreleme](web-content-filtering.md).

### <a name="network-firewall"></a>Ağ güvenlik duvarı

Ağ güvenlik duvarı, ağ güvenlik tehditleri riskini azaltmaya yardımcı olur. Güvenlik ekibiniz, kuruluşunuzun cihazlarına veya cihazlarına hangi trafiğin akabileceğine karar veren kurallar ayarlayabilir. Ağ güvenlik duvarınızı yapılandırmak için Microsoft Endpoint Manager kullanmanızı öneririz. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Microsoft Endpoint Manager portalında güvenlik duvarı ilkesi" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Temel güvenlik duvarı ayarlarını yapılandırmak için şu adımları izleyin:

1. Microsoft Endpoint Manager yönetim merkezine ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) gidin ve oturum açın.

2. **Uç nokta güvenliği** > **Güvenlik Duvarı'nı** ve ardından **+ İlke Oluştur'u** seçin.

3. **Windows 10 ve üzeri** gibi bir platform seçin, **Microsoft Defender Güvenlik Duvarı** profilini ve ardından **Oluştur'u** seçin. 

4. **Temel Bilgiler** sekmesinde, bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

5. **Microsoft Defender Güvenlik Duvarı** genişletin ve aşağı kaydırarak listenin en altına gelin.

6. Aşağıdaki ayarların her birini **Evet** olarak ayarlayın:

   - **Etki alanı ağları için Microsoft Defender Güvenlik Duvarı açma** 
   - **Özel ağlar için Microsoft Defender Güvenlik Duvarı açma**
   - **Genel ağlar için Microsoft Defender Güvenlik Duvarı açma**
   
   Etki alanı ağlarının, özel ağların ve genel ağların her birinin altındaki ayarların listesini gözden geçirin. Bunları **Yapılandırılmadı** olarak bırakabilir veya kuruluşunuzun gereksinimlerine uyacak şekilde değiştirebilirsiniz.

   Ardından **İleri'yi** seçin.

7. **Kapsam etiketleri** sekmesinde, kuruluşunuz kapsam etiketleri kullanıyorsa **+ Kapsam etiketlerini seçin'i** ve ardından kullanmak istediğiniz etiketleri seçin. Ardından **İleri'yi** seçin. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. [Dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

8. **Atamalar** sekmesinde **Tüm kullanıcıları ekle** ve **+ Tüm cihazları ekle'yi** ve ardından **İleri'yi** seçin. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

9. **Gözden Geçir + oluştur** sekmesinde ilke ayarlarınızı gözden geçirin ve **oluştur'u** seçin.

> [!TIP]
> Güvenlik duvarı ayarları ayrıntılıdır ve karmaşık görünebilir. [Windows Defender Güvenlik Duvarı yapılandırmak için en iyi yöntemler](/windows/security/threat-protection/windows-firewall/best-practices-configuring) bölümüne bakın.

### <a name="application-control"></a>Uygulama denetimi

Windows Defender Uygulama Denetimi (WDAC), yalnızca güvenilen uygulamaların ve işlemlerin çalışmasına izin vererek Windows uç noktalarınızın korunmasına yardımcı olur. Çoğu kuruluş, WDAC'nin aşamalı dağıtımını kullandı. Diğer bir ifadeyle, çoğu kuruluş WDAC'yi ilk başta tüm Windows uç noktalarına dağıtmaz. Aslında, kuruluşunuzun Windows uç noktalarının tam olarak yönetilip yönetilmediğine, hafifçe yönetilip yönetilmediğine veya "Kendi Cihazını Getir" uç noktalarına bağlı olarak, WDAC'yi tüm uç noktalara veya bazı uç noktalara dağıtabilirsiniz.

WDAC dağıtımınızı planlamaya yardımcı olmak için aşağıdaki kaynaklara bakın:

- [Windows için Uygulama Denetimi](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Uygulama Denetimi ilkesi tasarım kararlarını Windows Defender](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Farklı senaryolarda Uygulama Denetimi dağıtımını Windows Defender: cihaz türleri](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Sonraki adımlar

Kurulum ve yapılandırma işlemini tamamladığınıza göre, sonraki adımınız Uç Nokta için Defender'ı kullanmaya başlamaktır. 

- [Uç Nokta için Defender Plan 1'i kullanmaya başlama](mde-plan1-getting-started.md)
