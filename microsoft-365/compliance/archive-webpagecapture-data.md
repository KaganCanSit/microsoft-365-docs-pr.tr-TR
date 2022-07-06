---
title: Microsoft 365'te web sayfası verilerini arşivleye bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'te Veritas'tan Web Sayfası Yakalama verilerini içeri aktarmak ve arşiv etmek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal saklama, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivleyebilmenizi sağlar.
ms.openlocfilehash: f73f7fd0328b1e64437ea4ccb52259f461b4d41d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630619"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Web sayfası verilerini arşivleye bağlayıcı ayarlama

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına web sayfalarından verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, belirli bir web sitesinde veya etki alanının tamamında belirli web sayfalarını (ve bu sayfalardaki bağlantıları) yakalayan bir [Web Sayfası Yakalama](https://globanet.com/webpage-capture) bağlayıcısı sağlar. Bağlayıcı web sayfası içeriğini PDF, PNG veya özel dosya biçimine dönüştürür ve dönüştürülen dosyaları bir e-posta iletisine ekler ve ardından bu e-posta öğelerini Microsoft 365'teki kullanıcı posta kutularına aktarır.

Web sayfası içeriği kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma ve bekletme ilkeleri ile bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken Web Sayfası Yakalama bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-webpage-data"></a>Web sayfası verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış, Microsoft 365'te web sayfası içeriğini arşivlerken bağlayıcı kullanma işlemini açıklar.

![Web sayfası verileri için iş akışı arşivleme.](../media/WebPageCaptureConnectorWorkflow.png)

1. Kuruluşunuz bir Web Sayfası Yakalama sitesi ayarlamak ve yapılandırmak için web sayfası kaynağıyla birlikte çalışır.

2. Her 24 saatte bir, web sayfası kaynak öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca bir web sayfasının içeriğini dönüştürür ve bir e-posta iletisine ekler.

3. Uyumluluk portalında oluşturduğunuz Web Sayfası Yakalama bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve web sayfası öğelerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen web sayfası öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **Web Sayfası Yakalama** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve web sayfası öğeleri bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her web sayfası öğesi, [2. Adımda](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site) Web Sayfası Yakalama bağlayıcısını yapılandırırken sağlanan e-posta adresleriyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- Web sayfası öğelerini dönüştürmek üzere özel bir dosya biçimi ayarlamak için Veritas desteğiyle çalışmanız gerekir. Daha fazla bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- 1. Adımda Web Sayfası Yakalama bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>1. Adım: Web Sayfası Yakalama bağlayıcısını ayarlama

İlk adım **, Veri Bağlayıcıları'na** erişmek ve Web Sayfası kaynak verileri için bir bağlayıcı oluşturmaktır.

1. **Veri bağlayıcıları** > **Web Sayfası Yakalama'ya**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **Web Sayfası Yakalama** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Web Sayfası Yakalama bağlayıcısını yapılandırma

İkinci adım, Veritas Merge1 sitesinde Web Sayfası Yakalama bağlayıcısını yapılandırmaktır. Web Sayfası Yakalama bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için aşağıdaki adımları izleyin:

1. **Web Sayfası Eşleme Kullanıcıları Microsoft 365 kullanıcıları ile yakala** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Web Sayfası Yakalama öğeleri, kuruluşunuzdaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcısı ile ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>4. Adım: Web Sayfası Yakalama bağlayıcısını izleme

Web Sayfası Yakalama bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **Web Sayfası Yakalama** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.