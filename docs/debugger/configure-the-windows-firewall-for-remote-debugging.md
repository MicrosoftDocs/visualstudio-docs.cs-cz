---
title: Konfigurace brány Windows Firewall pro vzdálené ladění | Dokumentace Microsoftu
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da505c6193dd7d05cc10a8e7cec8383f8ee3adfc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058594"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Konfigurace brány Windows Firewall pro vzdálené ladění

V síti chráněné bránou Windows Firewall brána firewall musí být nakonfigurovaný tak, aby povolovala vzdálené ladění. Visual Studio a nástroje pro vzdálené ladění zkuste otevřít porty brány firewall na správné během instalace nebo spuštění, ale může také třeba otevřít porty nebo ručně povolit aplikacím. 

Toto téma popisuje postup konfigurace brány Windows firewall pro povolení vzdáleného ladění na Windows 10, 8 a 8.1 a 7; a počítače Windows Server 2012 R2, 2012 a 2008 R2. Visual Studio a vzdálený počítač nemusí běžet stejný operační systém. Například v počítači s Visual Studio můžete spustit Windows 10 a vzdáleného počítače můžete spustit systém Windows Server 2012 R2.      
  
>[!NOTE]
>Pokyny ke konfiguraci brány Windows firewall se mírně liší v různých operačních systémech a pro starší verze systému Windows. Nastavení systému Windows 8 a 8.1, Windows 10 a Windows Server 2012 pomocí slova *aplikace*, zatímco Windows 7 a Windows Server 2008 pomocí slova *program*.  

## <a name="configure-ports-for-remote-debugging"></a>Konfigurace portů pro vzdálené ladění  

Visual Studio a vzdálený ladicí program se pokusí otevřít správné porty během instalace nebo spuštění. Nicméně v některých scénářích, jako je brána firewall jiného výrobce, budete muset ručně otevřít porty. 

**Otevření portu:**
  
1. Ve Windows **Start** nabídky, vyhledejte a otevřete **brány Windows Firewall s pokročilým zabezpečením**. V systému Windows 10, je to **Windows Defender Firewall s pokročilým zabezpečením**.
   
1. Nový příchozí port, vyberte **příchozí pravidla** a pak vyberte **nové pravidlo**. Odchozí pravidla, vyberte **odchozí pravidla** místo.

1. V **pravidla Průvodce vytvořením nového příchozího**vyberte **Port**a pak vyberte **Další**. 
   
1. Vyberte buď **TCP** nebo **UDP**, v závislosti na číslo portu z následující tabulky.
   
1. V části **určité místní porty**, zadejte číslo portu z následující tabulky a vyberte **Další**.
   
1. Vyberte **povolit připojení**a pak vyberte **Další**.
   
1. Vyberte jeden nebo více typů sítě, které chcete povolit, včetně typu sítě pro vzdálené připojení a pak vyberte **Další**.
   
1. Přidání názvu pravidla (třeba **msvsmon**, **IIS**, nebo **Webdeploy**) a pak vyberte **Dokončit**.

   Nové pravidlo by se měla zobrazit a vybrat v **příchozí pravidla** nebo **odchozí pravidla** seznamu.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění

Pro vzdálené ladění, je třeba otevřít na vzdáleném počítači následující porty:

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|   
|-|-|-|-|
|4022|příchozí|TCP|Pro sady VS 2017. Port číslo zvýší o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu [přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).|  
|4023|příchozí|TCP|Pro sady VS 2017. Port číslo zvýší o 2 pro každou verzi sady Visual Studio. Toto je pouze použité pro vzdálené ladění 32bitový proces z 64bitovou verzi vzdáleného ladicího programu. Další informace najdete v tématu [přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).| 
|3702|Odchozí|UDP|(Volitelné) Vyžaduje se pro zjišťování vzdálený ladicí program.|    
  
Pokud vyberete **použít spravovaný režim kompatibility** pod **nástroje** > **možnosti** > **ladění**Open Tyto porty další vzdálený ladicí program. Spravovaný režim kompatibility ladicí program umožňuje starší verze, Visual Studio 2010 verze ladicího programu. 

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|  
|-|-|-|-|  
|135, 139, 445|Odchozí|TCP|Požadováno.|  
|137, 138|Odchozí|UDP|Požadováno.|  

