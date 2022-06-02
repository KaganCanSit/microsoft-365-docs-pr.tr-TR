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
ms.openlocfilehash: bc7bba0d91e9b2ff1f9baddc52f717450660d070
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838923"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Saldırı simülasyonu eğitimi için yük otomasyonları

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de saldırı simülasyonu eğitimi bölümünde, yük otomasyonları (_yük toplama_ olarak da bilinir) kuruluşunuzdaki kullanıcılar tarafından bildirilen gerçek dünya kimlik avı saldırı iletilerinden bilgi toplar. Kuruluşunuzda bu iletilerin sayısı büyük olasılıkla düşük olsa da, kimlik avı saldırılarında aranacak koşulları belirtebilirsiniz (örneğin, alıcılar, sosyal mühendislik tekniği, gönderen bilgileri vb.). Saldırı simülasyonu eğitimi, hedeflenen kullanıcılara zararsız simülasyonları otomatik olarak başlatmak için saldırıda kullanılan iletileri ve yükleri taklit eder.

Kullanılabilir yük otomasyonlarını görmek için adresinden Microsoft 365 Defender portalını <https://security.microsoft.com>açın **, e-posta & işbirliği** \> **Saldırı benzetimi eğitim** \> **Otomasyonları** sekmesine \> gidin ve **yük otomasyonları'nı** seçin. Doğrudan **Yük otomasyonlarını** seçebileceğiniz **Otomasyonlar** sekmesine gitmek için kullanın <https://security.microsoft.com/attacksimulator?viewid=automations>.

Her yük otomasyonu için aşağıdaki bilgiler gösterilir:

- **Otomasyon adı**
- **Tür**: Değer **Payload** değeridir.
- **Toplanan öğeler**
- **Son değiştirme**
- **Durum**: Değer **Hazır** veya **Taslak'tır**.

Listeden bir yük otomasyonu seçtiğinizde, aşağıdaki bilgileri içeren bir ayrıntılar açılır öğesi görüntülenir:

- **Genel** sekmesi: Simülasyon otomasyonu hakkında temel bilgileri görüntüler.
- **Çalıştırma geçmişi** sekmesi: Bu sekme yalnızca **Durum** değeri **Hazır** olan yük otomasyonları için kullanılabilir.

## <a name="create-payload-automations"></a>Yük otomasyonları oluşturma

Yük otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com/>**, E-posta & işbirliği** \> **Saldırı benzetimi eğitimi** \> **Otomasyonları** sekmesi **Yük otomasyonları'na**\> gidin. Doğrudan **Yük otomasyonlarını** seçebileceğiniz **Otomasyonlar** sekmesine gitmek için kullanın <https://security.microsoft.com/attacksimulator?viewid=automations>.

   Otomasyon oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Otomasyon oluşturma**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Yük otomasyonları sekmesindeki Simülasyon oluştur düğmesi" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

   > [!NOTE]
   > Oluşturma sihirbazı sırasında herhangi bir noktada Kaydet **ve kapat'a** tıklayarak ilerlemenizi kaydedebilir ve yük otomasyonunu daha sonra yapılandırmaya devam edebilirsiniz. **Yük otomasyonlarında** yük otomasyonunu seçip Otomasyonu düzenle simgesine tıklayarak ![kaldığınız yerden devam edebilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Otomasyonu düzenleyin**. Kısmen tamamlanan yük otomasyonu **, Taslak** **Durum** değerine sahip olacaktır.

2. **Otomasyon adı** sayfasında aşağıdaki ayarları yapılandırın:

   - **Ad**: Yük otomasyonu için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: Yük otomasyonu için isteğe bağlı ayrıntılı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

3. **Çalıştırma koşulları** sayfasında, otomasyonun ne zaman çalıştırılacağını belirleyen gerçek kimlik avı saldırısının koşullarını seçin.

   Koşul ekle simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Koşul ekleyin** ve aşağıdaki koşullardan birini seçin:

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

   Her koşulu yalnızca bir kez kullanabilirsiniz. Birden çok koşul AND mantığını (\<Condition1\> ve \<Condition2\>) kullanır.

   Başka bir koşul eklemek için Koşul ekle simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Koşul ekleyin**.

   Bir koşulu ekledikten sonra kaldırmak için ![Kaldır simgesi.](../../media/m365-cc-sc-delete-icon.png).

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Otomasyonu gözden geçir** sayfasında yük otomasyonunuzun ayrıntılarını gözden geçirebilirsiniz.

   Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

5. **Yeni otomasyon oluşturuldu** sayfasında bağlantıları kullanarak otomasyonu açabilir veya **Simülasyonlar** sayfasına gidebilirsiniz.

   İşiniz bittiğinde **Bitti'ye** tıklayın.

**Otomasyonlar'daki Payload otomasyonlarına** döndüğünüzde, oluşturduğunuz oturum açma sayfası artık listeleniyor.

## <a name="turn-payload-automations-on-or-off"></a>Yük otomasyonlarını açma veya kapatma

Yük otomasyonlarını yalnızca **Durum** değerinin **Hazır** olduğu durumlarda açabilir veya kapatabilirsiniz. **Durum** değerinin **Taslak** olduğu eksik yük otomasyonlarını açamaz veya kapatamazsınız.

Yük otomasyonunu açmak için, onay kutusuna tıklayarak bu otomasyonu listeden seçin. ![Aç simgesine tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) Görüntülenen simgeyi **açın** ve iletişim kutusunda **Onayla'ya** tıklayın.

Yük otomasyonunu kapatmak için, onay kutusuna tıklayarak bu yükü listeden seçin. Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) Görüntülenen simgeyi **açın** ve iletişim kutusunda **Onayla'ya** tıklayın.

## <a name="modify-payload-automations"></a>Yük otomasyonlarını değiştirme

**Payload otomasyonlarında** mevcut bir yük otomasyonunu değiştirmek için aşağıdaki adımlardan birini yapın:

- Onay kutusuna tıklayarak listeden yük otomasyonunu seçin. ![Otomasyonu düzenle simgesine tıklayın.](../../media/m365-cc-sc-edit-icon.png) Görüntülenen **otomasyon simgesini düzenleyin**.
- Onay kutusu dışında satırda herhangi bir yere tıklayarak listeden yük otomasyonunu seçin. Açılan ayrıntılar açılır penceresinde, **Genel** sekmesinde **, Ad**, **Açıklama** veya **Çalıştırma koşulları** bölümlerinde **Düzenle'ye** tıklayın.

Yük otomasyonu sihirbazı, seçilen yük otomasyonunun ayarları ve değerleriyle birlikte açılır. Adımlar [, Yük otomasyonları oluşturma bölümünde açıklanan adımlarla](#create-payload-automations) aynıdır.

## <a name="remove-payload-automations"></a>Yük otomasyonlarını kaldırma

Yük otomasyonunu kaldırmak için, onay kutusuna tıklayarak listeden yük otomasyonunu seçin. Sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) Görüntülenen **sil** simgesine tıklayın ve ardından iletişim kutusunda **Onayla'ya** tıklayın.

## <a name="related-links"></a>İlgili bağlantılar

[Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md)

[Saldırı simülasyonu eğitimi için simülasyon otomasyonları](attack-simulation-training-simulation-automations.md)

[Saldırı simülasyonu eğitimiyle içgörüler elde etme](attack-simulation-training-insights.md)
