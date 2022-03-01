---
title: Gizlilik ve kişisel veriler
description: Hizmet tarafından toplanan, depolanan ve kullanılan verilerin ayrıntıları
keywords: GDPR, bekletme, silme, depolama, bekletme, işleme, güvenlik, denetim
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
manager: dougeby
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: medium
ms.openlocfilehash: a381bc70e73bf3bbb9f654f5d5dfffd2047f8ab5
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015458"
---
# <a name="privacy"></a>Gizlilik

Microsoft Yönetilen Masaüstü, çalışanların kendi cihazlarının dağıtılmalarını ve güncellenmelerini sağlamak için tasarlanmış kurumsal bulut müşterilerine bir Hizmet Olarak (ITaaS) Windows hizmetidir.

Ayrıca, IT hizmet yönetimi ve işlemleri sağlar, güvenlik ve olay yanıtlarını izler ve kullanıcı desteği sağlar. Bu makalede, Microsoft Yönetilen Masaüstü için veri platformu ve gizlilik uyumluluğu ile ilgili daha fazla ayrıntı bulabilirsiniz.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Yönetilen Masaüstü veri kaynakları ve amacı

Microsoft Yönetilen Masaüstü, hizmetini kurumsal müşterilere sunar ve çeşitli kaynaklardan veriler kullanarak müşterilerin kayıtlı cihazlarını düzgün bir şekilde yönetmektedir.

Bu kaynaklar Azure Active Directory, Microsoft Intune, Microsoft Windows 10 ve Uç Nokta için Microsoft Defender'ı içerir. Microsoft Tarafından Yönetilen Masaüstü tarafından yönetilen cihazlara kapsamlı bir görünüm sağlar. Hizmet, Microsoft Yönetilen Masaüstü'Microsoft hizmetleri ITaaS özelliklerini sağlamak için aşağıdaki özellikleri de kullanır:

