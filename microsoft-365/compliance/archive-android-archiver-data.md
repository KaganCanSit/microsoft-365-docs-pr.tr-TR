---
title: Android mobil verilerini arşivlemek için bağlayıcı ayarlama
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
description: Yöneticiler, Android cep telefonlarından SMS, MMS ve sesli aramaları içeri aktarmanız ve arşivlemek için bir TeleMessage bağlayıcısı kurabilirsiniz. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: b24ab6a39da645b3e17d1319a31e6398fb6b3c6a
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021540"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data"></a>Android mobil verilerini arşivlemek için bağlayıcı ayarlama

Android cep telefonlarından SMS, MMS, sesli Microsoft 365 uyumluluk merkezi ve arama günlüklerini içeri aktarın ve arşivleyebilirsiniz. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı her gün kuruluşun TeleMessage hesabına bağlanır ve TeleMessage Android Arşivleyici'yi kullanan çalışanların mobil iletişimini Microsoft 365.

Android cep telefonlarından veriler kullanıcı posta kutularında depolendikten sonra, Android Arşivleyici verilerine Microsoft 365 Bekletme, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Android Arşivleyici mobil iletişiminde arama veya Android Archiver bağlayıcı verilerini içeren posta kutusunu bir özel durum durumunda bir özel dosya Advanced eDiscovery ilişkilendirilebilirsiniz. Android Archiver bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 bu uygulama, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-android-mobile-data"></a>Android mobil verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Android mobil verilerini mobil cihazlarda arşivlemek için bağlayıcı kullanma Microsoft 365.

![Android Arşivleyici bağlayıcısı iş akışı.](../media/AndroidArchiverConnectorWorkflow.png)

1. Your organization works with TeleMessage to set an Android Archiver connector. Daha fazla bilgi için [bkz. Android Arşivleyici](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. Gerçek zamanlı olarak, sms, MMS, sesli arama ve arama günlükleri kurumnizin Android cep telefonlarından TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız, Android Arşivleyici bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde alınan Android verilerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Bağlayıcı, Android verilerini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda Android Arşivleyici adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Kullanıcının E-posta adresi *özelliğinin değerini kullanarak eşleme* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir. Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, her kullanıcı için cep telefonu numarasını Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının cep telefonu numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı kullanıcının e-posta öğesi e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı  bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Android iletişim verilerini arşivlemek için gereken bazı uygulama adımları Microsoft 365'nin dışındadır ve uyumluluk merkezinde bağlayıcıyı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan Android Arşivleyici hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Bağlayıcıyı  oluşturmadan önce bu hesapta oturum açın.

- TeleMessage hesabında Android Arşivleyici hizmeti gerektiren tüm kullanıcıları kaydetme. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarının cep telefonlarına TeleMessage Android Archiver uygulamasını yükleyin ve etkinleştirin.

- Android Arşivleyici bağlayıcısı oluşturan kullanıcıya, Çalışma Alanı içinde Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Bunun için, sayfanın en son **sayfasındaki Veri bağlayıcıları** sayfasına bağlayıcı Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-an-android-archiver-connector"></a>Android Arşivleyici bağlayıcısı oluşturma

Son adım, mobil cihazlarda bir Android Arşivleyici bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, TeleMessage sitesine bağlanmak ve Android iletişimini İleti'deki ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcılarıAndroid [https://compliance.microsoft.com](https://compliance.microsoft.com) **Arşivleyicisi'ne** >  **gidin ve tıklayın**.

2. **Android Arşivleyici ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **TeleMessage'da Oturum Aç** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

   - **Kullanıcı adı:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra, açılır pencereyi kapatın ve Sonraki'ye **tıklayın**.

6. Kullanıcı eşleme **sayfasında, otomatik** kullanıcı eşlemesini etkinleştirin ve Ardından'ya **tıklayın**. Özel eşlemeye ihtiyacınız olursa, CSV dosyasını karşıya yükleyin ve İleri'ye **tıklayın**.

7. Ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için Son'a** tıklayın.

8. Yeni bağlayıcı için içeri aktarma **işleminin ilerlemesini** görmek için Veri bağlayıcıları sayfasındaki Bağlayıcılar sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
