---
title: Yakınlaştırma verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: 17a-4 Zoom DataParser bağlayıcısı ayar kullanmayı ve bu bağlayıcıyı kullanarak Verileri yakınlaştır'ı içeri aktarmayı ve Microsoft 365.
ms.openlocfilehash: 5159dcd02c9c1d5dccafe841a9945be744c81a64
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021497"
---
# <a name="set-up-a-connector-to-archive-zoom-data"></a>Yakınlaştırma verilerini arşivlemek için bağlayıcıyı ayarlama

17a-4 LLC'den [Zoom DataParser'ı](https://www.17a-4.com/dataparser/) kullanarak Yakınlaştır platformundan verileri kendi Microsoft 365 aktarın. DataParser, üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaran şekilde yapılandırılmış bir Microsoft 365. Zoom DataParser bağlayıcısı, Verileri yakınlaştır'ı e-posta ileti biçimine dönüştürür ve sonra bu öğeleri yakınlaştırılmış bir şekilde kullanıcı posta Microsoft 365.

Yakınlaştırma verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir e-postada içeri aktarıp Microsoft 365 yakınlaştırma bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-zoom-data"></a>Verileri yakınlaştırmak için arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Verileri yakınlaştır ve yakınlaştır'ı arşivlemek için veri bağlayıcısı Microsoft 365.

![17a-4'te verileri yakınlaştırmak için iş akışı arşivleme.](../media/ZoomDataParserConnectorWorkflow.png)

1. Zoom DataParser'ı ayarlamak ve yapılandırmak için, organizasyonunız 17a-4 ile çalışır.

2. Yakınlaştırma öğeleri düzenli olarak DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Dosya üzerinde oluştursanız bile Zoom DataParser bağlayıcısı Microsoft 365 uyumluluk merkezi DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarabilir.

4. Kullanıcı posta kutularında Yakınlaştır **VeriParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Yakınlaştır öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Yakınlaştırma öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Zoom DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-zoom-dataparser-connector"></a>1. Adım: Zoom DataParser bağlayıcısı ayarlama

İlk adım, sayfada Veri bağlayıcıları sayfasına erişmek ve Microsoft 365 uyumluluk merkezi için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıOom  > <https://compliance.microsoft.com>**DataParser'a gidin ve bu öğeye tıklayın**.

2. Zoom **DataParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Zoom DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-zoom-dataparser-connector"></a>2. Adım: Zoom DataParser bağlayıcıyı yapılandırma

Zoom DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Zoom DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-zoom-dataparser-connector"></a>4. Adım: Zoom DataParser bağlayıcılarını izleme

Zoom DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz Zoom DataParser bağlayıcılarını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
