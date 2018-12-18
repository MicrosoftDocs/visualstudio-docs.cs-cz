---
title: Assignculture – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c35d949f2d3cf3924a63ce6db0e596af1fccddbd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235648"
---
# <a name="assignculture-task"></a>AssignCulture – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento úkol přijímá seznam položek, které mohou obsahovat platný řetězec identifikátor jazykové verze .NET jako součást názvu souboru a vytvoří položky, které mají metadat s názvem `Culture` obsahuje odpovídající jazykovou verzi identifikátor. Například má název souboru Form1.fr-fr.resx vložený jazykovou verzi identifikátor "fr-fr", takže tento úkol vytvoří položka, která má stejný název souboru s metadaty `Culture` rovna `fr-fr`. Úloha také vytvoří seznam názvů souborů pomocí jazykové verze odebrána z názvu souboru.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `AssignCulture` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AssignedFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek dostali `Files` parametrů, s `Culture` přidání pro každou položku metadat položky.<br /><br /> Pokud příchozí položky `Files` již obsahuje parametr `Culture` položka metadat, původní položka metadat se používá.<br /><br /> Pouze přiřadí úlohu `Culture` položka metadat, pokud název souboru obsahuje identifikátor platné jazykové verze. Identifikátor jazykové verze musí být mezi poslední dvě tečky v názvu souboru.|  
|`AssignedFilesWithCulture`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje dílčí položky z `AssignedFiles` parametr, který máte `Culture` položka metadat.|  
|`AssignedFilesWithNoCulture`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje dílčí položky z `AssignedFiles` parametr, který není `Culture` položka metadat.|  
|`CultureNeutralAssignedFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje stejný seznam položek, které se vytvářejí v `AssignedFiles` parametrů, s výjimkou pomocí jazykové verze odebrána z názvu souboru.<br /><br /> Úloha pouze odebere jazykovou verzi z názvu souboru, pokud je identifikátor platná jazyková verze.|  
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje seznam souborů s názvy vložených jazykovou verzi přiřadit jazykovou verzi pro.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad provede `AssignCulture` úloh s `ResourceFiles` kolekci položek.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 Následující tabulka popisuje výhody výstupní položky po spuštění úlohy. Metadata položky se zobrazí v závorkách po provedení položky.  
  
|Kolekce položek|Obsah|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (žádné další metadata)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (žádné další metadata)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`žádné další metadata)|  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



