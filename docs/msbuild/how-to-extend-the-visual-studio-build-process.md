---
title: Rozšíří proces sestavení
description: Seznamte se s různými způsoby, jak upravit proces sestavení, abyste mohli řídit a přizpůsobit, jak vaše projekty sestavují.
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67b2eff1ca7c1871eacad7608b56b6916e3cc8e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914358"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postupy: rozšiřování procesu sestavení sady Visual Studio

Proces sestavení sady Visual Studio je definován řadou souborů MSBuild *. targets* , které jsou importovány do souboru projektu. Jeden z těchto importovaných souborů, *Microsoft. Common. targets*, se dá rozšířit tak, aby bylo možné spouštět vlastní úlohy v několika fázích procesu sestavení. Tento článek vysvětluje dvě metody, které můžete použít k rozšiřování procesu sestavení sady Visual Studio:

- Přepsání specifických předdefinovaných cílů definovaných v rámci běžných cílů (*Microsoft. Common. targets* nebo souborů, které importuje).

- Přepsání vlastností "DependsOn" definovaných v běžných cílech.

## <a name="override-predefined-targets"></a>Přepsat předdefinované cíle

Společné cíle obsahují sadu předdefinovaných prázdných cílů, které jsou volány před a za některými hlavními cíli v procesu sestavení. Například MSBuild volá `BeforeBuild` cíl před hlavním `CoreBuild` cílem a `AfterBuild` cíl po `CoreBuild` cíli. Ve výchozím nastavení nedělají prázdné cíle v běžných cílech nic, ale můžete přepsat jejich výchozí chování definováním cílů, které chcete v souboru projektu, který importuje společné cíle. Přepsáním předdefinovaných cílů můžete pomocí úloh MSBuild získat větší kontrolu nad procesem sestavení.

