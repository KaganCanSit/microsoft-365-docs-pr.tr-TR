---
title: IRM'yi şirket içi AD RMS sunucusunu kullanmak üzere yapılandırma
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3ecde857-4b7c-451d-b4aa-9eeffc8a8c61
ms.collection:
- M365-security-compliance
description: Bir Active Directory Rights Management Service (AD RMS) sunucusunu kullanmak Exchange Online altında Bilgi Hakları Yönetimi'nin (IRM) nasıl yapılandırıldığından emin olun.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f87992fc9be676b9485d6ec7a7b7ff1f3a4d39d9
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010039"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>IRM'yi şirket içi AD RMS sunucusunu kullanmak üzere yapılandırma

Exchange Online'te Şirket içi dağıtımlarla kullanım için, Exchange Online'te Bilgi Hakları Yönetimi (IRM), Active Directory Rights Management Services Server 2008 ve sonraki güncelleştirmelerde bir bilgi koruma teknolojisi olan Windows kullanır. IRM koruması, e-posta iletisine bir AD RMS hak ilkesi şablonu uygulanarak e-postaya uygulanır. Haklar iletinin kendisine iliştirilir ve böylelikle koruma, hem çevrimiçi, hem çevrimdışı hem de kurum güvenlik duvarı içinde ve dışında gerçekleşir.

Bu konu başlığında, IRM'yi ad RMS sunucusu kullanmak üzere nasıl yapılandırabilirsiniz? Proje yönetimi ve Azure Hak Yönetimi'Office 365 İleti Şifrelemesi yeni özellikleri Azure Active Directory hakkında daha fazla bilgi için SSS'ye [Office 365 İleti Şifrelemesi bakın](./ome-faq.yml).

2013'te IRM hakkında daha fazla bilgi Exchange Online [için](information-rights-management-in-exchange-online.md) bkz. Exchange Online.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Bu görevi tamamlamak için tahmini süre: 30 dakika

- Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerekli olduğunu görmek için, Mesajlaşma ilkesi ve uyumluluk izinleri başlığında yer alan "Bilgi [Hakları Yönetimi" girdisini](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) bakın.

