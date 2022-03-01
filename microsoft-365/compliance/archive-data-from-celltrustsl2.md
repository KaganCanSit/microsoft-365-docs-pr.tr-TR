---
title: CellTrust SL2 platformundan verileri arşivle ve Microsoft 365
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
description: Mobil iletişim verilerini içeri aktarma ve arşivlemek için CellTrust SL2 veri bağlayıcısı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: d1b0d651acb09ebe1a4fe2437ddd0434e48f9c2e
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021460"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>CellTrust SL2'den verileri arşivle'den Microsoft 365

CellTrust SL2, mobil iletişim verilerini yakalar ve FINRA, HIPAA, FOIA ve TCPA gibi yasal düzenlemelere ilişkin elektronik keşif gereksinimlerini karşılamak için önde gelen arşivleme teknolojileriyle tümleştirilmiştir. SL2 Veri Bağlayıcısı, mobil iletişim öğelerini bu öğelere Microsoft 365. Bu makalede, arşivleme için CellTrust SL2 Veri Bağlayıcısı'Microsoft 365 SL2 veri bağlayıcısı kullanarak SL2'yi veri kaynağıyla tümleştirme işlemi açıklanmıştır. Bu işlemi tamamlamak için CellTrust SL2 hizmetine abone olduğunuz ve SL2 mimarisini biliyor olmanız gerekir. CellTrust SL2 hakkında daha fazla bilgi için bkz.<https://www.celltrust.com>

Microsoft 365'ta kullanıcı posta kutularına veri aktarıldıktan sonra, Microsoft 365 Saklama, eBulma, Microsoft 365 bekletme ilkeleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir dosyada içeri aktararak ve arşivlenen CellTrust SL2 Veri Bağlayıcısı'nın Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>CellTrust SL2 Veri Bağlayıcısı ile arşivlemeye genel bakış

CellTrust'ın SL2 platformu, birden çok kaynakta yer alan iletişim verilerini yakalar. SL2 veri kaynakları, Kişiler'den Kişiye (P2P) veya Uygulamaya Göre (A2P) kaynaktır. Bu makalede açıklanan işlem yalnızca P2P veri kaynaklarıyla ilgilidir. Tüm P2P veri kaynakları için, işbirliğinde en az bir taraf SL2 hizmetine abone olan bir SL2 kullanıcısıdır. Aşağıdaki genel bakış makalesinde, aynı tabloda CellTrust SL2 Veri Bağlayıcısı'nın Microsoft 365.

![CellTrust SL2 hizmeti için iş akışı arşivleme.](../media/CellTrustSL2ConnectorWorkflow.png)

1. SL2 kullanıcıları, iş veya hizmetlerde SL2 hizmetlerinden veri gönderir ve Microsoft Azure.

2. CellTrust'ın SL2 Bulut Hizmeti ortamında, kuruluşun SL2 etki alanı vardır. Etki alanınız bir veya daha fazla kuruluş birimine (OU) sahip olabilir. SL2 Bulut Hizmeti, verilerinizi Microsoft Azure platformunda üst düzeyde güvenli bir alana aktararak verilerinizin son derece güvenli bir Microsoft Azure sağlar. SL2 planınıza (Enterprise, SMB veya Kamu) bağlı olarak, etki alanınız Microsoft Azure Global'da veya Microsoft Azure barındırıldı.

3. CellTrust SL2 Veri Bağlayıcısı'ı oluşturdukta, etki alanınız ve OU'lar (SL2 planınız ne olursa olsun) verileri Microsoft 365. Veri akışı, veri kaynakları, OUs veya tek başına etki alanı temel alarak raporlamayı destekleyecek şekilde yapılandırılmıştır. Sonuç olarak, kuruma tüm veri kaynaklarınızı akışla akışı için yalnızca bir bağlayıcının Microsoft 365.

4. Bağlayıcı, her eşlenmiş kullanıcının altında **CellTrust SL2 Office 365 bir lisansa sahip bir klasör oluşturur**. Bu eşleme, bir e-posta adresi kullanarak CellTrust SL2 Office 365 bir posta kutusuna bağlar. CellTrust SL2'deki bir kullanıcı kimliğinde Office 365 yoksa, kullanıcının verileri arşivlenir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- CellTrust SL2 bulut hizmeti ortamında etki alanınız olduğunu doğrulayın. SL2 üretim veya deneme etki alanı alma hakkında ek bilgi için [CellTrust ile iletişime geçin](https://www.celltrust.com/contact-us/#form).

- SL2 etki alanının yönetici hesabına erişmek için kimlik bilgilerini alın.

- 1. Adımda CellTrust SL2 veri bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, kaynakta Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu CellTrust veri bağlayıcısı ABD GCC tarafından Microsoft 365 ortamlarda kullanılabilir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>1. Adım: CellTrust SL2 bağlayıcısı oluşturma

İlk adım, dosyanın içinde bir veri bağlayıcısı Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com> bölmesinde **Veri bağlayıcıları'nın** üzerine gidin ve bu bağlayıcılara tıklayın.

2. Genel Bakış **sekmesinde Filtre'ye** **tıklayın,** **CellTrust'ı** seçin ve filtreyi uygula'yı seçin.

   ![CellTrust bağlayıcılarını görüntülemek için filtreyi yapılandır.](../media/DataConnectorsFilter.png)

3. **CellTrust SL2 (önizleme)'ye tıklayın**.

