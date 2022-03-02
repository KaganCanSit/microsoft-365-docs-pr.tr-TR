---
title: Verileri tek bir dosyada SQL için bağlayıcıyı Microsoft 365
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
description: Bir 17a-4 veri bağlayıcısı ayarlamayı ve SQL veri kaynağında verileri içeri SQL arşivlemeyi Microsoft 365.
ms.openlocfilehash: d233ea9d843599613a41385c09ef4aaced14254f
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021542"
---
# <a name="set-up-a-connector-to-archive-sql-data"></a>Verilerinizi arşivlemek için bağlayıcıyı SQL ayarlama

SQL veritabanındaki verileri SQL veritabanındaki kullanıcı posta kutularına içeri ve arşivlemek için SQL [DataParser'ı](https://www.17a-4.com/sql-dataparser/) 17a-4 LLC Microsoft 365 kullanın. DataParser' SQL üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaran bir Microsoft 365. Yeni SQL DataParser bağlayıcısı, SQL verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365.

Kullanıcı SQL kutularında veriler depo kullandıktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. SQL'da verileri içeri aktarma ve arşivlemek için Microsoft 365 bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-sql-data"></a>Verileri arşivlemeye SQL genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı içinde yer alan verileri arşivlemek SQL kullanma Microsoft 365.

![17a-4 SQL için iş akışı arşivleme.](../media/SQLDatabaseDataParserConnectorWorkflow.png)

1. Verileriniz DataParser'ı ayarlamak ve yapılandırmak için, 17a-4 SQL çalışır.

2. Düzenli aralıklarla, SQL DataParser tarafından toplanan öğeler. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Veri SQL VeriParser bağlayıcısı Microsoft 365 uyumluluk merkezi DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma bağlar.

4. Kullanıcı posta kutularında **SQL DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve SQL bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her SQL öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda SQL DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, Exchange Online'te Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-sql-dataparser-connector"></a>1. Adım: DataParser bağlayıcısı SQL ayarlama

İlk adım, ana sayfada Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi verileri için bir 17a-4 SQL oluşturmaktır.

1. Veri Bağlayıcıları'ne <https://compliance.microsoft.com> **gidin ve ardından VeriParser** >  **SQL tıklayın**.

2. **VeriParser SQL açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve VeriParser bağlantı SQL adımları tamamlayın.

## <a name="step-2-configure-the-sql-dataparser-connector"></a>2. Adım: SQL DataParser bağlayıcıyı yapılandırma

DataParser bağlayıcısı için gereken bağlayıcıyı yapılandırmak için 17a-4 SQL ile çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Yeni SQL DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak kendi Microsoft 365.

## <a name="step-4-monitor-the-sql-dataparser-connector"></a>4. Adım: DataParser SQL izleme

DataParser bağlayıcısı SQL, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve SQL özellikleri ve bağlayıcıyla ilgili bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz VeriParser bağlayıcısı öğesini seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.