---
title: Microsoft 365 grupları için AAD sınıflandırma ve duyarlılık etiketleri
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: Bu makalede klasik Azure Active Directory sınıflandırması ve duyarlılık etiketleri ele alınmaktadır.
ms.openlocfilehash: 260b71d703f2534e5e2ddcf4ef45fe28a914eeab
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623793"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Microsoft 365 grupları için Azure Active Directory sınıflandırma ve duyarlılık etiketleri

Bu makalede klasik Azure Active Directory sınıflandırması ve duyarlılık etiketleri ele alınmaktadır.

Duyarlılık etiketleri [bu hizmetler](./sensitivity-labels-teams-groups-sites.md) tarafından desteklenir.

Duyarlılık etiketleri hakkında tam bilgi için bkz. [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md).

Duyarlılık etiketleri ve sitelerin ve Microsoft 365 gruplarının davranışları hakkında daha fazla bilgi edinmek için bkz. [Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](sensitivity-labels-teams-groups-sites.md).

Klasik AAD sınıflandırmasından duyarlılık etiketlerine geçiş yaparken en iyi yöntemler için aşağıdaki senaryolara bakın.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Senaryo 1: Kiracı hiçbir zaman belgeler ve e-postalar için klasik AAD sınıflandırmaları veya duyarlılık etiketleri kullanmaz

- Kiracı Yönetici, AAD powershell cmdlet'i aracılığıyla "EnableMIPLabels" kiracı bayrağını true olarak ayarlayarak gruplar için duyarlılık etiketlerini etkinleştirir.
- Kiracı Yönetici[, Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) duyarlılık etiketlerini oluşturur.
    - Kiracı yöneticisi, şifreleme ve filigran gibi dosya ve e-postayla ilgili eylemleri seçebilir.
    - Kiracı yöneticisi duyarlılık etiketlerine Microsoft 365 Grupları ve SharePoint Online sitesiyle ilgili eylemleri seçebilir.
- Kiracı Yönetici ilkeyi yayımlar.
- **Uyumlu iş yükleri** duyarlılık etiketlerini gösterir. Grup oluşturmak için duyarlılık etiketlerini kullanın. Uyumlu iş yükleri, duyarlılık etiketlerini destekleyen hizmetlerdir.
- **Uyumlu olmayan iş yükleri** , duyarlılık etiketlerini henüz desteklemeyen hizmetlerdir. Ancak gruplar, uyumlu olmayan iş yükleri aracılığıyla duyarlılık etiketiyle ilişkilendirilemez. Bu tür grupları duyarlılık etiketleriyle ilişkilendirmek için kiracı yöneticileri PowerShell cmdlet'lerini çalıştırabilir.

Tablo 1. Uyumlu ve uyumlu olmayan iş yüklerinin davranışı : grup oluşturma, düzenleme veya silme

|Iş yük -ünü|Kullanıcı grup penceresinde hangi etiket listesini görür?|Yeni grup oluştur |Grubu düzenle |Grubu sil |
|:-------|:-------|:--------|:--------|:--------|   
|Uyumlu   |duyarlılık etiketleri. |Davranışta değişiklik yok. |Davranışta değişiklik yok. |Davranışta değişiklik yok. |
|Uyumlu değil |Görünür duyarlılık etiketi yok. |Kullanıcı duyarlılık etiketini seçmeden bir grup oluşturabilir. <br><br> Yöneticinin arka planda duyarlılık etiketleri uygulamak için cmdlet'leri çalıştırabileceğini unutmayın. |**Olay 1**: Daha önce hiçbir duyarlılık etiketi seçilmedi. Kullanıcı grubu düzenleyebilir.<br><br> **Olay 2**: Daha önce cmdlet kullanılarak arka planda uygulanan duyarlılık etiketi. Kullanıcı, etiketle ilgili olarak geçersiz gizlilik ayarı birleşimini seçtiği durum hariç olmak üzere bir grubu başarıyla düzenleyebilir. |Davranışta değişiklik yok.|

> [!NOTE]
> Outlook masaüstü istemcisi (Win 32) söz konusu olduğunda, yönetici kiracısında duyarlılık etiketlerini etkinleştirdikten ve kullanıcıları Outlook masaüstü istemcisinin eski bir sürümünde (Win 32) bulunuyorsa:
>
> - Kullanıcı, Outlook masaüstü istemcisinin eski sürümünde duyarlılık etiketlerinin göründüğünü görür.
> - Ancak, kullanıcı bir grubu düzenlediğinde ve grubu bir duyarlılık etiketiyle kaydettiğinde, seçilen gizlilik ayarı uygulanan duyarlılık etiketinin gizlilik ayarı tarafından geçersiz kılınabilir.
>
> Kullanıcılarınızın Outlook istemcisinin eski bir sürümünde daha yeni bir sürüme yükseltmesini öneririz.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Senaryo 2: Kiracı zaten klasik AAD [sınıflandırmalarını](../enterprise/manage-microsoft-365-groups-with-powershell.md) kullanıyor

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Olay A: Kiracı hiçbir zaman belgeler ve e-postalar için duyarlılık etiketlerini kullanmaz

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com), mevcut klasik Azure AD etiketleriyle aynı ada sahip duyarlılık etiketleri oluşturmanızı öneririz.
2. Bu duyarlılık etiketlerini mevcut Microsoft 365 gruplarına ve SharePoint sitelerine ad eşleme kullanarak uygulamak için PowerShell cmdlet'ini kullanın.
3. Yönetici klasik Azure AD etiketlerini silmeyi seçebilirsiniz:
    - Uyumlu iş yükleri, bu duyarlılık etiketlerini ve grupların bunlarla oluşturulduğunu gösterir.
    - Uyumlu olmayan iş yükleri grup oluştururken çalışır, ancak bunlara hiçbir duyarlılık etiketi eklenmez.
