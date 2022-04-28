---
title: AT&T SMS/MMS Ağ verilerini arşivecek bir bağlayıcı ayarlama
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
description: Yöneticiler, AT&T Mobil Ağı'ndan SMS ve MMS verilerini içeri aktarmak ve arşiv etmek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için Microsoft Purview'daki üçüncü taraf veri kaynaklarından verileri arşivlemenizi sağlar.
ms.openlocfilehash: 7d73e6a5e5a5190609cd50bd055af8b7aec969b7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093185"
---
# <a name="set-up-a-connector-to-archive-att-smsmms-data"></a>AT&T SMS/MMS verilerini arşivleye bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

AT&T Mobile Network'ten SMS ve MMS verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir TeleMessage bağlayıcısı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun AT&T Ağına bağlanır ve SMS ve MMS verilerini Microsoft Purview'daki posta kutularına aktarır.

SMS ve MMS iletileri kullanıcı posta kutularında depolandıktan sonra,&T Ağ verilerine Dava Tutma, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft 365 Purview özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak AT&T Ağ verilerinde arama yapabilir veya AT&T Ağ bağlayıcısı verilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlerken AT&T Ağ bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-att-network-data"></a>AT&T Ağ verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'da AT&T Ağ verilerini arşiv etmek için bağlayıcı kullanma işlemini açıklar.

![ATT Ağ arşivleme iş akışı.](../media/ATTNetworkConnectorWorkflow.png)

1. Kuruluşunuz TeleMessage ile birlikte çalışarak BIR AT&T Ağı bağlayıcısı ayarlar. Bilgi için bkz [. AT&T Ağ Arşivleyicisi](https://www.telemessage.com/office365-activation-for-atnt-network-archiver/).

2. Gerçek zamanlı olarak, kuruluşunuzun AT&T Ağından gelen SMS ve MMS iletileri TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz AT&T Ağ bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki SMS ve MMS iletilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca SMS ve MMS iletilerinin içeriğini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli kullanıcıların posta kutusuna aktarır. Kullanıcının posta kutusunda **AT&T SMS/MMS Ağ Arşivleyicisi** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bu eşlemeyi *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak yapar. Her SMS ve MMS iletisi, iletinin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.
 
   *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, kuruluşunuzdaki kullanıcılar için cep telefonu numarasını ve ilgili Microsoft 365 e-posta adresini içerir. Hem otomatik kullanıcı eşlemesini hem de özel eşlemeyi etkinleştirirseniz, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Bir cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı içeri aktarmaya çalıştığı öğenin e-posta adresi özelliğindeki değerleri kullanır. Bağlayıcı, özel eşleme dosyasında veya e-posta öğesinin e-posta adresi özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-begin"></a>Başlamadan önce

AT&T Ağ verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365 dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- [TeleMessage'dan mobil arşivleyici hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Uyumluluk merkezinde bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- TELEMessage ekleme formlarını doldurabilmek ve at&T'den ileti arşivleme hizmetini sipariş edebilmek için AT&T hesabınızın ve faturalama iletişim bilgilerinizi alın.

- AT&T SMS/MMS Ağ arşivlemeyi gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Çalışanlarınızın AT&T mobil ağında şirkete ait ve şirkete ait cep telefonlarına sahip olması gerekir. Microsoft 365'da iletileri arşivleme, çalışana ait veya "Kendi Cihazlarını Getir (KCG) cihazları için kullanılamaz.

- AT&T Ağ bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-a-att-network-connector"></a>AT&T Ağ bağlayıcısı oluşturma

Önceki bölümde açıklanan önkoşulları tamamladıktan sonra, uyumluluk portalında bir AT&T Ağ bağlayıcısı oluşturabilirsiniz. Bağlayıcı, TeleMessage sitesine bağlanmak ve SMS ve MMS iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcılarıAT** \  **&T Ağı'na**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **AT&T Ağ ürün** açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **TeleMessage'da Oturum Aç** sayfasındaki 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.

   - **Username:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra açılır pencereyi kapatabilir ve sonraki sayfaya gidebilirsiniz.

6. Kullanıcı eşleme sayfasında otomatik kullanıcı **eşlemesini** etkinleştirin. Özel eşlemeyi etkinleştirmek için, kullanıcı eşleme bilgilerini içeren bir CSV dosyasını karşıya yükleyin ve **İleri'ye** tıklayın.

7. Ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni **bağlayıcının** içeri aktarma işleminin ilerleme durumunu görmek için uyumluluk merkezindeki **Veri bağlayıcıları sayfasındaki Bağlayıcılar** sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
