---
title: Geliştirme/test ortamında bir ekibi güvenlik yalıtımıyla yapılandırma
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
description: Çalışanlarınızın her yerden ve her zaman uzaktan çalışmasını sağlayan güvenlik ve altyapıyı yapılandırın.
ms.openlocfilehash: 0e54d3840e9207fd7e8b5c50415ad2ca60751059
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934257"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Geliştirme/test ortamında bir ekibi güvenlik yalıtımıyla yapılandırma

Bu makale, geliştirme/test ortamında [güvenlik yalıtımına sahip bir ekip](secure-teams-security-isolation.md) oluşturmak için adım adım yönergeler sağlar.

[Şirket Stratejisi yalıtılmış ekibi için yapılandırma.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Üretimde bu tür bir ekibi dağıtmadan önce bu geliştirme/test ortamını kullanarak belirli ihtiyaçlarınıza yönelik denemeler yapın ve ayarlarda ince ayar yapın.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>1. Aşama: Microsoft 365 Kurumsal test ortamınızı oluşturma

Hassas ve son derece hassas ekipleri minimum gereksinimlerle basit bir şekilde test etmek istiyorsanız [Basit temel yapılandırma](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.

Sanal bir kuruluşta hassas ve son derece hassas ekipleri test etmek istiyorsanız [Parola karması eşitlemesi](../enterprise/password-hash-sync-m365-ent-test-environment.md) başlığı altında yer alan yönergeleri izleyin.

> [!NOTE]
> Bir ekibi güvenlik yalıtımıyla test etmek, İnternet'e bağlı bir sanal intranet ve bir Active Directory Domain Services (AD DS) ormanı için dizin eşitlemesi içeren sanal kurumsal test ortamını gerektirmez. Burada, bir ekibi güvenlik yalıtımıyla test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>2. Aşama: Azure Active Directory (Azure AD) grubunuzu ve kullanıcılarınızı oluşturma ve yapılandırma

Bu aşamada, kurgusal kuruluşunuz için bir Azure AD grubu ve kullanıcıları oluşturup yapılandıracaksınız.

İlk olarak, Azure portal ile bir güvenlik grubu oluşturun.

1. Tarayıcınızda ayrı bir sekme oluşturun ve konumundaki Azure portal [https://portal.azure.com](https://portal.azure.com)gidin. Gerekirse, Microsoft 365 E5 deneme sürümünüz veya ücretli aboneliğiniz için genel yönetici hesabının kimlik bilgileriyle oturum açın.

2. Azure portal Azure Active Directory > **Grupları'na** tıklayın.

3. **Gruplar - Tüm gruplar** dikey penceresinde **+ Yeni grup'a** tıklayın.

4. **Grup** dikey penceresinde:

  - **Grup türünde Güvenlik'i** seçin.

  - **Ad** alanına **C-Suite** yazın.

  - **Üyelik türünde** **Atanan'ı** seçin.

5. **Oluştur'a** tıklayın ve ardından **Grup** dikey penceresini kapatın.

Ardından, yeni **C-Suite** grubu üyelerine otomatik olarak bir Microsoft 365 E5 lisansı atanması için otomatik lisanslamayı yapılandırın.

1. Azure portal Azure Active Directory > **Lisanslar > Tüm ürünler'e** tıklayın.

2. Listede **Microsoft 365 Kurumsal E5'i** seçin ve **ata'ya** tıklayın.

3. **Lisans ata** dikey penceresinde **Kullanıcılar ve gruplar'a** tıklayın.

4. Grup listesinde **C-Suite** grubunu seçin.

5. **Seç'e** ve ardından **Ata'ya** tıklayın.

6. Tarayıcınızda Azure portal sekmesini kapatın.

Ardından [Graph için Azure Active Directory PowerShell modülüne bağlanın](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Kuruluşunuzun adını, konumunuzu ve ortak bir parolayı doldurun ve ardından powershell komut isteminden veya Tümleşik Betik Ortamı'ndan (ISE) bu komutları çalıştırarak yeni kullanıcı hesapları oluşturun ve bunları C-Suite grubuna ekleyin:

```powershell
$orgName="<organization name, such as contoso-test for the contoso-test.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Burada yaygın bir parolanın kullanımı, geliştirme/test ortamı için otomasyon ve yapılandırma kolaylığıdır. Açıkçası, üretim abonelikleri için bu kesinlikle önerilmez.

Grup tabanlı lisanslamanın düzgün çalıştığını doğrulamak için bu adımları kullanın.

1. [Microsoft 365 yönetici merkezi](https://admin.microsoft.com)'nde oturum açın.

2. Tarayıcınızın yeni **Microsoft 365 yönetim merkezi** sekmesinde **Kullanıcılar'a** tıklayın.

3. Kullanıcı listesinde **CEO'ya** tıklayın.

4. **CEO** kullanıcı hesabının özelliklerini listeleyen bölmede, **ürün lisanslarında** **Microsoft 365 Kurumsal E5** lisansının atandığını doğrulayın.

## <a name="phase-3-create-your-team"></a>3. Aşama: Ekibinizi oluşturma

Bu aşamada, üst düzey liderlik ekibinin üyelerinin şirket stratejisi üzerinde işbirliği yapmasına yönelik güvenlik yalıtımına sahip bir ekip oluşturup yapılandıracaksınız.

İlk olarak, [bu makaledeki](../compliance/sensitivity-labels-teams-groups-sites.md) adımlara geçmeden önce Microsoft Teams, Office 365 grupları ve SharePoint sitelerdeki içeriği korumak için duyarlılık etiketlerini etkinleştirin.

Ardından ekibi oluşturun:

1. Teams'da, uygulamanın sol tarafındaki **Teams'e** tıklayın ve ardından ekip listesinin en altında **Katıl'a veya ekip oluştur'a** tıklayın.
2. **Ekip oluştur'a** tıklayın (ilk kart, sol üst köşe).
3. **Sıfırdan ekip oluştur'u** seçin.
4. **Duyarlılık** listesinde varsayılanı koruyun.
5. **Gizlilik'in** altında **Özel'e** tıklayın.
6. **Şirket Stratejisi** yazın ve Ardından **OluşturKapat'a** >  tıklayın.

Ardından, özel kanalların oluşturulmasını Şirket Stratejisi grubunun sahipleriyle kısıtlayın.

1. Ekipte **Diğer seçenekler'e** ve ardından **Ekibi yönet'e** tıklayın.
2. **Ayarlar** sekmesinde **Üye izinleri'ni** genişletin.
3. **Üyelerin özel kanal oluşturmasına izin ver** onay kutusunu temizleyin.

Ardından, aşağıdaki ayarlarla bir duyarlılık etiketi yapılandırmanız gerekir:

- Adı Şirket Stratejisidir
- Şifreleme etkinleştirildi
- Şirket Stratejisi grubunun Co-Author izinleri vardır

Şu adımları izleyin:

1. Microsoft Purview uyumluluk portalını açın, **Çözümler'in** altında <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Bilgi koruması'nı**</a> seçin.
1. **Etiket oluştur'a** tıklayın.
1. Etiket adı için **Şirket Stratejisi** yazın.
1. Araç ipucu olarak **Üst düzey liderlik şirketi stratejisi belgelerini** yazın ve **İleri'ye** tıklayın.
1. **Şifreleme** sayfasındaki **Şifreleme** açılan listesinde **Uygula'yı** seçin.
1. Ekip izinlerini eklemek için:<br>
  a. **İzin ata'ya** tıklayın.<br>
  b. **Kullanıcı veya grup ekle'ye** tıklayın, **Şirket Stratejisi'ne** ve ardından **Ekle'ye** tıklayın.<br>
  c. **İzinleri seç'e** tıklayın.<br>
  d. Açılan **listeden Birlikte Yaz'ı** seçin ve **kaydet'e** tıklayın.<br>
1. **İleri**'ye tıklayın.
1. **İçerik işaretleme** sayfasında **İleri'ye** tıklayın.
1. **Site ve grup ayarları** sayfasında **Site ve grup ayarlarını** **Açık** olarak ayarlayın.
1. **Gruba bağlı Office 365 ekip sitelerinin gizliliği** açılan listesinde **Özel'i seçin. Siteye yalnızca üyeler erişebilir**.
1. **Yönetilmeyen cihazlar'ın** altında **Erişimi engelle'yi** seçin.
1. **İleri**'ye tıklayın.
1. **Office uygulamalar için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
1. **Gönder'e** ve ardından **Bitti'ye** tıklayın.

Ardından, yeni etiketi şu adımlarla yayımlayın:

1. Microsoft Purview uyumluluk portalında <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**, Bilgi koruması'nda**</a> **Etiket ilkeleri** sekmesini seçin.
2. **Etiketleri yayımla'ya** tıklayın.
3. **Yayımlamak için duyarlılık etiketlerini seçin sayfasında, Yayımlamak** **için duyarlılık etiketlerini seçin'e** tıklayın.
4. **Şirket Stratejisi'ne** tıklayın ve **ekle'ye** tıklayın.
5. **İleri**'ye tıklayın.
6. **Kullanıcılara ve gruplara yayımla** sayfasında **Kullanıcıları ve grupları seç'e** tıklayın.
7. **Ekle'ye** tıklayın ve ardından **Şirket Stratejisi'ne** tıklayın.
8. **Ekle'ye** ve ardından **Bitti'ye** tıklayın.
9. **İleri**'ye tıklayın.
10. İlke ayarları sayfasında, **Kullanıcılar bir etiketi veya daha düşük sınıflandırma etiketini kaldırmak için gerekçe sağlamalıdır** onay kutusunu seçin ve **ardından İleri'ye** tıklayın.
11. İlke adı için **Şirket Stratejisi** yazın ve **İleri'ye** tıklayın.
12. **Gönder'e** ve ardından **Bitti'ye** tıklayın.

**Şirket Stratejisi** etiketinin yayımlandıktan sonra kullanıma sunulması biraz zaman alabilir.

Ardından, yeni etiketinizi **Şirket Stratejisi** ekibine uygulayın ve dosya ve klasörleri yanlışlıkla hedeflenenden daha geniş bir hedef kitleye paylaşma riskini azaltmak için varsayılan paylaşım bağlantı türünü güncelleştirin.

1. SharePoint yönetim merkezini açın, **Siteler'in** altında <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> seçin.
1. **Şirket Stratejisi** sitesini seçin.
1. **İlkeler** sekmesindeki **Duyarlılık'ın** altında **Düzenle'yi** seçin.
1. **Şirket Stratejisi** etiketini ve ardından **Kaydet'i** seçin.
1. **İlkeler** sekmesinde, **Dış paylaşım'ın** altında **Düzenle'yi** seçin.
1. **Yalnızca kuruluşunuzdaki kişileri** seçin.
1. **Varsayılan paylaşım** bağlantı türü'nün altında **Kuruluş düzeyi ayarıyla aynı** onay kutusunu temizleyin ve **Mevcut erişimi olan kişiler'i** seçin.
1. **Kaydet**'i seçin.

Ardından, **Şirket Stratejisi** ekibi için yalnızca sahiplere yönelik site paylaşımını yapılandırın.

1. Teams'da **Şirket Stratejisi** ekibinin **Genel** sekmesine gidin.
2. Ekibin araç çubuğunda **Dosyalar'a** tıklayın.
3. Üç noktaya tıklayın ve ardından **SharePoint aç'a** tıklayın.
4. Temel alınan SharePoint sitesinin araç çubuğunda ayarlar simgesine ve ardından **Site izinleri'ne** tıklayın.
5. Site izinleri bölmesinde, **Site Paylaşımı'nın** altında Üyelerin **paylaşım şeklini değiştir'e** tıklayın.
6. **Paylaşım izinleri'nin** altında **Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir'i seçin ve** **Kaydet'e** tıklayın.
7. **İzinler** ve **Ayarlar** bölmelerini kapatın.

Şirket Stratejisi grubunun üyesi olarak oturum açarsanız, Word, Excel ve PowerPoint Giriş araç **çubuğundaki Duyarlılık** seçeneğinde **Şirket Stratejisi'ni** görürsünüz. Etiketi bir dosyaya atamak için **Duyarlılık** seçeneğinden **Şirket Stratejisi** etiketini seçin.

Şirket Stratejisi ekibi için elde edilen yapılandırma aşağıdadır.

![Şirket Stratejisi yalıtılmış ekibi için yapılandırma.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Sonraki adım

Üretim dağıtımına hazır olduğunuzda bu [yapılandırma yönergelerine](secure-teams-security-isolation.md) bakın.
