---
title: LinkedIn verilerini arşivlemek için bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Yöneticilerin LinkedIn Şirket & verileri içeri aktararak yerel bir bağlayıcı kullanarak yerel bir bağlayıcıyı nasıl ayar kuruluş Microsoft 365.
ms.openlocfilehash: 944a8bcbd06a07653ccf5e98e28807d279b66023
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322205"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>LinkedIn verilerini arşivlemek için bağlayıcı ayarlama

LinkedIn Company sayfalarından verileri Microsoft 365 uyumluluk merkezi ve arşivlemek için aşağıdaki bağlantıda bir bağlayıcı kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı belirli LinkedIn Company sayfasının hesabına her 24 saatte bir bağlanır. Bağlayıcı, Şirket sayfasına gönderilen iletileri bir e-posta iletisine dönüştürür ve sonra bu öğeleri Şirket'te bir posta kutusuna Microsoft 365.

LinkedIn Company sayfa verileri bir posta kutusunda depo olduktan sonra, LinkedIn verilerine Microsoft 365 Bekletme, İçerik Araması, In-Place Arşivleme, Denetim ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama kullanarak bu öğeleri arayabilir veya depolama posta kutusunu bir özel durum durumunda bir koruyucuyla Advanced eDiscovery. LinkedIn verilerini başka bir kuruluşta içeri aktarın ve Microsoft 365 bağlayıcı oluşturmak, kuruma resmi ve mevzuat ilkeleriyle uyumlu çalışma konusunda yardımcı olabilir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- LinkedIn Şirket Sayfası bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Arşivlemek istediğiniz LinkedIn Şirket Sayfasının yöneticisi olan bir LinkedIn kullanıcı hesabının oturum açma kimlik bilgilerine (e-posta adresi veya telefon numarası ve parola) sahip olmak gerekir. Bağlayıcıyı ayarlarken LinkedIn'de oturum ataş için bu kimlik bilgilerini kullanırsanız.

- LinkedIn bağlayıcısı, bir günde toplam 200.000 öğe içeri aktarabilirsiniz. Bir günde 200.000'den fazla LinkedIn öğesi varsa, bu öğelerin hiçbiri bu öğelere Microsoft 365.

## <a name="create-a-linkedin-connector"></a>LinkedIn bağlayıcısı oluşturma

1. Veri bağlayıcılarıLinkedIn <https://compliance.microsoft.com> Şirket **sayfalarına** >  **gidin ve bu sayfalara tıklayın**.

2. **LinkedIn şirket sayfaları ürün sayfasında** Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet koşulları **sayfasında Kabul** Et'i **seçin**.

4. **LinkedIn ile oturum açma sayfasında LinkedIn** ile **oturum açma'ya tıklayın**.

   LinkedIn oturum açma sayfası görüntülenir.

   ![LinkedIn oturum açma sayfası.](../media/LinkedInSigninPage.png)

5. LinkedIn oturum açma sayfasında, arşivlemek istediğiniz şirket sayfasıyla ilişkilendirilmiş LinkedIn hesabının e-posta adresini (veya telefon numarasını) ve parolasını girin ve ardından Oturum **aç'a tıklayın**.

   Oturum ataş hesabınızla ilişkilendirilmiş tüm LinkedIn Şirket Sayfalarının listesiyle bir sihirbaz sayfası görüntülenir. Bağlayıcı yalnızca bir şirket sayfası için yalnızdırabilirsiniz. Kuruluşta birden çok LinkedIn Şirket Sayfası varsa, her biri için bir bağlayıcı oluşturmanız gerekir.

   ![LinkedIn Şirket Sayfaları listesinin yer olduğu bir sayfa görüntülenir.](../media/LinkedInSelectCompanyPage.png)

6. Öğelerini arşivlemek istediğiniz şirket sayfasını seçin ve ardından Sonraki'ye **tıklayın**.

7. Depolama **konumunu seçin** sayfasında, kutunun içini tıklatın, LinkedIn öğelerinin aktarın Microsoft 365 posta kutusunun e-posta adresini seçin ve sonra da Sonraki'yi **tıklatın**. Öğeler bu posta kutusunun gelen kutusu klasörüne aktarılır.

8. Bağlayıcı **ayarlarını gözden** geçirmek için Sonraki'ne tıklayın ve sonra **da bağlayıcı kurulumunu** tamamlamak için Son'a tıklayın.

Bağlayıcıyı oluşturdukktan sonra, yeni bağlayıcının içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına geri dönebilirsiniz (bağlayıcı listesini güncelleştirmek için Gerekirse  Yenile'yi seçin). Durum sütunundaki **değer** , **Başlamayı bekliyor olarak gösterir**. İlk içeri aktarma işleminin başlat olması 24 saat kadar sürebilir. Bağlayıcı LinkedIn öğelerini ilk kez çalıştırıyor ve içeri aktarıyorsa, bağlayıcı her 24 saatte bir çalışır ve önceki 24 saat içinde LinkedIn Şirket Sayfasında oluşturulan tüm yeni öğeleri içeri aktaracak.

Daha fazla ayrıntı görüntülemek için Veri bağlayıcıları sayfasındaki **listeden** bağlayıcıyı seçerek uç uç sayfasını görüntüleyebilirsiniz. **Durum'un** altında, görüntülenen tarih aralığı bağlayıcı oluşturulurken seçilen yaş filtresini gösterir.

## <a name="more-information"></a>Daha fazla bilgi

LinkedIn öğeleri, dosyadaki depolama posta kutusunun gelen kutusunda yer alan LinkedIn alt klasörüne Microsoft 365. Bunlar, e-posta iletileri olarak görünür.