---
title: Yediemin denetim etkinliğini görüntüleme
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: eKeşif (Premium) Koruyucu Yönetimi aracını kullanarak olayınızdaki koruyucular için etkinliğe kolayca erişip arama gerçekleştirin.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 3ead391eee7fc35a66a0d9472278ee75878de4df
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627007"
---
# <a name="view-custodian-audit-activity"></a>Yediemin denetim etkinliğini görüntüleme

Kullanıcının belirli bir belgeyi görüntüleyip görüntülemediğini veya bir öğeyi posta kutusundan temizleyip temizlemediğini bulmanız mı gerekiyor? Microsoft Purview eKeşif (Premium) artık Microsoft Purview uyumluluk portalı mevcut denetim günlüğü arama aracıyla tümleştirilmiştir. Bu ekli deneyimi kullanarak, eBulma (Premium) Koruyucu Yönetimi aracını kullanarak olayınızdaki koruyucular için etkinliğe kolayca erişerek ve etkinlikte arama yaparak araştırmanızı kolaylaştırabilirsiniz.

## <a name="get-permissions"></a>İzinleri alma

Denetim günlüğünde arama yapmak için Exchange Online'da View-Only Denetim Günlükleri veya Denetim Günlükleri rolüne atanmış olmanız gerekir. Varsayılan olarak, bu roller <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezindeki</a> İzinler sayfasındaki Uyumluluk Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. Kullanıcıya en düşük ayrıcalık düzeyiyle eBulma (Premium) denetim günlüğünde arama yapma olanağı vermek için, Exchange Online özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve kullanıcıyı yeni rol grubunun üyesi olarak ekleyebilirsiniz. Daha fazla bilgi için bkz. Exchange Online rol gruplarını yönetme.

> [!IMPORTANT]
> Bir kullanıcıya uyumluluk portalındaki İzinler sayfasında Denetim Günlükleri veya Denetim Günlükleri rolünü View-Only atarsanız, denetim günlüğünde arama yapamaz. İzinleri Exchange Online atamanız gerekir. Bunun nedeni, denetim günlüğünde arama yapmak için kullanılan temel cmdlet'in Exchange Online bir cmdlet olmasıdır.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>1. Adım: Bir koruyucu tarafından gerçekleştirilen etkinlikler için denetim günlüğünde arama yapma

1. **eBulma > eBulma (Premium)** bölümüne gidin ve servis talebini açın.
  
2. **Kaynaklar** sekmesine tıklayın.
  
3. **Koruyucular** sayfasında, listeden bir koruyucu seçin ve açılır sayfada **Koruyucu etkinliğini görüntüle'ye** tıklayın.

    Koruyucu etkinlikleri arama sayfası görüntülenir. Önceki adımda seçtiğiniz koruyucunun **, Koruyucu** açılan kutusunda görüntülendiğini unutmayın. Açılan kutudan farklı koruyucular seçebilirsiniz, ancak aynı anda yalnızca bir koruyucunun etkinliklerini arayabilirsiniz.

    ![Koruyucu etkinlikler arama sayfası.](../media/AeDCustodianActivities1.png)
   
4. Aşağıdaki arama ölçütlerini yapılandırın:
      
   1. **Etkinlikler** - Arayabileceğiniz etkinlikleri görüntülemek için açılan listeye tıklayın. Aramayı çalıştırdıktan sonra yalnızca seçili etkinliklere ilişkin denetim kayıtları görüntülenir. **Tüm etkinlikler için sonuçları göster** seçildiğinde, koruyucu tarafından gerçekleştirilen ve diğer arama ölçütlerine uyan tüm etkinliklerin sonuçları görüntülenir.

      ![Etkinliklerin Listesi.](../media/CustodianActivityAudit.PNG)
      
   1. **Başlangıç tarihi ve Bitiş tarihi** - Bu dönemde gerçekleşen olayları görüntülemek için bir tarih ve saat aralığı seçin. Son yedi gün varsayılan olarak seçilir. Tarih ve saat Eşgüdümlü Evrensel Saat (UTC) biçiminde gösterilir. Belirtebileceğiniz maksimum tarih aralığı bir yıldır.
      
   1. **Koruyucular** - Bu kutuya tıklayın ve arama sonuçlarını görüntülemek üzere belirli bir koruyucu seçin. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliğin denetim kayıtları sonuç listesinde görüntülenir.
      
5. Tıklatın ![Arama Düğmesi.](../media/SearchButton.PNG)  arama ölçütlerinizi kullanarak aramayı çalıştırmak için. Arama sonuçları yüklenir ve birkaç dakika sonra Koruyucu Etkinlikleri arama sayfasındaki Sonuçlar altında görüntülenir. 

## <a name="step-2-view-the-audit-log-search-results"></a>2. Adım: Denetim günlüğü arama sonuçlarını görüntüleme

Denetim günlüğü aramasının sonuçları, Koruyucu Denetim günlüğü sayfasındaki Sonuçlar altında görüntülenir. En fazla 5.000 (en yeni) olay, 150 olaylık artışlarla görüntülenir. Daha fazla olay görüntülemek için Sonuçlar bölmesindeki kaydırma çubuğunu kullanabilir veya Shift + End tuşlarına basarak sonraki 150 olayı görüntüleyebilirsiniz.

Sonuçlar, arama tarafından döndürülen her olay hakkında aşağıdaki bilgileri içerir.
- **Tarih**: Olayın gerçekleştiği tarih ve saat (UTC biçiminde).

