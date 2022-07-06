---
title: eBulma çözüm serisi Veri taşması senaryosu - Arama ve temizleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Kuruluşunuzdaki bir veri sızıntısı olayını yönetmek ve yanıtlamak için eBulma ve arama araçlarını kullanın.
ms.openlocfilehash: b65d6057921d310c3e22e5494218271c7693c162
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630201"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>eBulma çözüm serisi: Veri taşması senaryosu - Arama ve temizleme

 **Veri taşması nedir ve neden önem vermelisiniz?** Veri taşması, gizli bir belgenin güvenilmeyen bir ortama yayımlanmasıdır. Bir veri taşması olayı algılandığında, dökülmenin boyutunu ve konumlarını hızla değerlendirmek, çevresindeki kullanıcı etkinliklerini incelemek ve ardından taşan verileri sistemden kalıcı olarak temizlemek önemlidir.
  
## <a name="data-spillage-scenario"></a>Veri taşması senaryosu

Contoso'da baş bilgi güvenlik görevlisisiniz. Bir çalışanın bilmeden çok gizli bir belgeyi e-posta yoluyla birden çok kişiyle paylaştığı veri taşması durumu size bildirilir. Bu belgeyi kimlerin dahili ve harici olarak aldığını hızla değerlendirmek istiyorsunuz. Tanımlandıktan sonra, incelemeleri için olay bulgularını diğer araştırmacılarla paylaşmak ve ardından verileri Office 365 kalıcı olarak kaldırmak istiyorsunuz. Araştırma tamamlandıktan sonra, gelecekte başvurmak üzere kalıcı kaldırma kanıtını ve diğer olay ayrıntılarını içeren bir rapor oluşturmak istiyorsunuz.
  
### <a name="scope-of-this-article"></a>Bu makalenin kapsamı

Bu belge, erişilebilir veya kurtarılabilir olmaması için iletiyi Microsoft 365'ten kalıcı olarak kaldırma yönergelerinin listesini sağlar. Bir iletiyi silmek ve silinmiş öğe saklama süresi dolana kadar kurtarılabilir hale getirmek için bkz. [Kuruluşunuzda e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Veri taşması olaylarını yönetmek için iş akışı

Veri taşması olayının nasıl yönetileceğini aşağıda bulabilirsiniz:

