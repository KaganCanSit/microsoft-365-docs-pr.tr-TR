---
title: Otomatik araştırma ve düzeltme görevlerinizi görüntülemek ve onaylamak için İşlem merkezine gidin
description: Otomatik araştırma hakkındaki ayrıntıları görüntülemek ve bekleyen eylemleri onaylamak için İşlem merkezini kullanın
keywords: İşlem merkezi, tehdit koruması, araştırma, uyarı, beklemede, otomatik, algılama
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 631849997fffc0e4f90a9aa9d1850646b764a52a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493497"
---
# <a name="the-action-center"></a>İşlem merkezi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

İşlem merkezi, olay ve uyarı görevleri için aşağıdakiler gibi "tek bir cam bölmesi" deneyimi sağlar:

- Bekleyen düzeltme eylemlerini onaylama.
- Zaten onaylanmış düzeltme eylemlerinin denetim günlüğünü görüntüleme.
- Tamamlanan düzeltme eylemleri gözden geçirilir.

İşlem merkezi, iş yerindeki Microsoft 365 Defender kapsamlı bir görünüm sağladığından, güvenlik operasyonları ekibiniz daha etkili ve verimli bir şekilde çalışabilir.

## <a name="the-unified-action-center"></a>Birleşik İşlem merkezi

Birleşik İşlem merkezi ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) cihazlarınız için bekleyen ve tamamlanan düzeltme eylemlerini, e-posta & işbirliği içeriğini ve kimlikleri tek bir konumda listeler.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Microsoft 365 Defender portalındaki birleşik İşlem merkezi." lightbox="../../media/m3d-action-center-unified.png":::

Örneğin: 

- Daha önce Office 365 Güvenlik & Uyumluluk Merkezi' ni ()[https://protection.office.com](https://protection.office.com) kullanıyorsanız<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Microsoft 365 Defender portalında</a> birleşik İşlem merkezini deneyin.
- Microsoft Defender Güvenlik Merkezi()[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center) içinde İşlem merkezini kullanıyorsanız<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Microsoft 365 Defender portalında</a> birleşik İşlem merkezini deneyin.
- <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">zaten Microsoft 365 Defender portalını</a> kullanıyorsanız İşlem merkezinde ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) çeşitli geliştirmeler görürsünüz.

Birleşik İşlem merkezi, Uç Nokta için Defender ve Office 365 için Defender genelinde düzeltme eylemlerini bir araya getirir. Tüm düzeltme eylemleri için ortak bir dil tanımlar ve birleşik bir araştırma deneyimi sağlar. Güvenlik operasyonları ekibinizin düzeltme eylemlerini görüntülemek ve yönetmek için "tek bir cam bölmesi" deneyimi vardır.  

Uygun izinlere ve aşağıdaki aboneliklerden birine veya daha fazlasına sahipseniz birleşik İşlem merkezini kullanabilirsiniz:

