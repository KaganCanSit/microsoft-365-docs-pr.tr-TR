---
title: Microsoft 365'te Red tail Speak verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Red tail Speak verilerini Veritas'tan Microsoft 365'e aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivlenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 28fb3de980fd9520afb69c9ec74fb9392f14a0d6
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639236"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Redtail Speak verilerini arşivleye bir bağlayıcı ayarlama

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına Redtail Speak'den verileri içeri aktarmak ve arşiv uygulamak için Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, öğelerin [Redtail'ten](https://globanet.com/redtail/) alındığı kuruluşunuzun SFTP sunucusundan öğeleri yakalamak için yapılandırılmış bir Redtail Speak bağlayıcısı sağlar. Bağlayıcı, Redtail Speak'deki içeriği e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'te kullanıcının posta kutusuna aktarır.

Redtail Speak verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken Redtail Speak bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Redtail Speak verilerini arşivleme işlemine genel bakış

Aşağıdaki genel bakışta, Microsoft 365'te Redtail Speak verilerini arşivleyen bir bağlayıcı kullanma işlemi açıklanmaktadır.

![Redtail Speak verileri için arşivleme iş akışı.](../media/RedtailSpeakConnectorWorkflow.png)

1. Kuruluşunuz, iletilerin Redtail Speak'den kuruluşunuzun SFTP sunucusuna günlük olarak iletildiği bir SMTP ağ geçidi ayarlamak ve yapılandırmak için Redtail Speak ile birlikte çalışır.

2. Her 24 saatte bir, Redtail Speak öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca Redtail Speak öğelerini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Redtail Speak bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülmüş Redtail Speak öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **Redtail Speak** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Redtail Speak öğesi, öğenin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 2. Adım'da kuruluşunuzun SFTP sunucusunu belirtmeniz gerekir. Bu adım, Veritas Merge1'in SFTP aracılığıyla Redtail Speak verilerini toplamak için onunla iletişim kurabilmesi için gereklidir.

- 1. Adımda Redtail Speak Importer bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>1. Adım: Redtail Speak bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Redtail Speak verileri için bir bağlayıcı oluşturmaktır.

1. **Veri bağlayıcıları** &gt; **Redtail Speak'a**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve öğesini seçin.

2. **Redtail Speak** ürün açıklaması sayfasında **Yeni bağlayıcı ekle'yi** seçin.

3. **Hizmet koşulları** sayfasında **Kabul Et'i** seçin.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'yi** seçin.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Redtail Speak bağlayıcısını yapılandırma

İkinci adım, Merge1 sitesinde Redtail Speak bağlayıcısını yapılandırmaktır. Redtail Speak bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

**Kaydet & Son'u** seçtikten sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Kullanıcıları Microsoft 365 kullanıcılarına seslendir** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Redtail Speak öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcısı ile ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'yi** seçin, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>4. Adım: Redtail Speak bağlayıcısını izleme

Redtail Speak bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti **bölmesinden Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve bunu seçin.

2. Açılan sayfayı görüntülemek için **Bağlayıcılar** sekmesini ve ardından **Redtail Speak** bağlayıcısını seçin. Bu sayfada bağlayıcıyla ilgili özellikler ve bilgiler görüntülenir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısını seçin. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.