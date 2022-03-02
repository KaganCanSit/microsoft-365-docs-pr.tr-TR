---
title: İş için Microsoft Defender'da (önizleme) roller ve izinler atama
description: İş için Microsoft Defender'da (önizleme) roller ve izinler atamayı öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 134b5ec8bcd390cc7f7908a09be5c2d1bd85169c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027484"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da (önizleme) roller ve izinler atama

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Microsoft 365 Defender portalında İş için Microsoft Defender'ı yapılandırma, raporları görüntüleme veya algılanan tehditlere karşı yanıt eylemleri gerçekleştirme gibi görevleri gerçekleştirmek için, güvenlik ekibinize uygun izinlerin atanmamış olması gerekir. İzinler, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) veya [Azure Active Directory.](/azure/active-directory/roles/manage-roles-portal) 

## <a name="what-to-do"></a>Ne yapmalı?

1. [İş için Defender(önizleme) özelliğinde roller hakkında bilgi sahibi olur.](#roles-in-defender-for-business)

2. [Güvenlik ekibinin rol atamalarını görüntüleme veya düzenleme](#view-or-edit-role-assignments).

3. [Sonraki adımlarınıza devam edin](#next-steps).

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>


## <a name="roles-in-defender-for-business"></a>İş için Defender'daki Roller

Aşağıdaki tabloda, İş için Defender'da (önizleme) atanabilir üç rol açık almaktadır. [Yönetici rolleri hakkında daha fazla bilgi edinin](../../admin/add-users/about-admin-roles.md). <br/><br/>

| İzin düzeyi | Açıklama |
|:---|:---|
| **Genel yöneticiler** (genel yöneticiler olarak da adlandırılır) <br/><br/> *En iyi uygulama olarak, genel yöneticilerin sayısını sınırlayın.* | Genel yöneticiler her türlü görevi gerçekleştirebilir. İş için Microsoft Defender (önizleme) Microsoft 365 için organizasyona oturum veren kişi, varsayılan olarak genel yöneticidir. <br/><br/> Genel yöneticiler tüm kullanıcı portalları genelinde ayarlara erişim Microsoft 365 değiştirebilir. Örneğin: <br/>- Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Güvenlik yöneticileri** (güvenlik yöneticileri olarak da adlandırılır) | Güvenlik yöneticileri aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlik ilkelerini görüntüleme ve yönetme <br/>- Güvenlik tehditlerini ve uyarılarını görüntüleme ve yönetme (bu etkinlikler, uç noktalarda yanıt eylemlerinin yer almalarını içerir) <br/>- Güvenlik bilgilerini ve raporlarını görüntüleme |
| **Güvenlik gözetmeni** | Güvenlik okuyucuları aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlik ilkelerini görüntüleme <br/>- Güvenlik tehditlerini ve uyarıları görüntüleme <br/>- Güvenlik bilgilerini ve raporlarını görüntüleme  |


## <a name="view-or-edit-role-assignments"></a>Rol atamalarını görüntüleme veya düzenleme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde, İzinler ve **& seçin** ve **ardından Azure AD'nin altında** Roller'i **seçin**.

3. Yan bölmesini açmak için aşağıdaki rollerden birini seçin:

   - Genel yönetici
   - Güvenlik yöneticisi
   - Güvenlik gözetmeni

   > [!IMPORTANT]
   > Microsoft, kişilerin yalnızca görevlerini yerine bunlar için ihtiyaçları olan görevlere erişmeleri için onlara erişim verilmesini önerebilir. Bu kavramı, izinler *için en az ayrıcalık* olarak çağırmayılarız. Daha fazla bilgi edinmek için bkz [. Uygulamalara en az ayrıcalıklı erişim için en iyi yöntemler](/azure/active-directory/develop/secure-least-privileged-access). 

4. Yan bölmede, **Azure AD'de üyeleri yönet bağlantısını** seçin. Bu eylem, rol atamalarınızı Azure Active Directory yönetlerinizi görüntüley oyunu (Azure AD) görüntülemenize ve yönetmenize yardımcı olur.

5. Bir kullanıcı seçerek profilini açın ve ardından Atanan **roller'i seçin**.

   - Rol eklemek için + Ödev **ekle'yi seçin**.
   - Rolü kaldırmak için, **X Atamaları kaldır'ı seçin**. 

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [3. Adım: E-posta bildirimlerini ayarlama](mdb-email-notifications.md)

- [4. Adım: Cihazları İş için Microsoft Defender'a ekleme (önizleme)](mdb-onboard-devices.md)