---
title: Otomatik araştırma ve düzeltme özelliklerini yapılandırma
description: Uç Nokta için Microsoft Defender'da otomatik araştırma ve düzeltme yeteneklerinizi ayarlayın.
keywords: yapılandırma, kurulum, otomatik, araştırma, algılama, uyarılar, düzeltme, yanıt
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: 3f51ce7c0eb45861a8b5277266b18e6d03e53178
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021634"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da otomatik araştırma ve düzeltme özelliklerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kuruluşta Uç Nokta için [Microsoft Defender](/windows/security/threat-protection/) (Uç Nokta için [Defender)](/microsoft-365/security/defender-endpoint/automated-investigations) kullanıyorsa, otomatik araştırma ve düzeltme özellikleri güvenlik işlemleri ekip zaman ve çalışmanızı kurtarabilir. Bu blog [gönderisinde de](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946) ana hatlarıyla açıklanan bu özellikler, güvenlik analisti tarafından tehditleri araştırmak ve düzeltmek için atılması gereken ideal adımları taklit ediyor. [Otomatik araştırma ve düzeltme hakkında daha fazla bilgi edinmek için](/microsoft-365/security/defender-endpoint/automated-investigations):

Otomatik araştırmayı ve düzeltmeyi yapılandırmak için:

1. [Özellikleri açma](#turn-on-automated-investigation-and-remediation); ve
2. [Cihaz gruplarını ayarlayın](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Otomatik araştırmayı ve düzeltmeyi açma

1. Genel yönetici veya güvenlik yöneticisi olarak, Genel Microsoft 365 Defender ( ) gidin<https://security.microsoft.com> ve oturum açın.
2. Gezinti bölmesinde, **Tamam'ı Ayarlar**.
3. Genel bölümünde **Gelişmiş** **özellikler'i seçin**.
4. Hem Otomatik **Araştırma'ya hem de Uyarıları** **otomatik olarak çöz'e açma**.

## <a name="set-up-device-groups"></a>Cihaz gruplarını ayarlama

1. İzinler Microsoft 365 Defender ()<https://security.microsoft.com> sayfasında **, Ayarlar altında** Cihaz **grupları'ı seçin**.
2. **+ Cihaz grubu ekle'yi seçin**.
3. Aşağıdaki gibi en az bir cihaz grubu oluşturun:
   - Cihaz grubu için bir ad ve açıklama belirtin.
   - Otomasyon **düzeyi listesinde,** Tam - otomatik olarak tehditleri düzeltmek **gibi bir düzey seçin**. Otomasyon düzeyi düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi alınıp alınmayacaklarını belirler. Daha fazla bilgi edinmek için [bkz. Otomatik araştırma ve düzeltme otomasyon düzeyleri](automation-levels.md).
   - Üyeler bölümünde **,** cihazları tanımlamak ve eklemek için bir veya birden çok koşullar kullanın.
   - Kullanıcı **erişimi sekmesinde**, [Azure Active Directory cihaz grubuna](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) erişimi olması gereken kullanıcı gruplarını seçin.
4. Cihaz **grubu** ayarlamayı bitirdikten sonra Bitti'yi seçin.

## <a name="next-steps"></a>Sonraki adımlar

- [Bekleyen ve tamamlanmış düzeltme eylemlerini görüntülemek için İşlem Merkezi'ne ziyaret edin](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Bekleyen eylemleri gözden geçirme ve onaylama](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)
