---
title: Denetim günlüğünde paylaşım denetimini kullanma
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
search.appverid:
- SPO160
- MOE150
- BCS160
- MET150
ms.collection:
- M365-security-compliance
- SPO_Content
ms.assetid: 50bbf89f-7870-4c2a-ae14-42635e0cfc01
description: Yönetici, kuruluşlarının dışındaki kullanıcılarla paylaşılan kaynakları tanımlamak Microsoft 365 denetim günlüğünde paylaşım denetimini kullanmayı öğrenebilir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff05b655617608332b4b838e07a6af55e8b4d010
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987304"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Denetim günlüğünde paylaşım denetimini kullanma

Paylaşım, SharePoint Online ve OneDrive İş'te önemli bir etkinliktir ve kuruluşlarda yaygın olarak kullanılır. Yöneticiler, kuruluşlarında paylaşımın nasıl kullanıla olduğunu belirlemek için denetim günlüğünde paylaşım denetimini kullanabilir. 
  
## <a name="the-sharepoint-sharing-schema"></a>The SharePoint Sharing schema

Paylaşım olayları (paylaşım ilkesi ve paylaşım bağlantılarıyla ilgili olaylar dahil değildir) dosya ve klasörle ilgili olaylardan birincil olarak farklıdır: bir kullanıcı, başka bir kullanıcı üzerinde etkili bir eylem gerçekleştirmektedir. Örneğin, bir kaynak Kullanıcı A, Kullanıcı B'ye bir dosyaya erişim izni verdiği zaman. Bu örnekte, A Kullanıcısı, hareket  *eden kullanıcı ve*  B Kullanıcısı da hedef  *kullanıcıdır*. Eylemli SharePoint şemasında, eyleme sahip kullanıcının eylemi yalnızca dosyanın kendisini etkiler. Kullanıcı A dosyası açtığında, **FileAccessed** olayında gereken tek bilgi, işlemden geçen kullanıcıdır. Bu farkı ele almak için, paylaşım olayları hakkında daha fazla bilgi *yakalayan SharePoint* Paylaşımı şeması olarak adlandırılan ayrı bir şema vardır. Bu, yöneticilerin kaynağı kimin paylaştığını ve kaynağın paylaşılıyor olan kullanıcıyla ilgili görünürlük sağlar. 
  
Paylaşım şeması, paylaşım olaylarıyla ilgili denetim kaydında iki ek alan sağlar: 
  
- **TargetUserOrGroupType:** Hedef kullanıcının veya grubun Üye, Konuk, SharePointGroup, SecurityGroup veya İş Ortağı olup olmadığını tanımlar.

- **TargetUserOrGroupName:** Kaynağın paylaşıldı olduğu hedef kullanıcı veya grubun UPN'lerini veya adını depolar (önceki örnekte Kullanıcı B). 

Bu iki alan, Kullanıcı, İşlem ve Tarih gibi denetim günlüğü şemasının diğer özelliklerine ek olarak, hangi kullanıcının hangi kaynağı kim ve ne zaman  paylaştığıyla ilgili  tüm *bilgileri* *sağlar*. 
  
Paylaşım hikayesi için önemli olan başka bir şema özelliği daha vardır. Denetim günlüğü arama sonuçlarını dışarı aktarsanız, **dışarı aktaran** CSV dosyasındaki Denetim Verileri sütununda paylaşım olaylarıyla ilgili bilgiler depolar. Örneğin, bir kullanıcı siteyi başka bir kullanıcıyla paylaştığında, bu  işler, hedef kullanıcı bir Kullanıcı Grubu'SharePoint  işler. **Denetim Verileri sütunu**, yöneticilere bağlam sağlamak için bu bilgileri yakalar. Denetim [Verileri sütunundaki](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) bilgileri ayrıştırma yönergeleri için 2. **Adıma** bakın.

## <a name="sharepoint-sharing-events"></a>SharePoint paylaşma hakkında

