---
title: WhatsApp verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, WhatsApp verilerini kendi dosya dosyalarında içeri aktaracak ve arşivecek bir TeleMessage Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: b94d22b787e88de241bee404774caaabf5ac02ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313237"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>WhatsApp verilerini arşivlemek için bağlayıcıyı ayarlama

WhatsApp aramalarını, sohbetlerini, eklerini, dosyalarını ve silinen iletilerini içeri aktarın ve Microsoft 365 uyumluluk merkezi teleMessage bağlayıcıyı kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı her gün kuruluşun TeleMessage hesabına bağlanır ve TeleMessage WhatsApp Telefon Archiver veya TeleMessage WhatsApp Cloud Archiver kullanarak çalışanların mobil iletişimini Microsoft 365.

WhatsApp verileri kullanıcı posta kutularında depolandığı için, WhatsApp verilerine Microsoft 365 Saklama, İçerik araması ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik arama kullanarak WhatsApp iletilerinde arama veya WhatsApp iletilerini içeren posta kutusunu bir özel durumda bir özel durumla Advanced eDiscovery. WhatsApp bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 düzenlemeler ve devlet ilkeleriyle uyumlu kalmasınıza yardımcı olabilir.

## <a name="overview-of-archiving-whatsapp-data"></a>WhatsApp verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış veri kaynağında WhatsApp verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![WhatsApp arşivleme iş akışı.](../media/WhatsAppConnectorWorkflow.png)

1. Your organization works with TeleMessage to set a WhatsApp Archiver connector. Daha fazla bilgi için bkz [. WhatsApp Arşivleyici](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. Gerçek zamanlı olarak, kuruluş whatsApp verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturduktan sonra, WhatsApp bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde WhatsApp verilerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı, WhatsApp verilerini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, WhatsApp verilerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta **kutusunda WhatsApp Arşivleyicisi** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her WhatsApp iletisi, iletinin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de kullanabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Her WhatsApp öğesi için bağlayıcı önce özel eşleme dosyasına bakarak hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsiniz. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı, kullanıcıya özel Microsoft 365 veya WhatsApp öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

WhatsApp iletişim verilerini arşivlemek için gereken bazı uygulama adımları Microsoft 365 uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan WhatsApp Arşivleyici hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage hesabında WhatsApp arşivlemesi gereken tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarının cep [telefonlarına TeleMessage whatsApp Telefon Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) uygulamasını yükleyin ve etkinleştirin. Alternatif olarak, çalışanlarının cep telefonlarına normal WhatsApp veya WhatsApp İş uygulamalarını yükleyebilir ve TeleMessage web sitesinde QR kodunu taratarak WhatsApp Bulut Arşivleyici hizmetini etkinleştirebilirsiniz. Daha fazla bilgi için bkz [. WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Verizon Network bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atan olmalıdır. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-whatsapp-archiver-connector"></a>WhatsApp Arşivleyici bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, ilgili bölümde WhatsApp bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve WhatsApp verilerini İleti'de ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcılarıWhatsApp [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Arşivleyici'ye** >  gidin **ve bu bağlayıcılara tıklayın**.

2. **WhatsApp Arşivleyici ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **TeleMessage'da Oturum Aç** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

   - **Kullanıcı adı:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra, açılır pencereyi kapatıp bir sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme **sayfasında, otomatik** kullanıcı eşlemesini etkinleştirin ve Ardından'ya **tıklayın**. Özel eşlemeye ihtiyacınız olursa, CSV dosyasını karşıya yükleyin ve İleri'ye **tıklayın**.

7. Ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

8. Yeni bağlayıcı için içeri aktarma **işleminin ilerlemesini** görmek için Veri bağlayıcıları sayfasındaki Bağlayıcılar sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
