---
title: Yönetim merkezinde eklentileri yönetme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Merkezi eklentileri kullanarak kuruluşta kullanıcılara ve gruplara eklenti dağıtma hakkında bilgi öğrenin.
ms.openlocfilehash: d2d1c4d36bf37ad82ac5c720931146c0dfb2220d
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028406"
---
# <a name="manage-add-ins-in-the-admin-center"></a>Yönetim merkezinde eklentileri yönetme

Office eklentileri belgelerinizi kişiselleştirmenize ve web'de bilgilere erişmenizi kolaylaştırmanıza yardımcı olur. Bkz[. Office eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Yönetici, kuruluşta kullanıcılar için eklentileri dağıttıktan sonra, eklentileri özel veya açık olarak düzenleyebilir, silebilir ve eklentilere erişimi yönetebilir.

Yönetim merkezinden eklenti yükleme hakkında daha fazla bilgi için bkz [. Yönetim merkezinde eklentileri dağıtma](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Eklenti durumları

Eklenti Açık veya Kapalı **durumda** **olabilir.**
  
| Durum | Durum nasıl oluşur? | Etki |
|:-----|:-----|:-----|
|**Etkin**  <br/> |Yönetici, eklentiyi karşıya yükledi ve kullanıcılara veya gruplara atadı.  <br/> |Eklentiye atanan kullanıcılar ve gruplar bunu ilgili istemcilerde görür.  <br/> |
|**Kapalı**  <br/> |Yönetici eklentiyi kapattı.  <br/> |Eklentiye atanan kullanıcılar ve gruplar artık buna erişemez.  <br/> Eklenti durumu Etkin olarak değiştirilirse, kullanıcılar ve gruplar buna yeniden erişebilir.  <br/> |
|**Silindi**  <br/> |Yönetici eklentiyi sildi.  <br/> |Eklentiye atanan kullanıcılar ve gruplar artık buna erişemez.  <br/> |
   
Artık hiç kimse kullanmayacaksa, eklentiyi silmeyi göz önünde bulundurabilirsiniz. Örneğin, yılın yalnızca belirli zamanlarında kullanılan bir eklentiyi kapatmanın mantıklı olabilir.

## <a name="delete-an-add-in"></a>Eklentiyi silme

Ayrıca, dağıtılmış olan eklentiyi de silebilirsiniz.

1. Yönetim merkezinde Ayarlar  > **Integrated uygulamalar sayfasına** gidin.

2. Dağıtılmış eklentiyi seçin ve sonra da Yapılandırma **sekmesini** seçin.

3. Yapılandırma **bölmesinde Gelişmiş** **Özellikler'e Ayarlar** > **.**

4. Listeden eklentiyi yeniden seçin.

5. **Eklentiyi Kaldır'ı seçin**. Sağ alt köşedeki Eklenti düğmesini kaldırın.

6. Seçimlerinizi doğrula ve Kaldır'ı **seçin**.

## <a name="edit-add-in-access"></a>Eklenti erişimini düzenleme

Dağıtım sonrası, yöneticiler eklentilere kullanıcı erişimini de yönetebilir.

1. Yönetim merkezinde Ayarlar  > **Integrated uygulamalar sayfasına** gidin.

2. Dağıtılmış eklentiyi seçin.

3. **Access'in olduğu** her **Who Düzenle'ye tıklayın**.

4. Değişiklikleri kaydedin.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Office Store'a tüm istemcilerde kapatarak eklenti indirmelerini engelleme (Outlook)

> [!NOTE]
> Outlook eklenti yüklemesi [farklı bir işlem](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins) tarafından yönetilir.

Bir kuruluş olarak Office Mağazası'ndan yeni Office eklentilerinin indirilmesini engellemek isteyebilirsiniz. Bunu Merkezi Dağıtım ile birlikte kullanarak, kuruluşunuzdaki kullanıcılara yalnızca kuruluşun onayladığı eklentilerin dağıtılmasını sağlayabilirsiniz.
  
**Eklenti alımını kapatmak için**
  
1. Yönetim merkezinde Kuruluş **ayarları Ayarlar** \> gidin.[](https://go.microsoft.com/fwlink/p/?linkid=2053743)

2. **Kullanıcıya ait uygulamalar ve hizmetler'i seçin**.
    
3. Kullanıcıların Office mağazasına erişmesine izin verme seçeneğinin Office temizleme.

    Bu işlem tüm kullanıcıların mağazadan aşağıdaki eklentileri almasını engeller.
      
    - Şu platformlardan Word, Excel ve PowerPoint 2016 eklentileri:
        
      - Windows
      - Mac
      - Office
        
        
    - **AppSource** içinde başlayan alımlar
        
    - Web site içindeki Microsoft 365
        
    Mağazaya erişmeye çalışan bir kullanıcı aşağıdaki iletiyi görebilir: Microsoft 365, Microsoft 365 Mağazası eklentilerinin tek tek **satın Office için yapılandırılmış.**
  
Office Mağazası'nı kapatma desteği aşağıdaki sürümlerde sağlanır:
  
- Windows: 16.0.9001 - Şu anda sağlanmaktadır.
    
- Mac: 16.10.18011401 - Şu anda sağlanmaktadır.
    
- iOS: 2.9.18010804 - Şu anda sağlanmaktadır.
    
- Web - Şu anda sağlanmaktadır.
    
Bu durum yöneticinin Office Mağazası'ndan eklenti atamak için Merkezi Dağıtım'ı kullanmasını engellemez.

> [!NOTE] 
> Mağaza'Visio devre Visio, Bing Haritalar ve Kişiler Graph gibi eklentiler, şeritte yine gösterir. Bu bağlantıları kaldırmak için yöneticilerin Grup İlkesi Nesnesi (GPO) aracılığıyla Store'ı devre dışı bırakması gerekir.
  
Kullanıcının Microsoft hesabıyla oturum açmasını engellemek için, oturum açmayı yalnızca kuruluş hesabını kullanacak şekilde kısıtlayabilirsiniz. Daha fazla bilgi için bkz[. Office 2016'da kimlik, kimlik doğrulama ve yetkilendirme](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Kullanıcıların Office mağazasına erişimini engellemek, kullanıcıların ağ paylaşımından test etmek Office Eklentileri Kenardan [Yüklemelerini de engelleyebilirsiniz](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Eklentilerle son kullanıcı deneyimi hakkında daha fazla bilgi

Bir eklentiyi dağıtdikten sonra, son kullanıcılarınız eklentiyi kendi Office başlatabilirsiniz. Eklenti, eklentinin desteklediği tüm platformlarda görüntülenir. Bkz[. Office Eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
Eklenti, eklenti komutlarını destekliyorsa bu komutlar Office şeridinde görünür. Aşağıdaki örnekte **Alıntılar** eklentisinin **Alıntı Ara** komutu görünür. 

![Office Ara'nın olduğu Şerit.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Dağıtılmış eklenti, eklenti komutlarını desteklemiyorsa veya dağıtılmış tüm eklentileri görmek istiyorsanız, bunları **Eklentilerim** bölümünde görüntüleyebilirsiniz. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Word 2016, Excel 2016 veya PowerPoint 2016'da

1. **Eklentilerimi \> Ekle'yi seçin**. 
    
2. Office Eklentileri penceresinde **Yönetici Tarafından Yönetilen** sekmesini seçin. 
    
3. Daha önce dağıttılan eklentiye çift tıklayın (bu örnekte **Alıntılar**).

    ![Yeni Eklentiler Office Yönetici Tarafından Yönetilen sekmesi.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Outlook'ta

1. Giriş **şeridinde** Eklentileri **Al'ı seçin**.

    ![Mağaza'daki Outlook.](../../media/getaddinsicon.png)
  
2. Sol **gezintide Yönetici** tarafından yönetilen'i seçin. 

## <a name="related-content"></a>İlgili içerik

[Reşit olmayanlar ve diğer kişilerden eklenti Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

