---
title: Çift Anahtar Şifrelemesi'ne genel bakış ve SSS
description: Özellikler için Çift Anahtar Şifrelemesi hakkında sık Microsoft 365.
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
ms.openlocfilehash: 269937e78ffee6956df5a4dc8dc978fa30043912
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320991"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Double Key Encryption frequently asked questions

Çift Anahtar Şifrelemesi'nin nasıl çalıştığını merak ediyor musunuz? Burada yanıta göz asın.

## <a name="what-is-double-key-encryption-for-microsoft-365-dke"></a>Şifreleme için Çift Anahtar Şifrelemesi (DKE) Microsoft 365 nedir?

Ürün Ürünleri için Çift Anahtar Microsoft 365, müşterilerin özel gereksinimleri karşılamak üzere yüksek hassas verilerini korumalarına olanak sağlar. Müşterilerin şifreleme anahtarları üzerinde tam denetime sahiplerine yardımcı olur. Verileri korumak için iki anahtar kullanır; bir anahtara ve güvenli bir şekilde depolanan ikinci bir anahtara Microsoft Azure. Çift Anahtar Şifrelemesi ile korunan verileri görüntülemek için her iki anahtara da erişim gerekir. Microsoft bu anahtarlardan yalnızca birinin erişimine sahip olduğu için, korumalı verilere Microsoft erişilemez durumda kalır ve veri gizliliği ve güvenliğiniz üzerinde tam denetime sahip olursiniz.  

Anahtarınızı istediğiniz konumda (şirket içi anahtar yönetim sunucusu veya bulutta) talep etmek için kullanılan Çift Anahtar Şifrelemesi hizmetini barındırabilirsiniz. Hizmeti aynı diğer herhangi bir uygulama gibi sürdürürsiniz. Çift Anahtar Şifrelemesi, Çift Anahtar Şifreleme hizmetine erişimi denetlemenizi sağlar. Çok hassas verilerinizi şirket içinde depolu veya buluta taşıyabilirsiniz. Anahtarınız üzerinde tam denetime sahip olduğunuz için üçüncü taraf erişimini engelleme konusunda emin olabilirsiniz. Çift Anahtar Şifrelemesi, verilerinizi ve anahtarı aynı konumda depolamanıza olanak sağlar.

DKE, Genel Veri Koruma Yönetmeliği (GDPR), Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA), Gramm-Leach-Bliley Yasası (GLBA), Rusya'nın veri yerelleştirme yasası - Federal Yasalar No gibi çeşitli düzenlemeler ve standartlar genelinde yasal gereksinimleri karşılamanıza yardımcı olur. 242-FZ, Avustralya Federal Gizlilik Yasası 1988 ve Yeni Zelanda Gizlilik Yasası 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Yerleşik duyarlılık etiketlemesi için çift Microsoft Office Şifreleme kullanabilir miyim?

Belgeleri Çift Anahtar Şifrelemesi ile korumak için Azure Information Protection birleşik etiketleme istemcisini kullan gerekir. Şu anda, yerleşik Microsoft Office etiketlemeyi kullanaasiniz.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>DKE Microsoft 365 Uygulamaları hangi bilgileri kullanabilirim?

Word, Excel ve PowerPoint'un masaüstü sürümlerini kullanarak belgeleri korumak için DKE Windows. Aynı anda *.12711 veya sonraki bir sürümünü (Word, PowerPoint ve Excel masaüstü sürümleri) kullanırkenn emin Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Çift Anahtar Şifrelemesi ile var olan anahtarın (HYOK) çözümü arasında ne fark vardır?

Çift Anahtar Şifrelemesi, verilerinizi iki anahtarla şifreler. Şifreleme anahtarınız sizin denetimindedir ve ikinci anahtar Microsoft Azure, şifrelenmiş verilerinizi buluta taşımanıza olanak sağlar. HYOK içeriğinizi tek bir anahtarla korur ve anahtar her zaman şirket içindedir.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Double Key Encrypted belgeleri dıştan paylaşılır mı?

Double Key Encrypted belgelerini, şu kullanıcılar olduğu sürece ayrı bir kiracıda kullanıcılarla paylaşabilirsiniz:

- Çift Anahtar Şifreleme hizmetinizin anahtarına erişmek için gerekli izninize sahip olun.

- Aynı bağlantıda anahtarınıza erişmek için gerekli Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>HYOK ile korunan belgelere ne olur?

Çift Anahtar Şifrelemesi'nin dağıtımı mevcut HYOK kurulumlarınızı etkilemez. Bununla birlikte, Çift Anahtar Şifrelemesi'ne HYOK ile paralel olarak başlamayı öneririz.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Microsoft tarafından havayla eşlenen olmayan ortamımda Çift Anahtar Şifrelemesi çalıştırabilirsiniz mi?

DKE bu ortamları desteklemez, çünkü hizmet bu ortamlara erişim Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Double Key Encrypted belgelerini nerede depo indirebilirsiniz?

Çift Anahtarlı Şifreli belgeleri şirket içinde veya bulutta depoabilirsiniz. Bulutta, şifrelenmiş içeriği SharePoint Online'a ve OneDrive İş. Microsoft'un özel anahtarınıza erişimi kalmaya neden olduğu için, şifrelenmiş veriler Microsoft'a opak kalır. Bu aynı zamanda, şifrelenmiş belgeleri Web Apps'te çevrimiçi olarak Office anlamına gelir.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Çift Anahtar Şifreleme hangi bölgelerde ve dillerde kullanılabilir? Çift Anahtar Şifreleme dünya çapında kullanılabilir mi?

DKE etiketleri, sitedeki diğer duyarlılık etiketleriyle aynı dillere Microsoft Bilgi Koruması. Çift Anahtar Şifreleme dünya çapında kullanılabilir.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>DKE olmayan bir etiketi DKE etiketine dönüştürür mü?

Hayır. Bir etiket oluşturdukktan sonra DKE ekleriz. Bunun yerine, Çift Anahtar **Şifrelemesi Kullan'ı** seçmeniz ve etiketi oluşturmanız için Çift Anahtar Şifreleme hizmetinizin URL'sini sağlamanız gerekir.

## <a name="how-do-i-roll-my-dke-keys"></a>DKE tuşlarımı nasıl yuvarlayacağım?

Azure'da depoladığı anahtarı döndürme (döndürme veya yeniden tuşlama olarak da adlandırılan) hakkında yönergeler için bkz. [Azure Information Protection kiracı anahtarınız için işlemler](/azure/information-protection/operations-customer-managed-tenant-key).

DKE [hizmeti için yeni](double-key-encryption.md#tenant-and-key-settings) anahtar oluşturma hakkında bilgi için bkz. Kiracı ve anahtar ayarları.

Anahtar  oluşturmada, bir ad ve GUID'ye sahip oluruz. Ardından, bir anahtarı döndürersiniz, eski kaydı ad ve GUID ile birlikte tutmanıza ama aynı adı başka GUID olan yeni bir kayıt eklemenize neden olabilir. Yeni anahtar, ortak anahtar API'sini yeni şifreleme için geri döndüren bir şekilde etkin olarak ayarlanır. Yeni içeriğin ve eski içeriğin şifresinin çözülmüş olması için her iki anahtar da şifre çözme için kullanılabilir.