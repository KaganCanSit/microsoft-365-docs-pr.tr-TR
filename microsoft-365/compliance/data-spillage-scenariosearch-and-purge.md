---
title: eBulma çözümü serisi Veri taşma senaryosu - Arama ve temizleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: eBulma ve arama araçlarını kullanarak, kurumda bir veri taşma olayı yönetmek ve buna yanıt verin.
ms.openlocfilehash: 98dbb4ec36b7fb8166732aa855eefe3db6c5bbdc
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449562"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>eBulma çözümü serisi: Veri taşma senaryosu - Arama ve temizleme

 **Veri taşma nedir ve neden önemli olmalı?** Verilerin taşma tarihi, gizli bir belgenin güvenilmeyen bir ortamda yayımlanmamış bir ortamda yayımlarıdır. Bir veri taşma olayı algılandığında, taşma yerinin boyutunu ve konumlarını hızla değerlendirmek, bunun çevresinde kullanıcı etkinliklerini incelemek ve sonra da dökülen verileri sistemden kalıcı olarak temizlemek önemlidir. 
  
## <a name="data-spillage-scenario"></a>Veri taşma senaryosu

Contoso'da müşteri adayı bilgileri güvenlik görevlisisiniz. Bir çalışanın bilinmeyen bir şekilde çok gizli bir belgeyi e-posta aracılığıyla birden çok kişi ile paylaştığı veri taşma durumu hakkında bilgi sahibisiniz. Bu belgeyi şirket içinde ve dışında kimlerin alan olduğunu hızla değerlendirmek istiyorsanız. Tanımlananda, olay bulgularını gözden geçirmesi gereken diğer olaylarla paylaşmak ve ardından verileri dosyadan kalıcı olarak kaldırmak Office 365. Araştırma tamamlandıktan sonra, bundan sonra herhangi bir başvuru için kalıcı olarak kaldırma kanıtı ve diğer olay ayrıntılarına sahip bir rapor oluşturmak istediğinize karar verirsiniz.
  
### <a name="scope-of-this-article"></a>Bu makalenin kapsamı

