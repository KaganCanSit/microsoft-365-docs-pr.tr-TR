---
title: Duyarlılık etiketleriyle çalışmaya başlama
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Kuruluşun verilerini korumaya yardımcı olmak ama nereden başlayacağınıza emin değil misiniz? Etiketleme yolculuğunuza yardımcı olacak bazı pratik kılavuzu okuyun.
ms.openlocfilehash: b5d7a6c18f112b7f35aa2599ff2639894a735f9b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014165"
---
# <a name="get-started-with-sensitivity-labels"></a>Duyarlılık etiketleriyle çalışmaya başlama

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Duyarlılık etiketlerinin ne olduğu ve bu etiketlerin kuruluş verilerinizi korumanıza nasıl yardımcı olduğu hakkında bilgi için bkz[. Duyarlılık etiketleri hakkında bilgi.](sensitivity-labels.md)

[Azure Information Protection'a](/azure/information-protection/what-is-information-protection) sahipsiniz ve Azure portaldan yönetilen Azure Information Protection etiketlerini kullanmaya devam ediyorsanız, bu etiketleri birleşik etiket [platformuna geçirmeniz gerekir](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). Daha Windows için, yayımlanmış [duyarlılık etiketleriniz için hangi etiket](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) istemcisinin kullanıla bir etiket istemcisi seçebilirsiniz.

Duyarlılık etiketlerini kullanarak kuruluş verilerinizi korumaya başlamaya hazırsanız:

1. **Etiketleri oluşturun.** Duyarlılık etiketlerinizi oluşturmak ve farklı içerik duyarlılık düzeyleri için kuruluş sınıflandırma taksonomisi'ne göre adlar oluşturun. Kullanıcılarınıza anlamlı gelen yaygın adları veya terimleri kullanın. Henüz kurulmuş bir taksonominiz yoksa, Kişisel, Genel, Genel, Gizli ve Çok Gizli gibi etiket adlarla başlamayı düşünün. Bundan sonra benzer etiketleri kategoriye göre gruplandıran alt etiketleri kullanabilirsiniz. Etiket  oluşturma, kullanıcıların uygun etiketi seçmesine yardımcı olmak için araç ipucu metnini kullanın.
    
    Sınıflandırma taksonomisi tanımlama konusunda daha kapsamlı kılavuzlar için, Hizmet Güveni Portalı'& "Veri Sınıflandırması Ve Duyarlılık Etiketi Taksonomisi" teknik [incelemesini indirin](https://aka.ms/DataClassificationWhitepaper).

2. **Her etiketin neler yapalını tanımlayın.** Her etiketle ilişkili olarak istediğiniz koruma ayarlarını yapılandırabilirsiniz. Örneğin, yalnızca bir üst bilgi veya alt bilgi uygulandığında daha düşük duyarlılık içeriğinin (örneğin" Genel" etiketi) uygulanması gerekirken, daha yüksek duyarlılık içeriğinin de ("Gizli" etiketi gibi) filigran ve şifrelemeye sahip olması gerekir.

3. **Etiketleri yayımlama.** Duyarlılık etiketleriniz yapılandırıldıktan sonra, bunları bir etiket ilkesi kullanarak yayımlayın. Etiketlere sahip olması gereken kullanıcı ve gruplara ve hangi ilke ayarlarının gerektiğine karar verin. Tek bir etiket yeniden kullanılabilir; bunu bir kez tanımlarsanız ve daha sonra bunu farklı kullanıcılara atanmış çeşitli etiket ilkelerine  dahilebilirsiniz. Örneğin, yalnızca birkaç kullanıcıya bir etiket ilkesi ataarak duyarlılık etiketlerinizi pilot edinebilirsiniz. Daha sonra, etiketleri kuruluş genelinde kullanıma hazır hale geldiğinde, etiketleriniz için yeni bir etiket ilkesi oluşturabilir ve bu kez tüm kullanıcıları belirtebilirsiniz.


> Sizin için 1-3 adımlarını içeren otomatik varsayılan etiketler ve varsayılan etiket ilkesi oluşturmak için uygun olabilirsiniz. Daha fazla bilgi için bkz[. Posta için varsayılan etiketler Microsoft Bilgi Koruması](mip-easy-trials.md).

Duyarlılık etiketlerini dağıtmak ve uygulamak için temel akış:

![Duyarlılık etiketleri için iş akışını gösteren diyagram.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Duyarlılık etiketleri için abonelik ve lisans gereksinimleri

Birkaç farklı abonelik duyarlılık etiketlerini ve kullanıcıların lisans gereksinimlerini kullandığınız özelliklere göre destekler.

Uyumluluk özelliklerinden yararlanmak için kullanıcılarınızı lisanslama Microsoft 365 görmek için, güvenlik Microsoft 365 uyumluluğu için lisanslama & [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Duyarlılık etiketleri için özellik düzeyinde lisans gereksinimleri için Bilgi Koruması [:](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-sensitivity-labeling) Duyarlılık etiketleme bölümüne ve ilgili [PDF'ye](https://go.microsoft.com/fwlink/?linkid=2139145) indirme bölümüne bakın.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Duyarlılık etiketlerini oluşturmak ve yönetmek için gereken izinler

Duyarlılık etiketleri oluşturacak uyumluluk ekibimizin üyelerinin site üzerinde izinleri Microsoft 365 uyumluluk merkezi.

Varsayılan olarak, kiracınıza hizmet veren genel yöneticiler bu yönetim merkezine erişim sahibi olur ve uyumluluk görevlilerine ve diğer kullanıcılara, tüm kiracı yöneticisi izinlerini vermeden erişim izni vetir. Bu sınırlı yönetici temsilcisi erişimi için, kullanıcıları Uyumluluk Veri **Yöneticisi, Uyumluluk** Yöneticisi **veya Güvenlik** Yöneticisi **rol grubuna** ekleyin. 

Alternatif olarak, varsayılan rolleri kullanarak yeni bir rol grubu oluşturabilir ve bu gruba Duyarlılık Etiketi Yöneticisi veya  **Kuruluş Yapılandırması** rolleri eklersiniz. Salt okunur bir rol için Duyarlılık **Etiketi Okuyucu kullanın**. 

> [!NOTE]
> Şimdi önizlemede aşağıdaki rol gruplarını kullanabilirsiniz:
> - **Bilgi Koruması**
> - **Bilgi Koruması Yöneticileri**
> - **Bilgi Koruma Analistleri**
> - **Bilgi Koruma Koruma KorumaLarı**
> - **Bilgi Koruma Okuyucuları**
>
> Her birinin ve bunların içerdiği yeni rollerin açıklaması için, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> **Permissions &** >  **rolesCompliance** >  center  > **Öğesini** seçin ve sonra uçarak çıkış bölmesinde açıklamayı gözden geçirin. Ya da Güvenlik [ve Uyumluluk Merkezi'nde rol & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Varsayılan rol grubuna, rollerine kullanıcı ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için bkz. Kullanıcı ekleme [Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca duyarlılık etiketlerini ve bunların etiket ilkelerini oluşturmak ve yapılandırmak için gereklidir. Etiketleri uygulama veya hizmetlerde uygulamak zorunda değildir. Duyarlılık etiketleriyle ilgili belirli yapılandırmalar için ek izinler gerekirse, bu izinler ilgili belge yönergelerinde listelenir.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Duyarlılık etiketleri için dağıtım stratejisi
Kuruluşta duyarlılık etiketlerini dağıtmanın başarılı bir stratejisi, iş ve teknik gereksinimleri tanımlayan ve yöneten, kavram kanıtı testi, iç denetim noktaları ve onaylar ve üretim ortamı için son dağıtımda çalışan bir sanal ekip oluşturmaktır.

Sonraki bölümde yer alan tabloyu kullanarak, en etkili iş gereksinimlerinize uygun olarak en iyi bir veya iki senaryoyu tanımlamanızı öneririz. Bu senaryolar dağıtıldıktan sonra, dağıtımda bir veya iki öncelik belirlemek için listeye geri dönebilirsiniz.

Müşteri Hızlandırma Ekibi [(CAT)](https://microsoft.github.io/ComplianceCxE/) sitesinden gelen kaynaklardan biri olan [](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/)Microsoft Bilgi Koruması Hızlandırma ve Veri Kaybı Önleme için Dağıtım Hızlandırma Kılavuzu'nda ek genel dağıtım kılavuzu ve en iyi uygulamaları bulabilirsiniz.

## <a name="common-scenarios-for-sensitivity-labels"></a>Duyarlılık etiketleri için genel senaryolar

Tüm senaryolarda duyarlılık etiketleri [ve ilkeleri oluşturma ve yapılandırma gerekir](create-sensitivity-labels.md).

|Yapmak istiyorum...|Belgeler|
|----------------|---------------|
|İçerik oluşturulduktan sonra Office için duyarlılık etiketlerini yönetme; tüm platformlarda el ile etiketleme desteği içerir |[Office uygulamalarında duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md)|
|Etiketi Dosya Gezgini ve PowerShell'e genişletebilirsiniz ve bu uygulama Office için Windows (gerekirse)|[Windows için Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/rms-client/aip-clientv2)|
|Belgeleri ve e-postaları duyarlılık etiketleriyle şifrele, bu içeriğe kimlerin erişeni ve nasıl kullanıla olacağını kısıtla |[Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md)|
|Birlikte kimlik doğrulaması, eKbulma, veri kaybını önleme, arama ve belgeler şifrelenirken Web üzerinde Office için duyarlılık etiketlerini etkinleştirme | [SharePoint ve Office dosyaları için duyarlılık OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Belgeler şifrelenirken birlikte yazma ve otomatik Office masaüstü uygulamalarını kullanma | [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma özelliği etkinleştirme](sensitivity-labels-coauthoring.md)
|Belgelere ve e-postalara otomatik olarak duyarlılık etiketleri uygulama | [Otomatik olarak içeriğe duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md)|
|Teams ve SharePoint'de içeriği korumak için duyarlılık Teams kullanın |[Site oluşturma, Microsoft Teams grupları Microsoft 365 duyarlılık SharePoint kullanma](sensitivity-labels-teams-groups-sites.md)|
|Bir çalışma kitaplığında tanımlanan belgelerin otomatik olarak sınıflandırılması ve korunması için belge anlama modeline duyarlılık SharePoint etiket ekleme |[Microsoft SharePoint Syntex'da bir modele duyarlılık SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Belirli bir duyarlılık etiketiyle dosya veya e-posta paylaşımı konusunda kullanıcıları engelleme veya uyarma |[DLP ilkelerde duyarlılık etiketlerini koşullar olarak kullanma](dlp-sensitivity-label-as-condition.md) |
|Belirli bir duyarlılık etiketine sahip dosyaları veya e-postaları korumak veya silmek için bekletme etiketi uygulama|[İçeriği tutmak veya silmek için otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md) |
|Şirket içi veri depolarında depolanan dosyaları bulma, etiketleme ve koruma |[Dosyaları otomatik olarak sınıflandırmak ve korumak için Azure Information Protection tarayıcısını dağıtma](/azure/information-protection/deploy-aip-scanner)|
|Buluttaki veri depolarında depolanan dosyaları bulma, etiketleme ve koruma|[Bulutta depolanan düzenlemeye tabi ve hassas verileri keşfetme, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Dış verilerde etiket uygulama Power BI görüntüleme ve verilerin hizmetin dışında kaydedilebilir şekilde korunmasını sağlar|[Power BI'de duyarlılık etiketleri](/power-bi/admin/service-security-sensitivity-label-overview)|
|Kuruluşumda duyarlılık etiketlerinin nasıl kullanılıyor olduğunu izleme ve anlama|[Veri sınıflandırması hakkında bilgi](data-classification-overview.md)|
|Duyarlılık etiketlerini üçüncü taraf uygulamalarına ve hizmetlere genişletme|[Microsoft Bilgi Koruması SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Azure Blob Depolama, Azure Files, Azure Data Lake Depolama ve çok bulutlu veri kaynakları gibi Azure Purview varlıklarımda yer alan içerik genelinde duyarlılık etiketlerini genişletme|[Azure Purview'da etiketleme](/azure/purview/create-sensitivity-label) |


## <a name="end-user-documentation-for-sensitivity-labels"></a>Duyarlılık etiketleri için son kullanıcı belgeleri

En etkili son kullanıcı belgeleri, seçtiğiniz etiket adları ve yapılandırmaları için size yol gösterici yönergeler ve yönergeler olarak sağlanmıştır. Bu belgeye ilişkin iç bağlantı belirtmek **için Kullanıcılara** özel yardım sayfasının bağlantısını sağlama etiket ilkesi ayarını kullanabilirsiniz. Bundan sonra kullanıcılar Duyarlılık düğmesinden ona **kolayca erişebilir** :

- Yerleşik etiketleme için: Daha Fazla **Bilgi menü** seçeneği.
- Azure Information Protection birleşik etiketleme istemcisi **için: Bilgi** Koruması iletişim kutusundaki > **ve Geri** Bildirim menü Microsoft Azure Daha Fazla Bilgi bağlantısına tıklayın.

Özelleştirilmiş belgelerinizi sağlamanıza yardımcı olması için, kullanıcılarınızı eğitmenize yardımcı olmak için kullanabileceğiniz aşağıdaki sayfa ve indirmelere bakın: Duyarlılık Etiketleri için Son Kullanıcı [Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Temel yönergeler için aşağıdaki kaynakları da kullanabilirsiniz:

- [Office'te dosyalarınıza ve e-postalarınıza duyarlılık etiketleri uygulama](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [E-Office'de duyarlılık etiketleriyle ilgili bilinen Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Web'de dosyalarınıza ve e-postanıza otomatik olarak duyarlılık etiketleri Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Otomatik olarak duyarlılık etiketleri uygulama veya öneriyle ilgili bilinen sorunlar](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Azure Information Protection birleşik etiketleme kullanıcı kılavuzu](/azure/information-protection/rms-client/clientv2-user-guide)

Duyarlılık etiketleriniz PDF belgeleri için şifreleme uygulamazsa, bu belgeler Microsoft Edge veya Mac üzerinde Windows açılabilir. Daha fazla bilgi ve alternatif okuyucular için bkz. [Korumalı PDF'ler için hangi PDF okuyucular destek görüyor?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
