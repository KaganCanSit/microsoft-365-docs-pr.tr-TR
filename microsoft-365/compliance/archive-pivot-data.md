---
title: Microsoft 365'de Pivot verilerini arşivleye bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'da Veritas'tan Pivot verilerini içeri aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal saklama, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 7719dabb59180d6c3dc579c02fbc76b0d77ec1a7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001664"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Pivot verilerini arşivleye bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Verileri Pivot platformundan Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından (düzenli olarak) öğeleri yakalamak ve ardından bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir [Pivot](https://globanet.com/pivot/) bağlayıcısı sağlar. Pivot, finansal piyasa katılımcılarıyla işbirliğine olanak tanıyan bir anlık ileti platformudur. Bağlayıcı, sohbet iletileri gibi öğeleri kullanıcıların Pivot hesaplarından e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır.

Pivot verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için Pivot bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-pivot-data"></a>Pivot verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'de Pivot verilerini arşivlemek için bağlayıcı kullanma işlemini açıklar.

![Pivot verileri için iş akışı arşivleme.](../media/PivotConnectorWorkflow.png)

1. Kuruluşunuz Bir Pivot kaynak sitesi ayarlamak ve yapılandırmak için Pivot ile birlikte çalışır.

2. 24 saatte bir, Pivot öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca Pivot öğelerini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Pivot bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve Pivot öğelerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak Pivot öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Pivot** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her Pivot öğesi, öğenin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- 1. Adımda Pivot bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-pivot-connector"></a>1. Adım: Pivot bağlayıcısını ayarlama

İlk adım, Microsoft uyumluluk merkezindeki **Veri Bağlayıcıları** sayfasına erişmek ve Pivot verileri için bir bağlayıcı oluşturmaktır.

1. **Veri** **bağlayıcılarıPivot'a**[https://compliance.microsoft.com](https://compliance.microsoft.com/) >  gidin ve tıklayın.

2. **Özet** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-pivot-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Pivot bağlayıcısını yapılandırma

İkinci adım, Birleştir1 sitesinde Pivot bağlayıcısını yapılandırmaktır. Veritas Merge1 sitesinde Pivot bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve Microsoft 356 uyumluluk merkezinde bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Pivot kullanıcılarını Microsoft 365 kullanıcılara eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Pivot öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-pivot-connector"></a>4. Adım: Pivot bağlayıcısını izleme

Pivot bağlayıcısını oluşturduktan sonra uyumluluk portalında bağlayıcının durumunu görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **Pivot** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.