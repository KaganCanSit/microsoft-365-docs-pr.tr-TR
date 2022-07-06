---
title: Android mobil verilerini arşivleye bağlayıcı ayarlama
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
description: Yöneticiler, Android cep telefonlarından SMS, MMS ve sesli aramaları içeri aktarmak ve arşivlendirmek için bir TeleMessage bağlayıcısı ayarlayabilir. Bu sayede Microsoft 365'teki üçüncü taraf veri kaynaklarından verileri arşivleyebilir, böylece kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 3fa2a8556b6974d457dc4f7b5d86413d31dc8386
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621633"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data"></a>Android mobil verilerini arşivleye bağlayıcı ayarlama

Android cep telefonlarından SMS, MMS, sesli aramalar ve arama günlüklerini içeri aktarmak ve arşivlerken Microsoft Purview uyumluluk portalı bir TeleMessage bağlayıcısı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun TeleMessage hesabına bağlanır ve TeleMessage Android Arşivleyicisi'ni kullanan çalışanların mobil iletişimini Microsoft 365'teki posta kutularına aktarır.

Android cep telefonlarındaki veriler kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, İçerik Arama ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini Android Arşivleyici verilerine uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak Android Arşivleyici mobil iletişiminde arama yapabilir veya Android Arşivleyici bağlayıcısı verilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlemek için Android Arşivleyici bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-android-mobile-data"></a>Android mobil verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te Android mobil verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![Android Arşivleyici bağlayıcısı iş akışı.](../media/AndroidArchiverConnectorWorkflow.png)

1. Kuruluşunuz Bir Android Arşivleyici bağlayıcısı ayarlamak için TeleMessage ile birlikte çalışır. Daha fazla bilgi için bkz. [Android Archiver](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. Gerçek zamanlı olarak, kuruluşunuzun Android cep telefonlarındaki SMS, MMS, sesli aramalar ve arama günlükleri TeleMessage sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz Android Arşivleyici bağlayıcısı her gün TeleMessage sitesine bağlanır ve önceki 24 saat içindeki Android verilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca Android verilerini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, mobil iletişim öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda Android Archiver adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak eşleme yapar. Her e-posta iletisi, e-posta iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir. *Kullanıcının E-posta adresi* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, her kullanıcı için cep telefonu numarasını ve buna karşılık gelen Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Kullanıcının cep telefonu numarasına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı kullanıcının e-posta öğesinin e-posta adresi özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya *e-posta öğesinin Kullanıcının e-posta adresi* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Android iletişim verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365'in dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- [TeleMessage'dan Android Archiver hizmetini](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) sipariş edin ve kuruluşunuz için geçerli bir yönetim hesabı alın. Bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- Android Archiver hizmetini gerektiren tüm kullanıcıları TeleMessage hesabına kaydedin. Kullanıcıları kaydederken, Microsoft 365 hesapları için kullanılan e-posta adresini kullandığınızdan emin olun.

- Çalışanlarınızın cep telefonlarına TeleMessage Android Archiver uygulamasını yükleyin ve etkinleştirin.

- Android Arşivleyici bağlayıcısı oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu TeleMessage veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="create-an-android-archiver-connector"></a>Android Archiver bağlayıcısı oluşturma

Son adım, uyumluluk portalında bir Android Arşivleyici bağlayıcısı oluşturmaktır. Bağlayıcı, TeleMessage sitesine bağlanmak ve Android iletişimini Microsoft 365'teki ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. **Veri bağlayıcıları** > **Android Arşivleyicisi'ne**[https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Android Arşivleyici** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **TeleMessage'da Oturum Aç** sayfasındaki 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.

   - **Username:** TeleMessage kullanıcı adınız.

   - **Parola:** TeleMessage parolanız.

5. Bağlayıcı oluşturulduktan sonra açılır pencereyi kapatın ve **İleri'ye** tıklayın.

6. Kullanıcı eşleme sayfasında, otomatik kullanıcı **eşlemesini** etkinleştirin ve **İleri'ye** tıklayın. Özel eşlemeye ihtiyacınız olması durumunda bir CSV dosyasını karşıya yükleyin ve **İleri'ye** tıklayın.

7. Ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları sayfasındaki Bağlayıcılar** sekmesine gidin.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
