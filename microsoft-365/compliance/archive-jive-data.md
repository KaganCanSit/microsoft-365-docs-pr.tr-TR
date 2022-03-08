---
title: Jive verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, veri kaynağında Veritas'tan Jive verilerini içeri aktarma ve arşivlemek için bir bağlayıcı Microsoft 365. Bu bağlayıcı, üçüncü taraf verilerini Microsoft 365'de arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 6133073227e60a0a6ba9022b4b6cac59f85157e6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313279"
---
# <a name="set-up-a-connector-to-archive-jive-data"></a>Jive verilerini arşivlemek için bağlayıcıyı ayarlama

İş birliği platformundan verileri Microsoft 365 uyumluluk merkezi ve Microsoft 365 posta kutularına aktarın ve arşiv için, çalışma Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalayan (düzenli olarak) ve bu öğeleri başka bir öğeye aktaracak şekilde yapılandırılmış bir [Jive](https://globanet.com/jive/) bağlayıcısı Microsoft 365. Bağlayıcı, bir kullanıcının Jive hesabından e-posta iletileri, sohbetler ve ekler gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'da kullanıcının posta kutusuna aktarıyor.

Jive verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Jive bağlayıcısı kullanarak verileri başka bir kuruluşta içeri Microsoft 365 arşivlemek, kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-jive-data"></a>Jive verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Jive verilerini tek bir tabloda arşivlemek için bağlayıcı Microsoft 365.

![Jive verileri için iş akışı arşivleme.](../media/JiveConnectorWorkflow.png)

1. Your organization works with Jive to set up and configure a Jive site.

2. Her 24 saatte bir, Jive'den gelen öğeler Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı, Jive öğelerinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturtlayın Jive bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve içeriği Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, [3](#step-3-map-users-and-complete-the-connector-setup). Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak dönüştürülmüş öğeleri belirli kullanıcıların posta kutularına alır. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Jive** adlı yeni bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Jive öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda Jive bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-jive-connector"></a>1. Adım: Jive bağlayıcıyı ayarlama

İlk adım, çalışma sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi Jive verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıJive'ye [https://compliance.microsoft.com](https://compliance.microsoft.com/) **gidin ve** **bu öğeye** >  tıklayın.

2. Jive **ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-jive-connector"></a>2. Adım: Jive bağlayıcıyı yapılandırma

İkinci adım, Birleştirme1 sitesinde Jive bağlayıcıyı yapılandırmaktır. Jive bağlayıcıyı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Jive%20User%20Guide.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu aşağıdaki Microsoft 365 uyumluluk merkezi izleyin:

1. **Jive kullanıcılarını kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. Jive öğeleri, kurumdaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-jive-connector"></a>4. Adım: Jive bağlayıcıyı izleme

Jive bağlayıcıyı oluşturduk sonra, bağlayıcının durumunu bağlayıcının hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve açılır **sayfayı görüntülemek için Jive** bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.