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
description: E-SharePoint ve belge kitaplıklarını korumak için Microsoft Azure Active Directory Rights Management Services (RMS) aracılığıyla SharePoint Online IRM'yi kullanmayı öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 8c0f60ad1a571ba13ba83e3e92c1b5aca6535bb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311641"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

IRM SharePoint, dosyaların liste ve kitaplık düzeyindeki dosyalarına uygulanır. Kuruluşun IRM korumasını kullanamadan önce Hak Yönetimi'nin ayarlanmış olması gerekir. IRM, kullanım kısıtlamalarını şifrelemek ve atamak için Azure Information Protection'ın Azure Hak Yönetimi hizmetini kullanır. Bazı Microsoft 365 planlar Azure Hak Yönetimi'nden kaynaklanmaz. Daha fazla bilgi edinmek için Uygulama [Office hizmetleri Azure Hak Yönetimini nasıl destekler? makaleyi okuyun](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Yönetim merkezini kullanarak IRM SharePoint açma

Organizasyon, listeleri ve kitaplıkları IRM ile SharePoint için, önce, kurum için Hak Yönetimi hizmetini etkinleştirmeniz gerekir. Bkz. Azure Hak Yönetimini [Etkinleştirme](/information-protection/deploy-use/activate-service). Hak Yönetimi hizmetini etkinleştirmek için genel yönetici ayrıcalıklarına sahip bir iş veya okul hesabı kullan olmanız gerekir. Aksi takdirde, IRM özelliklerini SharePoint Online ile SharePoint.
  
Hak Yönetimi hizmetini etkinleştirdikten sonra, IRM'SharePoint yönetim merkezinde oturum açma.
  
1. Genel yönetici veya yönetici SharePoint.
    
2. Uygulama başlatıcı simgesini seçin. ![Uygulama başlatıcı simgesi Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) seçin ve sol üstteki **Yönetici'yi** seç Microsoft 365 yönetim merkezi. (Yönetici kutucuğunu görmüyorsanız, kuruluş içinde yönetici izinlerine sahip değilseniz.) 
    
3. Sol bölmede Yönetim merkezleri **ve yönetim** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint seçin</a>.
    
4. Sol bölmede **ayarlar'ı ve** ardından klasik ayarlar **sayfasını seçin**.
    
5. Bilgi Hakları **Yönetimi (IRM) bölümünde**, Yapılandırmanız için belirtilen **IRM** hizmetini kullan'ı seçin ve sonra **da IRM hizmetini yenile'yi Ayarlar**. IRM ayarlarını yeniledikten sonra, kuruluşta yer alan kişiler kendi kullanıcı listelerinde ve belge kitaplıklarında IRM SharePoint kullanmaya başlayabilir. Ancak, bunu yapma seçenekleri Kitaplık Kitaplığı'nın ve Liste Listesi'Ayarlar bir Ayarlar.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>IRM etkinleştirme SharePoint kitaplıklarını ve listelerini etkinleştirme
<a name="__toc220831191"> </a>

IRM ayarlarını yeniledikten sonra, site sahipleri kendi posta listelerini ve belge SharePoint IRM ile koruyabilirler. Daha fazla bilgi için Bkz [. Liste veya kitaplı kitaplara Bilgi Hakları Yönetimi'ne uygulama](apply-irm-to-a-list-or-library.md).
  
Site sahipleri bir liste veya kitaplık için IRM'yi etkinleştir ettiklerinde, o liste veya kitaplıkta desteklenen tüm dosya türlerini koruyabilirler. IRM bir kitaplık için etkinleştirildiğinde, hak yönetimi o kitaplıkta yer alan tüm dosyalara uygulanır. IRM'yi bir liste için etkinleştirebilirsiniz; hak yönetimi gerçek liste öğelerine değil, yalnızca liste öğelerine eklenmiş dosyalara uygulanır.
  
Kişiler bir IRM etkinleştirilmiş liste veya kitaplıkta dosya indirdikten sonra, bu dosyalar şifrelenir ve böylelikle yalnızca yetkili kişiler bunları ilebilir. Hak yönetimi olan her dosya aynı zamanda dosyayı gören kişiler üzerinde kısıtlamalar dayatan bir verme lisansı içerir. Genel kısıtlamalar arasında dosyayı salt okunur yapma, metin kopyalamayı devre dışı bırakma, kişilerin yerel bir kopya kaydetmesini ve dosyayı yazdırmasını önleme gibi kısıtlamalar yer almaktadır. IRM desteği olan dosya türlerini okuyabilen istemci programları, bu kısıtlamaları uygulamak için hakları yönetilen dosyanın içindeki verme lisansını kullanır. Hak yönetimiyle yönetilen bir dosya indirildikten sonra bile korumasını böyle korur. IRM'yi bir liste veya kitaplıkta etkinleştirmek için bkz [. Liste veya kitaplara Bilgi Hakları Yönetimi'ne uygulama](apply-irm-to-a-list-or-library.md).
  
Tarayıcıda IRM etkinleştirilmiş bir kitaplığı kullanarak belgeleri Office oluşturamaz veya düzenleyemezsiniz. Bunun yerine, IRM şifreli dosyaları tek indirebilir ve düzenleyebilir. Birden çok kullanıcıda birlikte yazma  *veya yazma hakkında*  daha fazla bilgi için, iade ve iadeyi kullanın. 
  
IRM korumalı bir kitaplıktan PDF dosyası indirken korumalı Microsoft 365 bir PDF dosyası oluşturur. Dosyanın uzantısı değişmez, ancak dosya korunur. Bu dosyayı görüntülemek için Azure Information Protection görüntüleyicisi, tam Azure Information Protection istemcisi veya korumalı PDF dosyalarını görüntülemeyi destekleyen başka bir uygulamaya ihtiyacınız vardır. 
  
SharePoint Online aşağıdaki dosya türlerinin şifrelerini destekler:
  
- PDF
    
- Aşağıdaki programlara uygun 97-2003 dosya Microsoft Office: Word, Excel ve PowerPoint
    
- Aşağıdaki Office için open XML biçimlerini Microsoft Office: Word, Excel ve PowerPoint
    
- XML Kağıt Belirtimi (XPS) biçimi
 
> [!NOTE]
> IRM koruması korumalı belgelere (dijital olarak imzalanmış PDF dosyaları gibi) SharePoint karşıya yüklemede belgeyi açması gerekmektedir. 

## <a name="next-steps"></a>Sonraki adımlar
<a name="__toc220831191"> </a>

SharePoint Online için IRM'i etkinleştirdikten sonra, listelere ve kitaplıklara hak yönetimi uygulamaya başlayabilirsiniz. Bilgi için, Liste [veya kitaplı kitaplara Bilgi Hakları Yönetimi'ne uygulama.](apply-irm-to-a-list-or-library.md)
  
Windows için yeni OneDrive eşitleme istemcisi artık IRM korumalı SharePoint belge kitaplıkları ve OneDrive konumlarını eşitlemeyi destekler (kitaplığın IRM ayarı belge erişim haklarının süresinin dolması için ayarlanmaz). Daha fazla bilgi için veya yeni eşitleme istemcisini dağıtmaya başlama için bkz. Yeni eşitleme [istemcisini OneDrive eşitleme için Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)