![Veri taşması olaylarını yönetmek için 8 aşamalı iş akışı.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(İsteğe bağlı) 1. Adım: Servis talebine kimlerin erişebileceğini yönetme ve uyumluluk sınırlarını ayarlama](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[2. Adım: eBulma olayı oluşturma](#step-2-create-an-ediscovery-case)<br/>
[3. Adım: Taşan verileri arama](#step-3-search-for-the-spilled-data)<br/>
[4. Adım: Olay bulgularını gözden geçirme ve doğrulama](#step-4-review-and-validate-case-findings)<br/>
[5. Adım: Taşan verilerin nasıl paylaşıldığını denetlemek için ileti izleme günlüğünü kullanma](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[6. Adım: Posta kutularını hazırlama](#step-6-prepare-the-mailboxes)<br/>
[7. Adım: Taşan verileri kalıcı olarak silme](#step-7-permanently-delete-the-spilled-data)<br/>
[8. Adım: Doğrulama, silme kanıtı sağlama ve denetim](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Başlamadan önce bilmeniz gerekenler

- Bu makalede açıklanan veri taşması iş akışı, Microsoft Teams'de sohbet iletilerini silmez. Teams sohbet iletilerini aramak ve silmek için bkz. [Teams'de sohbet iletilerini arama ve temizleme](search-and-delete-Teams-chat-messages.md).

- Bir posta kutusu beklemede olduğunda, saklama süresi dolana veya saklama serbest bırakılana kadar silinmiş bir ileti Kurtarılabilir Öğeler klasöründe kalır. [6. adım](#step-6-prepare-the-mailboxes) , posta kutularından ayrı tutmanın nasıl kaldırılacağını açıklar. Saklamayı kaldırmadan önce kayıt yönetiminize veya hukuk departmanlarınıza danışın. Kuruluşunuzun beklemedeki posta kutusunun mı yoksa veri taşması olayının mı öncelikli olduğunu tanımlayan bir ilkesi olabilir. 

- Veri taşması araştırmacısının servis talebine kimlerin erişebileceğini arayıp yönetebileceği kullanıcı posta kutularını denetlemek için uyumluluk sınırları ayarlayabilir ve [1. Adım'da](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries) açıklanan özel bir rol grubu oluşturabilirsiniz. Bunu yapmak için Kuruluş Yönetimi rol grubunun bir üyesi olmanız veya rol yönetimi rolüne atanmış olmanız gerekir. Siz veya kuruluşunuzdaki bir yönetici uyumluluk sınırlarını zaten ayarladıysanız, 1. Adımı atlayabilirsiniz.

- Servis talebi oluşturmak için eBulma Yöneticisi rol grubunun üyesi olmanız veya Servis Talebi Yönetimi rolüne atanmış özel bir rol grubunun üyesi olmanız gerekir. Üye değilseniz, microsoft 365 yöneticisinden [sizi eBulma yöneticisi rol grubuna eklemesini](assign-ediscovery-permissions.md) isteyin.

- İçerik Araması oluşturmak ve çalıştırmak için eBulma Yöneticisi rol grubunun üyesi olmanız veya Uyumluluk Araması yönetim rolüne atanmış olmanız gerekir. İletileri silmek için Kuruluş Yönetimi rol grubunun üyesi olmanız veya Arama ve Temizleme yönetimi rolüne sahip olmanız gerekir. Rol grubuna kullanıcı ekleme hakkında bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).

- 8. Adım'da denetim günlüğü eBulma etkinliklerinde arama yapmak için, kuruluşunuzda denetimin açık olması gerekir. Son 90 gün içinde gerçekleştirilen etkinlikleri arayabilirsiniz. Denetimi etkinleştirme ve kullanma hakkında daha fazla bilgi edinmek için 8. [Adım'daki Veri taşması araştırma işlemini](#auditing-the-data-spillage-investigation-process) denetleme bölümüne bakın.

## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(İsteğe bağlı) 1. Adım: Servis talebine kimlerin erişebileceğini yönetme ve uyumluluk sınırlarını ayarlama

Kuruluş uygulamanıza bağlı olarak, veri taşması olayını araştırmak ve uyumluluk sınırlarını ayarlamak için kullanılan eBulma olayına kimlerin erişebileceğini denetlemeniz gerekir. Bunu yapmanın en kolay yolu, araştırmacıları Microsoft Purview uyumluluk portalı mevcut bir rol grubunun üyesi olarak eklemek ve ardından rol grubunu eBulma olayının bir üyesi olarak eklemektir. Yerleşik eBulma rol grupları ve eBulma olayına üye ekleme hakkında bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).
  
Ayrıca, kuruluş gereksinimlerinize uygun yeni bir rol grubu da oluşturabilirsiniz. Örneğin, kuruluştaki bir grup veri taşması araştırmacısının tüm veri taşması olaylarına erişmesini ve bu olaylarda işbirliği yapmalarını isteyebilirsiniz. Bunu yapmak için bir "Veri Taşması Araştırmacısı" rol grubu oluşturabilir, uygun rolleri (Dışarı Aktarma, RMS Şifre Çözme, Gözden Geçirme, Önizleme, Uyumluluk Araması ve Olay Yönetimi) atayabilir, veri taşması araştırmacılarını rol grubuna ekleyebilir ve ardından rol grubunu veri taşması eBulma olayının bir üyesi olarak eKleyebilirsiniz. Bunun nasıl yapılacağını açıklayan ayrıntılı yönergeler için bkz. [Office 365'da eBulma araştırmaları için uyumluluk sınırlarını ayarlama](set-up-compliance-boundaries.md). 
  
## <a name="step-2-create-an-ediscovery-case"></a>2. Adım: eBulma olayı oluşturma

eBulma olayı, veri taşması araştırmanızı yönetmek için etkili bir yol sağlar. 1. Adımda oluşturduğunuz rol grubuna üye ekleyebilir, rol grubunu yeni bir eBulma olayının üyesi olarak ekleyebilir, taşan verileri bulmak için yinelemeli aramalar yapabilir, paylaşacak bir raporu dışarı aktarabilir, servis talebinin durumunu izleyebilir ve gerekirse servis talebinin ayrıntılarına geri bakabilirsiniz. Veri taşması olayları için kullanılan eBulma olayları için bir adlandırma kuralı oluşturmayı göz önünde bulundurun ve gerekirse gelecekte bulup başvurabilmeniz için olay adı ve açıklamasında olabildiğince fazla bilgi sağlayın.
  
Yeni bir servis talebi oluşturmak için güvenlik ve uyumluluk merkezinde eBulma özelliğini kullanabilirsiniz. [eKeşif kullanmaya başlama (Standart)](get-started-core-ediscovery.md#step-3-create-a-ediscovery-standard-case) bölümünde "Yeni servis talebi oluşturma" konusuna bakın.
  
## <a name="step-3-search-for-the-spilled-data"></a>3. Adım: Taşan verileri arama

Artık bir servis talebi ve yönetilen erişim oluşturduğunuza göre, taşan verileri bulmak ve taşan verileri içeren posta kutularını tanımlamak üzere yinelemeli olarak arama yapmak için servis talebini kullanabilirsiniz. [7. Adımda](#step-7-permanently-delete-the-spilled-data) aynı iletileri silmek için e-posta iletilerini bulmak için kullandığınız arama sorgusunu kullanacaksınız.
  
eBulma servis talebiyle ilişkilendirilmiş bir içerik araması oluşturmak için bkz. [eBulma (Standart) durumunda içerik arama](search-for-content-in-core-ediscovery.md).
  
> [!IMPORTANT]
> Arama sorgusunda kullandığınız anahtar sözcükler, aradığınız gerçek taşan verileri içerebilir. Örneğin, sosyal güvenlik numarası içeren belgeleri arıyorsanız ve bunu arama anahtar sözcüğü olarak kullanıyorsanız, daha fazla taşmasını önlemek için sorguyu daha sonra silmeniz gerekir. Bkz. 8. Adımda [arama sorgusunu silme](#deleting-the-search-query) .
  
## <a name="step-4-review-and-validate-case-findings"></a>4. Adım: Olay bulgularını gözden geçirme ve doğrulama

İçerik araması oluşturduktan sonra, arama sonuçlarını gözden geçirip doğrulamanız ve bunların yalnızca silinmesi gereken e-posta iletilerinden oluştuğundan emin olmanız gerekir. İçerik aramasında, daha fazla veri taşmasını önlemek için arama sonuçlarını dışarı aktarmadan 1.000 e-posta iletisinin rastgele örneklemesini önizleyebilirsiniz. Önizleme sınırlamaları hakkında daha fazla bilgiyi [İçerik Arama Sınırları'nda](limits-for-content-search.md) okuyabilirsiniz.
  
Gözden geçirebileceğiniz posta kutusu başına 1.000'den fazla posta kutunuz veya 100'den fazla e-posta iletiniz varsa, tarih aralığı veya gönderen/alıcı gibi ek anahtar sözcükler veya koşullar kullanarak ilk aramayı birden çok aramaya bölebilir ve her aramanın sonuçlarını tek tek gözden geçirebilirsiniz. [7. Adımda](#step-7-permanently-delete-the-spilled-data) iletileri silerken kullanılacak tüm arama sorgularını not aldığınızdan emin olun.

Dökülen veriler içeren bir e-posta iletisi bulduğunuzda, iletinin alıcılarını denetledikten sonra iletinin dışarıdan paylaşılıp paylaşılmadığını belirleyin. İletiyi daha fazla izlemek için, ileti izleme günlüklerini kullanabilmeniz için gönderen bilgilerini ve tarih aralıklarını toplayabilirsiniz. Bu işlem [5. Adım'da](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared) açıklanmıştır.

Arama sonuçlarını doğruladıktan sonra, bulgularınızı ikincil bir inceleme için başkalarıyla paylaşmak isteyebilirsiniz. 1. Adımda servis talebine atadığınız kişiler hem eBulma hem de Microsoft Purview eKeşif (Premium) içindeki servis talebi içeriğini gözden geçirebilir ve olay bulgularını onaylayabilir. Gerçek içeriği dışarı aktarmadan da rapor oluşturabilirsiniz. Bu raporu, [8. Adım'da](#step-8-verify-provide-a-proof-of-deletion-and-audit) açıklanan silme kanıtı olarak da kullanabilirsiniz.
  
 **İstatistiksel rapor oluşturmak için:**
  
1. eBulma servis talebinin **Arama** sayfasına gidin ve rapor oluşturmak istediğiniz aramaya tıklayın. 
    
2. Açılır sayfada **Diğer > Raporu dışarı aktar'a** tıklayın.
 
      Raporu dışarı aktar sayfası görüntülenir.

    ![Aramayı seçin ve açılır sayfada Diğer > Raporu dışarı aktar'a tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. **Tanınmayan biçime sahip, şifrelenen veya başka nedenlerle dizine eklenemeyen öğeler de dahil olmak üzere Tüm öğeler'i** seçin ve rapor **oluştur'a** tıklayın.

4. eBulma durumunda dışarı aktarma işlerinin listesini görüntülemek için **Dışarı Aktar'a** tıklayın. Oluşturduğunuz dışarı aktarma işini görüntülemek üzere listeyi güncelleştirmek için **Yenile'ye** tıklamanız gerekebilir.

5. Dışarı aktarma işine tıklayın ve açılır sayfada Raporu **indir'e** tıklayın.
 
    ![Dışarı Aktar sayfasında dışarı aktarmaya ve ardından "Raporu indir"e tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

**Dışarı Aktarma Özeti** raporu, sonuçlarla birlikte bulunan konum sayısını ve arama sonuçlarının boyutunu içerir. Silme işleminden sonra oluşturulan raporla karşılaştırmak ve silme kanıtı olarak sağlamak için bunu kullanabilirsiniz. **Sonuçlar** raporu, e-posta okunduysa konu, gönderen, alıcılar, her iletinin tarihleri ve boyutu gibi arama sonuçlarının daha ayrıntılı bir özetini içerir. Bu rapordaki ayrıntılardan herhangi biri gerçek dökülen verileri içeriyorsa, araştırma tamamlandığında Results.csv dosyasını kalıcı olarak sildiğinizden emin olun.

Raporları dışarı aktarma hakkında daha fazla bilgi için bkz. [İçerik Arama raporunu dışarı aktarma](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>5. Adım: Taşan verilerin nasıl paylaşıldığını denetlemek için ileti izleme günlüğünü kullanma

Taşan veri içeren e-postanın paylaşılıp paylaşılmadığını daha fazla araştırmak için, isteğe bağlı olarak ileti izleme günlüklerini gönderen bilgileriyle ve 4. Adımda topladığınız tarih aralığı bilgileriyle sorgulayabilirsiniz. İleti izleme için bekletme süresi, gerçek zamanlı veriler için 30 gündür ve geçmiş veriler için 90 gündür.
  
Güvenlik ve uyumluluk merkezinde İleti izleme özelliğini veya powershell Exchange Online ilgili cmdlet'leri kullanabilirsiniz. İleti izlemenin döndürülen verilerin eksiksizliği konusunda tam garanti sağlamadığını unutmayın. İleti izleme kullanma hakkında daha fazla bilgi için bkz: 
  
- [Güvenlik & Uyumluluk Merkezi'nde ileti izleme](../security/office-365-security/message-trace-scc.md)
    
- [Güvenlik & Uyumluluk Merkezi'nde Yeni İleti İzleme](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>6. Adım: Posta kutularını hazırlama

Arama sonuçlarının yalnızca silinmesi gereken iletileri içerdiğini gözden geçirip doğruladıktan sonra, aktarılan verileri sildiğinizde 7. Adımda kullanmak üzere etkilenen posta kutularının e-posta adreslerinin listesini toplamanız gerekir. Ayrıca, dökülen verileri içeren posta kutularında tek öğe kurtarmanın etkinleştirilip etkinleştirilmediğine veya bu posta kutularından herhangi birinin beklemede olmasına bağlı olarak e-posta iletilerini kalıcı olarak silebilmeniz için önce posta kutularını hazırlamanız gerekebilir.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Taşan veri içeren posta kutularının adreslerinin listesini alma

Dökülen verilerle posta kutularının e-posta adreslerinin listesini toplamanın iki yolu vardır.

**1. Seçenek: Taşan veri içeren posta kutularının adreslerinin listesini alma**

1. eBulma servis talebini açın, **Arama** sayfasına gidin ve uygun içerik aramasını seçin. 
    
2. Açılır sayfada **Sonuçları görüntüle'ye** tıklayın.
    
3. **Tek tek sonuçlar** açılan listesinde **İstatistikleri ara'ya** tıklayın.
    
4. **Tür** açılan listesinde **Üst konumlar'a** tıklayın.
    
    ![Arama istatistiklerinin Üst konumlar sayfasında arama sonuçlarını içeren posta kutularının listesini alın.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Arama sonuçlarını içeren posta kutularının listesi görüntülenir. Her posta kutusunda arama sorgusuyla eşleşen öğelerin sayısı da görüntülenir.
    
5. Listedeki bilgileri kopyalayıp bir dosyaya kaydedin veya bilgileri CSV dosyasına indirmek için **İndir'e** tıklayın. 
    
**2. Seçenek: Dışarı aktarma raporundan posta kutusu konumlarını alma**

[4. Adımda](#step-4-review-and-validate-case-findings) indirdiğiniz Dışarı Aktarma Özeti raporunu açın. Raporun ilk sütununda, her posta kutusunun e-posta adresi **Konumlar** altında listelenir.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Taşan verileri silebilmeniz için posta kutularını hazırlama

Tek öğeli kurtarma etkinleştirilirse veya bir posta kutusu beklemeye alınırsa, kalıcı olarak silinmiş (temizlenmiş) bir ileti Kurtarılabilir Öğeler klasöründe tutulur. Bu nedenle, dökülen verileri temizlemeden önce mevcut posta kutusu yapılandırmalarını denetlemeniz ve tek öğe kurtarmayı devre dışı bırakmanız ve bekletme veya saklama ilkesini kaldırmanız gerekir. Bir kerede bir posta kutusu hazırlayabileceğinizi ve aynı komutu farklı posta kutularında çalıştırabileceğinizi veya aynı anda birden çok posta kutusu hazırlamak için bir PowerShell betiği oluşturabileceğinizi unutmayın.

- Tek öğe kurtarmanın etkinleştirilip etkinleştirilmediğini veya posta kutusunun beklemeye alınıp alınmadığını veya bir bekletme ilkesine atanıp atanmadığını denetleme yönergeleri için [, bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki Öğeleri silme](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) başlığı altındaki "1. Adım: Posta kutusu hakkında bilgi toplama" konusuna bakın. 

- Tek öğe kurtarmayı devre dışı bırakma yönergeleri için [, bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme başlığı altındaki](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) "2. Adım: Posta kutusunu hazırlama" bölümüne bakın. 

- Posta kutusundan ayrı tutma veya bekletme ilkesini kaldırma yönergeleri için [, bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme başlığı altındaki](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) "3. Adım: Posta kutusundan tüm ayrı tutmaları kaldırma" bölümüne bakın. 

- Herhangi bir saklama türü kaldırıldıktan sonra posta kutusuna yerleştirilen gecikme saklamayı kaldırma hakkında yönergeler için [, Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki Öğeleri silme](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) başlığı altında yer alan "4. Adım: Posta kutusundan gecikme saklamayı kaldırma" konusuna bakın.

> [!IMPORTANT]
> Saklama veya saklama ilkesini kaldırmadan önce kayıt yönetiminize veya hukuk departmanlarınıza danışın. Kuruluşunuzun beklemedeki posta kutusunun mı yoksa veri taşması olayının mı öncelikli olduğunu tanımlayan bir ilkesi olabilir. 
  
Dökülen verilerin kalıcı olarak silindiğini doğruladıktan sonra posta kutusunu önceki yapılandırmalara geri döndürdüğünüzden emin olun. [7. Adım'daki](#step-7-permanently-delete-the-spilled-data) ayrıntılara bakın.

## <a name="step-7-permanently-delete-the-spilled-data"></a>7. Adım: Taşan verileri kalıcı olarak silme

6. Adımda topladığınız ve hazırladığınız posta kutusu konumlarını ve 3. Adımda oluşturulan ve iyileştirilmiş arama sorgusunu kullanarak, dökülen verileri içeren e-posta iletilerini bulmak için artık taşan verileri kalıcı olarak silebilirsiniz.  Daha önce açıklandığı gibi, iletileri silmek için Kuruluş Yönetimi rol grubunun üyesi olmanız veya arama ve temizleme yönetimi rolüne atanmış olmanız gerekir. Rol grubuna kullanıcı ekleme hakkında bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).

Dökülen iletileri silmek için bkz. [E-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).

Taşan verileri silerken aşağıdaki sınırları göz önünde bulundurun:

- Arama ve temizleme eylemi yaparak öğeleri silmek için kullanabileceğiniz en fazla posta kutusu sayısı 50.000'dir. 3. Adımda oluşturduğunuz arama 50.000'den fazla posta kutusunda arama yaparsanız temizleme eylemi başarısız olur. Tek bir aramada 50.000'den fazla posta kutusunda arama yapmak genellikle aramayı kuruluşunuzdaki tüm posta kutularını içerecek şekilde yapılandırdığınızda gerçekleşebilir. Bu kısıtlama, 50.000'den az posta kutusu arama sorgusuyla eşleşen öğeler içerdiğinde bile geçerlidir.

- Posta kutusu başına bir kerede en fazla 10 öğe kaldırılabilir. İletileri arama ve kaldırma özelliği bir olay yanıtı aracı olması amaçlandığından, bu sınır iletilerin posta kutularından hızla kaldırılmasına yardımcı olur. Bu özellik, kullanıcı posta kutularını temizlemeye yönelik değildir.

> [!IMPORTANT]
> eBulma (Premium) durumundaki bir gözden geçirme kümesindeki e-posta öğeleri bu makaledeki yordamlar kullanılarak silinemez. Bunun nedeni, bir gözden geçirme kümesindeki öğelerin canlı hizmetteki bir Azure Depolama konumunda kopyalanıp depolanan kopyaları olmasıdır. Bu, 3. Adımda oluşturduğunuz bir içerik araması tarafından döndürülmeyecekleri anlamına gelir. Gözden geçirme kümesindeki öğeleri silmek için, gözden geçirme kümesini içeren eBulma (Premium) servis talebini silmeniz gerekir. Daha fazla bilgi için bkz. [eBulma (Premium) servis talebini kapatma veya silme](close-or-delete-case.md).
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>8. Adım: Doğrulama, silme kanıtı sağlama ve denetim

Veri taşması olayını yönetmek için iş akışındaki son adım, dökülen verilerin eBulma olayına gidip hiçbir sonuç döndürülmediğini onaylamak için bu verileri silmek için kullanılan arama sorgusunu yeniden çalıştırarak posta kutusundan kalıcı olarak kaldırıldığını doğrulamaktır. Taşan verilerin kalıcı olarak kaldırıldığını onayladıktan sonra, bir raporu dışarı aktarabilir ve silme kanıtı olarak (özgün raporla birlikte) ekleyebilirsiniz. Daha sonra, gelecekte başvurmanız gerekirse dosyayı yeniden açmanızı sağlayacak [olan servis talebini kapatabilirsiniz](close-reopen-delete-core-ediscovery-cases.md) . Ayrıca, posta kutularını önceki durumlarına geri döndürebilir, dökülen verileri bulmak için kullanılan arama sorgusunu silebilir ve veri taşması olayını yönetirken gerçekleştirilen görevlerin denetim kayıtlarını arayabilirsiniz.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Posta kutularını önceki durumlarına geri döndürme

Aktarılan veriler silinmeden önce posta kutularını hazırlamak için 6. Adımda herhangi bir posta kutusu yapılandırmasını değiştirdiyseniz, bunları önceki durumlarına geri döndürmeniz gerekir. [Beklemedeki bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki Öğeleri silme](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state) bölümünde "6. Adım: Posta kutusunu önceki durumuna geri döndürme" bölümüne bakın.
  
### <a name="deleting-the-search-query"></a>Arama sorgusunu silme

3. Adımda oluşturduğunuz ve kullandığınız arama sorgusundaki anahtar sözcükler gerçek taşan verilerin bazılarını içeriyorsa, daha fazla veri taşmasını önlemek için arama sorgusunu silmeniz gerekir.
  
1. Güvenlik ve uyumluluk merkezinde eBulma servis talebini açın, **Arama** sayfasına gidin ve uygun içerik aramasını seçin.

2. Açılır sayfada **Sil'e** tıklayın.

    ![Aramayı seçin ve açılır sayfada Sil'e tıklayın.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Veri taşması araştırma işlemini denetleme

Araştırma sırasında gerçekleştirilen eBulma etkinlikleri için denetim günlüğünde arama yapabilirsiniz. Dökülen verileri silmek için 7. Adımda çalıştırdığınız **New-ComplianceSearchAction -Purge** komutunun denetim kayıtlarını döndürmek için denetim günlüğünde de arama yapabilirsiniz. Daha fazla bilgi için bkz.:

- [Denetim günlüğünde arama yapma](search-the-audit-log-in-security-and-compliance.md)

- [Denetim günlüğünde eKeşif etkinliklerini ara](search-for-ediscovery-activities-in-the-audit-log.md)
