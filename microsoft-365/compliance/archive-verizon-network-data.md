---
title: Verizon Network verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, temlik yoluyla Verizon Network'te SMS ve MMS verilerini içeri aktaracak ve arşivacak bir TeleMessage bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 32921c3db589785e6ec3245f2f8867d49d1de9a5
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021513"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Verizon Network verilerini arşivlemek için bir bağlayıcı ayarlama

Verizon Network'Microsoft 365 uyumluluk merkezi Kısa İleti Hizmeti (SMS) ve Multimedya İleti Hizmeti (MMS) verilerini içeri aktararak arşivlemek için ileti kaynağında TeleMessage bağlayıcıyı kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı her gün kuruluşun Verizon Network'e bağlanır ve SMS ve MMS verilerini aynı anda posta kutularına Microsoft 365.

Verizon Network bağlayıcı verileri kullanıcı posta kutularında depolanıyorsa, Verizon Microsoft 365 Bekletme, İçerik Arama ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Verizon SMS ve MMS iletilerinde arama veya Verizon Network verilerini içeren posta kutusunu bir özel olayda bir özel durum Advanced eDiscovery ilişkilendirilebilirsiniz. Verileri başka bir e-postada içeri aktararak ve arşiv Microsoft 365 ve bir Verizon Network bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-verizon-network-data"></a>Verizon Network verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Kendi 365'te Verizon Network verilerini arşivlemek için bağlayıcı Microsoft 365.

![Verizon Network arşivleme iş akışı.](../media/VerizonNetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage and Verizon to set a Verizon Network connector. Daha fazla bilgi için bkz [. Verizon Network Archiver](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. Her 24 saatte bir, kuruluş ve Verizon Network'den gelen SMS ve MMS iletileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız Verizon Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde SMS ve MMS iletilerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı SMS ve MMS iletilerinin içeriğini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli kullanıcının posta kutusunda **Verizon SMS/MMS Ağ** Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her SMS ve MMS iletisi, iletinin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de kullanabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Bağlayıcı önce özel eşleme dosyasına bakarak her Verizon öğesi için hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsiniz. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı özel eşleme dosyasında veya Verizon Microsoft 365 e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Verizon Network verilerini arşivlemek için gereken bazı uygulama adımları Microsoft 365'nin dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan Verizon Network Archiver hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage ekleme formlarınızı doldurarak ve ileti arşivleme hizmetini Verizon'den sipariş etmek için Verizon Network hesabınızla fatura kişi ayrıntılarınızı alın.

- TeleMessage hesabında Verizon SMS ve MMS arşivlemesi gerektiren tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarınız Verizon mobil ağında kurumsal ve kurumsal olarak sorumlu cep telefonlarına sahip olmalıdır. İletileri tek Microsoft 365 sahipli veya Kendi Cihazlarınızı Getir (BYOD) cihazlarında kullanılamaz.

- Verizon Network bağlayıcısı oluşturan kullanıcıya, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-verizon-network-connector"></a>Verizon Network bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, aşağıdaki bölümde Verizon Network bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve SMS ve MMS mesajlarını İleti'de ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. [https://compliance.microsoft.com](https://compliance.microsoft.com) **Data connectorsVerizon Network'e gidin** >  ve **bu öğeye tıklayın**.

2. **Verizon Network ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

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