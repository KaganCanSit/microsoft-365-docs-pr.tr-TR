---
title: Uç Nokta için Microsoft Defender'da cihaz grupları oluşturma ve yönetme
description: Grup için geçerli kuralları onaylayabilir ve cihaz grupları oluşturabilir ve otomatik düzeltme düzeyleri oluşturabilirsiniz
keywords: cihaz grupları, gruplar, düzeltme, düzey, kurallar, aad grubu, rol, ata, derece
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 951e49ddb7cb9ed0154fa70f66d54944a8aae066
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010812"
---
# <a name="create-and-manage-device-groups"></a>Cihaz grupları oluşturma ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Azure Active Directory
- Office 365
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kurumsal bir senaryoda güvenlik işlemi ekiplerine genellikle bir cihaz kümesi atanır. Bu cihazlar, etki alanları, bilgisayar adları veya belirlenen etiketler gibi öznitelikler kümesine göre birlikte gruptur.

Uç Nokta için Microsoft Defender'da cihaz grupları oluşturabilir ve bunları kullanarak şunları yapmak için kullanabilirsiniz:

- İlgili uyarılar ve verilere erişimi, atanmış RBAC rolleriyle belirli Azure AD [kullanıcı gruplarıyla sınırlandırma](rbac.md)
- Farklı cihaz kümeleri için farklı otomatik düzeltme ayarlarını yapılandırma
- Otomatik soruşturmalar sırasında uygulamak için belirli düzeltme düzeyleri atama
- Araştırmada, Grup **filtresini kullanarak** Cihazlar listesine belirli cihaz **gruplarına filtre** uygulama.

Kimlerin belirli bir işlemde yer atayasını kontrol etmek veya cihaz gruplarını bir kullanıcı grubuna ataarak bilgileri görmek için, rol tabanlı erişim (RBAC) bağlamında cihaz grupları oluşturabilirsiniz. Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).

> [!TIP]
> RBAC uygulamasına kapsamlı bir bakış için, şunları okuyun: [SOC'niz RBAC ile düz çalışıyor mu](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015)?

Cihaz grubu oluşturma işleminin bir parçası olarak şunları da

- Bu grup için otomatik düzeltme düzeyini ayarlayın. Düzeltme düzeyleri hakkında daha fazla bilgi için bkz. [Tehditleri araştırmak ve düzeltmek için Otomatik araştırmayı kullanma](automated-investigations.md).
- Cihaz adı, etki alanı, etiketler ve işletim sistemi platformuna göre gruba hangi cihaz grubunun ait olduğunu belirleyen eşleşen kuralı belirtin. Bir cihaz diğer gruplarla da eşleniyorsa, yalnızca en yüksek dereceli cihaz grubuna eklenir.
- Cihaz grubuna erişimi olması gereken Azure AD kullanıcı grubunu seçin.
- Cihaz grubunu, oluşturulduktan sonra diğer gruplara göre dereceye göre sıralar.

> [!NOTE]
> Cihaz grubuna Azure AD grubu atamadığınız zaman, o cihaz grubuna tüm kullanıcılar tarafından erişilebilir.

## <a name="create-a-device-group"></a>Cihaz grubu oluşturma

1. Gezinti bölmesinde, Uç Noktalar **İzinleri Ayarlar** \> **Grupları'Ayarlar seçin** \>  \>.

2. Cihaz **grubu ekle'ye tıklayın**.

3. Grup adını ve otomasyon ayarlarını girin ve gruba hangi cihazların ait olduğunu belirleyen eşleşen kuralı belirtin. Bkz [. Otomatik soruşturma nasıl başlatılır](automated-investigations.md#how-the-automated-investigation-starts).

    > [!TIP]
    > Etiketlemeyi, gruplama cihazlarını etiketlemek için kullanmak için bkz [. Cihaz etiketleri oluşturma ve yönetme](machine-tags.md).

4. Bu kuralla eşleşmesi için birkaç cihazı önizle. Kuraldan memnunsanız Kullanıcı erişimi **sekmesine** tıklayın.

5. Oluşturduğunuz cihaz grubuna erişen kullanıcı gruplarını attayabilirsiniz.

    > [!NOTE]
    > Yalnızca RBAC rollerine atanmış Azure AD kullanıcı gruplarına erişim izni veabilirsiniz.

6. **Kapat**'a tıklayın. Yapılandırma değişiklikleri uygulanır.

## <a name="manage-device-groups"></a>Cihaz gruplarını yönetme

Eşleştirme sırasında daha yüksek veya daha düşük öncelik verilmesi için cihaz grubunun sıradaki derecelerini yükseltebilirsiniz veya düşürebilirsiniz. Bir cihaz birden fazla grupla eş olduğunda, yalnızca en yüksek dereceli gruba eklenir. Ayrıca grupları düzenleyebilir ve silebilirsiniz.

> [!WARNING]
> Cihaz grubunun silinmesi e-posta bildirim kurallarını etkileyebilir. Cihaz grubu bir e-posta bildirim kuralı altında yapılandırıldısa, bu kuraldan kaldırılır. Cihaz grubu, bir e-posta bildirimi için yapılandırılmış tek grupsa, cihaz grubuyla birlikte bu e-posta bildirimi kuralı da silinir.

Varsayılan olarak, cihaz gruplarına portal erişimi olan tüm kullanıcılar tarafından erişilebilir. Cihaz grubuna Azure AD kullanıcı grupları ataarak varsayılan davranışı değiştirebilirsiniz.

Hiçbir grupla eşleşmemiş cihazlar, Gruplandırlanmamış cihazlar (varsayılan) grubuna eklenir. Bu grubun sıradaki sıradakini değiştiremez veya silemezsiniz. Bununla birlikte, bu grubun düzeltme düzeyini değiştirebilir ve bu gruba erişen Azure AD kullanıcı gruplarını tanımlayabilirsiniz.

> [!NOTE]
> Cihaz grubu yapılandırmasında değişikliklerin uygulanması birkaç dakika sürebilir.

### <a name="add-device-group-definitions"></a>Cihaz grubu tanımları ekleme

Cihaz grubu tanımları, her koşul için birden çok değer de içerebilir. Tek bir cihaz grubunun tanımına birden çok etiket, cihaz adı ve etki alanı oluşturabilirsiniz.

1. Yeni bir cihaz grubu oluşturun, ardından **Cihazlar sekmesini seçin** .
2. Koşullardan biri için ilk değeri ekleyin.
3. Aynı `+` özellik türünde başka satırlar eklemek için öğesini seçin.

> [!TIP]
> Özellik başına birden çok değere izin veren aynı koşul türüne sahip satırlar arasında 'VEYA' işleci kullanın.
> Her özellik türü (etiket, cihaz adı, etki alanı) için en çok 10 satır (değer) ebilirsiniz.

Cihaz grupları tanımlarına bağlama hakkında daha fazla bilgi için bkz. [Cihaz grupları - Microsoft 365 bakın](https://sip.security.microsoft.com/homepage).

## <a name="related-topics"></a>İlgili konular

- [Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md)
- [Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md)
- [GRAPH API'sini kullanarak kiracı cihaz gruplarının listesini edinin](/graph/api/device-list-memberof)
