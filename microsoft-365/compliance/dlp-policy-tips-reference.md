---
title: Veri Kaybı Önleme ilke ipuçları başvurusu
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Veri kaybını önleme (DLP) ilkesine bir ilke ipucunun, kullanıcıya DLP ilkesiyle çakışan içerikle çalıştığını haber verme hakkında bilgi öğrenin.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 227a6438bf1eb645e5bd85acfafeb8222d0b1427
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "63005002"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Veri Kaybı Önleme ilke ipuçları başvurusu

Web Access'Outlook DLP ilkesi ipuçları, aşağıdakiler dışında, bir DLP ilkesinde iş yükünün Exchange tüm koşullar, özel durumlar ve eylemler için de geçerlidir:

**Koşullar:**

- Gönderen:
- GönderenIn Etki Alanı:
- Alıcı,
- Üst bilgi sözcük veya tümcecik içeriyor
- Üst bilgi eşleşme düzenleri
- Belge boyutu eşit veya büyüktür
- İleti türü:
- İletinin önem öneme sahip olduğu
- İçerik karakter kümesi sözcükler içeriyor
- Konu veya gövde sözcük veya tümcecik içeriyor
- Konu veya gövde desenlerini eşler
- İçerik karakter kümesi sözcükler içeriyor
- İçerik alındı
- Gönderen ilke ipucu geçersiz k oldu mu
- İleti boyutu eşittir veya büyüktür
- Sender AD özniteliği sözcük veya tümcecik içeriyor
- Sender AD özniteliği desenlere eşler
- Belge içeriği sözcükler veya tümcecikler içerir
- Belge içeriği desenlere eşler

**Eylemler:**

- Onay için iletiyi gönderenin yöneticisine iletme
- Onay için iletiyi belirli onaylayanlara iletme
- İletiyi belirli kullanıcılara yönlendirme
- Alıcıyı To Box'a ekleme
- Bilgi Kutusuna alıcı ekleme
- Gizli Kutusuna alıcı ekleme
- Gönderenin yöneticisini alıcı olarak ekleme
- HTML yasal uyarı ekleme
- E-posta konusunu hazırlayın
- O365 İleti Şifrelemesi'ne ve hak korumasını kaldırma

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 ve sonrakileri, yalnızca bazı koşullar ve özel durumlar için ilke ipuçlarının göstermeyi destekler

Şu anda Outlook 2013 ve sonraki sürümü, aşağıda belirtilen koşullar ve buna karşılık gelen özel durumlar dışında herhangi bir koşul veya özel durum içeren ilkeler için ilke ipuçlarının göstermeyi destekler:

- İçeriği içerir (yalnızca Hassas bilgi türlerinde çalışır. Duyarlılık etiketleri desteklenmiyor)
- İçerik paylaşılıyor

Tüm koşulların, Outlook istemci uygulamasında yazan e-postalar için uygun olduğunu ve burada içerik üzerinde koruyucu eylemler gerçekleştireceklerini unutmayın. Bununla birlikte, kullanıcılara ilke ipuçlarının göstermek, yukarıda adı geçenlerden farklı olarak kullanılan hiçbir durumda desteklanmaz.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Outlook 2013 ve sonraki bir Office masaüstü uygulamaları desteğinde, yalnızca bazı hassas bilgi türlerine ilişkin ilke ipuçlarının gösteriliyor olması

Masaüstü için Outlook (2013 ve sonrası) ve Masaüstü'de Office uygulamaları (Word, Excel, PowerPoint) içinde DLP ilkesi ipuçlarının göster algılandığında algılandığında saptanan hazır hazır bilgi türleri listesi aşağıda ve veleridir:

