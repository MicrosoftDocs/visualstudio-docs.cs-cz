---
title: Konfigurace brány Windows Firewall pro vzdálené ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f232446ed699bd7cc034e4b6d6148b665830cf2d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535522"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurace brány firewall ve Windows pro vzdálené ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak nakonfigurovat bránu firewall, aby povolovala vzdálené ladění na počítačích, na kterých běží tyto operační systémy:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Pokud síť, na které ladíte ladění, není chráněná bránou firewall, tato konfigurace není nutná. Jinak počítač, který je hostitelem sady Visual Studio a vzdálený počítač, který má být laděn, vyžaduje změny v konfiguraci brány firewall.  
  
  **Protokol IPSec** Vyžaduje-li vaše síť, aby byla komunikace provedena pomocí protokolu IPSec, je nutné otevřít další porty na hostitelském počítači sady Visual Studio i na vzdáleném počítači.  
  
  **Webový server** Pokud ladíte vzdálený webový server, je nutné otevřít další port na vzdáleném počítači.  
  
  Všimněte si, že oba počítače nemusí spouštět stejný operační systém. Například počítač s Visual Studiem může používat Windows 10 a vzdálený počítač může používat Windows Server 2012 R2.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Konfigurace brány Windows Firewall na počítači se systémem Visual Studio  
 Pokyny pro konfiguraci brány Windows Firewall se mírně liší v různých operačních systémech. V systému Windows 7 nebo Windows Server 2008 se používá **program** Word. v systému Windows 8/8.1, Windows 10 a Windows Server **2012 se používá aplikace Word.**  V následujících krocích použijeme **aplikaci Word.**  
  
1. Otevřete stránku brány Windows Firewall. (Do pole Hledat v nabídce **Start** zadejte **Windows Firewall**).  
  
2. Klikněte na možnost **povolení aplikace nebo funkce přes bránu Windows Firewall**.  
  
3. V seznamu **povolené aplikace a funkce** vyhledejte **Visual Studio Remote Debugger zjišťování**. Pokud je seznam uveden, ujistěte se, že je vybrán a že je vybrán také jeden nebo více typů sítě.  
  
4. Pokud není v seznamu **Visual Studio Remote Debugger zjišťování** , klikněte na možnost **povolení jiné aplikace**. Pokud se v okně **Přidat aplikaci** pořád nezobrazí, klikněte na **Procházet** a přejděte na ** \<Visual Studio installation directory> \Common7\IDE\Remote Debugger**. Vyhledejte příslušnou složku pro aplikaci (x86, x64, AppX) a pak vyberte **msvsmon.exe**. Pak klikněte na **Přidat**.  
  
5. V seznamu **povolené aplikace a funkce** vyberte možnost **Visual Studio sledování vzdáleného ladění**. Podívejte se na jeden nebo více typů sítí (**doména, domů/práce (privátní), veřejné**), se kterým chcete komunikovat monitor vzdáleného ladění. Typy musí zahrnovat síť, ke které je připojený počítač s Visual Studiem.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Otevření portu v počítači se systémem Visual Studio pro povolení zjišťování  
 Aby bylo možné zjišťování počítačů se spuštěným vzdáleným ladicím programem, je nutné, aby byl příchozí protokol UDP port 3702. Pokud ho chcete přidat, přečtěte si téma Postup konfigurace portů v bráně firewall.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Konfigurace brány Windows firewall vzdáleného počítače pro vzdálené ladění  
 Komponenty vzdáleného ladění mohou být nainstalovány na vzdáleném počítači nebo spouštěny ze sdíleného adresáře. V obou případech je nutné nakonfigurovat bránu firewall vzdáleného počítače. Komponenty vzdáleného ladění jsou umístěny v těchto umístěních:  
  
 **\<Visual Studio installation directory>Ladicí program \Common7\IDE\Remote**  
  
 Pokyny pro konfiguraci brány Windows Firewall se mírně liší v různých operačních systémech. V systému Windows 7 nebo Windows Server 2008 se používá **program** Word. v systému Windows 8/8.1, Windows 10 a Windows Server **2012 se používá aplikace Word.**  V následujících krocích použijeme **aplikaci Word.**  
  
