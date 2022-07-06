---
title: Şifreleme için BitLocker
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Office 365 bitLocker şifrelemesini nasıl kullandığını ve kaybolan veya çalınan bilgisayarlar ve diskler nedeniyle veri hırsızlığı olasılığını nasıl azaltacağınızı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dec62da7bc4d29891dcd86ec378faeb52a2d3d9f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633905"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>Şifreleme için BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM)

Microsoft sunucuları, birim düzeyinde bekleyen müşteri verilerini içeren disk sürücülerini şifrelemek için BitLocker kullanır. BitLocker şifrelemesi, Windows'ta yerleşik olarak sunulan bir veri koruma özelliğidir. BitLocker, başka işlem veya denetimlerde (örneğin, erişim denetimi veya donanımın geri dönüştürülmesine) yönelik kilitlenmeler olması durumunda tehditlere karşı koruma sağlamak için kullanılan teknolojilerden biridir ve bu da birinin müşteri verilerini içeren disklere fiziksel erişim elde etmelerine neden olabilir. Bu durumda BitLocker, kaybolan, çalınan veya uygunsuz şekilde kullanımdan kaldırılan bilgisayarlar ve diskler nedeniyle veri hırsızlığı veya açığa çıkarma olasılığını ortadan kaldırır.

BitLocker, Exchange Online, SharePoint Online ve Skype Kurumsal müşteri verilerini içeren disklerde Gelişmiş Şifreleme Standardı (AES) 256 bit şifreleme ile dağıtılır. Disk kesimleri, Birim Ana Anahtarı (VMK) ile şifrelenen ve sunucudaki Güvenilir Platform Modülü'ne (TPM) bağlı olan Tam Birim Şifreleme Anahtarı (FVEK) ile şifrelenir. VMK, FVEK'yi doğrudan korur ve bu nedenle VMK'yi korumak kritik hale gelir. Aşağıdaki şekilde, belirli bir sunucu için BitLocker anahtar koruma zinciri örneği gösterilmektedir (bu örnekte, Exchange Online sunucu kullanılarak).

Aşağıdaki tabloda, belirli bir sunucu için BitLocker anahtar koruma zinciri (bu örnekte bir Exchange Online sunucusu) açıklanmaktadır.

| ANAHTAR KORUYUCUSU | TANECİKLİLİK | NASıL OLUŞTURULDU? | NEREDE DEPOLANıR? | KORUMA |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| AES 256 bit Dış Anahtar | Sunucu Başına | BitLocker API'leri | TPM veya Gizli Dizi Güvenli | Kasa / Access Control |
|  |  |  | Posta Kutusu Sunucusu Kayıt Defteri | TPM şifreli |
| 48 basamaklı Sayısal Parola | Disk Başına | BitLocker API'leri | Active Directory | Kasa / Access Control |
| Veri Kurtarma Aracısı olarak X.509 Sertifikası (DRA), Ortak Anahtar Koruyucusu olarak da adlandırılır | Ortam (örneğin, Exchange Online çok kiracılı) | Microsoft CA | Derleme Sistemi | Hiçbir kullanıcının özel anahtarın tam parolası yoktur. Parola fiziksel koruma altındadır. |


BitLocker anahtar yönetimi, Bir Microsoft veri merkezinde şifrelenmiş disklerin kilidini açmak/kurtarmak için kullanılan kurtarma anahtarlarının yönetimini içerir. Microsoft 365, ana anahtarları güvenli bir paylaşımda depolar ve bu anahtarlara yalnızca ekranı görüntülenen ve onaylanan kişiler erişebilir. Anahtarların kimlik bilgileri, erişim denetimi verileri için güvenli bir depoda ("gizli depo" olarak adlandırdığımız), tam zamanında erişim yükseltme aracı kullanılarak erişim için yüksek düzeyde yükseltme ve yönetim onayları gerektirir.

BitLocker, iki yönetim kategorisine giren anahtarları destekler:

- BitLocker tarafından yönetilen anahtarlar, genellikle kısa ömürlüdür ve bir sunucuya veya belirli bir diske yüklenmiş bir işletim sistemi örneğinin ömrüne bağlıdır. Bu anahtarlar, sunucu yeniden yükleme veya disk biçimlendirmesi sırasında silinir ve sıfırlanır.

- BitLocker dışında yönetilen ancak disk şifre çözme için kullanılan BitLocker kurtarma anahtarları. BitLocker, bir işletim sisteminin yeniden yüklendiği ve şifrelenmiş veri disklerinin zaten mevcut olduğu senaryo için kurtarma anahtarlarını kullanır. Kurtarma anahtarları, yanıtlayıcının disk kilidini açması gerekebileceği Exchange Online Yönetilen Kullanılabilirlik izleme yoklamaları tarafından da kullanılır.

BitLocker korumalı birimler tam birim şifreleme anahtarıyla şifrelenir ve bu da bir birim ana anahtarıyla şifrelenir. BitLocker, şifreleme anahtarlarının hiçbir zaman açık bir şekilde depolanmadığından veya kablo üzerinden gönderilmediğinden emin olmak için FIPS uyumlu algoritmalar kullanır. Bekleyen müşteri verilerinin Microsoft 365 uygulaması, varsayılan BitLocker uygulamasından sapmaz.
