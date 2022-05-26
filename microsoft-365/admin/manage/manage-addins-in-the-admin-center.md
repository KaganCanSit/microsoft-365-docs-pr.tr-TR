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
description: Kuruluşunuzdaki kullanıcılara ve gruplara eklenti dağıtmak için Merkezi eklentileri kullanma hakkında bilgi edinin.
ms.openlocfilehash: 96bbdf5d4d9e4f1697fa0b85f902d8d758d356fa
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65678974"
---
# <a name="manage-add-ins-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi eklentileri yönetme

Office Eklentileri, belgelerinizi kişiselleştirmenize ve web'deki bilgilere erişme yönteminizi kolaylaştırmanıza yardımcı olur. Bkz. [Office Eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Genel yönetici veya exchange yöneticisi bir kuruluştaki kullanıcılar için eklentileri dağıttığı zaman eklentileri kapatabilir veya açabilir, düzenleyebilir, silebilir ve eklentilere erişimi yönetebilir.

Yönetim merkezinden eklentileri yükleme hakkında daha fazla bilgi için bkz. [Yönetim merkezinde eklentileri dağıtma](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Eklenti durumları

Eklenti **Açık** veya **Kapalı** durumda olabilir.
  
| Durum | Durum nasıl oluşur? | Etki |
|:-----|:-----|:-----|
|**Etkin**  <br/> |Yönetici, eklentiyi karşıya yükledi ve kullanıcılara veya gruplara atadı.  <br/> |Eklentiye atanan kullanıcılar ve gruplar bunu ilgili istemcilerde görür.  <br/> |
|**Kapalı**  <br/> |Yönetici eklentiyi kapattı.  <br/> |Eklentiye atanan kullanıcılar ve gruplar artık buna erişemez.  <br/> Eklenti durumu Etkin olarak değiştirilirse, kullanıcılar ve gruplar buna yeniden erişebilir.  <br/> |
|**Silindi**  <br/> |Yönetici eklentiyi sildi.  <br/> |Eklentiye atanan kullanıcılar ve gruplar artık buna erişemez.  <br/> |
   
Artık kimse kullanmıyorsa eklentiyi silmeyi göz önünde bulundurun. Örneğin, bir eklentinin yalnızca yılın belirli zamanlarında kullanılması durumunda eklentinin kapatılması mantıklı olabilir.

## <a name="delete-an-add-in"></a>Eklentiyi silme

Dağıtılan bir eklentiyi de silebilirsiniz.

1. Yönetim merkezinde **Ayarlar** >  **Integrated apps** sayfasına gidin.

2. Dağıtılan eklentiyi ve ardından **Yapılandırma** sekmesini seçin.

3. **Yapılandırma** bölmesinde **Gelişmiş Ayarlar** >  **Add-ins'e** gidin.

4. Listeden eklentiyi yeniden seçin.

5. **Eklentiyi Kaldır'ı** seçin. Sağ alt köşedeki Eklenti düğmesini kaldırın.

6. Seçimlerinizi doğrulayın ve **Kaldır'ı** seçin.

## <a name="edit-add-in-access"></a>Eklenti erişimini düzenleme

Dağıtım sonrasında, yöneticiler eklentilere kullanıcı erişimini de yönetebilir.

1. Yönetim merkezinde **Ayarlar** >  **Integrated apps** sayfasına gidin.

2. Dağıtılan eklentiyi seçin.

3. Access Who altında **Düzenle'ye** tıklayın.

4. Değişiklikleri kaydedin.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>tüm istemcilerde Office Mağazası'nı kapatarak eklenti indirmelerini engelleme (Outlook hariç)

> [!NOTE]
> Outlook eklenti yüklemesi [farklı bir işlem](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins) tarafından yönetilir.

Kuruluş olarak yeni Office Eklentilerin Office Store'dan indirilmesini engellemek isteyebilirsiniz. Bunu Merkezi Dağıtım ile birlikte kullanarak, kuruluşunuzdaki kullanıcılara yalnızca kuruluşun onayladığı eklentilerin dağıtılmasını sağlayabilirsiniz.
  
**Eklenti alımını kapatmak için**
  
1. Yönetim merkezinde kuruluş [ayarları](https://go.microsoft.com/fwlink/p/?linkid=2053743) **Ayarlar** \> sayfasına gidin.

2. **Kullanıcıya ait uygulamalar ve hizmetler'i** seçin.
    
3. Kullanıcıların Office deposuna erişmesine izin verme seçeneğini temizleyin.

    Bu işlem tüm kullanıcıların mağazadan aşağıdaki eklentileri almasını engeller.
      
    - Şu platformlardan Word, Excel ve PowerPoint 2016 eklentileri:
        
      - Windows
      - Mac
      - Office
        
        
    - **AppSource** içinde başlayan alımlar
        
    - Microsoft 365 içindeki eklentiler
        
    Mağazaya erişmeye çalışan bir kullanıcı şu iletiyi görür: **Üzgünüz, Microsoft 365 Office Store eklentilerinin tek tek edinilmesini engelleyecek şekilde yapılandırılmıştır.**
  
Office Mağazası'nı kapatma desteği aşağıdaki sürümlerde sağlanır:
  
- Windows: 16.0.9001 - Şu anda kullanılabilir.
    
- Mac: 16.10.18011401 - Şu anda sağlanmaktadır.
    
- iOS: 2.9.18010804 - Şu anda sağlanmaktadır.
    
- Web - Şu anda kullanılabilir.
    
Bu durum yöneticinin Office Mağazası'ndan eklenti atamak için Merkezi Dağıtım'ı kullanmasını engellemez.

> [!NOTE] 
> Visio Veri Görselleştiricisi, Bing Haritalar ve Kişiler Graph gibi eklentiler, yönetici Mağaza'yı devre dışı bırakmış olsa bile şeritte görünmeye devam eder. Bu bağlantıları kaldırmak için yöneticilerin Mağaza'yı grup ilkesi Nesnesi (GPO) aracılığıyla devre dışı bırakması gerekir.
  
Kullanıcının Microsoft hesabıyla oturum açmasını engellemek için, oturum açmayı yalnızca kuruluş hesabını kullanacak şekilde kısıtlayabilirsiniz. Daha fazla bilgi için bkz. [Office 2016'da kimlik, kimlik doğrulaması ve yetkilendirme](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Kullanıcıların office mağazasına erişmesini engellemek, [ağ paylaşımından test için Office Eklentileri Dışarıdan Yüklemelerini](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins) de engeller.

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Eklentilerle son kullanıcı deneyimi hakkında daha fazla bilgi

Bir eklentiyi dağıttığınızda, son kullanıcılarınız eklentiyi kendi Office uygulamalarında kullanmaya başlayabilir. Eklenti, eklentinin desteklediği tüm platformlarda görünür. Bkz. [Office Eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
Eklenti, eklenti komutlarını destekliyorsa bu komutlar Office şeridinde görünür. Aşağıdaki örnekte **Alıntılar** eklentisinin **Alıntı Ara** komutu görünür. 

![Arama Alıntıları ile şeridi Office.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Dağıtılmış eklenti, eklenti komutlarını desteklemiyorsa veya dağıtılmış tüm eklentileri görmek istiyorsanız, bunları **Eklentilerim** bölümünde görüntüleyebilirsiniz. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Word 2016, Excel 2016 veya PowerPoint 2016'da

1. **Eklentilerimi Ekle'yi \>** seçin. 
    
2. Office Eklentileri penceresinde **Yönetici Tarafından Yönetilen** sekmesini seçin. 
    
3. Daha önce dağıtılan eklentiye (bu örnekte **Alıntılar**) çift tıklayın.

    ![Office Eklentileri sayfasının Yönetilen sekmesini Yönetici.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Outlook'ta

1. **Giriş** şeridinde **Eklentileri Al'ı** seçin.

    ![Outlook'de Depola düğmesi.](../../media/getaddinsicon.png)
  
2. Sol gezinti bölmesinden **Yönetici tarafından yönetilen**'i seçin. 

## <a name="related-content"></a>İlgili içerik

[küçükler ve Microsoft Store eklentileri alma](./minors-and-acquiring-addins-from-the-store.md)

