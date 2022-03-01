---
title: Uç Nokta Cihaz Denetimi Cihazı Yüklemesi için Microsoft Defender
description: Bu konu başlığı altında, Uç Nokta Cihaz Denetimi Cihazı Yüklemesi için Microsoft Defender hakkında bilgi edinebilirsiniz
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3ff727f95dd62c205cee7e9606cb024a5ea88bda
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014057"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Uç Nokta Cihaz Denetimi Cihazı Yüklemesi için Microsoft Defender

**Geçerli olduğu yer:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta Cihaz Denetim Cihazı Yüklemesi için Microsoft Defender aşağıdaki görevi gerçekleştirebilirsiniz:

- Kişilerin belirli cihazları yüklemesini engelin.
- Kişilerin belirli cihazları yüklemesine izin ver, ancak diğer cihazları engelle.

> [!NOTE]
> Cihaz Yükleme ve Çıkarılabilir depolama erişimi denetimi arasındaki farkı bulmak için bkz. Uç Nokta Cihaz Denetimi Çıkarılabilir Veya Koruma için [Microsoft Defender Depolama.](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true)

|Ayrıcalık|İzin|
|---|---|
|Access|Cihaz yüklemesi |
|Eylem Modu|İzin Ver, Engelle |
|CSP Desteği|Evet|
|GPO Desteği|Evet|
|Kullanıcı Tabanlı Destek|Hayır|
|Makine Tabanlı Destek|Evet|

## <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Server 2022'de, Windows 10 11 cihazda Windows Kurulumu Windows dağıtın.

## <a name="device-properties"></a>Cihaz özellikleri

Cihaz Yükleme desteği aşağıdaki cihaz özelliklerini destekler:

