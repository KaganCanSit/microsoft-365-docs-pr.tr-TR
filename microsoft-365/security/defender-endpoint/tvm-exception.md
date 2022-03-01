---
title: Güvenlik önerileri için özel durumlar oluşturma ve görüntüleme - Tehdit ve Güvenlik Açığı Yönetimi
description: Çalışma sayfalarında güvenlik önerileri için özel durumlar oluşturun Tehdit ve Güvenlik Açığı Yönetimi.
keywords: Uç nokta tvm düzeltmesi için Microsoft Defender, Uç nokta tvm için Microsoft Defender, Tehdit ve Güvenlik Açığı Yönetimi, tehdit & güvenlik açığı yönetimi, tehdit & güvenlik açığı yönetimi düzeltme, tvm düzeltme intune, tvm düzeltme sccm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a3986d44027824f2ba9ca508567d518cce270450
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008093"
---
# <a name="create-and-view-exceptions-for-security-recommendations---threat-and-vulnerability-management"></a>Güvenlik önerileri için özel durumlar oluşturma ve görüntüleme - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Bir öneri şu anda uygun olmadığınız bir düzeltme isteğine alternatif olarak, öneriler için özel durumlar oluşturabilirsiniz. Kuruluşta cihaz grupları varsa, özel durumu belirli cihaz grupları için kapsamına bakabilirsiniz. Özel durumlar, seçili cihaz grupları için veya geçmiş ve mevcut tüm cihaz grupları için oluşturulabilir.

Öneri için bir özel durum oluşturulduğunda, öneri özel durum süresinin sonuna kadar etkin olmaz. Öneri durumu Tam özel durum veya **Kısmi özel** **durum (cihaz** grubuna göre) olarak değişir.

## <a name="permissions"></a>İzinler

Yalnızca "özel durumları işleme" izni olan kullanıcılar özel durumları yönetebilir (oluşturma veya iptal etme de dahil). [RBAC rolleri hakkında daha fazla bilgi edinmek için](user-roles.md):

![Özel durum işleme izni görünümü.](images/tvm-exception-permissions.png)

## <a name="create-an-exception"></a>Özel durum oluşturma

Özel durum oluşturmak istediğiniz güvenlik önerilerini seçin ve özel durum seçenekleri'ne **tıklayın ve** formu doldurun.

!["Özel durum seçenekleri" düğmesinin bir güvenlik önerisi uç kutusunda konum olduğunu gösterme.](images/tvm-exception-options.png)

### <a name="exception-by-device-group"></a>Cihaz grubuna göre özel durum

Bu özel durumu tüm geçerli cihaz gruplarına uygulayabilir veya belirli cihaz gruplarını seçebilirsiniz. Bu özel durum, gelecekteki cihaz gruplarına dahil değildir. Özel durumu zaten olan cihaz grupları listede görüntülenmez. Yalnızca belirli cihaz gruplarını seçmeniz halinde öneri durumu "etkin" olan "kısmi özel durum" durumuna değiştirir. Tüm cihaz gruplarını seçmeniz halinde durum , "tam özel durum" olarak değişir.

![Cihaz grubu açılan liste gösteriliyor.](images/tvm-exception-device-group-500.png)

#### <a name="filtered-views"></a>Filtrelenmiş görünümler

Bu sayfaların herhangi birsinde cihaz grubuna göre filtre Tehdit ve Güvenlik Açığı Yönetimi, seçenek olarak yalnızca filtrelenmiş cihaz gruplarınız görünür.

Bu, herhangi bir sayfadaki cihaz grubuna göre filtre Tehdit ve Güvenlik Açığı Yönetimi:

![Seçili cihaz grupları filtresini gösterme.](images/tvm-selected-device-groups.png)

Filtrelenmiş cihaz gruplarında özel durum görünümü:

![Filtrelenmiş cihaz grubu açılan liste gösteriliyor.](images/tvm-exception-device-filter500.png)

#### <a name="large-number-of-device-groups"></a>Çok fazla sayıda cihaz grubu

Kuruluşta 20'den fazla cihaz grubu varsa **, filtrelenmiş** cihaz grubu seçeneğinin yanındaki Düzenle'yi seçin.

![Çok fazla sayıda grubun nasıl düzenlenemez?](images/tvm-exception-edit-groups.png)

Dahil etmek istediğiniz cihaz gruplarını arayabilirsiniz ve bu grupları seçebilirsiniz. Ara'nın altındaki onay işareti simgesini seçerek hepsini işaretleyin/işaretini kaldırın.

![Büyük cihaz grubu uçarak çıkış gösteriliyor.](images/tvm-exception-device-group-flyout-400.png)

### <a name="global-exceptions"></a>Genel özel durumlar

Genel yönetici izinlerine sahipseniz, genel bir özel durum oluşturabilir ve iptal edebilirsiniz. Bu, **geçerli** ve gelecekteki tüm cihaz gruplarını etkiler ve yalnızca benzer izinlere sahip bir kullanıcı bunu değiştirebilir. Öneri durumu, "etkin" olan "tam özel durum" durumuna değiştirir.

![Genel özel durum seçeneğini gösterme.](images/tvm-exception-global.png)

