---
title: Merkezi Dağıtım eklentilerinin kurum için uygun olup olmadığını belirleme
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
description: Kiracınızı ve kullanıcılarınızı gereksinimleri karşılamıyorsa, bu şekilde merkezi dağıtım kullanarak eklentilerin dağıtımını Office gerekir.
ms.openlocfilehash: 856e48db79627e0e736c05fe0062680017e24418
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506977"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Merkezi Dağıtım eklentilerinin kurum için uygun olup olmadığını belirleme

Merkezi Dağıtım, çoğu müşteri için önerilen ve özellik açısından en zengin yol Office kullanıcılara ve gruplara dağıtım yapmaktır. Yöneticiyseniz, Merkezi Dağıtım'ı kullanmak için kuruluş ve kullanıcılarının gereksinimleri karşı olup olmadığını belirlemek üzere bu kılavuzu kullanın.

Merkezi Dağıtım şu avantajları sağlar:

- Yönetici, bir eklentiyi doğrudan bir kullanıcıya, bir grup aracılığıyla birden çok kullanıcıya veya kuruluşta yer alan herkese dağıtarak atayır (bilgi için bkz. Yönetici gereksinimi bölümü).
- Eklenti, Office başlatıldığında otomatik olarak indirilir. Eklenti, eklenti komutlarını destekliyorsa, eklenti aynı uygulamanın içindeki şeritte otomatik olarak Office görünür.
- Yönetici eklentiyi kapatıyor veya silebilirse ya da kullanıcı eklentinin atandığı gruptan Azure Active Directory, eklenti artık kullanıcılara görünmez.

Merkezi Dağıtım, Mac ve Online Windows uygulamalarının üç masaüstü Office destekler. Merkezi Dağıtım iOS ve Android (Yalnızca Outlook Mobil Eklentileri) de destekler.

Tüm kullanıcılar için eklentinin istemcide görünmesi 24 saati bulabilir.

## <a name="before-you-begin"></a>Başlamadan önce

