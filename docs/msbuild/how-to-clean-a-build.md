---
title: 'Postupy: Vyčištění sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9d039d6f6f5593538063e751348148786667000
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879054"
---
# <a name="how-to-clean-a-build"></a>Postupy: Vyčištění sestavení
Při čištění sestavení se odstraní všechny pomocných a výstupních souborů, byste museli opustit jenom soubory projektu a součást. Ze souborů projektu a komponenty nových instancí přechodný a výstupních souborů může pak být sestavena. Knihovny běžných úloh, které je součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zahrnuje [Exec](../msbuild/exec-task.md) úkol, který můžete použít ke spuštění příkazů systému. Další informace o knihovně úkoly, naleznete v tématu [úkolů odkaz](../msbuild/msbuild-task-reference.md).  
  
## <a name="create-a-directory-for-output-items"></a>Vytvořte adresář pro výstupní položky  
 Ve výchozím nastavení *.exe* soubor, který je vytvořen při sestavení projektu, je umístěn ve stejném adresáři jako projektu a zdrojových souborech. Nicméně jsou obvykle výstupní položky vytvořené v samostatných directory.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Chcete-li vytvořit adresář pro výstupní položky  
  
1.  Použití `Property` element zadat umístění a název adresáře. Například vytvořte adresář *BuiltApp* v adresáři projektu a zdrojových souborech:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Použití [MakeDir](../msbuild/makedir-task.md) úkolu k vytvoření adresáře, pokud adresář neexistuje. Příklad:  
  
     ```xml
     <MakeDir Directories = "$(builtdir)"  
      Condition = "!Exists('$(builtdir)')" />
     ```
  
## <a name="remove-the-output-items"></a>Odebrat výstupní položky  
 Před vytvořením nové instance pomocných a výstupních souborů, pravděpodobně chcete vymazat všechny předchozí výskyty pomocných a výstupních souborů. Použití [removedir –](../msbuild/removedir-task.md) úlohy můžete odstranit z disku adresář a všechny soubory a adresáře, které obsahuje.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Chcete-li odebrat adresář a všechny soubory obsažené v adresáři  
  
-   Použití `RemoveDir` na odebrat adresář úlohy. Příklad:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu projektu obsahuje nový cíl kódu `Clean`, který používá `RemoveDir` úlohy můžete odstranit adresář a všechny soubory a adresáře, které obsahuje. Také v tomto příkladu `Compile` cílové vytvoří samostatný adresář pro výstupní položky, které jsou odstraněny při sestavení Probíhá čištění.  
  
 `Compile` je definován jako výchozí cíl a je proto použít automaticky, pokud zadáte jiný cíl nebo cíle. Použít přepínač příkazového řádku **-target** určit jiný cíl. Příklad:  
  
 `msbuild <file name>.proj -target:Clean`  
  
 **-Target** přepínače můžete zkrátila na **-t** a můžete zadat více než jeden cíl. Například pro použití cíle `Clean` pak cíl `Compile`, typ:  
  
 `msbuild <file name>.proj -t:Clean;Compile`  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Exec – úloha](../msbuild/exec-task.md)   
 [Makedir – úloha](../msbuild/makedir-task.md)   
 [Removedir – úloha](../msbuild/removedir-task.md)   
 [CSC – úloha](../msbuild/csc-task.md)   
 [Cíle](../msbuild/msbuild-targets.md)