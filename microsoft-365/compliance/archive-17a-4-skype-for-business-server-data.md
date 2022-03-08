---
title: Verileri tek bir e-postada Skype Kurumsal Sunucu için bağlayıcıyı Microsoft 365
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
description: 17a-4 veri bağlayıcısı ayarlamayı ve Skype Kurumsal Sunucu veri kaynağında verileri içeri Skype Kurumsal Sunucu için DataParser bağlayıcısı Microsoft 365.
ms.openlocfilehash: 8c36b46ad8c49c44b87a11a688e15fcf27d82de0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311837"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-server-data"></a>Verilerinizi arşivlemek için bağlayıcıyı Skype Kurumsal Sunucu ayarlama

[Skype Server DataParser'ı](https://www.17a-4.com/skype-server-dataparser/) 17a-4 LLC'den kullanarak Skype Kurumsal Sunucu'dan Microsoft 365 posta kutularına veri aktarın. DataParser' Skype Kurumsal üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaran bir Microsoft 365. Yeni Skype Kurumsal Sunucu DataParser bağlayıcısı, Skype Kurumsal Sunucu verilerini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365.

Verileri Skype Kurumsal Sunucu posta kutularında depodikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Skype Kurumsal Sunucu'da verileri içeri aktararak ve arşivlerken Microsoft 365, kuruluş ilkeleriyle uyumlu olması için bir uyumluluk bağlayıcısı kullanabilirsiniz.

## <a name="overview-of-archiving-skype-for-business-server-data"></a>Verileri arşivlemeye Skype Kurumsal Sunucu genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı içinde yer alan verileri arşivlemek Skype Kurumsal Sunucu veri bağlayıcısı kullanma Microsoft 365.

![17a-4 Skype Kurumsal Sunucu verileri arşivleme için iş akışı.](../media/SkypeServerDataParserConnectorWorkflow.png)

1. Verileriniz VeriParser'ı ayarlamak ve yapılandırmak için 17a-4 Skype Kurumsal Sunucu çalışır.

2. Düzenli aralıklarla, Skype Kurumsal Sunucu DataParser tarafından toplanan öğeler. DataParser, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Veri Skype Kurumsal Sunucu veriparser bağlayıcısı Microsoft 365 uyumluluk merkezi DataParser'a bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma bağlar.

4. Kullanıcı posta kutularında **VeriParser adlı Skype Kurumsal Sunucu** Gelen Kutusu klasöründe bir alt klasör oluşturulur ve Skype Kurumsal Sunucu bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Skype Kurumsal Sunucu öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir DataParser hesabı oluşturun. Bunu yapmak için [17a-4 LLC ile iletişime geçin](https://www.17a-4.com/contact/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Skype Kurumsal Sunucu DataParser bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu 17a-4 veri bağlayıcısı, ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-a-skype-for-business-server-dataparser-connector"></a>1. Adım: DataParser Skype Kurumsal Sunucu ayarlama

İlk adım, çalışma sayfasındaki Veri bağlayıcıları sayfasına erişmek Microsoft 365 uyumluluk merkezi veri oluşturmak için bir 17a-4 Skype Kurumsal Sunucu oluşturmaktır.

1. Veri Bağlayıcıları'nın <https://compliance.microsoft.com> **veri bağlayıcıları'Skype Kurumsal Sunucu** >  **tıklayın**.

2. **VeriParser Skype Kurumsal Sunucu açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. 17a-4 hesabınızla oturum açın ve VeriParser bağlantı Skype Kurumsal Sunucu adımları tamamlayın.

## <a name="step-2-configure-the-skype-for-business-server-dataparser-connector"></a>2. Adım: Skype Kurumsal Sunucu DataParser bağlayıcıyı yapılandırma

DataParser bağlayıcısı için gereken bağlayıcıyı yapılandırmak için 17a-4 Skype Kurumsal Sunucu kullanın.

## <a name="step-3-map-users"></a>3. Adım: Kullanıcıları eşleme

Yeni Skype Kurumsal Sunucu DataParser bağlayıcısı, verileri Microsoft 365 e-posta adreslerine aktarmadan önce kullanıcıları otomatik olarak Microsoft 365.

## <a name="step-4-monitor-the-skype-for-business-server-dataparser-connector"></a>4. Adım: DataParser Skype Kurumsal Sunucu izleme

Skype Kurumsal Sunucu DataParser bağlayıcısı oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve Skype Kurumsal Sunucu özellikleri ve bağlayıcıyla ilgili bilgileri içeren açılır sayfayı görüntülemek için oluşturduğunuz VeriParser bağlayıcısı öğesini seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
