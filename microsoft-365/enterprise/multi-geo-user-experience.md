---
title: Çok coğrafi ortamda kullanıcı deneyimi
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Kullanıcı deneyimi için SharePoint, OneDrive ve Exchange deneyimiyle ilgili bilgi Microsoft 365.
ms.openlocfilehash: 638aa7d65f9243bfd110eebac6473d641e1d0b61
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015176"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Çok coğrafi ortamda kullanıcı deneyimi

Kullanıcılarınız yeni bir yapılandırmada şunları OneDrive Multi-Geo:

## <a name="exchange-mailbox"></a>Exchange kutusu

Kullanıcının posta kutusu Exchange tercih ettiği veri konuma sağlandı ve PDL'leri değişirse otomatik olarak yeniden konumlandı. Kullanıcılar çok Outlook bir Web üzerinde Outlook deneyiminde hiçbir değişiklik yaşamadan veri ve kaynak veri kullanımını normal olarak kullanabilir.

## <a name="hub-sites"></a>Merkez siteleri

SharePoint Merkezi siteleri, çalışanların içerik bulmalarını ve etkileşimlerini güçlendirirken, bir yandan da projelerin, departmanların veya bölgelerin eksiksiz ve tutarlı bir temsilini sağlar. Çok coğrafi bir ortamda, uydu konumlarından siteler, merkez konumu ne olursa olsun bir merkez sitesiyle kolayca ilişkilendirilebilir. Kullanıcılar, sitelerin coğrafi konumu ne olursa olsun, tek bir arama deneyimi aracılığıyla hub'da arama ve sonuçları elde kullanılabilir.

## <a name="microsoft-365-app-launcher"></a>Microsoft 365 başlatıcı

Uygulama başlatıcısı, çok coğrafi farklıdır ve her kutucuğu iş yükünün uygun coğrafi konumunu gösterir. Veri SharePoint OneDrive kutucukları, kullanıcıya kullanıcının sağlanan coğrafi konuma karşılık gelen konuma işaretacaktır. Bu, kullanıcının merkezi konumda bir OneDrive olduğu anlamına gelir; SharePoint kutucuğu onu merkezi konumda SP Giriş'e işaret ediyor ancak grup sitesi PDL'lerine karşılık gelen konumda sağlandı. 

## <a name="office-applications"></a>Office uygulamaları

Office Word, Excel ve PowerPoint gibi uygulamalar, oturum OneDrive her kullanıcı için doğru coğrafi konumu otomatik olarak algılar. Kullanıcıların kendi sitelerinin veya sitelerinin coğrafi URL'sini OneDrive SharePoint gerekir.

## <a name="onedrive-sync-app"></a>OneDrive eşitleme uygulaması

OneDrive eşitleme uygulaması (sürüm 17.3.6943.0625 ve sonraki sürümler), kullanıcı için doğru konumu OneDrive konumu otomatik olarak algılar. Eşitleme uygulaması desteği, coğrafi konumlarına bakılmaksızın grup tabanlı siteleri eşitleme olanağını içerir. Groove eşitleme istemcisi multi-geo için desteklenmiyor. 

## <a name="onedrive-location"></a>OneDrive konumu

Kullanıcılar tercih OneDrive veri konumlarında kendi tercihlerine sahip olur. Kullanıcı yanlış coğrafi konum içeren bir OneDrive URL'sine (örneğin, önceki bir coğrafi konumdaki yer işaretine) gitse, otomatik olarak uygun coğrafi konumdaki OneDrive URL'ye yeniden yönlendirilir.

## <a name="onedrive-ios-and-android"></a>iOS OneDrive Android'i ayarlama 

En OneDrive iOS ve Android mobil uygulamaları, coğrafi konumlarına bakılmaksızın OneDrive dosyaları ve dosyaları size gösterir. Mobil OneDrive arama tüm coğrafi konumlardan ilgili sonuçları gösterir. Bu uygulamaların en son sürümünü indirin.

Daha fazla bilgi için bkz. [iOS OneDrive da E-OneDrive'i](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) [kullanma ve Android için E-OneDrive'i](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) kullanma.

