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
description: BitLocker'Office 365 kayıp veya çalınmış bilgisayarlar ve diskler nedeniyle veri hırsızlığı riskini azaltan BitLocker şifrelemesi'ni nasıl kullandığını öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 343a5966dc24954e98d7d31977aacbc09daaba11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986730"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>Şifreleme için BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM)

Microsoft sunucuları bitLocker kullanarak, işlem düzeyi düzeyinde müşteri verileri içeren disk sürücülerini şifreler. BitLocker şifrelemesi, bu şifrelemede yerleşik olarak Windows. BitLocker, diğer işlemlerde veya denetimlerde atlamalar (örneğin, erişim denetimi veya donanımın geri dönüşümi) durumunda birinin müşteri verilerini içeren disklere fiziksel erişim elde  alımına yol açmayacak şekilde tehditlere karşı korumak için kullanılan teknolojilerden biridir. Bu durumda BitLocker kayıp, çalınma veya uygun olmayan şekilde izinli bilgisayar ve diskler nedeniyle veri hırsızlığı veya açık kalma olasılarını ortadan kaldırıyor.

BitLocker, Exchange Online, SharePoint Online ve Skype Kurumsal'de müşteri verilerini içeren diskler üzerinde Gelişmiş Şifreleme Standardı (AES) 256 bit şifreleme ile Skype Kurumsal. Disk sabiti, sunucudaki Güvenilen Platform Modülü'ne (TPM) bağlı olan Toplu Ana Anahtar (VMK) ile şifrelenmiş olan Tam Toplu Şifreleme Anahtarı (FVEK) ile şifrelenir. VMK doğrudan FVEK'yi korur ve dolayısıyla VMK'nin korunması kritik öneme sahip olur. Aşağıdaki şekilde, verili bir sunucu (bu örnekte, bir Veritabanı Sunucusu kullanarak) bitLocker anahtar koruma zincirinin bir örneği Exchange Online verilmiştir.

Aşağıdaki tabloda, belirli bir sunucu (bu örnekte bir veritabanı veya sunucu) için BitLocker anahtar koruma zinciri Exchange Online verilmiştir.

| ANAHTAR KEY | AYRıNTıLıLıK | NASıL OLUŞTURULUR? | NEREDE DEPOLANıR? | KORUMA |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| AES 256 bit Dış Anahtar | Sunucu Başına | BitLocker API'leri | TPM veya Gizli Kasa | Kasa / Erişim Denetimi |
|  |  |  | Posta Kutusu Sunucusu Kayıt Defteri | TPM şifreli |
| 48 basamaklı Sayısal Parola | Disk Başına | BitLocker API'leri | Active Directory | Kasa / Erişim Denetimi |
| Ortak Anahtar Anahtar Olarak Da Adlandırılan X.509 Veri Kurtarma Aracısı (DRA) Olarak Sertifika | Ortam (örneğin, Exchange Online çok boyutlu) | Microsoft CA | Derleme Sistemi | Hiç kimse özel anahtarın tam parolasını sahip olmaz. Parola fiziksel koruma altında. |


BitLocker anahtar yönetimi, Microsoft veri merkezinde şifreli disklerin kilidini açmak/kurtarmak için kullanılan kurtarma anahtarlarının yönetimini içerir. Microsoft 365 anahtarlara güvenli bir paylaşımda depolar, yalnızca ekranlı olarak ekranı olan ve onaylanan bireyler erişebilirsiniz. Anahtarların kimlik bilgileri erişim denetim verileri için güvenli bir depoda depolanır (buna "gizli depo" denir) ve bu, tam zamanında erişim yükseltme aracı kullanarak yüksek düzeyde yükseltme ve yönetim onayları gerektirir.

BitLocker, iki yönetim kategorisine ayrılır:

- BitLocker tarafından yönetilen anahtarlar, genel olarak çok kısa ömürlü olan ve sunucuya veya verilen bir diske yüklenmiş bir işletim sistemi örneğinin yaşam süresine bağlı olan. Bu anahtarlar sunucu yeniden yüklemesi veya disk biçimlendirmesi sırasında silinir ve sıfırlanır.

- BitLocker dışında yönetilen ancak disk şifresini çözmek için kullanılan BitLocker kurtarma anahtarları. BitLocker, işletim sisteminin yeniden yüklenme senaryosu için kurtarma anahtarlarını kullanır ve zaten şifrelenmiş veri diskleri vardır. Kurtarma anahtarları, yanıtlayanların bir diskin kilidini açması gerek Exchange Online yönetilen kullanılabilirlik izleme sistemi tarafından da kullanılabilir.

BitLocker korumalı birimler tam toplu şifreleme anahtarıyla şifrelenir ve bu da bir toplu işlem ana anahtarıyla şifrelenir. BitLocker, şifreleme anahtarlarının hiçbir zaman net bir şekilde kablo üzerinden depo veya gönderildiğini garanti etmek için FIPS uyumlu algoritmalar kullanır. Müşteri Microsoft 365 rest-protection uygulamasının varsayılan BitLocker uygulamasından sapmaz.
