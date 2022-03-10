---
title: Bekletme ilkeleri ve bekletme etiketi ilkeleri sınırları
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Bekletme ilkeleri ve bekletme etiketi ilkeleri için ilke başına en fazla ilke ve öğe sayısını anlama
ms.openlocfilehash: 4cd8fc5f141f9e039a271e8534e156e4df0582e9
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419135"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Bekletme ilkeleri ve bekletme etiketi ilkeleri sınırları

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Verilerinizde kuruluşun [verilerini otomatik olarak korumak](retention.md#retention-policies-and-retention-labels) veya silmek için bekletme ilkelerini ve bekletme etiketi ilkelerini kullanırken, dikkat olması gereken bazı maksimum numaralar vardır.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Kiracı başına en fazla bekletme etiketi sayısı

Kiracı başına en fazla 1.000 bekletme etiketi destekçisi.

## <a name="maximum-number-of-policies-per-tenant"></a>Kiracı başına en fazla ilke sayısı

Tek bir kiracı en çok 10.000 ilkeye (herhangi bir yapılandırma) sahip olabilir. Bu üst sayı bekletme için farklı ilkeler ve DLP için ilkeler, bilgi engelleri, eKbulma bekletmeleri, Mahkeme bekletmeleri, Bekletmeler ve duyarlılık In-Place gibi uyumluluk ilkeleri içerir. Bununla birlikte, bu üst değer şunları hariç tutar:

- Bulut ekleri için SharePoint ve OneDrive için otomatik etiketleme ilkeleri.
- Yalnızca silme SharePoint OneDrive değil, yalnızca silmeyi veya korumayı ve sonra da silmeyi tercihen etiket ilkeleri yayımlanmıştır.
- Exchange kayıtları yönetiminden [(MRM) bekletme ilkelerini gönderme](/exchange/security-and-compliance/messaging-records-management/messaging-records-management).

Bu 10.000 ilke sınırı içinde, iş yükü başına bekletmeye yönelik ilke sayısı üst sınırı da vardır:

- Exchange (herhangi bir yapılandırma): 1.800
    - Posta kutusu başına: Performansı etkilemeden önce en fazla 25 olması önerilir; Desteklenen sınır 50'dir.
- SharePoint veya OneDrive: (otomatik olarak dahil edilen tüm siteler): 13
- SharePoint veya OneDrive (dahil veya dışarıda bırakılan belirli konumlar): 2.600

> [!NOTE]
> Exchange ve SharePoint için bu üst sayılar bekletmeye özel değildir, ancak eBulma bekletmeleri, Mahkeme bekletmeleri ve bekletmeleri içeren diğer saklama ilkesi In-Place paylaşılır.

Microsoft Teams ve Yammer için bekletme ilkeleri, verileri bekletme amacıyla depolamak amacıyla posta kutularını kullanmasa da, Exchange Online için en fazla ilke sayısı Teams ve Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Uyarlanabilir ilke kapsamları için en fazla

Bekletme ilkesine ek başka uyarlanabilir ilke [](retention.md#adaptive-or-static-policy-scopes-for-retention) kapsamlarının sayısında bir sınırlama yoktur, ancak her uyarlanabilir kapsamı tanımlayan sorgu için bazı üst sınırlar vardır:

- Öznitelik veya özellik değerleri için dize uzunluğu: 200
- Grup veya grup içindeki özniteliklerin veya özelliklerin sayısı: 10
- Grup sayısı: 10
- Gelişmiş sorguda karakter sayısı: 10.000

Grup içindeki öznitelikleri veya özellikleri gruplama desteklenmiyor. Bu, tek bir uyarlanabilir kapsam içinde desteklenen özellik veya öznitelik sayısı üst sayısının 100 olduğu anlamına gelir.

## <a name="maximum-number-of-items-per-policy"></a>İlke başına en fazla öğe sayısı

> [!IMPORTANT]
> Statik ilke kapsamlarını [uyarlanabilir ilke kapsamları yerine, yalnızca uyarlanabilir ilke kapsamları kullanıyorsanız uygulanabilir](retention.md#adaptive-or-static-policy-scopes-for-retention).

Belirli kullanıcıları Microsoft 365, belirli kullanıcı gruplarını veya belirli siteleri dahil etmek veya dışarıda tutmak için statik kapsamlar ve isteğe bağlı yapılandırma kullanıyorsanız, ilke başına dikkat gereken bazı sınırlamalar vardır. 

Statik kapsamlar için bekletme için ilke başına en fazla öğe sayısı:

- Exchange kutuları: 1.000
- Microsoft 365 Grupları: 1.000
- Teams mesajları: 1.000
- Teams sohbetleri: 1.000
- Yammer iletileri: 1000
- Yammer iletileri: 1.000
- SharePoint siteleri: 100
- OneDrive hesapları: 100

Skype Kurumsal için kapsamları belirli olmalı ve ilke başına desteklenen en fazla sayı 1.000'tir.

Bu sınırlamalar ilkeler başına bir ilkeye göre olduğundan, bu sayıların üzerinden çıkan belirli dahilleri veya hariç tutmaları kullanırsanız, aynı bekletme ayarlarına sahip ek ilkeler oluşturabilirsiniz. Bu nedenle birden çok bekletme [ilkesi kullanan bazı örnek senaryolar](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) ve çözümler için sonraki bölüme bakın.

Bununla birlikte, birden çok ilke daha yüksek yönetim yüklerine neden olur. Dahil ve dışlama içeren birden çok ilke oluşturmak ve tutmak yerine uyarlanabilir kapsamlar kullanmayı göz önünde bulundurarak.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Üst sınırı aşmamak için birden çok ilke kullanma örnekleri

Aşağıdaki örnekler statik kapsamlara yöneliktir ve bir bekletme ilkesi için yalnızca konumu belirtemezseniz ve önceki bölümde belgelenmiş en fazla öğe sayısını hesaba eklemeniz gereken bazı tasarım çözümleri sağlar.

Exchange örnek:

- **Gereksinim**: 40.000'den fazla kullanıcı posta kutusu olan bir kuruluşta, çoğu kullanıcının e-postası 7 yıl tutulsa da, tanımlanan kullanıcıların (425) alt kümesi e-postalarının yalnızca 5 yıl tutulmış olması gerekir.

- **Çözüm**: E-postayı 7 Exchange süresi olan bir e-posta için tek bir bekletme ilkesi oluşturun ve kullanıcıların alt kümesini dışlayın. Ardından, e-postanızı 5 Exchange bekletme süresi olan ve kullanıcı alt kümesini içeren ikinci bir bekletme ilkesi oluşturun. 
    
    Her iki durumda da, dahil edilen ve dışarıda bırakılan numara, tek bir ilke için belirtilen en fazla posta kutusu sayısının altında yer almaktadır ve kullanıcıların alt kümesi, ikinci ilkeden daha uzun bir bekletme süresine sahip olduğundan, ilk [](retention.md#the-principles-of-retention-or-what-takes-precedence) ilkeden açıkça dış bırakilmelidir. Kullanıcıların alt kümesi için daha uzun bir bekletme ilkesi gerekirse, onları ilk ilkenin dışında tutmanız gerekmez.
     
    Bu çözümle, herhangi biri kuruluşa yeni katılırsa, posta kutuları 7 yıl süreyle otomatik olarak ilk ilkeye dahil edilir ve desteklenen en yüksek sayı üzerinde hiçbir etkisi olmaz. Ancak, numaraları dahil etmek ve dışarıda tutmak için 5 yıllık bekletme süresi gerektiren yeni kullanıcılar vardır ve bu sınır 1.000'e ulaşılacaktır.

SharePoint örnek:

- **Gereksinim**: Kuruluşta binlerce SharePoint sitesi vardır, ancak yalnızca 2.000 site için 10 yıl bekletme süresi gerekir ve 8.000 site için 4 yıllık bir bekletme süresi gerekir.

- **Çözüm**: 100 site içeren 10 yıllık bir bekletme süresi olan SharePoint için 20 bekletme ilkesi oluşturun ve 100 siteyi içeren 4 yıllık bir bekletme süresi olan SharePoint için 80 bekletme ilkesi oluşturun.
    
    Tüm siteyi veya siteleri SharePoint gerek SharePoint, belirli siteleri belirten bekletme ilkeleri oluşturmanız gerekir. Bekletme ilkesi belirtilen 100'den fazla siteyi desteklemey olduğundan, iki bekletme süresi için birden çok ilke oluşturmanız gerekir. Bu bekletme ilkeleri, en fazla dahil edilen site sayısına sahiptir, dolayısıyla korunması gereken bir sonraki yeni site bekletme süresine bakılmaksızın yeni bir bekletme ilkesi gerektirir.

## <a name="maximum-number-of-items-for-disposition"></a>En fazla konumlandırma için öğe sayısı

İçeriğin [yok olması](disposition.md) için dikkat gereken bazı sınırlamalar vardır:

- Her bekletme etiketi için aşama başına bekleyen 1.000.000 öğe

- Öğe at edildikten sonra en fazla yedi yıl boyunca saklama kanıtı ve bu süre için bekletme etiketi başına 1.000.000 öğe sınırlaması. 
    
Kayıt olarak işaretlenmiş öğeler için bu sınırın 1.000.000'in üzerinde olan bir yok durum kanıtına ihtiyacınız varsa [Microsoft Desteği'ne başvurun](../admin/get-help-support.md).
