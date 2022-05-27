---
title: Saldırı simülasyonu eğitimi için yük otomasyonları
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'de Saldırı simülasyonu eğitimi için otomatik simülasyonları toplamak ve başlatmak için yük otomasyonlarını (yük toplama) kullanmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 862547884f9a7697382affda734af0f323c86c4a
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739571"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Saldırı simülasyonu eğitimi için yük otomasyonları

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de saldırı simülasyonu eğitimi bölümünde, yük otomasyonları (_yük toplama_ olarak da bilinir) kuruluşunuzdaki kullanıcılar tarafından bildirilen gerçek dünya kimlik avı iletilerinden bilgi toplar. Kuruluşunuzda bu iletilerin sayısı büyük olasılıkla düşük olsa da, kimlik avı saldırılarında aranacak koşulları belirtebilirsiniz (örneğin, alıcılar, sosyal mühendislik tekniği, gönderen bilgileri vb.). Saldırı simülasyonu eğitimi, hedeflenen kullanıcılara zararsız simülasyonları otomatik olarak başlatmak için saldırıda kullanılan iletileri ve yükleri taklit eder.

Yük otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com/>**, E-posta & işbirliği** \> **Saldırı benzetimi eğitimi** \> **Otomasyonları** sekmesi **Yük otomasyonları'na**\> gidin.

   Doğrudan **Yük otomasyonlarını** seçebileceğiniz **Otomasyonlar** sekmesine gitmek için kullanın <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. **Yük otomasyonları** bölümünde Otomasyon oluştur simgesi'ne tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Otomasyon oluşturma**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Yük otomasyonları sekmesindeki Simülasyon oluştur düğmesi" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Oluşturma sihirbazı açılır. Bu makalenin geri kalanında sayfalar ve içerdikleri ayarlar açıklanmaktadır.

> [!NOTE]
> Oluşturma sihirbazı sırasında herhangi bir noktada Kaydet **ve kapat'a** tıklayarak ilerlemenizi kaydedebilir ve yük otomasyonunu daha sonra yapılandırmaya devam edebilirsiniz. **Yük otomasyonlarında** yük otomasyonunu seçip Otomasyonu düzenle simgesine tıklayarak ![kaldığınız yerden devam edebilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Otomasyonu düzenleyin**.

## <a name="automation-name"></a>Otomasyon adı

**Otomasyon adı** sayfasında aşağıdaki ayarları yapılandırın:

- **Ad**: Yük otomasyonu için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Yük otomasyonu için isteğe bağlı ayrıntılı bir açıklama girin.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="run-conditions"></a>Çalıştırma koşulları

**Çalıştırma koşulları** sayfasında, otomasyonun ne zaman çalıştırılacağını belirleyen gerçek kimlik avı saldırısının koşullarını seçin.

Her koşulu yalnızca bir kez kullanabilirsiniz. Birden çok koşul AND mantığını (\<Condition1\> ve \<Condition2\>) kullanır.

![Koşul ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Koşul ekleyin**.

- **No. kampanyada hedeflenen kullanıcıların** sayısı: Aşağıdaki ayarları yapılandırın:
  - **Eşittir**, **Küçüktür**, **Büyüktür**, **Küçüktür veya eşittir** veya **Büyüktür veya eşittir**.
  - **Değer girin**: Kimlik avı kampanyası tarafından hedeflenen kullanıcı sayısı.
- **Belirli bir kimlik avı tekniğine sahip kampanyalar**: Kullanılabilir değerlerden birini seçin:
  - **Kimlik bilgisi toplama**
  - **Kötü amaçlı yazılım eki**
  - **Ekteki bağlantı**
  - **Kötü amaçlı yazılım bağlantısı**
  - **Sürücüye göre URL**
- **Belirli gönderen etki alanı**: Bir gönderen e-posta etki alanı değeri girin (örneğin, contoso.com).
- **Belirli bir gönderen adı**: Bir gönderen adı değeri girin.
- **Belirli bir gönderen e-postası**: Gönderen e-posta adresini girin.
- **Belirli kullanıcı ve grup alıcıları**: Kullanıcının veya grubun adını veya e-posta adresini yazmaya başlayın. Göründüğünde seçin.

Bir koşulu ekledikten sonra kaldırmak için ![Kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png).

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="review-automation"></a>Otomasyonu gözden geçirme

**Otomasyonu gözden geçir** sayfasında yük otomasyonunuzun ayrıntılarını gözden geçirebilirsiniz.

Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

İşiniz bittiğinde **Gönder'e** tıklayın.
