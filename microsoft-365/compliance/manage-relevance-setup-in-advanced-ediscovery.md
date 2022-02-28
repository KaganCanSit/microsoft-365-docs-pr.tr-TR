---
title: Advanced eDiscovery'te İlgi Derecesi kurulumunu Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: fd6be6d3-2e8d-449d-9851-03ab7546e6aa
ROBOTS: NOINDEX, NOFOLLOW
description: Dosyaları ilgi derecelerine göre puanla almak ve analitik sonuçlar oluşturmak Advanced eDiscovery'de İlgi Düzeyi eğitimi ayarlama önerilerini okuyun.
ms.openlocfilehash: bed912c0631511e9d3d4839e5d6925de79554163
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988088"
---
# <a name="manage-relevance-setup-in-advanced-ediscovery-classic"></a>İlgi Düzeyi kurulumunu Advanced eDiscovery (klasik)

> [!NOTE]
> Advanced eDiscovery için, Office 365 E3 Uyumluluk eklentili bir kullanıcı veya E5 aboneliği gerekir. Bu plana sahip değil ve deneme sürümü Advanced eDiscovery, [Office 365 Kurumsal E5 deneme sürümüne Office 365 Kurumsal](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 Advanced eDiscovery Uygunluk teknolojisi, dosyaları uygunluk durumlarına göre puanlama için uzman rehberli yazılımlar kullanır. Advanced eDiscovery Uygunluk Durumu, Erken Vaka Değerlendirmesi (ECA), içerik derlemesi ve dosya örneği gözden geçirme için kullanılabilir. 
  
 Advanced eDiscovery, Uygunluk eğitimi için bileşenleri ve davayla ilgili dosyaların etiketlerini içerir. Advanced eDiscovery, her dosya için İlgi Dereceleri sağlamak üzere İlgili ve İlgili Değil dosyalarının eğitimli örneklerinden bilgi verir ve dosya gözden geçirme işlemi sırasında ve sonrasında kullanılmaktadır. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>İlgi Düzeyi eğitimi ayarlama yönergeleri

 eBulma Öncesi'ninde **, Vakalar** penceresinde bir vaka seçin ve Vakaya **git'e tıklayın**. İlgi **Derecesi** **ayarı'nı**\> tıklatın. İlgi Düzeyini ayarlamak için bu önerilen yönergeleri izleyin. 
  
- **Etiketleme**: Tutarlılık eğitim sürecinin etkililiği, uzmanın dosya örneklerini hassas ve tutarlılıkla etiketleme yeteneğine bağlıdır.

- **Olay sorunları**:
  
  - Her sorunda, İlgi Düzeyi eğitim süreci boyunca aynı uzmanı kullanın. Aynı sorunun birden çok uzman tarafından aynı anda etiketlemeye izin verilmez.
  
  - Her dosya grubunun yalnızca belirli bir konuyla ilgili olup olmadığını belirler.

  - Sorun çok genel olarak tanımlanmışsa, Advanced eDiscovery çok fazla dosya getirebilirsiniz. Sorun çok dar bir şekilde tanımlanmışsa, İlgi Düzeyi eğitim süreci daha fazla zaman alabilirsiniz. 

  - Her uygun eğitim döngüsü sırasında, Advanced eDiscovery tek bir etkin soruna odaklanır ve buna uygun olarak örnek sonuçlar görüntülenir.

  - Çok soruna neden olan bir senaryoda Örnekleme modu, işlemeye dahil edilecek sorunların seçimini sağlar. "Kapalı" olarak tanımlanan sorunlar Örnekleme modu değiştirilene kadar işlanmaz. Bir sorun yalnızca bir uzman için "boşta" veya "açık" olabilir.

  - Advanced eDiscovery ayrıcalık dosyaları oluşturmak için bu dosyalar kullanılabilir. Ayrıcalık için ayrı bir sorun ayarlayın. Mümkünse, önce ilgi derecesi için eğitin ve sonra yalnızca içerikli kümede ayrıcalık için eğitin (kültürlü kümeyi ayrı bir vaka olarak yeniden yükleyin). 

  - Toplu işlem hesaplaması, yalnızca açık örnekler olmadığınız zaman yapılabilir (Toplu Hesaplama tıklatilirken, açık örneklere sahip kullanıcıların bir listesi görüntülenir). Diğer kullanıcıların örneklerini "kapatmak" için (bu işlem yalnızca bu kullanıcılar bu örnekleri etiketlemezse yapılır), bir Yönetici "Uygunlık derecesini değiştir" yardımcı programını "Tüm kullanıcılar örneği" seçeneğiyle kullanabilir.

- **Meta** veriler: Advanced eDiscovery üzerinde odaklanan verilerdir. Meta verileri ilgi düzeyi ölçütleri kapsamında dikkate değerlendirmez.

- **Zenginlik**: Bir sorunun Zenginliği Değerlendirme'den sonra %3'den azsa, uygunluğu eğitimi olarak bilinen Uygun ve uygun değil dosyalarına göz önünde bulundurabilirsiniz.

- **Dosya boyutu**: Büyük dosyalar (ayıklanan metnin 5.242.880 karakteri üzerinde) İlgi Düzeyi'ne göre göz ardı edilir. Dosyalar İlgi Düzeyi eğitim sürecine katılmaz ve Toplu Hesaplama'nın ardından bir İlgi Düzeyi puanı almaz. 5 MB'den büyük dosyalar Değerlendirme kümesine dahil olabilir.

## <a name="setting-up-case-issues"></a>Büyük/harf sorunlarını ayarlama

Bu bölümde açıklanan parametreler uygun Advanced eDiscovery **uygun olacak şekilde** \> **kullanılabilir**.
  
- Sorunlar, dosyaları eğitecek bir kullanıcıya atanabilir.

- Bundan sonra, alınan dosyaların işlenen yüke eklenmiş olması gerekir.

- Sorunları dikkatle tanımlayın ve sırayın, çünkü bu ilgi düzeyi eğitim sonuçlarını etkileyesin.

Parametreler ayar olduktan sonra, gözden geçiren / uzman Uygunlik sekmesinde dosyaları **eğitime başlayabilir** .
