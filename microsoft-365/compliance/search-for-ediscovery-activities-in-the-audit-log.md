---
title: Denetim günlüğünde eBulma etkinliklerini arama
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
description: eBulma izinleri atanan kullanıcılar İçerik araması, Çekirdek eKbulma ve proje görevleri Advanced eDiscovery hangi etkinliklerin günlüğe kaydedileceğini Microsoft 365 uyumluluk merkezi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eb1a6f1ee0ff9c84f4dbfc7f42427ae9dda499de
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021603"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Denetim günlüğünde eBulma etkinliklerini arama

Microsoft 365 uyumluluk merkezi'ta veya buna karşılık gelen PowerShell cmdlet'leri çalıştırarak gerçekleştirilen İçerik Arama ve eKbulma ile ilgili etkinlikler (Çekirdek eKbulma ve Advanced eDiscovery için) denetim günlüğüne kaydedilir. Yöneticiler, eBulma yöneticileri (ya da eBulma izinleri atanmış herhangi bir kullanıcı) etkinlik, aşağıdaki İçerik Arama ve Çekirdek eKbulma görevlerini aşağıdaki olay olaylarında gerçekleştirecek Microsoft 365 uyumluluk merkezi:
  
- Çekirdek ve temel durumlarını oluşturma Advanced eDiscovery yönetme

- İçerik aramalarını oluşturma, başlatma ve düzenleme

- Arama sonuçlarını önizleme, dışarı aktarma ve silme gibi arama eylemleri gerçekleştirme

- Web'de koruyucuları ve gözden geçirme kümelerini Advanced eDiscovery

- İçerik arama için izin filtrelemeyi yapılandırma

- eBulma Yönetici rolünü yönetme
  
Denetim günlüğünde arama, gereken izinler ve arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi için bkz. Denetim günlüğünde arama [Microsoft 365 uyumluluk merkezi](search-the-audit-log-in-security-and-compliance.md).
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>eBulma etkinlikleri için arama ve görüntüleme

Şu anda, denetim günlüğünde eBulma etkinliklerini görüntülemek için birkaç şey yapmak gerekir. Şöyle yapılır:
  
1. İş veya <https://compliance.microsoft.com> okul hesabınızla oturum açın ve gidin.

2. Denetim bölmesinin sol gezinti Microsoft 365 uyumluluk merkezi Denetim'e **tıklayın**.

3. Etkinlikler **açılan listesinde**, **eBulma** etkinlikleri veya Etkinlik Advanced eDiscovery **altında**, aranacak bir veya birden çok etkinlik'i tıklatın.

    > [!NOTE]
    > Etkinlikler **açılan** listesi, **eBulma cmdlet etkinlikleri adlı ve cmdlet** denetim günlüğünden kayıtları geri dönecek bir grup etkinlik de içerir.
  
4. Bir tarih ve saat aralığı seçerek, o dönem içinde  meydana gelen eBulma olaylarını görüntüleniyor.

5. Kullanıcılar **kutusunda** , arama sonuçlarını görüntülemek için bir veya birden çok kullanıcı seçin. Tüm kullanıcıların girdilerini geri dönmek için bu kutuyu boş bırakın.

6. Arama **ölçütlerinizi** kullanarak arama çalıştırmak için Ara'ya tıklayın.

7. Arama sonuçları görüntülendikten sonra, sonuçları filtrelemek **veya sıralamak** için Sonuçları filtrele'yi tıklatın. Ne yazık ki, belirli etkinlikleri açıkça dışarıda tutmak için filtrelemeyi kullanaasiniz. 

8. Etkinlikle ilgili ayrıntıları görüntülemek için, arama sonuçları listesinde etkinlik kaydına tıklayın. 

    Olay **kaydından** ayrıntılı özellikleri içeren bir Ayrıntılar uçarak giriş sayfası görüntülenir. Ek ayrıntıları görüntülemek için Daha fazla **bilgi'ye tıklayın**. Bu özelliklerin açıklaması için [, eBulma etkinlikleri için ayrıntılı özellikler bölümüne](#detailed-properties-for-ediscovery-activities) bakın.