- AD RMS sunucusunun, Sunucu Windows 2008 veya sonraki bir gelecek şekilde çalışıyor olması gerekir. AD RMS'yi dağıtma hakkında ayrıntılı bilgi için bkz [. AD RMS Kümesi yükleme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Hizmeti yükleme ve yapılandırma ve hizmete Windows PowerShell hakkında ayrıntılar için bkz. [Uzak PowerShell kullanarak Bağlan'Exchange Online'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu konu başlığı altında yer alan yordamlara uygulanabilecek klavye kısayolları hakkında bilgi için, Exchange Yönetim Merkezi'nde [yer alan Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Sorun mu var? Exchange forumlarında yardım alın. [Exchange Server, Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=60612) veya [Exchange Online Protection'da](https://go.microsoft.com/fwlink/p/?linkId=267542) [forumları ziyaret edin](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>Bunu nasıl yapacaksınız?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>1. Adım: AD RMS sunucusundan güvenilir bir yayımlama etki alanını (TPD) dışarı aktarma için AD RMS konsolunu kullanma

İlk adım, şirket içi AD RMS sunucusundan bir XML dosyasına güvenilen yayımlama etki alanı (TPD) dışarı aktarma işlemidir. TPD, RMS özelliklerini kullanmak için gereken aşağıdaki ayarları içerir:

- Sertifikaları ve lisansları imzalamak ve şifrelemek için kullanılan sunucu lisans sertifikası (SLC)

- Lisans ve yayımlama için kullanılan URL'ler

- Bu TPD için belirli SLC ile oluşturulan AD RMS hak ilkesi şablonları

TPD'yi içeri aktarabilir, bu alan tüm alanlarında Exchange Online.

1. Ad RMS Active Directory Rights Management Services açın ve ardından ad RMS kümesini genişletin.

2. Konsol ağacında Güven İlkeleri'ne **ve sonra** Güvenilen Yayımlama Etki **Alanları'na tıklayın**.

3. Sonuçlar bölmesinde, dışarı aktarmak istediğiniz etki alanının sertifikasını seçin.

4. Eylemler bölmesinde **Güvenilen Yayımlama** Etki Alanını **Dışarı Aktar'a tıklayın**.

5. Yayımlama etki **alanı dosyası kutusunda** , **dosyayı yerel bilgisayarda belirli** bir konuma kaydetmek için Farklı Kaydet'e tıklayın. Dosya adı uzantısını belirttiğinizden emin olarak bir dosya `.xml` adı yazın ve Kaydet'e **tıklayın**.

6. Parola ve **Parolayı** **Onayla** kutularına, güvenilir yayımlama etki alanı dosyasını şifrelemek için kullanılacak güçlü bir parola yazın. TPD'yi bulut tabanlı e-posta kuruluşa aktardıysanız bu parolayı belirtmeniz gerekir.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>2. Adım: TPD Exchange i içeri aktararak kaynak yönetim Exchange Online

TPD bir XML dosyasına aktarıldıktan sonra, bu dosyayı xml dosyasına aktarmanız Exchange Online. Bir TPD aktarıldında, kuruluşun AD RMS şablonları da aktarılır. İlk TPD içe aktarıldında, bulut tabanlı kuruluş için varsayılan TPD olur. Başka bir TPD'yi içeri aktardısanız,  Varsayılan anahtarı kullanarak bunu kullanıcıların kullanabileceği varsayılan TPD olarak değiştirebilirsiniz.

TPD'yi içeri aktarma işlemi için, aşağıdaki komutu Windows PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

_ExtranetLicensingUrl_ ve _IntranetLicensingUrl parametrelerinin_ değerlerini Active Directory Rights Management Services. Konsol ağacında AD RMS kümesini seçin. Lisans URL'leri sonuçlar bölmesinde görüntülenir. bu URL'ler, içeriğin şifresinin çözülmesi gereken ve TPD'nin Exchange Online olduğunda e-posta istemcileri tarafından kullanılır.

Bu komutu çalıştırsanız, parola girmeniz istenir. AD RMS sunucunuzdan TPD'yi dışarı aktardıysanız belirttiğiniz parolayı girin.

Örneğin, aşağıdaki komut AD RMS sunucunuzdan dışarı aktarmış ve Yönetici hesabının masaüstüne kaydeden XML dosyasını kullanarak Dışarı Aktarıldı TPD adlı TPD'yi içeri aktarır. Name parametresi, TPD'ye bir ad belirtmek için kullanılır.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>TPD'yi başarıyla aktarılmış olduğunu nasıl biliyorsunuz?

TPD'yi başarıyla aktarmış olduğunu doğrulamak için, **Get-RMSTrustedPublishingDomain** cmdlet'ini çalıştırarak Exchange Online TPD'leri alın. Ayrıntılar için [Get-RMSTrustedPublishingDomain'daki örneklere bakın](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>3. Adım: AD RMS Exchange ilkesi şablonunu dağıtmak için Kullanıcı Grubu Yönetim Kabuğu'nu kullanma

TPD'yi içeri aktardikten sonra, ad RMS hak ilkesi şablonunun dağıtıldığından emin olun. Dağıtılmış şablon, Web üzerinde Outlook e-posta iletisine uygulayabilecek Outlook Web App (eski adı Outlook Web App) kullanıcıları tarafından görülebilir.

Varsayılan TPD'de bulunan tüm şablonların listesini geri dönmek için, aşağıdaki komutu çalıştırın:

```powershell
Get-RMSTemplate -Type All | fl
```

Tür parametresinin _değeri_ `Archived`, şablon kullanıcılar tarafından görülmeyebilir. Yalnızca varsayılan TPD'de dağıtılmış şablonlar Web üzerinde Outlook.

Şablonu dağıtmak için aşağıdaki komutu çalıştırın:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Örneğin, aşağıdaki komut Şirket için Gizli şablonunu içeri aktarmaktadır.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) ve [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Do Not Forward şablonu

Varsayılan TPD'yi şirket içi kuruluştan Exchange Online'a aktarıyorsanız, **Do Not Forward** adlı bir AD RMS hak ilkesi şablonu içeri aktarılır. Varsayılan olarak, varsayılan TPD'yi içeri aktarıldığında bu şablon dağıtılmıştır. **Set-RMSTemplate** cmdlet'ini, İte etme şablonunu **değiştirmek için kullanasınız**.

İletiye **İleti gönderme** şablonu uygulandığında, yalnızca iletide adreslenen alıcılar iletiyi okuyabilir. Buna ek olarak, alıcılar şunları da gerçekleştirene kadar:

- İletiyi başka bir kişiye iletin.
- İletiden içerik kopyalayın.
- İletiyi yazdırma.

> [!IMPORTANT]
> **İtelamama** şablonu, bir iletide yer alan bilgilerin üçüncü taraf ekran yakalama programları, kameralar veya kullanıcılar tarafından el ile yazı yazarak kopyalanır

IRM koruma gereksinimlerinizi karşılamak için, şirket içi kuruluşun AD RMS sunucusunda ek AD RMS hak ilkesi şablonları oluşturabilirsiniz. Başka AD RMS hak ilkesi şablonları oluşturursanız, TPD'yi şirket içi AD RMS sunucusundan yeniden dışarı aktarmanız ve bulut tabanlı e-posta kuruluşunda TPD'yi yenilemeniz gerekir.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>AD RMS hak ilkesi şablonunu başarıyla dağıtık olduğunu nasıl bilebilirsiniz?

Ad RMS hak ilkesi şablonunu başarıyla dağıtık ve AD RMS hak ilkesi şablonunu doğrulamak için **, Get-RMSTemplate** cmdlet'ini çalıştırarak şablonun özelliklerini kontrol edin. Ayrıntılar için [Get-RMSTemplate'daki örneklere bakın](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>4. Adım: IRM'yi etkinleştirmek Exchange Yönetim Kabuğu'nu kullanma

TPD'yi içeri aktardıktan ve AD RMS hak ilkesi şablonunu dağıttıktan sonra, aşağıdaki komutu çalıştırarak bulut tabanlı e-posta kuruluşta IRM'yi etkinleştirin.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>IRM'i başarıyla etkinleştirmiş olduğunu nasıl biliyorsunuz?

IRM'i başarıyla etkinleştirdiğini doğrulamak için, [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) cmdlet'ini çalıştırarak kuruluş içinde IRM Exchange Online çalıştırın.

## <a name="how-do-you-know-this-task-worked"></a>Bu görevin çalıştığını nasıl biliyorsunuz?
<a name="sectionSection2"> </a>

TPD'yi başarıyla aktarılmış ve IRM'yi etkinleştirmiş olmak için, şunları yapın:

- **IRM işlevselliğini test etmek için Test-IRMConfiguration** cmdlet'ini kullanın. Ayrıntılar için, [Test-IRMConfiguration'daki](/powershell/module/exchange/test-irmconfiguration) "Örnek 1"e bakın.

- Genişletilmiş menüden İzinleri ayarla Web üzerinde Outlook seçerek (Diğer Seçenekler Simgesi)'te IRM  ile yeni bir![ ileti yazın ve IRM ile koruyun.](../media/ITPro-EAC-MoreOptionsIcon.gif)
