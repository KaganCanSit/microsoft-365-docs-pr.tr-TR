---
title: Microsoft 365'da Senfoni verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler Veritas Symphony'den verileri Microsoft 365 içeri aktarmak ve arşivlemesi için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'da üçüncü taraf veri kaynaklarından verileri arşivleyabilmenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 119d5b34d32cd193d4ab5e89d6e435c3fc24a574
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64938565"
---
# <a name="set-up-a-connector-to-archive-symphony-data"></a>Senfoni verilerini arşivleye bağlayıcı ayarlama

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına Senfoni verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Senfoni, finansal hizmetler sektöründe kullanılan bir mesajlaşma ve işbirliği platformudur. Veritas, uyumluluk portalında üçüncü taraf veri kaynağından öğeleri yakalamak (düzenli olarak) ve ardından bu öğeleri kullanıcı posta kutularına aktarmak için yapılandırabileceğiniz bir [Senfoni](https://globanet.com/symphony) veri bağlayıcısı sağlar. Bağlayıcı, bir öğenin içeriğini Senfoni hesabından bir e-posta iletisi biçimine dönüştürür ve sonra öğeyi Microsoft 365 bir posta kutusuna aktarır.

Senfoni iletişimleri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için Bir Senfoni bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-symphony-data"></a>Senfoni verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakış, Microsoft 365'da Symphony iletişimlerini arşivleyemek için veri bağlayıcısı kullanma işlemini açıklar.

![Senfoni arşivleme iş akışı.](../media/SymphonyConnectorWorkflow.png)

1. Kuruluşunuz bir Senfoni sitesi ayarlamak ve yapılandırmak için Senfoni ile birlikte çalışır.

2. Her 24 saatte bir Senfoni'den gelen sohbet iletileri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca sohbet iletisinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Senfoni bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen ileti öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Symphony** adlı yeni bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her sohbet iletisi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://globanet.com/ms-connectors-contact) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- 1. Adımda Senfoni bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-symphony-connector"></a>1. Adım: Senfoni bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Senfoni verileri için bir bağlayıcı oluşturmaktır.

1. [https://compliance.microsoft.com](https://compliance.microsoft.com/) Adresine gidin ve **Veri bağlayıcılarıSymphony** >  seçeneğine tıklayın.

2. **Senfoni** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="configure-the-symphony-connector-on-the-veritas-merge1-site"></a>Veritas Merge1 sitesinde Senfoni bağlayıcısını yapılandırma

İkinci adım, Merge1 sitesinde Senfoni bağlayıcısını yapılandırmaktır. Veritas Merge1 sitesinde Senfoni bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Dış kullanıcıları Microsoft 365 kullanıcılarla eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Senfoni öğeleri, kuruluşunuzdaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-symphony-connector"></a>4. Adım: Senfoni bağlayıcısını izleme

Senfoni bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **Senfoni** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.