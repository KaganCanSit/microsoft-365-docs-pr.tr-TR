---
title: PST dosyalarını içeri aktarma işlemiyle ilgili verilere filtre uygulama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 26af16df-34cd-4f4a-b893-bc1d2e74039e
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: PST dosyalarını içeri aktarma işlemi zaman içeri aktarma hizmetsinde akıllı içeri Microsoft 365 kullanarak verilere filtre uygulama hakkında bilgi Microsoft 365.
ms.openlocfilehash: 593ce847803fdc3529fbe9276721e6bb8cf79069
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990592"
---
# <a name="filter-data-when-importing-pst-files"></a>PST dosyalarını içeri aktarma işlemiyle ilgili verilere filtre uygulama

PST dosyalarında hedef posta kutularına gerçekten içeri aktarılan öğeleri filtrelemek için, Içeri Aktarma hizmetine Microsoft 365 Akıllı İçeri Aktarma özelliğini kullanın. Bu, şu şekilde çalışır:
  
- Siz PST içeri aktarma işini oluşturduk ve gönderdikten sonra, PST dosyaları Microsoft bulutunda bir Azure depolama alanına karşıya yüklenen dosyalar.
  
- Microsoft 365 posta kutusu öğelerinin yaşını ve PST dosyalarında yer alan farklı ileti türlerini tanımarak PST dosyalarıdaki verileri güvenli ve güvenli bir şekilde analiz eder.
  
- Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, hangi verilerin içeri aktarılamayacaklarını kontrol etmek için filtreler ayarlayan filtreler ayarlayan ve içeri aktarılan verileri olduğu gibi PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır. Örneğin, şunları seçebilirsiniz:
  
  - Yalnızca belirli bir yaşa sahip öğeleri içeri aktarın.
  
  - Seçili ileti türlerini içeri aktarma.
  
  - Belirli kişiler tarafından gönderilen veya alınan iletileri kapsam dışında tutabilirsiniz.
  
- Filtre ayarlarını yapılandırdikten sonra, Microsoft 365 içeri aktarma işsinde belirtilen hedef posta kutularına yalnızca filtre ölçütüne uyan verileri içeri aktarabilirsiniz.
  
Aşağıdaki grafik Akıllı İçeri Aktarma işlemini gösterir ve gerçekleştir görevleri ve Akıllı İçeri Aktarma tarafından gerçekleştirilen görevleri Office 365.
  
