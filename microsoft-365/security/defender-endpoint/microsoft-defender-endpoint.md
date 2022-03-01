---
title: Uç Nokta için Microsoft Defender
description: Uç Nokta için Microsoft Defender, gelişmiş kalıcı tehditlere karşı savunmaya yardımcı olan bir kurumsal uç nokta güvenlik platformudur.
keywords: Uç nokta için Microsoft Defender'a giriş, Uç nokta için Microsoft Defender, siber güvenlik, gelişmiş kalıcı tehdit, kurumsal güvenlik, makine davranışı algılayıcısı, bulut güvenliği, çözümleme, tehdit zekası, saldırı yüzeyini azaltma, yeni nesil koruma, otomatik araştırma ve düzeltme, Microsoft tehdit uzmanları, güvenli puan, gelişmiş tarama, Microsoft 365 Defender, siber tehdit avı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: high
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: intro-overview
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4308c203093d2170cc1a6316db824ee9935363f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019497"
---
# <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Microsoft Defender, kurumsal ağların gelişmiş tehditleri engellemesini, algılamasını, araştırmasını ve yanıtlamasını önlemeye yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur.

> [!TIP]
> Yakında, Uç Nokta için Microsoft Defender iki plan olarak kullanılabilir olacak. Bu makalede, Uç Nokta Planı 2 için Microsoft Defender'da bulunan özellikler ve özellikler açıklanmıştır. [Uç Nokta Plan 1 ve Plan 2 için Microsoft Defender hakkında daha fazla bilgi öğrenin](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Uç Nokta için Defender, Windows 10'de ve Microsoft'un güçlü bulut hizmetinin yerleşik teknolojisini aşağıdaki birleşimini kullanır:

- **Uç nokta** davranış algılayıcıları: Windows 10'a yerleştirilmiş olan bu algılayıcılar, işletim sisteminden davranışsal sinyaller toplar ve bu algılayıcı verilerini Uç Nokta için Microsoft Defender'ın özel, yalıtılmış bulut örneğine gönderir.

- Bulut güvenlik **analizi**: Windows ekosistemi, kurumsal bulut ürünleri (Office 365 gibi) ve çevrimiçi varlıklar genelinde büyük verilerden, cihaz öğrenmeden ve benzersiz Microsoft optik bağlantılardan yararlanarak davranışsal sinyaller içgörülere, algılamalara ve gelişmiş tehditlere karşı önerilen yanıtlara çevrilir.

- **Tehdit zekası**: Microsoft ekipleri, güvenlik ekipleri tarafından oluşturulan ve iş ortakları tarafından sağlanan tehdit zekası tarafından geliştirilmiş tehdit zekası, tehdit zekası ile toplanan algılayıcı verilerinde gözlemlenen saldırgan araçları, teknikler ve yordamları belirlemek ve uyarılar oluşturmak için Uç Nokta için Defender'ı sağlar.

