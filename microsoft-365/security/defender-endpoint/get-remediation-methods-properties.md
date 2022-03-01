---
title: Düzeltme etkinliği yöntemleri ve özellikleri
description: API yanıtı kiracı & güvenlik açığı yönetimi düzeltme etkinlikleri için tehdit oluşturur. Tüm düzeltme etkinliklerini, yalnızca bir düzeltme etkinliğini veya seçili bir düzeltme görevi için açık cihazları hakkında bilgi isteğinde bulundurabilirsiniz.
keywords: api'ler, düzeltme, düzeltme API'si, almak, düzeltme görevleri, düzeltme yöntemleri, düzeltme özellikleri,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 124a44f6a04e4e4e77d80ac91ed4da169e2a4aae
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014047"
---
# <a name="remediation-activity-methods-and-properties"></a>Düzeltme etkinliği yöntemleri ve özellikleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

API yanıtı, [& güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md) için oluşturulmuş tehdit düzeltme etkinliklerini içerir.

## <a name="methods"></a>Yöntemler

Yöntem|Veri türü|Açıklama
:---|:---|:---
[Tüm düzeltme etkinliklerini listele](get-remediation-all-activities.md)|Araştırma koleksiyonu|Tüm düzeltme etkinlikleri hakkında bilgi verir.
[Bir düzeltme etkinliğinin açık cihazları listesi](get-remediation-exposed-devices-activities.md)|İnceleme varlığı|Belirtilen düzeltme etkinliği için belirtilen cihazlar hakkında bilgi verir.
[Kimlikle bir düzeltme etkinliği elde](get-remediation-one-activity.md)|İnceleme varlığı|Belirtilen düzeltme etkinliğiyle ilgili bilgileri verir.

Düzeltme etkinlikleri hakkında [daha fazla bilgi öğrenin](tvm-remediation.md).

## <a name="properties"></a>Özellikler

Özellik Kimliği|Veri türü|Açıklama
:---|:---|:---
Kategori|Dize|Düzeltme etkinliğinin kategorisi (Yazılım/Güvenlik yapılandırması)
completerEmail|Dize|Düzeltme etkinliği başka biri tarafından el ile tamamlandıktan sonra, bu sütunda o kişinin e-postası yer alır
completerId|Dize|Düzeltme etkinliği başka biri tarafından el ile tamamlandıktan sonra, bu sütunda o kişinin nesne kimliği yer açılar
tamamlanmaMethod|Dize|Bir düzeltme etkinliği "otomatik olarak" (tüm cihazlara yama varsa) veya "tamamlandı olarak işaretle" seçeneğini seçen bir kişi tarafından "el ile" tamamılabilir.
createdOn|DateTime|Bu düzeltme etkinliğinin oluşturulma zamanı
Açıklama|Dize|Bu düzeltme etkinliğinin açıklaması
dueOn|DateTime|Bu düzeltme etkinliği için oluşturanın ayarlanacak son tarih
fixedDevices||Düzeltilmiştir cihaz sayısı
Kimlik|Dize|Bu düzeltme etkinliğinin kimliği
adKimlik|Dize|İlgili ürün adı
Öncelik|Dize|Bu düzeltme etkinliği için oluşturana öncelik (Yüksek\Orta\Düşük)
ürünkimlik|Dize|İlgili ürün kimliği
productivityImpactRemediationType|Dize|Yalnızca kullanıcıları etkilemeyen cihazlar için birkaç yapılandırma değişikliği talep edilebilir. Bu değer, "tüm ışıklı cihazlar" veya "yalnızca kullanıcı etkisi olan cihazlar" arasındaki seçimi gösterir.
rbacGroupNames|Dize|İlgili cihaz grubu adları
recommendedProgram|Dize|Yükseltme için önerilen program
önerilenVendor|Dize|Yükseltme için önerilen satıcı
recommendedVersion|Dize|Güncelleştirme/yükseltme için önerilen sürüm
relatedComponent|Dize|Bu düzeltme etkinliğinin ilgili bileşeni (güvenlik önerisi için ilgili bileşene benzer)
requesterEmail|Dize|Oluşturucu e-posta adresi
requesterId|Dize|Oluşturan nesne kimliği
istekte bulunduran Notlar|Dize|Bu düzeltme etkinliği için oluşturan kişi tarafından eklenen notlar (ücretsiz metin)
Scid|Dize|İlgili güvenlik önerisinin SCID'si
Durum|Dize|Düzeltme etkinliği durumu (Etkin/Tamamlandı)
statusLastModifiedOn|DateTime|Durum alanı güncelleştirilen tarih
targetDevices|Long|Bu düzeltmenin uygulan uygulana uygun olduğu, açık cihaz sayısı
Başlık|Dize|Bu düzeltme etkinliğinin başlığı
Tür|Dize|Düzeltme türü
vendorId|Dize|İlgili satıcı adı

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlikle bir düzeltme etkinliği elde](get-remediation-one-activity.md)

- [Tüm düzeltme etkinliklerini listele](get-remediation-all-activities.md)

- [Bir düzeltme etkinliğinin açık cihazları listesi](get-remediation-exposed-devices-activities.md)

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)

- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
