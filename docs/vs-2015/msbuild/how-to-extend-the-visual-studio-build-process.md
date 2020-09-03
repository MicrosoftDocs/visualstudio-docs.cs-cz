---
title: 'Postupy: rozšiřování procesu sestavení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 789c60da5be841721ab3a999120e2fe560ffd588
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156612"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postupy: Rozšíření procesu sestavení sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Proces sestavení je definován řadou [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souborů. targets, které jsou importovány do souboru projektu. Jeden z těchto importovaných souborů, Microsoft. Common. targets, se dá rozšířit tak, aby bylo možné spouštět vlastní úlohy v několika fázích procesu sestavení. Toto téma vysvětluje dvě metody, které můžete použít k rozšiřování [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] procesu sestavení:

- Přepsání specifických předdefinovaných cílů definovaných v Microsoft. Common. targets.

- Přepisování vlastností "DependsOn" definovaných v Microsoft. Common. targets.

## <a name="overriding-predefined-targets"></a>Přepsání předdefinovaných cílů
 Soubor Microsoft. Common. targets obsahuje sadu předdefinovaných prázdných cílů, které jsou volány před a za některými hlavními cíli v procesu sestavení. Například [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] volá `BeforeBuild` cíl před hlavním `CoreBuild` cílem a `AfterBuild` cíl po `CoreBuild` cíli. Ve výchozím nastavení prázdné cíle v Microsoft. Common. targets nedělají nic, ale můžete přepsat jejich výchozí chování definováním cílů, které chcete v souboru projektu, který importuje Microsoft. Common. targets. Díky tomu můžete použít [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkoly k poskytnutí větší kontroly nad procesem sestavení.

#### <a name="to-override-a-predefined-target"></a>Přepsání předdefinovaného cíle

1. Identifikujte předdefinovaný cíl v Microsoft. Common. targets, který chcete přepsat. Úplný seznam cílů, které můžete bez obav přepsat, najdete v následující tabulce.

2. Definujte cíl nebo cíle na konci souboru projektu, bezprostředně před `</Project>` značku. Příklad:

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. Sestavte soubor projektu.

   V následující tabulce jsou uvedeny všechny cíle v Microsoft. Common. targets, které můžete bezpečně přepsat.

|Cílový název|Popis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po dokončení základní kompilace. Většina úprav se provádí v jednom z těchto dvou cílů.|
|`BeforeBuild`, `AfterBuild`|Úkoly vložené v jednom z těchto cílů se spustí před nebo po vše ostatní v sestavení. **Poznámka:**  `BeforeBuild` Cíle a `AfterBuild` jsou již definovány v komentářích na konci většiny souborů projektu. To umožňuje snadno přidat události před a po sestavení do souboru projektu.|
|`BeforeRebuild`, `AfterRebuild`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po vyvolání základní funkce opětovného sestavení. Pořadí cíle provádění v Microsoft. Common. targets je: `BeforeRebuild` , `Clean` , `Build` a pak `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po vyvolání základní čisté funkce.|
|`BeforePublish`, `AfterPublish`|Úlohy vložené v jednom z těchto cílů jsou spouštěny před nebo po vyvolání základní funkce publikování.|
|`BeforeResolveReference`, `AfterResolveReferences`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po vyřešení odkazů na sestavení.|
|`BeforeResGen`, `AfterResGen`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po vygenerování prostředků.|

## <a name="overriding-dependson-properties"></a>Přepsání vlastností "DependsOn"
 Přepsání předdefinovaných cílů představuje snadný způsob, jak roztáhnout proces sestavení, ale protože [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vyhodnocuje definici cílů postupně, neexistuje žádný způsob, jak zabránit jinému projektu, který importuje projekt z přepsání cílů, které jste již přepsali. Takže například poslední `AfterBuild` cíl definovaný v souboru projektu, po importu všech ostatních projektů, bude ten, který se používá během sestavení.

 Můžete chránit před nezamýšlenými přepsáními cílů přepsáním vlastností "DependsOn", které se používají v `DependsOnTargets` atributech v souboru Microsoft. Common. targets. Například `Build` cíl obsahuje `DependsOnTargets` hodnotu atributu `"$(BuildDependsOn)"` . Rozmyslete si:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Tato část XML značí, že před `Build` spuštěním cíle se musí nejdřív spustit všechny cíle zadané ve `BuildDependsOn` Vlastnosti. `BuildDependsOn`Vlastnost je definována jako:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Tuto hodnotu vlastnosti lze přepsat deklarováním jiné vlastnosti pojmenované `BuildDependsOn` na konci souboru projektu. Zahrnutím předchozí `BuildDependsOn` vlastnosti do nové vlastnosti můžete přidat nové cíle na začátek a konec cílového seznamu. Příklad:

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 Projekty, které importují soubory projektu, mohou tyto vlastnosti přepsat bez přepsání vlastního nastavení, které jste provedli.

#### <a name="to-override-a-dependson-property"></a>Přepsání vlastnosti "DependsOn"

1. Identifikujte předdefinovanou vlastnost DependsOn v Microsoft. Common. targets, kterou chcete přepsat. Seznam běžně přepsaných vlastností "DependsOn" najdete v následující tabulce.

2. Na konci souboru projektu definujte jinou instanci vlastnosti nebo vlastností. Do vlastnosti New přidejte původní vlastnost, například `$(BuildDependsOn)` .

3. Definujte vlastní cíle před nebo po definici vlastnosti.

4. Sestavte soubor projektu.

### <a name="commonly-overridden-dependson-properties"></a>Běžně přepsané vlastnosti "DependsOn"

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`BuildDependsOn`|Vlastnost, která má být přepsána, pokud chcete vložit vlastní cíle před nebo po celém procesu sestavení.|
|`CleanDependsOn`|Vlastnost, která má být přepsána, pokud chcete vyčistit výstup z vlastního procesu sestavení.|
|`CompileDependsOn`|Vlastnost, která má být přepsána, pokud chcete vložit vlastní procesy před nebo po kroku kompilace.|

## <a name="see-also"></a>Viz také
 [Visual Studio Integration](../msbuild/visual-studio-integration-msbuild.md) [MSBuild – koncepty](../msbuild/msbuild-concepts.md) [. Soubory cílů](../msbuild/msbuild-dot-targets-files.md)
