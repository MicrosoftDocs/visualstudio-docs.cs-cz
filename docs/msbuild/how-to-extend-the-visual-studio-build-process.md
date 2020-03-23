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
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093940"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postup: Rozšíření procesu sestavení sady Visual Studio

Proces sestavení sady Visual Studio je definován řadou souborů MSBuild *.targets,* které jsou importovány do souboru projektu. Jeden z těchto importovaných *souborů, Microsoft.Common.targets*, lze rozšířit tak, aby bylo možné spouštět vlastní úlohy na několika místech v procesu sestavení. Tento článek vysvětluje dvě metody, které můžete použít k rozšíření procesu sestavení sady Visual Studio:

- Přepsání konkrétních předdefinovaných cílů definovaných ve společných cílech (*Microsoft.Common.targets* nebo v importech souborů).

- Přepsání vlastností "DependsOn" definovaných ve společných cílech.

## <a name="override-predefined-targets"></a>Přepsat předdefinované cíle

Společné cíle obsahuje sadu předdefinovaných prázdných cílů, které jsou volány před a po některé z hlavních cílů v procesu sestavení. Například MSBuild volá `BeforeBuild` cíl před `CoreBuild` hlavním `AfterBuild` cílem a `CoreBuild` cíl po cíl. Ve výchozím nastavení prázdné cíle v běžných cílech nedělají nic, ale jejich výchozí chování můžete přepsat definováním požadovaných cílů v souboru projektu, který importuje společné cíle. Přepsáním předdefinovaných cílů můžete pomocí úloh MSBuild poskytnout větší kontrolu nad procesem sestavení.
Společné cíle obsahuje sadu předdefinovaných prázdných cílů, které jsou volány před a po některé z hlavních cílů v procesu sestavení. Například MSBuild volá `BeforeBuild` cíl před `CoreBuild` hlavním `AfterBuild` cílem a `CoreBuild` cíl po cíl. Ve výchozím nastavení prázdné cíle v běžných cílech nedělají nic, ale jejich výchozí chování můžete přepsat definováním požadovaných cílů v souboru projektu, který importuje společné cíle. Přepsáním předdefinovaných cílů můžete pomocí úloh MSBuild poskytnout větší kontrolu nad procesem sestavení.

