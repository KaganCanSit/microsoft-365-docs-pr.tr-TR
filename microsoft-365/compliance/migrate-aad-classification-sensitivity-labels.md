---
title: Azure Active Directory grupları için sınıflandırma ve duyarlılık Microsoft 365 oluşturma
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: Bu makalede, klasik Azure Active Directory sınıflandırma ve duyarlılık etiketleri elelanmıştır.
ms.openlocfilehash: 0a8c12d3d133000a880c58366a9f2b13ed8cbf49
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988160"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Azure Active Directory grupları için sınıflandırma ve duyarlılık Microsoft 365 oluşturma

Bu makalede, klasik Azure Active Directory sınıflandırma ve duyarlılık etiketleri elelanmıştır.

Duyarlılık etiketleri bu hizmetler tarafından [desteklemektedir](./sensitivity-labels-teams-groups-sites.md).

Duyarlılık etiketleri hakkında tam bilgi için bkz[. Duyarlılık etiketleri hakkında bilgi.](sensitivity-labels.md)

Duyarlılık etiketleri ve siteler ve Microsoft 365 gruplarına davranışı hakkında daha fazla bilgi edinmek için Microsoft Teams[' da, Microsoft 365](sensitivity-labels-teams-groups-sites.md) gruplarında ve sitelerde içeriği korumak için SharePoint kullanma.

Klasik sınıflandırmadan duyarlılık etiketlerine ve klasik sınıflandırmadan AAD en iyi yöntemler için aşağıdaki senaryolara bakın.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Senaryo 1: Kiracı hiçbir zaman klasik AAD sınıflandırmaları veya duyarlılık etiketlerini belgeler ve e-postalar için kullanmdı

- Kiracı Yöneticisi, AAD powershell cmdlet'i aracılığıyla "EnableMIPLabels" kiracı bayrağını true olarak ayar AAD grupların duyarlılık etiketlerini etkinleştirir.
- Kiracı Yöneticisi, dosyanın içinde duyarlılık [etiketlerini Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com).
    - Kiracı yöneticisi dosya ve şifreleme ve filigranlama gibi e-postayla ilgili eylemleri seçebilir.
    - Kiracı yöneticisi, Microsoft 365 Gruplar'ı SharePoint Online siteyle ilgili eylemleri duyarlılık etiketlerine eklemeyi seçebilir.
- Kiracı Yöneticisi ilkeyi yayımlar.
- **Uyumlu iş yükleri** duyarlılık etiketlerini gösterir. Grup oluşturmak için duyarlılık etiketlerini kullanın. Uyumlu iş yükleri, duyarlılık etiketlerini destekleyen hizmetlerdir.
- **Uyumlu olmayan iş yükleri** , henüz duyarlılık etiketlerini desteklemeyen hizmetlerdir. Ancak gruplar oluşturulsa da, uyumlu olmayan iş yükleri üzerinden duyarlılık etiketiyle ilişkilendirilebilirler. Bu tür grupları duyarlılık etiketleriyle ilişkilendirmek için kiracı yöneticileri PowerShell cmdlet'lerini çalıştırabilirsiniz.

Tablo 1. Uyumlu ve uyumlu olmayan iş yüklerinin davranışı – grupları oluşturma, düzenleme veya silme

|workload|Kullanıcı grup penceresinde hangi etiket listesini görüyor?|Yeni grup oluşturma |Grubu düzenle |Grubu sil |
|:-------|:-------|:--------|:--------|:--------|   
|Uyumlu   |duyarlılık etiketleri. |Herhangi bir davranış değişikliği yoktur. |Herhangi bir davranış değişikliği yoktur. |Herhangi bir davranış değişikliği yoktur. |
|Uyumlu değil |Duyarlılık etiketi görünmüyor. |Kullanıcı duyarlılık etiketini seçmeden bir grup oluşturabilir. <br><br> Yöneticinin, arka planda duyarlılık etiketleri uygulamak için cmdlet'leri çalıştırabileceklerini unutmayın. |**1. Örnek**: Daha önce hiçbir duyarlılık etiketi seçilmemiş. Kullanıcı grubu düzenleyebilir.<br><br> **2. Örnek**: Daha önce cmdlet kullanılarak arka planda uygulanmış duyarlılık etiketi. Kullanıcı, etikete göre geçersiz gizlilik ayarı seçimi olduğu durum dışında grubu başarılı bir şekilde düzenleyebilir. |Herhangi bir davranış değişikliği yoktur.|

> [!NOTE]
> Outlook masaüstü istemcisi (Win 32) durumunda, yönetici kiracılarında duyarlılık etiketlerine izin verdikten ve kullanıcı Outlook masaüstü istemcisinde (Win 32) daha eski bir sürümde:
>
> - Kullanıcı duyarlılık etiketlerini Outlook masaüstü istemcisinin eski sürümünde görür.
> - Bununla birlikte, kullanıcı grubu düzenler ve grubu bir duyarlılık etiketiyle kaydederse, seçilen gizlilik ayarı uygulanan duyarlılık etiketinin gizlilik ayarı tarafından geçersiz kılınır.
>
> Kullanıcılarınızı, eski bir Outlook istemci sürümüne yükseltmelerini öneririz.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Senaryo 2: Kiracı zaten klasik sınıflandırmaları AAD [kullanıyor](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Durum A: Kiracı, belgeler ve e-postalar için hiçbir zaman duyarlılık etiketleri kullanmdı

1. Uygulama [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) mevcut Azure AD etiketleriyle aynı adla duyarlılık etiketleri oluşturmalarını öneririz.
2. Bu duyarlılık etiketlerini, ad eşlemesi kullanarak var olan grup ve sitelere Microsoft 365 için PowerShell SharePoint kullanın.
3. Yönetici, klasik Azure AD etiketlerini silmeyi seçebilir:
    - Uyumlu iş yükleri bu duyarlılık etiketlerini ve grupların kendileriyle oluşturulacaklarını gösterir.
    - Uyumlu olmayan iş yükleri grup oluştururken çalışır ancak onlara duyarlılık etiketi ekli değildir.
4. Yöneticiler, etiket eklemeden bu gruplara duyarlılık etiketleri uygulamak için PowerShell cmdlet'lerini çalıştırabilirsiniz.
    - Alternatif olarak, bir yönetici klasik Azure AD etiketlerini tutmayı seçebilir:
        - Uyumlu iş yükleri bu duyarlılık etiketlerini gösterir ve gruplarla oluşturulur. Uyumlu iş yükleri, duyarlılık etiketlerini destekleyen hizmetlerdir.
        - Uyumlu olmayan iş yükleri grup oluştururken ve klasik Azure AD etiketlerini gösterirken çalışır. Bu klasik Azure AD etiketleri, uyumlu olmayan iş yükleriyle oluşturulan bu gruplara eklidir.
5. Yöneticilerin, klasik Azure AD etiketleriyle bu gruplara duyarlılık etiketleri uygulamak için PowerShell cmdlet'lerini çalıştırmalarını kesinlikle öneririz.

Tablo 2. Uyumlu ve uyumlu olmayan iş yüklerinin davranışı – grupları oluşturma, düzenleme veya silme

|workload|Kullanıcı grup penceresinde hangi etiket listesini görüyor?|Yeni grup oluşturma |Grubu düzenle |Grubu sil |
|:-------|:-------|:--------|:--------|:--------|   
|Uyumlu   |duyarlılık etiketleri. |Herhangi bir davranış değişikliği yoktur. |Herhangi bir davranış değişikliği yoktur. |Herhangi bir davranış değişikliği yoktur. |
|Uyumlu değil |Eski klasik AAD etiketleri. |Kullanıcı, klasik Azure AD etiketinin seçili olduğu bir grup oluşturabilir. <br><br>Yöneticinin, arka planda duyarlılık etiketleri uygulamak için cmdlet'leri çalıştırabileceklerini unutmayın. |**1. Örnek**: Daha önce hiçbir duyarlılık etiketi seçilmemiş. Kullanıcı grubu düzenleyebilir.<br><br> **2. Durum**: Daha AAD klasik metin etiketleri. Kullanıcı grubu düzenleyebilir.<br><br> **3. Örnek**: Daha önce cmdlet kullanılarak arka planda uygulanmış duyarlılık etiketi. Kullanıcı, etikete göre geçersiz gizlilik ayarı seçiminde bulunduğu tek bir durum hariç olmak üzere grubu düzenleyebilir. |Kullanıcı grubu silebilir. |

> [!NOTE]
> Outlook masaüstü istemcisi (Win 32) durumunda, yönetici kiracılarında duyarlılık etiketlerine izin verdikten ve kullanıcı Outlook masaüstü istemcisinde (Win 32) daha eski bir sürümde:
>
> - Kullanıcı duyarlılık etiketlerini Outlook masaüstü istemcisinin eski sürümünde görür.
> - Bununla birlikte, kullanıcı grubu düzenler ve grubu bir duyarlılık etiketiyle kaydederse, seçilen gizlilik ayarı uygulanan duyarlılık etiketinin gizlilik ayarı tarafından geçersiz kılınır.
>
> Kullanıcılarınızı, eski bir Outlook istemci sürümüne yükseltmelerini öneririz.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>B Durumu: Kiracı, belgeler ve e-postalar için duyarlılık etiketleri kullandı

1. Yönetici, 'EnableMIPLabels' kiracı bayrağını doğru olarak ayarladığı için kiracıda duyarlılık etiketi özelliğini etkinleştir olduğu anda, grup/site/ekip oluştur ve düzenle iletişim kutularına belge ve e-posta duyarlılık etiketleri görünür.
2. Yönetici, ilgili grup ayarlarını belirterek grup/site/ekip üzerinde gizlilik ve dış kullanıcı erişimini zorunlu kılınması için aynı belge ve e-posta duyarlılık etiketlerini kullanabilir:
    1. Site [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) ve **Gruplar sekmesini** seçin.
    2. Belge veya e-posta duyarlılık etiketini düzenleyin.

## <a name="sample-script"></a>Örnek betik

Klasik ad etiketleri olan grupları duyarlılık etiketlerine AAD için bkz. [Klasik Azure AD grup sınıflandırması](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).