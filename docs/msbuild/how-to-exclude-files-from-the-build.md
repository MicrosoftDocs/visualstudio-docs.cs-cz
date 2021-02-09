---
title: 'Postupy: vyloučení souborů ze sestavení | Microsoft Docs'
description: Přečtěte si, jak explicitně vyloučit nebo podmíněně zahrnout soubory ze sestavení v souborech projektu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e838460f1e42f34e92a99198b9d4a0e34ce71dcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914371"
---
# <a name="how-to-exclude-files-from-the-build"></a>Postupy: vyloučení souborů ze sestavení

V souboru projektu můžete použít zástupné znaky k zahrnutí všech souborů do jednoho adresáře nebo vnořené sady adresářů jako vstupů pro sestavení. Může však existovat jeden soubor v adresáři nebo jeden adresář ve vnořené sadě adresářů, které nechcete zahrnout jako vstup pro sestavení. Tento soubor nebo adresář můžete explicitně vyloučit ze seznamu vstupů. V projektu může být také soubor, který chcete zahrnout pouze za určitých podmínek. Můžete explicitně deklarovat podmínky, za kterých je soubor součástí sestavení.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Vyloučení souboru nebo adresáře ze vstupů pro sestavení

 Seznamy položek jsou vstupní soubory pro sestavení. Položky, které chcete zahrnout, jsou deklarovány buď samostatně, nebo jako skupiny pomocí `Include` atributu. Příklad:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Pokud jste použili zástupné znaky, které budou zahrnovat všechny soubory v jednom adresáři nebo vnořené sady adresářů jako vstupy pro sestavení, může existovat jeden nebo více souborů v adresáři nebo v jednom adresáři v rámci vnořené sady adresářů, které nechcete zahrnout. Chcete-li vyloučit položku ze seznamu položek, použijte `Exclude` atribut.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Zahrnutí všech souborů *. cs* nebo *. vb* s výjimkou *Form2*

- Použijte jeden z následujících `Include` atributů a `Exclude` :

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    nebo

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Zahrnutí všech souborů *. cs* nebo *. vb* s výjimkou *Form2* a *Form3*

- Použijte jeden z následujících `Include` atributů a `Exclude` :

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    nebo

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Zahrnutí všech souborů *. jpg* v podadresářích adresáře *imagí* s výjimkou těch v adresáři *Version2*

- Použijte následující `Include` atributy a `Exclude` :

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Je nutné zadat cestu pro oba atributy. Použijete-li absolutní cestu k určení umístění souborů v `Include` atributu, je nutné také použít absolutní cestu v `Exclude` atributu; Pokud použijete relativní cestu v `Include` atributu, je nutné také použít relativní cestu v `Exclude` atributu.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Použití podmínek k vyloučení souboru nebo adresáře ze vstupů pro sestavení

 Pokud existují položky, které chcete zahrnout, například v sestavení ladění, ale ne v sestavení verze, můžete použít `Condition` atribut k určení podmínek, za kterých se má položka zahrnout.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Zahrnutí *vzorce souboru. vb* pouze do sestavení vydaných verzí

- Použijte `Condition` atribut podobný následujícímu:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří projekt se všemi soubory *. cs* v adresáři s výjimkou *Form2.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" Exclude="Form2.cs"/>

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

- [Položky](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [Postupy: výběr souborů k sestavení](../msbuild/how-to-select-the-files-to-build.md)
