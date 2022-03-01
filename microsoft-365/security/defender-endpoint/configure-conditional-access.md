---
title: Uç Nokta için Microsoft Defender'da Koşullu Erişimi Yapılandırma
description: Koşullu erişim uygulamak için Intune, Microsoft 365 Defender ve Azure'da adımlar hakkında bilgi edinin
keywords: koşullu erişim, koşullu, erişim, cihaz riski, risk düzeyi, tümleştirme, intune tümleştirmesi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8706f756b4e8d0ba87a747396e8f7ef71d66460c
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996461"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da Koşullu Erişimi Yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Bu bölüm, Koşullu Erişim'i düzgün bir şekilde uygulamak için ihtiyacınız olan tüm adımlarda size yol sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

> [!WARNING]
> Bu senaryoda Azure AD kayıtlı cihazların desteklene olmadığını unutmayın.</br>
> Yalnızca Intune'a kayıtlı cihazlar de desteklemektedir.

Tüm cihazlarınızı Intune'a kayıtlı olduğundan emin olun. Intune'da cihazları kaydetmek için aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz:

- IT Yöneticisi: Otomatik kaydı etkinleştirme hakkında daha fazla bilgi için bkz. Windows [Kaydı](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Son kullanıcı: Intune'da Windows 10 ve Windows 11 cihazınızı kaydetme hakkında daha fazla bilgi için bkz. [Windows 10 cihazınızı Intune'a kaydetme](/intune/quickstart-enroll-windows-device)
- Son kullanıcı alternatifi: Azure AD etki alanına katılma hakkında daha fazla bilgi için bkz [. Nasıl yapılan: Azure AD birleştirme uygulamanızı planlama](/azure/active-directory/devices/azureadjoin-plan).

Uygulama adımlarını, Intune portalını Microsoft 365 Defender Azure AD portalını kullanarak atılması gereken adımlar vardır.

Bu portallara erişmek ve Koşullu erişim uygulamak için gereken rolleri not etmek önemlidir:

- **Microsoft 365 Defender**- Tümleştirmeyi açmak için portalda bir genel yönetici rolüyle oturum açabilirsiniz.
- **Intune** - Yönetim izinleri olan güvenlik yöneticisi haklarıyla portalda oturum açın.
- **Azure AD portalı** - Genel yönetici, güvenlik yöneticisi veya Koşullu Erişim yöneticisi olarak oturum açın.

> [!NOTE]
> Intune tarafından yönetilen Microsoft Intune Azure AD'nin 11 cihazla birlikte katıldığı bir Windows 10 Windows gerekir.

Koşullu Erişim'i etkinleştirmek için aşağıdaki adımları izleyin:

- 1. Adım: Bağlantı Microsoft Intune bağlantısını Microsoft 365 Defender
- 2. Adım: Intune'da Uç Nokta tümleştirmesi için Defender'ı açma
- 3. Adım: Intune'da uyumluluk ilkesi oluşturma
- 4. Adım: İlkeyi atama 
- 5. Adım: Azure AD Koşullu Erişim ilkesi oluşturma

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>1. Adım: Microsoft Intune açma

1. Gezinti bölmesinde, Genel Gelişmiş **Ayarlar** \> **Uç Noktaları Ve** \>  \> **Bağlantı için Microsoft Intune** \> **seçin**.
2. Bu ayarı Microsoft Intune Açık olarak **seçin**.
3. Kaydetme **tercihleri'ne tıklayın**.

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>2. Adım: Intune'da Uç Nokta tümleştirmesi için Defender'ı açma

