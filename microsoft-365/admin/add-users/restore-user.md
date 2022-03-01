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
description: Bir kullanıcı hesabını sildikten sonra 30 gün içinde hesabı ve tüm verileri geri yükleyebilirsiniz; kullanıcı aynı hesap ile oturum yükleyebilir.
ms.openlocfilehash: fc011f9589d789a7eb2faa332a104ef670cf6590
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014041"
---
# <a name="restore-a-user"></a>Kullanıcıyı geri yükleme
   
Kullanıcı hesabını, sildikten sonra 30 gün içinde geri yüklerseniz, hesap ve tüm ilişkili veriler geri yüklenir. Kullanıcı aynı iş veya okul hesabı ile oturum açabilir. Posta kutusu tümüyle geri yüklenir. Belirli bir kullanıcı hesabının geri yüklenemez duruma gelmesine ne kadar süre kaldığını öğrenmeniz gerekiyorsa [bize ulaşın](../../business-video/get-help-support.md).
  
Birkaç ipucu:
  
- Hesaba atamak için lisansların kullanılabilir olduğundan emin olun.
    
- İşletmeniz Active Directory kullanıyorsa, kullanıcı hesabını geri yükleme yönergeleri için bkz. Active Directory'de silinen kullanıcı [hesaplarıyla ilgili Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Bir veya daha fazla kullanıcı hesabını geri yükleme

Bu adımları Microsoft 365 genel yönetici veya kullanıcı yönetimi yöneticisi siz olmak gerekir. 

1. Yönetim merkezinde Kullanıcılar Silinmiş kullanıcılar **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank"></a>

2. Silinmiş **kullanıcılar sayfasında** , geri yüklemek istediğiniz kullanıcıların adlarını seçin ve geri yükle'yi **seçin**.
    
3. Parolalarını ayarlamak için istemleri izleyin ve geri yükle'yi **seçin**.
    
4. Kullanıcı başarıyla geri yüklendiyse, E-posta **gönder ve kapat'ı seçin**. Ad çakışmasıyla veya ara sunucu adresi çakışmasıyla karşılaşırsanız, hesabınızı geri yüklemek için aşağıdaki yönergelere bakın.
    
Bir kullanıcıyı geri yüklendikten sonra, parolasının değiştirdiğini ve bu parolayı izlemiş olduğunu ona bildirmeyi sağlarsınız.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Kullanıcı adı çakışması olan bir kullanıcıyı geri yükleme

Bir kullanıcı hesabını silip aynı kullanıcı adıyla yeni bir kullanıcı hesabı oluşturup (aynı kullanıcı için veya benzer adlı başka bir kullanıcı için) daha sonra silinmiş hesabı geri yüklemeye çalıştığınızda, kullanıcı adı çakışması olur.
  
Bu sorunu gidermek için, etkin kullanıcı hesabını geri yüklediğiniz hesapla değiştirin. Alternatif olarak, aynı kullanıcı adına sahip iki hesap olmaması için, geri yüklemekte olduğunuz hesaba farklı bir kullanıcı adı atayın. Adımları aşağıda görebilirsiniz.

1. Yönetim merkezinde Kullanıcılar Silinmiş kullanıcılar **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank"></a>
  
2. Silinmiş **kullanıcılar sayfasında** , geri yüklemek istediğiniz kullanıcıların adlarını seçin ve geri yükle'yi **seçin**.
    
    > [!NOTE]
    > İki veya daha fazla kullanıcı geri yüklenemezse, geri yükleme işleminin bazı kullanıcılar için başarısız olduğu bir hata iletisiyle size bildirilir. Geri yüklenmeyen kullanıcıları görmek için günlüğe bakın ve sonra başarısız olunan hesapları tek tek geri yükleyin. 
  
3. Parolayı ayarlamak için istemleri izleyin ve Geri Yükle'yi **seçin**.
    
4. Hesabın geri yüklenmesiyle ilgili bir sorun olduğunu belirten bir ileti görüntülenir. Aşağıdakilerden birini yapın:
    
     - Geri yüklemeyi iptal edip geçerli etkin kullanıcıyı yeniden adlandırın. Daha sonra geri yüklemeyi yeniden deneyin.
    
     - VEYA kullanıcı için yeni bir birincil e-posta adresi yazın ve Geri Yükle'yi **seçin**.
    
5. Sonuçları gözden geçirin ve **Kapat**'ı seçin.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Proxy adresi çakışması olan bir kullanıcıyı geri yükleme

Ara sunucu adresi bulunan bir kullanıcı hesabını silip aynı ara sunucu adresini başka bir hesaba atayıp silinen hesabı geri yüklemeye çalıştığınızda, ara sunucu adresi çakışması oluşur. Bu sorunu çözmek için aşağıdaki adımları izleyin.
  
Bunu yapmak için[, e-Microsoft 365](about-admin-roles.md) izinlerine sahip olmak gerekir. 

1. Yönetim merkezinde Kullanıcılar Silinmiş kullanıcılar **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank"></a>

2. **Silinmiş kullanıcılar** sayfasında, geri yüklemek istediğiniz kullanıcıyı seçin ve **Geri yükle**'yi seçin. 
    
3. Geri Yükleme **sayfasında** , parolayı ayarlamak için yönergeleri izleyin ve Geri Yükle'yi **seçin**. Çakışan proxy adresleri geri yüklediğiniz kullanıcıdan otomatik olarak kaldırılır.
    
4. Sonuçları gözden geçirin ve **Kapat**'ı seçin.

## <a name="related-content"></a>İlgili içerik

[Kullanıcı silme](delete-a-user.md) (makale)\
[Yönetici rollerini atama](assign-admin-roles.md) (video)\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)
