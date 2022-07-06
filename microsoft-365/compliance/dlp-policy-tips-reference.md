---
title: Veri Kaybı Önleme ilkesi ipuçları referansı
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
description: Veri kaybı önleme (DLP) ilkesine bir ilke ipucu eklemeyi öğrenin ve kullanıcıya DLP ilkesiyle çakişen içerikle çalıştığını bildirin.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 04743bdabba4089a7cfdbb46fbb25d427927f6c0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638355"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Veri Kaybı Önleme ilkesi ipuçları referansı

Outlook Web Access'teki DLP ilkesi ipuçları, aşağıdakiler dışında bir DLP ilkesindeki Exchange iş yükünde geçerli olan tüm koşullar, özel durumlar ve eylemler için desteklenir:

**Koşul -ları:**

- Alıcı,
- Üst bilgi sözcükler veya tümcecikler içeriyor
- Üst bilgi desenleri eşleştirir
- İleti türü:
- İçerik karakter kümesi sözcükler içeriyor
- Gönderen ilke ipucunu geçersiz kıldı mı?
- İleti boyutu eşittir veya büyüktür
- Sender AD özniteliği sözcükler veya tümcecikler içeriyor
- Gönderen AD özniteliği desenleri eşleştirir
- Gönderen IP aralıkları
- Alıcı AD özniteliği sözcükler veya tümcecikler içeriyor
- Alıcı AD özniteliği desenleri eşleştirir
- Belge adı sözcükler veya tümcecikler içeriyor
- Belge adı desenler ile eşleşir
- Belge içeriği sözcükler veya tümcecikler içeriyor
- Belge içeriği desenler ile eşleşir

**Eylem:**

- Onay için iletiyi gönderenin yöneticisine iletme
- Onay için iletiyi belirli onaylayanlara iletme
- İletiyi belirli kullanıcılara yeniden yönlendirme
- Alıcıları To Box'a ekleme
- Bilgi Kutusu'na alıcı ekleme
- Gizli Kutu'ya alıcı ekleme
- Gönderenin yöneticisini alıcı olarak ekleme
- HTML bildirimi ekleme
- Önceden ekli e-posta konusu
- O365 İleti Şifrelemesi ve hak korumasını kaldırma

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 ve üzeri yalnızca bazı koşullar ve özel durumlar için ilke ipuçlarını göstermeyi destekler

Şu anda, Outlook 2013 ve üzeri, aşağıda belirtilen koşullar ve ilgili özel durumlar dışında herhangi bir koşul veya özel durum içermeyen ilkeler için ilke ipuçlarının gösterilmesini destekler:

- İçerik içerir (yalnızca Hassas bilgi türleri için çalışır. Duyarlılık etiketleri desteklenmez)
- İçerik paylaşılıyor

Tüm koşulların, içerikle eşleşecekleri ve içerik üzerinde koruyucu eylemler uygulayacakları Outlook istemci uygulamasında yazılan e-postalar için çalıştığını unutmayın. Ancak, kullanıcılara ilke ipuçlarının gösterilmesi, yukarıda bahsedilenler dışında kullanılan koşullar için desteklenmez.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Outlook 2013 ve üzeri ile Masaüstündeki Office uygulamaları yalnızca bazı hassas bilgi türlerine yönelik ilke ipuçlarını gösteren destek

Masaüstünde Outlook (2013 ve üzeri) ve Masaüstündeki Office uygulamalarında (Word, Excel, PowerPoint) DLP ilkesi ipuçlarını göstermek için algılanacak kullanıma hazır hassas bilgi türlerinin listesi şunlardır:

