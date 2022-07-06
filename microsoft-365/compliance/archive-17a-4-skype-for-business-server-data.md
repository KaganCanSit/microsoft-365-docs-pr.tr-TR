---
title: Microsoft 365'te Skype Kurumsal Sunucu verileri arşivleye bir bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Microsoft 365'te Skype Kurumsal Sunucu verilerini içeri aktarmak ve arşivlemek için 17a-4 Skype Kurumsal Sunucu DataParser bağlayıcısı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 9b503ea1305e7997d6a66ace0a402a9557d0cc31
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639324"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-server-data"></a>Skype Kurumsal Sunucu verilerini arşivleye bağlayıcı ayarlama

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına bir Skype Kurumsal Sunucu verileri içeri aktarmak ve arşivlemek için 17a-4 LLC'deki [Skype Server DataParser'ı](https://www.17a-4.com/skype-server-dataparser/) kullanın. DataParser, üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri Microsoft 365'e aktarmak için yapılandırılmış bir Skype Kurumsal bağlayıcısı içerir. Skype Kurumsal Sunucu DataParser bağlayıcısı, Skype Kurumsal Sunucu verileri e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'teki kullanıcı posta kutularına aktarır.

Skype Kurumsal Sunucu veriler kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken Skype Kurumsal Sunucu bağlayıcı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-skype-for-business-server-data"></a>Skype Kurumsal Sunucu verileri arşivlemeye genel bakış

Aşağıdaki genel bakış, Microsoft 365'te Skype Kurumsal Sunucu verileri arşivlerken veri bağlayıcısı kullanma işlemini açıklar.

![17a-4 arasındaki Skype Kurumsal Sunucu verileri için arşivleme iş akışı.](../media/SkypeServerDataParserConnectorWorkflow.png)

1. Kuruluşunuz, Skype Kurumsal Sunucu DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli olarak, Skype Kurumsal Sunucu öğeler DataParser tarafından toplanır. DataParser ayrıca iletinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Microsoft Purview uyumluluk portalı oluşturduğunuz Skype Kurumsal Sunucu DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Kullanıcı posta kutularında **Skype Kurumsal Sunucu DataParser** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Skype Kurumsal Sunucu öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Skype Kurumsal Sunucu öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC](https://www.17a-4.com/contact/) ile iletişime geçin. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda Skype Kurumsal Sunucu DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-a-skype-for-business-server-dataparser-connector"></a>1. Adım: Skype Kurumsal Sunucu DataParser bağlayıcısı ayarlama

İlk adım, uyumluluk portalındaki Veri bağlayıcıları sayfasına erişmek ve Skype Kurumsal Sunucu veriler için bir 17a-4 bağlayıcısı oluşturmaktır.

1. **Veri bağlayıcıları** **Skype Kurumsal Sunucu DataParser'a**<https://compliance.microsoft.com> >  gidin ve tıklayın.

2. **Skype Kurumsal Sunucu DataParser** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. 17a-4 hesabınızda oturum açın ve Skype Kurumsal Sunucu DataParser bağlantı sihirbazındaki adımları tamamlayın.

## <a name="step-2-configure-the-skype-for-business-server-dataparser-connector"></a>2. Adım: Skype Kurumsal Sunucu DataParser bağlayıcısını yapılandırma

Skype Kurumsal Sunucu DataParser bağlayıcısını yapılandırmak için 17a-4 Desteği ile çalışın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Skype Kurumsal Sunucu DataParser bağlayıcısı, verileri Microsoft 365'e aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-skype-for-business-server-dataparser-connector"></a>4. Adım: Skype Kurumsal Sunucu DataParser bağlayıcısını izleme

Skype Kurumsal Sunucu DataParser bağlayıcısı oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz Skype Kurumsal Sunucu DataParser bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
