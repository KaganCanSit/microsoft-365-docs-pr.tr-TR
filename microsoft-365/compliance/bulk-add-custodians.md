---
title: Koruyucuları eBulma (Premium) olayına aktarma
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
description: Microsoft Purview eKeşif'teki (Premium) bir olaya hızla birden çok koruyucu ve ilişkili veri kaynağı eklemek için toplu içeri aktarma aracını kullanın.
ms.openlocfilehash: 7913c8674dc5560539196f34e323f05955a6850e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64950367"
---
# <a name="import-custodians-to-an-ediscovery-premium-case"></a>Koruyucuları eBulma (Premium) olayına aktarma

Birçok koruyucu içeren Microsoft Purview eKeşif (Premium) vakalarında, bir servis talebine eklemek için gerekli bilgileri içeren bir CSV dosyası kullanarak birden çok koruyucuyu aynı anda içeri aktarabilirsiniz. İçeri aktarma koruyucuları aracı, içeri aktarma işi oluşturulmadan önce CSV dosyasını da doğrular. Bu, bir koruyucunun olaya eklenmesini engelleyen hatalar olduğunu öğrenmeden önce içeri aktarma işinin tamamlanmasını beklemek yerine CSV dosyasındaki hataları düzeltebileceğiniz anlamına gelir.

## <a name="before-you-import-custodians"></a>Koruyucuları içeri aktarmadan önce

- CSV dosyası başına en fazla 1.000 koruyucu (satır) içeri aktarabilirsiniz.

- Her koruyucu için en fazla 500 veri kaynağı ilişkilendirebilirsiniz.  

- Yalnızca kuruluşunuzun Azure Active Directory parçası olan koruyucuları içeri aktarabilirsiniz.

- Her koruyucu benzersiz bir e-posta adresine sahip olmalıdır.

- Etkin olmayan bir posta kutusunu koruyucu olarak içeri aktarmak veya etkin olmayan bir posta kutusunu başka bir koruyucuyla ilişkilendirmek için, etkin olmayan posta kutusunun e-posta adresine bir "." ön eki ekleyin (örneğin, .sarad@contoso.onmmicrosoft.com).

## <a name="import-custodians"></a>Koruyucuları içeri aktarma

1. eBulma (Premium) servis talebini açın ve **Veri kaynakları** sekmesini seçin.

2. **Veri kaynağı** >  **ekleKaynakları içeri aktar'a** tıklayın.

3. **Şablon alma** sihirbazı sayfasında **CSV şablonunu indir'e** tıklayarak bir koruyucu şablonu CSV dosyası indirin.

   ![Koruyucuları içeri aktar açılır sayfasından bir CSV şablonu indirin.](../media/ImportCustodians1.png)

