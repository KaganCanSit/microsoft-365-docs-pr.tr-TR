---
title: Temel Mobil Kullanım ve Güvenlik içinde cihaz güvenliği ilkeleri oluşturma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- MET150
description: Kuruluş bilginizi koruyan cihaz ilkeleri oluşturmak için Temel Mobil Kullanım ve Güvenlik'i kullanın.
ms.openlocfilehash: c0fa9cec0b9029d2cd55aace0c758e6c81e265b0
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018762"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Temel Mobil Kullanım ve Güvenlik içinde cihaz güvenliği ilkeleri oluşturma

Temel Mobil Kullanım ve Güvenlik'i kullanarak yetkisiz erişime karşı kuruluşla ilgili kuruluş Microsoft 365 ilkeler oluşturabilirsiniz. İlkeleri, cihazınızın kullanıcısı uygun bir mobil cihaz lisansına sahip olduğu ve cihazı Temel Mobil Microsoft 365 ve Güvenlik'e kaydettir olduğu tüm mobil cihazlara uygulayabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

> [!IMPORTANT]
> Mobil cihaz ilkesi oluşturmadan önce Temel Mobil Kullanım ve Güvenlik'i etkinleştirmeniz ve ayarlamanız gerekir. Daha fazla bilgi için bkz. Temel Hareketlilik ve Güvenlik'e Genel Bakış.

- Temel Mobil Kullanım ve Güvenlik tarafından destekleyen cihazlar, mobil cihaz uygulamaları ve güvenlik ayarları hakkında bilgi edinin. Bkz [. Temel Hareketlilik ve Güvenlik Özellikleri](capabilities.md).
- İlkeleri dağıtmak Microsoft 365 kullanıcıların ve bu kullanıcılara erişimin engellenmiş olarak dışında tutmak istediğiniz kullanıcılar için farklı güvenlik grupları Microsoft 365. Yeni bir ilkeyi organizasyona dağıtmadan önce, az sayıda kullanıcıya dağıtarak ilkeyi test uygulamanızı öneririz. Yalnızca kendinizi veya az sayıda kullanıcınızı içeren ve ilkeyi sizin için test Microsoft 365 bir güvenlik grubu oluşturabilir ve kullanabilirsiniz. Güvenlik grupları hakkında daha fazla bilgi edinmek için bkz [. Güvenlik grubu oluşturma, düzenleme veya silme](../email/create-edit-or-delete-a-security-group.md).
- Microsoft 365'te Temel Mobil Kullanım ve Güvenlik Microsoft 365 için genel yönetici Microsoft 365 gerekir. Daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'& bakın](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- İlkeleri dağıtmadan önce, Temel Hareketlilik ve Güvenlik'te bir cihaz kaydetmenin olası etkilerini organizasyona haber verirsiniz. İlkeleri nasıl ayar kullandığınıza bağlı olarak, uyumlu olmayan cihazların Microsoft 365'a ve yüklü uygulamalar, fotoğraflar ve kişisel bilgiler dahil olmak üzere kayıtlı bir cihaza erişimi engellenmiş olabilir ve veriler silinebilir.

> [!NOTE]
> Kişiler için Temel Mobil Kullanım ve Güvenlik içinde Microsoft 365 İş Standart ilkeler ve erişim Exchange ActiveSync yönetim merkezinde oluşturulmuş mobil cihaz posta kutusu ilkelerini ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">cihaz erişim Exchange geçersiz kılar</a>. Cihaz Microsoft 365 İş Standart için Temel Mobil Kullanım ve Güvenlik'e Exchange ActiveSync, cihaza uygulanan tüm mobil cihaz posta kutusu ilkesi veya cihaz erişim kuralı yoksayılır. Bu konuda daha fazla Exchange ActiveSync için bkz[. Exchange ActiveSync'da Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>1. Adım: Cihaz ilkesi oluşturma ve test grubuna dağıtma

Başlamadan önce Temel Hareketlilik ve Güvenlik'i etkinleştirdikten ve ayarlayın. Yönergeler için bkz. [Temel Hareketlilik ve Güvenlik'e Genel Bakış](overview.md).

