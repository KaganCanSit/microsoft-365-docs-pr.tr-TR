---
title: Microsoft 365'da Rogers Network verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'da Rogers Network verilerini içeri aktarmak ve arşivlemek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 54c57c2ddf8d4224884137efb0cfa4679a13b46d
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758717"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Rogers Network verilerini arşivleye bir bağlayıcı ayarlama

Rogers mobil ağından SMS ve MMS verilerini içeri aktarmak ve arşivlemek için Microsoft 365 uyumluluk merkezi TeleMessage bağlayıcısını kullanın. [Rogers Network Archiver bağlayıcısını](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/) ayarlayıp yapılandırdıktan sonra kuruluşunuzun Rogers mobil ağına bağlanır ve SMS ve MMS verilerini Microsoft 365'deki posta kutularına aktarır.

Rogers mobil ağındaki veriler kullanıcı posta kutularında depolandıktan sonra, dava tutma, İçerik arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft 365 uyumluluk özelliklerini verilere uygulayabilirsiniz. Örneğin, İçerik araması veya Core eKeşif olayıyla ilişkilendirilmiş bir arama kullanarak Rogers mobil ağından SMS ve MMS iletilerini arayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için Rogers Network Archiver bağlayıcısı kullanmak, kuruluşunuzun kurumsal idare düzenlemeleri ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Rogers mobil ağ verilerini arşivleme hakkında genel bakış

Aşağıdaki genel bakış, Microsoft 365'de Rogers SMS ve MMS verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![Rogers Ağ arşivleme iş akışı.](../media/RogersNetworkConnectorWorkflow.png)

1. Kuruluşunuz, Rogers Network Archiver bağlayıcısı ayarlamak için TeleMessage ile birlikte çalışır. Daha fazla bilgi için bkz[. Microsoft 365 için TeleMessage Rogers Ağ Arşivleyicisi'ni etkinleştirme](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. Kuruluşunuzun Rogers mobil ağ verileri gerçek zamanlı olarak TeleMessage sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi oluşturduğunuz Rogers Ağ Arşivleyicisi bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki e-posta iletilerini Microsoft Cloud'daki güvenli bir Azure Depolama alanına aktarır.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda Rogers SMS/MMS Ağ Arşivleyicisi adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *eşlemeyi Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her e-posta iletisi, e-posta iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

   *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası Kullanıcının cep telefonu numarasını ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı kullanıcının e-posta öğesinin e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya kullanıcının *e-posta öğesinin e-posta adresi* özelliğinde geçerli bir Microsoft 365 kullanıcı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- [TeleMessage'dan Rogers Network Archiver hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- Rogers Network arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Çalışanlarınızın O2 mobil ağında şirkete ait ve şirkete ait cep telefonlarına sahip olması gerekir. Microsoft 365'da iletileri arşivleme, çalışana ait veya "Kendi Cihazlarını Getir (KCG) cihazları için kullanılamaz.

- Ekleme formlarını tamamlayabilmeniz ve rogers'tan ileti arşivleme hizmetini sipariş edebilmeniz için kuruluşunuzun Rogers hesabı ve faturalama iletişim bilgilerini alın.

- 3. Adımda Rogers Ağ Arşivleyici bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-rogers-network-archiver-connector"></a>Rogers Network Archiver bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra, Microsoft 365 uyumluluk merkezi Rogers Ağ Arşivleyicisi bağlayıcısını oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak ve Rogers SMS/MMS verilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcılarıRogers** >  **Ağ Arşivleyicisi'ne**<https://compliance.microsoft.com> gidin ve tıklayın.

2. **Rogers Ağ Arşivleyicisi** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

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
