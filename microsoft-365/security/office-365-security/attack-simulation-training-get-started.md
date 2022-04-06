---
title: Kullanmaya başlayın benzetimi eğitimlerini kullanma
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
description: Yöneticiler, Plan 2 kuruluşlarında sanal kimlik avı ve parola saldırılarını çalıştırmak için Saldırı benzetimi Microsoft 365 E5 Office 365 için Microsoft Defender kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 244d0ae912a5cc2dc163b62f44b44877c0318b88
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507421"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Kullanmaya başlayın Saldırı benzetimi eğitimlerini Office 365 için Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Plan** [2 Office 365 için Microsoft Defender için geçerlidir](defender-for-office-365.md)

Kuruluşta Tehdit Microsoft 365 E5 yanıt Microsoft 365 E5 yanıt özelliklerini içeren Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2 [varsa, gerçekçi](office-365-ti.md) saldırı senaryolarını çalıştırmak için Microsoft 365 Defender portalında Saldırı benzetimi eğitimi'ne  Bu sanal saldırılar, gerçek bir saldırı alt çizginizi etkilemeden önce zayıf kullanıcıları tanımlamanıza ve bu kullanıcılara yardımcı olabilir. Daha fazla bilgi edinmek için bu makaleyi okuyun.

> [!NOTE]
> Saldırı benzetimi eğitimi, Tehdit yönetimi Saldırı veya altında bulunan Güvenlik & Uyumluluk Merkezi'nde bulunan **eski** \> Attack Her v1 deneyiminin **yerini** aldı <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Oturum açma Microsoft 365 Defender için, ' gidin<https://security.microsoft.com>. Saldırı benzetimi eğitimi, E-posta **ve işbirliği Saldırı benzetim** \> **eğitimi ile kullanılabilir**. Doğrudan Saldırı benzetimi eğitimine gitmek için kullanın <https://security.microsoft.com/attacksimulator>.

- Farklı abonelikler genelinde Saldırı benzetimi eğitimi'nin kullanılabilirliği hakkında daha fazla Microsoft 365 için bkz[. Office 365 için Microsoft Defender açıklaması.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)