1. Tarayıcınızdan, yazın <https://protection.office.com/devicev2>.

2. İlke **oluştur'a seçin**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Temel Mobil Kullanım ve Güvenlik ilkesi ayarları.":::

3. İlke **ayarları sayfasında** , kuruma uygulanan mobil cihazlara uygulanacak gereksinimleri belirtin.

4. **E-posta profilinin** yönetilmesini gerektirme: Etkinleştirildiğinde, Temel Hareketlilik ve Güvenlik ile yönetilen e-posta profili olmayan cihazlar uyumlu kabul edilir. Cihaz doğru hedefli değilken veya kullanıcı e-posta hesabını cihazda el ile ayarlamışsa, yönetilen bir e-posta profiline sahip değildir. Etkin Değil ( **varsayılan)** olarak bıraksanız, bu ayar uyumluluk veya uyumluluk dışı olarak değerlendirilmez. Kullanıcıların bu seçenek seçildiğinde uyumlu hale nasıl gelecek yönergeleri görmek için bkz [. Var olan bir e-posta hesabı bulundu](/intune-user-help/existing-company-email-account-found).

5. Bu **ilkeyi şimdi uygulamak istiyor musunuz?** sayfasında, bu ilkeyi uygulamak istediğiniz grupları seçin.

6. Bu **ilkeyi oluştur'a seçin**.

İlke, her kullanıcının cihazına ileri bir kez mobil cihaz kullanarak Microsoft 365 için geçerlidir. Kullanıcıların daha önce mobil cihazlarına uygulanmış bir ilke yoksa, siz ilkeyi dağıt sonrasında cihazlarında Temel Mobil Kullanım ve Güvenlik'i kaydetme ve etkinleştirme adımlarını içeren bir bildirim alırlar. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md). Intune Hizmeti tarafından barındırılan Temel Mobil Kullanım ve Güvenlik'te kaydı tamamlayana kadar e-postaya, OneDrive ve diğer hizmetlere erişim kısıtlanır. Intune Şirket Portalı uygulamasını kullanarak kaydı tamamlandıktan sonra, hizmetleri kullanabilirler ve ilke cihazlarına uygulanır.

## <a name="step-2-verify-that-your-policy-works"></a>2. Adım: İlkenizin çalıştığını doğrulama

Cihaz ilkesi oluşturduktan sonra, ilkenin kuruma dağıtmadan önce beklediğiniz gibi çalıştığını kontrol edin.