- ABA Yönlendirme Numarası
- Arjantin Ulusal Kimliği (DNI) Numarası
- Australia Bank Hesap Numarası
- Avustralya Tıbbi Hesap Numarası
- Avustralya Pasaport Numarası
- Avustralya Vergi Dosyası Numarası
- Azure DocumentDB Kimlik Doğrulaması Anahtarı  
- Azure IAAS Veritabanı Bağlantı Dizesi ve Azure SQL Bağlantı Dizesi  
- Azure IoT Bağlantı Dizesi  
- Azure Yayımlama Ayarları Parolası  
- Azure Önbellek Bağlantı Dizesini Yeniden Dağıt  
- Azure SAS  
- Azure Service Bus Bağlantı Dizesi  
- Azure Depolama Hesap Anahtarı  
- Azure Depolama Hesap Anahtarı (Generic)  
- Belçika Ulusal Numarası
- Brezilya CPF Numarası
- Brezilya Yasal Varlık Numarası (CNPJ)
- Brezilya Ulusal Kimlik Kartı (RG)
- Kanada Banka Hesap Numarası
- Kanada Sürücü Lisans Numarası
- Kanada Sistem Sağlığı Hizmeti Numarası
- Kanada Pasaport Numarası
- Kanada Kişisel Sağlık Kimlik Numarası (PHIN)
- Kanada Sosyal Sigorta Numarası
- Şili Kimlik Kartı Numarası
- Çin Yerleşik Kimlik Kartı (ÇK) Numarası
- Kredi Kartı Numarası
- Hırvatistan Kimlik Kartı Numarası  
- Hırvatistan Kişisel Kimlik (OIB) Numarası  
- Çek Kişisel Kimlik Numarası  
- Danimarka Kişisel Kimlik Numarası
- Enforcement Agency (DEA) Numarası
- AB Banka Kartı Numarası
- EU Sürücü Lisans Numarası  
- AB Ulusal Kimlik Numarası  
- AB Pasaport Numarası  
- AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik  
- AB Vergi Tanımlama Numarası (TIN)  
- Finlandiya Ulusal Kimliği
- Finlandiya Pasaport Numarası
- Fransa Sürücü Lisans Numarası
- Fransa Ulusal Kimlik Kartı (CNI)
- Fransa Pasaport Numarası
- France Social Security Number (INSEE)
- Almanca Sürücü Lisans Numarası
- Almanca Pasaport Numarası
- Almanya Kimlik Kartı Numarası
- Yunanistan Ulusal Kimlik Kartı  
- Hong Kong Kimlik Kartı (HKID) Numarası
- Hindistan Kalıcı Hesap Numarası (PAN)
- Hindistan Benzersiz Tanımlama (Aadhaar) Numarası
- Endonezya Kimlik Kartı (KTP) Numarası
- Uluslararası Bankacılık Hesap Numarası (IBAN)
- Uluslararası Hastalık Sınıflandırması (ICD-10-CM)  
- Uluslararası Hastalık Sınıflandırması (ICD-9-CM)  
- IP Adresi
- Ireland Personal Public Service (PPS) Numarası 
- İsrail Banka Hesap Numarası
- İsrail Ulusal Kimliği
- İtalya Sürücüsü Lisans Numarası
- Japonya Banka Hesap Numarası
- Japonya Sürücüsü Lisans Numarası
- Japonya Pasaport Numarası
- Japonya'daki Yerleşik Kayıt Numarası
- Japonya Sosyal Sigorta Numarası (SN)
- Japonca İkamet Kartı Numarası
- Malezya Kimlik Kartı Numarası
- Hollanda Genel Hizmet Numarası (BSN)  
- Yeni Zelanda Sağlık Numarası
- Norveç Kimlik Numarası  
- Filipinler Birleşik Çok Amaçlı Kimlik Numarası
- Polonya Kimlik Kartı
- Polonya Ulusal Kimliği (PESEL)
- Polonya Pasaport
- Portekiz Portekiz Kart Numarası
- Suudi Arabistan Ulusal Kimliği
- Singapur Ulusal Kayıt Kimlik Kartı (NRIC) Numarası
- Güney Afrika Kimlik Numarası  
- Güney Kore Yerleşik Kayıt Numarası
- İspanya Sosyal Güvenlik Numarası (SSN)
- SQL Server Bağlantı Dizesi  
- İsveç Ulusal Kimliği
- İsveç Pasaport Numarası
- SWIFT Kodu
- Tayvan Ulusal Kimliği
- Tayvan Pasaport Numarası
- Tayvan Yerleşik Sertifikası (ARC/TARC)
- Tay Dili Nüfus Kimlik Kodu
- Türkçe Ulusal Kimlik Numarası
- B.K. Sürücü Lisans Numarası
- B.K. SeçmeLi Rulo Numarası
- B.K. Ulusal Sistem Sağlığı Hizmeti Numarası
- B.K. Ulusal Sigorta Numarası (NINO)
- ABD / U.K. Pasaport Numarası
- ABD Banka Hesap Numarası
- ABD Sürücü Lisans Numarası
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)
- ABD Sosyal Güvenlik Numarası (SSN)

