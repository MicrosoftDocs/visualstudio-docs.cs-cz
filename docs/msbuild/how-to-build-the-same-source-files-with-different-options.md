---
title: 'Postupy: sestavení stejných zdrojových souborů s různými možnostmi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c31da244e5c264bb81498c6091aefce7e6318bb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633938"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Postupy: sestavení stejných zdrojových souborů s různými možnostmi

Při sestavování projektů je často možné kompilovat stejné komponenty s různými možnostmi sestavení. Můžete například vytvořit sestavení pro ladění s informacemi o symbolech nebo sestavením pro vydání bez informací o symbolu, ale s povolenými optimalizacemi. Nebo můžete sestavit projekt pro spuštění na konkrétní platformě, jako je například x86 nebo x64. Ve všech těchto případech většina možností sestavení zůstává stejná; pro řízení konfigurace sestavení je změněno pouze několik možností. Pomocí nástroje MSBuild použijete vlastnosti a podmínky k vytvoření různých konfigurací sestavení.

## <a name="use-properties-to-control-build-settings"></a>Použití vlastností k řízení nastavení sestavení

`Property`Element definuje proměnnou, která je v souboru projektu odkazována několikrát, jako je například umístění dočasného adresáře, nebo pro nastavení hodnot vlastností, které jsou použity v několika konfiguracích, jako je například sestavení ladění a sestavení pro vydání. Další informace o vlastnostech naleznete v tématu [MSBuild Properties](../msbuild/msbuild-properties.md).

Můžete použít vlastnosti pro změnu konfigurace sestavení bez nutnosti změnit soubor projektu. `Condition`Atribut `Property` elementu a `PropertyGroup` elementu umožňuje změnit hodnotu vlastností. Další informace o podmínkách MSBuild naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Nastavení skupiny vlastností, které závisejí na jiné vlastnosti

- Použijte `Condition` atribut v elementu, `PropertyGroup` který se podobá následujícímu:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Definování vlastnosti, která závisí na jiné vlastnosti

- Použijte `Condition` atribut v elementu, `Property` který se podobá následujícímu:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Zadat vlastnosti na příkazovém řádku

Po zapsání souboru projektu pro přijetí více konfigurací je nutné mít možnost měnit tyto konfigurace při každém sestavení projektu. Nástroj MSBuild poskytuje tuto možnost tím, že povoluje zadání vlastností na příkazovém řádku pomocí přepínače **-Property** nebo **-p** .

### <a name="to-set-a-project-property-at-the-command-line"></a>Nastavení vlastnosti projektu na příkazovém řádku

- Použijte přepínač **-Property** s hodnotou vlastnosti a vlastnosti. Příklad:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  nebo

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Chcete-li zadat více než jednu vlastnost projektu na příkazovém řádku

- Použijte přepínač **-Property** nebo **-p** vícekrát s hodnotami vlastností a vlastností, nebo použijte přepínač- **Property** nebo **-p** a oddělte více vlastností středníky (;). Příklad:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  nebo

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Proměnné prostředí se také považují za vlastnosti a jsou automaticky začleněny nástrojem MSBuild. Další informace o použití proměnných prostředí naleznete v tématu [How to: use Environment Variables in a Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Hodnota vlastnosti, která je zadána v příkazovém řádku, má přednost před jakoukoli hodnotou, která je nastavena pro stejnou vlastnost v souboru projektu a tato hodnota v souboru projektu má přednost před hodnotou v proměnné prostředí.

  Toto chování lze změnit pomocí `TreatAsLocalProperty` atributu ve značce projektu. U názvů vlastností, které jsou uvedeny s tímto atributem, hodnota vlastnosti zadaná v příkazovém řádku nemá přednost před hodnotou v souboru projektu. Příklad najdete v části dále v tomto tématu.

## <a name="example"></a>Příklad

Následující příklad kódu, projekt "Hello World", obsahuje dvě nové skupiny vlastností, které lze použít k vytvoření sestavení pro ladění a sestavení pro vydání.

Chcete-li sestavit ladicí verzi tohoto projektu, zadejte:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Chcete-li vytvořit prodejní verzi tohoto projektu, zadejte:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `TreatAsLocalProperty` atribut. `Color`Vlastnost má hodnotu `Blue` v souboru projektu a na `Green` příkazovém řádku. Pomocí `TreatAsLocalProperty="Color"` ve značce projektu vlastnost příkazového řádku ( `Green` ) nepřepisuje vlastnost, která je definována v souboru projektu ( `Blue` ).

Chcete-li sestavit projekt, zadejte následující příkaz:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>Viz také

- [Nástroji](../msbuild/msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Project – element (MSBuild)](../msbuild/project-element-msbuild.md)
