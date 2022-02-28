---
title: Contoso Windows 10 Enterprise dağıtım bilgileri
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'ya, Microsoft Endpoint Configuration Manager yükseltmeleri dağıtmak için Contoso'ya nasıl Windows 10 Enterprise.
ms.openlocfilehash: 7fe6efd176e156b75337ba79db6c1db839b0ed03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988627"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Contoso Windows 10 Enterprise dağıtım bilgileri

Kuruluş için Microsoft 365'Microsoft 365 yaygın olarak yaygın olarak Windows uyumlu bilgisayar ve cihazları arasında Windows%7, Windows 8.1 (%65) ve Windows 10'i %25) bir Windows'i bir Windows 10 vardı. Contoso, gelişmiş güvenlikten yararlanmak Windows 10 Enterprise için bilgisayarlarını yükseltmek ve güncelleştirmelerin otomatik dağıtımlarından daha düşük bir IT yükünü yükseltmek istedi. 

Contoso, altyapılarını ve iş gereksinimlerini değerlendirdikten sonra dağıtım için şu temel gereksinimleri belirledi:

- Mümkün olan en fazla sayıda bilgisayar ve cihaz Windows 10 Enterprise
- Yerinde yükseltmelerin yuvarlansı mevcut Configuration Manager altyapısından faydalanıyor
- Hangi sürümlerin dağıtıla Windows 10 Enterprise güncelleştirmelerin halkalar aracılığıyla yapılması için denetim
- Bilgisayarlar ve cihazlar en düşük IT yönetim maliyetleriyle ve son kullanıcılar için çok az etkiyle güncel kalsın

Güncel, Contoso'nun iş  ihtiyaçlarını karşılamak üzere desteklenen Windows 10 Enterprise sürümü olarak tanımlanır ve bu da Windows 10 Enterprise'un en son sürümünü çalıştıran Windows uyumlu tüm bilgisayarlardan farklı olabilir.

## <a name="deployment-tools"></a>Dağıtım araçları

Contoso, 2013'te yapılan yerinde yükseltmelerden Windows 10 Enterprise sırasında Windows çözümlerini kullandı:

- Yükseltme Hazırlığı  

  Sistem, uygulama ve sürücü verilerini çözümleme için toplar, sonra yükseltmeyi engellebilir uyumluluk sorunlarını tanımlar ve sorunları Microsoft'un düzeltmesi önerilir.

- Güncelleştirme Uyumluluğu  

  En güncel güncelleştirmelerde olduğundan emin olmak için Windows güncelleştirmeleri ile ilgili olarak cihazlarınızı durumunu gösterir.

- Cihaz Durumu  

  Sık sık kilitlenmeye neden olan, dolayısıyla yeniden değiştirilebilir veya değiştirilmesi gereken cihazları ve cihaz kilitlenmelere neden olan cihaz sürücülerini tanımlar ve bu sürücülerin kilitlenme sayısını azaltacak alternatif sürümlerinin önerileriyle. Son kullanıcılara Windows istemleri gönderen Bilgi Koruması'nın hatalı yapılandırılmasını sağlayan bildirim sağlar.
 
Contoso'da mevcut bir Yapılandırma Yöneticisi (Geçerli Dalı) altyapısı vardır. Configuration Manager, büyük ortamlar için ölçekler ve yükleme, güncelleştirmeler ve ayarlar üzerinde kapsamlı denetim sağlar. Ayrıca, postalarınızı dağıtmayı ve yönetmeyi daha kolay ve verimli hale getirir yerleşik Windows 10 Enterprise.

## <a name="planning-process"></a>Planlama süreci

Contoso, yüklü uygulama kümelerini ve bu uygulamalarla uyumluluklarını belirlemek için Windows Analytics'te Yükseltme Hazırlığı'Windows 10 Enterprise.

## <a name="deployment-process"></a>Dağıtım işlemi

Contoso, Microsoft'un en iyi uygulama önerilerini içeren aşağıdaki süreci uygulamak Windows 10 Enterprise yerinde yükseltme dağıtımını tamamlamak için:

1. Configuration Manager için eş önbelleği etkinleştirildi.
2. Toplu Lisanslama Windows Resimlerine dayalı olarak özelleştirilmiş paketlerde oluşturulmuş.
3. Yapılandırma Yöneticisi, dağıtım paketlerine dağıtım Windows dağıtım noktalarına ve dağıtılan derlemeleri üç doğrulama ve dağıtım hazırlama gruplarına dağıtmak için kullanılır.
4. Windows Analytics'in Cihaz Durumu ve Güncelleştirme Uyumluluğu çözümlerini kullanarak doğrulama ve dağıtım hazırlama halkalarında bilgisayarlar ve cihazlar için başarının değerlendirilmesi.
5. Contoso, Windows Çözümleme bilgilerine dayanarak geniş dağıtım grubuna dağıtım Windows 10 Enterprise kullanıcı sürümünü belirledi.
6. Seçilen kullanıcı paketini geniş dağıtım grubuna dağıtmak için Configuration Manager dağıtım Windows sıralarını randı.
7. Sorunları ele alan Cihaz Durumu ve Güncelleştirme Uyumluluğu çözümleri kullanılarak geniş dağıtım grubunda izlenen bilgisayarlar ve cihazlar.

Burada, Contoso'nun yerinde yükseltme ve devam eden güncelleştirmeler dağıtım mimarisi vardır.

![Contoso'nun Windows 10 Enterprise altyapısı.](../media/contoso-win10/contoso-win10-fig1.png)

Bu altyapı şunları sağlar:

- Yapılandırma Yöneticisi; şu şekilde:
  - Microsoft Network'Windows 10 Enterprise Microsoft Toplu Lisanslama Merkezi'nden paketler için resimler elde edilir.
  - Dağıtım paketleri için merkezi yönetim noktasıdır.
- Normalde Contoso'nun bölgesel merkez ofislerinde bulunan bölgesel dağıtım noktaları.
- Windows yerinde yükseltme veya grup üyeliğine göre devam eden güncelleştirmeler için dağıtım paketlerini alan ve yük alan çeşitli konumlarda yer alan bilgisayar ve cihazları kullanabilirsiniz.

## <a name="next-step"></a>Sonraki adım

Contoso'un, kuruluş genelinde geçerli etki alanı bilgilerini dağıtmak ve tutmak için Configuration Manager [altyapısından Kurumlar için Microsoft 365 Uygulamaları](contoso-o365pp.md) sahip olduğunu öğrenin. 

## <a name="see-also"></a>Ayrıca bkz.

[Windows 10 Enterprise](/windows/deployment/)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)