---
title: Bloomberg verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Bloomberg verilerini aynı dosyada içeri aktararak arşivlemek için 17a-4 Bloomberg DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: 1a3efc520e4427d49329b1c04dc6fe96e560d298
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021545"
---
# <a name="set-up-a-connector-to-archive-bloomberg-data"></a>Bloomberg verilerini arşivlemek için bağlayıcı ayarlama

[Bloomberg DataParser'ı](https://www.17a-4.com/Bloomberg-dataparser/) 17a-4 LLC'den Bloomberg'den kendi Microsoft 365 için kullanın. DataParser'da üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri üçüncü taraf veri kaynağına aktaran bir Bloomberg bağlayıcısı Microsoft 365. Bloomberg DataParser bağlayıcısı, Bloomberg verilerini e-posta iletisi biçimine dönüştürür ve bu öğeleri kendi posta kutularına Microsoft 365.

Bloomberg verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Bloomberg bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365 düzenlemelere uyumlu kalmasınıza yardımcı olabilir.

## <a name="overview-of-archiving-bloomberg-data"></a>Bloomberg verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Bloomberg verilerini aynı dosyada arşivlemek için veri bağlayıcısı Microsoft 365.

![Bloomberg verileri için 17a-4 arasında iş akışı arşivleme.](../media/BloombergDataParserConnectorWorkflow.png)

1. Organizasyonunız Bloomberg DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak, Bloomberg öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta sizin açtığınız Bloomberg DataParser bağlayıcısı, DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Bloomberg DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Bloomberg öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Bloomberg öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Bloomberg DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, çalışma sayfalarındaki Posta Kutusu İçeri/Dışarı Aktarma rolüne Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-bloomberg-dataparser-connector"></a>1. Adım: Bloomberg DataParser bağlayıcısı ayarlama

İlk adım, çalışma sayfasındaki Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Bloomberg verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıBloomberg <https://compliance.microsoft.com>  > **DataParser'a gidin ve tıklayın**.

2. **Bloomberg DataParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Bloomberg DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-bloomberg-dataparser-connector"></a>2. Adım: Bloomberg DataParser bağlayıcılarını yapılandırma

Bloomberg DataParser bağlayıcısı'nın yapılandırılması için 17a-4 Desteği ile çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Bloomberg DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-bloomberg-dataparser-connector"></a>4. Adım: Bloomberg DataParser bağlayıcılarını izleme

Bloomberg DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz Bloomberg DataParser bağlayıcılarını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
