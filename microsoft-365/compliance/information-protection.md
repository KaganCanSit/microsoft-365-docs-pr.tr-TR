---
title: Microsoft Purview Information Protection
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
description: Microsoft Purview Information Protection özelliklerini uygulayarak hassas bilgileri nerede olursa olsun korumanıza yardımcı olun.
ms.openlocfilehash: 97f5172479d889ec1914cfc46102a58a83165269
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285488"
---
# <a name="protect-your-sensitive-data-with-microsoft-purview"></a>Microsoft Purview ile hassas verilerinizi koruma

>*[Microsoft 365 Güvenlik & Uyumluluğu için Lisanslama](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!TIP]
> *Dokuz Microsoft Purview çözümlerinin tamamının premium sürümlerini ücretsiz olarak deneyebileceğinizi biliyor muydunuz?* Sağlam Purview özelliklerinin kuruluşunuzun uyumluluk gereksinimlerini karşılamasına nasıl yardımcı olabileceğini keşfetmek için 90 günlük Purview çözümleri deneme sürümünü kullanın. Microsoft 365 E3 ve Office 365 E3 müşterileri artık [Microsoft Purview uyumluluk portalı deneme hub'ında](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef) başlayabilir. [Kaydolabilecek kişiler ve deneme koşulları](compliance-easy-trials.md) hakkında ayrıntılı bilgi edinin.

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Microsoft Purview Information Protection (eski adıyla** Microsoft Bilgi Koruması) özelliklerini uygulayarak hassas bilgileri nerede yaşarsa yaşasın veya seyahat etseler keşfetmenize, sınıflandırmanıza ve korumanıza yardımcı olur.

Bu bilgi koruma özellikleri verilerinizi [tanımanızı, verilerinizi korumanızı](#know-your-data) ve [veri kaybını önlemenizi sağlar](#prevent-data-loss). [](#protect-your-data)

![Microsoft Purview Information Protection hassas verileri keşfetmenize, sınıflandırmanıza ve korumanıza nasıl yardımcı olduğunu gösteren görüntü.](../media/powered-by-intelligent-platform.png)

Kuruluşunuz için bir Microsoft Purview Information Protection çözümü dağıtmaya yönelik açıklayıcı yönergeler için bkz. [Microsoft Purview ile bilgi koruma çözümü dağıtma](information-protection-solution.md).

Verilerinizi yönetme hakkında bilgi için bkz. [Microsoft Purview ile verilerinizi yönetme](manage-Information-governance.md).

## <a name="know-your-data"></a>Verileriniz hakkında bilgi edinme

Veri ortamınızı anlamak ve karma ortamınızda hassas verileri tanımlamak için aşağıdaki özellikleri kullanın:

|Yeteneği|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:--------------------|
|[Hassas bilgi türleri](sensitive-information-type-learn-about.md)| Yerleşik veya özel normal ifadeler ya da bir işlev kullanarak hassas verileri tanımlar. Doğrulayıcı kanıt anahtar sözcükleri, güvenilirlik düzeylerini ve yakınlığı içerir.| [Yerleşik hassas bilgi türünü özelleştirme](customize-a-built-in-sensitive-information-type.md)|
|[Eğitilebilir sınıflandırıcılar](classifier-learn-about.md)| Öğedeki öğeleri (desen eşleştirme) tanımlamak yerine ilgilendiğiniz verilerin örneklerini kullanarak hassas verileri tanımlar. Yerleşik sınıflandırıcıları kullanabilir veya kendi içeriğinizle bir sınıflandırıcı eğitebilirsiniz.| [Eğitilebilir sınıflandırıcıları kullanmaya başlama](classifier-get-started-with.md) |
|[Veri sınıflandırması](data-classification-overview.md) | Kuruluşunuzda duyarlılık etiketi, bekletme etiketi olan veya sınıflandırılmış öğelerin grafik tanımlaması. Bu bilgileri, kullanıcılarınızın bu öğeler üzerinde gerçekleştirecekleri eylemlerle ilgili içgörüler elde etmek için de kullanabilirsiniz. | [İçerik gezginini kullanmaya başlama](data-classification-content-explorer.md) <p> [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Verilerinizi koruma

Şifreleme, erişim kısıtlamaları ve görsel işaretler içeren esnek koruma eylemleri uygulamak için aşağıdaki özellikleri kullanın:

|Yeteneği|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|---------------------|
|[Duyarlılık etiketleri](sensitivity-labels.md)| Kuruluşunuzun içinde ve dışında hareket eden verilerinizi etiketlemek ve korumak için uygulamalar, hizmetler ve cihazlar arasında tek bir çözüm. <br /><br /> Örnek senaryolar: <br />- [Office uygulamaları için duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md) <br />- [Belgeleri ve e-postaları şifreleme](encryption-sensitivity-labels.md) <br />-  [etiketleri Power BI uygulama ve görüntüleme](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Duyarlılık etiketlerine yönelik senaryoların kapsamlı bir listesi için Kullanmaya başlayın belgelerine bakın.|[Hassasiyet etiketlerini kullanmaya başlama](get-started-with-sensitivity-labels.md) |
|[Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/rms-client/aip-clientv2)| Windows bilgisayarlar için etiketlemeyi Dosya Gezgini ve PowerShell'e genişletir ve gerekirse Office uygulamalarına yönelik ek özellikler sunar| [Azure Information Protection birleşik etiketleme istemcisi yönetici kılavuzu](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Çift Anahtarlı Şifreleme](double-key-encryption.md)| Her koşulda, yalnızca kuruluşunuz korumalı içeriğin şifresini çözebilir veya yasal gereksinimler için şifreleme anahtarlarını coğrafi sınır içinde tutmanız gerekir. | [Çift Anahtar Şifrelemesi Dağıtma](double-key-encryption.md#deploy-dke)|
|[Office 365 İleti Şifrelemesi (OME)](ome.md)| Herhangi bir cihazdaki herhangi bir kullanıcıya gönderilen e-posta iletilerini ve ekli belgeleri şifreler, böylece yalnızca yetkili alıcılar e-postayla gönderilen bilgileri okuyabilir. <br /><br />  Örnek senaryo: [Gelişmiş İleti Şifrelemesi ile şifrelenen e-postayı iptal etme](revoke-ome-encrypted-mail.md) | [Yeni İleti Şifrelemesi özelliklerini ayarlama](set-up-new-message-encryption-capabilities.md)|
|[Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md) | Yetkisiz sistemler veya personel tarafından verilerin görüntülenmesine karşı koruma sağlar ve Microsoft veri merkezlerinde BitLocker disk şifrelemesini tamamlar. | [Office 365 için Müşteri Anahtarını Ayarlama](customer-key-set-up.md)|
|[SharePoint Bilgi Hakları Yönetimi (IRM)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|SharePoint listeleri ve kitaplıkları korur, böylece kullanıcı bir belgeyi kullanıma alırsa indirilen dosya yalnızca yetkili kişilerin belirttiğiniz ilkelere göre dosyayı görüntüleyebilir ve kullanabilir. | [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)|
[Rights Management bağlayıcısı](/azure/information-protection/deploy-rms-connector) |Exchange veya SharePoint Sunucusu kullanan mevcut şirket içi dağıtımlar ya da Windows Sunucu ve Dosya Sınıflandırma Altyapısı (FCI) çalıştıran dosya sunucuları için yalnızca koruma. | [RMS bağlayıcısını dağıtma adımları](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Azure Information Protection birleşik etiketleme tarayıcısı](/azure/information-protection/deploy-aip-scanner)| Şirket içindeki veri depolarında bulunan hassas bilgileri bulur, etiketler ve korur. | [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)| Bulutta bulunan veri depolarında bulunan hassas bilgileri bulur, etiketler ve korur. | [Bulutta depolanan düzenlenmiş ve hassas verileri bulma, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Microsoft Purview Veri Haritası](/azure/purview/overview) |Hassas verileri tanımlar ve Microsoft Purview Veri Eşlemesi varlıklarındaki içeriğe otomatik etiketleme uygular. Bunlar Azure Data Lake ve Azure Dosyalar gibi depolamadaki dosyaları ve Azure SQL DB ve Cosmos DB'deki sütunlar gibi şemaya oluşturulmuş verileri içerir. |[Microsoft Purview Veri Haritası'nda etiketleme](/azure/purview/create-sensitivity-label) |
|[Microsoft Bilgi Koruması SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|Duyarlılık etiketlerini üçüncü taraf uygulamalara ve hizmetlere genişletir. <br /><br />  Örnek senaryo: [Duyarlılık etiketi ayarlama ve alma (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[Microsoft Bilgi Koruması (MIP) SDK kurulumu ve yapılandırması](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Veri kaybını önleme

Hassas bilgilerin yanlışlıkla fazla paylaşılmasını önlemeye yardımcı olmak için aşağıdaki özellikleri kullanın:


|Yeteneği|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:---------------------|
|[Microsoft Purview Veri Kaybı Önleme](dlp-learn-about-dlp.md)| Hassas öğelerin yanlışlıkla paylaşılmasını önlemeye yardımcı olur. | [Varsayılan DLP ilkesini kullanmaya başlama](get-started-with-the-default-dlp-policy.md)|
|[Uç nokta veri kaybı önleme](endpoint-dlp-learn-about.md)| DLP özelliklerini Windows 10 bilgisayarlarda kullanılan ve paylaşılan öğelere genişletir. | [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)|
|[Microsoft Uyumluluk Uzantısı](dlp-chrome-learn-about.md) | DLP özelliklerini Chrome tarayıcısına genişletir | [Microsoft Uyumluluk Uzantısını kullanmaya başlama](dlp-chrome-get-started.md)|
|[Microsoft Purview veri kaybı önleme şirket içi tarayıcı (önizleme)](dlp-on-premises-scanner-learn.md)|Bu dosyalar için dosya etkinliklerinin ve koruyucu eylemlerin DLP izlemesini şirket içi dosya paylaşımlarına ve SharePoint klasörlerine ve belge kitaplıklarına genişletir.|[Microsoft Purview veri kaybı önleme şirket içi tarayıcı (önizleme) ile Kullanmaya başlayın](dlp-on-premises-scanner-get-started.md)|
|[Microsoft Teams sohbette ve kanal iletilerinde hassas bilgileri koruma](dlp-microsoft-teams.md) | Sohbet ve kanal iletilerini Teams için bazı DLP işlevlerini genişletir | [Microsoft Teams'teki varsayılan veri kaybı önleme ilkesi hakkında daha fazla bilgi edinme (önizleme)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Microsoft Purview Information Protection lisans gereksinimleri, bu sayfada listelenen her özellik için lisans gereksinimleri ayarlamak yerine kullandığınız senaryolara ve özelliklere bağlıdır. Microsoft Purview Information Protection lisans gereksinimlerinizi ve seçeneklerinizi anlamak için güvenlik **&** [uyumluluğuna yönelik Microsoft 365 kılavuzunun Information Protection](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) bölümlerine ve özellik düzeyi lisanslama gereksinimleri için ilgili [PDF indirme](https://go.microsoft.com/fwlink/?linkid=2139145) bölümüne bakın.
