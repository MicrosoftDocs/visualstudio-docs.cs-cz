---
title: 'Postupy: připojení ke skriptu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 719654916087e7c7f4249ff52abbed628a2c56a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704499"
---
# <a name="how-to-attach-to-script"></a>Postupy: Připojení ke skriptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma vysvětluje, jak ručně připojit ladicí program sady Visual Studio k souboru skriptu pro ladění.  
  
### <a name="to-attach-to-a-running-process"></a>Připojení ke spuštěnému procesu  
  
1. V nabídce **ladění** vyberte možnost **připojit k procesu**. (Pokud není otevřený žádný projekt, v nabídce **nástroje** vyberte možnost **připojit k procesu** .)  
  
2. V dialogovém okně **připojit k procesu** se podívejte na seznam **procesy k dispozici** a vyhledejte proces skriptu, ke kterému se chcete připojit. Procesy skriptu můžete identifikovat tak, že prohlížíte sloupec **typ** .  
  
   1. Pokud je proces, který chcete ladit, spuštěn v jiném počítači, je nejprve nutné vybrat vzdálený počítač. Další informace naleznete v tématu [How to: SELECT a Remote Computer](https://msdn.microsoft.com/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2. Pokud je proces spuštěn pod jiným uživatelským účtem, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .  
  
   3. Pokud jste připojení prostřednictvím **připojení ke vzdálené ploše**, zaškrtněte políčko **Zobrazit procesy ve všech relacích** .  
  
3. Klikněte na proces, ke kterému se chcete připojit.  
  
4. V poli **připojit k** byste měli vidět **kód skriptu** nebo **automaticky: kód skriptu**. Pokud se zobrazí cokoli jiného, postupujte takto:  
  
   1. Klikněte na **Vybrat**.  
  
   2. V dialogovém okně **Vybrat typ kódu** klikněte na možnost **ladit tyto typy kódu** a vyberte možnost **skript**.  
  
   3. Klikněte na **OK**.  
  
5. Klikněte na **připojit**.  
  
    V tomto okamžiku se může zobrazit upozornění, že ladění skriptů je v Internet Exploreru zakázané. Pokud k tomu dojde, přečtěte si téma [Upozornění: ladění skriptů zakázáno](../debugger/warning-script-debugging-disabled.md).  
  
   Seznam **procesy k dispozici** se zobrazí automaticky při otevření dialogového okna **procesy** . Procesy mohou začínat a zastavovat na pozadí, když je dialogové okno otevřeno. Obsah proto nemusí být vždy aktuální. Seznam můžete kdykoli aktualizovat, aby se zobrazil aktuální seznam procesů stisknutím tlačítka **aktualizovat** .  
  
   Můžete být připojeni k více programům při ladění, ale pouze jeden program je v ladicím programu aktivní. Aktivní program můžete nastavit na panelu nástrojů umístění ladění. Další informace najdete v tématu [Postup: nastavení aktuálního procesu](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Všechny příkazy pro spuštění nabídky **ladění** ovlivňují aktivní program. V dialogovém okně procesy můžete všechny laděné programy přerušit. Viz [použití zarážek](../debugger/using-breakpoints.md).  
  
> [!NOTE]
> Pokud se pokusíte připojit k procesu, který je vlastněn nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
 V některých případech se při ladění v relaci Terminálové služby (Vzdálená plocha) nezobrazí v seznamu procesy k dispozici všechny dostupné procesy. [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)]Pokud používáte aplikaci Visual Studio jako omezeného uživatele v systému nebo novějších verzích, v seznamu procesy k dispozici nebude zobrazen proces spuštěný v relaci 0, který se používá pro služby a jiné serverové procesy, včetně w3wp.exe. Problém můžete vyřešit spuštěním sady Visual Studio v rámci účtu správce nebo spuštěním sady Visual Studio z konzoly serveru, nikoli pomocí relace Terminálové služby. Pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu zadáním vsjitdebugger.exe-p ProcessId do příkazového řádku Windows. ID procesu můžete určit pomocí tlist.exe. Chcete-li získat tlist.exe, Stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na webu [Windows Hardware Developer Central](https://developer.microsoft.com/windows/hardware).  
  
## <a name="see-also"></a>Viz také  
 [Ladění skriptů na straně klienta](../debugger/client-side-script-debugging.md)   
 [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Upozornění zabezpečení: připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu.](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)