Özel hassas bilgi türlerinin, yukarıdaki hazır ve hassas bilgi türlerinin yanı sıra DLP ilkesi ipuçları için de destek olduğunu unutmayın.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Uç nokta cihazlerinde Veri Kaybı Önleme yalnızca bazı hassas bilgi türleri için ilke ipuçlarını destekler

Uç nokta cihazlarında tespit edilen, ilk kutusunda olmayan hassas bilgi türleri listesi aşağıdaki gibidir:

- ABA Yönlendirme Numarası 
- Arjantin Ulusal Kimliği (DNI) Numarası 
- Australia Bank Hesap Numarası 
- Avustralya Tıbbi Hesap Numarası 
- Avustralya Pasaport Numarası 
- Avustralya Vergi Dosyası Numarası 
- Avustralya İş Numarası 
- AvustralyaLı Şirket Numarası 
- Avusturya Sürücü Lisans Numarası 
- Avusturya Kimlik Kartı 
- Avusturya Pasaport Numarası 
- Avusturya Sosyal Güvenlik Numarası 
- Avusturya Vergi Kimlik Numarası 
- Avusturya Katma Değer Vergisi (KDV) Numarası 
- Azure DocumentDB Kimlik Doğrulaması Anahtarı 
- Azure IAAS Veritabanı Bağlantı Dizesi ve Azure SQL Bağlantı Dizesi 
- Azure IoT Bağlantı Dizesi 
- Azure Yayımlama Ayarları Parolası 
- Azure Önbellek Bağlantı Dizesini Yeniden Dağıt 
- Azure SAS 
- Azure Service Bus Bağlantı Dizesi 
- Azure Depolama Hesap Anahtarı 
- Azure Depolama Hesap Anahtarı (Generic) 
- Belçika Sürücü Lisans Numarası 
- Belçika Ulusal Numarası 
- Belçika Pasaport Numarası 
- Belçika Değeri Eklenen Vergi Numarası 
- Brezilya CPF Numarası 
- Brezilya Yasal Varlık Numarası (CNPJ) 
- Brezilya Ulusal Kimlik Kartı (RG) 
- Bulgaristan Sürücü Lisans Numarası 
- Bulgaristan Pasaport Numarası 
- Bulgaristan Muntaz 
- Kanada Banka Hesap Numarası 
- Kanada Sürücü Lisans Numarası 
- Kanada Sistem Sağlığı Hizmeti Numarası 
- Kanada Pasaport Numarası 
- Kanada Kişisel Sağlık Kimlik Numarası (PHIN) 
- Kanada Sosyal Sigorta Numarası 
- Şili Kimlik Kartı Numarası 
- Çin Yerleşik Kimlik Kartı (ÇK) Numarası 
- Kredi Kartı Numarası 
- Hırvatistan Sürücüsü Lisans Numarası 
- Hırvatistan Kimlik Kartı Numarası 
- Hırvatistan Ulusal Kimlik Kartı Numarası 
- Hırvatistan Pasaport Numarası 
- Hırvatistan Kişisel Kimlik (OIB) Numarası 
- CSCAN-AZURE0060 Azure Depolama Hesabı Paylaşılan Erişim İmzası 
- CSCAN-GENERAL0140 Genel Simetrik Anahtar 
- Kıbrıs Sürücüsü Lisans Numarası 
- Kıbrıs Kimlik Kartı 
- Kıbrıs Pasaport Numarası 
- Kıbrıs Vergi Kimlik Numarası 
- Çek Sürücüsü Lisans Numarası 
- Çek Kişisel Kimlik Numarası 
- Çek Cumhuriyeti Pasaport Numarası 
- Danimarka Sürücüsü Lisans Numarası 
- Danimarka Pasaport Numarası 
- Danimarka Kişisel Kimlik Numarası 
- Enforcement Agency (DEA) Numarası 
- Estonya Sürücü Lisans Numarası 
- Estonya Pasaport Numarası 
- Estonya Kişisel Kimlik Kodu 
- AB Banka Kartı Numarası 
- EU Sürücü Lisans Numarası 
- AB Ulusal Kimlik Numarası 
- AB Pasaport Numarası 
- AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik 
- AB Vergi Tanımlama Numarası (TIN) 
- Finlandiya Sürücüsü Lisans Numarası 
- Finlandiya Avrupa Sağlık Sigorta Numarası 
- Finlandiya Ulusal Kimliği 
- Finlandiya Pasaport Numarası 
- Fransa Sürücü Lisans Numarası 
- Fransa Sağlık Sigorta Numarası 
- Fransa Ulusal Kimlik Kartı (CNI) 
- Fransa Pasaport Numarası 
- France Social Security Number (INSEE) 
- Fransa Vergi Tanımlama Numarası (numéro SPI.) 
- Fransa Değeri Eklenen Vergi Numarası 
- Almanca Sürücü Lisans Numarası 
- Almanca Pasaport Numarası 
- Almanya Kimlik Kartı Numarası 
- Almanya Vergi Kimlik Numarası 
- Almanya'nın Katma Değer Vergi Numarası 
- Yunanistan Sürücü Lisans Numarası 
- Yunanistan Ulusal Kimlik Kartı 
- Yunanistan Pasaport Numarası 
- Yunanistan Sosyal Güvenlik Numarası (AMKA) 
- Yunan Vergi Kimlik Numarası 
- Hong Kong Kimlik Kartı (HKID) Numarası 
- Macarca Sosyal Güvenlik Numarası (TAJ) 
- Macarca Katma Değer Vergi Numarası 
- Macaristan Sürücü Lisans Numarası 
- Macaristan Pasaport Numarası 
- Macaristan Kişisel Kimlik Numarası 
- Macaristan Vergi Tanımlama Numarası 
- Hindistan Kalıcı Hesap Numarası (PAN) 
- Hindistan Benzersiz Tanımlama (Aadhaar) Numarası 
- Endonezya Kimlik Kartı (KTP) Numarası 
- Uluslararası Bankacılık Hesap Numarası (IBAN) 
- Uluslararası Hastalık Sınıflandırması (ICD-10-CM) 
- Uluslararası Hastalık Sınıflandırması (ICD-9-CM) 
- IP Adresi 
- İrlanda Sürücü Lisans Numarası 
- İrlanda Pasaport Numarası 
- Ireland Personal Public Service (PPS) Numarası 
- İsrail Banka Hesap Numarası 
- İsrail Ulusal Kimliği 
- İtalya Sürücüsü Lisans Numarası 
- İtalya Mali Kodu 
- İtalya Pasaport Numarası 
- İtalya Değeri Eklenen Vergi Numarası 
- Japonya Banka Hesap Numarası 
- Japonya Sürücüsü Lisans Numarası 
- Japonya Pasaport Numarası 
- Japonya'daki Yerleşik Kayıt Numarası 
- Japonya Sosyal Sigorta Numarası (SN) 
- Şirket için Japonca Numaram 
- Japonca Kişisel Numaram 
- Japonca İkamet Kartı Numarası 
- Letonya Sürücüsü Lisans Numarası 
- Letonya Pasaport Numarası 
- Letonya Kişisel Kodu 
- Litvanya Sürücü Lisans Numarası 
- Litvanya Pasaport Numarası 
- Litvanya Kişisel Kodu 
- Luxemburg Sürücü Lisans Numarası 
- Luxemburg Ulusal Kimlik Numarası (Doğal kişiler) 
- Luxemburg Ulusal Kimlik Numarası (Doğal olmayan kişiler) 
- Luxemburg Passport Numarası 
- Malezya Kimlik Kartı Numarası 
- Malta Sürücü Lisans Numarası 
- Malta Kimlik Kartı Numarası 
- Malta Pasaport Numarası 
- Malta Vergi No Numarası 
- Hollanda Genel Hizmet Numarası (BSN) 
- Hollanda Sürücü Lisans Numarası 
- Hollanda Pasaport Numarası 
- Hollanda Vergi Kimlik Numarası 
- Hollanda Katma Değer Vergi Numarası 
- Yeni Zelanda banka hesap numarası 
- Yeni Zelanda Sürücü Lisans Numarası 
- Yeni Zelanda Iç Geliri numarası 
- Yeni Zelanda Sağlık Numarası 
- Yeni Zelanda Sosyal Yardım Numarası 
- Norveç Kimlik Numarası 
- Filipinler Birleşik Çok Amaçlı Kimlik Numarası 
- Polonya Sürücü Lisans Numarası 
- Polonya Kimlik Kartı 
- Polonya Ulusal Kimliği (PESEL) 
- Polonya Pasaport 
- Polonya Vergi Kimlik Numarası 
- Lehçe REGON Numarası 
- Portekiz Portekiz Kart Numarası 
- Portekiz Sürücü Lisans Numarası 
- Portekiz Pasaport Numarası 
- Portekiz Vergi Tanımlama Numarası 
- Romanya Sürücü Lisans Numarası 
- Romanya Pasaport Numarası 
- Romanya Kişisel Sayısal Kodu (CNP) 
- Rusça Pasaport Numarası (Yurtiçi) 
- Rusça Pasaport Numarası (Uluslararası) 
- Suudi Arabistan Ulusal Kimliği 
- Singapur Ulusal Kayıt Kimlik Kartı (NRIC) Numarası 
- Slovakya Sürücüsü Lisans Numarası 
- Slovakya Pasaport Numarası 
- Slovakya Kişisel Numarası 
- Slovenya Sürücüsü Lisans Numarası 
- Slovenya Pasaport Numarası 
- Slovenya Vergi Kimlik Numarası 
- Slovenya benzersiz ana numarayı 
- Güney Afrika Kimlik Numarası 
- Güney Kore Yerleşik Kayıt Numarası 
- İspanya DNI 
- İspanya Sürücüsü Lisans Numarası 
- İspanya Pasaport Numarası 
- İspanya Sosyal Güvenlik Numarası (SSN) 
- İspanya Vergi Kimlik Numarası 
- SQL Server Bağlantı Dizesi 
- İsveç Sürücü Lisans Numarası 
- İsveç Ulusal Kimliği 
- İsveç Pasaport Numarası 
- İsveç Vergi Kimlik Numarası 
- SWIFT Kodu 
- Swiss Social Security Number AHV 
- Tayvan Ulusal Kimliği 
- Tayvan Pasaport Numarası 
- Tayvan Yerleşik Sertifikası (ARC/TARC) 
- Tay Dili Nüfus Kimlik Kodu 
- Türkçe Ulusal Kimlik Numarası 
- B.K. Sürücü Lisans Numarası 
- B.K. SeçmeLi Rulo Numarası 
- B.K. Ulusal Sistem Sağlığı Hizmeti Numarası 
- B.K. Ulusal Sigorta Numarası (NINO) 
- B.K. Benzersiz Vergi Mükellefi Başvuru Numarası 
- ABD / U.K. Pasaport Numarası 
- ABD Banka Hesap Numarası 
- ABD Sürücü Lisans Numarası 
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) 
- ABD Sosyal Güvenlik Numarası (SSN) 
- Ukrayna Pasaport Numarası (Yurtiçi) 
- Ukrayna Pasaport Numarası (Uluslararası) 
 