> [!NOTE]
> Projekty ve stylu sady SDK mají implicitní import cílů *za poslední řádek souboru projektu*. To znamená, že nemůžete přepsat výchozí cíle, pokud neurčíte své importy ručně, jak je popsáno v tématu [How to: use MSBuild Project SDK](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Přepsání předdefinovaného cíle

1. Identifikujte předdefinovaný cíl v rámci běžných cílů, které chcete přepsat. Úplný seznam cílů, které můžete bez obav přepsat, najdete v následující tabulce.

2. Definujte cíl nebo cíle na konci souboru projektu, bezprostředně před `</Project>` značku. Příklad:

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

3. Sestavte soubor projektu.

V následující tabulce jsou uvedeny všechny cíle v rámci běžných cílů, které lze bezpečně přepsat.

|Název cíle|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Úkoly, které jsou vloženy v jednom z těchto cílů, jsou spouštěny před nebo po dokončení základní kompilace. Většina úprav se provádí v jednom z těchto dvou cílů.|
|`BeforeBuild`, `AfterBuild`|Úkoly, které jsou vloženy v jednom z těchto cílů, budou spouštěny před nebo po vše ostatní v sestavení. **Poznámka:**  `BeforeBuild` Cíle a `AfterBuild` jsou již definovány v komentářích na konci většiny souborů projektu, což vám umožní snadno přidat události před a po sestavení do souboru projektu.|
|`BeforeRebuild`, `AfterRebuild`|Úkoly, které jsou vloženy v jednom z těchto cílů, jsou spouštěny před nebo po vyvolání základní funkce opětovného sestavení. Pořadí cíle provádění v *Microsoft. Common.* targets je: `BeforeRebuild` , `Clean` , `Build` a pak `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Úlohy, které jsou vložené v jednom z těchto cílů, se spouštějí před nebo po vyvolání základní čisté funkce.|
|`BeforePublish`, `AfterPublish`|Úlohy, které jsou vložené v jednom z těchto cílů, se spouštějí před nebo po vyvolání základní funkce publikování.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Úkoly, které jsou vloženy v jednom z těchto cílů, jsou spouštěny před nebo po vyřešení odkazů na sestavení.|
|`BeforeResGen`, `AfterResGen`|Úkoly vložené v jednom z těchto cílů jsou spouštěny před nebo po vygenerování prostředků.|

## <a name="example-aftertargets-and-beforetargets"></a>Příklad: AfterTargets a BeforeTargets

Následující příklad ukazuje, jak použít `AfterTargets` atribut k přidání vlastního cíle, který má něco s výstupními soubory. V tomto případě zkopíruje výstupní soubory do nové složky *CustomOutput*.  Příklad také ukazuje, jak vyčistit soubory vytvořené pomocí vlastní operace sestavení s `CustomClean` cílem pomocí `BeforeTargets` atributu a určením, že se vlastní čistá operace spouští před `CoreClean` cílem.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Nezapomeňte použít jiné názvy než předdefinované cíle uvedené v tabulce v předchozí části (například se jmenuje vlastní cíl sestavení `CustomAfterBuild` , ne `AfterBuild` ), protože tyto předdefinované cíle jsou přepsány IMPORTEM sady SDK, které je také definují. Nevidíte import cílového souboru, který přepíše tyto cíle, ale je implicitně přidán na konec souboru projektu, když použijete `Sdk` metodu atributu odkazující na sadu SDK.

## <a name="override-dependson-properties"></a>Přepsat vlastnosti DependsOn

Přepsání předdefinovaných cílů představuje snadný způsob, jak tento proces sestavení roztáhnout, protože nástroj MSBuild vyhodnocuje definici cílů sekvenčně, neexistuje žádný způsob, jak zabránit jinému projektu, který importuje projekt z přepsání cílů, které jste již přepsali. Takže například poslední `AfterBuild` cíl definovaný v souboru projektu, po importu všech ostatních projektů, bude ten, který se používá během sestavení.

Můžete chránit před nezamýšlenými přepsáními cílů přepsáním vlastností DependsOn, které se používají v `DependsOnTargets` atributech napříč běžnými cíli. Například `Build` cíl obsahuje `DependsOnTargets` hodnotu atributu `"$(BuildDependsOn)"` . Rozmyslete si:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Tato část XML značí, že před `Build` spuštěním cíle se musí nejdřív spustit všechny cíle zadané ve `BuildDependsOn` Vlastnosti. `BuildDependsOn`Vlastnost je definována jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Tuto hodnotu vlastnosti lze přepsat deklarováním jiné vlastnosti pojmenované `BuildDependsOn` na konci souboru projektu. Zahrnutím předchozí `BuildDependsOn` vlastnosti do nové vlastnosti můžete přidat nové cíle na začátek a konec cílového seznamu. Příklad:

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

Projekty, které importují soubory projektu, mohou tyto vlastnosti přepsat bez přepsání vlastního nastavení, které jste provedli.

#### <a name="to-override-a-dependson-property"></a>Přepsání vlastnosti DependsOn

1. Identifikujte předdefinovanou vlastnost DependsOn ve společných cílech, které chcete přepsat. Seznam běžně přepsaných vlastností DependsOn najdete v následující tabulce.

2. Na konci souboru projektu definujte jinou instanci vlastnosti nebo vlastností. Do vlastnosti New přidejte původní vlastnost, například `$(BuildDependsOn)` .

3. Definujte vlastní cíle před nebo po definici vlastnosti.

4. Sestavte soubor projektu.

### <a name="commonly-overridden-dependson-properties"></a>Běžně přepsané vlastnosti DependsOn

|Název vlastnosti|Description|
|-------------------|-----------------|
|`BuildDependsOn`|Vlastnost, která má být přepsána, pokud chcete vložit vlastní cíle před nebo po celém procesu sestavení.|
|`CleanDependsOn`|Vlastnost, která má být přepsána, pokud chcete vyčistit výstup z vlastního procesu sestavení.|
|`CompileDependsOn`|Vlastnost, která má být přepsána, pokud chcete vložit vlastní procesy před nebo po kroku kompilace.|

## <a name="example-builddependson-and-cleandependson"></a>Příklad: BuildDependsOn a CleanDependsOn

Následující příklad je podobný jako `BeforeTargets` `AfterTargets` příklad a, ale ukazuje, jak dosáhnout podobných funkcí. Rozšiřuje sestavení pomocí nástroje `BuildDependsOn` pro přidání vlastní úlohy `CustomAfterBuild` , která zkopíruje výstupní soubory po sestavení a také přidá odpovídající `CustomClean` úlohu pomocí `CleanDependsOn` .  

V tomto příkladu je to projekt ve stylu sady SDK. Jak je uvedeno v poznámce o projektech ve stylu sady SDK výše v tomto článku, je nutné použít metodu ručního importu namísto `Sdk` atributu, který sada Visual Studio používá, když generuje soubory projektu.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

Pořadí prvků je důležité. `BuildDependsOn`Elementy a `CleanDependsOn` musí následovat po importu souboru standardních cílů sady SDK.

## <a name="see-also"></a>Viz také

- [integrace sady Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [soubory. targets](../msbuild/msbuild-dot-targets-files.md)
