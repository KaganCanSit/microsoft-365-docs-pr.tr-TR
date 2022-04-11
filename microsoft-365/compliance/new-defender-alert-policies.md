---
title: Office 365 için Microsoft Defender'da yeni uyarı ilkeleri
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkDEFENDER
ROBOTS: noindex,nofollow
description: Office 365 için Microsoft Defender için yeni uyarı ilkeleri yayınlıyoruz. Ayrıca, yeni ilkelerle değiştirilen iki mevcut uyarı ilkesi de kullanımdan kaldırılmıştır.
ms.openlocfilehash: afdc547fc658b40c2eee7a92ef2043326e159b32
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759489"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da yeni uyarı ilkeleri

Office 365 için Microsoft Defender, teslim sonrası algılamalarla ilgili yeni ve geliştirilmiş uyarı ilkeleri kullanıma sunm Office 365 için Microsoft Defender. Bu, bunlarla ilişkili Otomatik Araştırma & Yanıtı (AIR) playbook'larında yapılan iyileştirmeleri içerir. Ayrıca, bu ilkeler tarafından oluşturulan uyarıları kuruluşunuz üzerindeki etkileriyle daha iyi uyumlu hale getirmek için altı varsayılan uyarı ilkesi için önem derecesi sınıflandırmasını değiştiriyoruz.

## <a name="post-delivery-detections"></a>Teslim sonrası algılamalar

