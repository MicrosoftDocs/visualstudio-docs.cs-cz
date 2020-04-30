---
title: Ladění kódu GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c57fab57b4f9baf24212e2806d6d4acd913dff91
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586732"
---
# <a name="debugging-gpu-code"></a>Ladění kódu GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete ladit kód jazyka C++, který je spuštěn na grafické jednotce procesoru (GPU). Podpora ladění GPU v aplikaci Visual Studio zahrnuje detekci časování, spouštění procesů a připojování k nim a integraci do ladicích oken.  
  
## <a name="supported-platforms"></a>Podporované platformy  
 Ladění je podporováno v [!INCLUDE[win7](../includes/win7-md.md)]systémech [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)], a [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Pro ladění v emulátoru softwaru, [!INCLUDE[win8](../includes/win8-md.md)]nebo [!INCLUDE[winserver8](../includes/winserver8-md.md)] je vyžadován. Pro ladění na hardwaru je nutné nainstalovat ovladače pro grafickou kartu. Ne všichni dodavatelé hardwaru implementují všechny funkce ladicího programu. Omezení najdete v dokumentaci dodavatele.  
  
> [!NOTE]
> Nezávislí výrobci hardwaru, kteří chtějí podporovat ladění GPU v aplikaci Visual Studio, musí vytvořit knihovnu DLL, která implementuje rozhraní VSD3DDebug a cílí na jejich vlastní ovladače.  
  
## <a name="configuring-gpu-debugging"></a>Konfigurace ladění GPU  
 Ladicí program nemůže v rámci stejného spuštění aplikace přerušit u kódu procesoru a kódu GPU. Ve výchozím nastavení se ladicí program přerušuje na kód procesoru. Chcete-li ladit kód GPU, použijte jeden z těchto dvou kroků:  
  
- V seznamu **typ ladění** na panelu nástrojů **standardní** vyberte možnost **pouze GPU**.  
  
- V **Průzkumník řešení**v místní nabídce projektu vyberte možnost **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte možnost **ladění**a pak vyberte možnost **GPU pouze** v seznamu **Typ ladicího programu** .  
  
## <a name="launching-and-attaching-to-applications"></a>Spouštění a připojování k aplikacím  
 Pomocí příkazů ladění sady Visual Studio můžete spustit a zastavit ladění GPU. Další informace naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md). Také je možné připojit ladicí program GPU ke spuštěnému procesu, ale pouze v případě, že tento proces spustí kód GPU. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Spustit aktuální dlaždici ke kurzoru a spustit ke kurzoru  
 Při ladění na GPU máte dvě možnosti, jak spustit do umístění kurzoru. Příkazy pro obě možnosti jsou k dispozici v místní nabídce editoru kódu.  
  
1. Příkaz **spustit do kurzoru** spustí vaši aplikaci, dokud nedosáhne pozice kurzoru a potom se přeruší. To neznamená, že aktuální vlákno běží na kurzor; místo toho znamená, že první vlákno, které dosáhne bodu kurzoru, vyvolá přerušení. Viz [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)  
  
2. Příkaz **Spustit aktuální dlaždici ke kurzoru** spustí vaši aplikaci, dokud všechna vlákna v aktuální dlaždici nedosáhne kurzoru a potom se přeruší.  
  
## <a name="debugging-windows"></a>Okna ladění  
 Pomocí některých oken ladění můžete prozkoumat, opatřit příznakem a zablokovat vlákna GPU. Další informace naleznete v tématu:  
  
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)  
  
- [Použití okna úloh](../debugger/using-the-tasks-window.md)  
  
- [Postupy: použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md)  
  
- [Ladit vlákna a procesy](../debugger/debug-threads-and-processes.md) (panel nástrojů umístění ladění)  
  
- [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Výjimky synchronizace dat  
 Ladicí program může během provádění identifikovat několik podmínek synchronizace dat. Když je zjištěna podmínka, ladicí program vstoupí do stavu přerušení. Máte dvě možnosti –**přerušit** nebo **pokračovat**. Pomocí dialogového okna **výjimky** můžete nakonfigurovat, zda ladicí program detekuje tyto podmínky a také podmínky, pro které bude přerušen. Další informace naleznete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md). Můžete také použít dialogové okno **Možnosti** , chcete-li určit, že ladicí program by měl ignorovat výjimky, pokud data, která jsou zapsána, nezmění hodnotu dat. Další informace naleznete v části [Obecné, ladění, dialogové okno Možnosti](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="troubleshooting"></a>Řešení potíží  
  
### <a name="specifying-an-accelerator"></a>Určení akcelerátoru  
 Zarážky v kódu GPU jsou k dispozice pouze v případě, že kód je spuštěn v akcelerátoru [akcelerátor::d irect3d_ref](https://msdn.microsoft.com/library/a514b1a7-3b3f-4011-be6c-f7b0d9a42663) (ref). Pokud ve svém kódu nezadáte akcelerátor, je referenční akcelerátor automaticky vybrán jako **typ akcelerátoru ladění** ve vlastnostech projektu. Pokud kód explicitně vybere akcelerátor, pak referenční akcelerátor nebude použit během ladění a zarážky nebudou k dispozice, pokud hardware GPU nepodporuje ladění. To lze napravit psaním kódu tak, aby při ladění používal akcelerátor REF. Další informace naleznete v tématu Vlastnosti projektu a [použití akcelerátoru a Accelerator_view objektů](https://msdn.microsoft.com/library/18f0dc66-8236-4420-9f46-1a14f2c3fba1) a [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Podmíněné zarážky  
 Podmíněné zarážky v kódu GPU jsou podporované, ale ne každý výraz se dá na zařízení vyhodnotit. Pokud výraz nejde vyhodnotit na zařízení, vyhodnotí se v ladicím programu. Ladicí program může běžet pomaleji než zařízení.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Chyba: došlo k potížím s konfigurací vybraného typu akcelerátoru ladění.  
 K této chybě dochází, pokud dojde k nekonzistenci mezi nastavením projektu a konfigurací počítače, na kterém ladíte. Další informace naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Chyba: ovladač ladění pro vybraný typ akcelerátoru ladění není v cílovém počítači nainstalován.  
 K této chybě dochází, pokud provádíte ladění na vzdáleném počítači. Ladicí program nemůže určit, do kdy spustit, zda jsou ovladače nainstalovány na vzdáleném počítači. Ovladače jsou k dispozici od výrobce grafické karty.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Chyba: zjišťování časový limit a obnovení (TDR) musí být zakázáno ve vzdálené lokalitě.  
 Je možné, že C++ AMP výpočty překračují výchozí časový interval, který je nastavený při detekci a procesu obnovení časového limitu systému Windows (TDR). Pokud k tomu dojde, bude výpočet zrušen a data budou ztracena. Další informace najdete v tématu [zpracování TDRS v C++ amp](https://blogs.msdn.com/b/nativeconcurrency/archive/2012/03/07/handling-tdrs-in-c-amp.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Návod: ladění aplikace C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Spuštění ladění GPU v aplikaci Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)
