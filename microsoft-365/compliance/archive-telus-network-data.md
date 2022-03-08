---
title: TelUS Network verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, iş yerinde TELUS Ağı'nda SMS verilerini içeri aktarıp arşivlemek için telemessage bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 7aca24c39f9eba5dba532f1224ad68d5ff1d4568
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327399"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>TELUS Ağ verilerini arşivlemek için bağlayıcıyı ayarlama

Kısa İleti Hizmeti (SMS) verilerini Microsoft 365 uyumluluk merkezi TELUS Ağı'nda içeri aktarıp arşivlemek için, ileti kaynağında TeleMessage bağlayıcıyı kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı her gün kuruluşun TELUS Ağı'ne bağlanır ve SMS verilerini E-posta'daki posta kutularına Microsoft 365.

SMS mesajları kullanıcı posta kutularında depolanıyorsa, TELUS verilerine mahkeme Microsoft 365, İçerik Arama ve bekletme Microsoft 365 uyumluluk özellikleri uygulayabilirsiniz. Örneğin, İçerik Araması'nı kullanarak TELUS SMS iletilerinde arama veya TELUS verilerini içeren posta kutusunu bir özel durum durumunda bir koruyucuyla Advanced eDiscovery alabilirsiniz. Verileri kendi web sitelerine içeri aktarıp arşivlemek için TELUS Network bağlayıcısı kullanmak Microsoft 365 düzenleme ve devlet ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-telus-network-data"></a>TELUS Ağ verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, telUS Ağ verilerini tek bir tabloda arşivlemek için bağlayıcı Microsoft 365.

![TELUS Network arşivleme iş akışı.](../media/TelusNetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage and TELUS to set a TELUS Network connector. Daha fazla bilgi için bkz. [TELUS Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. Gerçek zamanlı olarak, kuruluşun TELUS Ağı'nın SMS mesajları TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturduktan sonra TELUS Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saatte gelen SMS mesajlarını Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı SMS mesajlarının içeriğini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta **kutusunda TELUS SMS Ağ** Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Kullanıcının E-posta adresi *özelliğinin değerini kullanarak eşleme* yapar. Her SMS'in bu özelliği vardır ve bu özellik SMS mesajı her katılımcının e-posta adresiyle doldurulur.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de kullanabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsanız, bağlayıcı önce özel eşleme dosyasına bakarak bakarak her TELUS öğesinde yer alır. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı, kullanıcıya özel Microsoft 365 veya TELUS öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

TELUS Network verilerini arşivlemek için gereken bazı uygulama adımları, Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan TELUS Network Archiver hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage ekleme formlarınızı doldurarak ileti arşivleme hizmetini TELUS'tan sipariş etmek için TELUS Network hesabı ve fatura kişi ayrıntılarınızı alın.

- TelUS SMS Ağı arşivlemesi gerektiren tüm kullanıcıları TeleMessage hesabında kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- ÇalışanlarınızıTELUS mobil ağına kurumsal ve kurumsal olarak sorumlu cep telefonları olmalıdır. İletileri tek Microsoft 365 sahipli veya Kendi Cihazlarınızı Getir (BYOD) cihazlarında kullanılamaz.

- TELUS Ağ bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atan olmalıdır. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-telus-network-connector"></a>TELUS Ağ bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, aşağıdaki bölümde TELUS Network bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, temlik, TeleMessage sitesine bağlanmak ve SMS mesajlarını İleti'de ilgili kullanıcı posta kutusu kutularına Microsoft 365.

1. Veri bağlayıcılarıTELUS [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Network'e gidin ve** >  **bu bağlantıya tıklayın**.

2. **TELUS Ağı ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**

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
