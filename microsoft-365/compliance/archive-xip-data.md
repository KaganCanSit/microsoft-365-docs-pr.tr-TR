---
title: XIP kaynak verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, XIP kaynak verilerini Veri görevlerinden içeri aktarıp bu veri kaynağına arşivlemek için bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 02ea9d58e200a14e5141c1a29c527067bb98bd16
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318235"
---
# <a name="set-up-a-connector-to-archive-xip-source-data"></a>XIP kaynak verilerini arşivlemek için bağlayıcıyı ayarlama

XIP kaynak platformundan verileri Microsoft 365 uyumluluk merkezi ve bu platformda yer alan kullanıcı posta kutularına içeri aktarmak ve Microsoft 365 kullanın. Veritas, öğeleri [başka bir dosyaya](https://globanet.com/xip/) almak için XIP dosyası kullanmana olanak sağlayan bir XIP Microsoft 365. XIP dosyası ZIP dosyasına benzer, ancak dijital imzanın kullanılmaktadır. Dijital imza, XIP kaynak dosyası ayıklanmadan önce VeriTas Merge 1 tarafından doğrulanır. Bağlayıcı, XIP kaynak dosyasındaki içeriği bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri aynı dosyadaki kullanıcı posta kutularına Microsoft 365.

XIP kaynak verileri kullanıcı posta kutularında depo olduktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir e-postada içeri aktarıp Microsoft 365 için XIP bağlayıcısı kullanmak, düzenleme ve devlet ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-the-xip-source-data"></a>XIP kaynak verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, XIP kaynak verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365.

![XIP kaynak verileri için iş akışı arşivleme.](../media/XIPConnectorWorkflow.png)

1. Bir XIP sitesini ayarlamak ve yapılandırmak için, organizasyonunız XIP kaynağıyla çalışır.

2. XIP kaynak öğeleri her 24 saatte bir Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı, içeriği e-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları XIP bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş ileti öğelerini, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini  kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Gelen Kutusu klasöründe **XIP** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her kaynak öğe, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda XIP bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-xip-connector"></a>1. Adım: XIP bağlayıcıyı ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi XIP kaynak verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) **XIP'ye gidin ve bu** \> **öğeye tıklayın**.

2. **XIP ürün açıklaması** sayfasında Yeni bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-xip-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde XIP bağlayıcıyı yapılandırma

İkinci adım, Birleştirme1 sitesinde XIP bağlayıcıyı yapılandırmaktır. XIP bağlayıcısı yapılandırma hakkında daha fazla bilgi için bkz. [Üçüncü Taraf Bağlayıcıları Kullanım Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XIP%20User%20Guide%20.pdf).'

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **XIP kullanıcılarını kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. XIP kaynak öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-xip-connector"></a>4. Adım: XIP bağlayıcıyı izleme

XIP bağlayıcıyı oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından XIP** bağlayıcıyı seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.