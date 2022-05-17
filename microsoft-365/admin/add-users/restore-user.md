---
title: Kullanıcıyı geri yükleme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: Kullanıcı hesabını sildikten sonraki 30 gün içinde hesabı ve tüm verileri geri yükleyebilirsiniz ve kullanıcı aynı hesapla oturum açabilir.
ms.openlocfilehash: 2f9a28e5000c1ba826b5458916f30c3e8a438253
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436217"
---
# <a name="restore-a-user-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi bir kullanıcıyı geri yükleme
   
Kullanıcı hesabını, sildikten sonra 30 gün içinde geri yüklerseniz, hesap ve tüm ilişkili veriler geri yüklenir. Kullanıcı aynı iş veya okul hesabı ile oturum açabilir. Posta kutusu tümüyle geri yüklenir. Belirli bir kullanıcı hesabının geri yüklenemez duruma gelmesine ne kadar süre kaldığını öğrenmeniz gerekiyorsa [bize ulaşın](../../business-video/get-help-support.md).
  
Birkaç ipucu:
  
- Hesaba atamak için lisansların kullanılabilir olduğundan emin olun.
    
- İşletmeniz Active Directory kullanıyorsa, kullanıcı hesabını geri yükleme yönergeleri için bkz. [Office 365'da silinen kullanıcı hesaplarının sorunlarını giderme](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Bir veya daha fazla kullanıcı hesabını geri yükleme

Bu adımları gerçekleştirmek için Microsoft 365 genel yöneticisi veya kullanıcı yönetimi yöneticisi olmanız gerekir. 

1. Yönetim merkezinde **Kullanıcılar** <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">Silinmiş kullanıcılar</a> \> sayfasına gidin.

2. **Silinmiş kullanıcılar** sayfasında, geri yüklemek istediğiniz kullanıcıların adlarını seçin ve ardından **Geri Yükle'yi** seçin.
    
3. Parolalarını ayarlamak için istemleri izleyin ve ardından **Geri Yükle'yi** seçin.
    
4. Kullanıcı başarıyla geri yüklendiyse **E-posta gönder ve kapat'ı** seçin. Ad çakışmasıyla veya ara sunucu adresi çakışmasıyla karşılaşırsanız, hesabınızı geri yüklemek için aşağıdaki yönergelere bakın.
    
Bir kullanıcıyı geri yükledikten sonra, parolasının değiştiğini bildirdiğinizden ve bu kullanıcıyı takip ettiğinizden emin olun.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Kullanıcı adı çakışması olan bir kullanıcıyı geri yükleme

Bir kullanıcı hesabını silip aynı kullanıcı adıyla yeni bir kullanıcı hesabı oluşturup (aynı kullanıcı için veya benzer adlı başka bir kullanıcı için) daha sonra silinmiş hesabı geri yüklemeye çalıştığınızda, kullanıcı adı çakışması olur.
  
Bu sorunu gidermek için, etkin kullanıcı hesabını geri yüklediğiniz hesapla değiştirin. Alternatif olarak, aynı kullanıcı adına sahip iki hesap olmaması için, geri yüklemekte olduğunuz hesaba farklı bir kullanıcı adı atayın. Adımları aşağıda görebilirsiniz.

1. Yönetim merkezinde **Kullanıcılar** <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">Silinmiş kullanıcılar</a> \> sayfasına gidin.
  
2. **Silinmiş kullanıcılar** sayfasında, geri yüklemek istediğiniz kullanıcıların adlarını seçin ve ardından **Geri Yükle'yi** seçin.
    
    > [!NOTE]
    > İki veya daha fazla kullanıcı geri yüklenemezse, geri yükleme işleminin bazı kullanıcılar için başarısız olduğu bir hata iletisiyle size bildirilir. Geri yüklenmeyen kullanıcıları görmek için günlüğe bakın ve sonra başarısız olunan hesapları tek tek geri yükleyin. 
  
3. Parolayı ayarlamak için istemleri izleyin ve **Geri Yükle'yi** seçin.
    
4. Hesabın geri yüklenmesiyle ilgili bir sorun olduğunu belirten bir ileti görüntülenir. Aşağıdakilerden birini yapın:
    
     - Geri yüklemeyi iptal edip geçerli etkin kullanıcıyı yeniden adlandırın. Daha sonra geri yüklemeyi yeniden deneyin.
    
     - VEYA, kullanıcı için yeni bir birincil e-posta adresi yazın ve **Geri Yükle'yi** seçin.
    
5. Sonuçları gözden geçirin ve **Kapat**'ı seçin.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Proxy adresi çakışması olan bir kullanıcıyı geri yükleme

Ara sunucu adresi bulunan bir kullanıcı hesabını silip aynı ara sunucu adresini başka bir hesaba atayıp silinen hesabı geri yüklemeye çalıştığınızda, ara sunucu adresi çakışması oluşur. Bu sorunu çözmek için aşağıdaki adımları izleyin.
  
Bunu yapmak için Microsoft 365 yönetici [izinlerine](about-admin-roles.md) sahip olmanız gerekir. 

1. Yönetim merkezinde **Kullanıcılar** <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">Silinmiş kullanıcılar</a> \> sayfasına gidin.

2. **Silinmiş kullanıcılar** sayfasında, geri yüklemek istediğiniz kullanıcıyı seçin ve **Geri yükle**'yi seçin. 
    
3. **Geri Yükle** sayfasında, parolayı ayarlamak için yönergeleri izleyin ve **Geri Yükle'yi** seçin. Çakışan proxy adresleri geri yüklediğiniz kullanıcıdan otomatik olarak kaldırılır.
    
4. Sonuçları gözden geçirin ve **Kapat**'ı seçin.

## <a name="related-content"></a>İlgili içerik

[Kullanıcı silme](delete-a-user.md) (makale)\
[Yönetici rolleri atama](assign-admin-roles.md) (video)\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)
