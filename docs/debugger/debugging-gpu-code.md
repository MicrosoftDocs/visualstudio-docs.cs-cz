---
title: Ladění kódu GPU | Microsoft Docs
description: Přečtěte si o ladění kódu C++, který běží na grafickém procesoru (GPU) v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19191d8d46e17da52b13f692db605168b06b38d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872674"
---
# <a name="debugging-gpu-code"></a>Ladění kódu GPU
Můžete ladit kód jazyka C++, který je spuštěn na grafické jednotce procesoru (GPU). Podpora ladění GPU v aplikaci Visual Studio zahrnuje detekci časování, spouštění procesů a připojování k nim a integraci do ladicích oken.

## <a name="supported-platforms"></a>Podporované platformy
 Ladění je podporováno v systémech [!INCLUDE[win7](../debugger/includes/win7_md.md)] , [!INCLUDE[win8](../debugger/includes/win8_md.md)] , Windows 10 [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] , [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] a Windows Server 2016. Pro ladění v emulátoru softwaru se [!INCLUDE[win8](../debugger/includes/win8_md.md)] vyžaduje Windows 10 nebo [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] windows Server 2016. Pro ladění na hardwaru je nutné nainstalovat ovladače pro grafickou kartu. Ne všichni dodavatelé hardwaru implementují všechny funkce ladicího programu. Omezení najdete v dokumentaci dodavatele.

> [!NOTE]
> Nezávislí výrobci hardwaru, kteří chtějí podporovat ladění GPU v aplikaci Visual Studio, musí vytvořit knihovnu DLL, která implementuje rozhraní VSD3DDebug a cílí na jejich vlastní ovladače.

## <a name="configuring-gpu-debugging"></a>Konfigurace ladění GPU
 Ladicí program nemůže v rámci stejného spuštění aplikace přerušit u kódu procesoru a kódu GPU. Ve výchozím nastavení se ladicí program přerušuje na kód procesoru. Chcete-li ladit kód GPU, použijte jeden z těchto dvou kroků:

- V seznamu **typ ladění** na panelu nástrojů **standardní** vyberte možnost **pouze GPU**.

- V **Průzkumník řešení** v místní nabídce projektu vyberte možnost **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte možnost **ladění** a pak vyberte možnost **GPU pouze** v seznamu **Typ ladicího programu** .

## <a name="launching-and-attaching-to-applications"></a>Spouštění a připojování k aplikacím
 Pomocí příkazů ladění sady Visual Studio můžete spustit a zastavit ladění GPU. Další informace naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md). Také je možné připojit ladicí program GPU ke spuštěnému procesu, ale pouze v případě, že tento proces spustí kód GPU. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Spustit aktuální dlaždici ke kurzoru a spustit ke kurzoru
 Při ladění na GPU máte dvě možnosti, jak spustit do umístění kurzoru. Příkazy pro obě možnosti jsou k dispozici v místní nabídce editoru kódu.

1. Příkaz **spustit do kurzoru** spustí vaši aplikaci, dokud nedosáhne pozice kurzoru a potom se přeruší. To neznamená, že aktuální vlákno běží na kurzor; místo toho znamená, že první vlákno, které dosáhne bodu kurzoru, vyvolá přerušení. Viz [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)

2. Příkaz **Spustit aktuální dlaždici ke kurzoru** spustí vaši aplikaci, dokud všechna vlákna v aktuální dlaždici nedosáhne kurzoru a potom se přeruší.

## <a name="debugging-windows"></a>Okna ladění
 Pomocí některých oken ladění můžete prozkoumat, opatřit příznakem a zablokovat vlákna GPU. Další informace naleznete v tématu:

- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)

- [Používání okna úloh](../debugger/using-the-tasks-window.md)

- [Postupy: použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md)

- [Ladit vlákna a procesy](../debugger/debug-threads-and-processes.md) (panel nástrojů umístění ladění)

- [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>Výjimky synchronizace dat
 Ladicí program může během provádění identifikovat několik podmínek synchronizace dat. Když je zjištěna podmínka, ladicí program vstoupí do stavu přerušení. Máte dvě možnosti –**přerušit** nebo **pokračovat**. Pomocí dialogového okna **výjimky** můžete nakonfigurovat, zda ladicí program detekuje tyto podmínky a také podmínky, pro které bude přerušen. Další informace naleznete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md). Můžete také použít dialogové okno **Možnosti** , chcete-li určit, že ladicí program by měl ignorovat výjimky, pokud data, která jsou zapsána, nezmění hodnotu dat. Další informace naleznete v části [Obecné, ladění, dialogové okno Možnosti](../debugger/general-debugging-options-dialog-box.md).

## <a name="troubleshooting"></a>Řešení potíží

### <a name="specifying-an-accelerator"></a>Určení akcelerátoru
 Zarážky v kódu GPU jsou k dispozice pouze v případě, že kód je spuštěn v akcelerátoru [akcelerátor::d irect3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) (ref). Pokud ve svém kódu nezadáte akcelerátor, je referenční akcelerátor automaticky vybrán jako **typ akcelerátoru ladění** ve vlastnostech projektu. Pokud kód explicitně vybere akcelerátor, pak referenční akcelerátor nebude použit během ladění a zarážky nebudou k dispozice, pokud hardware GPU nepodporuje ladění. To lze napravit psaním kódu tak, aby při ladění používal akcelerátor REF. Další informace naleznete v tématu Vlastnosti projektu a [použití akcelerátoru a Accelerator_view objektů](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) a [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="conditional-breakpoints"></a>Podmíněné zarážky
 Podmíněné zarážky v kódu GPU jsou podporované, ale ne každý výraz se dá na zařízení vyhodnotit. Pokud výraz nejde vyhodnotit na zařízení, vyhodnotí se v ladicím programu. Ladicí program může běžet pomaleji než zařízení.

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Chyba: došlo k potížím s konfigurací vybraného typu akcelerátoru ladění.
 K této chybě dochází, pokud dojde k nekonzistenci mezi nastavením projektu a konfigurací počítače, na kterém ladíte. Další informace naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Chyba: ovladač ladění pro vybraný typ akcelerátoru ladění není v cílovém počítači nainstalován.
 K této chybě dochází, pokud provádíte ladění na vzdáleném počítači. Ladicí program nemůže určit, do kdy spustit, zda jsou ovladače nainstalovány na vzdáleném počítači. Ovladače jsou k dispozici od výrobce grafické karty.

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Chyba: zjišťování časový limit a obnovení (TDR) musí být zakázáno ve vzdálené lokalitě.
 Je možné, že C++ AMP výpočty překračují výchozí časový interval, který je nastavený při detekci a procesu obnovení časového limitu systému Windows (TDR). Pokud k tomu dojde, bude výpočet zrušen a data budou ztracena. Další informace najdete v tématu [zpracování TDRS v C++ amp](/archive/blogs/nativeconcurrency/handling-tdrs-in-c-amp).

## <a name="see-also"></a>Viz také
- [Návod: ladění aplikace C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Spuštění ladění GPU v aplikaci Visual Studio](/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)