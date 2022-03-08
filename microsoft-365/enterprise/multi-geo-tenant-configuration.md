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
description: Bu makalede uydu konumları ekleme ve Multi-Geo için kiracınızı yapılandırma Microsoft 365 öğrenin.
ms.openlocfilehash: 9842ff2295a64f544940f579d732c688735ae341
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312089"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 Multi-Geo kiracı yapılandırması

Kiracınızı Multi-Geo Microsoft 365 yapılandırmadan önce [Multi-Geo için plan yapmayı Microsoft 365 emin olun](plan-for-multi-geo.md). Bu makaledeki adımları takip etmek için, uydu konumları olarak etkinleştirmek istediğiniz coğrafi konumların ve bu konumlara sağlanmasını istediğiniz test kullanıcılarının bir listesi gerekir.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Kaynak planınıza Multi-Geo Özelliklerini Microsoft 365 kiracınıza ekleme

Multi-Geo Microsoft 365 kullanmak için, Birden Çok Coğrafi _(Multi-Geo_) özelliğine Microsoft 365 gerekir. Bu planı kiracınıza eklemek için hesap ekibiyle birlikte çalışabilirsiniz. Hesap takımınız sizi uygun lisans uzmanıyla bağlantı kuracak ve kiracınızı yapılandıracak.

Bu _Plan'daki Multi-Geo Microsoft 365_, kullanıcı düzeyi hizmet planı olduğunu unutmayın. Uydu konumda barındırmak istediğiniz her kullanıcı için bir lisansa ihtiyacınız var. Uydu konumlarında kullanıcıları eklerken zamanla daha fazla lisans  eklersiniz.

Kiracınız Microsoft 365 planında _Multi-Geo_ Özellikleri ile sağlandıktan sonra, Coğrafi konumlar sekmesi OneDrive yönetim SharePoint  kullanılabilir hale gelecektir.

## <a name="add-satellite-locations-to-your-tenant"></a>Kiracınıza uydu konumları ekleme

Verileri depolamak istediğiniz her coğrafi konum için bir uydu konumu eklemeniz gerekir. Kullanılabilir coğrafi konumlar aşağıdaki tabloda gösterilmektedir:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Yönetim merkezinde coğrafi konumlar sayfasının SharePoint görüntüsü.](../media/sharepoint-multi-geo-admin-center.png)

Uydu konumu eklemek için

1. SharePoint yönetim merkezini açın. ve Geo <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**konumlar'a gidin**</a>.

1. Konum **ekle'yi seçin**.

1. Eklemek istediğiniz konumu seçin ve sonra da Sonraki'yi **seçin**.

1. Coğrafi konumla kullanmak istediğiniz etki alanını yazın ve ekle'yi **seçin**.

1. **Kapat**'ı seçin.

Sağlama, kiracının boyutuna bağlı olarak birkaç saat ile 72 saat arasında sürebilir. Uydu konumunun sağlanması tamamlandıktan sonra bir e-posta onayı alırsınız. Yeni coğrafi konum, OneDrive yönetim merkezinin Coğrafi konumlar sekmesindeki haritada  mavi görüntülendiğinde, kullanıcıların tercih ettiği veri konumunu bu coğrafi konuma ayarlamaya devam edebilirsiniz. 

> [!IMPORTANT]
> Yeni uydu konumunuz varsayılan ayarlarla ayarlanır. Bu, uydu konumunu yerel uyumluluk gereklerine uygun şekilde yapılandırmanıza olanak sağlar.

## <a name="setting-users-preferred-data-location"></a>Kullanıcıların tercih edilen veri konumunu ayarlama
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Gerekli uydu konumlarını etkinleştirebilirsiniz ve kullanıcı hesaplarınızı uygun tercih edilen veri konumunu kullanmak üzere güncelleştirebilirsiniz. Her kullanıcı merkezi konumda kalıyor olsa bile, her kullanıcı için tercih edilen veri konumu ayarlamayı öneririz.

