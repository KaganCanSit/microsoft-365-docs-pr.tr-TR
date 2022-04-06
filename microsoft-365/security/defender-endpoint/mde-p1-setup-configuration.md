---
title: Plan 1'i Uç Nokta için Microsoft Defender ve yapılandırma
description: Uç Nokta Plan 1 için Defender'ı ayarlamayı ve yapılandırmayı öğrenin. Gereksinimleri gözden geçirmek, promosyon planlamak ve ortamınızı ayarlamak.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/14/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 741450f2573e0d750a1d3de5012f97cf16a0780d
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569102"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Plan 1'i Uç Nokta için Microsoft Defender ve yapılandırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, Uç Nokta Planı 1 için Defender'ı ayarlama ve yapılandırma açıklanmıştır. Yardım ister kendiniz yapıyor olun, dağıtım sırasında bu makaleyi kılavuz olarak kullanabilirsiniz.  

## <a name="the-setup-and-configuration-process"></a>Kurulum ve yapılandırma işlemi

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Uç Nokta için Microsoft Defender için kurulum ve dağıtım akışı Plan 1" lightbox="images/mde-p1-deploymentflow.png":::

Uç Nokta Plan 1 için Defender genel kurulum ve yapılandırma işlemi aşağıdaki gibidir: <br/><br/>


