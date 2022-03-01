---
title: WeChat verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Web sayfalarında bir bağlayıcı ayarlayın ve Microsoft 365 uyumluluk merkezi WeChat verilerini içeri aktarın ve Microsoft 365.
ms.openlocfilehash: 5dec31d163c22a372ac7c43cfc6f3963bcc4b900
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021562"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>WeChat verilerini arşivlemek için bağlayıcı ayarlama

WeChat ve WeCom aramalarını, sohbetlerini, eklerini, dosyalarını ve geri çağırma iletilerini içeri aktarın ve Microsoft 365 uyumluluk merkezi teleMessage bağlayıcıyı kullanın. Bağlayıcıyı ayardikten ve yapılandırdikten sonra, bu bağlayıcı kuruluşun TeleMessage hesabına bağlanır ve TeleMessage WeChat Arşivleyicisi'i kullanarak çalışanların mobil iletişimini Microsoft 365.

WeChat Arşivleyicisi bağlayıcı verileri kullanıcı posta kutularında depolendikten sonra, WeChat iletişim verilerine Mahkeme Microsoft 365, eKbulma, In-Place Arşivleme, Denetim, İletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak WeChat iletişiminde arama veya WeChat Arşivleyici bağlayıcı verilerini içeren posta kutusunu bir özel olayda özel bir Advanced eDiscovery ilişkilendirilebilirsiniz. Verileri şirket içinde içeri ve arşivleye almak için WeChat Arşivleyici bağlayıcısı Microsoft 365 düzenleme düzenlemelerine ve mevzuat ilkelerine uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-wechat-communication-data"></a>WeChat iletişim verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, WeChat iletişim verilerini aynı tabloda arşivlemek için bağlayıcı kullanma Microsoft 365.

![WeChat Arşivleyici verileri için arşivleme iş akışı.](../media/WeChatConnectorWorkflow.png)

1. Your organization works with TeleMessage to set a WeChat Archiver connector.

2. Gerçek zamanlı olarak, kuruluşa ait WeChat verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta 24 saat içinde 24 saat içinde oluşturulan WeChat Arşivleyicisi bağlayıcısı, TeleMessage sitesine bağlanır ve önceki 24 saat içinde gönderilen e-posta iletilerini Microsoft Bulut'un güvenli bir Azure Depolama alanına aktarıyor.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda WeChat Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, Kullanıcının E-posta adresi *özelliğinin değerini kullanarak eşleme* yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir. Kullanıcının E-posta adresi özelliğinin değerini kullanarak otomatik kullanıcı  eşlemeye ek olarak, CSV eşleme dosyası yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, Kullanıcının mobil Numarasını ve her kullanıcı için Microsoft 365 posta kutusu adresini içermeli. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşlemesi olur. Kullanıcının mobil numarasına karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı, e-posta öğesinin Kullanıcı 'nın e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 e-posta öğesinin e-posta adresi özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- WeChat arşiv bağlayıcısı ayarlamak için TeleMessage ile çalışma. Daha fazla bilgi için bkz[. Daha fazla bilgi için TeleMessage WeChat Arşivleyicisi'Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- E-posta için bir TeleMessage Microsoft 365 ayarlayın ve geçerli bir şirket yönetim hesabı açın. Daha fazla bilgi için bkz[. Mobil Arşivleme'Microsoft 365 Sıralama](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/).

- TeleMessage hesabında WeChat arşivlemesi gerektiren tüm kullanıcıları, kullanıcının hesaplarında kullanılan e-posta adresiyle Microsoft 365.

- Tencent WeCom uygulamasını kurumuz kullanan kullanıcıların cep telefonlarına yüklemeniz ve etkinleştirmeniz gerekir. WeCom uygulaması, kullanıcıların diğer WeChat ve WeCom kullanıcıleriyle iletişim kurmasına ve sohbet kurmasına olanak sağlar.

- Dosya kutusunda bir WeChat Arşivleyici bağlayıcısı oluşturan Microsoft 365 uyumluluk merkezi Kutusunda Posta Kutusu İçeri/Dışarı Aktarma rolüne Exchange Online. Bu, uyumluluk merkezinin Veri **bağlayıcıları sayfasında bağlayıcı** eklemek için gereklidir. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu TeleMessage veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="create-a-wechat-archiver-connector"></a>WeChat Arşivleyicisi bağlayıcısı oluşturma

Bu bölümdeki adımları takip edin ve arşiv kısmında bir WeChat Arşivleyicisi Microsoft 365 uyumluluk merkezi. Bağlayıcı, teleMessage sitesine bağlanmak ve WeChat iletişim verilerini E-Posta'da ilgili kullanıcı posta kutularına aktarımı için Microsoft 365.

1. Veri bağlayıcılarıWeChat <https://compliance.microsoft.com> **Arşivleyicisi'ne** >  **gidin ve bu öğeye tıklayın**.

2. **WeChat Arşivleyicisi ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **TeleMessage'da Oturum Aç** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

    - **Kullanıcı** Adı: TeleMessage kullanıcı adınız.

    - **Parola**: TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra, sonraki sayfaya gitmek için açılır pencereyi kapatabilirsiniz.

6. Kullanıcı eşleme **sayfasında** , otomatik kullanıcı eşlemesini etkinleştirin. Csv dosyasına özel bir kullanıcı eşlemesi de yükleyebilirsiniz.

7. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

8. Yeni bağlayıcı **için** içeri aktarma **işleminin ilerlemesini** görmek için Veri bağlayıcıları sayfasındaki Bağlayıcılar sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
