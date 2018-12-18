---
title: 'Postupy: použití vyhrazených znaků XML v souborech projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647dba94840383410d06f6e5bf96ec3b0146c394
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077656"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Postupy: použití vyhrazených znaků XML v souborech projektu
Při vytváření souborů projektu, můžete potřebovat použít vyhrazené znaky jazyka XML, třeba v hodnotách vlastnosti nebo hodnoty parametrů úloh. Nicméně některé znaky vyhrazené musí nahradit odpovídajícími pojmenovaná entita, tak, aby soubor projektu může být analyzován.  
  
## <a name="use-reserved-characters"></a>Použití vyhrazených znaků  
 Následující tabulka popisuje vyhrazených znaků jazyka XML, které se musí nahradit odpovídajícími odpovídající pojmenovaná entita tak, aby soubor projektu může být analyzován.  
  
|Vyhrazené znaky|Pojmenovaná entita|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;Očekávaný|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Použití dvojitých uvozovek v souboru projektu  
  
-   Nahraďte odpovídající entity s názvem dvojité uvozovky &amp;quot;. Například umístit dvojitých uvozovek `EXEFile` seznam položek, zadejte:  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu dvojité uvozovky jsou používány zvýrazněte název souboru ve zprávě, která je výstupní soubor projektu.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    
