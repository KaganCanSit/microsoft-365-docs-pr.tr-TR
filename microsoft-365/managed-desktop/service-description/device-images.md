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
ms.openlocfilehash: 535dfc84ced9c4a2935d8e2c44c1e4c6135e9373
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "63034443"
---
# <a name="device-images"></a>Cihaz resimleri


İster yeni cihazlar [sipariş edin](#new-devices) ister [mevcut cihazları yeniden](#existing-devices) kullanın, cihaz görüntüsü için cihaz gereksinimlerimizi karşılaması için çeşitli [seçenekleriniz vardır](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>Yeni cihazlar
Onaylanmış bir üreticiden yeni [bir cihaz sipariş](device-requirements.md#minimum-requirements) ettiyken, cihazları doğru Microsoft Yönetilen Masaüstü resmi ve yazılım yapılandırmasıyla birlikte sevk etme adımlarını izleyin. Belirli bir cihaz modelini hizmete ilk kez kaydetmeyi planlasanız, beklediğiniz kullanıcı deneyimini sunması için bir örneği test edin. Daha fazla bilgi için bkz. [Yeni cihazları doğrulama](/microsoft-365/managed-desktop/get-started/validate-device).

### <a name="dell"></a>Dell
Doğrudan, Microsoft Yönetilen Masaüstü tarafından onaylanan resmin siparişiniz için cihazlara uygulandığından emin olan Dell satış temsilcisiyle birlikte çalışabilirsiniz. Dell cihazları, görüntü ve sipariş süreci hakkında daha fazla soru için, ilgili cihazla MMD_at_dell@dell.com.

### <a name="hp"></a>HP 
HP'den yeni cihazlar sipariş ettiyken, Mağaza [Windows Pro](https://www.microsoft.com/windows/business/devices#view-all-filter) iş cihazları sitesinde bulunan her model için Ek gereksinimler bölümünde listelenen belirli SKU'nun (Microsoft Yönetilen Masaüstü cihazlarını gösterecek şekilde görünüme filtre uygulama) olduğundan emin olun.

Özel durum olarak onaylanmış ancak şu anda Cihaz Listesi sayfasında listelenmiyorsa, HP'den bir cihaz sipariş ediyorsanız modeliniz için SKU'nun kullanılmalarını istediğinizden emin olun.[](customizing.md) Özel durum isteğinizi kullanarak bu bilgiyi size almak için HP ile birlikte çalışacağız. Ayrıca, şu adresleri kullanarak cihazlar ve cihaz siparişi yönergeleriyle ilgili sorularınız için doğrudan HP'ye başvurabilirsiniz:
 
- Amerika: mmd-americas@hp.com
- Avrupa/Orta Doğu/Afrika: mmd-emea@hp.com
- Asya Pasifik/Japonya: mmd-apj@hp.com
- Genel: mmd@hp.com

### <a name="lenovo"></a>Lenovo
Microsoft Yönetilen Masaüstü'de kullanım için Lenovo'dan cihazlar sipariş ettiyken, siparişin bir parçası olarak dahil edilen belirli bir parça numarasını göstermeniz gerekir. Lenovo satış temsilcinize veya Lenovo Kanal İş Ortağı'nıza başvurun ve cihaz gereksinimlerimizi karşılayacak sistemle *"özel* teklif modeli" [oluşturmalarını iste](device-requirements.md#minimum-requirements). Microsoft Yönetilen Masaüstü ile uyumlu, önceden yüklenmiş bir resim eklemek için, satış temsilcisine "*SBB0Q94938 – MMD Enablement* sistem yapı taşı parça numarası" ifadesini referans olarak göndermesi gerekir. Önerilen hizmetler, destek ve görüntüleme hizmetleri için Lenovo satış temsilciniz veya Lenovo Kanal İş Ortağı ile birlikte çalışabilirsiniz.

### <a name="microsoft"></a>Microsoft
Cihaz gereksinimlerini karşılamaya çalışan tüm Microsoft cihazları, Microsoft Yönetilen Masaüstü ile çalışan bir resimle birlikte gelir. Başka adım gerekmez.

Microsoft cihazı üzerinde fabrikanın en son görüntüsünü elde etmek için Surface uzmanınız ile birlikte surface "Tirnak PO" işlemini kullanmak için birlikte çalışabilirsiniz.

## <a name="existing-devices"></a>Mevcut cihazlar

Hem cihaz gereksinimlerini hem de yazılım gereksinimlerini karşılayana kadar  [mevcut cihazları](device-requirements.md#minimum-requirements) yeniden [kullanabilirsiniz](device-requirements.md#installed-software). Üreticinize uygun adımları izleyin.

Cihazları üreticinin resmiyle veya Microsoft Yönetilen Masaüstü ''evrensel resim' kullanarak yeniden görüntüye sınabilirsiniz. Uygun bir üretici resmi elde etmek için, yeniden [kullanılabilir modele](#new-devices) en az bir yeni cihaz sipariş edebilirsiniz. Ardından, görüntüyü bu cihazdan elde edebilirsiniz ve tam olarak aynı modelin diğer cihazlarına uygulayabilirsiniz.

> [!NOTE]
> Resimleri oluşturmak, test etmek ve dağıtmak sizin sorumluluğumdadır. Ayrıca, "evrensel resim" dahil olmak üzere, özel resimler yerine, mümkün olduğunda üretici tarafından sağlanan uygun resimlerin kullanılması önerilir.

### <a name="hp"></a>HP

HP Corporate Ready Image ile sevk edilen HP Ticari Bilgisayarlar a içerir. Kurtarma için WIM dosyası. Bu görüntüyü, fabrika geri yükleme görüntüsünü aynı modelin diğer cihazlarına uygulamak için kullanabilirsiniz.

Bu adımlar cihaza bağlı tüm verileri kaldıracak, bu nedenle başlatmadan önce tutmak istediğiniz tüm verileri saklayabilirsiniz.

1. WinPE [ile önyüklenebilir bir USB](/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) sürücüsü oluşturun.
2. Bu dosyaları C:SOURCES kaynağından\\ USB sürücüye kopyalayın:
    - Fabrika kurtarma WIM dosyası (örneğin, HPEliteBook840G7NotebookPCCR2004.wim\_\_\_\_\_\_\_)
    - DEPLOY. CMD
    - ReCreatePartitions.txt
3. [Cihazı WinPE'ye önyükler](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) USB sürücüsüne bağlan'a iki bağlantıyla ulaşabilirsiniz
4. Komut isteminde Komut İstemi [ 'Diskpart.exe](/windows-server/administration/windows-commands/diskpart#additional-references).
5. Diskpart'ta, çalıştırın `list disk`ve birincil depolama disk numarasını (normalde Disk 0) not alırsınız.
6. Yazarak Disk bölümü'den çıkın `exit`.
7. Komut isteminde şunu çalıştırın: `deploy.cmd <sys_disk> <recovery_wim>`*sys_disk* az önce belirlediğimiz birincil depolama diskin disk numarası ve recovery_wim , 'ın dosya adıdır. Daha önce kopyalanmış olan WIM dosyası.
8. USB sürücüyü kaldırın ve ardından cihazı yeniden başlatın.

### <a name="microsoft"></a>Microsoft 

Microsoft Surface cihazları, her modele özgü " [metal kurtarma](https://support.microsoft.com/en-us/surfacerecoveryimage) " resimleri içerir. Bu görüntüleri cihazları yeniden kullanım için kullanabilirsiniz.

Bu resimler, Windows Ortamını (WinRE) kullanır ve bu otomatik değildir, el ile yapılan bir işlemdir. Surface için USB kurtarma [sürücüsü oluşturma ve kullanma'daki adımları izleyin](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07).


### <a name="universal-image"></a>Evrensel resim
Microsoft Yönetilen Masaüstü, Microsoft Yönetilen Masaüstü ile kullanabileceğiniz Windows Pro Microsoft 365 Uygulamaları resim Enterprise resim oluşturdu. Bununla birlikte, en iyisi mümkün olduğunda üretici tarafından sağlanan Microsoft Yönetilen Masaüstü'ne uygun resimleri kullanmaktır. Bu, kullanıcı oturum a açınce güncelleştirilen eski bir Windows sürümü de olsa en iyisidir. Microsoft Yönetilen Masaüstü Evrensel görüntüsünü kullanmak son seçenek olabilir.

- Görüntüyü, en son aylık Windows 30-60 günde bir ve yılda en az Microsoft 365 Uygulamaları kez Enterprise güncelleştirmeleriyle güncelleştiriz.
- Resimde, aşağıdaki kurtarma senaryolarına uygun olarak, Microsoft 365 Uygulamaları Enterprise sağlanıyor olduğundan emin Windows paketi yer almaktadır.
- Resmi USB sürücüleriyle dağıtabilirsiniz. Sürücü eklemek için betik kullanılabilir bir işlem içerir (resimle birlikte verilen belgelerde ana hatlarıyla açıklanmıştır).
- Dahil edilen betikleri ve klasörleri, belirli birikmeli güncelleştirmeler ekleme, dosya kopyalama kodu ekleme veya diğer denetimleri gerçekleştirme gibi diğer özelleştirmelerle kullanmak üzere değiştirebilirsiniz.
- SÜRÜCÜLER ve kalite güncelleştirmeleri, USB Windows dağıtımı sırasında sürücüye eklenir.

> [!NOTE]
> Dağıtılan resmin son görüntüsüyle ilgili tüm gerekli sürücüleri eklemek, tüm testleri yapmak ve sorun olmadığını sağlamak sizin sorumluluğumdadır. Evrensel Resmi "olduğu gibi" sağlar, ancak teknik rehberlik sağlar ve soruları yanıtlarız. İletişim MMDImage@microsoft.com.

Yönetici portalında değişiklik isteği oluşturarak Evrensel Resim içeriği ve belgeleri için istek [gönderin](../get-started/access-admin-portal.md).


