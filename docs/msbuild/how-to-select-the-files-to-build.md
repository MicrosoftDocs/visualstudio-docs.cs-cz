---
title: 'Postupy: výběr souborů pro sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ef956b94ca263dac5ce57c7b122576060bb7a05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820665"
---
# <a name="how-to-select-the-files-to-build"></a>Postupy: výběr souborů pro sestavení
Při vytváření projektu, který obsahuje několik souborů, můžete vytvořit seznam každý soubor samostatně v souboru projektu nebo k zahrnutí všech souborů v jednom adresáři nebo vnořenou sadu adresáře můžete použít zástupné znaky.  
  
## <a name="specify-inputs"></a>Zadejte vstupy  
 Položky představují vstup pro sestavení. Další informace o položky, naleznete v tématu [položky](../msbuild/msbuild-items.md).  
  
 Chcete-li zahrnout soubory pro sestavení, musí být obsažena v seznamu položek v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] souboru projektu. Více souborů je přidat do seznamů položek včetně soubory jednotlivě nebo použití zástupných znaků zahrnout více souborů najednou.  
  
#### <a name="to-declare-items-individually"></a>Chcete-li deklarovat položky jednotlivě  
  
-   Použití `Include` atributy podobně jako následující:  
  
     `<CSFile Include="form1.cs"/>`  
  
     or 
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Pokud se položky v kolekci položek nejsou ve stejném adresáři jako soubor projektu, musíte zadat úplnou nebo relativní cesta k položce. Příklad: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Chcete-li deklarovat více položek  
  
-   Použití `Include` atributy podobně jako následující:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     or 
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specify-inputs-with-wildcards"></a>Zadejte vstupy se zástupnými znaky  
 Můžete také použít zástupné znaky rekurzivně zahrnout všechny soubory nebo pouze konkrétní soubory z podadresáře jako vstupy pro sestavení. Další informace o zástupných znacích naleznete v tématu [položky](../msbuild/msbuild-items.md)  
  
 Následující příklady jsou založené na projekt, který obsahuje soubory grafiky v následujících adresářů a podadresářů, když je soubor projektu umístění v *projektu* adresáře:  
  
 *Project\Images\BestJpgs*  
  
 *Project\Images\ImgJpgs*  
  
 *Project\Images\ImgJpgs\Img1*  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Zahrnout všechny *.jpg* soubory *Imagí* adresáři a jeho podadresářích  
  
-   Pomocí následujících `Include` atribut:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Zahrnout všechny *.jpg* souborů, začínající souborem *img*  
  
-   Pomocí následujících `Include` atribut:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Chcete-li zahrnout všechny soubory v adresářích s názvy končící na *formátu JPG využívá*  
  
-   Použijte jednu z následujících `Include` atributy:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     or
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="pass-items-to-a-task"></a>Předejte položky k úkolu  
 V souboru projektu, můžete použít @ zápis () v úlohách k určení celé položky seznamu jako vstup pro sestavení. Tento typ notation můžete použít, ať už samostatně seznam všech souborů, nebo použít zástupné znaky.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Použití všech Visual C# nebo Visual Basic souborů jako vstupy  
  
-   Použití `Include` atributy podobný následujícímu:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     or 
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  K určení vstupů pro sestavení; musíte použít zástupné znaky s položkami Nelze zadat vstupy pomocí `Sources` atribut [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úkoly, jako [Csc](../msbuild/csc-task.md) nebo [Vbc –](../msbuild/vbc-task.md). V následujícím příkladu není platný v souboru projektu:  
> 
>  `<CSC Sources="*.cs">...</CSC>`  
  
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
 Následující příklad kódu používá zástupný znak zahrnout všechny *.cs* soubory.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Položky](../msbuild/msbuild-items.md)
