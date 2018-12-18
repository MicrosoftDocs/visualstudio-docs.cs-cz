---
title: 'Postupy: vyloučení souborů ze sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2adfd3d571fe16fcbfe273e5513ebea724403cd
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080685"
---
# <a name="how-to-exclude-files-from-the-build"></a>Postupy: vyloučení souborů ze sestavení
V souboru projektu můžete použít zástupné znaky jako vstupy pro sestavení zahrnout všechny soubory v jednom adresáři nebo vnořenou sadu adresáře. Ale může být jeden soubor v adresáři nebo jednoho adresáře v vnořenou sadu adresáře, které nechcete zahrnout jako vstupy pro sestavení. Tento soubor nebo adresář můžete explicitně vyloučit z seznam vstupů. V projektu, který chcete zahrnout za určitých podmínek může být také soubor. Můžete explicitně deklarovat podmínky, za kterých je soubor součástí sestavení.  
  
## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Vyloučení souboru nebo adresáře ze vstupů pro sestavení  
 Seznamy jsou položky vstupních souborů pro sestavení. Položky, které chcete zahrnout jsou deklarovány, samostatně nebo jako skupiny použití `Include` atribut. Příklad:  
  
```xml  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Pokud použijete zástupné znaky mají zahrnout všechny soubory v jednom adresáři nebo vnořenou sadu adresáře jako vstupy pro sestavení může být jeden nebo více souborů v adresáři nebo v jednom adresáři vnořenou sadu adresáře, které nechcete zahrnout. Chcete-li vyloučit položku ze seznamu položek, použijte `Exclude` atribut.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Zahrnout všechny *.cs* nebo *.vb* soubory s výjimkou *Form2*  
  
-   Použijte jednu z následujících `Include` a `Exclude` atributy:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
    or
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Zahrnout všechny *.cs* nebo *.vb* soubory s výjimkou *Form2* a *Form3*  
  
-   Použijte jednu z následujících `Include` a `Exclude` atributy:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
    or
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Zahrnout všechny *.jpg* soubory nacházejí v podadresářích *Imagí* s výjimkou těch v adresáři *větev Version2* adresáře  
  
-   Pomocí následujících `Include` a `Exclude` atributy:  
  
    ```xml  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Je nutné zadat cestu pro oba atributy. Pokud použijete absolutní cestu k určení umístění souboru v `Include` atribut, musíte taky použít absolutní cesta ve `Exclude` atribut; Pokud použijete relativní cestu ve `Include` atributu, musí také použít relativní cestu ve `Exclude`atribut.  
  
## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Podmínky použití pro vyloučení souboru nebo adresáře ze vstupů pro sestavení  
 Pokud jsou položky, které chcete zahrnout, například v sestavení pro ladění, ale nikoli sestavení pro vydání, můžete použít `Condition` atribut k určení podmínek, za které chcete zahrnout položky.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Zahrnout soubor *Formula.vb* pouze v sestaveních pro vydání  
  
-   Použití `Condition` atribut podobný následujícímu:  
  
    ```xml  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří projekt se všemi *.cs* soubory v adresáři s výjimkou *Form2.cs*.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
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
 [Položky](../msbuild/msbuild-items.md)   
 [Nástroj MSBuild](../msbuild/msbuild.md)   
 [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md)   
