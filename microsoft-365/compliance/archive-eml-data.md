---
title: EML verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler EML verilerini Veritas'tan veri kaynağına aktaracak ve arşivleyacak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: aafa253cc4a507946acd56cfbd52af79d8250ee6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325355"
---
# <a name="set-up-a-connector-to-archive-eml-data"></a>EML verilerini arşivlemek için bağlayıcıyı ayarlama

EML verilerini kendi Microsoft 365 uyumluluk merkezi posta kutularına içeri aktararak arşivlemek için veri kaynağında bir Veritas Microsoft 365 kullanın. EML, bir dosyaya kaydedilen e-posta iletisi için dosya uzantısıdır. Bağlayıcı, öğenin içeriğini kaynak biçimden e-posta iletisi biçimine dönüştürür ve sonra öğeyi kullanıcı posta kutusuna içeri dönüştürür.

EML iletileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. E-postada verileri içeri aktararak ve arşiv Microsoft 365 EML bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-eml-data"></a>EML verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, EML verilerini aynı tabloda arşivlemek için bağlayıcı kullanma Microsoft 365.

![EML verileri için iş akışı arşivleme.](../media/EMLConnectorWorkflow.png)

1. Organizasyonunız EML sitesini ayarlamak ve yapılandırmak için EML kaynağıyla çalışır.

2. HER 24 saatte bir, EML kaynağından gelen içerik öğeleri Veri Görev Birleştirme1 sitesine kopyalanır. Bu işlem sırasında, EML dosyasının içeriği e-posta iletisi biçimine dönüştürülür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları EML bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş ileti öğelerini, 3. Adımda açıklanan otomatik kullanıcı eşleme işleminin *E-posta* özelliği değerini kullanarak belirli kullanıcıların posta kutularına [içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Bu işlem sırasında, kullanıcı posta kutularında EML adlı Gelen Kutusu klasöründe yer alan **eml** adlı bir alt klasör oluşturulur ve EML öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her iletide, içerik öğesinin tüm katılımcılarının e-posta adresiyle doldurulan bu özellik yer alır.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda EML bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-an-eml-connector"></a>1. Adım: EML Bağlayıcısı ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve EML verileri Microsoft 365 uyumluluk merkezi bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıEML'ye [https://compliance.microsoft.com](https://compliance.microsoft.com/) **gidin ve bu bağlayıcılara** >  **tıklayın**.

2. **EML ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-eml-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde EML bağlayıcısı yapılandırma

İkinci adım, VeriTas Merge1 sitesinde EML bağlayıcısı yapılandırmaktır. EML bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20EML%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. EML kaynak öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, EML öğeleri bu kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-eml-connector"></a>4. Adım: EML bağlayıcıyı izleme

EML bağlayıcıyı oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **sonra açılır sayfayı görüntülemek için EML** bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.