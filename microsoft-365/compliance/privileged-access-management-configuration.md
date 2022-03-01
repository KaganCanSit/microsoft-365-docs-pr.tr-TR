---
title: Ayrıcalıklı erişim yönetimiyle çalışmaya başlama
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: ''
description: Bu makalede, microsoft iş yersinde ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırma hakkında daha fazla bilgi Office 365.
ms.openlocfilehash: fd7216b09b17f7f900a9aee98059918a1796fe19
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2022
ms.locfileid: "63010137"
---
# <a name="get-started-with-privileged-access-management"></a>Ayrıcalıklı erişim yönetimiyle çalışmaya başlama

Bu konu başlığı, kurumda ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırmada size yol sağlar. Ayrıca erişimden yönetmek <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">ve Microsoft 365 yönetim merkezi</a> için Exchange Management PowerShell'i kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Ayrıcalıklı erişim yönetimiyle çalışmaya başlamadan önce, Microsoft 365 [ve tüm](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) eklentileri onaylamanız gerekir. Ayrıcalıklı erişim yönetimine erişmek ve bu erişimi kullanmak için, kuruluş aşağıdaki aboneliklerden veya eklentilerden biri olabilir:

- Microsoft 365 E5 (ücretli veya deneme sürümü)
- Microsoft 365 E3 (veya Office 365 E3 aboneliği + Enterprise Mobil kullanım ve Güvenlik E3 aboneliği) + Microsoft 365 E5 Uyumluluk eklenti
- Tüm Microsoft 365, Office 365, Exchange, SharePoint veya OneDrive İş aboneliği + Microsoft 365 E5 Insider Risk Yönetimi eklentisi
- Microsoft 365 A5 (ücretli veya deneme sürümü)
- Microsoft 365 A3 (veya Office 365 A3 aboneliği + Enterprise Mobility and Security A3 aboneliği) + Microsoft A5 Compliance eklenti
- Eğitim Microsoft 365, Office 365, Exchange, SharePoint veya OneDrive aboneliği + Microsoft 365 A5 Insider Risk Yönetimi eklentisi
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 Kurumsal E3 aboneliği + Office 365 Gelişmiş Uyumluluk eklentiyi içerir (artık yeni abonelikler için kullanılamaz, nota bakın)

Ayrıcalıklı erişim yönetimi isteklerini gönderen ve yanıt veren kullanıcıların yukarıdaki lisanslardan biri atanmış olması gerekir.

> [!IMPORTANT]
> Office 365 Gelişmiş Uyumluluk artık tek başına abonelik olarak satılmaz. Geçerli aboneliklerin süresi dolduğunda, müşteriler aynı veya ek uyumluluk özelliklerini içeren yukarıdaki aboneliklerden birini kullanmalı.