Lütfen unutmayın; yukarıdaki ilk ve son derece hassas bilgi türlerine ek olarak özel hassas bilgi türleri de algılanır

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Microsoft uygulamaları genelinde DLP ilkesi ipuçları için Destek Matrisi

|**Uygulama ve platform**|**DLP ilkesi ipucu desteği**|**Desteklenen hassas bilgi türleri**|**Desteklenen eylemler ve yüklenmler**|**Açıklamalar**|
|:--|:--|:--|:--|:--|
|**Outlook Web'de**|:::image type="icon" source="../media/rightmrk.png" border="false":::|hepsi|alt küme||
|**Outlook Win32 (ver. 2105 derleme 14026.20000 ve yarı yıllık kanal ver. 2102 derleme 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alt küme|alt küme|Hassas bilgi türleri ve DLP koşulları desteği için ayrıntılar için bkz. [Outlook 2013](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) ve sonraki bilgisayarlar, yalnızca bazı koşullar ve özel durumlar ile [Outlook 2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) ve sonraki sonrası için ilke ipuçlarını göstermeyi destekler ve Masaüstü'de Outlook uygulamaları ile Office desteği, hassas bilgi türleri ve DLP koşulları desteğiyle ilgili ayrıntılar için, Outlook  Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|Mobil cihazlarda DLP ilkesi ipuçları Outlook desteklenmiyor|
|**SharePoint Online/OneDrive İş Web istemcisi**|:::image type="icon" source="../media/rightmrk.png" border="false":::|hepsi|DLP'de tüm SPO/ODB yüklemleri ve eylemleri||
|**SharePoint Win32/ OneDrive İş Win32 istemcisi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|Masaüstü istemci uygulamalarının herhangi bir SharePoint veya OneDrive DLP ilkesi ipuçları desteklenmiyor|
|**Word, Excel, PowerPoint Web Client**|:::image type="icon" source="../media/rightmrk.png" border="false":::|hepsi|DLP'de tüm SPO/ODB yüklemleri ve eylemleri|DLP ilkesi ipucu, belge SPO veya ODB web uygulamasında barındırıldısa ve DLP ilkesi zaten damgalı ise destekler.|
|**Word, Excel, PowerPoint Mobile Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|DLP ilkesi ipuçları, bu ipuçları için mobil Office.|
|**Teams Web/ Teams Desktop/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|hepsi|DLP Teams tüm tüm yüklemler|İlke ipuçları, bir ileti "Bu ileti bayrakla işaretlenmiş. Ne yapabilirim?" Kullanıcı bağlantıya tıklandığında, algılanan hassas bilgi türlerini gözden geçirerek geçersiz kılamaz veya yöneticinin izin verilirse sorun bildirebilirsiniz. Dosyalar için ilke ipucu gösterilmez. Alıcı belgeye erişmeyi çalıştığında, izin verilmiyorsa erişim reddedilmiş olabilir.|
|**Win32 Uç Nokta Cihazları**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alt küme|DLP ilkesinde tüm Uç Nokta DLP yüklemleri ve eylemleri|Bkz [. Uç Noktada Veri Kaybı Önleme yalnızca bazı hassas bilgi türleri için ilke ipuçlarını destekler](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**macOS cihazlar (önizleme)**|yalnızca varsayılan ipuçları|hepsi|alt küme|Veri kaybı önleme ilkeleri macOS cihazlarda zorunlu kılınabilir. Özel ilke ipuçları desteklenmiyor.|
|**Üçüncü taraf bulut uygulamaları**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|Üçüncü taraf bulut uygulamaları, Veri Kaybı Önleme ilke ipuçlarını desteklemez|
|**On-prem**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok||
|**Word, Excel, PowerPoint Win32 İstemcisi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|alt küme|alt küme|Lütfen masaüstü [Outlook 2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) ve sonraki Office uygulamalarına ve desteklenen hassas bilgi türlerinin listesi için yalnızca bazı hassas bilgi türlerine ilişkin ilke ipuçlarını gösteren Masaüstü desteği uygulamalarına bakın</br></br>WXP istemci uygulamaları için ilke ipuçları, tam olarak aşağıdaki veya DLP ilkesinde koşulların veya eylemlerin bir alt kümesi bulunan tüm DLP ilkeleri için SharePoint Online veya OneDrive İş Sitelerinde depolanan belgelerde çalışır:</br> <ul><li>İçerik hassas bilgi türleri içeriyor</li><li>Erişim Kapsamı (İçerik şirket içinde/dışında paylaşılır)</li><li>Kullanıcıya Bildirim (ilke ipuçları/kullanıcı bildirimleri)</li><li>Herkesi engelle</li><li>Olay raporları</li></ul></br> Başka herhangi bir koşul veya eylem varsa, bu ilkeye yönelik DLP ilkesi ipucu Word, Masaüstü veya Masaüstü Excel PowerPoint.</br>Diğer [ayrıntılar için bkz. Excel, PowerPoint ve Word'de](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word) ilke ipuçları|
||||||
