---
title: Microsoft Defender'ı Uç nokta dağıtımı için hazırlama
description: Uç Nokta için Microsoft Defender'ın dağıtımı için paydaş onayını, zaman çizelgelerini, ortamın dikkate alınacak noktalarını ve benimseme siparişlerini hazırlama
keywords: dağıtma, hazırlama, paydaş, zaman çizelgesi, ortam, uç nokta, sunucu, yönetim, benimseme
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 29f9aabf2c0345e46123ba76869718c15d8d1885
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019492"
---
# <a name="prepare-microsoft-defender-for-endpoint-deployment"></a>Microsoft Defender'ı Uç nokta dağıtımı için hazırlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender'ın Dağıtımı üç aşamalı bir işlemdir:

|![dağıtım aşaması - hazırlama.](images/phase-diagrams/prepare.png)<br>Aşama 1: Hazırlama|[![dağıtım aşaması - kurulum](images/phase-diagrams/setup.png)](production-deployment.md)<br>[Aşama 2: Kurulum](production-deployment.md)|[![dağıtım aşaması - ekleme](images/phase-diagrams/onboard.png)](onboarding.md)<br>[Aşama 3: Ekleme](onboarding.md)|
|---|---|---|
|*Buradasınız!*|||

Şu anda hazırlık aşamasındayız.

Hazırlık, başarılı bir dağıtım için çok önemli. Bu makalede, Uç Nokta için Defender'ı dağıtırken göz önünde bulundurarak düşünmeniz gereken noktalara yönlendirildiniz.

## <a name="stakeholders-and-approval"></a>Paydaşlar ve onay

Aşağıdaki bölüm, projede yer alan ve onaylaması, gözden geçirmesi veya bilgi sahibi olması gereken tüm paydaşları tanımlamak için hizmet vermektedir.

Aşağıdaki tabloya organizasyonunıza uygun olarak proje katılımcıları ekleyin.

- SO = Projeyi onayla
- R = Bu projeyi gözden geçirme ve girdi sağlama
- I = Bu proje hakkında bilgi verildi

<br>

****

|Name|Rol|Eylem|
|---|---|---|
|Ad ve e-posta girin|**Baş Bilgi Güvenliği Görevlisi (CISO)** *Yeni teknoloji dağıtımı için kuruluş içinde sponsor olarak hizmet veren bir yönetim temsilcisi.*|SO|
|Ad ve e-posta girin|**Siber Savunma Operasyon Merkezi (CDOC)** Genel Müdürü BU değişikliğin müşteriler güvenlik işlemleri ekibinde bulunan süreçlerle nasıl hizalı olduğunu tanımlamaktan sorumlu *CDOC ekibinden bir temsilci.*|SO|
|Ad ve e-posta girin|**Güvenlik** *Mimarı Bu değişikliğin kuruluşta temel* Güvenlik mimarisiyle nasıl uyumlu olduğunu tanımlamaktan sorumlu Güvenlik ekibinden bir temsilci.|R|
|Ad ve e-posta girin|**workplace Architect** *A representative from IT team of defining how of the this change is aligned with the core workplace architecture in organization.*|R|
|Ad ve e-posta girin|**Güvenlik Analisti** CDOC ekibinin algılama özellikleri, kullanıcı deneyimi ve bu değişikliğin genel kullanışlılığıyla ilgili girdileri güvenlik işlemleri açısından sağlayacak *bir temsilci.*|I|
||||

## <a name="environment"></a>Ortam

Bu bölüm, proje katılımcılarının ortamınızı derinlemesine anladığını ve teknolojiler ve süreçlerde gerekli olan olası bağımlılıkları ve/veya değişiklikleri belirlemeye yardımcı olduğundan emin olmak için kullanılır.

<br>

****

|Nedir?|Açıklama|
|---|---|
|Uç nokta sayısı|İşletim sistemine göre uç noktaların toplam sayısı.|
|Sunucu sayısı|İşletim sistemi sürümüne göre Sunucuların toplam sayısı.|
|Yönetim altyapısı|Yönetim altyapısı adı ve sürümü (örneğin, Geçerli System Center Configuration Manager 1803).|
|CDOC dağıtımı|Yüksek düzey CDOC yapısı (örneğin, Contoso'ya sağlanan Katman 1, Avrupa ve Asya genelinde dağıtılan Katman 2 ve Katman 3'ü evde).|
|Güvenlik bilgileri ve olay (SIEM)|SIEM teknolojisi kullanımda.|
|||

## <a name="role-based-access-control"></a>Rol tabanlı erişim denetimi

