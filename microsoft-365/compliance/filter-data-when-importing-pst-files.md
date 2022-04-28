---
title: PST dosyalarını içe aktarırken verileri filtreleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: PST dosyalarını Microsoft 365 içeri aktarırken Microsoft 365 içeri aktarma hizmetindeki akıllı içeri aktarma özelliğini kullanarak verileri filtrelemeyi öğrenin.
ms.openlocfilehash: 5ff78126f9e2d02181635433d7a94ede0e191c8d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099751"
---
# <a name="filter-data-when-importing-pst-files"></a>PST dosyalarını içe aktarırken verileri filtreleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

hedef posta kutularına aktarılan PST dosyalarındaki öğeleri filtrelemek için Microsoft 365 İçeri Aktarma hizmetindeki yeni Akıllı İçeri Aktarma özelliğini kullanın. Şu şekilde çalışır:
  
- BIR PST içeri aktarma işi oluşturup gönderdikten sonra, PST dosyaları Microsoft bulutunda bir Azure depolama alanına yüklenir.
  
- Microsoft 365, posta kutusu öğelerinin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini belirleyerek PST dosyalarındaki verileri güvenli ve güvenli bir şekilde analiz eder.
  
- Analiz tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarındaki tüm verileri olduğu gibi içeri aktarma veya hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak içeri aktarılan verileri kırpma seçeneğiniz vardır. Örneğin, şunları seçebilirsiniz:
  
  - Yalnızca belirli bir yaştaki öğeleri içeri aktarın.
  
  - Seçili ileti türlerini içeri aktarın.
  
  - Belirli kişiler tarafından gönderilen veya alınan iletileri hariç tutun.
  
- Filtre ayarlarını yapılandırdıktan sonra, Microsoft 365 yalnızca filtreleme ölçütlerini karşılayan verileri içeri aktarma işinde belirtilen hedef posta kutularına aktarır.
  
Aşağıdaki grafik, Akıllı İçeri Aktarma işlemini gösterir ve gerçekleştirdiğiniz görevleri ve Office 365 tarafından gerçekleştirilen görevleri vurgular.
  
