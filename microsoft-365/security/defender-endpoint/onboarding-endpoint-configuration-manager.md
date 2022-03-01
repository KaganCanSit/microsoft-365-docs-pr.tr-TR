---
title: Microsoft Endpoint Configuration Manager kullanarak işe Microsoft Endpoint Configuration Manager
description: Microsoft Endpoint Configuration Manager kullanarak Uç Nokta için Microsoft Defender'a nasıl Microsoft Endpoint Configuration Manager
keywords: ekleme, yapılandırma, dağıtma, dağıtım, uç nokta yapılandırma yöneticisi, Uç nokta için Microsoft Defender, koleksiyon oluşturma, uç nokta algılama yanıtı, yeni nesil koruma, saldırı yüzeyini azaltma, microsoft uç nokta yapılandırma yöneticisi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a4668969982563bdc050a8e71b00980d52a7e6ff
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998225"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager kullanarak işe Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu makale, Dağıtım kılavuzunda yer almaktadır ve örnek bir ekleme yöntemi olarak hareket almaktadır.

Planlama [başlığında](deployment-strategy.md) , cihazları hizmete eklemeye için çeşitli yöntemler sağlanmıştır. Bu konu birlikte yönetim mimarisini kapsar.

![Yerel bulut mimarisi görüntüsü.](images/co-management-architecture.png)
 *Ortam mimarisi diyagramı*

Uç Nokta için Defender çeşitli uç noktaların ve araçların onboarding'i destekler ama bu makale bunları desteklemez. Diğer desteklenen dağıtım araçları ve yöntemleri kullanılarak genel ekleme hakkında bilgi için bkz. [Eklemeye genel bakış](onboarding.md).

Bu konu başlığı, kullanıcıları şu konuda yönlendirmektedir:

- 1. Adım: Windows cihazları hizmete ekleme
- 2. Adım: Defender'ı Uç nokta özellikleri için yapılandırma

Bu ekleme kılavuzu, bu kılavuzu kullanırken atılması gereken aşağıdaki temel Microsoft Endpoint Configuration Manager:

- **Web'de koleksiyon Microsoft Endpoint Configuration Manager**
- **Microsoft Endpoint Configuration Manager kullanarak Uç Nokta özellikleri için Microsoft Defender'ı Microsoft Endpoint Configuration Manager**

> [!NOTE]
> Bu Windows dağıtımda yalnızca bu cihazlar ele amektedir.

## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>1. Adım: Windows kullanarak cihazları Microsoft Endpoint Configuration Manager

### <a name="collection-creation"></a>Koleksiyon oluşturma

Yeni Windows cihazlara Microsoft Endpoint Configuration Manager için, dağıtım var olan bir koleksiyonu hedef alan veya test amacıyla yeni bir koleksiyon oluşturulabilir.

Grup ilkesi veya el ile yöntem gibi araçların kullanımı, sisteme hiçbir aracı yüklemez.

Oyun Microsoft Endpoint Configuration Manager konsolda ekleme işlemi, konsol içindeki uyumluluk ayarlarının bir parçası olarak yapılandırılır.

Bu gerekli yapılandırmayı alan tüm sistem, Configuration Manager istemcisi bu ilkeyi yönetim noktasından almaya devam ettiği sürece bu yapılandırmayı sürdürür.

Microsoft Endpoint Configuration Manager kullanarak uç noktaları ekleme için aşağıdaki Microsoft Endpoint Configuration Manager.

1. Uygulama Microsoft Endpoint Configuration Manager Varlıklara ve **Uyumluluğuna Genel Bakış Cihaz \> Koleksiyonlarına \> gidin**.

    ![Sihirbazın Microsoft Endpoint Configuration Manager görüntüsü1.](images/configmgr-device-collections.png)

2. Cihaz **Koleksiyonu'ne sağ tıklayın** ve Cihaz Koleksiyonu **Oluştur'u seçin**.

    ![Sihirbaz2 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-create-device-collection.png)

3. Bir Ad **ve Sınırlama** **Koleksiyonu girin,** ardından Sonraki'yi **seçin**.

    ![Sihirbaz3 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-limiting-collection.png)

4. Kural **Ekle'yi ve** sonra Sorgu **Kuralı'nı seçin**.

    ![Sihirbaz4 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-query-rule.png)

