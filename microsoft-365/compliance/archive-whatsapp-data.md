---
title: Microsoft 365'te WhatsApp verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'te WhatsApp verilerini içeri aktarmak ve arşiv etmek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu sayede Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivleyebilir, böylece kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: cf596cd4c48e68759321f4f477ef387c7e8cfc74
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637715"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>WhatsApp verilerini arşivleye bağlayıcı ayarlama

WhatsApp çağrılarını, sohbetleri, ekleri, dosyaları ve silinen iletileri içeri aktarmak ve arşiv etmek için Microsoft Purview uyumluluk portalı TeleMessage bağlayıcısını kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun TeleMessage hesabına bağlanır ve TeleMessage WhatsApp Phone Archiver veya TeleMessage WhatsApp Cloud Archiver'ı kullanarak çalışanların mobil iletişimini Microsoft 365'teki posta kutularına aktarır.

WhatsApp verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, İçerik araması ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini WhatsApp verilerine uygulayabilirsiniz. Örneğin, İçerik aramasını kullanarak WhatsApp iletilerinde arama yapabilir veya WhatsApp iletilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken WhatsApp bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-whatsapp-data"></a>WhatsApp verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te WhatsApp verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![WhatsApp arşivleme iş akışı.](../media/WhatsAppConnectorWorkflow.png)

1. Kuruluşunuz, WhatsApp Archiver bağlayıcısı ayarlamak için TeleMessage ile birlikte çalışır. Daha fazla bilgi için bkz [. WhatsApp Archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. Gerçek zamanlı olarak, kuruluşunuzun WhatsApp verileri TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz WhatsApp bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki WhatsApp verilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca içeriği WhatsApp verilerini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, WhatsApp verilerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **WhatsApp Archiver** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her WhatsApp iletisi, iletinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

   *Kullanıcının E-posta adresi* özelliğinin değerini kullanan otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek de özel eşleme uygulayabilirsiniz. Bu eşleme dosyası, kuruluşunuzdaki kullanıcılar için cep telefonu numarasını ve buna karşılık gelen Microsoft 365 e-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirseniz, her WhatsApp öğesi için bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğindeki değerleri kullanır. Bağlayıcı, özel eşleme dosyasında veya WhatsApp öğesinin e-posta adresi özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

WhatsApp iletişim verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365'in dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- [WhatsApp Archiver hizmetini TeleMessage'dan](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- WhatsApp arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- TeleMessage [WhatsApp Phone Archiver uygulamasını](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) çalışanlarınızın cep telefonlarına yükleyin ve etkinleştirin. Alternatif olarak, çalışanlarınızın cep telefonlarına normal WhatsApp veya WhatsApp Business uygulamalarını yükleyebilir ve TeleMessage web sitesindeki bir QR kodunu tarayarak WhatsApp Cloud Archiver hizmetini etkinleştirebilirsiniz. Daha fazla bilgi için bkz [. WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Verizon Ağ bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-whatsapp-archiver-connector"></a>WhatsApp Archiver bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra uyumluluk portalında WhatsApp bağlayıcısını oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak ve WhatsApp verilerini Microsoft 365'teki ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcıları** > **WhatsApp Archiver'a**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **WhatsApp Archiver** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

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