Unutmayın gereken bazı şeyler:

- Öneri genel özel durum altında olursa, cihaz grupları için yeni oluşturulan özel durumlar, genel özel durum sona erene veya iptal edilene kadar askıya alınır. Bu noktadan sonra, yeni cihaz grubu özel durumları kullanım süresi dolana kadar geçerli olur.
- Bir önerinin belirli cihaz grupları için özel durumları zaten varsa ve bir genel özel durum oluşturulursa, cihaz grubu özel durumu süresi dolana kadar askıya alınır veya genel özel durum süresi sona ermeden önce iptal edilir.

### <a name="justification"></a>Yaslama

Söz konusu güvenlik önerisini düzeltme yerine, dosyalamanız gereken özel durum için gerekçelendirmenizi seçin. Gerekçe bağlamını doldurun ve özel durum süresini ayarlayın.

Aşağıdaki listede, özel durum seçeneklerinin ardındaki gerekçeler ayrıntılarıyla ve almaktadır:

- **Üçüncü taraf denetimi** - Üçüncü taraf bir ürün veya yazılım zaten bu öneriye yöneliktir - Bu gerekçelendirme türünü seçmek, risk azaltmanız nedeniyle pozlama puanınızı düşürecektir ve güvenli puanınızı artıracaktır
- **Alternatif azaltma** - Zaten bu öneriye adres olan bir iç araçtır - Bu gerekçelendirme türünü seçmek, pozlama puanınızı düşürecektir ve güvenliğiniz artıracaktır çünkü risk azaltıldı
- **Risk kabul edildi** - Düşük risklere neden olur ve/veya öneriyi uygulamak çok pahalıdır
- **Planlı düzeltme (yetkisiz kullanım)** - Zaten planlandı ancak yürütme veya yetkilendirmeyi bekliyor

## <a name="view-all-exceptions"></a>Tüm özel durumları görüntüleme

Düzeltme sayfasında **Özel** Durumlar **sekmesine** gidin. Gerekçelendirmeye, türe ve duruma göre filtre uygulama.

 Daha fazla ayrıntıya sahip bir açılır sayfa açmak için bir özel durum seçin. Cihazlar grubu başına özel durumlar, özel durum olarak dışarı aktarabilirsiniz tüm cihaz grubunun bir listesini içerir. Ayrıca ilgili öneriyi  bakarak veya özel durumu iptal edebilirsiniz.

![Düzeltme sayfasında "Özel Durumlar" sekmesini gösterme.](images/tvm-exception-view.png)

## <a name="how-to-cancel-an-exception"></a>Özel durumu iptal etme

Bir özel durumu iptal etmek için **, Düzeltme sayfasında** Özel Durumlar **sekmesine** gidin. Özel durumu seçin.

Tüm cihaz grupları için veya genel bir özel durum için özel durumu iptal etmek için Tüm cihaz **grupları için özel durumu iptal et düğmesini** seçin. Yalnızca izinlerine sahip olduğu cihaz grupları için özel durumları iptal edebilirsiniz.

![İptal düğmesi.](images/tvm-exception-cancel.png)

### <a name="cancel-the-exception-for-a-specific-device-group"></a>Belirli bir cihaz grubu için özel durumu iptal etme

Özel durumu iptal etmek için belirli cihaz grubunu seçin. Cihaz grubu için bir uç uçarak çıkış görüntülenir ve Özel durumu iptal **et'i seçin**.

![Belirli bir cihaz grubu seçmeyi gösterir.](images/tvm-exception-device-group-hover.png)

## <a name="view-impact-after-exceptions-are-applied"></a>Özel durumlar uygulandıktan sonra etkisini görüntüleme

Güvenlik Ayarları Öneriler, Sütunları özelleştir'i seçin  ve Açık cihazlar (özel durumlar dışından sonra) ve Etki (özel durumlardan sonra **)** **kutularını işaretleyin**.

![Sütunları özelleştirme seçeneklerini gösterir.](images/tvm-after-exceptions.png)

Açık olan cihazlar (özel durumlar dışından sonra) sütunu, özel durumlar uygulandıktan sonra da güvenlik açıklarına açık kalan cihazları gösterir. Saldırıya maruz kalmayı etkileyen özel durum gerekçeleri 'üçüncü taraf denetimi' ve 'alternatif risk azaltma'dır. Diğer gerekçeler cihazın maruz kalma süresini azaltmaz ve yine de açığa çıkarılacağı düşünülebilir.

Etki (özel durumlar dışından sonra), özel durumlar uygulandıktan sonra puanın etkilenme puanına veya güvenli puana kalan etkiyi gösterir. Puanları etkileyen özel durumlar 'üçüncü taraf denetimi' ve 'alternatif azaltma'dır. Diğer gerekçeler cihazın maruz kalma süresini azaltmaz, dolayısıyla pozlama puanı ve güvenlik puanı değişmez.

![Tablodaki sütunları gösterme.](images/tvm-after-exceptions-table.png)

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik açıklarını düzeltme](tvm-remediation.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Pozlama puanı](tvm-exposure-score.md)
- [Cihazlar için Microsoft Güvenli Puan](tvm-microsoft-secure-score-devices.md)