> [!IMPORTANT]
> Kullanıcının tercih ettiği veri konumu, uydu konumu veya merkezi konum olarak yapılandırılmamış bir konuma ayarlanmışsa, OneDrive ve SharePoint posta kutuları sağlarken sistem varsayılan olarak merkezi konumu kullanır.

> [!TIP]
> Çok coğrafi alanı daha geniş bir kuruluşa yuvarlamadan önce, test kullanıcısı veya küçük bir kullanıcı grubuyla doğrulamaya başlamanızı öneririz.

Diğer Azure Active Directory (Azure AD) iki tür kullanıcı nesnesi vardır: yalnızca bulut kullanıcıları ve eşitlenmiş kullanıcılar. Lütfen kullanıcı türünüz için uygun yönergeleri izleyin.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Kullanıcının Tercih Edilen Veri Konumunu Azure AD Depolama Alanı kullanarak Bağlan 

Şirketinizin kullanıcıları şirket içi Active Directory sisteminden Azure AD'ye eşitlenmişse, bunların PreferredDataLocation ad'de doldurulması ve Azure AD ile eşitlenmesi gerekir.

Eşitlemeyi eşitleme Azure Active Directory Bağlan[:](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) Şirket içi Active Directory Etki Alanı Hizmetleri'nden (AD DS) Azure AD'ye Tercih Edilen Veri Konumu eşitlemesi'ni yapılandırmak üzere Microsoft 365 kaynakları için tercih edilen veri konumunu yapılandırma.

Standart kullanıcı oluşturma iş akışınız kapsamında kullanıcının Tercih Edilen Veri Konumu'nun ayarlamayı da eklemenizi öneririz.

> [!IMPORTANT]
> Herhangi bir sağlama OneDrive yeni kullanıcılar için, hesaba lisans atarak değişikliklerin kullanıcının OneDrive İş'da oturum a OneDrive için yayılması için kullanıcının PDL'si Azure AD ile eşitlendikten sonra en az 48 saat OneDrive İş. (Tercih edilen veri konumu, kullanıcı oturum atımadan önce ayar OneDrive İş yeni posta OneDrive doğru konumda sağlanmasını sağlar.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Yalnızca bulut kullanıcıları için Tercih Edilen Veri Konumunu ayarlama 

Şirketinizin kullanıcıları şirket içi Active Directory sisteminden Azure AD'ye eşitlenmezse (bu, kullanıcıların Microsoft 365 veya Azure AD'de oluşturuldukları anlamına gelir) PDL'nin Şirket için Microsoft Azure Active Directory Modülü kullanılarak ayarlanmış Windows PowerShell.

