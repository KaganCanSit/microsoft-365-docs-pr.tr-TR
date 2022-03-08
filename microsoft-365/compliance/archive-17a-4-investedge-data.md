---
title: Verilerinizi Arşivle'ye arşivlemek için bir bağlayıcı Microsoft 365
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
description: 17a-4 InvestEdge DataParser bağlayıcısı ayar kullanmayı ve bu bağlayıcıya Yatırım Yatırımlandı verilerini içeri aktarmayı ve Microsoft 365.
ms.openlocfilehash: 5ee98f1bd4800685160bf77d5bcbc13ca4fe6c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318319"
---
# <a name="set-up-a-connector-to-archive-investedge-data"></a>YatırımEdge verilerini arşivlemek için bir bağlayıcı ayarlama

17a-4 LLC'den [InvestEdge DataParser'ı](https://www.17a-4.com/investedge-dataparser/) kullanarak, verilerinizi InvestEdge'den kendi Microsoft 365 aktarın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaran bir InvestEdge Microsoft 365. InvestEdge DataParser bağlayıcısı, InvestEdge verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365.

InvestEdge verileri kullanıcı posta kutularında depolandıktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktarma ve arşivlemek için bir InvestEdge bağlayıcısı kullanmak Microsoft 365 kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-investedge-data"></a>Yatırım Verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Veri Bağlayıcısı kullanarak Verilerin Arşivini Arşivleme işlemi Microsoft 365.

![17a-4'te yatırıldı verileri için iş akışı arşivleme.](../media/InvestEdgeDataParserConnectorWorkflow.png)

1. Kuruluşlarınız, InvestEdge DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli aralıklarla, Yatırım Yapılan öğeler DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Veri Kaynağı'Microsoft 365 uyumluluk merkezi oluşturmış olduğunuz InvestEdge DataParser bağlayıcısı, DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında, **Gelen Kutusu klasöründe investEdge DataParser** adlı bir alt klasör oluşturulur ve YatırımEdge öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her InvestEdge öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda InvestEdge DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-investedge-dataparser-connector"></a>1. Adım: InvestEdge DataParser bağlayıcısı ayarlama

İlk adım, çalışma sayfasındaki Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Yatırıldı verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıInvestEdge <https://compliance.microsoft.com>  > **DataParser'a gidin ve bu öğeye tıklayın**.

2. **InvestEdge DataParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve InvestEdge DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-investedge-dataparser-connector"></a>2. Adım: InvestEdge DataParser bağlayıcılarını yapılandırma

InvestEdge DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

InvestEdge DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-investedge-dataparser-connector"></a>4. Adım: InvestEdge DataParser bağlayıcılarını izleme

InvestEdge DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu çalışma Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz InvestEdge DataParser bağlayıcılarını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
