---
title: Rozšíření procesu sestavení
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca0c55951d4928347528814d043bb8a7c55be9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633847"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postupy: rozšíření procesu sestavení sady Visual Studio

Proces sestavení sady Visual Studio je definován řadou souborů MSBuild *. targets* , které jsou importovány do souboru projektu. Jeden z těchto importovaných souborů, *Microsoft. Common. targets*, se dá rozšířit tak, aby bylo možné spouštět vlastní úlohy v několika fázích procesu sestavení. Tento článek vysvětluje dvě metody, které můžete použít k rozšiřování procesu sestavení sady Visual Studio:

- Přepsání specifických předdefinovaných cílů definovaných v rámci běžných cílů (*Microsoft. Common. targets* nebo souborů, které importuje).

- Přepsání vlastností "DependsOn" definovaných v běžných cílech.
## <a name="override-predefined-targets"></a>Přepsání předdefinovaných cílů

## <a name="override-predefined-targets"></a>Přepsání předdefinovaných cílů

Společné cíle obsahují sadu předdefinovaných prázdných cílů, které jsou volány před a za některými hlavními cíli v procesu sestavení. Například MSBuild volá `BeforeBuild` cíl před hlavní `CoreBuild` cíle a `AfterBuild` cíl po `CoreBuild` cíl. Ve výchozím nastavení nedělají prázdné cíle v běžných cílech nic, ale můžete přepsat jejich výchozí chování definováním cílů, které chcete v souboru projektu, který importuje společné cíle. Přepsáním předdefinovaných cílů můžete pomocí úloh MSBuild získat větší kontrolu nad procesem sestavení.
Společné cíle obsahují sadu předdefinovaných prázdných cílů, které jsou volány před a za některými hlavními cíli v procesu sestavení. Například MSBuild volá `BeforeBuild` cíl před hlavní `CoreBuild` cíle a `AfterBuild` cíl po `CoreBuild` cíl. Ve výchozím nastavení nedělají prázdné cíle v běžných cílech nic, ale můžete přepsat jejich výchozí chování definováním cílů, které chcete v souboru projektu, který importuje společné cíle. Přepsáním předdefinovaných cílů můžete pomocí úloh MSBuild získat větší kontrolu nad procesem sestavení.

> [!NOTE]
> Projekty ve stylu sady SDK mají implicitní import cílů *za poslední řádek souboru projektu*. To znamená, že nemůžete přepsat výchozí cíle, pokud neurčíte své importy ručně, jak je popsáno v tématu [How to: use MSBuild Project SDK](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Chcete-li přepsat předdefinované cíle

1. Identifikujte předdefinovaný cíl v rámci běžných cílů, které chcete přepsat. Najdete v následující tabulce pro úplný seznam cílů, které je možné bezpečně přepsat.

2. Na konci souboru projektu definujte cíl nebo cíle, bezprostředně před tagem `</Project>`. Příklad:

    ```xml
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

3. Vytváření souboru projektu.

V následující tabulce jsou uvedeny všechny cíle v rámci běžných cílů, které lze bezpečně přepsat.

|Název cíle|Popis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po dokončení základní kompilace. Většina nastavení se provádějí v jednom z těchto dva cíle.|
|`BeforeBuild`, `AfterBuild`|Úlohy, které jsou vloženy v jednom z těchto cílů se spustí před nebo za všechno ostatní v sestavení. **Poznámka:**  Cíle `BeforeBuild` a `AfterBuild` jsou již definovány v komentářích na konci většiny souborů projektu, což vám umožní snadno přidat události před a po sestavení do souboru projektu.|
|`BeforeRebuild`, `AfterRebuild`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní znovu sestavit funkcí je vyvolána. Pořadí cíle provádění v *Microsoft. Common.* targets je: `BeforeRebuild`, `Clean`, `Build`a potom `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní vyčištění funkce vyvolána.|
|`BeforePublish`, `AfterPublish`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní publikování funkcí je vyvolána.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po odkazy na sestavení se vyřeší.|
|`BeforeResGen`, `AfterResGen`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po generování prostředků.|

## <a name="override-dependson-properties"></a>Přepsání vlastností DependsOn

Přepsání předdefinovaných cílů představuje snadný způsob, jak tento proces sestavení roztáhnout, protože nástroj MSBuild vyhodnocuje definici cílů sekvenčně, neexistuje žádný způsob, jak zabránit jinému projektu, který importuje projekt z přepsání cílů, které už máte. přetížen. Takže například poslední `AfterBuild` cíl definovaný v souboru projektu, poté, co byly importovány všechny ostatní projekty, bude ten, který se používá během sestavení.

Můžete chránit před nezamýšlenými přepsáními cílů přepsáním vlastností DependsOn, které se používají v `DependsOnTargets` atributů napříč běžnými cíli. Například cíl `Build` obsahuje `DependsOnTargets` hodnotu atributu `"$(BuildDependsOn)"`. Rozmyslete si:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Tato část XML značí, že před spuštěním cíle `Build` se musí nejdřív spustit všechny cíle zadané ve vlastnosti `BuildDependsOn`. Vlastnost `BuildDependsOn` je definována takto:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Tuto hodnotu vlastnosti lze přepsat deklarací jiné vlastnosti s názvem `BuildDependsOn` na konci souboru projektu. Zahrnutím předchozí vlastnosti `BuildDependsOn` do nové vlastnosti můžete přidat nové cíle na začátek a konec cílového seznamu. Příklad:

```xml
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

Projekty, které importuje soubory projektu můžete přepsat tyto vlastnosti, aniž byste museli přepsat přizpůsobení, které jste provedli.

#### <a name="to-override-a-dependson-property"></a>K přepsání vlastností DependsOn

1. Identifikujte předdefinovanou vlastnost DependsOn ve společných cílech, které chcete přepsat. Najdete v následující tabulce seznam běžně potlačených vlastností DependsOn.

2. Definujte další instanci vlastnosti nebo vlastnosti na konci souboru projektu. Do vlastnosti New přidejte původní vlastnost, například `$(BuildDependsOn)`.

3. Definujte vlastní cíle před nebo po definici vlastnosti.

4. Vytváření souboru projektu.

### <a name="commonly-overridden-dependson-properties"></a>Běžně potlačených vlastností DependsOn

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`BuildDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní cíle před nebo po dokončení celého sestavení.|
|`CleanDependsOn`|Vlastnost, která má přepsat, pokud chcete vyčistit výstup z vlastního procesu sestavení.|
|`CompileDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní procesy před nebo po kompilační krok.|

## <a name="see-also"></a>Viz také

- [Integrace sady Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [soubory. targets](../msbuild/msbuild-dot-targets-files.md)
