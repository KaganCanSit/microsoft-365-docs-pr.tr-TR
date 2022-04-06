---
title: Ağ cihazı bulma ve güvenlik açığı yönetimi
description: Anahtarlar, yönlendiriciler, WLAN denetleyicileri ve güvenlik duvarı işletim sistemleri için güvenlik önerileri ve güvenlik açığı algılama özelliği artık kullanılabilir.
keywords: ağ cihazları, ağ cihazları güvenlik açığı algılaması, anahtarın işletim sistemleri, yönlendiriciler, WLAN denetleyicileri ve güvenlik duvarları
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f6092800de89ebfdeed35230b1ade296e0396a85
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468787"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Ağ cihazı bulma ve güvenlik açığı yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> 04-13-2021'de\) yayımlanan [Ağ](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) cihazı bulma ve güvenlik açığı değerlendirmesi Blogu\(, Uç Nokta için Defender'daki yeni  Ağ cihazı bulma özellikleri hakkında öngörüler sağlar. Bu makalede, Ağ cihazı bulma özelliği tarafından ele  alınan görevle ilgili genel bir bakış ve bu yeni özellikleri kullanmaya başlama hakkında ayrıntılı bilgi bulabilirsiniz.

Ağ bulma özellikleri, mobil **portalın ve** uygulama <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">konsollarının Cihaz Microsoft 365 Defender</a> bölümünde Microsoft 365 Defender kullanılabilir.

Önceden yapılandırılmış Uç Nokta için Microsoft Defender düzenli taramaları gerçekleştirmek için her ağ kesimi üzerinde belirlenen bir kimlik doğrulama cihazı kullanılır. Bulunduktan sonra, Uç Nokta İçin Defender güvenlik Tehdit ve Güvenlik Açığı Yönetimi bulunan anahtarlar, yönlendiriciler, WLAN denetleyicileri, güvenlik duvarları ve VPN ağ geçitleri için tümleşik iş akışları sağlar.

Ağ cihazları bulunduktan ve sınıflandırılıldıktan sonra, güvenlik yöneticileri en son güvenlik önerilerini alma ve kuruluşları genelinde dağıtılan ağ cihazlarıyla ilgili son bulunan güvenlik açıklarını gözden geçirebilirsiniz.

## <a name="approach"></a>Yaklaşım

Ağ cihazları standart uç nokta olarak yönetilmiyor Uç Nokta için Defender'ın, ağ cihazlarına yerleşik bir algılayıcısı olmaz. Bu tür cihazlar, uzaktan taramanın cihazlardan gerekli bilgileri edineni aracısız bir yaklaşım gerektirir. Ağ topolojisi ve özelliklerine bağlı olarak, Uç Nokta için Microsoft Defender'a ekli tek bir cihaz veya birkaç cihaz SNMP (salt okunur) kullanarak ağ cihazlarının kimliği doğrulanmış taramalarını gerçekleştirecek.

İki tür cihaz olacağını unutmayın:

- **Değerlendirme cihazı**: Ağ cihazlarını taramak için kullanabileceğiniz, önceden orada olan bir cihaz.
- **Ağ cihazları**: Taramayı ve eklemeyi planlayınız ağ cihazları.

### <a name="vulnerability-management-for-network-devices"></a>Ağ cihazları için güvenlik açığı yönetimi

Ağ cihazları bulunduktan ve sınıflandırılıldıktan sonra, güvenlik yöneticileri en son güvenlik önerilerini alma ve kuruluşları genelinde dağıtılan ağ cihazlarıyla ilgili son bulunan güvenlik açıklarını gözden geçirebilirsiniz.

## <a name="operating-systems-that-are-supported"></a>Desteklenen işletim sistemleri

Aşağıdaki işletim sistemleri şu anda desteklemektedir:

- Cisco IOS, IOS-XE, NX-OS
- Juniper JUNOS
- HPE ArubaOS, Eşzamanlı Geçiş Yazılımı
- Palo Alto Networks PAN-OS

Zaman içinde, müşteri kullanımından toplanmış veriler temel alarak daha fazla ağ satıcıları ve işletim sistemi eklenir. Bu nedenle, bu listede belirtilmemiş olsalar bile tüm ağ cihazlarınızı yapılandırmanız teşvik edilecektir.

## <a name="how-to-get-started"></a>Nasıl başlandı?

İlk adımınız, kimliği doğrulanmış ağ taramalarını gerçekleştirecek bir cihaz seçmektir.

1. Tarama yapmayı planlamış olan ağ cihazları için yönetim bağlantı noktasına ağ bağlantısı olan uç nokta için Defender eklemeli bir cihaza (istemci veya sunucu) karar verin.

2. Uç nokta için Defender değerlendirme cihazı ile hedefli ağ cihazları arasındaki SNMP trafiğine izin ver (örneğin, Güvenlik Duvarı tarafından) gerekir.