![Akıllı veri aktarma işlemi Office 365.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>PST içeri aktarma işi oluşturma

- Bu konudaki adımlarda, Ağ karşıya yükleme veya sürücü gönderimi kullanarak Içeri Aktarma hizmeti Office 365 PST içeri aktarma işi oluşturduğunuz varsayılacaktır. Adım adım yönergeler için aşağıdaki konulardan birini izleyin:
    
  - [PST dosyalarını diğer dosyalara içeri yüklemek için ağ karşıya Office 365](use-network-upload-to-import-pst-files.md)
    
  - [PST dosyalarını içeri aktarma işlemi için sürücü gönderimi Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Ağ karşıya yükleme kullanarak bir içeri aktarma işi oluşturduktaktan sonra, Güvenlik & Uyumluluk Merkezi'nin İçeri Aktar sayfasındaki içeri aktarma işinin durumu Çözümleme devam ediyor olarak ayarlanır; bu da Microsoft 365'in yüklediğiniz PST dosyalarında bulunan verileri çözümlemektedir. **Yenile'yi**![ tıklatın.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) seçin. 
    
- Sürücü gönderimi içeri aktarma işlerinde, Microsoft veri merkezi personeli sabit sürücünizi alana ve PST dosyalarını kuruluşun Azure depolama alanına yükledikten sonra, veriler Microsoft 365 tarafından analiz edilir.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Posta kutularına alınan verileri filtreleme

PST içeri aktarma işini oluşturduktan sonra, içeri aktarma işlemi öncesinde verileri filtrelemek için bu adımları Office 365.
  
1. Yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> gidin ve kuruluşta yönetici hesabının kimlik bilgilerini kullanarak oturum açın.
    
2. İlke bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi İçeri **Aktar'a** \> **tıklayın**.
    
    Kuruma uygun içeri aktarma işleri İçeri Aktar **sekmesinde** listelenir. Durum **sütunundaki** Çözümleme tamamlandı **değeri**, iş verileri tarafından çözümlene ve içeri aktarma için Microsoft 365 hazır olan içeri aktarma işlerini gösterir.
    
    ![Çözümlemenin tamamlandı durumu, Microsoft 365 PST dosyalarında çözümleme olduğunu gösterir.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Tamamlamak istediğiniz içeri aktarma işini seçin ve bu işi tamamlamak için **İçeri Aktar'Office 365**.
  
    PST dosyaları ve içeri aktarma işiyle ilgili diğer bilgilerle birlikte dışarı uçan bir sayfa görüntülenir.

4. Verileri içeri **aktar'a Office 365**.
    
    Verilerinizi **filtrele** sayfası görüntülenir. Verilerin yaşıyla ilgili bilgiler dahil olmak üzere, PST dosyalarında içeri aktarma işiyle ilgili veriler hakkında veri içgörüleri içerir. 
    
    ![Verilerinizi filtrele sayfası, içeri aktarma işi için PST dosyalarıyla ilgili veri içgörülerini gösterir.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. Verileri kırpmak isteyip istemiyor musunuz? verileri kırpmak Microsoft 365, Verilerinizi filtrelemek istiyor musunuz **?** alanında, aşağıdakilerden birini yapın:
  
    a. Evet **, içeri aktarmadan önce verileri kırpmak istiyorum'a** ve sonra Sonraki'ye **tıklayın**.
  
    Verileri **Başka bir Office 365 sayfası sayfası**, gerçekleştirilen çözümlemeden ayrıntılı veri içgörüleriyle Microsoft 365 görüntülenir. 
  
    ![Microsoft 365 PST dosyalarıyla ilgili çözümlemelerinden ayrıntılı veri içgörülerini görüntüler.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Bu sayfada yer alan grafikte, aktarılan veri miktarı gösterilir. PST dosyalarında bulunan her ileti türüyle ilgili bilgiler grafikte görüntülenir. İmleci her çubuğun üzerine gelerek ilgili ileti türüyle ilgili belirli bilgileri görüntülayabilirsiniz. PST dosyalarının çözümlemelerine dayalı olarak, yaş değerleri farklı olan bir açılan liste de vardır. Açılan listede bir yaş seçildiğinde grafik, seçilen yaş için ne kadar veri aktarılamayacaklarını gösterecek şekilde güncelleştirilir. 
  
    b. Alınan veri miktarını azaltmak üzere ek filtreleri yapılandırmak için, Diğer filtreleme **seçenekleri'ne tıklayın**.
  
    ![Alınan verileri kırpmak için Diğer seçenekler sayfasındaki filtreleri yapılandırabilirsiniz.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Şu filtreleri yapılandırabilirsiniz:
  
      - **Yaş** - Yalnızca belirtilen yaştan daha yeni olan öğelerin aktarılmaz için bir yaş seçin. Aşağıdakilerin [Yaş filtresinin](#more-information) yaş demetlerini nasıl Microsoft 365 hakkında açıklama için Daha fazla bilgi **bölümüne** bakın. 
  
      - **Tür** - Bu bölüm, içeri aktarma işi için PST dosyalarında bulunan tüm ileti türlerini gösterir. Dışarıda tutmak istediğiniz ileti türünün yanındaki kutunun işaretini kaldırabilirsiniz. Diğer ileti türünü dışlamazsınız. Diğer [kategorisine](#more-information) dahil edilen posta kutusu öğelerinin listesi için Daha fazla bilgi bölümüne bakın.
  
      - **Kullanıcılar** - Belirli kişiler tarafından gönderilen veya alınan iletileri hariç tutabilirsiniz. Kime: alanında, Kime: alanında veya bilgi: alanında görünen kullanıcıları hariç tutmak için, bu alıcı türünün yanındaki Kullanıcıları dışla'ya tıklayın. Kişinin e-posta adresini (SMTP adresi) yazın ve Yeni **Ekle simgesine**![ tıklayın.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) bu alıcı türünü dışlanan kullanıcılar listesine eklemek için, kaydet'e tıklayın ve ardından dışlanan  kullanıcıların listesini kaydetmek için Kaydet'e tıklayın. 
  
        > [!NOTE]
        > Microsoft 365, Kişiler filtresini ayarlama sonucu elde edilen veri **içgörülerini göstermez**. Bununla birlikte, bu filtreyi belirli kişiler tarafından gönderilen veya alınan iletileri dışarıda tutmak üzere ayarsanız, söz konusu iletiler gerçek içeri aktarma işlemi sırasında hariç tutulacak. 
  
    c. Filtre **ayarlarınızı** kaydetmek **için Diğer filtreleme seçenekleri** uçarak giriş sayfasında Uygula'ya tıklayın. 
  
    Verileri şu ana kadar içeri aktar **Office 365** sayfasındaki veri içgörüleri, filtre ayarlarına göre içeri aktar edilecek toplam veri miktarı da dahil olmak üzere, filtre ayarlarınıza göre güncelleştirilir. Filtre ayarlarının özeti de gösterilir. Gerekirse ayarı **değiştirmek için** filtrenin yanındaki Düzenle'ye tıkabilirsiniz. 
  
    ![Veri içgörüleri, filtre ayarlarınıza göre güncelleştirilir.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. **İleri**'ye tıklayın.
  
    Filtre ayarlarınızı gösteren bir durum sayfası görüntülenir. Tekrar, filtre ayarlarından herhangi birini düzenleyebilirsiniz.
  
    e. İçeri **aktarmayı başlatmak için** Verileri içeri aktar'a tıklayın. Alınan toplam veri miktarı görüntülenir. 
  
    Veya
  
    a. Hayır **, PST dosyalarında yer alan tüm verileri içeri** aktararak tüm verileri içeri aktarmayı istiyorum'a ve sonra Office 365'e **tıklayın**.
  
    b. Verileri şu **ana kadar içeri aktar Office 365** içeri **aktarmayı başlatmak için Verileri içeri** aktar'a tıklayın. Alınan toplam veri miktarı görüntülenir. 
  
6. İçeri Aktar **sekmesinde Yenile'ye**  ![tıklayın](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png). İçeri aktarma işinin durumu **Durum sütununda görüntülenir** .
  
7. Her PST dosyasının durumu ve yapılandırmış olunan filtre ayarları gibi daha ayrıntılı bilgileri görüntülemek için işi içeri aktarma işini tıklatın.

## <a name="more-information"></a>Daha fazla bilgi

- Yaş Microsoft 365 artışlarını nasıl belirlersiniz? Bir PST Microsoft 365 çözümleyene kadar, her öğenin gönderilen veya alınan zaman damgasına bakarak görüntüler (bir öğenin hem gönderilmiş hem de alınan zaman damgası varsa, en eski tarih seçilidir). Daha Microsoft 365 zaman damgasının yıl değerine bakarak, öğenin yaşını belirlemek için bu değeri geçerli tarihle karşılaştırıldığında. Bu asma değerler daha sonra Yaş filtresi açılan listesinde değer **olarak** kullanılır. Örneğin, bir PST dosyasında 2016, 2015 ve 2014 iletileri varsa, Yaş filtresinde yer alan değerler **1** yıl, **2** yıl  ve **3 yıl olur**.
  
- Aşağıdaki tabloda, Diğer seçenekler uçarak giriş sayfasındaki Tür filtresinin Diğer kategorisinde yer  alan ileti türleri listelanmıştır (önceki yordamın 5b. adımına bakın).  Şu anda, PST'leri içeri aktararak "Diğer" kategorisindeki öğeleri Office 365. 
  
    |**İleti sınıfı kimliği**|**Bu ileti sınıfını kullanan posta kutusu öğeleri**|
    |:-----|:-----|
    |IPM. Etkinlik  <br/> |Günlük girdileri  <br/> |
    |IPM. Belge  <br/> |Belgeler ve dosyalar (e-posta iletisine ekli değil)  <br/> |
    |IPM. Dosya  <br/> |(IPM ile aynıdır. Belge)  <br/> |
    |IPM. Note.IMC.Notification  <br/> |İnternet'e Bağlan ağ geçidi olan internet Exchange Server tarafından gönderilen raporlar  <br/> |
    |IPM. Note.Microsoft.Faks  <br/> |Faks iletileri  <br/> |
    |IPM. Note.Rules.Oof.Template.Microsoft  <br/> |Ofis dışında otomatik yanıt iletileri  <br/> |
    |IPM. Note.Rules.ReplyTemplate.Microsoft  <br/> |Gelen kutusu kuralı tarafından gönderilen yanıtlar  <br/> |
    |IPM. OLE. Sınıf  <br/> |Yinelenen seri için özel durumlar  <br/> |
    |IPM. Geri Çekme.Rapor  <br/> |İleti geri çağırma raporları  <br/> |
    |IPM. Uzak  <br/> |Uzak posta iletileri  <br/> |
    |IPM. Rapor  <br/> |Öğe durum raporları  <br/> |
