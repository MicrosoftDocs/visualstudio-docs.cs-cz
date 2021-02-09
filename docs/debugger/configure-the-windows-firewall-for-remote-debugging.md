---
title: Konfigurace brány Windows Firewall pro vzdálené ladění | Microsoft Docs
description: Nakonfigurujte bránu Windows Firewall pro vzdálené ladění. Nakonfigurujte porty pro vzdálené ladění. Řešení potíží s připojením vzdáleného ladění.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 959d015bd23c91ec2ba6215c7a5b42d13b37ee29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865823"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Konfigurace brány Windows Firewall pro vzdálené ladění

V síti chráněné bránou Windows Firewall musí být brána firewall nakonfigurovaná tak, aby povolovala vzdálené ladění. Visual Studio a nástroje pro vzdálené ladění se snaží otevřít správné porty brány firewall během instalace nebo po spuštění, ale možná budete muset otevřít taky porty nebo ruční povolení aplikací.

Toto téma popisuje, jak nakonfigurovat bránu Windows Firewall tak, aby povolovala vzdálené ladění ve Windows 10, 8/8.1 a 7. a v počítačích se systémem Windows Server 2012 R2, 2012 a 2008 R2. V aplikaci Visual Studio a ve vzdáleném počítači nemusí běžet stejný operační systém. Například počítač s Visual Studiem může používat systém Windows 10 a vzdálený počítač může používat systém Windows Server 2012 R2.

>[!NOTE]
>Pokyny pro konfiguraci brány Windows Firewall se mírně liší v různých operačních systémech a ve starších verzích Windows. Nastavení Windows 8/8.1, Windows 10 a Windows Server 2012 *používají aplikaci Word, zatímco* Windows 7 a windows Server 2008 používají wordový *program*.

## <a name="configure-ports-for-remote-debugging"></a>Konfigurace portů pro vzdálené ladění

Visual Studio a vzdálený ladicí program se při instalaci nebo spuštění pokusí otevřít správné porty. V některých scénářích, jako je například brána firewall jiného výrobce, možná budete muset porty otevřít ručně.

**Otevření portu:**

1. V nabídce **Start** systému Windows vyhledejte a otevřete **bránu Windows Firewall s pokročilým zabezpečením**. Ve Windows 10 se jedná **o bránu firewall v programu Windows Defender s pokročilým zabezpečením**.

1. Pro nový port pro příchozí spojení vyberte **příchozí pravidla** a pak vyberte **nové pravidlo**. U odchozího pravidla vyberte místo toho **odchozí pravidla** .

1. V Průvodci vytvořením **nového příchozího pravidla** vyberte **port** a pak vyberte **Další**.

1. V závislosti na čísle portu z následujících tabulek vyberte buď **TCP** , nebo **UDP**.

1. V části **konkrétní místní porty** zadejte číslo portu z následujících tabulek a vyberte **Další**.

1. Vyberte možnost **Povolení připojení** a pak vyberte **Další**.

1. Vyberte jeden nebo více typů sítí, které chcete povolit, včetně typu sítě pro vzdálené připojení, a pak vyberte **Další**.

1. Přidejte název pravidla (například **msvsmon**, **IIS** nebo **nasazení webu**) a pak vyberte **Dokončit**.

   Nové pravidlo by se mělo zobrazit a vybrat v seznamu **příchozí pravidla** nebo **odchozí pravidla** .

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění

Pro vzdálené ladění musí být na vzdáleném počítači otevřené následující porty:

