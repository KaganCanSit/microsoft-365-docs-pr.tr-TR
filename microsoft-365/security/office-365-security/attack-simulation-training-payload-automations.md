---
title: Saldırı benzetimi eğitimi için Yük otomasyonları
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler, Office 365 Plan 2 için Microsoft Defender'daki Saldırı benzetimi eğitimi için otomatik benzetimleri toplamak ve başlatmak için yük otomasyonlarını (yük toplama) kullanmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 0e090b79c8e04de5f0e9e81449d805d2b124bc59
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989994"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Saldırı benzetimi eğitimi için Yük otomasyonları

 [Office 365 için Microsoft Defender plan 2 için geçerlidir](defender-for-office-365.md)

Microsoft 365 E5 için Microsoft Defender veya Office 365 Plan 2'de Saldırı benzetimi eğitimi'nden, yük otomasyonları (yük toplama olarak da _bilinir) kuruluş_ kullanıcılar tarafından bildirilen gerçek dünyaya yönelik kimlik avı iletilerinden bilgi toplar. Bu iletilerin sayısı büyük olasılıkla organizasyonda az olsa da, kimlik avı saldırılarında (örneğin, alıcılar, sosyal mühendislik tekniği, gönderen bilgileri, vb.) bakacak koşulları belirtebilirsiniz. Saldırı benzetimi eğitimi ardından, saldırıda kullanılan mesaj ve yükü hedefli kullanıcılara zararsız benzetimler yapmak için otomatik olarak taklit eder.

Yük otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com/>ve işbirliği **&** \> **Saldırı benzetimi eğitimi** \> **Payload otomasyonları sekmesine** gidin.

   Doğrudan **Payload otomasyonları sekmesine gitmek** için kullanın <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. Payload **otomasyonları sekmesinde Benzetim** simgesi oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Benzetim oluşturun**.

   ![Yazılım portalının Saldırı benzetimi eğitimi'nin Payload otomasyonları sekmesinde benzetim Microsoft 365 Defender.](../../media/attack-sim-training-sim-automations-create.png)

3. Oluşturma sihirbazı açılır. Bu makalenin kalan kalanında, sayfaları ve bunların içerdiği ayarlar açıklanmıştır.

> [!NOTE]
> Benzetim oluşturma sihirbazının herhangi bir noktasında, ilerlemenizi kaydetmek  ve benzetimi daha sonra yapılandırmaya devam etmek için Kaydet ve kapat'a tıklarsınız. Tamamlanmamış benzetimlerin **Benzetimler** **sekmesinde** Durum değeri **Taslağı** vardır. Benzetimi seçerek ve benzetim simgesini düzenle'ye tıklayarak, kalan yerden ![devamabilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Benzetimi** düzenleyin.## Benzetimi adla ve açıkların.

## <a name="automation-name"></a>Otomasyon adı

Otomasyon **adı sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:

- **Ad**: Benzetim için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Benzetim için isteğe bağlı olarak ayrıntılı bir açıklama girin.

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
