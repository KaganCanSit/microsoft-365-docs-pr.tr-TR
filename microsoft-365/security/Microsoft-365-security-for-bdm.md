---
title: Microsoft 365 İş İçin Güvenlik Karar Alıcıları (BDM)
description: Kuruluşların şu anda Microsoft 365 ortamları için karşı karşıya kaldığı en yaygın tehdit ve saldırı senaryoları ve bu riskleri azaltmak için önerilen eylemler.
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.openlocfilehash: 6a961e3d2740809eb4f3c0741277ef267db1b9ee
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935335"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 İş İçin Güvenlik Karar Alıcıları (BDM)

Bu makalede, kuruluşların şu anda Microsoft 365 ortamlarında karşılaştığı en yaygın tehdit ve saldırı senaryolarından bazıları ve bu riskleri azaltmak için önerilen eylemler ele alınmaktadır. Microsoft 365 çok çeşitli önceden yapılandırılmış güvenlik özellikleriyle birlikte gelse de, müşteri olarak bulut hizmetlerine erişmek için kullanılan kendi kimliklerinizin, verilerinizin ve cihazlarınızın güvenliğini sağlama sorumluluğunu üstlenmenizi gerektirir. Bu kılavuz Kozeta Beam (Microsoft Bulut Güvenliği Mimarı) ve Thiagaraj Sundararajan (Microsoft Kıdemli Danışmanı) tarafından geliştirilmiştir.

