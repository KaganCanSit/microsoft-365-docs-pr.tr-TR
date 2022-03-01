---
title: O2 Ağ verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, O2 mobil ağına ait SMS ve MMS verilerini Kendi Verileriniz'de içeri aktaracak ve arşivleyilecek bir TeleMessage bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 873396df23e9d4834c0da37e31af599d7fc0fb38
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021566"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>O2 Ağ verilerini arşivlemek için bağlayıcı ayarlama

O2 mobil ağına gelen Kısa Microsoft 365 uyumluluk merkezi (SMS) mesajlarını ve sesli aramaları içeri aktararak arşivlemek için, iletide TeleMessage bağlayıcısı kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı, her gün kuruluşun O2 Ağına bağlanır ve SMS ile sesli aramaları gelen kutunuzda posta kutularına Microsoft 365.

SMS mesajları ve sesli aramalar kullanıcı posta kutularında depolanıyorsa, O2 Ağ verilerine Mahkeme Microsoft 365, İçerik Arama ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak O2 Ağ SMS'lerini ve sesli aramalarını arayabilir veya O2 Ağ verilerini içeren posta kutusunu bir özel durum örneğinde özel kişi Advanced eDiscovery ilişkilendirilebilirsiniz. Verileri başka bir kuruluşta içeri aktararak ve arşivlerken O2 Network bağlayıcısı kullanmak Microsoft 365 kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-o2-network-data"></a>O2 Ağ verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış veri kaynağında O2 Ağ verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![O2 Ağ arşivleme iş akışı.](../media/O2NetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage and O2 to set an O2 Network connector. Daha fazla bilgi için bkz [. O2 Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Her 24 saatte bir, kuruluşun O2 Ağına gelen SMS mesajları ve sesli aramalar TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız O2 Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde yapılan SMS mesajlarını ve sesli aramaları Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı, SMS mesajlarının ve sesli aramaların içeriğini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli kullanıcıların posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta kutusunda **O2 SMS ve Voice Network Archiver** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her SMS iletisi ve sesli arama, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsanız, bağlayıcı önce özel eşleme dosyasına bakarak her O2 öğesinde yer alır. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı, kullanıcıya özel Microsoft 365 veya O2 öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

O2 Ağ verilerini arşivlemek için gereken uygulama adımlarının bazıları Uyumluluk Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan O2 Network Archiver hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage ekleme formlarınızı doldurarak ileti arşivleme hizmetini O2'den sipariş etmek için O2 Ağ hesabı ve fatura kişi ayrıntılarınızı alın.

- O2 SMS ve Voice Network arşivlemesi gereken tüm kullanıcıları TeleMessage hesabında kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarınızı O2 mobil ağına kurumsal ve kurumsal olarak sorumlu cep telefonları olmalıdır. İletileri Tek Microsoft 365, çalışana ait "Kendi Cihazlarınızı Getirin (BYOD) cihazlarında kullanılamaz.

- Bir O2 Ağ bağlayıcısı oluşturan kullanıcıya, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-an-o2-network-connector"></a>O2 Ağ bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, son bölümde bir O2 Ağ bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, telemessage sitesine bağlanmak ve SMS mesajlarını ve sesli aramaları İleti'deki ilgili kullanıcı posta kutusu kutularına göndermek için Microsoft 365.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) O2 **Ağ'a gidip** \> **bu öğeye tıklayın**.

2. **O2 Ağ ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**

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