---
title: Microsoft Defender Virüsten Koruma kimlikleri ve hata kodları
description: Olay kimliklerini ve hatalarını Microsoft Defender Virüsten Koruma ve çözümlerini denetleyin
keywords: olay, hata kodu, siem, günlük, sorun giderme, wef, windows olay iletme
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/27/2022
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: db4401e1215ab50e47425dee15a1337466e1e98a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015227"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Sorunları gidermek için olay günlüklerini ve hata kodlarını Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu konu başlığıyla ilgili bir Microsoft Defender Virüsten Koruma karşılaşırsanız, eşleşen bir sorunu ve olası çözümü bulmak için bu konu başlığıdaki tablolarda arama bulabilirsiniz.

Tablolar listesi:

- [Microsoft Defender Virüsten Koruma kimlikleri (](#windows-defender-av-ids)bu kimlikler Windows 10, Windows 11 ve 24 saat Windows Server 2016)
- [Microsoft Defender Virüsten Koruma hata kodlarını geri tıklatın](#error-codes)
- [İç Microsoft Defender Virüsten Koruma istemci hata kodları (geliştirme ve test sırasında Microsoft tarafından kullanılır)](#internal-error-codes)

> [!TIP]
> Ayrıca, aşağıdaki özelliklerin çalıştığını onaylamak için demo.wd.microsoft.com'de Uç nokta [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) için Microsoft Defender tanıtım web sitesini ziyaret edebilirsiniz:
>
> - Bulut teslimi koruma
> - Hızlı öğrenme (ilk görüşte engelle dahil)
> - İstenmeyen bir uygulama engellemesi olabilir

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>Microsoft Defender Virüsten Koruma kimlikleri

Microsoft Defender Virüsten Koruma kimliklerini, olay Windows kayıtlarına kaydedilir.

Olay günlüğünü doğrudan görüntüebilirsiniz veya üçüncü taraf bir güvenlik bilgileri ve olay yönetimi (SIEM) aracınız varsa, uç noktalarızdan belirli olayları ve hataları gözden geçirmek için [Microsoft Defender Virüsten Koruma](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) istemci olay kimliklerini de kullanabilirsiniz.

Bu bölümdeki tabloda, ana Microsoft Defender Virüsten Koruma kimlikleri ve mümkün olduğu durumda hatayı düzeltmek veya çözmek için önerilen çözümler verilmektedir.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Etkinlik Microsoft Defender Virüsten Koruma için

1. Olay **Görüntüleyicisi'ni açın**.
2. Konsol ağacında Uygulama ve Hizmet **Günlükleri'ne ve ardından Microsoft'a** genişletin, sonra **Windows'a** Windows Defender.
3. İşlem'i çift **tıklatın**.
4. Olaylarınızı bulmak için ayrıntılar bölmesinde tek tek olayların listesini görüntüleyin.
5. Alt bölmede, Genel ve Ayrıntılar sekmelerinin altında bir olayla ilgili belirli **ayrıntıları görmek için** **olayı** tıklatın.

<table>
<tr>
<th colspan="2" >Olay Kimliği: 1000</th>
</tr>
<tr>
<td>
Simgesel ad:
</td>
<td>
<b>MALWAREPROTECTION_SCAN_STARTED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımlardan koruma taraması başlatıldı. </b>
</td>
</tr>
<tr>
<td >
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kaynakları Tarama: &lt; Taranan kaynaklar (dosyalar/dizinler/BHO gibi).&gt;</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1001</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_COMPLETED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma taraması tamamlandı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Domainlt&gt;\&; KullanıcıScan&gt;</dt> 
<dt>Zamanı: &lt;Tarama süresi.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1002</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_CANCELLED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma taraması bitmeden önce durduruldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Domainlt&gt;&amp;; KullanıcıScan&gt;</dt> 
<dt>Zamanı: &lt;Tarama süresi.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1003</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_PAUSED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımlardan koruma taraması duraklatıldı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt;Domainlt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1004</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_RESUMED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımlardan koruma taraması devam ettirildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt;Domainlt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1005</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma taraması başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
<dl>
<dt>Tarama Kimliği: &lt; İlgili taramanın kimlik numarası.&gt;</dt>
<dt> Tarama Türü: &lt;Tarama türü&gt;, örneğin:<ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Örneğin, parametreleri&gt; tarama:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt> 
<dt>Hata Kodu: Tehdit &lt;durumuyla ilişkilendirilmiş&gt; hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Virüsten koruma istemcisi bir hatayla karşılaştı ve geçerli tarama durduruldu. bir istemci tarafı sorunu nedeniyle tarama başarısız olabilir. Bu olay kaydı tarama kimliğini, tarama türünü (Microsoft Defender Virüsten Koruma, kötü amaçlı yazılım önleme, kötü amaçlı yazılım önleme), tarama parametrelerini, taramayı başlatan kullanıcıyı, hata kodunu ve hatanın açıklamasını içerir.
Bu olayın sorunlarını gidermek için:
<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa <a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Destek sitesine</a> gidin ve hata kodunu <b>aramak için Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1006</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_DETECTED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı kötü amaçlı yazılım veya başka olası istenmeyen yazılım bulundu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1007</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, bilgisayarınızı kötü amaçlı yazılımdan veya diğer olası istenmeyen yazılımlardan korumaya yönelik bir eylem gerçekleştirmektedir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma makinenizi kötü amaçlı yazılımdan veya diğer olası istenmeyen yazılımlardan korumak için bir eylem yaptı. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Kullanıcı: &lt; Domainlt&gt;\&; KullanıcıAdı&gt;</dt>
<dt>: &lt;Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit KimliğiSeverlik&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt>
<dt> Eylem: &lt;Eylem&gt;, örneğin:<ul>
<li>Temizle: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/var olmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiğiniz eylemler listesinden tek bir kullanıcı tanımlı eylemdir</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütmesi engellendi</li>
</ul>
</dt>
<dt>Durum: &lt; StatusSignature&gt;</dt> 
<dt>Sürüm: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1008</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, sisteminizi kötü amaçlı yazılımdan veya diğer istenmeyen yazılımlardan korumaya yönelik bir eylem gerçekleştirmeyi çalıştı, ancak eylem başarısız oldu.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bir hatayla veya başka olası istenmeyen yazılımlarla ilgili bir eylemde bulundu. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Kullanıcı: &lt; Domainlt&gt;\&; KullanıcıAdı&gt;</dt>
<dt>: &lt;Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit KimliğiSeverlik&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluAction&gt;</dt>
<dt>: &lt;Eylem&gt;, örneğin:<ul>
<li>Temizle: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/var olmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiğiniz eylemler listesinden tek bir kullanıcı tanımlı eylemdir</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütmesi engellendi</li>
</ul>
</dt>
<dt>Hata Kodu: &lt; Hata kodu&gt; Tehdit durumuyla ilişkilendirilmiş sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hatanın&gt; hata açıklaması. </dt> 
<dt>Durum: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1009</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, bir öğeyi karantinadan geri yüklendi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma karantinadan geri yüklendi. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluKullanıcılar&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Sürüm: &lt;Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1010</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, öğeyi karantinadan geri yükleyemedi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma karantinadan geri yüklemeye çalışırken bir hatayla karşılaştı. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluKullanıcılar&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; Kullanıcı&gt;</dt> 
<dt>Hata Kodu: Tehdit &lt;durumuyla ilişkilendirilmiş&gt; hata kodu Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hatanın&gt; hata açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1011</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu karantinadan bir öğeyi sildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma öğe karantinadan silindi.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluKullanıcılar&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Sürüm: &lt;Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1012</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu karantinadan bir öğeyi silemez.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma karantinadan silene kadar bir hatayla karşılaştı.
Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluKullanıcılar&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; Kullanıcı&gt;</dt> 
<dt>Hata Kodu: Tehdit &lt;durumuyla ilişkilendirilmiş&gt; hata kodu Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hatanın&gt; hata açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1013</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, kötü amaçlı yazılım geçmişini ve diğer olası istenmeyen yazılımları sildi.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yazılımı ve diğer olası istenmeyen yazılımların geçmişini kaldırmıştır.
<dl>
<dt>Saat: Olayın olduğu zaman, örneğin geçmişin temizli olduğu zaman. Bu parametre tehdit olaylarında kullanılmaz, dolayısıyla bu parametrenin düzeltme zamanı veya bulaşma zamanı olup olmadığı konusunda karışıklık olmaz. Bunlar için, özel olarak bunları Eylem Zamanı veya Algılama Zamanı olarak çağırmamız gerekir.</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1014</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
Kötü amaçlı yazılımdan koruma platformu kötü amaçlı yazılım geçmişini ve diğer olası istenmeyen yazılımları silemez.
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, kötü amaçlı yazılım geçmişini ve diğer olası istenmeyen yazılımları kaldırmaya çalışırken bir hatayla karşılaştı.
<dl>
<dt>Saat: Olayın olduğu zaman, örneğin geçmişin temizli olduğu zaman. Bu parametre tehdit olaylarında kullanılmaz, dolayısıyla bu parametrenin düzeltme zamanı veya bulaşma zamanı olup olmadığı konusunda karışıklık olmaz. Bunlar için, özel olarak bunları Eylem Zamanı veya Algılama Zamanı olarak çağırmamız gerekir.</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt> 
<dt>Hata Kodu: Tehdit &lt;durumuyla ilişkilendirilmiş&gt; hata kodu Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hatanın&gt; hata açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1015</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_BEHAVIOR_DETECTED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu şüpheli davranış algıladı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma şüpheli davranış algıladı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:
<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>ID: Enumeration matching severity.</dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine fidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;File name&gt; of the file.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1116</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_DETECTED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu kötü amaçlı yazılım veya diğer olası istenmeyen yazılım algıladı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yazılım algıladı veya istenmeyen başka bir yazılım algıladı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:
<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma tehdite karşı düzenli bir işlemden askıya alabilir ve önlem alabilir. Tehdide el ile kaldırmak için, Microsoft Defender Virüsten Koruma <b>Temizle'ye tıklayın</b>.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1117</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, bilgisayarınızı kötü amaçlı yazılımdan veya diğer olası istenmeyen yazılımlardan korumaya yönelik bir eylem gerçekleştirmektedir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma makinenizi kötü amaçlı yazılımdan veya diğer olası istenmeyen yazılımlardan korumak için bir eylem yaptı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:
<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, örneğin:<ul>
<li>Temizle: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/var olmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiğiniz eylemler listesinden tek bir kullanıcı tanımlı eylemdir</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek eylemlerin açıklamasıError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine&gt;</dt> NOT: Microsoft Defender Virüsten Koruma her güncelleştirmede, Microsoft Security Essentials, Kötü Amaçlı Yazılımları Temizleme Aracı veya System Center Endpoint Protection  bir kötü amaçlı yazılım algılarsa, aşağıdaki sistem ayarlarını ve kötü amaçlı yazılımın değiştirmiş olabileceği hizmetleri geri yükleyebilir:<ul>
<li>Varsayılan Internet Explorer veya Microsoft Edge ayarı</li>
<li>Kullanıcı Erişimi Denetimi ayarları</li>
<li>Chrome ayarları</li>
<li>Önyükleme Denetimi Verileri</li>
<li>Regedit ve Görev Yöneticisi kayıt defteri ayarları</li>
<li>Windows Güncelleştirme, Arka Plan Akıllı Aktarım Hizmeti ve Uzaktan Yordam Çağrısı hizmeti</li>
<li>Windows Sistemi dosyalarını yükleme</li></ul>
Yukarıdaki bağlam aşağıdaki istemci ve sunucu sürümleri için geçerlidir:
<table>
<tr>
<th>İşletim sistemi</th>
<th>İşletim sistemi sürümü</th>
</tr>
<tr>
<td>
İstemci İşletim Sistemi
</td>
<td>
Windows Vista (Service Pack 1 veya Service Pack 2), Windows 7 ve sonrası
</td>
</tr>
<tr>
<td>
Sunucu İşletim Sistemi
</td>
<td>
Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 ve Windows Server 2016
</td>
</tr>
</table>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma kaldırmış veya karantinaya alınmış.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1118</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, sisteminizi kötü amaçlı yazılımdan veya diğer istenmeyen yazılımlardan korumaya yönelik bir eylem gerçekleştirmeyi çalıştı, ancak eylem başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım veya diğer olası istenmeyen yazılımlara yönelik bir işlem sırasında kritik olmayan bir hatayla karşılaştı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:
<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, örneğin:<ul>
<li>Temizle: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/var olmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiğiniz eylemler listesinden tek bir kullanıcı tanımlı eylemdir</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek eylemlerin açıklamasıError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma amaçlı yazılım düzeltmesi ile ilgili bir görevi tamamlanamadı. Bu kritik bir hata değildir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1119</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_CRITICALLY_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu, kötü amaçlı yazılım veya başka olası istenmeyen yazılımlar üzerinde eylem yapmaya çalışırken kritik bir hatayla karşılaştı. Olay iletisinde daha fazla ayrıntı var.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bir kötü amaçlı yazılım veya başka olası istenmeyen yazılımlar üzerinde işlem sırasında kritik bir hatayla karşılaştı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Ad: &lt; Tehdit adıKimliği&gt;</dt>
<dt>: &lt;Tehdit Azlığı&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Ciddi</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin her tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yol: &lt; Dosya yoluYönteme&gt;</dt>
<dt> Kaynağı: &lt;Algılama kaynağı&gt;, örneğin:
<ul>
<li>Unknown</li>
<li>Yerel bilgisayar</li>
<li>Ağ paylaşımı</li>
<li>İnternet</li>
<li>Gelen trafik</li>
<li>Giden trafik</li>
</ul>
</dt>
<dt>Algılama Türü: &lt;Algılama türü&gt;, örneğin:<ul>
<li>Heuristics</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: Sistem başlatıldı</li>
<li>Gerçek zamanlı: başlatılan gerçek zamanlı bileşen</li>
<li>IOAV: IE İndirmeleri ve Outlook Başlatması</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Buna, önyükleme sırası tarafından algılanan kötü amaçlı yazılım da dahildir</li>
<li>Uzaktan attestation</li>
</ul>Kötü amaçlı yazılımdan koruma Tarama Arabirimi (AMSI). Betikleri (PowerShell, VBS) korumak için kullanılan betikler, üçüncü taraflarca da çağrılsa da kullanılır.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, örneğin:<ul>
<li>Temizle: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/var olmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiğiniz eylemler listesinden tek bir kullanıcı tanımlı eylemdir</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek eylemlerin açıklamasıError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İstemci Microsoft Defender Virüsten Koruma kritik sorunlar nedeniyle bu hatayla karşılaştı. Uç nokta korumalı değil. Hata açıklamasını gözden geçirin ve aşağıdaki ilgili <b>Kullanıcı eylemi adımlarını</b> izleyin.
<table>
<tr>
<th>Eylem</th>
<th>Kullanıcı eylemi</th>
</tr>
<tr>
<td>
<b>Kaldır</b>
</td>
<td>
Tanımları güncelleştirin ve kaldırmanın başarılı olduğunu doğrulayın.
</td>
</tr>
<tr>
<td>
<b>Temizle</b>
</td>
<td>
Tanımları güncelleştirin ve düzeltmenin başarılı olduğunu doğrulayın.
</td>
</tr>
<tr>
<td>
<b>Karantina</b>
</td>
<td>
Tanımları güncelleştirin ve kullanıcının gerekli kaynaklara erişme izni olduğunu doğrulayın.
</td>
</tr>
<tr>
<td>
<b>İzin Ver</b>
</td>
<td>
Kullanıcının gerekli kaynaklara erişme izni olduğunu doğrulayın.
</td>
</tr>
</table>

Bu olay devam ederse:<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa <a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Destek sitesine</a> gidin ve hata kodunu <b>aramak için Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1120</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_THREAT_HASH</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Microsoft Defender Virüsten Koruma kaynağı için karmaları ertelemiş olabilir.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma iyi durumdadır ve çalışıyor durumdadır.
<dl>
<dt>Geçerli Platform Sürümü: &lt; Geçerli platform sürümüTüm&gt;</dt> 
<dt>Kaynak Yolu: &lt;PathHashes&gt;</dt>
<dt>: &lt;Karmalar&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Not: Bu olay yalnızca şu ilke ayarlanırsa günlüğe kaydedilir: <b>ThreatFileHashLogging unsigned</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1127</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_FOLDER_GUARD_SECTOR_BLOCK</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Denetimli Klasör Erişimi(CFA), güvenilmeyen bir sürecin bellekte değişiklik yapmasını engelledi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Denetimli Klasör Erişimi güvenilmeyen bir sürecin disk sabitini değiştirmesini engellemiş.
<br/> Olay kaydı hakkında daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>EtkinlikKimlik: &lt; &gt;Örneğin OlayKimlik: 1127Version</dt>
<dt>: &lt;&gt;Sürüm, örneğin:</dt> 
<dt>0Level: &lt;Level&gt;, örneğin: win:</dt>
<dt>WarningTimeCreated: &lt;SystemTime&gt;,</dt> olayın oluşturulma 
<dt>zamanıEventRecordID: &lt;EventRecordID&gt;, olay günlüğüExecution</dt> ProcessID' içinde olayın dizin numarası
<dt>: &lt;Execution ProcessID&gt;, eventChannel</dt>: Olay 
<dt>&gt;kanalını oluşturan işlem; &lt;örneğin: Microsoft- Windows-Windows Defender/</dt>
<dt>OperationalCompcomp: &lt;Computer nameSecurity&gt;</dt> 
<dt>UserID: &lt;Security UserIDProduct&gt;</dt> 
<dt>Name: &lt;Product&gt; Name, örneğin: Microsoft Defender Virüsten Koruma</dt> 
<dt>Product Version: &lt;Product Version&gt;</dt>
<dt> Algılama Zamanı: &lt;Algılama Zamanı&gt;, CFA güvenilmeyen bir işlemi</dt> engellemiş 
<dt>olduğu saatKullanıcılar: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;&gt;</dt> Cihaz adı, güvenilmeyen bir işlemden değişiklik için erişilen cihazın veya diskin adı 
<dt>Süreç Adı: &lt;&gt;Süreç yolu, CFA'nın</dt> değişiklik için cihaza veya diske erişimini engellemiş süreç yolu 
<dt>adıSecurity Intelligence Sürüm: &lt;Güvenlik&gt;</dt> zekası 
<dt>sürümüEngine Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Kullanıcı Powershell veya Veri Merkezi'nde CFA <i></i> için İzin Verilen İşlemler listesine engellenen işlemi Windows Güvenliği ekleyebilir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1150</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTHY</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformuz durumu bir izleme platformuna raporlarsa, bu olay kötü amaçlı yazılımdan koruma platformunun çalışıyor olduğunu ve iyi durumda olduğunu gösterir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma iyi durumdadır ve çalışıyor durumdadır.
<dl>
<dt>Platform Sürümü: &lt; Geçerli platform sürümüSignature&gt;</dt> 
<dt>Sürüm: &lt;Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma durumu iyi durumdadır. Bu olay saatte bir rapor edilir.
</td>
</tr>

<tr>
<th colspan="2">Olay Kimliği: 1151</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTH_REPORT</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Endpoint Protection durumu raporu (UTC'de saat)</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Virüsten koruma istemcisinin durum raporu.
<dl>
<dt>Platform Sürümü: &lt; Geçerli platform&gt;</dt> 
<dt>sürümüEngine Sürüm: &lt;Antimalware Engine&gt;</dt> 
<dt>Sesli Gerçek Zamanlı İnceleme altyapısı sürümü: &lt;Network Realtime Inspection engine&gt;</dt> 
<dt>sürümAntivirus imza sürümü: &lt;Virüsten&gt;</dt> koruma imza 
<dt>sürümüAntiware imza sürümü: &lt;Antiware imza sürümüNetwork&gt;</dt> 
<dt>Realtime Inspection imza sürümü: &lt; Ağ Gerçek&gt;</dt> Zamanlı İnceleme imza 
<dt>sürümüRTP durumu: &lt;Gerçek&gt;</dt> Zamanlı koruma durumu (Etkin veya Devre Dışı)
<dt>OA durumu: &lt;Erişim&gt; durumu (</dt>Etkin veya Devre Dışı)
<dt>IOAV durumu: &lt;IE İndirmeleri ve Outlook Express Ekler&gt; durumu (Etkin</dt> veya Devre Dışı)
<dt>BM durumu: &lt;Davranış İzleme&gt; durumu (Etkin</dt> veya Devre Dışı)Virüsten koruma imza yaşı
<dt>: &lt;Virüsten koruma imzası yaşı&gt;  (gün içinde)</dt> 
<dt>Casus yazılım imza yaşı: &lt; Casus yazılım imza&gt; yaşı (</dt>gün içinde)Son hızlı tarama yaşı
<dt>: &lt;Son&gt;</dt> hızlı tarama yaşı (gün içinde)Son tam tarama yaşı
<dt>: &lt;Son&gt;</dt> tam tarama yaşı (gün içinde)
<dt>Virüsten koruma imzası oluşturma süresi: ?&lt; Virüsten koruma imza oluşturma zamanıAntiware&gt;</dt> 
<dt>imza oluşturma zamanı: ?&lt; Casus yazılımdan koruma imza oluşturma zamanıEn&gt;</dt> 
<dt>son hızlı tarama başlangıç zamanı: ?&lt; Son hızlı tarama başlangıç zamanıEn&gt;</dt> 
<dt>son hızlı tarama bitiş saati: ?&lt; Son hızlı&gt;</dt> tarama bitiş saati Son hızlı tarama kaynağı: 
<dt>&lt;&gt; Son hızlı tarama kaynağı (0 = tarama çalışmadı, 1 = kullanıcı tarafından başlatıldı, 2 = sistem başlatıldı)</dt>
<dt>Son tam tarama başlangıç zamanı: ?&lt; Son tam tarama başlangıç zamanıEn&gt;</dt> 
<dt>son tam tarama bitiş saati: ?&lt; Son tam tarama&gt;</dt> bitiş saati Son tam tarama kaynağı: 
<dt>&lt;&gt; Son tam tarama kaynağı (0 = tarama çalışmadı, 1 = kullanıcı tarafından başlatıldı, 2 = sistem başlatıldı)</dt>
<dt>Ürün durumu: İç sorun giderme için
</dl>
</td>
</tr>

<tr>
<th colspan="2">Olay Kimliği: 2000</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma tanımları başarıyla güncelleştirildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Virüsten koruma imza sürümü güncelleştirildi.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüÖnel&gt;</dt> 
<dt>İmza Sürümü: &lt;Önceki imza sürümüSignature&gt;</dt>
<dt> Type: &lt;Signature type&gt;, örneğin: <ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Güncelleştirme Türü: &lt; Güncelleştirme türü:&gt; Tam veya Delta.</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Sürümü: &lt;Geçerli altyapı sürümüPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma durumu iyi durumdadır. İmzalar başarıyla güncelleştirildiğinde bu olay bildiriliyor.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2001</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Güvenlik zekası güncelleştirmesi başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, imzaları güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Yeni güvenlik zekası sürümü: &lt; Yeni sürüm numarasıPrevious&gt;</dt> 
<dt>security intelligence version: &lt;Previous versionUpdate&gt;</dt>
<dt> Source: &lt;Update source&gt;, örneğin:
<ul>
<li>Güvenlik zekası güncelleştirme klasörü</li>
<li>İç güvenlik zekası güncelleştirme sunucusu</li>
<li>Microsoft Update Server</li>
<li>Dosya paylaşımı</li>
<li>Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi (MMPC)</li>
</ul>
</dt>
<dt>Güncelleştirme Aşaması: &lt;Güncelleştirme aşaması&gt;, örneğin:
<ul>
<li>Arama</li>
<li>İndir</li>
<li>Yükle</li>
</ul>
</dt>
<dt>Kaynak Yolu: Evrensel Adlandırma Kuralı (UNC), Windows Server Update Services (WSUS)/Microsoft Update/ADL için dosya paylaşımı adı.</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Güncelleştirme Türü: &lt; Güncelleştirme türü:&gt; Tam veya Delta.</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Sürümü: &lt;Geçerli altyapı sürümüPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine versionError&gt;</dt> 
<dt>Code: &lt;&gt; Error code Result code associated with threat status. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Bu hata, tanımları güncelleştirmeyle ilgili bir sorun olduğunda oluşur.
Bu olayın sorunlarını gidermek için:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Tanımları güncelleştirin</a> ve doğrudan uç nokta üzerinde yeniden yer almaktadır.</li>
<li>Bu hata hakkında daha fazla bilgi için %Windir%\WindowsUpdate.log dosyasındaki girdileri gözden geçirebilirsiniz.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2002</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı başarıyla güncelleştirildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma sürümü güncelleştirildi.
<dl>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüÖnceci&gt;</dt> 
<dt>Altyapı Sürümü: &lt;Önceki altyapı sürümüEngine&gt;</dt> 
<dt>Türü: &lt;Altyapısı&gt; türü,</dt> kötü amaçlı yazılımdan koruma altyapısı veya Ağ İnceleme Sistemi altyapısı. 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma durumu iyi durumdadır. Kötü amaçlı yazılımdan koruma altyapısının başarıyla güncelleştirildiğinde bu olay bildiriliyor.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2003</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı güncelleştirmesi başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, altyapısını güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Yeni Altyapı Sürümü:</dt>
<dt>Önceki Altyapı Sürümü: &lt;Önceki altyapı sürümüEngine&gt;</dt> 
<dt>Türü: &lt;Altyapısı&gt; türü, kötü amaçlı yazılımdan koruma altyapısı veya Ağ İnceleme Sistemi altyapısı.</dt> 
<dt>Kullanıcı: &lt; Domainlt&gt;\&; Kullanıcı&gt;</dt> 
<dt>Hata Kodu: Tehdit &lt;durumuyla ilişkilendirilmiş&gt; hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
en Microsoft Defender Virüsten Koruma güncelleştirmesi başarısız oldu. Bu olay, istemcinin kendisini güncelleştiremezse gerçekleşir. Bu olay genellikle güncelleştirme sırasında ağ bağlantısının kesintiye neden olmasıdır.
Bu olayın sorunlarını gidermek için:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Tanımları güncelleştirin</a> ve doğrudan uç nokta üzerinde yeniden yer almaktadır.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2004</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_REVERSION</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma tanımları yüklenirken bir sorun oldu. Kötü amaçlı yazılımdan koruma altyapısı, bilinen son iyi tanım kümelerini yüklemeye çalışacak.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma imzaları yüklemeye çalışırken bir hatayla karşılaştı ve bilinen bir dizi imzaya geri dönme girişiminde bulundu.
<dl>
<dt>İmzalar Denendi:</dt>
<dt>Hata Kodu: &lt;Tehdit durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüEngine&gt;</dt> 
<dt>Sürüm: &lt;Kötü amaçlı yazılımdan koruma altyapısı sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
En Microsoft Defender Virüsten Koruma istemci en son tanım dosyasını indirip uygulamayı indirmeyi ve yükleyemedi. bu hata, istemci tanımları yüklemeye çalışırken bir hatayla karşılaştığında veya dosya bozuk olduğunda oluşabilir. Microsoft Defender Virüsten Koruma, bilinen, iyi bilinen bir dizi tanıma geri dönme girişiminde  çalışırken bu işlemi geri amayacaktır.
Bu olayın sorunlarını gidermek için:
<ol>
<li>Bilgisayarı yeniden başlatın ve yeniden deneyin.</li>
<li>En son tanımları siteden <a href="https://aka.ms/wdsi">Microsoft Güvenlik Zekası indirin</a>.
Not: Siteden indirilen tanımlar dosyasının boyutu 60 MB'yi aşıyor olabilir ve tanımları güncelleştirmek için uzun vadeli bir çözüm olarak kullanılmamaları gerekir.
</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2005</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_PLATFORMOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformu eski olduğundan, kötü amaçlı yazılımdan koruma altyapısı yüklenemedi. Kötü amaçlı yazılımdan koruma platformu, bilinen son iyi kötü amaçlı yazılımdan koruma altyapısını yüker ve güncelleştirmeyi dener.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma platform sürümü destekçinmemektedir, çünkü kötü amaçlı yazılımdan koruma altyapısı yüklenemedi. Microsoft Defender Virüsten Koruma iyi bilinen son motora geri dönecektir ve bir platform güncelleştirmesi denenir.
<dl>
<dt>Geçerli Platform Sürümü: &lt;Geçerli platform sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2006</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Platform güncelleştirmesi başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, platformu güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Geçerli Platform Sürümü: &lt; Geçerli platform sürümüError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2007</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_ALMOSTOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Platform yakında güncel olmayacaktır. Güncel korumayı korumak için en son platformu indirin.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılımdan koruma altyapısının gelecek sürümlerini desteklemek için kısa süre içinde daha yeni bir platform sürümü gerekir. Kullanılabilen en iyi Microsoft Defender Virüsten Koruma korumak için en yeni platform platformunu indirin.
<dl>
<dt>Geçerli Platform Sürümü: &lt;Geçerli platform sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2010</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı, ek tanım almak için Dinamik İmza Hizmeti'i kullandı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma <i>korunmasına yardımcı olmak için ek</i> imzaları almak için Dinamik İmza Hizmeti'ne tıklayın.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüSignature&gt;</dt>
<dt> Type: &lt;Signature type&gt;, örneğin: <ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüDynamic&gt;</dt>
<dt> Signature Type: &lt;Dinamik imza türü&gt;, örneğin:
<ul>
<li>Sürüm</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
<li>Süre</li>
</ul>
</dt>
<dt>Persistence Path: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit&gt; type, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Persistence Limit: Persistence limit of the fastpath signature.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2011</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Dinamik İmza Hizmeti, güncel olmayan dinamik tanımları sildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma <i>imzaları atmak için Dinamik</i> İmza Hizmeti'ne kullandınız.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüSignature&gt;</dt>
<dt> Type: &lt;Signature type&gt;, örneğin: <ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüDynamic&gt;</dt>
<dt> Signature Type: &lt;Dinamik imza türü&gt;, örneğin:
<ul>
<li>Sürüm</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
<li>Süre</li>
</ul>
</dt>
<dt>Persistence Path: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistence limit&gt; type, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Persistence Limit: Persistence limit of the fastpath signature.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Herhangi bir işlem gerekmez. Microsoft Defender Virüsten Koruma durumu iyi durumdadır. Bu olay, Dinamik İmza Hizmeti'nin güncel olmayan dinamik tanımları başarıyla siğili olduğu bildiriliyor.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2012</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı, Dinamik İmza Hizmeti'nin kullanımına çalışırken bir hatayla karşılaştı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, Dinamik İmza Hizmeti'nin kullanımına çalışırken <i>bir hatayla karşılaştı</i>.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüSignature&gt;</dt>
<dt> Type: &lt;Signature type&gt;, örneğin: <ul>
<li>Virüsten koruma</li>
<li>Antiware</li>
<li>Kötü amaçlı yazılımdan koruma</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş Hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
<dt> Dinamik İmza Türü: &lt;Dinamik imza türü&gt;, örneğin:
<ul>
<li>Sürüm</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
<li>Süre</li>
</ul>
</dt>
<dt>Persistence Path: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit&gt; type, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Persistence Limit: Persistence limit of the fastpath signature.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İnternet bağlantısı ayarlarınızı denetleyin.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2013</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED_ALL </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Dinamik İmza Hizmeti tüm dinamik tanımları sildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma Dinamik İmza Hizmeti <i>imzaları atılır</i>.
<dl>
<dt>Geçerli İmza Sürümü: &lt;Geçerli imza sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2020</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOADED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı temiz bir dosya indirdi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bir dosya indirdim.
<dl>
<dt>Dosya adı: &lt; Dosya adı&gt; Dosyanın adı.</dt> 
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümü&gt;</dt> 
<dt>Geçerli Altyapı Sürümü: &lt;Geçerli altyapı sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2021</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOAD_FAILED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı temiz bir dosyayı indiremedi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma dosya indirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Dosya adı: &lt; Dosya adı&gt; Dosyanın adı.</dt> 
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümü&gt;</dt> 
<dt>Geçerli Altyapı Sürümü: Geçerli &lt;altyapı sürümüError&gt;</dt> 
<dt>Kodu: Tehdit &lt;durumuyla&gt; ilişkilendirilmiş hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İnternet bağlantısı ayarlarınızı denetleyin.
Kullanıcı Microsoft Defender Virüsten Koruma, Dinamik İmza Hizmeti'nin belirli bir tehditle karşı karşıya olduğu en son tanımları indirirken bir hatayla karşılaştı. Bu hataya büyük olasılıkla bir ağ bağlantısı sorunu neden olur.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2030</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALLED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı indirildi ve bir sonraki sistem yeniden başlatma işlemiyle çevrimdışı olarak çalıştırılacak şekilde yapılandırıldı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma virüsten koruma yazılımını bir sonraki yeniden başlatmada çalıştırılacak şekilde indirdi ve yapılandırdı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2031</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALL_FAILED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı çevrimdışı taramayı indiremiyor ve yapılandıramıyor.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, çevrimdışı virüsten koruma yazılımını indirmeye ve yapılandırmaya çalışırken bir hatayla karşılaştı.
<dl>
<dt>Hata Kodu: &lt; Hata kodu&gt; Tehdit durumuyla ilişkilendirilmiş sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2040</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_OS_EXPIRING </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Bu işletim sistemi sürümü için kötü amaçlı yazılımdan koruma desteği yakında sona eçir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sistemi desteği kısa süre içinde sona erecek. Destek Microsoft Defender Virüsten Koruma dışında bir işletim sisteminde çalıştırarak tehditlere karşı korunmak için yeterli bir çözüm sağlanmaz.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2041</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_OS_EOL </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Bu işletim sistemi için kötü amaçlı yazılımdan koruma desteği sona erdi. Destek devam etmek için işletim sistemini yükseltmeniz gerekir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sistemi desteğinizin süresi doldu. Destek Microsoft Defender Virüsten Koruma dışında bir işletim sisteminde çalıştırarak tehditlere karşı korunmak için yeterli bir çözüm sağlanmaz.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2042</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_PROTECTION_EOL </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı artık bu işletim sistemini desteklemez ve artık sisteminizi kötü amaçlı yazılımdan korumaz. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sistemi desteğinizin süresi doldu. Microsoft Defender Virüsten Koruma artık işletim sisteminiz üzerinde desteklenmiyor, çalışmayı durdurdu ve kötü amaçlı yazılım tehditlerine karşı korunmaz.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 3002</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_FAILURE </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Gerçek zamanlı koruma bir hatayla karşılaştı ve başarısız oldu.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma Real-Time Koruması özelliği bir hatayla karşılaştı ve başarısız oldu.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'de</li>
<li>Internet Explorer indirmeleri ve Microsoft Outlook Express ekleri</li>
<li>Davranış izleme</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Hata Kodu: &lt; Hata kodu&gt; Tehdit durumuyla ilişkilendirilmiş sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>Neden: Gerçek Microsoft Defender Virüsten Koruma koruma özelliğini yeniden başlatma nedeni.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Sistemi yeniden başlatmalı ve tam tarama çalıştırabilirsiniz, çünkü sistem bir süre korunmazdı.
Bu Microsoft Defender Virüsten Koruma istemcinin gerçek zamanlı koruma özelliği, hizmetlerden biri başlatılamadı diye bir hatayla karşılaştı.
Bunun ardından 3007 olay kimliği gelirse, hata geçicidir ve kötü amaçlı yazılımdan koruma istemcisi bu hatadan kurtarıldı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 3007</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_RECOVERED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Bir hatadan kurtarılan gerçek zamanlı koruma. Bu hatayı gördüğünüzde tam sistem taraması çalıştırmayı öneririz. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma Zamanlı Koruma özelliği yeniden başlattı. Bu aracı çalışırken gözden kaçırmış olduğunu algılamak için tam sistem taraması çalıştırmanız önerilir.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'de</li>
<li>IE, Express Outlook indirir ve indirir</li>
<li>Davranış izleme</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Neden: Gerçek Microsoft Defender Virüsten Koruma koruma özelliğini yeniden başlatma nedeni.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Gerçek zamanlı koruma özelliği yeniden başlatıldı. Bu olay tekrar yaşanıyorsa <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek ile iletişime geçin</a>.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5000</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_RTP_ENABLED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Gerçek zamanlı koruma etkinleştirilir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım ve diğer olası istenmeyen yazılımlar için gerçek zamanlı koruma taraması etkinleştirildi.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5001</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_RTP_DISABLED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Gerçek zamanlı koruma devre dışı bırakılır. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım için gerçek zamanlı koruma taraması ve diğer olası istenmeyen yazılımlar devre dışı bırakıldı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5004</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_CONFIGURED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Gerçek zamanlı koruma yapılandırması değişti. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma koruma özelliği yapılandırması değişti.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'de</li>
<li>IE, Express Outlook indirir ve indirir</li>
<li>Davranış izleme</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Yapılandırma: </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5007</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_CONFIG_CHANGED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platform yapılandırması değişti.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yapılandırma değişti. Bu beklenmeyen bir olaysa, ayarları gözden geçirebilirsiniz çünkü bu kötü amaçlı yazılımdan neden olabilir.
<dl>
<dt>Eski değer: &lt; Eski değer numarası Eski&gt; virüsten koruma yapılandırma değeri.</dt> 
<dt>Yeni değer: &lt; Yeni değer numarası&gt; Yeni virüsten koruma yapılandırma değeri.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5008</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_FAILURE</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma altyapısı bir hatayla karşılaştı ve başarısız oldu.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma beklenmeyen bir hatadan dolayı sonlandırıldı.
<dl>
<dt>Hata Türü: &lt; Hata türü&gt;, örneğin: Kilitlenme veya</dt> 
<dt>HangException Kodu: Hata &lt;koduKaynağı&gt;</dt>
<dt>: &lt;Kaynak&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Bu olayın sorunlarını gidermek için:<ol>
<li>Hizmeti yeniden başlatmayı deneyin.<ul>
<li>Kötü amaçlı yazılımdan koruma, virüsten koruma ve casus yazılım için, yükseltilmiş bir komut istemine <b>net stop msmpsvc</b> yazın ve ardından kötü amaçlı yazılımdan koruma altyapısını yeniden başlatmak için <b>net start msmpsvc</b> yazın.</li>
<li>Ağ İnceleme Sistemi <i>için</i>, yükseltilmiş komut istemine <b>net start nissrv yazın</b> ve ardından NiSSRV.exe dosyasını kullanarak Ağ İnceleme Sistemi altyapısını yeniden başlatmak için <b>net start nissrv</b> yazın.<i></i>
</li>
</ul>
</li>
<li>Aynı şekilde başarısız olursa, <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> Destek Sitesine erişerek ve Arama kutusuna hata numarasını girerek hata kodunu arayabilir ve Microsoft Teknik <b></b> <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Destek'e başvurun</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İstemci Microsoft Defender Virüsten Koruma beklenmeyen bir hatadan dolayı durduruldu.
Bu olayın sorunlarını gidermek için:
<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa <a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Destek sitesine</a> gidin ve hata kodunu <b>aramak için Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5009</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_ENABLED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılım için tarama ve diğer istenmeyen yazılımlar etkindir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma amaçlı yazılım için tarama ve diğer olası istenmeyen yazılımlar etkinleştirildi.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5010</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_DISABLED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılım tarama ve diğer istenmeyen yazılımlar devre dışı bırakılır.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma amaçlı yazılım tarama ve istenmeyen başka yazılımlar devre dışı bırakılır.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5011</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_ENABLED</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Virüs tarama etkinleştirilmiştir.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma tarama özelliği etkinleştirilmiştir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5012</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_DISABLED </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Virüs tarama devre dışı bırakılır. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma tarama devre dışı bırakılır.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5013</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>
</b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Tamper protection blocked a change to Microsoft Defender Virüsten Koruma.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Bu durumda, Müdahale koruması etkinleştirilirse, Defender'ın ayarlarından herhangi birini engellemeye çalışır ve Hangi ayar değişikliğinin engellenmiş olduğunu belirtirse Olay Kimliği 5013 oluşturulur.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5100</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_EXPIRATION_WARNING_STATE </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformunun süresi yakında dolmaz. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yetkisiz kullanım süresi girmiştir ve yakında süresi dolacak. Son kullanma tarihinden sonra, bu program virüslere, casus yazılımlara ve diğer olası istenmeyen yazılımlara karşı korumayı devre dışı bırakacak.
<dl>
<dt>Son Kullanma Nedeni: Süre Microsoft Defender Virüsten Koruma süresi dolmaz.</dt> 
<dt>Son Kullanma Tarihi: Microsoft Defender Virüsten Koruma tarihi.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5101</th>
</tr>
<tr><td>
Simgesel ad:
</td>
<td >
<b>MALWAREPROTECTION_DISABLED_EXPIRED_STATE </b>
</td>
</tr>
<tr>
<td>
İleti:
</td>
<td >
<b>Kötü amaçlı yazılımdan koruma platformunun süresi doldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma süresi doldu. Virüslere, casus yazılımlara ve diğer olası istenmeyen yazılımlara karşı koruma devre dışı bırakılır.
<dl>
<dt>Sona Erme Nedeni:</dt>
<dt>Sona Erme Tarihi: </dt>
<dt>Hata Kodu: &lt;Tehdit&gt; durumuyla ilişkilendirilmiş hata kodu Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Microsoft Defender Virüsten Koruma hata kodlarını Microsoft Defender Virüsten Koruma Bu deneyimle ilgili bir sorun yaşanıyorsa genellikle sorunu gidermenize yardımcı olacak bir hata kodu ve olacaktır. Çoğunlukla hata, güncelleştirme yüklemede bir sorun olduğu anlamına gelir.
Bu bölümde, bu hataları gidermeyle ilgili Microsoft Defender Virüsten Koruma bilgiler yer almaktadır.
- Hata kodu - Şimdi ne yapmak gerekir? hata - Öneri için olası neden

Bu tablolarda yer alan bilgileri, hata kodlarıyla ilgili Microsoft Defender Virüsten Koruma kullanın.


<table>
<tr>
<th colspan="2">Hata kodu: 0x80508007</th>
</tr>
<tr>
<td>İleti</td>
<td>
<b>ERR_MP_NO_MEMORY </b>
</td>
</tr>
<tr>
<td>
Olası neden
</td>
<td>
Bu hata bellek yetersiz olabileceğini gösterir.
</td>
</tr>
<tr>
<td>Çözüm</td>
<td>
<ol>
<li>Cihazınızın kullanılabilir belleğini kontrol edin.</li>
<li>Cihazınızın belleğini kapatmak için çalışan kullanılmayan tüm uygulamaları kapatın.</li>
<li>Cihazı yeniden başlatın ve taramayı yeniden çalıştırın.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x8050800C</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_BAD_INPUT_DATA</b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, güvenlik ürününüzle ilgili bir sorun olabileceğini gösterir.
</td>
</tr><tr><td>Çözüm</td><td>
<ol>
<li>Tanımları güncelleştirin. Ya:<ol>
<li>Güncelleştirme <b>sekmesindeki Tanımları</b> güncelleştir <b>düğmesine Microsoft Defender Virüsten Koruma</b>. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Veya
</li>
<li>En son tanımları siteden <a href="https://aka.ms/wdsi">Microsoft Güvenlik Zekası indirin</a>.
Not: Siteden indirilen tanımlar dosyasının boyutu 60 MB'yi aşıyor olabilir ve tanımları güncelleştirmek için uzun vadeli bir çözüm olarak kullanılmamaları gerekir.
</li>
</ol>
</li>
<li>Tam taramayı çalıştırın.
</li>
<li>Cihazı yeniden başlatın ve yeniden deneyin.</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508020</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_BAD_CONFIGURATION </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, bir altyapı yapılandırma hatası olabileceğini belirtir; genellikle bu durum, motorun düzgün çalışmasına izin vermeyebilir girdi verileriyle ilgilidir.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x805080211
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, bir Microsoft Defender Virüsten Koruma karantinaya alınama olduğunu gösterir.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508022
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdit kaldırma işleminin tamamlanması için yeniden başlatmanın gerekli olduğunu gösterir.
</td>
</tr>
<tr>
<th colspan="2">
0x80508023
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_THREAT_NOT_FOUND </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdit artık medyada olmadığını veya kötü amaçlı yazılımın cihazınızı taramanızı durdurmanızı durdur olabileceğini gösterir.
</tr><tr><td>Çözüm
</td>
<td>
Bu <a href="https://www.microsoft.com/security/scanner/default.aspx">Microsoft Güvenlik Tarayıcısı sonra</a> güvenlik yazılımınızı güncelleştirin ve yeniden deneyin.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508024 </th></tr>
<tr>
<td>İleti</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tam sistem taramasının gerekli olabileceğini gösterir.
</td></tr>
<tr>
<td>Çözüm</td><td>
Tam sistem taraması çalıştırın.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508025
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_MANUAL_STEPS_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdit kaldırma işleminin tamamlanması için el ile gerekli adımların gerekli olduğunu gösterir.
</td></tr><tr><td>Çözüm</td><td>
Microsoft Kötü Amaçlı Yazılımdan Koruma Anılanı'nde belirtilen <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">el ile düzeltme adımlarını izleyin</a>. Tehdite özgü bağlantıyı olay geçmişinde bulabilirsiniz.<br/></td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508026
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, kapsayıcı türü içindeki kaldırmanın destekleneney olduğunu gösterir.
</td></tr><tr><td>Çözüm</td><td>
Microsoft Defender Virüsten Koruma arşiv içinde algılanan tehditleri düzeltmek mümkün değildir. Algılanan kaynakları el ile kaldırmayı göz önünde bulundurabilirsiniz.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508027
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, düşük ve orta tehdit kaldırmanın devre dışı bırak olabileceğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Algılanan tehditleri denetleme ve bunları gereken şekilde çözme.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508029
</th>
</tr><tr><td>İleti</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdit için yeniden uyarının gerekli olduğunu gösterir.
</td></tr><tr><td>Çözüm</td><td>
Tam sistem taraması çalıştırın.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508030
</th>
</tr><tr><td>İleti</td>
<td><b>ERROR_MP_CALLISTO_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, çevrimdışı taramanın gerekli olduğunu gösterir.
</td></tr><tr><td>Çözüm</td><td>
Çevrimdışı çevrimdışı Microsoft Defender Virüsten Koruma. Bunun nasıl yapldır olduğuyla ilgili makaleyi Microsoft Defender Virüsten Koruma <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">okuyabilirsiniz</a>.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508031
</th>
</tr><tr><td>İleti</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, Microsoft Defender Virüsten Koruma platformunun geçerli sürümünü destekleme olmadığını ve yeni bir platform sürümü gerektirdiğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Microsoft Defender Virüsten Koruma 11'de Windows 10 ve Windows kullanabilirsiniz. Daha Windows 8, Windows 7 ve Windows Vista'da yeni sürümler <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">System Center Endpoint Protection</a>.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Aşağıdaki hata kodları hata kodlarının dahili olarak test Microsoft Defender Virüsten Koruma.

Bu hataları görüyorsanız, tanımları güncelleştirmeyi [deneyebilir](manage-updates-baselines-microsoft-defender-antivirus.md) ve doğrudan uç nokta üzerinde yeniden can olmaya zorlarsiniz.


<table>
<tr>
<th colspan="3">İç hata kodları</th>
</tr>
<tr>
<th><b>Hata kodu</b></th>
<th>İleti görüntüleniyor</th>
<th>Hata ve çözüm için olası neden</th>
</tr>
<tr>
<td>
0x80501004
</td>
<td>
<b>ERROR_MP_NO_INTERNET_CONN </b>
</td>
<td>
İnternet bağlantınızı kontrol edin ve taramayı yeniden çalıştırın.
</td>
</tr>
<tr>
<td>
0x80501000
</td>
<td>
<b>ERROR_MP_UI_CONSOLIDATION_BAS</b> E
</td>
<td rowspan="34">
Bu bir iç hatadır. Nedeni net bir şekilde tanımlanmamıştır.
</td>
<td rowspan="36">

</td>
</tr>
<tr>
<td>
0x80501001
</td>
<td>
<b>ERROR_MP_ACTIONS_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80501002
</td>
<td>
<b>ERROR_MP_NOENGINE</b>
</td>
</tr>
<tr>
<td>
0x80501003
</td>
<td>
<b>ERROR_MP_ACTIVE_THREATS</b>
</td>
</tr>
<tr>
<td>
0x805011011
</td>
<td>
<b>MP_ERROR_CODE_LUA_CANCELLED </b>
</td>
</tr>
<tr>
<td>
0x80501101
</td>
<td>
<b>ERROR_LUA_CANCELLATION </b>
</td>
</tr>
<tr>
<td>
0x80501102
</td>
<td>
<b>MP_ERROR_CODE_ALREADY_SHUTDOWN</b>
</td>
</tr>
<tr>
<td>
0x80501103
</td>
<td>
<b>MP_ERROR_CODE_RDEVICE_S_ASYNC_CALL_PENDING </b>
</td>
</tr>
<tr>
<td>
0x80501104
</td>
<td>
<b>MP_ERROR_CODE_CANCELLED</b>
</td>
</tr>
<tr>
<td>
0x80501105
</td>
<td>
<b>MP_ERROR_CODE_NO_TARGETOS</b>
</td>
</tr>
<tr>
<td>
0x80501106
</td>
<td>
<b>MP_ERROR_CODE_BAD_REGEXP</b>
</td>
</tr>
<tr>
<td>
0x80501107
</td>
<td>
<b>MP_ERROR_TEST_INDUCED_ERROR</b>
</td>
</tr>
<tr>
<td>
0x80501108
</td>
<td>
<b>MP_ERROR_SIG_BACKUP_DISABLED</b>
</td>
</tr>
<tr>
<td>
0x80508001
</td>
<td>
<b>ERR_MP_BAD_INIT_MODULES</b>
</td>
</tr>
<tr>
<td>
0x80508002
</td>
<td>
<b>ERR_MP_BAD_DATABASE</b>
</td>
</tr>
<tr>
<td>
0x80508004
</td>
<td>
<b>ERR_MP_BAD_UFS </b>
</td>
</tr>
<tr>
<td>
0x8050800C
</td>
<td>
<b>ERR_MP_BAD_INPUT_DATA</b>
</td>
</tr>
<tr>
<td>
0x8050800D
</td>
<td>
<b>ERR_MP_BAD_GLOBAL_STORAGE</b>
</td>
</tr>
<tr>
<td>
0x8050800E
</td>
<td>
<b>ERR_MP_OBSOLETE</b>
</td>
</tr>
<tr>
<td>
0x8050800F
</td>
<td>
<b>ERR_MP_NOT_SUPPORTED</b>
</td>
</tr>
<tr>
<td>
0x8050800F 0x80508010
</td>
<td>
<b>ERR_MP_NO_MORE_ITEMS </b>
</td>
</tr>
<tr>
<td>
0x80508011
</td>
<td>
<b>ERR_MP_DUPLICATE_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508012
</td>
<td>
<b>ERR_MP_BAD_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508013
</td>
<td>
<b>ERR_MP_BAD_USERDB_VERSION</b>
</td>
</tr>
<tr>
<td>
0x80508014
</td>
<td>
<b>ERR_MP_RESTORE_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80508016
</td>
<td>
<b>ERR_MP_BAD_ACTION</b>
</td>
</tr>
<tr>
<td>
0x80508019
</td>
<td>
<b>ERR_MP_NOT_FOUND</b>
</td>
</tr>
<tr>
<td>
0x80509001
</td>
<td>
<b>ERR_RELO_BAD_EHANDLE</b>
</td>
</tr>
<tr>
<td>
0x80509003
</td>
<td>
<b>ERR_RELO_KERNEL_NOT_LOADED</b>
</td>
</tr>
<tr>
<td>
0x8050A001
</td>
<td>
<b>ERR_MP_BADDB_OPEN</b>
</td>
</tr>
<tr>
<td>
0x8050A002
</td>
<td>
<b>ERR_MP_BADDB_HEADER</b>
</td>
</tr>
<tr>
<td>
0x8050A003
</td>
<td>
<b>ERR_MP_BADDB_OLDENGINE</b>
</td>
</tr>
<tr>
<td>
0x8050A004
</td>
<td>
<b>ERR_MP_BADDB_CONTENT </b>
</td>
</tr>
<tr>
<td>
0x8050A005
</td>
<td>
<b>ERR_MP_BADDB_NOTSIGNED</b>
</td>
</tr>
<tr>
<td>
0x8050801
</td>
<td>
<b>ERR_MP_REMOVE_FAILED</b>
</td>
<td>
Bu bir iç hatadır. Kötü amaçlı yazılım kaldırma başarılı değilken bu tetiklenir.
</td>
</tr>
<tr>
<td>
0x80508018
</td>
<td>
<b>ERR_MP_SCAN_ABORTED </b>
</td>
<td>
Bu bir iç hatadır. Taramanın tamamı başarısız olduğunda tetiklenen bir durum olabilir.
</td>
</tr>
</table>

## <a name="related-topics"></a>İlgili konular

- [Koruma hakkında Microsoft Defender Virüsten Koruma bildirme](report-monitor-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
