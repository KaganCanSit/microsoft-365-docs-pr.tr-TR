---
title: Eklentilerin Merkezi Dağıtımının kuruluşunuz için çalışıp çalışmadığını belirleme
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: Office Eklentileri dağıtmak için Merkezi Dağıtım'ı kullanabilmek için kiracınızın ve kullanıcılarınızın gereksinimleri karşılayıp karşılamadığını belirleyin.
ms.openlocfilehash: 4d135e76034880e1419e296f2c201536be98b4bc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093778"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Eklentilerin Merkezi Dağıtımının kuruluşunuz için çalışıp çalışmadığını belirleme

Merkezi Dağıtım, çoğu müşterinin kuruluşunuzdaki kullanıcılara ve gruplara Office Eklentileri dağıtması için önerilen ve en zengin özelliklere sahip yöntemdir. Yöneticiyseniz, kuruluşunuzun ve kullanıcılarınızın Merkezi Dağıtım'ı kullanabilmeniz için gereksinimleri karşılayıp karşılamadığını belirlemek için bu kılavuzu kullanın.

Merkezi Dağıtım şu avantajları sağlar:

- Yönetici bir eklentiyi doğrudan bir kullanıcıya, bir grup aracılığıyla birden çok kullanıcıya veya kuruluştaki herkese dağıtabilir ve atayabilir (bilgi için yönetici gereksinimi bölümüne bakın).
- İlgili Office uygulaması başlatıldığında eklenti otomatik olarak indirilir. Eklenti eklenti komutlarını destekliyorsa, eklenti otomatik olarak Office uygulamasının içindeki şeritte görünür.
- Yönetici eklentiyi kapatır veya silerse veya kullanıcı Azure Active Directory veya eklentinin atandığı bir gruptan kaldırılırsa, eklentiler artık kullanıcılar için görünmez.

Merkezi Dağıtım, Mac ve Çevrimiçi Office uygulamaları Windows üç masaüstü platformlarını destekler. Merkezi Dağıtım ayrıca iOS ve Android'i de destekler (yalnızca mobil eklentiler Outlook).

Tüm kullanıcılar için eklentinin istemcide görünmesi 24 saati bulabilir.

## <a name="before-you-begin"></a>Başlamadan önce

