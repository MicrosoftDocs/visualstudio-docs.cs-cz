---
title: Projekty a řešení
description: Tento dokument poskytuje přehled projektů a řešení v Visual Studio pro Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: b63e1206624c5aab6af67d9e4fbd30473d4f7f5d
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938594"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekty a řešení v Visual Studio pro Mac

Tento článek poskytuje přehled konceptů *projektu* a *řešení* v Visual Studio pro Mac.

> [!NOTE] 
> Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [projekty a řešení v aplikaci Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekty

Při vytváření nové aplikace, webu atd. v Visual Studio pro Mac začněte s projektem. Projekt obsahuje všechny požadované soubory (zdrojový kód, obrázky, datové soubory atd.), které jsou potřeba ke kompilaci spustitelného souboru, knihovny nebo webu.

Projekt je definován souborem (například `.csproj` pro projekty v jazyce C#), který obsahuje kód XML, který definuje hierarchii souborů a složek, cest k souborům a nastavení specifického pro projekt, jako je například nastavení sestavení.

Když je projekt načten pomocí Visual Studio pro Mac, Oblast řešení používá soubor projektu k zobrazení souborů a složek v projektu. Během kompilace nástroj MSBuild přečte nastavení ze souboru projektu a vytvoří spustitelný soubor.

## <a name="solutions"></a>Řešení

*Řešení* je kontejner, který seskupuje jeden nebo více souvisejících projektů. Řešení jsou popsána pomocí textového souboru (rozšíření `.sln` ) s vlastním jedinečným formátem, není určeno k úpravám rukou.

## <a name="managing-projects-in-the-solution-pad"></a>Správa projektů v Oblast řešení

Po vytvoření nebo načtení projektu můžete použít Oblast řešení k zobrazení a správě projektu nebo řešení a souborů obsažených v. Následující ilustrace znázorňuje Oblast řešení pomocí řešení .NET Core, které obsahuje dva projekty:

![Ukázkové řešení s více projekty](media/solution-example.png)

Vlastnosti projektů a řešení lze spravovat buď Poklikáním na název projektu nebo řešení, nebo kliknutím pravým tlačítkem a výběrem **možností**.

Další informace o těchto možnostech najdete v článku [Správa řešení a vlastností projektu](managing-solutions-and-project-properties.md) .

## <a name="see-also"></a>Viz také

- [Řešení a projekty v aplikaci Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
