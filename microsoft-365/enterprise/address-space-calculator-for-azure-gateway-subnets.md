---
title: Azure ağ geçidi alt ağları için adres alanı hesaplayıcısı
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/07/2021
audience: ITPro
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
description: 'Özet: C3, Python veya PowerShell ile bir Azure ağ geçidi alt 6 6 sının adres alanını hesaplayın.'
ms.openlocfilehash: a19233b6ec68c92dbf65ecb6a73fc1a0a16e6d31
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094890"
---
# <a name="address-space-calculator-for-azure-gateway-subnets"></a>Azure ağ geçidi alt ağları için adres alanı hesaplayıcısı

Diğer ağlara bağlı Azure altyapı hizmetlerindeki bir sanal ağın (VNet) ağ geçidi alt ağına sahip olması gerekir. Ağ geçidi alt ağı tanımlamaya yönelik en iyi yöntemler şunlardır:

- Ağ geçidi alt ağı ön ek uzunluğu en fazla 29 olabilir (örneğin, 10.119.255.248/29), ancak geçerli öneri 27 ön ek uzunluğu kullanmanızdır (örneğin, 10.119.255.224/27).
- Ağ geçidi alt ağlarının adres alanını tanımlarken, sanal ağ adres alanının son bölümünü kullanın.

İkinci öneri için, ağ geçidi alt ağı için kullanılan bitleri 0 ve sanal ağ adres alanında kalan bitleri 1 olarak ayarlayarak ağ geçidi alt 6'nın adres alanını belirleyebilirsiniz. ağ geçidi alt ağ adres alanını ikiliye ve ondalık değere dönüştürmeye gerek kalmadan hızlı bir şekilde hesaplamak için, C# veya Python ile yazılmış veya PowerShell komut bloğuyla yazılmış bir konsol uygulaması kullanabilirsiniz.

Bu makale, sanal ağ adresi ön eki ve ağ geçidi alt ağ ön eki uzunluğu için w.x.y.z/n değerlerine göre ağ geçidi alt ağ adres alanını hesaplayan C#, Python ve PowerShell kod bloklarını içerir.

## <a name="c-code-block"></a>C# kod bloğu

C# dilinde bir konsol uygulaması oluşturmak için bu kod bloğunu kullanın.

```c#
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace ConsoleApplication1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // Declare variables. 
            const long wOctet = 16777216;  
            const long xOctet = 65536; 
            const long yOctet = 256; 
            double D; 
            int w, x, y, z, vnetPrefLen, gwPrefLen; 
            long d, w2, x2, y2, z2; 
             
 
            // Get the five values needed from the keyboard. 
            Console.WriteLine("**************************************************************************"); 
            Console.WriteLine("*** Gateway subnet address space calculator for Azure virtual networks ***");             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine(); 
            Console.WriteLine("Please supply your virtual network address space in the form of w.x.y.z/n."); 
            Console.WriteLine(); 
            Console.WriteLine("w="); 
            w = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("x="); 
            x = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("y="); 
            y = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("z="); 
            z = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("n="); 
            vnetPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
            Console.WriteLine("Now supply the prefix length of your gateway subnet:"); 
            gwPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
 
            // Perform the calculation. 
            D = w * wOctet + x * xOctet + y * yOctet + z; 
            for (int i = vnetPrefLen + 1; i < gwPrefLen + 1; i++) 
            { 
                D = D + Math.Pow(2, 32 - i); 
            } 
            d = Convert.ToInt64(D); 
            w2 = d / wOctet; 
            x2 = (d - w2 * wOctet) / xOctet;  
            y2 = (d - w2 * wOctet - x2 * xOctet) / yOctet; 
            z2 = d - w2 * wOctet - x2 * xOctet - y2 * yOctet; 
             
            // Display the result.             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine("For the Azure virtual address space {0}.{1}.{2}.{3}/{4}", w, x, y, z, vnetPrefLen); 
            Console.WriteLine("and gateway prefix length of {0}, the gateway subnet address space is:", gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("{0}.{1}.{2}.{3}/{4}", w2, x2, y2, z2, gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("Press ENTER to quit."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="python-code-block"></a>Python kod bloğu

Python'da konsol uygulaması oluşturmak için bu kod bloğunu kullanın.

```python
import math 
# Collect the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet 
print("**************************************************************************")  
print("*** Gateway subnet address space calculator for Azure virtual networks ***")  
print("**************************************************************************\n")   
print("Please supply your virtual network address space in the form of w.x.y.z/n.");  
w=int(input("w = ")) 
x=int(input("x = ")) 
y=int(input("y = ")) 
z=int(input("z = ")) 
n=int(input("n = ")) 
print("")  
g=int(input("Now supply the prefix length of your gateway subnet: ")) 
print("")  
 
# Calculate  
wOctet = 16777216  
xOctet = 65536  
yOctet = 256  
D = w * wOctet + x * xOctet + y * yOctet + z 
for index in range(n + 1,g + 1): 
    D += 2**(32 - index)  
 
w2 = math.floor(D / wOctet)  
x2 = math.floor((D - w2 * wOctet) / xOctet) 
y2 = math.floor((D - w2 * wOctet - x2 * xOctet) / yOctet) 
z2 = D - w2 * wOctet - x2 * xOctet - y2 * yOctet  
 
# Display the result  
gwAddrPref= "Your gateway address prefix is: " + str(w2) + "." + str(x2) + "." + str(y2) + "." + str(z2) + "/" + str(g)  
print(gwAddrPref) 
```


## <a name="powershell-command-block"></a>PowerShell komut bloğu

Değerleri doldurun ve sonuçta elde edilen komut bloğunu bir PowerShell penceresinde veya PowerShell Tümleşik Betik Ortamı'nda (ISE) çalıştırın.

```powershell
# Specify the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet: 
$w= 
$x= 
$y= 
$z= 
$n= 
$g= 
# Calculate 
$wOctet = 16777216 
$xOctet = 65536 
$yOctet = 256 
[long]$D = $w * $wOctet + $x * $xOctet + $y * $yOctet + $z; 
for ($i = $n + 1; $i -lt $g + 1; $i++) 
{ 
$D = $D + [math]::pow(2, 32 - $i) 
} 
$w2 = [math]::floor($D / $wOctet) 
$x2 = [math]::floor( ($D - $w2 * $wOctet) / $xOctet ) 
$y2 = [math]::floor( ($D - $w2 * $wOctet - $x2 * $xOctet) / $yOctet ) 
$z2 = $D - $w2 * $wOctet - $x2 * $xOctet - $y2 * $yOctet 
# Display the result 
$dx= [string]$w2 + "." + [string]$x2 + "." + [string]$y2 + "." + [string]$z2 + "/" + [string]$g 
Write-Host "Your gateway address prefix is: " $dx
```
    
## <a name="related-topics"></a>İlgili konular

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)