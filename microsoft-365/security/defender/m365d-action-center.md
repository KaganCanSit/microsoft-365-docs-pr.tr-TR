---
title: Otomatik araştırma ve düzeltme görevlerinizi görüntülemek ve onaylamak için İşlem merkezi'ne gidin.
description: İşlem Merkezi'nde bekleyen eylemlerin otomatik olarak araştırma ve onaylama ile ilgili ayrıntılarını görüntüleme
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
ms.openlocfilehash: e4ac7636b019b0e8c1d00487e95335ede4600d85
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570051"
---
# <a name="the-action-center"></a>İşlem merkezi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

İşlem merkezi, olay ve uyarı görevleri için "tek bir cam bölmesi" deneyimi sağlar:

- Bekleyen düzeltme eylemleri onaylıyor.
- Zaten onaylanmış düzeltme eylemlerinin denetim günlüğünü görüntüleme.
- Tamamlanan düzeltme eylemleri gözden geçirildi.

İşlem merkezi iş yerindeki işlerinizi Microsoft 365 Defender bir görünüm sağladığıdan, güvenlik işlemleri ekibinin daha verimli ve verimli bir şekilde çalışmasına olanak sağlar.

## <a name="the-unified-action-center"></a>Birleşik İşlem merkezi

Birleşik İşlem merkezi ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), cihazlarınız için bekleyen ve tamamlanmış düzeltme eylemlerini, e-posta & içeriğini ve kimlikleri tek bir konumda listeler.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="En son portalda birleşik Microsoft 365 Defender." lightbox="../../media/m3d-action-center-unified.png":::

Örneğin: 

