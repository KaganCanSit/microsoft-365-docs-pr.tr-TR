---
title: Güvenlik önerileri için Tehdit ve Güvenlik Açığı Yönetimi
description: Aynı güvenlik önerisinde tehdit, ihlal olasılığı ve değere göre öncelik sırasına göre işlem Tehdit ve Güvenlik Açığı Yönetimi.
keywords: Tehdit ve Güvenlik Açığı Yönetimi için Microsoft Defender TVM güvenlik önerisi, siber güvenlik önerisi, işlemli güvenlik önerisi
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
ms.openlocfilehash: 57c1909ff54fea6b9151e212f465abb75bab48f8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325327"
---
# <a name="security-recommendations---threat-and-vulnerability-management"></a>Güvenlik önerileri - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Organizasyonda tanımlanan siber güvenlik zayıf noktaları eyleme değiştirilebilir güvenlik önerilerine eşlenmiş ve etkilerinden önceliklidir. Önceliklendirmeli öneriler, güvenlik açıklarını azaltmak veya düzeltmek ve uyumluluğu düzeltmek için süreyi kısaltmaya yardımcı olur.

Her güvenlik önerisi, işlemle ilgili düzeltme adımlarını içerir. Görev yönetimine yardımcı olması için öneri, Görev Yönetimi ve Yönetim Microsoft Intune Microsoft Endpoint Configuration Manager. Tehdit ortamınız değişirse öneri aynı zamanda ortamınıza sürekli bilgi toplayan bir öneri de değişir.

