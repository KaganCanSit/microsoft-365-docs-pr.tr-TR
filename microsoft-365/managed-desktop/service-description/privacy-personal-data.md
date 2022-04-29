---
title: Gizlilik ve kişisel veriler
description: Hizmet tarafından toplanan, depolanan ve kullanılan verilerin ayrıntıları
keywords: GDPR, saklama, silme, depolama, saklama, işleme, güvenlik, denetim
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
ms.openlocfilehash: e7c9912e3890d9b13003c7f3264490f67c4fc305
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128356"
---
# <a name="privacy"></a>Gizlilik

Microsoft Managed Desktop, çalışanların Windows cihazlarının dağıtılıp güncelleştirilmelerini sağlamak üzere tasarlanmış kurumsal bulut müşterilerine yönelik bir Hizmet Olarak BT (ITaaS) hizmetidir.

Ayrıca BT hizmeti yönetimi ve işlemleri sağlar, güvenlik ve olay yanıtlarını izler ve kullanıcı desteği sağlar. Bu makalede, Microsoft Managed Desktop için veri platformu ve gizlilik uyumluluğu hakkında daha fazla ayrıntı sağlanır.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Veri kaynaklarını ve amacı Microsoft Managed Desktop

Microsoft Managed Desktop, hizmetini kurumsal müşterilere sağlar ve çeşitli kaynaklardan alınan verileri kullanarak müşterilerin kayıtlı cihazlarını düzgün bir şekilde yönetir.

Bu kaynaklar Azure Active Directory, Microsoft Intune, Microsoft Windows 10 ve Uç Nokta için Microsoft Defender içerir. Microsoft Managed Desktop yönettiği cihazların kapsamlı bir görünümünü sağlar. Hizmet, Microsoft Managed Desktop ITaaS özelliklerini sağlamasını sağlamak için de bu Microsoft hizmetleri kullanır:

