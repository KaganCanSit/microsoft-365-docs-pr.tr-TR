---
title: Yazılım envanteri Tehdit ve Güvenlik Açığı Yönetimi
description: Yazılım stoku için yazılım Uç Nokta için Microsoft Defender sayfası Tehdit ve Güvenlik Açığı Yönetimi yazılımda kaç zayıf noktanın ve güvenlik açıklarının algı olduğunu gösterir.
keywords: Tehdit ve Güvenlik Açığı Yönetimi, Uç Nokta için Microsoft Defender Uç Nokta için Microsoft Defender satın Uç Nokta için Microsoft Defender ve yazılım & güvenlik açığı yönetimi için Uç Nokta için Microsoft Defender ve & güvenlik açığı yönetimi için, Uç Nokta için Microsoft Defender tvm yazılım envanteri, TVM yazılım envanteri
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cbd4634e779fe2bf853aaf014b59b1e7e1c1928f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470053"
---
# <a name="software-inventory---threat-and-vulnerability-management"></a>Yazılım envanteri - Tehdit ve Güvenlik Açığı Yönetimi


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Yazılım envanteri, Tehdit ve Güvenlik Açığı Yönetimi bilinen yazılımların listesidir. Yazılım envanteri sayfasındaki varsayılan filtre resmi Ortak Platform Numaralara [(CPE) sahip tüm yazılımları görüntüler](https://nvd.nist.gov/products/cpe). Görünüm, satıcının adı, zayıf noktaların sayısı, tehdit ve açık cihaz sayısı gibi ayrıntıları içerir.

**CPE Kullanılabilir filtresini kaldırabilir**, daha fazla görünürlük elde etmek ve kuruluşlarınız genelinde tüm yüklü yazılımlarda arama kapsamınızı artırabilirsiniz. Bu, CPE olmayan yazılımlar dahil olmak üzere tüm yazılımların artık yazılım envanter listesinde görüntüleniyor olduğu anlamına gelir.

> [!NOTE]
> CPE'ler güvenlik açığı yönetimi tarafından yazılımı ve güvenlik açıklarını tanımlamak için kullanılırken, CPE olmayan yazılım ürünleri yazılım stok sayfasında gösterse bile, bunlar Tehdit ve Güvenlik Açığı Yönetimi tarafından ve açıklardan yararlanma, açık cihaz sayısı ve zayıf kalma gibi bilgiler tarafından desteklanmaz.

## <a name="how-it-works"></a>Nasıl çalışır?

Keşif alanında, güvenlik algılama ve yanıt özelliklerinde algılama ve güvenlik açığı değerlendirmesi ile aynı [sinyal Uç Nokta için Microsoft Defender sinyallerden yararlanıyoruz](overview-endpoint-detection-response.md).

Gerçek zamanlı olduğu için dakikalar içinde güvenlik açığı bilgilerini keşfedilene kadar görmeye devam edersiniz. Altyapı, birden çok güvenlik akışından bilgileri otomatik olarak yakalar. Aslında, belirli bir yazılımın canlı tehdit kampanyasıyla bağlantılı olup değildir. Ayrıca, kullanılabilir olduğu anda bir Threat Analytics raporunun bağlantısını da sağlar.

## <a name="navigate-to-the-software-inventory-page"></a>Yazılım stoku sayfasına gidin

Yazılım envanteri sayfasına erişmek için, **portalda yer** alan Tehdit ve Güvenlik Açığı Yönetimi menüsünde Yazılım [envanteri Microsoft 365 Defender seçin](portal-overview.md).

Yazılımları, cihazlar listesinden tek tek cihazlar sayfalarında belirli [cihazlarda görüntüleme](machines-view-overview.md).

> [!NOTE]
> Bu özelliği kullanarak yazılım Uç Nokta için Microsoft Defender genel arama, boşluk yerine alt çizgi koymaya emin olun. Örneğin, en iyi arama sonuçları için "Windows 10" veya "windows_10" yerine "windows_11 Windows 10" veya "Windows 11" yazın.

## <a name="software-inventory-overview"></a>Yazılım envantere genel bakış

Yazılım **envanteri** sayfası, satıcı adı, bulunanlar, onlarla ilişkilendirilmiş tehdit, açık cihazlar, etkilenme puanına etki ve etiketler dahil olmak üzere ağ üzerinde yüklü yazılımların listesiyle açılır.

Varsayılan olarak, görünüm Ürün Kodu **(CPE) ile filtrelenmiştir: Kullanılabilir**. Ayrıca, liste görünümünü yazılımda bulunan zayıflıklara, onlarla ilişkilendirilmiş tehditlere ve yazılımın destek sonuna ulaşıp ulaşmamış olduğu gibi etiketlere göre filtreleebilirsiniz.

:::image type="content" source="images/tvm-software-inventory.png" alt-text="Yazılım envanteri giriş sayfası" lightbox="images/tvm-software-inventory.png":::

Araştırmak istediğiniz yazılımı seçin. Sayfada bilgilerin daha küçük bir görünümüne sahip bir açılır panel açılır. Araştırmanın daha derine inip Yazılım sayfasını aç'ı seçin veya Yanlış raporu bildir'i seçerek teknik **tutarsızlıkları bayrakla atabilirsiniz**.

### <a name="software-that-isnt-supported"></a>Desteklenen olmayan yazılım

Şu anda tehdit ve tehdit tarafından desteklenen & güvenlik açığı yönetimi yazılım stoku sayfasında yer alan yazılımlar olabilir. Desteklenem, yalnızca sınırlı veriler kullanılabilir. "Zayıf" bölümündeki "Kullanılamaz" seçeneğiyle desteklenmeyen yazılıma göre filtre uygulama.

:::image type="content" source="images/tvm-unsupported-software-filter.png" alt-text="Desteklenmeyen yazılım filtresi" lightbox="images/tvm-unsupported-software-filter.png":::

Aşağıda, yazılımın destekli olmadığını gösterir:

- Zayıflar alanı "Kullanılamaz" ifadesini gösteriyor
- Exposed devices field shows a dash
- Yan panele ve yazılım sayfasına eklenen bilgilendirme metni
- Yazılım sayfasında güvenlik önerileri, bulunan güvenlik açıkları veya olay zaman çizelgesi bölümleri bulun olmayacaktır

## <a name="software-inventory-on-devices"></a>Cihazlarda yazılım envanteri

Mobil Microsoft 365 Defender gezinti bölmesinde Cihaz envanterine **[gidin](machines-view-overview.md)**. Cihaz sayfasını açmak için cihazın adını seçin (Bilgisayar1 gibi), ardından yazılım envanteri sekmesini seçerek  cihazda var olan bilinen tüm yazılımların listesini görüntüleyin. Daha fazla bilgili açılır öğesini açmak için belirli bir yazılım girdisini seçin.

Yazılım, şu anda yazılım destekçisi tarafından desteklenemeyebilir ve cihaz Tehdit ve Güvenlik Açığı Yönetimi. Bununla birlikte, yalnızca sınırlı veriler kullanılabilir. Yazılımın desteklenmiyor olup olmadığını bilirsiniz, çünkü "Zayıf" sütununda "Kullanılamaz" ifadesini gösterir.

CPE olmayan yazılımlar cihaza özgü bu yazılım envanteri altında da gösterebilirsiniz.

### <a name="software-evidence"></a>Yazılım kanıtı

Kayıt defterinden, diskten veya her iki cihazdan belirli bir yazılım algılanın kanıtına bakın. Bu cihazı, cihaz yazılım envanteri'nin herhangi bir cihazında bulabilirsiniz.

Açılır sayfayı açmak için bir yazılım adı seçin ve "Yazılım Kanıtı" adlı bölümü seçin.

:::image type="content" source="images/tvm-software-evidence.png" alt-text="Windows 10 listesinden gelen liste" lightbox="images/tvm-software-evidence.png":::

## <a name="software-pages"></a>Yazılım sayfaları

Yazılım sayfalarını birkaç farklı şekilde görüntüleyebilirsiniz:

- Yazılım envanteri > Açılır sayfada bir > **adı seçin> Açılır sayfada Yazılımı aç'ı** seçin
- [Güvenlik önerileri sayfası >](tvm-security-recommendation.md) Açılır sayfada > **için bir** öneri seçin
- [Olay zaman çizelgesi](threat-and-vuln-mgt-event-timeline.md) > Etkinlik çizelgesi > Çıkışta "İlgili bileşen" adlı bölümde köprüye bağlı yazılım adını (Visual Studio 2017 gibi) seçin

 Belirli bir yazılımın tüm ayrıntılarını ve aşağıdaki bilgileri birlikte tam bir sayfa görüntülenir:

- Satıcı bilgilerini içeren yan panel, kuruluşta yazılımın yaygın kullanımı (yüklü olduğu cihaz sayısı ve yama sağ olmayan cihazlar dahil), kullanılabilir olup olmadığı ve açıkta açık bulunan cihazlar, açıkları açık olup olmadığı ve etkilenme puanına etkiler.
- Güvenlik açıklarının ve hatalı yapılandırmaların sayısını ve önem derecesini gösteren veri görselleştirmeleri. Ayrıca, maruz kalan cihazların sayısına sahip grafikler.
- Şu tür bilgileri gösteren sekmeler:
  - Zayıflıklar ve güvenlik açıkları için ilgili güvenlik önerileri tanımlanır.
  - Bulunan güvenlik açıklarının adlandırılmış CVE'leri.
  - Yazılımın yüklü olduğu cihazlar (cihaz adı, etki alanı, işletim sistemi ve daha fazlası ile birlikte).
  - Yazılım sürümü listesi (sürümün yüklü olduğu cihaz sayısı, bulunan güvenlik açıklarının sayısı ve yüklü cihazların adları dahil).

    :::image type="content" source="images/tvm-software-page-example.png" alt-text="Yazılım Visual Studio, zayıf olan, açıkta olan cihazlar ve daha fazlasının olduğu en iyi 2017." lightbox="images/tvm-software-page-example.png":::

## <a name="report-inaccuracy"></a>Rapor yanlışlığı

Hatalı güvenlik açığı bilgileri ve değerlendirme sonuçları gördüğünüzde hatalı rapor edin.

1. Yazılım envanteri sayfasında yazılım açılır sayfasını açın.
2. Hatalı **bildir'i seçin**.
3. Uçarak çıkış bölmesinden rapor etmek istediğiniz sorunu seçin:

    - bir yazılım ayrıntısı yanlış
    - yazılım, kuruluşumda herhangi bir cihaza yüklü değil
    - Yüklü veya açık cihaz sayısı yanlış

4. Yanlışlık hakkında istenen ayrıntıları doldurun. Bu, bildiriyor olduğunuz soruna bağlı olarak değişir.

![Rapor yanlışlığı](images/report-inaccuracy-software.png)

5. **Gönder'i seçin**. Geri bildiriminiz tüm uzmanlara Tehdit ve Güvenlik Açığı Yönetimi gönderilir.

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Etkinlik zaman çizelgesi](threat-and-vuln-mgt-event-timeline.md)
- [Cihazlar listesini görüntüleme Uç Nokta için Microsoft Defender düzenleme](machines-view-overview.md)
