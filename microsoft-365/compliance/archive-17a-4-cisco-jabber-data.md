---
title: Cisco Cisco Ciscober verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Cisco Cisco Ciscober verilerini aynı dosyada içeri aktarma ve arşivlemek için 17a-4 Cisco Cisco Ciscober DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: 4236b64c805a2524eac080663cdf4fe1e77a595a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329231"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>Cisco Cisco Ciscober verilerini arşivlemek için bağlayıcı ayarlama

Cisco Cisco Ciscober'den, 17a-4 LLC'den Cisco Cisco Ciscober [VeriParser'i](https://www.17a-4.com/jabber-dataparser/) kullanarak verileri iş yer Microsoft 365 alın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaracak şekilde yapılandırılmış bir Cisco Cisco Microsoft 365. Cisco Ciscober DataParser bağlayıcısı, Cisco Cisco Ciscober verilerini e-posta iletisi biçimine dönüştürür ve bu öğeleri aynı Microsoft 365.

Cisco Cisco Ciscober verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Cisco Cisco Ciscober bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 düzenlemeler ve devlet ilkeleriyle uyumlu kalmasınıza yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Cisco Ciscober verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Cisco Cisco Ciscober verilerini aynı dosyada arşivlemek için veri bağlayıcısı Microsoft 365.

![Cisco Cisco Ciscober verileri için 17a-4 arasında arşivleme iş akışı.](../media/CiscoJabberDataParserConnectorWorkflow.png)

1. Organizasyonunız Cisco Cisco Ciscober DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak Cisco Cisco Ciscober öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Dosyada oluştursanız bile Cisco Cisco Ciscober DataParser bağlayıcısı, DataPars Microsoft 365 uyumluluk merkezi er'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Cisco Cisco Ciscober DataParser** adlı bir Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Cisco Cisco Ciscober öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Tüm Cisco Cisco Ciscober öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Cisco Cisco Ciscober DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-cisco-jabber-dataparser-connector"></a>1. Adım: Cisco Cisco Ciscober DataParser bağlayıcısı ayarlama

İlk adım, dosyanın Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Cisco Cisco Ciscober verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıCiscoBer <https://compliance.microsoft.com>  > **DataParser'a gidin ve tıklayın**.

2. **Cisco Cisco CiscoBer DataParser ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Cisco Cisco Ciscober DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-cisco-jabber-dataparser-connector"></a>2. Adım: Cisco Cisco Ciscober DataParser bağlayıcılarını yapılandırma

Cisco Cisco Ciscober DataParser bağlayıcılarını yapılandırmak için 17a-4 Desteği ile birlikte çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Cisco Ciscober DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-cisco-jabber-dataparser-connector"></a>4. Adım: Cisco Cisco Ciscober DataParser bağlayıcılarını izleme

Cisco Cisco Cisco DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz Cisco Ciscober DataParser bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
