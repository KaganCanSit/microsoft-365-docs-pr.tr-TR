---
title: Denetim günlüğünde eKeşif etkinliklerini ara
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 67cc7f42-a53d-4751-b929-6005c80798f7
description: Kullanıcılara eBulma izinleri atanan kullanıcılar Microsoft Purview uyumluluk portalında İçerik arama, eBulma (Standart) ve eBulma (Premium) görevlerini gerçekleştirdiğinde hangi olayların günlüğe kaydedileceklerini öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 519347ed8f074fc15c8618f6ceb84159314c5915
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941841"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Denetim günlüğünde eKeşif etkinliklerini ara

Microsoft Purview uyumluluk portalında veya ilgili PowerShell cmdlet'leri çalıştırılarak gerçekleştirilen İçerik Arama ve eBulma ile ilgili etkinlikler (Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium)) için denetim günlüğüne kaydedilir. Yöneticiler veya eBulma yöneticileri (veya eBulma izinleri atanmış herhangi bir kullanıcı) uyumluluk portalında aşağıdaki İçerik Arama ve eBulma (Standart) görevlerini gerçekleştirdiğinde olaylar günlüğe kaydedilir:
  
- Çekirdek ve eBulma (Premium) servis taleplerini oluşturma ve yönetme

- İçerik aramalarını oluşturma, başlatma ve düzenleme

- Arama sonuçlarını önizleme, dışarı aktarma ve silme gibi arama eylemleri gerçekleştirme

- eBulma'da koruyucuları ve gözden geçirme kümelerini yönetme (Premium)

- İçerik araması için izin filtrelemeyi yapılandırma

- eBulma Yöneticisi rolünü yönetme
  
