---
title: IRM’yi bir şirket içi AD RMS sunucusunda kullanmak üzere yapılandırma
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
description: Exchange Online'da Bilgi Hakları Yönetimi'ni (IRM) Active Directory Rights Management Service (AD RMS) sunucusu kullanacak şekilde yapılandırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5bd4a104d4cceedbdb82c1ff2baac0b547b74fbe
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637515"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>IRM’yi bir şirket içi AD RMS sunucusunda kullanmak üzere yapılandırma

Exchange Online'daki Bilgi Hakları Yönetimi (IRM), şirket içi dağıtımlarla kullanmak için Windows Server 2008 ve sonraki sürümlerde bir bilgi koruma teknolojisi olan Active Directory Rights Management Services'i (AD RMS) kullanır. E-posta iletisine AD RMS hak ilkesi şablonu uygulanarak e-postaya IRM koruması uygulanır. Korumanın çevrimiçi, çevrimdışı ve kuruluşunuzun güvenlik duvarının içinde ve dışında gerçekleşmesi için, haklar iletinin kendisine eklenir.

Bu konu başlığında, IRM'yi AD RMS sunucusu kullanacak şekilde nasıl yapılandırabileceğiniz gösterilmektedir. Azure Active Directory ve Azure Rights Management ile Microsoft Purview İleti Şifrelemesi kullanma hakkında bilgi için [bkz. İleti şifrelemesi SSS](./ome-faq.yml).

Exchange Online'da IRM hakkında daha fazla bilgi edinmek için bkz. [Exchange Online'de Bilgi Hakları Yönetimi](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Bu görevi tamamlamak için tahmini süre: 30 dakika

- Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Hangi izinlere ihtiyacınız olduğunu görmek için, [Microsoft Mesajlaşma ilkesi ve uyumluluk izinleri](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) konusunda "Bilgi Hakları Yönetimi" girdisine bakın.

- AD RMS sunucusu Windows Server 2008 veya sonraki bir sürümünü çalıştırıyor olmalıdır. AD RMS'yi dağıtma hakkında ayrıntılı bilgi için bkz. [AD RMS Kümesi Yükleme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Windows PowerShell yükleme ve yapılandırma ve hizmete bağlanma hakkında ayrıntılı bilgi için bkz[. PowerShell Exchange Online bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu konudaki yordamlara uygulanabilecek klavye kısayolları hakkında bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi için klavye kısayolları](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Sorun mu yaşıyorsunuz? Exchange forumlarında yardım isteyin. [Exchange Server, Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=60612) veya [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) forumlarını ziyaret edin.[](https://go.microsoft.com/fwlink/p/?linkId=267542)

## <a name="how-do-you-do-this"></a>Bunu nasıl yapıyorsun?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>1. Adım: BIR AD RMS sunucusundan güvenilen yayımlama etki alanını (TPD) dışarı aktarmak için AD RMS konsolunu kullanma

İlk adım, güvenilen yayımlama etki alanını (TPD) şirket içi AD RMS sunucusundan bir XML dosyasına aktarmaktır. TPD, RMS özelliklerini kullanmak için gereken aşağıdaki ayarları içerir:

- Sertifikaları ve lisansları imzalamak ve şifrelemek için kullanılan sunucu lisans sertifikası (SLC)

- Lisanslama ve yayımlama için kullanılan URL'ler

- Bu TPD için belirli SLC ile oluşturulan AD RMS hak ilkesi şablonları

TPD'yi içeri aktardığınızda, Exchange Online depolanır ve korunur.

1. Active Directory Rights Management Services konsolunu açın ve AD RMS kümesini genişletin.

2. Konsol ağacında **Güven İlkeleri'ni** genişletin ve Güvenilen **Yayımlama Etki Alanları'na** tıklayın.

3. Sonuçlar bölmesinde, dışarı aktarmak istediğiniz etki alanının sertifikasını seçin.

4. **Eylemler** bölmesinde **Güvenilen Yayımlama Etki Alanını Dışarı Aktar'a** tıklayın.

5. **Yayımlama etki alanı dosyası** kutusunda, dosyayı yerel bilgisayardaki belirli bir konuma kaydetmek için **Farklı Kaydet'e** tıklayın. Dosya adı uzantısını belirttiğinizden `.xml` emin olmak için bir dosya adı yazın ve **Kaydet'e** tıklayın.

6. **Parola** ve **Parolayı Onayla** kutularına, güvenilen yayımlama etki alanı dosyasını şifrelemek için kullanılacak güçlü bir parola yazın. TPD'yi bulut tabanlı e-posta kuruluşunuza aktarırken bu parolayı belirtmeniz gerekir.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>2. Adım: TPD'yi Exchange Online içeri aktarmak için Exchange Yönetim Kabuğu'nı kullanma

TPD bir XML dosyasına aktarıldıktan sonra, Exchange Online içeri aktarmanız gerekir. TPD içeri aktarıldığında kuruluşunuzun AD RMS şablonları da içeri aktarılır. İlk TPD içeri aktarıldığında, bulut tabanlı kuruluşunuz için varsayılan TPD olur. Başka bir TPD'yi içeri aktarırsanız, **Varsayılan** anahtarını kullanarak bunu kullanıcılar için kullanılabilen varsayılan TPD yapabilirsiniz.

TPD'yi içeri aktarmak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Active Directory Rights Management Services konsolunda _ExtranetLicensingUrl_ ve _IntranetLicensingUrl_ parametrelerinin değerlerini alabilirsiniz. Konsol ağacında AD RMS kümesini seçin. Lisans URL'leri sonuçlar bölmesinde görüntülenir. Bu URL'ler, içeriğin şifresinin çözülmesi gerektiğinde ve Exchange Online hangi TPD'nin kullanılacağını belirlemesi gerektiğinde e-posta istemcileri tarafından kullanılır.

Bu komutu çalıştırdığınızda bir parola girmeniz istenir. AD RMS sunucunuzdan TPD'yi dışarı aktarırken belirttiğiniz parolayı girin.

Örneğin aşağıdaki komut, AD RMS sunucunuzdan dışarı aktardığınız ve Yönetici hesabının masaüstüne kaydettiğiniz XML dosyasını kullanarak Dışarı Aktarılan TPD adlı TPD'yi içeri aktarır. Name parametresi, TPD'ye bir ad belirtmek için kullanılır.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>TPD'yi başarıyla içeri aktardığını nasıl anlarsınız?

TPD'yi başarıyla içeri aktardığınızdan emin olmak için **get-RMSTrustedPublishingDomain** cmdlet'ini çalıştırarak Exchange Online kuruluşunuzdaki TPD'leri alın. Ayrıntılar için [bkz. Get-RMSTrustedPublishingDomain'deki](/powershell/module/exchange/get-rmstrustedpublishingdomain) örnekler.

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>3. Adım: Ad RMS hak ilkesi şablonunu dağıtmak için Exchange Management Shell'i kullanma

