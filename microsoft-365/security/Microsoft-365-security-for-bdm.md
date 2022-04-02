---
title: Microsoft 365 Karar Vericileri için Güvenlik (BDM)
description: Şu anda kuruluşların karşılaştığı en yaygın tehdit ve saldırı senaryoları Microsoft 365 risklerin azaltılmasına yönelik önerilen eylemler.
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
ms.openlocfilehash: 59b74fdc13cc21f0266e0f110935f76656827f65
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755180"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 Karar Vericileri için Güvenlik (BDM)

Bu makalede, kuruluşların şu anda en çok karşılaştığı tehdit ve saldırı senaryolarından bazıları açık Microsoft 365 risklerin azaltılmasına yönelik önerilen eylemler ele alınmaktadır. Microsoft 365 önceden yapılandırılmış çok sayıda güvenlik özelliğiyle birlikte gelir, ancak bu aynı zamanda müşteri olarak bulut hizmetlerine erişmek için kullanılan kimliklerinizi, verilerinizi ve cihazlarınızı güvende altına almak için sorumluluk sahibi olmak da gerekir. Bu kılavuz, Sundararajan (Microsoft Kıdemli Danışman) ve Fareta Beam (Microsoft Bulut Güvenlik Mimarı) tarafından geliştirilmiştir.

Bu makale, kiracınız, e-postanız ve kiracınız e-posta gibi en kritik hizmetleri ve varlıkları yönetmek için kullanılan hesapları korumaktan başlayarak, çalışma önceliğe SharePoint. Güvenliğin yaklaşan olması için yöntemli bir yol sağlar ve aşağıdaki elektronik tabloyla birlikte çalışır, böylece organizasyonu genelinde paydaşlar ve ekipler ile ilerlemenizi izleyebilirsiniz: [BDMs elektronik](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx) tablosu için Microsoft 365 güvenliği sağlar.

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Bir BDM güvenlik Microsoft 365 sayfası örneği" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Microsoft, normal etkinliklerinize göre güvenlik nedenlerinizi otomatik olarak çözümlemek, puan atamak ve güvenlik iyileştirme önerileri sağlamak için kiracınız içinde Güvenli Puan aracını size sağlar. Bu makalede önerilen eylemleri gerçekleştirmeden önce, geçerli puanınızı ve önerilerinizi notun. Bu makalede önerilen işlemler puanınızı artıracaktır. En yüksek puanı elde etmek değil, kullanıcılarınız için üretkenliği olumsuz etkilemeden ortamınızı koruma fırsatlarını takip etmektir. [Bkz. Microsoft Güvenli Puan](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Kurumsal portalda iş ortamı koruma önlemleri sağlayan Güvenli Puan Microsoft 365 Defender örneği" lightbox="../media/security/security-for-bdms-overview.png":::

Başlamadan önce bir şey daha var. . . denetim [günlüğünün açık olduğundan emin olun](../compliance/search-the-audit-log-in-security-and-compliance.md). Daha sonra bir olayı veya ihlali araştırmak zorunda olduğunuz durumda bu verilere ihtiyacınız olur.

## <a name="protect-privileged-accounts"></a>Ayrıcalıklı hesapları koruma

İlk adım olarak, ortamdaki kritik hesapların ek bir koruma katmanına sahip olmasını öneririz, çünkü bu hesapların kritik hizmetleri ve kaynakları yönetmesi ve değiştirme izni vardır ve bu da güvenliği ihlal edilirse kuruluşun tamamını olumsuz yönde etkiliyor olabilir. Ayrıcalıklı hesapları korumak, güvenliği tehlikeye atılmış bir hesabın izinlerini yönetime yükseltmek isteyen bir saldırgana karşı korunmanın en etkili yollarındandır.