Microsoft, en az ayrıcalıklar kavramının kullanılması önerisindedir. Uç Nokta için Defender, uygulama içindeki yerleşik Azure Active Directory. Microsoft, [kullanılabilen farklı rolleri gözden geçirmenizi ve](/azure/active-directory/roles/permissions-reference) bu uygulamanın her bir kişilik için ihtiyaçlarınızı çözmek için doğru rolleri seçmenizi önerir. Dağıtım tamamlandıktan sonra bazı rollerin geçici olarak uygulanması ve kaldırılması gerekiyor olabilir.

<br>

****

|Kişilikler|Roller|Azure AD Rolü (gerekiyorsa)|Ata|
|---|---|---|---|
|Güvenlik Yöneticisi||||
|Güvenlik Analisti||||
|Uç Nokta Yöneticisi||||
|Altyapı Yöneticisi||||
|İş Sahibi/Proje Katılımcısı||||
|

Microsoft, dizin [izinlerine Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) ek denetim, denetim ve erişim incelemesi sağlamak için rollerinizi yönetmek için Privileged Identity Management'in kullanılması önerilir.

Uç Nokta için Defender izinleri yönetmek için iki yolu destekler:

- **Temel izin yönetimi**: İzinleri tam erişim veya salt okunur olarak ayarlayın. Aynı kuruluşta Genel Yönetici veya Güvenlik Yöneticisi Azure Active Directory kullanıcılar tam erişime sahip olabilir. Güvenlik okuyucusu rolü salt okunur erişime sahiptir ve makineleri/cihaz envanterini görüntüleme iznine sahip değildir.

- **Rol tabanlı erişim denetimi (RBAC)**: Rolleri tanımlayarak, Azure AD kullanıcı gruplarını rollere ataarak ve kullanıcı gruplarına cihaz gruplarına erişim ataarak ayrıntılı izinleri ayarlayın. Daha fazla bilgi için. Bkz [. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).

Microsoft, yalnızca işletme gerekçelendirmesi olan kullanıcıların Uç Nokta için Defender'a erişemelerini sağlamak için RBAC'den yararlanarak çalışmanız önerilir.

İzin yönergeleriyle ilgili ayrıntıları burada bulabilirsiniz: [Rol oluşturma ve rolü bir grup için Azure Active Directory attayabilirsiniz](/microsoft-365/security/defender-endpoint/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group).

Aşağıdaki örnek tablo, ortamınız için gereken RBAC yapısını belirlemenize yardımcı olacak Siber Savunma Operasyon Merkezi yapısını tanımlamak için hizmet vermektedir.

<br>

****

|Katman|Açıklama|İzin Gerekli|
|---|---|---|
|Katman 1|**Yerel güvenlik işlemleri ekibi / IT ekibi** <p> Bu ekip genellikle coğrafi konum içindeki uyarıları önceler ve araştırır ve etkin bir düzeltmenin gerekli olduğu durumlarda Katman 2'ye ilerler.||
|Katman 2|**Bölgesel güvenlik işlemleri ekibi** <p> Bu ekip bölge için tüm cihazları görebilir ve düzeltme eylemleri gerçekleştirebilirsiniz.|Verileri görüntüleme|
|Katman 3|**Global güvenlik işlemleri ekibi** <p> Bu ekip güvenlik uzmanlarından oluşur ve portaldan tüm eylemleri görmeye ve gerçekleştirmeye yetkilidir.|Verileri görüntüleme <p> Uyarılar araştırma Etkin düzeltme eylemleri <p> Uyarılar araştırma Etkin düzeltme eylemleri <p> Portal sistem ayarlarını yönetme <p> Güvenlik ayarlarını yönetme|
||||

## <a name="adoption-order"></a>Benimseme Sırası

Birçok durumda, kuruluşlarda mevcut uç nokta güvenlik ürünleri yerlerinde olur. Her kuruluşun korumasız en az bir virüsten koruma çözümü olması gerekir. Ancak bazı durumlarda, bir kuruluş zaten EDR çözüme sahip olabilir.

Geçmişten bu kadar yoğun zamanı olan ve uygulama katmanı ve altyapı bağımlılıklarına bağlı sıkı bağımlılıklar nedeniyle elde etmek zor olan tüm güvenlik çözümlerini değiştiriyor. Bununla birlikte, işletim sisteminde Uç Nokta için Defender yerleşik olarak olduğundan, üçüncü taraf çözümlerin yerini almak artık çok kolay.

Kullanılacak Uç Nokta için Defender bileşenini seçin ve uygun olanları kaldırın. Aşağıdaki tabloda, Microsoft'un uç nokta güvenlik paketinin nasıl etkinleştirilmelidir için öneride olduğu gösterilmiştir.