Denetim günlüğünde arama yapma, gerekli izinler ve arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz. [Uyumluluk portalında denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>eBulma etkinliklerini arama ve görüntüleme

Şu anda, denetim günlüğünde eBulma etkinliklerini görüntülemek için birkaç özel işlem yapmanız gerekir. Şöyle yapılır:
  
1. <https://compliance.microsoft.com> adresine gidin ve iş veya okul hesabınızı kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Denetim'e** tıklayın.

3. **Etkinlikler** açılan listesinde, **eBulma etkinlikleri** veya **eBulma (Premium) etkinlikleri** altında, aranacak bir veya daha fazla etkinliğe tıklayın.

    > [!NOTE]
    > **Etkinlikler** açılan listesi, cmdlet denetim günlüğünden kayıt döndürecek **eBulma cmdlet etkinlikleri** adlı bir etkinlik grubunu da içerir.
  
4. Bu dönemde gerçekleşen eBulma olaylarını görüntülemek için bir tarih ve saat aralığı seçin.

5. **Kullanıcılar** kutusunda, arama sonuçlarını görüntülemek üzere bir veya daha fazla kullanıcı seçin. Tüm kullanıcıların girdilerini döndürmek için bu kutuyu boş bırakın.

6. Arama ölçütlerinizi kullanarak aramayı çalıştırmak için **Ara'ya** tıklayın.

7. Arama sonuçları görüntülendikten sonra, sonuçta elde edilen etkinlik kayıtlarını filtrelemek veya sıralamak için **Sonuçları** filtrele'ye tıklayabilirsiniz. Ne yazık ki, belirli etkinlikleri açıkça dışlamak için filtrelemeyi kullanamazsınız. 

8. Bir etkinlikle ilgili ayrıntıları görüntülemek için arama sonuçları listesinde etkinlik kaydına tıklayın. 

    Olay kaydındaki ayrıntılı özellikleri içeren bir **Ayrıntılar** açılır sayfası görüntülenir. Ek ayrıntıları görüntülemek için **Daha fazla bilgi'ye** tıklayın. Bu özelliklerin açıklaması [için eBulma etkinlikleri için ayrıntılı özellikler](#detailed-properties-for-ediscovery-activities) bölümüne bakın.

9. İsterseniz, denetim günlüğü arama sonuçlarını bir CSV dosyasına aktarabilir ve ardından bu kayıtları biçimlendirmek ve filtrelemek için Excel Power Query özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>eBulma etkinlikleri

Aşağıdaki tabloda, bir yönetici veya eBulma yöneticisi uyumluluk portalını kullanarak eBulma ile ilgili bir etkinlik gerçekleştirdiğinde günlüğe kaydedilen İçerik Arama ve eBulma (Standart) etkinlikleri açıklanmaktadır. Bu listedeki etkinlikleri aradığınızda eBulma (Premium) içinde gerçekleştirilen bazı etkinlikler döndürülebilir.
  
> [!NOTE]
> Bu bölümde açıklanan eBulma etkinlikleri, sonraki bölümde açıklanan eBulma cmdlet etkinliklerine benzer bilgiler sağlar. Bu bölümde açıklanan eBulma etkinliklerini kullanmanızı öneririz çünkü bunlar 30 dakika içinde denetim günlüğü arama sonuçlarında görünür. eBulma cmdlet etkinliklerinin denetim günlüğü arama sonuçlarında görünmesi 24 saat kadar sürebilir.
  
|**Kolay ad**|**Işlem**|**Karşılık gelen cmdlet**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|eBulma servis talebine üye eklendi  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |EBulma servis talebinin üyesi olarak bir kullanıcı eklendi. Bir servis talebinin üyesi olarak, kullanıcı kendisine gerekli izinlerin atanıp atanmadığına bağlı olarak büyük/küçük harfle ilgili çeşitli görevleri gerçekleştirebilir.  <br/> |
|Değiştirilen içerik araması  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Mevcut bir içerik araması değiştirildi. Değişiklikler içerik konumlarını eklemeyi veya kaldırmayı ya da arama sorgusunu düzenlemeyi içerebilir.  <br/> |
|eKeşif yönetici üyeliği değiştirildi  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Kuruluşunuzdaki eBulma Yöneticileri listesi değiştirildi. eBulma Yöneticileri listesi bir grup yeni kullanıcıyla değiştirildiğinde bu etkinlik günlüğe kaydedilir. Tek bir kullanıcı eklenir veya kaldırılırsa CaseAdminAdded işlemi günlüğe kaydedilir.  <br/> |
|eBulma servis talebi değiştirildi  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |Bir eBulma servis talebi değiştirildi. Değişiklikler arasında açık servis talebini kapatma veya kapalı servis talebi yeniden açma sayılabilir.  <br/> |
|eBulma servis talebi üyeliği değiştirildi  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |eBulma servis talebinin üyelik listesi değiştirildi. Tüm üyeler bir grup yeni kullanıcıyla değiştirildiğinde bu etkinlik günlüğe kaydedilir. Tek bir üye eklenir veya kaldırılırsa CaseMemberAdded veya CaseMemberRemoved işlemi günlüğe kaydedilir.  <br/> |
|Arama izinleri filtresi değiştirildi  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Arama izinleri filtresi değiştirildi.  <br/> |
|eBulma servis talebi saklama için arama sorgusu değiştirildi  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |eBulma servis talebiyle ilişkili sorgu tabanlı ayrı tutma değiştirildi. Olası değişiklikler arasında sorguyu veya sorgu tabanlı ayrı tutma için tarih aralığını düzenleme yer alır.  <br/> |
|İçerik arama önizleme öğesi indirildi  <br/> |PreviewItemDownloaded  <br/> |Yok  <br/> |Kullanıcı, arama sonuçlarının önizlemesini yaparken bir öğeyi yerel bilgisayarına indirdi ( **Özgün öğeyi indir** bağlantısına tıklayarak).  <br/> |
|listelenen içerik arama önizleme öğesi  <br/> |PreviewItemListed  <br/> |Yok  <br/> |Kullanıcı **, arama sonuçlarından** en fazla 1.000 öğeyi listeleyen önizleme arama sonuçları sayfasını görüntülemek için Arama sonuçlarını önizle'ye tıkladı.  <br/> |
|görüntülenen içerik arama önizleme öğesi  <br/> |PreviewItemRendered  <br/> |Yok  <br/> |Bir eBulma yöneticisi, arama sonuçlarının önizlemesini görüntülerken öğeye tıklayarak öğeyi görüntüledi.  <br/> |
|İçerik araması oluşturuldu  <br/> |AramaOluştur  <br/> |New-ComplianceSearch  <br/> |Yeni bir içerik araması oluşturuldu.  <br/> |
|eBulma yöneticisi oluşturuldu  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Bir kullanıcı kuruluşta eBulma Yöneticisi olarak eklendi.  <br/> |
|EBulma servis talebi oluşturuldu  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Bir eBulma olayı oluşturuldu. Bir servis talebi oluşturulduğunda, yalnızca bir ad vermeniz gerekir. Üye ekleme, ayrı tutma oluşturma ve servis talebiyle ilişkili içerik aramaları oluşturma gibi büyük/küçük harfle ilgili diğer görevler, günlüğe ek olayların kaydedilmesine neden olur.  <br/> |
|Arama izinleri filtresi oluşturuldu  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Arama izinleri filtresi oluşturuldu.  <br/> |
|eBulma servis talebi saklama için arama sorgusu oluşturuldu  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |eBulma olayıyla ilişkili sorgu tabanlı bir ayrı tutma oluşturuldu.  <br/> |
|Silinen içerik araması  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |Mevcut bir içerik araması silindi.  <br/> |
|Silinen eBulma yöneticisi  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |Kuruluşunuzdan bir eBulma Yöneticisi silindi.  <br/> |
|Silinen eBulma servis talebi  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |Bir eBulma olayı silindi. Servis talebiyle ilişkili tüm ayrı tutmaların, servis talebinin silinebilmesi için önce kaldırılması gerekir.  <br/> |
|Silinen arama izinleri filtresi  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Arama izinleri filtresi silindi.  <br/> |
|eBulma servis talebi saklama için arama sorgusu silindi  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |eBulma servis talebiyle ilişkili sorgu tabanlı ayrı tutma silindi. Sorgunun ayrı tutmadan kaldırılması genellikle ayrı tutmanın silinmesinin sonucudur. Ayrı tutma veya ayrı tutma sorgusu silindiğinde, beklemedeki içerik konumları serbest bırakılır.  <br/> |
|İçerik aramasının indirilmiş dışarı aktarması  <br/> |SearchExportDownloaded  <br/> |Yok  <br/> |Bir kullanıcı, içerik aramasının sonuçlarını yerel bilgisayarına indirdi. Arama sonuçlarının indirilebilmesi için önce içerik arama etkinliğinin başlatılmış **bir dışarı aktarımının** başlatılması gerekir.  <br/> |
|İçerik aramasının önizlemesi yapılan sonuçlar  <br/> |SearchPreviewed  <br/> |Yok  <br/> |Bir kullanıcı içerik aramasının sonuçlarının önizlemesini görüntüledi.  <br/> |
|İçerik aramasının sonuçları temizlenmiş  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Kullanıcı **, New-ComplianceSearchAction -Purge** komutunu çalıştırarak İçerik aramasının sonuçlarını temizledi.  <br/> |
|İçerik arama analizi kaldırıldı  <br/> |KaldırıldıSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama hazırlama eylemi (arama sonuçlarını eBulma (Premium) için hazırlamak için) silindi. Hazırlık eylemi iki haftadan kısaysa, eBulma (Premium) için hazırlanan arama sonuçları Microsoft Azure depolama alanından silindi. Hazırlık eylemi 2 haftadan eskiyse, bu olay yalnızca ilgili hazırlık eyleminin silindiğini gösterir.  <br/> |
|İçerik aramasının dışarı aktarımı kaldırıldı  <br/> |KaldırıldıSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama dışarı aktarma eylemi silindi. Dışarı aktarma eylemi iki haftadan kısa bir süre önceyse, Microsoft Azure depolama alanına yüklenen arama sonuçları silinir. Dışarı aktarma eylemi 2 haftadan eskiyse, bu olay yalnızca ilgili dışarı aktarma eyleminin silindiğini gösterir.  <br/> |
|eBulma durumundan üye kaldırıldı  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Bir kullanıcı eBulma olayının üyesi olarak kaldırıldı.  <br/> |
|İçerik aramasının önizleme sonuçları kaldırıldı  <br/> |KaldırıldıSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama önizleme eylemi silindi.  <br/> |
|İçerik aramada gerçekleştirilen temizleme eylemi kaldırıldı  <br/> |KaldırıldıSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama temizleme eylemi silindi.  <br/> |
|Arama raporu kaldırıldı  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama dışarı aktarma raporu eylemi silindi.  <br/> |
|İçerik arama analizi başlatıldı  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |İçerik aramasının sonuçları eBulma(Premium) içinde analiz için hazırlandı.  <br/> |
|İçerik araması başlatıldı  <br/> |Arama Başlatıldı  <br/> |Start-ComplianceSearch  <br/> |İçerik araması başlatıldı. Uyumluluk portalını kullanarak içerik araması oluşturduğunuzda veya değiştirdiğinizde, arama otomatik olarak başlatılır.<br/> |
|İçerik aramasının dışarı aktarımı başlatıldı  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Bir kullanıcı içerik aramasının sonuçlarını dışarı aktardı.  <br/> |
|Dışarı aktarma raporu başlatıldı  <br/> |Arama Raporu  <br/> |New-ComplianceSearchAction  <br/> |Kullanıcı bir içerik arama raporunu dışarı aktardı.  <br/> |
|Durdurulan içerik araması  <br/> |AramaStopped  <br/> |Stop-ComplianceSearch  <br/> |Kullanıcı içerik aramalarını durdurdu.  <br/> |
|(yok)|CaseViewed|Get-ComplianceCase|Kullanıcı, uyumluluk merkezinde eBulma (Standart) servis talebini görüntüledi. Bu olayın denetim kaydı, görüntülenen servis talebinin adını içerir. |
|(yok)|SearchViewed|Get-ComplianceSearch|Kullanıcı, eBulma (Standart) durumundaki **Aramalar** sekmesindeki aramaya erişerek veya İçerik arama sayfasından erişerek uyumluluk merkezinde **İçerik aramasını** görüntüledi. Bu olayın denetim kaydı, görüntülenen aramanın kimliğini içerir.|
|(yok)|ViewedSearchExported|Get-ComplianceSearchAction -Dışarı Aktarma|Kullanıcı, İçerik arama sayfasının **Dışarı Aktarmalar** sekmesindeki dışarı aktarma işlemine erişerek uyumluluk merkezinde **İçerik arama dışarı aktarma** işlemini görüntüledi. Bu etkinlik, kullanıcı bir eBulma (Standart) olayıyla ilişkili dışarı aktarmayı görüntülediğinde de günlüğe kaydedilir.|
|(yok)|ViewedSearchPreviewed|Get-ComplianceSearchAction -Önizleme|Kullanıcı, uyumluluk merkezinde İçerik aramasının sonuçlarının önizlemesini görüntüledi. Bu etkinlik, kullanıcı eBulma (Standart) olayıyla ilişkili bir aramanın sonuçlarını önizlediğinde de günlüğe kaydedilir.|
|||||
  
## <a name="ediscovery-premium-activities"></a>eBulma (Premium) etkinlikleri

Aşağıdaki tabloda, denetim günlüğüne kaydedilen eBulma (Premium) etkinlikleri açıklanmaktadır. Bu etkinlikler, eBulma (Premium) durumunda etkinliğin ilerleme durumunu izlemenize yardımcı olmak için kullanılabilir.

|**Kolay ad**|**Işlem**|**Açıklama**|
|:-----|:-----|:-----|
|Başka bir gözden geçirme kümesine veri eklendi|AddWorkingSetQueryToWorkingSet|Kullanıcı, bir gözden geçirme kümesindeki belgeleri farklı bir gözden geçirme kümesine ekledi.|
|Gözden geçirme kümesine veri eklendi|AddQueryToWorkingSet|Kullanıcı, eBulma (Premium) olayıyla ilişkilendirilmiş içerik aramasından gelen arama sonuçlarını bir gözden geçirme kümesine ekledi.|
|Kümeyi gözden geçirmek için Microsoft 365 olmayan veriler eklendi|AddNonOffice365DataToWorkingSet|Kullanıcı bir gözden geçirme kümesine Microsoft 365 olmayan veriler ekledi.|
|Kümeyi gözden geçirmek için düzeltilmiş belgeler eklendi|AddRemediatedData|Kullanıcı, bir gözden geçirme kümesine düzeltilen dizin oluşturma hataları olan belgeleri karşıya yükler.|
|Gözden geçirme kümesindeki analiz edilen veriler|RunAlgo|Kullanıcı bir inceleme kümesindeki belgeler üzerinde analiz çalıştırmıştı.|
|Gözden geçirme kümesinde ek açıklamalı belge|AnnotateDocument|Kullanıcı, bir gözden geçirme kümesindeki bir belgeye açıklama eklemiştir. Ek açıklama, belgedeki içeriği yeniden boyutlandırmayı içerir.|
|Karşılaştırılan yük kümeleri|LoadComparisonjob|Kullanıcı, bir gözden geçirme kümesindeki iki farklı yük kümesini karşılaştırmıştı. Yük kümesi, servis talebiyle ilişkili bir içerik aramasından alınan verilerin bir gözden geçirme kümesine eklenmesidir.|
|Redakte edilmiş belgeler PDF'ye dönüştürüldü|BurnJob|Kullanıcı, gözden geçirme kümesindeki tüm yeniden uygulanan belgeleri PDF dosyalarına dönüştürdü.|
|Gözden geçirme kümesi oluşturuldu|CreateWorkingSet|Kullanıcı bir gözden geçirme kümesi oluşturdu.|
|Gözden geçirme kümesi araması oluşturuldu|CreateWorkingSetSearch|Kullanıcı, bir gözden geçirme kümesindeki belgelerde arama yapılan bir arama sorgusu oluşturdu.|
|Etiket oluşturuldu|CreateTag|Kullanıcı bir gözden geçirme kümesinde bir etiket grubu oluşturdu. Etiket grubu bir veya daha fazla alt etiket içerebilir. Bu etiketler daha sonra gözden geçirme kümesindeki belgeleri etiketlemek için kullanılır.|
|Gözden geçirme kümesi araması silindi|DeleteWorkingSetSearch|Kullanıcı bir gözden geçirme kümesindeki arama sorgusunu sildi.|
|Etiket silindi|DeleteTag|Kullanıcı, bir gözden geçirme kümesindeki bir etiketi veya etiket grubunu sildi.|
|İndirilen belge|DownloadDocument|Kullanıcı bir inceleme kümesinden belge indirdi.|
|Etiket düzenlendi|UpdateTag|Kullanıcı bir gözden geçirme kümesindeki etiketi değiştirdi.|
|Gözden geçirme kümesinden dışarı aktarılan belgeler|Dışarı Aktarma İşi|Kullanıcı bir gözden geçirme kümesinden belgeleri dışarı aktardı.|
|Büyük/küçük harf ayarı değiştirildi|UpdateCaseSettings|Kullanıcı bir servis talebinin ayarlarını değiştirdi. Olay ayarları, olay bilgilerini, erişim izinlerini ve arama ve analiz davranışını denetleen ayarları içerir.|
|Gözden geçirme kümesi araması değiştirildi|UpdateWorkingSetSearch|Kullanıcı bir gözden geçirme kümesindeki arama sorgusunu düzenlemiş.|
|Önizlemeli gözden geçirme kümesi araması|PreviewWorkingSetSearch|Kullanıcı, bir gözden geçirme kümesindeki arama sorgusunun sonuçlarının önizlemesini yaptı.|
|Düzeltilmiş hata belgeleri|ErrorRemediationJob|Kullanıcı, dizin oluşturma hataları içeren dosyaları düzeltir.|
|Etiketli belge|TagFiles|Kullanıcı, gözden geçirme kümesindeki bir belgeyi etiketler.|
|Sorgunun etiketli sonuçları|TagJob|Kullanıcı, bir gözden geçirme kümesindeki arama sorgusu ölçütleriyle eşleşen tüm belgeleri etiketler.|
|Gözden geçirme kümesinde görüntülenen belge|ViewDocument|Kullanıcı bir belgeyi gözden geçirme kümesinde görüntüledi.|
|||

## <a name="ediscovery-cmdlet-activities"></a>eBulma cmdlet etkinlikleri

Aşağıdaki tabloda, bir yönetici veya kullanıcı uyumluluk merkezini kullanarak veya Güvenlik & Uyumluluk Merkezi PowerShell'de ilgili cmdlet'i çalıştırarak eBulma ile ilgili bir etkinlik gerçekleştirdiğinde günlüğe kaydedilen cmdlet denetim günlüğü kayıtları listelenir. Denetim günlüğü kaydındaki ayrıntılı bilgiler, bu tabloda listelenen cmdlet etkinlikleri ve önceki bölümde açıklanan eBulma etkinlikleri için farklıdır.
  
Daha önce belirtildiği gibi, eBulma cmdlet etkinliklerinin denetim günlüğü arama sonuçlarında görünmesi 24 saat kadar sürebilir.
  
> [!TIP]
> Aşağıdaki tablodaki **İşlem** sütunundaki cmdlet'ler TechNet'teki ilgili cmdlet yardım konusuna bağlıdır. Her cmdlet için kullanılabilir parametrelerin açıklaması için cmdlet yardım konusuna gidin. Bir cmdlet ile kullanılan parametre ve parametre değeri, günlüğe kaydedilen her eBulma cmdlet etkinliği için denetim günlüğü girişine eklenir. 
  
|**Kolay ad**|**İşlem (cmdlet)**|**Açıklama**|
|:-----|:-----|:-----|
|eBulma durumunda ayrı tutma oluşturuldu  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |eBulma servis talebi için ayrı tutma oluşturuldu. İçerik kaynağı belirterek veya belirtmeden ayrı tutma oluşturulabilir. İçerik kaynakları belirtilirse, bunlar denetim günlüğü girdisinde tanımlanır.  <br/> |
|eBulma durumundan ayrı tutma silindi  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |eBulma servis talebiyle ilişkili ayrı tutma silindi. Ayrı tutmanın silinmesi, ayrı tutmadaki tüm içerik konumlarını serbest bırakır. Ayrı tutmanın silinmesi, ayrı tutma ile ilişkili servis talebi saklama kurallarının silinmesine de neden olur (aşağıdaki **Remove-CaseHoldRule** bölümüne bakın).  <br/> |
|eBulma durumunda ayrı tutma değiştirildi  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |eBulma ile ilişkili ayrı tutma değiştirildi. Olası değişiklikler arasında içerik konumlarını ekleme veya kaldırma veya ayrı tutmayı kapatma (devre dışı bırakma) sayılabilir.  <br/> |
|eBulma servis talebi saklama için arama sorgusu oluşturuldu  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |eBulma olayıyla ilişkili sorgu tabanlı bir ayrı tutma oluşturuldu.  <br/> |
|eBulma servis talebi saklama için arama sorgusu silindi  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |eBulma servis talebiyle ilişkili sorgu tabanlı ayrı tutma silindi. Sorgunun ayrı tutmadan kaldırılması genellikle ayrı tutmanın silinmesinin sonucudur. Ayrı tutma veya ayrı tutma sorgusu silindiğinde, beklemedeki içerik konumları serbest bırakılır.  <br/> |
|eBulma servis talebi saklama için arama sorgusu değiştirildi  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |eBulma servis talebiyle ilişkili sorgu tabanlı ayrı tutma değiştirildi. Olası değişiklikler arasında sorguyu veya sorgu tabanlı ayrı tutma için tarih aralığını düzenleme yer alır.  <br/> |
|EBulma servis talebi oluşturuldu  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Bir eBulma olayı oluşturuldu. Bir servis talebi oluşturulduğunda, yalnızca bir ad vermeniz gerekir. Üye ekleme, ayrı tutma oluşturma ve servis talebiyle ilişkili içerik aramaları oluşturma gibi büyük/küçük harfle ilgili diğer görevler, günlüğe ek olayların kaydedilmesine neden olur.  <br/> |
|Silinen eBulma servis talebi  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |Bir eBulma olayı silindi. Servis talebiyle ilişkili tüm ayrı tutmaların, servis talebinin silinebilmesi için önce kaldırılması gerekir.  <br/> |
|eBulma servis talebi değiştirildi  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |Bir eBulma servis talebi değiştirildi. Değişiklikler arasında açık servis talebini kapatma veya kapalı servis talebi yeniden açma sayılabilir.  <br/> |
|eBulma servis talebine üye eklendi  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |EBulma servis talebinin üyesi olarak bir kullanıcı eklendi. Bir servis talebinin üyesi olarak, kullanıcı kendisine gerekli izinlerin atanıp atanmadığına bağlı olarak büyük/küçük harfle ilgili çeşitli görevleri gerçekleştirebilir.  <br/> |
|eBulma durumundan üye kaldırıldı  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Bir kullanıcı eBulma olayının üyesi olarak kaldırıldı.  <br/> |
|eBulma servis talebi üyeliği değiştirildi  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |eBulma servis talebinin üyelik listesi değiştirildi. Tüm üyeler bir grup yeni kullanıcıyla değiştirildiğinde bu etkinlik günlüğe kaydedilir. Tek bir üye eklenir veya kaldırılırsa **Add-ComplianceCaseMember** veya **Remove-ComplianceCaseMember** işlemi günlüğe kaydedilir.  <br/> |
|İçerik araması oluşturuldu  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Yeni bir içerik araması oluşturuldu.  <br/> |
|Silinen içerik araması  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Mevcut bir içerik araması silindi.  <br/> |
|Değiştirilen içerik araması  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Mevcut bir içerik araması değiştirildi. Değişiklikler, arama yapılan içerik konumlarını eklemeyi veya kaldırmayı ve arama sorgusunu düzenlemeyi içerebilir.  <br/> |
|İçerik araması başlatıldı  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |İçerik araması başlatıldı. Uyumluluk merkezi GUI'sini kullanarak içerik araması oluşturduğunuzda veya değiştirdiğinizde, arama otomatik olarak başlatılır. **New-ComplianceSearch** veya **Set-ComplianceSearch** cmdlet'ini kullanarak arama oluşturur veya değiştirirseniz, aramayı başlatmak için **Start-ComplianceSearch** cmdlet'ini çalıştırmanız gerekir.  <br/> |
|Durdurulan içerik araması  <br/> |[Uyumluluğu DurdurArama](/powershell/module/exchange/stop-compliancesearch) <br/> |Çalışan bir içerik araması durduruldu.  <br/> |
|İçerik arama eylemi oluşturuldu  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |İçerik arama eylemi oluşturuldu. İçerik arama eylemleri arama sonuçlarının önizlemesini görüntülemeyi, arama sonuçlarını dışarı aktarmayı, arama sonuçlarını eBulma'da (Premium) analiz için hazırlamayı ve içerik aramasının arama ölçütlerine uyan öğeleri kalıcı olarak silmeyi içerir.  <br/> |
|Silinen içerik arama eylemi  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |İçerik arama eylemi silindi.  <br/> |
|Arama izinleri filtresi oluşturuldu  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Arama izinleri filtresi oluşturuldu.  <br/> |
|Silinen arama izinleri filtresi  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Arama izinleri filtresi silindi.  <br/> |
|Arama izinleri filtresi değiştirildi  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Arama izinleri filtresi değiştirildi.  <br/> |
|eBulma yöneticisi oluşturuldu  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Kuruluşunuzda eBulma Yöneticisi olarak bir kullanıcı eklendi.  <br/> |
|Silinen eBulma yöneticisi  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |Kuruluşunuzdan bir eBulma Yöneticisi silindi.  <br/> |
|eKeşif yönetici üyeliği değiştirildi  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Kuruluşunuzdaki eBulma Yöneticileri listesi değiştirildi. eBulma Yöneticileri listesi bir grup yeni kullanıcıyla değiştirildiğinde bu etkinlik günlüğe kaydedilir. Tek bir kullanıcı eklenir veya kaldırılırsa **Add-eDiscoveryCaseAdmin** veya **Remove-eDiscoveryCaseAdmin** işlemi günlüğe kaydedilir.  <br/> |
|(yok)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Bu etkinlik, kullanıcı eBulma (Standart) veya eBulma (Premium) servis taleplerinin listesini görüntülediğinde günlüğe kaydedilir. Bu etkinlik, kullanıcı eBulma'da (Standart) belirli bir olayı görüntülediğinde de günlüğe kaydedilir. Kullanıcı belirli bir olayı görüntülediğinde, denetim kaydı görüntülenen servis talebinin kimliğini içerir. Kullanıcı yalnızca servis taleplerinin listesini görüntülediyse, denetim kaydı bir servis talebi kimliği içermez.|
|(yok)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Bu etkinlik, kullanıcı bir eBulma (Standart) olayıyla ilişkili İçerik aramalarının veya aramalarının listesini görüntülediğinde günlüğe kaydedilir. Bu etkinlik, kullanıcı belirli bir İçerik aramasını görüntülediğinde veya eBulma (Standart) olayıyla ilişkili belirli bir aramayı görüntülediğinde de günlüğe kaydedilir. Kullanıcı belirli bir aramayı görüntülediğinde, denetim kaydı görüntülenen aramanın kimliğini içerir. Kullanıcı yalnızca arama listesini görüntülediyse, denetim kaydı arama kimliği içermez.
|(yok)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Bu etkinlik, kullanıcı eBulma (Standart) olayıyla ilişkili uyumluluk arama eylemlerinin (dışarı aktarmalar, önizlemeler veya temizlemeler gibi) listesini görüntülediğinde günlüğe kaydedilir. Bu etkinlik, kullanıcı belirli bir uyumluluk arama eylemini (dışarı aktarma gibi) veya eBulma (Standart) olayıyla ilişkili belirli bir eylemi görüntülediğinde de günlüğe kaydedilir. Kullanıcı bir arama eylemini görüntülediğinde, denetim kaydı görüntülenen arama eyleminin kimliğini içerir. Kullanıcı yalnızca eylemlerin listesini görüntülediyse, denetim kaydı eylem kimliği içermez.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>eBulma etkinlikleri için ayrıntılı özellikler

Aşağıdaki tabloda, arama sonuçlarında listelenen bir eBulma etkinliği için açılır sayfaya eklenen özellikler açıklanmaktadır. Bu özellikler, denetim günlüğü arama sonuçlarını dışarı aktardığınızda CSV dosyasına da eklenir. eBulma etkinliği için denetim günlüğü kaydı, aşağıda listelenen tüm ayrıntılı özellikleri içermez.
  
> [!TIP]
> Arama sonuçlarını dışarı aktardığınızda, CSV dosyası çok değerli bir özellikte aşağıdaki tabloda açıklanan ayrıntılı özellikleri içeren **AudtiData** adlı bir sütun içerir. Her özelliğin kendi sütununa sahip olması için bu sütunu birden çok sütuna bölmek için Excel'daki Power Query özelliğini kullanabilirsiniz. Bu, bu özelliklerden birini veya daha fazlasını sıralamanıza ve filtrelemenize olanak verir. Daha fazla bilgi için Denetim [günlüğünde arama'nın](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file) "Arama sonuçlarını bir dosyaya aktarma" bölümüne bakın. 
  
