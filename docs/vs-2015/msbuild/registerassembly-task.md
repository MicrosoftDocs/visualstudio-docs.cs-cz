---
title: Registerassembly – úloha | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ca8def8de6a290822a6736f70a401ed7e0cf9bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230240"
---
# <a name="registerassembly-task"></a>RegisterAssembly – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Načte metadata v rámci zadaného sestavení a přidá nezbytné položky registru, které umožní klientům modelu COM vytvořit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] třídy transparentně. Chování této úlohy je podobné, ale nejsou identické, která [Regasm.exe (Nástroj registrace sestavení)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `RegisterAssembly` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Assemblies`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sestavení, které chcete být registrována pomocí modelu COM.|  
|`AssemblyListFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Obsahuje informace o stavu mezi `RegisterAssembly` úloh a [unregisterassembly –](../msbuild/unregisterassembly-task.md) úloh. Díky tomu `UnregisterAssembly` úloh v pokusu o zrušení registrace sestavení, které se nepodařilo zaregistrovat v `RegisterAssembly` úloh.|  
|`CreateCodeBase`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vytvoří položku základu kódu v registru, který určuje cestu k souboru pro sestavení, která není nainstalována v globální mezipaměti sestavení. Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC).|  
|`TypeLibFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje knihovnu typů, chcete-li generovat z určeného sestavení. Vygenerovanou knihovnu typů obsahuje definice dostupných typů definovaných v rámci sestavení. Knihovnu typů se vygeneruje pouze tehdy, pokud platí jedna z následujících akcí:<br /><br /> -Knihovnu typů s tímto názvem neexistuje v tomto umístění.<br />-Existuje knihovnu typů, ale je starší než předávaný v sestavení.<br /><br /> Pokud je novější než předávaný sestavení knihovny typů, se nevytvoří nový, ale sestavení bude pořád zaregistrovaný.<br /><br /> Pokud tento parametr zadán, musí mít stejný počet položek, jako `Assemblies` parametr nebo úloha se nezdaří. Pokud nejsou zadány žádné vstupy, bude úloha ve výchozím nastavení název sestavení a změňte rozšíření položky na .tlb.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `RegisterAssembly` úloh k registraci sestavení určené parametrem `MyAssemblies` kolekci položek.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



