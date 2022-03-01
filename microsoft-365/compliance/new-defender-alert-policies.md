---
title: Office 365 için Microsoft Defender'daki yeni uyarı Office 365
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
description: İş için Microsoft Defender'a yönelik yeni uyarı ilkelerini Office 365. Ayrıca, yeni uyarı ilkeleriyle değiştirilmiş olan iki uyarı ilkelerini de gerildireceğiz.
ms.openlocfilehash: 895a1fa51b9db5991bdb5235fd467bbac581d02e
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005468"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'daki yeni uyarı Office 365

Microsoft Defender for Office 365 is introducing new and improved alert policies related to post-delivery detections. Bu, ilgili Otomatik Araştırma ve Yanıt (AIR) & kitaplarına yönelik iyileştirmeleri içerir. Buna ek olarak, bu ilkeler tarafından oluşturulan uyarıları organizasyonu üzerindeki etkisiyle daha iyi hizalamak için altı varsayılan uyarı ilkelerinin önem derecesini değiştireceğiz.

## <a name="post-delivery-detections"></a>Teslim sonrası algılamaları

Office 365 için Microsoft Defender otomatik temizlemesi (ZAP) gelen kutusundan iletileri kaldırıyorsa, teslim sonrası algılamalarla ilgili dört yeni varsayılan uyarı ilkeleri tanıteceğiz. Bu dört yeni uyarı ilkeleri, ZAP senaryolarını kapsıyor olan mevcut iki varsayılan uyarı ilkelerinin yerini alacak ve kuruluşlara temel algılama ve ilgili göstergeler hakkında gelişmiş ayrıntılar sağlayacaktır. Bu uyarılar (ve bu uyarılardan tetiklenen AIR çalışma kitapları) URL kötü amaçlı bir dosyayı mı yoksa dosyanın kötü amaçlı bir URL'yi mi içerdiği de dahil olmak üzere e-postaların ve varlıkların tehditlerini doğru biçimde yakalar.

