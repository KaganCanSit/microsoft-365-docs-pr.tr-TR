---
title: Slack verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365
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
description: 17a-4 Slack DataParser bağlayıcısı ayar yapmayı ve bu bağlayıcıyı kullanarak Slack verilerini içeri aktarmayı ve Microsoft 365.
ms.openlocfilehash: bfc345b13992590b7a066dc6135a7432d4d267e1
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021419"
---
# <a name="set-up-a-connector-to-archive-slack-data"></a>Slack verilerini arşivlemek için bağlayıcı ayarlama

[DataParser'ı 17a-4 LLC'den](https://www.17a-4.com/slack-dataparser/) kullanarak Slack platformundan kendi Microsoft 365 posta kutularına veri aktarın ve arşivlendi. DataParser' üçüncü taraf bir veri kaynağından öğe yakalamak ve bu öğeleri başka bir kaynaktan içeri aktararak başka bir öğeye içeri aktaran bir Slack Microsoft 365. Slack DataParser bağlayıcısı, Slack verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri kendi posta kutularına Microsoft 365.

Slack verileri kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Slack bağlayıcısı kullanarak verileri kendi web'de içeri aktarın Microsoft 365 da, kurumnizin devlet ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-slack-data"></a>Slack verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Kendi Verileriniz'de Slack verilerini arşivlemek için veri bağlayıcısı Microsoft 365.

![17a-4'den Slack verileri için iş akışı arşivleme.](../media/SlackDataParserConnectorWorkflow.png)

1. Organizasyonunız Slack VeriParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli aralıklarla, Slack öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız bile Slack DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Slack DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Slack öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Slack öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Slack VeriParser bağlayıcısı oluşturan (ve 3. Adımda bunu tamamlayan) kullanıcı, Exchange Online'te Posta Kutusu İçeri/Dışarı Aktarma rolüne atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-slack-dataparser-connector"></a>1. Adım: Slack VeriParser bağlayıcısı ayarlama

İlk adım, ana sayfada Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi Slack verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıSlack <https://compliance.microsoft.com>  > **DataParser'a gidin ve tıklayın**.

2. **Slack VeriParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Slack VeriParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-slack-dataparser-connector"></a>2. Adım: Slack DataParser bağlayıcıyı yapılandırma

Slack DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışabilirsiniz.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Slack DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-slack-dataparser-connector"></a>4. Adım: Slack DataParser bağlayıcılarını izleme

Slack VeriParser bağlayıcısı oluşturdukta, bağlayıcının durumunu çalışma Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra, oluşturduğunuz Slack DataParser bağlayıcısı'nın bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