- ABA Yönlendirme Numarası
- Arjantin Ulusal Kimlik (DNI) Numarası
- Avustralya Banka Hesap Numarası
- Avustralya Tıbbi Hesap Numarası
- Avustralya Pasaport Numarası
- Avustralya Vergi Dosya Numarası
- Azure DocumentDB Kimlik Doğrulama Anahtarı  
- Azure IAAS Veritabanı Bağlantı Dizesi ve Azure SQL Bağlantı Dizesi  
- Azure IoT Bağlantı Dizesi  
- Azure Yayımlama Ayarı Parolası  
- Azure Redis Cache Bağlantı Dizesi  
- Azure SAS  
- bağlantı dizesini Azure Service Bus  
- Azure Depolama Hesabı Anahtarı  
- Azure Depolama Hesabı Anahtarı (Genel)  
- Belçika Ulusal Numarası
- Brezilya CPF Numarası
- Brezilya Tüzel Kişilik Numarası (CNPJ)
- Brezilya Ulusal Kimlik Kartı (RG)
- Kanada Banka Hesap Numarası
- Kanada Ehliyet Numarası
- Kanada Sağlık Hizmeti Numarası
- Kanada Pasaport Numarası
- Kanada Kişisel Sağlık Kimlik Numarası (PHIN)
- Kanada Sosyal Sigorta Numarası
- Şili Kimlik Kartı Numarası
- Çin Yerleşik Kimlik Kartı (PRC) Numarası
- Kredi Kartı Numarası
- Hırvatistan Kimlik Kartı Numarası  
- Hırvatistan Kişisel Kimlik (OIB) Numarası  
- Çek Kişisel Kimlik Numarası  
- Danimarka Kişisel Kimlik Numarası
- Uyuşturucu Uygulama Dairesi (DEA) Numarası
- AB Banka Kartı Numarası
- AB Ehliyet Numarası  
- AB Ulusal Kimlik Numarası  
- AB Pasaport Numarası  
- AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik  
- AB Vergi Kimlik Numarası (TIN)  
- Finlandiya Ulusal Kimliği
- Finlandiya Pasaport Numarası
- Fransa Ehliyet Numarası
- Fransa Ulusal Kimlik Kartı (CNI)
- Fransa Pasaport Numarası
- Fransa Sosyal Güvenlik Numarası (INSEE)
- Alman Sürücü Belgesi Numarası
- Alman Pasaport Numarası
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
- İrlanda Kişisel Kamu Hizmeti (PPS) Numarası 
- İsrail Banka Hesap Numarası
- İsrail Ulusal Kimliği
- İtalya Ehliyet Numarası
- Japonya Banka Hesap Numarası
- Japonya Sürücü Belgesi Numarası
- Japonya Pasaport Numarası
- Japonya Yerleşik Kayıt Numarası
- Japonya Sosyal Sigorta Numarası (SIN)
- Japon İkamet Kartı Numarası
- Malezya Kimlik Kartı Numarası
- Hollanda VatandaşLık Hizmeti (BSN) Numarası  
- Yeni Zelanda Sağlık Bakanlığı Numarası
- Norveç Kimlik Numarası  
- Filipinler Birleşik Çok Amaçlı Kimlik Numarası
- Polonya Kimlik Kartı
- Polonya Ulusal Kimliği (PESEL)
- Polonya Pasaportu
- Portekiz Vatandaş Kart Numarası
- Suudi Arabistan Ulusal Kimliği
- Singapur Ulusal Kayıt Kimlik Kartı (NRIC) Numarası
- Güney Afrika Kimlik Numarası  
- Güney Kore Yerleşik Kayıt Numarası
- İspanya Sosyal Güvenlik Numarası (SSN)
- bağlantı dizesini SQL Server  
- İsveç Ulusal Kimliği
- İsveç Pasaport Numarası
- SWIFT Kodu
- Tayvan Ulusal Kimliği
- Tayvan Pasaport Numarası
- Tayvan Yerleşik Sertifikası (ARC/TARC)
- Tay Nüfus Tanımlama Kodu
- Türkiye Ulusal Kimlik numarası
- INGİLTERE. Ehliyet Numarası
- INGİLTERE. Seçim Rulosu Numarası
- INGİLTERE. Ulusal Sağlık Hizmeti Numarası
- INGİLTERE. Ulusal Sigorta Numarası (NINO)
- Birleşik Krallık / Birleşik Krallık Pasaport Numarası
- ABD Banka Hesap Numarası
- ABD Ehliyet Numarası
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)
- ABD Sosyal Güvenlik Numarası (SSN)

