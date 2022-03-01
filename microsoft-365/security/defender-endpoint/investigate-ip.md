---
title: Uyarıyla ilişkilendirilmiş IP adresini araştırma
description: Cihazlar ve dış IP adresleri arasındaki olası iletişimi incelemek için araştırma seçeneklerini kullanın.
keywords: araştırma, araştırma, IP adresi, uyarı, Uç Nokta için Microsoft Defender, dış IP
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 2e314f15719d4a6a0e75d5fd26ae788e2382b75a
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997044"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cihazlarınız ve dış İnternet protokolü (IP) adresleri arasındaki olası iletişimi inceler.

Kuruluşta, Komut ve Denetim (C2) sunucuları gibi şüpheli veya bilinen bir kötü amaçlı IP adresiyle iletişim kuran tüm cihazların belirlenmesi, ihlalle ilgili olası dosyaların ve virüs bulaşmış cihazların kapsamını belirlemeye yardımcı olur.

Aşağıdaki bölümlerde yer alan bilgileri IP adresi görünümünde bulabilirsiniz:

- IP dünya çapında
- DNS adlarını ters çevirme
- Bu IP ile ilgili uyarılar
- Kuruluşta IP
- Yaygınlık

## <a name="ip-worldwide-and-reverse-dns-names"></a>IP Worldwide ve Reverse DNS names

IP adresi ayrıntıları bölümünde, IP adresinin ASN ve Ters DNS adları gibi öznitelikleri yer almaktadır.

## <a name="alerts-related-to-this-ip"></a>Bu IP ile ilgili uyarılar

Bu **IP ile ilgili Uyarılar** bölümü IP ile ilişkili uyarıların listesini sağlar.

## <a name="ip-in-organization"></a>Kuruluşta IP

**Kuruluşta IP bölümü**, kuruluşta IP adresinin yaygın olarak kullanımıyla ilgili ayrıntılar sağlar.

## <a name="prevalence"></a>Yaygınlık

Yaygın **yaygınlık** bölümü, bu IP adresine kaç cihaz bağlantısı olduğunu, IP'nin ne zaman ilk ve en son ne zaman olduğunu görüntüler. Bu bölümün sonuçlarını zaman dönemine göre filtrenin; varsayılan süre 30 gündür.

## <a name="most-recent-observed-devices-with-ip"></a>IP ile en son gözlemlenen cihazlar

IP **ile en son gözlemlenen** cihazlar bölümü, IP adresi üzerinde gözlemlenen olaylar ve ilişkili uyarılar üzerinde kronolojik bir görünüm sağlar.

**Dış IP'yi araştırma:**

1. Arama **çubuğu** açılan **menüsünden** IP'yi seçin.
2. ARAMA alanına IP **adresini** girin.
3. Arama simgesine tıklayın veya Enter tuşuna **basın**.

IP adresiyle ilgili ayrıntılar görüntülenir. Bunlar: kayıt ayrıntıları (varsa), ters IP'ler (örneğin, etki alanları), bu IP Adresi ile iletişim kurduğu kuruluşta cihazların yaygın kullanımı (seçilebilir bir süre boyunca) ve kuruluşta bu IP adresiyle iletişim kurduğu gözlemlenen cihazlar.

> [!NOTE]
> Arama sonuçları yalnızca kuruluşta yer alan cihazlarla iletişimde gözlemlenen IP adresleri için döndürülür.

Arama ölçütlerini tanımlamak için arama filtrelerini kullanın. Zaman çizelgesi arama kutusunu, kuruluşta IP adresiyle iletişim kurarken gözlemlenen tüm cihazların, iletişimle ilişkilendirilmiş dosyanın ve gözlemlenen son tarihin sonuçlarını filtrelemek için de zaman çizelgesi arama kutusunu kullanabilirsiniz.

Cihaz adlardan herhangi birini tıklatmak sizi bu cihazın görünümüne alır ve burada bildirilen uyarıları, davranışları ve olayları incelemeye devam edebilirsiniz.

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
