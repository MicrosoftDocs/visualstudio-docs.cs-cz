---
title: Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461397"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Dialogové okno Možnosti: \> Projekty a řešení se staví a spouštějí

V tomto dialogovém okně můžete zadat maximální počet c++ nebo C# projekty, které můžete sestavit současně, některé výchozí chování sestavení a některá nastavení protokolu sestavení. Chcete-li získat přístup k těmto možnostem, vyberte**možnost Možnosti** **nástrojů** > rozbalit **položku Projekty a řešení**a pak vyberte Příkaz Sestavit a **spustit**.

**Maximální počet paralelních sestavení projektu**

Určuje maximální počet c++ a C# projekty, které lze sestavit současně. Chcete-li optimalizovat proces sestavení, maximální počet paralelních sestavení projektu je automaticky nastaven na počet procesorů počítače. Maximum je 32.

**Vytvářejte pouze projekty po spuštění a závislosti na spuštění**

Vytvoří pouze spouštěcí projekt a jeho závislosti při použití klávesy **F5,** **příkazu** > nabídky**Ladění ladění** start nebo příslušných příkazů v nabídce **Sestavení.** Pokud není zaškrtnuto, jsou vytvořeny všechny projekty a závislosti.

**Při spuštění, když jsou projekty zastaralé**

*Platí pouze pro projekty jazyka C++.*

Při spuštění projektu s **příkazem F5** nebo **příkazu** > Ladění**zahájit ladění** se zobrazí výchozí nastavení **Prompt pro sestavení** zprávy, pokud je konfigurace projektu zastaralá. Vyberte **vždy sestavit** sestavit projekt při každém spuštění. Vyberte **Nikdy sestavovat** potlačit všechny automatické sestavení při spuštění projektu.

**Při spuštění, když dojde k chybám sestavení nebo nasazení**

*Platí pouze pro projekty jazyka C++.*

Při spuštění projektu s **příkazem F5** nebo **ladění** > **start ladění,** výchozí nastavení **Prompt ke spuštění** zobrazí zprávu, pokud projekt by měl být spuštěn i v případě, že sestavení se nezdařilo. Vyberte **Spustit starou verzi,** chcete-li automaticky spustit poslední dobrou sestavu, což může mít za následek neshody mezi spuštěný kód a zdrojový kód. Výběrem **možnosti Nespouštět** zprávu potlačíte.

**Pro nová řešení použijte aktuálně vybraný projekt jako spouštěcí projekt**

Pokud je tato možnost nastavena, nová řešení používají jako spouštěcí projekt aktuálně vybraný projekt.

**Podrobnost výstupu sestavení projektu MSBuild**

Určuje, kolik informací z procesu sestavení se zobrazí v okně **Výstup.**

**Podrobnost souboru protokolu sestavení projektu MSBuild**

*Platí pouze pro projekty jazyka C++.*

Určuje, kolik informací je zapsáno do souboru protokolu sestavení, který je umístěn na adrese * \\ \<ProjectName\\\<>\Debug ProjectName>.log*.

## <a name="see-also"></a>Viz také

- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Dialogové okno Možnosti, projekty a řešení](projects-and-solutions-options-dialog-box.md)
- [Dialogové okno Možnosti, Projekty a řešení, Webové projekty](options-dialog-box-projects-and-solutions-web-projects.md)