---
title: Saldırı simülasyonu eğitimini kullanmaya başlama
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Microsoft 365 E5 veya Plan 2 kuruluşlarında sanal kimlik avı ve parola saldırıları çalıştırmak için Saldırı simülasyonu eğitimini kullanmayı öğrenebilir Office 365 için Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79c8db9a088484a56e559ab4c3e33d68ebf33380
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840155"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Office 365 için Defender'da Saldırı simülasyonu eğitimini kullanarak Kullanmaya başlayın

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

[Kuruluşunuzda Tehdit Araştırması ve Yanıt özelliklerini](office-365-ti.md) içeren Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2 varsa, Microsoft 365 Defender portalında Saldırı simülasyonu eğitimini kullanarak gerçekçi saldırı senaryolarını Organizasyon. Bu sanal saldırılar, gerçek bir saldırı sonucu etkilemeden önce savunmasız kullanıcıları belirlemenize ve bulmanıza yardımcı olabilir. Daha fazla bilgi edinmek için bu makaleyi okuyun.

Saldırı simülasyonu eğitimi hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMhvB]

> [!NOTE]
> Saldırı simülasyonu eğitimi, Tehdit yönetimi **Saldırı simülatörü** veya <https://protection.office.com/attacksimulator>konumundaki Güvenlik & Uyumluluk Merkezi'nde bulunan eski Saldırı Simülatörü v1 **deneyiminin** \> yerini alır.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açmak için adresine <https://security.microsoft.com>gidin. Saldırı simülasyonu eğitimi **, E-posta ve işbirliği** \> **Saldırı simülasyonu eğitimi'nde** sağlanır. Doğrudan Saldırı simülasyonu eğitimine gitmek için kullanın <https://security.microsoft.com/attacksimulator>.