|Öneri  |E3 |E5  |
|---------|---------|---------|
|Tüm yönetim hesapları için çok faktörlü kimlik doğrulamasını (MFA) zorunlu kılın.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|Azure AD Azure Active Directory Azure Privileged Identity Management bir defalık ayrıcalıklı erişimi uygulamak için bir (Azure AD) hizmeti (PIM) hizmeti kullanın. Ayrıca, kimin erişimi olduğunu keşfeder ve ayrıcalıklı erişimi gözden geçirsiniz.|         | ![yeşil onay işareti.](../media/green-check-mark.png)|
|Aynı konumda yer alan ve ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim denetimlerini yönetmek için ayrıcalıklı erişim Office 365. |         | ![yeşil onay işareti.](../media/green-check-mark.png)|
|Hizmetleri yönetmek için Privileged Access İş Istasyonları'nın (BUN) kullanımını yapılandırarak kullanın. İnternet'e göz atarak ve yönetim hesabınızla ilgili e-postayı kontrol etmek için aynı iş istasyonlarını kullanmayın.|  !![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)::: |

Aşağıdaki diyagramda bu özellikler örnek olarak ve göstermektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="Ayrıcalıklı hesapları koruma araçları tarafından sunulan özelliklere bir örnek" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Ek öneriler:

- Şirket içinde eşitlenen hesaplara bulut hizmetleri için yönetici rolleri atanmaması gerekir. Bu, bir saldırganın bulut hizmetlere yönetici erişimi elde etmek için şirket içi hesapları uygulamasını önlemeye yardımcı olur.
- Hizmet hesaplarına yönetici rolleri atanmaması gerekir. Bu hesaplar çoğunlukla izlenmz ve süresi dolmamış parolalarla ayarlanır. başlangıç olarak AADConnect ve ADFS hizmet hesaplarının varsayılan olarak Genel Yöneticiler olmadığını garanti edin.
- Yönetici hesaplarından lisansları kaldırın. Belirli yönetici hesaplarına lisans atamak için belirli bir kullanım durumu yoksa, bu hesaplardan lisansları kaldırın.

## <a name="reduce-the-surface-of-attack"></a>Saldırının yüzeyini azaltma

Bir sonraki odak alanı saldırının yüzeyini azaltıyor. Bu çabalar, kullanıcılarınız ve hizmetleriniz üzerinde çok az çabayla ve etkiyle gerçek olabilir. Saldırının yüzey alanı azaltarak, saldırganların organizasyona karşı saldırı başlatmanın daha az yolu olur.

İşte birkaç örnek:

- POP3, IMAP ve SMTP protokollerini devre dışı bırak. Modern kuruluşların çoğu artık bu eski protokolleri kullanmaz. Bunları güvenle devre dışı bırakarak yalnızca gerektiğinde özel durumlara izin veabilirsiniz.
- Kiracıda Genel Yöneticilerin sayısını mutlak en düşük düzeyde azaltarak devam edin. Bu işlem, tüm Bulut uygulamaları için saldırının yüzey alanı sayısını doğrudan azaltır.
- Ortamınıza artık kullanılmadan sunucuları ve uygulamaları kullanın.
- Artık kullanılmaan hesapları devre dışı bırakmak ve silmek için bir işlem gerçekleştirin.

## <a name="protect-against-known-threats"></a>Bilinen tehditlere karşı koruma

Bilinen tehditlere kötü amaçlı yazılım, güvenliği ihlal edilmiş hesaplar ve kimlik avı dahildir. Bu tehditlere karşı bazı korumalar kullanıcılarınız üzerinde doğrudan hiçbir etkisi olmayacak şekilde hızlı bir şekilde uygulansa da, diğerleri için daha fazla planlama ve kullanıcı eğitimi gerekir.

