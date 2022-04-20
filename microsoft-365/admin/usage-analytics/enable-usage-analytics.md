---
title: Microsoft 365 kullanım analizini etkinleştirme
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
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Power BI'daki Microsoft 365 Kullanım Analizi şablon uygulamasını kullanarak kiracınız için veri toplamaya nasıl başlayacağınızı öğrenin.
ms.openlocfilehash: cc2b74696dbdab416493be1909f1781b31f201a6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946956"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Microsoft 365 kullanım analizini etkinleştirme

Microsoft 365 ABD Government Community Cloud (GCC) kiracısında Microsoft 365 kullanım analizini etkinleştirmek için bkz. [Microsoft 365 için Bağlan Kullanım Analizi ile verileri Government Community Cloud (GCC).](connect-to-gcc-data-with-usage-analytics.md)

## <a name="before-you-begin"></a>Başlamadan önce

Microsoft 365 kullanım analizini kullanmaya başlamak için önce verileri <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> kullanılabilir hale getirmeniz, ardından şablon uygulamasını Power BI'de başlatmanız gerekir.

## <a name="get-power-bi"></a>Power BI'ı alma

Henüz Power BI yoksa [Power BI Pro kaydolabilirsiniz](https://go.microsoft.com/fwlink/p/?linkid=845347). Deneme sürümüne kaydolmak için **Ücretsiz deneyin'i** veya Power BI Pro almak için **Şimdi satın alın'ı** seçin.


Ayrıca, Power BI'ın bir sürümünü satın almak için **Ürünler**'i de genişletebilirsiniz.

> [!NOTE]
> Şablon uygulamasını yüklemek, özelleştirmek ve dağıtmak için Power BI Pro lisansına ihtiyacınız vardır. Daha fazla bilgi için bkz [. Önkoşullar](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Verilerinizi paylaşmak için hem sizin hem de verileri paylaştığınız kişilerin Power BI Pro lisansına sahip olması veya içeriğin [Power BI premium hizmetteki](/power-bi/service-premium-what-is) bir çalışma alanında olması gerekir.

## <a name="enable-the-template-app"></a>Şablon uygulamasını etkinleştirme

Şablon uygulamasını etkinleştirmek için **bir Genel yönetici** olmanız gerekir.

Daha fazla bilgi için [yönetici rolleri hakkında](../add-users/about-admin-roles.md) bilgi edinin.

1. Yönetim merkezinde **Ayarlar** \> **Kuruluş ayarları** \> **Hizmetleri** sekmesine gidin.

2. **Hizmetler** sekmesinde **Raporlar'ı** seçin.

3. Açılan Raporlar panelinde Rapor **verilerini Power BI için kullanım analizi Microsoft 365 kullanılabilir duruma getir** seçeneğini **KaydetmeDe** \> olarak ayarlayın.

Veri toplama işlemi, kiracınızın boyutuna bağlı olarak iki ile 48 saat içinde tamamlanır. Veri toplama tamamlandığında **Power BI git** düğmesi etkinleştirilir (artık gri olmaz). İşlem tamamlandıktan sonra uygulama, kuruluşunuz düzeyinde geçmiş kullanım verileri sağlar. 

> [!NOTE]
> **"Kullanıcı Etkinliği"** sekmesinin verileri yalnızca geçerli ayın on beşinci gününden ve sonraki ayın ilk gününden sonra yenilenir, bu nedenle ilk yenileme tamamlanana kadar başlangıçta boş kalır.

## <a name="start-the-template-app"></a>Şablon uygulamasını başlatma

Şablon uygulamasını başlatmak için genel **yönetici**, **rapor okuyucu**, **Exchange yönetici**, **Skype Kurumsal yönetici** veya **SharePoint yöneticisi olmanız gerekir**.

1. Kiracı kimliğini kopyalayın ve **Power BI git'i** seçin.

2. Power BI'a ulaştığınızda oturum açın. Ardından gezinti menüsünden **UygulamalarUyrunu**-> **al'ı seçin**.

3. **Uygulamalar** sekmesinde arama kutusuna Microsoft 365 yazın ve ardından **Microsoft 365 kullanım analizi**\> **Şimdi edinin**'i seçin.

    [![Şimdi edinin'i seçin.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Uygulama yüklendikten sonra. Kutucuğu seçerek açın.

5. Uygulamayı örnek verilerle görüntülemek için Uygulamayı **keşfet'i** seçin. Uygulamayı kuruluşunuzun verilerine bağlamak için **Bağlan** seçin.

6. **kullanım analizi Microsoft 365 için Bağlan ekranında Bağlan'ı** seçin, ardından (1. adımda) kopyaladığınız kiracı kimliğini (tireler olmadan) yazın ve **İleri'yi** seçin.

7. Sonraki ekranda, **Oturum açma Kimlik Doğrulama yöntemi** \> olarak **OAuth2'yi** seçin. Başka bir kimlik doğrulama yöntemi seçerseniz şablon uygulamasına bağlantı başarısız olur.

    ![Kimlik doğrulama yöntemi olarak Microsoft hesabı'nı seçin.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Şablon uygulamasının örneği açıldıktan sonra Microsoft 365 kullanım analizi panosu web'deki Power BI'de kullanılabilir. Panonun ilk yüklemesi 2-30 dakika arasında sürer.

Kiracı düzeyi toplamları, kabul ettikten sonra tüm raporlarda kullanılabilir. **Kullanıcı düzeyi ayrıntıları, kabul ettikten sonra yalnızca bir sonraki takvim ayının 5'inde kullanılabilir duruma gelir**. Bu, Kullanıcı Etkinliği altındaki tüm raporları etkiler (Bu raporları görüntüleme ve kullanma hakkında ipuçları için bkz. [Microsoft 365 kullanım analizinde raporlarda gezinme](navigate-and-utilize-reports.md) ve bunları kullanma).

## <a name="make-the-collected-data-anonymous"></a>Toplanan verilerin anonim olmasını sağlama

Raporlar, kuruluşunuzun kullanım verileri hakkında bilgi sağlar. Varsayılan olarak, raporlar kullanıcılar, gruplar ve siteler için tanımlanabilir adlarla bilgileri görüntüler. 1 Eylül 2021'den itibaren, şirketlerin yerel gizlilik yasalarını desteklemesine yardımcı olmak için devam eden taahhüdümüzün bir parçası olarak tüm raporlar için kullanıcı bilgilerini varsayılan olarak gizleyeceğiz.
  
Genel yöneticiler, kiracıları için bu değişikliği geri alabilir ve kuruluşlarının gizlilik uygulamaları izin verirse tanımlanabilir kullanıcı bilgilerini gösterebilir. Bu, aşağıdaki adımları izleyerek Microsoft 365 yönetim merkezi elde edilebilir:
  
1. Yönetim merkezinde **Ayarlar** **Kuruluş Ayarlar** \> \> **Hizmetleri** sayfasına gidin.

2. **Raporlar**'ı seçin. 
  
3. Deyimin işaretini kaldırın **Tüm raporlarda, kullanıcılar, gruplar ve siteler için kimliği kaldırılmış adları görüntüleyin ve** değişikliklerinizi kaydedin.  
  
Bu değişikliklerin etkili olması birkaç dakika sürer. Tanımlanabilir kullanıcı bilgilerinin gösterilmesi, Microsoft Purview uyumluluk portalı denetim günlüğünde günlüğe kaydedilen bir olaydır.   

## <a name="related-content"></a>İlgili içerik

[Kullanım analizi hakkında](usage-analytics.md) (makale)\
[Kullanım analizinin en son sürümünü alma](get-the-latest-version-of-usage-analytics.md) (makale)\
[Microsoft 365 kullanım analizinde raporlarda gezinme ve bunları kullanma](navigate-and-utilize-reports.md) (makale)