TPD'yi içeri aktardıktan sonra, bir AD RMS hak ilkesi şablonunun dağıtılmış olduğundan emin olmanız gerekir. Dağıtılmış şablon, Web üzerinde Outlook (eski adıyla Outlook Web App) kullanıcıları tarafından görülebilir ve bu şablon daha sonra şablonları bir e-posta iletisine uygulayabilir.

Varsayılan TPD'de bulunan tüm şablonların listesini döndürmek için aşağıdaki komutu çalıştırın:

```powershell
Get-RMSTemplate -Type All | fl
```

_Tür_ parametresinin değeri ise`Archived`, şablon kullanıcılara görünmez. Web üzerinde Outlook'da yalnızca varsayılan TPD'deki dağıtılmış şablonlar kullanılabilir.

Şablonu dağıtmak için aşağıdaki komutu çalıştırın:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Örneğin, aşağıdaki komut Şirket Gizli şablonunu içeri aktarır.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) ve [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>İletme şablonu

Varsayılan TPD'yi şirket içi kuruluşunuzdan Exchange Online'a aktardığınızda, **İletme** adlı bir AD RMS hak ilkesi şablonu içeri aktarılır. Varsayılan olarak, varsayılan TPD'yi içeri aktardığınızda bu şablon dağıtılır. **İletme** şablonunu değiştirmek için **Set-RMSTemplate** cmdlet'ini kullanamazsınız.

İletiye **İletme** şablonu uygulandığında, iletiyi yalnızca iletide adreslenen alıcılar okuyabilir. Ayrıca alıcılar aşağıdakileri yapamaz:

- İletiyi başka bir kişiye iletin.
- İletideki içeriği kopyalayın.
- İletiyi yazdırın.

> [!IMPORTANT]
> **İletme** şablonu, bir iletideki bilgilerin üçüncü taraf ekran yakalama programlarıyla, kameralarla veya kullanıcıların bilgileri el ile transkribe etmeleriyle kopyalanmasını önleyemez

IRM koruma gereksinimlerinizi karşılamak için şirket içi kuruluşunuzdaki AD RMS sunucusunda ek AD RMS hak ilkesi şablonları oluşturabilirsiniz. Ek AD RMS hak ilkesi şablonları oluşturursanız, TPD'yi şirket içi AD RMS sunucusundan yeniden dışarı aktarmanız ve TPD'yi bulut tabanlı e-posta kuruluşunda yenilemeniz gerekir.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>AD RMS hak ilkesi şablonunu başarıyla dağıttığınız nasıl anlarsınız?

ve AD RMS hak ilkesi şablonunu başarıyla dağıttığınız doğrulamak için **Get-RMSTemplate** cmdlet'ini çalıştırarak şablonun özelliklerini denetleyin. Ayrıntılar için [Get-RMSTemplate'deki örneklere](/powershell/module/exchange/get-rmstemplate) bakın.

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>4. Adım: IRM'yi etkinleştirmek için Exchange Yönetim Kabuğu'nı kullanma

TPD'yi içeri aktardıktan ve bir AD RMS hak ilkesi şablonu dağıttıktan sonra, bulut tabanlı e-posta kuruluşunuzda IRM'yi etkinleştirmek için aşağıdaki komutu çalıştırın.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>IRM'nin başarıyla etkinleştirildiğini nasıl anlarsınız?

IRM'yi başarıyla etkinleştirdiğinizden emin olmak için [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) cmdlet'ini çalıştırarak Exchange Online kuruluştaki IRM yapılandırmasını denetleyin.

## <a name="how-do-you-know-this-task-worked"></a>Bu görevin çalıştığını nasıl anlarsınız?
<a name="sectionSection2"> </a>

TPD'yi başarıyla içeri aktarıp IRM'yi etkinleştirdiğinizden emin olmak için aşağıdakileri yapın:

- IRM işlevselliğini test etmek için **Test-IRMConfiguration** cmdlet'ini kullanın. Ayrıntılar için bkz. [Test-IRMConfiguration'daki](/powershell/module/exchange/test-irmconfiguration) "Örnek 1".

- genişletilmiş menüden **İzinleri ayarla** seçeneğini belirleyerek Web üzerinde Outlook yeni bir ileti oluşturup IRM ile koruyun (![Diğer Seçenekler Simgesi).](../media/ITPro-EAC-MoreOptionsIcon.gif)).
