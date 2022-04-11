---
title: Microsoft 365'da Telegram iletişim verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Telegram iletişim verilerini Microsoft 365 içeri aktarmak ve arşivlerken kullanmak için telemessage bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: e44eaa160bc78015191d2ceaca99bebbd31462fc
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64762089"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Telegram iletişim verilerini arşivleye bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi TeleMessage bağlayıcısını kullanarak Telegram sohbetlerini, eklerini, dosyalarını ve silinen iletileri ve aramaları içeri aktarın ve arşivleyin. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, kuruluşunuzun TeleMessage hesabına bağlanır ve Telegram Arşivleyicisi'ni kullanan çalışanların mobil iletişimini Microsoft 365'deki posta kutularına aktarır.

Telegram Arşivleyici bağlayıcısı verileri kullanıcı posta kutularında depolandıktan sonra, Telegram iletişim verilerine Dava Tutma, İçerik arama ve Microsoft 365 saklama ilkeleri gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak Telegram iletişiminde arama yapabilir veya Telegram Archiver bağlayıcı verilerini içeren posta kutusunu Advanced eDiscovery durumdaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için Telegram Arşivleyici bağlayıcısı kullanmak, kuruluşunuzun kurumsal idare düzenlemeleri ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-telegram-communications-data"></a>Telegram iletişim verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakış, Microsoft 365'de Telegram iletişim verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![Telegram iletişim arşivleme iş akışı.](../media/TelegramConnectorWorkflow.png)

1. Kuruluşunuz TeleMessage ile birlikte çalışarak bir Telegram Arşivleyici bağlayıcısı ayarlar. Daha fazla bilgi için bkz[. Microsoft 365 için TeleMessage Telegram Arşivleyicisi'ni etkinleştirme](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. Gerçek zamanlı olarak, kuruluşunuzun Telegram verileri TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi oluşturduğunuz Telegram Archiver bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki e-posta iletilerini Microsoft Cloud'daki güvenli bir Azure Depolama alanına aktarır.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda Telegram Archiver adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her e-posta iletisi, e-posta iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

> *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası Kullanıcının cep telefonu numarasını ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, e-posta öğesinin Kullanıcının e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya kullanıcının *e-posta öğesinin e-posta adresi* özelliğinde geçerli bir Microsoft 365 kullanıcı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Telegram arşivleme hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- Telegram arşivleme gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Telegram Archiver uygulamasını çalışanlarınızın cep telefonlarına yükleyin ve etkinleştirin. Telegram Archiver uygulaması, diğer Telegram kullanıcılarıyla iletişim kurmalarına ve sohbet etmelerine olanak tanır.

- 3. Adımda Telegram Arşivleyici bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-telegram-archiver-connector"></a>Telegram Arşivleyici bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra, Microsoft 365 uyumluluk merkezi Telegram Arşivleyici bağlayıcısını oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak için sağladığınız bilgileri kullanır ve Telegram iletişim verilerini Microsoft 365'deki ilgili kullanıcı posta kutusu kutularına aktarır.

1. **Telegram Archiver** > **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Telegram Arşivleyici** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **TeleMessage'da Oturum Aç** sayfasındaki 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.

    - **Username:** TeleMessage kullanıcı adınız.

    - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra açılır pencereyi kapatabilir ve sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme sayfasında otomatik kullanıcı **eşlemesini** etkinleştirin. Özel eşlemeyi etkinleştirmek için, kullanıcı eşleme bilgilerini içeren bir CSV dosyasını karşıya yükleyin ve **İleri'ye** tıklayın.

7. Ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları sayfasındaki Bağlayıcılar** sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
