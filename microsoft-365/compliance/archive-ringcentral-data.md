---
title: Microsoft 365'de RingCentral verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, RingCentral verilerini Veritas'tan Microsoft 365 içeri aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'da üçüncü taraf veri kaynaklarından verileri arşivleyabilmenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, eBulma ve saklama ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: c09adf8710014cbf031740902ffbb6c29232a5b8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001636"
---
# <a name="set-up-a-connector-to-archive-ringcentral-data"></a>RingCentral verilerini arşivleye bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

RingCentral platformundaki verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri Microsoft 365 aktarmak için yapılandırılmış bir [RingCentral](https://www.veritas.com/insights/merge1/ringcentral) bağlayıcısı sağlar. Bağlayıcı sohbetler, ekler, görevler, notlar ve gönderiler gibi içerikleri RingCentral'dan e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'daki kullanıcı posta kutularına aktarır.

RingCentral verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için RingCentral bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-ringcentral-data"></a>RingCentral verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'da RingCentral verilerini arşivleye bağlayıcı kullanma işlemini açıklar.

![RingCentral verileri için arşivleme iş akışı.](../media/RingCentralConnectorWorkflow.png)

1. Kuruluşunuz bir RingCentral sitesi ayarlamak ve yapılandırmak için RingCentral ile birlikte çalışır.

2. Her 24 saatte bir RingCentral öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca RingCentral öğelerini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz RingCentral bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve RingCentral içeriğini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında Gelen Kutusu klasöründe **RingCentral** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her RingCentral öğesi, öğenin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/form/requestacall/ms-connectors-contact) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- RingCentral hesabınızdan veri getirmek için bir RingCentral uygulaması oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

- 1. Adımda RingCentral bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-ringcentral-connector"></a>1. Adım: RingCentral bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve RingCentral verileri için bir bağlayıcı oluşturmaktır.

1. **Veri** **bağlayıcılarıRingCentral'a**<https://compliance.microsoft.com> >  gidin ve tıklayın.

2. **RingCentral** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-ringcentral-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde RingCentral'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde RingCentral bağlayıcısını yapılandırmaktır. RingCentral bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **RingCentral kullanıcılarını Microsoft 365 kullanıcılara eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. RingCentral öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-ringcentral-connector"></a>4. Adım: RingCentral bağlayıcısını izleme

RingCentral bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com/> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından **RingCentral** bağlayıcısını seçerek bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