- [Uç Nokta için Defender](../defender-endpoint/microsoft-defender-endpoint.md)
- [Office 365 için Defender](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Daha fazla bilgi için bkz [. Gereksinimler](./prerequisites.md).

## <a name="using-the-action-center"></a>İşlem merkezini kullanma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın. 
2. Gezinti bölmesinde **İşlem merkezi'ni** seçin. 

İşlem merkezini ziyaret ettiğinizde iki sekme görürsünüz: **Bekleyen eylemler** ve **Geçmiş**. Aşağıdaki tabloda, her sekmede görecekleri özetlemektedir:

|Sekme  |Açıklama  |
|---------|---------|
|**Bekleyen**     | Dikkat gerektiren eylemlerin listesini görüntüler. Eylemleri birer birer onaylayabilir veya reddedebilir ya da aynı eylem türüne sahipse (Karantina dosyası gibi) birden çok eylem seçebilirsiniz. <p>**İpucu**: Otomatik araştırmalarınızın zamanında tamamlayabilmesi için bekleyen eylemleri en kısa sürede gözden geçirip onayladığınızdan (veya reddettiğinizden) emin olun.       |
|**Geçmiş**     | Aşağıdakiler gibi gerçekleştirilen eylemler için bir denetim günlüğü görevi görür: <br/>- Otomatik araştırmalar sonucunda gerçekleştirilen düzeltme eylemleri <br/>- Şüpheli veya kötü amaçlı e-posta iletileri, dosyaları veya URL'leri üzerinde gerçekleştirilen düzeltme eylemleri<br/>- Güvenlik operasyonları ekibiniz tarafından onaylanan düzeltme eylemleri <br/>- Canlı Yanıt oturumları sırasında uygulanan çalıştırılan komutlar ve düzeltme eylemleri<br/>- Virüsten korumanız tarafından gerçekleştirilen düzeltme eylemleri <p>Belirli eylemleri geri almak için bir yol sağlar (bkz. [Tamamlanan eylemleri geri alma](m365d-autoir-actions.md#undo-completed-actions)).        |

İşlem merkezinde verileri özelleştirebilir, sıralayabilir, filtreleyebilir ve dışarı aktarabilirsiniz.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="İşlem merkezinin sıralama, filtreleme ve özelleştirme özellikleri" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Öğeleri artan veya azalan düzende sıralamak için bir sütun başlığı seçin.
- Geçen gün, hafta, 30 gün veya 6 aya ait verileri görüntülemek için zaman aralığı filtresini kullanın.
- Görüntülemek istediğiniz sütunları seçin.
- Her veri sayfasına eklenecek öğe sayısını belirtin.
- Yalnızca görmek istediğiniz öğeleri görüntülemek için filtreleri kullanın.
- Sonuçları bir .csv dosyasına aktarmak için **Dışarı Aktar'ı** seçin.

## <a name="actions-tracked-in-the-action-center"></a>İşlem merkezinde izlenen eylemler

Onay bekleyen veya önceden gerçekleştirilen tüm eylemler İşlem merkezinde izlenir. Kullanılabilir eylemler şunlardır:

- Soruşturma paketini toplayın 
- Cihazı yalıtma (bu eylem geri alınabilir) 
- Offboard makine 
- Sürüm kodu yürütme 
- Karantinadan serbest bırakma 
- İstek örneği 
- Kod yürütmeyi kısıtla (bu eylem geri alınabilir) 
- Antivirüs taraması başlat 
- Durdurma ve karantinaya al 
- Ağdaki cihazları içerin

İşlem merkezi, [otomatik araştırmaların](m365d-autoir.md) sonucu olarak otomatik olarak gerçekleştirilen düzeltme eylemlerine ek olarak, güvenlik ekibinizin algılanan tehditleri ve Microsoft 365 Defender tehdit koruması özelliklerinin bir sonucu olarak gerçekleştirilen eylemleri de izler. Otomatik ve el ile düzeltme eylemleri hakkında daha fazla bilgi için bkz. [Düzeltme eylemleri](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Eylem kaynağı ayrıntılarını görüntüleme

(**YENİ!**) Geliştirilmiş İşlem merkezi artık her eylemin nereden geldiğini belirten bir **Eylem kaynağı** sütunu içerir. Aşağıdaki tabloda olası **Eylem kaynağı** değerleri açıklanmaktadır:

| Eylem kaynağı değeri | Açıklama |
|:-----|:---|
| **El ile cihaz eylemi** | Bir cihazda el ile gerçekleştirilen eylem. Örnek olarak [cihaz yalıtımı](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) veya [dosya karantinası](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files) verilebilir. |
| **El ile e-posta eylemi** | E-postada el ile gerçekleştirilen bir eylem. Örneğin, e-posta iletilerini geçici olarak silme veya [e-posta iletisini düzeltme](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Otomatik cihaz eylemi** | Dosya veya işlem gibi bir varlık üzerinde gerçekleştirilen otomatik bir eylem. Karantinaya dosya gönderme, işlemi durdurma ve kayıt defteri anahtarını kaldırma gibi otomatik eylemlere örnek olarak verilebilir. (Bkz[. Uç Nokta için Microsoft Defender düzeltme eylemleri](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **Otomatik e-posta eylemi** | E-posta iletisi, ek veya URL gibi e-posta içeriğinde gerçekleştirilen otomatik bir eylem. E-posta iletilerini geçici silme, URL'leri engelleme ve dış posta iletmeyi kapatma gibi otomatik eylemlere örnek olarak verilebilir. (Bkz[. Office 365 için Microsoft Defender düzeltme eylemleri](../office-365-security/air-remediation-actions.md).) |
| **Gelişmiş avcılık eylemi** | [Gelişmiş avcılık](./advanced-hunting-overview.md) özelliğine sahip cihazlarda veya e-postada gerçekleştirilen eylemler. |
| **Gezgin eylemi** | [Explorer](../office-365-security/threat-explorer.md) ile e-posta içeriğinde gerçekleştirilen eylemler. |
| **El ile canlı yanıt eylemi** | [Canlı yanıt](../defender-endpoint/live-response.md) içeren bir cihazda gerçekleştirilen eylemler. Örnek olarak dosya silme, işlemi durdurma ve zamanlanmış görevi kaldırma verilebilir. |
| **Canlı yanıt eylemi** | [Uç Nokta için Microsoft Defender API'leri](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) olan bir cihazda gerçekleştirilen eylemler. Bir cihazı yalıtma, virüsten koruma taraması çalıştırma ve dosya hakkında bilgi alma gibi eylemlere örnek olarak verilebilir. |

## <a name="required-permissions-for-action-center-tasks"></a>İşlem merkezi görevleri için gerekli izinler

İşlem merkezinde bekleyen eylemleri onaylama veya reddetme gibi görevleri gerçekleştirmek için, aşağıdaki tabloda listelenen izinlere sahip olmanız gerekir:

|Düzeltme eylemi |Gerekli roller ve izinler |
|--|----|
|Uç Nokta için Microsoft Defender düzeltme (cihazlar) |Azure Active Directory'de (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) veya Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) atanan **Güvenlik Yöneticisi** rolü<br/>--- veya ---<br/>Uç Nokta için Microsoft Defender'de atanan **etkin düzeltme eylemleri** rolü <br/> <br/> Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <br/>- [Yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Rol tabanlı erişim denetimi için roller oluşturma ve yönetme (Uç Nokta için Microsoft Defender)](../defender-endpoint/user-roles.md)  |
|Office 365 için Microsoft Defender düzeltme (Office içeriği ve e-posta)  |Azure AD ([https://portal.azure.com](https://portal.azure.com)) veya Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) olarak atanan **Güvenlik Yöneticisi** rolü<br/>--- ve --- <br/>Güvenlik & Uyumluluk Merkezi'nde [https://protection.office.com](https://protection.office.com) () atanan **Arama ve Temizleme** rolü <br/><br/>**ÖNEMLİ**: **Güvenlik Yöneticisi** rolü yalnızca Office 365 Güvenlik & Uyumluluk Merkezi'nde ([https://protection.office.com](https://protection.office.com) ) atanmışsa, İşlem merkezine veya Microsoft 365 Defender özelliklerine erişemezsiniz. **Azure AD veya Microsoft 365 yönetim merkezi'da Güvenlik Yöneticisi** rolü atanmış olmalıdır. <br/><br/>Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <br/>- [Yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Güvenlik & Uyumluluk Merkezi'ndeki izinler](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Azure AD'de Genel **Yönetici** rolü atanmış kullanıcılar, İşlem merkezindeki bekleyen eylemleri onaylayabilir veya reddedebilir. Ancak, en iyi uygulama olarak, kuruluşunuzun **Genel Yönetici** rolü atanmış kişi sayısını sınırlaması gerekir. İşlem merkezi izinleri için önceki tabloda listelenen **Güvenlik Yöneticisi**, **Etkin düzeltme eylemleri** **ve Arama ve Temizleme** rollerini kullanmanızı öneririz.

## <a name="next-step"></a>Sonraki adım 

- [Düzeltme eylemlerini görüntüleyin ve yönetin](m365d-autoir-actions.md)
