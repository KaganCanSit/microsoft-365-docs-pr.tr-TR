---
title: Bekletme etiketlerini kullanarak kayıtları bildir
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
ms.openlocfilehash: 93e51698109819f4743dd4b5b45f5a5177739a2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324851"
---
# <a name="declare-records-by-using-retention-labels"></a>Bekletme etiketlerini kullanarak kayıtları bildir

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Belgeleri ve e-postaları kayıt [olarak beyan](records-management.md#records) etmek için, içeriği [kayıt](retention.md#retention-labels) veya mevzuat kaydı olarak **işaret** eden bekletme **etiketleri kullanırsınız**.

Kayıt mı yoksa mevzuat kaydı mı kullanmaya karar verilmiyorsa, bkz. İzin verilen veya engellenen eylemlerle ilgili [kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). Mevzuat kayıtlarını kullanmak zorundaysanız, önce sonraki bölümde açıklandığı gibi bir PowerShell komutu çalıştırmalısiniz.

Bu etiketleri bekletme etiketi ilkesinde yayımlayın; böylelikle kullanıcılar ve yöneticiler bunları içeriğe uygulayabilir veya öğeleri kayıt olarak işaret eden etiketler için (ancak yasal düzenleme kayıtları olarak değil), bu etiketleri kayıt beyan etmek istediğiniz içeriğe otomatik olarak uygulayabilirsiniz.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>İçeriği yasal düzenleme kaydı olarak işaretleme seçeneğini görüntüleme

> [!NOTE]
> Aşağıdaki yordam, denetim günlüğünün Bekletme ilkesi ve bekletme  etiketi etkinlikleri bölümünde bekletme etiketleri için günlüğe kaydetme Yasal düzenlemelere kaydetme [seçeneği olan](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) denetlenebilir bir eylemdir.

Varsayılan olarak, bekletme etiketi sihirbazında içeriği yasal düzenlemelere uygun kayıt olarak işaretlemek için olan bekletme etiketi seçeneği görüntülenmez. Bu seçeneği görüntülemek için önce bir PowerShell komutunu çalıştırmalısiniz:

1. [Bağlan Güvenlik ve Office 365 Merkezi PowerShell& e bakın](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    Onaylamanız istendiğinde, ayar hemen yürürlüğe girecektir.

Bekletme etiketi sihirbazında bu seçeneği görme konusunda fikir değiştirirseniz, aynı cmdlet'i yanlış değerle çalıştırarak yeniden **gizleyebilirsiniz** : `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>Bekletme etiketlerini kayıtları bildir olacak şekilde yapılandırma

Kayıt Yönetimi çözümünden bir bekletme **etiketi** oluşturmak için Microsoft 365 uyumluluk merkezi, öğeleri kayıt olarak işaretleme seçeneğiniz vardır. Önceki bölümden PowerShell komutunu kullandıysanız, alternatif olarak öğeleri mevzuat kaydı olarak işaretebilirsiniz.

Örneğin:

![İçeriği kayıt veya mevzuat olarak işaretlemek için bir bekletme etiketi yapılandırabilirsiniz.](../media/recordversioning6.png)

Artık bu bekletme etiketini kullanarak, gerektiğinde belgelerinizi SharePoint OneDrive e-Exchange e-postalara uygulayabilirsiniz.

Tam yönergeler için:

- [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)

- [İçeriklere otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md) (mevzuat kayıtları için desteklenmiyor)

## <a name="tenant-setting-for-editing-record-properties"></a>Kayıt özelliklerini düzenlemek için kiracı ayarı

SharePoint ve OneDrive'te öğeleri kayıt olarak (mevzuat kayıtları yerine) beyan etmek için bekletme etiketleri kullanıyorsanız, kullanıcıların 0 bayttan büyük dosyalar olduğunda kilitli bir kaydın özelliklerini düzenlemelerine olanak sağlayan varsayılan kiracı ayarını değiştirmeniz gerekip gerek olmadığını düşünün.[](record-versioning.md)

Bu varsayılanı değiştirmek için Microsoft 365 uyumluluk merkezi [](https://compliance.microsoft.com/) > **Cords yönetimiAcords** >  yönetim **ayarlarıRetention** >  >  etiketleri Kayıt özelliklerinin düzenlenmesine izin ver ve sonra Kullanıcıların kayıt özelliklerini düzenlemesine izin ver ayarını devre dışı **bırak**.

## <a name="applying-the-configured-retention-label-to-content"></a>Yapılandırılmış bekletme etiketini içeriğe uygulama

Öğeleri kayıt veya mevzuat kaydı olarak işaret alan bekletme etiketleri kullanıcıların bunları uygulamalarda uygulamalarına uygulayabilecekleri zaman:

- Örneğin Exchange posta kutusuna yazma erişimi olan tüm kullanıcılar bu etiketleri uygulayabilir.
- Varsayılan SharePoint ve OneDrive için, varsayılan Üyeler grubunda (Katkıda Bulun izin düzeyi) tüm kullanıcılar bu etiketleri uygulayabilir.

Bekletme etiketi kullanılarak kayıt olarak işaretlenmiş bir belge örneği:

![Kayıt olarak etiketlenen belgenin Ayrıntılar bölmesi.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>Denetim günlüğünde kayıt bildirilen etiketli öğeleri arama

Öğeleri kayıt olarak ifade etmek için etiketleme eylemleri denetim günlüğüne kaydedilir.

Diğer SharePoint için:
- Dosya **ve sayfa etkinlikleri'den**, bir dosya **için Bekletme etiketi değiştirildi'yi seçin**. Bu denetim olayı öğeleri kayıt, mevzuat kaydı veya standart bekletme etiketleri olarak işaret alan bekletme etiketlerine yöneliktir.

Diğer Exchange için:
- Posta **Exchange etkinlikleri için,** Kayıt **olarak etiketli ileti'yi seçin**. Bu denetim olayı, öğeleri kayıt veya mevzuat kaydı olarak işaret alan bekletme etiketlerine yöneliktir.

Bu olayları arama hakkında daha fazla bilgi için bkz. Güvenlik ve Uyumluluk [Merkezi'nde denetim & arama](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Sonraki adımlar

Kayıt sürümü kaydetmeyi kullanarak [başka bir dosyada veya başka bir dosyada depolanan SharePoint kullanabileceğiniz OneDrive](record-versioning.md).