1. Tarayıcınızdan, yazın [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Yönetilen **cihazların listesini görüntüle'yi seçin**.
3. İlkenin uygulandığı kullanıcı cihazlarının durumunu kontrol edin. Cihazların **Durumunun** Yönetilsin **mi?**
4. Ayrıca, cihazı seçerek Fabrika sıfırlaması'nın veya Şirket verilerini Yönet'den kaldır düğmesini  tıklatarak da **cihazda tam veya** seçmeli temizleme özelliğini de sebilirsiniz. Yönergeler için bkz. [Mobil cihazı şu cihazda Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>3. Adım: İlkeyi organizasyonunıza dağıtma

Cihaz ilkesi oluşturduktan ve bu ilkenin beklendiği gibi çalıştığını doğruladıktan sonra, bunu organizasyona dağıtın.

1. Tarayıcı türünüzden: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Dağıtmak istediğiniz ilkeyi seçin ve Uygulanan **gruplar'ın** yanındaki **Düzenle'yi seçin.**
3. Eklemek istediğiniz grubu ara öğesini seçin ve Seç'e **tıklayın**.
4. Kapat **ve Ayarı** **Değiştir'i seçin.**
5. **İlkeyi Kapat** ve **Düzenle'yi seçin.**

İlke, her kullanıcının mobil cihazına ileri bir kez oturum açmaları için geçerlidir. bu ilke, Microsoft 365 cihazından oturum açması için geçerlidir. Kullanıcıların mobil cihazlarına uygulanmış bir ilke yoksa, cihazlarında Temel Mobil Kullanım ve Güvenlik için kaydolma ve etkinleştirme adımlarını dan yer alan bir bildirim alırlar. Kayıt işlemi tamamlandıktan sonra ilke cihaza uygulanır. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>4. Adım: Desteklenmeyen cihazlar için e-posta erişimini engelleme

Kuruluş bilgilerin güvenliğini sağlamak için Temel Mobil Kullanım ve Güvenlik tarafından Microsoft 365 mobil cihazlarda e-postanıza uygulama erişimini engellemeniz gerekir. Desteklenen cihazların listesi için bkz. [Desteklenen cihazlar](../../admin/basic-mobility-security/capabilities.md).

**Uygulama erişimini engellemek için:**

1. Tarayıcınızdan, yazın [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Kuruluş **genelindeki cihaz erişim ayarlarını yönet'i seçin**.
3. Desteklenmeyen cihazları engellemek için Cihaz, Mobil Cihazlar için **Temel** Mobil Kullanım ve Güvenlik tarafından desteklenmiyorsa **Engelle'yi seçin ve Microsoft 365 Kaydet'i** **seçin**.

   :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Temel Hareketlilik ve Güvenlik bloğu erişim seçeneği.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>5. Adım: Koşullu erişim denetimlerinden çıkarılacak güvenlik gruplarını seçme

Bazı kişilerin mobil cihazlarında koşullu erişim denetimlerini dışarıda tutmak istemiyorsanız ve bu kişiler için bir veya daha fazla güvenlik grubu oluşturduysanız, güvenlik gruplarını buraya ekleyin. Bu gruplarda yer alan kişilerin desteklenen mobil cihazları için zorunlu ilkeleri olmayacaktır. Bu seçenek, artık kurumda Temel Mobil Kullanım ve Güvenlik kullanmak istemiyorsanız önerilir.

1. Tarayıcınızdan, yazın [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Kuruluş **genelindeki cihaz erişim ayarlarını yönet'i seçin**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Temel Hareketlilik ve Güvenlik bir ilke seçeneği oluşturun.":::

3. **Dışlamak** istediğiniz kullanıcıların erişimlerini engellemek istediğiniz güvenlik grubunu eklemek için Ekle'yi Microsoft 365. Kullanıcı bu listeye ekli olduğunda, desteklenmeyen bir cihaz Microsoft 365 e-postayla veya e-postayla oturum aya erişim sağlar.

4. Grup seçin panelinde kullanmak istediğiniz güvenlik **grubunu** seçin.

5. Adı seçin ve sonra Da **Ekle'yi** >  **seçin**.

6. Kuruluş genelinde **cihaz erişimi ayarları panelinde Kaydet'i** **seçin**.

   :::image type="content" source="../../media/basic-mobility-security/bms-8-allow-access.png" alt-text="Temel Hareketlilik ve Güvenlik izin ver erişim seçeneği.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Farklı cihaz türlerinde güvenlik ilkelerinin etkileri nedir?

Kullanıcı cihazlarına ilkeyi uygulasanız bile, her cihazın üzerindeki etkisi cihaz türleri arasında bir değişiklik gösterir. İlkelerin farklı cihazlar üzerindeki etkisiyle ilgili örnekler için aşağıdaki tabloya bakın.

|**Güvenlik İlkesi**|**Android 4 ve sonrası**|**Samsung KNOX**|**iOS 6 ve sonrası**|**Notlar**|
|:-----|:-----|:-----|:-----|:-----|
|Şifreli yedekleme gerektir|Hayır|Evet|Evet|iOS şifreli yedekleme gereklidir.|
|Bulut yedeklemeyi engelle|Evet|Evet|Evet|iOS'ta Android'de Google yedeklemesini (gri renkte), bulut yedeklemesini engelle.|
|Belge eşitlemesini engelleme|Hayır|Hayır|Evet|iOS: Buluttaki belgeleri engelin.|
|Fotoğraf eşitlemeyi engelleme |Hayır|Hayır|Evet|iOS (yerel): Fotoğraf Akışını Engelle.|
|Ekran yakalamayı engelle |Hayır|Evet|Evet|Denenenler engellenmiş.|
|Görüntülü konferansı engelleme |Hayır|Hayır|Evet|FaceTime iOS'ta engellenir, Skype üzerinde engellenir.|
|Tanılama verilerini göndermeyi engelleme |Hayır|Evet|Evet|Android'de Google kilitlenme raporu göndermeyi engelin.|
|Uygulama mağazasına erişimi engelleme |Hayır|Evet|Evet|Android giriş sayfasında App Store simgesi yok, Windows, iOS'ta yok.|
|Uygulama mağazası için parola gerektir |Hayır|Hayır|Evet|iOS: iTunes satın almaları için parola gereklidir.|
|Çıkarılabilir depolama alanına bağlantıyı engelleme |Hayır|Evet|Yok|Android: Ayarlarda SD kart gri görünür Windows kullanıcıya haber verin, yüklü uygulamalar kullanılamıyor|
|Bağlantı Bluetooth engelleme |Notlara bakın|Notlara bakın|Evet|Android'de bir ayar olarak BlueTooth'u devre dışı bırakaaaz. Bunun yerine, BlueTooth gerektiren tüm işlemleri devre dışı bırakıırk: Gelişmiş Ses Dağıtımı, Ses/Görüntü Uzaktan Denetim, eller serbest cihazlar, kulaklık, Telefon Kitap Erişimi ve Seri Bağlantı Noktası. Bunlardan biri kullanılırken, sayfanın en altında küçük bir konuşma iletisi görüntülenir.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>İlkeyi silemez veya kullanıcı ilkeden kaldırırken ne olur?

İlkeyi silseniz veya ilkenin dağıtıldığı gruptan bir kullanıcı kaldırsanız, ilke ayarları Microsoft 365 e-posta profili ve önbelleğe alınmış e-postalar kullanıcının cihazından kaldırılabilir. Farklı cihaz türlerinde nelerin kaldırıldığına bakın.

|**Kaldırılanlar**|**iOS 6 ve sonrası**|**Android 4 ve sonrası (Samsung KNOX dahil)**|
|:-----|:-----|:-----|
|Yönetilen e-posta <sup>profilleri1</sup>|Evet|Hayır|
|Bulut yedeklemeyi engelle|Evet|Hayır|

<sup>1</sup> İlke, E-posta profili yönetiliyor seçeneğiyle dağıtılmışsa, yönetilen e-posta profili ve bu profilde önbelleğe alınan e-postalar kullanıcı cihazından silinir.

İlke, her kullanıcı için mobil cihazdan kaldırılır. İlke, cihazı Basic Mobility and Security ile bir sonraki sefer denetlerken geçerli olur. Bu kullanıcı cihazlarına uygulanan yeni bir ilkenin dağıtımında, bu cihazlarda Temel Hareketlilik ve Güvenlik'e yeniden kaydolmaları istenir.

Ayrıca, cihazı tamamen temiz veya kuruluş bilgilerini cihazdan seçmeli olarak temizebilirsiniz. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'te mobil cihazı temizleme](wipe-mobile-device.md).

## <a name="related-content"></a>İlgili içerik

[Temel Hareketlilik ve Güvenlik'e Genel Bakış](overview.md) (makale)\
[Temel Hareketlilik ve Güvenlik Özellikleri](capabilities.md) (makale)