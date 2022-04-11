---
title: ServiceNow 17a-4 DataParser verilerini Microsoft 365'de arşivleme için bağlayıcı ayarlama
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
description: ServiceNow verilerini Microsoft 365 içeri aktarmak ve arşivleme amacıyla 17a-4 ServiceNow DataParser bağlayıcısını ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 23bc0e27aeffba5f215414ea51e9195040c7da47
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761571"
---
# <a name="set-up-a-connector-to-archive-data-from-servicenow"></a>ServiceNow'dan verileri arşivleme için bağlayıcı ayarlama

ServiceNow'dan Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına verileri içeri aktarmak ve arşivlemek için 17a-4 LLC'deki [ServiceNow DataParser'ı](https://www.17a-4.com/dataparser/) kullanın. DataParser, üçüncü taraf veri kaynağındaki öğeleri yakalamak ve bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir ServiceNow bağlayıcısı içerir. ServiceNow DataParser bağlayıcısı ServiceNow verilerini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır.

ServiceNow verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için ServiceNow bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-servicenow-data"></a>ServiceNow verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakışta ServiceNow verilerini Microsoft 365'de arşivleme amacıyla veri bağlayıcısı kullanma işlemi açıklanmaktadır.

![17a-4'ten ServiceNow verileri için arşivleme iş akışı.](../media/ServiceNowDataParserConnectorWorkflow.png)

1. Kuruluşunuz ServiceNow DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. ServiceNow öğeleri düzenli olarak DataParser tarafından toplanır. DataParser ayrıca iletinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi oluşturduğunuz ServiceNow DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Kullanıcı posta kutularında **ServiceNow DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve ServiceNow öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her ServiceNow öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC](https://www.17a-4.com/contact/) ile iletişime geçin. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda ServiceNow DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-a-servicenow-dataparser-connector"></a>1. Adım: ServiceNow DataParser bağlayıcısı ayarlama

İlk adım, Microsoft 365 uyumluluk merkezi Veri bağlayıcıları sayfasına erişmek ve ServiceNow verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri **bağlayıcılarıServiceNow DataParser'a** > <https://compliance.microsoft.com> gidin ve tıklayın.

2. **ServiceNow DataParser** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. 17a-4 hesabınızda oturum açın ve ServiceNow DataParser bağlantı sihirbazındaki adımları tamamlayın.

## <a name="step-2-configure-the-servicenow-dataparser-connector"></a>2. Adım: ServiceNow DataParser bağlayıcısını yapılandırma

ServiceNow DataParser bağlayıcısını yapılandırmak için 17a-4 Desteği ile çalışın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

ServiceNow DataParser bağlayıcısı, verileri Microsoft 365 içeri aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-servicenow-dataparser-connector"></a>4. Adım: ServiceNow DataParser bağlayıcısını izleme

ServiceNow DataParser bağlayıcısı oluşturduktan sonra bağlayıcının durumunu Microsoft 365 uyumluluk merkezi görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntülemek için oluşturduğunuz ServiceNow DataParser bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