Eklentilerin merkezi dağıtımı için kullanıcıların Microsoft 365 İş lisansları (Business Basic, Business Standard, Business Premium), Office 365 Kurumsal lisansları (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisansları (E3/E5/F3) kullanmaları (ve Office  Office 365 Eğitim lisanslarını (A1/A3/A5) veya Microsoft 365 Eğitim lisanslarını (A3/A5) kullanarak ve Exchange Online ve etkin Exchange Online posta kutularına sahip olur. Abonelik dizininizin Azure Active Directory içinde veya federasyonda olması gerekir.
Aşağıda Office ve Exchange için belirli gereksinimleri görüntüleyebilir veya [Merkezi Dağıtım Uyumluluk Denetleyicisi'ni](#centralized-deployment-compatibility-checker) kullanabilirsiniz.

Merkezi Dağıtım şunları desteklemez:

- Office MSI sürümünü hedefleyen eklentiler (Outlook 2016 hariç)
- Şirket içi dizin hizmeti
- Exchange Şirket İçi Posta Kutusuna eklenti dağıtımı
- SharePoint'e eklenti dağıtımı
- uygulamaları Teams
- Bileşen Nesne Modeli (COM) veya Office için Visual Studio Araçları (VSTO) eklentilerinin dağıtımı.
- SKU'lar gibi Exchange Online içermeyen Microsoft 365 dağıtımları: İş için Microsoft 365 Uygulamaları ve Enterprise için Microsoft 365 Uygulamaları.

### <a name="office-requirements"></a>Office Gereksinimleri

- Word, Excel ve PowerPoint eklentileri için kullanıcılarınızın aşağıdakilerden birini kullanıyor olması gerekir:
  - Windows bir cihazda, Microsoft 365 İş lisanslarının Sürüm 1704 veya üzeri (Business Basic, Business Standard, Business Premium), Office 365 Kurumsal lisansları (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisansları (E3/E5/F3).
  - Mac'te Sürüm 15.34 veya üzeri.

- Outlook için kullanıcılarınızın aşağıdakilerden birini kullanıyor olması gerekir:
  - Microsoft 365 business lisanslarının (Business Basic, Business Standard, Business Premium), Office 365 Kurumsal lisanslarının (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisanslarının (E3/E5/F3) 1701 veya sonraki sürümleri.
  - Office Professional Plus 2019 veya Office Standard 2019 sürümü 1808 veya üzeri.
  - Office Professional Plus 2016 (MSI) veya Office Standard 2016 (MSI) sürüm 16.0.4494.1000 veya üzeri\*
  - Office Professional Plus 2013 (MSI) veya Office Standard 2013 (MSI) sürümü 15.0.4937.1000 veya üzeri\*
  - Office Mac 2016 Sürüm 16.0.9318.1000 veya üzeri
- iOS için Outlook mobil sürüm 2.75.0 veya üzeri
- Android için Outlook mobil sürüm 2.2.145 veya üzeri

    *Outlook MSI sürümleri, yönetici tarafından yüklenen eklentileri "Eklentilerim" bölümünde değil uygun Outlook şeridinde gösterir.

### <a name="exchange-online-requirements"></a>Exchange Online gereksinimleri

Microsoft Exchange, eklenti bildirimlerini kuruluşunuzun kiracısında depolar. Eklentileri dağıtan yönetici ve bu eklentileri alan kullanıcılar OAuth kimlik doğrulamasını destekleyen bir Exchange Online sürümünde olmalıdır.

Kullanılan mevcut yapılandırmanın hangisi olduğunu öğrenmek için kuruluşunuzun Exchange yöneticisiyle görüşün. Kullanıcı başına OAuth bağlantısı, [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell cmdlet komutu kullanılarak doğrulanabilir.

### <a name="admin-requirements"></a>Yönetici gereksinimleri

Bir eklentiyi Merkezi Dağıtım aracılığıyla dağıtmak için, kuruluşta Genel yönetici veya Exchange yöneticisi olmanız gerekir.

> [!NOTE]
> Uygulama **Yöneticisi** rolü eklendiğinde veya **Uygulama Kayıtları** özelliği aşağıdaki görüntüde gösterildiği gibi Azure Active Directory yönetim merkezinde true olarak ayarlandıysa Exchange yöneticisi bir eklenti dağıtabilir:
>
> ![Görüntü](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Merkezi Dağıtım Uyumluluk Denetleyicisi

Merkezi Dağıtım Uyumluluk Denetleyicisi'ni kullanarak, kiracınızdaki kullanıcıların Word, Excel ve PowerPoint için Merkezi Dağıtım kullanacak şekilde ayarlanıp ayarlanmadığını doğrulayabilirsiniz. Outlook desteği için Uyumluluk Denetleyicisi gerekmez. [Uyumluluk denetleyicisini](https://aka.ms/officeaddindeploymentorgcompatibilitychecker) indirin.

#### <a name="run-the-compatibility-checker"></a>Uyumluluk denetleyicisini çalıştırma

1. Yükseltilmiş PowerShell.exe penceresini başlatın.

2. Aşağıdaki komutu çalıştırın:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. **Invoke-CompatibilityCheck** komutunu çalıştırın:

   ```powershell
   Invoke-CompatibilityCheck
   ```

   Bu komut sizden _TenantDomain_ (örneğin, _TailspinToysIncorporated.onmicrosoft.com_) ve _TenantAdmin_ kimlik bilgilerini (genel yönetici kimlik bilgilerinizi kullanın) ister ve ardından onay ister.

   > [!NOTE]
   > Kiracınızdaki kullanıcıların sayısına bağlı olarak, denetleyici dakikalar içinde veya saatler içinde tamamlanabilir.

Aracın çalışması bittiğinde, virgülle ayrılmış dosya (.csv) biçiminde bir çıkış dosyası üretir. Dosya varsayılan olarak **geçerli çalışma dizinine** kaydedilir. Çıkış dosyası aşağıdaki bilgileri içerir:

- Kullanıcı Adı
- Kullanıcı Kimliği (Kullanıcının e-posta adresi)
- Merkezi Dağıtım için hazır - Diğer öğeler doğruysa
- Office planı - Lisanslandıkları Office planı
- Office Etkinleştirildi - Office'i etkinleştirdiyse
- Desteklenen Posta Kutusu - OAuth özellikli bir posta kutusu kullanıyorsa

> [!NOTE]
> Merkezi Dağıtım PowerShell modülü kullanılırken çok faktörlü kimlik doğrulaması desteklenmez. Modül yalnızca Temel kimlik doğrulaması ile çalışır.

## <a name="user-and-group-assignments"></a>Kullanıcı ve grup atamaları

Merkezi Dağıtım özelliği şu anda Microsoft 365 grupları, dağıtım listeleri ve güvenlik grupları dahil olmak üzere Azure Active Directory tarafından desteklenen grupların çoğunu destekler.

> [!NOTE]
> Posta hesabı etkin olmayan güvenlik grupları şu anda desteklenmemektedir.

Merkezi Dağıtım tek tek kullanıcılara, gruplara ve kiracıdaki herkese atamaları destekler. Merkezi Dağıtım, üst düzey gruplardaki veya üst grupları olmayan gruplardaki kullanıcıları destekler, ancak iç içe gruplardaki veya üst grupları olan gruplardaki kullanıcıları desteklemez.

Merve, Zeynep ve Satış Bölümü grubunun bir eklentiye atandığı aşağıdaki örneğe bakın. Batı Sahili Satış Bölümü iç içe bir grup olduğundan, Burak ve Ahmet hiçbir eklentiye atanmaz.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Bir grubun iç içe gruplar içerip içermediğini öğrenme

Bir grubun iç içe gruplar içerip içermediğini saptamanın en kolay yolu, Outlook içindeki kişi kartlarını görüntülemektir. E-postanın **Kime** alanına grup adını girer ve çözümlendiğinde grup adını seçerseniz, bu ad size kullanıcı veya iç içe gruplar içerip içermediğini gösterir. Aşağıdaki örnekte, Test Grubu için Outlook kişi kartının **Üyeler** sekmesinde, hiçbir kullanıcıyı olmadığı ve yalnızca iki alt grubu olduğu gösteriliyor.

![Outlook kişi kartının Üyeler sekmesi.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Grubun, herhangi bir grubun üyesi olup olmadığını öğrenmek için grubu çözerek ters sorgu da yapabilirsiniz. Aşağıdaki örnekte, Alt Grup 1'in Outlook kişi kartının **Üyelik** sekmesinde, Test Grubunun bir üyesi olduğunu görebilirsiniz.

![Outlook kişi kartının Üyelik sekmesi.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Alternatif olarak, bir grup içindeki grupların listesini bulmak için sorguları çalıştırmak için Azure Active Directory Graph API kullanabilirsiniz. Daha fazla bilgi için bkz[. Gruplarda işlemler| başvuru Graph API](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Destek için Microsoft'a başvurma

Siz veya kullanıcılarınız, merkezi olarak dağıtılan web için Office uygulamaları (Word, Excel vb.) kullanırken eklentiyi yüklerken sorunlarla karşılaşırsanız Microsoft desteğine başvurmanız gerekebilir ([nasıl yapılacağını öğrenin](../../business-video/get-help-support.md)). Destek biletinde Microsoft 365 ortamınız hakkında aşağıdaki bilgileri sağlayın.

|Ortam|Hata ayıklama bilgisi|
|---|---|
|Office|Charles/Fiddler günlükleri <br/> Kiracı Kimliği ([nasıl yapılacağını öğrenin](/onedrive/find-your-office-365-tenant-id)) <br/> Correlationıd. Office sayfalarından birinin kaynağını görüntüleyin ve Bağıntı Kimliği değerini arayın ve destek için gönderin:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Zengin istemciler (Windows, Mac)|Charles/Fiddler günlükleri <br/> İstemci uygulamasının numaralarını oluşturma (tercihen **Dosya/Hesap'tan** ekran görüntüsü olarak)|

## <a name="related-content"></a>İlgili içerik

[Yönetim merkezinde eklentileri dağıtma](../manage/manage-deployment-of-add-ins.md) (makale)\
[Yönetim merkezinde eklentileri yönetme](manage-addins-in-the-admin-center.md) (makale)\
[Merkezi Dağıtım SSS](../manage/centralized-deployment-faq.yml) (makale)\
[İş kullanıcıları için Microsoft 365 en son Office istemcisine](../setup/upgrade-users-to-latest-office-client.md) yükseltme (makale)