|**Özellik**|**Açıklama**|
|:-----|:-----|
|Durumda  <br/> |Oluşturulan, değiştirilen veya silinen eBulma servis talebinin kimliği (GUID).  <br/> |
|ClientApplication  <br/> |eBulma cmdlet etkinlikleri bu özellik için **EMC** değerine sahiptir. Bu, etkinliğin uyumluluk merkezi GUI'sini kullanarak veya PowerShell'de cmdlet'i çalıştırılarak gerçekleştirildiğini gösterir.  <br/> |
|ClientIP  <br/> |Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi IPv4 veya IPv6 adres biçiminde görüntülenir.  <br/> |
|ClientRequestId  <br/> | eBulma etkinlikleri için bu özellik genellikle boş olur.  <br/> |
|CmdletVersion  <br/> |Kuruluşunuzda çalışan uyumluluk merkezi sürümünün derleme numarası.  <br/> |
|CreationTime  <br/> |eBulma etkinliğinin tamamlandığı Eşgüdümlü Evrensel Saat (UTC) içindeki tarih ve saat.  <br/> |
|EffectiveOrganization  <br/> |Microsoft 365 kuruluşunun adı.  <br/> |
|ExchangeLocations  <br/> |İçerik aramasında yer alan veya eBulma servis talebine askıya eklenen Exchange Online posta kutuları.  <br/> |
|Dışlamalar  <br/> |eBulma durumunda içerik aramasından veya ayrı tutmadan hariç tutulan posta kutusu veya site konumları.  <br/> |
|ExtendedProperties  <br/> |bir içerik aramasından, içerik arama eyleminden ek özellikler veya eBulma durumunda tutun; örneğin, nesne GUID'si ve etkinlik gerçekleştirilirken kullanılan ilgili cmdlet ve cmdlet parametreleri.  <br/> |
|Kimliği  <br/> |Rapor girdisinin kimliği. Kimlik, denetim günlüğü girdisini benzersiz olarak tanımlar.  <br/> |
|NonPIIParameters  <br/> |Operation özelliğinde tanımlanan cmdlet ile kullanılan parametrelerin (herhangi bir değer olmadan) listesi. Bu özellikte listelenen parametreler, Parameters özelliğinde listelenen parametrelerle aynıdır.  <br/> |
|Objectıd  <br/> |Operation özelliğinde listelenen etkinlik tarafından oluşturulan, erişilen, değiştirilen veya silinen nesnenin GUID'i veya adı (örneğin, İçerik araması veya eBulma (Standart) olayı). Bu nesne, denetim günlüğü arama sonuçlarındaki Öğe sütununda da tanımlanır.  <br/> |
|Nesnetürü  <br/> |Kullanıcının oluşturduğu, sildiği veya değiştirdiği eBulma nesnesinin türü; örneğin, bir içerik arama eylemi (önizleme, dışarı aktarma veya temizleme), eBulma olayı veya içerik araması.  <br/> |
|Işlem  <br/> |Gerçekleştirilen eBulma etkinliğine karşılık gelen işlemin adı.  <br/> |
|OrganizationId  <br/> |Microsoft 365 kuruluşunuzun GUID'i.  <br/> |
|Parametre  <br/> |karşılık gelen cmdlet ile kullanılan parametrelerin adı ve değeri.  <br/> |
|PublicFolderLocations  <br/> |Exchange Online içindeki içerik aramasında yer alan veya eBulma servis talebine beklemeye konulan ortak klasör konumları.  <br/> |
|Sorgu  <br/> |İçerik araması veya sorgu tabanlı ayrı tutma gibi etkinlikle ilişkili arama sorgusu.  <br/> |
|Kayıt Türü  <br/> |Kayıt tarafından belirtilen işlem türü. **18** değeri [, eBulma cmdlet etkinlikleri](#ediscovery-cmdlet-activities) bölümünde listelenen bir etkinlikle ilgili bir olayı gösterir. **24** değeri [, eBulma etkinliklerini arama ve görüntüleme](#how-to-search-for-and-view-ediscovery-activities) bölümünde listelenen bir etkinlikle ilgili olayı gösterir.  <br/> |
|ResultStatus  <br/> |Eylemin (Operation özelliğinde belirtilen) başarılı olup olmadığını gösterir.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Etkinliğin bir uyumluluk merkezi olayı olduğunu gösterir. Tüm eBulma etkinlikleri bu özellik için **0** değerine sahip olacaktır.  <br/> |
|SharepointLocations  <br/> |İçerik aramasında yer alan veya eBulma servis talebine askıya eklenen SharePoint Online siteleri.  <br/> |
|Starttime  <br/> |eBulma etkinliğinin başlatıldığı Eşgüdümlü Evrensel Saat (UTC) tarihi ve saati.  <br/> |
|Userıd  <br/> |Kaydın günlüğe kaydedilmesiyle sonuçlanan etkinliği gerçekleştiren kullanıcı (Operation özelliğinde belirtilir). Sistem hesapları (NT AUTHORITY\SYSTEM gibi) tarafından gerçekleştirilen eBulma etkinliğinin kayıtları da denetim günlüğüne eklenir.  <br/> |
|UserKey  <br/> |UserId özelliğinde tanımlanan kullanıcı için alternatif bir kimlik. eBulma etkinlikleri için bu özelliğin değeri genellikle UserId özelliğiyle aynıdır.  <br/> |
|UserServicePlan  <br/> |Kuruluşunuz tarafından kullanılan abonelik. eBulma etkinlikleri için bu özellik genellikle boş olur.  <br/> |
|Usertype  <br/> |İşlemi gerçekleştiren kullanıcının türü. Aşağıdaki değerler kullanıcı türünü gösterir.  <br/> 0 Normal bir kullanıcı. 2 Kuruluşunuzda bir yönetici. 3 Microsoft veri merkezi yöneticisi veya veri merkezi sistem hesabı. 4 Bir sistem hesabı. 5 Bir uygulama. 6 Hizmet sorumlusu. |
|Sürüm  <br/> |Günlüğe kaydedilen etkinliğin sürüm numarasını (Operation özelliğiyle tanımlanır) gösterir.  <br/> |
|Iş yük -ünü  <br/> |Etkinliğin gerçekleştiği hizmet. eBulma etkinlikleri için değer **SecurityComplianceCenter'dir**.  <br/> |
