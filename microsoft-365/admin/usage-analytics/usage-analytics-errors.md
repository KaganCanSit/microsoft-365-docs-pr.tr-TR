---
title: Microsoft 365 kullanım analizi sorun giderme
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a73632a1-62c8-4a13-8115-913773b30f93
description: Hızlı Kullanım Analizi şablon uygulamasındaki Microsoft 365 gidermeyi öğrenin.
ms.openlocfilehash: afa9841b38beefcfdd091f27e7b1f328cdf52a5e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019008"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Microsoft 365 kullanım analizi sorun giderme

Microsoft 365 kullanım analizi ilgili en yaygın olarak karşılaşılan sorunlar konusunda yardım almak için aşağıdaki hata iletileri listesini keşfedin.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>İsteğinizi işleyemiyoruz. Önce aşağıdaki veri kaynağından bu verilere abone Microsoft 365 yönetim merkezi

 **Hata Kodu:** 422 
  
 **Bu iletiyi göreceğiniz durum:** Power BI Kullanım Analizi şablon uygulamasına bağlanırken veya Microsoft 365 Raporlama API'lerini doğrudan Microsoft 365 de kullanabilirsiniz. 
  
 **Neden:** Uygulamaya bağlanamadan önce veri kaynağından verilere abone Microsoft 365 yönetim merkezi. Önce bu adım yapılmazsa, kiracı kimliğinizi sağlasanız bile şablon uygulamasına Microsoft 365. 
  
 **Bu hatayı düzeltmek için:** Verilere abone olmak için yönetim merkezi Rapor **Kullanımı sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> \> gidin ve ana pano sayfasında Microsoft 365 kullanım analizi kutucuğunu bulun. Çalışmaya başla **düğmesini seçin** ve açılan Raporlar bölmesinde Verileri  şu şekilde kullanılabilir hale Microsoft 365 **için kullanım Power BI** Kaydet ayarını **açın**.
  
