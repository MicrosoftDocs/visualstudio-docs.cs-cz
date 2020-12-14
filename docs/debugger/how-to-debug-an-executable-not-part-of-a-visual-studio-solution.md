---
title: Ladění aplikace, která není součástí řešení sady Visual Studio
titleSuffix: ''
Description: Naučte se ladit aplikaci, která není součástí řešení sady Visual Studio. Může být možné připojit ladicí program sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
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
ms.openlocfilehash: fd4d5497a4c29502fe4d7e4825b1767991c79298
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398659"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Ladění aplikace, která není součástí řešení sady Visual Studio (C++, C#, Visual Basic, F #)

Možná budete chtít ladit aplikaci (soubor *. exe* ), která není součástí řešení sady Visual Studio. Může se jednat o [otevřený projekt složky](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) nebo jste vy nebo někdo jiný, možná aplikaci vytvořili mimo aplikaci Visual Studio, nebo jste aplikaci získali někde jinde.

- V případě otevřeného projektu složky v aplikaci Visual Studio (který neobsahuje soubor projektu nebo řešení) si přečtěte téma [spuštění a ladění kódu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) nebo v jazyce C++ [Konfigurace parametrů ladění s launch.vs.jsna](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Pro aplikaci, která neexistuje v aplikaci Visual Studio, je obvyklým způsobem ladění spustit aplikaci mimo aplikaci Visual Studio a pak k ní připojit pomocí příkazu **připojit k procesu** v ladicím programu sady Visual Studio. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Připojení k aplikaci vyžaduje ruční kroky, které zabírají několik sekund. Kvůli této prodlevě připojení nepomůže ladit problém při spuštění nebo aplikaci, která nečeká na vstup uživatele a rychle se dokončí.

   V těchto situacích můžete vytvořit projekt aplikace Visual Studio EXE pro aplikaci nebo ho importovat do stávajícího řešení C#, Visual Basic nebo C++. Ne všechny programovací jazyky podporují projekty EXE.

>[!IMPORTANT]
>Funkce ladění pro aplikaci, která není vytvořená v aplikaci Visual Studio, jsou omezené bez ohledu na to, jestli se k aplikaci připojujete nebo ji přidáte do řešení sady Visual Studio.
>
>Pokud máte zdrojový kód, nejlepším přístupem je import kódu do projektu sady Visual Studio. Pak spusťte ladicí sestavení aplikace.
>
>Pokud nemáte zdrojový kód a aplikace nemá [ladicí informace](../debugger/how-to-set-debug-and-release-configurations.md) v kompatibilním formátu, jsou dostupné funkce ladění velmi málo.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Vytvoření nového projektu EXE pro existující aplikaci

1. V aplikaci Visual Studio vyberte **soubor**  >  **otevřít**  >  **projekt**.

1. V dialogovém okně **Otevřít projekt** vyberte možnost **všechny soubory projektu**, pokud ještě není vybraná, v rozevírací nabídce vedle pole **název souboru**.

1. Přejděte k souboru *. exe* , vyberte ho a vyberte **otevřít**.

   Soubor se zobrazí v novém dočasném řešení sady Visual Studio.

1. Spusťte ladění aplikace výběrem příkazu pro spuštění, jako je **spuštění ladění**, z nabídky **ladění** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Import aplikace do existujícího řešení sady Visual Studio

1. Otevřete řešení v jazyce C++, C# nebo Visual Basic otevřené v aplikaci Visual Studio a vyberte **soubor**  >  **Přidat**  >  **existující projekt**.

1. V dialogovém okně **Otevřít projekt** vyberte možnost **všechny soubory projektu**, pokud ještě není vybraná, v rozevírací nabídce vedle pole **název souboru**.

1. Přejděte k souboru *. exe* , vyberte ho a vyberte **otevřít**.

   Soubor se zobrazí jako nový projekt v rámci aktuálního řešení.

1. Když je vybraný nový soubor, spusťte ladění aplikace výběrem příkazu pro spuštění, jako je **spuštění ladění**, z nabídky **ladění** .

### <a name="see-also"></a>Viz také
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Soubory DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))