Eklentilerin merkezi dağıtımı, kullanıcıların Microsoft 365 İş lisansları (İş Temel, İş Standart, İş Premium), Office 365 Kurumsal lisansları (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisansları (E3/E5/F3) (E3/E5/F3) kullanıyor ve Office  (A3/A5) Office 365 Eğitim lisansları (A1/A3/A5) veya Microsoft 365 Eğitim lisansları (A3/A5) ve posta kutularına sahip Exchange Online sahip Exchange Online kullanabilirsiniz. Abonelik dizininizin başka bir dizinde veya başka bir Azure Active Directory.
Aşağıdaki Uyumluluk Ayarları ve Uyumluluk Office Exchange veya Merkezi Dağıtım Uyumluluk [Denetleyicisi'ni kullanabilirsiniz](#centralized-deployment-compatibility-checker).

Merkezi Dağıtım şunları desteklemez:

- MSI sürümünü hedef Office eklentiler (diğer Outlook 2016)
- Şirket içi dizin hizmeti
- Posta Kutusu Için Exchange Eklenti Dağıtımı
- SharePoint'e eklenti dağıtımı
- Teams uygulamaları
- Bileşen Nesne Modeli (COM) veya Office için Visual Studio Araçları (VSTO) eklentilerinin dağıtımı.
- SKus Microsoft 365 SKus: Exchange Online ve İş için Microsoft 365 Uygulamaları gibi Microsoft 365 Uygulamaları dağıtımları Enterprise.

### <a name="office-requirements"></a>Office Gereksinimleri

- Word, Excel ve PowerPoint eklentileri için kullanıcılarınızı aşağıdakilerden birini kullanıyor olması gerekir:
  - Windows cihazında, Microsoft 365 İş lisanslarının Sürüm 1704 veya daha sonraki bir sürümünde (İş Temel, İş Standart, İş Premium), Office 365 Kurumsal lisansları (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisansları (E3/E5/F3).
  - Mac'te, Sürüm 15.34 veya sonraki bir sürümde.

- Bu Outlook için, kullanıcılarınızı aşağıdakilerden birini kullanıyor olması gerekir:
  - Microsoft 365 İş lisanslarının 1701 sürümü veya daha sonraki sürümü (İş Temel, İş Standart, İş Premium), Office 365 Kurumsal lisansları (E1/E3/E5/F3) veya Microsoft 365 Kurumsal lisansları (E3/E5/F3).
  - 2019 ya da 1808 Office Professional Plus 2019 Office Standard.
  - Office Professional Plus 2016 (MSI) veya Office Standard 2016 (MSI) sürüm 16.0.4494.1000 veya sonrası\*
  - Office Professional Plus 2013 (MSI) veya Office Standard 2013 (MSI) sürümünün 15.0.4937.1000 veya Office Standard sürümü\*
  - Sonraki sürüm 16.0.9318.1000 veya Office Mac 2016
- iOS için mobil uygulamanın 2.75.0 Outlook sürümü
- Android için mobil uygulamanın 2.2.145 Outlook sürümü

    *Eklentilerin MSI Outlook", "Eklentilerim" bölümünde değil, uygun Outlook eklentiler şeridinde yönetici tarafından yüklenmiş eklentileri gösterir.

### <a name="exchange-online-requirements"></a>Exchange Online gereksinimleri

Microsoft Exchange, eklenti bildirimlerini kuruluşunuzun kiracısında depolar. Eklentileri dağıtan yönetici ve bu eklentileri alan kullanıcıların OAuth kimlik doğrulamasını destekleyen bir Exchange Online sürümünde olması gerekir.

Kullanılan mevcut yapılandırmanın hangisi olduğunu öğrenmek için kuruluşunuzun Exchange yöneticisiyle görüşün. Kullanıcı başına OAuth bağlantısı, [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell cmdlet komutu kullanılarak doğrulanabilir.

### <a name="admin-requirements"></a>Yönetici gereksinimleri

Bir eklentiyi Merkezi Dağıtım yoluyla dağıtmak için Genel yönetici veya kuruluşta Exchange yönetici olmak gerekir.

> [!NOTE]
> Bir Exchange yöneticisi, aşağıdaki resimde gösterildiği gibi Uygulama Yöneticisi rolü ekleniyorsa veya Uygulama Kayıtları özelliği Azure Active Directory merkezinde true  olarak ayarlanmışsa eklentiyi dağıtabilirsiniz:
>
> ![görüntü](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Merkezi Dağıtım Uyumluluk Denetleyicisi

Merkezi Dağıtım Uyumluluk Denetleyicisi'ni kullanarak, kiracınız kullanıcılarının Word, Excel ve PowerPoint için Merkezi Dağıtım'ı kullanmak üzere ayar PowerPoint. Outlook desteği için Uyumluluk Denetleyicisi gerekmez. Uyumluluk [denetleyicisini indirin](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Uyumluluk denetleyicisini çalıştırma

1. Yükseltilmiş PowerShell.exe penceresini başlatın.

2. Aşağıdaki komutu çalıştırın:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. **Invoke-CompatibilityCheck komutunu** çalıştırın:

   ```powershell
   Invoke-CompatibilityCheck
   ```

   Bu komut sizden _TenantDomain_ (örneğin, _TailspinToysIncorporated.onmicrosoft.com_) ve _TenantAdmin_ kimlik bilgilerini (genel yönetici kimlik bilgilerinizi kullanma) istendiğinde ve ardından izin istiyor.

   > [!NOTE]
   > Kiracınızdaki kullanıcıların sayısına bağlı olarak, denetleyici dakikalar içinde veya saatler içinde tamamlanabilir.

Aracın çalışması bittiğinde, virgülle ayrılmış dosya (.csv) biçiminde bir çıkış dosyası üretir. Dosya varsayılan olarak geçerli **çalışma dizinine** kaydedilir. Çıkış dosyası aşağıdaki bilgileri içerir:

- Kullanıcı Adı
- Kullanıcı Kimliği (Kullanıcının e-posta adresi)
- Merkezi Dağıtım için hazır - Diğer öğeler doğruysa
- Office planı - Office lisansına sahip olduğu iş planı
- Office Etkinleştirildi - Office'i etkinleştirdiyse
- Desteklenen Posta Kutusu - OAuth özellikli bir posta kutusu kullanıyorsa

> [!NOTE]
> Çok faktörlü kimlik doğrulaması, Merkezi Dağıtım PowerShell modülü kullanılırken desteklanmaz. Modül yalnızca Temel kimlik doğrulamasıyla çalışır.

## <a name="user-and-group-assignments"></a>Kullanıcı ve grup atamaları

Merkezi Dağıtım özelliği şu anda grup grupları, dağıtım listeleri ve güvenlik grupları Azure Active Directory grupları Microsoft 365 grupların çoğunu destekler.

> [!NOTE]
> Posta hesabı etkin olmayan güvenlik grupları şu anda desteklenmemektedir.

Merkezi Dağıtım tek tek kullanıcılara, gruplara ve kiracıya herkesin atamalarını destekler. Merkezi Dağıtım, üst düzey gruplardaki veya üst grupları olmayan gruplardaki kullanıcıları destekler, ancak iç içe gruplardaki veya üst grupları olan gruplardaki kullanıcıları desteklemez.

Merve, Zeynep ve Satış Bölümü grubunun bir eklentiye atandığı aşağıdaki örneğe bakın. Batı Sahili Satış Bölümü iç içe bir grup olduğundan, Burak ve Ahmet hiçbir eklentiye atanmaz.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Bir grubun iç içe gruplar içerip içermediğini öğrenme

Bir grubun iç içe gruplar içerip içermediğini saptamanın en kolay yolu, Outlook içindeki kişi kartlarını görüntülemektir. Bir e-postanın To alanına grup  adını girer ve ardından grup adı çöz geldiğinde seçin; grup adı, içinde kullanıcılar mı yoksa iç içe gruplar mı içerdiğini gösterir. Aşağıdaki örnekte, Test Grubu için Outlook kişi kartının **Üyeler** sekmesinde, hiçbir kullanıcıyı olmadığı ve yalnızca iki alt grubu olduğu gösteriliyor.

![Kişi kartının Outlook sekmesi.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Grubun, herhangi bir grubun üyesi olup olmadığını öğrenmek için grubu çözerek ters sorgu da yapabilirsiniz. Aşağıdaki örnekte, Alt Grup 1'in Outlook kişi kartının **Üyelik** sekmesinde, Test Grubunun bir üyesi olduğunu görebilirsiniz.

![Kişi kartının üyelik Outlook.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Alternatif olarak, Azure Active Directory Graph API grupların listesini bulmak için sorgu çalıştırmak üzere Sorgular'ı kullanabilirsiniz. Daha fazla bilgi için bkz[. Gruplar üzerinde işlemler| Graph API başvuru.](/previous-versions/azure/ad/graph/api/groups-operations)

### <a name="contacting-microsoft-for-support"></a>Destek için Microsoft'a başvurma

Siz veya kullanıcılarınız merkezi olarak dağıtılan Web için Office uygulamalarını (Word, Excel, vb.) kullanırken eklentiyi yüklerken sorunlarla karşılaşırsanız, Microsoft desteğine başvurun (nasıl olduğunu [öğrenin](../../business-video/get-help-support.md)). Destek biletine bir Microsoft 365 ortamınız hakkında aşağıdaki bilgileri sağlar.

|Ortam|Hata ayıklama bilgisi|
|---|---|
|Office|Charles/Fiddler günlükleri <br/> Kiracı Kimliği ([nasıl olduğunu öğrenin](/onedrive/find-your-office-365-tenant-id)) <br/> Bağıntı Kimliği. Ofis sayfalarından birinin kaynağını görüntüp Bağıntı Kimliği değerini aratır ve destek için gönderin:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Zengin istemciler (Windows, Mac)|Charles/Fiddler günlükleri <br/> İstemci uygulamasının derleme numaraları (tercihen Dosya/Hesap'tan **ekran görüntüsü)**|

## <a name="related-content"></a>İlgili içerik

[Yönetim merkezinde eklentileri dağıtma (makale](../manage/manage-deployment-of-add-ins.md) )\
[Yönetim merkezinde eklentileri yönetme (makale](manage-addins-in-the-admin-center.md) )\
[Merkezi Dağıtım SSS](../manage/centralized-deployment-faq.yml) (makale)\
[Kurumsal Microsoft 365 son istemciye yükseltme (Office](../setup/upgrade-users-to-latest-office-client.md))