## <a name="we-are-processing-your-data"></a>Verilerinizi işliyoruz

 **Bu iletiyi göreceğiniz durum:** Kaynak **Microsoft 365 Kullanım panosunda** yer alan kullanım **analizi** kutucuğunun Microsoft 365 yönetim merkezi. 
  
 **Neden:** Şablon [uygulamasındaki verileri ilk kullanıcıdan](enable-usage-analytics.md) görmeyi kabul Microsoft 365 yönetim merkezi, Microsoft 365 sisteminiz için geçmiş kullanım verileri oluşturmaya başlar. Kiracınızın boyutuna bağlı olarak bu adım 2 saat ile 48 saat arasında sürebilir. 
  
 **Bunu düzeltmek için:** Sabırlı olun, ancak 3 gün sonra ileti Verileriniz hazır olarak değişmezse [İş desteği için Microsoft 365 ile iletişime geçin](Destek al](.). /get-help-support.md).
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Şu anda isteğinizi işleyemiyoruz. Kuruluşunuz için verilerin hazırlanması sürüyor

 **Hata Kodu:** 423 
  
 **Bu iletiyi göreceğiniz durum:** Power BI'de, Microsoft 365 Usage Analytics şablon uygulamasına bağlanırken veya doğrudan Microsoft 365 API'leri çağırabilirsiniz. 
  
 **Neden:** Yönetim [merkezinden şablon uygulamasındaki](enable-usage-analytics.md) verileri görmeyi kabul ettiyseniz, Microsoft 365 sisteminiz için geçmiş kullanım verileri oluşturmaya başlar. Kiracının boyutuna bağlı olarak, bu adım iki saat ile 48 saat arasında sürebilir. 
  
 **Bunu düzeltmek için:** Sabırlı olun, ancak 3 gün içinde ileti Verileriniz hazır olarak değişmezse işletmeler için destek [Microsoft 365'e başvurun](../../business-video/get-help-support.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Sağladığınız kiracı kimliği doğru biçimde değil

 **Hata Kodu:** 400 
  
 **Bu iletiyi göreceğiniz durum:** Power BI'de, Microsoft 365 Usage Analytics şablon uygulamasına bağlanırken veya doğrudan Microsoft 365 API'leri çağırabilirsiniz. 
  
 **Neden:** Kiracı kimliği bir guid'tir ve xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx biçiminde olmalıdır. Kiracı giriş kutusuna başka bir dize girersiniz, bu hatayı alırsınız. 
  
 **Bu hatayı düzeltmek için:** Yönetim merkezi Rapor **Kullanımı'ne** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">gidin</a> ve ana Microsoft 365 sayfasındaki kullanım analizi kutucuğunu bulun. Kiracı kimliği kutucukta listelenir. Şablonu buradan kopyalayıp şablon uygulamasına bağlanmaya uygun iletişim kutusuna yapıştırabilirsiniz. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Sağladığınız kiracı kimliği sistemimiz tarafından tanınmıyor

 **Hata Kodu:** 404 
  
 **Bu iletiyi göreceğiniz durum:** Power BI Kullanım Analizi şablon uygulamasına bağlanırken veya Microsoft 365 Raporlama API'lerini doğrudan Microsoft 365 de kullanabilirsiniz. 
  
 **Neden:** Sağladığınız kiracı kimliği geçerli değil veya mevcut değil. 
  
 **Bu hatayı düzeltmek için:** Yönetim merkezi Rapor **Kullanımı'ne** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">gidin</a> ve ana Microsoft 365 sayfasındaki kullanım analizi kutucuğunu bulun. Kiracı kimliği kutucukta listelenir. Şablonu buradan kopyalayıp şablon uygulamasına bağlanmaya uygun iletişim kutusuna yapıştırabilirsiniz. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Power BI'da yeniden oturum açmak için lütfen kimlik bilgilerinizi tekrar girin

Hata Kodu: 302
  
 **Bu iletiyi göreceğiniz durum:** Power BI Kullanım Analizi şablon uygulamasına bağlanırken veya Microsoft 365 Raporlama API'lerini doğrudan Microsoft 365 de kullanabilirsiniz. 
  
 **Neden:** Yetkilendirme kodu başarısız oldu ve kimlik bilgilerinizi yeniden girmeniz gerekebilir. 
  
 **Bu hatayı düzeltmek için:** Power BI oturumunu kapatın ve sonra yeniden oturum açın. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>Bu verilere erişmek için doğru yetkilendirmeye sahip değilsiniz. Bu hizmetten verilere erişim elde edebilmeniz için genel yönetici veya ürün yöneticilerinden biri olmanız gerekir

 **Hata Kodu:** 403 
  
 **Bu iletiyi göreceğiniz durum:** Power BI Kullanım Analizi şablon uygulamasına bağlanırken veya Microsoft 365 Raporlama API'lerini doğrudan Microsoft 365 de kullanabilirsiniz. 
  
 **Neden:** Şablon uygulamasına bağlanmaya çalışan kullanıcı bu verilere erişmek için doğru yetkilendirme düzeyine sahip olduğundan, yetkilendirme kodu başarısız oldu. 
  
 **Bu hatayı düzeltmek için:** Şablon uygulamasına bağlanmak için Genel  **yönetici,** **Exchange** yöneticisi, Skype Kurumsal yöneticisi,  **SharePoint,** Genel okuyucu veya Rapor okuyucusu olan bir kullanıcının kimlik bilgilerini girin. Daha [fazla bilgi için bkz.](../add-users/about-admin-roles.md) Yönetici rolleri hakkında. 
  
## <a name="refresh-failed"></a>Yenileme başarısız oldu

 **Bu iletiyi göreceğiniz durum:** Power BI'dan e-posta alındı veya yenileme geçmişinde başarısız durum var. 
  
 **Neden:** Bazen şablon uygulamasına bağlı kullanıcının kimlik bilgileri sıfırlanır ve şablon uygulamasının bağlantı ayarlarında güncelleştirilmez; bu da kullanıcının yenileme hatası hatalarını görmelerine neden olur. 
  
 **Bu hatayı düzeltmek için:** Daha Power BI' de, Microsoft 365 Kullanım Analizi şablonu uygulamasına karşılık gelen veri kümesi bulun, Yenilemeyi zamanla'ı seçin ve yönetici kimlik bilgilerinizi girin. 
  
Bu işe yaramadı mı? Önbelleği temizleyin ve şablon uygulamasını yeniden oluşturun.
  
  
