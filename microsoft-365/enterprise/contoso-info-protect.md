---
title: Contoso Corporation için bilgi koruması
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'un, dijital varlıklarının buluttaki güvenliğini Microsoft 365 için Kurumsal'daki bilgi koruma özelliklerini nasıl kullandığını anlıyoruz.
ms.openlocfilehash: 1dff2cadd5afa66b3b469a2debedddbb347db0e5
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63007219"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Contoso Corporation için bilgi koruması

Contoso, bilgi güvenliği konusunda ciddidir. Ürün tasarımlarını ve mülkiyeti üretim tekniklerini tanımlayan fikri mülkiyetin sızıntısını veya gizli kalmaları, bu ürünleri rekabetçi bir dezavantaja zorlar.

Contoso, hassas dijital varlıklarını buluta taşımadan önce, şirket içi bilgi sınıflandırma ve koruma gereksinimlerini kurumsal hizmetlere ilişkin bulut tabanlı Microsoft 365 emin olmak için aldı.

## <a name="contoso-data-security-classification"></a>Contoso veri güvenliği sınıflandırması

Contoso verileriyle ilgili bir çözümleme gerçekleştirdi ve aşağıdaki sınıflandırma düzeylerini belirledi.

| Düzey 1: Temel | Düzey 2: Hassas | Düzey 3: Son derece düzenlemeye tabi |
|:-------|:-----|:-----|
| Veriler şifrelenir ve yalnızca kimliği doğrulanmış kullanıcılar tarafından kullanılabilir.<BR> <BR> Şirket içinde ve bulut tabanlı depolama ve iş yüklerinde depolanan tüm veriler için sağlanır. Veriler hizmette yer alırken ve hizmet ile istemci cihazları arasında iletilirken şifrelenir. <BR><BR>Düzey 1 verilerine örnek olarak, yönetim, satış ve destek çalışanları için normal iş iletişimleri (e-posta) ve dosyalar örnek olarak verilmiştir. | Düzey 1'in yanı sıra güçlü kimlik doğrulama ve veri kaybına karşı koruma.<BR> <BR> Güçlü kimlik doğrulaması, SMS doğrulamasına sahip Azure AD Multi-Factor Authentication'i (MFA) içerir. Veri kaybını önleme özelliği hassas veya kritik bilgilerin Microsoft bulutu dışına çıkarılamamalarını sağlar.<BR><BR>Düzey 2 verilerine örnek olarak, yeni ürünler için finansal ve yasal bilgiler, araştırma ve geliştirme verileri örnek olarak verilmiştir. | Düzey 2'nin yanı sıra en yüksek şifreleme, kimlik doğrulama ve denetim düzeyleri.<BR><BR>Akıllı kartlarla ve ayrıntılı denetim ve uyarılarla birlikte MFA ile birlikte, bölgesel düzenlemelere uygun olarak, geriye kalanı ve buluttaki veriler için en yüksek şifreleme düzeyleri.<BR> <BR>Düzey 3 verilerine örnek olarak müşteri ve iş ortağı kişisel bilgileri, ürün mühendislik belirtimleri ve özel üretim teknikleri örnek olarak verilmiştir.  |
||||

## <a name="contoso-information-policies"></a>Contoso bilgi ilkeleri
Aşağıdaki tabloda Contoso bilgi ilkeleri listelemektedir.


| Değer | Access | Veri bekletme | Bilgi koruması |
|:-------|:-----|:-----|:-----|
| Düşük iş değeri (Düzey 1: Temel) | Tüm kullanıcılara erişime izin ver'inin.  | 6 ay | Şifrelemeyi kullanın. |
| Orta ölçekli iş değeri (Düzey 2: Hassas) | Contoso çalışanları, alt yüklenicileri ve iş ortaklarına erişim izni ver. <BR><BR> MFA, Aktarım Katmanı Güvenliği (TLS) ve Mobil Uygulama Yönetimi'yi (MAM) kullanın. | 2 yıl  | Veri bütünlüğü için karma değerler kullanın.  |
| Yüksek iş değeri (Düzey 3: Çok düzenlemeye tabi) | Mühendislik ve üretimde yöneticilere ve liderlere erişim izni verme. <BR> <BR> Yalnızca yönetilen ağ cihazlarıyla Hak Yönetimi Sistemi (RMS).  | 7 yıl  | Inkarlamama için dijital imzaları kullanın.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Kurumsal belgelerle bilgi koruma için Contoso Microsoft 365 yolu

Contoso, bilgi koruma gereksinimlerine kurumsal Microsoft 365 için şu adımları izledi:

1. Hangi bilgilerin korunması gerekenleri belirleme

   Contoso, şirket içinde bulunan ve site ve dosya paylaşımlarında bulunan mevcut dijital SharePoint kapsamlı bir inceleme yaptı ve her varlığı sınıflandırıldı.

2. Veri düzeyleri için erişim, bekletme ve bilgi koruma ilkelerini belirleme

   Contoso, veri düzeylerine bağlı olarak, buluta taşınırken var olan dijital varlıkları korumak için kullanılan ayrıntılı ilke gereksinimlerini belirledi.

