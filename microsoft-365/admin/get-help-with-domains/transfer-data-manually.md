---
title: İki hesap arasında verileri el ile aktarma
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Planı veya şirket adını değiştirdiğini ya da Microsoft 365 birden çok aboneliği tek bir abonelikte birleştirmişken, iki farklı hesap arasında el ile veri aktarmayı öğrenin.
ms.openlocfilehash: 7d6cb9e055fd27e8f9b0a26e7ff4bfffa97421ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316723"
---
# <a name="transfer-data-manually-between-two-accounts"></a>İki hesap arasında verileri el ile aktarma

Sleeve'lerinizi toplamaya ve takvimde zaman öbeklerini toplamaya hazırlanma: İki iş hesabı arasında veri Microsoft 365 elle, karmaşık ve zaman alıcı bir işlemdir. Bu otomatik veya desteklenen bir işlem değildir. Başlamaya hemen başlamış oluruz.
  
> [!CAUTION]
> E-posta, e-posta, Skype Kurumsal web sitesi ve Microsoft 365 bir genel web sitesinin çalışmayyacağız. Kullanıcıların yeni kullanıcı adları ve parolaları olur ve kullanıcı adlarını ve parolaları Outlook.

**Bu konudaki yönergeleri kullanarak verileri yalnızca el ile aktarma (aşağıdakilerden biri geçerlidir):**
  
- Farklı bir hizmet ailesinde bir plana ihtiyacınız var.

- Şirket adınız değişti ve yeni bir abonelik oluşturduk ve farklı ilk etki alanı adları kullanmak istediğiniz için verilerinizi geçirmeye karar verdiniz.

- Birden çok aboneliği yeni bir abonelikte birleştirmelisiniz.

> [!IMPORTANT]
> Abonelik planınızı değiştirmeniz gerekirse ve Plan değiştir sihirbazını kullanabilirsiniz ya da Plan değiştir sihirbazı çalışmasa bile aynı abonelik ailesinde yeni bir abonelik planına aktarmanız gerekirse, verilerinizi el ile aktarmanız gerekmez ve çalışma süresi de yoktur.[](../../commerce/subscriptions/switch-to-a-different-plan.md)