4. **CellTrust SL2 (önizleme) ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

5. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

6. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**. Siz girdikten sonra, bağlayıcıyı **Veri bağlayıcıları** sayfasında girersiniz.

7. **CellTrust hesabınızla oturum açın sayfasında CellTrust'da** **Oturum Açın'a tıklayın**. Yeni bir tarayıcı penceresinde, güven için **CellTrust Portalı'Microsoft 365** yeniden yönlendirildisiniz.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>2. Adım: Arşivlemek istediğiniz etki alanlarını veya OUs'u seçin

Sonraki adım, CellTrust SL2 etki alanınız için bir yönetici hesabında oturum açmalı ve arşivlenen etki alanlarını ve OUS'ları Microsoft 365.

1. CellTrust Microsoft 365 **Bağlayıcısı** sayfasında, oturum açma sayfasını görüntülemek için SL2 bulut hizmetinin ortamınızı seçin.

   Normalde, ortamınızı temsil eden bir seçenek görüyor olur. Öte yandan, etki alanlarınız birden çok ortamda yer aldısa, her ortam için seçenekler de vardır. Seçiminizi yaptıktan sonra SL2 oturum açma sayfasına yönlendirilin.

2. Etki Alanı veya OU Yönetici hesabı kimlik bilgilerinizle oturum açın.

   SL2 etki alanı yöneticisi olarak oturum açın, etki alanı adınızı ve bu etki alanındaki OUs'ları seçin. OUS'niz yoksa, yalnızca etki alanının adını görüyorsunuz. OU Yöneticisi olarak oturum açmak için yalnızca OU'nizin adını görüyorsunuz.

3. Arşivlemek istediğiniz iş birimlerini etkinleştirin. Etki alanı seçilirken OUs otomatik olarak seç olmaz. Arşivlemek için her OU'yi ayrı olarak etkinleştirmeniz gerekir.

   ![Arşivlemek için OUs'u etkinleştirin.](../media/EnableCellTrustOUs.png)

4. Seçimlerinizi tamamladikten sonra, tarayıcı penceresini kapatın ve çalışma sayfasındaki sihirbaz Microsoft 365 uyumluluk merkezi. Birkaç saniye sonra, sihirbaz kullanıcıları eşlemenin bir sonraki adımına otomatik olarak ilerler.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Son adım, kullanıcıları eşlemek ve aşağıdaki bağlantıda bağlayıcı kurulumunu tamamlamak Microsoft 365 uyumluluk merkezi.

1. Kullanıcı eşleme **sayfasında, kullanıcıların** **e-posta** adresi hem SL2'de hem de Başka bir dosyada aynı ise Otomatik kullanıcı eşlemesini Microsoft 365. Aksi takdirde, kullanıcıların SL2 adreslerini kendi adres defteri adreslerine eşleen bir CSV dosyası yükerek e-posta Microsoft 365 gerekir.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

   Yeni bağlayıcı, Veri bağlayıcıları **sayfasındaki listeye** eklenir.

## <a name="get-help-from-celltrust"></a>CellTrust'dan yardım al

CellTrust SL2 veri bağlayıcısı ayarlama konusunda yardım almak için [CellTrust](https://www.celltrust.com/contact-us/#support) Müşteri Desteği sayfasına bakın.

## <a name="more-information"></a>Daha fazla bilgi

- Etki alanı yöneticisi, etki alanı için veya bu etki alanındaki herhangi bir OUs için bir bağlayıcı kurabilirsiniz. OU Yönetici hesabını kullanıyorsanız, yalnızca belirli bir OU için bağlayıcı kurabilirsiniz.

- Yukarıdaki adımları başarıyla tamamlamak için, size bir lisans Microsoft 365 E5 ve yönetici hakları için Microsoft Office sahip olmak gerekir.

- Yeni bağlayıcıyı test etmek için SL2 mobil uygulamanızı veya SL2 portalını kullanarak bir metin mesajı gönderin. Gelen Kutunuza Microsoft 365 ve Gelen **Kutunuzda CellTrust SL2** klasörünü açın. Posta kutunuzda kısa mesajların yer alması birkaç dakika sürebilir.

- Birçok yasa ve düzenleme, elektronik iletişimin, istenen durumlarda kanıt olarak üretilecek şekilde korunmasını gerektirir. Elektronik Keşif (eBulma), elektronik iletişimin üretimine uyumlu olmak için kullanılır. Enterprise Arşivleme (EIA) çözümleri eBulma gerçekleştirmek için tasarlanmıştır ve bekletme ilkesi yönetimi, veri sınıflandırması ve içerik idaresi gibi özellikler sağlar. Microsoft 365, kuruluşu etkileyen yasal düzenlemelere ve standartlara uyumluluk için uzun vadeli bir bekletme çözümü sunar.

- Bu belgede *kullanılan arşivleme* terimi, dijital bir Bilgi Arşivleme (EIA) çözümünde kullanım bağlamında arşivleme Enterprise ifade eder. EIA çözümlerinin yasal işlemler, mahkemeler, denetimler ve soruşturmalar için belgeler üreten eBulma özellikleri vardır. Olağanüstü durum kurtarma ve iş sürekliliği sağlamak için kullanılan yedekleme ve geri yükleme bağlamında arşivleme, bu belgenin içindeki terimin hedeflenen kullanımı değildir.