Mevcut bir Office 365 Kurumsal E5 planınız yoksa ve ayrıcalıklı erişim yönetimini denemek için mevcut Office 365 aboneliğinize [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) ekleyebilir veya Microsoft 365 Kurumsal E5 deneme sürümüne kaydolabilirsiniz.[](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="enable-and-configure-privileged-access-management"></a>Ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırma

Kuruluşta ayrıcalıklı erişimi ayarlamak ve kullanmak için şu adımları izleyin:

- [1. Adım: Onaylayan grubu oluşturma](privileged-access-management-configuration.md#step1)

    Ayrıcalık erişimini kullanmaya başlamadan önce, yükseltilmiş ve ayrıcalıklı görevlere erişim için gelen istekler için kimlerin onay yetkisine ihtiyacı olduğunu belirler. Onaylayanlar grubunun bir parçası olan kullanıcılar erişim isteklerini onaylıyor olabilir. Bu grup, E-posta iletisinde posta özellikli bir güvenlik grubu Office 365.

- [2. Adım: Ayrıcalıklı erişimi etkinleştirme](privileged-access-management-configuration.md#step2)

    Ayrıcalıklı erişim, Office 365 yönetimi erişim denetimi dışında tutmak istediğiniz bir dizi sistem hesabı da içinde olmak üzere, varsayılan onaylayan grubuyla birlikte Office 365 açıkça etkinleştirilmelidir.

- [3. Adım: Erişim ilkesi oluşturma](privileged-access-management-configuration.md#step3)

    Onay ilkesi oluşturmak, tek tek görevlerde kapsamı belirli onay gereksinimlerini tanımlamaya olanak sağlar. Onay türü seçenekleri Otomatik veya **El** **ile'ye sahiptir**.

- [4. Adım: Ayrıcalıklı erişim isteklerini gönderme/onaylama](privileged-access-management-configuration.md#step4)

    Etkinleştirildikten sonra, ayrıcalıklı erişim için ilişkili onay ilkesi tanımlanmış herhangi bir görev için onay gerekir. Onay ilkesinde yer alan görevler için, kullanıcıların görevi yürütmek için gerekli izinleri olması için istekte veya erişim onayı verilmesi gerekir.

Onay verildikten sonra, istekte olan kullanıcı istenen görevi yürütür ve ayrıcalıklı erişim kullanıcı adına görevi yetkilendirip yürütür. Onay, istenen süre boyunca (varsayılan süre 4 saattir) geçerli kalır ve istekte bulunan kişi, istenen görevi birden çok kez yürütür. Bu tür tüm yürütmeler günlüğe kaydedilir ve güvenlik ve uyumluluk denetimi için kullanılabilir durumda olur.

> [!NOTE]
> Exchange Management PowerShell kullanarak ayrıcalıklı erişimi etkinleştirmek ve yapılandırmak için, [Bağlan'ta multi-Factor authentication kullanarak Exchange Online PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) kullanarak Exchange Online PowerShell'i Office 365 izleyin. Exchange Online PowerShell'e bağlanırken ayrıcalıklı erişimi etkinleştirmek üzere bu adımları kullanmak için, çok faktörlü kimlik doğrulamasını etkinleştirmeniz Exchange Online. Çok faktörlü kimlik doğrulamasıyla bağlantı, isteklerinizi imzalamak için ayrıcalıklı erişim tarafından kullanılan bir Kimlik Doğrulama Belirteci oluşturur.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>1. Adım: Onaylayan grubu oluşturma

1. [E-posta Microsoft 365 yönetim merkezi](https://admin.microsoft.com) yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim merkezinde **GroupsA groupadresi'ne**<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> >  gidin.

3. Posta **etkin güvenlik grubunu seçin ve** ardından yeni grubun **Ad**, Grup **e-posta** adresi **ve Açıklama** alanlarını doldurun.

4. Grubu kaydedin. Grubun tam olarak yapılandırılması ve grup içinde görünmesi birkaç dakika Microsoft 365 yönetim merkezi.

5. Yeni onaylayanin grubunu seçin ve gruba **kullanıcı** eklemek için düzenle'yi seçin.

6. Grubu kaydedin.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>2. Adım: Ayrıcalıklı erişimi etkinleştirme

### <a name="in-the-microsoft-365-admin-center"></a>Alan Microsoft 365 Yönetici'nde

1. Microsoft 365 Yönetici [Center'da,](https://admin.microsoft.com) bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim merkezinde **privacyPrivileged access** **Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & gidin**</a> > .

3. Ayrıcalıklı görevler **için onay gerektir denetimlerini** etkinleştirin.

4. 1. Adımda oluşturduğunuz onaylayan grubunu Varsayılan **onaylayanlar grubu olarak attay ın**.

5. **Kaydet ve** **Kapat'ı tıklatın**.

### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Ayrıcalıklı erişimi etkinleştirmek ve onaylayanın grubunu atamak için, Exchange Online PowerShell'de şu komutu çalıştırın:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Örneğin:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Sistem hesapları özelliği, kuruluşlarınız içindeki belirli otomasyonların ayrıcalıklı erişime bağımlı olmadan çalışamadan çalışamalarını sağlamak için kullanılabilir durumdadır; bununla birlikte, bu tür dışlamaların olağanüstü olması ve izin verilenlerin düzenli olarak onaylanması ve denetlenması önerilir.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>3. Adım: Erişim ilkesi oluşturma

Organizasyonunız için en fazla 30 ayrıcalıklı erişim ilkeleri oluşturabilir ve yapılandırarak.

### <a name="in-the-microsoft-365-admin-center"></a>Alan Microsoft 365 Yönetici'nde

1. Microsoft 365 Yönetici [Center'da,](https://admin.microsoft.com) bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim Merkezi'nde **gizlilik Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access'e gidin.

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. **İlkeleri yapılandır'ı** ve ardından **İlke ekle'yi seçin**.

5. Açılan alanlardan, organizasyonunız için uygun değerleri seçin:

    **İlke türü**: Görev, Rol veya Rol Grubu

    **İlke kapsamı**: Exchange

    **İlke** adı: Kullanılabilir ilkelerden seçim

    **Onay türü**: El ile veya Otomatik

    **Onay grubu**: 1. Adımda oluşturulan onaylayanlar grubunu seçin

6. **Oluştur'a ve** sonra **Kapat'a seçin**. İlkenin tam olarak yapılandırılması ve etkinleştirilmesi birkaç dakika sürebilir.

### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Onay ilkesi oluşturmak ve tanımlamak için, PowerShell'de Exchange Online çalıştırın:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Örneğin:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>4. Adım: Ayrıcalıklı erişim isteklerini gönderme/onaylama

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Ayrıcalıklı görevleri yürütmek için yükseltme yetkilendirmesi talep

Ayrıcalıklı erişim istekleri, istek gönderildikten sonra 24 saat boyunca geçerlidir. Onaylanmadı veya reddedilirse, isteklerin süresi dolar ve erişim onaylanmaz.

#### <a name="in-the-microsoft-365-admin-center"></a>Alan Microsoft 365 Yönetici'nde

1. Kimlik bilgilerinizi [kullanarak Microsoft 365 Yönetici Merkezi'nde](https://admin.microsoft.com) oturum açma.

2. Yönetim Merkezi'nde **gizlilik Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access'e gidin.

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. Yeni **istek'i seçin**. Açılan alanlardan, organizasyonunız için uygun değerleri seçin:

    **İstek türü**: Görev, Rol veya Rol Grubu

    **İstek kapsamı**: Exchange

    **İstek:** Kullanılabilir ilkelerden seçim

    **Süre (saat)**: Erişim için istenen saat sayısı. İsteğin gerçek saat sayısı üzerinde bir sınır yoktur.

    **Açıklamalar**: Erişim isteğinize ilişkin açıklamalar için metin alanı

5. **Kaydet'i ve** sonra **Kapat'ı seçin**. İsteğiniz, e-posta yoluyla onaylayan grubuna gönderilir.

#### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Exchange Online PowerShell'de onay isteği oluşturmak ve onaylayanın grubuna göndermek için aşağıdaki komutu çalıştırın:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Örneğin:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Yükseltme isteklerinin durumunu görüntüleme

Onay isteği oluşturulduktan sonra, yönetim merkezinde veya ilişkili istek kimliği kullanılarak Exchange PowerShell Yönetimi'nde yükseltme isteği durumu gözden geçir edilebilir.

#### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. E-posta [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) kimlik bilgilerinizle oturum açma.

2. Yönetim merkezinde **privacyPrivileged access** **Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & gidin**</a> > .

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. Gönderilen **istekleri** Beklemede, Onaylandı **, Reddedildi** veya Müşteri Kasa **durumuna** göre filtrelemek **için Görüntüle'yi** seçin.

#### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Belirli bir istek kimliğine Exchange Online için PowerShell'de aşağıdaki komutu çalıştırın:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Örneğin:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Yükseltme yetkilendirme isteğini onaylama

Bir onay isteği oluşturulduğunda, ilgili onaylayan grubunun üyeleri bir e-posta bildirimi alır ve istek kimliğiyle ilişkilendirilmiş isteği onaylar. İstekten sonra, istek onayı veya engellemesi e-posta iletisi aracılığıyla size bildirilecek.

#### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. E-posta [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) kimlik bilgilerinizle oturum açma.

2. Yönetim merkezinde **privacyPrivileged access** **Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & gidin**</a> > .

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. Ayrıntıları görüntülemek ve istek üzerinde işlem yapmak için listelenen istekten bir istek seçin.

5. İsteği **onaylamak için** Onayla'ya veya isteği **reddetmek için** Reddet'e seçin. Önceden onaylanmış istekler İptal'i seçerek erişim iptal **edilebilir**.

#### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Bir yükseltme yetkilendirme isteğini onaylamak için, Exchange Online PowerShell'de şu komutu çalıştırın:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Örneğin:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Yükseltme yetkilendirme isteğini reddetmek için, PowerShell'de Exchange Online çalıştırın:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Örneğin:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Office 365'de ayrıcalıklı erişim Office 365

Artık kuruluşta gerekli yoksa, ayrıcalıklı erişim ilkelerini silebilirsiniz.

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. [E-posta Microsoft 365 yönetim merkezi](https://admin.microsoft.com) yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim merkezinde **privacyPrivileged access** **Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & gidin**</a> > .

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. **İlkeleri yapılandır'ı seçin**.

5. Silmek istediğiniz ilkeyi seçin ve sonra da İlkeyi **Kaldır'ı seçin**.

6. **Kapat**'ı seçin.

### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Ayrıcalıklı erişim ilkesi silmek için, Exchange Online Powershell'de şu komutu çalıştırın:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>E-postada ayrıcalıklı erişimi Office 365

Gerekirse, kurum için ayrıcalıklı erişim yönetimini devre dışı  örneğin. Ayrıcalıklı erişimi devre dışı bırakmak, ilişkili onay ilkelerini veya onaylayan grupları silemez.

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. [E-Microsoft 365 yönetim merkezi](https://admin.microsoft.com) yönetici hesabının kimlik bilgileriyle oturum açın.

2. Yönetim Merkezi'nde **gizlilik Ayarlar** >  **Org Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged** >  access'e gidin.

3. Ayrıcalıklı erişim **denetimi için onay gerektir'i** etkinleştirin.

### <a name="in-exchange-management-powershell"></a>PowerShell Exchange Yönetimi'ne

Ayrıcalıklı erişimi devre dışı bırakmak için, Exchange Online Powershell'de şu komutu çalıştırın:

```PowerShell
Disable-ElevatedAccessControl
```
