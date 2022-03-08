---
title: Verileri başka bir öğede arşivlemek için bağlayıcıyı Microsoft 365
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
description: Verileri başka bir dosyada içeri aktarma ve arşivlemek için 17a-4 Fuze DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: a5ee335876e6f74487c919930126b1cac70e8df2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316275"
---
# <a name="set-up-a-connector-to-archive-fuze-data"></a>Fuze verilerini arşivlemek için bağlayıcı ayarlama

17a-4 LLC'den [Füze VeriParser'i](https://www.17a-4.com/fuze-dataparser/) kullanarak, verileri Fuze'dan kendi Microsoft 365 alın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaracak şekilde yapılandırılmış bir Donuz Microsoft 365. Dondur DataParser bağlayıcısı, Verileri dondurarak e-posta ileti biçimine dönüştürür ve bu öğeleri kullanıcı posta kutularına Microsoft 365.

Dondur verileri kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktarın ve arşiv Microsoft 365 Dondur bağlayıcısı kullanmak, kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmada yardımcı olabilir.

## <a name="overview-of-archiving-fuze-data"></a>Fuze verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Verileri kendi verilerinize arşivlemek için veri bağlayıcısı Microsoft 365.

![17a-4'te Verileri Dondur için arşivleme iş akışı.](../media/FuzeDataParserConnectorWorkflow.png)

1. Organizasyonunız, Fuze DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli aralıklarla, Dondur öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. VeriParser'de oluştursanız bile Dondur Microsoft 365 uyumluluk merkezi DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma bağlar.

4. Kullanıcı posta kutularında **Fuze DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Füze öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Donze öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Fuze DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-fuze-dataparser-connector"></a>1. Adım: Fuze DataParser bağlayıcısı ayarlama

İlk adım, sayfada Veri bağlayıcıları sayfasına erişmek ve Microsoft 365 uyumluluk merkezi için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıYazdır'a <https://compliance.microsoft.com> **gidin** >  **ve bu bağlayıcılara tıklayın**.

2. **VeriParser ürün açıklamasını Dondur** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Fuze DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-fuze-dataparser-connector"></a>2. Adım: Fuze DataParser bağlayıcıyı yapılandırma

Fuze DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Fuze DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-fuze-dataparser-connector"></a>4. Adım: Fuze DataParser bağlayıcılarını izleme

Füstür DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu görünüm Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra, oluşturduğunuz Fuze DataParser bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
