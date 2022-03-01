---
title: Tahmini ve gerçek eBulma arama sonuçları arasındaki farklar
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
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Tahmini ve gerçek arama sonuçlarının, aramalarda eBulma araçlarıyla çalışma süresinde neden değişiklik göster Office 365.
ms.openlocfilehash: 16b63b96421cfbf3f9d67e1373061b49ff5db225
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032485"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Tahmini ve gerçek eBulma arama sonuçları arasındaki farklar

Bu konu, aşağıdaki eBulma araçlarından birini kullanarak Microsoft 365 için geçerlidir: 

- İçerik arama
- Core eKovery

eBulma aramasında çalıştırsanız, kullanmakta olduğunuz araç, arama ölçütlerine uyan öğe sayısını (ve bunların toplam boyutunu) tahminini verir. Örneğin, çalışma sayfasında bir arama Microsoft 365 uyumluluk merkezi, seçili aramanın uç uç sayfasında tahmini arama sonuçları görüntülenir.
  
![Arama uç sayfası üzerinde görüntülenen sonuçların tahmini.](../media/EstimatedSearchResults1.png)
  
Bu, sonuçları yerel bir bilgisayara ve arama sonuçlarıyla birlikte indirilen Dışarı Aktarma Özeti raporunda dışarı aktararak eBulma Dışarı Aktarma Aracı'da görüntülenen toplam boyut ve öğe sayısı tahminini aynıdır.
  
**eBulma Dışarı Aktarma aracında tahmini sonuçlar**

