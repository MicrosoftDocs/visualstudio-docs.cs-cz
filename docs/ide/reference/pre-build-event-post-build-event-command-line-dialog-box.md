---
title: Dialogové okno Příkazový řádek události před sestavením / po sestavení
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38712c25718670ea15324e3daf6fadc138cb08a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567915"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Dialogové okno Příkazový řádek události před sestavením události/po sestavení

Můžete zadat události před nebo po sestavení pro [stránku události sestavení, Návrhář projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) přímo do textového pole nebo můžete vybrat makra před a po sestavení ze seznamu dostupných maker.

> [!NOTE]
> Události předběžného sestavení se nespustí, pokud je projekt aktuální a neaktivuje se žádné sestavení.

## <a name="ui-element-list"></a>Seznam prvků uživatelského rozhraní

**Textové pole příkazového řádku**

Obsahuje události, které mají být spuštěny pro předběžné sestavení nebo po sestavení.

> [!NOTE]
> Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory BAT. Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

**Makra**

Rozbalí textové pole, aby se zobrazil seznam maker, která chcete vložit do textového pole příkazového řádku.

**Tabulka maker**

Zobrazí seznam dostupných maker a jejich hodnotu. Popis každého z nich naleznete níže v části Makra. Do textového pole příkazového řádku můžete vybrat pouze jedno makro najednou.

**Vložit**

Vloží do textového pole příkazového řádku makro vybrané v tabulce maker.

### <a name="macros"></a>Makra

Některé z těchto maker můžete použít k určení umístění souborů nebo k získání skutečného názvu vstupního souboru v případě více výběrů. Tato makra nerozlišují malá a velká písmena.

|Makro|Popis|
|-----------|-----------------|
|`$(ConfigurationName)`|Název aktuální konfigurace projektu, například "Ladění".|
|`$(OutDir)`|Cesta k adresáři výstupního souboru vzhledem k adresáři projektu. To překládá na hodnotu vlastnosti Výstupní adresář. Obsahuje koncové zpětné lomítko '\\'.|
|`$(DevEnvDir)`|Instalační adresář sady Visual Studio (definovaný jednotkou a cestou); zahrnuje koncové zpětné lomítko '\\..|
|`$(PlatformName)`|Název aktuálně cílové platformy. Například "AnyCPU".|
|`$(ProjectDir)`|Adresář projektu (definovaný jednotkou a cestou); zahrnuje koncové zpětné lomítko '\\..|
|`$(ProjectPath)`|Absolutní název cesty projektu (definovaný jednotkou, cestou, základním názvem a příponou souboru).|
|`$(ProjectName)`|Základní název projektu.|
|`$(ProjectFileName)`|Název souboru projektu (definovaný se základním názvem a příponou souboru).|
|`$(ProjectExt)`|Přípona souboru projektu. Obsahuje '.' před příponou souboru.|
|`$(SolutionDir)`|Adresář řešení (definovaný s jednotkou a cestou); zahrnuje koncové zpětné lomítko '\\..|
|`$(SolutionPath)`|Absolutní název cesty řešení (definovaný jednotkou, cestou, základním názvem a příponou souboru).|
|`$(SolutionName)`|Základní název řešení.|
|`$(SolutionFileName)`|Název souboru řešení (definovaný se základním názvem a příponou souboru).|
|`$(SolutionExt)`|Přípona souboru řešení. Obsahuje '.' před příponou souboru.|
|`$(TargetDir)`|Adresář primárního výstupního souboru pro sestavení (definovaný jednotkou a cestou). Obsahuje koncové zpětné lomítko '\\'.|
|`$(TargetPath)`|Absolutní název cesty primárního výstupního souboru pro sestavení (definovaný jednotkou, cestou, základním názvem a příponou souboru).|
|`$(TargetName)`|Základní název primárního výstupního souboru pro sestavení.|
|`$(TargetFileName)`|Název souboru primárního výstupního souboru pro sestavení (definovaný jako základní název a přípona souboru).|
|`$(TargetExt)`|Přípona souboru primárního výstupního souboru pro sestavení. Obsahuje '.' před příponou souboru.|

## <a name="see-also"></a>Viz také

- [Specifikace vlastních událostí sestavení v sadě Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Stránka Události sestavení, návrhář projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Postupy: Specifikace událostí sestavení (C#)](../../ide/how-to-specify-build-events-csharp.md)