> [!NOTE]
> Projekty ve stylu sady SDK mají implicitní import cílů *za posledním řádkem souboru projektu*. To znamená, že výchozí cíle nelze přepsat ručně, jak je popsáno v [části Postup: Použití sad Sad SDK projektu MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Přepsání předdefinovaného cíle

1. Identifikujte předdefinovaný cíl ve společných cílech, které chcete přepsat. Úplný seznam cílů, které můžete bezpečně přepsat, naleznete v následující tabulce.

2. Definujte cíl nebo cíle na konci souboru `</Project>` projektu bezprostředně před značkou. Například:

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

3. Vytvořte soubor projektu.

V následující tabulce jsou uvedeny všechny cíle ve společných cílech, které můžete bezpečně přepsat.

|Cílový název|Popis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po dokončení kompilace jádra. Většina úprav se provádí v jednom z těchto dvou cílů.|
|`BeforeBuild`, `AfterBuild`|Úkoly, které jsou vloženy do jednoho z těchto cílů bude spuštěna před nebo po všechno ostatní v sestavení. **Poznámka:**  Cíle `BeforeBuild` `AfterBuild` a jsou již definovány v komentářích na konci většiny souborů projektu, což umožňuje snadno přidat události před a po sestavení do souboru projektu.|
|`BeforeRebuild`, `AfterRebuild`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po obnovení základní funkce je vyvolána. Pořadí provádění cíle v *Microsoft.Common.targets* `BeforeRebuild` `Clean`je: , , `Build`a potom `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po vyvolání základní čisté funkce.|
|`BeforePublish`, `AfterPublish`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po vyvolání základní funkce publikování.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Úkoly, které jsou vloženy do jednoho z těchto cílů spustit před nebo po sestavení odkazy jsou vyřešeny.|
|`BeforeResGen`, `AfterResGen`|Úkoly, které jsou vloženy do jednoho z těchto cílů spustit před nebo po vygenerování prostředků.|

## <a name="example-aftertargets-and-beforetargets"></a>Příklad: AfterTargets a BeforeTargets

Následující příklad ukazuje, jak `AfterTargets` použít atribut k přidání vlastního cíle, který dělá něco s výstupními soubory. V tomto případě zkopíruje výstupní soubory do nové složky *CustomOutput*.  Příklad také ukazuje, jak vyčistit soubory vytvořené vlastní operace `CustomClean` sestavení s `BeforeTargets` cílem pomocí atributu a určení, `CoreClean` že vlastní čisté operace běží před cílem.

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
> Nezapomeňte použít jiné názvy než předdefinované cíle uvedené v tabulce v předchozí části (například jsme pojmenovali vlastní cíl sestavení zde `CustomAfterBuild`, ne `AfterBuild`), protože tyto předdefinované cíle jsou přepsány importem sady SDK, který je také definuje. Nevidíte import cílového souboru, který přepíše tyto cíle, ale je implicitně přidán na konec `Sdk` souboru projektu při použití metody atributu odkazování na sdk.

## <a name="override-dependson-properties"></a>Přepsat vlastnosti DependsOn

Přepsání předdefinovaných cílů je snadný způsob, jak rozšířit proces sestavení, ale protože MSBuild vyhodnocuje definici cílů postupně, neexistuje žádný způsob, jak zabránit jinému projektu, který importuje projekt z přepsání cílů, které již máte Přepsání. Takže například poslední `AfterBuild` cíl definovaný v souboru projektu po importu všech ostatních projektů bude ten, který se používá během sestavení.

Můžete chránit před nezamýšlenými přepsání cílů přepsánídependsOn `DependsOnTargets` vlastnosti, které se používají v atributy v rámci společné cíle. `Build` Cíl například obsahuje `DependsOnTargets` hodnotu `"$(BuildDependsOn)"`atributu . Rozmyslete si:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Tato část jazyka XML `Build` označuje, že před spuštěním `BuildDependsOn` cíle musí být nejprve spuštěny všechny cíle zadané ve vlastnosti. Vlastnost `BuildDependsOn` je definována jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Tuto hodnotu vlastnosti můžete přepsat deklarováním jiné vlastnosti pojmenované `BuildDependsOn` na konci souboru projektu. Zahrnutím `BuildDependsOn` předchozí vlastnosti do nové vlastnosti můžete přidat nové cíle na začátek a konec cílového seznamu. Například:

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

Projekty, které importují soubory projektu, mohou přepsat tyto vlastnosti bez přepsání provedených vlastních nastavení.

#### <a name="to-override-a-dependson-property"></a>Chcete-li přepsat DependsOn vlastnost

1. Identifikujte předdefinovanou vlastnost DependsOn ve společných cílech, které chcete přepsat. Seznam běžně přepsaných vlastností DependsOn naleznete v následující tabulce.

2. Definujte jinou instanci vlastnosti nebo vlastností na konci souboru projektu. Do nové vlastnosti `$(BuildDependsOn)`zahrňte například původní vlastnost.

3. Definujte vlastní cíle před nebo za definicí vlastnosti.

4. Vytvořte soubor projektu.

### <a name="commonly-overridden-dependson-properties"></a>Běžně přepsané dependson vlastnosti

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`BuildDependsOn`|Vlastnost přepsat, pokud chcete vložit vlastní cíle před nebo po celém procesu sestavení.|
|`CleanDependsOn`|Vlastnost přepsat, pokud chcete vyčistit výstup z vlastního procesu sestavení.|
|`CompileDependsOn`|Vlastnost přepsat, pokud chcete vložit vlastní procesy před nebo po kroku kompilace.|

## <a name="example-builddependson-and-cleandependson"></a>Příklad: BuildDependsOn a CleanDependsOn

Následující příklad je podobný `BeforeTargets` `AfterTargets` a příklad, ale ukazuje, jak dosáhnout podobné funkce. `BuildDependsOn` Rozšiřuje sestavení pomocí přidat vlastní úkol, `CustomAfterBuild` který zkopíruje výstupní soubory po sestavení `CustomClean` a také `CleanDependsOn`přidá odpovídající úlohu pomocí .  

V tomto příkladu se jedná o projekt ve stylu sady SDK. Jak je uvedeno v poznámce o projektech ve stylu sady SDK dříve `Sdk` v tomto článku, je nutné použít metodu ručního importu namísto atributu, který visual studio používá při generování souborů projektu.

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

Pořadí prvků je důležité. `BuildDependsOn` Prvky `CleanDependsOn` a se musí zobrazit po importu standardního souboru cílů sady SDK.

## <a name="see-also"></a>Viz také

- [Integrace se sadou Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [.targets soubory](../msbuild/msbuild-dot-targets-files.md)