| Veri kaynağı | Amaç |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Cihaz kurulum deneyiminin yönetimi, diğer hizmetlere bağlantıların yönetilmesi ve IT profesyonelleri için işlem desteği. |
| [Windows güncelleştirme](/windows/deployment/update/waas-manage-updates-wufb) | Güncelleştirme Windows 10 Enterprise fazla bilgi sağlamak için bu tanılama verilerini Windows 10 kullanır. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Cihaz yönetimi ve verilerinizi güvende tutma. Aşağıdaki veri kaynakları aşağıdaki veri kaynaklarının Microsoft Endpoint Manager:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): Tüm kullanıcı hesaplarının kimlik doğrulaması ve kimliği.</li><li>[Microsoft Intune](/mem/intune/): Cihaz yapılandırmalarını, cihaz yönetimini ve uygulama yönetimini dağıtma.</li><li>[Uç Nokta Analizi](/mem/analytics/overview): Cihaz ve uygulama kullanımıyla ilgili analitik öngörüler.</li><li>[Windows Pilot](/microsoft-365/windows/windows-autopilot): Cihaz hazırlama ve dağıtım.</li><li>[Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/): Cihaz güvenliği izleme ve güvenlik zekası verileri gibi güvenlik hizmetleri sağlar.</li></ul>
| [Microsoft Yönetilen Masaüstü](https://endpoint.microsoft.com/#home) | Müşteri tarafından sağlanan veya hizmeti çalıştırma sırasında hizmet tarafından oluşturulan veriler. |
| [Microsoft 365 için uygulamalarınızı oluşturun](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Yönetim Microsoft 365 Uygulamaları.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Yönetilen Masaüstü veri işlemi ve depolama

Microsoft Yönetilen Masaüstü, kurumsal müşterilere hizmet sunmak için birden çok Microsoft ürünü ve hizmetinin verilerine güvenmektedir.

Kayıtlı cihazları korumak ve korumak için bu hizmetlerden verileri Microsoft Yönetilen Masaüstü'ne işlemeyi ve kopyalamayı sağlarız. Verileri işlemeyi sağlarken, Çevrimiçi Hizmetler Koşulları ve Microsoft Gizlilik Bildirimi'ne başvurularak, [belgelenmiş yönergeleri](https://www.microsoft.com/licensing/product-licensing/products) [takip ederiz](https://privacy.microsoft.com/privacystatement).

Microsoft Yönetilen Masaüstü'nin işlemci görevleri uygun gizlilik, güvenlik ve güvenden emin olmaktır. Microsoft Yönetilen Masaüstü, kişisel kişisel verilerin düzgün işlenmesini sağlamak için ek gizlilik ve güvenlik önlemleri almaktadır.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Yönetilen Masaüstü veri depolaması ve personel konumu

Microsoft Yönetilen Masaüstü verilerini ABD'nin Azure veri merkezlerinde depolar.

Microsoft Yönetilen Masaüstü ve diğer hizmetler tarafından alınan kişisel verilerin hizmetin çalışır durumda olması gerekir. Microsoft Yönetilen Masaüstü'nden bir cihaz kaldırılırsa, kişisel verileri en çok 30 gün süreyle tutariz. Bununla birlikte, Uç Nokta için Microsoft Defender tarafından toplanan uyarı verileri, güvenlik nedeniyle 180 gün süreyle depolanır. Veri bekletme hakkında daha fazla bilgi için bkz[. Veri bekletme, silme ve Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

Microsoft Yönetilen Masaüstü Mühendislik İşlemleri ve Güvenlik İşlemleri ekipleri ABD ve Hindistan'da bulunur.

### <a name="microsoft-windows-10-diagnostic-data"></a>Microsoft Windows 10 verilerini güncelleştirme

Microsoft Yönetilen Masaüstü, [Windows 10, güncel bir şekilde verilerinizi](/windows/privacy/windows-diagnostic-data) güvende Windows sorunları gidermek ve ürün geliştirmeleri yapmak için Gelişmiş Tanılama verilerini kullanır.

Gelişmiş tanılama verileri ayarı, Microsoft Yönetilen Masaüstü'ne kaydolan cihazlar ve bunların ayarları, yetenekleri ve cihaz durumu hakkında daha ayrıntılı bilgi içerir. İyileştirilmiş tanılama verileri seçildiğinde, gerekli tanılama verileri de içinde olmak üzere veriler toplanır. Daha fazla bilgi için bkz[. Tanılama Windows ayarları](/windows/privacy/changes-to-windows-diagnostic-data-collection) ve veri toplama hakkında tanılama Windows 10 verileri toplama.

Tanılama veri terminolojisi, verilerin gelecek sürümlerinde Windows. Microsoft Yönetilen Masaüstü, yalnızca hizmet için gereken verileri işlemeyi taahhüt ediyor. Bu, tanılama düzeyinin İsteğe Bağlı olarak değiş değişecek olmasıyla **birlikte, Microsoft** Yönetilen Masaüstü hizmet için gereken tanılama veri toplamaya yönelik sınırlı tanılama ilkelerini uygulayacak. Daha fazla bilgi için bkz[. Tanılama Windows veri toplamada yapılan değişiklikler](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Yönetilen Masaüstü yalnızca, uygulama ve cihaz güvenilirliği ve performans bilgileri gibi kayıtlı cihazlardan Windows 10 isteğe bağlı tanılama verilerini işler ve depolar. Microsoft Yönetilen Masaüstü, müşterilerin sohbet ve tarayıcı geçmişi, ses, metin veya konuşma verileri gibi kişisel verilerini işlemez ve depolamaz.

Microsoft Windows 10'un tanılama veri toplaması hakkında daha fazla bilgi için, Microsoft Gizlilik Bildirimi'nin Kişisel verileri nerede depoları ve işlemesi bölümüne bakın.[](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule)

### <a name="microsoft-windows-update-for-business"></a>İş Windows Microsoft Güncelleştirmesi

Microsoft Windows İş Güncelleştirmesi, güncelleştirme durumunu ve Windows tanılamada yer alan verileri kullanır. Microsoft Yönetilen Masaüstü bu verileri kullanır ve bu verileri azaltmak ve tüm kayıtlı cihazların önceden tanımlanmış bir güncelleştirme tempos nedeniyle güncel olmasını sağlamak için sorunları çözmek için kullanır.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Microsoft Yönetilen Masaüstü tarafından kullanılan veriler, Azure Active Directory (Azure AD) tarafından coğrafi bir konumda depolanır. Coğrafi konum, Microsoft Apps Enterprise ve Azure gibi Microsoft çevrimiçi hizmetlere abone olarak kuruluş tarafından sağlanan konuma dayalıdır. Azure AD verilerinizin nerede bulunduğu hakkında daha fazla bilgi için bkz. [Azure Active Directory - Verileriniz nerede?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune işlemlerini ve hizmetlerini desteklemek için microsoft Yönetilen Masaüstü'ne veri toplar, işler ve paylaşımlar sağlar. Intune'da toplanan veriler hakkında daha fazla bilgi için bkz [. Intune'da veri toplama](/mem/intune/protect/privacy-data-collect) 

Veri konumlarını daha Microsoft Intune için bkz. [Müşteri verilerinizin Microsoft 365 nerede depolanır](/microsoft-365/enterprise/o365-data-locations). Intune, müşteri verileri için yönetici tarafından yapılan depolama konumu seçimlerine saygılıdır.

### <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

Uç Nokta için Microsoft Defender yönetim, izleme ve raporlama amacıyla Microsoft Yönetilen Masaüstü'ne kayıtlı cihazların bilgilerini toplar ve depolar. Toplanan bilgiler:

- Dosya verileri (dosya adları, boyutu ve karmalar gibi)
- Süreç verileri (çalışan süreçler, karmalar)
- Kayıt defteri verileri
- Ağ bağlantısı verileri
- Cihaz ayrıntıları (cihaz tanımlayıcıları, cihaz adları ve işletim sistemi sürümü gibi)

Uç noktanın veri toplaması ve depolama konumları için Microsoft Defender hakkında daha fazla bilgi için bkz. Uç nokta veri depolaması ve gizliliği için [Microsoft Defender](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Uygulamaları için Enterprise

Microsoft 365 Uygulamaları için Enterprise, bu uygulamaların en son sürümle güncel olduğundan emin olmak için Microsoft Yönetilen Masaüstü ile veri toplar ve bilgi paylaşımı sağlar. Bu güncelleştirmeler, Microsoft Yönetilen Masaüstü tarafından yönetilen önceden tanımlanmış güncelleştirme kanallarını temel almaktadır. Verilerinizin veri toplama Microsoft 365 Uygulamaları depolama konumları hakkında daha fazla bilgi için bkz. Uç nokta veri [depolaması ve gizliliği için Microsoft Defender](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Önemli veri değişikliği bildirimi

Microsoft Yönetilen Masaüstü, hizmet iletişim çerçevemizde ana hatlarıyla açıklanan değişiklik denetim sürecini izler.

Bu durumu, Microsoft 365 ve Microsoft Yönetilen Masaüstü Yönetim portalı üzerinden, hizmetle ilgili olarak hem güvenlik olayları hem de önemli değişiklikler hakkında müşterilere bildirim sunarsınız.

Toplanmış veri türlerinde ve burada depolandığı yerde yapılan değişiklikler, malzeme değişikliği olarak kabul edilir. Standart uygulama olarak bu değişikliğin ürün ve hizmetleri için en az 30 gün içinde gelişmiş Microsoft 365 bildirimini sağlarız. Daha fazla bilgi için bkz [. Hizmet değişiklikleri ve iletişim](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Uyumluluk

Microsoft Yönetilen Masaüstü'ne dış denetimler yapıldı ve kapsamlı bir uyumluluk teklifi kümesi elde edildi. Daha fazla bilgiyi Uyumluluk altında [bulabilirsiniz](/microsoft-365/managed-desktop/intro/compliance). Denetim raporları, Microsoft Enterprise Online Services için merkezi [](https://aka.ms/stp)bir depo olarak hizmet veren Microsoft Hizmet Güveni Portalı'Enterprise kullanılabilir. Microsoft Yönetilen Masaüstü bu belgelerin içinde, "İzleme ve Yönetim" kategorisi altında listelenir.

### <a name="data-subject-requests"></a>Veri konusu istekleri

Microsoft Yönetilen Masaüstü GDPR ve CCPA gizlilik düzenlemelerine uygundur ve bu düzenlemeler kişisel verileriyle ilgili belirli haklar verir.

Bu haklar şunlardır:

- Kişisel verilerin kopyalarını alma
- Düzeltme talep ediyor
- İşlemeyi kısıtlama
- Silindi
- Elektronik biçimde alınarak başka bir denetleyiciye taşınabilirsiniz.

Veri Konusu İstekleri (DSR) hakkında daha genel bilgiler için bkz. Veri Konusu İstekleri [ve GDPR ve CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Microsoft Yönetilen Masaüstü olay yönetim sistemi tarafından toplanan veriler üzerinde veri konusu isteklerini alıştırmak için, aşağıdaki veri konusu isteklerine bakın:

| Veri konusu istekleri | Açıklama |
| ------ | ------ |
| Uç nokta uyarıları için Microsoft Defender'dan veriler | Güvenlik yöneticiniz, Yönetim Portalı'na bir rapor isteği göndererek Uç Nokta uyarıları için Microsoft Defender ile ilgili kişisel verilerin silinmesini veya [ayıklamasını ister](https://aka.ms/memadmin). <br><br> Aşağıdaki bilgileri sağlar: <br><ul><li>İstek türü: İsteği değiştir</li><li>Kategori: Güvenlik</li><li>Alt kategori: Diğer</li><li>Açıklama: İlgili cihaz adlarını girin.</li></ul> |
| Microsoft Yönetilen Masaüstü destek isteklerinden veriler | YÖNETIM yöneticiniz, Yönetim Portalı'na bir rapor isteği göndererek kişisel verilerle ilgili destek isteklerinin silinmesini veya [ayıklamasını talep edebilirsiniz](https://aka.ms/memadmin). <br><br> Aşağıdaki bilgileri sağlar: <ul><li>İstek türü: İsteği değiştir</li><li>Kategori: Güvenlik</li><li>Alt kategori: Diğer</li><li>Açıklama: İlgili cihaz adlarını veya kullanıcı adlarını girin.</li></ul>

Hizmetle ilgili diğer ürünlerin DSR'leri için aşağıdaki makalelere bakın:

- Windows [verilerini toplama](/compliance/regulatory/gdpr-dsr-windows)
- Microsoft [Intune verileri](/compliance/regulatory/gdpr-dsr-intune)
- Azure Active [Directory verileri](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Yasal

**Kurumsal müşteriler tarafından sağlanan ürünlerin son kullanıcılarına Microsoft'un gizlilik bildirimi**:

[Microsoft Gizlilik Bildirimi son](https://privacy.microsoft.com/privacystatement) kullanıcılara, iş hesabıyla Microsoft ürünlerinde oturum a açınca:

1. Kuruluşları, hesaplarını kontrol ve yönetme (gizlilikle ilgili ayarları denetleme dahil) ve verilerine erişim ve işleme işlemlerini tamamlar.
1. Microsoft, kuruluşa ve son kullanıcılara hizmet sağlamak için verileri toplar ve işler.