- Cihaz Kimliği
- Donanım Kimliği
- Uyumlu Kimlik
- Cihaz Sınıfı
- 'Çıkarılabilir Cihaz' Cihaz türü: Bazı cihazlar Çıkarılabilir Cihaz olarak sınıflandırılabilir. Bağlı olduğu cihazın sürücüsü cihazın çıkarılabilir olduğunu gösterirken, cihaz çıkarılabilir olarak kabul edilir. Örneğin, bir USB cihazının, cihazın bağlı olduğu USB hub sürücüleri tarafından çıkarılabilir olduğu bildiriliyor.
Daha fazla bilgi için bkz. [Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>İlkeler

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Bu Cihaz Kimlikleri ile eşleşmeye izin ver cihazların yüklenmesine izin ver

Bu ilke ayarı, Donanım Kimliklerini Tak ve Çalıştır listesini ve yüklemesine izin verilen cihazlar için Windows kimlikleri belirtmenize olanak tanır. Bu ilke ayarı yalnızca, Tüm cihazla eşleşme ölçütleri ilkesi  ayarı genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ayarı etkinleştirildiğinde kullanılacak şekilde tasarlanmıştır.

Tüm cihazla eşleşme ölçütleri ilkesi ayarı genelinde Cihaz  yüklemesine izin ver ve Engelle ilkeleri için katmanlı değerlendirme sırası uygula ayarıyla birlikte bu ilke ayarı etkinleştirildiğinde, Windows'in, özellikle hiyerarşide aynı veya daha üst katmanda yer alan başka bir ilke ayarı özellikle bu yüklemeyi engellemediği sürece, Oluştur ve Çalıştır donanım kimliği veya uyumlu kimlik bulunan tüm cihaz varsa bu cihazı yüklemesine veya güncelleştirmesine izin verilir.  örneğin, aşağıdaki ilke ayarları gibi:

- Bu cihaz kimlikleri ile eşleşmesi cihazlar yüklemesini engelin.
- Bu cihaz örneği kimliklerinin eşleşmesini engelleyen cihazlar yüklemesini engelin.

Tüm cihaz **yükleme ölçütleri ilkesi** genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ilke ayarı bu ilke ayarıyla etkinleştirilmemişse, özellikle yüklemeyi engelleyen diğer tüm ilke ayarları geçerli olur.

> [!NOTE]
> Diğer **ilke** ayarları ilkesi ayarında, Cihaz yüklemesine izin ver ve Cihazı yükleme ilkelerini tüm cihazla  uyumlu, desteklenen hedef Windows 10 Windows sürümleri ve 11. Mümkün olduğunda, tüm cihazla eşleşme ölçütleri  ilkesi ayarında Cihaz yüklemesine izin ver ve Engelle ilkeleri için Katmanlı değerlendirme sırası uygula'nın kullanılması önerilir.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Bu cihaz örneği kimliklerinin herhangi biri ile eşleşmesi olan cihazların yüklenmesine izin ver

Bu ilke ayarı, cihaz yüklemesine izin verilen cihazlar için Tak ve Çalıştır cihaz Windows kimliklerini belirtmenizi sağlar. Bu ilke ayarı yalnızca, Tüm cihazla eşleşme ölçütleri ilkesi  ayarı genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ayarı etkinleştirildiğinde kullanılacak şekilde tasarlanmıştır.

Bu ilke ayarı Tüm cihazla eşleşme ölçütleri ilkesi  ayarı genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ayarıyla birlikte etkinleştirildiğinde, Windows'in, Eklenti ve Oynat cihaz örneği kimliği, hiyerarşide özellikle aynı veya daha üst katmanda yer alan başka bir ilke ayarı özellikle bu yüklemeyi engellemediği sürece, oluştursanız bile, Ekle ve Çalıştır cihaz örneği kimliği bulunan herhangi bir cihazı yüklemesine veya güncelleştirmesine izin verilir.  örneğin, aşağıdaki ilke ayarları gibi:

- Bu cihaz örneği kimlikleri ile eşleşmeye neden olan cihazların yüklenmesine engel olun

Tüm cihaz **yükleme ölçütleri ilkesi** genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ilke ayarı bu ilke ayarıyla etkinleştirilmemişse, özellikle yüklemeyi engelleyen diğer tüm ilke ayarları geçerli olur.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Bu cihaz kurulum sınıflarına uyumlu sürücüleri kullanan cihazların yüklenmesine izin ver

Bu ilke ayarı, yüklemesine izin verilen sürücü paketleri için cihaz kurulum sınıfı genel benzersiz tanımlayıcıları (GUID) Windows bir liste belirtmenize olanak sağlar. Bu ilke ayarı yalnızca, Tüm cihazla eşleşme ölçütleri ilkesi  ayarı genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ayarı etkinleştirildiğinde kullanılacak şekilde tasarlanmıştır.

Tüm cihazla eşleşme ölçütleri ilke ayarı genelinde Cihaz  yüklemesine izin ver ve Engelle ilkeleri için katmanlı değerlendirme sırası uygula ayarıyla birlikte bu ilke ayarı etkinleştirildiğinde, Windows'un cihaz kurulumu sınıf GUID'leri sizin oluşturmakta olduğu listede görünen sürücü paketlerini yüklemesine veya güncelleştirmesine izin verilir; ancak hiyerarşide aynı veya daha üst katmanda yer alan başka bir ilke ayarı bu yüklemeyi özellikle engellemediği sürece,  örneğin, aşağıdaki ilke ayarları gibi:

- Bu cihaz sınıfları için cihazların yüklemesini engelleme
- Bu cihaz kimlikleri ile eşleşmesi olan cihazların yüklemesini engelleme
- Bu cihaz örneği kimlikleri ile eşleşmeye neden olan cihazların yüklenmesine engel olun

Tüm cihaz **yükleme ölçütleri ilkesi** genelinde Cihaz yüklemesine izin ver ve Engelle için katmanlı değerlendirme sırası uygula ilke ayarı bu ilke ayarıyla etkinleştirilmemişse, özellikle yüklemeyi engelleyen diğer tüm ilke ayarları geçerli olur.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Tüm cihaz eşleşme ölçütleri genelinde Cihaz yüklemesine izin ver ve Engelle ilkeleri için katmanlı değerlendirme sırası uygulama

Bu ilke ayarı, belirli bir cihaz için birden çok yükleme ilkesi ayarı geçerli olduğunda İlke ayarlarına izin ver ve Engelle ayarlarının uygulanma sırası değişir. Daha belirli eşleşme ölçütlerinin daha az belirli eşleşme ölçütlerinin yerini alan, kurulmuş bir hiyerarşiye dayalı olarak örtüşen cihaz eşleşme ölçütlerinin uygulanması için bu ilke ayarını etkinleştirin. Cihaz eşleşme ölçütlerini belirten ilke ayarları için değerlendirmenin hiyerarşik sırası şöyledir:

**Cihaz örneği kimlikleri** \> **Cihaz Kimlikleri** \> **Cihaz kurulum sınıfı** \> **Çıkarılabilir cihazlar**

#### <a name="device-instance-ids"></a>Cihaz örneği kimlikleri

1. Bu cihaz örneği kimlikleri ile uyumlu sürücüler kullanan cihazların yüklemesini engelin.
2. Bu cihaz örneği kimlikleri ile uyumlu sürücüleri kullanan cihazların yüklenmesine izin ver.

#### <a name="device-ids"></a>Cihaz Kimlikleri

1. Bu cihaz kimlikleri ile uyumlu sürücüler kullanan cihazların yüklemesini engelin.
2. Bu cihaz kimlikleri ile uyumlu sürücüleri kullanan cihazların yüklenmesine izin ver.

#### <a name="device-setup-class"></a>Cihaz kurulum sınıfı

1. Bu cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların yüklemesini engelin.
2. Bu cihaz kurulum sınıflarına uyumlu sürücüleri kullanan cihazların yüklenmesine izin ver.

#### <a name="removable-devices"></a>Çıkarılabilir cihazlar

Çıkarılabilir cihazların yüklemesini engelleme

> [!NOTE]
> Bu ilke ayarı, Diğer ilke ayarları ilkesi ayarında açıklanan **Cihazların yüklemesini engelle ayarına göre daha ayrıntılı denetim** sağlar. Bu çakışan ilke ayarları aynı anda etkinleştirilmişse, Tüm cihazla eşleşme ölçütleri  ilkesi ayarına izin ver ve Cihazı yükleme ilkelerini engelle için katmanlı değerlendirme sırası uygula ayarı etkinleştirilir ve diğer ilke ayarı yoksayılır.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Bu cihaz kimlikleri ile eşleşmeye neden olan cihazların yüklemesini engelleme

Bu ilke ayarı, donanım kimliklerini Tak ve Çalıştır listesini ve yüklemeyi engelleyen cihazlar için Windows kimlikler belirtmenize olanak tanır. Varsayılan olarak, bu ilke ayarı kullanıcıların cihaz yüklemelerine izin veren diğer tüm Windows ilke ayarına göre önceliklidir.

> [!NOTE]
> Geçerli cihazlar için bu ilke ayarının yerine geçmek amacıyla bu cihaz örneği **kimlikleri** ilke ayarına uyan cihazların yüklenmesine izin ver ayarını etkinleştirmek için, Cihaz yükleme ilkelerinin  tüm cihazla eşleşmesi ölçüt ilkesi ayarında İzin Ver ve Cihazı yükleme ilkelerini engelleme için katmanlı değerlendirme sırası uygula ayarını etkinleştirin.

Bu ilke ayarını etkinleştirirseniz Windows donanım kimliği veya uyumlu kimliği bulunan bir cihazı yüklemesi engellendiğinden, bu ayar sizin oluşturmanıza göre görüntülenir. Bir uzak masaüstü sunucusunda bu ilke ayarını etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinde uzak masaüstü sunucusuna yeniden yönlendirilmesine etki ediyordur.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, cihazlar diğer ilke ayarları tarafından izin verilen şekilde yüklenebilir ve güncelleştirilebilir veya önlenebilir.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Bu cihaz örneği kimlikleri ile eşleşmeye neden olan cihazların yüklenmesine engel olun

Bu ilke ayarı, cihaz yüklemesi engel olan cihazlar için Tak ve Çalıştır cihaz Windows kimlikleri belirtmenize olanak tanır. Bu ilke ayarı, kullanıcıların cihaz yüklemelerine izin veren diğer tüm Windows ilke ayarına göre önceliklidir.

Bu ilke ayarını etkinleştirirseniz, Windows kimliği sizin oluşturmanızda cihaz örneği kimliği görünen bir cihazı yüklemesi engellenebilir. Bir uzak masaüstü sunucusunda bu ilke ayarını etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinde uzak masaüstü sunucusuna yeniden yönlendirilmesine etki ediyordur.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, cihazlar diğer ilke ayarları tarafından izin verilen şekilde yüklenebilir ve güncelleştirilebilir veya önlenebilir.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Bu cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların yüklemesini engelleme

Bu ilke ayarı, cihaz kurulum sınıfı genel benzersiz tanımlayıcıları (GUID) içeren ve yüklemesi engel olan sürücü paketleri için bir Windows belirtmenize olanak sağlar. Varsayılan olarak, bu ilke ayarı kullanıcıların cihaz yüklemelerine izin veren diğer tüm Windows ilke ayarına göre önceliklidir.

> [!NOTE]
> Bu cihaz kimliklerinin herhangi biri ile eşleşmeye izin ver ve Bu cihaz örneğin kimlikleri ilke ayarlarından herhangi birini eşleyen cihazların yüklenmesine izin ver ilke ayarlarını geçerli cihazlar için bu ilke ayarının yerine kullanmak için, Cihaz yüklemesine  izin ver ve Cihazı yükleme ilkelerini tüm cihaz yüklemesi için izin ver ve Engelle ölçütleri ilke ayarı için Katmanlı değerlendirme sırası uygula ayarını etkinleştirin. 

Bu ilke ayarını etkinleştirirseniz, Windows kurulum sınıfı GUID'leri oluştur listesinde görünen sürücü paketlerini yüklemesi veya güncelleştirmesi engellenebilir. Bir uzak masaüstü sunucusunda bu ilke ayarını etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinde uzak masaüstü sunucusuna yeniden yönlendirilmesine etki ediyordur.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, Windows ilke ayarları tarafından izin verilen veya engellenebilir şekilde cihazları yükleyebilir ve güncelleştirebilirsiniz.

### <a name="prevent-installation-of-removable-devices"></a>Çıkarılabilir cihazların yüklemesini engelleme

Bu ilke ayarı, çıkarılabilir Windows yüklemesini önlemeye olanak tanır. Bağlı olduğu cihazın sürücüsü cihazın çıkarılabilir olduğunu gösterirken, cihaz çıkarılabilir olarak kabul edilir. Örneğin, Evrensel Seri Yol (USB) cihazının, cihazın bağlı olduğu USB hub sürücüleri tarafından çıkarılabilir olduğu bildiriliyor. Varsayılan olarak, bu ilke ayarı kullanıcıların cihaz yüklemelerine izin veren diğer tüm Windows ilke ayarına göre önceliklidir.

> [!NOTE]
> Bu cihaz kurulum sınıflarını kullanan cihazların yüklenmesine izin **ver, Bu** cihaz kimlikleri ile eşleşmeye izin ver ve Tüm cihaz eşleşme ölçütleri ilkesi ayarında cihaz  yüklemesine izin ver ve Tüm cihaz yüklemesi ölçütleri ilke ayarında cihaz yüklemesine izin ver ilke ayarlarının yerine bu ilke ayarının yerine geç ayarını  etkinleştirmek için, Cihaz yüklemesine izin ver ve Tüm cihaz yüklemesi ilkelerini engelleme ölçütleri ilkesi ayarı için Katmanlı değerlendirme uygula ayarını etkinleştirin. 

Bu ilke ayarını etkinleştirirseniz, Windows çıkarılabilir cihazların yüklemesi engellenmiştir ve mevcut çıkarılabilir cihazların sürücüleri güncelleştirilemez. Uzak masaüstü sunucusunda bu ilke ayarını etkinleştirirseniz, ilke ayarı çıkarılabilir cihazların uzak masaüstü istemciden uzak masaüstü sunucusuna yeniden yönlendirmesini etkiler.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, Windows olarak çıkarılabilir cihazlar için sürücü paketlerini izin verilen veya diğer ilke ayarlarının engellemiş olduğu şekilde yükleyebilir ve güncelleştirebilirsiniz.

## <a name="common-removable-storage-access-control-scenarios"></a>Ortak Çıkarılabilir Depolama Access Denetimi senaryoları

Uç Nokta Çıkarılabilir veya Erişim Denetimi'Depolama Microsoft Defender'ı tanımanıza yardımcı olmak için, takip etmek için bazı yaygın senaryoları bir araya getirdik.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Senaryo 1: Yalnızca yetkili bir USB usb sürücü yüklemelerine izin verirken tüm USB cihazlarının yüklemesini engelleme

Bu senaryoda, aşağıdaki ilkeler kullanılır:

- Bu cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların yüklemesini engelin.
- Tüm cihaz eşleşme ölçütleri genelinde Cihaz yüklemesine izin ver ve Engelle ilkeleri için katmanlı değerlendirme sırası uygulama.
- Bu cihaz örnek kimliklerinin herhangi biri ile eş alan cihazların yüklenmesine izin ver veya Bu cihaz kimlikleri ile eşleşmeye izin ver cihazların yüklenmesine izin ver.

#### <a name="deploying-and-managing-policy-via-intune"></a>Intune aracılığıyla ilke dağıtma ve yönetme

Cihaz yükleme özelliği, Intune aracılığıyla cihaza ilke uygulamana olanak sağlar.

#### <a name="licensing"></a>Lisanslama

Cihaz yükleme işlemini başlatmadan önce cihaz aboneliğinizi Microsoft 365 [gerekir](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Cihaz yüklemesi'ne erişmek ve cihaz yüklemesini kullanmak için cihaz Microsoft 365 E3.

#### <a name="permission"></a>İzin

Intune'da ilke dağıtımı için, hesabın cihaz yapılandırma profillerini oluşturma, düzenleme, güncelleştirme veya silme izinleri olması gerekir. Bu izinlerle özel roller oluşturabilir veya yerleşik rollerden herhangi birini kullanabilirsiniz:

- İlke ve profil Yöneticisi rolü
- Cihaz Yapılandırması profilleri için Rapor Oluştur/Düzenle/Güncelleştir/Oku/Sil/Görüntüle izinleri açıkken özel bir rol de kullanabilirsiniz
- Veya Genel yönetici

#### <a name="deploying-policy"></a>İlke dağıtma

In Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. Yapılandırma **Bu cihaz kurulum sınıflarını eşleyen sürücüleri kullanarak cihazların yüklemesini engelle**.

    - Uç nokta güvenliği > Saldırı yüzeyini azaltmayı > İlke Oluşturma > Platform: Windows 10 (ve sonrası) &: Cihaz denetimi.

      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="profili düzenle":::

2. BIR USB cihazı takın ve aşağıdaki hata iletisini alırsınız:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="hata iletisi":::

3. Tüm **cihaz eşleşme ölçütleri genelinde Cihaz yükleme ilkelerine İzin Ver ve Engelle için Katmanlı değerlendirme sırası uygulama'ya olanak sağlar**.

    - **şimdilik yalnızca OMA-URI'yi** destekleme: Cihazlar > Yapılandırma profilleri > Profil > Platformu: Windows 10 (ve sonrası) & Profil: Özel

      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="satır düzenleme":::

4. İzin verilen USB Örneği Kimliğini etkinleştir ve ekle – Bu cihaz kimlikleri ile **eşleşmesi olan cihazların yüklenmesine izin ver**.

    - Adım 1 Cihaz denetimi profilini güncelleştirme

      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="cihaz denetimi":::

    PCI\CC_0C03 ekleme; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Üst ekran USB20_HUB üzerindeki USB\USB20_HUB bağlantısı, tek bir USB thumb-drive'ı etkinleştirmek için tek bir donanım kimliğini etkinleştirmek için yeterli değildir. Hedef usb cihazının önceki tüm USB cihazlarının engellenmiş (izin verilmiyor) olduğundan da emin olun. Cihaz Yöneticisi'ni açabilir ve PnP ağacına cihazların yüklenme yolunu görmek için görünümü 'Bağlantılara göre cihazlar' olarak değiştirebilirsiniz. Bu durumda hedef USB usb sürücüsüne de izin verilmiyor olabilir:

    - "Intel(R) USB 3.0 kullanılabilir Ana Bilgisayar Denetleyicisi – 1.0 (Microsoft)" -> PCI\CC_0C03
    - "USB Kök Merkezi (USB 3.0)" -> USB\ROOT_HUB30
    - "Generic USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="cihaz denetimi":::

    > [!NOTE]
    > Sistemdeki bazı cihazların, sisteme yüklemelerini tanımlamak için çeşitli bağlantı katmanları vardır. USB flash sürücüler bu tür cihazlardır. Dolayısıyla, bir sistemde bunları engelleme veya izin verme konularına bakarak, her cihaz için bağlantı yolunu anlamak önemlidir. Sistemlerde yaygın olarak kullanılan ve bu gibi durumlarda "İzin Ver listesi" oluşturmak için iyi bir başlangıç sağlayan birkaç genel cihaz kimlikleri vardır. Aşağıdaki örneklerden biridir (tüm USB'ler için her zaman aynı değildir; Cihaz Yöneticisi aracılığıyla yönetmek istediğiniz cihazın PnP ağacını anlamanız gerekir):
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (Ana Bilgisayar Denetleyicileri için)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (USB Kök Hub'lar için)/ USB\USB20_HUB (Genel USB Hub'lar için)/
    >
    > Özellikle masaüstü makineleri için, klavye ve farelerin bağlı olduğu tüm USB cihazlarını yukarıdaki listede listeleyebilirsiniz. Bu yapılam, kullanıcının HID cihazları aracılığıyla makinesine erişmesini engelleyebilir.
    >
    > Farklı bilgisayar üreticilerinin bazen USB cihazlarını PnP ağacına yerleştirmenin farklı yolları vardır, ancak genel olarak bu şekilde yapılır.

5. İzin verilen USB'i yeniden takın. Artık buna izin verilmiyor ve kullanılabilir olduğunu görüyorsunuz.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="sürücüyü kaldır":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Grup İlkesi aracılığıyla ilke dağıtma ve yönetme

Cihaz yükleme özelliği, Grup İlkesi aracılığıyla ilke uygulamana olanak sağlar.

#### <a name="licensing"></a>Lisanslama

Cihaz yüklemesi'ne erişmek ve bu cihazı kullanmak için E3'Windows gerekir.

#### <a name="deploying-policy"></a>İlke dağıtma

Dağıtım ayrıntılarını burada bulabilirsiniz: [Grup İlkesi (Grup İlkesi (Windows 10) - Windows İstemcisi ile Cihaz Yükleme'Windows.](/windows/client-management/manage-device-installation-with-group-policy)

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'Depolama Access Denetimi'nin çıkarılabilir verilerini görüntüleme

En [Microsoft 365 portalı](https://sip.security.microsoft.com/homepage), Cihaz Denetim Cihazı Yüklemesi tarafından engellenen çıkarılabilir depolama alanını gösterir. Güvenlik Microsoft 365 için aşağıdaki aboneliğe sahip olmak gerekir:

- Microsoft 365 raporlaması

```kusto
//events triggered by Device Installation policies
DeviceEvents
| where ActionType == "PnpDeviceBlocked" or ActionType == "PnpDeviceAllowed"
| extend parsed=parse_json(AdditionalFields)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaDeviceId = tostring(parsed.MatchingDeviceId)
| project Timestamp , DeviceId, DeviceName, ActionType, MediaClassGuid, MediaDeviceId, MediaInstanceId, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="depolamayı engelleme":::

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Dağıtılan ilkeyi hedef makinenin alır mı?

Güvenlik portalında kötü amaçlı yazılımlardan koruma istemci sürümünü almak için aşağıdaki Microsoft 365 kullanabilirsiniz:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>İzin Ver ilkesi neden çalışmıyor?

Tek bir USB başparmak sürücüsü yalnızca tek bir donanım kimliğini etkinleştirmek için yeterli değildir. Hedef usb cihazlarının önünde yer alan tüm USB cihazlarının engellenmiş (izin verilmiyor) olduğundan emin olun.

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Cihaz yükleme hakkında sss":::
