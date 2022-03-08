---
title: Microsoft 365'te verileri arşivlemek için bağlayıcı ayarlama
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
description: Microsoft 365'te verileri içeri aktarma ve arşivlemek için 17a-4 FactSet DataParser bağlayıcısı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 8c3728e1866d67b2ec7972b2a8857a2ba045022f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326223"
---
# <a name="set-up-a-connector-to-archive-factset-data"></a>Gerçek Ayarla verilerini arşivlemek için bağlayıcı ayarlama

FactSet platformundan Microsoft 365 kuruluşunun kullanıcı posta kutularına veri almak ve arşivlemek için 17a-4 LLC'den [FactSet DataParser'ı](https://www.17a-4.com/factset-dataparser/) kullanın. DataParser, üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri Microsoft 365'e aktaran bir FactSet bağlayıcısı içerir. FactSet DataParser bağlayıcısı, FactSet verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te kullanıcı posta kutularına alır.

Bilgi Kümesi verileri kullanıcı posta kutularında depolanıyorsa, Mahkeme Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmanız ve arşivlemeniz için FactSet bağlayıcısı kullanmak, kurum gerek resmi ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-factset-data"></a>Bilgi Kümesi verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Microsoft 365'te verileri arşivlemek için veri bağlayıcısı kullanma işlemi açıkılmaktadır.

![FactSet data from 17a-4 için arşivleme iş akışı.](../media/FactSetDataParserConnectorWorkflow.png)

1. Kuruluş, FactSet DataParser'ı ayarlamak ve yapılandırmak için 17a-4 ile çalışır.

2. Düzenli aralıklarla, FactSet öğeleri DataParser tarafından toplanır. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezinde oluşturdukları FactSet DataParser bağlayıcısı DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarıyor.

4. Kullanıcı posta kutularında, Gelen Kutusu **klasöründeki FactSet DataParser** adlı bir alt klasör oluşturulur ve FactSet öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Bilgi Kümesi öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda FactSet DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, Microsoft 365 uyumluluk **merkezinin Veri** bağlayıcıları sayfasında bağlayıcı eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [, Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) uyumluluk merkezinde İzinler'in "Özel bir rol grubu oluşturma" bölümüne bakın.

- Bu 17a-4 veri bağlayıcısı, Microsoft 365 ABD Kamu Bulutu'nın GCC ortamlarında kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde kuruluş müşteri verilerini depolamayı, iletip işlemeyi ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-factset-dataparser-connector"></a>1. Adım: FactSet DataParser bağlayıcısı ayarlama

İlk adım, Microsoft 365 uyumluluk merkezinde Veri bağlayıcıları sayfasına erişmek ve FactSet verileri için bir 17a-4 bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarıFactSet  > <https://compliance.microsoft.com>**DataParser'a gidin ve bu öğeye tıklayın**.

2. FactSet **DataParser ürün açıklaması** sayfasında Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve FactSet DataParser bağlantı sihirbazında adımları tamamlayın.

## <a name="step-2-configure-the-factset-dataparser-connector"></a>2. Adım: FactSet DataParser bağlayıcıyı yapılandırma

FactSet DataParser bağlayıcıyı yapılandırmak için 17a-4 Desteği ile çalışma.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

FactSet DataParser bağlayıcısı, verileri Microsoft 365'e aktarmadan önce kullanıcıları otomatik olarak Microsoft 365 e-posta adresleriyle eşler.

## <a name="step-4-monitor-the-factset-dataparser-connector"></a>4. Adım: FactSet DataParser bağlayıcılarını izleme

FactSet DataParser bağlayıcısı oluşturdukta, Bağlayıcı durumunu Microsoft 365 uyumluluk merkezinde görüntüebilirsiniz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra, oluşturduğunuz FactSet DataParser bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