Bu bölümdeki yordamlar için [Microsoft Azure Active Directory Modülü için Windows PowerShell gerekir](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Bu modülü zaten yüklemişsiniz, lütfen en son sürüme güncelleştirin.

1.  [Bağlan için bir](/powershell/connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) dizi genel yönetici kimlik bilgileriyle oturum açın.

2.  Her [kullanıcınız için tercih edilen veri konumunu ayarlamak üzere Set-MsolUser](/powershell/msonline/v1/set-msoluser) cmdlet'ini kullanın. Örneğin:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Tercih edilen veri konumunun doğru güncelleştirildiğini onaylamak için, Get-MsolUser kontrol edin. Örneğin:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![set-msoluser gösteren PowerShell penceresinin ekran görüntüsü.](../media/multi-geo-tenant-configuration-image3.png)

Standart kullanıcı oluşturma iş akışınız kapsamında kullanıcının Tercih Edilen Veri Konumu'nun ayarlamayı da eklemenizi öneririz.

> [!IMPORTANT]
> Sağlanan lisansı OneDrive yeni kullanıcılar için, hesabı lisans edin ve kullanıcının PDL'si değişikliklerin OneDrive'te oturum açından önce yayılması için ayar yapıldıktan sonra en az 48 OneDrive. (Tercih edilen veri konumu, kullanıcı oturum atımadan önce ayar OneDrive İş yeni posta OneDrive doğru konumda sağlanmasını sağlar.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive Sağlama ve PDL'nin etkisi

Kullanıcının zaten kiracıda oluşturulmuş OneDrive varsa, PDL'sini ayarlama, var olan kullanıcı kimlik bilgilerini otomatik olarak OneDrive. Bir kullanıcının bilgilerini taşımak için OneDrive Geo [Move OneDrive İş bakın](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online, PLD değişir ve MailboxRegion artık Posta Kutusu Veritabanının Coğrafi Konum koduyla eş eşleşmezse kullanıcının posta kutusunu otomatik olarak yeniden kullanır. Daha fazla bilgi için [bkz. Exchange Online kutularını çok coğrafi ortamda yönetme](./administering-exchange-online-multi-geo.md).

Kullanıcının kiracı içinde OneDrive sitesi yoksa, kullanıcının PDL değerine uygun olarak OneDrive, kullanıcının PDL değerine uygun olarak şirketin uydu konumlarından biri ile eşladığı varsayıldı.

## <a name="configuring-multi-geo-search"></a>Multi-Geo aramasını yapılandırma

Çok coğrafi kiracınız, arama sorgusunun kiracı içinde herhangi bir yerden sonuç vermelerine olanak sağlayan bir toplam arama özelliklerine sahip olur.

Varsayılan olarak, her arama dizini ilgili coğrafi konumda yer alıyor olsa bile, bu giriş noktalarından yapılan aramalar toplam sonuçları verir:

- OneDrive İş

- Delve

- SharePoint Giriş

- Arama Merkezi

Buna birden fazla coğrafi konumda arama, arama API'sini kullanan özel arama uygulamalarınız için SharePoint yapılandırabilirsiniz.

Sınırlamalar ve [farklılıklar gibi yönergeler OneDrive İş için Multi-Geo'da](configure-search-for-multi-geo.md) Arama'OneDrive İş'yi yapılandırmayı gözden geçirmeyi gözden geçirmeyi unutmayın.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Multi-Geo Microsoft 365 yapılandırmayı doğrulama

Aşağıda, Multi-Geo olarak şirketinize geniş bir şekilde bilgi Microsoft 365 doğrulama planınıza eklemek istediğiniz bazı temel kullanım örnekleri verilmiştir. Bu testleri ve şirketinize uygun ek kullanım durumlarını tamamlandıktan sonra, kullanıcıları ilk pilot grubunuza eklemeyi seçebilirsiniz.

**OneDrive İş**

OneDrive uygulama başlatıcıda Microsoft 365'ı seçin ve kullanıcının PDL'si tabanlı olarak otomatik olarak kullanıcı için uygun coğrafi konuma yönlendiril telefonlar olduğunu onaylayın. OneDrive İş konumda sağlamayı başlatabilirsiniz. Hazır olduktan sonra, bazı belgeleri karşıya yükleme ve indirmeyi deneyin.

**OneDrive Mobil Uygulaması**

test hesabı kimlik OneDrive ile OneDrive Mobil Uygulama'nıza oturum açın. Mobil cihazınızı kullanarak en son OneDrive İş ve bu dosyalarla etkileşim kurabilirsiniz.

**OneDrive eşitleme istemcisi**

Oturum açma sırasında OneDrive eşitleme istemcisinin coğrafi konumu OneDrive İş olarak algılamayı onaylayın. Eşitleme istemcisini indirmeniz gerekirse, eşitleme istemci **kitaplığında Eşitle'OneDrive** tıkekleyebilirsiniz.

**Office uygulamaları**

Word gibi bir OneDrive İş bir uygulamada oturum Office erişebilirsiniz. Office uygulamasını açın ve "OneDrive – " öğesini <TenantName>seçin. Office dosyanızı OneDrive ve açabilirsiniz dosyaları gösterir.

**Paylaşım**

Daha fazla OneDrive deneyin. Kişi seçicinin coğrafi konumlarından bağımsız olarak tüm SharePoint çevrimiçi kullanıcılarınızı gösterip gösterir; bunu onaylayın.
