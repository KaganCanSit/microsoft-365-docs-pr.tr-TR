---
title: Microsoft 365 Multi-Geo kiracı yapılandırması
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Bu makalede, microsoft 365 Multi-Geo için uydu konumları eklemeyi ve kiracınızı yapılandırmayı öğrenin.
ms.openlocfilehash: 2a82872e7c917421c0eb418cf0582eb33d2a53c9
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941206"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 Multi-Geo kiracı yapılandırması

Kiracınızı Microsoft 365 Multi-Geo için yapılandırmadan önce [Microsoft 365 Multi-Geo planı](plan-for-multi-geo.md) makalesini okuduğunuzdan emin olun. Bu makaledeki adımları izlemek için, uydu konumları olarak etkinleştirmek istediğiniz coğrafi konumların ve bu konumlar için sağlamak istediğiniz test kullanıcılarının bir listesine ihtiyacınız vardır.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Microsoft 365 planınızdaki Multi-Geo Özelliklerini kiracınıza ekleme

Microsoft 365 Multi-Geo'yı kullanmak için _Microsoft 365 planında Multi-Geo Özelliklerine_ sahip olmanız gerekir. Bu planı kiracınıza eklemek için hesap ekibinizle birlikte çalışın. Hesap ekibiniz sizi uygun lisans uzmanına bağlar ve kiracınızı yapılandırtır.

_Microsoft 365 planındaki Multi-Geo Özelliklerinin_ kullanıcı düzeyinde bir hizmet planı olduğunu unutmayın. Uydu konumunda barındırmak istediğiniz her kullanıcı için bir lisansa ihtiyacınız vardır. Uydu konumlarına kullanıcı eklerken zaman içinde daha fazla lisans ekleyebilirsiniz.

Kiracınız  _Microsoft 365 planında Multi-Geo Özellikleri_ ile sağlandıktan sonra **, Coğrafi konumlar** sekmesi OneDrive ve SharePoint yönetim merkezlerinde kullanılabilir duruma gelir.

## <a name="add-satellite-locations-to-your-tenant"></a>Kiracınıza uydu konumları ekleme

Verileri depolamak istediğiniz her coğrafi konum için bir uydu konumu eklemeniz gerekir. Kullanılabilir coğrafi konumlar aşağıdaki tabloda gösterilmiştir:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![SharePoint yönetim merkezindeki coğrafi konumlar sayfasının ekran görüntüsü.](../media/sharepoint-multi-geo-admin-center.png)

Uydu konumu eklemek için

1. SharePoint yönetim merkezini açın. ve <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**Coğrafi konumlara**</a> gidin.

1. **Konum ekle'yi** seçin.

1. Eklemek istediğiniz konumu seçin ve ardından **İleri'yi** seçin.

1. Coğrafi konumla kullanmak istediğiniz etki alanını yazın ve **Ekle'yi** seçin.

1. **Kapat**'ı seçin.

Sağlama, kiracınızın boyutuna bağlı olarak birkaç saatten 72 saate kadar sürebilir. Uydu konumunun sağlanması tamamlandıktan sonra bir e-posta onayı alırsınız. Yeni coğrafi konum, OneDrive yönetim merkezindeki **Coğrafi konumlar** sekmesindeki haritada mavi renkte göründüğünde, kullanıcıların tercih ettiği veri konumunu bu coğrafi konuma ayarlayabilirsiniz.

> [!IMPORTANT]
> Yeni uydu konumunuz varsayılan ayarlarla ayarlanır. Bu, uydu konumunu yerel uyumluluk gereksinimlerinize uygun şekilde yapılandırmanıza olanak sağlar.

## <a name="setting-users-preferred-data-location"></a>Kullanıcıların tercih edilen veri konumunu ayarlama
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span>

Gerekli uydu konumlarını etkinleştirdikten sonra, kullanıcı hesaplarınızı tercih edilen uygun veri konumunu kullanacak şekilde güncelleştirebilirsiniz. Bu kullanıcı merkezi konumda kalıyor olsa bile her kullanıcı için tercih edilen bir veri konumu ayarlamanızı öneririz.

