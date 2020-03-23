---
title: 'Postup: Vyberte soubory k sestavení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0566078c7f90faf204c35024e2c308b5ef881c01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633808"
---
# <a name="how-to-select-the-files-to-build"></a>Postup: Vyberte soubory, které chcete sestavit.

Při vytváření projektu, který obsahuje několik souborů, můžete v souboru projektu vypsat každý soubor samostatně nebo můžete pomocí zástupných znaků zahrnout všechny soubory do jednoho adresáře nebo vnořené sady adresářů.

## <a name="specify-inputs"></a>Určení vstupů

Položky představují vstupy pro sestavení. Další informace o položkách naleznete v [tématu Položky](../msbuild/msbuild-items.md).

Chcete-li zahrnout soubory pro sestavení, musí být zahrnuty do seznamu položek v souboru projektu MSBuild. Do seznamů položek lze přidat více souborů buď zahrnutím souborů jednotlivě, nebo použitím zástupných znaků k zahrnutí mnoha souborů najednou.

#### <a name="to-declare-items-individually"></a>Deklarování položek jednotlivě

- Použijte `Include` atributy podobné následujícím u následujících:

    `<CSFile Include="form1.cs"/>`

    – nebo –

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Pokud položky v kolekci položek nejsou ve stejném adresáři jako soubor projektu, je nutné zadat úplnou nebo relativní cestu k položce. Například: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Deklarování více položek

- Použijte `Include` atributy podobné následujícím u následujících:

    `<CSFile Include="form1.cs;form2.cs"/>`

    – nebo –

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Určení vstupů pomocí zástupných znaků

Zástupné znaky můžete také použít k rekurzivně zahrnout všechny soubory nebo pouze určité soubory z podadresářů jako vstupy pro sestavení. Další informace o zástupných zástupcích naleznete v [tématu Items](../msbuild/msbuild-items.md)

Následující příklady jsou založeny na projektu, který obsahuje grafické soubory v následujících adresářích a podadresářích, se souborem projektu umístěným v adresáři *aplikace Project:*

*Projekt\Obrázky\Nejlepší Jpgs*

*Projekt\Obrázky\ImgJpgs*

*Projekt\Obrázky\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Zahrnutí všech *souborů JPG* do *adresáře a* podadresářů Obrázky

- Použijte následující `Include` atribut:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Zahrnout všechny *soubory JPG* začínající *na img*

- Použijte následující `Include` atribut:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Zahrnutí všech souborů do adresářů s názvy končícími *na jpgs*

- Použijte jeden z `Include` následujících atributů:

    `Include="Images\**\*jpgs\*.*"`

    – nebo –

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Předání položek úkolu

V souboru projektu můžete pomocí zápisu @() v úkolech určit celý seznam položek jako vstup pro sestavení. Tento zápis můžete použít, zda vypíšete všechny soubory samostatně nebo použijete zástupné znaky.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Použití všech souborů jazyka Visual C# nebo Visual Basic jako vstupů

- Použijte `Include` atributy podobné následujícímu:

    `<CSC Sources="@(CSFile)">...</CSC>`

    – nebo –

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> K určení vstupů pro sestavení je nutné použít zástupné znaky s položkami; nelze zadat vstupy pomocí `Sources` atributu v úkolech MSBuild, například [Csc](../msbuild/csc-task.md) nebo [Vbc](../msbuild/vbc-task.md). Následující příklad není v souboru projektu platný:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje projekt, který obsahuje všechny vstupní soubory samostatně.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example"></a>Příklad

Následující příklad kódu používá zástupný znak zahrnout všechny soubory *.cs.*

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Postup: Vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)
- [Items](../msbuild/msbuild-items.md)