![Office 365'daki Akıllı İçeri Aktarma işlemi.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>PST içeri aktarma işi oluşturma

- Bu konudaki adımlarda, ağ yükleme veya sürücü gönderimini kullanarak Office 365 İçeri Aktarma hizmetinde bir PST içeri aktarma işi oluşturduğunuz varsayılır. Adım adım yönergeler için aşağıdaki konulardan birine bakın:
    
  - [PST dosyalarını Office 365 içeri aktarmak için ağ karşıya yükleme özelliğini kullanma](use-network-upload-to-import-pst-files.md)
    
  - [PST dosyalarını Office 365 aktarmak için sürücü gönderimi kullanma](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Ağ karşıya yüklemesini kullanarak içeri aktarma işi oluşturduktan sonra, Güvenlik & Uyumluluk Merkezi'ndeki İçeri Aktar sayfasındaki içeri aktarma işinin durumu **Analiz sürüyor** olarak ayarlanır; bu da Microsoft 365 karşıya yüklediğiniz PST dosyalarındaki verileri analiz ettiği anlamına gelir. **Yenilerefresh'e**![ tıklayın.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) öğesini seçin. 
    
- Sürücü gönderimi içeri aktarma işleri için, Microsoft veri merkezi personeli sabit sürücünüzü aldıktan ve PST dosyalarını kuruluşunuzun Azure depolama alanına yükledikten sonra veriler Microsoft 365 tarafından analiz edilir.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Posta kutularına aktarılan verileri filtreleme

PST içeri aktarma işini oluşturduktan sonra, verileri Office 365 içeri aktarmadan önce filtrelemek için bu adımları izleyin.
  
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalına</a> gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.
    
2. Uyumluluk portalının sol bölmesinde **Veri yaşam döngüsü yönetimi** \> **İçeri Aktar'a** tıklayın.
    
    Kuruluşunuzun içeri aktarma işleri **İçeri Aktar** sekmesinde listelenir. **Durum** sütunundaki **Çözümleme tamamlandı** değeri, Microsoft 365 tarafından analiz edilmiş ve içeri aktarma için hazır olan içeri aktarma işlerini gösterir.
    
    ![Çözümlemenin tamamlanma durumu, Microsoft 365 PST dosyalarındaki verileri analiz etmiş olduğunu gösterir.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Tamamlamak istediğiniz içeri aktarma işini seçin ve **Office 365 için içeri aktar'a** tıklayın.
  
    PST dosyaları ve içeri aktarma işiyle ilgili diğer bilgiler içeren bir açılır sayfa görüntülenir.

4. **Office 365 için İçeri Aktar'a** tıklayın.
    
    **Verilerinizi filtreleyin** sayfası görüntülenir. İçeri aktarma işinin PST dosyalarındaki veriler hakkında veri içgörüleri içerir ve verilerin yaşıyla ilgili bilgiler de buna dahildir. 
    
    ![Verilerinizi filtreleyin sayfasında içeri aktarma işi için PST dosyalarının veri içgörüleri gösterilir.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. Microsoft 365'a aktarılan verileri kırpmak isteyip istemediğinize bağlı olarak, **Verilerinizi filtrelemek istiyor musunuz?** bölümünde aşağıdakilerden birini yapın:
  
    a. **Evet, içeri aktardığınız verileri kırpmak için içeri aktarmadan önce filtrelemek istiyorum'a** tıklayın ve ardından **İleri'ye** tıklayın.
  
    **Verileri Office 365 içeri aktar sayfası**, Microsoft 365 gerçekleştirilen analizden ayrıntılı veri içgörüleriyle birlikte görüntülenir. 
  
    ![Microsoft 365, PST dosyalarının analizinden ayrıntılı veri içgörüleri görüntüler.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Bu sayfadaki grafik, içeri aktarılacak veri miktarını gösterir. PST dosyalarında bulunan her ileti türüyle ilgili bilgiler grafikte görüntülenir. İleti türüyle ilgili belirli bilgileri görüntülemek için imleci her çubuğun üzerine getirebilirsiniz. PST dosyalarının analizine göre farklı yaş değerlerine sahip bir açılan liste de vardır. Açılan listeden bir yaş seçtiğinizde, grafik seçilen yaş için ne kadar veri içeri aktarılacağını gösterecek şekilde güncelleştirilir. 
  
    b. İçeri aktarılan veri miktarını azaltmak üzere ekleme filtrelerini yapılandırmak için **Diğer filtreleme seçenekleri'ne** tıklayın.
  
    ![İçeri aktarılan verileri kırpmak için Diğer seçenekler sayfasındaki filtreleri yapılandırın.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Şu filtreleri yapılandırabilirsiniz:
  
      - **Yaş** - Yalnızca belirtilen yaştan daha yeni olan öğelerin içeri aktarılması için bir yaş seçin. Microsoft 365 **Yaş** filtresi için yaş demetlerini nasıl belirlediğinin açıklaması için [Daha fazla bilgi](#more-information) bölümüne bakın. 
  
      - **Tür** - Bu bölüm, içeri aktarma işinin PST dosyalarında bulunan tüm ileti türlerini gösterir. Dışlamak istediğiniz ileti türünün yanındaki kutunun işaretini kaldırabilirsiniz. Diğer ileti türünü dışlayamazsınız. Diğer kategorisine dahil edilen posta kutusu öğelerinin listesi için [Daha fazla bilgi](#more-information) bölümüne bakın.
  
      - **Kullanıcılar** - Belirli kişiler tarafından gönderilen veya alınan iletileri dışlayabilirsiniz. Kimden: alanında, Kime: alanında veya iletinin Bilgi: alanında görünen kişileri dışlamak için, bu alıcı türünün yanındaki **Kullanıcıları dışla'ya** tıklayın. Kişinin e-posta adresini (SMTP adresi) yazın, **EkleYeni**![ simgesine tıklayın.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) bunları bu alıcı türü için dışlanan kullanıcılar listesine eklemek için ve ardından **Kaydet'e** tıklayarak dışlanan kullanıcıların listesini kaydedin. 
  
        > [!NOTE]
        > Microsoft 365 **, Kişiler** filtresinin ayarlanmasından kaynaklanan veri içgörülerini göstermez. Ancak, bu filtreyi belirli kişiler tarafından gönderilen veya alınan iletileri dışlayacak şekilde ayarlarsanız, bu iletiler gerçek içeri aktarma işlemi sırasında dışlanır. 
  
    c. Filtre ayarlarınızı kaydetmek için **Diğer filtreleme seçenekleri** açılır sayfasında **Uygula'ya** tıklayın. 
  
    Verileri **Office 365 aktar sayfasındaki veri** içgörüleri, filtre ayarlarına göre içeri aktarılacak toplam veri miktarı dahil olmak üzere filtre ayarlarınıza göre güncelleştirilir. Filtre ayarlarının özeti de gösterilir. Gerekirse ayarı değiştirmek için filtrenin yanındaki **Düzenle'ye** tıklayabilirsiniz. 
  
    ![Veri içgörüleri, filtre ayarlarınıza göre güncelleştirilir.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. **İleri**'ye tıklayın.
  
    Filtre ayarlarınızı gösteren bir durum sayfası görüntülenir. Yine, filtre ayarlarından herhangi birini düzenleyebilirsiniz.
  
    e. **İçeri aktarmayı başlatmak için Verileri içeri** aktar'a tıklayın. İçeri aktarılacak toplam veri miktarı görüntülenir. 
  
    Veya
  
    a. PST dosyalarındaki tüm verileri Office 365 aktarmak için **Hayır, her şeyi içeri aktarmak istiyorum'a** tıklayın ve ardından **İleri'ye** tıklayın.
  
    b. **verileri Office 365 içeri aktar** sayfasında İçeri aktarma işlemini başlatmak için **Verileri içeri aktar'a** tıklayın. İçeri aktarılacak toplam veri miktarı görüntülenir. 
  
6. **İçeri Aktar** sekmesinde **Yenile'ye** ![tıklayın.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png). İçeri aktarma işinin durumu **Durum** sütununda görüntülenir.
  
7. Her PST dosyasının durumu ve yapılandırdığınız filtre ayarları gibi daha ayrıntılı bilgileri görüntülemek için içeri aktarma işine tıklayın.

## <a name="more-information"></a>Daha fazla bilgi

- Microsoft 365 yaş filtresinin artışlarını nasıl belirler? Microsoft 365 bir PST dosyasını analiz ettiğinde, her öğenin gönderilen veya alınan zaman damgasına bakar (bir öğenin hem gönderilmiş hem de alınan zaman damgası varsa, en eski tarih seçilir). Ardından Microsoft 365 bu zaman damgasının yıl değerine bakar ve öğenin yaşını belirlemek için bu değeri geçerli tarihle karşılaştırır. Bu yaşlar daha sonra **Yaş** filtresinin açılan listesinde değerler olarak kullanılır. Örneğin, bir PST dosyasında 2016, 2015 ve 2014'ten iletiler varsa, **Yaş** filtresindeki değerler **1 yıl**, **2 yıl** ve **3 yıl** olur.
  
- Aşağıdaki tabloda, **Diğer seçenekler** açılır sayfasındaki **Tür** filtresindeki **Diğer** kategorisine dahil edilen ileti türleri listelenmiştir (önceki yordamdaki 5b. adıma bakın). Şu anda, PST'leri Office 365 içeri aktarırken "Diğer" kategorisindeki öğeleri dışlayamazsınız. 
  
    |**İleti sınıfı kimliği**|**Bu ileti sınıfını kullanan posta kutusu öğeleri**|
    |:-----|:-----|
    |IPM. Etkinlik  <br/> |Günlük girişleri  <br/> |
    |IPM. Belge  <br/> |Belgeler ve dosyalar (e-posta iletisine eklenmemiş)  <br/> |
    |IPM. Dosya  <br/> |(IPM ile aynı. Belge)  <br/> |
    |IPM. Note.IMC.Notification  <br/> |İnternet'e Exchange Server ağ geçidi olan Internet Mail Bağlan tarafından gönderilen raporlar  <br/> |
    |IPM. Note.Microsoft.Fax  <br/> |Faks iletileri  <br/> |
    |IPM. Note.Rules.Oof.Template.Microsoft  <br/> |İş yeri dışında otomatik yeniden yanıt iletileri  <br/> |
    |IPM. Note.Rules.ReplyTemplate.Microsoft  <br/> |Gelen kutusu kuralı tarafından gönderilen yanıtlar  <br/> |
    |IPM. OLE. Sınıfı  <br/> |Yinelenen seriler için özel durumlar  <br/> |
    |IPM. Recall.Report  <br/> |İleti geri çağırma raporları  <br/> |
    |IPM. Uzaktan  <br/> |Uzak posta iletileri  <br/> |
    |IPM. Rapor  <br/> |Öğe durum raporları  <br/> |