::: moniker range="vs-2017"

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|
|-|-|-|-|
|4022|Příchozí|TCP|Pro VS 2017. Číslo portu se zvýší o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Příchozí|TCP|Pro VS 2017. Číslo portu se zvýší o 2 pro každou verzi sady Visual Studio. Tento port se používá pouze pro vzdálené ladění 32 procesu z 64 verze vzdáleného ladicího programu. Další informace najdete v tématu  [Přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Odesílaná|UDP|Volitelné Vyžaduje se pro zjišťování vzdáleného ladicího programu.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|
|-|-|-|-|
|4024|Příchozí|TCP|Pro VS 2019. Číslo portu se zvýší o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Příchozí|TCP|Pro VS 2019. Číslo portu se zvýší o 2 pro každou verzi sady Visual Studio. Tento port se používá pouze pro vzdálené ladění 32 procesu z 64 verze vzdáleného ladicího programu. Další informace najdete v tématu  [Přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Odesílaná|UDP|Volitelné Vyžaduje se pro zjišťování vzdáleného ladicího programu.|

::: moniker-end

Pokud vyberete možnost **použít spravovaný režim kompatibility** v části **nástroje**  >    >  **ladění** možností, otevřete tyto další porty vzdáleného ladicího programu. Režim kompatibility spravovaný ladicím programem povoluje starší verzi sady Visual Studio 2010 ladicího programu.

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|
|-|-|-|-|
|135, 139, 445|Odesílaná|TCP|Povinná hodnota.|
|137, 138|Odesílaná|UDP|Povinná hodnota.|

Pokud vaše zásady domény vyžadují síťovou komunikaci pomocí protokolu IPSec, je nutné otevřít další porty v aplikaci Visual Studio i ve vzdálených počítačích. Chcete-li ladit na vzdáleném webovém serveru služby IIS, otevřete port 80 na vzdáleném počítači.

|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|
|-|-|-|-|
|500, 4500|Odesílaná|UDP|Vyžaduje se, pokud vaše zásady domény vyžadují síťovou komunikaci pomocí protokolu IPSec.|
|80|Odesílaná|TCP|Vyžaduje se pro ladění webového serveru.|

Postup povolení konkrétních aplikací přes bránu Windows Firewall najdete v tématu [Konfigurace vzdáleného ladění prostřednictvím brány Windows Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfigurace vzdáleného ladění přes bránu Windows Firewall

Nástroje pro vzdálené ladění můžete nainstalovat na vzdálený počítač nebo je spouštět ze sdílené složky. V obou případech je nutné správně nakonfigurovat bránu firewall vzdáleného počítače.

Ve vzdáleném počítači jsou nástroje pro vzdálené ladění v:

*\<Visual Studio installation directory\>\\\\ \\ Vzdálený ladicí program IDE Common7\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Povolení a konfigurace vzdáleného ladicího programu přes bránu Windows Firewall

1. V nabídce **Start** systému Windows vyhledejte a otevřete **bránu Windows Firewall** nebo **firewall v programu Windows Defender**.

1. Vyberte možnost **povolení aplikace přes bránu Windows Firewall**.

1. Pokud se **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** nezobrazuje v části **povolené aplikace a funkce**, vyberte **změnit nastavení** a pak vyberte **Povolit jinou aplikaci**.

1. Pokud se aplikace vzdáleného ladicího programu ještě nezobrazuje v dialogovém okně **Přidat aplikaci** , vyberte **Procházet** a přejděte na * \<Visual Studio installation directory\> \\ Common7 \\ \\ vzdáleného ladicího programu IDE \\ \<x86*, *x64*, or *Appx*\> , v závislosti na příslušné architektuře vaší aplikace. Vyberte *msvsmon.exe* a pak vyberte **Přidat**.

1. V seznamu **aplikace** vyberte **vzdálený ladicí program** , který jste právě přidali. Vyberte **typy sítě** a pak vyberte jeden nebo více typů sítí, včetně typu sítě pro vzdálené připojení.

1. Vyberte **Přidat** a pak vyberte **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Řešení potíží s připojením vzdáleného ladění

Pokud se k aplikaci nemůžete připojit pomocí vzdáleného ladicího programu, ujistěte se, že jsou správné porty brány firewall pro vzdálené ladění, protokoly, typy sítě a nastavení aplikace.

- V nabídce **Start** systému Windows vyhledejte a otevřete **bránu Windows Firewall** a vyberte možnost **povolení aplikace přes bránu Windows Firewall**. Ujistěte se, že se **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** zobrazuje v seznamu **povolené aplikace a funkce** s vybraným zaškrtávacím políčkem a jsou vybrány správné typy sítě. Pokud ne, [přidejte správné aplikace a nastavení](#configure-remote-debugging-through-windows-firewall).

- V nabídce **Start** systému Windows vyhledejte a otevřete **bránu Windows Firewall s pokročilým zabezpečením**. Ujistěte se, že se **vzdálený ladicí program** nebo **Visual Studio Remote Debugger** zobrazuje v části **příchozí pravidla** (a volitelně **odchozí pravidla**) se zelenou ikonou zaškrtnutí a že všechna nastavení jsou správná.

  - Chcete-li zobrazit nebo změnit nastavení pravidla, klikněte pravým tlačítkem myši na aplikaci **vzdáleného ladicího programu** v seznamu a vyberte možnost **vlastnosti**. Pomocí karet **vlastnosti** můžete pravidlo Povolit nebo zakázat nebo změnit čísla portů, protokoly nebo typy sítí.
  - Pokud se v seznamu pravidel nezobrazí aplikace vzdáleného ladicího programu, [přidejte a nakonfigurujte správné porty](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Viz také

- [Vzdálené ladění](../debugger/remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu sady Visual Studio](../debugger/remote-debugger-port-assignments.md)