|**Görevler**|**Adımlar**|
|:-----|:-----|
|Taşımak istediğiniz planı satın alın.  <br/> |Kaydol sırasında, ilk etki alanı adlarında kullanmak üzere şirket adını belirtirsiniz:  *yourcompany*  .onmicrosoft.com,  *yourcompany*  -public.sharepoint.com, and  *yourcompany*  .sharepoint.com. Var olan aboneliklerde  *, şirket adı*  olarak var olan adlardan farklı bir ad kullan gerekir.  <br/> > [!NOTE]> Aboneliği iptal etmenizden sonra, şirketinizi kullanan ilk etki alanı adlarının sistemlerimizin kullanımına dahil edilmesi normalde en  *az*  birkaç ay sürer. Eski Microsoft 365 aboneliğinizin tüm verilerini kaydetmeyi ve bu aboneliği iptal yapmayı planlasanız bile, eski şirket değeriniz yeni bir  abonelikte hemen kullanılamaz.           |
|Eski Microsoft 365 aboneliğinden özel etki Microsoft 365 kaldırın.  <br/> | Kullanıcı [e-posta adreslerinden etki alanı](remove-a-domain.md) adını kaldırmak ve e-postanın DNS kayıtlarını ve özel etki alanı için Lync'i kaldırmak için, etki alanını kaldırmadan önce gerekli adımları izleyin. Genel web sitenizi aynı Microsoft 365 barındırıyorsanız, bu kaydın CNAME kaydını da kaldırmanız gerekir.  <br/> > [!IMPORTANT]> E-postayı bu özel etki alanına yönlendiren MX kaydını kaldırdikten sonra, etki alanını yeni hesabınıza ekleyene, yeni MX kaydını ayarlamaya ve kullanıcılarınızı ayarlamaya kadar e-posta çalışmayı durdurur. Lync için DNS kayıtlarını kaldırabilirsiniz, Lync çalışmayı durdurur. Ayrıca, genel web sitenize göre CNAME kaydını kaldırdikten sonra bu kayıt kullanılamaz.           [Etki alanını kaldırın](remove-a-domain.md) .  <br/> |
|Yeni aboneliğiniz için özel etki alanlarınızı ayarlayın ve kullanıcılarınızı ayarlayın.  <br/> | Özel etki alanınız için gerekli DNS kayıtlarını oluşturma da içinde olmak üzere yeni aboneliğinizi ayarlayın.  <br/>  Kullanıcılarınızı, özel etki alanınız üzerinde e-posta adresleriyle oluşturun.  <br/> |
|Eski aboneliğinize yeni aboneliğinize veri aktarabilirsiniz.  <br/> | Ayrı tarayıcı pencerelerde her iki hesapta da oturum açın:  <br/>  Tarayıcı simgesine sağ tıklayın ve iki özel tarayıcı penceresini açın. Her iki hesapta da oturum açma için iki pencere içinde farklı kimlik bilgileri kullanabilirsiniz.  <br/> [Abonelikler arasında yönetim ayarlarını aktarma](#email) <br/> [Ekip sitesi yapısını ve verilerini aktarma](#transfer-team-site-structure-and-data) <br/> [Bir genel web sitesini abonelikler arasında aktarma](#transfer-a-public-website-between-subscriptions) <br/> [Abonelikler arasında yönetim ayarlarını aktarma](#email) <br/> |
|Daha fazla bilgi için Microsoft Destek'i arayarak, sahip olduğunuz plan aboneliğini Microsoft 365.  <br/> | Yeni aboneliğinizin çalıştığını ve tüm verilerin aktarıldı olduğunu doğrulayın.  <br/>  [Eski aboneliğinizi iptal](../../business-video/get-help-support.md) etmek için müşteri desteğine başvurun.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Abonelikler arasında yönetim ayarlarını aktarma

Her hesapta aşağıdaki sayfalara gidin ve yeni hesabı eski hesabın ayarlarına göre ayarlayın.
  
Microsoft 365'dan Microsoft 365 Orta Ölçekli İşletme veya Microsoft 365 Kurumsal'e veri aktarıyorsanız, yönetici sayfaları farklı yapılandırılmıştır. Video izleyin[: Microsoft 365 Kurumsal](../index.yml) ve yönetici ayarlarına bakmak için aşağıdaki yerlere gidin.
  
Orta Microsoft 365 Kurumsal ve Microsoft 365 için:
  
|**Konum**|**Amaç**|
|:-----|:-----|
|**Yönetici** \>  \> Microsoft 365 **Hizmeti ayarları** <br/> |Posta, siteler, Lync, kullanıcı yazılımı, parolalar, topluluk, hak yönetimi ve mobil ayarları için her sekmeyi seçin.  <br/> |
|**Yönetici** \> **Exchange** <br/> | Exchange Online ayarları  <br/> |
|**Yönetici** \> **SharePoint** <br/> | SharePoint Online ayarları  <br/> |
|**Yönetici** \> **Skype Kurumsal** <br/> |Ek Skype Kurumsal ayarları  <br/> |

Küçük Microsoft 365 Küçük İşletme için
  
|**Konum**|**Amaç**|
|:-----|:-----|
|**Yönetici** \> **Kuruluş genelinde ayarları yönetme** <br/> |Yönetim ayarları  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Bir genel web sitesini abonelikler arasında aktarma

Web sitesinde barındırılan bir genel Microsoft 365 varsa, web sitesini kaydetmeniz ve yeni aboneliğinize yeniden oluşturmanız gerekir.
  
> [!NOTE]
> Genel web siteniz bir DNS barındırma sağlayıcısında barındırıldısa, değişiklik yapmak gerekmez. Geçişiniz bu durumdan etkilenmez.
  
SharePoint Online ortamındaki belge kitaplığını veya liste içeriğini dosya paylaşımlarına veya yerel bir bilgisayara kaydetmek için bkz. [SharePoint Online içeriği el ile geçiş](/sharepoint/troubleshoot/migration-tool/content-manual-migration).
  
> [!NOTE]
> Genel site geçiş uygulaması, verileri farklı bir aboneliğe aktar aşağıdaki abonelikte aktar aşağıdakilere ek olarak devreder.
  
## <a name="transfer-team-site-structure-and-data"></a>Ekip sitesi yapısını ve verilerini aktarma

Ekip sitesi verilerini kaydetmenin veya aktarmanın çeşitli yolları vardır:
  
- Eski siteyi şablon olarak kaydedebilir ve şablonu yeni siteye aktarabilirsiniz.

- Belgeleri aktarımı için, önce yeni sitede hiyerarşinizi el ile yeniden oluşturun. Ardından, aynı anda her SharePoint ekip sitelerini de açabilir, Windows Explorer ile her iki belge kitaplığını da açabilir ve belgeleri kopyalayıp yapıştırabilirsiniz. Bkz [. Video: Explorer ile Aç'ı kullanarak kitaplık dosyalarını kopyalama veya taşıma](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).

- Liste verilerini aktarımı için, liste [şablonunu kaydedin](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393) ve kaydedilen şablonu kullanarak yeni sitede listeyi yeniden oluşturun.

- SharePoint Online ortamındaki (OneDrive İş veya ekip siteleri) belge kitaplığını veya liste içeriğini dosya paylaşımlarına veya yerel bir bilgisayara kaydetmek için bkz. SharePoint Online içeriğinin el ile geçiş [hakkında bilgiler](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

## <a name="transfer-users-data-between-subscriptions"></a>Kullanıcıların verilerini abonelikler arasında aktarma

### <a name="email"></a>E-posta:

Yeni aboneliğinizi [ayardikten sonra kullanıcılardan e-postalarını, kişilerini,](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) görevlerini ve takvim bilgilerini taşımalarını iste. Eski e-postalarına, e-posta gibi ilk kullanıcı adını kullanarak sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>OneDrive İş veri toplama:

Kullanıcılardan Yeni OneDrive İş [kopyalamalarını/eşitlemelerini](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd) ve sonra yeni aboneliklerine yeniden eklemelerini iste.

### <a name="onenote"></a>OneNote 

Kullanıcılardan Yeni [aboneliklerini yedeklemelerini OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) [Yedekten notları geri yüklemelerini](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) iste.
