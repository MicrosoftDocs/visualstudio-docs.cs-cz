---
title: Zobrazení knihoven DLL a spustitelných souborů
description: Zobrazení knihoven DLL a spustitelných souborů (.exe soubory), které vaše aplikace používá v okně moduly během relace ladění v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385406"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Zobrazení knihoven DLL a spustitelných souborů v okně moduly (C#, C++, Visual Basic, F #)

Během ladění sady Visual Studio obsahuje okno **moduly** seznam a zobrazuje informace o knihovnách DLL a spustitelných souborech (*.exe* soubory), které vaše aplikace používá.

> [!NOTE]
> Okno moduly není k dispozici pro ladění SQL nebo skriptu.

## <a name="use-the-modules-window"></a>Použití okna moduly

Chcete-li otevřít okno moduly, při ladění vyberte možnost **ladit**  >  **moduly systému Windows**  >   (nebo stiskněte klávesy **CTRL + ALT + U**).

Ve výchozím nastavení okno **moduly** seřadí moduly podle pořadí načítání. Pokud chcete řadit podle libovolného sloupce okna, vyberte záhlaví v horní části sloupce.

## <a name="load-symbols"></a>Načíst symboly

Sloupec **stav symbolu** v okně **moduly** zobrazuje, které moduly mají načteny symboly ladění. Pokud je stav **přeskočeno načítání symbolů**, **nelze najít nebo otevřít soubor PDB** nebo načíst **zakázané zahrnutím/vyloučením nastavení**, můžete symboly načíst ručně. Další informace o načítání a používání symbolů naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Postup ručního načtení symbolů:**

1. V okně **moduly** klikněte pravým tlačítkem myši na modul, pro který nejsou načteny symboly.

   - Vyberte **informace o načtení symbolů** pro podrobnosti o tom, proč nebyly symboly načteny.

   - Vyberte **načíst symboly** pro ruční načtení symbolů.

1. Pokud symboly nenačtete, vyberte **Nastavení symbolu** a otevřete dialogové okno **Možnosti** a zadejte nebo změňte umístění pro načítání symbolů.

   Můžete si stáhnout symboly z veřejných serverů Microsoft Symbol Servers nebo jiných serverů nebo načíst symboly ze složky v počítači. Podrobnosti najdete v tématu [určení umístění symbolů a chování při načítání](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Změna nastavení chování při načítání symbolů:**

1. V okně **moduly** klikněte pravým tlačítkem na libovolný modul.

1. Vyberte **Nastavení symbolu**.

1. Vyberte **načíst všechny symboly** nebo vyberte moduly, které chcete zahrnout nebo vyloučit.

1. Vyberte **OK**. Změny se projeví v další relaci ladění.

**Změna chování při načítání symbolů pro určitý modul:**

1. V okně **moduly** klikněte pravým tlačítkem na modul.

1. V nabídce kliknutím pravým tlačítkem myši vyberte nebo zrušte výběr **vždy automaticky načíst**. Změny se projeví v další relaci ladění.

## <a name="see-also"></a>Viz také
- [Přerušení provádění](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)