- Daha önce Güvenlik ve Uyumluluk Office 365 () &[https://protection.office.com](https://protection.office.com), portalında birleşik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">İşlem merkezini Microsoft 365 Defender.</a>
- İşlem merkezini Microsoft Defender Güvenlik Merkezi ()[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center) kullanıyorsanız, Microsoft 365 Defender portalında birleşik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender deneyin</a>.
- Zaten Iş Merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalını Microsoft 365 Defender</a>, İşlem Merkezinde () çeşitli geliştirmeler olduğunu görüyorsunuz[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

Birleşik İşlem Merkezi, Uç Nokta ve Diğer Eylemler için Defender genelinde düzeltme eylemlerini Office 365 için Defender. Tüm düzeltme eylemleri için ortak bir dil tanımlar ve birleşik bir araştırma deneyimi sağlar. Güvenlik işlemleri ekibinin düzeltme eylemlerini görüntülemeye ve yönetmeye yönelik "tek bir cam" deneyimi vardır.  

Uygun izinlere ve aşağıdaki aboneliklerden bir veya birden fazlasına sahipsanız, birleşik İşlem Merkezini kullanabilirsiniz:

- [Uç Nokta için Defender](../defender-endpoint/microsoft-defender-endpoint.md)
- [Office 365 için Defender](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [Gereksinimler](./prerequisites.md).

## <a name="using-the-action-center"></a>İşlem merkezini kullanma

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender ve</a> oturum açın. 
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**. 

İşlem merkezini ziyaret edinca iki sekme görüntülenir: **Bekleyen eylemler ve** **Geçmiş**. Aşağıdaki tabloda her sekmede neler göreceğiniz özetlenmiştir:

|Sekme  |Açıklama  |
|---------|---------|
|**Beklemede**     | Dikkat gerektiren eylemlerin listesini görüntüler. Eylemleri tek tek onaylar veya reddedebilirsiniz ya da aynı türde bir eyleme (Dosyayı karantina gibi) sahip olan birden çok eylemi de kullanabilirsiniz. <p>**İpucu**: Otomatik soruşturmaların zamanında tamamlanması için bekleyen eylemleri en kısa zamanda gözden geçirmeyi ve onaylamayı (veya reddetmeyi) emin olun.       |
|**Geçmiş**     | Yapılan işlemler için denetim günlüğü olarak görev sağlar: <br/>- Otomatik soruşturmalar sonucunda  alınan düzeltme eylemleri <br/>- Şüpheli veya kötü amaçlı e-posta iletileri, dosyalar veya URL'ler üzerinde yapılan düzeltme eylemleri<br/>- Güvenlik işlemleri ekibinin onayını alan düzeltme eylemleri <br/>- Canlı Yanıt oturumları sırasında uygulanan çalıştıran ve düzeltme eylemleri olan komutlar<br/>- Virüsten korumanız tarafından  alınan düzeltme eylemleri <p>Bazı eylemleri geri almak için bir yol sağlar (bkz. [Tamamlanmış eylemleri geri alma](m365d-autoir-actions.md#undo-completed-actions)).        |

İşlem merkezinde verileri özelleştirilebilir, sıra koruma, filtreleme ve dışarı aktarabilirsiniz.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="İşlem Merkezi'nin sıralama, filtreleme ve özelleştirme özellikleri" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Öğeleri artan veya azalan düzende sıralamak için bir sütun başlığı seçin.
- Son gün, hafta, 30 gün veya 6 aya yönelik verileri görüntülemek için zaman süresi filtresini kullanın.
- Görüntülemek istediğiniz sütunları seçin.
- Her veri sayfasına kaç öğe ek gerektirmezseniz.
- Yalnızca görmek istediğiniz öğeleri görüntülemek için filtreleri kullanın.
- Sonuçları **bir .csv** dışarı aktar'ı seçin.

## <a name="actions-tracked-in-the-action-center"></a>İşlem merkezinde izlenen eylemler

İster onay bekliyor ister zaten alınmış olsun, tüm eylemler İşlem merkezinde iz alınır. Kullanılabilir eylemler şunlardır:

- Soruşturma paketini topla 
- Cihazı yalıt (bu işlem geri alın alabilir) 
- Offboard makinesi 
- Sürüm kodu yürütme 
- Karantinadan çıkar 
- İstek örneği 
- Kod yürütmeyi kısıtlama (bu eylem geri alınabilir) 
- Virüsten koruma taraması çalıştırma 
- Durdurma ve karantina 

Otomatik soruşturmalar sonucunda otomatik olarak alınan düzeltme eylemlerine ek [olarak, İşlem](m365d-autoir.md) Merkezi güvenlik ekibinin algılandırilen tehditlere yönelik olarak gerçekleştir olduğu eylemleri ve Microsoft 365 Defender'te tehdit koruması özelliklerinin bir sonucu olarak alınan eylemleri de izler. Otomatik ve el ile düzeltme eylemleri hakkında daha fazla bilgi için bkz [. Düzeltme eylemleri](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Eylem kaynağı ayrıntılarını görüntüleme

(**Yenİ!**) Geliştirilmiş İşlem merkezi artık her **eylemin nereden** geldiğini size söyleyen bir Eylem kaynağı sütunu içerir. Aşağıdaki tabloda, olası Eylem **kaynağı değerleri açık** almaktadır:

| Eylem kaynağı değeri | Açıklama |
|:-----|:---|
| **El ile cihaz eylemi** | Cihazda el ile yapılan bir eylem. Örnek olarak [cihaz yalıtlığı](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) veya dosya [karantinası örnek olarak verilmiştir](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **El ile e-posta eylemi** | E-posta üzerinde el ile yapılan bir eylem. Örneğin, e-posta iletilerini geçici olarak silme [veya e-posta iletilerini düzeltme örneği](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Otomatik cihaz eylemi** | Dosya veya işlem gibi bir varlık üzerinde  alınan otomatik bir eylem. Otomatik eylemlere örnek olarak, dosyayı karantinaya gönderme, işlemi durdurma ve kayıt defteri anahtarını kaldırma işlemleri örnek olarak verilmiştir. (Bkz[. Düzeltme eylemleri Uç Nokta için Microsoft Defender](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **Otomatik e-posta eylemi** | E-posta iletisi, ek veya URL gibi e-posta içeriği üzerinde  alınan otomatik bir eylem. Otomatik eylem örnekleri arasında e-posta iletilerini geçici olarak silme, URL'leri engelleme ve dış posta iletmeyi kapatma yer alır. (Bkz[. Düzeltme eylemleri Office 365 için Microsoft Defender](../office-365-security/air-remediation-actions.md).) |
| **Gelişmiş av eylemi** | Gelişmiş avla cihazlar veya e-posta [üzerinde alınan eylemler](./advanced-hunting-overview.md). |
| **Gezgin eylemi** | Explorer ile e-posta içeriği üzerinde [alınan eylemler](../office-365-security/threat-explorer.md). |
| **El ile canlı yanıt eylemi** | Canlı yanıta sahip bir cihazda [alınan eylemler](../defender-endpoint/live-response.md). Örnek olarak dosya silme, işlemi durdurma ve zamanlanmış görevi kaldırma örnek olarak verilmiştir. |
| **Canlı yanıt eylemi** | Çok API'leri olan [bir Uç Nokta için Microsoft Defender.](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) Eylemlere örnek olarak bir cihazı yalıtma, virüsten koruma taraması çalıştırma ve dosya hakkında bilgi alma örneklerinden bazıları verilmiştir. |

## <a name="required-permissions-for-action-center-tasks"></a>İşlem merkezi görevleri için gerekli izinler

İşlem merkezinde bekleyen eylemleri onaylama veya reddetme gibi görevleri gerçekleştirmek için, aşağıdaki tabloda listelenmiş olarak izinlerin atanmış olması gerekir:

|Düzeltme eylemi |Gerekli roller ve izinler |
|--|----|
|Uç Nokta için Microsoft Defender düzeltme (cihazlar) |**Azure Active Directory** (Azure AD) () veya güvenlik rolüne ([https://portal.azure.com](https://portal.azure.com)) atanan Microsoft 365 yönetim merkezi.[https://admin.microsoft.com](https://admin.microsoft.com)<br/>--- veya ---<br/>**Bir çalışma yerinde atanmış** etkin düzeltme Uç Nokta için Microsoft Defender <br/> <br/> Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <br/>- [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference)<br/>- [Rol tabanlı erişim denetimi için rol oluşturma ve yönetme (Uç Nokta için Microsoft Defender)](../defender-endpoint/user-roles.md)  |
|Office 365 için Microsoft Defender düzeltme (Office ve e-posta)  |**Azure** AD 'ye () veya kullanıcıya ([https://portal.azure.com](https://portal.azure.com)) atanan Microsoft 365 yönetim merkezi rolü [https://admin.microsoft.com](https://admin.microsoft.com)<br/>--- ve --- <br/>**Güvenlik Ve Uyumluluk Merkezi'nde** atanan rolü & Temizleme ([https://protection.office.com](https://protection.office.com)) <br/><br/>**ÖNEMLİ**: Yalnızca Office 365 Güvenlik  ve Uyumluluk Merkezi'ne ()[https://protection.office.com](https://protection.office.com) Güvenlik Yöneticisi rolü &, İşlem merkezi veya güvenlik özelliklerine Microsoft 365 Defender. Azure **AD'ye veya güvenlik** yöneticisi rolüne Güvenlik Yöneticisi rolünü Microsoft 365 yönetim merkezi. <br/><br/>Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <br/>- [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference)<br/>- [Güvenlik ve Uyumluluk & İzinler](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Azure AD'de **Genel Yönetici** rolüne sahip olan kullanıcılar İşlem merkezinde bekleyen tüm eylemi onaylar veya reddeder. Bununla birlikte, en iyi yöntem olarak, organizasyonda Genel Yönetici rolü atanan kişi **sayısını sınırlaması** gerekir. İşlem merkezi izinleri **için yukarıdaki** tabloda listelenen Güvenlik **Yöneticisi, Etkin** düzeltme eylemleri ve  Arama ve Temizleme rollerini kullanmanızı öneririz.

## <a name="next-step"></a>Sonraki adım 

- [Düzeltme eylemlerini görüntüleyin ve yönetin](m365d-autoir-actions.md)
