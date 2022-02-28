---
title: Bağlan Analizi ile Microsoft 365 Government Community Cloud (GCC) verilerine erişim
f1.keywords:
- CSH
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Power BI'te Microsoft 365 Kullanım Analizi şablon uygulamasını kullanarak Microsoft 365 Government Community Cloud (GCC) kiracısı alanınız içinde yer alan verilere nasıl bağlanabilirsiniz Power BI.
ms.openlocfilehash: 3930ffe82c998797aade84e92145adac5fa2ea98
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985331"
---
# <a name="connect-to-microsoft-365-government-community-cloud-gcc-data-with-usage-analytics"></a>Bağlan Analizi ile Microsoft 365 Government Community Cloud (GCC) verilerine erişim

Bir rapor (kiracı) kiracısı içinde Microsoft 365 Kullanım Analizi raporuyla verilerinize bağlanmak Microsoft 365 Government Community Cloud GCC kullanın. 

> [!NOTE]
> Bu yönergeler özellikle kiracılara Microsoft 365 GCC yöneliktir. 

## <a name="before-you-begin"></a>Başlamadan önce

Başlangıçta Kullanım Analizi'Microsoft 365 yapılandırmak için: 

- Veri toplamayı etkinleştirmek Microsoft 365 Genel yönetici olmak gerekir. 
- Şablon dosyasını [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) için bu şablon uygulamasına ihtiyacınız vardır. 
- Raporu yayımlamak [Power BI Pro görüntülemek için](https://go.microsoft.com/fwlink/p/?linkid=845347) Premium lisans veya Premium lisansınız gerekir. 

## <a name="step-1-make-you-organizations-data-available-for-the-microsoft-365-usage-analytics-report"></a>1. Adım: En son Kullanım Analizi raporu için Microsoft 365 verilerini kullanma

1. Gezinti Microsoft 365 yönetim merkezi, Raporlar'ı ve ardından **Kullanım'ı** **seçin**. 
2. Kullanım **Raporları sayfasındaki** Kullanım Analizi Microsoft 365 Raporu'Başlarken **.** 
3. Kullanım **analizi Power BI'nin altında** Kurumsal kullanım verilerini Microsoft kullanım analizi için kullanılabilir hale Power BI ardından Kaydet'i **seçin**.

    ![Kiracı verilerinizi kullanılabilir hale geldi.](../../media/usage-analytics/make-data-available.png) 



    Bu işlem, kuruluş verilerinizin bu rapor için erişilebilir olmasını sağlarken, verilerinizi kullanım çözümlemeleri için kullanıma hazır hale Microsoft 365 **belirten bir ileti alırsınız**. Bu işlem 24 saat sürebilir. 

4. Kuruluş verileriniz hazır olduğunda, sayfa yenilenmesi verilerinizin artık kullanılabilir olduğunu belirten bir ileti görüntüler ve kiracı kimlik **numaranızı da** sağlar. Kiracı verilerinize bağlanmaya çalışırken sonraki bir adımda kiracı kimliğini kullanacağız. 
 
    ![Kiracı Kimliği.](../../media/usage-analytics/tenant-id-gcc.png) 
 
    > [!IMPORTANT]
    > Verileriniz kullanılabilir olduğunda, Power BI Marketi'ne git'i seçmeyebilirsiniz. Bunu Power BI gerekir.  Kiracılar için gereken bu rapora GCC şablonu uygulaması Power BI Marketi'Power BI yoktur.  


## <a name="step-2-download-the-power-bi-template-connect-to-your-data-and-publish-the-report"></a>2. Adım: Power BI şablonunu indirme, verilerinize bağlanma ve raporu yayımlama

Microsoft 365 GCC kullanıcıların verilerine bağlanmak için Microsoft 365 Kullanım Analizi rapor şablonu dosyasını indirip kullanabilirler. Şablon dosyasını Power BI Desktop kullanmak için bu belgeyi açabilirsiniz. 

 > [!NOTE]
 > Şu anda, Microsoft 365 Usage Analytics raporu için bir şablon uygulaması, GCC Marketi'Power BI değildir.  

1. Power BI [şablonunu indirdikten sonra](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit), şablona başka bir Power BI Desktop. 
2. Bir **TenantID istendiğinde**, 1. adımda bu rapor için kurum verilerinizi hazırlarken edinmiş olduğunuz kiracı kimliğini girin. Sonra **Yükle'yi seçin**. Verilerinizin yüklemesi birkaç dakika sürer. 

    ![Kiracı kimliğini girin.](../../media/usage-analytics/add-tenant-id.png) 



3. Yükleme tamamlandığında raporunuz görüntülenir ve verilerinizin yönetici özetini görüntülersiniz. 

    ![Yönetici Özeti.](../../media/usage-analytics/exec-summary.png) 
 

4. Değişikliklerinizi rapora kaydedin. 
5. Raporu **,** görüntülen Power BI Desktop Power BI Online hizmetine yayımlamak için Yayınla menüsünde Yayımla'yı seçin. Bunun için Power BI Pro lisansı veya Power BI Premium gerekir. Yayımlama işleminin [bir parçası olarak](/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports), Power BI Online Service'te kullanılabilir bir çalışma alanında yayımlamak için bir hedef seçmeniz gerekir.

## <a name="related-content"></a>İlgili içerik

[Kullanım analizi hakkında](usage-analytics.md) </br>
[Kullanım analizinin en son sürümünü edinme](get-the-latest-version-of-usage-analytics.md) </br>
[Kullanım analizinde raporlarda gezinmek Microsoft 365 kullanmak](navigate-and-utilize-reports.md) </br>