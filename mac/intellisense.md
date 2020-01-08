---
title: IntelliSense
description: Informace o použití IntelliSense v Visual Studio pro Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405810"
---
# <a name="intellisense"></a>IntelliSense

Technologie IntelliSense poskytuje několik funkcí, které vám pomůžou zlepšit možnosti psaní a úprav kódu. Například kromě dokončování kódu poskytuje modul IntelliSense také seznamy členů, informace o parametrech a rychlé informace.

V Visual Studio pro Mac je technologie IntelliSense poskytována pomocí základní služby editoru a je podporována v mnoha jazycích, například C#XAML, F#, JavaScript a dalších. Visual Studio pro Mac také obsahuje pokročilé funkce technologie IntelliSense, jako je například schopnost zobrazit dokončování z knihoven, které ještě nejsou naimportovány do projektu.

## <a name="code-completion"></a>Dokončování kódu

Při psaní v rámci podporovaného souboru, jako je C# například soubor kódu, se v seznamu pro doplňování zobrazí platné dokončování pro řetězec, který právě píšete a který se aktualizuje při psaní. Kromě toho, pokud odstraníte text, seznam se znovu automaticky aktualizuje, aby zahrnoval širší rozsah možností pro dokončení daného řetězce. 

Okno dokončení také nabízí podporu pro filtrování zahrnutých dokončení podle typu. Například je možné omezit členy seznamu tak, aby představovaly pouze typy, jako jsou třídy nebo Delegáti. Tento proces filtrování lze povolit buď kliknutím na konkrétní ikonu představující typ, který bude filtrován nebo prostřednictvím klávesových zkratek, které odpovídají danému typu. Ikony, které jsou umístěny v dolní části okna dokončení, jsou následující:

| Ikona                         | Name          | Klíčové slovo    | Klávesová zkratka |
| -----------------------------|---------------| -----------|--------|
| ![Ikona třídy](media/classes-icon.png)  | třída         | `class`    |  ⌥ C
| ![Ikona konstanty](media/constant-icon.png) | – konstanta      | `const`    |  ⌥ O
| ![Ikona delegáta](media/delegate-icon.png) | delegát      | `delegate` |  ⌥ D
| ![Ikona výčtu](media/enums-icon.png)    | enum          | `enum`     |  ⌥ E
| ![Ikona události](media/event-icon.png)    | event         |            |  ⌥ V
| ![Ikona pole](media/fields-icon.png)   | pole         |            |  ⌥ F
| ![Ikona rozhraní](media/interface-icon.png)| rozhraní     | `interface`|  ⌥ I
| ![Ikona klíčového slova](media/keyword-icon.png)  | klíčové slovo       |            |  ⌥ K
| ![Ikona metody](media/method-icon.png)   | metoda        |            |  ⌥ M
| ![Ikona oboru názvů](media/namespace-icon.png)| Obor názvů     | `namespace`|  ⌥ N
| ![Ikona props](media/props-icon.png)    | vlastnost      |            |  ⌥ P
| ![Ikona fragmentu](media/snippet-icon.png)  | zlomk       | `class`    |  ⌥ S
| ![Ikona struktury](media/struct-icon.png)   | struktura     | `struct`   |  ⌥ S

Kliknutím na některou z ikon nebo stisknutím odpovídajících klávesových zkratek se seznam dokončení omezí jenom na typy, které definuje sada filtrů.  

![Filtrování typu IntelliSense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Okno parametrů

Další funkcí technologie IntelliSense je možnost poskytnout seznam parametrů tam, kde je to vhodné. Seznam parametrů poskytuje podrobné informace o signaturách metody pro volání kódu. Kliknutím na šipky nahoru/dolů v rámci podpisu můžete cyklicky procházet jednotlivé dostupné signatury parametrů, abyste určili nejvhodnější požadavky. Kromě podrobností o povolených typech dat může být také popis definovaný v cílové metodě prostřednictvím komentářů XML.

![Seznam parametrů](media/intellisense-parameter.png)

Při vyplňování parametrů bude mít parametr, který právě upravujete, tučný, zatímco neaktivní parametry budou mít standardní váhu. 


## <a name="triggering-completion-window-and-parameter-window"></a>Aktivace okna dokončení a okna parametrů

Okno dokončování se automaticky aktivuje při psaní v rámci zdrojového souboru. Můžete ale také aktivovat okno dokončení pomocí `control-space`zástupce. Tato kombinace kláves způsobí, že se seznam dokončení zobrazí na aktuální pozici blikajícího kurzoru. 

Můžete také ručně aktivovat vzhled okna parametrů zadáním `control-shift-space`. Když je blikající kurzor na pozici, která je platná pro seznam parametrů, seznam parametrů se zobrazí poblíž pozice blikajícího kurzoru.

## <a name="see-also"></a>Viz také:

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoring kódu (Visual Studio ve Windows)](/visualstudio/ide/refactoring-in-visual-studio)
