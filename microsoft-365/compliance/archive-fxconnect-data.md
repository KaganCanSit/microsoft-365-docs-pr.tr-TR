---
title: Fx verilerini aynı dosyada Bağlan için bağlayıcıyı Microsoft 365
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
ms.collection: M365-security-compliance
description: Yöneticiler, veri kaynağında Veritas FX verileri içeri aktarma ve arşivlemek için Bağlan bir bağlayıcı Microsoft 365. Bu bağlayıcı, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: a625cc6d7367521ab30f4018b04f1ad8449efa55
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328309"
---
# <a name="set-up-a-connector-to-archive-fx-connect-data"></a>FX verilerini arşivlemek için bağlayıcıyı Bağlan ayarlama

FX Bağlan işbirliği platformundan verileri kendi Microsoft 365 uyumluluk merkezi kullanıcı posta kutularına içeri aktarmak ve arşivlemek için veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas, [FX Bağlan](https://globanet.com/fx-connect/) öğelerini yakalamak ve bu öğeleri kendi dosya dosyalarında içeri Bağlan için yapılandırılmış bir FX Microsoft 365. Bağlayıcı, FX Bağlan'den gelen ticari ürünler, iletiler ve diğer ayrıntılar gibi içerikleri kuruluş FX Bağlan hesabından bir e-posta ileti biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te kullanıcının posta kutusuna dönüştürür.

FX Bağlan verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. FX Bağlan bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-fx-connect-data"></a>FX verilerini arşivlemeye Bağlan genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı kullanarak FX özet bilgilerini arşivleme Bağlan işlemi Microsoft 365.

![FX verileri için iş Bağlan arşivleme.](../media/FXConnectConnectorWorkflow.png)

1. Kuruluş, FX Bağlan sitesi ayarlamak ve yapılandırmak için FX Bağlan çalışıyor.

2. Her 24 saatte bir, FX Bağlan öğeleri Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı FX veri öğelerini de Bağlan-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'te Bağlan FX Bağlan bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve FX Bağlan öğelerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini 3. Adımda açıklandığı gibi kullanarak  öğeleri belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **FX Bağlan** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her FX Bağlan bu özelliği içerir; bu özellik, öğenin tüm katılımcılarının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun.  Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda FX Bağlan bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-fx-connect-connector"></a>1. Adım: FX Bağlan ayarlama

İlk adım, çalışma sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi FX bağlayıcısı verileri için bir bağlayıcı Bağlan oluşturmaktır.

1. Veri bağlayıcılarıFX [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Veri Bağlayıcıları'ne gidin** >  **ve Bağlan**.

2. FX Ürün **Bağlan** fx sayfasında Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-fx-connect-connector-on-the-veritas-merge1-site"></a>2. Adım: Veri Bağlan sitesinde FX veri kaynağı bağlayıcısı yapılandırma

İkinci adım, Merge1 sitesinde FX Bağlan bağlayıcıyı yapılandırmaktır. FX Bağlayıcısı bağlayıcısı'nın nasıl yapılandır Bağlan için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20FX%20Connect%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **FX kullanıcılarını Bağlan eşleme sayfasında Microsoft 365 kullanıcı** eşlemesini etkinleştirin. FX veri Bağlan, organizasyondaki *kullanıcıların* e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-fx-connect-connector"></a>4. Adım: FX Bağlan izleme

FX veri bağlayıcısı Bağlan, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır sayfayı **görüntülemek Bağlan** FX bağlayıcısı bağlayıcısı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.