9. İsterseniz, denetim günlüğü arama sonuçlarını bir CSV dosyasına aktarabilirsiniz ve ardından bu kayıtları biçimlendirmek ve filtrelemek için Excel Power Query özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz [. Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>eBulma etkinlikleri

Aşağıdaki tabloda, yönetici veya eBulma yöneticisi bu özelliği kullanarak eBulma ile ilgili bir etkinlik gerçekleştirdiğinde günlüğe kaydedilen İçerik Arama ve Çekirdek eBulma etkinlikleri Microsoft 365 uyumluluk merkezi. Bu listede Advanced eDiscovery bazı etkinlikler için arama gerçekleştiriliyor olabilir.
  
> [!NOTE]
> Bu bölümde açıklanan eBulma etkinlikleri, bir sonraki bölümde açıklanan eBulma cmdlet etkinliklerine benzer bilgiler sağlar. Bu bölümde açıklanan eBulma etkinliklerini kullanmanızı öneririz, çünkü bunlar 30 dakika içinde denetim günlüğü arama sonuçlarında görünür. eKbulma cmdlet etkinliklerinin denetim günlüğü arama sonuçlarında görünmesi 24 saat kadar sürebilir.
  
|**Kolay ad**|**Operation**|**Karşılık gelen cmdlet**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|eBulma vakaya üye eklendi  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |Bir kullanıcı eBulma durumuna üye olarak eklendi. Bir vakanın üyesi olarak, kullanıcıya gerekli izinlerin atanıp atanmama durumuna bağlı olarak, büyük/küçük harfle ilgili çeşitli görevleri gerçekleştirebilir.  <br/> |
|İçerik araması değiştirildi  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Var olan bir içerik araması değiştirilmiştir. Değişiklikler, içerik konumlarını eklemeyi veya kaldırmayı ya da arama sorgusunu düzenlemeyi içerebilir.  <br/> |
|eBulma yönetici üyeliği değiştirildi  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Kuruluşta eBulma Yöneticileri listesi değiştirildi. eBulma Yöneticileri listesi bir grup yeni kullanıcıyla değiştirili olduğunda bu etkinlik günlüğe kaydedilir. Tek bir kullanıcı eklenir veya kaldırılırsa CaseAdminAdded işlemi günlüğe kaydedilir.  <br/> |
|eBulma durumu değiştirildi  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |eBulma durumu değiştirilmiştir. Değişiklikler arasında açık bir vakayı kapatma veya kapalı bir vakayı yeniden açma vardır.  <br/> |
|eBulma olay üyeliği değiştirildi  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |eBulma davalarının üyelik listesi değiştirildi. Tüm üyeler bir yeni kullanıcı grubuyla değiştirili olduğunda bu etkinlik günlüğe kaydedilir. Tek bir üye eklenir veya kaldırılırsa, CaseMemberAdded veya CaseMemberRemoved işlemi günlüğe kaydedilir.  <br/> |
|Arama izinleri filtresi değiştirildi  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Arama izinleri filtresi değiştirildi.  <br/> |
|eBulma büyük/harf ayrımı için arama sorgusu değiştirildi  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı bir tutma değiştirilmiştir. Olası değişiklikler arasında, sorgu tabanlı bir tutma için sorguyu veya tarih aralığını düzenleme de vardır.  <br/> |
|İçerik arama önizleme öğesi indirildi  <br/> |PreviewItemDownloaded  <br/> |Yok  <br/> |Bir kullanıcı arama sonuçlarının önizlemesini görüntülerken bir öğeyi yerel bilgisayarına indirdi (Özgün öğeyi indir bağlantısına tıklayarak).  <br/> |
|Listelenen içerik arama önizleme öğesi  <br/> |PreviewItemListed  <br/> |Yok  <br/> |Kullanıcı, arama **sonuçlarından** en çok 1.000 öğe listeen önizleme arama sonuçları sayfasını görüntülemek için Arama sonuçlarını önizleme'ye tıkladı.  <br/> |
|İçerik arama önizleme öğesi görüntülandı  <br/> |PreviewItemRendered  <br/> |Yok  <br/> |eBulma yöneticisi, arama sonuçlarının önizlemesine bakarak bir öğeyi görüntüledi.  <br/> |
|İçerik araması oluşturuldu  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Yeni bir içerik araması oluşturuldu.  <br/> |
|eBulma yöneticisi oluşturuldu  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Kuruluşta eBulma Yöneticisi olarak bir kullanıcı eklendi.  <br/> |
|eBulma durumu oluşturuldu  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Bir eBulma durumu oluşturulmuş. Olay oluşturulduğunda bu vakaya yalnızca bir ad ver gerekir. Olayla ilgili diğer görevlerde üye ekleme, uzha oluşturma ve vakayla ilişkili içerik aramaları oluşturulması ek olayların günlüğe kaydedilene kadar devam ediyor.  <br/> |
|Arama izinleri filtresi oluşturuldu  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Bir arama izinleri filtresi oluşturulmuş.  <br/> |
|eBulma durumunda tutma için arama sorgusu oluşturuldu  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı bir tutma oluşturuldu.  <br/> |
|Silinmiş içerik araması  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |Var olan bir içerik araması silinmiştir.  <br/> |
|eBulma yöneticisi silindi  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |eBulma Yöneticisi, kuruluştan silinmiştir.  <br/> |
|eBulma durumu silindi  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |eBulma durumu silindi. Davayla ilişkilendirilmiş tüm tutmaların, dosyanın silinmeden önce kaldırılması gerekir.  <br/> |
|Silinmiş arama izinleri filtresi  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Arama izinleri filtresi silindi.  <br/> |
|eBulma büyük/harf ayrımı için silinen arama sorgusu  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı tutma silinmiştir. Sorgunun sıyrıdan kaldırılması çoğunlukla sıyrı silmenin sonucudur. Bir tutma veya tutma sorgusu silindiğinde, o anda tutukta olan içerik konumları yayımlanmaz.  <br/> |
|İndirilen içerik arama  <br/> |SearchExportDownloaded  <br/> |Yok  <br/> |Bir kullanıcı içerik arama sonuçlarını yerel bilgisayarına indirdi. Arama **sonuçları indirilmeden önce** İçerik arama etkinliğinin Başlatıldı dışa aktarması başlatılmış olması gerekir.  <br/> |
|İçerik aramanın önizlemesi sonuçları  <br/> |SearchPreviewed  <br/> |Yok  <br/> |Bir kullanıcı içerik arama sonuçlarının önizlemesini görüntüledi.  <br/> |
|İçerik arama sonuçları temiz edildi  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Kullanıcı, **New-ComplianceSearchAction -Purge komutunu çalıştırarak İçerik arama sonuçlarını temiz** etti.  <br/> |
|İçerik arama çözümlemesi kaldırıldı  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama hazırlama eylemi (arama sonuçlarını bu arama için Advanced eDiscovery) silinmiştir. Hazırlık eylemi iki haftadan kısa sürüyorsa, bu eylem için hazırlanmış arama Advanced eDiscovery bu Microsoft Azure alanı silinmiştir. Hazırlık eylemi 2 haftadan daha eski ise, bu etkinlik yalnızca buna karşılık gelen hazırlık eyleminin silinmiş olduğunu gösterir.  <br/> |
|İçerik arama dışarı aktarması kaldırıldı  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama dışarı aktarma eylemi silindi. Dışarı aktarma eylemi iki haftadan kısa sürüyorsa, bu eylemin depolama alanına Microsoft Azure sonuçları silinmiştir. Dışarı aktarma eylemi 2 haftadan eski bir eylemse, bu olay yalnızca ilgili dışarı aktarma eyleminin silinmiş olduğunu gösterir.  <br/> |
|eBulma durumundan üye kaldırıldı  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Bir kullanıcı eBulma davana üye olarak kaldırıldı.  <br/> |
|İçerik aramanın önizleme sonuçları kaldırıldı  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama önizleme eylemi silindi.  <br/> |
|İçerik arama üzerinde gerçekleştirilen temizleme eylemi kaldırıldı  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama temizleme eylemi silindi.  <br/> |
|Arama raporu kaldırıldı  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |İçerik arama dışarı aktarma raporu eylemi silindi.  <br/> |
|İçerik aramanın başlatıldı çözümlemesi  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |İçerik arama sonuçları, bu içerik aramalarında çözümleme için Advanced eDiscovery.  <br/> |
|İçerik araması başlatıldı  <br/> |AramaBaşlatıldı  <br/> |Start-ComplianceSearch  <br/> |İçerik araması başlatildi. İçerik aramanızı oluşturmak veya değiştirmek için arama Microsoft 365 uyumluluk merkezi, arama otomatik olarak başlatılır.<br/> |
|İçerik aramalarını dışarı aktarmaya başladı  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Kullanıcı içerik arama sonuçlarını dışarı aktardı.  <br/> |
|Başlatıldı dışarı aktarma raporu  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |Kullanıcı içerik arama raporunu dışarı aktardı.  <br/> |
|İçerik arama durduruldu  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |Kullanıcı içerik aramalarını durdurdu.  <br/> |
|(yok)|CaseViewed|Get-ComplianceCase|Kullanıcı uyumluluk merkezinde Bir Çekirdek eKbulma durumu görüntüledi. Bu olayın denetim kaydı, görüntülenen olayın adını içerir. |
|(yok)|SearchViewed|Get-ComplianceSearch|Kullanıcı, Core eKovery örneğinde Arama sekmesine erişerek veya İçerik arama  sayfasında buna erişerek uyumluluk merkezinde İçerik **aramalarını** görüntüledi. Bu olayın denetim kaydı, görüntülenen aramanın kimliğini içerir.|
|(yok)|ViewedSearchExported|Get-ComplianceSearchAction -Export|Kullanıcı, İçerik arama sayfasının Dışarı Aktarmalar sekmesinde dışarı aktarmaya erişerek uyumluluk merkezinde İçerik **arama dışarı** **aktarmayı görüntüledi** . Bu etkinlik, kullanıcı Çekirdek eBulma durumuyla ilişkilendirilmiş bir dışarı aktarmayı görüntülerken de günlüğe kaydedilir.|
|(yok)|ViewedSearchPreviewed|Get-ComplianceSearchAction -Preview|Bir kullanıcı uyumluluk merkezinde İçerik arama sonuçlarının önizlemesini görüntüledi. Bu etkinlik, kullanıcı Çekirdek eBulma durumuyla ilişkilendirilmiş bir aramanın sonuçlarının önizlemesini görüntüleye olduğunda da günlüğe kaydedilir.|
|||||
  
## <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery etkinlikleri

Aşağıdaki tabloda, denetim Advanced eDiscovery kaydedilen günlük etkinlikleri açık almaktadır. Bu etkinlikler, bir olayda etkinliğin ilerlemesini izlemede yardımcı Advanced eDiscovery kullanılabilir.

|**Kolay ad**|**Operation**|**Açıklama**|
|:-----|:-----|:-----|
|Başka bir gözden geçirme kümesine veri eklendi|AddWorkingSetQueryToWorkingSet|Kullanıcı bir gözden geçirme kümesinden belgeleri farklı bir gözden geçirme kümesine ekledi.|
|Gözden geçirme kümesine veri eklendi|AddQueryToWorkingSet|Kullanıcı, büyük/küçük harf kullanımıyla ilişkilendirilmiş içerik arama Advanced eDiscovery gözden geçirme kümesine ekledi.|
|Gözden geçirme kümesine Microsoft 365 olmayan veriler eklendi|AddNonOffice365DataToWorkingSet|Kullanıcı, gözden Microsoft 365 olmayan verileri gözden geçirme kümesine ekledi.|
|Düzeltilen belgeleri gözden geçirme kümesi eklendi|AddRemediatedData|Kullanıcı, gözden geçirme kümesinde düzeltilen dizin oluşturma hataları olan belgeleri karşıya yükledi.|
|Gözden geçirme kümesinde çözümlendi veriler|RunAlgo|Kullanıcı gözden geçirme kümesinde belgeler üzerinde çözümlemeler yaptı.|
|Gözden Geçirme kümesinde ek açıklamalı belge|AnnotateDocument|Kullanıcı gözden geçirme kümesinde bir belgeye ek açıklama ek açıklaması yaptı. Ek açıklama, belgedeki içeriği kırmızıtarak işlemden içerir.|
|Karşılaştırmalı yükleme kümeleri|LoadComparisonJob|Kullanıcı, gözden geçirme kümesinde iki farklı yükleme kümesi karşılaştırdı. Yükleme kümesi, olayla ilişkilendirilmiş içerik aramalarından gelen verilerin gözden geçirme kümesine ekli olduğu durum değeridir.|
|Redacted belgeleri PDF'ye dönüştürme|BurnJob|Kullanıcı gözden geçirme kümesinde tüm redacted belgelerini PDF dosyalarına dönüştürtü.|
|Gözden geçirme kümesi oluşturuldu|CreateWorkingSet|Kullanıcı bir gözden geçirme kümesi oluşturdu.|
|Gözden geçirme kümesi araması oluşturuldu|CreateWorkingSetSearch|Kullanıcı, gözden geçirme kümesinde belgelerde arama yapılan bir arama sorgusu oluşturdu.|
|Etiket oluşturuldu|CreateTag|Kullanıcı, gözden geçirme kümesinde bir etiket grubu oluşturdu. Etiket grubu bir veya birden çok alt etiket içerebilir. Bu etiketler daha sonra belgeleri gözden geçirme kümesinde etiketlemek için kullanılır.|
|Gözden geçirme kümesi araması silindi|DeleteWorkingSetSearch|Kullanıcı gözden geçirme kümesinde bir arama sorgusunu sildi.|
|Etiket silindi|DeleteTag|Kullanıcı gözden geçirme kümesinde bir etiketi veya etiket grubunu sildi.|
|İndirilen belge|DownloadDocument|Kullanıcı gözden geçirme kümesinden bir belge indirdi.|
|Etiket düzenlenmiş|Etiketi Güncelleştir|Kullanıcı, gözden geçirme kümesinde etiketi değiştirdi.|
|Gözden geçirme kümesinden dışarı aktarıldı belgeler|ExportJob|Kullanıcı gözden geçirme kümesinden belgeleri dışarı aktardı.|
|Büyük/yeni harf ayarı değiştirildi|UpdateCaseSettings|Kullanıcı vakanın ayarlarını değiştirdi. Olay ayarları arasında olay bilgileri, erişim izinleri ve arama ve çözümleme davranışını kontrol etmek için ayarlar yer almaktadır.|
|Gözden geçirme kümesi araması değiştirildi|UpdateWorkingSetSearch|Kullanıcı bir gözden geçirme kümesinde arama sorgusunu düzenledi.|
|Önizlemesi gözden geçirme kümesi araması|PreviewWorkingSetSearch|Kullanıcı, gözden geçirme kümesinde arama sorgusunun sonuçlarını önizledi.|
|Düzeltmiş hata belgeleri|ErrorRemediationJob|Kullanıcı dizin oluşturma hataları içeren dosyaları düzeltir.|
|Etiketli belge|TagFiles|Kullanıcı gözden geçirme kümesinde bir belgeyi etiketler.|
|Sorgunun etiketlenmiş sonuçları|TagJob|Kullanıcı, gözden geçirme kümesinde arama sorgusunun ölçütlerine uyan tüm belgeleri etiketler.|
|Gözden Geçirme kümesinde belge görüntülenmiş|ViewDocument|Kullanıcı belgeyi gözden geçirme kümesinde görüntüledi.|
|||

## <a name="ediscovery-cmdlet-activities"></a>eKbulma cmdlet etkinlikleri

Aşağıdaki tabloda, yönetici veya kullanıcı uyumluluk merkezini kullanarak veya ilgili cmdlet'i Güvenlik ve Uyumluluk Merkezi PowerShell'de çalıştırarak eBulma ile ilgili bir etkinlik gerçekleştirdiğinde günlüğe kaydedilen cmdlet & denetim günlüğü kayıtları listelemektedir. Denetim günlüğü kaydında yer alan ayrıntılı bilgiler, bu tabloda listelenen cmdlet etkinlikleri ve önceki bölümde açıklanan eBulma etkinlikleri için farklıdır.
  
Daha önce de belirtildiği gibi, eBulma cmdlet etkinliklerinin denetim günlüğü arama sonuçlarında görünmesi 24 saat kadar sürebilir.
  
> [!TIP]
> Aşağıdaki tablonun **Operation sütunundaki** cmdlet'ler TechNet'te ilgili cmdlet yardım konusuyla bağlantılıdır. Her cmdlet'in kullanılabilir parametrelerinin açıklaması için cmdlet yardım konu başlığına gidin. Parametre ve cmdlet ile kullanılan parametre değeri, günlüğe kaydedilen her eKbulma cmdlet etkinliği için denetim günlüğü girdisine dahil edilir. 
  
|**Kolay ad**|**Operation (cmdlet)**|**Açıklama**|
|:-----|:-----|:-----|
|eBulma durumunda ayrı tutma oluşturuldu  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |eBulma vakası için ayrı tutma oluşturulmuş. bir tutma, içerik kaynağı belirterek veya belirtmeden oluşturulabilir. İçerik kaynakları belirtilirse, bunlar denetim günlüğü girdisinde tanımlanır.  <br/> |
|eBulma durumundan ayrı tutma silinmiş  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |eBulma durumuyla ilişkilendirilmiş bir tutma silinmiştir. Bir tutmanın silinmesi, tüm içerik konumlarını basılı tutmadan itibaren serbest tutar. Ayrıca tutmanın silinmesi, tutmayla ilişkilendirilmiş vaka tutma kurallarının silinmesine de neden olur (aşağıdaki **CaseHoldRule'ya** bakın).  <br/> |
|eBulma durumunda ayrı tutma değiştirildi  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |eBulma ile ilişkilendirilmiş bir tutma değiştirilmiştir. Olası değişiklikler arasında içerik konumlarını ekleme veya kaldırma ya da tutma özelliğini kapatma (devre dışı bırakma) yer almaktadır.  <br/> |
|eBulma durumunda tutma için arama sorgusu oluşturuldu  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı bir tutma oluşturuldu.  <br/> |
|eBulma büyük/harf ayrımı için silinen arama sorgusu  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı tutma silinmiştir. Sorgunun sıyrıdan kaldırılması çoğunlukla sıyrı silmenin sonucudur. Bir tutma veya tutma sorgusu silindiğinde, o anda tutukta olan içerik konumları yayımlanmaz.  <br/> |
|eBulma büyük/harf ayrımı için arama sorgusu değiştirildi  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |eBulma durumuyla ilişkilendirilmiş sorgu tabanlı bir tutma değiştirilmiştir. Olası değişiklikler arasında, sorgu tabanlı bir tutma için sorguyu veya tarih aralığını düzenleme de vardır.  <br/> |
|eBulma durumu oluşturuldu  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Bir eBulma durumu oluşturulmuş. Olay oluşturulduğunda bu vakaya yalnızca bir ad ver gerekir. Olayla ilgili diğer görevlerde üye ekleme, uzha oluşturma ve vakayla ilişkili içerik aramaları oluşturulması ek olayların günlüğe kaydedilene kadar devam ediyor.  <br/> |
|eBulma durumu silindi  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |eBulma durumu silindi. Davayla ilişkilendirilmiş tüm tutmaların, dosyanın silinmeden önce kaldırılması gerekir.  <br/> |
|eBulma durumu değiştirildi  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |eBulma durumu değiştirilmiştir. Değişiklikler arasında açık bir vakayı kapatma veya kapalı bir vakayı yeniden açma vardır.  <br/> |
|eBulma vakaya üye eklendi  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |Bir kullanıcı eBulma durumuna üye olarak eklendi. Bir vakanın üyesi olarak, kullanıcıya gerekli izinlerin atanıp atanmama durumuna bağlı olarak, büyük/küçük harfle ilgili çeşitli görevleri gerçekleştirebilir.  <br/> |
|eBulma durumundan üye kaldırıldı  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Bir kullanıcı eBulma davana üye olarak kaldırıldı.  <br/> |
|eBulma olay üyeliği değiştirildi  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |eBulma davalarının üyelik listesi değiştirildi. Tüm üyeler bir yeni kullanıcı grubuyla değiştirili olduğunda bu etkinlik günlüğe kaydedilir. Tek bir üye eklenir veya kaldırılırsa, **Add-ComplianceCaseMember** veya **Remove-ComplianceCaseMember** işlemi günlüğe kaydedilir.  <br/> |
|İçerik araması oluşturuldu  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Yeni bir içerik araması oluşturuldu.  <br/> |
|Silinmiş içerik araması  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Var olan bir içerik araması silinmiştir.  <br/> |
|İçerik araması değiştirildi  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Var olan bir içerik araması değiştirilmiştir. Değişiklikler, arama yapılan içerik konumlarını eklemeyi veya kaldırmayı içerebilir ve arama sorgusunu düzenlemeyi içerebilir.  <br/> |
|İçerik araması başlatıldı  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |İçerik araması başlatildi. Uyumluluk merkezi GUI'sini kullanarak içerik araması  oluşturmanız veya bu aramada değişiklik yaptıysanız, arama otomatik olarak başlatılır. Yeni Uyumluluk Arama veya **Set-ComplianceSearch** cmdlet'ini kullanarak  bir arama oluşturmanız veya değiştirmenizi sağlarsanız, arama başlatmak için **Start-ComplianceSearch** cmdlet'ini çalıştırmalısiniz.  <br/> |
|İçerik arama durduruldu  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |Çalışan bir içerik araması durduruldu.  <br/> |
|İçerik arama eylemi oluşturuldu  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |İçerik arama eylemi oluşturulmuş. İçerik arama eylemleri, arama sonuçlarının önizlemesini görüntülemek, arama sonuçlarını dışarı aktarmayı, Advanced eDiscovery'de çözümleme için arama sonuçlarını hazırlamayı ve içerik arama ölçütlerine uyan öğeleri kalıcı olarak silmeyi içerir.  <br/> |
|Silinmiş içerik arama eylemi  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |İçerik arama eylemi silindi.  <br/> |
|Arama izinleri filtresi oluşturuldu  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Bir arama izinleri filtresi oluşturulmuş.  <br/> |
|Silinmiş arama izinleri filtresi  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Arama izinleri filtresi silindi.  <br/> |
|Arama izinleri filtresi değiştirildi  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Arama izinleri filtresi değiştirildi.  <br/> |
|eBulma yöneticisi oluşturuldu  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Bir kullanıcı, kuruluşta eBulma Yöneticisi olarak eklendi.  <br/> |
|eBulma yöneticisi silindi  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |eBulma Yöneticisi, kuruluştan silinmiştir.  <br/> |
|eBulma yönetici üyeliği değiştirildi  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Kuruluşta eBulma Yöneticileri listesi değiştirildi. eBulma Yöneticileri listesi bir grup yeni kullanıcıyla değiştirili olduğunda bu etkinlik günlüğe kaydedilir. Tek bir kullanıcı eklenir veya kaldırılırsa, **eDiscoveryCaseAdmin Veya** **Remove-eDiscoveryCaseAdmin** işlemi günlüğe kaydedilir.  <br/> |
|(yok)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Kullanıcı Çekirdek eKbulma veya başka durumların listesini görüntüledi ya da bu Advanced eDiscovery kaydedilir. Bu etkinlik, kullanıcı Core eDiscovery'de belirli bir vakayı görüntülerken de günlüğe kaydedilir. Kullanıcı belirli bir vakayı görüntüley ise, denetim kaydı görüntülenen vakanın kimliğini içerir. Kullanıcı yalnızca bir vaka listesini görüntüledi ise, denetim kaydı bir vaka kimliği içermemektedir.|
|(yok)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Kullanıcı, Çekirdek eKbulma durumuyla ilişkilendirilmiş İçerik aramaları veya aramalarını görüntüledi olduğunda bu etkinlik günlüğe kaydedilir. Ayrıca, kullanıcı belirli bir İçerik aramasini veya Core eKovery durumuyla ilişkilendirilmiş belirli bir aramayı görüntülerken de bu etkinlik günlüğe kaydedilir. Kullanıcı belirli bir arama görüntüley ise, denetim kaydı görüntülenen aramanın kimliğini içerir. Kullanıcı yalnızca arama listesini görüntüledi ise, denetim kaydı bir arama kimliği içermemektedir.
|(yok)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Bir kullanıcı, Çekirdek eKbulma durumuyla ilişkilendirilmiş uyumluluk arama eylemleri (dışarı aktarmalar, önizlemeler veya temizlemeler gibi) veya eylemler listesini görüntüledi olduğunda bu etkinlik günlüğe kaydedilir. Bu etkinlik, kullanıcı belirli bir uyumluluk arama eylemını (dışarı aktarma gibi) veya Core eKbulma durumuyla ilişkilendirilmiş belirli bir eylemi görüntülerken de günlüğe kaydedilir. Kullanıcı bir arama eylemunu görüntüley kendisinde görüntülenmi, denetim kaydında, görüntülenen arama eyleminin kimliği yer alan. Kullanıcı yalnızca eylem listesini görüntülediyse, denetim kaydı bir eylem kimliği içermemektedir.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>eBulma etkinlikleri için ayrıntılı özellikler

Aşağıdaki tabloda, arama sonuçlarında listelenen bir eBulma etkinliğinin uç uç sayfasında bulunan özellikler açık bulunmaktadır. Denetim günlüğü arama sonuçlarını dışarı aktarsanız da bu özellikler CSV dosyasına dahil edilir. eBulma etkinliğinin denetim günlüğü kaydı, aşağıda listelenen her ayrıntılı özelliği içermez.
  
> [!TIP]
> Arama sonuçlarını dışarı aktarsanız, CSV dosyasında çok değerli bir özellikte aşağıdaki tabloda açıklanan ayrıntılı özellikleri içeren **AudtiData** adlı bir sütun yer alır. Power Query özelliğini kullanarak bu Excel her özelliğin kendi sütunu olacak şekilde birden çok sütuna bölebilirsiniz. Bu, bu özelliklerden bir veya birden fazlası için sıralama ve filtreleme sağlar. Daha fazla bilgi için, Denetim günlüğünde arama yapın bölümündeki "Arama sonuçlarını dosyaya aktarma" [bölümüne bakın](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Özellik**|**Açıklama**|
|:-----|:-----|
|Büyük//harf  <br/> |Oluşturulan, değiştirilen veya silinen eBulma örneğinin kimliği (GUID).  <br/> |
|ClientApplication  <br/> |eKbulma cmdlet etkinliklerinin bu özellik için **EMC** değeri vardır. Bu, etkinliğin uyumluluk merkezi GUI kullanılarak veya PowerShell'de cmdlet çalıştırarak gerçekleştirildiğini gösterir.  <br/> |
|ClientIP  <br/> |Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi, IPv4 veya IPv6 adres biçiminde görüntülenir.  <br/> |
|ClientRequestId  <br/> | eBulma etkinlikleri için bu özellik genellikle boştur.  <br/> |
|CmdletVersion  <br/> |Kuruluşta çalışan uyumluluk merkezi sürümünün derleme numarası.  <br/> |
|CreationTime  <br/> |eBulma etkinliğinin tamamlandıktan sonra Eşgüdümle Evrensel Saat (UTC) olarak tarih ve saat.  <br/> |
|EffectiveOrganization  <br/> |Microsoft 365 kuruluş adı.  <br/> |
|ExchangeLocations  <br/> |İçerik Exchange Online dahil olan veya bir eBulma durumunda ayrı ayrı yerleştirilen posta kutularının durumu.  <br/> |
|Dışlamalar  <br/> |eBulma durumunda içerik arama veya yerinde tutma dışında bırakılan posta kutusu veya site konumları.  <br/> |
|ExtendedProperties  <br/> |İçerik arama, içerik arama eylemi veya eBulma durumunda tutmanın ek özellikleri (nesne GUID, etkinlik gerçekleştirilirken kullanılan ilgili cmdlet ve cmdlet parametreleri gibi).  <br/> |
|Kimlik  <br/> |Rapor girdisi kimliği. Kimlik, denetim günlüğü girdisini benzersiz olarak tanımlar.  <br/> |
|NonPIIParameters  <br/> |Operation özelliğinde tanımlanan cmdlet ile kullanılan parametrelerin listesi (değer olmadan). Bu özellikte listelenen parametreler, Parameters özelliğinde listelenenlerle aynıdır.  <br/> |
|ObjectId  <br/> |Operation özelliğinde listelenen etkinlik tarafından oluşturulan, erişilen, değiştirilen veya silinen nesnenin GUID'si veya adı (örneğin, bir İçerik arama veya Temel eBulma örneği). Bu nesne, denetim günlüğü arama sonuçları öğe sütununda da tanımlanır.  <br/> |
|ObjectType  <br/> |Kullanıcının oluşturduğu, silmemiş veya değiştirmiş olduğu eBulma nesnesinin türü; örneğin, içerik arama eylemi (önizleme, dışarı aktarma veya temizleme), eBulma durumu veya içerik araması.  <br/> |
|Operation  <br/> |Gerçekleştirilen eBulma etkinliğine karşılık gelen işlem adı.  <br/> |
|OrganizationId  <br/> |Yardımcı kuruluş için Microsoft 365 GUID.  <br/> |
|Parametreler  <br/> |İlgili cmdlet ile kullanılan parametrelerin adı ve değeri.  <br/> |
|PublicFolderLocations  <br/> |İçerik aramada yer Exchange Online veya eBulma durumunda ayrı bir yerde bulunan ortak klasör konumları.  <br/> |
|Sorgu  <br/> |İçerik arama veya sorgu tabanlı tutma gibi etkinlikle ilişkilendirilmiş arama sorgusu.  <br/> |
|RecordType  <br/> |Kayıt tarafından gösterilen işlem türü. **18** değeri [, eBulma cmdlet etkinlikleri bölümünde listelenen bir etkinlikle ilgili olayı](#ediscovery-cmdlet-activities) gösterir. **24** değeri, eBulma etkinlikleri için arama ve görüntüleme bölümünde listelenen etkinlikle [ilgili olayı](#how-to-search-for-and-view-ediscovery-activities) gösterir.  <br/> |
|ResultStatus  <br/> |Eylemin (Operation özelliğinde belirtilen eylem) başarılı olup olmadığını gösterir.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Etkinliğin bir uyumluluk merkezi olayı olduğunu gösterir. Tüm eBulma etkinliklerinin bu özellik için **0** değeri olur.  <br/> |
|SharepointLocations  <br/> |İçerik SharePoint dahil olan veya bir eBulma durumunda ayrı ayrı yerleştirilen çevrimiçi siteler.  <br/> |
|StartTime  <br/> |eBulma etkinliğinin başlat alındığı Tarih ve Eşgüdümli Evrensel Saat (UTC) saat.  <br/> |
|UserId  <br/> |Kaydın günlüğe kaydedilmiş olmasıyla sonuç veren etkinliği (Operation özelliğinde belirtilen etkinlik) gerçekleştiren kullanıcı. Sistem hesapları (NT AUTHORITY\SYSTEM gibi) tarafından gerçekleştirilen eBulma etkinliğinin kayıtları da denetim günlüğüne dahil edilir.  <br/> |
|UserKey  <br/> |UserId özelliğinde tanımlanan kullanıcının alternatif kimliği. eBulma etkinlikleri için, bu özelliğin değeri normalde UserId özelliğiyle aynıdır.  <br/> |
|UserServicePlan  <br/> |Organizasyon tarafından kullanılan abonelik. eBulma etkinlikleri için bu özellik genellikle boştur.  <br/> |
|UserType  <br/> |İşlemleri gerçekleştirilen kullanıcının türü. Kullanıcı türü aşağıdaki değerlerle belirtilmiştir.  <br/> 0 Normal bir kullanıcı. 2 Kuruluş yöneticiniz. 3 Microsoft veri merkezi yöneticisi veya veri merkezi sistem hesabı. 4 Sistem hesabı. 5 Uygulama. 6 Hizmet sorumlusu. |
|Sürüm  <br/> |Günlüğe kaydedilen etkinliğin (Operation özelliği tarafından tanımlanan etkinlik) sürüm numarasını gösterir.  <br/> |
|workload  <br/> |Etkinliğin bulunduğu hizmet. eBulma etkinlikleri için değer **SecurityComplianceCenter'nedir**.  <br/> |