3. Farklı bilgi düzeyleri için duyarlılık etiketleri ve ayarları oluşturma

   Contoso, veri düzeyleri için duyarlılık etiketleri oluşturdu ve şifreleme, izinler ve filigranları içeren, yüksek düzeyde düzenlemeye tabi olan etiketlerini oluşturdu.

4. Şirket içi sitelerden veya dosya SharePoint sitelerine, yeni şirket içi sitelerine SharePoint taşıma

    Sitelere atanan varsayılan bekletme SharePoint devralınan dosyalar yeni sitelere geçirilir.

5. Çalışanları yeni belgeler için duyarlılık etiketlerini nasıl kullanabileceğini, yeni site oluştururken Contoso SharePoint IT ile nasıl etkileşim kuracaklarını ve dijital varlıkları her zaman sitelerde nasıl depolayacaklarını SharePoint eğitin

    Kötü çalışan bilgi depolama alışkanlıklarını değiştirmek çoğunlukla bulut için bilgi koruma geçişinin en zor bölümü olarak kabul edilir. Contoso IT ve yönetimi, çalışanların dijital varlıklarını her zaman bulutta etiketleye ve depolamaya ihtiyacı vardır; şirket içi dosya paylaşımlarını kullanmaktan kaçınmak ve üçüncü taraf bulut depolama hizmetlerini veya USB sürücülerini kullanmaz.

## <a name="conditional-access-policies-for-information-protection"></a>Bilgi koruması için koşullu Erişim ilkeleri

Contoso, koşullu erişim ve Exchange Online SharePoint bir parçası olarak aşağıdaki Koşullu Erişim ilkeleri kümesi yapılandırdı ve bunları uygun gruplara uyguladı:

- [Cihazlar ilkeleri üzerinde yönetilen ve yönetilemeyen uygulama erişimi](../security/office-365-security/identity-access-policies.md)
- [Exchange Online ilkelerini erişme](../security/office-365-security/secure-email-recommended-policies.md)
- [SharePoint ilkelerini erişme](../security/office-365-security/sharepoint-file-access-policies.md)

Burada, bilgi koruması için Contoso ilkeleri kümesi ortaya çıkan bir dizi var.

:::image type="content" alt-text="Cihaz, Exchange Online ve Koşullu SharePoint ilkelerini kullanın." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Contoso ayrıca kimlik ve oturum açma için ek Koşullu Erişim ilkeleri yapılandırdı. Bkz [. Contoso Corporation'ın kimliği](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).
>

Bu ilkeler şunları sağlar:

- İzin verilen uygulamalar ve kuruluşun verileriyle gerçekleştir eylemleri, uygulama koruma ilkeleri tarafından tanımlanır.
- Bilgisayarlar ve mobil cihazlar uyumlu olmalıdır.
- Exchange Online için Office 365 şifreleme (OME) Exchange Online.
- SharePoint zorlanan kısıtlamaları kullanır.
- SharePoint yalnızca tarayıcı erişimi için ve yönetim dışı cihazlara erişimi engellemek için erişim denetimi ilkelerini kullanır.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Kurumsal Microsoft 365 Contoso veri düzeylerine eşleme

Aşağıdaki tabloda, Contoso veri düzeyleri Kurumsal'daki bilgi koruma Microsoft 365 eşler.

| Düzey | Microsoft 365 hizmetleri | Windows 10 ve Kurumlar için Microsoft 365 Uygulamaları | Güvenlik ve uyumluluk |
|:-------|:-----|:-----|:-----|
| Düzey 1: Temel  | SharePoint Access Exchange Online ve koşullu erişim ilkelerini biçimlendirme <BR> Sitelere SharePoint izinler | Duyarlılık etiketleri <BR> BitLocker <BR> Windows Koruma | Cihaz Koşullu Erişim ilkeleri ve Mobil Uygulama Yönetimi ilkeleri |
| Düzey 2: Hassas | Düzey 1 artı: <BR> <BR> Duyarlılık etiketleri <BR> Microsoft 365 sitelerde bekletme SharePoint tutma <BR> Veri Kaybı Önleme ve SharePoint Önleme Exchange Online <BR> Yalıtılmış SharePoint siteler  | Düzey 1 artı: <BR> <BR> Dijital varlıklarda duyarlılık etiketleri  | Düzey 1 |
| Düzey 3: Son derece düzenlemeye tabi | Düzey 2 artı: <BR><BR> Ticari sır bilgileri için kendi anahtarınızı (BYOK) şifreleme ve koruma altına alma <BR> Microsoft 365 hizmetleriyle etkileşime sahip iş hattı uygulamaları için Azure Microsoft 365 kasa | Düzey 2 | Düzey 1 |
|||||

Sonuçta elde edilen Contoso bilgi koruma yapılandırması şu şekilde olur.

:::image type="content" alt-text="Contoso'nun sonuçta bilgi koruma yapılandırması yapılandırmasını sağlar." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Sonraki adım

Kimlik ve erişim yönetimi, tehdit [koruması, bilgi Microsoft 365](contoso-security-summary.md) ve güvenlik yönetimi için Contoso'nın kuruluş genelinde güvenlik özelliklerini nasıl kullandığını öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Güvenlik yol haritası](../security/office-365-security/security-roadmap.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)