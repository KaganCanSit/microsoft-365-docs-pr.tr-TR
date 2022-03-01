---
title: Kullanıcıların bulut koruma düzeyini Microsoft Defender Virüsten Koruma
description: Bulut koruma düzeyinizi bulut koruması Microsoft Defender Virüsten Koruma.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, saldırganlık, koruma düzeyi
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 4723b84e285e508e33ca4b54a1897bbed036a897
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996506"
---
# <a name="specify-the-cloud-protection-level"></a>Bulut koruma düzeyini belirtme

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Bulut koruması, geleneksel güvenlik Microsoft Defender Virüsten Koruma güncelleştirmelerinden çok daha hızlı bir şekilde uç noktalarınıza koruma sağlamak için Bulut Koruması ile birlikte çalışır. Bulut koruma düzeyinizi, Önerilen) veya Grup Microsoft Endpoint Manager kullanarak yapılandırabilirsiniz.

> [!NOTE]
> Yüksek, **Yüksek** **+veya Sıfır** olan ile düşük olan **seçim bazı yasal** dosyaların algılandırılamana neden olabilir. Böyle bir durumda, algılanan dosyanın engellemesini kaldırabilirsiniz veya algılama ile ilgili ihtilaf portalında Microsoft 365 Defender.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Bulut Microsoft Endpoint Manager düzeyini belirtmek için E-depolamayı kullanma

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma.

2. Uç nokta **güvenliği Virüsten Koruma'ya** \> **seçin**.

3. Virüsten koruma profili seçin. (Henüz profiliniz yoksa veya yeni bir profil oluşturmak için, aşağıdaki Bağlantı sayfasında cihaz kısıtlama [ayarlarını yapılandırma Microsoft Intune](/intune/device-restrictions-configure).

4. **Özellikler'i seçin**. Ardından, Yapılandırma **ayarları'nın yanında** Düzenle'yi **seçin**.

5. Bulut **koruması'nın** kapsamını genişletin ve **Bulut teslimi koruma düzeyi** listesinde, aşağıdaki seçeneklerden birini seçin:

    - **Yapılandırılmadı**: Varsayılan durum.
    - **Yüksek**: Güçlü bir algılama düzeyi uygular.
    - **Yüksek artı**: Yüksek **düzeyi kullanır** ve ek koruma önlemleri uygular (istemci performansını etkileyebilir).
    - **Sıfır dayanıklılık**: Tüm bilinmeyen yürütülebilir dosyaları engeller.

6. Gözden **Geçir + kaydet'i** ve sonra Kaydet'i **seçin**.

> [!TIP]
> Yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:
>
> - [E-Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Intune'da uç nokta koruma ayarları ekleme](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Bulut koruma düzeyini belirtmek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar Yapılandırması **Yönetim** **şablonları'ne**\> gidin.

4. **MpEngine'in** **Bileşenleri Windows ağacını** \> **Microsoft Defender Virüsten Koruma** \> genişletin.

5. Bulut koruma düzeyi **seç ayarına çift tıklayın** ve bunu Etkin olarak **ayarlayın**. Koruma düzeyini seçin:

    - **Yapılandırılmadı**: Varsayılan durum.
    - **Varsayılan engelleme düzeyi** , yasal dosyaları algılama riskini artırmadan güçlü algılama sağlar.
    - **Orta engelleme düzeyi** yalnızca yüksek güven algılamaları için ortalama sağlar
    - **Yüksek engelleme düzeyi** , istemci performansını en iyi duruma getirerek güçlü bir algılama düzeyi uygular (ancak size hatalı pozitif sonuçlar için daha fazla fırsat da verir).
    - **Yüksek + engelleme düzeyi** ek koruma önlemleri uygular (istemci performansını etkileyebilir ve hatalı pozitif sonuçlar yapma ihtimalinizi artırır).
    - **Sıfır olan istenmeyen posta engelleme düzeyi bilinmeyen** tüm yürütülebilir dosyaları engeller.

6. **Tamam**'ı seçin.

7. Güncelleştirilmiş Grup İlkesi Nesnenizi dağıtın. Bkz [. Grup İlkesi Yönetim Konsolu](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Şirket içinde Grup İlkesi Nesneleri mi kullanıyorsunuz? Buluttaki çevirinin nasıl olduğunu öğrenin. [Grup İlkesi çözümlemesini kullanarak şirket içi grup ilkesi nesnelerinizi Çözümleme - Microsoft Endpoint Manager.](/mem/intune/configuration/group-policy-analytics)
  
## <a name="see-also"></a>Ayrıca bkz.

[Bulut korumasının etkin olması için neden Microsoft Defender Virüsten Koruma](why-cloud-protection-should-be-on-mdav.md)
