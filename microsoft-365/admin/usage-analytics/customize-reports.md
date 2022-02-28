---
title: Microsoft 365 kullanım analizinde raporları özelleştirme
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
ms.assetid: 9b76065f-29b9-4b89-8059-c5f9db9ddbf6
description: Tarayıcıda ve çalışma sayfalarında raporları özelleştirmeyi Power BI Desktop.
ms.openlocfilehash: 32cf44c8d72160a583a841e26c2ad6934bd7eef2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984702"
---
# <a name="customize-the-reports-in-microsoft-365-usage-analytics"></a>Microsoft 365 kullanım analizinde raporları özelleştirme

Microsoft 365 kullanım analizi, Power BI kullanıcıların kullanıcı kitlelerini nasıl benimseyen ve nasıl kullanabileceğine Microsoft 365. Pano, kullanım verileriyle etkileşim kurmak için yalnızca bir başlangıç noktasıdır. Raporlar, daha kişiselleştirilmiş öngörüler edinmek için özelleştirilebilir.

Ayrıca, Power BI masaüstü uygulaması sayesinde, işletmeniz hakkında daha zengin öngörüler edinmek için raporlarınızı başka veri kaynaklarına bağlayarak raporlarınızı daha da özelleştirebilirsiniz.

## <a name="customizing-reports-in-the-browser"></a>Raporları tarayıcıda özelleştirme

Aşağıdaki iki örnekte, mevcut bir görselin nasıl değiştirileceği ve nasıl yeni görsel oluşturulacağı gösterilmiştir.

### <a name="modify-an-existing-visual"></a>Mevcut bir görseli değiştirme

Bu örnekte, Etkinleştirme/ **Lisanslama raporu** içinde **Etkinleştirme sekmesinin nasıl değiştirki olduğu** görüntülenir.

1. Etkinleştirme **/Lisanslama raporunun** içinde Etkinleştirme **sekmesini** seçin.

