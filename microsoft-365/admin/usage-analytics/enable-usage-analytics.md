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
description: Hızlı Kullanım Analizi şablon uygulamasını kullanarak kiracınız için Microsoft 365 toplamaya nasıl başlayacağınızı Power BI.
ms.openlocfilehash: b547acc5adf312458e82108a36bbd9c0cbf60f10
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027540"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Microsoft 365 kullanım analizini etkinleştirme

ABD Microsoft 365 (GCC) Microsoft 365 Government Community Cloud kiracıda Microsoft 365 kullanım çözümlemelerini etkinleştirmek için bkz[. Bağlan'Microsoft 365 Government Community Cloud Analizi ile GCC (veri) içerir](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Başlamadan önce

Daha fazla kullanım Microsoft 365 için önce verileri mobil uygulamada kullanılabilir hale <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi ardından şablon</a> uygulamasını Power BI.

## <a name="get-power-bi"></a>Power BI'ı alma

Henüz oturum açmadısanız Power BI için [kaydol Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Deneme **sürümüne kaydolmak** için Ücretsiz deneyin'i veya denemeyi satın **almak için** Şimdi satın Power BI Pro.


Ayrıca, Power BI'ın bir sürümünü satın almak için **Ürünler**'i de genişletebilirsiniz.

> [!NOTE]
> Şablon uygulamasını Power BI Pro, özelleştirmek ve dağıtmak için bu lisansa ihtiyacınız vardır. Daha fazla bilgi için lütfen [Önkoşullar'a bakın](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Verilerinizi paylaşmak için hem sizin hem de verileri paylaşırken sahip olduğunuz kişilerin Power BI Pro lisansına sahip olması veya içeriğin Power BI premium bir hizmette çalışma [alanında olması gerekir](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Şablon uygulamasını etkinleştirme

Şablon uygulamasını etkinleştirmek için Genel yönetici **olmak gerekir**.

Daha [fazla bilgi için bkz](../add-users/about-admin-roles.md) . yönetici rolleri.

1. Yönetim merkezinde Kuruluş ayarları Hizmetleri **Ayarlar** \> **gidin**\>.

2. Hizmetler sekmesinde **Raporlar'ı**  **seçin**.

3. Açılan Raporlar panelinde Rapor verilerini, Çalışma **için kullanım Microsoft 365 için** kullanılabilir Power BI **Açık olarak** \> **ayarlayın**.

Veri toplama işlemi, kiracının boyutuna bağlı olarak iki - 48 saat içinde tamamlanır. Veri **toplama Power BI** Git düğmesi etkinleştirilir (artık gri değildir). Bu tamam, uygulamanın geçmiş kullanım verileri kuruluş düzeyine bağlıdır. 

> [!NOTE]
> "Kullanıcı Etkinliği **"** sekmesinin verileri yalnızca geçerli ayın on beşinci gününden ve sonraki ayın ilk gününden sonra yenilenir, dolayısıyla ilk yenileme tamamlanana kadar başlangıçta boş kalır.

## <a name="start-the-template-app"></a>Şablon uygulamasını başlatma

Şablon uygulamasını başlatmak için genel **yönetici, rapor** **okuyucusu,** genel yönetici, **Exchange** veya **Skype Kurumsal yönetici** **SharePoint gerekir**.

1. Kiracı kimliğini kopyalayın ve Kiracıya **git'i Power BI**.

2. Power BI'a ulaştığınızda oturum açın. Ardından **UygulamalarSeçenekler** -> menüsünden uygulamaları edinin öğesini seçin.

3. **Uygulamalar** sekmesinde arama kutusuna Microsoft 365 yazın ve ardından **Microsoft 365 kullanım analizi**\> **Şimdi edinin**'i seçin.

    [![Şimdi al'ı seçin.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Uygulama yüklendikten sonra. Kutucuğu seçerek açın.

5. Örnek **verileri olan** uygulamayı görüntülemek için Uygulamayı keşfet'i seçin. Uygulamayı **Bağlan** verilerine bağlamak için Diğer'i seçin.

6. **Bağlan'i** **Bağlan** kullanım Microsoft 365 seçin, ardından 1. adımda kopyaladığı kiracı kimliğini (tire olmadan) yazın ve Sonraki'yi **seçin**.

7. Sonraki ekranda, Kimlik doğrulama yöntemi **Olarak OAuth2'yi** **seçin Oturum** \> **açma**. Başka herhangi bir kimlik doğrulama yöntemi seçerseniz, şablon uygulamasına bağlantı başarısız olur.

    ![Kimlik doğrulama yöntemi olarak Microsoft hesabını seçin.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Şablon uygulaması örneği Microsoft 365 web'de Power BI kullanım analizi panosu Power BI kullanılabilir. Panonun ilk yüklemesi 2-30 dakika arasında sürer.

Kiracı düzeyi toplamları, kabul edildikten sonra tüm raporlarda kullanılabilir. **Kullanıcı düzeyi ayrıntılar, kabul sonrasında yalnızca sonraki takvim 5.00'de kullanılabilir hale gelecektir**. Bu, Kullanıcı Etkinliği altındaki tüm raporları etkiler (Bu [](navigate-and-utilize-reports.md) raporları görüntülemeye ve kullanmaya Microsoft 365 için bkz. Raporlarda gezinme ve raporlardan yararlanma.

## <a name="make-the-collected-data-anonymous"></a>Toplanan verilerin anonim olmasını sağlama

Raporlar, kurum kurum kullanım verileri hakkında bilgi sağlar. Varsayılan olarak, raporlar kullanıcılar, gruplar ve siteler için tanımlayıcı adlar içeren bilgiler görüntüler. 1 Eylül 2021'den başlayarak, şirketlerin yerel gizlilik yasalarını desteklemelerine yardımcı olmak için devam eden taahhüdlerimizin bir parçası olarak tüm raporlar için kullanıcı bilgilerini varsayılan olarak gizleriz.
  
Genel yöneticiler bu değişikliği kiracıları için geri döndürebilir ve kuruluşlarının gizlilik uygulamaları buna izin verdiyse tanımlanabilecek kullanıcı bilgilerini gösterebilir. Aşağıdaki adımları kullanarak Microsoft 365 yönetim merkezi sağ edilebilir:
  
1. Yönetim merkezinde Kuruluş Yönetim Merkezi **Ayarlar** \> **Hizmetler Ayarlar** \> **gidin.**

2. **Raporlar**'ı seçin. 
  
3. Tüm raporlarda **ifadenin işaretini kaldırın, kullanıcılar,** gruplar ve siteler için tanımlanmamış adları görüntüler ve sonra değişikliklerinizi kaydedin.  
  
Bu değişikliklerin etkilisi birkaç dakika sürer. Tanınmaya neden olan kullanıcı bilgilerini gösterme, denetim günlüğüne Microsoft 365 uyumluluk merkezi olaydır.   

## <a name="related-content"></a>İlgili içerik

[Kullanım analizi hakkında](usage-analytics.md) (makale)\
[Kullanım analizinin en son sürümünü edinin](get-the-latest-version-of-usage-analytics.md) (makale)\
[Kullanım analizinde raporlarda gezinmek Microsoft 365 kullanmak](navigate-and-utilize-reports.md) (makale)
