---
title: Koruyucuları bir vakaya Advanced eDiscovery aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Bir vakaya hızla çeşitli koruyucular ve ilişkili veri kaynaklarını hızla eklemek için toplu içeri aktarma aracını Advanced eDiscovery.
ms.openlocfilehash: f02745f8eb9dff2ce54d128d967486b0dd9cbc7a
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63405986"
---
# <a name="import-custodians-to-an-advanced-ediscovery-case"></a>Koruyucuları bir vakaya Advanced eDiscovery aktarma

Birçok Advanced eDiscovery koruyucu içeren diğer durumlarda, bir vakaya eklemek için gerekli bilgileri içeren bir CSV dosyası kullanarak birden çok koruyucuları bir kerede içeri aktarabilirsiniz. İçeri aktarma koruyucu aracı, içeri aktarma işi oluşturulmadan önce CSV dosyasını da doğrular. Bu, içeri aktarma işinin tamamlandıktan sonra bir özel dosya eklinin eklenmesini engelleyen hatalar olduğunu öğrenmek için beklemek yerine CSV dosyasındaki tüm hataları düzeltebilirsiniz.

## <a name="before-you-import-custodians"></a>Koruyucuları içeri aktarmadan önce

- CSV dosyası başına en çok 1.000 koruyucu (satır) içeri aktarabilirsiniz.

- Her custo ortak için en fazla 500 veri kaynağı ilişkilendirilebilirsiniz.  

- Yalnızca, kuruluş kuruluşlarının parçası olan koruyucuları içeri Azure Active Directory.

- Her koruyucu, benzersiz bir e-posta adresine sahip olmalıdır.

- Etkin olmayan bir posta kutusunu özel kişi olarak içeri aktararak veya etkin olmayan bir posta kutusunu başka bir özel kişi ile ilişkilendirmek için, etkin olmayan posta kutusunun e-posta adresine bir "." öneki ekleyin (örneğin, .sarad@contoso.onmmicrosoft.com).

## <a name="import-custodians"></a>Koruyucuları içeri aktarma

1. Büyük/Advanced eDiscovery açın ve Veri **kaynakları sekmesini** seçin.

2. Veri **kaynağı ekleEkleçleri** >  **sınırla'ya tıklayın**.

3. Şablon al **sihirbazı sayfasında** , özel şablon **CSV dosyasını** indirmek için CSV şablonunu indir'e tıklayın.

   ![Koruyucuları içeri aktarma sayfasından bir CSV şablonu indirin.](../media/ImportCustodians1.png)