![eBulma Dışarı Aktarma aracında tahmini sonuçlar.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Dışarı Aktarma Özeti raporunda tahmini sonuçlar**

![Tahmini arama sonuçları Dışarı Aktarma Özeti raporuna dahil edilir.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Öte yandan, Dışarı Aktarma Özeti raporunun önceki ekran görüntüsünde fark ettiysiniz, indirilen gerçek arama sonuçlarının boyutu ve sayısı, tahmini arama sonuçlarının boyutundan ve sayısından farklıdır.
  
![Tahmin edilen ve indirilen arama sonuçları arasındaki fark.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Bu farkların bazı nedenleri şöyledir:
  
- **Sonuçların tahmin edilen yolu**. Arama sonuçlarının tahmini, arama sorgusu ölçütlerine uyan öğelerin tahminini (gerçek sayısını değil) ifade etmektir. Bu öğelerin tahminini Exchange için, kullanmakta olduğu eBulma aracı tarafından Exchange veritabanından arama ölçütlerine uyan ileti kimliklerinin listesi isteniyor. Ancak arama sonuçlarını dışarı aktarsanız, arama yeniden çalıştır alınır ve gerçek iletiler bu Exchange alınır. Dolayısıyla bu farklar, tahmini öğe sayısının ve gerçek öğe sayısının nasıl belirleneceği nedeniyle ortaya çıkan sonuçlar olabilir.

- **Arama sonuçlarını tahmin ve dışarı aktarma zamanı arasında yapılan değişiklikler**. Arama sonuçlarını dışarı aktarıyorken, arama dizininde arama ölçütlerine uyan en son öğeleri toplamak için arama yeniden başlatılır. Tahmin edilen arama sonuçlarının ne zaman topladığı ve ne zaman dışarı aktarıldıklarına kadar, arama ölçütlerine uyan başka öğeler de oluşturulmuş, gönderilmiş veya alınmıştır. Ayrıca, arama sonuçları dışarı aktar gelmeden önce içerik konumdan temiz aranmalarından dolayı artık arama dizininde yer alan öğelerin artık orada olmadığı tahmin ediliyor olabilir. Bu sorunu azaltmak için bir yol, eBulma arama için bir tarih aralığı belirtmektir. Bir diğer yol da, içerik konumlarını yerinde tutmak ve bu şekilde öğelerin korunmasını ve temiz olamamaktır. 

   Nadiren de olsa, bir tutma uygulandığında bile yerleşik takvim öğelerinin bakımı (kullanıcı tarafından düzenlenemez ama birçok arama sonucu içinde bulunur) zaman zaman kaldırılabilir. Takvim öğelerinin düzenli olarak kaldırılması, dışarı aktarılmış daha az öğeye neden olacak.

- **Bağımsız olmayan öğeler**. Arama için tekinde olmayan öğeler, tahmini ve gerçek arama sonuçları arasında farklara neden olabilir. Arama sonuçlarını dışarı aktararak, tek tek olmayan öğeleri  dahilebilirsiniz. Arama sonuçlarını dışarı aktarıyorsanız, dışarı aktaran başka öğeler de olabilir. Bu, tahmin edilen ve dışarı aktaran arama sonuçları arasında bir fark yaratabilir.

    İçerik arama aracını kullanırken, arama sonuçlarını dışarı aktarsanız bile, bağımsız öğeleri dahil seçeneğiniz vardır. Arama tarafından döndürülen, bağımsız olmayan öğelerin sayısı, diğer tahmini arama sonuçlarıyla birlikte çıkış sayfasında listelenir. Hiçbirindex olmayan öğeler de tahmini arama sonuçlarının toplam boyutuna dahil edilir. Arama sonuçlarını dışarı aktarken, tek tek öğeleri dahil alma veya dahilma seçeneğiniz vardır. Bu seçeneklerin nasıl yapılandırıldığında, indirilen tahmini arama sonuçları ile gerçek arama sonuçları arasında farklar olabilir.

- **Tüm içerik konumlarını içeren İçerik arama sonuçlarını dışarı aktarma**. Sonuçları dışarı aktarmış olduğunuz arama, kurumdaki tüm içerik konumlarında yapılan bir arama ise, yalnızca içerik konumlarından gelen ve arama ölçütleriyle eşleşmesi gereken öğelerin bulunduğu tek tek bağımsız öğeler dışarı aktarıldı. Başka bir deyişle, bir posta kutusunda veya sitede hiç arama sonucu bulunamıyorsa, bu posta kutusu veya sitedeki tek hiçbirinde olmayan öğeler dışarı aktar olmaz. Bununla birlikte, tüm içerik konumlarından (arama sorgusuyla eşleşmeen hiç öğe içermemiş olanlar dahil olanlar bile) içeremeyen tek tek öğeler, tahmini arama sonuçlarına dahil edilir.

    Alternatif olarak, dışarı aktarıyorsanız arama sonuçları dahil edilen belirli içerik konumlarından çıkarılacaksa, aramada belirtilen tüm içerik konumlarından tek tek hariç tutulacak tek tek öğeler (arama ölçütleri tarafından hariç tutulmayacak) dışarı aktarılacaktır. Bu durumda, tahminiinde olmayan öğelerin sayısı ve dışarı aktarıldık, ancak dışarı aktarlanmamış öğelerin sayısı aynı olur.

    Kurumdaki her konumdan tekninde olmayan öğeleri dışarı aktarmama nedeni, dışarı aktarma hataları olasılığını artırarak arama sonuçlarını dışarı aktarma ve indirmenin zamanını artırmasıdır.

- **Satır ve satırlardaki SharePoint OneDrive, arama tahminlerine dahil değildir**. Sitelerden ve SharePoint hesaplarından gelen OneDrive İş, tahmini arama sonuçlarına dahil değildir. Bunun nedeni, SharePoint dizine eksiz öğeler için veri içermemiş olmasıdır. Arama tahminlerine yalnızca posta kutularından gelen, satırlanmamış öğeler dahil edilir. Bununla birlikte, arama sonuçlarını dışarı aktarmada, bağımsız öğeler de dahil olursanız, SharePoint ve OneDrive bu öğeler de dahil edilir ve bu da gerçekten dışarı aktaran öğelerin sayısını artıracaktır. Bunun sonucunda, tahmini sonuçlarla (SharePoint ve OneDrive sitelerine ekli olmayan) gerçek öğeler arasında farklar olur. Yalnızca arama ölçütlerine uyan öğeler içeren içerik konumlarından tekinde olmayan öğeleri dışarı aktarma kuralı bu durumda da geçerlidir.

- **Belge ve sürüm SharePoint OneDrive**. Bir SharePoint ve OneDrive hesapları aranıyorsa, bir belgenin birden çok sürümü tahmini arama sonuçları sayısına dahil değildir. Ancak, arama sonuçlarını dışarı aktararak tüm belge sürümlerini ekleme seçeneğiniz vardır. Arama sonuçlarını dışarı aktaracak belge sürümleri eklersiniz, dışarı aktarılmış öğelerin gerçek sayısı (ve toplam boyutu) artırılacaktır.

- **SharePoint seçin**. SharePoint'daki klasörlerin adı bir arama sorgusuyla eşebiliyorsa, arama tahminsinde bu klasörlerin sayısı (ancak bu klasörlerdeki öğelerin değil) yer alır. Arama sonuçlarını dışarı aktarsanız bile, klasördeki öğeler dışarı aktarıldı ancak gerçek klasör dışarı aktarıldı. Sonuçta, dışarı aktarıldı olarak dışarı aktaran öğelerin sayısının tahmini arama sonucu sayısından daha fazla olur. Bir klasör boşsa, gerçek klasör dışarı aktarılamay olduğundan dışarı aktaran gerçek arama sonuçlarının sayısı bir öğeyle azalır.

- **SharePoint seçin**. Bir liste adının SharePoint bir arama sorgusuyla eş eşleşmesi, arama tahminini listede yer alan tüm öğelerin sayısını içerir. Arama sonuçlarını dışarı aktarsanız bile, liste (ve liste öğeleri) tek bir CSV dosyası olarak dışarı aktarıldı. Bu, gerçekten dışarı aktaran gerçek öğe sayısını azaltır. Listede ekler varsa, ekler ayrı belgeler olarak dışarı aktarıldı ve bu da dışarı aktarıldı öğe sayısını artıracaktır.

- **Ham dosya biçimleri ve dışarı aktarıldı dosya biçimleri**. Daha Exchange için arama sonuçlarının tahmini boyutu, işlenmemiş veya işlenmemiş ileti Exchange hesaplanır. Bununla birlikte, e-posta iletileri BIR PST dosyasında veya tek tek iletiler olarak (EML dosyaları olarak biçimlendirilmiş) dışarı aktarıldı. Bu dışarı aktarma seçeneklerinin her ikisi de ham veya ham Exchange biçimden farklı bir dosya biçimi kullanır ve bu da dışarı aktarıldı toplam dosya boyutunun tahmini dosya boyutundan farklı olmasına neden olur.

- **Dışarı aktarma sırasında Exchange yinelemelerini de.** Diğer Exchange için, yinelemenin de-yinelemesi dışarı aktarıldı öğe sayısını azaltır. Dışarı aktararak arama sonuçlarını yineleme seçeneğiniz vardır. Birden Exchange iletilerde, birden çok posta kutusunda bulunsa bile bu iletinin yalnızca bir örneği dışarı aktarıldı anlamına gelir. Tahmini arama sonuçları bir iletinin her örneğini içerir. Dolayısıyla, arama sonuçlarını dışarı aktarmada yinelemeyi de geri alma seçeneğini kullanırsanız, dışarı aktarılan gerçek öğe sayısı tahmini öğe sayısından oldukça az olabilir.

Arama sonuçları raporu (Results.csv dosya) her yinelenen ileti için bir girdi içerir ve yinelenen iletinin bulunduğu kaynak posta kutusunu tanımlar. Bu, yinelenen ileti içeren tüm posta kutularını tanımlamanıza yardımcı olur.

> [!NOTE]
> Arama sonuçlarını dışarı aktarabilir veya yalnızca  raporları indirirken Şifrelenmiş veya tanınmayan biçime sahip öğe bulundur seçeneğini seçmezseniz, dizin hatası raporları indirilir ancak bu raporlarda hiçbir girdisi yok olur. Bu, hiçbir dizin hatası olmadığını gösterir. Yalnızca, bağımsız olmayan öğelerin dışarı aktarmaya dahil olmadığı anlamına gelir.