Paylaşım, bir kullanıcı (uygun kullanıcı) *kaynağı başka bir* kullanıcıyla (hedef kullanıcı) paylaşmak istediği *zaman tanımlanır* . Kaynağı dış kullanıcıyla (kuruluş dışından olan ve kuruluşun Azure Active Directory'sinde konuk hesabı olmayan kullanıcı) paylaşmayla ilgili denetim kayıtları, denetim günlüğüne kaydedilen aşağıdaki olaylar tarafından tanımlanır:

- **SharingInvitationCreated:** Bir dış kullanıcıyla (büyük olasılıkla site) kaynağı paylaşmayı deneen bir kullanıcı. Bunun sonucunda, hedef kullanıcıya dış paylaşım daveti gönderilir. Bu noktada kaynağa erişim ve verilmedi.

- **SharingInvitationAccepted:** Dış kullanıcı, paylaşan kullanıcı tarafından gönderilen paylaşım davetini kabul etmiş ve artık kaynağa erişim iznine sahip.

- **AnonymousLinkCreated:** Kaynak için anonim bağlantı ("Herkes" bağlantısı olarak da adlandırılan) oluşturulur. Anonim bağlantı oluşturula ve kopyalana kadar, anonim bağlantı içeren tüm belgenin hedef kullanıcıyla paylaşılıyor olduğu kabul edilebilir.

- **AnonymousLinkUsed:** Adın da anlaşılacağı gibi, kaynağa erişmek için anonim bir bağlantı kullanılırken bu olay günlüğe kaydedilir. 

- **SecureLinkCreated:** Bir kullanıcı, kaynağı belirli bir kişi ile paylaşmak için bir "belirli kişiler bağlantısı" oluşturdu. Bu hedef kullanıcı, kurum dışından bir kullanıcı olabilir. Kaynağın paylaşıldı olduğu kişi **AddedToSecureLink olayın denetim kaydında** tanımlanır. Bu iki olay için zaman damgaları neredeyse birbirinin aynısı olur.

- **AddedToSecureLink:** Belirli bir kişiler bağlantısına kullanıcı eklendi. Bu olayda, ilgili belirli kişiler bağlantısına eklenen kullanıcıları tanımlamak için **TargetUserOrGroupName** alanını kullanın. Bu hedef kullanıcı, kurum dışından bir kullanıcı olabilir.

## <a name="sharing-auditing-work-flow"></a>Denetim iş akışını paylaşma
  
Bir kullanıcı (sorumlu kullanıcı) kaynağı başka bir kullanıcıyla (hedef kullanıcı) paylaşmak isterse, önce SharePoint (veya OneDrive İş) hedef kullanıcının e-posta adresinin kuruluşun dizininde yer alan bir kullanıcı hesabıyla ilişkilendirilmiş olup olduğunu denetler. Hedef kullanıcı dizinde ise (ve buna karşılık gelen bir konuk kullanıcı hesabı varsa), SharePoint şunları yapar:
  
-  Hedef kullanıcıyı uygun kullanıcı grubuna ekleyerek kaynak üzerinde hemen hedef kullanıcı izinlerini atar ve **addedToGroup SharePoint günlüğe** kaydeder. 
    
- Hedef kullanıcının e-posta adresine bir paylaşım bildirimi gönderir.
    
- Bir **SharingSet olayı günlüklerini** günlüğe kaydeder. Bu olay, Paylaşım ve denetim günlüğü arama aracının etkinlikler seçicisinde erişim isteği etkinlikleri altında  "Paylaşılan dosya, klasör veya site" kolay bir adına sahip. 1. Adım'daki [ekran görüntüsüne bakın](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Hedef kullanıcının kullanıcı hesabı dizinde değilse, SharePoint şunları yapar: 
    
   - Kaynağın nasıl paylaşıldıklarına bağlı olarak, aşağıdaki olaylardan birini günlüğe kaydeder:
   
      - **AnonymousLinkCreated**
   
      - **SecureLinkCreated**
   
      - **AddedToSecureLink** 

      - **SharingInvitationCreated** (bu etkinlik yalnızca paylaşılan kaynak bir site olduğunda günlüğe kaydedilir)
    
   - Hedef kullanıcı gönderilen paylaşım davetini kabul ettiklerinde (davetteki bağlantıya tıklayarak), SharePoint bir **SharingInvitationAccepted** etkinliği kaydeder ve kaynağa erişmek için hedef kullanıcı izinlerini atar. Hedef kullanıcıya anonim bağlantı gönderilirse, hedef kullanıcı kaynağa erişmek için bağlantıyı kullandıktan sonra **AnonymousLinkUsed** olayı günlüğe kaydedilir. Güvenli bağlantılar için, dış **kullanıcı kaynağa** erişmek için bağlantıyı kullandığında FileAccessed olayı günlüğe kaydedilir.

Hedef kullanıcı hakkında, davette kullanıcının kimliği ve daveti kabul eden kullanıcı gibi ek bilgiler de günlüğe kaydedilir. Bazı durumlarda, bu kullanıcılar (veya e-posta adresleri) farklı olabilir. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Dış kullanıcılarla paylaşılan kaynakları tanımlama

Yöneticiler için yaygın bir gereksinim, kuruluş dışındaki kullanıcılarla paylaşılan tüm kaynakların listesini oluşturmaktır. Yöneticiler bu listeyi Office 365 denetim kullanarak oluşturabilirsiniz. Şöyle yapılır:
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>1. Adım: Paylaşım olaylarını arama ve sonuçları bir CSV dosyasına aktarma

İlk adım, denetim günlüğünde paylaşım olayları için arama yapmaktır. Denetim günlüğünde arama hakkında daha fazla bilgi (gerekli izinler dahil) için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)
  
