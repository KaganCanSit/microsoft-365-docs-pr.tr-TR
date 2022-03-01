---
title: Önkoşullar &- Tehdit ve Güvenlik Açığı Yönetimi
description: Tehdit ve Güvenlik Açığı Yönetimi'i kullanmaya başlamadan önce, ilgili yapılandırmalara ve izinlere sahip olduğundan emin olun.
keywords: tehdit & güvenlik açığı yönetimi, izin önkoşulları Tehdit ve Güvenlik Açığı Yönetimi, Uç Nokta TVM İzinleri için Microsoft Defender önkoşulları ve güvenlik açığı yönetimi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 343a5fd1033a6d954c7cd62e2558a4b401f69b20
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998186"
---
# <a name="prerequisites--permissions---threat-and-vulnerability-management"></a>Önkoşullar &- Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Cihazlarınızı şu şekilde kullanın:

- Uç Nokta için Microsoft Defender'a ekli olarak alındı

- Desteklenen [işletim sistemleri ve platformları çalıştırma](tvm-supported-os.md)

- Güvenlik açığı değerlendirme algılama oranlarınızı artırmak için ağnıza şu zorunlu güncelleştirmelerin yüklenmiş ve dağıtılmış olması gerekir:

  > Sürüm | Güvenlik güncelleştirmesi KB numarası ve bağlantısı
  > :---|:---
  > Windows 10 1709 Sürümü | [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) ve [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
  > Windows 10 1803 Sürümü | [KB4493464 ve](https://support.microsoft.com/help/4493464) [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
  > Windows 10 1809 Sürümü | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
  > Windows 10 1903 Sürümü | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)

- Yeni iş Microsoft Intune [Microsoft Endpoint Configuration Manager](/mem/intune/fundamentals/what-is-intune) [tehditlerini](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) düzeltmeye yardımcı olmak için Tehdit ve Güvenlik Açığı Yönetimi. Configuration Manager kullanıyorsanız konsolunuzu en son sürüme güncelleştirin.

  > [!NOTE]
  > Intune bağlantınız etkinleştirilmişse, bir düzeltme isteği oluştururken Intune güvenlik görevi oluşturma seçeneğiniz olur. Bağlantı ayarlanmazsa bu seçenek görünmez.

- Cihaz sayfasında görüntülenen en az bir güvenlik önerisine sahip olun

- Birlikte yönetilen olarak etiketlenir veya işaretlenir

## <a name="relevant-permission-options"></a>İlgili izin seçenekleri

1. Portalda, Microsoft 365 Defender yöneticisiyle veya Genel yönetici rolüyle hesap kullanarak oturum açın.
2. Gezinti bölmesinde, Uç Noktaları **Ayarlar > Seçin ve > seçin**.

Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi için roller oluşturma ve yönetme](user-roles.md).

### <a name="view-data"></a>Verileri görüntüleme

- **Güvenlik işlemleri** - Portalda tüm güvenlik işlemleri verilerini görüntüleme
- **Tehdit güvenlik açığı yönetimi**- Portalda Tehdit ve Güvenlik Açığı Yönetimi verilerini görüntüleme

### <a name="active-remediation-actions"></a>Etkin düzeltme eylemleri

- **Güvenlik işlemleri** - Yanıt eylemleri alma, bekleyen düzeltme eylemlerini onaylama veya yok sayma, otomasyon ve göstergeler için izin verilen/engellenen listeleri yönetme
- **Tehdit ve güvenlik açığı yönetimi- Özel durum işleme** - Yeni özel durumlar oluşturma ve etkin özel durumları yönetme
- **Tehdit ve güvenlik açığı yönetimi- Düzeltme işleme** - Yeni düzeltme istekleri gönderme, bilet oluşturma ve mevcut düzeltme etkinliklerini yönetme

Daha fazla bilgi için [bkz. RBAC izin seçenekleri](user-roles.md#permission-options)

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Desteklenen işletim sistemleri ve platformlar](tvm-supported-os.md)
- [Cihaz değeri atama](tvm-assign-device-value.md)
- [Tehdit ve güvenlik açığı yönetimi panosu](tvm-dashboard-insights.md)

