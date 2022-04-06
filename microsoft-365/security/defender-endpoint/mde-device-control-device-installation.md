---
title: Cihaz Denetimi Cihazı Yüklemesini Uç Nokta için Microsoft Defender
description: Bu konu başlığında, Uç Nokta için Microsoft Defender Cihaz Denetimi Cihazı Yüklemesi hakkında bir kılavuz sağlanır
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
ms.openlocfilehash: dc05633d1badfc29b2179915ac6d318dd9523834
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666404"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Cihaz Denetimi Cihazı Yüklemesini Uç Nokta için Microsoft Defender

**Uygulandığı öğe**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender Cihaz Denetimi Cihazı Yüklemesi aşağıdaki görevi gerçekleştirmenizi sağlar:

- Kişilerin belirli cihazları yüklemesini engelleyin.
- Kişilerin belirli cihazları yüklemesine izin verin ancak diğer cihazları engelleyin.

> [!NOTE]
> Cihaz Yükleme ve Çıkarılabilir depolama erişim denetimi arasındaki farkı bulmak için bkz. [Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Koruması](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Ayrıcalık|Izni|
|---|---|
|Access|Cihaz yüklemesi |
|Eylem Modu|İzin Ver, Engelle |
|CSP Desteği|Evet|
|GPO Desteği|Evet|
|Kullanıcı Tabanlı Destek|Hayır|
|Makine Tabanlı Destek|Evet|

## <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Windows 10, Windows 11 cihazlarda Windows Server 2022'de Cihaz Yükleme'yi dağıtın.

## <a name="device-properties"></a>Cihaz özellikleri

Aşağıdaki cihaz özellikleri Cihaz Yükleme desteği tarafından desteklenir:

- Cihaz Kimliği
- Donanım Kimliği
- Uyumlu Kimlik
- Cihaz Sınıfı
- 'Çıkarılabilir Cihaz' Cihaz türü: Bazı cihazlar Çıkarılabilir Cihaz olarak sınıflandırılabilir. Bağlı olduğu cihazın sürücüsü cihazın çıkarılabilir olduğunu gösterdiğinde bir cihaz çıkarılabilir olarak kabul edilir. Örneğin, bir USB cihazının bağlı olduğu USB hub'ına ait sürücüler tarafından çıkarılabilir olduğu bildirilir.
Daha fazla bilgi için bkz. [Windows'de Cihaz Yüklemesi](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>İlkeler

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Bu Cihaz Kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver

Bu ilke ayarı, Windows yüklemesine izin verilen cihazlar için Tak ve Kullan donanım kimliklerinin ve uyumlu kimliklerin listesini belirtmenize olanak tanır. Bu ilke ayarı yalnızca **Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı etkinleştirildiğinde kullanılmak üzere tasarlanmıştır.

Bu ilke ayarı **, Tüm cihaz eşleştirme ölçütleri arasında cihaz yükleme ilkelerine izin ver ve Engelle için katmanlı değerlendirme sırası uygula** ilke ayarıyla birlikte etkinleştirildiğinde, Windows hiyerarşide aynı veya daha üst katmanda yer alan başka bir ilke ayarı özellikle engellemediği sürece, oluşturduğunuz listede Tak ve Kullan donanım kimliği veya uyumlu kimliği görünen tüm cihazları yüklemesine veya güncelleştirmesine izin verilir  aşağıdaki ilke ayarları gibi yükleme:

- Bu cihaz kimlikleriyle eşleşen cihazların yüklenmesini engelleyin.
- Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesini engelleyin.

**Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı bu ilke ayarıyla etkinleştirilmediyse, yüklemeyi özellikle engelleyen diğer ilke ayarları öncelikli olur.

> [!NOTE]
> **Diğer ilke ayarları tarafından açıklanmamış cihazların yüklenmesini engelle** ilke ayarı, desteklenen hedef Windows 10 sürümleri **ve Windows 11 için Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarıyla değiştirilmiştir. Mümkün olduğunda **tüm cihaz eşleştirme ölçütleri ilkesinde cihaz yükleme ilkelerine izin ver ve engelle için Katmanlı değerlendirme sırası uygula** ayarını kullanmanız önerilir.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver

Bu ilke ayarı, Windows yüklenmesine izin verilen cihazlar için Tak ve Kullan cihaz örneği kimliklerinin listesini belirtmenize olanak tanır. Bu ilke ayarı yalnızca **Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı etkinleştirildiğinde kullanılmak üzere tasarlanmıştır.

Bu ilke ayarı **, Tüm cihaz eşleştirme ölçütleri arasında cihaz yükleme ilkelerine izin ver ve Engelle için katmanlı değerlendirme sırası uygula** ilke ayarıyla birlikte etkinleştirildiğinde, Windows hiyerarşideki aynı veya daha üst katmandaki başka bir ilke ayarı özellikle bunu engellemediği sürece, oluşturduğunuz listede Tak ve Kullan cihaz örneği kimliği görünen herhangi bir cihazı yüklemesine veya güncelleştirmesine izin verilir  yüklemesini seçin; örneğin, aşağıdaki ilke ayarları:

- Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesini engelle

**Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı bu ilke ayarıyla etkinleştirilmediyse, yüklemeyi özellikle engelleyen diğer ilke ayarları öncelikli olur.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesine izin ver

Bu ilke ayarı, Windows yüklemesine izin verilen sürücü paketleri için cihaz kurulum sınıfı genel olarak benzersiz tanımlayıcıların (GUID) listesini belirtmenize olanak tanır. Bu ilke ayarı yalnızca **Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı etkinleştirildiğinde kullanılmak üzere tasarlanmıştır.

Bu ilke ayarı **, Tüm cihaz eşleştirme ölçütleri arasında cihaz yükleme ilkelerine izin ver ve Engelle için katmanlı değerlendirme sırası uygula** ilke ayarıyla birlikte etkinleştirildiğinde, Windows, hiyerarşideki aynı veya daha yüksek katmandaki başka bir ilke ayarı bu yüklemeyi özellikle engellemediği sürece, oluşturduğunuz listede cihaz kurulum sınıfı GUID'leri görünen sürücü paketlerini yüklemesine veya güncelleştirmesine izin verilir.  örneğin, aşağıdaki ilke ayarları:

- Bu cihaz sınıfları için cihazların yüklenmesini engelle
- Bu cihaz kimlikleriyle eşleşen cihazların yüklenmesini engelle
- Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesini engelle

**Tüm cihaz eşleştirme ölçütleri için cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı bu ilke ayarıyla etkinleştirilmediyse, yüklemeyi özellikle engelleyen diğer ilke ayarları öncelikli olur.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Tüm cihaz eşleştirme ölçütlerine cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygulama

Bu ilke ayarı, belirli bir cihaz için birden fazla yükleme ilkesi ayarı geçerli olduğunda, ilke ayarlarının uygulanmasına izin ver ve engelle değerlendirme sırasını değiştirir. Çakışan cihaz eşleştirme ölçütlerinin, daha belirli eşleşme ölçütlerinin daha az belirli eşleşme ölçütlerinin yerini aldığı yerleşik bir hiyerarşiye göre uygulandığından emin olmak için bu ilke ayarını etkinleştirin. Cihaz eşleştirme ölçütlerini belirten ilke ayarları için hiyerarşik değerlendirme sırası aşağıdaki gibidir:

**Cihaz örneği kimlikleri** \> **Cihaz Kimlikleri** \> **Cihaz kurulum sınıfı** \> **Çıkarılabilir cihazlar**

#### <a name="device-instance-ids"></a>Cihaz örneği kimlikleri

1. Bu cihaz örneği kimlikleriyle eşleşen sürücüleri kullanarak cihazların yüklenmesini engelleyin.
2. Bu cihaz örneği kimlikleriyle eşleşen sürücüleri kullanarak cihazların yüklenmesine izin verin.

#### <a name="device-ids"></a>Cihaz Kimlikleri

1. Bu cihaz kimlikleriyle eşleşen sürücüleri kullanarak cihazların yüklenmesini engelleyin.
2. Bu cihaz kimlikleriyle eşleşen sürücüleri kullanarak cihazların yüklenmesine izin verin.

#### <a name="device-setup-class"></a>Cihaz kurulum sınıfı

1. Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesini engelleyin.
2. Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesine izin verin.

#### <a name="removable-devices"></a>Çıkarılabilir cihazlar

Çıkarılabilir cihazların yüklenmesini engelleme

> [!NOTE]
> Bu ilke ayarı, **Diğer ilke ayarları ilke ayarı tarafından açıklanmayan cihazların yüklenmesini engelle** ilke ayarından daha ayrıntılı denetim sağlar. Bu çakışan ilke ayarları aynı anda etkinleştirilirse, **Tüm cihaz eşleştirme ölçütlerinde cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarı etkinleştirilir ve diğer ilke ayarı yoksayılır.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Bu cihaz kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesini engelle

Bu ilke ayarı, Windows yüklenmesi engellenen cihazlar için Tak ve Kullan donanım kimliklerinin ve uyumlu kimliklerin listesini belirtmenize olanak tanır. Varsayılan olarak, bu ilke ayarı, Windows bir cihazı yüklemesine izin veren diğer ilke ayarlarına göre önceliklidir.

> [!NOTE]
> Geçerli cihazlar için bu ilke ayarının yerine geçmek üzere **Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver** ilke ayarını etkinleştirmek için **, Tüm cihaz eşleştirme ölçütlerinde cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarını etkinleştirin.

Bu ilke ayarını etkinleştirirseniz, Windows donanım kimliği veya uyumlu kimliği oluşturduğunuz listede görünen bir cihaz yüklemesini engeller. Bu ilke ayarını bir uzak masaüstü sunucusunda etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinden uzak masaüstü sunucusuna yeniden yönlendirilmesini etkiler.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, cihazlar diğer ilke ayarları tarafından izin verilen veya engellenen şekilde yüklenebilir ve güncelleştirilebilir.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesini engelle

Bu ilke ayarı, Windows yüklenmesi engellenen cihazlar için Tak ve Kullan cihaz örneği kimliklerinin listesini belirtmenize olanak tanır. Bu ilke ayarı, Windows bir cihazı yüklemesine izin veren diğer ilke ayarlarına göre önceliklidir.

Bu ilke ayarını etkinleştirirseniz, Windows cihaz örneği kimliği oluşturduğunuz listede görünen bir cihazı yüklemesi engellenir. Bu ilke ayarını bir uzak masaüstü sunucusunda etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinden uzak masaüstü sunucusuna yeniden yönlendirilmesini etkiler.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, cihazlar diğer ilke ayarları tarafından izin verilen veya engellenen şekilde yüklenebilir ve güncelleştirilebilir.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesini engelle

Bu ilke ayarı, Windows yüklenmesi engellenen sürücü paketleri için cihaz kurulum sınıfı genel olarak benzersiz tanımlayıcıların (GUID) listesini belirtmenize olanak tanır. Varsayılan olarak, bu ilke ayarı, Windows bir cihazı yüklemesine izin veren diğer ilke ayarlarına göre önceliklidir.

> [!NOTE]
> **Bu cihaz kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver** ve **Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver** ilke ayarlarının geçerli cihazlar için bu ilke ayarının yerini almasını sağlamak için, **Tüm cihaz eşleştirme ölçütlerinde cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygula** ilke ayarını etkinleştirin.

Bu ilke ayarını etkinleştirirseniz, Windows cihaz kurulum sınıfı GUID'leri oluşturduğunuz listede görünen sürücü paketlerini yüklemesi veya güncelleştirmesi engellenir. Bu ilke ayarını bir uzak masaüstü sunucusunda etkinleştirirseniz, ilke ayarı belirtilen cihazların uzak masaüstü istemcisinden uzak masaüstü sunucusuna yeniden yönlendirilmesini etkiler.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, Windows diğer ilke ayarları tarafından izin verilen veya engellenen cihazları yükleyebilir ve güncelleştirebilir.

### <a name="prevent-installation-of-removable-devices"></a>Çıkarılabilir cihazların yüklenmesini engelleme

Bu ilke ayarı, Windows çıkarılabilir cihazları yüklemesini engellemenizi sağlar. Bağlı olduğu cihazın sürücüsü cihazın çıkarılabilir olduğunu gösterdiğinde bir cihaz çıkarılabilir olarak kabul edilir. Örneğin, bir Evrensel Seri Veri Yolu (USB) cihazının, cihazın bağlı olduğu USB hub'ına ait sürücüler tarafından çıkarılabilir olduğu bildirilir. Varsayılan olarak, bu ilke ayarı, Windows bir cihazı yüklemesine izin veren diğer ilke ayarlarına göre önceliklidir.

> [!NOTE]
> **Bu cihaz kurulum sınıflarıyla eşleşen sürücüleri kullanarak cihazların yüklenmesine izin ver**, **Bu cihaz kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver** ve **Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver** ilke ayarlarının geçerli cihazlar için bu ilke ayarının yerini almasını sağlamak için, **Tüm cihaz eşleştirme ölçütlerinde cihaz yükleme ilkelerine izin ver ve engelle ilke ayarı için Katmanlı değerlendirme sırası uygula** seçeneğini etkinleştirin.

Bu ilke ayarını etkinleştirirseniz, Windows çıkarılabilir cihazların yüklenmesi engellenir ve mevcut çıkarılabilir cihazların sürücüleri güncelleştirilemez. Bu ilke ayarını uzak masaüstü sunucusunda etkinleştirirseniz, ilke ayarı çıkarılabilir cihazların uzak masaüstü istemcisinden uzak masaüstü sunucusuna yeniden yönlendirilmesini etkiler.

Bu ilke ayarını devre dışı bırakır veya yapılandırmazsanız, Windows diğer ilke ayarları tarafından izin verilen veya engellenen çıkarılabilir cihazlar için sürücü paketlerini yükleyebilir ve güncelleştirebilir.

## <a name="common-removable-storage-access-control-scenarios"></a>Yaygın Çıkarılabilir Depolama Access Control senaryoları

Çıkarılabilir Depolama Access Control Uç Nokta için Microsoft Defender hakkında bilgi sahibi olmanıza yardımcı olmak için izlemeniz gereken bazı yaygın senaryoları bir araya topladık.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Senaryo 1: Yalnızca yetkili bir USB başparmak sürücüsünün yüklenmesine izin verirken tüm USB cihazlarının yüklenmesini engelleme

Bu senaryo için aşağıdaki ilkeler kullanılacaktır:

- Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesini engelleyin.
- Tüm cihaz eşleştirme ölçütlerine cihaz yükleme ilkelerine izin ver ve engelle için katmanlı değerlendirme sırası uygulayın.
- Bu cihaz örneği kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver veya Bu cihaz kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin ver.

#### <a name="deploying-and-managing-policy-via-intune"></a>Intune aracılığıyla ilke dağıtma ve yönetme

Cihaz yükleme özelliği, cihaza Intune aracılığıyla ilke uygulamanızı sağlar.

#### <a name="licensing"></a>Lisanslama

Cihaz yüklemeye başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) onaylamanız gerekir. Cihaz yüklemesine erişmek ve bunları kullanmak için Microsoft 365 E3 sahip olmanız gerekir.

#### <a name="permission"></a>Izni

Intune'da İlke dağıtımı için hesabın cihaz yapılandırma profillerini oluşturma, düzenleme, güncelleştirme veya silme izinleri olmalıdır. Özel roller oluşturabilir veya şu izinlere sahip yerleşik rollerden herhangi birini kullanabilirsiniz:

- İlke ve profil Yöneticisi rolü
- Veya Cihaz Yapılandırması profilleri için Raporları Oluşturma/Düzenleme/Güncelleştirme/Okuma/Silme/Görüntüleme izinlerinin açık olduğu özel rol
- Veya Genel yönetici

#### <a name="deploying-policy"></a>İlke dağıtma

Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. **Bu cihaz kurulum sınıfları ile eşleşen sürücüleri kullanarak cihazların yüklenmesini engelle'yi** yapılandırın.

    - Uç nokta güvenliği > Saldırı yüzeyini azaltma > İlke > Platformu Oluşturma: Windows 10 (ve üzeri) & Profili: Cihaz denetimi'ni açın.

      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Profili düzenle sayfası" lightbox="../../media/devicepolicy-editprofile.png":::

2. BIR USB, cihaz taktığınızda aşağıdaki hata iletisini görürsünüz:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Hata iletisi" lightbox="../../media/devicepolicy-errormsg.png":::

3. **Tüm cihaz eşleştirme ölçütleri genelinde cihaz yükleme ilkelerine izin ver ve engelle için Katmanlı değerlendirme sırasını uygula'yı** etkinleştirin.

    - **şimdilik yalnızca OMA-URI desteği**: Cihazlar > Yapılandırma profilleri > Profil oluşturma > Platform: Windows 10 (ve üzeri) & Profili: Özel

      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Satırı Düzenle sayfası" lightbox="../../media/devicepolicy-editrow.png":::

4. İzin verilen USB Örneği Kimliğini etkinleştirme ve ekleme – **Bu cihaz kimliklerinden herhangi biriyle eşleşen cihazların yüklenmesine izin verin**.

    - 1. adım Cihaz denetim profilini güncelleştirme

      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Cihaz Denetimi sayfasındaki bir tanımlayıcı" lightbox="../../media/devicepolicy-devicecontrol.png":::

    PCI\CC_0C03 ekleme; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Yukarıdaki ekran görüntüsündeki USB\USB20_HUB, tek bir USB başparmak sürücüsünü etkinleştirmek için yalnızca tek bir donanım kimliğini etkinleştirmenin yeterli olmamasıdır. Hedef cihazdan önceki tüm USB cihazlarının da engellenmediğinden (izin verilmediğinden) emin olmanız gerekir. PnP ağacında cihazların nasıl yüklendiğini görmek için Aygıt Yöneticisi açabilir ve görünümü 'Bağlantılara göre cihazlar' olarak değiştirebilirsiniz. Bizim örneğimizde, hedef USB başparmak sürücüsüne de izin verebilmek için aşağıdaki cihazlara izin verilmelidir:

    PCI\CC_0C03 ekleme; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Yukarıdaki ekran görüntüsündeki USB\USB20_HUB, tek bir USB başparmak sürücüsünü etkinleştirmek için yalnızca tek bir donanım kimliğini etkinleştirmenin yeterli olmamasıdır. Hedef cihazdan önceki tüm USB cihazlarının da engellenmediğinden (izin verilmediğinden) emin olmanız gerekir. PnP ağacında cihazların nasıl yüklendiğini görmek için Aygıt Yöneticisi açabilir ve görünümü 'Bağlantılara göre cihazlar' olarak değiştirebilirsiniz. Bizim örneğimizde, hedef USB başparmak sürücüsüne de izin verebilmek için aşağıdaki cihazlara izin verilmelidir:

    - "Intel(R) USB 3.0 eXtensible Konak Denetleyicisi – 1.0 (Microsoft)" -> PCI\CC_0C03
    - "USB Kök Hub'ı (USB 3.0)" -> USB\ROOT_HUB30
    - "Genel USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Aygıt Yöneticisi sayfasındaki Görünüm menü öğesi" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Sistemdeki bazı cihazların, sistemdeki yüklemelerini tanımlamak için çeşitli bağlantı katmanları vardır. USB başparmak sürücüleri bu tür cihazlardır. Bu nedenle, bir sistemde bunları engellemek veya izin vermek istediğinizde, her cihaz için bağlantı yolunu anlamak önemlidir. Sistemlerde yaygın olarak kullanılan ve bu gibi durumlarda "İzin ver listesi" oluşturmak için iyi bir başlangıç sağlayabilecek birkaç genel cihaz kimliği vardır. Aşağıda bir örnek verilmiştir (tüm USB'ler için her zaman aynı değildir; Aygıt Yöneticisi aracılığıyla yönetmek istediğiniz cihazın PnP ağacını anlamanız gerekir):
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (Konak Denetleyicileri için)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (USB Kök Hub'ları için)/ USB\USB20_HUB (Genel USB Hub'ları için)/
    >
    > Özellikle masaüstü makineler için, klavyelerinizin ve farelerinizin bağlı olduğu tüm USB cihazlarını yukarıdaki listede listelemek önemlidir. Bunun başarısız olması, kullanıcının HID cihazları aracılığıyla makinesine erişmesini engelleyebilir.
    >
    > Farklı bilgisayar üreticileri bazen USB cihazlarını PnP ağacına yerleştirmenin farklı yollarına sahiptir, ancak genel olarak bu şekilde yapılır.

5. İzin verilen USB'yi yeniden takın. Artık izin verilip verilmediğini göreceksiniz.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Sürücü ayrıntılarını kaldır sayfası" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>grup ilkesi aracılığıyla ilke dağıtma ve yönetme

Cihaz yükleme özelliği, grup ilkesi aracılığıyla ilke uygulamanıza olanak tanır.

#### <a name="licensing"></a>Lisanslama

Cihaz yüklemesine erişmek ve bunları kullanmak için Windows E3'e sahip olmanız gerekir.

#### <a name="deploying-policy"></a>İlke dağıtma

Dağıtım ayrıntılarını burada bulabilirsiniz: [grup ilkesi ile Cihaz Yüklemesini Yönetme (Windows 10) - Windows İstemcisi](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Cihaz Denetimi Çıkarılabilir Depolama Access Control verilerini Uç Nokta için Microsoft Defender'da görüntüleme

[Microsoft 365 güvenlik](https://sip.security.microsoft.com/homepage) portalı, Cihaz Denetimi Cihazı Yüklemesi tarafından engellenen çıkarılabilir depolama birimini gösterir. Microsoft 365 güvenliğine erişmek için aşağıdaki aboneliğe sahip olmanız gerekir:

- E5 raporlama için Microsoft 365

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

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="Blok depolama" lightbox="../../media/block-removable-storage2.png":::

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Hedef makinenin dağıtılan ilkeyi alıp almadığını nasıl anlayabilirim?

Microsoft 365 güvenlik portalında kötü amaçlı yazılımdan koruma istemcisi sürümünü almak için aşağıdaki sorguyu kullanabilirsiniz:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>İzin Ver ilkesi neden çalışmıyor?

Tek bir USB başparmak sürücüsünü etkinleştirmek için yalnızca tek bir donanım kimliğini etkinleştirmek yeterli değildir. Hedef cihazdan önceki tüm USB cihazlarının da engellenmediğinden (izin verilmediğinden) emin olun.

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Cihaz yükleme hakkında SSS" lightbox="../../media/devicemgrscrnshot.png":::
