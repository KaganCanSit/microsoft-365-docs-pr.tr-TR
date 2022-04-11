---
title: Cisco Jabber verilerini Microsoft 365'de arşivleme bağlayıcısı ayarlama
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
description: Cisco Jabber verilerini Microsoft 365 içeri aktarmak ve arşivleme amacıyla 17a-4 Cisco Jabber DataParser bağlayıcısını ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: eff37542d65d57dccf4bf0e2d53a87a77c182a3a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64762221"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>Cisco Jabber verilerini arşivleme amacıyla bağlayıcı ayarlama

17a-4 LLC'deki [Cisco Jabber DataParser'ı](https://www.17a-4.com/jabber-dataparser/) kullanarak Cisco Jabber'dan Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına verileri içeri aktarın ve arşivleyebilirsiniz. DataParser, üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir Cisco Jabber bağlayıcısı içerir. Cisco Jabber DataParser bağlayıcısı, Cisco Jabber verilerini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365 kullanıcı posta kutularına aktarır.

Cisco Jabber verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için Cisco Jabber bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Cisco Jabber verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakış, Cisco Jabber verilerini Microsoft 365'de arşivleme amacıyla veri bağlayıcısı kullanma işlemini açıklar.

![17a-4'ten Cisco Jabber verilerini arşivleme iş akışı.](../media/CiscoJabberDataParserConnectorWorkflow.png)

1. Kuruluşunuz Cisco Jabber DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak Cisco Jabber öğeleri DataParser tarafından toplanır. DataParser ayrıca iletinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi oluşturduğunuz Cisco Jabber DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Cisco Jabber DataParser** adlı bir alt klasör oluşturulur ve Cisco Jabber öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Cisco Jabber öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC](https://www.17a-4.com/contact/) ile iletişime geçin. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda Cisco Jabber DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-a-cisco-jabber-dataparser-connector"></a>1. Adım: Cisco Jabber DataParser bağlayıcısı ayarlama

İlk adım, Microsoft 365 uyumluluk merkezi Veri bağlayıcıları sayfasına erişmek ve Cisco Jabber verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. <https://compliance.microsoft.com> Adresine gidin ve **Veri bağlayıcılarıCisco** >  **Jabber DataParser'a** tıklayın.

2. **Cisco Jabber DataParser** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. 17a-4 hesabınızda oturum açın ve Cisco Jabber DataParser bağlantı sihirbazındaki adımları tamamlayın.

## <a name="step-2-configure-the-cisco-jabber-dataparser-connector"></a>2. Adım: Cisco Jabber DataParser bağlayıcısını yapılandırma

Cisco Jabber DataParser bağlayıcısını yapılandırmak için 17a-4 Desteği ile çalışın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Cisco Jabber DataParser bağlayıcısı, verileri Microsoft 365 içeri aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-cisco-jabber-dataparser-connector"></a>4. Adım: Cisco Jabber DataParser bağlayıcısını izleme

Cisco Jabber DataParser bağlayıcısı oluşturduktan sonra bağlayıcının durumunu Microsoft 365 uyumluluk merkezi görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz Cisco Jabber DataParser bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
