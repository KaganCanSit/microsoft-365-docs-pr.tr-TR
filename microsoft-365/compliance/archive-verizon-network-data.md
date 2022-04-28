---
title: Microsoft 365'da Verizon Ağ verilerini arşivleme bağlayıcısı ayarlama
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
description: Yöneticiler, SMS ve MMS verilerini Microsoft 365'da Verizon Ağı'ndan içeri aktarmak ve arşivlemek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 5c347cf6854719780e8c64038217bd841920cd80
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098614"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Verizon Ağ verilerini arşivleme için bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Verizon Network'ten Kısa Mesajlaşma Hizmeti (SMS) ve Multimedya Mesajlaşma Hizmeti (MMS) verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalındaki TeleMessage bağlayıcısını kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun Verizon Ağına bağlanır ve SMS ve MMS verilerini Microsoft 365'deki posta kutularına aktarır.

Verizon Ağ bağlayıcısı verileri kullanıcı posta kutularında depolandıktan sonra, Verizon verilerine Dava Tutma, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak Verizon SMS ve MMS iletilerinde arama yapabilir veya Verizon Network verilerini içeren posta kutusunu Microsoft Purview eKeşif (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için verizon ağı bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-verizon-network-data"></a>Verizon Ağ verilerini arşivleme genel bakış

Aşağıdaki genel bakış, verizon ağ verilerini Microsoft 365'de arşivleme amacıyla bağlayıcı kullanma işlemini açıklar.

![Verizon Ağ arşivleme iş akışı.](../media/VerizonNetworkConnectorWorkflow.png)

1. Kuruluşunuz TeleMessage ve Verizon ile birlikte çalışarak bir Verizon Network bağlayıcısı ayarlar. Daha fazla bilgi için bkz. [Verizon Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. 24 saatte bir, kuruluşunuzun Verizon Ağından gelen SMS ve MMS iletileri TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz Verizon Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki SMS ve MMS iletilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca SMS ve MMS iletilerinin içeriğini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **Verizon SMS/MMS Ağ Arşivleyicisi** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her SMS ve MMS iletisi, iletinin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

   *Kullanıcının E-posta adresi* özelliğinin değerini kullanan otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek de özel eşleme uygulayabilirsiniz. Bu eşleme dosyası, kuruluşunuzdaki kullanıcılar için cep telefonu numarasını ve ilgili Microsoft 365 e-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirseniz, bağlayıcı her Verizon öğesi için önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğindeki değerleri kullanır. Bağlayıcı, özel eşleme dosyasında veya Verizon öğesinin e-posta adresi özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Verizon Ağ verilerini arşivlemeniz için gereken uygulama adımlarından bazıları Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturabilmeniz için önce tamamlanması gerekir.

- [TeleMessage'dan Verizon Network Archiver hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- TeleMessage ekleme formlarını doldurabilmek ve verizon'dan ileti arşivleme hizmetini sipariş edebilmek için Verizon Network hesabınızın ve faturalama iletişim bilgilerinizi alın.

- Verizon SMS ve MMS arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Çalışanlarınızın Verizon mobil ağında şirkete ait ve şirkete ait cep telefonlarına sahip olması gerekir. Microsoft 365'de iletileri arşivleme, çalışana ait veya Kendi Cihazlarını Getir (KCG) cihazlarda kullanılamaz.

- Verizon Ağ bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-verizon-network-connector"></a>Verizon Ağ bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra, uyumluluk portalında Verizon Network bağlayıcısı oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak ve SMS ve MMS iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcılarıVerizon** >  **Ağı'na**[https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Verizon Network** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **TeleMessage'da Oturum Aç** sayfasındaki 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.
  
   - **Username:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra açılır pencereyi kapatabilir ve sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme sayfasında, otomatik kullanıcı **eşlemesini** etkinleştirin ve **İleri'ye** tıklayın. Özel eşlemeye ihtiyacınız olması durumunda bir CSV dosyasını karşıya yükleyin ve **İleri'ye** tıklayın.

7. Ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları sayfasındaki Bağlayıcılar** sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.