Office 365 için Microsoft Defender Sıfır saat otomatik temizleme (ZAP) gelen kutusundan iletileri kaldırdıktan sonra teslim sonrası algılamalarla ilgili dört yeni varsayılan uyarı ilkesi sunacağız. Bu dört yeni uyarı ilkesi, ZAP senaryolarını kapsayan mevcut iki varsayılan uyarı ilkesiyle değiştirilecek ve kuruluşlara temel algılama ve ilgili göstergeler hakkında gelişmiş ayrıntılar sağlayacaktır. Bu uyarılar (ve bu uyarılardan tetiklenecek AIR playbook'ları), URL'nin kötü amaçlı bir dosyaya işaret edip etmediğini veya dosyanın kötü amaçlı bir URL içermesi de dahil olmak üzere e-postaların ve varlıkların tehditlerini doğru bir şekilde yakalar.

Aşağıdaki tabloda yeni uyarı ilkeleri ve kaldırılacak mevcut uyarı ilkeleri listelenir. Dağıtımla ilgili ayrıntılar için [Bunun kuruluşunuzu nasıl etkileyeceği](#how-this-will-affect-your-organization) bölümüne bakın.

|Yeni veya mevcut uyarı ilkesi|Uyarı ilkesi adı|Uyarı ilkesi kimliği|
|---|---|---|
|Yeni|**Kötü amaçlı URL içeren e-posta iletileri teslimden sonra kaldırıldı**|8e6ba277-ef39-404e-aaf1-294f6d9a2b88|
|Yeni|**Kötü amaçlı dosya içeren e-posta iletileri teslimden sonra kaldırıldı**|4b1820ec-39dc-45f3-abf6-5ee80df51fd2|
|Yeni|**Kampanyadan gelen e-posta iletileri teslim edildi ve daha sonra kaldırıldı**|c8522cbb-9368-4e25-4ee9-08d8d899dfab|
|Yeni|**Teslimden sonra e-posta iletileri kaldırıldı**|b8f6b088-5487-4c70-037c-08d8d71a43fe|
|Var (kaldırılacak)|**Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırıldı**|EA8169FA-0678-4751-8854-AEBEA7ADECEB|
|Var (kaldırılacak)|**Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırıldı**|0179B3F7-3FDA-40C3-8F24-278563978DBB|

## <a name="alert-severity-enhancements"></a>Uyarı önem derecesi geliştirmeleri

Aşağıdaki tablo için önem derecesi sınıflandırmaları değiştirilen varsayılan uyarı ilkelerini tanımlar. Kuruluşunuzdaki olası risk ve etkiyle daha iyi uyum sağlamak ve güvenlik ekiplerinizin bu ilkeler tarafından oluşturulan uyarıları önceliklendirmesine yardımcı olmak için bu uyarı ilkeleri için önem derecesi sınıflandırmasını değiştiriyoruz.

|Uyarı|Uyarı ilkesi kimliği|Eski önem derecesi|Yeni önem derecesi|
|---|---|---|---|
|**Şüpheli e-posta iletme etkinliği**|BFD48F06-0865-41A6-85FF-ADB746423EBF|Orta|Yüksek|
|**Kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilen e-posta**|B26A5770-0C38-434A-9380-3A3C2C27BBB3|Bilgi|Düşük|
|**Kimlik avı olarak bildirilen e-postada olağan dışı artış**|A00D8C62-9320-4EEA-A7E5-966B9AC09558|Yüksek|Orta|
|**Yönetici Gönderimi sonucu tamamlandı**|AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41|Düşük|Bilgi|
|**İletme/yeniden yönlendirme kuralı oluşturma**|D59A8FD4-1272-41EE-9408-86F7BCF72479|Düşük|Bilgi|
|**eBulma araması başlatıldı veya dışarı aktarıldı**|6FDC5710-3998-47F0-AFBB-57CEFD7378A|Meduim|Bilgi|

## <a name="when-will-these-changes-happen"></a>Bu değişiklikler ne zaman gerçekleşecek?

Aşağıdaki tabloda, yeni uyarı ilkelerinin teslim sonrası uyarıları tetiklemeye ne zaman başlayacağı gösterilmiştir. Tabloda, mevcut iki uyarı ilkesi ne zaman kaldırılacağı da tanımlanır.

|Uyarı ilkesi|Tarih|
|---|---|
|**Teslimden sonra kötü amaçlı URL içeren e-posta iletileri kaldırıldı** (yeni)|Uyarılar 11 Nisan 2021'de tetiklenecek|
|**Kötü amaçlı dosya içeren e-posta iletileri teslimden sonra kaldırıldı** (yeni)|Uyarılar 11 Nisan 2021'de tetiklenecek|
|**Kampanyadan gelen e-posta iletileri teslim edildi ve daha sonra kaldırıldı** (yeni)|Uyarılar 28 Mayıs 2021'de tetiklenecek|
|**Kötü amaçlı e-postalar teslim edildi ve daha sonra kaldırıldı** (yeni)|Uyarılar 28 Mayıs 2021'de tetiklenecek|
|**Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırıldı** (mevcut, kaldırılacak)|Uyarı ilkesi Haziran 2021'de kaldırıldı. [Bu değişikliklere hazırlanmak için yapmanız gerekenler](#what-you-need-to-do-to-prepare-for-these-changes) bölümüne bakın.|
|**Teslimden sonra kaldırılan kötü amaçlı yazılım içeren e-posta iletileri** (mevcut, kaldırılacak)|Uyarı ilkesi Haziran 2021'de kaldırıldı. [Bu değişikliklere hazırlanmak için yapmanız gerekenler](#what-you-need-to-do-to-prepare-for-these-changes) bölümüne bakın.|

Uyarı önem derecesi değişiklikleri 14 Mayıs 2021'e kadar tüm kuruluşlara dağıtılacaktır.

## <a name="how-this-will-affect-your-organization"></a>Bu durum kuruluşunuzu nasıl etkileyecek?

Yeni uyarılar tetiklenmeye başlar ve yukarıda listelenen tarihlerde kuruluşunuzda AIR araştırmalarını tetikler. Kaldırılacak iki uyarıyı kullanıma hazır hale getiren güvenlik kuruluşları üzerindeki etkisini azaltmak için, mevcut uyarı ilkeleri tarafından tetiklenen uyarıları ve 5 Nisan 2021 *ile* 28 Mayıs 2021 tarihleri arasında yeni uyarı ilkeleri tarafından tetiklenen uyarıları görürsünüz. Bu, güvenlik ekiplerine gerekli değişiklikleri işlemek için zaman sağlamaktır. Bu kısa süre boyunca güvenlik ekiplerine artan uyarı hacminde yardımcı olmak için hem mevcut uyarılar hem de yeni uyarılar aynı AIR araştırması ile ilişkilendirilecek ve aynı Olayla ilişkilendirilecektir. Daha açık belirtmek gerekirse, uyarılar, AIR araştırmaları ve Olaylar için aşağıdaki davranışlar da buna dahildir:

- **Uyarılar**: Tasarım gereği, mevcut ve yeni uyarılar arasında aşağıdaki uyarı çiftlerini görürsünüz:

  - **Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırıldı** VE **Kötü amaçlı URL içeren e-posta iletileri teslimden sonra kaldırıldı**

  - **Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırıldı** VE **Kötü amaçlı dosya içeren e-posta iletileri teslimden sonra kaldırıldı**

  ![Yeni ve mevcut uyarılar için uyarı çiftleri.](../media/DefenderAlerts.png)

   Bu uyarı çiftlerini yönetme hakkında daha fazla bilgi [için bu değişikliklere hazırlanmak için yapmanız gerekenler](#what-you-need-to-do-to-prepare-for-these-changes) bölümüne bakın.

- **AIR İncelemeleri**: Uyarılar tek bir AIR Araştırmasıyla ilişkilendirilecek ve uyarılardan biri "tetikleme" ve diğeri "tekrarlanan" olarak sınıflandırılacaktır.

  ![AIR Araştırmalarında uyarı çiftleri.](../media/AIRAlerts.png)

- **Olaylar**: Her iki uyarı da aynı Olayla ilişkilendirilecektir

  ![Olaylar'daki uyarı çiftleri.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Bu değişikliklere hazırlanmak için yapmanız gerekenler

Kuruluşunuzun bu uyarıları nasıl kullandığı, hazırlanmak için yapmanız gerekenleri belirler. Uyarıları kullanıma hazır hale getirdiyseniz ve bunları bir API, uyarı e-posta bildirimi veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> ya da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> kullanıyorsanız, iş akışlarınızı değiştirmeniz gerekir.

**Bu uyarıları kullanıma hazır hale getirmediyseniz aşağıdakilerden birini yapabilirsiniz:**

- Kuruluşunuzdaki uyarı hacmini azaltmak için aşağıdaki uyarı ilkelerini (kaldırılmakta olan) devre dışı bırakın:

  - **Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırıldı**

  - **Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırıldı**

- Hiçbir şey yapma. Mevcut uyarı ilkelerini 28 Mayıs 2021'de devre dışı bırakacağız.

**Bu uyarıları kullanıma hazır hale getirdiyseniz:**

- 28 Mayıs 2021'de mevcut uyarı ilkesinin kaldırılmasını tahmin ederek yeni uyarıları iş akışlarınızın bir parçası olarak kullanmaya başlayın. Bilet sisteminizde özel mantığınız, uyarı e-posta bildirimleri aldığınız bir güvenlik posta kutunuz veya uyarı adına veya uyarı ilkesi kimliğine (CorrelationId) bağlı olan bir SIEM çözümü varsa, değişikliği karşılamak için mantığı değiştirmeniz gerekir.

  > [!NOTE]
  > Uyarılar, araştırmalar ve olaylardaki bilgiler değişmemiştir. Aslında bu bilgiler, bunlarla ilişkili tehditler hakkında ek ayrıntılarla geliştirilmiştir.

- Değişiklikleri yaptıktan sonra, kuruluşunuzdaki uyarı hacmini azaltmak için mevcut uyarı ilkelerini devre dışı bırakabilirsiniz:

  - **Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırıldı**

  - **Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırıldı**

  Alternatif olarak, bu uyarı ilkelerini 28 Mayıs 2021'de silene kadar etkin bırakabilirsiniz.
