---
title: Rol tabanlı erişim denetimi için roller oluşturma ve yönetme
description: Rol oluşturun ve rol tabanlı erişim denetimi uygulamasının bir parçası olarak bu role atanan izinleri Microsoft 365 Defender
keywords: kullanıcı rolleri, roller, access rbac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a959edf1eaefcb25fd3fb8279e7e03d317c4f12e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997555"
---
# <a name="create-and-manage-roles-for-role-based-access-control"></a>Rol tabanlı erişim denetimi için roller oluşturma ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-roles-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="create-roles-and-assign-the-role-to-an-azure-active-directory-group"></a>Rol oluşturma ve rolü bir grup Azure Active Directory atama

Aşağıdaki adımlar, iş yerlerinde roller oluşturmanıza Microsoft 365 Defender. Önceden bir kullanıcı grubu oluşturduğunuz Azure Active Directory varsaymaktadır.

1. Bir Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> veya Genel yönetici rolü atanmış bir hesabı kullanarak oturum açın.

2. Gezinti bölmesinde, Uç Noktalar **Rollerini Ayarlar** \> **Seçin** \> (**İzinler'in altında**).

3. Öğe **ekle'yi seçin**.

4. Role atamak istediğiniz rol adını, açıklamasını ve izinlerini girin.

5. Rolü **bir** Azure AD Güvenlik grubuna atamak için Sonraki'yi seçin.

6. Filtreyi kullanarak bu role eklemek istediğiniz Azure AD grubunu seçin.

7. **Kaydedin ve kapatın**.

8. Yapılandırma ayarlarını uygulama.

> [!IMPORTANT]
> Rolleri oluşturduktan sonra, bir cihaz grubu oluşturmanız ve yeni oluşturduğunuz bir role ataarak cihaz grubuna erişim sağlamanız gerekir.

### <a name="permission-options"></a>İzin seçenekleri

- **Verileri görüntüleme**
  - **Güvenlik işlemleri** - Portalda tüm güvenlik işlemleri verilerini görüntüleme
  - **Tehdit güvenlik açığı yönetimi**- Portalda Tehdit ve Güvenlik Açığı Yönetimi verilerini görüntüleme

- **Etkin düzeltme eylemleri**
  - **Güvenlik işlemleri** - Yanıt eylemleri alma, bekleyen düzeltme eylemlerini onaylama veya yok sayma, otomasyon ve göstergeler için izin verilen/engellenen listeleri yönetme
  - **Tehdit ve güvenlik açığı yönetimi- Özel durum işleme** - Yeni özel durumlar oluşturma ve etkin özel durumları yönetme
  - **Tehdit ve güvenlik açığı yönetimi- Düzeltme işleme** - Yeni düzeltme istekleri gönderme, bilet oluşturma ve mevcut düzeltme etkinliklerini yönetme

- **Uyarılar soruşturması** - Uyarıları yönetme, otomatik soruşturmalar başlatma, taramaları çalıştırma, soruşturma paketleri toplama, cihaz etiketlerini yönetme ve yalnızca taşınabilir yürütülebilir (PE) dosyaları indirme

- **Portal sistem ayarlarını yönetme** - Depolama ayarlarını, SIEM'yi ve tehdit intel API ayarlarını (genel olarak geçerlidir), gelişmiş ayarları, otomatik dosya yüklemelerini, rolleri ve cihaz gruplarını yapılandırma

    > [!NOTE]
    > Bu ayar yalnızca Uç nokta yöneticisi (varsayılan) için Microsoft Defender rolünde kullanılabilir.

- **Bulut için Defender'da** güvenlik ayarlarını yönetme - Uyarı gizleme ayarlarını yapılandırma, otomasyon için klasör dışlamalarını yönetme, ekleme ve çıkarılmış cihazları yönetme, e-posta bildirimlerini yönetme, değerlendirme laboratuvarı yönetme

- **Canlı yanıt özellikleri**
  - **Temel** komutlar:
    - Canlı yanıt oturumu başlatma
    - Uzak cihazda salt okunur canlı yanıt komutlarını gerçekleştirme (dosya kopyalama ve yürütme hariç)
    - Canlı yanıt yoluyla uzak cihazdan dosya indirme
  - **Gelişmiş** komutlar:
    - Dosya sayfasından PE ve PE olmayan dosyaları indirme
    - Upload uzak cihaza dosya yükleme
    - Dosya kitaplığından betiği görüntüleme
    - Dosyalar kitaplığından uzak cihazda betik yürütme

Kullanılabilir komutlar hakkında daha fazla bilgi için bkz [. Canlı yanıtı kullanarak cihazları araştırma](live-response.md).

## <a name="edit-roles"></a>Rolleri düzenleme

1. Hesapta Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> veya Genel yönetici rolü atanmış olarak oturum açın.

2. Gezinti bölmesinde, Uç Noktalar **Rollerini Ayarlar** \> **Seçin** \> (**İzinler'in altında**).

3. Düzenlemek istediğiniz rolü seçin.

4. **Düzenle**’ye tıklayın.

5. Role atanan ayrıntıları veya grupları değiştirebilirsiniz.

6. Kaydet ve **kapat'a tıklayın**.

## <a name="delete-roles"></a>Rolleri silme

1. Hesapta Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> veya Genel yönetici rolü atanmış olarak oturum açın.

2. Gezinti bölmesinde, Uç Noktalar **Rollerini Ayarlar** \> **Seçin** \> (**İzinler'in altında**).

3. Silmek istediğiniz rolü seçin.

4. Açılan düğmeye tıklayın ve Rolü **sil'i seçin**.

## <a name="related-topic"></a>İlgili konu

- [Portala erişmek için kullanıcı temel izinleri](basic-permissions.md)
- [Cihaz grupları oluşturma ve yönetme](machine-groups.md)