|Öneri  |E3  |E5  |
|---------|---------|---------|
|**Çok faktörlü kimlik doğrulamasını ayarlama ve oturum açma riski ilkeleri de içinde olmak üzere önerilen koşullu erişim ilkelerini kullanma**. Microsoft, Office 365 ve Microsoft 365 hizmetleri dahil olmak üzere tüm bulut uygulamalarını korumak için birlikte Office 365 ilkeler önermektedir ve Microsoft 365 vardır. Bkz [. Kimlik ve cihaz erişimi yapılandırmaları](./office-365-security/microsoft-365-policies-configurations.md). | |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerektirir**. Önerilen koşullu erişim ilkelerini uygulamak için gereken lisansa sahip değilsanız, en azından tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerekir.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Postada kötü amaçlı yazılımlara karşı koruma düzeyini yükseltin**. Varsayılan Office 365 veya Microsoft 365 ortamınız kötü amaçlı yazılıma karşı koruma içerir, ancak kötü amaçlı yazılımda yaygın olarak kullanılan dosya türlerine sahip ekleri engelleyerek bu korumayı artırabilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**E-postanızı hedefli kimlik avı saldırılarından koruyun**. Kimlik avı ortamınız veya ortamınız için bir veya daha fazla Office 365 etki Microsoft 365, hedefli kimlik avı korumasını yapılandırabilirsiniz. Office 365 için Defender'ın bir parçası olan Kimlik avı korumaları, organizasyonlarınızı kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarından ve diğer kimlik avı saldırılarından korumaya yardımcı olabilir. Özel etki alanını yapılandırmadınız, bunu yapmak zorunda değilsiniz.| |![yeşil onay işareti.](../media/green-check-mark.png)|
|**E-postada fidye yazılımı saldırılarına karşı koruyun**. Fidye yazılımları, dosyaları şifreleyerek veya bilgisayar ekranlarını kilitleyerek verilerinize erişimi engeller. Ardından, verilerinize erişim geri dönerek genellikle Bitcoin gibi şifreleme şifrelemeleri biçimine sahip "bilgi" istemeleri ile bu paralardan yararlanmaya çalışır. Fidye yazılımında yaygın olarak kullanılan dosya uzantılarını engellemek veya bu ekleri e-postayla alan kullanıcıları uyarmak için bir veya birden çok posta akış kuralı oluşturarak fidye yazılımlarına karşı savunmaya yardımcı olabilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**İş yapmayan ülkelerden gelen bağlantıları engelin**. Bu ülkelerden gelen tüm bağlantıları engellemek ve kiracınız çevresinde etkili bir şekilde coğrafi güvenlik duvarı oluşturmak için bir Azure AD koşullu erişim ilkesi oluşturun.| |![yeşil onay işareti.](../media/green-check-mark.png)|

Aşağıdaki diyagramda bu özellikler örnek olarak ve göstermektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="Farklı türlerin tehditlerine karşı korunmak için araçlar tarafından sunulan çeşitli özelliklere bir örnek" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::

## <a name="protect-against-unknown-threats"></a>Bilinmeyen tehditlere karşı koruma

Ayrıcalıklı hesaplarınıza ek korumalar ekledikten ve bilinen saldırılara karşı korumadan sonra, dikkati bilinmeyen tehditlere karşı korumak üzere shiftin. Ne kadar ileri düzey ve ne kadar ileri düzey desteksa, saldırı kuruluşları için yenilikçi ve yeni bilinmeyen yöntemleri kullanır. Microsoft'un çok büyük miktarda cihaz, uygulama ve hizmet toplanmış veri telemetrisi sayesinde Zero-Day saldırılarını önlemek, kum kutusu ortamlarını kullanmak ve içeriğinize erişime izin başlamadan önce geçerliliği kontrol etmek üzere Windows, Office 365 ve Azure üzerinde Office 365 için Defender'ı gerçekleştirebilirsiniz.

|Öneri  |E3  |E5  |
|---------|---------|---------|
|**Microsoft Defender'ı şu Office 365**:<br>*Kasa Ekle Kasa<br>* Bağlantılar    <br>*kimlik koruması için Defender'da SharePoint, OneDrive ve kimlik Microsoft Teams Uç Noktası<br> için Microsoft* Defender Office 365.|         |![yeşil onay işareti.](../media/green-check-mark.png) |
|**Uç nokta özellikleri için Microsoft Defender'ı yapılandırma**:<br>*<br>Windows Defender Virüsten Koruma* Exploit Protection <br> *Saldırı yüzeyini azaltma <br>*    Donanım tabanlı yalıtım <br>* Denetimli klasör erişimi     |         |![yeşil onay işareti.](../media/green-check-mark.png) |
|**SaaS uygulamalarını keşfetmek ve davranış çözümlemeleri** ile anormal algılamayı kullanmaya başlamak için Bulut Uygulamaları için Microsoft Defender'ı kullanın. |         |![yeşil onay işareti.](../media/green-check-mark.png) |

