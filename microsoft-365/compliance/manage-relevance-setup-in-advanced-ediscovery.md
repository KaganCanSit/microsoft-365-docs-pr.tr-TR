---
title: eBulma'da İlgi ayarlarını yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: EBulma'da (Premium) ilgili dosyaları puanlama ve analiz sonuçları oluşturma ile ilgili ilgi eğitimi ayarlama önerilerini okuyun.
ms.openlocfilehash: be9347468ef39fd5d6ae254ff4eb662a795f4f0b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098526"
---
# <a name="manage-relevance-setup-in-ediscovery-premium-classic"></a>eBulma (Premium) (klasik) içinde İlgi ayarlarını yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Microsoft Purview eKeşif (Premium), kuruluşunuz için Gelişmiş Uyumluluk eklentisi veya E5 aboneliğine sahip bir Office 365 E3 gerektirir. Bu plana sahip değilseniz ve eKeşif 'i (Premium) denemek istiyorsanız[, E5 Office 365 Kurumsal deneme sürümüne kaydolabilirsiniz](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 eKeşif (Premium) İlgi teknolojisi, dosyaları ilgilerine göre puanlama için uzman destekli yazılım kullanıyor. eBulma (Premium) İlgisi, Erken Vaka Değerlendirmesi (ECA), itlaf ve dosya örneği incelemesi için kullanılabilir. 
  
 eBulma (Premium), bir servis talebiyle ilgili dosyaların ilgi eğitimi ve etiketlenmesi için bileşenler içerir. eBulma (Premium), her dosya için İlgi puanları sağlamak üzere eğitilen İlgili ve İlgili Olmayan dosya örneklerinden bilgi edinerek, dosya gözden geçirme işlemi sırasında ve sonrasında kullanılabilecek analitik sonuçlar oluşturur. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>İlgi eğitimini ayarlama yönergeleri

 Önceden eBulma'da Servis **Talepleri** penceresinde bir servis talebi seçin ve Büyük **/küçük harfe git'e** tıklayın. **İlgi** \> **İlgisi kurulumu'nu** tıklatın. İlgiyi ayarlamak için bu önerilen yönergeleri izleyin. 
  
- **Etiketleme**: Yinelemeli İlgi eğitim sürecinin etkinliği, uzmanın dosya örneklerini hassas ve tutarlılıkla etiketleyebilmesine bağlıdır.

- **Servis talebi sorunları**:
  
  - Her sorun için, İlgi eğitim sürecinin tamamında aynı uzmanı kullanın. Aynı sorunun birden çok uzman tarafından aynı anda etiketlenmesine izin verilmez.
  
  - Her dosya grubunun yalnızca belirli bir sorunla ilgili olup olmadığını belirleyin.

  - Bir sorun çok genel tanımlanmışsa, eBulma (Premium) ilgili olmayan çok fazla dosya verebilir. Bir sorun çok dar bir şekilde tanımlanırsa İlgi eğitim süreci daha uzun sürebilir. 

  - Her İlgi eğitim döngüsü sırasında, eBulma (Premium) tek bir etkin soruna odaklanır ve buna göre ara örnek sonuçlar görüntülenir.

  - Birden çok sorunlu bir senaryoda, Örnekleme modu işlemeye dahil edilecek sorunların seçimini sağlar. "Kapalı" olarak tanımlanan sorunlar, Örnekleme modu değiştirilene kadar işlenmez. Sorun yalnızca bir uzman için "boşta" veya "açık" olabilir.

  - Aday ayrıcalık dosyaları oluşturmak için eBulma (Premium) kullanılabilir. Ayrıcalık için ayrı bir sorun ayarlayın. Mümkünse, önce ilgi için eğitin ve iptal edin ve ardından yalnızca itlaf kümesinde ayrıcalık için eğitin (ayrı bir durum olarak kümeyi yeniden yükleyin). 

  - Toplu işlem hesaplaması yalnızca açık örnek olmadığında gerçekleştirilebilir (Batch Hesaplama'ya tıklandığında açık örnekleri olan kullanıcıların listesi görüntülenir). Diğer kullanıcıların örneklerini "kapatmak" için (bu yalnızca bu kullanıcılar bu örnekleri etiketlemediği durumlarda gerçekleştirilmelidir), Yönetici "İlgiyi değiştir" yardımcı programını "Tüm kullanıcılar örneği" seçeneğiyle kullanabilir.

- **Meta veriler**: eBulma (Premium) içeriğe odaklanır. Meta verileri ilgi ölçütlerinin bir parçası olarak değerlendirmez.

- **Zenginlik**: Bir sorunun Zenginliği Değerlendirmeden sonra %3'ten azsa İlgi eğitimini bilinen İlgili ve İlgili Olmayan dosyalarla dağıtmayı göz önünde bulundurun.

- **Dosya boyutu**: Büyük dosyalar (ayıklanan metnin 5.242.880 karakterden fazla) İlgi bölümünde yoksayılır. Dosyalar İlgi eğitim sürecine katılmaz ve Batch Hesaplaması'nın ardından bir İlgi puanı almaz. 5 MB'ın üzerindeki dosyalar Değerlendirme kümesine dahil edilebilir.

## <a name="setting-up-case-issues"></a>Büyük/küçük harf sorunlarını ayarlama

Bu bölümde açıklanan parametreler eBulma (Premium) **İlgi** \> **İlgisi kurulumunda** kullanılabilir.
  
- Sorunlar, dosyaları eğitecek bir kullanıcıya atanmalıdır.

- daha sonra içeri aktarılan dosyaların işlenmekte olan yüke eklenmesi gerekir.

- İlgi eğitim sonuçlarını etkileyeecei için sorunları dikkatlice tanımlayın ve düzenleyin.

Parametreler ayarlandıktan sonra, gözden geçiren /uzman **İlgi sekmesinde dosyaları** eğitmeye başlayabilir.
