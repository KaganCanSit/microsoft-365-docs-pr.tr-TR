---
title: Uç nokta etki alanları için Microsoft Defender'ı araştırma
description: Cihazların ve sunucuların kötü amaçlı etki alanlarıyla iletişim kurmada olup olduğunu görmek için araştırma seçeneklerini kullanın.
keywords: etki alanını araştırma, etki alanı, kötü amaçlı etki alanı, Uç Nokta için Microsoft Defender, uyarı, URL
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bc309c3215524b20ff93c6f1f9c16248fdfffac1
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997063"
---
# <a name="investigate-a-domain-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Kuruluş ağınız içinde yer alan cihazların ve sunucuların bilinen kötü amaçlı bir etki alanıyla iletişim kurarak iletişim kurduğuna bakın.

Arama özelliğini kullanarak veya Cihaz zaman çizelgesinden bir etki alanı bağlantısına tıklayarak etki alanını **araştırabilirsiniz**.

Aşağıdaki bölümlerde yer alan bilgileri URL görünümünde görüntüebilirsiniz:

- URL ayrıntıları, Kişiler, Ad Sunucuları
- Bu URL ile ilgili uyarılar 
- Kuruluşta URL
- URL ile en son gözlemlenen cihazlar

## <a name="url-worldwide"></a>Url dünya çapında

Dünya **Çapında URL** bölümünde URL, Whois'in diğer ayrıntılarını içeren bir bağlantı, ilgili açık olay sayısı ve etkin uyarı sayısı liste edilmektedir.

## <a name="incident"></a>Olay

Olay **kartı** son 180 gün içinde olaylarda tüm etkin uyarıların çubuk grafiğini görüntüler.

## <a name="prevalence"></a>Yaygınlık

Yaygın **Destek** kartı, kuruluş içinde URL'nin belirli bir süre boyunca yaygın olarak kullanımıyla ilgili ayrıntılar sağlar.

Varsayılan süre son 30 gündür, ancak kartın köşesindeki aşağı dönük oku seçerek aralığı özelleştirebilirsiniz. Kullanılabilir en kısa aralık geçen gün boyunca yaygınlık için, en uzun aralık son 6 aydan fazladır.

## <a name="alerts"></a>Uyarılar

Uyarılar **sekmesi** , URL'yle ilişkilendirilmiş uyarıların listesini sağlar. Burada gösterilen tablo, Uyarılar sırası ekranında görünen ve yalnızca etki alanıyla ilişkili uyarıları, önem derecesini, durumunu, ilişkili olayı, sınıflandırmayı, soruşturma durumunu ve daha fazlasını gösteren, uyarıların filtrelenmiş bir sürümüdür.

Uyarılar sekmesi, sütun başlıklarının üstündeki eylem menüsünde Sütunları özelleştir'i **seçerek** daha fazla veya daha az bilgi gösterecek şekilde ayarlanabilir. Görüntülenen öğe sayısı da, aynı menüde sayfa başına **öğe seçerek** ayarlanabilir.

## <a name="observed-in-organization"></a>Kuruluşta gözlemlenen

**Kuruluşta Gözlemlenen sekmesi**, URL'de gözlemlenen olaylar ve ilişkili uyarılar üzerinde kronolojik bir görünüm sağlar. Bu sekme bir zaman çizelgesini ve saat, cihaz gibi olay ayrıntılarını listeleyilebilen bir özelleştirilebilir tabloyu ve bunun kısa bir açıklamasını içerir. 

Tablo üstbilgilerinin üstündeki metin alanlarına tarihleri girerek, farklı zaman dönemleri olan olayları görüntüebilirsiniz. Zaman aralığını, zaman çizelgesinin farklı alanlarını seçerek de özelleştirebilirsiniz.

**Etki alanını araştırma:**

1. Arama **çubuğu** açılan **menüsünden** URL'yi seçin.
2. Arama alanına **URL'yi** girin.
3. Arama simgesine tıklayın veya Enter tuşuna **basın**. URL ile ilgili ayrıntılar görüntülenir. Not: Arama sonuçları yalnızca kuruluşta yer alan cihazlardan gelen iletişimlerde gözlemlenen URL'ler için döndürülür.
4. Arama ölçütlerini tanımlamak için arama filtrelerini kullanın. Ayrıca, kuruluşta URL ile iletişim kurarken gözlemlenen tüm cihazların, iletişimle ilişkilendirilmiş dosyanın ve gözlemlenen son tarihin görüntülenen sonuçlarını filtrelemek için de zaman çizelgesi arama kutusunu kullanabilirsiniz.
5. Cihaz adlardan herhangi birini tıklatmak sizi bu cihazın görünümüne alır ve burada bildirilen uyarıları, davranışları ve olayları incelemeye devam edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
