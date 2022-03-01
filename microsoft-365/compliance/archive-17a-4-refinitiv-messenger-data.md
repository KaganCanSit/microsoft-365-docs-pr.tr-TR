---
title: Refinitiv E ayrıca Messenger verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Bu verileri aynı dosyada içeri aktarma ve arşivlemek için 17a-4 Refinitiv E ayrıca Messenger DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: 142cd5afa1c79c0a73f0ee810056ce2fb09134a5
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021423"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>Refinitiv E ilgili Messenger verilerini arşivlemek için bağlayıcı ayarlama

[Refinitiv Evitn Messenger DataParser'ı](https://www.17a-4.com/refinitiv-messenger-dataparser/) 17a-4 LLC'den başvinitiv E bukarak Messenger'dan kullanıcı posta kutularına içeri aktarma ve Microsoft 365 kullanın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri kaynakta içeri aktararak kaynak koda aktaran bir Refinitiv E belirli bir Messenger Microsoft 365. Refinitiv Evitn Messenger DataParser bağlayıcısı Refinitiv E kutunuzu Messenger verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri kullanıcı posta kutularına Microsoft 365.

Refinitiv E hem Messenger verileri kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri, bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Refinitiv Evitn Messenger bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurumnizin resmi ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>Refinitiv E burcici Messenger verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Refinitiv Evrinik Messenger verilerini arşivleyen bir veri bağlayıcısı kullanma işlemi Microsoft 365.

![Refinitiv E refinitiv Messenger verileri için 17a-4'te iş akışı arşivleme.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. Organizasyonunız Refinitiv E ayrıca Messenger DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak, Refinitiv Evrizan Messenger öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'te oluşturmakta istediğiniz Refinitiv Evitn Messenger DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Refinitiv E ayrıca messenger DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Refinitiv E bu klasöre Messenger öğeleri aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Refinitiv Evitn Messenger öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Hesap oluşturmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). 1. Adımda bağlayıcıyı  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Refinitiv E herhangi bir Messenger DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>1. Adım: Refinitiv E ilgili Messenger DataParser bağlayıcısı ayarlama

İlk adım, ana sayfada Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Refinitiv E öncelikle Messenger verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıRefinitiv  > <https://compliance.microsoft.com>**Ehinn Messenger DataParser'a gidin ve tıklayın**.

2. **Refinitiv Evitn Messenger DataParser ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Refinitiv Ehinn Messenger DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>2. Adım: Refinitiv E belirli bir Messenger DataParser bağlayıcısı yapılandırma

Refinitiv E belirli bir Messenger DataParser bağlayıcısı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Refinitiv Evitn Messenger DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>4. Adım: Refinitiv E burak Messenger DataParser bağlayıcılarını izleme

Refinitiv E herhangi bir Messenger DataParser bağlayıcısı oluşturduktan sonra, bağlayıcının durumunu ilgili bağlayıcının Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntülemek için oluşturduğunuz Refinitiv E ayrıca Messenger DataParser bağlayıcılarını seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
