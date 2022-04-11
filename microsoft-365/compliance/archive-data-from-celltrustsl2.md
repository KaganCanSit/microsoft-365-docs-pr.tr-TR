---
title: CellTrust SL2 platformundaki verileri Microsoft 365 arşivle
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
description: Mobil iletişim verilerini içeri aktarmak ve arşivlemek için CellTrust SL2 veri bağlayıcısını ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: e5e07e4138445e46cdd21edc0cfb01d871dd3b6e
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761164"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>CellTrust SL2'den Microsoft 365 verileri arşivle

CellTrust SL2 mobil iletişim verilerini yakalar ve FINRA, HIPAA, FOIA ve TCPA gibi düzenlemelere yönelik elektronik keşif gereksinimlerini karşılamak için önde gelen arşivleme teknolojileriyle tümleşir. SL2 Veri Bağlayıcısı mobil iletişim öğelerini Microsoft 365 aktarır. Bu makalede, arşivleme için CellTrust SL2 Veri Bağlayıcısı'nı kullanarak SL2'yi Microsoft 365 ile tümleştirme işlemi açıklanmaktadır. Bu işlemi tamamladığınızda CellTrust SL2 hizmetine abone olduğunuz ve SL2 mimarisi hakkında bilgi sahibi olduğunuz varsayılır. CellTrust SL2 hakkında bilgi için bkz <https://www.celltrust.com>. .

Veriler Microsoft 365 kullanıcı posta kutularına aktarıldıktan sonra, Dava Tutma, eBulma, Microsoft 365 bekletme ilkeleri ve iletişim uyumluluğu gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için CellTrust SL2 Veri Bağlayıcısı'nı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>CellTrust SL2 Veri Bağlayıcısı ile arşivleme genel bakış

CellTrust'ın SL2 platformu, birden çok kaynaktan gelen iletişim verilerini yakalar. SL2 veri kaynakları, Kişiden Kişiye (P2P) veya Uygulamadan Kişiye (A2P) veri kaynaklarıdır. Bu makalede açıklanan işlem yalnızca P2P veri kaynaklarıyla ilgili. Tüm P2P veri kaynakları için işbirliğindeki en az bir taraf, SL2 hizmetine abone olan bir SL2 kullanıcısıdır. Aşağıdaki genel bakış, Microsoft 365'de CellTrust SL2 Veri Bağlayıcısı'nı kullanma işlemini açıklar.

![CellTrust SL2 hizmeti için arşivleme iş akışı.](../media/CellTrustSL2ConnectorWorkflow.png)

1. SL2 kullanıcıları Microsoft Azure'da SL2 hizmetlerine veri gönderir ve bu hizmetlerden veri alır.

2. Kuruluşunuzun CellTrust'ın SL2 Bulut Hizmeti ortamında bir SL2 etki alanı vardır. Etki alanınızda bir veya daha fazla kuruluş birimi (OU) olabilir. SL2 Bulut Hizmeti, verilerinizi Microsoft Azure platformundaki son derece güvenli bir alana aktarır ve böylece verileriniz hiçbir zaman Microsoft Azure ortamından ayrılmaz. SL2 planınıza (Enterprise, SMB veya Kamu) bağlı olarak, etki alanınız Microsoft Azure Global veya Microsoft Azure Kamu'da barındırılır.

3. CellTrust SL2 Veri Bağlayıcısı'nı oluşturduktan sonra etki alanınız ve OU'larınız (SL2 planınızdan bağımsız olarak) Microsoft 365'a veri göndermeye başlar. Veri akışı, veri kaynaklarına, OU'lara veya etki alanına göre raporlamayı destekleyecek şekilde yapılandırılmıştır. Sonuç olarak, kuruluşunuzun tüm veri kaynaklarınızı Microsoft 365 beslemek için yalnızca bir bağlayıcıya ihtiyacı vardır.

