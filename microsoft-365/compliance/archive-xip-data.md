---
title: Microsoft 365'te XIP kaynak verilerini arşivleye bağlayıcı ayarlama
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
description: Yöneticiler, XIP kaynak verilerini Veritas'tan Microsoft 365'e aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivlenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: a5ae71c246170f7eda041dd521e779f9c6218278
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626897"
---
# <a name="set-up-a-connector-to-archive-xip-source-data"></a>XIP kaynak verilerini arşivleye bağlayıcı ayarlama

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına XIP kaynak platformundaki verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, öğeleri Microsoft 365'e aktarmak için XIP dosyası kullanılmasına olanak tanıyan bir [XIP](https://globanet.com/xip/) bağlayıcısı sağlar. XIP dosyası ZIP dosyasına benzer, ancak dijital imzanın kullanılmasına izin verir. Dijital imza, XIP kaynak dosyası ayıklanana kadar Veritas Merge 1 tarafından doğrulanır. Bağlayıcı, XIP kaynak dosyasındaki içeriği e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'teki kullanıcı posta kutularına aktarır.

XIP kaynak verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken XIP bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-the-xip-source-data"></a>XIP kaynak verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te XIP kaynak verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![XIP kaynak verileri için iş akışı arşivleme.](../media/XIPConnectorWorkflow.png)

1. Kuruluşunuz bir XIP sitesi ayarlamak ve yapılandırmak için XIP kaynağıyla çalışır.

2. 24 saatte bir XIP kaynak öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca içeriği e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz XIP bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen ileti öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **XIP** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her kaynak öğe, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- XIP bağlayıcısını 1. Adımda oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-xip-connector"></a>1. Adım: XIP bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve XIP kaynak verileri için bir bağlayıcı oluşturmaktır.

1. [https://compliance.microsoft.com](https://compliance.microsoft.com/) Adresine gidin ve **Veri bağlayıcıları** \> **XIP'ye** tıklayın.

2. **XIP** ürün açıklaması sayfasında **Yeni bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-xip-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde XIP bağlayıcısını yapılandırma

İkinci adım, Merge1 sitesinde XIP bağlayıcısını yapılandırmaktır. XIP bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XIP%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **XIP kullanıcılarını Microsoft 365 kullanıcıları ile eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. XIP kaynak öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcısı ile ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-xip-connector"></a>4. Adım: XIP bağlayıcısını izleme

XIP bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından **XIP** bağlayıcısını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.