---
title: Cihaz resimleri
description: Yeni cihazları sipariş etmek veya mevcut cihazları yeniden kullanılırken resim gereksinimleri
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: f1d00c12512b70ffd62372aaeae787acf1911573
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330293"
---
# <a name="device-images"></a>Cihaz resimleri

İster yeni cihazlar [sipariş edin](#new-devices) ister [mevcut cihazları yeniden](#existing-devices) kullanın, cihaz görüntüsü için cihaz gereksinimlerimizi karşılaması için çeşitli [seçenekleriniz vardır](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>Yeni cihazlar

Onaylanmış bir üreticiden yeni [bir cihaz sipariş](device-requirements.md#minimum-requirements) ettiyken, cihazları doğru Microsoft Yönetilen Masaüstü resmi ve yazılım yapılandırmasıyla birlikte sevk etme adımlarını izleyin.

Belirli bir cihaz modelini hizmete ilk kez kaydetmeyi planlasanız, beklediğiniz kullanıcı deneyimini sunması için bir örneği test edin. Daha fazla bilgi için bkz. [Yeni cihazları doğrulama](/microsoft-365/managed-desktop/get-started/validate-device).

### <a name="dell"></a>Dell

Doğrudan Dell satış temsilcisiyle çalışabilirsiniz.

Temsilci, Microsoft Yönetilen Masaüstü tarafından onaylanan resmin sizin siparişinize uygun cihazlara uygulanmasını sağlar. Dell cihazları, resim ve sipariş işlemi hakkında daha fazla bilgi için, ilgili cihazla MMD_at_dell@dell.com.

### <a name="hp"></a>HP

HP'den yeni cihazlar sipariş ettiyken, Mağaza veya İş cihazları sayfasında bulunan her model için Ek gereksinimler bölümünde listelenen [SKU'Windows Pro emin](https://www.microsoft.com/windows/business/devices#view-all-filter) olun. Microsoft Yönetilen Masaüstü cihazlarını liste görüntülemek için görünümü filtrele.

Hp'den bir özel durum olarak onaylanmış ancak şu anda Cihaz Listesi sayfasında listelenmiyorsa, modeliniz için SKU'nun kullanılmalarını talep edin.[](customizing.md) Özel durum isteğinizi kullanarak bu bilgiyi size almak için HP ile birlikte çalışacağız. Ayrıca, şu adresleri kullanarak cihazlar ve cihaz siparişi yönergeleriyle ilgili sorularınız için doğrudan HP'ye başvurabilirsiniz:

- Amerika: mmd-americas@hp.com
- Avrupa/Orta Doğu/Afrika: mmd-emea@hp.com
- Asya Pasifik/Japonya: mmd-apj@hp.com
- Genel: mmd@hp.com

### <a name="lenovo"></a>Lenovo

Lenovo'dan cihaz sipariş ettiyken, siparişte belirli bir parça numarası belirtebilirsiniz. Lenovo satış temsilcinize veya Lenovo Kanal İş Ortağı'nıza başvurun ve cihaz gereksinimlerimizi karşılayacak sistemle *"özel* teklif modeli" [oluşturmalarını iste](device-requirements.md#minimum-requirements).

Microsoft Yönetilen Masaüstü ile uyumlu önceden yüklenmiş bir resim eklemek için, satış temsilcisine "*SBB0Q94938 - MMD Enablement* sistem yapı taşı parça numarası" ifadesini göndermelerini sorun. Önerilen hizmetler, destek ve görüntüleme hizmetleri için Lenovo satış temsilciniz veya Lenovo Kanal İş Ortağı ile birlikte çalışabilirsiniz.

### <a name="microsoft"></a>Microsoft

Cihaz gereksinimlerini karşılamaya çalışan tüm Microsoft cihazları, Microsoft Yönetilen Masaüstü ile çalışan bir resimle birlikte gelir. Başka adım gerekmez.

Microsoft cihazı üzerinde fabrikanın en son görüntüsünü elde etmek için Surface uzmanınız ile birlikte surface "Tirnak PO" işlemini kullanmak için birlikte çalışabilirsiniz.

## <a name="existing-devices"></a>Mevcut cihazlar

Her ikisini de karşılayana kadar, var olan cihazları yeniden kullanabilirsiniz:

- [Cihaz gereksinimleri](device-requirements.md#minimum-requirements)
- [Yazılım gereksinimleri](device-requirements.md#installed-software)

Üreticinize uygun adımları izleyin.

Cihazları üreticinin resmiyle veya Microsoft Yönetilen Masaüstü "evrensel resim" kullanarak yeniden görüntüebilirsiniz. Uygun bir üretici resmi elde etmek için, yeniden kullanılabilir [modele](#new-devices) en az bir yeni cihaz sipariş edin. Ardından, görüntüyü bu cihazdan elde edebilirsiniz ve tam olarak aynı modelin diğer cihazlarına uygulayabilirsiniz.

> [!NOTE]
> Resimleri oluşturmak, test etmek ve dağıtmak sizin sorumluluğumdadır. Ayrıca, mümkün olduğunda, özel resimler yerine üretici tarafından sağlanan uygun resimlerin kullanılması önerilir; "evrensel resim" ifadesini içerir.

### <a name="hp"></a>HP

HP Corporate Ready Image ile sevk edilen HP Ticari Bilgisayarlar kurtarma için bir `.WIM` dosya içerir. Bu görüntüyü, fabrika geri yükleme görüntüsünü aynı modelin diğer cihazlarına uygulamak için kullanabilirsiniz.

Aşağıdaki adımlar cihaza bağlı tüm verileri kaldırır. Başlamadan önce, tutmak istediğiniz tüm verileri bu veriler için destekleyebilirsiniz.

**Cihaz verilerini kaldırmak için:**

1. WinPE [ile önyüklenebilir bir USB](/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) sürücüsü oluşturun.
2. Bu dosyaları USB sürücüye `C:\\SOURCES` kopyalayın:
    - Fabrika kurtarma WIM dosyası (örneğin, `HP\_EliteBook\_840\_G7\_Notebook\_PC\_CR\_2004.wim`)
    - `DEPLOY.CMD`
    - `ReCreatePartitions.txt`
3. [Cihazı WinPE'ye önyükler](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) USB sürücüsüne bağlan'a iki bağlantıyla ulaşabilirsiniz
4. Komut isteminde Komut İstemi [ 'Diskpart.exe](/windows-server/administration/windows-commands/diskpart#additional-references).
5. Diskpart'ta, çalıştırın `list disk`ve birincil depolama disk numarasını (normalde Disk 0) not alırsınız.
6. Yazarak Disk bölümü'den çıkın `exit`.
7. Komut isteminde, komutunu `deploy.cmd <sys_disk> <recovery_wim>`çalıştırın; burada `sys_disk` , belirlediğimiz birincil depolama diskin disk `recovery_wim` `.WIM` numarası ve daha önce kopyalanmış olan dosyanın dosya adıdır.
8. USB sürücüyü kaldırın ve ardından cihazı yeniden başlatın.

### <a name="microsoft"></a>Microsoft

Microsoft Surface cihazları, her modele özgü " [metal kurtarma](https://support.microsoft.com/en-us/surfacerecoveryimage) " resimleri içerir. Bu görüntüleri cihazları yeniden kullanım için kullanabilirsiniz.

Bu resimler Windows Ortamını (WinRE) kullanır. Bu el ile yapılan bir işlemdir (otomatik değildir). Surface için USB kurtarma [sürücüsü oluşturma ve kullanma'daki adımları izleyin](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07).

### <a name="universal-image"></a>Evrensel resim

Microsoft Yönetilen Masaüstü, Microsoft Yönetilen Masaüstü ile kullanabileceğiniz Windows Pro Microsoft 365 Uygulamaları resim Enterprise resim oluşturdu.

Bununla birlikte, en iyisi mümkün olduğunca üretici tarafından sağlanan Microsoft Yönetilen Masaüstü'ne uygun resimleri kullanmaktır. Bu, kullanıcı oturum a açınce daha eski bir Windows sürümünün güncelleştirilmiş olması gerekir. Microsoft Yönetilen Masaüstü Evrensel görüntüsünü kullanmak son seçenek olabilir.

- Görüntüyü en son 30-60 Windows aylık kalite güncelleştirmeleriyle ve yılda en az Microsoft 365 Uygulamaları kez Enterprise güncelleştirmelerle güncelleştiriz.
- Resimde, aşağıdaki kurtarma senaryolarına uygun olarak, Microsoft 365 Uygulamaları Enterprise sağlanıyor olduğundan emin Windows paketi yer almaktadır.
- Resmi USB sürücüleriyle dağıtabilirsiniz. Sürücüleri eklemek için betik kullanılabilir bir işlem içerir. Bu işlem, resimle birlikte verilen belgelerde ana hatlarıyla açıklanmıştır.
- Dahil edilen betikleri ve klasörleri, belirli birikmeli güncelleştirmeler ekleme, dosya kopyalama kodu ekleme veya diğer denetimleri gerçekleştirme gibi diğer özelleştirmelerle değiştirebilirsiniz.
- SÜRÜCÜLER ve kalite güncelleştirmeleri, USB Windows dağıtımı sırasında sürücüye eklenir.

> [!NOTE]
> Dağıtılan resmin son görüntüsüyle ilgili tüm gerekli sürücüleri eklemek, tüm testleri yapmak ve sorun olmadığını sağlamak sizin sorumluluğumdadır. Evrensel Resmi "olduğu gibi" sağlar, ancak teknik rehberlik sağlar ve soruları yanıtlarız. İletişim MMDImage@microsoft.com.

Yönetim portalında değişiklik isteği oluşturarak Evrensel Resim içeriği ve belgeleri için [istekler gönderin](../get-started/access-admin-portal.md).