- Bu makaledeki yordamları yerine **Azure Active Directory** önce Bu makalede izinlerin atanmamış olması gerekir. Özellikle, aşağıdaki rollerden birinin üyesi olmak gerekir:
  - **Genel Yönetici**
  - **Güvenlik Yöneticisi**
  - **Saldırı Benzetimi Yöneticileri**<sup>\*</sup>: Saldırı benzetim kampanyaları ile ilgili her yönüyle oluşturun ve yönetin.
  - **Saldırı Yük Yazarı**<sup>\*</sup>: Yöneticinin daha sonra başlat ödey yalnızca saldırı yüklerini oluşturun.

  <sup>\*</sup>Portalda bu role kullanıcı Microsoft 365 Defender şu anda desteklenmiyor.

  Daha fazla bilgi için [portalda İzinler Microsoft 365 Defender veya Yönetici](permissions-microsoft-365-security-center.md) [rolleri hakkında'ya bakın](../../admin/add-users/about-admin-roles.md).

- Saldırı benzetimi eğitimi için ilgili PowerShell cmdlet'leri yoktur.

- Saldırı benzetimi ve eğitimle ilgili veriler, proje hizmetleri için diğer müşteri Microsoft 365 depolanır. Daha fazla bilgi için [Microsoft 365 konumlarını görme.](../../enterprise/o365-data-locations.md) Saldırı benzetimi şu bölgelerde kullanılabilir: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE ve DEU.

  > [!NOTE]
  > NOR, ZAF, ARE ve DEU en son eklemedir. Bildirilen e-posta telemetrisi dışındaki tüm özellikler bu bölgelerde kullanılabilir. Bunu etkinleştirmek için çalışıyoruz ve bildirilen e-posta telemetrisi kullanılabilir olduğunda hemen müşterilerimizi bilgilendireceğiz.

- 15 Haziran 2021'den sonra, Saldırı benzetim eğitimi diğer GCC. Kuruluşta kamu için Office 365 G5 GCC veya Office 365 için Microsoft Defender (Plan 2) varsa, bu makalede açıklandığı gibi organizasyon içinde gerçekçi saldırı senaryoları çalıştırmak için Microsoft 365 Defender portalında Saldırı benzetimi eğitimini kullanabilirsiniz. Saldırı benzetimi eğitimi henüz GCC DoD ortamlarında kullanılamaz.

> [!NOTE]
> Saldırı benzetimi eğitimi, E3 müşterilerine deneme sürümü olarak bir özellik alt kümesi sunar. Deneme teklifi Kimlik Bilgileri Toplama yüklemesini kullanma ve 'ISA Kimlik Avı' veya 'Mass Market Phishing' eğitim deneyimlerini seçme olanağını içerir. E3 deneme tekliflerinin başka bir özelliği yoktur.

## <a name="simulations"></a>Benzetimler

*Kimlik avı* , geçerli veya güvenilir gönderenlerden gelen iletilerde hassas bilgileri çalmaya çalışan e-posta saldırılarının genel bir terimidir. *Kimlik avı* , sosyal mühendislik olarak sınıflandıracak tekniklerden bir alt _kümedir_.

Saldırı benzetimi eğitimi'nde, çeşitli sosyal mühendislik teknik türleri kullanılabilir:

- **Kimlik bilgileri** toplama: Bir saldırgan alıcıya URL içeren bir ileti gönderir. Alıcı URL'ye tıkladığında, normalde kullanıcı adını ve parolasını soran iletişim kutusunu gösteren bir web sitesine gönderilir. Normalde, hedef sayfa, kullanıcıya güveni oluşturmak amacıyla iyi bilinen bir web sitesini temsil edecek şekilde sıralanmaktadır.

- **Kötü amaçlı** yazılım eki: Bir saldırgan alıcıya ek içeren bir ileti gönderir. Alıcı eki açtığında, saldırganin ek kod yüklemelerine yardımcı olmak veya kendi güvenliklerini daha fazla sürek için kullanıcının cihazında rastgele kod (örneğin bir makro) çalıştırabilirsiniz.

- **Ekin bağlantısı**: Bu, kimlik bilgisi toplama karma bir ürün. Bir saldırgan alıcıya ekin içinde URL içeren bir ileti gönderir. Alıcı eki açtığında ve URL'ye tıkladığında, normalde kullanıcıdan kullanıcı adını ve parolasını isteyen bir iletişim kutusu gösteren bir web sitesine gönderilir. Normalde, hedef sayfa, kullanıcıya güveni oluşturmak amacıyla iyi bilinen bir web sitesini temsil edecek şekilde sıralanmaktadır.

- **Kötü amaçlı yazılım** bağlantısı: Bir saldırgan, alıcıya iyi bilinen bir dosya paylaşım sitesinde (örneğin, SharePoint Online veya Dropbox) ekin bağlantısını içeren bir ileti gönderir. Alıcı URL'ye tıkladığında, ek açılır ve kullanıcının cihazında rastgele kod (örneğin bir makro) çalıştırarak saldırganın ek kod yüklemelerine yardımcı olur veya kendilerinin daha fazla yer açmasına yardımcı olur.

- **Drive-by-url**: Bir saldırgan alıcıya URL içeren iletiler gönderir. Alıcı URL'ye tıkladığında, arka plan kodunu çalıştırmaya çalışan bir web sitesine gönderilir. Bu arka plan kodu, alıcı hakkında bilgi toplamaya veya cihazına rastgele kod dağıtmaya çalışır. Normalde, hedef web sitesi güvenliği tehlikeye atılmış veya iyi bilinen bir web sitesinin kopyası olarak bilinen bir web sitesidir. Web sitesini tanımanız, kullanıcıya bağlantının tıklayabilirsiniz konusunda ikna  olduğuna yardımcı olur. Bu teknik, su delikli _saldırı olarak da bilinir_.

> [!NOTE]
> Kimlik avı kampanyasında URL'yi kullanmadan önce, desteklenen web tarayıcıları içinde sanal kimlik avı URL'sinin kullanılabilir olup olmadığını kontrol edin. Birçok URL itibarı satıcıyla birlikte çalışırken bu benzetim URL'lerine her zaman izin vermemiz gerekir, ancak her zaman tam kapsamımız yok (örneğin, Google Kasa Gözatma). Çoğu satıcı, belirli URL'lere (örneğin, ) her zaman izin verme konusunda yol gösterir <https://support.google.com/chrome/a/answer/7532419>.

Saldırı benzetimi eğitimi tarafından kullanılan URL'ler aşağıdaki listede açıklanmıştır:

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

### <a name="create-a-simulation"></a>Benzetim oluşturma

Yeni benzetim oluşturma ve göndermeyle ilgili adım adım yönergeler için bkz. Kimlik avı [saldırılarını benzetimini kullanma](attack-simulation-training.md).

### <a name="create-a-payload"></a>Yük oluşturma

Bir benzetim içinde kullanmak üzere nasıl yük oluştur adım adım yönergeler için bkz. Saldırı benzetimi eğitimi [için özel bir yük oluşturma](attack-simulation-training-payloads.md).

### <a name="gaining-insights"></a>Öngörü kazanma

Raporlamayla nasıl öngörü kazanıla ilgili adım adım yönergeler için bkz. Saldırı [benzetim eğitimi aracılığıyla öngörüler kazanma](attack-simulation-training-insights.md).

> [!NOTE]
> Saldırı Saldırıları, Office 365 için Defender'te Kullanıcı tıklaymalarını izle ayarı kapalı olsa bile, bir kimlik avı kampanyasının hedefli alıcılarına gönderilen yükleme iletisinde URL'nin tıklama verilerini güvenli bir şekilde izlemek için Kasa Kasa Bağlantıları  kullanır.
