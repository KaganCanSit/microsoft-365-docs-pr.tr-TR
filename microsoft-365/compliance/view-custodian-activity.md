---
title: Yediemin denetim etkinliğini görüntüleme
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Davanız Advanced eDiscovery koruyucular etkinliğine kolayca erişmek ve bu etkinlikte arama yapmak için Özel Koruyucu Yönetim aracını kullanın.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: d0ea6e94bd48c055cac23d8a96477e036369dd5c
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018807"
---
# <a name="view-custodian-audit-activity"></a>Yediemin denetim etkinliğini görüntüleme

Kullanıcının belirli bir belgeyi görüntüp görüntülemediğni veya posta kutusundan bir öğeyi temiz olup bulamadığnı bulmanız mı gerekiyor? Advanced eDiscovery artık denetim günlüğü arama Microsoft 365 uyumluluk merkezi aracıyla tümleştirilmiştir. Bu eklenmiş deneyimi kullanarak, Advanced eDiscovery Custo bir Management aracını kullanarak, davanız içindeki koruyucular için etkinliklere kolayca erişerek ve bu etkinliklerde aramaarak araştırmanızı kolaylaştırabilirsiniz.

## <a name="get-permissions"></a>İzinleri al

Denetim günlüğünde arama View-Only için Exchange Online Günlükleri veya Denetim Günlükleri rolüne atanmış Exchange Online gerekir. Varsayılan olarak, bu roller yönetim merkezinin İzinler sayfasında yer alan Uyumluluk Yönetimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. Kullanıcıya Advanced eDiscovery denetim günlüğünde minimum düzeyde ayrıcalıkla arama yapma olanağı vermek için, Exchange Online'te özel bir rol grubu oluşturabilir, View-Only Denetim Günlükleri veya Denetim Günlükleri rolünü ekleyebilir ve sonra da kullanıcıyı yeni rol grubunun bir üyesi olarak ebilirsiniz. Daha fazla bilgi için bkz. Exchange Online'da rol gruplarını yönetme.

> [!IMPORTANT]
> Kullanıcıya denetim View-Only İzinler sayfasındaki Denetim Günlükleri veya Denetim Günlükleri rolü atarsanız, Microsoft 365 uyumluluk merkezi günlüğünde arama yapmak mümkün olmayacaktır. İzinleri aynı dosyanın Exchange Online. Çünkü, denetim günlüğünde arama yapmak için kullanılan temel cmdlet, bir Exchange Online cmdlet'tir.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>1. Adım: Denetim günlüğünde, özel denetim tarafından gerçekleştirilen etkinlikler için arama yapın

1. **eBulma E-> Advanced eDiscovery** gidin ve vakayı açın.
  
2. Kaynaklar **sekmesine** tıklayın.
  
3. Özel **görünümler sayfasında**, listeden bir özel bilgi seçin ve sonra da uçarak giriş sayfasındaKimlik etkinliğini görüntüle'ye tıklayın.

    Custo bu etkinlikleri arama sayfası görüntülenir. Önceki adımda seçtiğiniz **Custo custo bir** açılan kutusunda görüntülendiğinden emin olun. Açılan kutuda farklı koruyucular seçebilirsiniz, ancak bir defada yalnızca tek bir koruyucu için etkinlik arayabilirsiniz.

    ![Custo bir etkinlikler arama sayfası.](../media/AeDCustodianActivities1.png)
   
4. Aşağıdaki arama ölçütlerini yapılandırma:
      
   1. **Etkinlikler** - Arayabilirsiniz etkinlikleri görüntülemek için açılan listeye tıklayın. Siz arama çalıştırdikten sonra, yalnızca seçili etkinliklere yönelik denetim kayıtları görüntülenir. Tüm **etkinlikler için sonuçları göster'i seçerek** , diğer arama ölçütlerine uyan koruyucu tarafından gerçekleştirilen tüm etkinliklere yönelik sonuçlar görüntülenir.

      ![Etkinlikler Listesi.](../media/CustodianActivityAudit.PNG)
      
   1. **Başlangıç tarihi ve Bitiş tarihi** - Bir tarih ve saat aralığı seçerek, o dönem içinde 4. Son yedi gün varsayılan olarak seçilidir. Tarih ve saat, Eşgüdümli Evrensel Saat (UTC) biçiminde görüntülenir. Belirterek en uzun tarih aralığı bir yıldır.
      
   1. **Custodians** - Bu kutuya tıklayın ve ardından arama sonuçlarını görüntülemek için belirli bir custo custood seçeneğini seçin. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliğin denetim kayıtları, sonuç listesinde görüntülenir.
      
5. Tıkla ![Arama Düğmesi.](../media/SearchButton.PNG)  seçin. Arama sonuçları yüklenir ve birkaç dakika sonra Custo custo custs search sayfasındaki Sonuçlar altında görüntülenir. 

## <a name="step-2-view-the-audit-log-search-results"></a>2. Adım: Denetim günlüğü arama sonuçlarını görüntüleme

Denetim günlüğü aramanın sonuçları Custo audit günlüğü sayfasındaki Sonuçlar altında görüntülenir. 150 olaylık artışlarla en çok 5.000 (en yeni) olay görüntülenir. Daha fazla olay görüntülemek için, Sonuçlar bölmesindeki kaydırma çubuğunu kullanabilir veya Shift + End tuşlarına basarak sonraki 150 olayları görüntüleyebilirsiniz.

Sonuçlar, arama tarafından döndürülen her olay hakkında aşağıdaki bilgileri içerir.
- **Tarih**: Olayın olduğu tarih ve saat (UTC biçiminde).

