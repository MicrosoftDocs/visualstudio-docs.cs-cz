---
title: Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b2d047201214e3a7cd4c14c61baa041840decd8
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143317"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit

V tomto dialogovém okně můžete zadat maximální počet Visual C++ nebo C# projekty, které můžete vytvářet ve stejnou dobu, určité výchozí chování, ale taky popustit některé nastavení protokolu sestavení. Zpřístupníte tyto možnosti, vyberte **nástroje > Možnosti** rozbalte **projekty a řešení**a vyberte **sestavíte a spustíte**.

**maximální počet paralelních projektu sestavení**

Určuje maximální počet Visual C++ a C# projekty, které můžete vytvářet ve stejnou dobu. K optimalizaci procesu sestavení, je maximální číslo sestavení paralelního projektu automaticky nastaví počet procesorů počítače. Maximální počet je 32.

**Pouze při spuštění sestavit projekty a závislosti**

Sestavení projektu po spuštění a jeho závislosti, při použití klíče, vyberte F5 **ladit > Spustit** příkaz nabídky nebo použít příkazy na **sestavení** nabídky. Pokud je prázdné, jsou všechny projekty a závislosti sestavení.

**Spustit, pokud projekty jsou zastaralé**

*Platí pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pouze pro projekty.*

Při spuštění projektu pomocí F5 nebo **ladit > Spustit** příkazu, ve výchozím nastavení **zobrazit výzvu k vytvoření** zobrazí zprávu, pokud konfigurace projektu je zastaralý. Vyberte **vždy sestavení** a sestavte projekt pokaždé, když je spuštěn. Vyberte **nikdy nesestavovat** potlačit všechny automatické sestavení při spuštění projektu.

**Při spuštění, při sestavení nebo dojde k chybě nasazení**

*Platí pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pouze pro projekty.*

Při spuštění projektu pomocí F5 nebo **ladit > Spustit** příkazu, ve výchozím nastavení **výzva ke spuštění** zobrazí zprávu, pokud projekt by měl spustit i v případě, že sestavení selhalo. Vyberte **spuštění starší verze** automaticky spustit poslední úspěšný build, což může způsobit neshody mezi spuštěním kódu a zdrojový kód. Vyberte **nespouštět** k potlačení zprávy.

**Nové řešení použít aktuálně zvolený projekt jako spouštěný projekt**

Když nastavíte tuto možnost, nová řešení použít aktuálně zvolený projekt jako spouštěný projekt.

**Podrobnost výstupu sestavení projektu nástroje MSBuild**

Určuje, kolik informací se zobrazí v **výstup** okna pro sestavení.

**Úroveň podrobností MSBuild projektu sestavení protokolu souborů**

*Platí pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pouze pro projekty.*

Určuje, kolik informací je zapsána do souboru protokolu sestavení, které se nacházejí v \\... \\ *ProjectName*\Debug\\*ProjectName*. log.

## <a name="see-also"></a>Viz také:

- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Dialogové okno Možnosti, projekty a řešení](projects-and-solutions-options-dialog-box.md)
- [Dialogové okno Možnosti, Projekty a řešení, Webové projekty](options-dialog-box-projects-and-solutions-web-projects.md)