> [!IMPORTANT]
> Kullanıcının tercih edilen veri konumu uydu konumu veya merkezi konum olarak yapılandırılmamış bir konuma ayarlanırsa, OneDrive ve SharePoint siteleri ile Grup posta kutuları sağlanırken sistem varsayılan olarak merkezi konuma ayarlanır.

> [!TIP]
> Çok coğrafi konumu daha geniş kuruluşunuza dağıtmadan önce test kullanıcısı veya küçük bir kullanıcı grubuyla doğrulamalara başlamanızı öneririz.

Azure Active Directory'de (Azure AD) iki tür kullanıcı nesnesi vardır: yalnızca bulut kullanıcıları ve eşitlenmiş kullanıcılar. Lütfen kullanıcı türünüz için uygun yönergeleri izleyin.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Azure AD Connect kullanarak kullanıcının Tercih Edilen Veri Konumunu eşitleme

Şirketinizin kullanıcıları şirket içi Active Directory sisteminden Azure AD'ye eşitlenmişse PreferredDataLocation değerleri AD'de doldurulmalı ve Azure AD ile eşitlenmelidir.

Azure Active Directory Connect eşitlemesindeki işlemi izleyin: Tercih edilen Veri Konumu eşitlemesini şirket içi Active Directory Etki Alanı Hizmetlerinizden (AD DS) Azure AD'ye yapılandırmak [için Microsoft 365 kaynakları için tercih edilen veri konumunu yapılandırın](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) .

Kullanıcının Tercih Edilen Veri Konumunu standart kullanıcı oluşturma iş akışınızın bir parçası olarak ayarlamanızı öneririz.

> [!IMPORTANT]
> OneDrive sağlanmamış yeni kullanıcılar için hesabı lisanslayıp kullanıcının PDL'sinin Azure AD'ye eşitlenmesinden sonra kullanıcının OneDrive İş'te oturum açılabilmesi için en az 48 saat bekleyin. (Kullanıcı OneDrive İş'i sağlamak için oturum açmadan önce tercih edilen veri konumunu ayarlamak, kullanıcının yeni OneDrive'ını doğru konumda sağlamayı sağlar.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Yalnızca bulut kullanıcıları için Tercih Edilen Veri Konumunu ayarlama

Şirketinizin kullanıcıları şirket içi Active Directory sisteminden Azure AD'ye eşitlenmemişse ( yani Microsoft 365 veya Azure AD'de oluşturulmuşsa) PDL'nin Windows PowerShell için Microsoft Azure Active Directory Modülü kullanılarak ayarlanması gerekir.

Bu bölümdeki yordamlar Için [Windows PowerShell Modülü için Microsoft Azure Active Directory Modülü](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) gerekir. Bu modülü zaten yüklediyseniz lütfen en son sürüme güncelleştirdiğinizden emin olun.

1. Kiracınız için bir dizi genel yönetici kimlik bilgileriyle [bağlanın ve oturum açın](/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell&preserve-view=true).

2. Kullanıcılarınızın her biri için tercih edilen veri konumunu ayarlamak için [Set-MsolUser](/powershell/module/msonline/set-msoluser?view=azureadps-1.0&preserve-view=true) cmdlet'ini kullanın. Örneğin:

   ```powershell
   Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
   ```

    tercih edilen veri konumunun düzgün güncelleştirildiğini doğrulamak için Get-MsolUser cmdlet'ini kullanabilirsiniz. Örneğin:

   ```powershell
   (Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation
   ```

