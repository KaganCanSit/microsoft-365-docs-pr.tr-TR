---
title: FX verilerini aynı veri kaynağında Bağlan için 17a-4 DataParser bağlayıcısı Microsoft 365
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
description: FX veri içeri aktarma ve arşivlemek için 17a-4 FX Bağlan DataParser bağlayıcısı ayarlamayı ve Bağlan veri Microsoft 365.
ms.openlocfilehash: 129d5f6836d8cf447b77bf068a4c6b5f33b33703
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311809"
---
# <a name="set-up-a-connector-to-archive-data-from-fx-connect"></a>FX veri kaynağından verileri arşivlemek için bağlayıcıyı Bağlan

FX Bağlan'dan kendi Microsoft 365 posta kutularına veri almak ve arşivlemek için [FX Bağlan DataParser'ı](https://www.17a-4.com/dataparser-roadmap/) 17a-4 LLC Microsoft 365 kullanın. DataParser'da, üçüncü taraf bir Bağlan veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaran bir FX Microsoft 365. FX Bağlan DataParser bağlayıcısı FX Bağlan verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365.

FX Bağlan verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. FX Bağlan bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-fx-connect-data"></a>FX verilerini arşivlemeye Bağlan genel bakış

Aşağıdaki genel bakış makalesinde, verileri kendi verilerinize göre arşivlemek için veri Bağlan kullanma Microsoft 365.

![FX verileri için iş akışı Bağlan 17a-4 arasında olabilir.](../media/FXConnectDataParserConnectorWorkflow.png)

1. Kuruluş, FX veri kümesi DataParser'ı ayarlamak ve yapılandırmak için 17a-4 Bağlan çalışır.

2. Düzenli aralıklarla, FX Bağlan DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Bulutta Bağlan FX VeriParser bağlayıcısı DataParser'a bağlanır ve Microsoft 365 uyumluluk merkezi iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma bağlar.

4. Kullanıcı posta kutularında **FX Bağlan DataParser** adlı Bir Gelen Kutusu klasöründe bir alt klasör oluşturulur ve FX Bağlan öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her FX Bağlan bu özelliği içerir; bu özellik her katılımcının e-posta adresiyle doldurulur.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda FX Bağlan VeriParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-fx-connect-dataparser-connector"></a>1. Adım: FX VeriParser Bağlan ayarlama

İlk adım, ana sayfada Veri bağlayıcıları sayfasına erişmek ve FX Microsoft 365 uyumluluk merkezi verileri için bir 17a-4 bağlayıcısı Bağlan oluşturmaktır.

1. Veri BağlayıcılarıFX <https://compliance.microsoft.com> **ve DataParser'a** >  **Bağlan tıklayın**.

2. FX Veri **Bağlan açıklaması sayfasında** Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve FX VeriParser bağlantı Bağlan adımları tamamlayın.

## <a name="step-2-configure-the-fx-connect-dataparser-connector"></a>2. Adım: FX veri Bağlan bağlayıcıyı yapılandırma

FX VeriParser bağlayıcısı verilerini yapılandırmak için 17a-4 Bağlan ile çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

FX Bağlan DataParser bağlayıcısı, verileri diğer kullanıcılara aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle Microsoft 365.

## <a name="step-4-monitor-the-fx-connect-dataparser-connector"></a>4. Adım: FX Veri Bağlan bağlayıcısı izleme

FX VeriParser Bağlan oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz FX Bağlan DataParser bağlayıcısı öğesini seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