Aşağıdaki tabloda, kaldırılacak yeni uyarı ilkeleri ve var olan uyarı ilkeleri listelemektedir. Bu, [kuruluşlarınızı nasıl etkileyecek? bölümüne](#how-this-will-affect-your-organization) bakın.

| Yeni veya var olan uyarı ilkesi | Uyarı ilkesi adı | Uyarı ilkesi kimliği|
|:-----------------------------|:----------------|:--------------|
| Yeni| **Teslimden sonra kötü amaçlı URL içeren e-posta iletileri kaldırıldı**   | 8e6ba277-ef39-404e-aaf1-294f6d9a2b88 |
| Yeni| **Teslimden sonra kötü amaçlı dosya içeren e-posta iletileri kaldırıldı**  | 4b1820ec-39dc-45f3-abf6-5ee80df51fd2 |
| Yeni| **Bir kampanyadan gelen e-posta iletileri teslim edildi ve daha sonra kaldırıldı** | c8522cbb-9368-4e25-4ee9-08d8d899dfab |
| Yeni|**E-posta iletileri teslimden sonra kaldırıldı**                | b8f6b088-5487-4c70-037c-08d8d71a43fe |
| Mevcut (kaldırılır)| **Teslimden sonra kimlik avı URL'lerini içeren e-posta iletileri kaldırılıyor**| EA8169FA-0678-4751-8854-AEBEA7ADECEB |
| Mevcut (kaldırılır)| **Teslimden sonra kötü amaçlı yazılımları içeren e-posta iletileri kaldırıldı**| 0179B3F7-3FDA-40C3-8F24-278563978DBB |
||||

## <a name="alert-severity-enhancements"></a>Önem derecesi iyileştirmelerini uyarın

Aşağıdaki tabloda, önem derece sınıflandırmaları değiştiriliyor olan varsayılan uyarı ilkeleri tanımmektedir. Bu uyarı ilkelerinin önem derecesini, kuruluş üzerindeki olası risk ve etkiyle daha iyi uyumlu olacak şekilde değiştiriliyor ve güvenlik ekiplerinin bu ilkelerle oluşturulan uyarılara önceliklerini belirlemesine yardımcı oluyoruz.

| Uyarı| Uyarı ilkesi kimliği| Eski önem derecesi| Yeni önem derecesi  |
|:----------|:---------------|:------------|:--------------|
| **Şüpheli e-posta iletme etkinliği**| BFD48F06-0865-41A6-85FF-ADB746423EBF | Orta| Yüksek|
| **Kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilen e-posta** | B26A5770-0C38-434A-9380-3A3C2C27BBB3 | Bilgilendirme | Düşük|
| **Kimlik avı olarak bildirilen e-postada olağan dışı artış** | A00D8C62-9320-4EEA-A7E5-966B9AC09558 | Yüksek| Orta |
| **Yönetici Gönderimi sonucu tamamlandı** | AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41 | Düşük| Bilgilendirme |
| **Yönlendirme/yeniden yönlendirme kuralı oluşturma** | D59A8FD4-1272-41EE-9408-86F7BCF72479 | Düşük| Bilgilendirme |
| **eBulma araması başlatıldı veya dışarı aktarıldı** | 6FDC5710-3998-47F0-AFBB-57CEFD7378A | Meduim | Bilgilendirme |
|||||

## <a name="when-will-these-changes-happen"></a>Bu değişiklikler ne zaman gerçekleşecek?

Aşağıdaki tabloda, yeni uyarı ilkelerinin teslim sonrası uyarıları tetikleyene başlayacağı tarihi tanımlar. Tabloda ayrıca, var olan iki uyarı ilkelerinin ne zaman kaldırıldığı da tanımlar.

| Uyarı ilkesi| Tarih |
|:------------|:-----|
| **Teslimden sonra kötü amaçlı URL içeren e-posta iletileri kaldırıldı** (yeni) | Uyarılar 11 Nisan 2021'de tetik tetik başlayacaktır|
| **Teslimden sonra kötü amaçlı dosya içeren e-posta iletileri kaldırıldı** (yeni) | Uyarılar 11 Nisan 2021'de tetik tetik başlayacaktır |
| **Bir kampanyadan gelen e-posta iletileri teslim edildi ve daha sonra kaldırıldı** (yeni) | Uyarılar 28 Mayıs 2021'de tetik tetik başlayacaktır|
| **Kötü amaçlı e-postalar teslim edildi ve daha sonra kaldırıldı** (yeni) | Uyarılar 28 Mayıs 2021'de tetik tetik başlayacaktır|
| **Teslimden sonra kaldırılan kimlik avı URL'lerini içeren** e-posta iletileri (var olan, kaldırılacak)| Uyarı ilkesi Haziran 2021'de kaldırıldı. Bu [değişikliklere hazırlanmak için ne yapmak gerekir? bölümüne](#what-you-need-to-do-to-prepare-for-these-changes) bakın.|
| **Teslimden sonra kötü amaçlı yazılımları içeren e-posta** iletileri kaldırıldı (var olan ileti kaldırılacak) | Uyarı ilkesi Haziran 2021'de kaldırıldı. Bu [değişikliklere hazırlanmak için ne yapmak gerekir? bölümüne](#what-you-need-to-do-to-prepare-for-these-changes) bakın. |
|||

Uyarı önem düzeyi değişiklikleri 14 Mayıs 2021'e kadar tüm kuruluşlara aktaracak.

## <a name="how-this-will-affect-your-organization"></a>Bunun organizasyonlarınızı nasıl etkileyeceğini

Yeni uyarılar tetik tetiklenir ve yukarıda listelenen tarihlerde, organizasyonda AIR soruşturmalarını tetikler. Kaldırılacak olan iki uyarıyı işlemden kaldırmış olan güvenlik kuruluşları üzerindeki etkiyi azaltmak için, var olan uyarı ilkeleri tarafından tetiklenen uyarıları ve 5 Nisan 2021  ile 28 Mayıs 2021 arasında yeni uyarı ilkelerinin tetikleyen uyarılarını görmeye devam ediyorsanız. Bunun olması, güvenlik ekiplerine gerekli değişiklikleri işlemek için zaman sağlamaktır. Bu kısa süre içinde güvenlik ekiplerinin artan uyarı sesine yardımcı olması için, hem var olan uyarılar hem de yeni uyarılar aynı AIR soruşturması ile bağlantılı ve aynı Olay ile bağlantılı olacaktır. Daha açık olarak bu, uyarılar, AIR soruşturmaları ve Olaylar için aşağıdaki davranışı içerir:

- **Uyarılar**: Tasarım olarak, mevcut ve yeni uyarılarda aşağıdaki uyarı çiftlerini görüyorsunuz:

  - **Teslimden sonra kimlik avı URL'lerini içeren e-posta iletileri kaldırılıyor** AND **Email messages containing malicious URL removed after delivery**

  - **Teslimden sonra kötü amaçlı yazılımları içeren e-posta iletileri kaldırıldı** AND **Email messages containing malicious file removed after delivery**

  ![Yeni ve var olan uyarılar için uyarı çiftleri.](../media/DefenderAlerts.png)

   Bu uyarı çiftlerini yönetme hakkında daha fazla bilgi için Bu [değişikliklere hazırlanmak için ne yapmak gerekir? bölümüne](#what-you-need-to-do-to-prepare-for-these-changes) bakın.

- **AIR Investigations**: Uyarılar, biri "tetikleyici" ve diğeri de "tekrarlanan" olarak sınıflandırılmış uyarılarla tek bir AIR İncelemesi ile bağlantılıdır.

  ![AIR Investigations'te uyarı çiftleri.](../media/AIRAlerts.png)

- **Olaylar**: Her iki uyarı da aynı Olayla bağlantılıdır

  ![Olaylar'da uyarı çiftleri.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Bu değişikliklere hazırlanmak için gerekenler

Bu uyarılar, neleri hazırlamanız için ihtiyacınız olduğunu, kurum tarafından nasıl kullanılır? belirler. Uyarıları işlemden geçirdiysanız ve bunları bir API, bir uyarı e-posta bildirimi aracılığıyla ya da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> kullanıyorsanız, iş akışlarınızı değiştirmeniz gerekir.

**Bu uyarıları işlemden geçirmek için değilken aşağıdaki işlemlerden birini yapabilirsiniz:**

- Aşağıdaki uyarı ilkelerini (kaldırılan) devre dışı bırakarak, kurum içinde uyarı ses düzeyini azaltma:

  - **Teslimden sonra kimlik avı URL'lerini içeren e-posta iletileri kaldırılıyor**

  - **Teslimden sonra kötü amaçlı yazılımları içeren e-posta iletileri kaldırıldı**

- Hiçbir şey yapma. Mevcut uyarı ilkelerini 28 Mayıs 2021'de devre dışı bırakeceğiz.

**Bu uyarıları işlemden geçirdiysanız:**

- 28 Mayıs 2021'de var olan uyarı ilkesi kaldırmayı denerek, yeni uyarıları iş akışlarınız kapsamında tüket yapmaya başlayabilirsiniz. Bilet sisteminiz, uyarı e-posta bildirimleri veya uyarı adı ya da uyarı ilkesi Kimliğine (CorrelationId) bağlı olan SIEM çözümünü içeren bir güvenlik posta kutunuz varsa, değişikliği kabul etmek için mantığı değiştirmeniz gerekir.

  > [!NOTE]
  > Uyarılar, soruşturmalar ve olaylarda yer alan bilgiler değişmez. Aslında bu bilgiler, tehditlerle ilgili ek ayrıntılarla geliştirilmiştir.

- Değişikliklerinizi yaptıktan sonra, var olan uyarı ilkelerini devre dışı bırakarak, kurumda uyarı ses düzeyini azaltarak şunları kullanabilirsiniz:

  - **Teslimden sonra kimlik avı URL'lerini içeren e-posta iletileri kaldırılıyor**

  - **Teslimden sonra kötü amaçlı yazılımları içeren e-posta iletileri kaldırıldı**

  Alternatif olarak, bu uyarı ilkelerini 28 Mayıs 2021'de silene kadar etkinleştirebilirsiniz.
