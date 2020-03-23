---
title: IntelliSense
description: Informace o používání technologie IntelliSense v Sadě Visual Studio for Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405810"
---
# <a name="intellisense"></a>IntelliSense

Technologie IntelliSense poskytuje několik funkcí, které pomáhají zlepšit zážitek z psaní a úprav kódu. Například kromě dokončení kódu modul IntelliSense také poskytuje seznamy členů, informace o parametrech a rychlé informace.

V sadě Visual Studio for Mac je technologie IntelliSense poskytována službou základního editoru a je podporována v mnoha jazycích, jako je Například C#, XAML, F#, JavaScript a další. Visual Studio for Mac také obsahuje pokročilé funkce Technologie IntelliSense, jako je možnost zobrazit dokončení z knihoven, které ještě nejsou importovány do projektu.

## <a name="code-completion"></a>Dokončení kódu

Při psaní v podporovaném souboru, jako je například soubor kódu Jazyka C#, budou platné dokončení řetězce, který právě zadáváte, zobrazeno v seznamu dokončení a aktualizováno při psaní. Kromě toho, pokud odstraníte text, seznam bude opět automaticky aktualizovat tak, aby zahrnovala širší rozsah možností pro dokončení daného řetězce. 

Okno dokončení také nabízí podporu pro filtrování zahrnuté dokončení podle typu. Například je možné omezit členy seznamu pouze představují typy, jako jsou třídy nebo delegáti. Tento proces filtrování lze povolit buď kliknutím na konkrétní ikonu představující typ, který bude filtrován, nebo pomocí klávesových zkratek odpovídajících danému typu. Ikony, které jsou umístěny v dolní části okna dokončení, jsou následující:

| Ikona                         | Name (Název)          | Klíčové slovo    | Hotkey |
| -----------------------------|---------------| -----------|--------|
| ![Ikona tříd](media/classes-icon.png)  | třída         | `class`    |  啦 C
| ![Ikona konstanta](media/constant-icon.png) |  – konstanta      | `const`    |  啦 O
| ![Ikona delegáta](media/delegate-icon.png) | delegát      | `delegate` |  V D
| ![Ikona výčtu](media/enums-icon.png)    | enum          | `enum`     |  啦 E
| ![Ikona události](media/event-icon.png)    | event         |            |  V
| ![Ikona pole](media/fields-icon.png)   | pole         |            |  F
| ![Ikona rozhraní](media/interface-icon.png)| rozhraní     | `interface`|  ZI
| ![Ikona klíčového slova](media/keyword-icon.png)  | klíčové slovo       |            |  啦 K
| ![Ikona metody](media/method-icon.png)   | method        |            |  啦 M
| ![Ikona oboru názvů](media/namespace-icon.png)| Obor názvů     | `namespace`|  V N
| ![Ikona rekvizity](media/props-icon.png)    | property      |            |  啦 P
| ![Ikona úryvku](media/snippet-icon.png)  | Úryvek       | `class`    |  啦 S
| ![Ikona struktury](media/struct-icon.png)   | – struktura     | `struct`   |  啦 S

Kliknutím na některou z ikon nebo stisknutím odpovídajících klávesových zkratek se seznam dokončení omezí pouze na typy definované sadou filtrů.  

![Filtrování typu Intellisense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Okno parametru

Další funkcí technologie IntelliSense je možnost poskytnout seznam parametrů tam, kde je to vhodné. Seznam parametrů obsahuje podrobnosti o podpisech metody pro volaný kód. Kliknutím na šipky nahoru/dolů v podpisu můžete cykonoběhat každý z dostupných podpisů parametrů a určit nejvhodnější pro vaše potřeby. Kromě podrobností o typech povolených dat může být také popis definovaný v cílové metodě prostřednictvím komentářů XML.

![Seznam parametrů](media/intellisense-parameter.png)

Při vyplňování parametrů bude parametr, který právě upravujete, označen tučným písmem, zatímco neaktivní parametry budou mít standardní hmotnost. 


## <a name="triggering-completion-window-and-parameter-window"></a>Spuštění okna a parametru dokončení

Okno dokončení se spustí automaticky při psaní do zdrojového souboru. Okno dokončení však můžete také spustit `control-space`pomocí zástupce . Tato kombinace kláves způsobí, že seznam dokončení se zobrazí na aktuální pozici vašeho stříšky. 

Můžete také ručně aktivovat vzhled okna parametru `control-shift-space`zadáním . Pokud je vaše stříška v pozici, která je platná pro seznam parametrů, seznam parametrů se zobrazí v blízkosti pozice stříšky.

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoringový kód (Visual Studio v systému Windows)](/visualstudio/ide/refactoring-in-visual-studio)
