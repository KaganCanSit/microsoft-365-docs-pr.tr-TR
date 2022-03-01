---
title: Microsoft Yönetilen Masaüstü için kullanıcı desteği al
description: Kullanıcılar hizmet ve cihazlarla ilgili nasıl yardım alır?
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48be29f8db689ddd0911d7512b267ba50c85a469
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014288"
---
# <a name="getting-help-for-users"></a>Kullanıcılar için yardım alma

İş akışında yükseltilmiş cihaz erişimi veya Microsoft'a [](../service-description/user-support.md) yükseltme isteğinde bulundurmanız gereken noktaya ulaştınızsa, şu adımları izleyin:

>[!NOTE]
>Bu destek seçenekleri Test grubunda yer alan cihazlar için kullanılamaz.

## <a name="elevation-requests"></a>Yükseltme istekleri

Bir cihaza yükseltilmiş erişim isteğide bulundurmadan önce hangi eylemlerin en uygun olduğunu gözden geçirmek en iyisidir.

| Eylemler | Örnekler |
| ------ | ------ |
| **Tipik eylemler** yükseltme isteği işlemi için tasarlanmıştır. Microsoft Yönetilen Masaüstü cihazla ilgili sorunları giderirken düzenli olarak gerçekleştirilir. | <ul><li>Yerleşik sistem sorun gidericilerini, komut istemini veya İş Windows PowerShell sorunlarını giderme adımlarını giderme.</li><li>Tasarıma göre çalışması gereken bir şeyi düzeltmek için geçici bir çözüm kullanma (BitLocker etkinleştirmesi veya güncelleştirilen sistem saati gibi).</li><li>Cihaz Yöneticisi'ni yükseltme sürücüleri, cihazı kaldırma veya yeni değişiklikleri tarama gibi şeyleri yapmak için kullanın.</li></ul>
| **Önerilmez eylemler** | <ul><li>Yazılım veya tarayıcıları yükleme.</li><li>Çevre birimleri için sürücüler Windows ayarları dışında sürücüleri yükleme.</li><li>Dosyaları .msi veya .exe yükleme.</li><li>Windows yükleme.</li></ul>
| **Desteklenmiyor eylemler** | <ul><li>Microsoft Yönetilen Masaüstü güvenlik veya yönetim özellikleri veya işlemleriyle çakışan yazılım veya özellikleri yükleme.</li><li>Microsoft Yönetilen masaüstü Windows BitLocker gibi bir eklenti özelliğini devre dışı bırakma.</li><li>Kuruluş tarafından yönetilen ayarları değiştirme.</li><ul>

**Yükseltme isteği yapmak için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
1. Microsoft Yönetilen **Masaüstü bölümünde** Cihazlar'ı **seçin;** iki sekme vardır: **Cihazlar** sekmesi ve **Yükseltme istekleri** sekmesi.
1. Cihaz sekmesinde yeni bir yükseltme isteği **oluşturmak** için yükseltmek istediğiniz tek bir cihazı seçin.
1. Cihaz eylemleri açılan menüsünden Yükseltme **isteği'yi seçin**. Bu alanda cihazın adı önceden doldurulmuş olarak yeni bir yükseltme isteği uçarak girin gelecektir.
1. Bunun yerine, Yükseltme istekleri sekmesinde yeni bir yükseltme isteği **oluşturmak** için +Yeni yükseltme **isteği öğesini seçin.**
1. Şu ayrıntıları sağla:
    - **Destek bileti kimliği**: Bu, kendi destek bilet sisteminizdir.
    - **Cihaz adı**: Bu yalnızca Yükseltme istekleri sekmesinden **istek oluştururken** görüntülenir. Cihazın seri numarasını girin ve menüden cihazı seçin.
    - **Kategori**: Soruna en uygun kategoriyi seçin. Yakın bir seçenek yoksa Diğer'i **seçin**. Mümkünse bir kategori seçmek en iyisidir.
    - **Başlık**: Cihazda soruna ilişkin kısa bir açıklama girin.
    - **Eylem planı**: Yükseltme verildiktan sonra atılacak sorun giderme adımlarını sağlama.
1. **Gönder'i seçin**.
1. Tüm etkin ve kapalı istekler listesi ve ayrıntıları Yükseltme istekleri **sekmesinde** görülebilir.

## <a name="escalation-requests"></a>İlerlesyon istekleri

**Bir [sorunu](../service-description/user-support.md#escalation-portal) Microsoft'a yükseltme:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Kiracı yönetim **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Hizmet **istekleri'ne tıklayın**.
3. Hizmet istekleri **bölümünde + Yeni** destek **isteği'ne tıklayın**.
4. Başlık alanında kısa bir **açıklama** girin. Ardından, İstek **türünü Olay olarak** **ayarlayın**.
5. Soruna **en** **uygun Kategori ve** Alt kategoriyi seçin. Ardından, **Sonraki**'yi seçin.
6. Ayrıntılar **bölümünde** , aşağıdaki bilgileri sağlar:
    - **Açıklama**: Ekibimizin sorunu an çözmenize yardımcı olacak ek ayrıntılar ekleyin. Dosya iliştirmek zorundaysanız, dosyayı gönderdikten sonra isteği geri göndererek bunuabilirsiniz.
    - **Birincil kişi bilgileri**: Ekibimizle çalışmadan sorumlu olan ana kişi ile nasıl bağlantı kuramazsanız, ilgili bilgileri sağlar.
7. Önem Derecesi **düzeyini** seçin. Daha fazla bilgi için bkz [. Destek isteği önem derecesi tanımları](../working-with-managed-desktop/admin-support.md#support-request-severity-definitions).
8. Ekibin hızlı bir şekilde yanıt vermelerine yardımcı olmak için istek hakkında mümkün olan en fazla bilgiyi verin. İsteğin türüne bağlı olarak, farklı ayrıntılar sağlamanız gerekebilir.
9. Doğruluğu için sağlanıyor tüm bilgileri gözden geçirebilirsiniz.
10. Hazır olduğunda Oluştur'a **seçin**.