1. Otevřete stránku brány Windows Firewall. (Do pole Hledat v nabídce **Start** zadejte **Windows Firewall**.)  
  
2. Klikněte na možnost **povolení aplikace nebo funkce přes bránu Windows Firewall**.  
  
3. V seznamu **povolené aplikace a funkce** vyhledejte **Visual Studio sledování vzdáleného ladění**. Pokud je seznam uveden, ujistěte se, že je vybrán a že je vybrán také jeden nebo více typů sítě.  
  
4. Pokud není v seznamu **Visual Studio sledování vzdáleného ladění** , klikněte na možnost **povolení jiné aplikace**. Pokud se v **okně Přidat aplikaci**pořád nezobrazí, klikněte na **Procházet** a přejděte na ** \<Visual Studio installation directory> \Common7\IDE\Remote Debugger**. Vyhledejte příslušnou složku pro aplikaci (x86, x64, AppX) a pak vyberte **msvsmon.exe**. Pak klikněte na **Přidat**.  
  
5. V seznamu **povolené aplikace** vyberte možnost **Visual Studio sledování vzdáleného ladění**. Podívejte se na jeden nebo více typů sítí (**doména, domů/práce (privátní), veřejné**), se kterým chcete komunikovat monitor vzdáleného ladění. Typy musí zahrnovat síť, ke které je připojený počítač s Visual Studiem.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění  
  
|**Porty**|**Příchozí/odchozí**|**Protocol (Protokol)**|**Popis**|  
|-|-|-|-|
|3702|Odesílaná|UDP|Vyžaduje se pro zjišťování vzdáleného ladicího programu.|  
|4020||TCP|Pro VS 2015. Číslo portu se zvyšuje o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu Visual Studio Remote Debugger přiřazení portů.|  
|4021||TCP|Pro VS 2015. Číslo portu se zvyšuje o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu Visual Studio Remote Debugger přiřazení portů.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění pomocí spravovaného nebo nativního režimu kompatibility  
  
|**Porty**|**Příchozí/odchozí**|**Protocol (Protokol)**|**Popis**|  
|-|-|-|-|  
|135, 139, 445|Odesílaná|TCP|Povinná hodnota.|  
|137, 138|Odesílaná|UDP|Povinná hodnota.|  
|500, 4500|Odesílaná|UDP|Vyžaduje se, pokud vaše zásady domény vyžadují síťovou komunikaci pomocí protokolu IPSec.|  
|80|Odesílaná|TCP|Vyžaduje se pro ladění webového serveru.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Postup konfigurace portů v bráně Windows Firewall  
  
1. V nabídce **Start** vyhledejte **bránu Windows Firewall s pokročilým zabezpečením**.  
  
2. Klikněte na **příchozí pravidla** nebo **odchozí pravidla** a potom v seznamu **akcí** klikněte na **nové pravidlo** .  
  
3. Na stránce **Typ pravidla** vyberte **port** a pak klikněte na **Další**.  
  
4. Na stránce **protokol a porty** vyberte protokol portu (TCP nebo UDP). Vyberte **konkrétní místní porty** a zadejte jednu nebo více čísel portů, které chcete pro protokol povolit. Čísla oddělujte čárkami. Potom klikněte na **Další**.  
  
5. Na stránce **Akce** vyberte možnost **připojení povolte** a potom klikněte na tlačítko **Další**.  
  
6. Na stránce **profil** vyberte jeden nebo více typů sítě, které chcete pro port povolit. Typ, který vyberete, musí zahrnovat síť, ke které je připojený vzdálený počítač. Potom klikněte na **Další**.  
  
7. Na stránce **název** zadejte název pravidla a potom klikněte na tlačítko **Dokončit**.  
  
8. V seznamu **příchozí pravidla** nebo **odchozí pravidla** by se mělo zobrazit nové pravidlo.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)
