---
title: Úloha SGen | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 3be3aa5426c2d1283b8b4cded51cc9c2772642ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682087"
---
# <a name="sgen-task"></a>SGen – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří sestavení serializace XML pro typy v zadaném sestavení. Tato úloha zalomí XML Serializer Generator Tool (Sgen.exe). Další informace najdete v tématu [XML Serializer Generator Tool (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `SGen` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BuildAssemblyName`|Požadovaný parametr `String`.<br /><br /> Sestavení pro generování kódu serializace pro.|  
|`BuildAssemblyPath`|Požadovaný parametr `String`.<br /><br /> Cesta k sestavení, pro který má být generován kód serializace.|  
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , určuje, že chcete sestavení plně podepsané. Pokud `false` , určuje, že chcete umístit pouze veřejný klíč do sestavení.<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá buď s `KeyFile` `KeyContainer` parametrem nebo.|  
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje kontejner obsahující pár klíčů. Tím se sestavení podepíše vložením veřejného klíče do manifestu sestavení. Úloha pak podepíše konečné sestavení pomocí privátního klíče.|  
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje dvojici klíčů nebo veřejný klíč, který se má použít k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.|  
|`Platform`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví platformu kompilátoru, která se používá k vytvoření výstupního sestavení. Tento parametr může mít hodnotu `x86` , `x64` nebo `anycpu` . Výchozí je `anycpu`.|  
|`References`|Volitelný `String[]` parametr.<br /><br /> Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML.|  
|`SdkToolsPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je například resgen.exe.|  
|`SerializationAssembly`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje generované sestavení serializace.|  
|`SerializationAssemblyName`|Volitelný `String` parametr.<br /><br /> Určuje název vygenerovaného sestavení serializace.|  
|`ShouldGenerateSerializer`|Požadovaný parametr `Boolean`.<br /><br /> Pokud `true` by úloha Sgen měla generovat sestavení serializace.|  
|`Timeout`|Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval.|  
|`ToolPath`|Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (sgen.exe). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní, na které běží [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`Types`|Volitelný `String[]` parametr.<br /><br /> Získá nebo nastaví seznam konkrétních typů, pro které se má generovat Serializační kód. SGen vygeneruje kód serializace pouze pro tyto typy.|  
|`UseProxyTypes`|Požadovaný parametr `Boolean`.<br /><br /> Pokud `true` , úloha Sgen generuje kód serializace pouze pro typ proxy webové služby XML.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
