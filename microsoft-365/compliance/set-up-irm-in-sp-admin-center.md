---
title: Set up Information Rights Management (IRM) in SharePoint admin center
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: SharePoint listelerini ve belge kitaplıklarını korumak için Microsoft Azure Active Directory Rights Management Services (RMS) aracılığıyla SharePoint Online IRM'yi kullanmayı öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: af8f19fe455c1aca1d6b7aab045a9aea5b5efee5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632057"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

SharePoint Online'da IRM koruması liste ve kitaplık düzeyindeki dosyalara uygulanır. Kuruluşunuzun IRM korumasını kullanabilmesi için önce Rights Management'ı ayarlamanız gerekir. IRM, kullanım kısıtlamalarını şifrelemek ve atamak için Azure Information Protection Azure Rights Management hizmetine dayanır. Bazı Microsoft 365 planları Azure Rights Management'ı içerir ancak tümünü içermez. Daha fazla bilgi edinmek için [Bkz. Office uygulamaları ve hizmetleri Azure Rights Management'ı nasıl destekler](/azure/information-protection/understand-explore/office-apps-services-support)?
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>SharePoint yönetim merkezini kullanarak IRM hizmetini açma

Kuruluşunuzun SharePoint listelerini ve kitaplıklarını IRM ile koruyabilmesi için önce kuruluşunuz için Rights Management hizmetini etkinleştirmeniz gerekir. Nasıl yapılacağını öğrenmek için bkz [. Azure Rights Management'ı etkinleştirme](/information-protection/deploy-use/activate-service). Rights Management hizmetini etkinleştirmek için genel yönetici ayrıcalıklarına sahip bir iş veya okul hesabı kullanmanız gerekir. Aksi takdirde, SharePoint Online ile IRM özelliklerini kullanamazsınız.
  
Rights Management hizmetini etkinleştirdikten sonra, IRM'yi açmak için SharePoint yönetim merkezinde oturum açın.
  
1. Genel yönetici veya SharePoint yöneticisi olarak oturum açın.
    
2. Uygulama başlatıcı simgesini ![Office 365 uygulama başlatıcı simgesi seçin.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) öğesini seçin ve Yönetici seçerek **Microsoft 365 yönetim merkezi** açın. (Yönetici kutucuğunu görmüyorsanız, kuruluşunuzda yönetici izinlerine sahip değilsinizdir.) 
    
3. Sol bölmede <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezini</a> **Yönetici merkezleri'ni** \> seçin.
    
4. Sol bölmede **ayarlar'ı** ve ardından **klasik ayarlar sayfasını** seçin.
    
5. **Bilgi Hakları Yönetimi (IRM)** bölümünde **Yapılandırmanızda belirtilen IRM hizmetini kullan'ı** ve ardından **IRM Ayarlarını Yenile'yi** seçin. IRM ayarlarını yeniledikten sonra, kuruluşunuzdaki kişiler SharePoint listelerinde ve belge kitaplıklarında IRM kullanmaya başlayabilir. Ancak, bunu yapma seçeneklerinin Kitaplık Ayarları ve Liste Ayarları'nda görünmesi bir saat kadar sürebilir.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>IRM ile SharePoint belge kitaplıklarını ve listelerini etkinleştirme
<a name="__toc220831191"> </a>

IRM ayarlarını yeniledikten sonra, site sahipleri SharePoint listelerini ve belge kitaplıklarını IRM ile koruyabilir. Daha fazla bilgi için bkz. [Bir liste veya kitaplığa Bilgi Hakları Yönetimi Uygulama](apply-irm-to-a-list-or-library.md).
  
Site sahipleri bir liste veya kitaplık için IRM'yi etkinleştirdiğinde, bu liste veya kitaplıkta desteklenen tüm dosya türlerini koruyabilir. IRM bir kitaplık için etkinleştirildiğinde, hak yönetimi bu kitaplıktaki tüm dosyalara uygulanır. Bir liste için IRM'yi etkinleştirdiğinizde, hak yönetimi gerçek liste öğelerine değil, yalnızca liste öğelerine eklenmiş dosyalara uygulanır.
  
IRM özellikli bir liste veya kitaplıktaki dosyalar indirildiğinde, dosyalar yalnızca yetkili kişilerin görüntüleyebilmesi için şifrelenir. Haklarla yönetilen her dosya, dosyayı görüntüleyen kişilere kısıtlamalar getiren bir verme lisansı da içerir. Tipik kısıtlamalar arasında bir dosyanın salt okunur hale getirilmesi, metnin kopyalanmasının devre dışı bırakılması, kişilerin yerel kopyayı kaydetmesini engelleme ve kişilerin dosyayı yazdırmasını engelleme sayılabilir. IRM tarafından desteklenen dosya türlerini okuyabilen istemci programları, bu kısıtlamaları zorlamak için haklarla yönetilen dosya içindeki verme lisansını kullanır. Haklarla yönetilen bir dosya, indirildikten sonra bile korumasını böyle korur. Bir liste veya kitaplıkta IRM'yi etkinleştirmek için bkz. Liste [veya kitaplığa Bilgi Hakları Yönetimi Uygulama](apply-irm-to-a-list-or-library.md).
  
Tarayıcıda Office kullanarak IRM özellikli bir kitaplıkta belge oluşturamaz veya düzenleyemezsiniz. Bunun yerine, bir kerede bir kişi IRM ile şifrelenmiş dosyaları indirebilir ve düzenleyebilir. Birden çok kullanıcı arasında  *birlikte yazmayı* veya yazmayı yönetmek için iade etme ve kullanıma alma özelliğini kullanın. 
  
IRM korumalı bir kitaplıktan PDF dosyası indirdiğinizde, Microsoft 365 korumalı bir PDF dosyası oluşturur. Dosyanın uzantısı değişmez, ancak dosya korunur. Bu dosyayı görüntülemek için Azure Information Protection görüntüleyicisine, tam Azure Information Protection istemcisine veya korumalı PDF dosyalarını görüntülemeyi destekleyen başka bir uygulamaya ihtiyacınız olacaktır.
  
SharePoint Online aşağıdaki dosya türlerinin şifrelenmesini destekler:
  
- PDF
    
- Aşağıdaki Microsoft Office programları için 97-2003 dosya biçimleri: Word, Excel ve PowerPoint
    
- Aşağıdaki Microsoft Office programları için Office Open XML biçimleri: Word, Excel ve PowerPoint
    
- XML Kağıt Belirtimi (XPS) biçimi
 
> [!NOTE]
> SharePoint'in belgeyi karşıya yüklemede açması gerektiğinden, korumalı belgelere (dijital olarak imzalanan PDF dosyaları gibi) IRM koruması uygulanamaz. 

## <a name="next-steps"></a>Sonraki adımlar
<a name="__toc220831191"> </a>

SharePoint Online için IRM'yi etkinleştirdikten sonra, listelere ve kitaplıklara hak yönetimi uygulamaya başlayabilirsiniz. Bilgi için bkz. [Liste veya kitaplığa Bilgi Hakları Yönetimi uygulama](apply-irm-to-a-list-or-library.md).
  
Windows için yeni OneDrive eşitleme istemcisi artık IRM korumalı SharePoint belge kitaplıklarının ve OneDrive konumlarının eşitlenmesini destekliyor (kitaplığın IRM ayarı belge erişim haklarının süresi dolacak şekilde ayarlanmadıysa). Daha fazla bilgi için veya yeni eşitleme istemcisini dağıtmaya başlamak için bkz. [Windows için yeni OneDrive eşitleme istemcisini dağıtma](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)