4. Yöneticiler, bu gruplara etiketsiz duyarlılık etiketleri uygulamak için PowerShell cmdlet'lerini çalıştırabilir.
    - Alternatif olarak, bir yönetici klasik Azure AD etiketlerini korumayı seçebilir:
        - Uyumlu iş yükleri bu duyarlılık etiketlerini gösterir ve gruplarla birlikte oluşturulur. Uyumlu iş yükleri, duyarlılık etiketlerini destekleyen hizmetlerdir.
        - Uyumlu olmayan iş yükleri grup oluştururken çalışır ve klasik Azure AD etiketlerini gösterir. Bu klasik Azure AD etiketleri, uyumlu olmayan iş yükleriyle oluşturulan bu gruplara eklenir.
5. Yöneticilerin klasik Azure AD etiketleriyle bu gruplara duyarlılık etiketleri uygulamak için PowerShell cmdlet'lerini çalıştırmalarını kesinlikle öneririz.

Tablo 2. Uyumlu ve uyumlu olmayan iş yüklerinin davranışı : grup oluşturma, düzenleme veya silme

|Iş yük -ünü|Kullanıcı grup penceresinde hangi etiket listesini görür?|Yeni grup oluştur |Grubu düzenle |Grubu sil |
|:-------|:-------|:--------|:--------|:--------|   
|Uyumlu   |duyarlılık etiketleri. |Davranışta değişiklik yok. |Davranışta değişiklik yok. |Davranışta değişiklik yok. |
|Uyumlu değil |Eski klasik AAD etiketleri. |Kullanıcı, klasik Azure AD etiketi seçili bir grup oluşturabilir. <br><br>Yöneticinin arka planda duyarlılık etiketleri uygulamak için cmdlet'leri çalıştırabileceğini unutmayın. |**Olay 1**: Daha önce hiçbir duyarlılık etiketi seçilmedi. Kullanıcı grubu düzenleyebilir.<br><br> **Olay 2**: Daha önce seçilen klasik AAD etiketleri. Kullanıcı grubu düzenleyebilir.<br><br> **Olay 3**: Daha önce cmdlet kullanılarak arka planda uygulanan duyarlılık etiketi. Kullanıcının etiketle ilgili olarak geçersiz gizlilik ayarı birleşimi seçtiği bir durum hariç olmak üzere bir grubu düzenleyebilmesi gerekir. |Kullanıcı bir grubu silebilir. |

> [!NOTE]
> Outlook masaüstü istemcisi (Win 32) söz konusu olduğunda, yönetici kiracısında duyarlılık etiketlerini etkinleştirdikten ve kullanıcıları Outlook masaüstü istemcisinin eski bir sürümünde (Win 32) bulunuyorsa:
>
> - Kullanıcı, Outlook masaüstü istemcisinin eski sürümünde duyarlılık etiketlerinin göründüğünü görür.
> - Ancak, kullanıcı bir grubu düzenlediğinde ve grubu bir duyarlılık etiketiyle kaydettiğinde, seçilen gizlilik ayarı uygulanan duyarlılık etiketinin gizlilik ayarı tarafından geçersiz kılınabilir.
>
> Kullanıcılarınızın Outlook istemcisinin eski bir sürümünde daha yeni bir sürüme yükseltmesini öneririz.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Olay B: Kiracı belgeler ve e-postalar için duyarlılık etiketlerini kullandı

1. Yönetici ,'EnableMIPLabels' kiracı bayrağını true olarak ayarlayarak kiracıda duyarlılık etiketi özelliğini etkinleştirir etkinleştirmez, grup/site/ekip oluşturma ve düzenleme iletişim kutularındaki belge ve e-posta duyarlılık etiketleri görüntülenir.
2. Yönetici, ilgili grup ayarlarını belirterek grup/site/ekipte gizlilik ve dış kullanıcı erişimini zorunlu kılmak için aynı belgeyi ve e-posta duyarlılık etiketlerini kullanabilir:
    1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Siteler ve Gruplar** sekmesini seçin.
    2. Belgeyi veya e-posta duyarlılık etiketini düzenleyin.

## <a name="sample-script"></a>Örnek betik

Klasik AAD etiketlerine sahip grupları duyarlılık etiketlerine geçirmek için örnek betik için bkz. [Klasik Azure AD grup sınıflandırması](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).
