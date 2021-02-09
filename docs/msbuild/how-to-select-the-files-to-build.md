---
title: 'Postupy: výběr souborů k sestavení | Microsoft Docs'
description: Naučte se, jak vybrat soubory, které se mají sestavit v souboru projektu MSBuild, a to tak, že každý soubor uvedeme samostatně nebo pomocí zástupných znaků
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f324fb3999c94d8f26e329859e095f31740c76c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914236"
---
# <a name="how-to-select-the-files-to-build"></a>Postupy: výběr souborů k sestavení

Když sestavíte projekt, který obsahuje několik souborů, můžete každý soubor vytvořit samostatně v souboru projektu nebo můžete použít zástupné znaky k zahrnutí všech souborů do jednoho adresáře nebo do vnořené sady adresářů.

## <a name="specify-inputs"></a>Zadat vstupy

Položky reprezentují vstupy pro sestavení. Další informace o položkách naleznete v tématu [Items](../msbuild/msbuild-items.md).

Chcete-li zahrnout soubory pro sestavení, musí být obsaženy v seznamu položek v souboru projektu MSBuild. Do seznamů položek lze přidat více souborů buď jednotlivě, nebo pomocí zástupných znaků pro zahrnutí mnoha souborů najednou.

#### <a name="to-declare-items-individually"></a>Deklarace položek jednotlivě

- Použijte `Include` atributy podobné následujícímu:

    `<CSFile Include="form1.cs"/>`

    nebo

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Pokud položky v kolekci položek nejsou ve stejném adresáři jako soubor projektu, je nutné zadat úplnou nebo relativní cestu k položce. Příklad: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Deklarace více položek

- Použijte `Include` atributy podobné následujícímu:

    `<CSFile Include="form1.cs;form2.cs"/>`

    nebo

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Zadat vstupy se zástupnými znaky

Můžete také použít zástupné znaky k rekurzivnímu zahrnutí všech souborů nebo pouze konkrétních souborů z podadresářů jako vstupů pro sestavení. Další informace o zástupných znacích najdete v tématu [položky](../msbuild/msbuild-items.md) .

Následující příklady jsou založeny na projektu, který obsahuje grafické soubory v následujících adresářích a podadresářích, se souborem projektu umístěným v adresáři *projektu* :

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Zahrnutí všech souborů *. jpg* do adresáře a podadresářů *obrázků*

- Použijte následující `Include` atribut:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Zahrnutí všech souborů *. jpg* počínaje *img*

- Použijte následující `Include` atribut:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Zahrnutí všech souborů v adresářích s názvy končícími na *JPGs*

- Použijte jeden z následujících `Include` atributů:

    `Include="Images\**\*jpgs\*.*"`

    nebo

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Předání položek úkolu

V souboru projektu můžete použít notaci @ () v úlohách k určení celého seznamu položek jako vstupu pro sestavení. Tento zápis můžete použít, pokud chcete zobrazit seznam všech souborů samostatně, nebo použít zástupné znaky.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Použití všech souborů Visual C# nebo Visual Basic jako vstupů

- Použijte `Include` atributy podobné následujícímu:

    `<CSC Sources="@(CSFile)">...</CSC>`

    nebo

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Chcete-li určit vstupy pro sestavení, je nutné použít zástupné znaky s položkami. vstupy nemůžete zadat pomocí `Sources` atributu v úlohách MSBuild, jako je [CSC](../msbuild/csc-task.md) nebo [Vbc](../msbuild/vbc-task.md). Následující příklad není platný v souboru projektu:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>Příklad 1

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

## <a name="example-2"></a>Příklad 2

Následující příklad kódu používá zástupný znak pro zahrnutí všech souborů *. cs* .

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

- [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)
- [Položky](../msbuild/msbuild-items.md)