Aşağıdaki diyagramda bu özellikler örnek olarak ve göstermektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Bilinmeyen tehditlere karşı korunmak için araçlar tarafından sunulan özelliklere bir örnek" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::

Ek öneriler:

- TLS kullanarak e-postalar gibi iş ortağı kanalı iletişimlerini güvenli hale edinin.
- Federasyon Teams yalnızca iletişimde olduğunuz ortaklara açın.
- Gönderen etki alanlarını, tek tek gönderenleri veya kaynak IP'leri izin listesine eklemeyin çünkü bu, istenmeyen postayı ve kötü amaçlı yazılım denetimlerini atlar. Müşterilerde yaygın bir uygulama, kendi kabul edilen etki alanlarını veya diğer birçok etki alanı için e-posta akışı sorunlarının izin listesine bildiriliyor olmasıdır. Etki alanlarını İstenmeyen Posta ve Bağlantı Filtreleme listesine ekleme, bu durumda tüm istenmeyen posta denetimlerini atlar.
- Giden istenmeyen posta bildirimlerini etkinleştirme — Şirket içi kullanıcılardan herhangi biri dışarı istenmeyen posta e-postaları gönder olup olduğunu bildirmesi için Yardım masasına veya IT Yöneticisi ekibine şirket içinde dağıtım listesinde giden istenmeyen posta bildirimlerini etkinleştirin. Bu, hesabın ele geçirildi bir göstergesi olabilir.
- Uzak PowerShell'i tüm kullanıcılar için devre dışı bırakma — Uzak PowerShell daha çok Yöneticiler tarafından yönetim amacıyla veya programlı API erişimi için hizmetlere erişmek için kullanılır. Yönetici olmayan kullanıcıların erişim için bir ticari zorunlulukları olmadığı sürece onay almalarını önlemek için bu seçeneği devre dışı bırakmanız önerilir.
- Microsoft Azure Yönetim portalına erişimi engelin. Bunu, yöneticiler dışında tüm kullanıcıları engellemek için bir koşullu erişim kuralı oluşturarak gerçekleştirebilirsiniz.

## <a name="assume-breach"></a>İhlal olduğu varsay

Microsoft tehditlere ve saldırılara karşı önlemek için mümkün olan her türlü önlemi alırken, her zaman "İhlal Olduğunu Varsay" mindset altında çalışmayı öneririz. Bir Saldırgan ortama izinsiz giriş yapacak olsa bile, ortamdan veri veya kimlik bilgilerini açamıyorlarından emin olamamız gerekir. Bu nedenle Sosyal Güvenlik numaraları, kredi kartı numaraları, diğer kişisel bilgiler ve diğer kurumsal düzeydeki gizli bilgiler gibi hassas veri sızıntılarına karşı korumayı etkinleştirmenizi öneririz.


