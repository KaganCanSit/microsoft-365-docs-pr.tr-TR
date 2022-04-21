---
title: Microsoft 365'da LivePerson Konuşma Bulutu verilerini arşivleye bir bağlayıcı ayarlama
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
description: LivePerson Konuşma Bulutu verilerini Microsoft 365'da içeri aktarmak ve arşiv etmek için 17a-4 LivePerson Konuşma Bulutu VeriSiparser bağlayıcısı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 215818fec6dc186e20e19fcf247193a0616676eb
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998120"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>LivePerson Konuşma Bulutu verilerini arşivleye bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[LivePerson Konuşma Bulutu'ndaki](https://www.17a-4.com/liveperson-dataparser/) verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için 17a-4 LLC'den LivePerson Konuşma Bulutu VeriSiParser'ı kullanın. DataParser, üçüncü taraf veri kaynağındaki öğeleri yakalamak ve bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir LivePerson Konuşma Bulutu bağlayıcısı içerir. LivePerson Konuşma Bulutu DataParser bağlayıcısı, verileri e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır.

Veriler kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için LivePerson Konuşma Bulutu bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>LivePerson Konuşma Bulutu verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakış, LivePerson Konuşma Bulutu verilerini Microsoft 365'de arşivlerken veri bağlayıcısı kullanma işlemini açıklar.

![17a-4'ten LivePerson Konuşma Bulutu verilerini arşivleme iş akışı.](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Kuruluşunuz LivePerson Conversational Cloud DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. LivePerson Konuşma Bulutu öğeleri düzenli olarak DataParser tarafından toplanır. DataParser ayrıca iletinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Microsoft Purview uyumluluk portalında oluşturduğunuz LivePerson Konuşma Bulutu DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Kullanıcı posta kutularında **LivePerson Conversational Cloud DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her öğe, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC](https://www.17a-4.com/contact/) ile iletişime geçin. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda LivePerson Konuşma Bulutu DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>1. Adım: LivePerson Konuşma Bulutu VerileriParser bağlayıcısı ayarlama

İlk adım, uyumluluk portalındaki Veri bağlayıcıları sayfasına erişmek ve LivePerson Konuşma Bulutu verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. **Veri bağlayıcılarıLivePerson** >  **Konuşma Bulutu VerileriParser'a**<https://compliance.microsoft.com> gidin ve tıklayın.

2. **LivePerson Conversational Cloud DataParser** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. 17a-4 hesabınızda oturum açın ve LivePerson Conversational Cloud DataParser bağlantı sihirbazındaki adımları tamamlayın.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>2. Adım: LivePerson Konuşma Bulutu VerileriParser bağlayıcısını yapılandırma

LivePerson Conversational Cloud DataParser bağlayıcısını yapılandırmak için 17a-4 Desteği ile çalışın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

LivePerson Conversational Cloud DataParser bağlayıcısı, verileri Microsoft 365 içeri aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>4. Adım: LivePerson Konuşma Bulutu VerileriParser bağlayıcısını izleme

LivePerson Conversational Cloud DataParser bağlayıcısı oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz LivePerson Konuşma Bulutu DataParser bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
