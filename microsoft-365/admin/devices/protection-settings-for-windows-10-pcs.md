---
title: Bilgisayarlarında cihaz koruma ayarlarını düzenleme Windows 10 oluşturma
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: Mobil cihazların güvenliğini sağlamak Microsoft 365 için Microsoft 365 ayarları Windows 10 öğrenin.
ms.openlocfilehash: 4019fb5d76824dc33bb5947d1bd3b25072b39bbd
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007226"
---
# <a name="edit-or-create-device-protection-settings-for-windows-10-pcs"></a>Bilgisayarlarında cihaz koruma ayarlarını düzenleme Windows 10 oluşturma

Bu makale diğer Microsoft 365 İş Ekstra.

Kurulum sayfasında varsayılan güvenlik Windows ayarlarını değiştirdikten sonra, tüm kullanıcılara veya bir dizi kullanıcıya uygulanacak yeni ayarları ebilirsiniz. Ayrıca, oluşturduktan herhangi birini düzenleyebilirsiniz.

## <a name="watch-create-protection-settings-for-windows-10-devices"></a>İzle: Mobil cihazlar için Windows 10 ayarları oluşturma

Microsoft 365 İş Ekstra ile güvenli Windows 10 ilgili videoyu Microsoft 365 İş Ekstra:
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. Sol gezintide Cihaz İlkeleri **Ekle'yi** \>  \> seçin.
3. **İlke ekle** bölmesinde bu ilke için benzersiz bir ad girin. 
4. **İlke türü**'nün altında **Windows 10 Cihaz Yapılandırması**'nı seçin.
5. Expand **Secure Windows 10 Devices** \> configure the settings how you would like. Daha fazla bilgi için bkz [. Kullanılabilir ayarlar](#available-settings). 
    
    Varsayılan ayarlara dönmek için istediğiniz zaman **Varsayılan ayarlara sıfırla** bağlantısını kullanabilirsiniz. 
    
    ![Cihaz yapılandırmasının seçili Windows 10 ilke ekle bölmesi.](../../media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. Next decide **Who will get these settings?** If you don't want to use the default **All users** security group, Choose **Change**, search for the security group who will get these settings \> **Select**.
7. Son olarak, **Bitti**'yi seçerek ilkeyi kaydedin ve cihazlarınıza atayın. 

## <a name="edit-windows-10-protection-settings"></a>Koruma Windows 10 ayarlarını düzenleme
 
1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. Sol gezintide Cihaz İlkeleri'ne  \> **seçin**.
1. Var olan bir Windows ilkesi seçin ve sonra da **Düzenle'yi seçin**.
1. Değiştirmek **istediğiniz** ayarın yanındaki Düzenle'yi seçin ve sonra Kaydet'i **seçin**.

## <a name="available-settings"></a>Kullanılabilir ayarlar

Varsayılan olarak tüm ayarlar **Açık** durumdadır. Aşağıdaki ayarlar kullanılabilir.
  
Daha fazla bilgi için bkz[. Koruma özellikleri nasıl Microsoft 365 Premium Intune ayarlarıyla eşler](map-protection-features-to-intune-settings.md). 


|Ayar  <br/> |Açıklama  <br/> |
|:-----|:-----|
|Windows Defender Virüsten Koruma kullanarak bilgisayarların virüslere ve diğer tehditlere karşı korunmasına yardımcı ol  <br/> |Bilgisayarları internete bağlı olmanın getirdiği tehlikelerden korumak için Windows Defender Virüsten Koruma programının açık olması gerekir.  <br/> |
|Bilgisayarları Microsoft Edge'de web tabanlı tehditlere karşı korumaya yardımcı ol  <br/> |Edge'de, kullanıcıları kötü amaçlı sitelerden ve indirmelerden korumaya yardımcı olan ayarları açar.  <br/> |
|Cihazların saldırı alanını azaltan kuralları kullan  <br/> |Saldırı alanı azaltma özelliği açık olarak ayarlandığında zararlı yazılımlar tarafından cihazlara bulaşmak için tipik olarak kullanılan eylemleri ve uygulamaları engeller. Bu ayar yalnızca Windows Defender Virüsten Koruma yazılımı Açık olarak ayarlandığında kullanılabilir. Daha fazla bilgi edinmek için [Saldırı alanlarını azaltma](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) bölümüne bakın.  <br/> |
|Klasörleri fidye yazılımı gibi tehditlerden koruma  <br/> |Bu ayar, şirket verilerini fidye yazılımı gibi şüpheli veya zararlı uygulamalar tarafından gerçekleştirilen değişikliklere karşı korumak için denetimli klasör erişimini kullanır. Bu türdeki uygulamaların korumalı klasörlerde değişiklik yapması engellenir. Bu ayar yalnızca Windows Defender Virüsten Koruma yazılımı Açık olarak ayarlandığında kullanılabilir. Daha [fazla bilgi edinmek için bkz. Denetimli klasör erişimiyle](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA) klasörleri koruma.  <br/> |
|İnternetteki olası zararlı içeriklerin ağa erişimini engelle  <br/> |Kimlik avı dolandırıcılığı, açıkları kullanan yazılımlar veya diğer zararlı içerikleri barındırabilecek, saygınlığı düşük İnternet konumlarına yönelik giden kullanıcı bağlantılarını engellemek için bu ayarı kullanın. Bu ayarın kullanılabilir durumda Windows Defender Virüsten Koruma olarak **ayarlanmışsa kullanılabilir**. Daha fazla bilgi için bkz [. Ağın koruma](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus).  <br/> |
|BitLocker ile PC'lerdeki dosyaların ve klasörlerin yetkisiz erişime karşı korunmasına yardımcı ol  <br/> |BitLocker bilgisayar sabit sürücülerini şifreleyerek verileri korur ve bilgisayar kaybolduğunda veya çalındığında verilerin açığa çıkma durumuna karşı koruma sağlar. Daha fazla bilgi için bkz. [Bitlocker SSS](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Kullanıcıların Microsoft Store'ndan uygulama indirmesine izin ver  <br/> |Kullanıcıların Microsoft Store'ndan uygulama indirmesine ve yüklemesine izin verir. Uygulamalar, oyunlardan üretkenlik araçlarına kadar her şeyi içerebilir, dolayısıyla bu ayar **Açık** durumdadır ancak ek güvenlik için kapatabilirsiniz.  <br/> |
|Kullanıcıların Cortana'ya erişmesine izin ver  <br/> |Cortana çok yararlı olabilir! Cortana için ayarları açmak veya kapatmak, yol tarifleri vermek ve randevular için zamanında zamanında hazır olduğundan emin olmak için bu ayarı varsayılan olarak **Açık** durumda tutabilirsiniz.  <br/> |
|Kullanıcıların Microsoft'tan Windows ipucu ve reklam almasına izin ver  <br/> |Windows ipuçları kullanışlı olabilir ve yeni özellikler kullanıma sunulduğunda kullanıcıların yönlendirilmesine yardım edebilir.  <br/> |
|Windows 10 cihazları otomatik olarak güncelleştir  <br/> |Windows 10 cihazların son güncelleştirmeleri otomatik olarak aldığından emin olur.  <br/> |
|Cihaz şu kadar süre boşta kaldığında ekranı kapat  <br/> |Kullanıcı cihaz başında olmadığında şirket verilerinin korunmasını sağlar. Kullanıcı bir kafe gibi herkese açık bir konumda çalışıyorken kısa süreliğine uzaklaşabilir veya başka bir şeyle ilgilenebilir ve bu sırada diğer kişiler cihazdaki bilgilere bakabilir. Bu ayar sayesinde, ekran kapanmadan önce kullanıcının ne kadar süre boşta olabileceğini denetleyebilirsiniz.  <br/> |