Özel hassas bilgi türlerinin, yukarıdaki kullanıma hazır hassas bilgi türlerine ek olarak DLP ilkesi ipuçları için de desteklendiğini lütfen unutmayın.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Uç nokta cihazlarında Veri Kaybı Önleme yalnızca bazı hassas bilgi türleri için ilke ipuçlarını destekler

Uç nokta cihazlarında bulunan belgelerde algılanacak kullanıma açık hassas bilgi türlerinin listesi şunlardır:

- ABA Yönlendirme Numarası 
- Arjantin Ulusal Kimlik (DNI) Numarası 
- Avustralya Banka Hesap Numarası 
- Avustralya Tıbbi Hesap Numarası 
- Avustralya Pasaport Numarası 
- Avustralya Vergi Dosya Numarası 
- Avustralya İş Numarası 
- Avustralya Şirket Numarası 
- Avusturya Ehliyet Numarası 
- Avusturya Kimlik Kartı 
- Avusturya Pasaport Numarası 
- Avusturya Sosyal Güvenlik Numarası 
- Avusturya Vergi Kimlik Numarası 
- Avusturya Katma Değer Vergisi (KDV) Numarası 
- Azure DocumentDB Kimlik Doğrulama Anahtarı 
- Azure IAAS Veritabanı Bağlantı Dizesi ve Azure SQL Bağlantı Dizesi 
- Azure IoT Bağlantı Dizesi 
- Azure Yayımlama Ayarı Parolası 
- Azure Redis Cache Bağlantı Dizesi 
- Azure SAS 
- bağlantı dizesini Azure Service Bus 
- Azure Depolama Hesabı Anahtarı 
- Azure Depolama Hesabı Anahtarı (Genel) 
- Belçika Ehliyet Numarası 
- Belçika Ulusal Numarası 
- Belçika Pasaport Numarası 
- Belçika Katma Değer Vergisi Numarası 
- Brezilya CPF Numarası 
- Brezilya Tüzel Kişilik Numarası (CNPJ) 
- Brezilya Ulusal Kimlik Kartı (RG) 
- Bulgaristan Ehliyet Numarası 
- Bulgaristan Pasaport Numarası 
- Bulgaristan Tekdüzen Sivil Numarası 
- Kanada Banka Hesap Numarası 
- Kanada Ehliyet Numarası 
- Kanada Sağlık Hizmeti Numarası 
- Kanada Pasaport Numarası 
- Kanada Kişisel Sağlık Kimlik Numarası (PHIN) 
- Kanada Sosyal Sigorta Numarası 
- Şili Kimlik Kartı Numarası 
- Çin Yerleşik Kimlik Kartı (PRC) Numarası 
- Kredi Kartı Numarası 
- Hırvatistan Ehliyet Numarası 
- Hırvatistan Kimlik Kartı Numarası 
- Hırvatistan Ulusal Kimlik Kartı Numarası 
- Hırvatistan Pasaport Numarası 
- Hırvatistan Kişisel Kimlik (OIB) Numarası 
- CSCAN-AZURE0060 Azure Depolama Hesabı Paylaşılan Erişim İmzası 
- CSCAN-GENERAL0140 Genel Simetrik Anahtar 
- Kıbrıs Ehliyet Numarası 
- Kıbrıs Kimlik Kartı 
- Kıbrıs Pasaport Numarası 
- Kıbrıs Vergi Kimlik Numarası 
- Çek Ehliyet Numarası 
- Çek Kişisel Kimlik Numarası 
- Çek Cumhuriyeti Pasaport Numarası 
- Danimarka Ehliyet Numarası 
- Danimarka Pasaport Numarası 
- Danimarka Kişisel Kimlik Numarası 
- Uyuşturucu Uygulama Dairesi (DEA) Numarası 
- Estonya Sürücü Lisans Numarası 
- Estonya Pasaport Numarası 
- Estonya Kişisel Kimlik Kodu 
- AB Banka Kartı Numarası 
- AB Ehliyet Numarası 
- AB Ulusal Kimlik Numarası 
- AB Pasaport Numarası 
- AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik 
- AB Vergi Kimlik Numarası (TIN) 
- Finlandiya Ehliyet Numarası 
- Finlandiya Avrupa Sağlık Sigortası Numarası 
- Finlandiya Ulusal Kimliği 
- Finlandiya Pasaport Numarası 
- Fransa Ehliyet Numarası 
- Fransa Sağlık Sigortası Numarası 
- Fransa Ulusal Kimlik Kartı (CNI) 
- Fransa Pasaport Numarası 
- Fransa Sosyal Güvenlik Numarası (INSEE) 
- Fransa Vergi Kimlik Numarası (numéro SPI.) 
- Fransa Katma Değer Vergi Numarası 
- Alman Sürücü Belgesi Numarası 
- Alman Pasaport Numarası 
- Almanya Kimlik Kartı Numarası 
- Almanya Vergi Kimlik Numarası 
- Almanya Katma Değer Vergi Numarası 
- Yunanistan Ehliyet Numarası 
- Yunanistan Ulusal Kimlik Kartı 
- Yunanistan Pasaport Numarası 
- Yunanistan Sosyal Güvenlik Numarası (AMKA) 
- Yunan Vergi Kimlik Numarası 
- Hong Kong Kimlik Kartı (HKID) Numarası 
- Macar Sosyal Güvenlik Numarası (TAJ) 
- MacarCa Katma Değer Vergi Numarası 
- Macaristan Ehliyet Numarası 
- Macaristan Pasaport Numarası 
- Macaristan Kişisel Kimlik Numarası 
- Macaristan Vergi Kimlik Numarası 
- Hindistan Kalıcı Hesap Numarası (PAN) 
- Hindistan Benzersiz Tanımlama (Aadhaar) Numarası 
- Endonezya Kimlik Kartı (KTP) Numarası 
- Uluslararası Bankacılık Hesap Numarası (IBAN) 
- Uluslararası Hastalık Sınıflandırması (ICD-10-CM) 
- Uluslararası Hastalık Sınıflandırması (ICD-9-CM) 
- IP Adresi 
- İrlanda Ehliyet Numarası 
- İrlanda Pasaport Numarası 
- İrlanda Kişisel Kamu Hizmeti (PPS) Numarası 
- İsrail Banka Hesap Numarası 
- İsrail Ulusal Kimliği 
- İtalya Ehliyet Numarası 
- İtalya Mali Kodu 
- İtalya Pasaport Numarası 
- İtalya Katma Değer Vergi Numarası 
- Japonya Banka Hesap Numarası 
- Japonya Sürücü Belgesi Numarası 
- Japonya Pasaport Numarası 
- Japonya Yerleşik Kayıt Numarası 
- Japonya Sosyal Sigorta Numarası (SIN) 
- Japonca My Number Corporate 
- Japonca Numaram Kişisel 
- Japon İkamet Kartı Numarası 
- Letonya Ehliyet Numarası 
- Letonya Pasaport Numarası 
- Letonya Kişisel Kodu 
- Litvanya Sürücü Belgesi Numarası 
- Litvanya Pasaport Numarası 
- Litvanya Kişisel Kodu 
- Luxemburg Ehliyet Numarası 
- Luxemburg Ulusal Kimlik Numarası (Gerçek kişiler) 
- Luxemburg Ulusal Kimlik Numarası (Gerçek olmayan kişiler) 
- Luxemburg Pasaport Numarası 
- Malezya Kimlik Kartı Numarası 
- Malta Sürücü Belgesi Numarası 
- Malta Kimlik Kartı Numarası 
- Malta Pasaport Numarası 
- Malta Vergi Kimlik Numarası 
- Hollanda VatandaşLık Hizmeti (BSN) Numarası 
- Hollanda Ehliyet Numarası 
- Hollanda Pasaport Numarası 
- Hollanda Vergi Kimlik Numarası 
- Hollanda Katma Değer Vergisi Numarası 
- Yeni Zelanda banka hesap numarası 
- Yeni Zelanda Sürücü Lisans Numarası 
- Yeni Zelanda İç Gelir numarası 
- Yeni Zelanda Sağlık Bakanlığı Numarası 
- Yeni Zelanda Sosyal Yardım Numarası 
- Norveç Kimlik Numarası 
- Filipinler Birleşik Çok Amaçlı Kimlik Numarası 
- Polonya Sürücü Belgesi Numarası 
- Polonya Kimlik Kartı 
- Polonya Ulusal Kimliği (PESEL) 
- Polonya Pasaportu 
- Polonya Vergi Kimlik Numarası 
- Lehçe REGON Numarası 
- Portekiz Vatandaş Kart Numarası 
- Portekiz Sürücü Ehliyeti Numarası 
- Portekiz Pasaport Numarası 
- Portekiz Vergi Kimlik Numarası 
- Romanya Ehliyet Numarası 
- Romanya Pasaport Numarası 
- Romanya Kişisel Sayısal Kodu (CNP) 
- Rus Pasaport Numarası (Yurt İçi) 
- Rus Pasaport Numarası (Uluslararası) 
- Suudi Arabistan Ulusal Kimliği 
- Singapur Ulusal Kayıt Kimlik Kartı (NRIC) Numarası 
- Slovakya Sürücü Ehliyeti Numarası 
- Slovakya Pasaport Numarası 
- Slovakya Kişisel Numarası 
- Slovenya Ehliyet Numarası 
- Slovenya Pasaport Numarası 
- Slovenya Vergi Kimlik Numarası 
- Slovenya Benzersiz Ana Vatandaş Numarası 
- Güney Afrika Kimlik Numarası 
- Güney Kore Yerleşik Kayıt Numarası 
- İspanya DNI 
- İspanya Ehliyet Numarası 
- İspanya Pasaport Numarası 
- İspanya Sosyal Güvenlik Numarası (SSN) 
- İspanya Vergi Kimlik Numarası 
- bağlantı dizesini SQL Server 
- İsveç Ehliyet Numarası 
- İsveç Ulusal Kimliği 
- İsveç Pasaport Numarası 
- İsveç Vergi Kimlik Numarası 
- SWIFT Kodu 
- İsviçre Sosyal Güvenlik Numarası AHV 
- Tayvan Ulusal Kimliği 
- Tayvan Pasaport Numarası 
- Tayvan Yerleşik Sertifikası (ARC/TARC) 
- Tay Nüfus Tanımlama Kodu 
- Türkiye Ulusal Kimlik numarası 
- INGİLTERE. Ehliyet Numarası 
- INGİLTERE. Seçim Rulosu Numarası 
- INGİLTERE. Ulusal Sağlık Hizmeti Numarası 
- INGİLTERE. Ulusal Sigorta Numarası (NINO) 
- INGİLTERE. Benzersiz Vergi Mükellefi Başvuru Numarası 
- Birleşik Krallık / Birleşik Krallık Pasaport Numarası 
- ABD Banka Hesap Numarası 
- ABD Ehliyet Numarası 
- ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) 
- ABD Sosyal Güvenlik Numarası (SSN) 
- Ukrayna Pasaport Numarası (Yurt İçi) 
- Ukrayna Pasaport Numarası (Uluslararası) 
 
