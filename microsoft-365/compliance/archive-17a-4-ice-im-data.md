---
title: Buz buzları ve Sohbet verilerini Bağlan için bağlayıcıyı Microsoft 365
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
description: 17a-4 ICE Bağlan Chat DataParser bağlayıcısı ayar kullanmayı ve ayarlamayı ve kullanmayı öğrenin ICE Bağlan'de sohbet verilerini içeri Microsoft 365.
ms.openlocfilehash: 632426422bd8f9db984b66fdea08276b7345441c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021436"
---
# <a name="set-up-a-connector-to-archive-ice-connect-chat-data"></a>Sohbet verilerini dondurmak için Bağlan ayarlama

ICE [DataParser'ı](https://www.17a-4.com/ice-dataparser/) 17a-4 LLC'den ICE Bağlan'dan içeri aktararak ve arşivlerken Microsoft 365 kullanıcı posta kutularıyla sohbet edin. DataParser, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri üçüncü taraf veri kaynağına aktaran bir ICE Sohbet Microsoft 365. ICE DataParser bağlayıcısı, ICE Bağlan Sohbet verilerini e-posta iletisi biçimine dönüştürür ve bu öğeleri aynı Microsoft 365.

ICE Bağlan Sohbet verileri kullanıcı posta kutularında depolanıyorsa, Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Ice DataParser bağlayıcısı kullanarak verileri başka bir dosyada içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-ice-chat-data"></a>ICE Sohbet verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış veri bağlayıcısı kullanarak ICE'i arşivleme ve Sohbet verilerini Bağlan veri bağlayıcısı kullanma Microsoft 365.

![BUZ 17a-4 Bağlan Sohbet verileri için iş akışı arşivleme.](../media/ICEChatDataParserConnectorWorkflow.png)

1. Ice DataParser'ı ayarlamak ve yapılandırmak için, organizasyonunız 17a-4 ile çalışır.

2. Düzenli aralıklarla ICE Bağlan Sohbet öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Veri Kaynağı'Microsoft 365 uyumluluk merkezi ice dataparser bağlayıcısı, DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Kullanıcı posta kutularında **ICE DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve BUZ Bağlan Sohbet öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Sohbet Bağlan tüm ICE öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda ICE DataParser bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, veri kaynağında Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-an-ice-dataparser-connector"></a>1. Adım: ICE DataParser bağlayıcısı ayarlama

İlk adım, videonun Veri bağlayıcıları sayfasına erişmek ve Microsoft 365 uyumluluk merkezi Sohbet verileri için bir 17a-4 bağlayıcısı Bağlan oluşturmaktır.

1. Veri bağlayıcılarıICE <https://compliance.microsoft.com> **DataParser'a** >  gidin **ve bu öğeye tıklayın**.

2. **ICE DataParser ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve ICE DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-ice-dataparser-connector"></a>2. Adım: ICE DataParser bağlayıcıyı yapılandırma

ICE DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

ICE DataParser bağlayıcısı, verileri veri kaynağına aktarmadan Microsoft 365 otomatik olarak kendi e-posta adresleriyle Microsoft 365.

## <a name="step-4-monitor-the-ice-dataparser-connector"></a>4. Adım: ICE DataParser bağlayıcılarını izleme

BIR ICE DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve oluşturduğunuz ICE DataParser bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
