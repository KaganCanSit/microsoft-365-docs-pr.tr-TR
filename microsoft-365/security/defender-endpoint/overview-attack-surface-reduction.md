---
title: Saldırı yüzeyini azaltmayı (ASR) anlama ve kullanma
ms.reviewer: ''
description: Uç nokta için Microsoft Defender'ın saldırı yüzeyini azaltma özellikleri hakkında bilgi öğrenin.
keywords: asr, saldırı yüzeyini azaltma, Endpoint için Microsoft Defender, microsoft defender, virüsten koruma, av, windows defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.custom: asr
ms.topic: conceptual
ms.technology: mde
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: 78fdd5c6c02990943874807c285f8e5eb60ad6ad
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015231"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Saldırı yüzeyini azaltma özelliklerini anlama ve kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Saldırı yüzeyleri, kuruluşlarının siber tehditlere ve saldırılara açık olduğu tüm yerlerdir. Uç nokta için Defender, saldırı alanlarınızı azaltmanıza yardımcı olacak çeşitli özellikler içerir. Saldırı yüzeyini azaltma hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Saldırı yüzeyini azaltma özelliklerini yapılandırma

Ortamınıza saldırı yüzeyini azaltmayı yapılandırmak için şu adımları izleyin:

1. [Sistem yalıtlığı için donanım tabanlı Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Uygulama denetimi etkinleştirme.

   1. Temel ilkeleri gözden Windows. Bkz [. Örnek Temel İlkeler](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Uygulama [denetimi Windows Defender kılavuzuna bakın](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Uygulama Denetimi [(WDAC) Windows Defender dağıtma'ya bakın](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide).

3. [Denetimli klasör erişimini etkinleştirin](enable-controlled-folders.md).

4. [Ağ korumasını açma](enable-network-protection.md).

5. [Exploit Protection'i etkinleştirin](enable-exploit-protection.md).

6. [Saldırı yüzeyini azaltma kurallarını dağıtın](attack-surface-reduction-rules-deployment.md).

7. Ağ güvenlik duvarınızı ayarlayın.

   1. Gelişmiş güvenlikli Güvenlik [Windows Defender genel bir bakış elde.](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
   2. Güvenlik duvarı [Windows Defender tasarımına karar](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) vermek için Güvenlik Duvarı tasarım kılavuzunu kullanın.
   3. Gelişmiş güvenlik [Windows Defender duvarı ayarlamak](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) için Güvenlik Duvarı dağıtım kılavuzunu kullanın.

> [!TIP]
> Çoğu durumda saldırı yüzeyini azaltma özelliklerini yapılandırarak çeşitli yöntemlerden birini seçebilirsiniz:
>
> - Microsoft Endpoint Manager (artık Microsoft Intune ve Microsoft Endpoint Configuration Manager)
> - Grup İlkesi
> - PowerShell cmdlet'leri

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da saldırı yüzeyini azaltmayı test eder

Kuruluş güvenlik ekibinin bir parçası olarak, nasıl çalışacaklarını görmek üzere denetim modunda çalıştıracak şekilde saldırı yüzeyini azaltma özelliklerini yapılandırabilirsiniz. Denetim modunda şunları etkinleştirebilirsiniz:

- Saldırı yüzeyini azaltma kuralları
- Exploit protection
- Ağ koruması
- Denetim modunda denetimli klasör erişimi

Denetim modu, özelliği etkinleştirmiş olsaydı *neler* olacağının kaydını görmenizi sağlar.

Özelliklerin nasıl çalışta olduğunu test etmek için denetim modunu etkinleştirebilirsiniz. Yalnızca test için denetim modunun etkinleştirilmesi, denetim modunun iş hattı uygulamalarınızı etkilemesini önlemeye yardımcı olur. Ayrıca, belirli bir süre boyunca kaç şüpheli dosya değiştirme girişiminin olduğu hakkında da fikir de eldeebilirsiniz.

Özellikler, uygulamaların, betiklerin veya dosyaların değiştirilmesini engellemez veya engellemez. Öte yandan, Windows Günlüğü özellikleri tamamen etkinleştirmiş gibi olayları kaydedecek. Denetim moduyla, etkinleştirildiğinde özelliğin neleri etkileyeceğini görmek için olay günlüğünü gözden geçirebilirsiniz.

Denetlenen girdileri bulmak için Uygulamalar ve Hizmetler  \> **Microsoft** \> Windows **Windows Defender** \>  \> **gidin**.

Her olay için daha büyük ayrıntılar almak üzere Uç Nokta için Defender'ı kullanın. Saldırı yüzeyini azaltma kurallarını araştırırken bu ayrıntılar özellikle yararlı olur. Uç nokta konsolu için Defender'ın kullanımı [, uyarı zaman çizelgesi ve soruşturma senaryolarının bir parçası olarak sorunları araştırmana olanak sağlar](investigate-alerts.md).

Grup İlkesi, PowerShell ve yapılandırma hizmet sağlayıcılarını (CSP) kullanarak denetim modunu etkinleştirebilirsiniz.

> [!TIP]
> Özelliklerin çalıştığını onaylamak ve nasıl Windows Defender görmek için [demo.wd.microsoft.com'da](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Test Planı web sitesini ziyaret edebilirsiniz.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

| Denetim seçenekleri | Denetim modunu etkinleştirme | Etkinlikleri görüntüleme |
|---|---|---|
| Denetim tüm olaylar için geçerlidir | [Denetimli klasör erişimini etkinleştirme](enable-controlled-folders.md) | [Denetimli klasör erişimi olayları](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| Denetim tek tek kurallar için geçerlidir | [1. Adım: Denetimi kullanarak ASR kurallarını test edin](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [2. Adım: Saldırı yüzeyini azaltma kuralları raporlama sayfasını anlama](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| Denetim tüm olaylar için geçerlidir | [Ağ korumasını etkinleştirme](enable-network-protection.md) | [Ağ koruma olayları](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| Denetim, tek tek risk azaltmalara uygulanır | [Exploit Protection'i etkinleştirme](enable-exploit-protection.md) | [Exploit protection events](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

## <a name="view-attack-surface-reduction-events"></a>Saldırı yüzeyini azaltma etkinliklerini görüntüleme

Hangi kuralların veya ayarların çalıştığını izlemek için Olay Görüntüleyicisi'nde saldırı yüzeyini azaltma etkinliklerini gözden geçirebilirsiniz. Ayrıca, her türlü ayarın "gürültülü" olup olmadığını veya günlük iş akışınızı etkiley olup olmadığını da belirlenebilirsiniz.

Özellikleri değerlendirirken etkinlikleri gözden geçirmek yararlı olur. Özellikler veya ayarlar için denetim modunu etkinleştirebilir ve ardından tam olarak etkinleştirilmişse neler olacağını gözden geçirebilirsiniz.

Bu bölümde tüm olaylar, ilişkili özellikleri veya ayarları listelenmiş, özel görünümlerin nasıl özel görünümler oluşturularak belirli olaylara filtre uygulanmış olarak nasıl oluşturul açık olduğu anlatıldı.

E5 aboneliğiniz varsa ve Uç Nokta için Microsoft Defender kullanıyorsanız, Windows Güvenliği, bloklar ve uyarılar hakkında [ayrıntılı raporlama alın](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Saldırı yüzeyini azaltma özelliklerini gözden geçirmek için özel görünümleri kullanma

Etkinlik Görüntüleyicisi'nde özel Windows yalnızca belirli özelliklere ve ayarlara yönelik olayları görmek için. En kolay yol, özel görünümü BIR XML dosyası olarak içeri aktarmanızdır. XML'yi doğrudan bu sayfadan kopyaleyebilirsiniz.

Ayrıca, özelliğe karşılık gelen olay alanına el ile de gezinebilirsiniz.

#### <a name="import-an-existing-xml-custom-view"></a>Varolan bir XML özel görünümünü içeri aktarma

1. Boş bir .txt oluşturun ve kullanmak istediğiniz özel görünümün XML dosyasını .txt. Kullanmak istediğiniz özel görünümlerin her biri için bunu kullanın. Dosyaları aşağıdaki gibi yeniden adlandırabilirsiniz (dosya türünü aşağıdaki gibi .txt .xml:
    - Denetimli klasör erişimi olayları özel görünümü: *cfa-events.xml*
    - Exploit protection events custom view: *ep-events.xml*
    - Saldırı yüzeyini azaltma etkinlikleri özel görünümü: *asr-events.xml*
    - Ağ/ koruma olayları özel görünümü: *np-events.xml*

2. Olay **Görüntüleyicisi'ne** olay Başlat menüsü Görüntüleyicisi'ni **açın**.

3. Eylem Özel **Görünümü** \> **İçeri Aktar... seçeneğini seçin.**

   > [!div class="mx-imgBorder"]
   > ![Bile görüntüleyicisi penceresinin sol tarafından Özel görünümü içeri aktar'ı vurgulayan animasyon.](images/events-import.gif)

4. İstediğiniz özel görünüm için XML dosyasını ayıklayın ve seçin.

5. **Aç**'ı seçin.

6. Yalnızca bu özellikle ilgili olayları göstermek için filtre olan özel bir görünüm oluşturacak.

#### <a name="copy-the-xml-directly"></a>XML'yi doğrudan kopyalama

1. Olay **Görüntüleyicisi'ne** Başlat menüsü Görüntüleyicisi'ni Windows **açın**.

2. Sol panelde, **Eylemler'in altında Özel** Görünüm **Oluştur... öğesini seçin.**

   > [!div class="mx-imgBorder"]
   > ![Olay görüntüleyici penceresinde özel görünüm oluştur seçeneğini vurgulayan animasyon.](images/events-create.gif)

3. XML sekmesine gidin ve Sorguyu el ile **düzenle'yi seçin**. XML seçeneğini kullanırsanız, Filtre sekmesini kullanarak sorguyu **düzenley neler** olduğunu bir uyarıyla görebilirsiniz. **Evet**'i seçin.

4. Olayları filtrelemek istediğiniz özelliğin XML kodunu XML bölümüne yapıştırın.

5. **Tamam**'ı seçin. Filtreniz için bir ad belirtin. Bu, yalnızca bu özellikle ilgili olayları gösterecek şekilde filtre oluşturan özel bir görünüm oluşturur.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>Saldırı yüzeyini azaltma kuralı olayları için XML

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>Denetimli klasör erişimi olayları için XML

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>Exploit protection events için XML

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Security-Mitigations/KernelMode">
   <Select Path="Microsoft-Windows-Security-Mitigations/KernelMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Concurrency">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Contention">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Messages">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Operational">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Power">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Render">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Tracing">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/UIPI">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="System">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Security-Mitigations/UserMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-network-protection-events"></a>Ağ koruma olayları için XML

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>Saldırı yüzeyini azaltma etkinliklerinin listesi

Tüm saldırı yüzeyini azaltma olayları Microsoft > Windows'de Uygulamalar ve **> Hizmet Günlükleri > Windows** ardından aşağıdaki tabloda listelenmiş olarak klasör veya sağlayıcı altında yer alır.

Bu olaylara, Olay görüntüleyicisinde Windows erişabilirsiniz:

1. Başlat menüsünü **açın** , olay **görüntüleyicisi yazın** ve Olay Görüntüleyicisi'nin **sonucu** seçin.
2. **Microsoft > Windows >'>'i** genişletin ve ardından aşağıdaki tabloda Sağlayıcı **/kaynak altında listelenen** klasöre gidin.
3. Olayları görmek için alt öğeye çift tıklayın. Olaylar arasında kaydırarak bulmak için birini bulun.

   ![Olay Görüntüleyicisi'ni kullanmayı gösteren animasyon.](images/event-viewer.gif)

<br>

****

|Özellik|Sağlayıcı/kaynak|Olay Kimliği|Açıklama|
|---|---|:---:|---|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|1|ACG denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|2|ACG zorunlu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|3|Alt işlemlerin denetimine izin verme|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|4|Alt işlemlerin engel olmasına izin verme|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|5|Düşük bütünlük resimleri denetimini engelleme|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|6|Düşük bütünlük resimleri bloğu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|7|Uzaktan resim denetimini engelleme|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|8|Uzak resimleri engelleme|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|9|win32k sistem aramaları denetimini devre dışı bırakma|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|10|win32k sistem çağrıları engellemesini devre dışı bırakma|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|11|Kod bütünlüğü koruması denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|12|Kod bütünlüğü koruma bloğu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|13|EAF denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|14|EAF zorunlu kılınma|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|15|EAF+ denetim|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|16|EAF+ zorunlu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|17|IAF denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|18|IAF zorunlu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|19|STACKPivot denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|20|STACKPivot zorunlu|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|21|BUBANI ArayanYopya Denetimi denetle|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|22|ENFORCE CallerCheck enforce|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|23|BURAK SimExec denetimi|
|Exploit protection|Security-Mitigations (Kernel Modu/Kullanıcı Modu)|24|BURAK SimExec zorunlu|
|Exploit protection|WER-Diagnostics|5|CFG Bloğu|
|Exploit protection|Win32K (İşlemde)|260|Güvenilmeyen Yazı Tipi|
|Ağ koruması|Windows Defender (İşlem)|5007|Ayarların değiştir olduğu olay|
|Ağ koruması|Windows Defender (İşlem)|1125|Denetim modunda Ağ korumasının çalışma olduğu olay|
|Ağ koruması|Windows Defender (İşlem)|1126|Block-mode'da Ağ korumasının müdahalesi sırasında olay|
|Denetimli klasör erişimi|Windows Defender (İşlem)|5007|Ayarların değiştir olduğu olay|
|Denetimli klasör erişimi|Windows Defender (İşlem)|1124|Denetlenen Denetimli klasör erişimi olayı|
|Denetimli klasör erişimi|Windows Defender (İşlem)|1123|Engellenmiş Denetimli klasör erişimi olayı|
|Denetimli klasör erişimi|Windows Defender (İşlem)|1127|Engellenmiş Denetimli klasör erişimi sektör yazma bloğu olayı|
|Denetimli klasör erişimi|Windows Defender (İşlem)|1128|Denetlenen Denetimli klasör erişimi sektör yazma bloğu olayı|
|Saldırı yüzeyini azaltma|Windows Defender (İşlem)|5007|Ayarların değiştir olduğu olay|
|Saldırı yüzeyini azaltma|Windows Defender (İşlem)|1122|Denetim modunda kural geldiğinde olay|
|Saldırı yüzeyini azaltma|Windows Defender (İşlem)|1121|Engelleme modunda kural geldiğinde olay|

>[!NOTE]
> Kullanıcı açısından bakıldığında, ASR Uyarı modu bildirimleri saldırı yüzeyini azaltma kuralları için Windows Bildirimi olarak yapılır.
>
> ASR'de Ağ Koruması yalnızca Denetim ve Engelleme modları sağlar.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Saldırı yüzeyini azaltma hakkında daha fazla bilgi edinmek için kaynaklar

Videoda da belirtildiği gibi, Uç Nokta için Defender çeşitli saldırı yüzeyini azaltma özellikleri içerir. Daha fazla bilgi edinmek için aşağıdaki kaynakları kullanın:

| Makale | Açıklama |
|:---|:---|
| [Donanım tabanlı yalıtım](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Bir sistem başlatılırken ve çalışırken bütünlüğünü koruyun ve koruyun. Yerel ve uzak doğrulama aracılığıyla sistem bütünlüğünü doğrulama. Kötü amaçlı web sitelerine karşı Microsoft Edge için kapsayıcı yalıtım kullanın. |
| [Uygulama denetimi](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Uygulamalarınızı çalıştırmak için güven kazanmak amacıyla uygulama denetimi kullanın. |
| [Denetimli klasör erişimi](controlled-folders.md) | Kötü amaçlı veya şüpheli uygulamaların (dosya şifreleme fidye yazılımı da içinde) önemli sistem klasörlerinizin dosyalarında değişiklik yapmalarını önlemeye yardımcı olun (Yazılım Microsoft Defender Virüsten Koruma) |
| [Ağ koruması](network-protection.md) | Ağ trafiğinize ve kuruma bağlı cihazlarında bağlantı için korumayı genişletebilirsiniz. (Gerekli Microsoft Defender Virüsten Koruma) |
| [Exploit protection](exploit-protection.md) | Kuruluşun kullandığı işletim sistemlerinin ve uygulamalarının istismara karşı korunmasına yardımcı olun. Exploit protection ayrıca üçüncü taraf virüsten koruma çözümleriyle de çalışır. |
| [Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md) | Uygulamalarınız, kötü amaçlı yazılımı durdurmanıza yardımcı olan akıllı kurallarla güvenlik açıklarını (saldırı yüzeyleri) azaltabilirsiniz. (Gerekli Microsoft Defender Virüsten Koruma). |
| [Cihaz denetimi](device-control-report.md) | Kuruluşta çıkarılabilir depolama alanı ve USB sürücüleri gibi cihazlarda kullanılan medyayı denetleyerek ve bu medyayı denetleyerek veri kaybına karşı koruma sağlar. |
