---
title: Geliştirme/test ortamında güvenlik yalıtlığı olan bir ekibi yapılandırma
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
description: Çalışanlarınızı her yerden ve zamanda uzaktan çalışmalarına olanak sağlayan güvenlik ve altyapıyı yapılandırabilirsiniz.
ms.openlocfilehash: 8ea359f2c0de98ac35b90a379e5a60c4578e66cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323423"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Geliştirme/test ortamında güvenlik yalıtlığı olan bir ekibi yapılandırma

Bu makalede, bir geliştirme/test ortamında güvenlik yalıtlığı olan bir ekibi [oluşturmak](secure-teams-security-isolation.md) için adım adım yönergeler sağlar.

[Şirket Stratejisi yalıtılmış ekibin yapılandırması.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Bu türde ekibi üretimde dağıtmadan önce kendi özel ihtiyaçlarınıza yönelik ayarları denemek ve ince ayar yapmak için bu geliştirme/test ortamını kullanın.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Aşama 1: Test ortamınızı Microsoft 365 Kurumsal oluşturma

Yalnızca hassas ve çok hassas ekipleri en düşük gereksinimlerle hafif bir şekilde test etmek için Hafif taban yapılandırma [yönergelerini izleyin](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md).

Sanal bir kuruluşta hassas ve çok hassas ekipleri sınamak için Parola karması [eşitlemesi'nin yönergelerini izleyin](../enterprise/password-hash-sync-m365-ent-test-environment.md).

> [!NOTE]
> Güvenlik yalıtımlı bir ekibi test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada bir seçenek olarak sağlanır; böylelikle, bir ekibi güvenlik yalıtlığı ile test eder ve tipik bir kuruluşu temsil eden bir ortamda bu sınamayı sınabilirsiniz.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>Aşama 2: Grup (Azure AD) Azure Active Directory kullanıcılarınızı oluşturma ve yapılandırma

Bu aşamada, kurgusal organizasyonunız için bir Azure AD grubu ve kullanıcıları oluşturabilir ve yapılandırabilirsiniz.

İlk olarak, Azure portalıyla bir güvenlik grubu oluşturun.

1. Tarayıcınızda ayrı bir sekme oluşturun ve ardından 'da Azure portalına gidin [https://portal.azure.com](https://portal.azure.com). Gerekirse, deneme veya ücretli aboneliğiniz için genel yönetici hesabının Microsoft 365 E5 oturum açın.

2. Azure portalında Grup **Ekle'Azure Active Directory > tıklayın**.

3. Gruplar **- Tüm gruplar blade'de** , **+ Yeni grup'a tıklayın**.

4. Grup **blade'inde** :

  - Grup **türü'ne** **göre Güvenlik'i seçin**.

  - Ad **kutusuna C-Suite** **yazın**.

  - Üyelik **türü'ne** **atanan'ı seçin**.

5. **Oluştur'a** tıklayın ve sonra Grup **Blade'ini** kapatın.

Ardından, otomatik lisanslamayı yapılandırarak yeni **C-Suite** grubunun üyelerine otomatik olarak lisans Microsoft 365 E5 gerekir.

1. Azure portalında, Tüm ürünler **için Azure Active Directory > Lisansları > tıklayın**.

2. Listede **E5'e Microsoft 365 Kurumsal ardından** Ata'ya **tıklayın**.

3. Lisans blade **atama'da** Kullanıcılar ve **gruplar'a tıklayın**.

4. Grup listesinde **C-Suite grubunu** seçin.

5. **Seç'e** ve ardından **Ata'ya tıklayın**.

6. Tarayıcınızda Azure portal sekmesini kapatın.

Ardından, [Graph modülü için Azure Active Directory PowerShell'e bağlanın](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Yeni kullanıcı hesapları oluşturmak ve bunları C-Suite grubuna eklemek için, kuruluş adı, konum ve ortak bir parola girin ve powershell komut isteminden veya Tümleşik Betik Ortamı'nda (ISE) bu komutları çalıştırın:

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
> Burada yaygın kullanılan bir parolanın kullanımı, geliştirme/test ortamının otomasyonunu ve yapılandırmasını kolaylaştırmaktır. Bu, üretim abonelikleri için kesinlikle önerilmez.

Grup tabanlı lisanslamanın düzgün çalıştığını doğrulamak için bu adımları kullanın.

1. [Microsoft 365 yönetici merkezi](https://admin.microsoft.com)'nde oturum açın.

2. Tarayıcınızın yeni **Microsoft 365 yönetim merkezi** Kullanıcılar'a **tıklayın**.

3. Kullanıcı listesinde CEO'ya **tıklayın**.

4. **CEO** kullanıcı hesabının özelliklerini listeleen bölmede, Ürün lisanslarında bu hesaba **Microsoft 365 Kurumsal E5** lisansı **atan olduğunu doğrulayın**.

## <a name="phase-3-create-your-team"></a>Aşama 3: Ekibinizi oluşturma

Bu aşamada, üst yönetim ekibinin üyeleri için şirket stratejisi üzerinde işbirliği yapmak üzere güvenlik yalıtlığı olan bir ekip oluşturabilir ve yapılandırmış durumdayız.

İlk olarak, bu makaledeki adımlarla devam Microsoft Teams, Office 365 grupları ve SharePoint sitelerinin içeriğini korumak için duyarlılık [etiketlerini etkinleştirin](../compliance/sensitivity-labels-teams-groups-sites.md).

Ardından ekibi oluşturun:

1. Ekip Teams, **uygulamanın Teams** tarafındaki Ekip Ekle'ye tıklayın ve ekip listesinin alt kısmından Takıma katıl  veya ekip oluştur'a tıklayın.
2. Ekip **oluştur'a** (ilk kart, sol üst köşede) tıklayın.
3. **Sıfırdan ekip oluşturma'yi seçin**.
4. Duyarlılık **listesinde varsayılanı** kullanın.
5. **Gizlilik'in** altında **Özel'e tıklayın**.
6. Şirket **Stratejisi yazın ve** ardından **Oluştur'a** >  **tıklayın**.

Daha sonra, özel kanal oluşturulmasını Şirket Stratejisi grubunun sahipleriyle sınırlandırın.

1. Ekipte Diğer **seçenekler'e ve sonra** da Ekibi yönet'e **tıklayın**.
2. Ekle **Ayarlar** Üye **izinleri'ne tıklayın**.
3. Üyelerin **özel kanal oluşturmasına izin ver onay** kutusunu temizleyin.

Ardından, aşağıdaki ayarlara sahip bir duyarlılık etiketi yapılandırmamız gerekir:

- Bu ad Şirket Stratejisi'nedir
- Şifreleme etkinleştirildi
- Şirket Stratejisi grubunun güvenlik Co-Author vardır

Şu adımları izleyin:

1. Çalışma Microsoft 365 uyumluluk merkezi **Çözümler'in altında** Bilgi <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**koruması'ı seçin**</a>.
1. Etiket **oluştur'a tıklayın**.
1. Etiket **adı için** Şirket Stratejisi yazın.
1. Araç **ipucu olarak Üst düzey liderlik şirketi** strateji belgeleri yazın ve ardından Sonraki'ye **tıklayın**.
1. Şifreleme **sayfasındaki** Şifreleme açılan **listesinde** Uygula'ya **tıklayın**.
1. Ekip izinlerini eklemek için:<br>
  a. İzinleri **ata'ya tıklayın**.<br>
  b. Kullanıcı **veya grup ekle'ye tıklayın**, Şirket **Stratejisi'ne** ve ardından Ekle'ye **tıklayın**.<br>
  c. İzinleri **seç'e tıklayın**.<br>
  d. Açılan **listeden Ortak Yazar'ı** seçin ve ardından Kaydet'e **tıklayın**.<br>
1. **İleri**'ye tıklayın.
1. İçerik işaretleme **sayfasında,** Sonraki'ne **tıklayın**.
1. Site ve **grup ayarları sayfasında** , **Site ve grup ayarlarını On olarak** **ayarlayın**.
1. Grup **bağlantılı ekip siteleri Office 365 açılan listesinde** Özel - yalnızca üyeler siteye erişebilirsiniz'i **seçin**.
1. **Unmanaged devices altında Block** **access'i seçin**.
1. **İleri**'ye tıklayın.
1. Uygulamalarınız **için otomatik etiket Office, Ardından'ya** **tıklayın**.
1. **Gönder'e** ve ardından **Bitti'ye tıklayın**.

Ardından, yeni etiketi şu adımlarla yayımlayın:

1. Etiket Microsoft 365 uyumluluk merkezi, <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Bilgi koruması'nın**</a> Etiket ilkeleri **sekmesini** seçin.
2. Etiketleri **yayımla'ya tıklayın**.
3. Yayımlayacak **duyarlılık etiketlerini seçin sayfasında** Yayımlayacak duyarlılık **etiketlerini seç'e tıklayın**.
4. Şirket **Stratejisi'ne** ve ardından Ekle'ye **tıklayın**.
5. **İleri**'ye tıklayın.
6. Kullanıcılar ve **gruplara yayımla sayfasında** Kullanıcıları ve **grupları seç'e tıklayın**.
7. **Ekle'ye** tıklayın ve ardından Şirket **Stratejisi'ne tıklayın**.
8. **Ekle'ye** ve ardından **Bitti'ye tıklayın**.
9. **İleri**'ye tıklayın.
10. İlke ayarları sayfasında, Kullanıcılar bir etiketi **veya daha düşük** bir sınıflandırma etiketini kaldırmak için gerekçe sağlamalı onay kutusunu seçin ve sonra da Sonraki'ye **tıklayın**.
11. **İlke adı olarak** Şirket Stratejisi yazın ve Ardından Sonraki'ye **tıklayın**.
12. **Gönder'e** ve ardından **Bitti'ye tıklayın**.

Şirket Stratejisi etiketinin **yayımlandıktan** sonra kullanılabilir olması biraz zaman alıyor olabilir.

Ardından, yeni etiketinizi Şirket Stratejisi ekibine uygulayın ve yanlışlıkla dosya ve klasör paylaşma riskini hedef kitleye göre daha geniş bir kitleye azaltmak için varsayılan paylaşım bağlantı türünü güncelleştirin.

1. Siteler'SharePoint Etkin **siteler'i seçin**<a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**.**</a>
1. Şirket Stratejisi **sitesini** seçin.
1. **İlkeler sekmesindeki** **Duyarlılık'ın altında** Düzenle'yi **seçin**.
1. Şirket Stratejisi **etiketini seçin** ve sonra da Kaydet'i **seçin**.
1. **İlkeler sekmesindeki** Dış **paylaşım'ın altında** Düzenle'yi **seçin**.
1. Yalnızca **kuruluşta olan kişiler'i seçin**.
1. Varsayılan **paylaşım bağlantı** türü'nin altında Kuruluş **düzeyi ayarıyla aynı onay kutusunu temizleyin** ve Varolan erişimi olan **kişiler'i seçin**.
1. **Kaydet**'i seçin.

Ardından, Şirket Stratejisi ekibi için yalnızca sahipler için **site paylaşımını** yapılandırın.

1. Şirket Teams'de, **Şirket Stratejisi ekibinin** Genel **sekmesine** gidin.
2. Ekibin araç çubuğunda Dosyalar'a **tıklayın**.
3. Üç noktayı tıklatın ve sonra Üç **Nokta'da Aç'ı SharePoint**.
4. Temel sitenin araç çubuğunda SharePoint simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
5. Site izinleri bölmesinde, Site **Paylaşımı'nın altında Üyelerin** **paylaşma seçeneğini değiştir'e tıklayın**.
6. Paylaşım **izinleri'nin** **altında Yalnızca site sahipleri dosyaları, klasörleri ve siteyi** paylaşabilir'i seçin ve Kaydet'e **tıklayın**.
7. İzinler **ve** Gezinti **Ayarlar** kapatın.

Şirket Stratejisi grubunun bir üyesi olarak oturum alıyorsanız Word, Excel ve PowerPoint'nin  Giriş araç çubuğundaki  Duyarlılık seçeneğinde Şirket Stratejisi'PowerPoint. Etiketi **bir dosyaya** atamak için **Duyarlılık seçeneğinden** Şirket Stratejisi etiketini seçin.

Şirket Stratejisi ekibi için sonuçta elde edilen yapılandırma şu şekildedir.

![Şirket Stratejisi yalıtılmış ekibin yapılandırması.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Sonraki adım

Üretim dağıtımına hazır olduğunda bu yapılandırma [yönergelerine bakın](secure-teams-security-isolation.md).
