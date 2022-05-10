---
title: Hassasiyet etiketlerini kullanmaya başlama
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
description: Kuruluşunuzun verilerini korumaya yardımcı olmak için duyarlılık etiketlerini dağıtmaya hazırsınız, ancak nereden başlayacağınızdan emin değil misiniz? Etiketleme yolculuğunuza başlamanıza yardımcı olacak bazı pratik kılavuzları okuyun.
ms.openlocfilehash: f27f1a475f5880058db40894015dabdec9038be1
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286044"
---
# <a name="get-started-with-sensitivity-labels"></a>Hassasiyet etiketlerini kullanmaya başlama

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Duyarlılık etiketlerinin ne olduğu ve kuruluşunuzun verilerini korumanıza nasıl yardımcı olabileceği hakkında bilgi için bkz. [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md).

[Azure Information Protection'niz](/azure/information-protection/what-is-information-protection) varsa ve hala Azure portal yönetilen Azure Information Protection etiketlerini kullanıyorsanız, bu etiketleri [birleşik etiketleme platformuna](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform) geçirmeniz gerekir. Windows bilgisayarlar için, yayımlanmış duyarlılık etiketleriniz için [hangi etiketleme istemcisini kullanacağınızı seçebilirsiniz](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers).

Duyarlılık etiketlerini kullanarak kuruluşunuzun verilerini korumaya başlamaya hazır olduğunuzda:

1. **Etiketleri oluşturun.** Farklı duyarlılık düzeyleri için duyarlılık etiketlerinizi kuruluşunuzun sınıflandırma taksonomisine göre oluşturun ve adlandırın. Kullanıcılarınız için anlamlı olan ortak adlar veya terimler kullanın. Henüz yerleşik bir taksonominiz yoksa Kişisel, Genel, Genel, Gizli ve Çok Gizli gibi etiket adlarıyla başlamayı göz önünde bulundurun. Daha sonra benzer etiketleri kategoriye göre gruplandırmak için alt etiketleri kullanabilirsiniz. Etiket oluşturduğunuzda, kullanıcıların uygun etiketi seçmesine yardımcı olmak için araç ipucu metnini kullanın.
    
    Sınıflandırma taksonomisi tanımlamaya yönelik daha kapsamlı yönergeler için [Hizmet Güveni Portalı'ndan](https://aka.ms/DataClassificationWhitepaper) "Veri Sınıflandırma & Duyarlılık Etiketi Taksonomisi" teknik incelemesini indirin.

2. **Her etiketin neler yapabileceğini tanımlayın.** Her etiketle ilişkilendirılmasını istediğiniz koruma ayarlarını yapılandırın. Örneğin, daha düşük duyarlılık içeriğinin (örneğin, "Genel" etiketi) yalnızca bir üst bilgi veya alt bilginin uygulanmasını, daha yüksek duyarlılık içeriğinin (örneğin, "Gizli" etiket) filigran ve şifrelemeye sahip olmasını isteyebilirsiniz.

3. **Etiketleri yayımlayın.** Duyarlılık etiketleriniz yapılandırıldıktan sonra bir etiket ilkesi kullanarak yayımlayın. Etiketlerin hangi kullanıcı ve gruplara sahip olması gerektiğine ve hangi ilke ayarlarının kullanılacağına karar verin. Tek bir etiket yeniden kullanılabilir; bunu bir kez tanımlarsınız ve ardından farklı kullanıcılara atanan çeşitli etiket ilkelerine ekleyebilirsiniz. Örneğin, yalnızca birkaç kullanıcıya bir etiket ilkesi atayarak duyarlılık etiketlerinizi pilot olarak kullanabilirsiniz. Ardından, etiketleri kuruluşunuz genelinde kullanıma sunmaya hazır olduğunuzda, etiketleriniz için yeni bir etiket ilkesi oluşturabilir ve bu kez tüm kullanıcıları belirtebilirsiniz.


> Varsayılan etiketlerin otomatik olarak oluşturulmasına ve sizin için 1-3 arası adımları uygulayan bir varsayılan etiket ilkesine uygun olabilirsiniz. Daha fazla bilgi için bkz. [Microsoft Purview Information Protection için varsayılan etiketler ve ilkeler](mip-easy-trials.md).

Duyarlılık etiketlerini dağıtmak ve uygulamak için temel akış:

![Duyarlılık etiketleri için iş akışını gösteren diyagram.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Duyarlılık etiketleri için abonelik ve lisans gereksinimleri

Çeşitli abonelikler duyarlılık etiketlerini destekler ve kullanıcıların lisans gereksinimleri kullandığınız özelliklere bağlıdır.

Kullanıcılarınızın Microsoft Purview özelliklerinden yararlanması için lisanslama seçeneklerini görmek [için güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzuna](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) bakın. Duyarlılık etiketleri için, özellik düzeyi lisanslama gereksinimleri için [Microsoft Purview Information Protection: Duyarlılık etiketleme](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling) bölümüne ve ilgili [PDF indirme](https://go.microsoft.com/fwlink/?linkid=2139145) bölümüne bakın.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Duyarlılık etiketlerini oluşturmak ve yönetmek için gereken izinler

Duyarlılık etiketleri oluşturacak uyumluluk ekibinizin üyelerinin Microsoft Purview uyumluluk portalında izinlere sahip olması gerekir.

Varsayılan olarak, kiracınızın genel yöneticileri bu yönetim merkezine erişebilir ve uyumluluk görevlilerine ve diğer kişilere kiracı yöneticisinin tüm izinlerini vermeden erişim verebilir. Bu sınırlı yönetici erişimi temsilcisi için Kullanıcıları **Uyumluluk Verileri Yöneticisi**, **Uyumluluk Yöneticisi** veya **Güvenlik Yöneticisi** rol grubuna ekleyin. 

Alternatif olarak, varsayılan rolleri kullanmak için yeni bir rol grubu oluşturabilir ve bu gruba **Duyarlılık Etiketi Yöneticisi** veya **Kuruluş Yapılandırması** rolleri ekleyebilirsiniz. Salt okunur bir rol için **Duyarlılık Etiketi Okuyucusu'nu** kullanın. 

> [!NOTE]
> Artık önizleme aşamasında aşağıdaki rol gruplarını kullanabilirsiniz:
> - **Information Protection**
> - **Information Protection Yöneticileri**
> - **Information Protection Analistleri**
> - **Information Protection Araştırmacıları**
> - **Information Protection Okuyucular**
>
> Her birinin ve içerdikleri yeni rollerin açıklaması için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">, Microsoft Purview uyumluluk portalıNda</a> >  bir rol grubu seçin **&** **rollerİşlem** >  **merkeziRoller'i** >  seçin ve açılır bölmedeki açıklamayı gözden geçirin. Veya bkz [. Güvenlik & Uyumluluk Merkezi'nde rol grupları](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Varsayılan rol grubuna, rollere kullanıcı ekleme veya kendi rol gruplarınızı oluşturma yönergeleri için bkz. [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md).

Bu izinler yalnızca duyarlılık etiketleri ve bunların etiket ilkelerini oluşturmak ve yapılandırmak için gereklidir. Etiketleri uygulama veya hizmetlere uygulamalarına gerek yoktur. Duyarlılık etiketleriyle ilgili belirli yapılandırmalar için ek izinler gerekiyorsa, bu izinler ilgili belge yönergelerinde listelenir.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Duyarlılık etiketleri için dağıtım stratejisi
Bir kuruluş için duyarlılık etiketlerini dağıtmanın başarılı bir stratejisi, iş ve teknik gereksinimleri, kavram kanıtı testini, iç denetim noktalarını ve onayları ve üretim ortamı için son dağıtımı tanımlayan ve yöneten çalışan bir sanal ekip oluşturmaktır.

Sonraki bölümdeki tabloyu kullanarak, en etkili iş gereksinimlerinizle eşleşen en iyi bir veya iki senaryoyu tanımlamanızı öneririz. Bu senaryolar dağıtıldıktan sonra, dağıtım için bir veya iki öncelik belirlemek üzere listeye dönün.

## <a name="common-scenarios-for-sensitivity-labels"></a>Duyarlılık etiketleri için yaygın senaryolar

Tüm senaryolarda [duyarlılık etiketleri ve ilkeleri oluşturup yapılandırmanız](create-sensitivity-labels.md) gerekir.

|Yapmak istiyorum...|Belge|
|----------------|---------------|
|İçeriğin oluşturulduğu şekilde etiketlenmesi için Office uygulamalar için duyarlılık etiketlerini yönetme; tüm platformlarda el ile etiketleme desteği içerir |[Office uygulamalarında duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md)|
|Windows'da Office uygulamalarına yönelik ek özelliklerle etiketlemeyi Dosya Gezgini ve PowerShell'e genişletme (gerekirse)|[Windows için Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/rms-client/aip-clientv2)|
|Duyarlılık etiketleriyle belgeleri ve e-postaları şifreleyin ve bu içeriğe kimlerin erişebileceğini ve nasıl kullanılabileceğini kısıtlayın |[Şifreleme uygulamak için hassasiyet etiketleri kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md)|
|Belgeler şifrelendiğinde bile birlikte yazma, eBulma, veri kaybı önleme, arama desteğiyle Web üzerinde Office için duyarlılık etiketlerini etkinleştirin | [SharePoint ve OneDrive'daki Office dosyaları için hassasiyet etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md)
|Belgeler şifrelendiğinde Office masaüstü uygulamalarında birlikte yazma ve Otomatik Kaydetme kullanma | [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirme](sensitivity-labels-coauthoring.md)
|Belgelere ve e-postalara duyarlılık etiketlerini otomatik olarak uygulama | [İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md)|
|Teams ve SharePoint içeriği korumak için duyarlılık etiketlerini kullanma |[duyarlılık etiketlerini Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleri ile kullanma](sensitivity-labels-teams-groups-sites.md)|
|SharePoint ve OneDrive'da siteler ve tek tek belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanın |[SharePoint ve OneDrive'de siteler ve belgeler için varsayılan paylaşım bağlantısını ayarlamak için duyarlılık etiketlerini kullanma](sensitivity-labels-default-sharing-link.md)|
|SharePoint kitaplığındaki tanımlanan belgelerin otomatik olarak sınıflandırılması ve korunması için belge anlama modeline duyarlılık etiketi uygulama |[Microsoft SharePoint Syntex'da modele duyarlılık etiketi uygulama](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Belirli bir duyarlılık etiketine sahip dosya veya e-posta paylaşımını engelleme veya kullanıcıları uyarma |[DLP ilkelerinde duyarlılık etiketlerini koşul olarak kullanma](dlp-sensitivity-label-as-condition.md) |
|Kişisel verileri içeren içeriğin paylaşıldığını ve korunması gerektiğini belirten bir uyarı alırsam dosyaya duyarlılık etiketi uygulama| [Gizlilik Risk Yönetimi'nde uyarıları araştırma ve düzeltme](/privacy/priva/risk-management-alerts)|
|Belirli bir duyarlılık etiketine sahip dosyaları veya e-postaları korumak veya silmek için bekletme etiketi uygulama|[İçeriği korumak veya silmek için otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md) |
|Şirket içindeki veri depolarında depolanan dosyaları bulma, etiketleme ve koruma |[Dosyaları otomatik olarak sınıflandırmak ve korumak için Azure Information Protection tarayıcısını dağıtma](/azure/information-protection/deploy-aip-scanner)|
|Bulutta bulunan veri depolarında depolanan dosyaları bulma, etiketleme ve koruma|[Bulutta depolanan düzenlenmiş ve hassas verileri bulma, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|SQL veritabanı sütunlarını, dosya ve e-postalar için kullanılan duyarlılık etiketlerini kullanarak etiketleyin; böylece kuruluş, dışarı aktarıldığında bu yapılandırılmış verileri korumaya devam eden birleşik bir etiketleme çözümüne sahip olur |[Azure SQL Veritabanı, Azure SQL Yönetilen Örneği ve Azure Synapse Analytics için Veri Bulma & Sınıflandırması](/azure/azure-sql/database/data-discovery-and-classification-overview) <br /><br /> [şirket içi SQL Server için Veri Bulma ve Sınıflandırma SQL](/sql/relational-databases/security/sql-data-discovery-and-classification)|
|Power BI etiketleri uygulama ve görüntüleme ve hizmet dışında kaydedildiğinde verileri koruma|[Power BI duyarlılık etiketleri](/power-bi/admin/service-security-sensitivity-label-overview)|
|Kuruluşumda duyarlılık etiketlerinin nasıl kullanıldığını izleme ve anlama|[Veri sınıflandırması hakkında daha fazla bilgi edinme](data-classification-overview.md)|
|Duyarlılık etiketlerini üçüncü taraf uygulamalara ve hizmetlere genişletme|[Microsoft Bilgi Koruması SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Duyarlılık etiketlerini Azure Blob Depolama, Azure Dosyalar, Azure Data Lake Storage ve çok bulutlu veri kaynakları gibi Microsoft Purview Veri Eşlemesi varlıklarımdaki içerik genelinde genişletme|[Microsoft Purview Veri Haritası'nda etiketleme](/azure/purview/create-sensitivity-label) |

## <a name="end-user-documentation-for-sensitivity-labels"></a>Duyarlılık etiketleri için son kullanıcı belgeleri

En etkili son kullanıcı belgeleri, seçtiğiniz etiket adları ve yapılandırmaları için sağladığınız özelleştirilmiş yönergeler ve yönergeler olacaktır. Bu belgeler için **iç bağlantı belirtmek üzere Kullanıcılara özel bir yardım sayfasının bağlantısını sağlayın** etiket ilkesi ayarını kullanabilirsiniz. Kullanıcılar daha sonra **Duyarlılık** düğmesinden bu düğmeye kolayca erişebilir:

- Yerleşik etiketleme için: **Daha Fazla Bilgi** menü seçeneği.
- Azure Information Protection birleşik etiketleme istemcisi için: **yardım ve geri bildirim** menü seçeneği > Microsoft Azure Information Protection iletişim kutusundaki **Daha Fazla Bilgi Ver** bağlantısı.

Özelleştirilmiş belgelerinizi sağlamanıza yardımcı olmak için, kullanıcılarınızı eğitmek için kullanabileceğiniz şu sayfaya ve indirmelere bakın: [Duyarlılık Etiketleri için Son Kullanıcı Eğitimi](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Temel yönergeler için aşağıdaki kaynakları da kullanabilirsiniz:

- [Office'te dosyalarınıza ve e-postalarınıza duyarlılık etiketleri uygulama](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Office duyarlılık etiketleriyle ilgili bilinen sorunlar](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Office'da dosyalarınıza ve e-postalarınıza duyarlılık etiketlerini otomatik olarak uygulama veya önerme](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Duyarlılık etiketlerini otomatik olarak uygulama veya önerme ile ilgili bilinen sorunlar](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Azure Information Protection birleşik etiketleme kullanıcı kılavuzu](/azure/information-protection/rms-client/clientv2-user-guide)

Duyarlılık etiketleriniz PDF belgeleri için şifreleme uyguluyorsa, bu belgeler Windows veya Mac'te Microsoft Edge ile açılabilir. Daha fazla bilgi ve alternatif [okuyucular için bkz. Korumalı PDF'ler için hangi PDF okuyucular desteklenir?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
