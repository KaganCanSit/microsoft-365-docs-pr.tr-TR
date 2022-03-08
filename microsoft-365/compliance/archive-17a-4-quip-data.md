---
title: Aynı dosyada Quip verilerini arşivlemek için bağlayıcıyı Microsoft 365
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
description: Quip verilerini içeri aktarma ve burada arşivlemek için 17a-4 Quip DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: c3b781fcf7027bd3bdcd57db0e23165a3c33c940
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318291"
---
# <a name="set-up-a-connector-to-archive-quip-data"></a>Quip verilerini arşivlemek için bağlayıcı ayarlama

Quip'te yer alan verileri kendi Microsoft 365 posta kutularına içeri aktarmak ve arşivlemek için 17a-4 LLC'den [Quip DataParser'ı](https://www.17a-4.com/quip-dataparser/) kullanın. DataParser, üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaran bir Quip Microsoft 365. Quip DataParser bağlayıcısı, Quip verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri kendi posta kutularına Microsoft 365.

Quip verileri kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir e-postada içeri aktararak veya Microsoft 365 için Quip bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-quip-data"></a>Quip verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Veri Bağlayıcısı kullanarak Sessize'ye veri arşivleme işlemi Microsoft 365.

![17a-4'den Quip verileri için arşivleme iş akışı.](../media/QuipDataParserConnectorWorkflow.png)

1. Organizasyonunız Quip DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli aralıklarla, Quip öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız bile Quip DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Quip DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Quip öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Quip öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Quip DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-quip-dataparser-connector"></a>1. Adım: Quip DataParser bağlayıcısı ayarlama

İlk adım, tablo sayfasındaki Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Quip verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıQuip  > **DataParser'a gidin ve bu bağlayıcılara tıklayın**.<https://compliance.microsoft.com>

2. Quip **DataParser ürün açıklaması** sayfasında Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Quip DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-quip-dataparser-connector"></a>2. Adım: Quip DataParser bağlayıcıyı yapılandırma

Quip DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Quip DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-quip-dataparser-connector"></a>4. Adım: Quip DataParser bağlayıcılarını izleme

Quip DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra, oluşturduğunuz Quip DataParser bağlayıcısına tıklarsanız bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
