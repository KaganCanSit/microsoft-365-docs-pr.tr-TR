---
title: TeleMessage veya Sayı Arşivleyicisi'den verileri arşivlemek Enterprise ayarlama
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
description: Yöneticiler TeleMessage veya Number Archiver'dan SMS ve MMS verilerini içeri aktaracak ve arşivley edebilecek Enterprise kurabilirsiniz. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 01c72b630c61ff0fda764971872b2a776617c3d2
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021521"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Verileri arşivlemek için bağlayıcıyı Enterprise ayarlama

Microsoft 365 uyumluluk merkezi Numara Arşivleyicisi'ne ait Kısa İleti Hizmeti (SMS) ve Multimedya İleti Hizmeti (MMS) iletilerini, sohbet iletilerini, sesli arama kayıtlarını ve sesli arama günlüklerini içeri aktararak arşivlemek için Enterprise TeleMessage bağlayıcısını kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı her gün kuruluşun TeleMessage hesabına bağlanır ve TeleMessage Enterprise Number Archiver kullanarak çalışanların mobil iletişim verilerini Microsoft 365.

TeleMessage Enterprise Number Archiver bağlayıcı verileri kullanıcı posta kutularında depolendikten sonra, Sayı Arşivleyici verilerini arşivlemek için Mahkeme Saklama, İçerik Araması, Microsoft 365 In-Place Arşivleme, Denetim, İletişim uyumluluğu Microsoft 365 bekletme Enterprise uyumluluk özellikleri uygulayabilirsiniz. Örneğin, İçerik Arama kullanarak TeleMessage Enterprise Number Archiver SMS, MMS ve Sesli Arama'da arama veya Enterprise Sayı Arşivleyici bağlayıcısı verilerini içeren posta kutusunu bir Advanced eDiscovery durumunda bir koruyucu ile ilişkilendirilebilirsiniz. Verileri başka Enterprise ve arşiv için bir Sayı Arşivleyici bağlayıcısı Microsoft 365 kuruluşun devlet ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-enterprise-number-data"></a>Sayı verilerini arşivlemeye Enterprise genel bakış

Aşağıdaki genel bakış makalesinde, Bağlayıcı kullanarak verileri tek bir Enterprise arşivleme işlemi Microsoft 365.

![Enterprise arşivleme iş akışı.](../media/EnterpriseNumberConnectorWorkflow.png)

1. Your organization works with TeleMessage to set up an Enterprise Number Archiver connector. Diğer ayrıntılar için buraya [bakın](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/).

2. Microsoft 365 uyumluluk merkezi Enterprise'de oluşturtük Enterprise Sayı Arşivleyicisi bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde gönderilen e-posta iletilerini Microsoft Bulut'ta güvenli bir Azure Depolama alanına iletir.

3. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının Enterprise kutusunda Sayı Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Kullanıcının E-posta adresi *özelliğinin değerini kullanarak eşleme* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir. Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, Kullanıcının mobil Numarasını ve her kullanıcı için Microsoft 365 posta kutusu adresini içermeli. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının mobil numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı, e-posta öğesinin Kullanıcı 'nın e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Sayı Arşivleyicisi verilerini arşivlemek Enterprise uygulama adımlarının bazıları Microsoft 365'nin dışındadır ve uyumluluk merkezinde bağlayıcıyı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage Enterprise dan Numara Arşivleyici hizmeti](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş açın ve organizasyonunız için geçerli bir yönetim hesabı seçin. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage hesabında Numara SMS Enterprise MMS Ağ arşivlemesi gerektiren tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarının cep telefonlarına TeleMessage Enterprise Number Archiver uygulamasını yükleyin ve etkinleştirin.

- Sayı Arşivleyicisi bağlayıcısı Enterprise bu bağlayıcıda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-an-enterprise-number-archiver-connector"></a>Sayı Enterprise bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, üst bölümde Enterprise Number Archiver bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve SMS, MMS ve sesli arama mesajlarını İleti'de ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) ve Sayı **Arşivleyicisi'ne** \> **Enterprise tıklayın**.

2. Bağlayıcı Enterprise **Numarası Arşivleyici** ürün açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

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