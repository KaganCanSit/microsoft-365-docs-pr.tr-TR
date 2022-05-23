---
title: olay kimliklerini ve hata kodlarını Microsoft Defender Virüsten Koruma
description: Microsoft Defender Virüsten Koruma olay kimlikleri ve hataları için nedenleri ve çözümleri arama
keywords: olay, hata kodu, siem, günlüğe kaydetme, sorun giderme, wef, windows olay iletme
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
ms.openlocfilehash: 9008fe0d6a4c46d544e4d806c3a15b24c53f2f10
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637994"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma ile ilgili sorunları gidermek için olay günlüklerini ve hata kodlarını inceleyin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma ile ilgili bir sorunla karşılaşırsanız, eşleşen bir sorunu ve olası çözümü bulmak için bu konudaki tablolarda arama yapabilirsiniz.

Tablo listesi:

- [Microsoft Defender Virüsten Koruma olay kimlikleri](#windows-defender-av-ids) (bunlar Windows 10, Windows 11 ve Windows Server 2016 için geçerlidir)
- [İstemci hata kodlarını Microsoft Defender Virüsten Koruma](#error-codes)
- [İç Microsoft Defender Virüsten Koruma istemcisi hata kodları (Geliştirme ve test sırasında Microsoft tarafından kullanılır)](#internal-error-codes)

> [!TIP]
> Aşağıdaki özelliklerin çalıştığını onaylamak için [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Uç Nokta için Microsoft Defender tanıtım web sitesini de ziyaret edebilirsiniz:
>
> - Bulut tabanlı koruma
> - Hızlı öğrenme (ilk bakışta engelle dahil)
> - İstenmeyebilecek uygulama engelleme

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>olay kimliklerini Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma olay kimliklerini Windows olay günlüğüne kaydeder.

Olay günlüğünü doğrudan görüntüleyebilir veya üçüncü taraf güvenlik bilgileri ve olay yönetimi (SIEM) aracınız varsa, uç noktalarınızdaki belirli olayları ve hataları gözden geçirmek için [Microsoft Defender Virüsten Koruma istemci olay kimliklerini](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) de kullanabilirsiniz.

Bu bölümdeki tabloda ana Microsoft Defender Virüsten Koruma olay kimlikleri listelenir ve mümkün olduğunda hatayı düzeltmek veya çözmek için önerilen çözümler sağlanır.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Microsoft Defender Virüsten Koruma olayı görüntülemek için

1. **Olay Görüntüleyicisi** açın.
2. Konsol ağacında **Uygulama ve Hizmet Günlükleri'ni**, ardından **Microsoft'u**, **ardından Windows** ve **Windows Defender** genişletin.
3. **İşletimsel'e** çift tıklayın.
4. Ayrıntılar bölmesinde, olayınızı bulmak için tek tek olayların listesini görüntüleyin.
5. Alt bölmedeki **Genel** ve **Ayrıntılar** sekmelerinin altındaki bir olayla ilgili belirli ayrıntıları görmek için olaya tıklayın.

<table>
<tr>
<th colspan="2" >Olay Kimliği: 1000</th>
</tr>
<tr>
<td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma taraması başlatıldı. </b>
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Tarama Kaynakları: &lt; Taranan kaynaklar (dosyalar/dizinler/BHO gibi).&gt;</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1001</th>
</tr>
<tr><td>
Sembolik ad:
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserScan&gt;</dt> 
<dt>Saati: &lt;Taramanın süresi.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1002</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma taraması tamamlanmadan durduruldu. </b>
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Etki alanılt&gt;&amp;; UserScan&gt;</dt> 
<dt>Saati: &lt;Taramanın süresi.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1003</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma taraması duraklatıldı. </b>
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt;Etki alanılt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1004</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma taraması sürdürüldü. </b>
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt;Etki alanılt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1005</th>
</tr>
<tr><td>
Sembolik ad:
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
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Tarama Parametreleri: &lt;Tarama parametreleri&gt;, örneğin:<ul>
<li>Tam tarama</li>
<li>Hızlı tarama</li>
<li>Müşteri taraması</li>
</ul>
</dt>
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Virüsten koruma istemcisi bir hatayla karşılaştı ve geçerli tarama durduruldu. Tarama, istemci tarafı bir sorundan dolayı başarısız olabilir. Bu olay kaydı tarama kimliğini, tarama türünü (Microsoft Defender Virüsten Koruma, casus yazılımdan koruma, kötü amaçlı yazılımdan koruma), tarama parametrelerini, taramayı başlatan kullanıcıyı, hata kodunu ve hatanın açıklamasını içerir.
Bu olayla ilgili sorunları gidermek için:
<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa<a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Desteği sitesine</a> gidin, hata kodunu aramak için <b>Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1006</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı kötü amaçlı yazılım veya diğer istenmeyebilecek yazılımları buldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Adı: &lt;PIDSignature&gt; Sürümündeki İşlem</dt>
<dt>: &lt;Tanım sürümüİndirim&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1007</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu sisteminizi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için bir eylem gerçekleştirdi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bu makineyi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için eyleme geçti. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt>
<dt> Eylem: &lt;Eylem&gt;, örneğin:<ul>
<li>Temiz: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/varolmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiği bu eylem listesinden biri olan kullanıcı tanımlı eylem</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütülmesi engellendi</li>
</ul>
</dt>
<dt>Durum: &lt; StatusSignature&gt;</dt> 
<dt>Sürümü: &lt;Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1008</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu sisteminizi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için bir eylem gerçekleştirmeye çalıştı, ancak eylem başarısız oldu.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım veya diğer istenmeyebilecek yazılımlar üzerinde işlem yaparken bir hatayla karşılaştı. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluAction&gt;</dt>
<dt>: &lt;Eylem&gt;, örneğin:<ul>
<li>Temiz: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/varolmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiği bu eylem listesinden biri olan kullanıcı tanımlı eylem</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütülmesi engellendi</li>
</ul>
</dt>
<dt>Hata Kodu: &lt; Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>Durum: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1009</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu bir öğeyi karantinadan geri yükledi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bir öğeyi karantinadan geri yükledi. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluKullanıcı&gt;</dt>
<dt>: &lt;Etki alanılt&gt;\&; UserSignature&gt;</dt> 
<dt>Sürümü: &lt;Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1010</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu bir öğeyi karantinadan geri yükleyemedi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, bir öğeyi karantinadan geri yüklemeye çalışırken bir hatayla karşılaştı. Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluKullanıcı&gt;</dt>
<dt>: &lt;Etki alanılt&gt;\&; UserError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1011</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma bir öğeyi karantinadan sildi.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluKullanıcı&gt;</dt>
<dt>: &lt;Etki alanılt&gt;\&; UserSignature&gt;</dt> 
<dt>Sürümü: &lt;Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1012</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu bir öğeyi karantinadan silemedi.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bir öğeyi karantinadan silmeye çalışırken hatayla karşılaştı.
Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluKullanıcı&gt;</dt>
<dt>: &lt;Etki alanılt&gt;\&; UserError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1013</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu kötü amaçlı yazılım geçmişini ve diğer istenmeyebilecek yazılımları sildi.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, kötü amaçlı yazılım geçmişini ve istenmeyebilecek diğer yazılımları kaldırmıştır.
<dl>
<dt>Saat: Olayın gerçekleştiği zaman, örneğin geçmişin temizlenme zamanı. Bu parametre tehdit olaylarında kullanılmaz, böylece düzeltme süresi veya bulaşma süresiyle ilgili bir karışıklık olmaz. Bunlar için, bunları özellikle Eylem Zamanı veya Algılama Zamanı olarak adlandırıyoruz.</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1014</th>
</tr>
<tr><td>
Sembolik ad:
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
Kötü amaçlı yazılımdan koruma platformu kötü amaçlı yazılım geçmişini ve istenmeyebilecek diğer yazılımları silemedi.
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, kötü amaçlı yazılım geçmişini ve istenmeyebilecek diğer yazılımları kaldırmaya çalışırken bir hatayla karşılaştı.
<dl>
<dt>Saat: Olayın gerçekleştiği zaman, örneğin geçmişin temizlenme zamanı. Bu parametre tehdit olaylarında kullanılmaz, böylece düzeltme süresi veya bulaşma süresiyle ilgili bir karışıklık olmaz. Bunlar için, bunları özellikle Eylem Zamanı veya Algılama Zamanı olarak adlandırıyoruz.</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri. </dt>
<dt>Hata Açıklaması: &lt;Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1015</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu şüpheli davranış algılandı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma şüpheli bir davranış algılamıştır.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Adı: &lt;PIDSignature&gt;</dt> 
<dt>Id: Sabit listesi eşleşen önem derecesi</dt> içindeki işlem. 
<dt>İmza Sürümü: &lt; Tanım versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine versionFidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;Dosyanın dosya adı&gt;.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1116</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu kötü amaçlı yazılım veya diğer olası istenmeyen yazılımlar algıladı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım veya diğer istenmeyebilecek yazılımlar algıladı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;PROCESS in the PIDSignature&gt;</dt> 
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
Eylem gerekmez. Microsoft Defender Virüsten Koruma bu tehdit üzerinde askıya alabilir ve rutin eylemler gerçekleştirebilir. Tehdidi el ile kaldırmak istiyorsanız, Microsoft Defender Virüsten Koruma arabiriminde <b>Bilgisayarı Temizle'ye</b> tıklayın.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1117</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu sisteminizi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için bir eylem gerçekleştirdi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma bu makineyi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için eyleme geçti.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Adı: &lt;PIDAction&gt;</dt>
<dt>: &lt;Action&gt; içindeki işlem, örneğin:<ul>
<li>Temiz: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/varolmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiği bu eylem listesinden biri olan kullanıcı tanımlı eylem</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütülmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek actionsError&gt;</dt> 
<dt>Code: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu açıklaması. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİndirim&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürüm&gt;</dt> NOT: Microsoft Defender Virüsten Koruma, Microsoft Security Essentials, Kötü Amaçlı Yazılımları Temizleme Aracı veya System Center Endpoint Protection  bir kötü amaçlı yazılım algılar, kötü amaçlı yazılımın değiştirmiş olabileceği aşağıdaki sistem ayarlarını ve hizmetlerini geri yükler:<ul>
<li>Varsayılan Internet Explorer veya Microsoft Edge ayarı</li>
<li>Kullanıcı Access Control ayarları</li>
<li>Chrome ayarları</li>
<li>Önyükleme Denetimi Verileri</li>
<li>Regedit ve Görev Yöneticisi kayıt defteri ayarları</li>
<li>Windows Update, Arka Plan Akıllı Aktarım Hizmeti ve Uzaktan Yordam Çağrısı hizmeti</li>
<li>İşletim Sistemi dosyalarını Windows</li></ul>
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
Windows Vista (Service Pack 1 veya Service Pack 2), Windows 7 ve üzeri
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
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma bir tehdidi kaldırdı veya karantinaya alındı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1118</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu sisteminizi kötü amaçlı yazılımlardan veya istenmeyebilecek diğer yazılımlardan korumak için bir eylem gerçekleştirmeye çalıştı, ancak eylem başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım veya istenmeyebilecek diğer yazılımlar üzerinde işlem yaparken kritik olmayan bir hatayla karşılaştı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Adı: &lt;PIDAction&gt;</dt>
<dt>: &lt;Action&gt; içindeki işlem, örneğin:<ul>
<li>Temiz: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/varolmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiği bu eylem listesinden biri olan kullanıcı tanımlı eylem</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütülmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek actionsError&gt;</dt> 
<dt>Code: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu açıklaması. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİndirim&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma kötü amaçlı yazılım düzeltmesi ile ilgili bir görevi tamamlayamadı. Bu kritik bir hata değildir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1119</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu, kötü amaçlı yazılım veya istenmeyebilecek diğer yazılımlar üzerinde işlem yapmaya çalışırken kritik bir hatayla karşılaştı. Olay iletisinde daha fazla ayrıntı vardır.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma, kötü amaçlı yazılım veya istenmeyebilecek diğer yazılımlar üzerinde işlem yaparken kritik bir hatayla karşılaştı.<br/>Daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Adı: &lt; Tehdit nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Önem Derecesi&gt;, örneğin:<ul>
<li>Düşük</li>
<li>Orta</li>
<li>Yüksek</li>
<li>Şiddetli</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategori açıklaması&gt;, örneğin herhangi bir tehdit veya kötü amaçlı yazılım türü.</dt> 
<dt>Yolu: &lt; Dosya yoluDetection&gt;</dt>
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
<li>Sezgisel</li>
<li>Genel</li>
<li>Beton</li>
<li>Dinamik imza</li>
</ul>
</dt>
<dt>Algılama Kaynağı: &lt;Algılama kaynağı&gt; örneğin:<ul>
<li>Kullanıcı: kullanıcı tarafından başlatıldı</li>
<li>Sistem: sistem başlatıldı</li>
<li>Gerçek zamanlı: gerçek zamanlı bileşen başlatıldı</li>
<li>IOAV: IE İndirmeleri ve Outlook Express Ekleri başlatıldı</li>
<li>NIS: Ağ denetleme sistemi</li>
<li>IEPROTECT: IE - IExtensionValidation; bu, kötü amaçlı web sayfası denetimlerine karşı koruma sağlar</li>
<li>Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM). Bu, önyükleme dizisi tarafından algılanan kötü amaçlı yazılımları içerir</li>
<li>Uzaktan kanıtlama</li>
</ul>Kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI). Birincil olarak betikleri korumak için kullanılır (PowerShell, VBS), ancak üçüncü taraflarca da çağrılabilir.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Adı: &lt;PIDAction&gt;</dt>
<dt>: &lt;Action&gt; içindeki işlem, örneğin:<ul>
<li>Temiz: Kaynak temizlendi</li>
<li>Karantina: Kaynak karantinaya alındı</li>
<li>Kaldır: Kaynak silindi</li>
<li>İzin Ver: Kaynağın yürütülmesine/varolmasına izin verildi</li>
<li>Kullanıcı tanımlı: Normalde kullanıcının belirttiği bu eylem listesinden biri olan kullanıcı tanımlı eylem</li>
<li>Eylem yok: Eylem yok</li>
<li>Engelle: Kaynağın yürütülmesi engellendi</li>
</ul>
</dt>
<dt>Eylem Durumu: &lt; Ek actionsError&gt;</dt> 
<dt>Code: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu açıklaması. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİndirim&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Microsoft Defender Virüsten Koruma istemcisi kritik sorunlar nedeniyle bu hatayla karşılaştı. Uç nokta korunmuyor olabilir. Hata açıklamasını gözden geçirin ve aşağıdaki ilgili <b>Kullanıcı eylemi</b> adımlarını izleyin.
<table>
<tr>
<th>Eylem</th>
<th>Kullanıcı eylemi</th>
</tr>
<tr>
<td>
<b>Kaldırmak</b>
</td>
<td>
Tanımları güncelleştirin ve kaldırma işleminin başarılı olduğunu doğrulayın.
</td>
</tr>
<tr>
<td>
<b>Temiz</b>
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
<b>Izin</b>
</td>
<td>
Kullanıcının gerekli kaynaklara erişme izni olduğunu doğrulayın.
</td>
</tr>
</table>

Bu olay devam ederse:<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa<a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Desteği sitesine</a> gidin, hata kodunu aramak için <b>Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1120</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Microsoft Defender Virüsten Koruma bir tehdit kaynağının karmalarını çıkarmıştır.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma istemcisi çalışır durumda.
<dl>
<dt>Geçerli Platform Sürümü: &lt; Geçerli platform sürümüCihaz&gt;</dt> 
<dt>Kaynak Yolu: &lt;PathHashes&gt;</dt>
<dt>: &lt;Karmalar&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Not: Bu olay yalnızca şu ilke ayarlandıysa günlüğe kaydedilir: <b>ThreatFileHashLogging imzasız</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1127</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Denetimli Klasör Erişimi (CFA), güvenilmeyen bir işlemin bellekte değişiklik yapmasını engelledi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Denetimli Klasör Erişimi, güvenilmeyen bir işlemin disk kesimlerini değiştirme olasılığını engelledi.
<br/> Olay kaydı hakkında daha fazla bilgi için aşağıdakilere bakın:
<dl>
<dt>Eventıd: &lt; EventID&gt;, örneğin: 1127Version</dt>
<dt>: &lt;Sürüm&gt;, örneğin:</dt> 
<dt>0Level: &lt;Level&gt;, örneğin: win:</dt>
<dt>WarningTimeCreated: &lt;SystemTime&gt;, olayın oluşturulduğu</dt> 
<dt>zamanEventRecordID: EventRecordID, &lt;event logExecution ProcessID&gt;</dt>
<dt>: Execution ProcessID&gt;, eventChannel oluşturan işlem: &lt;</dt>
<dt>&lt;Olay kanalı&gt;, örneğin: Microsoft- Windows-Windows Defender/</dt>
<dt>OperationalComputer: &lt;Bilgisayar adıGüvenlik&gt;</dt> 
<dt>UserID: &lt;Güvenlik UserIDÜrün&gt;</dt> 
<dt>Adı: &lt;Ürün Adı&gt;, örneğin: Microsoft Defender Virüsten Koruma</dt> 
<dt>Ürün Sürümü: &lt;Ürün Sürümü&gt;</dt>
<dt> Algılama Süresi: &lt;Algılama Süresi&gt;, CFA'nın güvenilmeyen bir işlemi engellediği</dt> 
<dt>zamanKullanıcı: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;Cihaz adı&gt;, güvenilmeyen bir işlemin modifikasyonu için eriştiği cihazın veya diskin</dt> 
<dt>adıİşlem Adı: &lt;İşlem yolu&gt;, CFA'nın değişiklik için cihaza veya diske erişmesini engellediği işlem yolu</dt> 
<dt>adıGüvenlik Bilgileri Sürümü: &lt;Güvenlik zekası sürümüİngiltere&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Kullanıcı, Engellenen işlemi Powershell veya Windows Güvenliği Center kullanarak CFA için <i>İzin Verilen İşlem</i> listesine ekleyebilir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 1150</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformunuz durumu bir izleme platformuna bildirirse, bu olay kötü amaçlı yazılımdan koruma platformunun çalıştığını ve iyi durumda olduğunu gösterir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma istemcisi çalışır durumda.
<dl>
<dt>Platform Sürümü: &lt; Geçerli platform sürümüSignature&gt;</dt> 
<dt>Sürümü: &lt;Tanım sürümüİndirim&gt;</dt> 
<dt>Sürümü: &lt;Antimalware Engine sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma istemcisi iyi durumda. Bu olay saatlik olarak bildirilir.
</td>
</tr>

<tr>
<th colspan="2">Olay Kimliği: 1151</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Endpoint Protection istemci sistem durumu raporu (UTC saati)</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Virüsten koruma istemcisi sistem durumu raporu.
<dl>
<dt>Platform Sürümü: &lt; Geçerli platform sürümüİndir&gt;</dt> sürüm
<dt>: &lt;Antimalware Engine sürümNetwork&gt;</dt> 
<dt>Realtime Inspection altyapısı sürümü: &lt;Ağ Realtime Inspection altyapısı sürümüAntivirus&gt;</dt> 
<dt>imza sürümü: &lt;Virüsten koruma imzası sürümüAntispyware&gt;</dt> 
<dt>imza sürümü: &lt;Casus yazılımdan koruma imzası sürümüNetwork&gt;</dt> 
<dt>Realtime Inspection imza sürümü: &lt; Ağ Gerçek Zamanlı İnceleme imzası sürümüRTP&gt;</dt> 
<dt>durumu: &lt;Gerçek zamanlı koruma durumu&gt; (Etkin veya Devre Dışı)</dt>
<dt>OA durumu: &lt;Erişim durumunda&gt; (Etkin veya Devre Dışı)</dt>
<dt>IOAV durumu: &lt;IE İndirmeleri ve Outlook Hızlı Ekler durumu (Etkin veya Devre Dışı)BM durumu&gt;</dt>
<dt>: &lt;Davranış İzleme durumu&gt; (Etkin veya Devre Dışı)</dt>
<dt>Virüsten koruma imza yaşı: &lt;Virüsten koruma imza yaşı&gt;  (gün olarak)</dt> 
<dt>Casus yazılımdan koruma imzası yaşı: &lt; Casus yazılımdan koruma imza yaşı&gt; (gün)</dt>
<dt>Son hızlı tarama yaşı: &lt;Son hızlı tarama yaşı&gt; (gün)</dt>
<dt>Son tam tarama yaşı: &lt;Son tam tarama yaşı&gt; (gün olarak)Virüsten koruma</dt> 
<dt>imzası oluşturma zamanı: ?&lt; Virüsten koruma imzası oluşturma zamanıAntispyware&gt;</dt> 
<dt>imza oluşturma zamanı: ?&lt; Casus yazılımdan koruma imzası oluşturma zamanıLast&gt;</dt> 
<dt>hızlı tarama başlangıç zamanı: ?&lt; Son hızlı tarama başlangıç zamanıHizli&gt;</dt> 
<dt>tarama bitiş saati: ?&lt; Son hızlı tarama bitiş zamanıSon&gt;</dt> 
<dt>hızlı tarama kaynağı: &lt;Son hızlı tarama kaynağı&gt; (0 = tarama çalışmadı, 1 = kullanıcı tarafından başlatıldı, 2 = sistem başlatıldı)</dt>
<dt>Son tam tarama başlangıç zamanı: ?&lt; Son tam tarama başlangıç zamanıYeni&gt;</dt> 
<dt>tarama bitiş saati: ?&lt; Son tam tarama bitiş zamanıSon&gt;</dt> 
<dt>tam tarama kaynağı: &lt;Son tam tarama kaynağı&gt; (0 = tarama çalışmadı, 1 = kullanıcı tarafından başlatıldı, 2 = sistem başlatıldı)</dt>
<dt>Ürün durumu: İç sorun giderme için
</dl>
</td>
</tr>

<tr>
<th colspan="2">Olay Kimliği: 2000</th>
</tr>
<tr><td>
Sembolik ad:
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
Virüsten koruma imzası sürümü güncelleştirildi.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüÖnceki&gt;</dt> 
<dt>İmza Sürümü: &lt;Önceki imza sürümü&gt;</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Güncelleştirme Türü: &lt; Güncelleştirme türü&gt;( Tam veya Delta).</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserCurrent&gt;</dt> 
<dt>Altyapısı Sürümü: &lt;Geçerli altyapı sürümüÖnceki&gt;</dt> 
<dt>Altyapı Sürümü: &lt;Önceki altyapı sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma istemcisi iyi durumda. İmzalar başarıyla güncelleştirildiğinde bu olay bildirilir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2001</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Güvenlik bilgileri güncelleştirmesi başarısız oldu. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma imzaları güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Yeni güvenlik bilgileri sürümü: &lt; Yeni sürüm numarasıÖnceki&gt;</dt> 
<dt>güvenlik bilgileri sürümü: &lt;Önceki sürümGüncelleştirme&gt;</dt>
<dt> Kaynağı: &lt;Güncelleştirme kaynağı&gt;, örneğin:
<ul>
<li>Güvenlik bilgileri güncelleştirme klasörü</li>
<li>İç güvenlik bilgileri güncelleştirme sunucusu</li>
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
<dt>Kaynak Yol: Evrensel Adlandırma Kuralı (UNC) için dosya paylaşımı adı, Windows Sunucu Güncelleştirme Hizmetleri (WSUS)/Microsoft Update/ADL için sunucu adı.</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Güncelleştirme Türü: &lt; Güncelleştirme türü&gt;( Tam veya Delta).</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine versionError&gt;</dt> 
<dt>Code: &lt;Error code&gt; Result code with threat status. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Tanımları güncelleştirirken bir sorun olduğunda bu hata oluşur.
Bu olayla ilgili sorunları gidermek için:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Tanımları güncelleştirin</a> ve yeniden taramayı doğrudan uç noktada zorlar.</li>
<li>Bu hata hakkında daha fazla bilgi için %Windir%\WindowsUpdate.log dosyasındaki girdileri gözden geçirin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2002</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma altyapısı sürümü güncelleştirildi.
<dl>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüÖnceki&gt;</dt> 
<dt>Altyapı Sürümü: &lt;Önceki altyapı sürümüEngine&gt;</dt> 
<dt>Türü: &lt;Motor türü&gt;, kötü amaçlı yazılımdan koruma altyapısı veya Ağ İnceleme Sistemi altyapısı.</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; Kullanıcı&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma istemcisi iyi durumda. Kötü amaçlı yazılımdan koruma altyapısı başarıyla güncelleştirildiğinde bu olay bildirilir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2003</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma, altyapıyı güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Yeni Altyapı Sürümü:</dt>
<dt>Önceki Altyapı Sürümü: &lt;Önceki altyapı sürümüİngiliz&gt;</dt> 
<dt>Türü: &lt;Motor türü&gt;, kötü amaçlı yazılımdan koruma altyapısı veya Ağ İnceleme Sistemi altyapısı.</dt> 
<dt>Kullanıcı: &lt; Etki alanılt&gt;\&; UserError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Microsoft Defender Virüsten Koruma istemci güncelleştirmesi başarısız oldu. bu olay, istemci kendisini güncelleştiremediğinde oluşur. Bu olay genellikle bir güncelleştirme sırasında ağ bağlantısındaki bir kesintiden kaynaklanır.
Bu olayla ilgili sorunları gidermek için:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Tanımları güncelleştirin</a> ve yeniden taramayı doğrudan uç noktada zorlar.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2004</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma tanımları yüklenirken bir sorun oluştu. Kötü amaçlı yazılımdan koruma altyapısı bilinen son iyi tanım kümesini yüklemeyi dener.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma imzaları yüklemeye çalışırken bir hatayla karşılaştı ve bilinen iyi bir imza kümesine geri dönmeye çalışacak.
<dl>
<dt>İmza denendi:</dt>
<dt>Hata Kodu: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>İmza Sürümü: &lt; Tanım sürümüİngiliz&gt;</dt> 
<dt>Sürümü: &lt;Kötü amaçlı yazılımdan koruma altyapısı sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Microsoft Defender Virüsten Koruma istemcisi en son tanımlar dosyasını indirmeye ve yüklemeye çalıştı ve başarısız oldu. İstemci tanımları yüklemeye çalışırken bir hatayla karşılaştığında veya dosya bozuksa bu hata oluşabilir. Microsoft Defender Virüsten Koruma bilinen iyi bir tanım kümesine geri dönmeye çalışır.
Bu olayla ilgili sorunları gidermek için:
<ol>
<li>Bilgisayarı yeniden başlatın ve yeniden deneyin.</li>
<li><a href="https://aka.ms/wdsi">Microsoft Güvenlik Zekası sitesinden</a> en son tanımları indirin.
Not: Siteden indirilen tanım dosyasının boyutu 60 MB'ı aşabilir ve tanımları güncelleştirmek için uzun vadeli bir çözüm olarak kullanılmamalıdır.
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
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu güncel olmadığından kötü amaçlı yazılımdan koruma altyapısı yüklenemedi. Kötü amaçlı yazılımdan koruma platformu bilinen son iyi kötü amaçlı yazılımdan koruma altyapısını yükler ve güncelleştirmeyi dener.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
geçerli platform sürümü desteklenmediğinden Microsoft Defender Virüsten Koruma kötü amaçlı yazılımdan koruma altyapısı yüklenemedi. Microsoft Defender Virüsten Koruma bilinen son iyi altyapıya geri döner ve bir platform güncelleştirmesi denenecektir.
<dl>
<dt>Geçerli Platform Sürümü: &lt;Geçerli platform sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2006</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma platformu güncelleştirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Geçerli Platform Sürümü: &lt; Geçerli platform versionError&gt;</dt> 
<dt>Kodu: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2007</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma yakında kötü amaçlı yazılımdan koruma altyapısının gelecek sürümlerini desteklemek için daha yeni bir platform sürümü gerekecektir. Kullanılabilir en iyi koruma düzeyini korumak için en son Microsoft Defender Virüsten Koruma platformunu indirin.
<dl>
<dt>Geçerli Platform Sürümü: &lt;Geçerli platform sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2010</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı, ek tanımları almak için Dinamik İmza Hizmeti'ni kullandı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma makinenizin korunmasına yardımcı olmak üzere ek imzaları almak için <i>Dinamik İmza Hizmeti'nin</i> kullanılması.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümü&gt;</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
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
<dt>Kalıcılık Yolu: &lt; PathDynamic&gt;</dt> 
<dt>signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Kalıcılık Sınırı: Fastpath imzasının kalıcılık sınırı.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2011</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Dinamik İmza Hizmeti güncel olmayan dinamik tanımları sildi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma eski imzaları atmak için <i>Dinamik İmza Hizmeti</i> kullandı.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümü&gt;</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
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
<dt>Kalıcılık Yolu: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Sürüm numarasıDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistence limit type&gt;, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Kalıcılık Sınırı: Fastpath imzasının kalıcılık sınırı.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Hiçbir eylem gerekli değildir. Microsoft Defender Virüsten Koruma istemcisi iyi durumda. Bu olay, Dinamik İmza Hizmeti güncel olmayan dinamik tanımları başarıyla sildiğinde bildirilir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2012</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı Dinamik İmza Hizmeti'ni kullanmaya çalışırken bir hatayla karşılaştı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma<i>, Dinamik İmza Hizmeti'ni</i> kullanmaya çalışırken bir hatayla karşılaştı.
<dl>
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümü&gt;</dt>
<dt> İmza Türü: &lt;İmza türü&gt;, örneğin: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Geçerli Altyapı Sürümü: &lt; Geçerli altyapı sürümüHata&gt;</dt> 
<dt>Kodu: &lt;Hata kodu&gt; Tehdit durumuyla ilişkili sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
<dt> Dinamik İmza Türü: &lt;Dinamik imza türü&gt;, örneğin:
<ul>
<li>Sürüm</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
<li>Süre</li>
</ul>
</dt>
<dt>Kalıcılık Yolu: &lt; PathDynamic&gt;</dt> 
<dt>signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, örneğin:
<ul>
<li>VDM sürümü</li>
<li>Zaman damgası</li>
<li>Sınır yok</li>
</ul>
</dt>
<dt>Kalıcılık Sınırı: Fastpath imzasının kalıcılık sınırı.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İnternet bağlantı ayarlarınızı denetleyin.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2013</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma tüm <i>Dinamik İmza Hizmeti</i> imzalarını atmış.
<dl>
<dt>Geçerli İmza Sürümü: &lt;Geçerli imza sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2020</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma temiz bir dosya indirdi.
<dl>
<dt>Dosyaadı: &lt; Dosyanın dosya adı&gt;.</dt> 
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüGeçerli&gt;</dt> 
<dt>Altyapı Sürümü: &lt;Geçerli altyapı sürümü&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2021</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı temiz bir dosya indiremedi. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma temiz bir dosyayı indirmeye çalışırken bir hatayla karşılaştı.
<dl>
<dt>Dosyaadı: &lt; Dosyanın dosya adı&gt;.</dt> 
<dt>Geçerli İmza Sürümü: &lt; Geçerli imza sürümüGeçerli&gt;</dt> 
<dt>Altyapı Sürümü: &lt;Geçerli altyapı sürümüError&gt;</dt> 
<dt>Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
İnternet bağlantı ayarlarınızı denetleyin.
Microsoft Defender Virüsten Koruma istemcisi, en son tanımları belirli bir tehdide indirmek için Dinamik İmza Hizmeti'ni kullanırken bir hatayla karşılaştı. Bu hata büyük olasılıkla bir ağ bağlantısı sorunundan kaynaklanır.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2030</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı indirildi ve bir sonraki sistem yeniden başlatmada çevrimdışı çalışacak şekilde yapılandırıldı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma çevrimdışı virüsten korumayı bir sonraki yeniden başlatmada çalışacak şekilde indirip yapılandırdı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2031</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı çevrimdışı taramayı indiremedi ve yapılandıramadı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma çevrimdışı virüsten korumayı indirmeye ve yapılandırmaya çalışırken bir hatayla karşılaştı.
<dl>
<dt>Hata Kodu: &lt; Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2040</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Bu işletim sistemi sürümü için kötü amaçlı yazılımdan koruma desteği yakında sona erecek. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sisteminiz için desteğin süresi kısa süre sonra dolacaktır. Destek dışı bir işletim sisteminde Microsoft Defender Virüsten Koruma çalıştırmak, tehditlere karşı korunmak için yeterli bir çözüm değildir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2041</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Bu işletim sistemi için kötü amaçlı yazılımdan koruma desteği sona erdi. Sürekli destek için işletim sistemini yükseltmeniz gerekir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sisteminizin desteğinin süresi doldu. Destek dışı bir işletim sisteminde Microsoft Defender Virüsten Koruma çalıştırmak, tehditlere karşı korunmak için yeterli bir çözüm değildir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 2042</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma altyapısı artık bu işletim sistemini desteklemez ve artık sisteminizi kötü amaçlı yazılımlardan korumaz. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
İşletim sisteminizin desteğinin süresi doldu. Microsoft Defender Virüsten Koruma artık işletim sisteminizde desteklenmiyor, çalışmayı durdurdu ve kötü amaçlı yazılım tehditlerine karşı korunmuyor.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 3002</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma Real-Time Koruma özelliği bir hatayla karşılaştı ve başarısız oldu.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'te</li>
<li>Internet Explorer indirmeleri ve Microsoft Outlook Express ekleri</li>
<li>Davranış izleme</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Hata Kodu: &lt; Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt> 
<dt>Neden: Gerçek zamanlı korumanın Microsoft Defender Virüsten Koruma bir özelliği yeniden başlatmasının nedeni.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Sistemin bir süre korunmamış olması mümkün olduğundan sistemi yeniden başlatmanız ve tam tarama çalıştırmanız gerekir.
hizmetlerden biri başlatılamadığından Microsoft Defender Virüsten Koruma istemcisinin gerçek zamanlı koruma özelliği bir hatayla karşılaştı.
Ardından 3007 olay kimliği geliyorsa, hata geçicidir ve kötü amaçlı yazılımdan koruma istemcisi hatadan kurtarılır.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 3007</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Bir hatadan kurtarılan gerçek zamanlı koruma. Bu hatayı gördüğünüzde tam sistem taraması çalıştırmanızı öneririz. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma Gerçek Zamanlı Koruma bir özelliği yeniden başlattı. Bu aracı devre dışıyken kaçırılmış olabilecek öğeleri algılamak için tam sistem taraması çalıştırmanız önerilir.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'te</li>
<li>IE indirmeleri ve express eklerini Outlook</li>
<li>Davranış izleme</li>
<li>Ağ İnceleme Sistemi</li>
</ul>
</dt>
<dt>Neden: Gerçek zamanlı korumanın Microsoft Defender Virüsten Koruma bir özelliği yeniden başlatmasının nedeni.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Gerçek zamanlı koruma özelliği yeniden başlatıldı. Bu olay yeniden gerçekleşirse <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek'e</a> başvurun.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5000</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Gerçek zamanlı koruma etkindir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılımlar ve istenmeyebilecek diğer yazılımlar için gerçek zamanlı koruma taraması etkinleştirildi.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5001</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Gerçek zamanlı koruma devre dışı bırakıldı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılımlar ve istenmeyebilecek diğer yazılımlar için gerçek zamanlı koruma taraması devre dışı bırakıldı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5004</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma gerçek zamanlı koruma özelliği yapılandırması değişti.
<dl>
<dt>Özellik: &lt;Özellik&gt;, örneğin:
<ul>
<li>Access'te</li>
<li>IE indirmeleri ve express eklerini Outlook</li>
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
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformu yapılandırması değişti.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yapılandırması değişti. Bu beklenmeyen bir olaysa, kötü amaçlı yazılımların sonucu olabileceğinden ayarları gözden geçirmeniz gerekir.
<dl>
<dt>Eski değer: &lt; Eski değer numarası&gt; Eski virüsten koruma yapılandırma değeri.</dt> 
<dt>Yeni değer: &lt; Yeni değer numarası&gt; Yeni virüsten koruma yapılandırma değeri.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5008</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma altyapısı beklenmeyen bir hata nedeniyle sonlandırıldı.
<dl>
<dt>Hata Türü: &lt; Hata türü&gt;, örneğin: Kilitlenme veya</dt> 
<dt>HangException Kodu: &lt;Hata koduResource&gt;</dt>
<dt>: &lt;Kaynak&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Bu olayla ilgili sorunları gidermek için:<ol>
<li>Hizmeti yeniden başlatmayı deneyin.<ul>
<li>Kötü amaçlı yazılımdan koruma, virüsten koruma ve casus yazılım için, yükseltilmiş bir komut isteminde <b>net stop msmpsvc</b> yazın ve ardından <b>net start msmpsvc</b> yazarak kötü amaçlı yazılımdan koruma altyapısını yeniden başlatın.</li>
<li><i>Ağ İnceleme Sistemi</i> için, yükseltilmiş bir komut isteminde <b>net start nissrv</b> yazın ve ardından <b>net start nissrv</b> yazarak <i>ağ denetleme sistemi</i> altyapısını NiSSRV.exe dosyasını kullanarak yeniden başlatın.
</li>
</ul>
</li>
<li>Aynı şekilde başarısız olursa, <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Desteği Sitesine</a> erişip <b>Arama</b> kutusuna hata numarasını girerek hata kodunu arayın ve <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek'e</a> başvurun.</li>
</ol>
</td>
</tr>
<tr>
<td>
Kullanıcı eylemi:
</td>
<td >
Microsoft Defender Virüsten Koruma istemci altyapısı beklenmeyen bir hata nedeniyle durduruldu.
Bu olayla ilgili sorunları gidermek için:
<ol>
<li>Taramayı yeniden çalıştırın.</li>
<li>Aynı şekilde başarısız olursa<a href="https://go.microsoft.com/fwlink/?LinkId=215163">, Microsoft Desteği sitesine</a> gidin, hata kodunu aramak için <b>Arama</b> kutusuna hata numarasını girin.</li>
<li><a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknik Destek</a> ile iletişime geçin.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5009</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılım ve istenmeyebilecek diğer yazılımlar için tarama etkindir. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım ve diğer istenmeyebilecek yazılımlar için tarama etkinleştirildi.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5010</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılım ve istenmeyebilecek diğer yazılımlar için tarama devre dışı bırakıldı.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma kötü amaçlı yazılım ve diğer istenmeyebilecek yazılımlar için tarama devre dışı bırakıldı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5011</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Virüs taraması etkindir.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma virüs taraması etkinleştirildi.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5012</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Virüs taraması devre dışı bırakıldı. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma virüs taraması devre dışı bırakıldı.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5013</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kurcalama koruması, Microsoft Defender Virüsten Koruma değişikliğini engelledi.</b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Kurcalama koruması etkinleştirilirse, engellenirse Ve Olay Kimliği 5013 oluşturulursa Defender'ın ayarlarından herhangi birini değiştirme girişimi, hangi ayar değişikliğinin engellendiğini belirtir.
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5100</th>
</tr>
<tr><td>
Sembolik ad:
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
<b>Kötü amaçlı yazılımdan koruma platformunun süresi yakında dolacak. </b>
</td>
</tr>
<tr>
<td>
Açıklama:
</td>
<td >
Microsoft Defender Virüsten Koruma yetkisiz kullanım süresi girdi ve yakında sona erecek. Süre dolduktan sonra, bu program virüslere, casus yazılımlara ve istenmeyebilecek diğer yazılımlara karşı korumayı devre dışı bırakır.
<dl>
<dt>Süre Sonu Nedeni: Microsoft Defender Virüsten Koruma süresinin dolmasının nedeni.</dt> 
<dt>Son Kullanma Tarihi: Microsoft Defender Virüsten Koruma tarihi sona erer.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Olay Kimliği: 5101</th>
</tr>
<tr><td>
Sembolik ad:
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
Microsoft Defender Virüsten Koruma yetkisiz kullanım süresi doldu. Virüslere, casus yazılımlara ve istenmeyebilecek diğer yazılımlara karşı koruma devre dışı bırakılmıştır.
<dl>
<dt>Süre Sonu Nedeni:</dt>
<dt>Sona Erme Tarihi: </dt>
<dt>Hata Kodu: &lt;Tehdit durumuyla ilişkili hata kodu&gt; Sonuç kodu. Standart HRESULT değerleri.</dt> 
<dt>Hata Açıklaması: &lt; Hata açıklaması&gt; Hatanın açıklaması. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Microsoft Defender Virüsten Koruma istemci hata kodları Microsoft Defender Virüsten Koruma herhangi bir sorunla karşılaşırsa, genellikle sorunu gidermenize yardımcı olacak bir hata kodu verir. Çoğu zaman hata, güncelleştirme yüklenirken bir sorun olduğu anlamına gelir.
Bu bölüm, Microsoft Defender Virüsten Koruma istemci hataları hakkında aşağıdaki bilgileri sağlar.
- Hata kodu - Şu anda yapılması gerekenlerle ilgili hata - önerisinin olası nedeni

Microsoft Defender Virüsten Koruma hata kodlarıyla ilgili sorunları gidermeye yardımcı olması için bu tablolardaki bilgileri kullanın.


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
Bu hata, belleğiniz tükenmiş olabileceğini gösterir.
</td>
</tr>
<tr>
<td>Çözüm</td>
<td>
<ol>
<li>Cihazınızdaki kullanılabilir belleği denetleyin.</li>
<li>Cihazınızda bellek boşaltmak için çalışan kullanılmayan uygulamaları kapatın.</li>
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
<li>Tanımları güncelleştirin. İki durumdan biri:<ol>
<li>Windows Güvenliği uygulamasında güvenlik bilgileri güncelleştirmelerinizi alın. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Veya
</li>
<li><a href="https://aka.ms/wdsi">Microsoft Güvenlik Zekası sitesinden</a> en son tanımları indirin.
Not: Siteden indirilen tanım dosyasının boyutu 60 MB'ı aşabilir ve tanımları güncelleştirmek için uzun vadeli bir çözüm olarak kullanılmamalıdır.
</li>
</ol>
</li>
<li>Tam tarama çalıştırın.
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
Bu hata, bir altyapı yapılandırması hatası olabileceğini gösterir; genellikle bu, altyapının düzgün çalışmasına izin vermeyen giriş verileriyle ilgilidir.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x805080211
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, Microsoft Defender Virüsten Koruma bir tehdidi karantinaya alamadığını gösterir.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508022
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdit kaldırma işlemini tamamlamak için yeniden başlatma gerektiğini gösterir.
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
Bu hata, tehdidin artık medyada bulunmayabileceğini veya kötü amaçlı yazılımların cihazınızı taramanızı durdurabileceğini gösterir.
</tr><tr><td>Çözüm
</td>
<td>
<a href="https://www.microsoft.com/security/scanner/default.aspx">Microsoft Güvenlik Tarayıcısı</a> çalıştırın, ardından güvenlik yazılımınızı güncelleştirin ve yeniden deneyin.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508024 </th></tr>
<tr>
<td>İleti</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tam sistem taraması gerekebileceğini gösterir.
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
Bu hata, tehdit kaldırma işlemini tamamlamak için el ile adımlar gerektiğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
<a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">Microsoft Kötü Amaçlı Yazılımdan Koruma Ansiklopedisi'nde</a> açıklanan el ile düzeltme adımlarını izleyin. Olay geçmişinde tehdide özgü bir bağlantı bulabilirsiniz.<br/></td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508026
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, kapsayıcı türü içindeki kaldırma işleminin desteklenmeyebileceğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Microsoft Defender Virüsten Koruma, arşiv içinde algılanan tehditleri düzeltemiyor. Algılanan kaynakları el ile kaldırmayı göz önünde bulundurun.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508027
</th>
</tr><tr><td>İleti</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, düşük ve orta düzeydeki tehditlerin kaldırılmasının devre dışı bırakılabileceğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Algılanan tehditleri denetleyin ve gerektiği gibi çözün.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508029
</th>
</tr><tr><td>İleti</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, tehdidin yeniden taramasının gerekli olduğunu gösterir.
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
Bu hata, çevrimdışı tarama gerektiğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Çevrimdışı Microsoft Defender Virüsten Koruma çalıştırın. Bunun nasıl yapıldığını <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">çevrimdışı Microsoft Defender Virüsten Koruma makalesinde</a> okuyabilirsiniz.
</td>
</tr>
<tr>
<th colspan="2">Hata kodu: 0x80508031
</th>
</tr><tr><td>İleti</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Olası neden</td>
<td>
Bu hata, Microsoft Defender Virüsten Koruma platformun geçerli sürümünü desteklemediğini ve platformun yeni bir sürümünü gerektirdiğini gösterir.
</td></tr><tr><td>Çözüm</td><td>
Microsoft Defender Virüsten Koruma yalnızca Windows 10 ve Windows 11 kullanabilirsiniz. Windows 8, Windows 7 ve Windows Vista için <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">System Center Endpoint Protection</a> kullanabilirsiniz.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>aşağıdaki hata kodları, Microsoft Defender Virüsten Koruma iç testi sırasında kullanılır.

Bu hataları görürseniz [tanımları güncelleştirmeyi](manage-updates-baselines-microsoft-defender-antivirus.md) deneyebilir ve doğrudan uç noktada yeniden taramayı zorlayabilirsiniz.


<table>
<tr>
<th colspan="3">İç hata kodları</th>
</tr>
<tr>
<th><b>Hata kodu</b></th>
<th>İleti görüntüleniyor</th>
<th>Hata ve çözümün olası nedeni</th>
</tr>
<tr>
<td>
0x80501004
</td>
<td>
<b>ERROR_MP_NO_INTERNET_CONN </b>
</td>
<td>
İnternet bağlantınızı denetleyin ve taramayı yeniden çalıştırın.
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
Bu bir iç hatadır. Kötü amaçlı yazılım kaldırma işlemi başarılı olmadığında tetiklenebilir.
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
Bu bir iç hatadır. Tarama tamamlanamadıktan sonra tetiklenmiş olabilir.
</td>
</tr>
</table>

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)


## <a name="related-topics"></a>İlgili konular

- [Microsoft Defender Virüsten Koruma koruma raporu](report-monitor-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