|Öneri |E3|E5 |
|---------|---------|---------|
|**Sıfır güven ağının hedeflerine uygun hale getirmek için koşullu erişiminizi ve ilgili ilkeleri gözden geçirin ve en iyi duruma getirmek.** Bilinen tehditlere karşı koruma, önerilen bir dizi [ilke uygulama içerir](./office-365-security/microsoft-365-policies-configurations.md). Uygulamalarınızı ve verilerinizi, ağınıza erişimi kazanan korsanlara karşı koruma sağlamak için bu ilkeleri uygulamalarınızı gözden geçirebilirsiniz. Web için önerilen Intune uygulama koruma ilkesi, Windows 10 Koruması'Windows (WIP) etkinleştirir. WIP, e-posta, sosyal medya ve genel bulut gibi uygulamalar ve hizmetler aracılığıyla yanlışlıkla kuruluş verilerinizin sızdır ızdırağına karşı koruma sağlar. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Dış e-posta iletmeyi devre dışı bırakma**. Bir kullanıcının posta kutusuna erişim elde eden bilgisayar korsanları, posta kutusunu otomatik olarak e-postayı iletacak şekilde ayarerek postanızı çalarlar. Bu durum, kullanıcının farkında olmadan bile olabilir. Posta akış kuralı yapılandırarak bunun önüne geçebilirsiniz.|![yeşil onay işareti.](../media/green-check-mark.png) |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Anonim dış takvim paylaşımını devre dışı bırak**. Varsayılan olarak, dış anonim takvim paylaşımına izin verilir. [Hassas bilgilerin olası sızıntılarını](/exchange/sharing/sharing-policies/modify-a-sharing-policy) azaltmak için takvim paylaşımını devre dışı bırak.|![yeşil onay işareti.](../media/green-check-mark.png) |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Hassas veriler için veri kaybı önleme ilkelerini yapılandırma**. Kredi kartı numaraları, Sosyal &amp; Güvenlik numaraları ve banka hesabı numaraları gibi hassas verileri keşfetmek ve korumak için Güvenlik Uyumluluk Merkezinde Veri Kaybını Önleme İlkesi oluşturun. Microsoft 365, veri kaybı önleme ilkelerinde kullanabileceğiniz önceden tanımlanmış birçok hassas bilgi türü içerir. Ortamınıza özel olan hassas veriler için kendi hassas bilgi türlerinizi de oluşturabilirsiniz. |![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Veri sınıflandırma ve bilgi koruma ilkelerini uygulama**. Duyarlılık etiketleri kullanın ve bunları hassas verileri sınıflandırmak ve koruma uygulamak için kullanın. Bu etiketleri veri kaybı önleme ilkesinde de kullanabilirsiniz. Azure Information Protection etiketlerini kullanıyorsanız, diğer yönetim merkezlerinde yeni etiketler oluşturmaktan kaçınmanız önerilir.|         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Bulut Uygulamaları için Defender'ı kullanarak üçüncü taraf uygulama ve hizmetlerde verileri koruyun**. Salesforce, Box veya Diğer Uygulamalar gibi üçüncü taraf bulut uygulamaları genelinde hassas bilgileri korumak için Bulut Uygulamaları için Defender ilkelerini Dropbox. Bulut Uygulamaları için Defender ilkelerinde oluşturduğunuz hassas bilgi türlerini ve duyarlılık etiketlerini kullanabilir ve bunları SaaS uygulamalarınıza uygulayabilirsiniz. <br><br>Bulut Uygulamaları için Microsoft Defender, çok çeşitli otomatik işlemleri zorunlu hale uygulamanize olanak sağlar. İlkeler, sürekli uyumluluk taramaları, yasal eKbulma görevleri, herkesle paylaşılan hassas içerik için DLP ve daha fazlasını sağlamak için ayarlanır. Bulut Uygulamaları için Defender, 20'den fazla meta veri filtresine (örneğin, erişim düzeyi, dosya türü) dayalı olarak her dosya türünü izleyebilir. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Kullanıcıların [hassas bilgileri kendi cihazlarında](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) depolayamalarını belirlemek için Uç Nokta için Microsoft Defender Windows kullanın**. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**[Sunucularda ve dosya paylaşımlarında](/azure/information-protection/deploy-aip-scanner) bilgileri tanımlamak ve sınıflandırmak için AIP Scanner'ı kullanın**. Sonuçları görüntülemek ve uygun eylemler yapmak için AIP raporlama aracını kullanın.|         |![yeşil onay işareti.](../media/green-check-mark.png)|

Aşağıdaki diyagramda bu özellikler örnek olarak ve göstermektedir.
![İhlallere karşı korumak için önerilen özellikler.](../media/m365-security-bdm-illustrations-assume-breach.png)
 :::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="İhlallere karşı koruma için araç tarafından sunulan özelliklere bir örnek" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::

## <a name="continuous-monitoring-and-auditing"></a>Sürekli izleme ve denetim

Son olarak, Windows Microsoft 365 ve Cihazlar ile birlikte Microsoft 365 ortamının Sürekli İzleme ve Denetim'i, tüm izinsizleri hemen algılayabilecek ve düzeltmek için çok önemlidir. Güvenli Puan, Microsoft 365 Defender portalı ve Microsoft Akıllı Graph'in gelişmiş çözümlemesi gibi araçlar kiracınıza çok değerli bilgiler sağlar ve size benzersiz tehdit koruması ve algılama sağlamak için muazzam miktarlarda tehdit zekası ve güvenlik verileriyle bağlantı sağlar.

