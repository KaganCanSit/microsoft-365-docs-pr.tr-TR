---
title: kullanım etkinliği raporlarını Microsoft 365 yönetim merkezi Teams
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Microsoft Teams kullanım etkinliği raporunu almayı ve kuruluşunuzdaki Teams etkinliği hakkında içgörüler elde etmeyi öğrenin.
ms.openlocfilehash: 93bcb5d1e6c8d0e3bbb96671333bff1c6b7b429f
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781697"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-usage-activity"></a>Yönetim merkezinde raporları Microsoft 365 - kullanım etkinliği Microsoft Teams

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.

Yepyeni **Teams kullanım raporu**, kuruluşunuz genelinde kaç kullanıcının iletişim kurmak ve işbirliği yapmak için Teams kullandığını hızla görebilmeniz için etkin kullanıcı, kanal ve ileti sayısı dahil olmak üzere Teams'daki kullanım etkinliğine genel bir bakış sağlar.  Ayrıca etkin konuk sayısı, toplantılar ve iletiler gibi diğer Teams belirli etkinlikleri de içerir.

![Microsoft 365 raporları - etkinlik raporu Microsoft Teams.](../../media/teams-usage.png)

## <a name="how-to-get-to-the-microsoft-teams-usage-activity-report"></a>Microsoft Teams kullanım etkinliği raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. Pano giriş sayfasında, **Microsoft Teams etkinlik** kartındaki **Daha fazla görüntüle** düğmesine tıklayın.

   ![Microsoft 365 raporları - etkinlik kartı Microsoft Teams.](../../media/teams-usage-card.png)<br/>

3. **Microsoft Teams** raporlar sayfasında **, Teams Kullanımı** sekmesini seçin.

## <a name="interpret-the-microsoft-teams-usage-activity-report"></a>Microsoft Teams kullanım etkinliği raporunu yorumlama

Teams **Kullanımı** sekmesini seçerek Teams raporundaki kullanıcı etkinliğini görüntüleyebilirsiniz. Bu, aşağıdaki grafikleri görüntüler:

- **Kanal kullanımı**: Zaman içinde etkinlik türüne göre kanal kullanım sayısını izler.

  ![Teams kullanım etkinliği raporu - kanal kullanımı.](../../media/teams-usage-channel.png)

- **Ekip kullanımı**: Ekip sayısını zaman içinde türe ve etkinliğe göre izler.

  ![Teams kullanım etkinliği raporu - ekip kullanımı.](../../media/teams-usage-usage.png)

Ayrıca grafikte son etkinlik tarihi, etkin kullanıcılar, etkin kanallar ve diğer veriler gibi tek tek ekiplerin kullanım ayrıntıları yer alır.

![Microsoft 365 raporları - kullanım etkinliği tablosu Microsoft Teams.](../../media/teams-usage-table.png)

Raporda sütun eklemek veya rapordan sütun kaldırmak için tabloda Sütunları **seç'i** seçin.

