---
title: 'Postupy: vyčištění sestavení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8c64bb19d65540f8c72be9acb1c5f59deb3c8f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156642"
---
# <a name="how-to-clean-a-build"></a>Postupy: Vyčištění sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při čištění sestavení se odstraní všechny mezilehlé a výstupní soubory, přičemž se zachová pouze soubory projektu a součásti. Ze souborů projektu a součásti lze vytvořit nové instance zprostředkujících a výstupních souborů. Knihovna běžných úloh, které jsou k dispozici, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zahrnuje úlohu [exec](../msbuild/exec-task.md) , kterou můžete použít ke spouštění systémových příkazů. Další informace o knihovně úkolů najdete v tématu odkaz na [úlohu](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Vytvoření adresáře pro výstupní položky  
 Ve výchozím nastavení se soubor. exe, který je vytvořen při kompilování projektu, nachází ve stejném adresáři jako projekt a zdrojové soubory. Výstupní položky se ale obvykle vytvoří v samostatném adresáři.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Vytvoření adresáře pro výstupní položky  
  
1. Pomocí `Property` elementu definujte umístění a název adresáře. Vytvořte například adresář s názvem `BuiltApp` v adresáři, který obsahuje projekt a zdrojové soubory:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2. K vytvoření adresáře použijte úlohu [MakeDir –](../msbuild/makedir-task.md) , pokud adresář neexistuje. Příklad:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Odebírání výstupních položek  
 Před vytvořením nových instancí zprostředkujících a výstupních souborů je vhodné vymazat všechny předchozí instance zprostředkujících a výstupních souborů. Pomocí úlohy [RemoveDir –](../msbuild/removedir-task.md) můžete odstranit adresář a všechny soubory a adresáře, které obsahuje z disku.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Odebrání adresáře a všech souborů obsažených v adresáři  
  
- `RemoveDir`K odebrání adresáře použijte úlohu. Příklad:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu projektu obsahuje nový cíl, `Clean` , který používá `RemoveDir` úlohu k odstranění adresáře a všech souborů a adresářů, které obsahuje. V tomto příkladu `Compile` cíl vytvoří samostatný adresář pro výstupní položky, které jsou odstraněny při vyčištění sestavení.  
  
 `Compile` je definován jako výchozí cíl a je proto použit automaticky, pokud neurčíte jiný cíl nebo cíle. Použijte přepínač příkazového řádku **/target** a určete jiný cíl. Příklad:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Přepínač **/target** lze zkrátit na **/t** a může určovat více než jeden cíl. Chcete-li například použít cíl `Clean` `Compile` , zadejte cíl:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Exec – úloha](../msbuild/exec-task.md)   
 [MakeDir – – úloha](../msbuild/makedir-task.md)   
 [RemoveDir – – úloha](../msbuild/removedir-task.md)   
 [CSc – úloha](../msbuild/csc-task.md)   
 [Targets](../msbuild/msbuild-targets.md)
