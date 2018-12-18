---
title: SGen – úloha | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9e1d87b895108ac890ace3f077d4c1c0a26d8bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268031"
---
# <a name="sgen-task"></a>SGen – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vytvoří sestavení serializace XML pro typy v zadaném sestavení. Tato úloha zabalí nástroj XML Serializer Generator (Sgen.exe). Další informace najdete v tématu [nástroj XML Serializer Generator (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `SGen` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BuildAssemblyName`|Vyžaduje `String` parametru.<br /><br /> Sestavení pro generování kódu serializace pro.|  
|`BuildAssemblyPath`|Vyžaduje `String` parametru.<br /><br /> Cesta k sestavení pro generování kódu serializace pro.|  
|`DelaySign`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že chcete li plně podepsané sestavení. Pokud `false`, určuje, že chcete pouze umístit veřejný klíč v sestavení.<br /><br /> Tento parametr nemá žádný vliv, pokud nejsou použity s buď `KeyFile` nebo `KeyContainer` parametru.|  
|`KeyContainer`|Volitelné `String` parametru.<br /><br /> Určuje kontejner obsahující pár klíčů. Toto podepíše sestavení tak, že vloží veřejný klíč do manifestu sestavení. Úloha se pak podepíše konečné sestavení soukromým klíčem.|  
|`KeyFile`|Volitelné `String` parametru.<br /><br /> Určuje dvojici klíčů nebo veřejný klíč k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.|  
|`Platform`|Volitelné `String` parametru.<br /><br /> Získá nebo nastaví platformě kompilátoru sloužící ke generování výstupního sestavení. Tento parametr může mít hodnotu `x86`, `x64`, nebo `anycpu`. Výchozí hodnota je `anycpu`.|  
|`References`|Volitelné `String[]` parametru.<br /><br /> Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML.|  
|`SdkToolsPath`|Volitelné `String` parametru.<br /><br /> Určuje cestu k sadě SDK nástroje, jako je resgen.exe.|  
|`SerializationAssembly`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje sestavení vygenerované serializace.|  
|`SerializationAssemblyName`|Volitelné `String` parametru.<br /><br /> Určuje název generovaného serializace sestavení.|  
|`ShouldGenerateSerializer`|Vyžaduje `Boolean` parametru.<br /><br /> Pokud `true`, SGen – úloha by měl generovat sestavení serializace.|  
|`Timeout`|Volitelné `Int32` parametru.<br /><br /> Určuje množství času, v milisekundách, po jejichž uplynutí je spustitelný soubor s úkolem ukončen. Výchozí hodnota je `Int.MaxValue`, která udává, že neexistuje žádný časový limit.|  
|`ToolPath`|Volitelné `String` parametru.<br /><br /> Určuje umístění, kde bude úloha načtení základní spustitelného souboru (sgen.exe). Pokud není tento parametr zadán, použije úloha instalační cestu sady SDK odpovídající verzi rozhraní framework, na kterém běží [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`Types`|Volitelné `String[]` parametru.<br /><br /> Získá nebo nastaví seznam pro generování kódu serializace pro konkrétní typy. SGen – vygeneruje kód serializace pouze u typů.|  
|`UseProxyTypes`|Vyžaduje `Boolean` parametru.<br /><br /> Pokud `true`, SGen – úloha generuje kód serializace pouze pro typy XML webové služby serveru proxy.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)