3. Güvenlik açıkları için hangi ağ cihazlarının değerlendirileceklerine karar verin (örneğin: Cisco anahtarı veya Palo Alto Networks güvenlik duvarı).

4. Yapılandırılmış tüm ağ cihazlarda SNMP salt okunur'un etkinleştirildiğinden emin olun; bu şekilde Uç Nokta için Defender değerlendirme cihazı yapılandırılmış ağ cihazlarını sorgular. Bu özelliğin düzgün işlevselliği için 'SNMP yazma' gerekli değildir.

5. Taranacak ağ cihazlarının IP adreslerini (veya bu cihazların dağıtıldı olduğu alt ağları) alın.

6. Ağ cihazlarının SNMP kimlik bilgilerini alın (örneğin: Community String, noAuthNoPriv, authNoPriv, authPriv). Yeni bir değerlendirme işi yapılandırken kimlik bilgilerini sağlamanız gerekir.

7. Ara sunucu istemci yapılandırması: Uç nokta cihaz ara sunucu gereksinimleri için Defender dışında ek yapılandırma gerekmez.

8. Ağ tarayıcısının kimlik doğrulamasına ve düzgün çalışmasına izin vermek için, aşağıdaki etki alanlarını/URL'leri eklemeniz çok önemlidir:

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > İzin verilen veri toplamanın Uç nokta için Defender belgelenmiş listesinde tüm URL'ler belirtilmez.

## <a name="permissions"></a>İzinler

Değerlendirme işlerini yapılandırmak için aşağıdaki kullanıcı izni seçeneği gereklidir: **Defender'da güvenlik ayarlarını yönetme**. bu izni, Roller'e **Ayarlar** \> **bulabilirsiniz**. Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi için roller oluşturma ve yönetme](user-roles.md).

## <a name="install-the-network-scanner"></a>Ağ tarayıcısını yükleme

1. Güvenlik ve **Microsoft 365 Noktaları** \> **Ayarlar** \> **işleri'ne** \> gidin (**Ağ** **değerlendirmeleri'nin altında**).
    1. Değerlendirme Microsoft 365 Defender, Değerlendirme işleri Ayarlar > gidin.

2. Ağ tarayıcısını indirin ve Uç nokta değerlendirme cihazı için belirlenmiş Defender'a yükleyin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Tarayıcıyı indir düğmesi" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Ağ tarayıcısı yüklemesi & kaydı

Oturum açma işlemi belirlenen değerlendirme cihazında veya başka herhangi bir cihazda (örneğin, kişisel istemci cihazınız) tamamlandıktan sonra tamamlanır.

Ağ tarayıcısı kayıt işlemini tamamlamak için:

1. Komut satırda görünen URL'yi kopyalayın ve izleyin ve kayıt işlemini tamamlamak için sağlanan yükleme kodunu kullanın.

    > [!NOTE]
    > URL'yi kopya şekilde kopyalamak için Komut İstemi ayarlarını değiştirebilirsiniz.

2. Kodu girin ve "Defender'da güvenlik ayarlarını yönetme" adlı Uç Nokta için Defender iznine sahip bir Microsoft hesabı kullanarak oturum açın.

3. Bitirdikten sonra, oturum a imzalanannızı onaylayan bir ileti görüyorsanız.

## <a name="configure-a-new-assessment-job"></a>Yeni değerlendirme işini yapılandırma

Ayarlar'daki **Değerlendirme işleri** sayfasında Ağ değerlendirme **işi ekle'yi seçin**. Düzenli olarak taranacak ve cihaz stoka eklenecek ağ cihazlarını seçmek için ayarlama işlemini izleyin.

Ağ cihazı envanteri içinde cihaz yinelemesi önlemek için, her IP adresinin birden çok değerlendirme cihazında yalnızca bir kez yapılandırıldığından emin olun.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Ağ değerlendirme işi ekle düğmesi" lightbox="images/assessment-jobs-add.png":::

Ağ değerlendirme iş adımları ekleme:

1. Ağ tarayıcısının yüklü olduğu 'Değerlendirme işi' ve 'Değerlendirme cihazı' seçin. Bu cihaz, düzenli olarak kimliği doğrulanmış taramaları gerçekleştirecek.

2. Taranacak hedef ağ cihazlarının (veya bu cihazların dağıtıldı olduğu alt ağların) IP adreslerini ekleyin.

3. Hedef ağ cihazlarının gerekli SNMP kimlik bilgilerini ekleyin.

4. Düzenli ağ taraması başlatmak için yeni yapılandırılan ağ değerlendirme işini kaydedin.

### <a name="scan-and-add-network-devices"></a>Ağ cihazlarını tarama ve ekleme

