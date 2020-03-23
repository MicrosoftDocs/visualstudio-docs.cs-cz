---
title: 'Postup: Vyloučit soubory ze sestavení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1914f709a69dbb120e4439ddceeda8b70ad570b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633860"
---
# <a name="how-to-exclude-files-from-the-build"></a>Postup: Vyloučení souborů ze sestavení

V souboru projektu můžete pomocí zástupných znaků zahrnout všechny soubory do jednoho adresáře nebo vnořenou sadu adresářů jako vstupy pro sestavení. V adresáři však může být jeden soubor nebo jeden adresář v vnořené sadě adresářů, které nechcete zahrnout jako vstup pro sestavení. Tento soubor nebo adresář můžete explicitně vyloučit ze seznamu vstupů. V projektu může být také soubor, který chcete zahrnout pouze za určitých podmínek. Můžete explicitně deklarovat podmínky, za kterých je soubor součástí sestavení.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Vyloučení souboru nebo adresáře ze vstupů pro sestavení

 Seznamy položek jsou vstupní soubory pro sestavení. Položky, které chcete zahrnout, jsou deklarovány `Include` buď samostatně, nebo jako skupina používající atribut. Například:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Pokud jste pomocí zástupných znaků zahrnuli všechny soubory do jednoho adresáře nebo vnořenou sadu adresářů jako vstupy pro sestavení, může být v adresáři jeden nebo více souborů nebo jeden adresář v vnořené sadě adresářů, které nechcete zahrnout. Chcete-li položku ze seznamu `Exclude` položek vyloučit, použijte atribut.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Zahrnout všechny soubory *CS* nebo *.vb* kromě *form2*

- Použijte jednu `Include` z `Exclude` následujících možností a atributů:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    – nebo –

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Zahrnutí všech souborů *CS* nebo *.vb* kromě *for2* a *form3*

- Použijte jednu `Include` z `Exclude` následujících možností a atributů:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    – nebo –

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Zahrnutí všech souborů *JPG* do podadresářů *adresáře Obrázky* s výjimkou souborů v adresáři *Version2*

- Použijte následující `Include` `Exclude` a atributy:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Je nutné zadat cestu pro oba atributy. Pokud použijete absolutní cestu k určení `Include` umístění souborů v atributu, `Exclude` musíte také použít absolutní cestu v atributu; Pokud v `Include` atributu použijete relativní cestu, musíte také `Exclude` použít relativní cestu v atributu.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Použití podmínek k vyloučení souboru nebo adresáře ze vstupů pro sestavení

 Pokud existují položky, které chcete zahrnout, například v sestavení ladění, ale ne `Condition` vydání sestavení, můžete použít atribut k určení podmínek, za kterých chcete zahrnout položku.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Zahrnutí souboru *Formula.vb* pouze do sestavení verze

- Použijte `Condition` atribut podobný následujícímu:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří projekt se všemi soubory *CS* v adresáři s výjimkou *Form2.cs*.

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

- [Items](../msbuild/msbuild-items.md)
- [Msbuild](../msbuild/msbuild.md)
- [Postup: Vyberte soubory, které chcete sestavit.](../msbuild/how-to-select-the-files-to-build.md)
