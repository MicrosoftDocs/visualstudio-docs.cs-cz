---
title: 'Postup: Vytvoření stejných zdrojových souborů s různými možnostmi | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633938"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Postup: Vytvoření stejných zdrojových souborů s různými možnostmi

Při vytváření projektů často kompilujete stejné součásti s různými možnostmi sestavení. Můžete například vytvořit ladicí sestavení s informacemi o symbolu nebo sestavení verze bez informací o symbolu, ale s povolenými optimalizacemi. Nebo můžete vytvořit projekt pro spuštění na konkrétní platformě, například x86 nebo x64. Ve všech těchto případech většina možností sestavení zůstat stejné; pouze několik možností jsou změněny pro řízení konfigurace sestavení. S MSBuild, můžete použít vlastnosti a podmínky k vytvoření různých konfigurací sestavení.

## <a name="use-properties-to-control-build-settings"></a>Použití vlastností k řízení nastavení sestavení

Prvek `Property` definuje proměnnou, která je odkazována několikrát v souboru projektu, jako je například umístění dočasného adresáře, nebo nastavit hodnoty pro vlastnosti, které se používají v několika konfiguracích, jako je například sestavení ladění a sestavení verze. Další informace o vlastnostech naleznete v tématu [MSBuild properties](../msbuild/msbuild-properties.md).

Vlastnosti můžete změnit konfiguraci sestavení bez nutnosti měnit soubor projektu. Atribut `Condition` `Property` prvku a `PropertyGroup` prvek umožňuje změnit hodnotu vlastností. Další informace o podmínkách msbuildu naleznete v tématu [Conditions](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Nastavení skupiny vlastností, která závisí na jiné vlastnosti

- Použijte `Condition` atribut v `PropertyGroup` prvku podobném následujícímu:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Definování vlastnosti, která závisí na jiné vlastnosti

- Použijte `Condition` atribut v `Property` prvku podobném následujícímu:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Určení vlastností na příkazovém řádku

Jakmile je soubor projektu zapsán tak, aby přijímal více konfigurací, musíte mít možnost tyto konfigurace změnit při každém sestavení projektu. MSBuild poskytuje tuto schopnost tím, že vlastnosti, které mají být zadány na příkazovém řádku pomocí **-property** nebo **-p** přepínač.

### <a name="to-set-a-project-property-at-the-command-line"></a>Nastavení vlastnosti projektu na příkazovém řádku

- Použijte přepínač **vlastnosti -s** hodnotou vlastnosti a vlastnosti. Například:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  – nebo –

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Určení více než jedné vlastnosti projektu na příkazovém řádku

- Použijte **přepínač -vlastnost** nebo **-p** vícekrát s hodnotami vlastností a vlastností nebo použijte přepínač **one-property** nebo **-p** a oddělte více vlastností středníky (;). Například:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  – nebo –

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Proměnné prostředí jsou také považovány za vlastnosti a jsou automaticky začleněny do MSBuild. Další informace o použití proměnných prostředí naleznete v [tématu Postup: Použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Hodnota vlastnosti, která je zadána na příkazovém řádku, má přednost před libovolnou hodnotou, která je nastavena pro stejnou vlastnost v souboru projektu, a tato hodnota v souboru projektu má přednost před hodnotou v proměnné prostředí.

  Toto chování můžete změnit `TreatAsLocalProperty` pomocí atributu ve značce projektu. Pro názvy vlastností, které jsou uvedeny s tímto atributem, hodnota vlastnosti, která je zadána na příkazovém řádku nemá přednost před hodnotou v souboru projektu. Příklad najdete dále v tomto tématu.

## <a name="example"></a>Příklad

Následující příklad kódu, projekt "Hello World", obsahuje dvě nové skupiny vlastností, které lze použít k vytvoření sestavení ladění a sestavení verze.

Chcete-li vytvořit ladicí verzi tohoto projektu, zadejte:

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

Následující příklad ukazuje, jak `TreatAsLocalProperty` použít atribut. Vlastnost `Color` má hodnotu `Blue` v souboru `Green` projektu a v příkazovém řádku. Ve `TreatAsLocalProperty="Color"` značce projektu vlastnost příkazového`Green`řádku ( ) nepřepíše vlastnost definovanou v`Blue`souboru projektu ( ).

Chcete-li vytvořit projekt, zadejte následující příkaz:

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

- [Msbuild](../msbuild/msbuild.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Prvek projektu (MSBuild)](../msbuild/project-element-msbuild.md)
