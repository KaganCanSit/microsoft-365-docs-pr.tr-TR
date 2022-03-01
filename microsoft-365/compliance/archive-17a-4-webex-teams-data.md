---
title: Cisco Webex verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Cisco Webex verilerini aynı dosyada içeri aktarma ve arşivlemek için 17a-4 Cisco Webex DataParser bağlayıcısı ayarlamayı ve Microsoft 365.
ms.openlocfilehash: ee3e5cc3c5f5ea24588b3799073c2af73e66aa96
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021522"
---
# <a name="set-up-a-connector-to-archive-cisco-webex-data"></a>Cisco Webex verilerini arşivlemek için bağlayıcı ayarlama

17a-4 LLC'den [Cisco Webex DataParser'ı](https://www.17a-4.com/webex-dataparser/) kullanarak Cisco Webex platformundan kendi iş yeri veya kuruluşunun kullanıcı posta kutularına veri aktarın Microsoft 365 arşivlendi. DataParser'da, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri başka bir öğeye içeri aktaran bir Cisco Webex Microsoft 365. Cisco Webex DataParser bağlayıcısı, Cisco Webex verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri aynı Microsoft 365.

Cisco Webex verileri kullanıcı posta kutularında depolanıyorsa, mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Web'de verileri içeri aktararak ve arşivlenen Cisco Webex Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-webex-data"></a>Cisco Webex verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Cisco Webex verilerini aynı dosyada arşivlemek için veri bağlayıcısı Microsoft 365.

![Cisco WebEx verileri için 17a-4 arasında iş akışı arşivleme.](../media/WebexTeamsDataParserConnectorWorkflow.png)

1. Your organization works with 17a-4 to set up and configure the Cisco Webex DataParser.

2. Düzenli aralıklarla Cisco Webex öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Dosyada oluştursanız bile Cisco Webex DataParser bağlayıcısı Microsoft 365 uyumluluk merkezi DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **Cisco Webex DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Cisco Webex öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Cisco Webex öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Cisco Webex DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, aynı dosyada Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-cisco-webex-dataparser-connector"></a>1. Adım: Cisco Webex DataParser bağlayıcısı ayarlama

İlk adım, sayfada Veri bağlayıcıları sayfasına erişmek ve Cisco Webex Microsoft 365 uyumluluk merkezi için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri **bağlayıcılarıCisco** > <https://compliance.microsoft.com> **WebEx DataParser'a gidin ve tıklayın**.

2. **Cisco Webex DataParser ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve Cisco Webex DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-cisco-webex-dataparser-connector"></a>2. Adım: Cisco Webex DataParser bağlayıcıyı yapılandırma

Cisco Webex DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Cisco Webex DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-cisco-webex-dataparser-connector"></a>4. Adım: Cisco Webex DataParser bağlayıcılarını izleme

Cisco Webex DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz Cisco Webex DataParser bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