|Öneri |E3 |E5 |
|---------|---------|---------|
|Denetim **günlüğünün açık** olduğundan emin olun.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|**Güvenli Puanı haftalık olarak gözden** geçirme — Güvenli puan, şirketinizin Güvenlik durumuna erişmek ve Güvenli puan önerilerine dayalı işlemler yapmak için merkezi bir konumtur. Bu denetimi haftalık olarak gerçekleştirmeniz önerilir.|![yeşil onay işareti.](../media/green-check-mark.png)|![yeşil onay işareti.](../media/green-check-mark.png)|
|Diğer **araçlar için Microsoft Defender Office 365** kullanın:<br>*Tehdit soruşturması ve yanıt özellikleri<br>*    Otomatik araştırma ve yanıt |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|Uç Nokta **için Microsoft Defender'ı kullanın**:<br> *[Uç nokta algılama ve yanıt](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br>*    Otomatik araştırma ve düzeltme Güvenli puan <br>*    [Gelişmiş av](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![yeşil onay işareti.](../media/green-check-mark.png)|
|Bulut **Uygulamaları için Microsoft Defender'ı** kullanarak fidye yazılımlarını, güvenliği tehlikeye atılmış kullanıcıları veya uygulamaları belirlemek, yüksek riskli kullanımı çözümlemek ve riski organizasyonum ile sınırlandır etmek için otomatik olarak düzeltmek için bulut uygulamaları genelinde alışılmışın dışında bir davranış algılayın.|         |:::image type="content" source="../media/green-check-mark.png" alt-text="Yeşil renkli onay işareti örneği" lightbox="../media/green-check-mark.png":::|
|**Ortamınız genelinde tehditlere karşı izlemek için Microsoft Sentinel'i** veya geçerli SIEM aracınızı kullanın. |         |![yeşil onay işareti.](../media/green-check-mark.png)|
|**Şirket [içi Active](/azure-advanced-threat-protection/what-is-atp)** Directory ortamınıza yönelik tehditleri izlemek ve bu tehditlere karşı korumak için Identity için Microsoft Defender'ı dağıtın.   |         |![yeşil onay işareti.](../media/green-check-mark.png) |
|Karma **ve bulut iş yüklerinin** tehditlerini izlemek için Bulut için Microsoft Defender'ı kullanın. Bulut için Microsoft Defender, ücretsiz bir özellik katmanı ve kaynak saatleri veya işlemlerine göre ücretli olan standart bir özellik katmanı içerir.|         |         |

Aşağıdaki diyagramda bu özellikler örnek olarak ve göstermektedir.
:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="Tehdit koruması ve algılamayı etkinleştirme araçları tarafından sunulan özelliklere bir örnek" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::

En çok önerilen izleme eylemleri:

- **Microsoft Güvenli Puanı haftalık olarak gözden** geçirme — Güvenli puan, kiracının güvenlik durumuna erişmek ve en iyi önerilere dayalı işlemler yapmak için merkezi bir konumtur. Bu denetimi haftalık olarak gerçekleştirmeniz önerilir. Güvenli Puan, Azure AD, Intune, Bulut Uygulamaları için Defender ve Uç Nokta için Microsoft Defender'ın yanı sıra güvenlik önerilerini Office 365.
- **Riskli oturum açmaları haftalık olarak gözden geçirme** — Riskli oturum açmaları haftalık olarak gözden geçirmek için Azure AD yönetim merkezini kullanın. Önerilen kimlik ve cihaz erişim kuralları, riskli oturum açmalarda parola değişikliğini zorunlu kılınacak bir ilke içerir.  
- **En iyi kötü amaçlı** yazılımları ve kimlik avı kullanıcılarını haftalık olarak gözden geçirme — Office 365 Kötü amaçlı yazılım ve kimlik avı ile en çok hedef alan kullanıcıları gözden geçirmek ve bu kullanıcıların neden etkilendiğinin temel nedenini bulmak için Tehdit Gezgini'ni kullanarak Microsoft Defender'ı kullanın.