Pokud zásady vaší domény vyžadují síťové komunikace, která se má provést prostřednictvím protokolu IPSec, je nutné otevřít další porty v sadě Visual Studio i vzdálených počítačích. Chcete-li ladit na vzdálený webový server IIS, otevřete port 80 na vzdáleném počítači.

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|  
|-|-|-|-|  
|500, 4500|Odchozí|UDP|Povinné, pokud zásady vaší domény vyžadují síťové komunikace, která se má provést prostřednictvím protokolu IPSec.|  
|80|Odchozí|TCP|Vyžaduje se pro ladění webového serveru.|

Pokud chcete povolit konkrétní aplikace přes bránu Windows firewall, najdete v článku [konfigurovat vzdálené ladění přes bránu Windows Firewall](#configure-remote-debugging-through-windows-firewall). 

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfigurovat vzdálené ladění přes bránu Windows firewall

Můžete nainstalovat nástroje vzdálené ladění na vzdáleném počítači nebo spustit ze sdílené složky. V obou případech se musí správně nakonfigurovat brány firewall na vzdáleném počítači. 

Na vzdáleném počítači v jsou vzdálené ladicí nástroje:  
  
*\<Visual Studio Instalační adresář\>\\Common7\\IDE\\vzdálený ladicí program\\\<x86*, *x64*, nebo  *Appx*\> 
  
### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Povolit a konfigurovat vzdálený ladicí program přes bránu Windows Firewall 
  
1. Ve Windows **Start** nabídky, vyhledejte a otevřete **brány Windows Firewall**, nebo **firewallu v programu Windows Defender**. 
  
1. Vyberte **aplikace přes bránu Windows Firewall povolit**.  
  
1.  Pokud **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** nezobrazí v části **povolené aplikace a funkce**vyberte **změnit nastavení**a pak vyberte **jiné aplikace bude**. 

1.  Pokud aplikace vzdálený ladicí program stále není uvedená v **přidat aplikaci** dialogového okna, vyberte **Procházet**a přejděte do  *\<instalačního adresáře sady Visual Studio\> \\Common7\\IDE\\vzdálený ladicí program\\\<x86*, *x64*, nebo *Appx* \> , v závislosti na příslušnou architekturu pro vaši aplikaci. Vyberte *msvsmon.exe*a pak vyberte **přidat**.  
    
1.  V **aplikace** seznamu, vyberte **vzdálený ladicí program** , který jste právě přidali. Vyberte **typy síťového**a pak vyberte jeden nebo více typů sítě, včetně typu sítě pro vzdálené připojení. 
    
1.  Vyberte **přidat**a pak vyberte **OK**.

## <a name="troubleshooting"></a>Řešení potíží s připojení pro vzdálené ladění
  
Pokud se vzdálený ladicí program se nelze připojit k vaší aplikaci, ujistěte se, že vzdálené ladění porty brány firewall, protokoly, typy sítí a nastavení aplikace jsou správně. 

- V Windows **Start** nabídky, vyhledejte a otevřete **brány Windows Firewall**a vyberte **aplikace přes bránu Windows Firewall povolit**. Ujistěte se, že **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** se zobrazí v **povolené aplikace a funkce** se seznam s zaškrtnuté políčko a typy správná síť Vybrat. V opačném případě [správné aplikace a nastavení](#configure-remote-debugging-through-windows-firewall).
  
- V Windows **Start** nabídky, vyhledejte a otevřete **brány Windows Firewall s pokročilým zabezpečením**. Ujistěte se, že **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** se zobrazí v části **příchozí pravidla** (a volitelně také **odchozí pravidla**) s ikonou zelené zaškrtnutí a že všechna nastavení jsou správné. 
  
  - Zobrazit nebo změnit nastavení pravidel, klikněte pravým tlačítkem myši **vzdálený ladicí program** aplikace v seznamu a vyberte **vlastnosti**. Použití **vlastnosti** karty k povolení nebo zakázání pravidla nebo změnit port čísla, protokoly nebo typy sítě. 
  - Pokud aplikace vzdálený ladicí program se nezobrazí v seznamu pravidel [přidat a nakonfigurovat správné porty](#configure-ports-for-remote-debugging). 

## <a name="see-also"></a>Viz také:  
[Vzdálené ladění](../debugger/remote-debugging.md)

[Přiřazení portů vzdáleného ladicího programu služby Visual Studio](../debugger/remote-debugger-port-assignments.md)
