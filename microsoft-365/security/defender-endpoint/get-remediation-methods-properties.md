---
title: Düzeltme etkinliği yöntemleri ve özellikleri
description: API yanıtı, kiracınızda oluşturulan tehdit & güvenlik açığı yönetimi düzeltme etkinliklerini içerir. Seçilen bir düzeltme görevi için tüm düzeltme etkinliklerini, yalnızca bir düzeltme etkinliğini veya kullanıma sunulan cihazlarla ilgili bilgileri isteyebilirsiniz.
keywords: api'ler, düzeltme, düzeltme api'leri, alma, düzeltme görevleri, düzeltme yöntemleri, düzeltme özellikleri,
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
ms.openlocfilehash: 14f57d6590d580e0145abc2da788f184c88a721e
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840265"
---
# <a name="remediation-activity-methods-and-properties"></a>Düzeltme etkinliği yöntemleri ve özellikleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

API yanıtı, kiracınızda oluşturulan [Tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md) düzeltme etkinliklerini içerir.

## <a name="methods"></a>Yöntemler

Yöntem|Veri türü|Açıklama
:---|:---|:---
[Tüm düzeltme etkinliklerini listele](get-remediation-all-activities.md)|Araştırma koleksiyonu|Tüm düzeltme etkinlikleri hakkındaki bilgileri döndürür.
[Bir düzeltme etkinliğine maruz kalmış cihazları listele](get-remediation-exposed-devices-activities.md)|Araştırma varlığı|Belirtilen düzeltme etkinliği için kullanıma sunulan cihazlar hakkında bilgi döndürür.
[Kimlikle bir düzeltme etkinliği al](get-remediation-one-activity.md)|Araştırma varlığı|Belirtilen düzeltme etkinliğine ilişkin bilgileri döndürür.

[Düzeltme etkinlikleri](tvm-remediation.md) hakkında daha fazla bilgi edinin.

## <a name="properties"></a>Özellikler

Özellik Kimliği|Veri türü|Açıklama
:---|:---|:---
Kategori|Dize|Düzeltme etkinliğinin kategorisi (Yazılım/Güvenlik yapılandırması)
completerEmail|Dize|Düzeltme etkinliği bir kişi tarafından el ile tamamlandıysa, bu sütun kendi e-postasını içerir
completerId|Dize|Düzeltme etkinliği birisi tarafından el ile tamamlandıysa, bu sütun nesne kimliğini içerir
completionMethod|Dize|Bir düzeltme etkinliği "otomatik olarak" (tüm cihazlara düzeltme eki uygulandıysa) veya "tamamlandı olarak işaretle" seçeneğini seçen bir kişi tarafından "el ile" tamamlanabilir.
createdOn|Datetime|Bu düzeltme etkinliğinin oluşturulduğu saat
Açıklama|Dize|Bu düzeltme etkinliğinin açıklaması
dueOn|Datetime|Bu düzeltme etkinliği için oluşturanın ayarlandığı son tarih
fixedDevices||Düzeltilmiş cihaz sayısı
Kimlik|Dize|Bu düzeltme etkinliğinin kimliği
nameId|Dize|İlgili ürün adı
Öncelik|Dize|Bu düzeltme etkinliği için oluşturucu kümesinin önceliği (Yüksek\Orta\Düşük)
Productıd|Dize|İlgili ürün kimliği
productivityImpactRemediationType|Dize|Yalnızca kullanıcıları etkilemeyen cihazlar için birkaç yapılandırma değişikliği istenebilir. Bu değer, "kullanıma sunulan tüm cihazlar" veya "yalnızca kullanıcı etkisi olmayan cihazlar" arasındaki seçimi gösterir.
rbacGroupNames|Dize|İlgili cihaz grubu adları
önerilenProgram|Dize|Yükseltme için önerilen program
önerilenVendor|Dize|Yükseltmesi önerilen satıcı
recommendedVersion|Dize|Güncelleştirme/yükseltme için önerilen sürüm
relatedComponent|Dize|Bu düzeltme etkinliğinin ilgili bileşeni (güvenlik önerisi için ilgili bileşene benzer)
requesterEmail|Dize|Oluşturucu e-posta adresi
requesterId|Dize|Oluşturucu nesne kimliği
requesterNotes|Dize|Oluşturucunun bu düzeltme etkinliği için eklediği notlar (serbest metin)
Scid|Dize|İlgili güvenlik önerisinin SCID'sini
Durum|Dize|Düzeltme etkinliği durumu (Etkin/Tamamlandı)
statusLastModifiedOn|Datetime|Durum alanının güncelleştirilildiği tarih
targetDevices|Uzun|Bu düzeltmenin uygulanabilecek kullanıma sunulan cihaz sayısı
Başlık|Dize|Bu düzeltme etkinliğinin başlığı
Tür|Dize|Düzeltme türü
Vendorıd|Dize|İlgili satıcı adı

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlikle bir düzeltme etkinliği al](get-remediation-one-activity.md)

- [Tüm düzeltme etkinliklerini listele](get-remediation-all-activities.md)

- [Bir düzeltme etkinliğine maruz kalmış cihazları listele](get-remediation-exposed-devices-activities.md)

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)

- [Kuruluşunuzdaki güvenlik açıkları](tvm-weaknesses.md)
