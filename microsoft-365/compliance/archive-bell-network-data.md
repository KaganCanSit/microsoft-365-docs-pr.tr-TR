---
title: Bell SMS/MMS Ağ verilerini arşivlemek için bağlayıcı ayarlama
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
description: Yöneticiler Bell Network'te SMS ve MMS verilerini içeri aktaracak ve arşivacak bir TeleMessage bağlayıcısı kurabilirsiniz. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: fd2c986d31e148d209734f0aa65c7b12f950e2eb
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021482"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Bell Network verilerini arşivlemek için bağlayıcı ayarlama

Bell Network'den Kısa İleti Hizmeti (SMS) ve Multimedya İleti Hizmeti (MMS) iletilerini içeri aktarmak ve arşivlemek için, iletişim Microsoft 365 uyumluluk merkezi'de teleMessage bağlayıcısı kullanın. Bir bağlayıcı ayardikten ve yapılandırdikten sonra, bağlayıcı, her gün kuruluşun Bell Network'e bağlanır ve SMS ve MMS mesajlarını Gelen Kutusu'Microsoft 365.

SMS ve MMS iletileri kullanıcı posta kutularında depolanıyorsa, Bell Network verilerine Mahkeme Microsoft 365, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Bell Network SMS/MMS'de arama veya Bell Network bağlayıcı verilerini içeren posta kutusunu bir özel durum örneğinde bir özel kişi Advanced eDiscovery ilişkilendirilebilirsiniz. Verileri web'de içeri aktararak ve arşivlenen bir Bell Network Microsoft 365, kuruma ve resmi mevzuat ilkelerine uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-bell-network-data"></a>Bell Network verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Ağ bağlantılarında Bell Network verilerini arşivlemek için bağlayıcı Microsoft 365.

![Bell Network arşivleme iş akışı.](../media/BellNetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage and Bell to set a Bell Network connector. Daha fazla bilgi için bkz [. Bell Network Archiver](https://www.telemessage.com/office365-activation-for-bell-network-archiver).

2. Gerçek zamanlı olarak, kuruluşun Çan Ağı'sından gelen SMS ve MMS iletileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Bell Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde gelen SMS ve MMS mesajlarını Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı SMS ve MMS iletilerinin içeriğini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli kullanıcıların posta kutusuna içeri aktarıyor. Bell **SMS/MMS Ağ Arşivleyicisi** adlı yeni bir klasör belirli bir kullanıcının posta kutusunda oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her SMS ve MMS iletisi, iletinin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsanız, bağlayıcı önce özel eşleme dosyasına bakarak bakarak bu öğeyi görüntüler. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı, özel eşleme dosyasında veya Bell Network Microsoft 365 e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Bell Network verilerini arşivlemek için gereken bazı uygulama adımları, ağ Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan Bell Network Archiver hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage ekleme formlarınızı doldurmak ve ileti arşivleme hizmetini Bell'den sipariş etmek için Bell Network hesaplarınızı ve fatura kişi ayrıntılarınızı alın.

- Bell SMS/MMS Ağı arşivlemesi gereken tüm kullanıcıları TeleMessage hesabında kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarının Bell mobil ağına şirket tarafından ait ve kurumsal olarak sorumlu cep telefonları olmalıdır. İletileri Tek Microsoft 365, çalışana ait "Kendi Cihazlarınızı Getirin (BYOD) cihazlarında kullanılamaz.

- Bell Network bağlayıcısı oluşturan kullanıcıya, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-bell-network-connector"></a>Bell Network bağlayıcısı oluşturma

Son adım, ağ bağlantılarında bir Bell Network bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve SMS/MMS iletilerini kendi posta kutunuzda ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcılarıÇizim [https://compliance.microsoft.com](https://compliance.microsoft.com) **SMS/MMS** >  Ağ Arşivleyicisi'ne gidin **ve tıklayın**.

2. Zil Ağı **ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **TeleMessage'da Oturum Aç** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

   - **Kullanıcı adı:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra, açılır pencereyi kapatıp bir sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme **sayfasında** , otomatik kullanıcı eşlemesini etkinleştirin. Özel eşlemeyi etkinleştirmek için, kullanıcı eşleme bilgilerini içeren bir CSV dosyası yükleyin ve İleri'ye **tıklayın**.

7. Ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

8. Yeni **bağlayıcının** içeri aktarma **işleminin** ilerlemesini görmek için uyumluluk merkezinde Veri bağlayıcıları sayfasının Bağlayıcılar sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
