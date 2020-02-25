---
title: Ladit aplikaci, která není součástí řešení sady Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557914"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Ladit aplikaci, která není součástí řešení sady Visual Studio (C++, C#, Visual Basic, F#)

Možná budete chtít ladit aplikaci (soubor *. exe* ), která není součástí řešení sady Visual Studio. Může se jednat o [otevřený projekt složky](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) nebo jste vy nebo někdo jiný, možná aplikaci vytvořili mimo aplikaci Visual Studio, nebo jste aplikaci získali někde jinde.

- V případě otevřeného projektu složky v sadě Visual Studio (který neobsahuje soubor projektu nebo řešení) si přečtěte téma [spuštění a ladění kódu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) nebo C++, v případě [Konfigurace parametrů ladění pomocí souboru Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Pro aplikaci, která neexistuje v aplikaci Visual Studio, je obvyklým způsobem ladění spustit aplikaci mimo aplikaci Visual Studio a pak k ní připojit pomocí příkazu **připojit k procesu** v ladicím programu sady Visual Studio. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Připojení k aplikaci vyžaduje vyžadováno provedení ručních kroků, které pár sekund trvat. Kvůli tomuto zpoždění připojení nepomůže, ladění potíží při spuštění nebo vstupní aplikace, který nečeká na uživatele a rychle skončí.

   V těchto situacích můžete vytvořit projekt Visual Studio EXE pro aplikace, nebo ji naimportovat do existující C#, Visual Basic nebo C++ řešení. Ne všechny programovací jazyky podporují projekty EXE.

>[!IMPORTANT]
>Funkce ladění pro aplikace, které nebylo vytvořené v sadě Visual Studio jsou omezeny, ať už jste připojení k aplikaci nebo ho přidat do řešení sady Visual Studio.
>
>Pokud máte zdrojový kód, nejlepším řešením je import kódu do projektu sady Visual Studio. Potom spusťte sestavení pro ladění aplikace.
>
>Pokud nemáte zdrojový kód a aplikace nemá [ladicí informace](../debugger/how-to-set-debug-and-release-configurations.md) v kompatibilním formátu, jsou dostupné funkce ladění velmi málo.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Chcete-li vytvořit nový projekt EXE pro stávající aplikace

1. V aplikaci Visual Studio vyberte **soubor** > **otevřete** > **projekt**.

1. V dialogovém okně **Otevřít projekt** vyberte možnost **všechny soubory projektu**, pokud ještě není vybraná, v rozevírací nabídce vedle pole **název souboru**.

1. Přejděte k souboru *. exe* , vyberte ho a vyberte **otevřít**.

   Tento soubor objeví nové dočasné řešení sady Visual Studio.

1. Spusťte ladění aplikace výběrem příkazu pro spuštění, jako je **spuštění ladění**, z nabídky **ladění** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Importovat aplikace do existujícího řešení sady Visual Studio

1. C++V aplikaci Visual Studio, nebo Visual Basic otevřené řešení, vyberte soubor > přidat > existující projekt. C#

1. V dialogovém okně **Otevřít projekt** vyberte možnost **všechny soubory projektu**, pokud ještě není vybraná, v rozevírací nabídce vedle pole **název souboru**.

1. Přejděte k souboru *. exe* , vyberte ho a vyberte **otevřít**.

   Soubor se zobrazí jako nový projekt v aktuálním řešení.

1. Když je vybraný nový soubor, spusťte ladění aplikace výběrem příkazu pro spuštění, jako je **spuštění ladění**, z nabídky **ladění** .

### <a name="see-also"></a>Viz také
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Soubory DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))