- Farklı Microsoft 365 aboneliklerinde Saldırı simülasyonu eğitiminin kullanılabilirliği hakkında daha fazla bilgi için bkz. [hizmet açıklaması Office 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Bu makaledeki yordamları gerçekleştirmeden önce **Azure Active Directory'de** izinlerin atanmış olması gerekir. Özellikle, aşağıdaki rollerden birinin üyesi olmanız gerekir:
  - **Genel Yönetici**
  - **Güvenlik Yöneticisi**
  - **Saldırı Benzetimi Yöneticileri**<sup>\*</sup>: Saldırı simülasyonu kampanyalarının tüm yönlerini oluşturun ve yönetin.
  - **Saldırı Yükü Yazarı**<sup>\*</sup>: Bir yöneticinin daha sonra başlatabileceği saldırı yükleri oluşturun.

  <sup>\*</sup>Microsoft 365 Defender portalında bu role kullanıcı ekleme işlemi şu anda desteklenmiyor.

  Daha fazla bilgi için bkz. [Microsoft 365 Defender portalındaki izinler](permissions-microsoft-365-security-center.md) veya [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

- Saldırı benzetimi eğitimi için karşılık gelen PowerShell cmdlet'leri yoktur.

- Saldırı benzetimi ve eğitimle ilgili veriler, Microsoft 365 hizmetleri için diğer müşteri verileriyle birlikte depolanır. Daha fazla bilgi için bkz. [Microsoft 365 veri konumları](../../enterprise/o365-data-locations.md). Saldırı simülasyonu şu bölgelerde kullanılabilir: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE ve DEU.

  > [!NOTE]
  > NOR, ZAF, ARE ve DEU en son eklemelerdir. Bildirilen e-posta telemetrisi dışındaki tüm özellikler bu bölgelerde kullanılabilir. Bunu etkinleştirmek için çalışıyoruz ve bildirilen e-posta telemetrisi kullanılabilir duruma gelir gelmez müşterilerimizi bilgilendireceğiz.

- 15 Haziran 2021 itibariyle, saldırı simülasyonu eğitimi GCC... Kuruluşunuzda Office 365 G5 GCC veya Kamu için Office 365 için Microsoft Defender (Plan 2) varsa, kuruluşunuzda bu makalede açıklandığı gibi gerçekçi saldırı senaryoları çalıştırmak için Microsoft 365 Defender portalında Saldırı simülasyonu eğitimini kullanabilirsiniz. Saldırı simülasyonu eğitimi henüz GCC Yüksek veya DoD ortamlarında kullanılamaz.

> [!NOTE]
> Saldırı simülasyonu eğitimi, E3 müşterilerine deneme olarak bir özellik alt kümesi sunar. Deneme teklifi, Kimlik Bilgisi Toplama yükünü kullanma ve 'ISA Kimlik Avı' veya 'Kitle Market Kimlik Avı' eğitim deneyimlerini seçme özelliğini içerir. E3 deneme teklifinin parçası başka hiçbir özellik yoktur.

## <a name="simulations"></a>Simülasyon

*Kimlik avı* , güvenilir veya güvenilir gönderenlerden geliyormuş gibi görünen iletilerdeki hassas bilgileri çalmaya çalışan e-posta saldırıları için genel bir terimdir. *Kimlik avı* , _sosyal mühendislik_ olarak sınıflandırdığımız tekniklerin bir alt kümesinin bir parçasıdır.

Saldırı simülasyonu eğitiminde, birden çok sosyal mühendislik tekniği türü mevcuttur:

- **Kimlik bilgisi toplama**: Saldırgan, alıcıya URL içeren bir ileti gönderir. Alıcı URL'ye tıkladığında, genellikle kullanıcıdan kullanıcı adını ve parolasını isteyen bir iletişim kutusu gösteren bir web sitesine yönlendirilir. Genellikle hedef sayfa, kullanıcıya güven oluşturmak için iyi bilinen bir web sitesini temsil edecek şekilde temalıdır.

- **Kötü amaçlı yazılım eki**: Saldırgan, alıcıya ek içeren bir ileti gönderir. Alıcı eki açtığında, saldırganın ek kod yüklemesine veya kendini daha fazla geliştirmesine yardımcı olmak için kullanıcının cihazında rastgele kod (örneğin, bir makro) çalıştırılır.

- **Ekteki bağlantı**: Bu, kimlik bilgisi toplamanın karma bir örneğidir. Saldırgan, alıcıya ekin içinde URL içeren bir ileti gönderir. Alıcı eki açıp URL'ye tıkladığında, genellikle kullanıcıdan kullanıcı adını ve parolasını isteyen bir iletişim kutusu gösteren bir web sitesine yönlendirilir. Genellikle hedef sayfa, kullanıcıya güven oluşturmak için iyi bilinen bir web sitesini temsil edecek şekilde temalıdır.

- **Kötü amaçlı yazılım bağlantısı**: Saldırgan, alıcıya iyi bilinen bir dosya paylaşım sitesindeki bir ekin bağlantısını içeren bir ileti gönderir (örneğin, SharePoint Çevrimiçi veya Dropbox). Alıcı URL'ye tıkladığında, ek açılır ve saldırganın ek kod yüklemesine veya kendisini daha fazla geliştirmesine yardımcı olmak için kullanıcının cihazında rastgele kod (örneğin, bir makro) çalıştırılır.

- **Drive-by-URL**: Saldırgan, alıcıya URL içeren bir ileti gönderir. Alıcı URL'ye tıkladığında arka plan kodunu çalıştırmaya çalışan bir web sitesine yönlendirilir. Bu arka plan kodu, alıcı hakkında bilgi toplamaya veya cihazında rastgele kod dağıtmaya çalışır. Genellikle, hedef web sitesi gizliliği ihlal edilmiş iyi bilinen bir web sitesi veya iyi bilinen bir web sitesinin kopyasıdır. Web sitesi hakkında bilgi sahibi olmak, kullanıcıyı bağlantının tıklandığında güvenli olduğuna ikna etmeye yardımcı olur. Bu teknik bir _sulama deliği saldırısı_ olarak da bilinir.

> [!NOTE]
> Url'yi bir kimlik avı kampanyasında kullanmadan önce desteklenen web tarayıcılarınızda sanal kimlik avı URL'sinin kullanılabilirliğini denetleyin. Bu simülasyon URL'lerine her zaman izin vermek için birçok URL saygınlığı satıcısıyla çalışsak da, her zaman tam kapsama alanımız yoktur (örneğin, Google Kasa Gözatma). Çoğu satıcı, belirli URL'lere (örneğin, <https://support.google.com/chrome/a/answer/7532419>) her zaman izin vermenize olanak tanıyan yönergeler sağlar.

Saldırı simülasyonu eğitimi tarafından kullanılan URL'ler aşağıdaki listede açıklanmıştır:

- <https://www.mcsharepoint.com>
- <https://www.attemplate.com>
- <https://www.doctricant.com>
- <https://www.mesharepoint.com>
- <https://www.officence.com>
- <https://www.officenced.com>
- <https://www.officences.com>
- <https://www.officentry.com>
- <https://www.officested.com>
- <https://www.prizegives.com>
- <https://www.prizemons.com>
- <https://www.prizewel.com>
- <https://www.prizewings.com>
- <https://www.shareholds.com>
- <https://www.sharepointen.com>
- <https://www.sharepointin.com>
- <https://www.sharepointle.com>
- <https://www.sharesbyte.com>
- <https://www.sharession.com>
- <https://www.sharestion.com>
- <https://www.templateau.com>
- <https://www.templatent.com>
- <https://www.templatern.com>
- <https://www.windocyte.com>

### <a name="create-a-simulation"></a>Simülasyon oluşturma

Yeni simülasyon oluşturma ve gönderme hakkında adım adım yönergeler için bkz. [Kimlik avı saldırısı simülasyonu](attack-simulation-training.md).

### <a name="create-a-payload"></a>Yük oluşturma

Simülasyonda kullanmak üzere yük oluşturma hakkında adım adım yönergeler için bkz [. Saldırı benzetimi eğitimi için özel yük oluşturma](attack-simulation-training-payloads.md#create-payloads).

### <a name="gaining-insights"></a>İçgörü elde etme

Raporlama ile içgörü elde etme hakkında adım adım yönergeler için bkz [. Saldırı simülasyonu eğitimi aracılığıyla içgörü elde etme](attack-simulation-training-insights.md).

> [!NOTE]
> Saldırı Simülatörü, Kasa Bağlantılar ilkelerindeki **Kullanıcı tıklamalarını izle** ayarı kapatılmış olsa bile, kimlik avı kampanyasının hedeflenen alıcılarına gönderilen yük iletisindeki URL'nin tıklama verilerini güvenli bir şekilde izlemek için Office 365 için Defender Kasa Bağlantıları kullanır.
