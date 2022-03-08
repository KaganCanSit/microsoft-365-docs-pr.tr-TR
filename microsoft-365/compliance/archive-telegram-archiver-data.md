---
title: Her ikisinde de Zaman iletişim verilerini arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, her ikisinde de İleti iletişim verilerini içeri aktaracak ve arşivlecek bir TeleMessage bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 2fbe0a97572d13b6d2ba6e26ac02fd5ee8817b8a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312299"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Zaman iletişim verilerini arşivlemek için bağlayıcı ayarlama

Sohbetleri, ekleri, dosyaları, Microsoft 365 uyumluluk merkezi ve silinen iletileri ve aramaları içeri aktararak arşivlemek için, videonun içinde TeleMessage bağlayıcıyı kullanın. Siz bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı kuruluşun TeleMessage hesabına bağlanır ve Archiver'ı kullanan çalışanların mobil iletişimini Arşivleyici'deki posta kutularına Microsoft 365.

Arşivleyici bağlayıcı verileri kullanıcı posta kutularında depolendikten sonra, Microsoft 365 iletişim verilerine Mahkeme Tutma, İçerik araması ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Yalnız iletişiminde arama veya Arşivleyici bağlayıcısı verilerini içeren posta kutusunu bir olayda bir özel dosyayla Advanced eDiscovery. Verileri şirket içinde içeri aktararak veya arşivlenen bir Arşivleyici bağlayıcısı kullanmak Microsoft 365 düzenleme düzenlemelerine ve mevzuat ilkelerine uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-telegram-communications-data"></a>Communications iletişim verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Bağlayıcı kullanarak Communications iletişim verilerini aynı dosyada arşivleme işlemi Microsoft 365.

![Uzun iletişim arşivleme iş akışı.](../media/TelegramConnectorWorkflow.png)

1. Your organization works with TeleMessage to set a Archiver connector. Daha fazla bilgi için bkz[. Daha Fazla Bilgi için TeleMessage İleti Arşivleyicisi'Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. Gerçek zamanlı olarak, kuruluşa Ait Zaman'ın verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Archiver bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde gönderilen e-posta iletilerini Microsoft Bulut'un güvenli bir Azure Depolama alanına aktarıyor.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda Arşivleyici adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

> Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, Kullanıcının mobil Numarasını ve her kullanıcı için Microsoft 365 posta kutusu adresini içermeli. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının mobil numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı, e-posta öğesinin Kullanıcı 'nın e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Arşivleme arşivleme hizmetini sipariş etmek ve](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TeleMessage hesabında Arşivleme gerektiren tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarının cep telefonlarına Arşivleyici uygulamasını yükleyin ve etkinleştirin. Archive Archiver uygulaması diğer Kullanıcılarla iletişim kurmalarına ve sohbetlerine olanak sağlar.

- 3. Adımda Bir Arşivleyici Bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-telegram-archiver-connector"></a>Arşivleyici bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, Arşivleyici'de Arşivleyici bağlayıcısı'nın Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak için sizin sağlayınız bilgileri kullanır ve her ikisinde de Bire bir'deki ilgili kullanıcı posta kutusu kutularına İleti iletişim Microsoft 365.

1. Veri bağlayıcıları <https://compliance.microsoft.com> ve Diyagram **Arşivleyicisi'ne** > **gidin ve tıklayın**.

2. Arşivleyici **ürün açıklaması sayfasında** Bağlayıcı **ekle'ye tıklayın**.

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
