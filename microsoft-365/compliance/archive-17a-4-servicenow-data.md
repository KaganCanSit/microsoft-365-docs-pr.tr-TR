---
title: ServiceNow 17a-4 DataParser verilerini arşivlemek için bir bağlayıcı Microsoft 365
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
description: 17a-4 ServiceNow DataParser bağlayıcısı ayar kullanmayı ve bu bağlayıcıyı Kullanarak ServiceNow verilerini içeri aktarmayı ve Microsoft 365.
ms.openlocfilehash: 6fe10ffd8a5f850220b648c048c166415911a7d0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328911"
---
# <a name="set-up-a-connector-to-archive-data-from-servicenow"></a>ServiceNow'dan verileri arşivlemek için bağlayıcı ayarlama

17a-4 LLC'den [ServiceNow DataParser'ı](https://www.17a-4.com/dataparser/) kullanarak ServiceNow'daki verileri kendi Microsoft 365 aktarın. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaran bir ServiceNow Microsoft 365. ServiceNow DataParser bağlayıcısı ServiceNow verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri e-posta kutusunda kullanıcı posta Microsoft 365.

ServiceNow verileri kullanıcı posta kutularında depolanıyorsa, mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Bir ServiceNow bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-servicenow-data"></a>ServiceNow verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, ServiceNow verilerini arşivlemek için veri bağlayıcısı kullanma işlemi Microsoft 365.

![ServiceNow verileri için iş akışı arşivleme 17a-4.](../media/ServiceNowDataParserConnectorWorkflow.png)

1. Organizasyonunız ServiceNow DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak ServiceNow öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız bile ServiceNow DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **ServiceNow DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve ServiceNow öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her ServiceNow öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda ServiceNow DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-servicenow-dataparser-connector"></a>1. Adım: ServiceNow DataParser bağlayıcısı ayarlama

İlk adım, sitenin Veri bağlayıcıları sayfasına erişmek ve ServiceNow Microsoft 365 uyumluluk merkezi için bir 17a-4 bağlayıcısı oluşturmaktır.

1. **Veri bağlayıcılarıServiceNow** > <https://compliance.microsoft.com> **DataParser'a gidin ve tıklayın**.

2. **ServiceNow DataParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve ServiceNow DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-servicenow-dataparser-connector"></a>2. Adım: ServiceNow DataParser bağlayıcılarını yapılandırma

ServiceNow DataParser bağlayıcısı'nın yapılandırılması için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

ServiceNow DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-servicenow-dataparser-connector"></a>4. Adım: ServiceNow DataParser bağlayıcılarını izleme

ServiceNow DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından oluşturduğunuz ServiceNow DataParser bağlayıcılarını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
