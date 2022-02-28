---
title: Mobil cihazlarınız için uygulama koruma Windows 10 ayarlama
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Uygulama yönetimi ilkelerini oluşturma ve düzenleme ve kullanıcılarının kişisel cihazlarında iş dosyalarını koruma Windows 10 öğrenin.
ms.openlocfilehash: 6370f2c21ce9f8de1223d5445c87abf197c0cf89
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984118"
---
# <a name="set-or-edit-application-protection-settings-for-windows-10-devices"></a>Cihazlar için uygulama koruma ayarlarını Windows 10 düzenleme

Bu makale diğer Microsoft 365 İş Ekstra.

## <a name="edit-an-app-management-policy-for-windows-10"></a>E-Windows 10 için uygulama yönetimi Windows 10

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. Sol gezintide Cihaz İlkeleri'ne  \> **seçin**.
1. Var olan bir Windows ilkesi seçin ve sonra da **Düzenle'yi seçin**.
1. Değiştirmek **istediğiniz** ayarın yanındaki Düzenle'yi seçin ve sonra Kaydet'i **seçin**.

## <a name="create-an-app-management-policy-for-windows-10"></a>Windows 10 için uygulama yönetimi ilkesi oluşturma

Kullanıcılarınızın işle ilgili görevleri gerçekleştirdikleri kişisel Windows 10 cihazları varsa, verilerinizi bu cihazlarda da koruma altına alabilirsiniz.
  
1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. Sol gezintide Cihaz İlkeleri **Ekle'yi** \>  \> seçin.
3. **İlke ekle** bölmesinde bu ilke için benzersiz bir ad girin. 
4. **İlke türü**'nün altında **Windows 10 için Uygulama Yönetimi**'ni seçin.
5. Cihaz **türü altında,** Kişisel veya **Şirkete** **Ait'i seçin**.
6. **İş dosyalarını şifrele** seçeneği otomatik olarak açılır. 
7. Kullanıcıların çalışma dosyalarını kendi bilgisayarlarına kaydetmelerini istemiyorsanız, **Kullanıcıların şirket verilerini kişisel dosyalara kopyalamasını engelle ve çalışma dosyalarını OneDrive İş'e kaydetmelerini zorla** ilkesini **Açık** olarak ayarlayın. 
9. Mobil **cihazlarda verileri Windows genişletin**. Bu aç'i Açmanizi **öneririz**.
    Veri Kurtarma Aracısı sertifikasının bulunduğu konuma göz atmadan önce bir sertifika oluşturmanız gerekir. Yönergeler için bkz [. Şifreleme Dosya Sistemi (EFS) Veri Kurtarma Aracısı (DRA)](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate) sertifikasını oluşturma ve doğrulama.
    
    Varsayılan olarak iş dosyalarınız, cihazda depolanan ve kullanıcının profili ile ilişkilendirilmiş bir gizli anahtar kullanılarak şifrelenir. Yalnızca kullanıcı dosyanın şifresini çözebilir ve dosyayı açabilir. Bununla birlikte, cihaz kaybolursa veya kullanıcı kaldırılırsa, dosya şifrelenmiş halde kalabilir. Yönetici, dosyanın şifresini çözmek için Veri Kurtarma Aracısı (DRA) sertifikasını kullanabilir.
    
    ![Browse to Data Recovery Agent certificate.](../../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. Listelenen **tüm uygulamalara yönelik dosyaların** korun olduğundan emin olmak için başka etki alanları veya SharePoint Çevrimiçi konumlar eklemek için Ek ağ ve bulut konumlarını koru'ya tıklayın. Alanlara birden çok öğe girmeniz gerekiyorsa, öğeler arasında noktalı virgül (;) kullanın.
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](../../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Next decide **Who will get these settings?** If you don't want to use the default **All Users** security group, choose **Change**, choose the security groups who will get these settings \> **Select**.
12. Son olarak, **Ekle**'yi seçerek ilkeyi kaydedin ve cihazlarınıza atayın.