![Kullanım etkinliği raporunu Teams - sütunları seçin.](../../media/teams-usage-columns.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. **Ses süresi**, **video süresi** ve **ekran paylaşım süresi** için dışarı aktarılan biçim ISO8601 süre biçimini izler.

**Microsoft Teams kullanım etkinliği** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.

Veri kalitesini sağlamak için son üç güne ilişkin günlük veri doğrulama denetimleri gerçekleştiriyoruz ve algılanan boşlukları dolduracağız. İşlem sırasında geçmiş verilerde farklılıklar fark edebilirsiniz.

> [!Important]
> Belirli bir güne ilişkin veriler 48 saat içinde gösterilir. Örneğin, 10 Ocak verileri 12 Ocak'a kadar raporda görünmelidir.

### <a name="channel-usage-metrics"></a>Kanal kullanım ölçümleri

Kanal kullanım grafiğinde aşağıdaki ölçümlerle ilgili veriler gösterilir.

|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Etkin kanal kullanıcıları|Bu, iç etkin kullanıcıların, etkin konukların ve dış etkin kullanıcıların toplamıdır.  <br/><br/> **İç etkin kullanıcılar** - Belirtilen zaman aralığında en az bir panel eylemi olan kullanıcılar. Bu, konukları hariç tutar.   <br/> **Etkin konuklar** - Belirtilen zaman aralığında en az bir panel eylemi olan konuklar. Konuk, kuruluşunuzun dışından gelen ve dizinimdeki bir konuk hesabında oturum açarak paylaşılan kaynaklara erişen kişidir.  <br/> **Dış etkin kullanıcı** - Belirtilen zaman aralığında en az bir panel eylemi olan dış katılımcılar. Dış katılımcı, kuruluşunuzun dışından gelen ve dizininizdeki bir konuk hesabını değil kendi kimliğini kullanarak paylaşılan kanal gibi bir kaynağa katılan kişidir.|
|Etkin kanallar|Belirtilen zaman aralığında en az bir etkin kullanıcısı olan etkin ekiplerde geçerli kanallar. Buna genel, özel veya paylaşılan kanallar dahildir.|
|Kanal iletileri|Kullanıcının belirtilen zaman aralığında özel bir sohbette yayınladığı benzersiz iletilerin sayısı.|

### <a name="team-usage-metrics"></a>Ekip kullanım ölçümleri

Teams kullanım grafiğinde aşağıdaki ölçümlerle ilgili veriler gösterilir.

|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Özel ekipler|Etkin veya etkin olmayan özel bir ekip.|
|Genel ekipler|Etkin veya etkin olmayan genel bir ekip.|
|Etkin özel ekipler|Özel ve etkin bir ekip.|
|Etkin genel ekipler|Genel ve etkin bir ekip.|

### <a name="teams-details"></a>Teams ayrıntıları

Aşağıdaki ölçümlere ilişkin veriler tek tek ekipler tarafından kullanılabilir.

|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Ekip Kimliği|Ekip tanımlayıcısı|
|İç etkin kullanıcılar|Belirtilen zaman aralığında konuklar da dahil olmak üzere en az bir panel eylemi olan kullanıcılar. <br/> <br/> Aynı kiracıda bulunan iç kullanıcılar ve konuklar. dahili kullanıcılar konukları hariç tutar.|
|Etkin konuklar|Belirtilen zaman aralığında en az bir panel eylemi olan konuklar. <br/> <br/> Konuk, kuruluşunuz dışından gelen ve dizinimdeki bir konuk hesabında oturum açarak paylaşılan kaynaklara erişen kişiler olarak tanımlanır.|
|Dış etkin kullanıcılar|Belirtilen zaman aralığında en az bir panel eylemi olan dış katılımcılar.<br/><br/> Dış katılımcı, dizininizdeki konuk hesabını değil kendi kimliğini kullanarak kuruluşunuzun dışından bir kaynağa (paylaşılan kanal gibi) katılan bir kişi olarak tanımlanır.|
|Etkin kanallar|Belirtilen zaman aralığında en az bir etkin kullanıcısı olan etkin ekiplerde geçerli kanallar. Buna genel, özel veya paylaşılan kanallar dahildir.|
|Etkin paylaşılan kanallar|Belirtilen zamanda en az bir etkin kullanıcısı olan etkin ekiplerde geçerli paylaşılan kanallar. <br/> <br/>Paylaşılan kanal, ekip dışındaki kişilerle paylaşılabilen bir Teams kanalı olarak tanımlanır. Bu kişiler kuruluşunuzun içinde veya diğer Azure AD kuruluşlarından olabilir.|
|Toplam düzenli toplantı sayısı|Kullanıcının belirtilen süre boyunca düzenlediği tek seferlik zamanlanmış, yinelenen, geçici ve sınıflandırılmamış toplantıların toplamı.|
|Mesaj|Belirtilen zaman aralığındaki kanallardaki tüm posta iletilerinin sayısı.|
|Yanıt|Belirtilen zaman aralığındaki kanallardaki tüm yanıt iletilerinin sayısı.|
|Bahs -eder|Belirtilen zaman aralığında yapılan tüm bahsetmelerin sayısı.|
|Reaksiyon|Etkin bir kullanıcının belirtilen zaman aralığında yaptığı tepkilerin sayısı.|
|Acil iletiler|Belirtilen zaman aralığındaki acil iletilerin sayısı.|
|Kanal iletileri|Kullanıcının belirtilen zaman aralığında bir ekip sohbetinde yayınladığı benzersiz iletilerin sayısı.|
|Son etkinlik tarihi|Ekibin herhangi bir üyesinin bir eylem oluşturduğunuzda en son tarih.|

## <a name="make-the-user-specific-data-anonymous"></a>Kullanıcıya özgü verileri anonim hale getirme

Teams kullanıcı etkinlik raporundaki verileri anonim hale getirmek için genel yönetici olmanız gerekir. Bu, rapordaki görünen ad, e-posta ve Azure Active Directory Nesne Kimliği gibi tanımlanabilir bilgileri (MD5 karmalarını kullanarak) ve bunların dışarı aktarmasını gizler.

1. Microsoft 365 yönetim merkezi **Ayarlar** **Org Ayarlar** >  gidin ve **Hizmetler** sekmesinin altında **Raporlar'ı** seçin.

2. **Raporlar'ı** ve ardından **Anonim tanımlayıcıları görüntüle'yi** seçin. Bu ayar hem Microsoft 365 yönetim merkezi hem de Teams yönetim merkezindeki kullanım raporlarına uygulanır.

3. **Değişiklikleri kaydet'i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

[cihaz kullanım raporunu Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[kullanıcı etkinlik raporunu Microsoft Teams](../activity-reports/microsoft-teams-user-activity-preview.md)
