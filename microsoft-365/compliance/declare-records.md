---
title: Saklama etiketleri kullanarak kayıtları beyan etme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bekletme etiketlerini kullanarak kayıtları bildirin.
ms.openlocfilehash: 6a68f63c3f304ed4a5f3d79445cd713125327bd2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624299"
---
# <a name="declare-records-by-using-retention-labels"></a>Saklama etiketleri kullanarak kayıtları beyan etme

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Belgeleri ve e-postaları [kayıt](records-management.md#records) olarak bildirmek için, içeriği **kayıt** veya **mevzuat kaydı** olarak işaretleyen [bekletme etiketlerini](retention.md#retention-labels) kullanırsınız.

Kayıt mı yoksa mevzuat kaydı mı kullanacağınızdan emin değilseniz bkz. [İzin verilen veya engellenen eylemler için kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). Mevzuat kayıtlarını kullanmanız gerekiyorsa, sonraki bölümde açıklandığı gibi önce bir PowerShell komutu çalıştırmanız gerekir.

Daha sonra bu etiketleri bir bekletme etiketi ilkesinde yayımlayarak kullanıcıların ve yöneticilerin bunları içeriğe uygulayabilmesini sağlayabilir veya öğeleri kayıt olarak işaretleyen etiketler için (düzenleyici kayıt değil), bu etiketleri kayıt bildirmek istediğiniz içeriğe otomatik olarak uygulayabilirsiniz.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>İçeriği mevzuat kaydı olarak işaretleme seçeneğini görüntüleme

> [!NOTE]
> Aşağıdaki yordam, denetim günlüğünün [Bekletme ilkesi ve bekletme etiketi etkinlikleri](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) bölümünde **bekletme etiketleri için etkinleştirilen mevzuat kaydı seçeneğini** günlüğe kaydeden denetlenebilir bir eylemdir.

Varsayılan olarak, içeriği düzenleyici kayıt olarak işaretlemek için bekletme etiketi seçeneği bekletme etiketi sihirbazında görüntülenmez. Bu seçeneği görüntülemek için önce bir PowerShell komutu çalıştırmanız gerekir:

1. [Office 365 Güvenlik & Uyumluluğu PowerShell'e bağlanın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    Onaylama istemi yoktur ve ayar hemen etkinleşir.

Bekletme etiketi sihirbazında bu seçeneği görme konusunda fikrinizi değiştirirseniz, aynı cmdlet'i **false** değeriyle çalıştırarak yeniden gizleyebilirsiniz: `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>Kayıtları bildirmek için bekletme etiketlerini yapılandırma

Microsoft Purview uyumluluk portalı **Kayıt Yönetimi** çözümünden bir bekletme etiketi oluşturduğunuzda, öğeleri kayıt olarak işaretleme seçeneğiniz vardır. Önceki bölümden PowerShell komutunu çalıştırdıysanız, alternatif olarak öğeleri mevzuat kaydı olarak işaretleyebilirsiniz.

Örneğin:

![İçeriği kayıt veya mevzuat olarak işaretlemek için bir bekletme etiketi yapılandırın.](../media/declare-records.png)

Bu bekletme etiketini kullanarak artık gerektiğinde SharePoint veya OneDrive belgelerine ve Exchange e-postalarına uygulayabilirsiniz.

Tam yönergeler için:

- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)

- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md) (mevzuat kayıtları için desteklenmez)

## <a name="tenant-setting-for-editing-record-properties"></a>Kayıt özelliklerini düzenlemek için kiracı ayarı

SharePoint ve OneDrive'da öğeleri kayıt olarak (mevzuat kayıtları yerine) bildirmek için bekletme etiketleri kullanacaksanız, dosyalar 0 bayttan büyük olduğunda kullanıcıların [kilitli kaydın](record-versioning.md) özelliklerini düzenlemesine olanak tanıyan varsayılan kiracı ayarını değiştirmeniz gerekip gerekmediğini göz önünde bulundurun.

Bu varsayılanı değiştirmek için [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) >  **Kayıtlar yönetimi****Kayıtları yönetim** >  ayarları  > **Bekletme etiketleri** > **Kayıt özelliklerinin düzenlenmesine izin ver'e** gidin ve **ardından Kullanıcıların kayıt özelliklerini düzenlemesine izin ver** ayarını kapatın.

## <a name="applying-the-configured-retention-label-to-content"></a>Yapılandırılan bekletme etiketini içeriğe uygulama

Öğeleri kayıt veya mevzuat kaydı olarak işaretleyen bekletme etiketleri kullanıcıların bunları uygulamalarda uygulaması için kullanılabilir hale getirildiğinde:

- Exchange için, posta kutusuna yazma erişimi olan tüm kullanıcılar bu etiketleri uygulayabilir.
- SharePoint ve OneDrive için, varsayılan Üyeler grubundaki (Katkıda Bulunma izin düzeyi) tüm kullanıcılar bu etiketleri uygulayabilir.

Bekletme etiketi kullanılarak kayıt olarak işaretlenmiş belge örneği:

![Kayıt olarak etiketlenmiş belgenin Ayrıntılar bölmesi.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>Kayıt bildirilen etiketli öğeler için denetim günlüğünde arama yapma

Öğeleri kayıt olarak bildirmek için etiketleme eylemleri denetim günlüğüne kaydedilir.

SharePoint öğeleri için:
- **Dosya ve sayfa etkinlikleri'nden** **Dosya için bekletme etiketi değiştirildi'yi** seçin. Bu denetim olayı, öğeleri kayıt, mevzuat kaydı olarak işaretleyen veya standart bekletme etiketleri olan bekletme etiketlerine yöneliktir.

Exchange öğeleri için:
- **Exchange posta kutusu etkinliklerinden****, İletiyi kayıt olarak etiketle'yi** seçin. Bu denetim olayı, öğeleri kayıt veya mevzuat kaydı olarak işaretleyen bekletme etiketlerine yöneliktir.

Bu olayları arama hakkında daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'nde denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities) yapma.

## <a name="next-steps"></a>Sonraki adımlar

[SharePoint veya OneDrive'da depolanan kayıtları güncelleştirmek için kayıt sürümü oluşturmayı](record-versioning.md) nasıl kullanabileceğinizi anlayın.