<br>

****

|Bileşen|Açıklama|Benimseme Sırası Sırası|
|---|---|---|
|Uç Nokta & Yanıtı (EDR)|Uç nokta ve uç noktada algılama ve yanıtlama için Defender, gerçek zamanlı olarak yakın olan ve işlemlebilir gelişmiş saldırı algılamaları sağlar. Güvenlik analistleri uyarıları etkili bir şekilde önceliklendirmek, ihlallerin tam kapsamı için görünürlük kazanmak ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirmektedir. <p> [Daha fazla bilgi edinin.](/windows/security/threat-protection/windows-defender-atp/overview-endpoint-detection-response)|1|
|Tehdit & Güvenlik Açığı Yönetimi (TVM)|Tehdit & Güvenlik Açığı Yönetimi, Uç Nokta için Microsoft Defender'ın bir bileşenidir ve hem güvenlik yöneticilerine hem de güvenlik işlemleri ekiplerine aşağıdakiler gibi benzersiz değer sağlar: <ul><li>Uç nokta güvenlik uç noktada algılama ve yanıtlama ilişkili EDR öngörüler (EDR) öngörüleri</li><li>Olay soruşturmaları sırasında paha biçilemez cihaz güvenlik açığı bağlamı</li><li>Microsoft Intune ve Microsoft System Center Configuration Manager aracılığıyla yerleşik düzeltme System Center Configuration Manager</li></ul> <p> [Daha fazla bilgi edinin](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Introducing-a-risk-based-approach-to-threat-and-vulnerability/ba-p/377845).|2|
|Yeni nesil koruma (NGP)|Microsoft Defender Virüsten Koruma, masaüstü bilgisayarlar, taşınabilir bilgisayarlar ve sunucular için yeni nesil koruma sağlayan yerleşik bir kötü amaçlı yazılımdan koruma çözümüdür. Microsoft Defender Virüsten Koruma şunları içerir: <ul><li>Yeni ve ortaya çıkan tehditlerin neredeyse anında algılanması ve engellenmesi için bulut teslimi koruması. Makine öğrenimi ve Akıllı Güvenlik Graph ile bulut teslimi koruma, öğrenme ve korumanın desteklendiği yeni nesil teknolojilerin Microsoft Defender Virüsten Koruma.</li><li>Gelişmiş dosya ve süreç davranışı izleme ve diğer heuristics kullanarak taramada her zaman açık ("gerçek zamanlı koruma" olarak da bilinir).</li><li>Makine öğrenimi, insan ve otomatik büyük veri çözümlemelerine ve derinlemesine tehdit direnci araştırmalarına dayalı özel koruma güncelleştirmeleri.</li></ul> <p> [Daha fazla bilgi edinin](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10).|3|
|Saldırı Yüzeyini Azaltma (ASR)|Uç Nokta için Microsoft Defender'daki saldırı yüzeyini azaltma özellikleri, kuruluşta yeni ve ortaya çıkan tehditlere karşı korunmasına yardımcı olur. <br> [Daha fazla bilgi edinin.](/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction)|4|
|Düzeltme & (AIR) Otomatik İnceleme|Uç Nokta için Microsoft Defender Otomatik soruşturmalar'ı kullanarak tek tek araştırılması gereken uyarı ses düzeyini önemli ölçüde azaltır. Otomatik araştırma özelliği, çeşitli denetim algoritmalarını ve analistlerin (playbooks gibi) uyarıları incelemek ve ihlalleri çözmek için hemen düzeltme işlemleri yapmak için kullandığı süreçlerden faydalanr. Bu durum uyarı hacmini önemli ölçüde azaltarak güvenlik işlem uzmanlarının daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak verir. <p> [Daha fazla bilgi edinin.](/windows/security/threat-protection/windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection)|Uygulanamaz|
|Microsoft Tehdit Uzmanları (MTE)|Microsoft Tehdit Uzmanları, benzersiz ortamlarındaki kritik tehditlerin atlamaması için uzman düzeyinde izleme ve çözümleme özelliklerine sahip Güvenlik İşlem Merkezleri (SOC) sağlayan, yönetilen bir arama hizmetidir. <p> [Daha fazla bilgi edinin.](/windows/security/threat-protection/windows-defender-atp/microsoft-threat-experts)|Uygulanamaz|

## <a name="next-step"></a>Sonraki adım

![Aşama 2: Kurulum.](images/setup.png) <br> [Aşama 2: Kurulum](production-deployment.md)

Uç nokta dağıtımı için Microsoft Defender'ı ayarlayın.