Bu belgede, erişilebilir veya kurtarılabilir olması için ileti posta Microsoft 365 kalıcı olarak nasıl kaldırılabilir yönergelerin listesi ve sağlar. İletiyi silmek ve silinmiş öğe bekletme süresi dolana kadar kurtarılabilir hale etmek için bkz. Kurumda e-posta iletilerini [arama ve silme](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Veri taşma olaylarını yönetmek için iş akışı

Veri taşma olayı şöyle yönetebilirsiniz:

![Veri taşma olaylarını yönetmek için 8 adımlı iş akışı.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(İsteğe bağlı) 1. Adım: Vakaya kimlerin eriş erişeni yönetme ve uyumluluk sınırları ayarlama](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[2. Adım: eBulma durumu oluşturma](#step-2-create-an-ediscovery-case)<br/>
[3. Adım: Taşan verileri arama](#step-3-search-for-the-spilled-data)<br/>
[4. Adım: Olay bulgularını gözden geçirme ve doğrulama](#step-4-review-and-validate-case-findings)<br/>
[5. Adım: İleti izleme günlüğünü kullanarak taşan verilerin nasıl paylaşılıyor olduğunu denetleme](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[6. Adım: Posta kutularını hazırlama](#step-6-prepare-the-mailboxes)<br/>
[7. Adım: Taşan verileri kalıcı olarak silme](#step-7-permanently-delete-the-spilled-data)<br/>
[8. Adım: Doğrulama, silme kanıtı sağlama ve denetim](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Başlamadan önce bilmek gerekenler

- Posta kutusu saklamaya devam edince, bekletme süresi dolana veya saklama süresi yayımlanana kadar, silinmiş bir ileti Kurtarılabilir Öğeler klasöründe kalır. [6](#step-6-prepare-the-mailboxes) . adım posta kutularından hold'i kaldırmayı açıklar. Tutmayı kaldırmadan önce kayıt yönetiminize veya hukuk departmanınıza sorun. Kuruluşta, posta kutusunun tutarak mı yoksa veri taşma olayıyla mı öncelikli olduğunu tanımlayan bir ilkesi olabilir. 
    
- Hangi kullanıcı posta kutularında veri taşma izinlerinin olduğunu kontrol etmek için, kimlerin bu vakaya erişebileceklerini arayabilir ve yönetebilir, uyumluluk sınırları oluşturabilir ve 1. Adımda açıklanan özel bir rol [grubu oluşturabilirsiniz](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries). Bunu yapmak için, Kuruluş Yönetimi rol grubunun bir üyesi olmak veya rol yönetimi rolüne atanmış olmak gerekir. Siz veya kuruluş yöneticiniz zaten uyumluluk sınırları ayarlamışsa, 1. Adımı atlayabilirsiniz.
    
- Vaka oluşturmak için, eBulma Yöneticisi rol grubunun üyesi veya Olay Yönetimi rolüne atanmış özel bir rol grubunun üyesi olmak gerekir. Üye değilseniz, grup yöneticisinden Microsoft 365 sizi [eBulma Yöneticisi rol grubuna eklemelerini sorun](assign-ediscovery-permissions.md).
    
- İçerik Arama oluşturmak ve çalıştırmak için, eBulma Yöneticisi rol grubunun bir üyesi olmalı veya Uyumluluk Arama yönetim rolüne atanmış olar. İletileri silmek için, Kuruluş Yönetimi rol grubunun bir üyesi olmalı veya Arama ve Temizleme yönetimi rolüne atanmışsınızdır. Rol grubuna kullanıcı ekleme hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).
    
- 8. Adımda denetim günlüğü eBulma etkinliklerini aramak için, denetimin organizasyonunız için açık olması gerekir. Son 90 gün içinde gerçekleştirilen etkinlikleri arayabilirsiniz. Denetimi etkinleştirme ve kullanma hakkında daha fazla bilgi edinmek için 8. Adım'da Veri taşma [soruşturması](#auditing-the-data-spillage-investigation-process) sürecini denetleme bölümüne bakın. 
    
## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(İsteğe bağlı) 1. Adım: Vakaya kimlerin eriş erişeni yönetme ve uyumluluk sınırları ayarlama

Kuruluş alıştırmanıza bağlı olarak, bir veri taşma olayında araştırma yapmak ve uyumluluk sınırları ayarlamak için kullanılan eBulma olayına kimlerin erişeni denetlemeniz gerekir. Bunu yapmanın en kolay yolu, belgelerde var olan bir rol grubunun üyeleri olarak Microsoft 365 uyumluluk merkezi sonra da rol grubunu eBulma durumuna üye olarak eklemektir. Yerleşik eBulma rol grupları ve eBulma durumuna üye ekleme hakkında bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).
  
Ayrıca, kurumsal ihtiyaçlarını karşılamak için yeni bir rol grubu da oluşturabilirsiniz. Örneğin, kuruluşun bir grup veri taşma davalarına erişmesi ve bu vakalar üzerinde işbirliği yapmalarını istiyor olabilirsiniz. Bunu yapmak için bir "Veri Taşma Nedenleri" rol grubu oluşturarak, uygun rolleri (Dışarı Aktar, RMS Şifre Çözme, Gözden Geçir, Önizleme, Uyumluluk Araması ve Olay Yönetimi), veri taşma nedenlerini rol grubuna ekleyerek ve ardından rol grubunu veri taşma eKbulma durumuna bir üye olarak ekleyerek bunuabilirsiniz. Bunun [nasıl konuyla ilgili ayrıntılı yönergeleri için Office 365'de eBulma](set-up-compliance-boundaries.md) soruşturmaları için uyumluluk sınırlarını ayarlama. 
  
## <a name="step-2-create-an-ediscovery-case"></a>2. Adım: eBulma durumu oluşturma

eBulma vakası, veri taşma araştırmanızı yönetmek için etkili bir yol sağlar. 1. Adımda oluşturduğunuz rol grubuna üyeler ekleyebilir, rol grubunu yeni bir eBulma durumunun üyesi olarak ekleyebilir, taşan verileri bulmak için iteratif aramalar gerçekleştirebilirsiniz, paylaşmak üzere bir raporu dışarı aktarabilirsiniz, vakanın durumunu izleyebilir ve gerekirse olay ayrıntılarına geri başvurabilirsiniz. Veri taşma olaylarında kullanılan eBulma olayları için bir adlandırma kuralı belirlemeyi düşünebilirsiniz ve gerekirse gelecekte bulup başvurabilirsiniz.
  
Yeni vaka oluşturmak için, güvenlik ve uyumluluk merkezinde eKbulma'ya bakarak bunu kullanabilirsiniz. Core [eDiscovery ile çalışmaya başlama'daki "Yeni vaka oluşturma" bölüme bakın](get-started-core-ediscovery.md#step-3-create-a-core-ediscovery-case).
  
## <a name="step-3-search-for-the-spilled-data"></a>3. Adım: Taşan verileri arama

Artık vakayı oluşturduğunuza ve yönetilen erişime sahip olduğunuuza göre, bu durumu kullanarak dökülen verileri bulmak ve taşan verileri içeren posta kutularını tanımlamak için yine de arayabilirsiniz. 7. Adımda, aynı iletileri silmek üzere e-posta iletilerini bulmak için de aynı arama [sorgusunu kullanırsınız](#step-7-permanently-delete-the-spilled-data).
  
eBulma durumuyla ilişkilendirilmiş bir içerik araması oluşturmak için bkz. [Çekirdek eBulma durumunda içerik arama](search-for-content-in-core-ediscovery.md).
  
> [!IMPORTANT]
> Arama sorgusunda kullanabileceğiniz anahtar sözcükler, aramakta olduğunuz gerçek taşmış verileri içerebilir. Örneğin, sosyal güvenlik numarası içeren belgeleri arıyorsanız ve bunu arama anahtar sözcüğü olarak kullanıyorsanız, daha fazla taşma önlemek için sorguyu silebilirsiniz. Bkz [. 8. Adım'da](#deleting-the-search-query) arama sorgusunu silme.
  
## <a name="step-4-review-and-validate-case-findings"></a>4. Adım: Olay bulgularını gözden geçirme ve doğrulama

İçerik arama oluşturduklardan sonra, arama sonuçlarını gözden geçirmeniz, doğrulamanız ve bunların yalnızca silinmesi gereken e-posta iletilerinden oluşan sonuçları doğrulamanız gerekir. İçerik aramalarında, daha fazla veri taşmaması için arama sonuçlarını dışarı aktarmadan 1000 e-posta iletilerinin rastgele bir örneklemesini ön görebilirsiniz. Önizleme sınırlamaları hakkında daha fazla bilgi için İçerik Arama [Sınırlamaları makalesini okuyabilirsiniz](limits-for-content-search.md).
  
Posta kutusu başına 1.000'den fazla posta kutunuz veya 100'den fazla e-posta iletiniz varsa, tarih aralığı veya gönderen/alıcı gibi başka anahtar sözcükler veya koşullar kullanarak ilk aramanızı birden çok aramaya bölebilirsiniz ve her aramanın sonuçlarını tek tek gözden geçirebilirsiniz. [Adım 7'de](#step-7-permanently-delete-the-spilled-data) iletileri silerken kullanmak üzere tüm arama sorgularını not edin.

Taşmış veriler içeren bir e-posta iletisi bulursanız, iletinin dışarıdan paylaşılıyor olup olmadığını belirlemek için iletinin alıcılarını kontrol edin. İletiyi daha fazla takip etmek için, gönderen bilgilerini ve tarih aralıklarını toplayabilirsiniz, böylece ileti izleme günlüklerini kullanabilirsiniz. Bu işlem [5. Adım'da açıklanmıştır](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared).

Arama sonuçlarını doğruladıktan sonra, ikincil bir gözden geçirme için bulgularınızı başkalarla paylaşmak iyi olabilir. 1. Adımda vakaya atadınız kişiler hem eBulma hem de Değerlendirme'de olay içeriğini gözden geçirip Advanced eDiscovery bulguları onaylar. Gerçek içeriği dışarı aktarmadan da rapor üretebilirsiniz. Aynı raporu, 8. Adımda açıklanan silme kanıtı olarak da [kullanabilirsiniz](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **İstatistiksel rapor oluşturmak için:**
  
1. **eBulma** durumunda Ara sayfasına gidin ve rapor oluşturmak istediğiniz aramaya tıklayın. 
    
2. Dışarı aktarma sayfasında, Raporu Dışarı **Aktarma'ya > tıklayın**.
 
      Raporu dışarı aktar sayfası görüntülenir.

    ![Arama'yı seçin ve sonra dışarı > Dışarı aktarma raporu'ne tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. **Tanınmayan, şifrelenmiş veya** başka nedenlerle dizine eklenmemiş olanlar da dahil olmak üzere Tüm öğeler'i seçin ve ardından Rapor oluştur'a **tıklayın**.

4. eBulma durumunda, dışarı aktarma **işlerinin listesini** görüntülemek için Dışarı Aktar'a tıklayın. Oluşturduğunuz dışarı aktarma işini **görüntülemek** için listeyi güncelleştirmek için Yenile'ye tıklamanız gerekir.

5. Dışarı aktarma işini tıklatın ve sonra çıkış **sayfasında** Raporu indir'i tıklatın.
 
    ![Dışarı Aktar sayfasında dışarı aktarmaya tıklayın ve sonra da "Raporu indir"e tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Dışarı **Aktarma** Özeti raporu, sonuçları içeren konumların sayısını ve arama sonuçlarının boyutunu içerir. Bunu, silme sonrasında oluşturulan raporla karşılaştırmak ve bir silme kanıtı olarak sağlamak için kullanabilirsiniz. Sonuçlar **raporu** , e-posta okundu ise konu, gönderen, alıcılar ve her iletinin boyutu gibi arama sonuçlarının daha ayrıntılı bir özetini içerir. Bu raporda yer alan ayrıntılardan herhangi biri gerçek olarak taşmış verileri içeriyorsa, inceleme tamamlandığında Results.csv dosyanın kalıcı olarak silin.

Raporları dışarı aktarma hakkında daha fazla bilgi için bkz [. İçerik Arama raporunu dışarı aktarma](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>5. Adım: İleti izleme günlüğünü kullanarak taşan verilerin nasıl paylaşılıyor olduğunu denetleme

Taşan veri içeren e-postanın paylaşıldığını daha fazla araştırmak için, isteğe bağlı olarak ileti izleme günlüklerini gönderen bilgileriyle ve 4. Adımda toplanmış olan tarih aralığı bilgileriyle sorguleyebilirsiniz. İleti izleme için bekletme süresi gerçek zamanlı veriler için 30 gündür ve geçmiş verileri için 90 gündür.
  
Güvenlik ve uyumluluk merkezinde İleti izleme kullanabilir veya Exchange Online PowerShell'de ilgili cmdlet'leri kullanabilirsiniz. İleti izlemenin, döndürülen verilerin eksiksizliği konusunda tam garantiler sun olmadığını unutmayın. İleti izleme kullanma hakkında daha fazla bilgi için bkz: 
  
- [Güvenlik ve Uyumluluk Merkezi'& izleme](../security/office-365-security/message-trace-scc.md)
    
- [Güvenlik ve Uyumluluk Merkezi'nde & İzleme](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>6. Adım: Posta kutularını hazırlama

Arama sonuçlarının yalnızca silinmesi gereken iletileri içerdiğini gözden geçirdikten ve doğruladikten sonra, taşan verileri silerken 7. Adımda kullanmak üzere, etkilenen posta kutularının e-posta adreslerinin listesini toplamanız gerekir. Ayrıca, tek öğe kurtarmanın taşmış verileri içeren posta kutularda etkin olup olmadığını ya da bu posta kutulardan herhangi birini tutma durumuna bağlı olarak e-posta iletilerini kalıcı olarak silmeden önce posta kutularını hazırlamanız gerekir.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Taşan veriler olan posta kutularının adreslerinin listesini alın

Taşan veriler içeren posta kutularının e-posta adreslerinin listesini toplamanın iki yolu vardır.

**1. Seçenek: Taşan verilere sahip posta kutularının adreslerinin listesini alma**

1. eBulma olaylarını açın, Arama **sayfasına gidin** ve uygun içerik aramalarını seçin. 
    
2. Uçarak çıkış sayfasında Sonuçları **görüntüle'ye tıklayın**.
    
3. Tek tek **sonuçlar açılan** listesinde, arama **istatistikleri'ne tıklayın**.
    
4. Tür **açılan listesinde** En üst konumlar'a **tıklayın**.
    
    ![Arama istatistiklerinin En üst konumlar sayfasında, arama sonuçlarını içeren posta kutularının listesini alın.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Arama sonuçlarını içeren posta kutularının listesi görüntülenir. Her posta kutusunda, arama sorgusuyla eşanan sayıda öğe de görüntülenir.
    
5. Listede bilgileri kopyalayın ve bir dosyaya kaydedin veya bilgileri CSV dosyasına **indirmek** için İndir'e tıklayın. 
    
**2. Seçenek: Dışarı aktarma raporundan posta kutusu konumlarını alma**

4. Adımda indirdiğiniz Dışarı Aktarma [Özeti raporunu açın](#step-4-review-and-validate-case-findings). Raporun ilk sütununda, her posta kutusunun e-posta adresi Konumlar altında **listelenir**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Üzerine taşan verileri silecek şekilde posta kutularını hazırlama

Tek öğe kurtarma etkinse veya posta kutusu yerine basılı durumda olursa, kalıcı olarak silinmiş (temizlenebilir) bir ileti Kurtarılabilir Öğeler klasöründe korunur. Bu nedenle, taşan verileri temizlemeden önce mevcut posta kutusu yapılandırmalarını denetlemeniz ve tek öğe kurtarmayı devre dışı bırakmanız ve saklama ya da bekletme ilkelerini kaldırmanız gerekir. Bir posta kutusunu bir defada hazır bulundurabilirsiniz ve sonra farklı posta kutularında aynı komutu çalıştırabilirsiniz veya birden çok posta kutusunu aynı anda hazırlamak için bir PowerShell betiği oluşturabilirsiniz.

- Tek öğe kurtarmanın etkinleştirildiğinden veya posta kutusunun saklamaya yerleştirildiğinden veya bir bekletme ilkesine atanma yönergeleri için Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme altında yer alan "1. Adım: Posta kutusu hakkında bilgi toplama" konularına bakın.[](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) 

- Tek öğe kurtarmayı devre dışı bırakma yönergeleri için Bulut tabanlı [](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme'nin "2. Adım: Posta kutusunu hazırlama" bağlantılarına bakın. 

- Posta kutusundan bekletme veya bekletme ilkesi kaldırma yönergeleri için Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme konusunda yer alan "3. Adım: Posta kutusundan tüm bekletmeleri kaldırma" konusuna bakın.[](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) 

- Herhangi bir tutma türü kaldırıldıktan sonra posta kutusuna yerleştirilen gecikmeyi kaldırma yönergeleri için [](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme'nin "4. Adım: Posta kutusundan gecikmeyi kaldırma" konularına bakın.

> [!IMPORTANT]
> Bekletme veya bekletme ilkesi kaldırmadan önce kayıt yönetiminize veya hukuk departmanınıza sorun. Kuruluşta, posta kutusunun veya veri taşma olaylarının öncelikli olup olmadığını tanımlayan bir ilke olabilir. 
  
Geçmiş verilerin kalıcı olarak silindikten sonra posta kutusunu önceki yapılandırmalara döndürmeyi lütfen kullanın. [7. Adım'daki ayrıntılara bakın](#step-7-permanently-delete-the-spilled-data).

## <a name="step-7-permanently-delete-the-spilled-data"></a>7. Adım: Taşan verileri kalıcı olarak silme

6. Adımda topladığı ve hazırladığı posta kutusu konumlarını ve 3. Adımda oluşturulan ve iyileştirilmiş arama sorgusunu kullanarak, taşan verileri içeren e-posta iletilerini bulmak için, artık dökülen verileri kalıcı olarak silebilirsiniz.  Daha önce de belirtildiği gibi, iletileri silmek için, Kuruluş Yönetimi rol grubunun bir üyesi olmalı veya Arama ve Temizleme yönetim rolüne atanmış olasınız. Rol grubuna kullanıcı ekleme hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).

Taşan iletileri silmek için bkz. [E-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).

Taşan verileri silerek aşağıdaki sınırlamaları göz dışı edin:

- Arama ve temizleme eylemi yaparak öğeleri silmek için kullanabileceğiniz bir aramadaki posta kutusu sayısı üst sayısı 50.000'tir. 3. Adımda oluştursanız bile, 50.000'den fazla posta kutusu aranıyorsa temizleme eylemi başarısız olur. Aramayı genelde, tüm posta kutularını içermesi için yapılandırıldığında, tek bir aramada 50.000'den fazla posta kutusunda arama yapmak gerekir. Bu kısıtlama, 50.000'den az posta kutusunun arama sorgusuyla eşleşmesi için bile geçerlidir.

- Aynı anda posta kutusu başına en fazla 10 öğe kaldırılabilir. İletileri arama ve kaldırma özelliği bir olay yanıt aracı olarak amaçlanan bir özellik olduğundan, bu sınır iletilerin posta kutularından hızla kaldırılmasını sağlamaya yardımcı olur. Bu özellik, kullanıcı posta kutularını temizlemeyi amaçlamadı.

> [!IMPORTANT]
> Bir çalışma e-postasında yer alan Advanced eDiscovery-posta öğeleri, bu makaledeki yordamlar kullanılarak silinemez. Bunun nedeni, gözden geçirme kümesinde yer alan öğelerin canlı hizmette yer alan ve Azure'da bir konumda kopyalanan ve depolanan öğelerin kopyaları Depolama vardır. Bu, 3. Adımda oluşturdukları içerik arama tarafından döndürül olmayacakları anlamına gelir. Gözden geçirme kümesinde öğeleri silmek için, gözden geçirme kümesi Advanced eDiscovery büyük/küçük harflerini silmeniz gerekir. Daha fazla bilgi için bkz[. Vakayı kapatma Advanced eDiscovery silme](close-or-delete-case.md).
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>8. Adım: Doğrulama, silme kanıtı sağlama ve denetim

veri taşması olayı yönetmek için iş akışının son adımı, eBulma olayına gidip hiçbir sonuç döndürülme olmadığını onaylamak için kullanılan arama sorgusunu yeniden çalıştırarak, taşan verilerin posta kutusundan kalıcı olarak kaldırılmış olduğunu doğrulamaktır. Taşan verilerin kalıcı olarak kaldırıldığı onayını verdikten sonra, bir raporu dışarı aktararak (özgün raporla birlikte) silme kanıtı olarak  dahilebilirsiniz. Daha sonra [bu vakayı](close-reopen-delete-core-ediscovery-cases.md) kapatarak, gelecekte başvurmak zorundaysanız yeniden açmanız için olanak sağlayacaktır. Buna ek olarak, posta kutularını önceki durumlarına geri döndürebilir, geçmiş verileri bulmak için kullanılan arama sorgusunu silebilir ve veri taşma olayı yönetiminde gerçekleştirilen görevlerin denetim kayıtlarını arayabilirsiniz.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Posta kutularını önceki durumlarına geri döndürme

Geçmiş veriler silinmeden önce posta kutularını hazırlamak için 6. adımda herhangi bir posta kutusu yapılandırmasını değiştirdiyseniz, bunları önceki durumlarına geri döndürmelisiniz. Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme'de "6. Adım: Posta kutusunu önceki durumuna geri döndürme" [kutusuna bakın](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state).
  
### <a name="deleting-the-search-query"></a>Arama sorgusunu silme

3. Adımda oluşturduğunuz ve 3. Adımda kullanılan arama sorgusunun anahtar sözcükleri gerçek taşmış verilerin hepsini içeriyorsa, daha fazla veri taşması önlemek için arama sorgusunu silebilirsiniz.
  
1. Güvenlik ve uyumluluk merkezinde eBulma olaylarını açın, Arama sayfasına **gidin** ve uygun içerik aramalarını seçin.

2. Uçarak çıkış sayfasında Sil'e **tıklayın**.

    ![Arama'yı seçin ve sonra da uçarak çıkış sayfasında Sil'e tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Veri taşma soruşturma sürecini denetleme

Denetim günlüğünde, araştırma sırasında gerçekleştirilen eBulma etkinlikleri için arama yapın. Ayrıca, 7. Adımda randedilen verileri silmek için, denetim günlüğünde arama yapın ve Yeni **Uyumluluk AramaAction -Temizleme** komutunun denetim kayıtlarını geri getirebilirsiniz. Daha fazla bilgi için bkz.:

- [Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md)

- [Denetim günlüğünde eBulma etkinliklerini arama](search-for-ediscovery-activities-in-the-audit-log.md)
