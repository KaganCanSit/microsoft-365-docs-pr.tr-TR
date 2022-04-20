---
title: MICROSOFT 365'da FX Bağlan verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'da Veritas FX Bağlan verilerini içeri aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal saklama, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 79d4dca6c71f6654db7294d55761275d8b758727
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946736"
---
# <a name="set-up-a-connector-to-archive-fx-connect-data"></a>FX Bağlan verilerini arşivleye bağlayıcı ayarlama

Fx Bağlan işbirliği platformundaki verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Veritas, [FX Bağlan](https://globanet.com/fx-connect/) öğelerini yakalamak ve bu öğeleri Microsoft 365 aktarmak için yapılandırılmış bir FX Bağlan bağlayıcısı sağlar. Bağlayıcı, FX Bağlan içeriği (örneğin, kuruluşunuzun FX Bağlan hesabından gelen alım satimlar, iletiler ve diğer ayrıntılar) bir e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365 kullanıcının posta kutusuna aktarır.

FX Bağlan verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için FX Bağlan bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-fx-connect-data"></a>FX Bağlan verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'da FX Bağlan bilgilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![FX Bağlan verileri için arşivleme iş akışı.](../media/FXConnectConnectorWorkflow.png)

1. Kuruluşunuz, FX Bağlan sitesi ayarlamak ve yapılandırmak için FX Bağlan ile çalışır.

2. 24 saatte bir FX Bağlan hesaplarından alınan öğeler Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca FX Bağlan öğelerini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz FX Bağlan bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve FX Bağlan öğelerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak öğeleri belirli kullanıcıların posta kutularına aktarır. Gelen Kutusu klasöründe kullanıcı posta kutularında **FX Bağlan** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her FX Bağlan öğesi, öğenin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun.  Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://globanet.com/ms-connectors-contact) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- 1. Adımda FX Bağlan bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-fx-connect-connector"></a>1. Adım: FX Bağlan bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve FX Bağlan verileri için bir bağlayıcı oluşturmaktır.

1. **Veri bağlayıcılarıFX** >  **Bağlan'ne**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **FX Bağlan** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-fx-connect-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde FX Bağlan bağlayıcısını yapılandırma

İkinci adım, Merge1 sitesinde FX Bağlan bağlayıcısını yapılandırmaktır. FX Bağlan bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20FX%20Connect%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Kullanıcıları Microsoft 365 için Map FX Bağlan** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. FX Bağlan öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-fx-connect-connector"></a>4. Adım: FX Bağlan bağlayıcısını izleme

FX Bağlan bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com/> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **FX Bağlan** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.