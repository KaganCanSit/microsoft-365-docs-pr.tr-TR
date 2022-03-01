---
title: Microsoft Bilgi Koruması'da Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: Önemli Microsoft Bilgi Koruması seyahatler için nerede olursa olsun korumanıza yardımcı olacak özellikler (MIP) özelliklerini hayata geçirebilirsiniz.
ms.openlocfilehash: 2fccdafa662bfdf8390a53ac535c571f52f673de
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010767"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>Microsoft Bilgi Koruması'da Microsoft 365

>*[Güvenlik ve Uyumluluk Microsoft 365 lisansı &.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Önemli bilgileri nerede Microsoft Bilgi Koruması seyahat ederse keşfedin, sınıflandırsın ve korumanıza yardımcı olması için MiP'den (MIP) özellikler geliştirin.

MIP özellikleri, Uyumluluk Microsoft 365 dahil edilir ve size verilerinizi [bilmek, verilerinizi](#know-your-data) korumak ve veri kaybını önlemek [için gerekli araçları sağlar](#prevent-data-loss). [](#protect-your-data)

![MIP'nin hassas verileri bulaştırmanıza, sınıflandırmanıza ve korumanıza nasıl yardımcı olduğunu resmi.](../media/powered-by-intelligent-platform.png)

MiP çözümünün kurum için dağıtımıyla ilgili önkinde yardım için bkz[. MICROSOFT BILGI KORUMASı dağıtma](information-protection-solution.md).

Verilerinizi yönetme hakkında bilgi için bkz. [Microsoft 365'te Microsoft Bilgi Microsoft 365](manage-Information-governance.md).

## <a name="know-your-data"></a>Verilerinizi bilebilirsiniz

Verilerinizin yatay özelliklerini anlamak ve karma ortamınız genelinde hassas verileri tanımlamak için aşağıdaki özellikleri kullanın:

|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:--------------------|
|[Hassas bilgi türleri](sensitive-information-type-learn-about.md)| Yerleşik veya özel normal ifadeleri veya bir işlevi kullanarak hassas verileri tanımlar. Bu kanıt anahtar sözcükleri, güven düzeylerini ve yakınlığı içerir.| [Yerleşik hassas bilgi türünü özelleştirme](customize-a-built-in-sensitive-information-type.md)|
|[Eğitime uygun sınıflayıcılar](classifier-learn-about.md)| Öğede öğeleri tanımlamak (desen eşleştirmesi) yerine ilginizi çeken veri örneklerini kullanarak hassas verileri tanımlar. Yerleşik sınıflayıcıları kullanabilir veya bir sınıflandırıcıyı kendi içeriğiniz ile eğitebilirsiniz.| [Eğitilebilir sınıflayıcılarla çalışmaya başlama](classifier-get-started-with.md) |
|[Veri sınıflandırması](data-classification-overview.md) | Kuruluşta duyarlılık etiketi, bekletme etiketi olan veya sınıflandırılmış öğelerin grafik gösterimi. Bu bilgileri, kullanıcılarınızı bu öğeler üzerinde gerçekleştiren işlemlerle ilgili öngörüler elde etmek için de kullanabilirsiniz. | [İçerik gezginiyle çalışmaya başlama](data-classification-content-explorer.md) <p> [Etkinlik gezginiyle çalışmaya başlama](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Verilerinizi koruyun

Şifreleme, erişim kısıtlamaları ve görsel işaretler içeren esnek koruma eylemleri uygulamak için aşağıdaki özellikleri kullanın:

|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|---------------------|
|[Duyarlılık etiketleri](sensitivity-labels.md)| Uygulama, hizmet ve cihazlar arasında, verilerinizin etiket ve korunması için, kuruluş içinde ve dışında tek bir çözüm. <br /><br /> Örnek senaryolar: <br />- [Office uygulamaları için duyarlılık Office yönetme](sensitivity-labels-office-apps.md) <br />- [Belgeleri ve e-postaları şifreleme](encryption-sensitivity-labels.md) <br />-  [Etiket uygulama ve görüntüleme Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Duyarlılık etiketleriyle ilgili senaryoları içeren kapsamlı bir liste için, Çalışmaya başlama belgelerine bakın.|[Duyarlılık etiketleriyle çalışmaya başlama](get-started-with-sensitivity-labels.md) |
|[Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/rms-client/aip-clientv2)| Diğer Windows için, etiket özelliklerini Dosya Gezgini'ne ve PowerShell'e genişleter ve gerekirse Office uygulamaları için ek özellikler içerir| [Azure Information Protection birleşik etiketleme istemcisi yönetici kılavuzu](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Çift Anahtar Şifrelemesi](double-key-encryption.md)| Her durumda, korumalı içeriğin şifresini yalnızca organizasyonun çözebilecekleri gibi yasal düzenleme gereksinimleri de vardır; coğrafi bir sınır içinde şifreleme anahtarlarını tutmanız gerekir. | [Çift Anahtar Şifrelemesi'nin dağıtımı](double-key-encryption.md#deploy-dke)|
|[Office 365 İleti Şifrelemesi (OME)](ome.md)| Herhangi bir cihazdan herhangi bir kullanıcıya gönderilen e-posta iletilerini ve ekli belgeleri şifreler, böylece yalnızca yetkili alıcılar e-postayla gönderilen bilgileri okuyabilir. <br /><br />  Örnek senaryo: [Gelişmiş İleti Şifrelemesi ile şifrelenen e-postaları iptal etme](revoke-ome-encrypted-mail.md) | [Yeni İleti Şifreleme özelliklerini ayarlama](set-up-new-message-encryption-capabilities.md)|
|[Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md) | Yetkisiz sistemlere veya personele göre verileri görüntülemeye karşı korur ve Microsoft veri merkezlerinde BitLocker disk şifrelemesini tamamlar. | [Müşteri Için Müşteri Anahtarını Office 365](customer-key-set-up.md)|
|[SharePoint Hakları Yönetimi (IRM)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Bu SharePoint ve kitaplıkları korur; böylelikle kullanıcı bir belgeyi teslim geldiğinde, indirilen dosya yalnızca yetkili kişilerin sizin belirttiğiniz ilkelere göre dosyayı görüntüley ve kullanamalarını sağlar. | [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)|
[Hak Yönetimi bağlayıcısı](/azure/information-protection/deploy-rms-connector) |Exchange veya SharePoint Server ya da Windows Server ve Dosya Sınıflandırma Altyapısı (FCI) ile çalıştıran dosya sunucularını kullanan mevcut şirket içi dağıtımlar için yalnızca koruma. | [RMS bağlayıcıyı dağıtma adımları](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Azure Information Protection birleşik etiketleme tarayıcısı](/azure/information-protection/deploy-aip-scanner)| Şirket içi veri depolarında bulunan hassas bilgileri keşfeder, etiketler ve korur. | [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)| Buluttaki veri depolarında bulunan hassas bilgileri keşfeder, etiketler ve korur. | [Bulutta depolanan düzenlemeye tabi ve hassas verileri keşfetme, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Azure Purview](/azure/purview/overview) |Hassas verileri tanımlar ve Azure Purview varlıklarının içeriğine otomatik etiket uygular. Bunlar, Azure Veri Gölü ve Azure Dosyaları gibi depolamada yer alan dosyaları ve Azure SQL DB ve Cosmos DB'daki sütunlar gibi şematize verileri içerir. |[Azure Purview'da etiketleme](/azure/purview/create-sensitivity-label) |
|[Microsoft Bilgi Koruması SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|Duyarlılık etiketlerini üçüncü taraf uygulamalarına ve hizmetlere genişlettir. <br /><br />  Örnek senaryo: [Duyarlılık etiketini (C++) ayarlayın ve elde edin](/information-protection/develop/quick-file-set-get-label-cpp) |[Microsoft Bilgi Koruması (MIP) SDK kurulumu ve yapılandırması](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Veri kaybını önleme

Hassas bilgilerin yanlışlıkla başka şekilde kullanımını önlemek için aşağıdaki özellikleri kullanın:


|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:---------------------|
|[Veri kaybını önleme](dlp-learn-about-dlp.md)| Hassas öğelerin ilkel olarak paylaşımını önlemeye yardımcı olur. | [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)|
|[Uç nokta veri kaybını önleme](endpoint-dlp-learn-about.md)| DLP özelliklerini, bilgisayarlarında kullanılan ve paylaşılan öğelere Windows 10 genişlettir. | [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)|
|[Microsoft Uyumluluk Uzantısı](dlp-chrome-learn-about.md) | DLP özelliklerini Chrome tarayıcısına genişlettir | [Microsoft Uyumluluk Uzantısı ile çalışmaya başlama](dlp-chrome-get-started.md)|
|[Microsoft 365 kaybı önlemeyi önleme (önizleme)](dlp-on-premises-scanner-learn.md)|Bu dosyalar için dosya etkinliklerinin ve koruyucu eylemlerin DLP izleme süresini şirket içi dosya paylaşımlarına genişleter ve klasör SharePoint kitaplıklarını oluşturur.|[Şirket içi Microsoft 365 önleme (önizleme) özelliğiyle çalışmaya başlama](dlp-on-premises-scanner-get-started.md)|
|[Sohbet ve kanal iletileri Microsoft Teams hassas bilgileri koruma](dlp-microsoft-teams.md) | Sohbet ve kanal mesajlarını daha Teams DLP işlevselliğini genişleten | [E-postada (önizleme) varsayılan veri Microsoft Teams ilkesi hakkında bilgi](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Lisans gereksinimleri

MIP lisans gereksinimleri, bu sayfada listelenen her beceriye lisans gereksinimlerini ayarlamak yerine kullandığınız senaryolara ve özelliklere bağlıdır. MIP lisans gereksinimlerinizi ve seçeneklerinizi anlamak için, güvenlik ve uyumluluk  için Microsoft 365 kılavuzunda ve özellik düzeyi lisans gereksinimleri için ilgili [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) indirmesinde yer alan [&](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) Koruması bölümlerine bakın.