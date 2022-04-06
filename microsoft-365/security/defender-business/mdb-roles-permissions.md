---
title: Web'de roller ve izinler İş için Microsoft Defender
description: Aynı dosyada roller ve izinler atamayı İş için Microsoft Defender
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 33fb7548d2dbd231368a459cd58b9d50e7c4673e
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638256"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Web'de roller ve izinler İş için Microsoft Defender

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Güvenlik portalında Microsoft 365 Defender yapılandırma, İş için Microsoft Defender görüntüleme veya algılanan tehditlere karşı yanıt eylemleri gerçekleştirme gibi görevleri gerçekleştirmek için, güvenlik ekibinize uygun izinlerin atanmamış olması gerekir. İzinler, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) veya [Azure Active Directory.](/azure/active-directory/roles/manage-roles-portal) 

## <a name="what-to-do"></a>Ne yapmalı?

1. [İş için Defender'daki roller hakkında bilgi edinmek için:](#roles-in-defender-for-business)

2. [Güvenlik ekibinin rol atamalarını görüntüleme veya düzenleme](#view-or-edit-role-assignments).

3. [Sonraki adımlarınıza devam edin](#next-steps).

>
> **Bir dakika mı kaldı?**
> Lütfen bu konuda <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">kısa anket İş için Microsoft Defender</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="roles-in-defender-for-business"></a>İş için Defender'daki Roller

Aşağıdaki tabloda, İş için Defender'da atanabilir üç rol açık almaktadır. [Yönetici rolleri hakkında daha fazla bilgi edinin](../../admin/add-users/about-admin-roles.md). <br/><br/>

| İzin düzeyi | Açıklama |
|:---|:---|
| **Genel yöneticiler** (genel yöneticiler olarak da adlandırılır) <br/><br/> *En iyi uygulama olarak, genel yöneticilerin sayısını sınırlayın.* | Genel yöneticiler her türlü görevi gerçekleştirebilir. Şirketinizi sizin için veya Microsoft 365 için İş için Microsoft Defender varsayılan olarak genel yöneticidir. <br/><br/> Genel yöneticiler tüm kullanıcı portalları genelinde ayarlara erişim Microsoft 365 değiştirebilir. Örneğin: <br/>- Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) |
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

## <a name="need-to-add-users"></a>Kullanıcı eklemeniz mi gerekiyor?

Aboneliğinize henüz kullanıcı eklemedıysanız, bkz. [Kullanıcı ekleme ve lisansları aynı anda atama](../../admin/add-users/add-users.md).

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [3. Adım: E-posta bildirimlerini ayarlama](mdb-email-notifications.md)

- [4. Adım: Cihazları başka cihazlara İş için Microsoft Defender](mdb-onboard-devices.md)