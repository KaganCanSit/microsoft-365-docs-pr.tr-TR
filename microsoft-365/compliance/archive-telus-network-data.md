---
title: Microsoft 365'te TELUS Ağ verilerini arşivleye bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Yöneticiler, Microsoft 365'teki TELUS Ağı'ndan SMS verilerini içeri aktarmak ve arşiv etmek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu sayede Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivleyebilir, böylece kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 215f185aa655f031151799f77889976bca799766
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628957"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>TELUS Ağ verilerini arşivleye bağlayıcı ayarlama

Kuruluşunuzun TELUS Ağından Kısa Microsoft Mesajlaşma Hizmeti (SMS) verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı TeleMessage bağlayıcısını kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun TELUS Ağına bağlanır ve SMS verilerini Microsoft 365'teki posta kutularına aktarır.

SMS iletileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini TELUS verilerine uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak TELUS SMS iletilerinde arama yapabilir veya TELUS verilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken TELUS Ağ bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-telus-network-data"></a>TELUS Ağ verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te TELUS Ağ verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![TELUS Ağ arşivleme iş akışı.](../media/TelusNetworkConnectorWorkflow.png)

1. Kuruluşunuz TeleMessage ve TELUS ile birlikte çalışarak bir TELUS Ağ bağlayıcısı ayarlar. Daha fazla bilgi için bkz. [TELUS Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. Gerçek zamanlı olarak, kuruluşunuzun TELUS Ağından gelen SMS iletileri TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz TELUS Ağ bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki SMS iletilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca SMS iletilerinin içeriğini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **TELUS SMS Ağ Arşivleyicisi** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak eşleme yapar. Her SMS iletisi, SMS iletisinin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

   *Kullanıcının E-posta adresi* özelliğinin değerini kullanan otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek de özel eşleme uygulayabilirsiniz. Bu eşleme dosyası, kuruluşunuzdaki kullanıcılar için cep telefonu numarasını ve buna karşılık gelen Microsoft 365 e-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirseniz, her TELUS öğesi için bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğindeki değerleri kullanır. Bağlayıcı, özel eşleme dosyasında veya TELUS öğesinin e-posta adresi özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

TELUS Ağ verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365'in dışındadır ve uyumluluk merkezinde bağlayıcı oluşturabilmeniz için önce tamamlanması gerekir.

- [TeleMessage'dan TELUS Ağ Arşivleyicisi hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- TeleMessage ekleme formlarını doldurabilmeniz ve ileti arşivleme hizmetini TELUS'tan sipariş edebilmeniz için TELUS Ağ hesabınızın ve faturalama iletişim bilgilerinizi alın.

- TELUS SMS Ağı arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Çalışanlarınızın,TELUS mobil ağında şirkete ait ve şirkete ait cep telefonlarına sahip olması gerekir. Microsoft 365'te iletileri arşivleme, çalışana ait veya Kendi Cihazlarını Getir (KCG) cihazlarında kullanılamaz.

- TELUS Ağ bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-telus-network-connector"></a>TELUS Ağ bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra, uyumluluk portalında TELUS Ağ bağlayıcısı oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak ve SMS iletilerini Microsoft 365'teki ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcıları** > **TELUS Ağı'na**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **TELUS Ağ** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **TeleMessage'da Oturum Aç** sayfasındaki 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.

   - **Username:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra açılır pencereyi kapatabilir ve sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme sayfasında, otomatik kullanıcı **eşlemesini** etkinleştirin ve **İleri'ye** tıklayın. Özel eşlemeye ihtiyacınız olması durumunda bir CSV dosyasını karşıya yükleyin ve **İleri'ye** tıklayın.

7. Ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları sayfasındaki Bağlayıcılar** sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
