---
title: Cihaz yapılandırması
description: Microsoft Yönetilen Masaüstü cihazlarına uygulanan varsayılan ilkeler hakkında bilgi edinebilirsiniz.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 19acff97a1541dcf6151b531696cf373e604371f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327861"
---
# <a name="device-configuration"></a>Cihaz yapılandırması

<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Yeni bir Microsoft Yönetilen Masaüstü cihazı ayarlanırken, yapılandırmanın Microsoft Yönetilen Masaüstü'ne göre en iyi duruma getirilmiş olduğundan emin oluruz.

Yapılandırma, ekleme işleminin bir parçası olarak ayarlanmış bir dizi varsayılan ilke içerir. Bu ilkeler, mümkün olduğunda Mobil Cihaz Yönetimi (MDM) kullanılarak teslim edilir. Daha fazla bilgi için bkz. [Mobil Cihaz Yönetimi](/windows/client-management/mdm/).

>[!NOTE]
>Çakışmaları önlemek için, bu ilkeleri değiştirme.

Cihazlar bir imza resmiyle birlikte gelir ve ilk kullanıcı Azure Active Directory oturum asınca mobil etki alanına katılır. Cihaz, IT personelinizin müdahalesi olmadan gerekli ilkeleri ve uygulamaları otomatik olarak yükleyin.

## <a name="default-policies"></a>Varsayılan ilkeler

Bu tabloda, cihaz hazırlama sırasında tüm Microsoft Yönetilen Masaüstü cihazlarına uygulanan varsayılan ilkeler vurgulanır. Microsoft Yönetilen Masaüstü İşlemleri Ekibi tarafından onaylanmayacak ve Microsoft Yönetilen Masaüstü tarafından yönetilen nesnelerde algılanan tüm değişiklikler geri döndürülecek.

| İlke | Açıklama
| ----- | ----- |
| Güvenlik temeli | [Mobil cihaz yönetimi için Microsoft](/windows/device-security/windows-security-baselines) güvenlik temeli, tüm Microsoft Yönetilen Masaüstü cihazları için yapılandırılır. Bu taban çizgisi, endüstri standardı yapılandırmadır. Microsoft Yönetilen Masaüstü cihazlarını ve uygulamaları modern çalışma alanında güvende tutmak için Microsoft güvenlik uzmanları tarafından genel kullanıma yönelik olarak yayınlandı, iyi test edildi ve incelendi. <br><br>Sürekli olarak gelişmeye devam eden güvenlik tehditlerine karşı tehditleri azaltmak için, Microsoft güvenlik temeli güncelleştirilir ve her bir özellik güncelleştirmesi ile Microsoft Windows 10 cihazlara dağıtılır.<br><br>Daha fazla bilgi için bkz[. Windows temelleri atama](/windows/security/threat-protection/windows-security-baselines).
| Microsoft Yönetilen Masaüstü önerilen güvenlik şablonu | Bu şablon, kullanıcı deneyimini en iyi duruma getirmek için güvenlik temeli üzerinde önerilen bir dizi değişikliktir. Bu değişiklikler, Güvenlik [Sıfatı'nın içinde belge belgelenmiştir](#security-addendum). İlke ilkesine yönelik güncelleştirmeler, gereken esaslara göre yapılır.  
| Dağıtımı güncelleştirme | Yazılım Windows aşamalı dağıtımı gerçekleştirmek için İş için Güncelleştirme Güncelleştirmesini kullanın. IT yöneticileri dağıtım grubu ilkelerinin ayarlarını değiştiremez. Grup tabanlı dağıtım hakkında daha fazla bilgi için bkz. [Güncelleştirmeler Microsoft Yönetilen Masaüstü'nden nasıl yönetilir](updates.md).
| Tarifeli bağlantılar | Varsayılan olarak, tarifeli bağlantılar (örneğin LTE ağları) üzerinden yapılan güncelleştirmeler kapalıdır. Ancak, her kullanıcı bu ayarı bağımsız olarak açmak için sırasıyla Güncelleştirmeler'e **ve Ayarlar Seçenekler'e giderek bu ayarı açabilirsiniz**. <br><br>Tüm kullanıcıların tarifeli bağlantılar üzerinden güncelleştirmeleri etkinleştirmesine izin vermek [için bir değişiklik](../working-with-managed-desktop/admin-support.md) isteği gönderin; böylece tüm cihazlar için bu ayar etkin olur.
| Cihaz uyumluluğu | Bu ilkeler tüm Microsoft Yönetilen Masaüstü cihazları için yapılandırılır. Bir cihaz gerekli güvenlik yapılandırmasından uzaklaşarak uyumlu değil olarak bildiriliyor.

## <a name="windows-diagnostic-data"></a>Windows verilerini toplama

 Cihazlar, bilinen bir ticari tanımlayıcı altında Microsoft'a gelişmiş tanılama verileri sağlayacak şekilde ayarlanır. Microsoft Yönetilen Masaüstü'ne bağlı olarak, IT yöneticileri bu ayarları değiştiremez.

Genel Veri Koruma Yönetmeliği (GDPR) bölgelerindeki müşteriler için kullanıcılar sağlanan tanılama verileri düzeyini düşürebilirsiniz, ancak hizmette bir azaltma olur. Örneğin, Microsoft Yönetilen Masaüstü performans ve güvenlik  ihtiyaçlarını en iyi şekilde karşılamak için ayarlar ve ilkeler üzerinde yinelerken gereken verileri toplamaz. Daha fazla bilgi için bkz[. Windows tanılama verilerini yapılandırma.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="security-addendum"></a>Güvenlik sıfatı

 Bu bölümde, Varsayılan ilkelerde listelenen standart Microsoft Yönetilen Masaüstü ilkelerine ek olarak dağıtılacak ilkeler [özetlenmiştir](#default-policies). Bu yapılandırma finansal hizmetler ve son derece düzenlemeye tabi endüstrilere göre tasarlanmıştır ve kullanıcı üretkenliğini koruyarak en yüksek güvenlik için en iyi duruma getirilmiş.

### <a name="additional-security-policies"></a>Ek güvenlik ilkeleri

 Bu ilkeler, yüksek düzeyde düzenlemeye tabi endüstrilerin güvenliğini artırmak için eklenmiştir:

| İlke | Açıklama |
| ----- | ----- |
|Güvenlik izleme | Microsoft, Uç Nokta için [Microsoft Defender'ı kullanan cihazları izlemektedir](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Bir tehdit algılanırsa, Microsoft bu durumu müşteriye bildirerek cihazı yalıtır ve sorunu uzaktan onaylar. |
 | PowerShell V2'yi devre dışı bırakma | Microsoft, PowerShell V2'yi Ağustos 2017'de kaldırmıştı.<br><br>Bu özellik tüm Microsoft Yönetilen Masaüstü cihazlarında devre dışı bırakıldı. Bu değişiklik hakkında daha fazla bilgi için bkz[. Windows PowerShell 2.0'ın Kullanımdan Deprecation'sı](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/). |
