---
title: Microsoft 365'de Signal iletişim verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Signal iletişim verilerini Microsoft 365 içeri aktarmak ve arşivlemek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 5e075b643cf4e9ba339f1f30f968f935336c07c3
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992644"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Sinyal iletişim verilerini arşivleye bir bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Sinyal sohbetlerini, eklerini, dosyalarını ve silinen iletileri ve çağrıları içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalındaki TeleMessage bağlayıcısını kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, kuruluşunuzun TeleMessage hesabına bağlanır ve TeleMessage Sinyal Arşivleyicisi'ni kullanarak çalışanların mobil iletişimini Microsoft 365'deki posta kutularına aktarır.

Signal Archiver bağlayıcısı verileri kullanıcı posta kutularında depolandıktan sonra, Signal iletişim verilerine Dava Tutma, İçerik arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, İçerik aramasını kullanarak Sinyal iletişiminde arama yapabilir veya Signal Archiver bağlayıcı verilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için Sinyal Arşivleyici bağlayıcısı kullanmak, kuruluşunuzun kurumsal idare düzenlemeleri ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-signal-communications-data"></a>Sinyal iletişim verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'de Signal iletişim verilerini arşivleyen bir bağlayıcı kullanma işlemini açıklar.

![Sinyal iletişimleri arşivleme iş akışı.](../media/SignalConnectorWorkflow.png)

1. Kuruluşunuz Bir Signal Archiver bağlayıcısı ayarlamak için TeleMessage ile birlikte çalışır. Daha fazla bilgi için bkz[. Microsoft 365 için TeleMessage Signal Archiver'ı etkinleştirme](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. Kuruluşunuzun Sinyal verileri gerçek zamanlı olarak TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz Signal Archiver bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki e-posta iletilerini Microsoft Bulutu'ndaki güvenli bir Azure Depolama alanına aktarır.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda Signal Archiver adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *eşlemeyi Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her e-posta iletisi, e-posta iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

   *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası Kullanıcının cep telefonu numarasını ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, e-posta öğesinin Kullanıcının e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya kullanıcının *e-posta öğesinin e-posta adresi* özelliğinde geçerli bir Microsoft 365 kullanıcı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Signal Archiver hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- Sinyal arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Signal Archiver uygulamasını çalışanlarınızın cep telefonlarına yükleyin ve etkinleştirin. Signal Archiver uygulaması, diğer Signal kullanıcılarıyla iletişim kurmalarını ve sohbet etmelerini sağlar.

- 3. Adımda Sinyal Arşivleyici bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-signal-archiver-connector"></a>Sinyal Arşivleyici bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra uyumluluk portalında Signal Archiver bağlayıcısını oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak için sağladığınız bilgileri kullanır ve Signal iletişim verilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarır.

1. **Veri bağlayıcılarıSeç** >  **arşivleyici'ye**<https://compliance.microsoft.com> gidin ve tıklayın.

2. **Signal Archiver** ürün açıklaması sayfasında **Bağlayıcı ekle'ye tıklayın.**

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