Ayarlama işlemi sırasında, bunu doğrulamak için bir kez test taraması gerçekleştirin:

- Uç nokta için Defender değerlendirme cihazı ile yapılandırılmış hedef ağ cihazları arasında bağlantı vardır.
- Yapılandırılmış SNMP kimlik bilgileri doğru.

Her değerlendirme cihazı 1.500'e kadar başarılı IP adresi taraması destekleyene kadar. Örneğin, yalnızca 100 IP adresinin başarılı sonuçlar elde etmek için 10 farklı alt ağın taranıyor olmasıyla aynı değerlendirme cihazına 1.400 IP ek adresi taramanız mümkün olur.

Taranacak birden çok IP adresi aralığı/alt ağ varsa, test tarama sonuçlarının ortaya çıktısı birkaç dakika sürer. En çok 1.024 adres için test taraması kullanılabilir.

Sonuçlar ortaya çıktıktan sonra, düzenli taramaya hangi cihazların dahil olacağını seçebilirsiniz. Tarama sonuçlarını görüntülemeyi atlarsanız, tüm yapılandırılmış IP adresleri ağ değerlendirme işine (cihazın yanıtı ne olursa olsun) eklenir. Tarama sonuçları da dışarı aktarıldı.

## <a name="device-inventory"></a>Cihaz envanteri

Yeni bulunan cihazlar, Cihaz envanteri **sayfasındaki** yeni Ağ cihazları **sekmesi altında** gösterilir. Değerlendirme işi ekledikten sonra cihazlar güncelleştirilene kadar iki saat kadar sürebilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Cihaz envanteri'nin Ağ cihazları bölümü" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Sorun giderme

### <a name="network-scanner-installation-has-failed"></a>Ağ tarayıcısı yüklemesi başarısız oldu

Gerekli URL'lerin güvenlik duvarı ayarlarınıza izin verilen etki alanlarına ekli olduğunu doğrulayın. Ayrıca, ara sunucu ayarlarının Cihaz ara sunucusunu ve İnternet bağlantısı [ayarlarını yapılandırma konusunda açıklandığı gibi yapılandırıldığından emin olun](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Microsoft.com/devicelogin web sayfası gösternmdi

Gerekli URL'lerin güvenlik duvarınız içinde izin verilen etki alanlarına ekli olduğunu doğrulayın. Ayrıca, ara sunucu ayarlarının Cihaz ara sunucusunu ve İnternet bağlantısı [ayarlarını yapılandırma konusunda açıklandığı gibi yapılandırıldığından emin olun](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Ağ cihazları birkaç saat sonra cihaz envanteri içinde gösterilmez

Tarama sonuçları, değerlendirme iş yapılandırması tamamladıktan sonra yapılan ilk taramadan birkaç saat sonra güncelleştirilebilir.

Cihazlar hala gösterilmezse, ağ tarayıcısını yüklemiş ve ilgili değerlendirme iş yapılandırmasında bir "Çalıştır tarama" gerçekleştirmişsiniz olan değerlendirme cihazlarınız üzerinde 'MdatpNetworkScanService' hizmetinin çalıştığını doğrulayın.

5 dakika sonra yine de sonuç alasanız, hizmeti yeniden başlatın.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>En son görülen cihaz süresi 24 saatden uzundur

Tarayıcının düzgün bir şekilde çalışıyor olduğunu doğrulayın. Ardından tarama tanımına gidin ve "Sınamayı çalıştır" seçeneğini seçin. İlgili IP adreslerinden hangi hata iletilerinin döndürenleri kontrol edin.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Kullanıcı Tehdit ve Güvenlik Açığı Yönetimi izni gerekli

Kayıt işlemi bir hatayla tamamlandı: "Yeni bir aracı eklemek için yeterli izinlere sahip olmadığınız görünüyor. Gerekli izin 'Defender'da güvenlik ayarlarını yönet' iznidir."

Çıkmak için herhangi bir tuşa basın.

Sistem yöneticinizden size gerekli izinleri atamalarını iste. Alternatif olarak, ilgili başka bir üyeden oturum açma kodunu ve bağlantısını sağlayarak oturum açma sürecinde size yardımcı olabilir.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Kayıt işlemi, kayıt işlemi sırasında komut satırına verilen bağlantı kullanılarak başarısız oluyor

Farklı bir tarayıcı deneyin veya oturum açma bağlantısını ve kodunu farklı bir cihaza kopyalayın.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Metin komut satırına çok küçük veya metin kopya değil

Kopyalamaya ve metin boyutunu değiştirmeye izin vermek için cihazınızın komut satırı ayarlarını değiştirin.

## <a name="related-articles"></a>İlgili makaleler

- [Cihaz envanteri](machines-view-overview.md)
- [Gelişmiş özellikleri yapılandırma](advanced-features.md)