4. Koruyucu bilgileri CSV dosyasına ekleyin ve yerel bilgisayarınıza kaydedin. CSV dosyasındaki gerekli özellikler hakkında ayrıntılı bilgi için [Koruyucu CSV dosyası](#custodian-csv-file) bölümüne bakın.

5. Csv dosyasını koruyucu bilgileriyle birlikte hazırladıktan sonra **Veri kaynakları** sekmesine dönün ve Veri kaynağı  > **ekleYeniden** **koruyucuları** içeri aktar'a tıklayın.

6. **Upload CSV dosyası** sihirbazı sayfasında, **Upload csv dosyasına** tıklayın ve ardından koruyucu bilgilerini içeren CSV dosyasını karşıya yükleyin.

   CSV dosyasını karşıya yükledikten sonra içeri aktarma sihirbazı CSV dosyasını doğrular. Doğrulama hataları varsa sihirbaz, hataları görüntülemek için bir bağlantı içeren bir hata başlığı görüntüler.

   ![Daha fazla bilgi için bağlantı içeren doğrulama hatası başlığı.](../media/ImportCustodians2.png)

   Hata bilgileri, hatayı içeren hücrenin satırını ve sütununu tanımlar ve bir düzeltme eylemi önerir. Doğrulama hatasını düzeltmeniz ve ardından sabit CSV dosyasını yeniden yüklemeniz gerekir. İçeri aktarma koruyucu işini oluşturabilmeniz için ÖNCE CSV dosyasının başarıyla doğrulanması gerekir.

7. CSV dosyası başarıyla doğrulandıktan sonra, içeri aktarma işini başlatmak için **İleri'ye** ve ardından **İçeri Aktar'a** tıklayın.

İçeri aktarma işini başlattıktan sonra eBulma (Premium) aşağıdakileri yapar:

- Servis talebinin **İşler** sekmesinde **BulkAddCustodian** adlı bir iş oluşturur.

- Her koruyucu için tüm veri kaynaklarının Gelişmiş dizinlemesini gerçekleştirir.

- Tüm koruyucu veri kaynaklarını beklemeye alır (CSV dosyasındaki **Is OnHold** özelliği TRUE olarak ayarlandıysa)

İçeri aktarma koruyucu işi tamamlandığında, koruyucular ve ilişkili veri kaynakları olayın **Veri kaynakları** sayfasına eklenir.

## <a name="custodian-csv-file"></a>Koruyucu CSV dosyası

CSV koruyucu şablonunu indirdikten sonra, her satıra koruyucuları ve veri kaynaklarını ekleyebilirsiniz. Üst bilgi satırındaki sütun adlarını değiştirmediğinizden emin olun. Diğer veri kaynaklarını bir koruyucuyla ilişkilendirmek için iş yükü türü ve iş yükü konumu sütunlarını kullanın.

| Sütun adı|Açıklama|
|:------- |:------------------------------------------------------------|
|**Koruyucu kişiEmail**     |Koruyucunun UPN e-posta adresi. Örneğin, sarad@contoso.onmicrosoft.com.           |
|**Exchange Etkin** | Koruyucunun posta kutusunu dahil etmek veya eklememek için DOĞRU/YANLIŞ değeri.      |
|**OneDrive Etkin** | Koruyucunun OneDrive İş hesabını dahil etmek veya eklememek için DOĞRU/YANLIŞ değeri. |
|**Is OnHold**        | Koruyucu veri kaynaklarının beklemeye alıp almayacağını belirten DOĞRU/YANLIŞ değeri. <sup>1</sup>     |
|**İş Yükü1 Türü**         |Koruyucu ile ilişkilendirilecek veri kaynağının türünü gösteren dize değeri. Olası değerler şunlardır: <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- <sup>TeamsMailbox2</sup><br/>- <sup>YammerMailbox2</sup>. Bu iş yükü türleri için önceki değerler büyük/küçük harfe duyarlıdır. CSV dosyası üç iş yükü türüne ve karşılık gelen iş yükü konumlarına yönelik sütunlar içerir. Toplam 500 iş yükü türü ve konumu ekleyebilirsiniz.|
|**İş Yükü1 Konumu**     | İş yükü türünüze bağlı olarak, bu veri kaynağının konumudur. Örneğin, bir Exchange posta kutusunun e-posta adresi veya bir SharePoint sitesinin URL'si. |
|||

> [!NOTE]
> <sup>1</sup> Bir durumda 1.000'den fazla posta kutusu veya 100 siteyi beklemeye alırsanız, sistem eBulma saklamayı gerektiği gibi otomatik olarak ölçeklendirir. Bu, sistemin veri konumlarını tek bir ilkeye eklemek yerine otomatik olarak birden çok ayrı tutma ilkesine eklediği anlamına gelir. Ancak, kuruluş başına 10.000 servis talebi saklama ilkesi sınırı hala geçerlidir. Tutma sınırları hakkında daha fazla bilgi için bkz. [eBulma sınırları (Premium)](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> CSV dosyasına TeamsMailbox ve YammerMailbox iş yüklerini eklediğinizde, grup sitesi (TeamSite ve YammerSite) varsayılan olarak otomatik olarak eklenir. CSV dosyasında TeamsSite ve YammerSite'yi ayrı olarak belirtmeniz gerekmez.

İşte, koruyucu bilgileri içeren bir CSV dosyası örneği:<br/><br/>

|Koruyucu kişiEmail      | Exchange Etkin | OneDrive Etkin | Is OnHold | İş Yükü1 Türü | İş Yükü1 Konumu             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | |  |
|.johnj@contoso.onmicrosoft.com|TRUE|TRUE|TRUE||
|sarad@contoso.onmicrosoft.com|TRUE|TRUE|TRUE|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Daha önce açıklandığı gibi, etkin olmayan posta kutusunu koruyucu olarak içeri aktarmak veya etkin olmayan bir posta kutusunu başka bir koruyucuyla ilişkilendirmek için etkin olmayan posta kutusunun UPN adresine bir "." ön eki ekleyin.
