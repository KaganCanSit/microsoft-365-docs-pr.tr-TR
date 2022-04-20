---
title: Microsoft 365'da Fuze verilerini arşivleye bağlayıcı ayarlama
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
description: 17a-4 Fuze DataParser bağlayıcısını ayarlamayı ve kullanarak Microsoft 365'de Fuze verilerini içeri aktarmayı ve arşivlemeyi öğrenin.
ms.openlocfilehash: a1acd9462aa3497d3717219787cb9b9cd8f15cc3
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940873"
---
# <a name="set-up-a-connector-to-archive-fuze-data"></a>Fuze verilerini arşivleye bağlayıcı ayarlama

17a-4 LLC'deki [Fuze DataParser'ı](https://www.17a-4.com/fuze-dataparser/) kullanarak verileri fuze'den Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarın ve arşivleyebilirsiniz. DataParser, üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri Microsoft 365'e aktarmak için yapılandırılmış bir Fuze bağlayıcısı içerir. Fuze DataParser bağlayıcısı, Fuze verilerini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır.

Fuze verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için bir Fuze bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-fuze-data"></a>Fuze verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'da Fuze verilerini arşivlerken veri bağlayıcısı kullanma işlemini açıklar.

![17a-4 arasındaki Fuze verileri için arşivleme iş akışı.](../media/FuzeDataParserConnectorWorkflow.png)

1. Kuruluşunuz, Fuze DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak, Fuze öğeleri DataParser tarafından toplanır. DataParser ayrıca iletinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Microsoft Purview uyumluluk portalında oluşturduğunuz Fuze DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Kullanıcı posta kutularında Gelen Kutusu klasöründeki **Fuze DataParser** adlı bir alt klasör oluşturulur ve Fuze öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Fuze öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC](https://www.17a-4.com/contact/) ile iletişime geçin. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda Fuze DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-a-fuze-dataparser-connector"></a>1. Adım: Fuze DataParser bağlayıcısı ayarlama

İlk adım, uyumluluk portalındaki Veri bağlayıcıları sayfasına erişmek ve Fuze verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. **Veri bağlayıcılarıYeni VeriParser'a** > <https://compliance.microsoft.com> gidin ve **tıklayın**.

2. **Fuze DataParser** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. 17a-4 hesabınızda oturum açın ve Fuze DataParser bağlantı sihirbazındaki adımları tamamlayın.

## <a name="step-2-configure-the-fuze-dataparser-connector"></a>2. Adım: Fuze DataParser bağlayıcısını yapılandırma

Fuze DataParser bağlayıcısını yapılandırmak için 17a-4 Desteği ile çalışın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Fuze DataParser bağlayıcısı, verileri Microsoft 365 içeri aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-fuze-dataparser-connector"></a>4. Adım: Fuze DataParser bağlayıcısını izleme

Bir Fuze DataParser bağlayıcısı oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntülemek için oluşturduğunuz Veri Ayrıştırıcı bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