![Set-msoluser'ı gösteren PowerShell penceresinin ekran görüntüsü.](../media/multi-geo-tenant-configuration-image3.png)

Kullanıcının Tercih Edilen Veri Konumunu standart kullanıcı oluşturma iş akışınızın bir parçası olarak ayarlamanızı öneririz.

> [!IMPORTANT]
> OneDrive sağlanmamış yeni kullanıcılar için hesabı lisanslayıp kullanıcının PDL'sinin ayarlanmasından sonra kullanıcının OneDrive'da oturum açılabilmesi için değişikliklerin yayılması için en az 48 saat bekleyin. (Kullanıcı OneDrive İş'i sağlamak için oturum açmadan önce tercih edilen veri konumunu ayarlamak, kullanıcının yeni OneDrive'ını doğru konumda sağlamayı sağlar.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive Sağlama ve PDL'nin etkisi

Kullanıcının kiracıda zaten oluşturulmuş bir OneDrive sitesi varsa, PDL'sini ayarlamak mevcut OneDrive'ını otomatik olarak taşımaz. Kullanıcının OneDrive'larını taşımak için bkz. [OneDrive İş Coğrafi Olarak Taşıma](move-onedrive-between-geo-locations.md).

> [!NOTE]
> PLD değişirse ve MailboxRegion artık Posta Kutusu Veritabanı Coğrafi Konum koduyla eşleşmiyorsa Exchange Online kullanıcının posta kutusunu otomatik olarak yeniden yer değiştirir. Daha fazla bilgi için bkz. [Çok coğrafi ortamda Exchange Online posta kutularını yönetme](./administering-exchange-online-multi-geo.md).

Kullanıcının kiracı içinde bir OneDrive sitesi yoksa, kullanıcının PDL'sinin şirketin uydu konumlarından biriyle eşleşeceği varsayılarak, OneDrive bu kullanıcılar için PDL değerine uygun olarak sağlanır.

## <a name="configuring-multi-geo-search"></a>Multi-Geo aramasını yapılandırma

Çok coğrafi kiracınız, arama sorgusunun kiracı içinde herhangi bir yerden sonuç döndürmesine olanak sağlayan toplu arama özelliklerine sahip olacaktır.

Varsayılan olarak, her arama dizini ilgili coğrafi konumu içinde olsa bile bu giriş noktalarından yapılan aramalar toplam sonuçları döndürür:

- OneDrive İş
- Doğan
- SharePoint Giriş
- Arama Merkezi

Ayrıca, SharePoint arama API'sini kullanan özel arama uygulamalarınız için çok coğrafi arama özellikleri yapılandırılabilir.

Sınırlamalar ve farklılıklar da dahil olmak üzere yönergeler [için lütfen OneDrive İş Multi-Geo için Aramayı Yapılandırma'yı](configure-search-for-multi-geo.md) gözden geçirin.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Microsoft 365 Multi-Geo yapılandırmasını doğrulama

Microsoft 365 Multi-Geo'u şirketinize yaygın olarak kullanıma sunulmadan önce doğrulama planınıza dahil etmek isteyebileceğiniz bazı temel kullanım örnekleri aşağıdadır. Bu testleri ve şirketinizle ilgili ek kullanım örneklerini tamamladıktan sonra, ilk pilot grubunuzdaki kullanıcıları eklemeye devam etmeyi seçebilirsiniz.

**OneDrive İş**:

Microsoft 365 uygulama başlatıcısından OneDrive'ı seçin ve kullanıcının PDL'sine bağlı olarak otomatik olarak kullanıcı için uygun coğrafi konuma yönlendirildiğini onaylayın. OneDrive İş artık bu konumda sağlamayı başlatmalıdır. Sağlandıktan sonra bazı belgeleri karşıya yüklemeyi ve indirmeyi deneyin.

**OneDrive Mobil Uygulaması**:

Test hesabı kimlik bilgilerinizle OneDrive mobil Uygulamanızda oturum açın. OneDrive İş dosyalarınızı görebildiğinizi ve bunlarla mobil cihazınızdan etkileşim kurabildiğinizi onaylayın.

**OneDrive eşitleme istemcisi**:

Oturum açma sırasında OneDrive eşitleme istemcisinin OneDrive İş coğrafi konumunuzu otomatik olarak algıladığını onaylayın. Eşitleme istemcisini indirmeniz gerekiyorsa, OneDrive kitaplığında **Eşitle'ye** tıklayabilirsiniz.

**Office uygulamaları**:

Word gibi bir Office uygulamasından oturum açarak OneDrive İş'e erişebildiğinizi onaylayın. Office uygulamasını açın ve "OneDrive – \<TenantName\>" öğesini seçin. Office, OneDrive konumunuzu algılar ve açabileceğiniz dosyaları gösterir.

**Paylaşım**:

OneDrive dosyalarını paylaşmayı deneyin. Kişi seçicinin coğrafi konumlarından bağımsız olarak tüm SharePoint online kullanıcılarınızı size gösterdiğini onaylayın.