- **IP adresi**: Etkinlik günlüğe kaydedilirken kullanılan cihazın IP adresi. IP adresi, IPv4 veya IPv6 adres biçiminde görüntülenir.

- **Kullanıcı**: Olayı tetikleyen eylemi gerçekleştiren kullanıcı (veya hizmet hesabı).

- **Etkinlik**: Kullanıcı tarafından gerçekleştirilen etkinlik. Bu değer, Etkinlikler açılan listesinde seçtiğiniz etkinliklere karşılık gelen bir değerdir. Yönetici denetim günlüğünden Exchange için, bu sütundaki değer bir Exchange cmdlet'tir.

- **Öğe**: İlgili etkinliğin sonucunda oluşturulan veya değiştirilen nesne. Örneğin, görüntülenen veya değiştirilen dosya ya da güncelleştirilen kullanıcı hesabı. Tüm etkinliklerin bu sütunda değeri yoktur.

- **Ayrıntı**: Etkinlik hakkında ek ayrıntılar. Bir kez daha, tüm etkinliklerin değeri olmaz.

## <a name="step-3-filter-the-search-results"></a>3. Adım: Arama sonuçlarını filtreleme

Sıralamaya ek olarak, denetim günlüğü aramalarının sonuçlarına da filtre siniz. Bu, belirli bir kullanıcı veya etkinlik için sonuçları hızla filtrelemenize yardımcı olabilir. 

Sonuçları filtrelemek için:

 1. Denetim günlüğü araması oluşturun ve çalıştırın.
  
2. Sonuçlar görüntülendiğinde, Sonuçları **filtrele'ye tıklayın**.
 
3. Her sütun başlığının altında anahtar sözcük kutuları görüntülenir.
  
4. Sütun başlığının altındaki kutulardan birini tıklatın ve filtreyi kullandığınız sütuna bağlı olarak bir sözcük veya tümcecik yazın. Sonuçlar, filtrenize uygun olayları görüntülemek için dinamik olarak yeniden görüntülenir.
  
5. Filtreyi temizlemek için, filtre **kutusunda X'e** tıklayın veya yalnızca Filtreyi **gizle'ye tıklayın**.

## <a name="export-the-search-results-to-a-file"></a>Arama sonuçlarını dosyaya aktarma

Denetim günlüğü aramalarının sonuçlarını yerel bilgisayarınızdan bir virgülle ayrılmış değer (CSV) dosyasına aktarabilirsiniz. Bu dosyayı başka bir dosyada Microsoft Excel arama, sıralama, filtreleme ve tek sütunu (çok değerli hücreler içeren bir sütunu) birden çok sütuna bölme gibi özellikleri kullanabilirsiniz.

1. Denetim günlüğü arama çalıştırın ve ardından istediğiniz sonuçları elde inceye kadar arama ölçütlerini düzeltin.
  
2. Sonuçları dışarı aktar'a tıklayın ve aşağıdaki seçeneklerden birini belirleyin:

    - **Yüklenen sonuçları kaydet:** Yalnızca Custo audit günlük araması sayfasındaki **Sonuçlar'ın** altında görüntülenen girdileri dışarı **aktarmayı bu seçeneği** belirtin. İndirilen CSV dosyası, sayfada görüntülenen sütunların (ve verilerin) aynılarını (Tarih, Kullanıcı, Etkinlik, Öğe ve Ayrıntılar) içerir. CSV dosyasına, denetim günlüğü **girdilerinden** daha fazla bilgi içeren bir sütun daha (Diğer başlıklı) ek bir sütun ek olarak ve bu sütun da ek olarak gösterilir. Denetim günlüğü araması sayfasına yüklenen (ve görüntülenebilir) sonuçların aynılarını dışarı aktarıyor olun, çünkü en çok 5.000 girdi dışarı aktarılabilir.
        
    - **Tüm sonuçları indirin:** Denetim günlüğünden arama ölçütlerine uyan tüm girdileri dışarı aktaracak şekilde bu seçeneği belirtin. Büyük bir arama sonuçları kümesi için, Bu seçeneği kullanarak Denetim günlüğünden gelen tüm girdilerin yanı sıra **Custo audit** günlüğü araması sayfasında görüntülenebilir 5.000 sonucu da indirebilirsiniz. Bu seçenek, ham verileri denetim günlüğünden CSV dosyasına indirir ve Denetim Verileri adlı sütunda denetim günlüğü girdisinde yer alan ek bilgileri içerir. Bu dışarı aktarma seçeneğini belirtirseniz dosyanın indirilsi daha uzun sürebilir çünkü dosya, diğer seçeneği belirtirseniz indirilen dosyadan çok daha büyük olabilir.
    
      > [!IMPORTANT]
      > Tek bir denetim günlüğü aramalarından CSV dosyasına en çok 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den çok olay olduğunu varsayabilirsiniz. Bu sınırdan fazlasını dışarı aktarmayı deneyin ve denetim günlüğü girdilerinin sayısını azaltmak için bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girdiyi dışarı aktaracak şekilde, daha küçük tarih aralıklarında birden çok arama çalıştırmaya gerek kullanabilirsiniz.
        

3. Dışarı aktarma seçeneğini kullandıktan sonra, pencerenin en altında CSV dosyasını açmanızı, İndirilenler klasörüne kaydetmenizi veya belirli bir klasöre kaydetmenizi içeren bir ileti görüntülenir.

Denetim günlüğü arama sonuçlarını görüntüleme, filtreleme veya dışarı aktarma hakkında daha fazla bilgi için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)
