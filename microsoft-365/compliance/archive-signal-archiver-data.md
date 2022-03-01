---
title: Bir bağlayıcı kurarak Sinyal iletişim verilerini Arşivle'Microsoft 365
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
description: Yöneticiler Signal communications data data in Microsoft 365'i içeri aktaracak ve arşivlecek bir TeleMessage bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 57c8fc5a6c3de5f6c8d376f8dfddd360f2627395
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021515"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Signal iletişim verilerini arşivlemek için bağlayıcı ayarlama

Sohbet, ek, dosya, silinmiş Microsoft 365 uyumluluk merkezi ve çağrıları içeri aktararak arşivlemek için İleti İletisi bağlayıcısı'nın kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı kuruluşun TeleMessage hesabına bağlanır ve TeleMessage Signal Archiver'ı kullanan çalışanların mobil iletişimini Microsoft 365.

Sinyal Arşivleyici bağlayıcı verileri kullanıcı posta kutularında depolanıyorsa, Sinyal iletişim verilerine Mahkeme Microsoft 365, İçerik araması ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik aramalarını kullanarak Signal communication'da arama veya Sinyal Arşivleyici bağlayıcısı verilerini içeren posta kutusunu bir posta kutusunda bir özel dosyayla Advanced eDiscovery iş ortağınız olabilir. Verileri başka bir e-postada içeri aktararak ve Microsoft 365 için Sinyal Arşivleyici bağlayıcısı kullanmak Microsoft 365 kurumsal yönetim düzenlemeleri ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-signal-communications-data"></a>Signal iletişim verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Yeni E-posta'da Signal iletişim verilerini arşivlemek için bağlayıcı Microsoft 365.

![Signal communications archiving workflow.](../media/SignalConnectorWorkflow.png)

1. Your organization works with TeleMessage to set a Signal Archiver connector. Daha fazla bilgi için bkz[. Daha fazla bilgi için TeleMessage Sinyal Arşivleyicisi'Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. Gerçek zamanlı olarak, kuruluş sinyali verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturduktan sonra Sinyal Arşivleyicisi bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde e-posta iletilerini Microsoft Bulut'ta güvenli bir Azure Depolama alanına gönderir.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda Sinyal Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Eşlemeyi Kullanıcının E-posta *adresi özelliğini kullanarak* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, Kullanıcının mobil Numarasını ve her kullanıcı için Microsoft 365 posta kutusu adresini içermeli. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının mobil numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı, e-posta öğesinin Kullanıcı 'nın e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Sinyal Arşivleyicisi hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage hesabında Signal arşivlemesi gereken tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Sinyal Arşivleyici uygulamasını çalışanlarının cep telefonlarına yükleyin ve etkinleştirin. Signal Archiver uygulaması diğer Signal kullanıcıleriyle iletişim kurmalarını ve sohbetlerini sağlar.

- 3. Adımda Sinyal Arşivleyicisi bağlayıcısı oluşturan kullanıcıya, KaynakTaktör'de Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-signal-archiver-connector"></a>Sinyal Arşivleyici bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, çalışma sayfalarında Sinyal Arşivleyicisi bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, telemessage sitesine bağlanmak için sizin sağladınız bilgileri kullanır ve Sinyal iletişim verilerini İleti'de ilgili kullanıcı posta kutusu kutularına Microsoft 365.

1. Veri bağlayıcılarıSignal <https://compliance.microsoft.com> **Archiver'a gidin** >  **ve bu öğeye tıklayın**.

2. Sinyal **Arşivleyicisi ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın.**

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