1. [Azure portalda](https://portal.azure.com) oturum açın.
2. Cihaz **uyumluluğu** \> **Microsoft Defender ATP'yi seçin**.
3. **Bağlan Windows 10.0.15063+ cihazlarını Microsoft Defender Gelişmiş Tehdit Koruması olarak Açık** olarak **ayarlayın**.
4. **Kaydet**'e tıklayın.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>3. Adım: Intune'da uyumluluk ilkesi oluşturma

1. [Azure portalında Tüm](https://portal.azure.com) **hizmetler'i seçin**, **Intune'a** göre filtre uygulama ve Tüm Hizmetler'i **Microsoft Intune**.
2. Cihaz **Uyumluluk İlkeleri** \> **İlkeleri Oluştur'a** \> **seçin**.
3. Ad ve **Açıklama** **girin**.
4. **Platform'da** Seçenekler ve **Windows 10 seçin**.
5. Cihaz **Durumu ayarlarında,** Cihazın tercih **ettiğiniz düzeye** göre Cihaz Tehdit Düzeyi'nde veya altında yer ayarlama:

   - **Güvenli**: En güvenli düzeydir. Cihazın mevcut tehditlere sahip olamaz ve şirket kaynaklarına erişmeye devam edebilirsiniz. Herhangi bir tehdit bulunursa cihaz uyumlu olmayan olarak değerlendirilir.
   - **Düşük**: Yalnızca düşük düzeyli tehdit varsa cihaz uyumludur. Orta veya yüksek tehdit düzeylerine sahip cihazlar uyumlu değildir.
   - **Orta**: Cihazda bulunan tehditlerin düşük veya orta olması cihaza uyumludur. Yüksek düzeydeki tehditler algılanırsa cihaz uyumlu olmayan olarak değerlendirilir.
   - **Yüksek**: Bu düzey en az güvenlidir ve tüm tehdit düzeylerine izin verir. Dolayısıyla, yüksek, orta veya düşük tehdit düzeylerine sahip cihazlar uyumlu kabul edilir.

6. **Değişikliklerinizi kaydetmek** (**ve ilkeyi** oluşturmak) için Tamam'ı ve Oluştur'a tıklayın.

### <a name="step-4-assign-the-policy"></a>4. Adım: İlkeyi atama

1. [Azure portalında Tüm](https://portal.azure.com) **hizmetler'i seçin**, **Intune'a** göre filtre uygulama ve Tüm Hizmetler'i **Microsoft Intune**.
2. Cihaz **Uyumluluk İlkeleri** \> **'**> Uç nokta uyumluluk ilkesi için Microsoft Defender'ı seçin.
3. **Ödevler'i seçin**.
4. İlkeyi atamak için Azure AD gruplarınızı dahil edin veya dışlayın.
5. İlkeyi gruplara dağıtmak için Kaydet'i **seçin**. İlke tarafından hedef alan kullanıcı cihazları uyumluluk için değerlendirilir.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>5. Adım: Azure AD Koşullu Erişim ilkesi oluşturma

1. [Azure portalında,](https://portal.azure.com) Koşullu **Erişim Azure Active Directory** \> **ilkeyi** \> **açın**.
2. bir ilke Adı **girin ve** Kullanıcılar ve **gruplar'ı seçin**. İlke için gruplarınızı eklemek üzere Ekle veya Dışarıda Bırak seçeneklerini kullanın ve Bitti'yi **seçin**.
3. Bulut **uygulamaları'ı** seçin ve hangi uygulamaların korunmasını istediğinize seçin. Örneğin, Uygulamaları **seç'i ve ardından** **Office 365 SharePoint Online'ı ve Office 365 Exchange Online****.** **Değişikliklerinizi kaydetmek** için Bitti'yi seçin.

4. **İlkeyi** \> **uygulamalara ve** tarayıcılara uygulamak için Koşullar İstemci uygulamaları'ı seçin. Örneğin, **Evet'i seçin** ve ardından **Tarayıcı ve Mobil** uygulamalar **ile masaüstü istemcilerini etkinleştirin**. **Değişikliklerinizi kaydetmek** için Bitti'yi seçin.

5. Cihaz **uyumluluğuna** bağlı olarak Koşullu Erişim uygulamak için Ver'i seçin. Örneğin, Erişim ver **Cihazın uyumlu** \> **olarak işaret verilmesini gerektir'i seçin**. **Değişikliklerinizi kaydetmek** için Seç'i seçin.

6. **Değişikliklerinizi kaydetmek için** İlkeyi **etkinleştir'i ve** ardından Oluştur'a tıklayın.

Daha fazla bilgi için bkz [. Intune'da Koşullu Erişim ile Uç Nokta için Microsoft Defender'da uyumluluğu zorlama](/intune/advanced-threat-protection).

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