4. ÖZEL bilgileri CSV dosyasına ekleyin ve yerel bilgisayarınıza kaydedin. CSV [dosyasındaki gerekli özellikler hakkında ayrıntılı bilgi için Custo csv](#custodian-csv-file) dosyası bölümüne bakın.

5. CSV dosyasını özel kişi bilgileriyle hazır açtıktan sonra,  >  Veri kaynakları sekmesine geri gidin ve Veri  kaynağı **ekleM custod bilgilerini** yeniden içeri aktar'a tıklayın.

6. **CSV Upload sihirbazı** sayfasında, Csv Upload tıklayın ve custo cust  (özel dosya) bilgilerini içeren CSV dosyasını karşıya yükleyin.

   SIZ CSV dosyasını karşıya yükledikten sonra, içeri aktarma sihirbazı CSV dosyasını doğrular. Doğrulama hatası varsa, sihirbaz hataları görmek için bağlantı içeren bir hata başlığı görüntüler.

   ![Daha fazla bilgi bağlantısı içeren doğrulama hatası başlığı.](../media/ImportCustodians2.png)

   Hata bilgileri hatayı içeren hücrenin satır ve sütununu tanımlar ve bir düzeltme eylemi önerir. Herhangi bir doğrulama hatasını düzeltmeli ve sabit CSV dosyasını yeniden yükleyesiniz. İçeri aktarma koruyucu işini oluşturamadan önce CSV dosyasının başarıyla doğrulanması gerekir.

7. CSV dosyası doğrulandıktan sonra İleri'ye **tıklayın ve sonra** içeri aktarma işini **başlatmak için** İçeri Aktar'a tıklayın.

İçeri aktarma işini başladıktan sonra, Advanced eDiscovery şunları yapar:

- Vakanın İş **sekmesinde BulkAddCusto ötele** **adlı** bir iş oluşturur.

- Her custo veri kaynağı için Gelişmiş dizin oluşturma işlemi gerçekleştirir.

- Tüm custo custo **ve data sources (CSV dosyasındaki Is OnHold** özelliği TRUE olarak ayarlanmışsa)

İçeri aktarma koruyucu işi tamamlandığında, koruyucular ve ilişkili veri kaynakları, vakanın **Veri** kaynakları sayfasına eklenir.

## <a name="custodian-csv-file"></a>Custo bir CSV dosyası

CSV koruyucu şablonunu indirdikten sonra, her satıra koruyucuları ve bunların veri kaynaklarını indirebilirsiniz. Üst bilgi satırdaki sütun adlarını değiştirmeyebilirsiniz. Diğer veri kaynaklarını bir özel dosyayla ilişkilendirmek için iş yükü türü ve iş yükü konumu sütunlarını kullanın.

| Sütun adı|Açıklama|
|:------- |:------------------------------------------------------------|
|**Custo custo custo custemail**     |Custo bir UPN e-posta adresi. Örneğin, sarad@contoso.onmicrosoft.com.           |
|**Exchange Etkin** | Custo posta kutusunu eklemek veya dahil etmek için DOĞRU/YANLIŞ değeri.      |
|**OneDrive Etkin** | Custo OneDrive İş hesabını eklemek veya içermeyen için DOĞRU/YANLIŞ değeri. |
|**Is OnHold**        | Koruyucu veri kaynaklarının yerinde basılı olup olmadığını göstermek için DOĞRU/YANLIŞ değeri. <sup>1</sup>     |
|**workload1 tür**         |Custo ortak veri kaynağı türünü belirten dize değeri. Olası değerler şunlardır: <br/>- ExchangeMailbox<br/> - SharePointSitesi<br/>- <sup>TeamsMailbox2</sup><br/>- <sup>YammerMailbox2</sup>. Bu iş yükü türlerinin önceki değerleri büyük/harfe duyarlıdır. CSV dosyası, üç iş yükü türüyle bunların ilgili iş yükü konumlarının sütunlarını içerir. Toplam 500 iş yükü türü ve konumu  ekleyebilirsiniz.|
|**Workload1 Location**     | İş yükünüz bağlı olarak, veri kaynağının konumu bu olur. Örneğin, bir posta kutusunun e-Exchange adresi veya posta kutusunun URL'si SharePoint olabilir. |
|||

> [!NOTE]
> <sup>1 Bir</sup> durumda 1.000'den fazla posta kutusunu veya 100 siteyi ayrı tutarsanız, sistem eBulma tutma için gereken ölçeklendirmeyi otomatik olarak sağlar. Bu da, sistemin veri konumlarını tek bir ilkeye eklemek yerine otomatik olarak birden çok tutma ilkesine ekli olduğu anlamına gelir. Bununla birlikte, kuruluş başına 10.000 vaka tutma politikası sınırı yine de geçerlidir. Tutma sınırları hakkında daha fazla bilgi için bkz. Tutma [Advanced eDiscovery](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> CSV dosyasına TeamsMailbox ve YammerMailbox iş yüklerini dahil edersiniz, grup sitesi (Ekip Sitesi ve Yammer Sitesi) varsayılan olarak otomatik olarak eklenir. CSV dosyasında TeamsSite ve YammerSitesi'i ayrı olarak belirtmeniz gerekmez.

Aşağıda, koruyucu bilgileri olan bir CSV dosyası örneği ve şöyledir:<br/><br/>

|Custo custo custo custemail      | Exchange Etkin | OneDrive Etkin | Is OnHold | workload1 tür | Workload1 Location             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | SharePointSitesi | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | |  |
|.johnj@contoso.onmicrosoft.com|TRUE|TRUE|TRUE||
|sarad@contoso.onmicrosoft.com|TRUE|TRUE|TRUE|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Daha önce de belirtildiği gibi, etkin olmayan bir posta kutusunu custo custoactive olarak içeri aktaracak veya etkin olmayan bir posta kutusunu başka bir custo ortak yapmak için etkin olmayan posta kutusunun UPN adresine bir "." öneki ekleyin.