## <a name="onedrive-mobile-client"></a>OneDrive Mobil İstemcisi 

Mobil OneDrive İstemcisi coğrafi olarak farkındadır ve tüm coğrafi konumlardan ilgili içeriği ve sonuçları görüntüler.

## <a name="search"></a>Arama

Her coğrafi konumun kendi arama dizini ve Arama Merkezi vardır. Kullanıcı arama yaptığı zaman, sorgu tüm coğrafi konumlara gönderilir ve döndürülen sonuçlar birleştirilir ve sonra kullanıcı birleşik sonuçlar elde edilecek şekilde sıralandı. Kullanıcılar kendi coğrafi konumlarına bakılmaksızın tüm coğrafi konumlardan sonuçlar elde ediyor. [Özeller için bkz. OneDrive Multi-Geo](configure-search-for-multi-geo.md) arama ayarlarını yapılandırma.

Aşağıdaki arama istemcileri de desteklemektedir:

-   OneDrive

-   Delve

-   SharePoint Giriş

-   Arama Merkezi

-   Arama API'sini kullanan SharePoint arama uygulamaları

## <a name="sharepoint-home"></a>SharePoint Giriş 

SharePoint Multi-Geo'SharePoint, oturum sahibi tarafından belirlenen konuma göre kullanıcının bulunduğu OneDrive barındırıldı. Örneğin: Kullanıcının hesapları Avrupa uydu OneDrive barındırıyorsa, Avrupa'dan SharePoint Konumları işlenecektir. SharePoint ana sayfa coğrafi konumu ne olursa olsun kullanıcıyla ilgili tüm içeriği içerir. 

**Takip Edilen Siteler, Sitelerden Haberler, Son Siteler, Sık Kullanılan Siteler ve Önerilen siteler**

İçeriğin barındırıldı olduğu coğrafi konumdan bağımsız olarak, kullanıcının içerikle ilgili içerikle ilgili izinleri olduğu sürece, bu bileşenlerin hepsi kullanıcıya gösterir. 

**Özellikler Bağlantıları**

Yöneticiler her coğrafi konuma uygun SharePoint Ev sayfasında Öne Çıkan bağlantılar yapılandırabilirsiniz. Bu, yöneticinin her bölge için SP Giriş sayfasında bölgedeki kullanıcılara uygun bağlantıları özelliğini sağlar. 

## <a name="sharepoint-mobile-client"></a>SharePoint Mobil İstemcisi

Mobil SharePoint, çok coğrafi olarak farkındadır ve tüm coğrafi konumlardan ilgili içeriği ve sonuçları görüntüler.

## <a name="sharing"></a>Paylaşım

Kişi Seçici deneyimi, coğrafi konumlarından bağımsız olarak tüm kullanıcıları gösterir. Bu, kullanıcının aynı coğrafi konumdaki başka bir kullanıcıyla veya kiracının coğrafi konumlarının herhangi birsinde paylaşmasına olanak sağlar. Farklı coğrafi konumlardan içerikler Kullanıcının OneDrive, Word,  Excel, PowerPoint ve Office.com'daki Benimle Paylaşılan görünümünde gösterilir ve hangi coğrafi konumda barındırılıyor olursa olsun, Tek Sign-On deneyimiyle erişilebilir.

## <a name="teams-experience"></a>Teams Deneyimi

Teams, çok coğrafi bir hizmettir. OneDrive konum bilgileri ve son görüntülenen dosyalar kullanıcının coğrafi konumu ne olursa olsun gösterilir. @ bahsetmeler, tüm coğrafi konumlardan kullanıcılarla birlikte çalışır.

## <a name="user-profiles"></a>Kullanıcı profilleri

Kullanıcı profili bilgileri, kullanıcının coğrafi konumda ana bilgilerine sahip olur. Bir kullanıcı seçerek, kullanıcı için uygun coğrafi konuma yönlendirildiniz ve burada kullanıcının tüm profil ayrıntılarını göreceğiniz konum.

Bu Delve kapalı ise, çoklu coğrafi olarak fark SharePoint, bu deneyimin klasik profil deneyimiyle devam edin.


