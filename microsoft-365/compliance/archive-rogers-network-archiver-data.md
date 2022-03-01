---
title: Rogers Network verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Rogers Network verilerini kendi ağ bağlantılarında içeri aktaracak ve arşivacak bir TeleMessage Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: cdeeb8956620321b83bdd6b1ce85c656e7946936
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021474"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Rogers Network verilerini arşivlemek için bağlayıcı ayarlama

Mete'ler mobil Microsoft 365 uyumluluk merkezi SMS ve MMS verilerini içeri aktararak arşivlemek için metin kaynağında TeleMessage bağlayıcıyı kullanın. [Siz Mete](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/) Mete Ağ Arşivleyici bağlayıcısı ayardikten ve yapılandırdıktan sonra, bu bağlayıcı kuruluşun Metesi mobil ağına bağlanır ve SMS ve MMS verilerini Posta Kutuları'nda posta kutularına Microsoft 365.

Mete'ler mobil ağına gelen veriler kullanıcı posta kutularında depo kullandıktan sonra, verilere Mahkeme Microsoft 365, İçerik araması ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik arama kullanarak veya Çekirdek eKbulma durumuyla ilişkilendirilmiş bir arama kullanarak Mete'ler mobil ağına gelen SMS ve MMS iletilerini arayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak veya arşivlerken bir Rogers Network Archiver bağlayıcısı kullanmak Microsoft 365 organizasyona kurumsal yönetim düzenlemeleri ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Rogers mobil ağ verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde Mete'nin SMS ve MMS verilerini kendi verilerinizden arşivlemek için bağlayıcı Microsoft 365.

![Rogers Network arşivleme iş akışı.](../media/RogersNetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage to set a Rogers Network Archiver connector. Daha fazla bilgi için bkz[. Daha fazla bilgi için TeleMessage Rogers Network Archiver'ı etkinleştirme Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. Gerçek zamanlı olarak, kuruluşa ait Rogers mobil ağ verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturduktan sonra Rogers Network Archiver bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde gönderilen e-posta iletilerini Microsoft Bulut'un güvenli bir Azure Depolama alanına aktarıyor.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda Mete'ler SMS/MMS Ağ Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Eşlemeyi Kullanıcının E-posta *adresi özelliğini kullanarak* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, Kullanıcının mobil Numarasını ve her kullanıcı için Microsoft 365 posta kutusu adresini içermeli. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı kullanıcının e-posta öğesi e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Rogers Network Archiver hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) sipariş etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- Rogers Network arşivlemesi gerektiren tüm kullanıcıları TeleMessage hesabında kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarınızı O2 mobil ağına kurumsal ve kurumsal olarak sorumlu cep telefonları olmalıdır. İletileri Tek Microsoft 365, çalışana ait "Kendi Cihazlarınızı Getirin (BYOD) cihazlarında kullanılamaz.

- Ekleme formlarını tamamlayan ve ileti arşivleme hizmetini Rogers'tan sipariş etmek için, organizasyon için Rogers hesabını ve fatura kişi ayrıntılarını alın.

- 3. Adımda Rogers Ağ Arşivleyicisi bağlayıcısı oluşturan kullanıcıya, Çalışma Alanı'nda Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-rogers-network-archiver-connector"></a>Rogers Network Archiver bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, dosyanın sağ üst kısmında Rogers Network Archiver bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve Mete'ler SMS/MMS verilerini kendi posta kutunuzda ilgili kullanıcı posta kutusuna göndermek için Microsoft 365.

1. Veri bağlayıcılarıRogers <https://compliance.microsoft.com> **Ağ Arşivleyicisi'ne** >  **gidin ve bu öğeye tıklayın**.

2. **Rogers Network Archiver ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **TeleMessage'da Oturum Aç** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

    - **Kullanıcı adı:** TeleMessage kullanıcı adınız.

    - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra, açılır pencereyi kapatıp bir sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme **sayfasında** , otomatik kullanıcı eşlemesini etkinleştirin. Özel eşlemeyi etkinleştirmek için, kullanıcı eşleme bilgilerini içeren bir CSV dosyası yükleyin ve İleri'ye **tıklayın**.

7. Ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

8. Yeni bağlayıcı için içeri aktarma **işleminin ilerlemesini** görmek için Veri bağlayıcıları sayfasındaki Bağlayıcılar sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