Yukarıdaki kullanıma açık hassas bilgi türlerine ek olarak özel hassas bilgi türlerinin de algılandığını lütfen unutmayın

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Microsoft uygulamaları genelinde DLP ilkesi ipuçları için Destek Matrisi

|**Uygulama ve platform**|**DLP ilkesi ipucu desteği**|**Desteklenen hassas bilgi türleri**|**Koşul ve eylemler desteklenir**|**Açıklamalar**|
|:--|:--|:--|:--|:--|
|**Web Üzerinde Outlook**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tüm|Alt küme -sini||
|**Outlook Win32 (2105 derleme 14026.20000 ve altı aylık kanal ver. 2102 derleme 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alt küme -sini|Alt küme -sini|Bkz [. Outlook 2013 ve üzeri, yalnızca bazı koşullar ve özel durumlar için ilke ipuçlarının gösterilmesini](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) destekler ve [Outlook 2013 ve üzeri ile Masaüstünde Office uygulamaları](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) , outlook Win32'de DLP ilke ipuçlarını göstermek için desteklenen DLP koşulları ve eylemleri ve hassas bilgi türleri desteğiyle ilgili ayrıntılar için yalnızca bazı hassas bilgi türlerine yönelik ilke ipuçlarını gösterir.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|DLP ilkesi ipuçları Outlook Mobile'da desteklenmiyor|
|**SharePoint Online/OneDrive İş Web istemcisi**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tüm|DLP'deki tüm SPO/ODB önkoşulları ve eylemleri||
|**SharePoint Win32/ OneDrive İş Win32 istemcisi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|DLP ilkesi ipuçları SharePoint veya OneDrive masaüstü istemci uygulamalarında desteklenmez|
|**Word, Excel, PowerPoint Web İstemcisi**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tüm|DLP'deki tüm SPO/ODB önkoşulları ve eylemleri|Belge SPO veya ODB web uygulamasında barındırılıyorsa ve DLP ilkesi zaten damgalanmışsa DLP ilkesi ipucu desteklenir.|
|**Word, Excel, PowerPoint Mobile İstemcisi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|DLP ilkesi ipuçları Office için mobil uygulamalarda desteklenmez.|
|**Teams Web/ Teams Masaüstü/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tüm|DLP ilkesindeki tüm Teams önkoşulları|İlke ipuçları, bir ileti "Bu ileti bayrakla işaretlendi. Ne yapabilirim?" Bağlantıya tıklandığında, kullanıcı algılanan hassas bilgi türlerini gözden geçirebilir ve yönetici tarafından izin veriliyorsa bir sorunu geçersiz kılabilir veya bildirebilir. Dosyalar için hiçbir ilke ipucu gösterilmediğini unutmayın. Alıcı belgeye erişmeye çalıştığında, izin verilmiyorsa erişim reddedilir.|
|**Win32 Uç Nokta Cihazları**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alt küme -sini|DLP ilkesindeki tüm Uç Nokta DLP önkoşulları ve eylemleri|Bkz. [Uç Noktada Veri Kaybı Önleme yalnızca bazı hassas bilgi türleri için ilke ipuçlarını destekler](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**macOS cihazları**|yalnızca varsayılan ipuçları|Tüm|Alt küme -sini|Veri kaybı önleme ilkeleri macOS cihazlarda uygulanabilir. Özel ilke ipuçları desteklenmez.|
|**Üçüncü taraf bulut uygulamaları**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok|Veri Kaybı Önleme ilkesi ipuçları üçüncü taraf bulut uygulamalarında desteklenmez|
|**Şirket içi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|yok|yok||
|**Word, Excel, PowerPoint Win32 İstemcisi**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Alt küme -sini|Alt küme -sini|Desteklenen [hassas bilgi türleri listesi için yalnızca bazı hassas bilgi türlerine yönelik ilke ipuçlarını gösteren Outlook 2013 ve sonraki sürümlerine ve Masaüstü'nde Office uygulamalarına](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) bakın</br></br>WXP istemci uygulamalarına yönelik ilke ipuçları, DLP ilkesindeki koşulların veya eylemlerin tam olarak aşağıda veya bir alt kümesine sahip olan tüm DLP ilkeleri için SharePoint Online'da veya OneDrive İş Sitelerinde depolanan belgeler için çalışır:</br> <ul><li>İçerik hassas bilgi türleri içeriyor</li><li>Erişim Kapsamı (İçerik dahili/harici olarak paylaşılır)</li><li>Kullanıcıya Bildir (ilke ipuçları/kullanıcı bildirimleri)</li><li>Herkesi engelle</li><li>Olay raporları</li></ul></br> Başka bir koşul veya eylem varsa, söz konusu ilkenin DLP ilke ipucu Word, Excel veya PowerPoint'in masaüstü uygulamalarında görünmez.</br>Diğer ayrıntılar için bkz. [Excel, PowerPoint ve Word'de ilke ipuçları](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word)|
||||||
