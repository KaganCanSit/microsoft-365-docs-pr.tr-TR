---
title: Ayrıcalıklı erişim yönetimini kullanmaya başlama
description: Microsoft Purview'da ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırma hakkında daha fazla bilgi edinmek için bu makaleyi kullanın.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, ayrıcalıklı erişim yönetimi
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
ms.openlocfilehash: d53058e89fc1830b6f35eef270d84b99f2cc9f74
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626347"
---
# <a name="get-started-with-privileged-access-management"></a>Ayrıcalıklı erişim yönetimini kullanmaya başlama

Bu makale, kuruluşunuzda ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırma konusunda size yol gösterir. Ayrıcalıklı erişimi yönetmek ve kullanmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> veya Exchange Management PowerShell'i kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Ayrıcalıklı erişim yönetimine başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ve tüm eklentileri onaylamanız gerekir. Ayrıcalıklı erişim yönetimine erişmek ve bunları kullanmak için kuruluşunuzun aşağıdaki aboneliklerden veya eklentilerden birine sahip olması gerekir:

- Microsoft 365 E5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3 aboneliği (veya Office 365 E3 aboneliği + Enterprise Mobility ve Security E3 aboneliği) + Microsoft 365 E5 Uyumluluk eklentisi
- Herhangi bir Microsoft 365, Office 365, Exchange, SharePoint veya OneDrive İş aboneliği + Microsoft 365 E5 Insider Risk Management eklentisi
- Microsoft 365 A5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 A3 aboneliği (veya Office 365 A3 aboneliği + Enterprise Mobility and Security A3 aboneliği) + Microsoft A5 Uyumluluk eklentisi
- Herhangi bir Microsoft 365, Office 365, Exchange, SharePoint veya OneDrive Eğitim aboneliği + Microsoft 365 A5 Insider Risk Management eklentisi
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 Kurumsal E3 aboneliği + Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz, nota bakın)

Ayrıcalıklı erişim yönetimi isteklerini gönderen ve yanıtlayan kullanıcılara yukarıdaki lisanslardan biri atanmalıdır.

> [!IMPORTANT]
> Office 365 Gelişmiş Uyumluluk artık tek başına abonelik olarak satılmaz. Geçerli aboneliklerin süresi dolduğunda, müşterilerin aynı veya ek uyumluluk özelliklerini içeren yukarıdaki aboneliklerden birine geçiş yapması gerekir.

