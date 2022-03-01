---
title: Yerel Windows kullanarak cihazları ekleme
description: Cihazların hizmete dahil yapılandırmasını etkinleştirmek üzere cihazlara yapılandırma paketini dağıtmak için yerel bir betik kullanın.
keywords: Yerel bir betik kullanarak cihazları yapılandırma, cihaz yönetimi, Uç nokta cihazları için Microsoft Defender'ı yapılandırma
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6abd2c26f8557277b4c1b13e5189a42fea9a60f1
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034410"
---
# <a name="onboard-windows-devices-using-a-local-script"></a>Yerel Windows kullanarak cihazları ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Uç nokta için Defender'a cihazları el ile de ekleyebilirsiniz. Bunu, ağ üzerindeki tüm cihazları eklemeye karardan önce hizmeti test etmek için yapmak iyi bir durum olabilir.

> [!IMPORTANT]
> Bu betik, en fazla on cihaz için kullanım için en iyi duruma getirilmiş.
> Yerel betik, Uç Nokta için Microsoft Defender'ı değerlendirmeye yardımcı olan özel bir ekleme yöntemidir.
> Yerel bir betik kullanarak ekleme kullanılırken veri raporlama sıklığı, diğer ekleme yöntemlerine göre daha yüksek bir değere ayarlanır.
> Bu ayar değerlendirme amaçlıdır ve normalde üretim dağıtımlarında kullanılmaz. Bu nedenle, çevreyi etkileyen etki konusunda kaygılar olabilir, bu nedenle yerel betikleri kullanarak dağıtım sayısını on ile sınırlamanızı öneririz.
> Daha önce açıklandığı gibi bir üretim ortamına dağıtımıyorsanız, Grup İlkesi veya Dağıtım [Grubu gibi](configure-endpoints.md) diğer Microsoft Endpoint Configuration Manager.

Uç Nokta için [Defender'Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) çeşitli yolları görmek için PDF veya Dosya Ayarları'ne göz atabilirsiniz.[](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) 

## <a name="onboard-devices"></a>Cihazları ekleme 

1.  Hizmet ekleme sihirbazından indirdiğiniz .zip GP yapılandırma paketini (*WindowsDefenderATPOnboardingPackage.zip*) açın. Paketi portaldan da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>:

    1. Gezinti bölmesinde, Gezinti **Bölmesi'Ayarlar** >  **EndpointsDevice** >  **managementOnboarding** >  öğesini seçin.


Uç Nokta için [Defender'Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) çeşitli yolları görmek için PDF veya Dosya Ayarları'ne göz atabilirsiniz.[](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)

1. Hizmet ekleme sihirbazından indirdiğiniz .zip GP yapılandırma paketini (*WindowsDefenderATPOnboardingPackage.zip*) açın. Paketi portaldan da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>:
    1. Gezinti bölmesinde, Uç Noktaları **Cihaz yönetimi** \> Ayarlar **Ekleme'yi** \>  \> **seçin**.
    2. İşletim Windows 10 veya Windows 11 olarak seçin.
    3. Dağıtım yöntemi **alanında Yerel** **Betik'i seçin**.
    4. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. Yapılandırma paketinin içeriğini, eklemek istediğiniz cihazda (örneğin Masaüstü) bir konuma ayıklar. *WindowsDefenderATPLocalOnboardingScript.cmd adlı bir dosyanız olmalıdır*.

3. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:
   1. **Başlat'a gidin** ve **cmd yazın**.
   2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

    ![Window Başlat menüsü Yönetici olarak çalıştır'a işaret ediyor olabilir.](images/run-as-admin.png)

4.  Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyaladıysanız, şöyle yazın: *%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  **Enter tuşuna basın** veya Tamam'a **tıklayın**.

Cihazın uyumlu olduğunu nasıl el ile doğru şekilde doğrulayabilirsiniz hakkında bilgi için bkz. Uç nokta ekleme sorunları için [Microsoft Defender'da sorun giderme](troubleshoot-onboarding.md).

> [!TIP]
> Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta için Microsoft Defender uç noktası üzerinde algılama testi çalıştırma](run-detection-test.md).

## <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

Her cihaz için, bir yapılandırma değeri ayarp, derin çözümleme için bir dosya göndermek için bir istek Microsoft 365 Defender cihazdan örnek toplanabilir olup olmadığını ifade edebilirsiniz.

*Regedit* kullanarak veya .reg dosyası oluşturarak ve çalıştırarak, cihazda örnek paylaşım ayarını *el ile yapılandırabilirsiniz*.

Yapılandırma aşağıdaki kayıt defteri anahtarı girdisi aracılığıyla ayarlanır:

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Burada Ad türü bir D-WORD'tür. Olası değerler:

- 0 - Bu cihazdan örnek paylaşıma izin vermiyor
- 1 - Bu cihazdan tüm dosya türlerinin paylaşımına izin verir

Kayıt defteri anahtarının mevcut olması durumunda varsayılan değer 1'tir.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Eklemeyi doğrulamak için bir algılama testi çalıştırma

Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta cihazı için Microsoft Defender'da algılama testi çalıştırma](run-detection-test.md).

## <a name="offboard-devices-using-a-local-script"></a>Yerel betik kullanan offboard cihazları

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Bir portaldan çıkartan <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>
    1. Gezinti bölmesinde, Uç Noktalar **Cihaz yönetimi Ayarlar** \> **Çıkar'ı** \>  \> **seçin**.
    2. İşletim Windows 10 veya Windows 11 olarak seçin.
    3. Dağıtım yöntemi **alanında Yerel** **Betik'i seçin**.
    4. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. Bu dosyanın içeriğini .zip cihazlar tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

3. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:
   1. **Başlat'a gidin** ve **cmd yazın**.
   2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

        ![Window Başlat menüsü Yönetici olarak çalıştır'a işaret ediyor olabilir.](images/run-as-admin.png)

4. Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyalediysanız, şöyle yazın: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

5. **Enter tuşuna basın** veya Tamam'a **tıklayın**.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Komut dosyasının başarıyla tamamlandıktan ve [aracının çalıştığını](troubleshoot-onboarding.md) doğrulamak için, Ekleme sorunlarını giderme adımlarında farklı doğrulama adımlarını izleyin.

İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak da yapılabilir.

### <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.
2. Cihazlar **envanteri'ne tıklayın**.
3. Cihazların görüntüde olduğunu doğrulayın.

## <a name="related-topics"></a>İlgili konular
- [Grup Windows kullanarak diğer cihazları ekleme](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows cihazları Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Mobil Windows Yönetim araçlarını kullanarak cihazları ekleme](configure-endpoints-mdm.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](configure-endpoints-vdi.md)
- [Yeni eklenen Uç nokta cihazı için Microsoft Defender'da bir algılama testi çalıştırma](run-detection-test.md)
- [Uç nokta ekleme sorunları için Microsoft Defender'da sorun giderme](troubleshoot-onboarding.md)
