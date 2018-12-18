---
title: 'Postupy: připojení ke skriptu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c71364905e121ab32c9f5108717acdca32e1354e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790055"
---
# <a name="how-to-attach-to-script"></a>Postupy: Připojení ke skriptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma vysvětluje, jak ručně připojit ladicí program sady Visual Studio do souboru skriptu pro ladění.  
  
### <a name="to-attach-to-a-running-process"></a>Připojit ke spuštěnému procesu  
  
1. Na **ladění** nabídce zvolte **připojit k procesu**. (Pokud není otevřený žádný projekt, zvolte **připojit k procesu** na **nástroje** nabídky.)  
  
2. V **připojit k procesu** dialogové okno, podívejte se **procesy k dispozici** seznam a vyhledejte zpracovat skript, můžete ke kterému chcete připojit k. Procesy skriptu můžete identifikovat pohledem **typ** sloupce.  
  
   1.  Pokud je proces, který chcete ladit spuštěn na jiném počítači, musíte nejprve vybrat vzdálený počítač. Další informace najdete v tématu [postupy: výběr vzdáleného počítače](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2.  Pokud je proces spuštěn pod účtem jiného uživatele, vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.  
  
   3.  Pokud jste připojeni přes **připojení ke vzdálené ploše**, vyberte **Zobrazit procesy ve všech relacích** zaškrtávací políčko.  
  
3. Klikněte na tlačítko, které chcete připojit k procesu.  
  
4. V **připojit k** pole, měli byste vidět **kód skriptu** nebo **automatické: kód skriptu**. Pokud se zobrazí cokoli jiného, postupujte podle těchto kroků:  
  
   1.  Klikněte na tlačítko **vyberte**.  
  
   2.  V **vybrat typ kódu** dialogové okno, klikněte na tlačítko **ladit tyto typy kódu** a vyberte **skript**.  
  
   3.  Klikněte na tlačítko **OK**.  
  
5. Klikněte na tlačítko **připojit**.  
  
    V tomto okamžiku může zobrazit upozornění oznamující, že je v aplikaci Internet Explorer zakázáno ladění skriptů. Pokud k tomu dojde, přečtěte si téma [upozornění: ladění skriptů zakázáno](../debugger/warning-script-debugging-disabled.md).  
  
   **Procesy k dispozici** seznam se automaticky zobrazí při otevření **procesy** dialogové okno. Procesy můžete spouštět a zastavovat na pozadí při otevřeném dialogovém okně. Proto obsah nemusí být vždy aktuální. Můžete aktualizovat seznam kdykoli zobrazit aktuální seznam procesů stisknutím kombinace kláves **aktualizovat** tlačítko.  
  
   Můžete být připojení k více programům při ladění, ale pouze jeden program je v každém okamžiku aktivní v ladicím programu. Nastavit aktivní program na panelu nástrojů umístění ladění. Další informace najdete v tématu [postupy: nastavení aktuálního procesu](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Všechny **ladění** provádění příkazy vliv na aktivní program. V dialogovém okně procesy můžete přerušit všechny ladícího programu. Zobrazit [pomocí zarážek](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Pokud se pokusíte připojit k procesu, který je vlastněn nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu [upozornění zabezpečení: připojení k procesu vlastněnému nedůvěryhodným uživatelským může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 V některých případech při ladění v relaci Terminálové služby (Vzdálená plocha), seznam dostupných procesů nezobrazí všechny procesy k dispozici. Na [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] nebo novější verze, pokud používáte sadu Visual Studio jako uživatel s omezenými právy, seznam dostupných procesů nezobrazí procesy spuštěné v relaci 0, které se používá pro služby a ostatních serverové procesy, včetně w3wp.exe. Problém můžete vyřešit spuštěním sady Visual Studio pod administrátorským účtem nebo pomocí sady Visual Studio z konzoly serveru místo relace Terminálové služby. Pokud ani jeden z těchto řešení je možné, třetí možnost je připojit k procesu tak, že zadáte vsjitdebugger.exe -p ProcessId na příkazovém řádku Windows. Id procesu můžete určit pomocí tlist.exe. Chcete-li získat tlist.exe, stáhněte a nainstalujte ladění nástroje pro Windows, k dispozici na [Windows Hardware pro vývojáře centrální](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Viz také  
 [Ladění skriptů na straně klienta](../debugger/client-side-script-debugging.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)



