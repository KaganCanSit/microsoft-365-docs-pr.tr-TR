---
title: T SMS/MMS Ağ verilerini&için bağlayıcıyı ayarlama
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
description: Yöneticiler, AT&T Mobile Network'te SMS ve MMS verilerini içeri aktaracak ve arşivley edebilecek bir TeleMessage&kurabilirsiniz. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 2b1e03c4d434b08c3dce21ed42c24e4573513c24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322219"
---
# <a name="set-up-a-connector-to-archive-att-smsmms-data"></a>T SMS/MMS verilerini&için bağlayıcıyı ayarlama

AT&T Mobile Network'Microsoft 365 uyumluluk merkezi SMS ve MMS verilerini içeri aktararak arşivlemek için, iletişim&kullanın. Bir bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı her gün kuruluşta AT&T Ağı'ne bağlanır ve SMS ve MMS verilerini aynı anda posta kutularına Microsoft 365.

SMS ve MMS iletileri kullanıcı posta kutularında depolanıyorsa, AT Microsoft 365 T Ağ verilerine Mahkeme Tutma, İçerik Arama Microsoft 365 bekletme ilkeleri gibi uyumluluk&uygulayabilirsiniz. Örneğin, İçerik Arama'&KULLANARAK AT&T Ağ verileri için arama veya AT&T Ağ bağlayıcısı verilerini içeren posta kutusunu bir özel durum durumunda bir özel dosya Advanced eDiscovery ilişkilendirilebilirsiniz. AT&T Network bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-att-network-data"></a>AT ve T Ağ&arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı kullanarak AT ve T Ağ&arşivleme işlemi Microsoft 365.

![ATT Network arşivleme iş akışı.](../media/ATTNetworkConnectorWorkflow.png)

1. Your organization works with TeleMessage to set an AT&T Network connector. Bilgi için bkz. [AT&T Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-atnt-network-archiver/).

2. Gerçek zamanlı olarak, kuruluşun AT veya T Ağı'&SMS ve MMS iletileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'te oluştursanız AT&T Network bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içinde alınan SMS ve MMS mesajlarını Microsoft bulutunda güvenli bir Azure Depolama konuma iletir. Bağlayıcı SMS ve MMS iletilerinin içeriğini de e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli kullanıcıların posta kutusuna içeri aktarıyor. Kullanıcının posta kutusunda **AT&T SMS/MMS Ağ** Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi Kullanıcının E-posta *adresi özelliğinin değerini kullanarak* yapar. Her SMS ve MMS iletisi, iletinin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.
 
   Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, cep telefonu numarasını ve bunun Microsoft 365-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirsanız, bağlayıcı önce özel eşleme dosyasına bakarak her e-posta öğesine bakır. Kullanıcı bir cep telefonu numarasına Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğinde yer alan değerleri kullanır. Bağlayıcı, kullanıcıya özel Microsoft 365 veya e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-begin"></a>Başlamadan önce

AT&T Network verilerini arşivlemek için gereken bazı uygulama adımları Microsoft 365'nin dışındadır ve uyumluluk merkezinde bağlayıcıyı oluşturamadan önce tamamlanması gerekir.

- [TeleMessage'dan mobil arşivleyici hizmetini sipariş](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) etmek ve organizasyonunız için geçerli bir yönetim hesabı almak. Uyumluluk merkezinde bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- TEMessage ekleme&doldurmak ve AT&T'den ileti arşivleme hizmetini sipariş etmek için AT&T hesabı ve fatura kişi ayrıntılarınızı alın.

- TELEMessage hesabında AT veya T SMS&MMS Ağ arşivlemesi gerektiren tüm kullanıcıları kaydettirin. Kullanıcıları kaydettirerek, kendi hesaplarında kullanılan e-posta adresinin aynısını Microsoft 365.

- Çalışanlarınızı AT&T mobil ağına şirket kullanımına bağlı ve kurumsal olarak sorumlu cep telefonları olmalıdır. İletileri Tek Microsoft 365, çalışana ait "Kendi Cihazlarınızı Getirin (BYOD) cihazlarında kullanılamaz.

- T Ağ bağlayıcısı için AT&kullanıcıya Veri Bağlayıcısı Yönetici rolü atan olmalıdır. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-att-network-connector"></a>AT&T Network bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamlandıktan sonra, üst bölümde bir AT&T Network bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve SMS ve MMS mesajlarını İleti'de ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcılarıAT [https://compliance.microsoft.com](https://compliance.microsoft.com/) ve **T Ağı'&** \  **tıklayın**.

2. AT&**T Ağ ürün açıklaması sayfasında** Bağlayıcı ekle'ye **tıklayın**

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
