---
title: Çift Anahtar şifrelemeye genel bakış ve SSS
description: Çift Anahtar Şifrelemesi hakkında sık sorulan sorular.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: c42104ccb74aba71b143d1ee31b0ed5893d9396f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641844"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Çift Anahtar Şifrelemesi hakkında sık sorulan sorular

Çift Anahtar Şifrelemesi'nin nasıl çalıştığı hakkında bir sorunuz mu var? Burada bir yanıt olup olmadığını kontrol edin.

## <a name="what-is-double-key-encryption-dke"></a>Çift Anahtar Şifrelemesi (DKE) nedir?

Çift Anahtarlı Şifreleme, müşterilerin özel gereksinimleri karşılamak için yüksek oranda hassas verilerini korumasını sağlar. Şifreleme anahtarları için tam denetime sahip olmanıza yardımcı olur. Verileri korumak için iki anahtar kullanır; denetiminizdeki bir anahtar ve Microsoft Azure'da güvenli bir şekilde depolanan ikinci bir anahtar. Çift Anahtar Şifrelemesi ile korunan verilerin görüntülenmesi için her iki anahtara da erişim gerekir. Microsoft bu anahtarlardan yalnızca birine erişebildiğinden, korumalı veriler Microsoft tarafından erişilemez durumda kalır ve bu da veri gizliliği ve güvenliği üzerinde tam denetim sahibi olduğunuzdan emin olur.  

Anahtarınızı istemek için kullanılan Çift Anahtar Şifreleme hizmetini tercih ettiğiniz bir konumda (şirket içi anahtar yönetim sunucusu veya bulutta) barındırabilirsiniz. Hizmeti diğer tüm uygulamalar gibi korursunuz. Çift Anahtarlı Şifreleme, Çift Anahtar Şifreleme hizmetine erişimi denetlemenize olanak tanır. Son derece hassas verilerinizi şirket içinde depolayabilir veya buluta taşıyabilirsiniz. Anahtarınız için tam denetime sahip olduğunuzdan üçüncü taraf erişimini engelleme konusunda emin olabilirsiniz. Çift Anahtar şifrelemesi, verilerinizi ve anahtarınızı aynı konumda depolamanıza olanak tanır.

DKE, Genel Veri Koruma Yönetmeliği (GDPR), Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA), Gramm-Leach-Bliley Yasası (GLBA), Rusya'nın veri yerelleştirme yasası – Federal Yasa No. 242-FZ, Avustralya Federal Gizlilik Yasası 1988 ve Yeni Zelanda'nın Gizlilik Yasası 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Microsoft Office yerleşik duyarlılık etiketlemesiyle Çift Anahtar Şifrelemesi kullanabilir miyim?

Belgeleri Çift Anahtarlı Şifreleme ile korumak için Azure Information Protection birleşik etiketleme istemcisini kullanmanız gerekir. Şu anda Microsoft Office yerleşik duyarlılık etiketlemesini kullanamazsınız.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>DKE ile hangi Microsoft 365 Uygulamaları kullanabilirim?

Windows üzerinde Word, Excel ve PowerPoint'in masaüstü sürümlerini kullanarak belgeleri korumak için DKE etiketlerini kullanabilirsiniz. Windows'ta *.12711 veya üzerini (Word, PowerPoint ve Excel'in masaüstü sürümleri) kullandığınızdan emin olun.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Çift Anahtar Şifrelemesi'nin mevcut kendi anahtarınızı tutma (HYOK) çözümünden farkı nedir?

Çift Anahtar şifrelemesi verilerinizi iki anahtarla şifreler. Şifreleme anahtarınız sizin denetiminizde, ikinci anahtar ise Microsoft Azure'da depolandığından şifrelenmiş verilerinizi buluta taşıyabilirsiniz. HYOK içeriğinizi tek bir anahtarla korur ve anahtar her zaman şirket içinde olur.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Çift Anahtarlı Şifrelenmiş belgeler harici olarak paylaşılabilir mi?

Çift Anahtarla Şifrelenmiş belgeleri, bu kullanıcılar olduğu sürece ayrı bir kiracıdaki kullanıcılarla paylaşabilirsiniz:

- Çift Anahtar Şifreleme hizmetinizdeki anahtarınıza erişmek için gerekli izne sahip olmanız gerekir.

- Microsoft Azure'da anahtarınıza erişmek için gerekli izne sahip olmanız gerekir.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>HYOK ile korunan belgelere ne olur?

Çift Anahtar şifrelemesi dağıtmak mevcut HYOK kurulumunuzu etkilemez. Ancak, HYOK ile paralel olarak Çift Anahtar Şifrelemesi kullanmaya başlamanızı öneririz.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Çift Anahtar Şifrelemesini Microsoft dışı hava ile eşlenen ortamımda çalıştırabilir miyim?

Hizmetin Microsoft Azure'a erişmesi gerektiğinden DKE bu ortamları desteklemez.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Çift Anahtarlı Şifrelenmiş belgeleri nerede depolayabilirim?

Double Key Encrypted belgelerini şirket içinde veya bulutta depolayabilirsiniz. Bulutta, şifrelenmiş içeriği SharePoint Online'a taşıyabilir ve OneDrive İş. Microsoft'un özel anahtarınıza erişimi olmadığından, şifrelenmiş veriler Microsoft'ta gizlenmeye devam eder. Bu, şifrelenmiş belgeleri Office Web Apps çevrimiçi olarak görüntüleyememenizi de sağlar.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Çift Anahtar Şifreleme hangi bölgelerde ve dillerde kullanılabilir? Çift Anahtarlı Şifreleme dünya çapında kullanılabilir mi?

DKE etiketleri, Microsoft Purview Bilgi Koruması'daki diğer duyarlılık etiketleriyle aynı dillerde yerelleştirilir. Çift Anahtarlı Şifreleme dünya çapında kullanılabilir.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>DKE olmayan bir etiketi DKE etiketine dönüştürebilir miyim?

Hayır. Bir etiket oluşturduktan sonra etikete DKE ekleyemezsiniz. Bunun yerine, **Çift Anahtar Şifrelemesi Kullan'ı** seçmeniz ve etiketi oluştururken Çift Anahtar Şifrelemesi hizmetinizin URL'sini sağlamanız gerekir.

## <a name="how-do-i-roll-my-dke-keys"></a>DKE anahtarlarımı Nasıl yaparım??

Azure'da depoladığınız anahtarı döndürme (döndürme veya yeniden anahtarlama olarak da adlandırılır) ile ilgili yönergeler için bkz. [Azure Information Protection kiracı anahtarınız için işlemler](/azure/information-protection/operations-customer-managed-tenant-key).

DKE hizmeti için yeni anahtar oluşturma hakkında bilgi için bkz. [Kiracı ve anahtar ayarları](double-key-encryption.md#tenant-and-key-settings) .

Bir anahtar oluşturduğunuzda, bir ad ve GUID ayarlarsınız. Ardından, bir anahtarı döndürürseniz, eski kaydı ad ve GUID ile saklarsınız, ancak aynı ada ancak farklı GUID'ye sahip yeni bir kayıt eklersiniz. Ortak anahtar API'sinin yeni şifreleme için döndürmeye başlaması için yeni anahtar etkin olarak ayarlanır. Yeni içeriğin ve eski içeriğin şifresinin çözülebilmesi için her iki anahtar da şifre çözme için kullanılabilir.