4. Bağlayıcı, eşlenen her kullanıcının altında **CellTrust SL2** adlı uygun bir Office 365 lisansına sahip bir klasör oluşturur. Bu eşleme, bir CellTrust SL2 kullanıcısını bir e-posta adresi kullanarak Office 365 posta kutusuna bağlar. CellTrust SL2'deki bir kullanıcı kimliğinin Office 365 eşleşmesi yoksa, kullanıcının verileri arşivlenmez.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- CellTrust SL2 bulut hizmeti ortamında bir etki alanınız olduğunu doğrulayın. Üretim veya deneme SL2 etki alanı edinme hakkında ek bilgi için [CellTrust'a başvurun](https://www.celltrust.com/contact-us/#form).

- SL2 etki alanınızın yönetici hesabına erişmek için kimlik bilgilerini alın.

- 1. Adımda CellTrust SL2 veri bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu CellTrust veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda kullanılabilir. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>1. Adım: CellTrust SL2 bağlayıcısı oluşturma

İlk adım, Microsoft 365 uyumluluk merkezi bir veri bağlayıcısı oluşturmaktır.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Genel Bakış** sekmesinde **Filtre'ye** tıklayın ve **CellTrust'a Göre'yi** seçin ve ardından filtreyi uygulayın.

   ![CellTrust bağlayıcılarını görüntülemek için filtreyi yapılandırın.](../media/DataConnectorsFilter.png)

3. **CellTrust SL2 (önizleme)'** ye tıklayın.

4. **CellTrust SL2 (önizleme)** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

5. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

6. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın. Girdiğiniz ad, bağlayıcıyı oluşturduktan sonra **Veri bağlayıcıları** sayfasında tanımlar.

7. **CellTrust hesabınızda oturum açın sayfasında,** **CellTrust'da Oturum Aç'a** tıklayın. Yeni bir tarayıcı penceresinde **Microsoft 365 için CellTrust Portalı'na** yönlendirilirsiniz.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>2. Adım: Arşive eklenecek etki alanlarını veya OU'ları seçin

Bir sonraki adım, CellTrust SL2 etki alanınız için bir yönetici hesabında oturum açmak ve Microsoft 365 arşivleyebilmek için etki alanlarını ve OU'ları seçmektir.

1. CellTrust **Microsoft 365 Bağlayıcısı** sayfasında, oturum açma sayfasını görüntülemek için SL2 bulut hizmetinde ortamınızı seçin.

   Genellikle ortamınızı temsil eden bir seçenek görmeniz gerekir. Ancak, birden fazla ortamda etki alanınız varsa, her ortam için seçenekleri görürsünüz. Seçim yaptıktan sonra SL2 oturum açma sayfasına yönlendirilirsiniz.

2. Etki Alanı veya OU Yönetici hesabı kimlik bilgilerinizle oturum açın.

   SL2 etki alanı yöneticisi olarak oturum açarsanız, etki alanınızın adını ve o etki alanındaki OU'ları görürsünüz. OU'larınız yoksa, yalnızca etki alanınızın adını görürsünüz. OU Yöneticisi olarak oturum açarsanız yalnızca OU'nuzun adını görürsünüz.

3. Arşivlediğiniz iş birimlerini etkinleştirin. Etki alanı seçildiğinde OU'lar otomatik olarak seçilmez. Her OU'yı arşivlemeniz için ayrı ayrı etkinleştirmeniz gerekir.

   ![Arşiv için OU'ları etkinleştirin.](../media/EnableCellTrustOUs.png)

4. Seçimlerinizi bitirdiğinizde tarayıcı penceresini kapatın ve Microsoft 365 uyumluluk merkezi sihirbaz sayfasına dönün. Birkaç saniye sonra sihirbaz otomatik olarak kullanıcıları eşlemenin bir sonraki adımına ilerler.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Son adım, kullanıcıları eşlemek ve Microsoft 365 uyumluluk merkezi bağlayıcı kurulumunu tamamlamaktır.

1. Kullanıcılar için e-posta adresi hem SL2 hem de Microsoft 365 aynıysa, **Kullanıcı eşleme** sayfasında **Otomatik kullanıcı eşlemesini etkinleştir'i** seçin. Aksi takdirde, kullanıcıların SL2 adresini Microsoft 365 adresleriyle eşleyen bir CSV dosyasını karşıya yükleyerek e-posta adreslerini el ile kullanmanız gerekir.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

   Yeni bağlayıcı **, Veri bağlayıcıları** sayfasındaki listeye eklenir.

## <a name="get-help-from-celltrust"></a>CellTrust'dan yardım alma

CellTrust SL2 veri bağlayıcısını ayarlama konusunda yardım için CellTrust ile iletişim kurma hakkında ayrıntılar için CellTrust [Müşteri Desteği sayfasına](https://www.celltrust.com/contact-us/#support) bakın.

## <a name="more-information"></a>Daha fazla bilgi

- Etki alanı yöneticisi, etki alanı için bir bağlayıcı veya o etki alanındaki herhangi bir OU ayarlayabilir. OU Yönetici hesabını kullanıyorsanız, yalnızca ilgili OU için bir bağlayıcı ayarlayabilirsiniz.

- Yukarıdaki adımları başarıyla tamamlamak için Microsoft 365 E5 lisansına sahip olmanız ve uygun Microsoft Office yönetici haklarına sahip olmanız gerekir.

- Yeni bağlayıcıyı test etmek için SL2 mobil uygulamanızı kullanarak veya SL2 portalınızdan kısa mesaj gönderin. Microsoft 365 posta kutunuza gidin ve Gelen Kutunuzda **CellTrust SL2** klasörünü açın. Kısa mesajların posta kutunuzda görünmesi birkaç dakika sürebilir.

- Birçok yasa ve düzenleme, elektronik iletişimin istendiğinde kanıt olarak üretilebileceği şekilde korunmasını gerektirir. Elektronik Bulma (eKeşif) elektronik iletişimin üretimine uyum sağlamak için kullanılır. Enterprise Bilgi Arşivleme (EIA) çözümleri, eBulma gerçekleştirmek için tasarlanmıştır ve bekletme ilkesi yönetimi, veri sınıflandırması ve içerik denetimi gibi özellikler sağlar. Microsoft 365, kuruluşunuzu etkileyen düzenlemelere ve standartlara uyum için uzun vadeli bir saklama çözümü sunar.

- Bu belgede kullanılan *arşivleme* terimi, bir Enterprise Bilgi Arşivleme (ÇED) çözümü içinde kullanım bağlamında arşivlemeyi ifade eder. EIA çözümleri, yasal işlemler, davalar, denetimler ve soruşturmalar için belgeler üreten eBulma özelliklerine sahiptir. Olağanüstü durum kurtarma ve iş sürekliliği için kullanılan yedekleme ve geri yükleme bağlamında arşivleme, bu belgedeki terimin amaçlanan kullanımı değildir.