Bu makale, kiracınız, e-postanız ve SharePoint gibi en kritik hizmetleri ve varlıkları yönetmek için kullanılan hesapların korunmasından başlayarak çalışma önceliğine göre düzenlenmiştir. Güvenliğe yaklaşmak için yöntemsel bir yol sağlar ve kuruluşunuzdaki paydaşlar ve ekiplerle ilerleme durumunuzu izleyebilebilmeniz için aşağıdaki elektronik tabloyla birlikte çalışır: [BDM'ler elektronik tablosu için güvenlik Microsoft 365](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Microsoft 365 BDM güvenlik önerisi spreadhsheet örneği" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Microsoft, normal etkinliklerinize göre güvenlik duruşunuzu otomatik olarak analiz etmek, puan atamak ve güvenlik iyileştirme önerileri sağlamak için kiracınızdaki Güvenli Puan aracını sağlar. Bu makalede önerilen eylemleri gerçekleştirmeden önce geçerli puanınızı ve önerilerinizi not alın. Bu makalede önerilen eylemler puanınızı artıracaktır. Amaç, maksimum puanı elde etmek değil, ortamınızı kullanıcılarınız için üretkenliği olumsuz etkilemeyecek şekilde koruma fırsatlarının farkında olmaktır. Bkz. [Microsoft Güvenli Puanı](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="İşletmenize yönelik riskleri azaltma adımları" lightbox="../media/security/security-for-bdms-overview.png":::

Başlamadan önce bir şey daha. . . [denetim günlüğünü açtığınızdan](../compliance/search-the-audit-log-in-security-and-compliance.md) emin olun. Bir olayı veya ihlali araştırmanız gerektiğinde bu verilere daha sonra ihtiyacınız olacaktır.

## <a name="protect-privileged-accounts"></a>Ayrıcalıklı hesapları koruma

İlk adım olarak, bu hesapların kritik hizmetleri ve kaynakları yönetme ve değiştirme izinlerine sahip olması nedeniyle ortamdaki kritik hesaplara ek bir koruma katmanı verilmesini öneririz; bu da güvenliğin aşılması durumunda kuruluşun tamamını olumsuz etkileyebilir. Ayrıcalıklı hesapların korunması, güvenliği aşılmış bir hesabın izinlerini yönetim hesabına yükseltmeye çalışan bir saldırgana karşı korumanın en etkili yollarından biridir.

|Öneri  |E3 |E5  |
|---------|---------|---------|
|Tüm yönetim hesapları için çok faktörlü kimlik doğrulamasını (MFA) zorunlu kılma.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|Azure AD ve Azure kaynaklarına tam zamanında ayrıcalıklı erişim uygulamak için Azure Active Directory (Azure AD) Privileged Identity Management (PIM) uygulayın. Ayrıca kimlerin erişimi olduğunu keşfedebilir ve ayrıcalıklı erişimi gözden geçirebilirsiniz.|         | ![yeşil onay işareti.](../media/green-check-mark.png)|
|Office 365 ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim denetimini yönetmek için ayrıcalıklı erişim yönetimi uygulayın. |         | ![yeşil onay işareti.](../media/green-check-mark.png)|
|Hizmetleri yönetmek için Privileged Access Workstations'ı (PAW) yapılandırın ve kullanın. İnternet'e göz atmak ve yönetim hesabınızla ilgili olmayan e-postaları denetlemek için aynı iş istasyonlarını kullanmayın.|  !![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)::: |

Aşağıdaki diyagramda bu özellikler gösterilmektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="Ayrıcalıklı hesapları korumak için önerilen özellikler" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Ek öneriler:

- Şirket içinden eşitlenen hesaplara bulut hizmetleri için yönetici rolleri atanmadığından emin olun. Bu, bir saldırganın bulut hizmetlerine yönetim erişimi elde etmek için şirket içi hesapları uygulamasını önlemeye yardımcı olur.
- Hizmet hesaplarına yönetici rolleri atanmadığından emin olun. Bu hesaplar genellikle izlenmez ve süresi dolmayan parolalarla ayarlanır. AADConnect ve ADFS hizmetleri hesaplarının varsayılan olarak Genel Yönetici olmadığından emin olarak başlayın.
- Yönetici hesaplarından lisansları kaldırın. Belirli yönetici hesaplarına lisans atamak için belirli bir kullanım örneği yoksa, bu hesaplardan lisansları kaldırın.

## <a name="reduce-the-surface-of-attack"></a>Saldırı yüzeyini azaltma

Bir sonraki odak alanı saldırı yüzeyini azaltmaktır. Bu, kullanıcılarınız ve hizmetleriniz üzerinde çok az çaba ve etkiyle gerçekleştirilebilir. Saldırının yüzey alanını azaltarak, saldırganların kuruluşunuza karşı saldırı başlatmak için daha az yolu vardır.

İşte birkaç örnek:

- POP3, IMAP ve SMTP protokollerini devre dışı bırakın. Modern kuruluşların çoğu artık bu eski protokolleri kullanmıyor. Bunları güvenli bir şekilde devre dışı bırakabilir ve yalnızca gerektiğinde özel durumlara izin vekleyebilirsiniz.
- Kiracıdaki Genel Yönetici sayısını azaltın ve gereken en düşük düzeyde tutun. Bu, tüm Bulut uygulamaları için saldırının yüzey alanını doğrudan azaltır.
- Ortamınızda artık kullanılmayan sunucuları ve uygulamaları devre dışı bırakın.
- Artık kullanılmayan hesapları devre dışı bırakmak ve silmek için bir işlem uygulayın.

## <a name="protect-against-known-threats"></a>Bilinen tehditlere karşı koruma

Bilinen tehditler kötü amaçlı yazılım, güvenliği aşılmış hesaplar ve kimlik avıdır. Bu tehditlere karşı bazı korumalar kullanıcılarınızı doğrudan etkilemeden hızlı bir şekilde uygulanabilirken, diğerleri daha fazla planlama ve kullanıcı eğitimi gerektirir.

|Öneri  |E3  |E5  |
|---------|---------|---------|
|**Çok faktörlü kimlik doğrulamasını ayarlayın ve oturum açma riski ilkeleri de dahil olmak üzere önerilen koşullu erişim ilkelerini kullanın**. Microsoft, Office 365 ve Microsoft 365 hizmetleri dahil olmak üzere tüm bulut uygulamalarını korumak için birlikte çalışan bir dizi ilkeyi önerir ve test eder. Bkz. [Kimlik ve cihaz erişim yapılandırmaları](./office-365-security/microsoft-365-policies-configurations.md). | |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerektir**. Önerilen koşullu erişim ilkelerini uygulamak için gereken lisansa sahip değilseniz, en azından tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerekir.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Postadaki kötü amaçlı yazılımlara karşı koruma düzeyini yükseltin**. Office 365 veya Microsoft 365 ortamınız kötü amaçlı yazılımlara karşı koruma içerir, ancak kötü amaçlı yazılımlarda yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek bu korumayı artırabilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**E-postanızı hedeflenen kimlik avı saldırılarına karşı koruyun**. Office 365 veya Microsoft 365 ortamınız için bir veya daha fazla özel etki alanı yapılandırdıysanız, hedeflenen kimlik avı koruması yapılandırabilirsiniz. Office 365 için Defender bir parçası olan kimlik avı koruması, kuruluşunuzun kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarına ve diğer kimlik avı saldırılarına karşı korunmasına yardımcı olabilir. Özel bir etki alanı yapılandırmadıysanız, bunu yapmanız gerekmez.| |![yeşil onay işareti.](../media/green-check-mark.png)|
|**E-postadaki fidye yazılımı saldırılarına karşı koruma**. Fidye yazılımı dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilerinize erişimi ortadan kaldırır. Daha sonra, verilerinize erişimi geri döndürme karşılığında genellikle Bitcoin gibi kripto para birimleri biçiminde "fidye" isteyerek kurbanlardan para sızdırmaya çalışır. Fidye yazılımı için yaygın olarak kullanılan dosya uzantılarını engellemek veya bu ekleri e-postayla alan kullanıcıları uyarmak için bir veya daha fazla posta akışı kuralı oluşturarak fidye yazılımlarına karşı savunmaya yardımcı olabilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**İş yapmadığınız ülkelerden gelen bağlantıları engelleyin**. Bu ülkelerden gelen bağlantıları engellemek için bir Azure AD koşullu erişim ilkesi oluşturarak kiracınızın çevresinde etkili bir coğrafi güvenlik duvarı oluşturun.| |![yeşil onay işareti.](../media/green-check-mark.png)|

Aşağıdaki diyagramda bu özellikler gösterilmektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="Bilinen tehditlere karşı koruma için önerilen özellikler" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::


## <a name="protect-against-unknown-threats"></a>Bilinmeyen tehditlere karşı koruma

Ayrıcalıklı hesaplarınıza ek korumalar ekledikten ve bilinen saldırılara karşı koruma yaptıktan sonra dikkatinizi bilinmeyen tehditlere karşı korumaya çekin. Daha kararlı ve gelişmiş saldırganlar, kuruluşlara saldırmak için yenilikçi ve yeni, bilinmeyen yöntemler kullanır. Microsoft'un milyarlarca cihaz, uygulama ve hizmet üzerinde toplanan geniş veri telemetrisiyle, Zero-Day saldırılarına karşı önlem almak, kum kutusu ortamlarını kullanmak ve içeriğinize erişime izin vermeden önce geçerliliği denetlemek için Windows, Office 365 ve Azure'da Office 365 için Defender gerçekleştirebiliriz.

|Öneri  |E3  |E5  |
|---------|---------|---------|
|**Office 365 için Microsoft Defender yapılandırma**:<br>*Kasa Ekleri<br>* Kasa Bağlantıları    <br>Office 365 için Defender korumasında kimlik avı önleme *SharePoint, OneDrive ve Microsoft Teams<br> için* Uç Nokta için Microsoft Defender|         |![yeşil onay işareti.](../media/green-check-mark.png) |
|**Uç Nokta için Microsoft Defender özelliklerini yapılandırma**:<br>*<br>Windows Defender Virüsten Koruma* Exploit protection <br> *Saldırı yüzeyini azaltma <br>*    Donanım tabanlı yalıtım <br>* Denetimli klasör erişimi     |         |![yeşil onay işareti.](../media/green-check-mark.png) |
|SaaS uygulamalarını keşfetmek ve davranış analizini ve anomali algılamayı kullanmaya başlamak için **Microsoft Defender for Cloud Apps kullanın**. |         |![yeşil onay işareti.](../media/green-check-mark.png) |

Aşağıdaki diyagramda bu özellikler gösterilmektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Bilinmeyen tehditlere karşı korunmak için araçlar tarafından sunulan özelliklere örnek" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::


Ek öneriler:

- TLS kullanan e-postalar gibi iş ortağı kanalı iletişimlerinin güvenliğini sağlama.
- Teams Federasyonu yalnızca iletişim kurabileceğiniz İş Ortaklarına açın.
- İstenmeyen posta ve kötü amaçlı yazılım denetimlerini atlamalarına olanak tanıdığından, gönderen etki alanlarını, tek tek gönderenleri veya kaynak IP'leri izin verilenler listenize eklemeyin. Müşterilerle ortak bir uygulama, izin verilenler listesine e-posta akışı sorunlarının bildirilmiş olabileceği kendi kabul edilen etki alanlarını veya diğer birçok etki alanını eklemektir. İstenmeyen Posta ve Bağlantı Filtreleme listesine etki alanları eklemeyin, bu durum tüm istenmeyen posta denetimlerini atlar.
- Giden istenmeyen posta bildirimlerini etkinleştirme — İç kullanıcılardan herhangi birinin dışarıdan istenmeyen posta e-postaları gönderdiğini bildirmek için Yardım Masası'na veya BT Yöneticisi ekibine dahili olarak bir dağıtım listesine giden istenmeyen posta bildirimlerini etkinleştirin. Bu, hesabın gizliliğinin ihlal edildiğini gösteren bir gösterge olabilir.
- Uzak PowerShell'i tüm kullanıcılar için devre dışı bırakma — Uzak PowerShell, yönetim amacıyla veya programlı API erişimi için hizmetlere erişmek için çoğunlukla Yöneticiler tarafından kullanılır. Yönetici olmayan kullanıcıların erişecekleri bir iş gereksinimi olmadığı sürece keşiften kaçınmaları için bu seçeneği devre dışı bırakmanızı öneririz.
- Microsoft Azure Yönetim portalına yönetici olmayan tüm kullanıcılara erişimi engelleyin. Yöneticiler dışında tüm kullanıcıları engellemek için bir koşullu erişim kuralı oluşturarak bunu gerçekleştirebilirsiniz.

## <a name="assume-breach"></a>İhlal varsay

Microsoft tehditlere ve saldırılara karşı önlem almak için mümkün olan her önlemi alır ancak her zaman "İhlal Varsay" anlayışı altında çalışmanızı öneririz. Bir Saldırgan ortama izinsiz girmeyi başarmış olsa bile ortamdan veri veya kimlik bilgilerini dışarı aktaramadığından emin olmamız gerekir. Bu nedenle Sosyal Güvenlik numaraları, kredi kartı numaraları, diğer kişisel bilgiler ve diğer kurumsal düzeyde gizli bilgiler gibi hassas veri sızıntılarına karşı koruma sağlamanızı öneririz.


|Öneri |E3|E5 |
|---------|---------|---------|
|**Koşullu erişiminizi ve ilgili ilkelerinizi sıfır güven ağı için hedeflerinize uygun olacak şekilde gözden geçirin ve iyileştirin**. Bilinen tehditlere karşı koruma, [bir dizi önerilen ilkenin](./office-365-security/microsoft-365-policies-configurations.md) uygulanmasını içerir. Uygulamalarınızı ve verilerinizi ağınıza erişim elde eden korsanlara karşı koruduğunuzdan emin olmak için bu ilkeleri uygulamanızı gözden geçirin. Windows 10 için önerilen Intune uygulama koruma ilkesi Windows Information Protection (WIP) sağlar. WIP; e-posta, sosyal medya ve genel bulut gibi uygulamalar ve hizmetler aracılığıyla kuruluş verilerinizin yanlışlıkla sızmasına karşı koruma sağlar. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Dış e-posta iletmeyi devre dışı bırakın**. Kullanıcının posta kutusuna erişim elde eden korsanlar, posta kutusunu e-postayı otomatik olarak iletecek şekilde ayarlayarak postanızı çalabilir. Bu, kullanıcının farkındalığı olmadan bile gerçekleşebilir. Bir posta akışı kuralı yapılandırarak bunun olmasını önleyebilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png) |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Anonim dış takvim paylaşımını devre dışı bırakın**. Varsayılan olarak dış anonim takvim paylaşımına izin verilir. Hassas bilgilerin olası sızıntılarını azaltmak için [takvim paylaşımını devre dışı bırakın](/exchange/sharing/sharing-policies/modify-a-sharing-policy).|![yeşil onay işareti.](../media/green-check-mark.png) |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Hassas veriler için veri kaybı önleme ilkelerini yapılandırın**. Kredi kartı numaraları, Sosyal Güvenlik numaraları ve banka hesap numaraları gibi hassas verileri bulmak ve korumak için Güvenlik &amp; Uyumluluk merkezinde bir Microsoft Purview Veri Kaybı Önleme İlkesi oluşturun. Microsoft 365, veri kaybı önleme ilkelerinde kullanabileceğiniz birçok önceden tanımlanmış hassas bilgi türünü içerir. Ortamınız için özel olan hassas veriler için kendi hassas bilgi türlerinizi de oluşturabilirsiniz. |![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Veri sınıflandırma ve bilgi koruma ilkeleri uygulayın**. Duyarlılık etiketleri uygulayın ve bunları hassas verileri sınıflandırmak ve bunlara koruma uygulamak için kullanın. Bu etiketleri veri kaybı önleme ilkelerinde de kullanabilirsiniz. Azure Information Protection etiketlerini kullanıyorsanız, diğer yönetim merkezlerinde yeni etiketler oluşturmaktan kaçınmanızı öneririz.|         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Bulut için Defender Uygulamaları kullanarak üçüncü taraf uygulama ve hizmetlerdeki verileri koruyun**. Salesforce, Box veya Dropbox gibi üçüncü taraf bulut uygulamalarında hassas bilgileri korumak için Bulut için Defender Uygulamaları ilkelerini yapılandırın. Bulut için Defender Uygulamaları ilkelerinde oluşturduğunuz hassas bilgi türlerini ve duyarlılık etiketlerini kullanabilir ve bunları SaaS uygulamalarınıza uygulayabilirsiniz. <br><br>Microsoft Defender for Cloud Apps, çok çeşitli otomatik işlemleri zorunlu kılmanıza olanak tanır. İlkeler sürekli uyumluluk taramaları, yasal eBulma görevleri, genel olarak paylaşılan hassas içerik için DLP ve daha fazlasını sağlayacak şekilde ayarlanabilir. Bulut için Defender Uygulamalar, 20'den fazla meta veri filtresine (erişim düzeyi, dosya türü gibi) göre herhangi bir dosya türünü izleyebilir. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**[Uç Nokta için Microsoft Defender'ı](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) kullanarak kullanıcıların hassas bilgileri Windows cihazlarında depolayamadığını belirleyin**. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Sunucular ve dosya paylaşımları arasında bilgileri tanımlamak ve sınıflandırmak için [AIP Tarayıcısı'ni](/azure/information-protection/deploy-aip-scanner) kullanın**. Sonuçları görüntülemek ve uygun eylemleri yapmak için AIP raporlama aracını kullanın.|         |![yeşil onay işareti.](../media/green-check-mark.png)|

Aşağıdaki diyagramda bu özellikler gösterilmektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="Bilinmeyen tehditlere karşı koruma için önerilen özellikler" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::


## <a name="continuous-monitoring-and-auditing"></a>Sürekli izleme ve denetim

Son olarak, Windows ve Cihazlar ile birlikte Microsoft 365 ortamının Sürekli İzleme ve Denetimi, herhangi bir yetkisiz girişi hızla algılayıp düzeltebilmek için kritik öneme sahiptir. Güvenli Puan, Microsoft 365 Defender portalı ve Microsoft Intelligent Graph'ın gelişmiş analizi gibi araçlar kiracınıza çok değerli bilgiler sağlar ve benzersiz tehdit koruması ve algılaması sağlamak için çok büyük miktarlarda tehdit bilgileriyle güvenlik verilerini birbirine bağlar.

|Öneri |E3 |E5 |
|---------|---------|---------|
|**Denetim günlüğünün** açık olduğundan emin olun.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Güvenlik Puanı'nı haftalık olarak gözden geçirin** : Güvenli puan, şirketinizin Güvenlik durumuna erişmek ve Güvenli puan önerilerine göre eylemlerde bulunmanız için merkezi bir konumdur. Bu denetimin haftalık olarak gerçekleştirilmesi önerilir.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Office 365 için Microsoft Defender** araçlarını kullanın:<br>*Tehdit araştırması ve yanıt özellikleri<br>*    Otomatik araştırma ve yanıt |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Uç Nokta için Microsoft Defender'ın** kullanımı:<br> *[Uç nokta algılama ve yanıt](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br>*    Otomatik araştırma ve düzeltme Güvenli puan <br>*    [Gelişmiş avcılık](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![yeşil onay işareti.](../media/green-check-mark.png)|
|Fidye yazılımlarını, güvenliği aşılmış kullanıcıları veya sahte uygulamaları tanımlamak, yüksek riskli kullanımı analiz etmek ve riski kuruluşunuzla sınırlamak için otomatik olarak düzeltmek için bulut uygulamaları genelinde olağan dışı davranışları algılamak için **Microsoft Defender for Cloud Apps** kullanın.|         |:::image type="content" source="../media/green-check-mark.png" alt-text="Yeşil renkli onay işareti örneği" lightbox="../media/green-check-mark.png":::|
|Ortamınızdaki tehditleri izlemek için **Microsoft Sentinel'i** veya geçerli SIEM aracınızı kullanın. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**[şirket içi Active Directory](/azure-advanced-threat-protection/what-is-atp)** ortamınıza yönelik tehditleri izlemek ve tehditlere karşı korunmak için Kimlik için Microsoft Defender dağıtın.   |         |![yeşil onay işareti.](../media/green-check-mark.png) |
|Hibrit ve bulut iş yüklerindeki tehditleri izlemek için **Bulut için Microsoft Defender** kullanın. Bulut için Microsoft Defender, ücretsiz bir özellik katmanı ve kaynak saatlerine veya işlemlere göre ödenen standart bir özellik katmanı içerir.|         |         |

Aşağıdaki diyagramda bu özellikler gösterilmektedir.

:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="Sürekli izleme ve denetim için önerilen özellikler" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::


En çok önerilen izleme eylemleri:

- **Microsoft Güvenli Puanı'nı haftalık olarak gözden geçirin** : Güvenli puan, kiracınızın güvenlik durumuna erişmek ve en önemli önerilere göre eylemler yapmak için merkezi bir konumdur. Bu denetimin haftalık olarak gerçekleştirilmesi önerilir. Güvenli Puan, Azure AD, Intune, Bulut için Defender Uygulamaları ve Uç Nokta için Microsoft Defender yanı sıra Office 365 önerileri içerir.
- **Riskli oturum açma bilgilerini haftalık olarak gözden geçirme** — Riskli oturum açma bilgilerini haftalık olarak gözden geçirmek için Azure AD yönetim merkezini kullanın. Önerilen kimlik ve cihaz erişim kural kümesi, riskli oturum açma işlemleri için parola değişikliğini zorunlu kılmaya yönelik bir ilke içerir.  
- **En çok kötü amaçlı yazılımları ve kimlik avı kullanan kullanıcıları haftalık olarak gözden geçirin — Kötü amaçlı yazılım ve kimlik** avı ile hedeflenen en önemli kullanıcıları gözden geçirmek ve bu kullanıcıların neden etkilendiğinin kök nedenini bulmak için Office 365 için Microsoft Defender Tehdit Gezgini'ni kullanın.