5. Doğrudan **Üyelik** **Sihirbazı'nda Sonraki'ne tıklayın ve** sorgu deyimini **düzenle'ye tıklayın**.

     ![Sihirbaz5 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-direct-membership.png)

6. **Ölçütler'i** seçin ve ardından yıldız simgesini seçin.

     ![Sihirbaz6'nın Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-criteria.png)

7. Ölçüt türünü basit değer olarak **tutmak için İşletim** Sistemi **-** derleme numarası, **14393'e** eşit veya daha büyük olan işleç ve Tamam'a **tıklayın**.

    ![Sihirbaz7 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-simple-value.png)

8. **Sonraki'yi ve** **Kapat'ı seçin**.

    ![Sihirbaz8 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-membership-rules.png)

9. **İleri**'yi seçin.

    ![Sihirbaz9 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-confirm.png)

Bu görevi tamamladıktan sonra, artık ortamdaki tüm en uç noktaları Windows bir cihaz koleksiyonunuz olur.

## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>2. Adım: Uç nokta özellikleri için Microsoft Defender'ı yapılandırma

Bu bölüm, bilgisayar veya cihazlarınız için mobil cihazlarında Microsoft Endpoint Configuration Manager özellikleri Windows yardımcı olur:

- [**Uç nokta algılama ve yanıt**](#endpoint-detection-and-response)
- [**Yeni nesil koruma**](#next-generation-protection)
- [**Saldırı yüzeyini azaltma**](#attack-surface-reduction)

### <a name="endpoint-detection-and-response"></a>Uç nokta algılama ve yanıt

#### <a name="windows-10-and-windows-11"></a>Windows 10 ve Windows 11

Microsoft 365 Defender portalının içinde, `.onboarding` System Center Configuration Manager'de ilkeyi oluşturmak için kullanılmaktadır ve bu ilkeyi Windows 10 ve Windows 11 cihazlarına dağıtmak mümkündür.

1. Bir Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında,</a> Kullanıcı Ayarlar [ekleme'yi seçin](https://security.microsoft.com/preferences2/onboarding).

2. Dağıtım yöntemi'nin altında desteklenen **Dağıtım Microsoft Endpoint Configuration Manager.**

    ![Uç nokta ekleme sihirbazı10 için Microsoft Defender'ın görüntüsü.](images/mdatp-onboarding-wizard.png)

3. Paketi **indir'i seçin**.

    ![Uç nokta ekleme sihirbazı11 için Microsoft Defender'ın görüntüsü.](images/mdatp-download-package.png)

4. Paketi erişilebilir bir konuma kaydedin.
5. Uygulama Microsoft Endpoint Configuration Manager: **Microsoft Defender ATP İlkelerine Genel > Ve Uyumluluk > Endpoint Protection >'ne gidin**.

6. **Microsoft Defender ATP İlkeleri'ne sağ tıklayın ve** **Microsoft Defender ATP İlkesi Oluştur'u seçin**.

    ![Sihirbaz12 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-create-policy.png)

7. Adı ve açıklamayı girin, **Ekleme'nin seçili** olduğunu doğrulayın ve ardından Sonraki'yi **seçin**.

    ![Sihirbaz13 Microsoft Endpoint Configuration Manager görüntüsü.](images/configmgr-policy-name.png)

8. **Gözat'ı tıklatın**.

9. Yukarıdaki 4. adımdan indirilen dosyanın bulunduğu konuma gidin.

10. **İleri**'ye tıklayın.
11. Aracıyı uygun örneklerle (Yok **veya Tüm dosya** **türleri) yapılandırabilirsiniz**.

    ![Yapılandırma ayarları1 görüntüsü.](images/configmgr-config-settings.png)

12. Uygun telemetriyi (**Normal veya Hızlandırılmış** ) **seçin ve** ardından Sonraki'ye **tıklayın**.

    ![Yapılandırma ayarları2 görüntüsü.](images/configmgr-telemetry.png)

13. Yapılandırmayı doğrulayın ve ardından Sonraki'ye **tıklayın**.

     ![Yapılandırma ayarları3 görüntüsü.](images/configmgr-verify-configuration.png)

14. Sihirbaz **tamamlandığında** Kapat'a tıklayın.

15. Yeni oluşturduğunuz Microsoft Endpoint Configuration Manager için Defender ilkeye sağ tıklayın ve Dağıt'ı **seçin**.

     ![Yapılandırma ayarları4 görüntüsü.](images/configmgr-deploy.png)

16. Sağ panelde, daha önce oluşturulmuş koleksiyonu seçin ve Tamam'a **tıklayın**.

    ![Yapılandırma ayarları5 görüntüsü.](images/configmgr-select-collection.png)

#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>Windows Client'ın önceki sürümleri (Windows 7 ve Windows 8.1)

Windows'un önceki sürümlerinin eklemesi için gereken Uç Nokta Çalışma Alanı Kimliği ve Çalışma Alanı Anahtarı için Defender'ı tanımlamak Windows.

1. Mobil Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Uç Noktaları</a> **Ekleme'Ayarlar** \> **seçin** \> (**Cihaz** **Yönetimi'nin altında**).

2. İşletim sisteminin altında **7 SP1 Windows 8.1'i seçin**.

3. Çalışma Alanı **Kimliği'ne** ve **Çalışma Alanı Anahtarı'ne** kopyalayıp kaydedin. Bunlar bu işlemde daha sonra kullanılacaktır.

    ![Ekleme görüntüsü.](images/91b738e4b97c4272fd6d438d8c2d5269.png)

4. MMA (Microsoft Monitoring Agent) yükleme.

   MMA şu anda (Ocak 2019'dan itibaren) aşağıdaki işletim sistemlerinde Windows desteklemektedir:

   - Sunucu SKUs: Windows Server 2008 SP1 veya Daha Yeni
   - İstemci SKUs'ları: Windows 7 SP1 ve sonrası

   MMA aracısı, cihaza veya cihaza Windows gerekir. Aracıyı yüklemek için, bazı sistemlerin MMA ile verileri toplamak için Müşteri deneyimi ve tanılama [telemetrisi](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) için Güncelleştirme'sini indirmesi gerekir. Bu sistem sürümleri şunları içerir ancak bunlarla sınırlı değildir:

   - Windows 8.1
   - Windows 7
   - Windows Server 2016
   - Windows Server 2012 R2
   - Windows Server 2008 R2

   Özel olarak, Windows 7 SP1'de aşağıdaki düzeltme ekleri yük kurulmalı:

   - [KB4074598 yükleme](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
   - [KB3154518 .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (veya **sonrası) ya** da [KB3154518'i yükleyin](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework). Her ikisini de aynı sisteme yükleyemesiniz.

5. İnternet'e bağlanmak için proxy kullanıyorsanız Proxy ayarlarını yapılandırma bölümüne bakın.

Tamamlandığında, portalda bir saat içinde yerleşik uç noktaları görmelisiniz.

### <a name="next-generation-protection"></a>Yeni nesil koruma

Microsoft Defender Virüsten Koruma, masaüstü bilgisayarlar, taşınabilir bilgisayarlar ve sunucular için yeni nesil koruma sağlayan yerleşik bir kötü amaçlı yazılımdan koruma çözümüdür.

1. Uygulama konsolunda Microsoft Endpoint Configuration Manager Varlıklara **\> \> ve Uyumluluğuna Genel Bakış'a Endpoint Protection \>** Kötü amaçlı Yazılımdan Koruma **İlkeleri'ne gidin** ve Kötü amaçlı Yazılımdan Koruma İlkesi Oluştur'a seçin.

    ![Kötü amaçlı yazılımdan koruma ilkesi resmi.](images/9736e0358e86bc778ce1bd4c516adb8b.png)

2. **Zamanlanmış taramalar**, **Tarama ayarları**, **Varsayılan eylemler**, **Gerçek zamanlı** koruma, **Dışlama** ayarları, **Gelişmiş**, **Tehdit** geçersiz kılmaları, **Bulut Koruma** Hizmeti ve **Güvenlik** zekası güncelleştirmeleri'ne ve Tamam'a **tıklayın**.

    ![Yeni nesil koruma bölmesinin resmi1.](images/1566ad81bae3d714cc9e0d47575a8cbd.png)

    Belirli endüstrilerde veya bazı belirli kurumsal müşterilerin Virüsten Koruma'nın nasıl yapılandırılmayla ilgili belirli ihtiyaçları olabilir.

    [Hızlı tarama ile tam tarama ve özel tarama karşılaştırması](/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    Diğer ayrıntılar için bkz. [Windows Güvenliği çerçevesine bakın](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework).
  
    ![Yeni nesil koruma bölmesinin resmi2.](images/cd7daeb392ad5a36f2d3a15d650f1e96.png)

    ![Yeni nesil koruma bölmesinin görüntüsü3.](images/36c7c2ed737f2f4b54918a4f20791d4b.png)

    ![Yeni nesil koruma bölmesinin4 resmi.](images/a28afc02c1940d5220b233640364970c.png)

    ![Yeni nesil koruma bölmesinin resmi5.](images/5420a8790c550f39f189830775a6d4c9.png)

    ![Yeni nesil koruma bölmesinin resmi6.](images/33f08a38f2f4dd12a364f8eac95e8c6b.png)

    ![Yeni nesil koruma bölmesinin resmi7.](images/41b9a023bc96364062c2041a8f5c344e.png)

    ![Yeni nesil koruma bölmesinin resmi8.](images/945c9c5d66797037c3caeaa5c19f135c.png)

    ![Yeni nesil koruma bölmesinin9 resmi.](images/3876ca687391bfc0ce215d221c683970.png)

3. Yeni oluşturulan kötü amaçlı yazılımlardan koruma ilkesine sağ tıklayın ve Dağıt'ı **seçin**.

    ![Yeni nesil koruma bölmesinin resmi10.](images/f5508317cd8c7870627cb4726acd5f3d.png)

4. Yeni kötü amaçlı yazılımlardan koruma ilkesine hedef Windows Tamam'a **tıklayın**.

     ![Yeni nesil koruma bölmesinin resmi11.](images/configmgr-select-collection.png)

Bu görevi tamamladıktan sonra, görev ayarlarını başarıyla Windows Defender Virüsten Koruma.

### <a name="attack-surface-reduction"></a>Saldırı yüzeyini azaltma

Endpoint için Defender'ın saldırı yüzeyini azaltma sütunu, Exploit Guard altında bulunan özellik kümesi içerir. Saldırı yüzeyini azaltma (ASR) kuralları, Denetimli Klasör Erişimi, Ağ Koruması ve Exploit Protection.

Tüm bu özellikler bir denetim modu ve bir engelleme modu sağlar. Denetim modunda son kullanıcının hiçbir etkisi yoktur. Yaptığı tek şey ek telemetri toplamak ve telemetriyi portalda Microsoft 365 Defender. Dağıtımda amaç, güvenlik denetimlerini adım adım engelleme moduna taşımaktır.

Denetim modunda ASR kuralları ayarlamak için:

1. Uygulama konsolunda Microsoft Endpoint Configuration Manager ve **\> \> Uyumluluğuna Genel Bakış 'a Endpoint Protection \> Windows Defender Exploit Guard İlkesi** Oluştur'a gidin.

   ![Konsol0 Microsoft Endpoint Configuration Manager görüntüsü.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Saldırı **Yüzeyini Azaltma'yi seçin**.

3. Kurallara **Denetim'i ayarlayın ve** Sonraki'ne **tıklayın**.

    ![Konsol1 Microsoft Endpoint Configuration Manager görüntüsü.](images/d18e40c9e60aecf1f9a93065cb7567bd.png)

4. Yeni Exploit Guard ilkenizi onaylamak için Sonraki düğmesine **tıklayın**.

    ![Konsol2 Microsoft Endpoint Configuration Manager görüntüsü.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. İlke oluşturulduktan sonra Kapat'a **tıklayın**.

    ![Konsol3 Microsoft Endpoint Configuration Manager görüntüsü.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Yeni oluşturulan ilkeye sağ tıklayın ve Dağıt'ı **seçin**.

    ![Konsol4 Microsoft Endpoint Configuration Manager görüntüsü.](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. İlkeyi yeni oluşturulan site koleksiyonuna Windows tamam'a **tıklayın**.

    ![Konsol5 Microsoft Endpoint Configuration Manager görüntüsü.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Bu görevi tamamladıktan sonra, artık denetim modunda ASR kurallarını başarıyla yapılandırmış olursunuz.

Aşağıda, ASR kurallarının uç noktalara doğru uygulanıp uygulanmadı ılmasıyla ilgili ek adımlar verilmiştir. (Bu birkaç dakika sürebilir)

1. Web tarayıcısında Tamam'a <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

2. Sol **menüden** Yapılandırma yönetimi'ne tıklayın.

3. Saldırı **yüzeyi yönetim panelinde Saldırı yüzeyi yönetimi** için Git'e tıklayın.

    ![Saldırı yüzeyi yönetimi resmi.](images/security-center-attack-surface-mgnt-tile.png)

4. Saldırı **yüzeyini azaltma** kuralları raporlarındaki Yapılandırma sekmesine tıklayın. Her cihaz için ASR kuralları yapılandırmasına genel bakış ve ASR kuralları durumunu gösterir.

    ![Saldırı yüzeyini azaltma kuralları raporlarının ekran görüntüsü1.](images/f91f406e6e0aae197a947d3b0e8b2d0d.png)

5. ASR kurallarının yapılandırma ayrıntılarını gösteren her cihaza tıklayın.

    ![Saldırı yüzeyini azaltma kuralları raporlarının ekran görüntüsü2.](images/24bfb16ed561cbb468bd8ce51130ca9d.png)

Daha [fazla ayrıntı için bkz. ASR kuralı dağıtımını ve algılamalarını](/microsoft-365/security/defender-endpoint/configure-machines-asr) en iyi duruma getirme.

#### <a name="set-network-protection-rules-in-audit-mode"></a>Denetim modunda Ağ Koruma kurallarını ayarlama

1. Uygulama konsolunda Microsoft Endpoint Configuration Manager ve **\> \> Uyumluluğuna Genel Bakış 'a Endpoint Protection \> Windows Defender Exploit Guard İlkesi** Oluştur'a gidin.

    ![Configuration Manager1 System Center ekran görüntüsü.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Ağ **koruması'ı seçin**.

3. Ayarı Denetim olarak ayarlayın **ve Sonraki'yi** **tıklatın**.

    ![Configuration Manager2 System Center i ekran görüntüsü.](images/c039b2e05dba1ade6fb4512456380c9f.png)

4. Yeni Exploit Guard İlkesi'ne tıklayarak Sonraki'ne tıklayarak bu ilkeyi **onaylayın**.

    ![Exploit Guard ilke1 ekran görüntüsü.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. İlke oluşturulduktan sonra Kapat'a **tıklayın**.

    ![Exploit Guard ilke2 ekran görüntüsü.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Yeni oluşturulan ilkeye sağ tıklayın ve Dağıt'ı **seçin**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi1 ekran görüntüsü.](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. Yeni oluşturulan site koleksiyonunun Windows seçin ve Tamam'ı **seçin**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi2'nin ekran görüntüsü.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Bu görevi tamamladıktan sonra, artık denetim modunda Ağ Korumasını başarıyla yapılandırmış olursunuz.

#### <a name="to-set-controlled-folder-access-rules-in-audit-mode"></a>Denetim modunda Denetimli Klasör Erişimi kurallarını ayarlamak için

1. Uygulama Microsoft Endpoint Configuration Manager Assets and **ComplianceOverview'a** >  >  gidin **Endpoint Protection Windows Defender** >  **Exploit Guard'ı** seçin ve ardından **Exploit Guard İlkesi Oluştur'u seçin**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi3'in ekran görüntüsü.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Denetimli **klasör erişimi'ne tıklayın**.

3. Yapılandırmayı Denetim olarak ayarlayın **ve Sonraki'yi** **tıklatın**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi4'in ekran görüntüsü.](images/a8b934dab2dbba289cf64fe30e0e8aa4.png)

4. Sonraki seçeneğine tıklayarak yeni Exploit Guard **İlkesi'ne tıklayın**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi5'in ekran görüntüsü.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. İlke oluşturulduktan sonra Kapat'a **tıklayın**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi6'nın ekran görüntüsü.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Yeni oluşturulan ilkeye sağ tıklayın ve Dağıt'ı **seçin**.

    ![Microsoft Uç Nokta Yapılandırma Yöneticisi7'nin ekran görüntüsü.](images/8999dd697e3b495c04eb911f8b68a1ef.png)


7. İlkeyi yeni oluşturulan site koleksiyonuna Windows tamam'a **tıklayın**.


    ![Microsoft Uç Nokta Yapılandırma Yöneticisi8'in ekran görüntüsü.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Denetim modunda Denetimli klasör erişimini başarıyla yapılandırdısınız.

## <a name="related-topic"></a>İlgili konu

- [Microsoft Endpoint Manager kullanarak işe Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
