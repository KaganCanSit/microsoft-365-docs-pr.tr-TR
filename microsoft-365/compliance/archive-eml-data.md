---
title: Microsoft 365'te EML verilerini arşivleye bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Yöneticiler, EML verilerini Veritas'tan Microsoft 365'e aktarmak ve arşivlemesi için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivlenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 2d0d0afec6bfb35700ee8b22727f8732f111286a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636677"
---
# <a name="set-up-a-connector-to-archive-eml-data"></a>EML verilerini arşivleye bağlayıcı ayarlama

EML verilerini Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı veritas bağlayıcısını kullanın. EML, bir dosyaya kaydedilen e-posta iletisinin dosya uzantısıdır. Bağlayıcı, bir öğenin içeriğini kaynak biçimden e-posta iletisi biçimine dönüştürür ve sonra öğeyi bir kullanıcı posta kutusuna aktarır.

EML iletileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma ve bekletme ilkeleri ile bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken EML bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-eml-data"></a>EML verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te EML verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![EML verileri için iş akışı arşivleme.](../media/EMLConnectorWorkflow.png)

1. Kuruluşunuz BIR EML sitesi ayarlamak ve yapılandırmak için EML kaynağıyla çalışır.

2. 24 saatte bir EML kaynağındaki içerik öğeleri Veritas Merge1 sitesine kopyalanır. Bu işlem sırasında, bir EML dosyasının içeriği e-posta iletisi biçimine dönüştürülür.

3. Uyumluluk portalında oluşturduğunuz EML bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklanan otomatik kullanıcı eşleme işleminin *Email* özelliğinin değerini kullanarak dönüştürülen ileti öğelerini belirli kullanıcıların posta kutularına aktarır. Bu işlem sırasında, kullanıcı posta kutularında **EML** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve EML öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her ileti, içerik öğesinin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://globanet.com/ms-connectors-contact) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- 1. Adımda EML bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-an-eml-connector"></a>1. Adım: EML Bağlayıcısı ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve EML verileri için bir bağlayıcı oluşturmaktır.

1. **Veri bağlayıcıları** > **EML'ye**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **EML** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-eml-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde EML bağlayıcısını yapılandırma

İkinci adım, Veritas Merge1 sitesinde EML bağlayıcısını yapılandırmaktır. EML bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20EML%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Dış kullanıcıları Microsoft 365 kullanıcıları ile eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. EML kaynak öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcısı ile ilişkilendirebiliyorsa, EML öğeleri bu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-eml-connector"></a>4. Adım: EML bağlayıcısını izleme

EML bağlayıcısını oluşturduktan sonra bağlayıcı durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **EML** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.