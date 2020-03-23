---
title: Projekty a řešení
description: Tento dokument obsahuje přehled projektů a řešení v Sadě Visual Studio pro Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 92e7a47f7ea2b931c0b923d10e115843d315d024
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70107831"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekty a řešení ve Visual Studiu pro Mac

Tento článek obsahuje přehled konceptů *projektu* a *řešení* v Sadě Visual Studio pro Mac.

> [!NOTE] 
> Toto téma se týká Visual Studia pro Mac. Visual Studio ve Windows najdete [v tématu Projekty a řešení v sadě Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekty

Při vytváření nové aplikace, webu atd. Projekt obsahuje všechny požadované soubory (zdrojový kód, obrázky, datové soubory atd.), které jsou potřebné pro kompilaci spustitelného souboru, knihovny nebo webu.

Projekt je definován souborem (např. `.csproj` pro projekty jazyka C#), který obsahuje xml, který definuje hierarchii souborů a složek, cesty k souborům a nastavení specifická pro projekt, jako je například nastavení sestavení.

Při načtení projektu Visual Studio for Mac, Panel řešení používá soubor projektu k zobrazení souborů a složek v projektu. Během kompilace MSBuild přečte nastavení ze souboru projektu k vytvoření spustitelného souboru.

## <a name="solutions"></a>Řešení

*Řešení* je kontejner, který seskupuje jeden nebo více souvisejících projektů. Řešení jsou popsána textovým `.sln`souborem (příponou) s vlastním jedinečným formátem; není určen k ruční úpravě.

## <a name="managing-projects-in-the-solution-pad"></a>Správa projektů v panelu řešení

Po vytvoření nebo načtení projektu můžete pomocí panelu řešení zobrazit a spravovat projekt nebo řešení a soubory obsažené v aplikaci. Následující obrázek znázorňuje panel řešení s řešením .NET Core, který obsahuje dva projekty:

![Ukázkové řešení s více projekty](media/solution-example.png)

Vlastnosti projektů i řešení můžete spravovat poklepáním na název projektu nebo řešení nebo kliknutím pravým tlačítkem myši a výběrem **možnosti**.

Další informace o těchto možnostech jsou uvedeny v článku [Správa řešení a vlastností projektu.](managing-solutions-and-project-properties.md)

## <a name="see-also"></a>Viz také

- [Řešení a projekty v sadě Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