> [!TIP]
> Yeni güvenlik açığı olayları hakkında e-postalar almak için bkz. Uç Nokta için [Microsoft Defender'da güvenlik açığı e-posta bildirimlerini yapılandırma](configure-vulnerability-email-notifications.md)

## <a name="how-it-works"></a>Nasıl çalışır?

Kuruluşta her cihaz, müşterilerin doğru zamanda doğru şeylere odaklanmalarına yardımcı olacak üç önemli faktöre göre puanlandı.

- **Tehdit**: Kuruluş cihazlarında güvenlik açıkları ve açıkları açıkları ve ihlal geçmişinin özellikleri. Bu etmenlere bağlı olarak, güvenlik önerileri etkin uyarılara, sürekli tehdit kampanyaları ve bunlara karşılık gelen tehdit analitik raporlarına karşılık gelen bağlantıları gösterir.
- **İhlal** olasılığı: Kuruluş güvenliği, tehditlere karşı koruma eğilimidir.
- **İş değeri**: Kuruluş varlıklarını, kritik süreçleri ve fikri mülkiyetini verir.

## <a name="navigate-to-the-security-recommendations-page"></a>Güvenlik önerileri sayfasına gidin

Güvenlik önerileri sayfasına birkaç farklı şekilde erişin:

- güvenlik açığı yönetimi Microsoft 365 Defender portalında tehdit ve [gezinti Microsoft 365 Defender menüsü](portal-overview.md)
- Tehdit ve Güvenlik Açığı Yönetimi [panosunda en Tehdit ve Güvenlik Açığı Yönetimi önerileri](tvm-dashboard-insights.md)

aşağıdaki yerlerde ilgili güvenlik önerilerini görüntüleme:

- Yazılım sayfası
- Cihaz sayfası

### <a name="navigation-menu"></a>Gezinti menüsü

Güvenlik Açığı yönetimi **gezinti menüsüne gidin** ve Güvenlik Açığı Yönetimi gezinti **Öneriler**. Bu sayfada, kurumda bulunan tehditlere ve güvenlik açıklarına yönelik güvenlik önerilerinin listesi yer almaktadır.

### <a name="top-security-recommendations-in-the-threat-and-vulnerability-management-dashboard"></a>Tehdit ve Güvenlik Açığı Yönetimi panosunda en Tehdit ve Güvenlik Açığı Yönetimi önerileri

Herhangi bir günde Güvenlik Yöneticisi olarak, [Tehdit ve Güvenlik Açığı Yönetimi](tvm-dashboard-insights.md) panosuna bakarak Cihazlar için [Microsoft Güvenli](tvm-microsoft-secure-score-devices.md) Puanı ile açık kalma puanınızı yan yana [](tvm-exposure-score.md) görebilirsiniz. Bunun amacı, kuruluş **güvenlik** açıklarından daha az açık kalma sürelerini düşürmek  ve kuruluş cihazınızın cihaz güvenliğini siber güvenlik tehdit saldırılarına karşı daha iyi karşı daha iyi durumda olacak şekilde artırmaktır. En önemli güvenlik önerileri listesi bu hedefe ulaşmanıza yardımcı olabilir.

![Dört güvenlik önerisi olan En iyi güvenlik önerileri kartı örneği.](images/top-security-recommendations350.png)

En iyi güvenlik önerileri, önceki bölümde adı geçen önemli faktörlere dayalı olarak geliştirme fırsatlarının önceliklerini listelemektedir: tehdit, ihlal olasılığı ve değer. Öneri seçmek, sizi daha fazla ayrıntıya sahip güvenlik önerileri sayfasına götürebilirsiniz.

## <a name="security-recommendations-overview"></a>Güvenlik önerilerine genel bakış

Önerileri, bulunan zayıf noktaların sayısını, ilgili bileşenleri, tehdit öngörülerini, açık cihaz sayısını, durumu, düzeltme türünü, düzeltme etkinliklerini, etkilenme puanınızı ve Cihazlar için Microsoft Güvenli Puanı'nızı ve ilişkili etiketleri görebilirsiniz.

Eğilim **değiştiklerine göre,** Maruz cihazlar grafiğinin rengi değişir. ışıklı cihazların sayısı yükselmeye devam ediyorsa renk kırmızıya dönüşer. Açığa çıkarıla cihazların sayısında bir azalma olursa, grafiğin rengi yeşile dönüşecek.

> [!NOTE]
> Tehdit ve güvenlik açığı yönetimi, 30 gün önce kullanılabilir **olan cihazları** gösterir. Bu, cihaz 7 gündür 'Etkin Değil' durumunda olduğu Uç Nokta için Microsoft Defender'ın geri kalanından farklıdır.

![Güvenlik önerileri için giriş sayfası örneği.](images/tvmsecrec-updated.png)

### <a name="icons"></a>Simgeler

Yararlı simgeler şu an için hemen dikkat çekmenizi de sağlar:

- ![okunu kullanarak bir hedefe dokunun.](images/tvm_alert_icon.png) olası etkin uyarılar
- ![kırmızı hata.](images/tvm_bug_icon.png) ilişkili kamu açıkları
- ![ampul.](images/tvm_insight_icon.png) öneri içgörüleri

### <a name="explore-security-recommendation-options"></a>Güvenlik önerisi seçeneklerini keşfetme

Araştırmak veya işleme almak istediğiniz güvenlik önerilerini seçin.

:::image type="content" alt-text="Güvenlik önerisi uç sayfası örneği." source="images/secrec-flyouteolsw.png" lightbox="images/secrec-flyouteolsw.png":::

Uçarak çıkıştan, aşağıdaki seçeneklerden herhangi birini seçebilirsiniz:

- **Yazılım sayfasını aç** - Yazılım ve nasıl dağıtıldı hakkında daha fazla bağlam elde etmek için yazılım sayfasını açın. Bu bilgiler tehdit bağlamı, ilişkili öneriler, bulunan güvenlik açıkları, açık cihazların sayısı, güvenlik açıkları, yazılım yüklü aygıtlarla ilgili adlar ve ayrıntılı bilgiler ve sürüm dağıtımını içerebilir.

- [**Düzeltme seçenekleri**](tvm-remediation.md) - Bir bilet açmak için bir düzeltme isteği gönderin Microsoft Intune yöneticinizin teslim alıp göndermesi için. Düzeltme sayfasındaki düzeltme etkinliğini takip edin.

- [**Özel durum**](tvm-exception.md) seçenekleri - Bir özel durum gönderin, gerekçe belirleyin ve henüz bu sorunu düzeltmek için bir özel durum süresi ayarlayın.

> [!NOTE]
> Windows, Linux veya macOS cihazlarında yazılım değişikliği yapılırken verilerin güvenlik portalına yansıt olması normalde 2-4 saat sürer. iOS ve Android cihazlardaki değişikliklerin yansıt olması 8 saat kadar sürebilir. Daha uzun sürerken bazı durumlar olabilir.
> 
> Yapılandırma değişiklikleri 4 ile 24 saat arasında sürebilir.

### <a name="investigate-changes-in-device-exposure-or-impact"></a>Cihaz etkilenme veya etkiyi araştırma

Açığa çıkarulan cihazların sayısında büyük bir atlama ya da kuruluşun etkilenme puanı ve Cihazlar için Microsoft Güvenli Puanı üzerindeki etkisi net bir artış varsa, bu güvenlik önerisinin incelemeye değecek bir önerisi vardır.

1. Öneriyi ve Yazılımı **aç sayfasını seçin**
2. Yeni güvenlik **açıkları** veya yeni genel açık açıkları gibi söz konusu yazılımla ilgili tüm etkili olayları görüntülemek için Olay zaman çizelgesi sekmesini seçin. [Etkinlik zaman çizelgesi hakkında daha fazla bilgi](threat-and-vuln-mgt-event-timeline.md)
3. Düzeltme isteği gönderme gibi artışa veya organizasyonun açık kalma sayısına nasıl karar verebilirsiniz

## <a name="request-remediation"></a>Düzeltme isteği

Düzeltme Tehdit ve Güvenlik Açığı Yönetimi özelliği, düzeltme isteği iş akışı aracılığıyla Güvenlik ve IT yöneticileri arasındaki boşluğu köprüler. Sizin gibi güvenlik yöneticileri, Güvenlik önerisi sayfasından Intune'a kadar olan bir güvenlik açığını **düzeltmek için IT** Yöneticisinden talepte bulunabilirsiniz. [Düzeltme seçenekleri hakkında daha fazla bilgi](tvm-remediation.md)

### <a name="how-to-request-remediation"></a>Düzeltme isteği nasıl olur?

Düzeltme isteğide kullanmak istediğiniz güvenlik önerilerini seçin ve sonra da Düzeltme **seçenekleri'ne tıklayın**. Formu doldurun ve İsteği **gönder'i seçin**. Düzeltme [**isteğinizin durumunu**](tvm-remediation.md) görüntülemek için Düzeltme sayfasına gidin. [Düzeltme isteğide bulundurma hakkında daha fazla bilgi](tvm-remediation.md#request-remediation)

## <a name="file-for-exception"></a>Özel durum için dosya

Bir öneri şu anda uygun olmadığınız bir düzeltme isteğine alternatif olarak, öneriler için özel durumlar oluşturabilirsiniz. [Özel durumlar hakkında daha fazla bilgi](tvm-exception.md)

Yalnızca "özel durumlar işleme" izinleri olan kullanıcılar özel durum ekleyebilir. [RBAC rolleri hakkında daha fazla bilgi edinmek için](user-roles.md):

Öneri için bir özel durum oluşturulduğunda, öneri artık etkin değildir. Öneri durumu Tam özel durum veya **Kısmi özel** **durum (cihaz** grubuna göre) olarak değişir.

### <a name="how-to-create-an-exception"></a>Özel durum oluşturma

Özel durum oluşturmak istediğiniz bir güvenlik önerisi belirleyin ve sonra Özel Durum **seçenekleri'ne tıklayın**.

!["Özel durum seçenekleri" düğmesinin bir güvenlik önerisi uç kutusunda konum olduğunu gösterme.](images/tvm-exception-options.png)

Formu doldurun ve gönderin. Tüm özel durumlarınızı (mevcut ve geçmiş) görüntülemek için **Tehdit &** Güvenlik [](tvm-remediation.md) Açığı Yönetimi menüsünün altındaki Düzeltme sayfasına gidin ve Özel Durumlar sekmesini [seçin. Özel](tvm-exception.md#create-an-exception) durum oluşturma  hakkında daha fazla bilgi

## <a name="report-inaccuracy"></a>Rapor yanlışlığı

Belirsiz, yanlış, eksik veya zaten düzeltilen güvenlik önerisi bilgilerini gördüğünüzde hatalı pozitif bir sonuç bildirebilirsiniz.

1. Güvenlik önerilerini açın.

2. Rapor etmek istediğiniz güvenlik önerisinin yanındaki üç noktayı seçin ve ardından Hatalı **bildir'i seçin**.

    ![Güvenlik önerisinde "Yanlış bildir" düğmesinin yerini gösterme.](images/report-inaccuracy500.png)

3. Açılır bölmeden açılan menüden yanlış kategoriyi seçin, e-posta adresinizi ve yanlışla ilgili ayrıntıları doldurun.

4. **Gönder'i seçin**. Geri bildiriminiz tüm uzmanlara Tehdit ve Güvenlik Açığı Yönetimi gönderilir.

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Pozlama puanı](tvm-exposure-score.md)
- [Cihazlar için Microsoft Güvenli Puan](tvm-microsoft-secure-score-devices.md)
- [Güvenlik açıklarını düzeltme](tvm-remediation.md)
- [Güvenlik önerileri için özel durumlar oluşturma ve görüntüleme](tvm-exception.md)
- [Etkinlik zaman çizelgesi](threat-and-vuln-mgt-event-timeline.md)
