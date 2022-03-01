---
title: Verileri tek bir dosyada arşivlemek için bir VeriParser bağlayıcısı Microsoft 365
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
description: 17a-4 Her Zaman VeriParser bağlayıcısı ayar kullanmayı ve bu bağlayıcıyı kullanarak Verilerinizi Başka bir alanda içeri aktarmayı ve Microsoft 365.
ms.openlocfilehash: b949b646c227f26575182d173f1d34d54f40b3ed
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021499"
---
# <a name="set-up-a-connector-to-archive-data-from-symphony"></a>Zaman'dan verileri arşivlemek için bağlayıcı ayarlama

17a-4 LLC'den [VeriParser'ı](https://www.17a-4.com/Symphony-dataparser/) kullanarak, Veyalçın iletişim verilerini kendi Microsoft 365 aktarın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktararak üçüncü taraf veri kaynağına aktaran bir Microsoft 365. Sol VeriParser bağlayıcısı, Syk verisini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri daha sonra da kullanıcı posta kutularına Microsoft 365.

Güneş verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak veya arşiv Microsoft 365 bir Öğe bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-symphony-data"></a>Skpye verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Açık bir tabloda, Bu verileri arşivlemek için veri bağlayıcısı Microsoft 365.

![17a-4'e kadar olan Veri verileri için arşivleme iş akışı.](../media/SymphonyDataParserConnectorWorkflow.png)

1. Organization works with 17a-4 to set and configure the VeriParser.

2. Düzenli aralıklarla, Her biri DataParser tarafından Mırçın öğeleri toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Bu dosyada sizin Microsoft 365 uyumluluk merkezi VeriParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **VeriParer** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Bu Öğeler öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Bir Öğe, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda VeriParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, veri kaynağında Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-symphony-dataparser-connector"></a>1. Adım: Her Zaman VeriParser bağlayıcısı ayarlama

İlk adım, dosyanın Veri bağlayıcıları sayfasına erişmek ve Microsoft 365 uyumluluk merkezi Için Bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıSym <https://compliance.microsoft.com>  > **öğesinin DataParser'a gidin ve bu öğeye tıklayın**.

2. **VeriParser ürün açıklaması sayfasında** Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve BilgiParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-symphony-dataparser-connector"></a>2. Adım: Her Zaman VeriParser bağlayıcısı'nın yapılandırılması

Her Bir VeriParser bağlayıcısı yapılandırmak için 17a-4 Desteği ile birlikte çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

VeriParser bağlayıcısı, verileri veri kaynağına aktarmadan Microsoft 365 otomatik olarak e-posta adresleriyle Microsoft 365.

## <a name="step-4-monitor-the-symphony-dataparser-connector"></a>4. Adım: Her Zaman VeriParser bağlayıcısı izleme

Her Zaman VeriParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından oluşturduğunuz Her VeriParser bağlayıcısı'nın bağlayıcı özellikleriyle ilgili bilgileri içeren açılır sayfayı görüntülemek için bu bağlayıcıyı seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