| Veri kaynağı | Amaç |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Cihaz kurulum deneyiminin yönetimi, diğer hizmetlere bağlantıları yönetme ve BT uzmanları için operasyonel destek. |
| [İş İçin Windows Update](/windows/deployment/update/waas-manage-updates-wufb) | Windows 10 güncelleştirme hakkında ek bilgi sağlamak için Windows 10 Enterprise tanılama verilerini kullanır. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Cihaz yönetimi ve verilerinizin güvenliğini sağlamak için. Aşağıdaki veri kaynakları Microsoft Endpoint Manager altındadır:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): Tüm kullanıcı hesaplarının kimlik doğrulaması ve kimliği.</li><li>[Microsoft Intune](/mem/intune/): Cihaz yapılandırmalarını, cihaz yönetimini ve uygulama yönetimini dağıtma.</li><li>[Endpoint Analytics](/mem/analytics/overview): Cihaz ve uygulama kullanımı hakkında analitik içgörüler.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): Cihaz sağlama ve dağıtım.</li><li>[Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/): Cihaz güvenlik izleme ve güvenlik bilgileri verileri gibi güvenlik hizmetleri sağlar.</li></ul>
| [Microsoft Yönetilen Masaüstü](https://endpoint.microsoft.com/#home) | Müşteri tarafından sağlanan veya hizmet çalıştırılırken hizmet tarafından oluşturulan veriler. |
| [Kurumsal uygulamalar Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Microsoft 365 Uygulamaları yönetimi.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>veri işlemini ve depolamayı Microsoft Managed Desktop

Microsoft Managed Desktop, hizmetini kurumsal müşterilere sunmak için birden çok Microsoft ürün ve hizmetindeki verilere dayanır.

Kayıtlı cihazları korumak ve bakımını yapmak için bu hizmetlerden verileri işleyip Microsoft Managed Desktop kopyalarız. Verileri işlediğimizde, [Çevrimiçi Hizmet Koşulları](https://www.microsoft.com/licensing/product-licensing/products) ve [Microsoft Gizlilik Bildirimi'nde](https://privacy.microsoft.com/privacystatement) belirtildiği gibi sağladığınız belgelenmiş yönergeleri izleriz.

Microsoft Managed Desktop'ın işlemci görevleri arasında uygun gizlilik, güvenlik ve dayanıklılığın sağlanması yer alır. Microsoft Managed Desktop, kişisel verilerin düzgün işlenmesini sağlamak için ek gizlilik ve güvenlik önlemlerini devreye alır.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Veri depolama ve personel konumunu Microsoft Managed Desktop

Microsoft Managed Desktop verilerini Birleşik Devletler Azure veri merkezlerinde depolar.

Hizmetin çalışır durumda kalması için Microsoft Managed Desktop ve diğer hizmetler tarafından elde edilen kişisel veriler gereklidir. Bir cihaz Microsoft Managed Desktop kaldırılırsa, kişisel verileri en fazla 30 gün saklarız. Ancak, Uç Nokta için Microsoft Defender tarafından toplanan uyarı verileri güvenlik amacıyla 180 gün boyunca depolanır. Veri saklama hakkında daha fazla bilgi için bkz. [Microsoft 365 veri saklama, silme ve yok etme](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

Microsoft Managed Desktop Mühendislik Operasyon ve Güvenlik Operasyonları ekipleri Birleşik Devletler, Hindistan ve Romanya'da yer almaktadır.

### <a name="microsoft-windows-10-diagnostic-data"></a>Microsoft Windows 10 tanılama verileri

Microsoft Managed Desktop, Windows güvenli, güncel tutmak, sorunları gidermek ve ürün geliştirmeleri yapmak için Windows 10 [Gelişmiş tanılama verilerini](/windows/privacy/windows-diagnostic-data) kullanır.

Gelişmiş tanılama verileri ayarı, Microsoft Managed Desktop kaydedilen cihazlar ve bunların ayarları, özellikleri ve cihaz durumu hakkında daha ayrıntılı bilgiler içerir. Gelişmiş tanılama verileri seçildiğinde, gerekli tanılama verileri de dahil olmak üzere veriler toplanır. Daha fazla bilgi için bkz. [Windows 10 tanılama verileri ayarı ve veri toplama hakkında tanılama verileri toplama Windows değişiklikler](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Tanılama verisi terminolojisi, Windows gelecek sürümlerinde değişecektir. Microsoft Managed Desktop yalnızca hizmetin ihtiyaç duyduğu verileri işlemeye kararlıdır. Bu, tanılama düzeyinin **İsteğe bağlı** olarak değiştirileceği anlamına gelir, ancak Microsoft Managed Desktop hizmet için gerekli tanılama verileri toplamaya ince ayar yapmak için sınırlı tanılama ilkelerini uygular. Daha fazla bilgi için bkz. [Windows tanılama verilerini toplama değişiklikleri](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop yalnızca uygulama ve cihaz güvenilirliği ve performans bilgileri gibi kayıtlı cihazlardan kaynaklanan isteğe bağlı Windows 10 tanılama verilerini işler ve depolar. Microsoft Managed Desktop, müşterilerin sohbet ve tarayıcı geçmişi, ses, metin veya konuşma verileri gibi kişisel verilerini işlemez ve depolamaz.

Microsoft Windows 10 tanılama verilerini toplama hakkında daha fazla bilgi için Microsoft Gizlilik Bildirimi'nin [Kişisel verileri depolama ve işleme yeri](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) bölümüne bakın.

### <a name="microsoft-windows-update-for-business"></a>İş İçin Microsoft Windows Update

İş için Microsoft Windows Update, güncelleştirme durumunu ve hatalarını analiz etmek için Windows tanılama verilerini kullanır. Microsoft Managed Desktop bu verileri kullanır ve bunları kullanarak tüm kayıtlı cihazların önceden tanımlanmış bir güncelleştirme düzenine göre güncel olduğundan emin olmak için sorunları azaltır ve çözer.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Microsoft Managed Desktop tarafından kullanılan verilerin tanımlanması, coğrafi bir konumda Azure Active Directory (Azure AD) tarafından depolanır. Coğrafi konum, Enterprise ve Azure için Microsoft Apps gibi Microsoft çevrimiçi hizmetler abone olduğunda kuruluş tarafından sağlanan konumu temel alır. Azure AD verilerinizin bulunduğu yer hakkında daha fazla bilgi için bkz. [Azure Active Directory - Verileriniz nerede bulunur?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune, iş operasyonlarını ve hizmetlerini desteklemek için verileri toplar, işler ve Microsoft Managed Desktop paylaşır. Intune'de toplanan veriler hakkında daha fazla bilgi için bkz. [Intune'de veri toplama](/mem/intune/protect/privacy-data-collect)

Microsoft Intune veri konumları hakkında daha fazla bilgi için bkz. [Microsoft 365 müşteri verilerinizin depolandığı yer](/microsoft-365/enterprise/o365-data-locations). Intune, yönetici tarafından müşteri verileri için yapılan depolama konumu seçimlerine saygı gösterir.

### <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

Uç Nokta için Microsoft Defender yönetim, izleme ve raporlama amacıyla Microsoft Managed Desktop kayıtlı cihazlar için bilgileri toplar ve depolar. Toplanan bilgiler şunları içerir:

- Dosya verileri (dosya adları, boyut ve karmalar gibi)
- İşlem verileri (çalışan işlemler, karmalar)
- Kayıt defteri verileri
- Ağ bağlantısı verileri
- Cihaz ayrıntıları (cihaz tanımlayıcıları, cihaz adları ve işletim sistemi sürümü gibi)

Uç Nokta için Microsoft Defender veri toplama ve depolama konumları hakkında daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender veri depolama ve gizlilik](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Enterprise için Microsoft 365 Uygulamaları

Enterprise için Microsoft 365 Uygulamaları, bu uygulamaların en son sürümle güncel olduğundan emin olmak için verileri Microsoft Managed Desktop ile toplar ve paylaşır. Bu güncelleştirmeler, Microsoft Managed Desktop tarafından yönetilen önceden tanımlanmış güncelleştirme kanallarını temel alır. Microsoft 365 Uygulamaları veri toplama ve depolama konumları hakkında daha fazla bilgi için bkz. [veri depolama ve gizlilik Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Önemli veri değişikliği bildirimi

Microsoft Managed Desktop, hizmet iletişim çerçevemizde açıklandığı gibi bir değişiklik denetimi sürecini izler.

Müşterilere Microsoft 365 İleti Merkezi aracılığıyla bildirim göndeririz ve hem güvenlik olaylarını hem de hizmette yapılan önemli değişiklikleri Yönetici portalı Microsoft Managed Desktop.

Toplanan veri türlerinde ve depolandığı yerde yapılan değişiklikler önemli bir değişiklik olarak kabul edilir. Microsoft 365 ürün ve hizmetleri için standart uygulama olarak bu değişiklikle ilgili en az 30 gün ileri düzey bildirim sağlayacağız. Daha fazla bilgi için bkz [. Hizmet değişiklikleri ve iletişim](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Uyumluluk

Microsoft Managed Desktop dış denetimlerden geçmiş ve kapsamlı bir uyumluluk teklifi kümesi edinmiştir. [Uyumluluk](/microsoft-365/managed-desktop/intro/compliance) bölümünde daha fazla bilgi bulabilirsiniz. Denetim raporları, Microsoft Enterprise Online Services için merkezi bir depo olarak hizmet veren Microsoft [Hizmet Güveni Portalı'nda](https://aka.ms/stp) indirilebilir. Microsoft Managed Desktop bu belgelerde "İzleme ve Yönetim" kategorisi altında listelenir.

### <a name="data-subject-requests"></a>Veri sahibi istekleri

Microsoft Managed Desktop, veri sahiplerine kişisel verilerine özgü haklar veren GDPR ve CCPA gizlilik düzenlemelerini izler.

Bu haklar şunlardır:

- Kişisel verilerin kopyalarını alma
- Düzeltme isteğinde bulunma
- İşlenmeyi kısıtlama
- Silme
- Başka bir denetleyiciye taşınabilmesi için elektronik biçimde alma.

Veri Sahibi İstekleri (DSR) hakkında daha genel bilgi için bkz. [Veri Sahibi İstekleri, GDPR ve CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Microsoft Managed Desktop servis talebi yönetim sistemi tarafından toplanan veriler üzerinde veri sahibi isteklerini alıştırmak için aşağıdaki veri sahibi isteklerine bakın:

| Veri sahibi istekleri | Açıklama |
| ------ | ------ |
| Uç Nokta için Microsoft Defender uyarılarından gelen veriler | Güvenlik yöneticiniz, [Yönetici Portalı'nda](https://aka.ms/memadmin) bir rapor isteği göndererek Uç Nokta için Microsoft Defender uyarılarıyla ilgili kişisel verilerin silinmesini veya ayık olmasını isteyebilir. <br><br> Aşağıdaki bilgileri sağlayın: <br><ul><li>İstek türü: değişiklik isteği</li><li>Kategori: Güvenlik</li><li>Alt kategori: Diğer</li><li>Açıklama: İlgili cihaz adlarını belirtin.</li></ul> |
| Microsoft Managed Desktop destek isteklerindeki veriler | BT yöneticiniz, [Yönetim Portalı'nda](https://aka.ms/memadmin) bir rapor isteği göndererek kişisel verilerle ilgili destek isteklerinin silinmesini veya ayıksını isteyebilir. <br><br> Aşağıdaki bilgileri sağlayın: <ul><li>İstek türü: değişiklik isteği</li><li>Kategori: Güvenlik</li><li>Alt kategori: Diğer</li><li>Açıklama: İlgili cihaz adlarını veya kullanıcı adlarını belirtin.</li></ul>

Hizmetle ilgili diğer ürünlerden DSR'ler için aşağıdaki makalelere bakın:

- [Tanılama verilerini](/compliance/regulatory/gdpr-dsr-windows) Windows
- Microsoft [Intune verileri](/compliance/regulatory/gdpr-dsr-intune)
- Azure Active [Directory verileri](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Yasal

**Microsoft'un kuruluş müşterileri tarafından sağlanan ürünlerin son kullanıcılarına gizlilik bildirimi**:

[Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement), son kullanıcılara microsoft ürünlerinde bir iş hesabıyla oturum açtıklarında şu bilgileri bildirir:

1. Kuruluş, hesabını denetleyebiliyor ve yönetebiliyor (gizlilikle ilgili ayarları denetleme dahil) ve verilerine erişip işleyebilir.
1. Microsoft, hizmeti kuruluşa ve son kullanıcılara sağlamak için verileri toplayıp işleyebilirsiniz.