- **IP adresi**: Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi IPv4 veya IPv6 adres biçiminde görüntülenir.

- **Kullanıcı**: Olayı tetikleyen eylemi gerçekleştiren kullanıcı (veya hizmet hesabı).

- **Etkinlik**: Kullanıcı tarafından gerçekleştirilen etkinlik. Bu değer, Etkinlikler açılan listesinde seçtiğiniz etkinliklere karşılık gelir. Exchange yöneticisi denetim günlüğündeki bir olay için bu sütundaki değer bir Exchange cmdlet'idir.

- **Öğe**: İlgili etkinliğin sonucu olarak oluşturulan veya değiştirilen nesne. Örneğin, görüntülenen veya değiştirilen dosya veya güncelleştirilen kullanıcı hesabı. Tüm etkinliklerin bu sütunda değeri yoktur.

- **Ayrıntı**: Etkinlik hakkında ek ayrıntılar. Yine, tüm etkinliklerin bir değeri olmaz.

## <a name="step-3-filter-the-search-results"></a>3. Adım: Arama sonuçlarını filtreleme

Sıralamaya ek olarak, denetim günlüğü aramasının sonuçlarını da filtreleyebilirsiniz. Bu, belirli bir kullanıcı veya etkinlik için sonuçları hızla filtrelemenize yardımcı olabilir. 

Sonuçları filtrelemek için:

 1. Denetim günlüğü araması oluşturun ve çalıştırın.
  
2. Sonuçlar görüntülendiğinde **Sonuçları filtrele'ye** tıklayın.
 
3. Anahtar sözcük kutuları her sütun üst bilgisinin altında görüntülenir.
  
4. Sütun üst bilgisinin altındaki kutulardan birine tıklayın ve filtrelediğiniz sütuna bağlı olarak bir sözcük veya tümcecik yazın. Sonuçlar, filtrenizle eşleşen olayları görüntülemek için dinamik olarak yeniden okunur.
  
5. Filtreyi temizlemek için, filtre kutusunda **X** işaretine tıklayın veya **filtreyi gizle'ye** tıklayın.

## <a name="export-the-search-results-to-a-file"></a>Arama sonuçlarını bir dosyaya aktarma

Denetim günlüğü aramasının sonuçlarını yerel bilgisayarınızdaki virgülle ayrılmış değer (CSV) dosyasına aktarabilirsiniz. Bu dosyayı Microsoft Excel'de açabilir ve tek bir sütunu (çok değerli hücreler içeren) birden çok sütuna bölme, sıralama, filtreleme ve bölme gibi özellikleri kullanabilirsiniz.

1. Bir denetim günlüğü araması çalıştırın ve istediğiniz sonuçları elde edene kadar arama ölçütlerini düzeltin.
  
2. Sonuçları dışarı aktar'a tıklayın ve aşağıdaki seçeneklerden birini belirleyin:

    - **Yüklenen sonuçları kaydedin:** Yalnızca **Koruyucu Denetim günlüğü arama** sayfasındaki **Sonuçlar** altında görüntülenen girdileri dışarı aktarmak için bu seçeneği belirleyin. İndirilen CSV dosyası sayfada görüntülenen sütunların (ve verilerin) aynısını içerir (Tarih, Kullanıcı, Etkinlik, Öğe ve Ayrıntılar). CSV dosyasında denetim günlüğü girdisinden daha fazla bilgi içeren ek bir sütun ( **Daha fazla** başlıklı) bulunur. Denetim günlüğü arama sayfasında yüklenen (ve görüntülenebilir) sonuçları dışarı aktardığınız için en fazla 5.000 girdi dışarı aktarılır.
        
    - **Tüm sonuçları indirin:** Denetim günlüğünden arama ölçütlerine uyan tüm girişleri dışarı aktarmak için bu seçeneği belirleyin. Büyük bir arama sonuçları kümesi için, Denetim günlüğü arama sayfasında görüntülenebilen 5.000 sonuca ek olarak denetim **günlüğündeki** tüm girişleri indirmek için bu seçeneği belirleyin. Bu seçenek, ham verileri denetim günlüğünden CSV dosyasına indirir ve AuditData adlı bir sütundaki denetim günlüğü girdisinden ek bilgiler içerir. Bu dışarı aktarma seçeneğini belirlerseniz dosyanın indirilmesi daha uzun sürebilir çünkü diğer seçeneği belirlerseniz dosya indirilen dosyadan çok daha büyük olabilir.
    
      > [!IMPORTANT]
      > Tek bir denetim günlüğü aramasından CSV dosyasına en fazla 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den fazla olay olduğunu varsayabilirsiniz. Bu sınırdan daha fazlasını dışarı aktarmak için, denetim günlüğü girdilerinin sayısını azaltmak için bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girişi dışarı aktarmak için daha küçük tarih aralıklarıyla birden çok arama çalıştırmanız gerekebilir.
        

3. Dışarı aktarma seçeneğini seçtikten sonra pencerenin alt kısmında CSV dosyasını açmanızı, İndirilenler klasörüne kaydetmenizi veya belirli bir klasöre kaydetmenizi isteyen bir ileti görüntülenir

Denetim günlüğü arama sonuçlarını görüntüleme, filtreleme veya dışarı aktarma hakkında daha fazla bilgi için bkz. [Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.