<center><h2>Uç Nokta için Microsoft Defender</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Tehdit & Güvenlik Açığı Yönetimi</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Saldırı yüzeyini azaltma</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Yeni nesil koruma</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Uç nokta algılama ve yanıt</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Otomatik araştırma ve düzeltme</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Microsoft Tehdit Uzmanları</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Merkezi yapılandırma ve yönetim, API'ler</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
>
> - Uç nokta için Defender'daki en son iyileştirmeler: Uç nokta için [Microsoft Defender'daki yenilikleri öğrenin](whats-new-in-microsoft-defender-endpoint.md).
> - Uç Nokta için Microsoft Defender, son MITRE değerlendirmesinde endüstri lideri optikleri ve algılama özelliklerini gösteriyor. Okuma: [Analizler CK tabanlı değerlendirmede MITRE ATT&okuma](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

<a name="tvm"></a>

**[Tehdit & Güvenlik Açığı Yönetimi](next-gen-threat-and-vuln-mgt.md)**

Bu yerleşik özellik, uç nokta güvenlik açıklarının ve hatalı yapılandırmaların bulunması, önceliklendirmesi ve düzeltmesi için oyun değiştirme risk tabanlı bir yaklaşım kullanır.

<a name="asr"></a>

**[Saldırı yüzeyini azaltma](overview-attack-surface-reduction.md)**

Saldırı yüzeyini azaltma özellik kümesi yığındaki ilk savunma hattını sağlar. Yapılandırma ayarlarının doğru bir şekilde ayar olmasını ve risk azaltma tekniklerinin uygulandığını garanti ederek, bu özellikler saldırılara ve sömürüye karşı koyar. Bu özellik kümesi, kötü amaçlı [IP adreslerine](network-protection.md) , etki alanlarına ve [URL'lere](web-protection-overview.md) erişimi düzenleyen ağ koruması ve web koruması da içerir.

<a name="ngp"></a>

**[Yeni nesil koruma](next-generation-protection.md)**

Ağın güvenlik çevresini daha da güçlendirmek için, Uç Nokta için Microsoft Defender yeni nesil koruma kullanarak ortaya çıkan her türlü tehdityi yakalayacak şekilde tasarlanmıştır.

<a name="edr"></a>

**[Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md)**

Uç nokta algılama ve yanıt özellikleri, bunu ilk iki güvenlik sütununa yapıştıran gelişmiş tehditleri algılamak, araştırmak ve yanıtlamak için kullanılır. [Gelişmiş av](advanced-hunting-overview.md) , ihlalleri önceden bulmanızı ve özel algılamalar oluşturmanıza olanak sağlayan sorgu tabanlı bir tehdit arama aracı sağlar.

<a name="ai"></a>

**[Otomatik araştırma ve düzeltme](automated-investigations.md)**

Gelişmiş saldırılara hızlı yanıt ver özelliğiyle birlikte, Uç Nokta için Microsoft Defender dakikalar ölçeğinde uyarı hacmini azaltmaya yardımcı olan otomatik araştırma ve düzeltme özellikleri sunar.

<a name="ss"></a>

**[Cihazlar için Microsoft Güvenli Puan](tvm-microsoft-secure-score-devices.md)**

Uç nokta için Defender, kurumsal ağcının güvenlik durumunu dinamik olarak değerlendirmenize, korumasız sistemleri tanımlamanıza ve genel olarak kurum güvenliğinizi iyileştirmeye yardımcı olmak için önerilen işlemlere yardımcı olmak için Cihazlar için Microsoft Güvenli Puanı içerir.

<a name="mte"></a>

**[Microsoft Tehdit Uzmanları](microsoft-threat-experts.md)**

Uç noktanın yeni yönetilen tehdit arama hizmeti için Microsoft Defender önceden arama, öncelik belirleme ve güvenlik işlemi merkezlerinin (SOC) tehditlere hızla ve doğru biçimde yanıt vermesini sağlayan ek bağlam ve öngörüler sağlar.

> [!IMPORTANT]
> Uç nokta müşterileri için Defender'ın önceden Microsoft Tehdit Uzmanları Hedefli Saldırı Bildirimleri almak ve isteğe bağlı uzmanlarla işbirliği yapmak için önceden yönetilen tehdit arama hizmetine başvurması gerekir. Talep Üzerine Uzmanlar bir eklenti hizmetidir. Hedefli Saldırı Bildirimleri her zaman, siz bu hizmetlere kabul edildikten sonra Microsoft Tehdit Uzmanları tehdit arama hizmetine dahil edilir.
>
> Henüz kaydolmadısanız ve  \> bu avantajdan yararlanan özelliklerden yararlanan bir deneyim Ayarlar **için** \>  \> Genel **Gelişmiş Microsoft Tehdit Uzmanları** gidin. Kabul edildiktan sonra Hedefli Saldırı Bildirimleri'nin avantajlarından faydalanacak ve Talep Edilen Uzmanlar için 90 günlük bir deneme başlatacaksınız. Tam Uzman On Demand aboneliği almak için Microsoft temsilcinize başvurun.

<a name="apis"></a>

**[Merkezi yapılandırma ve yönetim, API'ler](management-apis.md)**

Uç Nokta için Microsoft Defender'ı var olan iş akışlarınıza tümleştirin.

<a name="mtp"></a>

**[Microsoft çözümleriyle tümleştirme](threat-protection-integration.md)**

Uç nokta için Defender, aşağıdakiler gibi çeşitli Microsoft çözümleriyle doğrudan tümleştirilmiştir:

- Bulut için Microsoft Defender
- Microsoft Sentinel
- Intune
- Bulut Uygulamaları için Microsoft Defender
- Kimlik için Microsoft Defender
- Office için Microsoft Defender
- Skype Kurumsal

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Microsoft 365 Defender ile Uç Nokta için Defender ve çeşitli Microsoft güvenlik çözümleri, gelişmiş saldırıları algılayan, önleyen, araştıran ve otomatik olarak yanıt veren uç nokta, kimlik, e-posta ve uygulamalar arasında yerel olarak tümleştirilmiş birleşik bir ihlal öncesi ve ihlal sonrası kurumsal savunma paketi sağlar.


## <a name="training-for-security-analysts"></a>Güvenlik analistleri için eğitim

Microsoft Learn'in bu öğrenme yolu ile, Uç Nokta için Defender'ı ve uç noktaların cihazlarınız ve sistemleriniz genelinde tehditlere karşı nasıl yardımcı olduğunu, algılamanıza, araştırmanıza ve bu tehditlere nasıl yanıt ver genelinde yardımcı olduğunu öğrenebilirsiniz.

|Eğitim:|Siber saldırıları algıla ve bu saldırılara Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender simgesi.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Uç nokta için Defender, tek, birleşik bir platformda güvenlik açığı yönetimi, uç nokta koruması, uç noktada algılama ve yanıtlama, mobil tehdit savunması ve yönetilen hizmetler sunan bir uç nokta güvenlik çözümüdür.<p> 2 sa 25 dak . Learning Yol - 9 Modüller|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/paths/defender-endpoint-fundamentals/)