| Sayı  | Adım  | Açıklama  |
|:---------:|:---------|:---------|
| 1 | [Gereksinimleri gözden geçirme](#review-the-requirements)  | Lisans, tarayıcı, işletim sistemi ve veri merkezi gereksinimlerini listeler   |
| 2 | [Dağıtımınızı planlayın](#plan-your-deployment) | Göz önünde bulundur yapılacak çeşitli dağıtım yöntemlerini listeler ve hangi yöntemin kullanımına karar vermenizi yardım edecek daha fazla kaynağın bağlantılarını içerir  |
| 3 | [Kiracı ortamınızı ayarlama](#set-up-your-tenant-environment) | Kiracı ortamınızı ayarlama görevlerini listeler |
| 4 | [Roller ve izinler atama](#assign-roles-and-permissions) | Güvenlik ekibinin düşünmesi gereken rolleri ve izinleri listeler <br/><br/>**İpucu**: Roller ve izinler atandığı anda, güvenlik ekipleriniz güvenlik portalı üzerinden Microsoft 365 Defender başlatabilir. Daha fazla bilgi edinmek için bkz [. Başlarken](mde-plan1-getting-started.md). |
| 5 | [Uç Nokta için Defender'a Ekleme](#onboard-to-defender-for-endpoint) | Uç Nokta Planı 1 için Defender'a almak için işletim sistemine göre çeşitli yöntemleri listeler ve her yönteme ilişkin daha ayrıntılı bilgilerin bağlantılarını içerir  |
| 6 | [Yeni nesil korumayı yapılandırma](#configure-next-generation-protection) | Bu makalede, yeni nesil koruma ayarlarınızın nasıl yapılandırıldığından Microsoft Endpoint Manager  |
| 7 | [Saldırı yüzeyini azaltma yeteneklerinizi yapılandırma](#configure-your-attack-surface-reduction-capabilities)        | Yapılandırabilirsiniz saldırı yüzeyini azaltma özellikleri türlerini listeler ve daha fazla kaynağın bağlantılarını içeren yordamlar içerir  |
 
## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirme

Aşağıdaki tabloda, Uç Nokta Planı 1 için Defender'ın temel gereksinimleri listelemektedir:<br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Lisans gereksinimleri | Uç Nokta Plan 1 için Defender |
| Tarayıcı gereksinimleri | Microsoft Edge <br/> Internet Explorer sürüm 11 <br/> Google Chrome |
| İşletim sistemleri | Windows 10, sürüm 1709 veya sonrası <br/>macOS: 11.5 (Big Sur), 10.15.7 (Catalina) veya 10.14.6 (Mojave) <br/>iOS <br/>Android OS  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Birleşik Devletler |


## <a name="plan-your-deployment"></a>Dağıtımınızı planlayın

Dağıtımınızı planlarken, çeşitli farklı mimariler ve dağıtım yöntemleri arasında seçim seçebilirsiniz. Her kuruluş benzersizdir, dolayısıyla aşağıdaki tabloda listelenmiş olarak, göz önünde bulunduracak çeşitli seçenekleriniz vardır: <br/><br/>

| Yöntem | Açıklama |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Microsoft Endpoint Manager dahil) | Yerel Intune uç noktaları yönetmek için kaynak kimlik bilgilerini kullanma |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Configuration Manager](/mem/configmgr/core/understand/introduction) (Microsoft Endpoint Manager dahil) | Şirket Intune Configuration Manager bulut ortamına yayılan uç noktaları ve iş yüklerini yönetmek için kullanıcı kimlik bilgilerini kullanma |
| [Yapılandırma Yöneticisi](/mem/configmgr/core/understand/introduction) | Uç Configuration Manager için Defender'ın bulut tabanlı gücüyle şirket içi uç noktaları korumak üzere başkalarını kullanma |
| Portaldan indirilen yerel Microsoft 365 Defender betiği | Pilot çalıştırmak veya yalnızca birkaç cihaza onboard yapmak için uç noktalarda yerel betikler kullanın |

Dağıtım seçenekleriniz hakkında daha fazla bilgi edinmek için bkz. [Uç nokta dağıtımı için Defender'ı planlama](deployment-strategy.md). Aşağıdaki posteri indirin: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Dağıtım stratejisi posteri küçük resmi":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Dağıtım posterini al](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Dağıtımınızı planlama hakkında daha ayrıntılı bilgi için bkz. [Uç Nokta için Microsoft Defender planlama](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Kiracı ortamınızı ayarlama

Kiracı ortamınızı ayarlama, aşağıdaki gibi görevleri içerir:

- Lisanslarınızı doğrulama
- Kiracınızı yapılandırma
- Ara sunucu ayarlarınızı yapılandırma (yalnızca gerekli olduğu zaman)
- Algılayıcıların düzgün çalışıyor olduğundan emin olun ve uç nokta için Defender'a verileri bildirin 

Bu görevler, Uç Nokta için Defender'ın kurulum aşamasında yer almaktadır. Bkz [. Uç Nokta için Defender'ı Ayarlama](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Roller ve izinler atama

Microsoft 365 Defender portalına erişmek için, Uç Nokta için Defender ayarlarını yapılandırabilir veya algılanan tehditlere yanıt eylemleri gerçekleştirme gibi görevleri gerçekleştirebilirsiniz; uygun izinlerin atanmamış olması gerekir. Uç Nokta için Defender [görev içindeki yerleşik rolleri Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Microsoft, kullanıcılara yalnızca görevlerini gerçekleştirmeleri için gereken izin düzeyini atamayı önermektedir. İzinleri, temel izin yönetimini kullanarak veya rol tabanlı erişim denetimi (RBAC [)](rbac.md) kullanarak atabilirsiniz. 

- Temel izin yönetimiyle, genel yöneticiler ve güvenlik yöneticileri tam erişime sahip olurken, güvenlik okuyucuları salt okunur erişime sahip olur.
- RBAC ile daha fazla rol üzerinden daha ayrıntılı izinler kurabilirsiniz. Örneğin, güvenlik okuyucularınız, güvenlik işleçleri, güvenlik yöneticileriniz, uç nokta yöneticileriniz ve daha fazlasınınız olabilir.


Aşağıdaki tabloda, kuruluşudaki Uç Nokta için Defender'da dikkate alıyacak önemli roller açık almaktadır: <br/><br/>

| Rol | Açıklama |
|:---|:---|
| Genel yöneticiler (genel yöneticiler olarak da adlandırılır) <br/><br/> *En iyi yöntem olarak, genel yöneticilerin sayısını sınırlayın.* | Genel yöneticiler her türlü görevi gerçekleştirebilir. Şirketinizi genel yönetici olarak veya Microsoft 365 için Uç Nokta için Microsoft Defender Plan 1 varsayılan olarak genel yöneticidir. <br/><br/> Genel yöneticiler tüm kullanıcı portalları genelinde ayarlara erişim Microsoft 365 değiştirebilir. Örneğin: <br/>- Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Microsoft Endpoint Manager merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Güvenlik yöneticileri (güvenlik yöneticileri olarak da adlandırılır) | Güvenlik yöneticileri, güvenlik işleci görevlerinin yanı sıra aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlikle ilgili ilkeleri izleme <br/>- Güvenlik tehditlerini ve uyarılarını yönetme <br/>- Raporları görüntüleme |
| Güvenlik operatörü | Güvenlik işleçleri güvenlik okuyucusu görevlerinin yanı sıra aşağıdaki görevleri gerçekleştirebilir: <br/>- Algılanan tehditlerle ilgili bilgileri görüntüleme <br/>- Algılanan tehditleri araştırma ve yanıtlama  |
| Güvenlik gözetmeni | Güvenlik okuyucuları aşağıdaki görevleri gerçekleştirebilir: <br/>- Posta hizmetleri genelinde güvenlikle Microsoft 365 ilkeleri görüntüleme <br/>- Güvenlik tehditlerini ve uyarıları görüntüleme <br/>- Raporları görüntüleme  |


> [!TIP]
> Microsoft Hesabı'nın rolleri hakkında daha fazla Azure Active Directory için bkz. Başka kullanıcılara yönetici [ve yönetici olmayan Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Ayrıca, Uç Nokta için Defender rolleri hakkında daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Uç Nokta için Defender'a Ekleme

Kuruluş uç noktalarını eklemeye hazır olduğunda, aşağıdaki tabloda listelenen gibi çeşitli yöntemlerden birini seçebilirsiniz: <br/><br/>

|Uç Nokta İşletim Sistemi | Ekleme yöntemleri|
|---|---|
| Windows 10 | [Yerel betik (10 cihaza kadar)](configure-endpoints-script.md) <br>  [Grup İlkesi](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobil Aygıt Yöneticisi](configure-endpoints-mdm.md) <br> [Microsoft Uç Noktası Yapılandırma Yöneticisi](configure-endpoints-sccm.md) <br> [VDI betikleri](configure-endpoints-vdi.md)  |
| macOS | [Yerel betikler](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Cihaz Yönetimi](mac-install-with-other-mdm.md) |
| iOS |[Uygulamaya dayalı](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Ardından, yeni nesil koruma ve saldırı yüzeyini azaltma yeteneklerinizi yapılandırmaya devam edin.

## <a name="configure-next-generation-protection"></a>Yeni nesil korumayı yapılandırma

Aşağıdaki resimde [Microsoft Endpoint Manager](/mem) gibi, kuruluş cihazlarınızı ve güvenlik ayarlarını yönetmek için Microsoft Endpoint Manager'i kullanmanızı öneririz:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Micorosft web portalında uç Endpoint Manager ilkeleri" lightbox="../../media/mde-p1/endpoint-policies.png":::

Yeni nesil korumanızı yeni nesil korumanızı Microsoft Endpoint Manager aşağıdaki adımları izleyin:

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma.

2. Uç **nokta** **güvenliğiAntivirus'u** >  seçin ve sonra da var olan bir ilkeyi seçin. (Mevcut bir ilkeniz yoksa, yeni bir ilke oluşturun.)

3. Virüsten koruma yapılandırma ayarlarınızı ayarlayın veya değiştirin. Yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın: <br/>

   - [Ayarlar'Windows 10 Microsoft Defender Virüsten Koruma ilke için Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [iOS'ta Uç Nokta için Defender'ı Yapılandırma](ios-configure-features.md)

4. Ayarlarınızı belirtmeyi bitirdikten sonra Gözden Geçir **+ kaydet'i seçin**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Saldırı yüzeyini azaltma yeteneklerinizi yapılandırma

Saldırı yüzeyini azaltma, tüm bu saldırılara açık olan yerleri ve yöntemleri azaltmayı ifade eder. Uç Nokta Planı 1 için Defender, uç noktalarınız genelinde saldırı yüzeylerinizi azaltmanıza yardımcı olan çeşitli özellikler ve özellikler içerir. Bu özellik ve özellikler aşağıdaki tabloda listelenmiştir: <br/><br/>

| Özellik/özellik | Açıklama |
|:---|:---|
| [Saldırı yüzeyini azaltma kuralları](#attack-surface-reduction-rules) | Yazılım tabanlı riskli davranışları sınırlamak ve organizasyonlu güvende tutmanıza yardımcı olmak için saldırı yüzeyini azaltma kurallarını yapılandırın. Saldırı yüzeyini azaltma kuralları, örneğin<br/>- Yürütülebilir dosyaları ve dosyaları indirmeye veya çalıştırmaya çalışan betikleri başlatma <br/>- Obfuscated veya aksi durumda şüpheli betikleri çalıştırma <br/>- Uygulamaların çoğunlukla günlük normal çalışma sırasında başlatmayacak davranışlar gerçekleştirme <br/><br/>Bu tür yazılım davranışları bazen yasal uygulamalarda görülebilir. Öte yandan, bu davranışlar genellikle kötü amaçlı yazılım yoluyla saldırganlar tarafından kötüye kullanım nedeniyle riskli olarak kabul edilir.  |
| [Fidye yazılımı azaltma](#ransomware-mitigation) | Denetimli klasör erişimini yapılandırarak, fidye yazılımı etkiyi ayarlayın ve bu da kuruma değerli verilerini fidye yazılımı gibi kötü amaçlı uygulamalara ve tehditlere karşı korumaya yardımcı olur. | 
| [Cihaz denetimi](#device-control) | Çıkarılabilir cihazlara (USB sürücüleri gibi) izin vermek veya engellemek üzere, organizasyon için cihaz denetim ayarlarını yapılandırabilirsiniz. | 
| [Ağ koruması](#network-protection) | Kuruluşta kişilerin İnternet'te tehlikeli etki alanlarına veya kötü amaçlı içeriğe erişen uygulamalar kullanmalarını engellemek için ağ koruması ayarlayın. |
| [Web koruması](#web-protection) | Kuruluş cihazlarınızı kimlik avı sitelerinden, açıklardan yararlanmak sitelerden ve güvenilmeyen veya düşük itibarlı diğer sitelerden korumak için web tehdit koruması ayarlayın. Kendi içerik kategorilerine göre web sitelerine erişimi izlemek ve düzenlemek için web içeriği filtrelemeyi ayarlayın (Boş Zaman, Yüksek bant genişliği, Yetişkin içeriği veya Yasal sorumluluk gibi). |
| [Ağ güvenlik duvarı](#network-firewall) | Ağ güvenlik duvarınızı, hangi ağ trafiğinin kuruluş cihazlarında yer alan veya bu cihazlardan çıkışa izin verildiğini belirleyen kurallarla yapılandırabilirsiniz. |
| [Uygulama denetimi](#application-control)  | Yalnızca güvenilen uygulamaların ve işlemlerin bilgisayar cihazlarınız üzerinde çalışmasına izin vermek Windows yapılandırabilirsiniz.    |

### <a name="attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kuralları

Saldırı yüzeyini azaltma kuralları saldırı ve saldırıyı azaltma Windows. Aşağıdaki Microsoft Endpoint Manager gösterildiği gibi, Aşağıdaki adımların kullanılması önerilir:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Microsoft Endpoint Manager portalında saldırı Microsoft Endpoint Manager kuralları" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma.

2. Uç **nokta güvenliğiAttack** >  **surface azaltma + İlke** >  **oluştur'ı seçin**.

3. Platform **için**, Sonraki **Windows 10 seçin**.

4. Profil **için** Saldırı yüzeyini **azaltma kuralları'ı seçin ve** ardından Oluştur'a **tıklayın**.

5. Temel **Bilgiler sekmesinde** , ilke için bir ad ve açıklama belirtin ve sonra da Sonraki'yi **seçin**.

6. Yapılandırma ayarları **sekmesinde Saldırı** Alanı Azaltma **Kuralları'nın kapsamını genişletin**.

7. Her kural için ayarları belirtin ve ardından Sonraki'yi **seçin**. (Her kuralın yaptığı iş hakkında daha fazla bilgi için bkz [. Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md).) 

8. Kapsam **etiketleri sekmesinde** , organizasyonunız kapsam etiketleri kullanıyorsa, **+** Kapsam etiketlerini seç'i seçin ve sonra da kullanmak istediğiniz etiketleri seçin. Sonra, Sonraki'yi **seçin**. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

9. Ödevler **sekmesinde** , ilkenizin uygulanması gereken kullanıcıları ve grupları belirtin ve ardından Sonraki'yi **seçin**. (Ödevler hakkında daha fazla bilgi edinmek için bkz[. Mobil cihazda kullanıcı ve cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

10. Gözden Geçir **+ oluştur sekmesinde** ayarları gözden geçirin ve ardından Oluştur'a **tıklayın**.

> [!TIP]
> Saldırı yüzeyini azaltma kuralları hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:
> - [Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyini azaltma kurallarını kullanın](attack-surface-reduction.md)
> - [Saldırı yüzeyini azaltma kurallarının listesini görüntüleme](attack-surface-reduction-rules-reference.md)
> - [Saldırı yüzeyini azaltma kuralları dağıtımı 3. Adım: ASR kurallarını uygulama](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Fidye yazılımı azaltma

Denetimli klasör erişimi, [yalnızca güvenilen uygulamaların](controlled-folders.md#what-is-controlled-folder-access) uç noktalarınız üzerinden korumalı klasörlere erişmesi için fidye yazılımı risklerini alıyor. 

Denetimli klasör Microsoft Endpoint Manager yapılandırmak için Denetimler'i kullanmalarını öneririz.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Microsoft Endpoint Manager portalında ASR ilkeleri" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma. 

2. Uç **Nokta Güvenliği'ne** ve ardından Saldırı Yüzeyini **Azaltma'ya seçin**.

3. **+ İlke Oluştur'a seçin**. 

4. Platform **için**, Saldırı **Windows 10 sonrası ve** **Profil için Saldırı** yüzeyini azaltma **kuralları'na tıklayın**. Ardından **Oluştur'a seçin**. 

5. Temel **Bilgiler sekmesinde** , ilkeyi bir adla ayarlayın ve bir açıklama ekleyin. **İleri**'yi seçin. 

6. Yapılandırma **ayarları sekmesindeki** Saldırı **Yüzeyini Azaltma Kuralları bölümünde** ekranı aşağı doğru kaydırın. Klasör **korumasını etkinleştir açılan** listesinde Etkinleştir'i **seçin**. bu diğer ayarları isteğe bağlı olarak belirtebilirsiniz:

   - Korunması **gereken ek klasörlerin listesi'nin** yanında, açılan menüyü seçin ve korunması gereken klasörleri ekleyin.
   - Korumalı **klasörlere erişimi olan uygulamaların listesi'nin** yanında, açılan menüyü seçin ve sonra korumalı klasörlere erişimi olması gereken uygulamaları ekleyin.
   - Saldırı **yüzeyini azaltma kurallarındaki** dosyaları ve yolları dışla'nın yanında, açılan menüyü seçin ve ardından saldırı yüzeyini azaltma kuralları dışında tutulacak dosyaları ve yolları ekleyin.

   Sonra, **Sonraki'yi seçin**.

7. Kapsam **etiketleri sekmesinde** , organizasyonunız kapsam etiketleri kullanıyorsa, **+** Kapsam etiketlerini seç'i seçin ve sonra da kullanmak istediğiniz etiketleri seçin. Sonra, Sonraki'yi **seçin**. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

8. Ödevler **sekmesinde Tüm** kullanıcıları **ekle'yi ve** + Tüm cihazları **ekle'yi ve sonra** da Sonraki'yi **seçin**. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

9. Gözden Geçir **+ oluştur sekmesinde** , ilkenizin ayarlarını gözden geçirin ve sonra Oluştur'a **tıklayın**. İlke, kısa süre sonra Uç nokta için Defender'a alınan tüm uç noktalara uygulanacaktır.

### <a name="device-control"></a>Cihaz denetimi

Çıkarılabilir cihazlardaki çıkarılabilir cihaz ve dosyaları engellemek veya buna izin vermek üzere Uç Nokta için Defender'ı yapılandırabilirsiniz. Cihaz denetimi Microsoft Endpoint Manager için Microsoft Endpoint Manager'i kullanmanızı öneririz.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager şablonları oluşturma" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma. 

2. **Cihaz** > **Yapılandırma profiller** > **Profil oluştur**’u seçin.

3. Platform **için**, Windows 10 **ve sonraki bir zaman** türünü seçin ve **Profil türü için** **Şablonlar'ı seçin**. 

   Şablon **adı'nın** altında Yönetim **Şablonları'ı seçin ve** sonra da Oluştur'a **seçin**. 

4. Temel **Bilgiler sekmesinde** , ilkeyi bir adla ayarlayın ve bir açıklama ekleyin. **İleri**'yi seçin. 

5. Yapılandırma ayarları **sekmesinde Tüm** **Seçenekler'i Ayarlar**. Ardından, çıkarılabilir cihazlarla `Removable` ilgili tüm ayarları görmek için arama kutusuna yazın.

6. Listeden, Çıkarılabilir Tüm Çıkarılabilir Depolama sınıfları **:** Tüm erişimi reddet gibi bir öğe seçerek açılır bölmesini açın. Her ayarın uç uç burada, etkin olduğunda, devre dışı bırakıldığında veya yapılandırılmamış durumdayken neler olduğu açıklandı. Bir ayar seçin ve ardından Tamam'ı **seçin**. 

7. Yapılandırmak istediğiniz her ayar için 6. adımı yinelayın. Sonra, **Sonraki'yi seçin**.

8. Kapsam **etiketleri sekmesinde** , organizasyonunız kapsam etiketleri kullanıyorsa, **+** Kapsam etiketlerini seç'i seçin ve sonra da kullanmak istediğiniz etiketleri seçin. Sonra, Sonraki'yi **seçin**. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

9. Ödevler **sekmesinde Tüm** kullanıcıları **ekle'yi ve** + Tüm cihazları **ekle'yi ve sonra** da Sonraki'yi **seçin**. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

10. Gözden Geçir **+ oluştur sekmesinde** , ilkenizin ayarlarını gözden geçirin ve sonra Oluştur'a **tıklayın**. İlke, kısa süre sonra Uç nokta için Defender'a alınan tüm uç noktalara uygulanacaktır.

> [!TIP]
> Daha fazla bilgi için bkz[. USB cihazlarını ve diğer çıkarılabilir medyayı klavyeyle Uç Nokta için Microsoft Defender](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Ağ koruması

Ağ korumasıyla, kimlik avı dolandırıcılığı, açıkları kullanan yazılımlar ve İnternet'e yönelik diğer zararlı içerikleri barındıran tehlikeli etki alanlarına karşı korunmanıza yardımcı olabilir. Ağ korumasını Microsoft Endpoint Manager için Microsoft Endpoint Manager'i öneririz.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Microsoft Endpoint Manager portalında uç Microsoft Endpoint Manager profili" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma. 

2. **Cihaz** > **Yapılandırma profiller** > **Profil oluştur**’u seçin.

3. Platform **için**, Windows 10 **ve sonraki bir zaman** türünü seçin ve **Profil türü için** **Şablonlar'ı seçin**. 

   Şablon **adı'nın altında** Uç nokta **koruması'nın seçin** ve sonra da Oluştur'a **seçin**. 

4. Temel **Bilgiler sekmesinde** , ilkeyi bir adla ayarlayın ve bir açıklama ekleyin. **İleri**'yi seçin. 

5. Yapılandırma ayarları **sekmesinde,** **Seçenekler'Microsoft Defender Exploit Guard** ve ardından Ağ **filtresi'ne genişletin**.

   Ağ **korumasını Etkinleştir** olarak **ayarlayın**. (Alternatif olarak, ilk başta **ortamınıza** ağ korumasının nasıl çalışta olduğunu görmek için Denetim'i seçebilirsiniz.)

   Sonra, **Sonraki'yi seçin**.

6. Ödevler **sekmesinde Tüm** kullanıcıları **ekle'yi ve** + Tüm cihazları **ekle'yi ve sonra** da Sonraki'yi **seçin**. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

7. Uygulanabilirlik **Kuralları sekmesinde** bir kural ayarlayın. Yapılandıracakları profil yalnızca belirttiğiniz birleştirilmiş ölçütlere uyan cihazlara uygulanır. 

   Örneğin, ilkeyi yalnızca belirli bir işletim sistemi sürümünü çalıştıran uç noktalara atamayı seçebilirsiniz.

   Sonra, **Sonraki'yi seçin**. 

8. Gözden Geçir **+ oluştur sekmesinde** , ilkenizin ayarlarını gözden geçirin ve sonra Oluştur'a **tıklayın**. İlke, kısa süre sonra Uç nokta için Defender'a alınan tüm uç noktalara uygulanacaktır.

> [!TIP]
> Ağ korumasını etkinleştirmek için, kimlik bilgileri Windows PowerShell grup ilkesi başka yöntemler kullanabilirsiniz. Daha fazla bilgi edinmek için bkz [. Ağ korumasını açma](enable-network-protection.md).

### <a name="web-protection"></a>Web koruması

Web korumasıyla, kuruluş cihazlarınızı web tehditlerine ve istenmeyen içeriğe karşı koruyabilirsiniz. Web korumanız [, web tehdit koruması ve](#configure-web-threat-protection) [web içeriği filtrelemesi içerir](#configure-web-content-filtering). Her iki özellik kümesi de yapılandır. Web koruma Microsoft Endpoint Manager için Microsoft Endpoint Manager'i kullanmanızı öneririz.

#### <a name="configure-web-threat-protection"></a>Web tehdit korumasını yapılandırma

1. Yönetim merkezine Microsoft Endpoint Manager ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açma.
 
2. Uç **nokta güvenliğiAttack** >  **yüzeyini azaltma'yi seçin** ve ardından + İlke **oluştur'a basın**.

3. Web koruma profili ve daha **Windows 10 bir** platform seçin, **ardından** Oluştur'a **tıklayın**. 

4. Temel **Bilgiler sekmesinde** bir ad ve açıklama belirtin ve ardından Sonraki'yi **seçin**.

5. Yapılandırma ayarları **sekmesinde Web** **Koruması'nın kapsamını genişletin**, aşağıdaki tabloda ayarları belirtin ve ardından Sonraki'yi **seçin**. <br/><br/>

   | Ayar | Öneri |
   |:---|:---|
   | **Ağ korumasını etkinleştirme** | Etkin olarak **ayarlanır**. Kullanıcıların kötü amaçlı siteleri veya etki alanlarını ziyaretlerini engelleme. <br/><br/>Alternatif olarak, ortamınıza nasıl **çalışacaklarını görmek için** ağ korumasını Denetim moduna da kurabilirsiniz. Denetim modunda ağ koruması kullanıcıların siteleri veya etki alanlarını ziyaretsini engellemez, ancak algılamaları olay olarak izlemez. |
   | **SmartScreen gerektiren Microsoft Edge'in eski sürümü** | Evet olarak **ayarlayın**. Kullanıcıların olası kimlik avı dolandırıcılığı ve kötü amaçlı yazılımlardan korunmasına yardımcı olur. |
   | **Kötü amaçlı site erişimini engelleme** | Evet olarak **ayarlayın**. Kullanıcıların kötü amaçlı olabilecek siteler hakkında uyarıları atlamalarını engelleme. |
   | **Doğrulanmamış dosya indirmeyi engelleme** | Evet olarak **ayarlayın**. Kullanıcıların uyarıları atlayarak ve doğrulanmamış dosyaları indirmesini sağlar. |

6. Kapsam **etiketleri sekmesinde** , organizasyonunız kapsam etiketleri kullanıyorsa, **+** Kapsam etiketlerini seç'i seçin ve sonra da kullanmak istediğiniz etiketleri seçin. Sonra, Sonraki'yi **seçin**. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

7. Ödevler **sekmesinde** , web koruma ilkesi alacak kullanıcıları ve cihazları belirtin ve ardından Sonraki'yi **seçin**.

8. Gözden Geçir **+ oluştur sekmesinde** , ilke ayarlarınızı gözden geçirin ve sonra Oluştur'a **tıklayın**.

> [!TIP]
> Web tehdit koruması hakkında daha fazla bilgi edinmek için bkz [. Kurumlarınızı web tehditlerine karşı koruma](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Web içeriği filtrelemeyi yapılandırma

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/) ) ve oturum açın.

2. **Ayarlar** >  **Endpoints'i seçin**.

3. **Kurallar'ın** altında **Web içeriği filtreleme'yi seçin** ve ardından + İlke **ekle'yi seçin**.

4. İlke **ekle açılır** menüsünde, **Genel sekmesinde** ilkeniz için bir ad belirtin ve sonra da Sonraki'yi **seçin**.

5. Engellenen **kategoriler'de**, engellemek istediğiniz bir veya birden çok kategoriyi seçin ve sonra da Sonraki'yi **seçin**.

6. Kapsam **sekmesinde** , bu ilkeyi almak istediğiniz cihaz gruplarını seçin ve sonra da Sonraki'yi **seçin**.

7. Özet sekmesinde **,** ilke ayarlarınızı gözden geçirin ve ardından Kaydet'i **seçin**.

> [!TIP]
> Web içeriği filtrelemeyi yapılandırma hakkında daha fazla bilgi edinmek için bkz [. Web içeriği filtreleme](web-content-filtering.md).

### <a name="network-firewall"></a>Ağ güvenlik duvarı

Ağ güvenlik duvarı, ağ güvenliği tehditlerinin azaltılmasına yardımcı olur. Güvenlik ekipleriniz, hangi trafiğin kuruluş cihazlarına veya bu cihazlardan akışa izin verdiğini belirleyen kurallar kurabilirsiniz. Ağ güvenlik Microsoft Endpoint Manager için Microsoft Endpoint Manager'i kullanmanızı öneririz. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Microsoft Endpoint Manager portalında güvenlik Microsoft Endpoint Manager ilkesi" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Temel güvenlik duvarı ayarlarını yapılandırmak için şu adımları izleyin:

1. Yönetim merkezine Microsoft Endpoint Manager ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açma.

2. **Endpoint securityFirewall'ı** >  ve ardından + İlke **Oluştur'u seçin**.

3. Güvenlik Duvarı ve sonrası **Windows 10 bir platform seçin**, **Microsoft Defender Güvenlik Duvarı profilini seçin** ve sonra da Oluştur'u **seçin**. 

4. Temel **Bilgiler sekmesinde** bir ad ve açıklama belirtin ve ardından Sonraki'yi **seçin**.

5. **Microsoft Defender Güvenlik Duvarı'nı** genişletin ve ardından listenin en altına kadar aşağı kaydırın.

6. Aşağıdaki ayarlardan her birini Evet olarak **ayarlayın**:

   - **Etki alanı ağları için Microsoft Defender Güvenlik Duvarı'nı açma** 
   - **Özel ağlar için Microsoft Defender Güvenlik Duvarı'nı açma**
   - **Ortak ağlar için Microsoft Defender Güvenlik Duvarı'nı açma**
   
   Etki alanı ağlarının, özel ağların ve ortak ağların her biri altındaki ayarların listesini gözden geçirebilirsiniz. Bunları Yapılandırılmadı olarak **bırakarak veya** bunları kuruluşun ihtiyaçlarına uyacak şekilde değiştirebilirsiniz.

   Sonra, **Sonraki'yi seçin**.

7. Kapsam **etiketleri sekmesinde** , organizasyonunız kapsam etiketleri kullanıyorsa, **+** Kapsam etiketlerini seç'i seçin ve sonra da kullanmak istediğiniz etiketleri seçin. Sonra, Sonraki'yi **seçin**. 
   
   Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

8. Ödevler **sekmesinde Tüm** kullanıcıları **ekle'yi ve** + Tüm cihazları **ekle'yi ve sonra** da Sonraki'yi **seçin**. (Alternatif olarak belirli kullanıcı veya cihaz gruplarını belirtebilirsiniz.)

9. Gözden Geçir **+ oluştur sekmesinde** , ilke ayarlarınızı gözden geçirin ve sonra Oluştur'a **tıklayın**.

> [!TIP]
> Güvenlik duvarı ayarları ayrıntılıdır ve karmaşık görünebilir. Güvenlik [Duvarı'nı yapılandırmak için en Windows Defender yöntemleri'ne bakın](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Uygulama denetimi

Windows Defender Denetimi (WDAC), yalnızca güvenilen uygulamalara ve işlemlerin çalışmasına izin vererek Windows uç noktalarınızı korumaya yardımcı olur. Çoğu kuruluş WDAC'nin aşamalı dağıtımını kullandı. Başka bir ifadeyle, çoğu kuruluş en başta tüm mobil mobil Windows WDAC'i yaygın olarak uygulamaz. Aslında, kuruluşta kullanılan Windows uç noktalarının tümüyle yönetilip yönetilmaytiğine, hafif bir şekilde yönetilse veya "Kendi Cihazınızı Getirin" uç noktalarına bağlı olarak WDAC'yi tüm uç noktalara veya bazı uç noktalara dağıtabilirsiniz.

WDAC dağıtımınızı planlamaya yardımcı olmak için aşağıdaki kaynaklara bakın:

- [Denetimler için uygulama Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender Denetimi ilkesi tasarım kararlarını alma](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender senaryolarda Uygulama Denetimi dağıtımını kontrol edin: cihaz türleri](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Sonraki adımlar

Artık kurulum ve yapılandırma sürecini takip etmeye başladığınıza göre, bir sonraki adımınız Uç Nokta için Defender'ı kullanmaya başlamanızdır. 

- [Kullanmaya başlayın Plan 1 için Defender ile Birlikte Uygulama](mde-plan1-getting-started.md)