Mevcut bir Office 365 Kurumsal E5 planınız yoksa ve ayrıcalıklı erişim yönetimini denemek istiyorsanız, [microsoft 365'i](/office365/admin/try-or-buy-microsoft-365) mevcut Office 365 aboneliğinize ekleyebilir veya Microsoft 365 Kurumsal E5 [deneme sürümüne kaydolabilirsiniz](https://www.microsoft.com/microsoft-365/enterprise).

## <a name="enable-and-configure-privileged-access-management"></a>Ayrıcalıklı erişim yönetimini etkinleştirme ve yapılandırma

Kuruluşunuzda ayrıcalıklı erişimi ayarlamak ve kullanmak için şu adımları izleyin:

- [1. Adım: Onaylayan grubu oluşturma](privileged-access-management-configuration.md#step1)

    Ayrıcalık erişimini kullanmaya başlamadan önce, yükseltilmiş ve ayrıcalıklı görevlere erişim için gelen istekler için kimlerin onay yetkilisine ihtiyacı olduğunu belirleyin. Onaylayanlar grubunun parçası olan tüm kullanıcılar erişim isteklerini onaylayabilir. Bu grup, Office 365 posta özellikli bir güvenlik grubu oluşturularak etkinleştirilir.

- [2. Adım: Ayrıcalıklı erişimi etkinleştirme](privileged-access-management-configuration.md#step2)

    Ayrıcalıklı erişim, ayrıcalıklı erişim yönetimi erişim denetiminden dışlanmasını istediğiniz bir dizi sistem hesabı dahil olmak üzere varsayılan onaylayan grubuyla Office 365 açıkça etkinleştirilmelidir.

- [3. Adım: Erişim ilkesi oluşturma](privileged-access-management-configuration.md#step3)

    Onay ilkesi oluşturmak, tek tek görevlerde kapsamı belirlenmiş belirli onay gereksinimlerini tanımlamanızı sağlar. Onay türü seçenekleri **Otomatik** veya **El ile'dir**.

- [4. Adım: Ayrıcalıklı erişim isteklerini gönderme/onaylama](privileged-access-management-configuration.md#step4)

    Etkinleştirildikten sonra ayrıcalıklı erişim, ilişkili onay ilkesi tanımlanmış olan tüm görevler için onay gerektirir. Onay ilkesine dahil edilen görevler için, kullanıcılar görevi yürütmek için gerekli izinlere sahip olmak için erişim onayı istemeli ve erişim onayı vermelidir.

Onay verildikten sonra, istekte bulunan kullanıcı istenen görevi yürütebilir ve ayrıcalıklı erişim görevi kullanıcı adına yetkilendirilir ve yürütür. Onay istenen süre (varsayılan süre 4 saattir) için geçerli kalır ve istekte bulunan, istenen görevi birden çok kez yürütebilir. Bu tür tüm yürütmeler günlüğe kaydedilir ve güvenlik ve uyumluluk denetimi için kullanılabilir hale getirilir.

> [!NOTE]
> Ayrıcalıklı erişimi etkinleştirmek ve yapılandırmak için Exchange Yönetimi PowerShell'i kullanmak istiyorsanız, Office 365 kimlik bilgilerinizle [Exchange Online PowerShell'e bağlanmak için Multi-Factor authentication kullanarak](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) PowerShell'e Exchange Online Bağlanma'daki adımları izleyin. Exchange Online PowerShell'e bağlanırken ayrıcalıklı erişimi etkinleştirme adımlarını kullanmak için kuruluşunuz için çok faktörlü kimlik doğrulamasını etkinleştirmeniz gerekmez. Çok faktörlü kimlik doğrulamasıyla bağlantı kurmak, isteklerinizi imzalamak için ayrıcalıklı erişim tarafından kullanılan bir Kimlik Doğrulama Belirteci oluşturur.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>1. Adım: Onaylayan grubu oluşturma

1. Kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Gruplar Grup**</a> > **ekle'ye** gidin.

3. **Posta etkin güvenlik grubunu** seçin ve ardından yeni grubun **Ad**, **Grup e-posta adresi** ve **Açıklama** alanlarını tamamlayın.

4. Grubu kaydedin. Grubun tam olarak yapılandırılması ve Microsoft 365 yönetim merkezi görünmesi birkaç dakika sürebilir.

5. Yeni onaylayanın grubunu seçin ve **düzenle'yi** seçerek gruba kullanıcı ekleyin.

6. Grubu kaydedin.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>2. Adım: Ayrıcalıklı erişimi etkinleştirme

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nde

1. Kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft 365 Yönetici Merkezi'nde](https://admin.microsoft.com) oturum açın.

2. Yönetim merkezinde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Ayrıcalıklı görevler için onay iste** denetimini etkinleştirin.

4. 1. Adımda oluşturduğunuz onaylayan grubunu **Varsayılan onaylayanlar grubu** olarak atayın.

5. **Kaydet** ve **Kapat'ı seçin**.

### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Ayrıcalıklı erişimi etkinleştirmek ve onaylayanın grubunu atamak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Örneğin:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Sistem hesapları özelliği, kuruluşunuzdaki belirli otomasyonların ayrıcalıklı erişime bağımlı olmadan çalışabilmesini sağlamak için kullanıma sunulmuştur, ancak bu tür dışlamaların istisnai olması ve izin verilenlerin düzenli olarak onaylanması ve denetlenmesi önerilir.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>3. Adım: Erişim ilkesi oluşturma

Kuruluşunuz için en fazla 30 ayrıcalıklı erişim ilkesi oluşturabilir ve yapılandırabilirsiniz.

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nde

1. Kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft 365 Yönetici Merkezi'nde](https://admin.microsoft.com) oturum açın.

2. Yönetici Merkezi'nde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Erişim ilkelerini ve isteklerini yönet'i** seçin.

4. **İlkeleri yapılandır'ı** ve **İlke ekle'yi** seçin.

5. Açılan alanlardan kuruluşunuz için uygun değerleri seçin:

    **İlke türü**: Görev, Rol veya Rol Grubu

    **İlke kapsamı**: Exchange

    **İlke adı**: Kullanılabilir ilkeler arasından seçim yapın

    **Onay türü**: El ile veya Otomatik

    **Onay grubu**: 1. Adımda oluşturulan onaylayan grubunu seçin

6. **Oluştur'u** ve ardından **Kapat'ı** seçin. İlkenin tam olarak yapılandırılması ve etkinleştirilmesi birkaç dakika sürebilir.

### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Onay ilkesi oluşturmak ve tanımlamak için PowerShell Exchange Online de aşağıdaki komutu çalıştırın:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Örneğin:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>4. Adım: Ayrıcalıklı erişim isteklerini gönderme/onaylama

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Ayrıcalıklı görevleri yürütmek için yükseltme yetkilendirmesi isteme

Ayrıcalıklı erişim istekleri, istek gönderildikten sonra 24 saate kadar geçerlidir. Onaylanmaz veya reddedilirse isteklerin süresi dolar ve erişim onaylanmaz.

#### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nde

1. Kimlik bilgilerinizi kullanarak [Microsoft 365 Yönetici Merkezi'ne](https://admin.microsoft.com) oturum açın.

2. Yönetici Merkezi'nde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Erişim ilkelerini ve isteklerini yönet'i** seçin.

4. **Yeni istek'i** seçin. Açılan alanlardan kuruluşunuz için uygun değerleri seçin:

    **İstek türü**: Görev, Rol veya Rol Grubu

    **İstek kapsamı**: Exchange

    **İstek:** Kullanılabilir ilkelerden seçim yapın

    **Süre (saat)**: İstenen erişimin saat sayısı. İstenebilecek saat sayısı için bir sınır yoktur.

    **Açıklamalar**: Erişim isteğinizle ilgili açıklamalar için metin alanı

5. **Kaydet'i** ve ardından **Kapat'ı** seçin. İsteğiniz onaylayanın grubuna e-postayla gönderilir.

#### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Onaylayanın grubuna onay isteği oluşturmak ve göndermek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Örneğin:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Yükseltme isteklerinin durumunu görüntüleme

Bir onay isteği oluşturulduktan sonra, yükseltme isteği durumu istek kimliğiyle ilişkili kullanılarak yönetim merkezinde veya Exchange Yönetimi PowerShell'de gözden geçirilebilir.

#### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. Kimlik bilgilerinizle [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Yönetim merkezinde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Erişim ilkelerini ve isteklerini yönet'i** seçin.

4. Gönderilen istekleri **Beklemede**, **Onaylandı**, **Reddedildi** veya **Müşteri Kasası** durumuna göre filtrelemek için **Görünüm'ü** seçin.

#### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Belirli bir istek kimliğinin onay isteği durumunu görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Örneğin:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Yükseltme yetkilendirme isteğini onaylama

Bir onay isteği oluşturulduğunda, ilgili onaylayan grubunun üyeleri bir e-posta bildirimi alır ve istek kimliğiyle ilişkili isteği onaylayabilir. İstek sahibine e-posta iletisi aracılığıyla istek onayı veya reddi bildirilir.

#### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. Kimlik bilgilerinizle [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Yönetim merkezinde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Erişim ilkelerini ve isteklerini yönet'i** seçin.

4. Ayrıntıları görüntülemek ve istek üzerinde işlem yapmak için listelenen bir isteği seçin.

5. İsteği onaylamak için **Onayla'yı** veya isteği reddetmek için **Reddet'i** seçin. Daha önce onaylanan istekler **İptal Et'i** seçerek erişimi iptal edebilir.

#### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Yükseltme yetkilendirme isteğini onaylamak için PowerShell'Exchange Online aşağıdaki komutu çalıştırın:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Örneğin:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Yükseltme yetkilendirme isteğini reddetmek için PowerShell'Exchange Online aşağıdaki komutu çalıştırın:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Örneğin:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Office 365'da ayrıcalıklı erişim ilkesini silme

Kuruluşunuzda artık gerekli değilse, ayrıcalıklı erişim ilkesini silebilirsiniz.

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. Kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Yönetim merkezinde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Erişim ilkelerini ve isteklerini yönet'i** seçin.

4. **İlkeleri yapılandır'ı** seçin.

5. Silmek istediğiniz ilkeyi seçin ve ardından **İlkeyi Kaldır'ı** seçin.

6. **Kapat**'ı seçin.

### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Ayrıcalıklı erişim ilkesini silmek için powershell Exchange Online de aşağıdaki komutu çalıştırın:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Office 365'de ayrıcalıklı erişimi devre dışı bırakma

Gerekirse, kuruluşunuz için ayrıcalıklı erişim yönetimini devre dışı bırakabilirsiniz. Ayrıcalıklı erişimi devre dışı bırakmak ilişkili onay ilkelerini veya onaylayan gruplarını silmez.

### <a name="in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi

1. Kuruluşunuzdaki bir yönetici hesabının kimlik bilgileriyle [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.

2. Yönetici Merkezi'nde **Ayarlar** > **Kuruluş Ayarları** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Güvenlik & Gizlilik**</a> > **Ayrıcalıklı erişimi'ne** gidin.

3. **Ayrıcalıklı erişim denetimi için onay gerektir'i** etkinleştirin.

### <a name="in-exchange-management-powershell"></a>Exchange Yönetimi PowerShell'de

Ayrıcalıklı erişimi devre dışı bırakmak için powershell Exchange Online de aşağıdaki komutu çalıştırın:

```PowerShell
Disable-ElevatedAccessControl
```