1. <https://compliance.microsoft.com> adresine gidin.

2. İş veya okul hesabınızla oturum açın.

3. Denetim bölmesinin sol Microsoft 365 uyumluluk merkezi'a **tıklayın**.

    **Denetim sayfası** görüntülenir.

4. **Etkinlikler'in altında** Paylaşım **ve erişim isteği etkinlikleri'ne** tıklar ve paylaşımla ilgili olayları arayabilirsiniz. 

    ![Etkinlikler'in altında Paylaşım ve erişim isteği etkinlikleri'ne seçin.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Bir tarih ve saat aralığına seçerek, o dönem içinde 4 kez 24 saat gibi paylaşım olaylarını bulabilirsiniz. 

6. **Arama'yı** çalıştırmak için Ara'ya tıklayın. 

7. Aramanın çalışması tamamlandığında ve sonuçlar görüntülendiğinde, Sonuçları dışarı aktar **Tüm sonuçları** **indir'e**\> tıklayın.

    Dışarı aktarma seçeneğini kullandıktan sonra, pencerenin altındaki bir ileti CSV dosyasını açmanızı veya kaydetmenizi ister.

8. Farklı **Kaydet'e**  \> tıklayın ve CSV dosyasını yerel bilgisayarınızdan bir klasöre kaydedin. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>2. Adım: Dışarı aktaran denetim günlüğünü biçimlendirmek için PowerQuery Düzenleyicisi'ni kullanma

Sonraki adım, Excel'daki Power Query Düzenleyicisi'nde JSON dönüştürme özelliğini kullanarak Denetim Verileri sütunundaki her özelliği (çok özellikli bir  JSON nesneden oluşur) kendi sütununa bölmektir. Bu, paylaşımla ilgili kayıtları görüntülemek için sütunları filtrelemenizi sağlar

Adım adım yönergeler için, Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme'nin "2. Adım: Power Query Düzenleyicisi'ni kullanarak dışarı aktarılan denetim günlüğünü [biçimlendirme" makalesinde yer alan](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor) ".

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>3. Adım: Dış kullanıcılarla paylaşılan kaynaklar için CSV dosyasına filtre uygulama

Sonraki adım, bu paylaşım olayları bölümünde daha önce açıklanan, paylaşımla ilgili farklı [SharePoint filtrelemektir](#sharepoint-sharing-events). Alternatif olarak, **TargetUserOrGroupType** sütununu filtre kullanarak bu özelliğin değeri Konuk olan tüm kayıtları **görüntüebilirsiniz**. 

Önceki adımda verilen yönergeleri izleyerek PowerQuery düzenleyicisini kullanarak CSV dosyasını hazırlamak için şunları yapın:
    
1. 2. Excel'da oluşturduğunuz yeni dosyanın adını açın. 

2. Giriş sekmesinde **,** Filtreyi **Sırala'& ve** filtre'ye **tıklayın**.
    
3. İşlemler **sütunundaki &** Filtreyi Sırala açılan listesinde, tüm  seçimleri silin, ardından aşağıdaki paylaşımla ilgili olaylardan birini veya birden fazlasını seçin ve Tamam'a **tıklayın**.
 
   - **SharingInvitationCreated**
   
   - **AnonymousLinkCreated**
   
   - **SecureLinkCreated**
   
   - **AddedToSecureLink** 
    
    Excel, seçtiğiniz olayların satırlarını görüntüler.
    
4. **TargetUserOrGroupType adlı sütuna gidin ve** bu sütunu seçin. 
    
5. Sıralama Düzeni **& açılan** listesinde tüm seçimleri silin, **ardından TargetUserOrGroupType:Guest öğesini seçin ve Tamam'a** **tıklayın**.
    
    Artık Excel Paylaşım olaylarının satırlarını GÖRÜNTÜLER VE dış kullanıcılar **TargetUserOrGroupType:Guest** değeriyle tanım olduğundan hedef kullanıcının kuruluş dışından olduğu yeri görüntüler. 
  
> [!TIP]
> Görüntülenen denetim kayıtları için **ObjectId** sütunu hedef kullanıcıyla paylaşılan kaynağı tanımlar;  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`örneğin.
