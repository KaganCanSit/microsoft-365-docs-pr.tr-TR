---
title: Saldırı benzetimi eğitimi için Yük otomasyonları
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
description: Yöneticiler, Plan 2'de Saldırı benzetimi eğitimi için otomatik benzetimleri toplamak ve başlatmak için yük otomasyonlarını (yük toplama) Office 365 için Microsoft Defender öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: aa223ab1abda110e32a9b9dc55e9dc76a1983321
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468445"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Saldırı benzetimi eğitimi için Yük otomasyonları

**Plan** [2 Office 365 için Microsoft Defender için geçerlidir](defender-for-office-365.md)

Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de Saldırı benzetim eğitimi'de, yük otomasyonları (yük toplama olarak da _bilinir) kuruluş_ kullanıcılar tarafından bildirilen gerçek dünyaya yönelik kimlik avı iletilerinden bilgi toplar. Bu iletilerin sayısı büyük olasılıkla organizasyonda az olsa da, kimlik avı saldırılarında (örneğin, alıcılar, sosyal mühendislik tekniği, gönderen bilgileri, vb.) bakacak koşulları belirtebilirsiniz. Saldırı benzetimi eğitimi ardından, saldırıda kullanılan mesaj ve yükü hedefli kullanıcılara zararsız benzetimler yapmak için otomatik olarak taklit eder.

Yük otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com/>ve işbirliği **&** \> **Saldırı benzetimi eğitimi** \> **Payload otomasyonları sekmesine** gidin.

   Doğrudan **Payload otomasyonları sekmesine gitmek** için kullanın <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. Yük **otomasyonları sekmesinde Otomasyon** simgesi oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Otomasyon oluşturun**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Yazılım portalının Saldırı benzetimi eğitimi'nin Payload otomasyon sekmesindeki Benzetim Microsoft 365 Defender düğmesi" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Oluşturma sihirbazı açılır. Bu makalenin kalan kalanında, sayfaları ve bunların içerdiği ayarlar açıklanmıştır.

> [!NOTE]
> Oluşturma sihirbazı sırasında herhangi bir noktada, ilerlemenizi kaydetmek ve  yük otomasyonunu daha sonra yapılandırmaya devam etmek için Kaydet ve kapat'a tıklayabilir. Yük otomasyonları sekmesinden yük otomasyonunu seçerek ve sonra da Otomasyon simgesini düzenle'ye tıklayarak, kalan yerden  ![devamabilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Otomasyonu düzenleyin**.

## <a name="automation-name"></a>Otomasyon adı

Otomasyon **adı sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:

- **Ad**: Yük otomasyonu için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Yük otomasyonu için isteğe bağlı olarak ayrıntılı bir açıklama girin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="run-conditions"></a>Çalıştırma koşulları

Çalıştırma **koşulları sayfasında** , otomasyonun ne zaman çalıştırıı belirleyen gerçek kimlik avı saldırısının koşullarını seçin.

Her koşulu yalnızca bir kez kullanabilirsiniz. Birden çok koşullar, AND mantığı ( ve )\<Condition1\> kullanır \<Condition2\>.

![Koşul ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Koşul ekle'yi** seçin.

- **Hayır. kampanyada hedeflenen kullanıcıların sayısı**: Aşağıdaki ayarları yapılandırma:
  - **Eşittir**, **Küçükten küçük**, **Büyük**, Küçük **veya eşit** veya Büyük **ya da büyük ya da eşit**.
  - **Değer girin**: Kimlik avı kampanyası tarafından hedeflenen kullanıcı sayısı.
- **Belirli bir kimlik avı tekniğine sahip** kampanyalar: Kullanılabilir değerlerden birini seçin:
  - **Kimlik bilgileri toplama**
  - **Kötü amaçlı yazılım eki**
  - **Ekin içinde bağlantı**
  - **Kötü amaçlı yazılım bağlantısı**
  - **Sürücüye göre URL**
- **Belirli bir gönderen etki** alanı: Gönderenin e-posta etki alanı değerini girin (örneğin, Contoso.com).
- **Belirli bir gönderen adı**: Gönderen adı değerini girin.
- **Belirli bir gönderen e-posta** adresi: Gönderenin e-posta adresini girin.
- **Belirli kullanıcı ve grup alıcıları**: Kullanıcının veya grubun adını veya e-posta adresini yazmaya başlayın. Görüntülendiğinde seçin.

Bir koşulu ekledikten sonra kaldırmak için ![Kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png).

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="review-automation"></a>Otomasyonu gözden geçirme

Otomasyonu **gözden geçir** sayfasında, yük otomasyonu ile ilgili ayrıntıları gözden geçirebilirsiniz.

Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

Bitirdikten sonra Gönder'e **tıklayın**.