2. Sayfanın en üstünde, Diğer **sayfa düğmesi üzerinden** Düzenle ![düğmesini seçerek düzenleme moduna Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) düğmesi.

    ![Sağ üst gezinti bölmesinde Raporu düzenle'ye tıklayın.](../../media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png)

3. Sağ üst kısmında Bu sayfayı **çoğalt'ı seçin**.

    ![Bu sayfayı çoğalt'ı seçin.](../../media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png)

4. Sağ altta, Android, iOS, Mac gibi işletim sistemi tabanlı etkinleştiren kullanıcıların sayısını gösteren çubuk grafiklerden birini seçin.

5. Sağ **tıklayın görsel** öğeler alanında, Mac Sayısı'nın **görselden** kaldırmak için yanındaki **X'i** seçin.

    ![Mac Sayısını kaldır'ı seçin.](../../media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png)

### <a name="create-a-new-visual"></a>Yeni görsel oluşturma

Aşağıdaki örnekte, yeni Yammer kullanıcılarının aylık olarak izlenmesi için nasıl yeni bir görsel oluşturulacağı gösterilmiştir.

1. Sol **gezintiyi kullanarak Ürün** Kullanımı raporuna gidin **ve Yammer seçin**.

2. Düzenleme modunda, Düzen'de Daha ![fazla sayfa düğmesini seçerek Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) ve **Düzenle'yi seçin**.

3. Sayfanın alt kısmında ![Sayfa ekle düğmesi Power BI.](../../media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png) seçin.

4. Sağ **tarafta yer alan** Görselleştirmeler alanında, Yığılmış çubuk grafiği ( **soldan** önce en üst satır) seçin.

    ![Çubuk Grafik'i seçin.](../../media/214c3fed-6eae-43e6-83fb-708a2d74406e.png)

5. Bu görsel öğenin sağ alt öğesini seçin ve sürükleyerek görsel öğeyi büyütin.

6. Sağdaki  Alanlar alanında Takvim tabloyu **genişletin**.

7. **MonthName** öğesini, alanlar bölümünde yer alan **Görselleştirmeler** alanındaki **Eksen** başlığının hemen altına sürükleyin.

    ![Ay Adını sürükleyin.](../../media/bff99987-8c4b-4618-89fd-47df557b0ed7.png)

8. Sağdaki **Alanlar** bölümünde **TenantProductUsage** tablosunu genişletin.

9. **FirstTimeUsers** öğesini alanlar bölümündeki **Değer** başlığının hemen altına sürükleyin.

10. **Ürün** öğesini **Filtreler** alanındaki **Görsel düzey filtreleri** başlığının hemen altına sürükleyin.

11. Görünen **Filtre Türü** alanında **Yammer** onay kutusunu seçin.

    ![Onay Yammer seçin.](../../media/82e99730-0de9-42da-928a-76aab0c3e609.png)

12. Görselleştirme listesinin hemen altındaki Görsel **Öğeler'de** ![Biçim simgesi Power BI seçin](../../media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png).

13. Başlığı genişletin ve **Başlık Metni** değerini **Aya Göre Yammer'ı İlk Kez Kullananlar** olarak değiştirin.

14. **Metin Boyutu** değerini **12** olarak değiştirin.

15. Sağ alttaki sayfanın adını düzenleyerek yeni sayfanın başlığını değiştirebilirsiniz.

16. En üstte Okuma Görünümü'ne ve ardından **Kaydet'e** tıklayarak raporu **kaydedin**.

## <a name="customizing-the-reports-in-power-bi-desktop"></a>Power BI Masaüstü'nde raporları özelleştirme

Çoğu müşteri için raporları ve grafik görsellerini Power BI web hizmetinde değiştirmek yeterli olacaktır. Ancak bazı müşterilerin, kendi işletmeleri bağlamında daha zengin öngörüler edinmek amacıyla bu verileri başka verilerle birleştirmesi gerekebilir. Böyle durumlarda, Power BI Masaüstü uygulamasını kullanarak raporlar özelleştirilebilir ve ek raporlar oluşturulabilir. [Power BI Masaüstü](https://go.microsoft.com/fwlink/p/?linkid=849797) uygulamasını ücretsiz indirebilirsiniz.

### <a name="use-the-reporting-apis"></a>Raporlama API'lerini kullanma

Bu raporları sağlayan doğrudan ODATA raporlama API'lerinden Microsoft 365 başlatabilirsiniz.

1. **Veri al** \> **Diğer** \> **ODATA Akışı** \> **Bağlan** bölümüne gidin.

2. URL penceresinde "Giriş" https://<i></i> reports.office.com/pbi/v1.0/\<tenantid\>

    **NOT:** Raporlama API'leri önizlemededir ve üretime geçene kadar değişebilir.

    ![Masaüstü için OData Power BI URL'si.](../../media/c0ef967e-a454-4eba-bc8e-61e113170053.png)

3. İstendiğinde Microsoft 365 kimlik doğrulaması yapmak için kullanıcı (kuruluş veya okul) Microsoft 365 bilgilerinizi girin.

    Benimseme şablonu [uygulama](usage-analytics.md#faq) raporlarına kimlerin erişmesine izin verilmiyor hakkında daha fazla bilgi Microsoft 365 SSS bölümüne bakın.

4. Bağlantı yetkilendirildiğinde, bağlanılabilecek veri kümelerini gösteren Gezgin penceresini görürsünüz.

    Hepsini seçin ve Yükle'yi **seçin**.

    Bunu yaptığınızda, veriler Power BI Masaüstünüze indirilir. Bu dosyayı kaydettikten sonra ihtiyacınız olan raporları oluşturmaya başlayabilirsiniz.

    ![RAPORLAMA API'sinde kullanılabilen ODATA değerleri.](../../media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png)

### <a name="use-the-microsoft-365-usage-analytics-template"></a>Microsoft 365 kullanım analizi şablonunu kullanma

Verilere bağlanmak için, Microsoft 365 kullanım analizi raporlarına karşılık gelen Power BI şablonunu da başlangıç noktası olarak kullanabilirsiniz. Pbit dosyasını kullanmanın avantajı, bağlantı dizesinin zaten oluşturulmuş olmasıdır. Ayrıca, temel şemanın döndürdüğü verilere ek olarak oluşturulmuş tüm özel ölçümlerden yararlanabilir ve bunları daha da geliştirebilirsiniz.

Power BI şablonu dosyasını [Microsoft İndirme Merkezi'nden indirebilirsiniz](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). Power BI şablon dosyasını indirdikten sonra, çalışmaya şu adımları izleyin:

1. Pbit dosyasını açın.

2. İletişim kutusuna kiracı kimliğinizi girin.

    ![Pbit dosyasını açmak için kiracı kimliğinizi girin.](../../media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png)

3. İstendiğinde, kimlik doğrulaması yapmak Microsoft 365 yönetici kimlik bilgilerinizi girin.

     ve bu raporlara kimlerin erişmesine izin Microsoft 365 fazla bilgi edinin.

    Yetki sağlandıktan sonra Power BI dosyasındaki veriler yenilenir.

    Verilerin yüklenmesi biraz zaman alabilir. Yükleme tamamlandığında, dosyayı bir .pbix dosyası olarak kaydedebilir ve raporları özelleştirmeye devam edebilir ya da bu rapora başka bir veri kaynağı ekleyebilirsiniz.

4. Rapor oluşturma, Power BI hizmetine yayımlama ve kuruluşunuzla paylaşma işlemlerini anlamak için [Power BI ile Çalışmaya Başlama](/power-bi/fundamentals/desktop-getting-started) belgelerini izleyin. Özelleştirme ve paylaşım için bu yolu izlerseniz, ek Power BI lisanslarına ihtiyaç duyabilirsiniz. Ayrıntılar için Power BI [lisanslama kılavuzuna](https://go.microsoft.com/fwlink/p/?linkid=849803) bakın.
